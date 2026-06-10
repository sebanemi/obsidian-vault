#include <TinyGPSPlus.h>
#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define GPS_BAUDRATE  9600
#define BTN_UP        2    // Navegar arriba / ciclar pantallas
#define BTN_SEL       3    // Seleccionar destino / volver a selección
#define SCREEN_WIDTH  128
#define SCREEN_HEIGHT 64
#define OLED_RESET    -1
#define OLED_ADDR     0x3C

// ─── Destinos hardcodeados ────────────────────────────────────
struct Destino {
  const char* nombre;   // Nombre corto para el menú (máx ~16 chars)
  const char* titulo;   // Título largo para la pantalla de info
  double lat;
  double lon;
};

const Destino DESTINOS[] = {
  { "Cancha de River",  "ESTADIO MONUMENTAL",  -34.5453, -58.4497 },
  { "Cancha de Tigre",  "ESTADIO DELLAGIOVANA",-34.4260, -58.5795 },
  { "Obelisco",         "OBELISCO - CABA",      -34.6037, -58.3816 },
  { "Mar del Plata",    "MAR DEL PLATA",        -38.0023, -57.5575 },
};
const uint8_t NUM_DESTINOS = sizeof(DESTINOS) / sizeof(DESTINOS[0]);

// ─── Estado global ────────────────────────────────────────────
TinyGPSPlus gps;
Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

// Modo: 0 = selección de destino, 1 = navegación (pantallas info)
uint8_t modo          = 0;
uint8_t destinoSel    = 0;   // índice del destino resaltado en el menú
uint8_t destinoActivo = 0;   // índice del destino confirmado
uint8_t pantalla      = 0;   // 0=posición, 1=distancia/rumbo, 2=hora/fecha
#define NUM_PANTALLAS 3

bool btnUpAnterior    = HIGH;
bool btnSelAnterior   = HIGH;

// ─── Prototipos ───────────────────────────────────────────────
void actualizarOLED();
void decimalAGMS(double valor, int& grados, int& minutos, int& segundos);
void pantallaMenu();
void pantallaPosicion(double lat, double lon);
void pantallaDistancia(double lat, double lon);
void pantallaHora();
void indicadorPantalla();

// ══════════════════════════════════════════════════════════════
void setup() {
  Serial.begin(9600);
  Serial1.begin(GPS_BAUDRATE);
  pinMode(BTN_UP,  INPUT_PULLUP);
  pinMode(BTN_SEL, INPUT_PULLUP);

  if (!display.begin(SSD1306_SWITCHCAPVCC, OLED_ADDR)) {
    Serial.println("OLED no encontrada");
    while (true);
  }
  display.clearDisplay();
  display.setTextColor(SSD1306_WHITE);
  display.setTextSize(1);
  display.setCursor(16, 24);
  display.print("Esperando GPS...");
  display.display();

  // Arrancar directo en el menú de selección
  actualizarOLED();
}

// ══════════════════════════════════════════════════════════════
void loop() {
  // Alimentar el parser GPS
  while (Serial1.available()) {
    char c = Serial1.read();
    gps.encode(c);
    Serial.write(c);
  }

  // ── Leer BTN_UP ──────────────────────────────────────────
  bool btnUpActual = digitalRead(BTN_UP);
  if (btnUpAnterior == HIGH && btnUpActual == LOW) {
    if (modo == 0) {
      // Navegar hacia abajo en el menú (botón arriba cicla circularmente)
      destinoSel = (destinoSel + 1) % NUM_DESTINOS;
    } else {
      // Ciclar entre pantallas de info
      pantalla = (pantalla + 1) % NUM_PANTALLAS;
    }
    actualizarOLED();
  }
  btnUpAnterior = btnUpActual;

  // ── Leer BTN_SEL ─────────────────────────────────────────
  bool btnSelActual = digitalRead(BTN_SEL);
  if (btnSelAnterior == HIGH && btnSelActual == LOW) {
    if (modo == 0) {
      // Confirmar destino y pasar a modo navegación
      destinoActivo = destinoSel;
      modo    = 1;
      pantalla = 0;
    } else {
      // Volver al menú de selección
      modo = 0;
    }
    actualizarOLED();
  }
  btnSelAnterior = btnSelActual;

  // Actualizar cuando llegan datos GPS nuevos (solo en modo navegación)
  if (modo == 1 && (gps.location.isUpdated() || gps.time.isUpdated())) {
    actualizarOLED();
  }
}

