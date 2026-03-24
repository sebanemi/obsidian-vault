# 🧠 📌 Pines del **MC6800** (explicación clara)

Los pines se agrupan en **5 grandes tipos**:

---

# 🔌 1. Alimentación

* **Vcc (pin 8)** → +5V
* **Vss (pin 1 y 21)** → Tierra (GND)

👉 Sin esto → no funciona nada.

---

# ⏱️ 2. Control del sistema

### 🔹 **RESET (pin 40)**

* Reinicia el micro
* Lo pone en estado inicial

👉 Es como prender la compu desde cero.

---

### 🔹 **ϕ2 (pin 37) – [[Clock]]**

* Señal de reloj
* Marca el ritmo del procesador

👉 Sin clock → el micro no “late”.

---

### 🔹 **TSC (pin 39)**

* Control del bus tri-state
* Permite que el micro libere el bus

👉 Se usa cuando hay varios dispositivos en el bus.

---

### 🔹 **HALT (pin 2)**

* Detiene el procesador

👉 Congela la ejecución.

---

# ⚡ 3. [[Interrupciones]]

### 🔹 **IRQ (pin 4)**

* Interrupción normal (enmascarable)

👉 Se puede ignorar con software.

---

### 🔹 **NMI (pin 6)**

* Interrupción no enmascarable

👉 NO se puede ignorar (muy importante, ej: errores críticos).

---

# 📦 4. [[Bus de datos]]

### 🔹 **D0 – D7 (pines 33–26)**

* Bus de datos de **8 bits**
* Bidireccional

👉 Por acá viajan los datos.

---

# 📍 5. [[Bus de Direcciones]] 

### 🔹 **A0 – A15 (pines 9–20 y 22–25)**

* Bus de direcciones de **16 bits**

👉 Permite direccionar hasta:
[
2^{16} = 64K \text{ direcciones}
]

👉 Sirve para decir:

> “quiero leer/escribir en ESTA posición de memoria”

---

# 🔄 6. Control del bus y memoria

### 🔹 **R/W (pin 34)**

* Define operación:

  * 1 → Leer
  * 0 → Escribir

👉 Fundamental para saber qué hace el micro.

---

### 🔹 **VMA (pin 5) – Valid Memory Address**

* Indica que la dirección es válida

👉 Señal de “ok, estoy accediendo a memoria”.

---

### 🔹 **BA (pin 7) – Bus Available**

* Indica que el bus está libre

👉 Usado en DMA.

---

### 🔹 **DBE (pin 36) – Data Bus Enable**

* Habilita el bus de datos

---

### 🔹 **R/W + VMA juntos**

👉 Son CLAVE:

* R/W → qué hace
* VMA → cuándo es válido

---

# ❌ 7. Pines no conectados

### 🔹 **N.C. (pins 35 y 38)**

* No conectados

👉 No se usan.

---

# 🧠 RESUMEN ULTRA CLARO

* **A0–A15 → Dirección**
* **D0–D7 → Datos**
* **R/W → Tipo de operación**
* **Clock → Ritmo**
* **IRQ / NMI → Interrupciones**
* **RESET → Reinicio**

---

# 💡 TIP DE PARCIAL (IMPORTANTE)

Si te preguntan:

👉 “¿Cómo se comunica con memoria?”

Decís:

> Usa un bus de direcciones (A0–A15) para seleccionar la posición, un bus de datos (D0–D7) para transferir información y la señal R/W para definir si lee o escribe.

---
Perfecto, ahora sí armemos el **flujo completo bien ordenado y realista** para el **Motorola MC6800** en los dos casos.

---

# 🔹 🧠 CASO 1: sumar dos números “grandes” ya en memoria

Supongamos que querés hacer:

```text
0x1234 + 0x0102
```

---

## 🔄 🔹 Flujo completo

### 1. 📥 Lectura desde memoria

Para cada byte:

1. La CPU pone la dirección en el **bus de direcciones (16 bits)**
    
2. Activa señal de **READ**
    
3. La memoria responde poniendo el byte en el **bus de datos (8 bits)**
    
4. La CPU lo carga en un registro (A o B)
    

👉 Esto se hace varias veces (porque son varios bytes)

---

### 2. 🧠 Suma en la ALU (clave)

