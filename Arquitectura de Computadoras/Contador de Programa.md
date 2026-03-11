El contador de programa es un registro especial dentro de la CPU que guarda la dirección de memoria de la próxima instrucción que el procesador debe ejecutar. 

## Idea simple
Se lo puede imaginar como un marcador o puntero que señala qué instrucción del programa se ejecuta después.

> [!NOTE] En otras palabras
> El CP le dice al procesador "donde seguir leyendo el programa"

Cuando una computadora ejecuta un programa, sigue el ciclo básico de la CPU.
1. Busca instrucción -> Mira el valor del CP para saber qué dirección de memoria leer
2. Decodificar -> La instrucción leída se interpreta para entender qué operación debe realizarse
3. Ejecutar -> Se ejecuta la instrucción
4. Actualizar el CP -> El contador de programa se incrementa para apuntar a la siguiente instrucción.

El Contador de Programa no siempre aumenta de uno en uno sino que cuando hay instrucciones como `if`, `while`, `for`, `goto` o saltos de programa, el procesador cambia manualmente el valor del contador para ir a otra parte del programa.