// ══════════════════════════════════════════════════════════════
void actualizarOLED() {
  display.clearDisplay();

  if (modo == 0) {
    pantallaMenu();
    display.display();
    return;
  }

  // Modo navegación
  if (!gps.location.isValid()) {
    display.setTextSize(1);
    display.setCursor(20, 20);
    display.print("Sin fix GPS...");
    display.setCursor(12, 32);
    display.print("Buscando senial");
    display.setCursor(4, 50);
    display.print("[SEL] = Cambiar dest.");
    display.display();
    return;
  }

  double lat = gps.location.lat();
  double lon = gps.location.lng();

  switch (pantalla) {
    case 0: pantallaPosicion(lat, lon); break;
    case 1: pantallaDistancia(lat, lon); break;
    case 2: pantallaHora();             break;
  }

  display.display();
}

// ─── Menú de selección de destino ────────────────────────────
//
//  ┌──────────────────────────────┐
//  │  >> SELECCIONAR DESTINO <<   │
//  │──────────────────────────────│
//  │  Cancha de River             │  ← ítem normal
//  │ >Cancha de Tigre             │  ← ítem seleccionado (invertido)
//  │  Obelisco                    │
//  │  Mar del Plata               │
//  │  [UP]=Navegar  [SEL]=OK      │
//  └──────────────────────────────┘
void pantallaMenu() {
  // Título
  display.setTextSize(1);
  display.setCursor(4, 0);
  display.print("> SELECCIONAR DESTINO");
  display.drawLine(0, 9, 127, 9, SSD1306_WHITE);

  // Mostrar hasta 4 ítems (caben bien en la pantalla)
  // Si hay más de 4 destinos, hacer scroll centrado en el seleccionado
  int8_t inicio = (int8_t)destinoSel - 1;
  if (inicio < 0) inicio = 0;
  if (inicio > (int8_t)(NUM_DESTINOS - 4)) inicio = max(0, (int8_t)(NUM_DESTINOS - 4));

  for (uint8_t i = 0; i < 4 && (inicio + i) < NUM_DESTINOS; i++) {
    uint8_t idx = inicio + i;
    uint8_t y   = 12 + i * 11;

    if (idx == destinoSel) {
      // Ítem seleccionado: fondo blanco, texto negro
      display.fillRect(0, y - 1, 128, 11, SSD1306_WHITE);
      display.setTextColor(SSD1306_BLACK);
      display.setCursor(2, y);
      display.print(">");
      display.setCursor(10, y);
      display.print(DESTINOS[idx].nombre);
      display.setTextColor(SSD1306_WHITE);
    } else {
      display.setCursor(10, y);
      display.print(DESTINOS[idx].nombre);
    }
  }

  // Pie de pantalla
  display.drawLine(0, 55, 127, 55, SSD1306_WHITE);
  display.setCursor(0, 57);
  display.print("[UP]=Mover  [SEL]=OK");
}

// ─── Convierte decimal → Grados°Min'Seg" ─────────────────────
void decimalAGMS(double valor, int &grados, int &minutos, int &segundos) {
  double absVal = fabs(valor);
  grados   = (int)absVal;
  double minFrac = (absVal - grados) * 60.0;
  minutos  = (int)minFrac;
  segundos = (int)round((minFrac - minutos) * 60.0);
  // Manejar overflow de segundos
  if (segundos >= 60) { segundos = 0; minutos++; }
  if (minutos  >= 60) { minutos  = 0; grados++;  }
}