Como es de 8 bits:

- Suma byte bajo
    
- Guarda **carry**
    
- Suma byte alto + carry
    

👉 Todo en pasos separados

---

### 3. 📤 Escritura del resultado

Para cada byte del resultado:

1. CPU pone dirección destino
    
2. CPU pone el byte en el bus de datos
    
3. Activa **WRITE**
    
4. Memoria guarda el valor
    

---

## 🔹 🎯 Resumen mental

- Memoria → CPU (por bus de datos)
    
- CPU → ALU (operación en 8 bits)
    
- CPU → Memoria (resultado, byte a byte)
    

---

## ✔️ Justificación

- Bus de datos = 8 bits → todo va byte a byte
    
- ALU = 8 bits → operaciones fragmentadas
    
- Bus de direcciones = 16 bits → indica dónde

# 🔥 🔹 Modelo mental final (el más importante)

👉 Todo el sistema funciona así:

1. CPU dice **“dónde”** → bus de direcciones
    
2. CPU dice **“leer o escribir”** → bus de control
    
3. Se mueve el **byte** → bus de datos
    

Y eso aplica a:

- RAM
    
- ROM
    
- Teclado
    
- Pantalla

👉 **Sí, un teclado _puede_ generar una interrupción… pero no necesariamente.**

Depende de **cómo esté diseñado el sistema**.

---

# 🔹 🧠 En el **Motorola MC6800**

Tiene:

- **IRQ** → interrupción enmascarable
    
- **NMI** → interrupción no enmascarable
    

---

# 🔹 🔄 Dos formas de leer el teclado

## ✅ 1. Polling (sin interrupciones)

👉 La CPU pregunta constantemente:

```asm
leer_teclado:
  LDA $F000   ; leo el teclado
  CMP #0
  BEQ leer_teclado
```

### 🔹 Flujo:

- CPU consulta el teclado todo el tiempo
    
- Si no hay dato → sigue preguntando
    
- Si hay dato → lo procesa
    

👉 ❗ No usa interrupciones

---

## ✅ 2. Con interrupciones (más avanzado)

👉 El teclado “avisa” cuando hay un dato

---

## 🔄 Flujo con interrupción

### 1. ⌨️ Usuario presiona tecla

El dispositivo:

- Coloca el dato internamente
    
- Activa la línea **IRQ** (o NMI)
    

---

### 2. ⚡ La CPU detecta la interrupción

- Termina la instrucción actual
    
- Guarda el estado (PC, registros) en el stack
    
- Salta a una **rutina de interrupción (ISR)**
    

---

### 3. 🧠 Rutina de interrupción

Ejemplo:

```asm
ISR_teclado:
  LDA $F000   ; leo el dato del teclado
  ; procesar
  RTI
```

---

### 4. 🔙 Vuelta al programa

- Se restaura el estado
    
- Continúa donde estaba
    

---

# 🔹 🎯 Entonces, respondiendo directo:

👉 **Sí, el ingreso por teclado puede ser una interrupción**  
👉 Pero también puede ser simplemente polling

---

# 🔹 ⚠️ Diferencia clave

|Método|Quién inicia|
|---|---|
|Polling|CPU|
|Interrupción|Dispositivo|

---

# 🔹 🔥 ¿Cuándo se usa cada uno?

### Polling:

- Sistemas simples
    
- Fácil de implementar
    
- Menos eficiente
    

### Interrupciones:

- Sistemas más complejos
    
- Más eficiente
    
- CPU no pierde tiempo esperando
    

---

# 🔹 💣 NMI vs IRQ

- **IRQ** → teclado, mouse, cosas normales
    
- **NMI** → eventos críticos (fallos, reset, etc.)
    

👉 Un teclado normalmente usaría **IRQ**, no NMI

---

# ✔️ Justificación

El MC6800 tiene líneas de interrupción porque:

- Permiten reaccionar a eventos externos sin polling
    
- Mejoran eficiencia
    
- Son fundamentales en sistemas interactivos
    

Pero el uso real depende del hardware conectado y del diseño del sistema.

---

# 🔥 Idea final (nivel examen)

👉 **El teclado no “es” una interrupción**  
👉 Es un dispositivo que _puede generar_ interrupciones
