1. ¿Cuál es la entrada del circuito?

La entrada es la tensión variable regulada por el pin central del potenciómetro. Esta señal se distribuye mediante el puente azul largo hacia las Gate de ambos transistores.

2. ¿Cuál es la salida?

La salida es el nodo común donde se unen los drenadores de ambos MOSFETs: el del NMOS es la columna 3 y el del PMOS es la columna 7. Este nodo se extiende directo al ánodo LED para comandar su encendido.

3. ¿Cuándo conduce cada transistor?

Los transistores operan en corte y saturación como interruptores complementarios según la tensión de entrada:

- NMOS: Tiene su Source a masa. Conduce cuando la entrada es alta ($\approx 9V$). Al activarse, tira la salida a tierra
- PMOS: Tiene su Source a $+9V$. Conduce cuando la entrada entrada es baja ($\approx 0V$). Al activarse, conecta la salida a la línea de alimentación.

4. ¿En qué condiciones el LED enciende y apaga?

El LED enciende cuando la entrada es baja. El PMOS conduce y el NMOS se apaga, aplicando los $+9V$ de la fuente al ánodo del LED. Por el otro lado, el LED se apaga cuando la entrada es alta. El NMOS conduce y el PMOS se apaga, derivando la salida a tierra y dejando el LED sin diferencia de potencial.

5. Tabla de verdad completa:

| **Entrada**  | **Estado NMOS** | **Estado PMOS** | **Estado del LED** | **Salida** |
| ------------ | --------------- | --------------- | ------------------ | ---------- |
| **0** (Bajo) | APAGADO (Corte) | CONDUCE (Sat.)  | ENCENDIDO          | **1**      |
| **1** (Alto) | CONDUCE (Sat.)  | APAGADO (Corte) | APAGADO            | **0**      |
6. ¿Qué función lógica implementa el sistema?

El circuito implementa la función lógica NOT (inversor). La salida es siempre el estado lógico inverso de la señal que entrega el potenciómetro de entrada.