// ─── Pantalla 0: Posición ─────────────────────────────────────
void pantallaPosicion(double lat, double lon) {
  int g, m, s;
  char buf[20];

  display.setTextSize(1);
  display.setCursor(0, 0);
  display.print("  POSICION");
  indicadorPantalla();
  display.drawLine(0, 9, 127, 9, SSD1306_WHITE);

  // ── Latitud ──────────────────────────────────────────────────
  decimalAGMS(lat, g, m, s);
  display.setTextSize(1);
  display.setCursor(0, 12);
  display.print("Lat:");
  display.setTextSize(1);
  display.setCursor(24, 12);
  display.print(lat >= 0 ? "N" : "S");

  display.setTextSize(2);
  display.setCursor(0, 22);
  snprintf(buf, sizeof(buf), "%d%c%02d'%02d\"", g, 0xF8, m, s);
  display.print(buf);

  // ── Longitud ─────────────────────────────────────────────────
  decimalAGMS(lon, g, m, s);
  display.setTextSize(1);
  display.setCursor(0, 40);
  display.print("Lon:");
  display.setTextSize(1);
  display.setCursor(24, 40);
  display.print(lon >= 0 ? "E" : "O");

  display.setTextSize(2);
  display.setCursor(0, 49);
  snprintf(buf, sizeof(buf), "%d%c%02d'%02d\"", g, 0xF8, m, s);
  display.print(buf);
}

// ─── Pantalla 1: Distancia / Rumbo ───────────────────────────
void pantallaDistancia(double lat, double lon) {
  double destLat = DESTINOS[destinoActivo].lat;
  double destLon = DESTINOS[destinoActivo].lon;

  double distM   = TinyGPSPlus::distanceBetween(lat, lon, destLat, destLon); //Como lo hace
  double rumbo   = TinyGPSPlus::courseTo(lat, lon, destLat, destLon);
  const char* cardinal = TinyGPSPlus::cardinal(rumbo);
  char buf[12];
  char linea[20];

  display.setTextSize(1);
  display.setCursor(0, 0);
  display.print(DESTINOS[destinoActivo].titulo);
  indicadorPantalla();
  display.drawLine(0, 9, 127, 9, SSD1306_WHITE);

  display.setTextSize(1);
  display.setCursor(0, 13);
  display.print("Distancia:");

  display.setTextSize(2);
  display.setCursor(0, 22);
  if (distM < 1000.0) {
    dtostrf(distM, 6, 0, buf);
    snprintf(linea, sizeof(linea), "%s m", buf);
  } else {
    dtostrf(distM / 1000.0, 6, 2, buf);
    snprintf(linea, sizeof(linea), "%s km", buf);
  }//estudiar
  display.print(linea);

  display.setTextSize(1);
  display.setCursor(0, 40);
  display.print("Rumbo:");

  display.setTextSize(2);
  display.setCursor(0, 49);
  dtostrf(rumbo, 3, 0, buf);
  snprintf(linea, sizeof(linea), "%s%c  %s", buf, 0xF8, cardinal);//estudiar
  display.print(linea);
}

// ─── Pantalla 2: Hora / Fecha ─────────────────────────────────
void pantallaHora() {
  char buf[20];

  display.setTextSize(1);
  display.setCursor(0, 0);
  display.print("  HORA / FECHA");
  indicadorPantalla();
  display.drawLine(0, 9, 127, 9, SSD1306_WHITE);

  if (!gps.time.isValid() || !gps.date.isValid()) {
    display.setTextSize(1);
    display.setCursor(10, 28);
    display.print("Sin hora GPS...");
    display.display();
    return;
  }

  uint8_t hora = (gps.time.hour() + 21) % 24;
  snprintf(buf, sizeof(buf), "%02d:%02d:%02d", hora, gps.time.minute(), gps.time.second());
  display.setTextSize(2);
  display.setCursor(16, 18);
  display.print(buf);

  snprintf(buf, sizeof(buf), "%02d/%02d/%04d",
           gps.date.day(), gps.date.month(), gps.date.year());
  display.setTextSize(2);
  display.setCursor(4, 44);
  display.print(buf);
}

// ─── Indicador de pantalla [N/3] ─────────────────────────────
void indicadorPantalla() {
  char ind[6];
  snprintf(ind, sizeof(ind), "[%d/%d]", pantalla + 1, NUM_PANTALLAS);
  display.setCursor(128 - (strlen(ind) * 6), 0);
  display.print(ind);
}