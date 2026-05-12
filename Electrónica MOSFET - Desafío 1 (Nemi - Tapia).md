1. Determinar si el circuito puede analizarse como pequeña señal

Inicialmente suponemos que el transistor está trabajando como amplificador. Además, luego de realizar las correcciones en el circuito, al variar la resistencia del potenciómetro, vemos que las rpm del motor aumentan de manera progresiva y no de manera abrupta, lo que sugiere que también estamos trabajando en pequeña señal.

2. Determinar el valor de $V_G$

$V_G$, al ser los valores de tensión del Gate, va a estar condicionado por el potenciómetro, entonces este valor puede variar entre 0V y 9V según la posición del cursor del potenciómetro.

3. Determinar el valor de $V_{GS}$

$$V_{GS}=V_G-V_S$$
Como el Source está conectado a masa, entonces $V_S=0V$, por lo tanto, el valor de $V_{GS}$ va a ser igual al valor de $V_G$.
$$V_{GS}=V_G$$
4. Determinar el modelo equivalente de pequeña señal en el MOSFET

El modelo realizado ya es el de pequeña señal por lo que el análisis sería el anterior.

5. Determinar dos errores de funcionamiento presentes en el circuito.

- El primer error que se encontró es que la resistencia del potenciómetro tenía un valor muy pequeño ($250p\Omega$), el cual fue cambiado por un valor mayor ($10k\Omega$).
- El segundo error que se encontró es que el potenciómetro solo tenía el pin Wipe y tierra conectados, entonces faltaba conectar el positivo, por lo que se hizo un puente desde el positivo de la parte superior de la protoboard hasta el positivo de la parte inferior de la misma.