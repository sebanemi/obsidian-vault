# Introducción

La arquitectura de la computadora es el hardware, pero no podemos estudiar el hardware sin estudiar el software a la vez.

En 8 bits, la cantidad de combinaciones posibles es $2^8$.

Se utiliza el sistema binario porque es más preciso a la hora de realizar acciones en los componentes.

Uno de los componentes más importantes de las computadoras son los [[Transistores]].

Dentro de una computadora, un transistor es una llave que se cierra con altos (1, HIGH, Estado de saturación) y se abre con bajos (0, LOW, Estado de corte).

Mezclando transistores y poniendo diodos yo puedo obtener distintas [[Compuertas Lógicas]] para obtener resultados.

## Clock

**Clock**: Otro componente, multivibrador que lo que hace es producir señales de onda cuadrada.

No puede haber computadoras sin clock.

Para poder manejar los cambios de estado si o sí tiene que haber un clock.

## [[Procesador]]

El procesador tiene que tener:

- secuencia
- iteración
- poder sincronizarse con eventos externos

## Interrupciones

Eventos externos se manejan como Interrupciones (*Interrupt Requests*).

La idea de dos bits de interrupciones es usar una para **no enmascarables** (Atención sí o sí) y otra para **enmascarables**.

El procesador debe guardar en memoria los registros para que si llega una interrupción, luego de atenderla, vuelva a lo que estaba antes.

---

**ALU**: Unidad lógica aritmética. Circuitos combinacionales y algebra de Boole. Se encarga de resolver comparaciones, sumas. 

---
## Datasheet MC6800

HALT: Se detiene el funcionamiento del procesador cuando está en 0
$Vss$ : Tierra, GND
$Vcc$ : Positivo, entrada de alimentación.
NMI: Interrupciones no enmascarables, ósea que no hay ninguna bandera que haga que no se ejecute.
IRQ: Pedido de interrupción, ósea que es una interrupción enmascarable. Las interrupciones enmascarables se guardan en las banderas (*Condition Code*, 6 bits, toma decisiones de saltar o no saltar).

Además de escribir en memoria, se escribe en las interfaces (serie y paralela). Una interface en serie manda 1 y 0 en serie. Una interface en paralelo pone en 1 y 0 varios pines a la vez. El procesador no solo escribe y lee en memoria sino que escribe o lee de una *patita* en paralelo.

R/W: Se comunica con la memoria y/o las interfaces y si está en alto es porque voy a leer está en alto y si voy a escribir está en bajo. Sabe donde por una dirección dada por el [[Bus de Direcciones]].

El fabricante para facilitar la interpretación de las direcciones de memoria en vez de darlas en binario, las da en **hexadecimal**.

**LEER** en el micro: Inicialmente está en el Fx0000.  Para las direcciones de inicio de reset o de interrupciones, en ese vector van las direcciones de inicio para cada caso. Para direccionar una locación de memoria necesito 16 bit (necesito 2 byte para cada dirección de memoria). Cada celda de memoria tiene 1 byte, entonces el bus de datos/dirección tiene 1 byte. 

La próxima instrucción se la da al procesador a través del **[[Contador de Programa]]**. Las instrucciones no ocupan todas el mismo espacio en memoria. Es un registro donde figura la dirección de la próxima instrucción, que necesita 16 bits para saber a donde ir.

Luego de una interrupción, usa una pila para volver a lo que estaba haciendo antes de tratar el evento. **[[Puntero de Pila]]**, pila de estados del procesador.

La memoria no está dentro de este chip, sino que está afuera en otro lado, no están integradas.

Apuntar a una dirección de memoria que está afuera y , de acuerdo a R/W, leer o escribir la información mediante el bus de datos, por eso es bidireccional.

Las instrucciones son de 8 bit, procesa 8 bit.

Los output buffer solamente guarda las direcciones de memoria.

Three-state control: Una señal que viene de afuera que al mandar un alto, se desconecta el bus de datos (estado de alta impedancia), entonces otro procesador se puede hacer cargo de las instrucciones y la memoria.

[[Acumuladores A y B]]: No puede manejar contenido de la memoria si estos datos no están en alguno o en ambos de los acumuladores. Para hacer cualquier operación lógica o matemática los datos tienen que estar en alguno o en los dos.

H de High y L de Low. En HIGH los bits mas significativos y en LOW, los menos.