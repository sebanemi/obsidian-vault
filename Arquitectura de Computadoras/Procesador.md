Un procesador es un autómata de estados finitos, que movido por un clock realiza un proceso repetitivo de **búsqueda** y  **decodificación** de las instrucciones y operandos de un programa, las **ejecuta** siguiendo las secuencias o iteraciones indicadas en el mismo, pudiendo **decidir** alterarla de acuerdo al resultado de las instrucciones  lógicas o matemáticas ejecutadas.

## Métodos

Leer, escribir y memorizar datos en código binario, para comunicarse con las MEMORIAS e INTERFACES de entradas y salidas.

EJECUTAR INSTRUCCIONES: Lógicas, Matemáticas, de movimiento de Datos, de Saltos, de interrupción y detención ejecutándolas secuencial mente o en lazos Iterativos de acuerdo al programa.

DECISIÓNES: Salta a distintas partes del PROGRAMA de acuerdo al resultado de Instrucciones LÓGICAS y Matemáticas

INTERRUPCIONES: De la secuencia del programa para atender eventos exteriores imprevistos en su ocurrencia.

DESCONECTARSE: Poniendo su Bus de Direcciones y Datos en Estado de Alta Impedancia para permitir que otro procesador acceda a las mismas memorias y periféricos

---
## Funcionalidad

Conectado a memorias e interfaces seriales y paralelas permite resolver problemas computacionales en plataformas informáticas, robóticas y mecatrónicas. 

## Bloques de su arquitectura

Que lo conectan con el exterior [[Bus de Datos]], [[Bus de Direcciones]] y [[Bus de Control]], para leer y escribir en memorias e interfaces de entrada/salida y otros dispositivos externos.

**Registros internos**: [[Contador de Programa]], [[Acumuladores A y B]], [[Registro Índice]], [[Registro de Condiciones]] y [[Puntero de Pila]]

**Bloques internos**: [[Unidad Lógica Aritmética]], [[Decodificador de Instrucciones]] y [[Unidad de control]] no son accesibles para el programador pero conocer su existencia nos ayuda a entender el funcionamiento del dispositivo.

---
El avance en la ejecución del programa siendo la secuencia de instrucciones o la iteración cuando están anidadas y las decisiones o bifurcaciones saltos del programa de acuerdo al resultado de la ejecución de instrucciones que alteran distintas banderas del registro de condiciones.