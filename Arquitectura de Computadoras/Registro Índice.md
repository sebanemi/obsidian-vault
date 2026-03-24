Registro interno de 16 bits que se usa principalmente par direccionamiento indexado, es decir, para acceder a datos en memoria de forma flexible. Es de 16 bits, por lo que puede apuntar a toda la memoria. No es acumulador (No se usa directamente para operaciones aritméticas típicas).

El registro índice guarda una **dirección base de memoria**. A esa dirección se le puede sumar un desplazamiento (offset) para acceder a distintas posiciones.

$$
Direccion = IX + offset
$$
Esto permite recorrer estructuras como arrays, tablas o buffers de forma muy eficiente.

---
## Usos:
1. Recorrer arreglos (arrays)
	- IX apunta al inicio del array
	- Vas sumando offsets (0, 1, 2, ...) para acceder a cada elemento
2. Acceso dinámico a memoria -> Se puede trabajar con direcciones que cambian en tiempo de ejecución
3. Estructuras más complejas
	 Sirve para manejar:
	 - Tablas
	 - Buffers
	 - Estructuras tipo registros

---

Sin un registro índice, tendrías que recalcular direcciones manualmente y usar muchas instrucciones adicionales. El IX simplifica esto porque actúa como un **puntero base**, permite cálculos de direcciones rápidos en hardware y hace el código más corto y eficiente.