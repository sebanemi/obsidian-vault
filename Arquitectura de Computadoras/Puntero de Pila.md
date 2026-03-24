Es un registro especial dentro del procesador que guarda la dirección de memoria del elemento que está en la parte superior de la pila.

En la pila se almacenan temporalmente cosas como:
- Direcciones de retorno de funciones
- Variables locales
- Registros del procesador
- Parámetros de funciones
- **GUARDA EL ESTADO DE LOS DATOS**

Cuando llega una interrupción, el procesador automáticamente guarda información importante en la pila.
1. Llega la interrupción
2. El procesador detiene temporalmente el programa actual
3. Guarda en la pila:
	- El contador de programa
	- El registro de estado
4. El stack pointer se actualiza porque se agregaron datos a la pila
5. El procesador salta a la rutina de servicio de interrupción
Cuando la interrupción termina
6. Se recuperan esos valores de la pila
7. El stack pointer vuelve a su posición anterior
8. El programa continúa exactamente donde estaba

Las interrupciones requieren preservar el contexto de ejecución del programa. Esto se logra utilizando la pila: el procesador empuja automáticamente el contador de programa y el registro de estado al stack, actualizando el stack pointer. La rutina de servicio de interrupción se ejecuta y luego una instrucción especial de retorno restaura esos valores desde la pila. Este mecanismo garantiza que el flujo del programa pueda continuar correctamente después de atender tanto interrupciones **enmascarables** como **no enmascarables**.