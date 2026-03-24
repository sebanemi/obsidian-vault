Es la forma en la que el microprocesador obtiene el operando (dato) que necesita. La instrucción no solo dice qué hacer, sino también dónde está el dato. El dato puede estar: dentro de la instrucción, en un registro o en memoria.

---
## Inmediato

El dato ya viene **dentro de la instrucción**.

`LDAA #10`
- `#` indica inmediato
- No hay acceso a memoria adicional
- El valor ya está pegado en la instrucción

La CPU lee la instrucción, toma el valor directamente y lo carga en A.

Se lo suele usar en constantes y en inicializaciones pero como **limitación** tiene que no se puede modificar ese valor sin cambiar el código.

---
## Directo

Se usa una dirección de 8 bits, que apunta a la página cero (0x0000 - 0x00FF).

`LDAA $80`

La CPU toma $80, lo interpreta como dirección 0x0080 y accede a la memoria ahí. Tiene la **ventaja** de ser más rápido (menos ciclos) y tener instrucciones más cortas.

Se optimiza porque no hace falta calcular una dirección de 16 bits completa y el hardware es más simple.

---
## Extendido

Se usa una dirección completa de 16 bits

`LDAA $1234`

La CPU lee los dos bytes de la dirección y accede a directamente a la memoria en 0x1234. Conviene usarlo cuando los datos no están en la página cero. Sin embargo, es más lento y tiene una instrucción más larga.

---
## Indexado

Usa el [[Registro Índice]] (IX) + un offset

`LDAA 5,X`

La CPU toma el valor de IX, suma el offset (5) y accede a esa dirección.

Es el modo más potente porque permite recorrer arrays, manejar estructuras dinámicas y simular punteros. **Detalle**: El offset es de 8 bits y puede ser positivo o negativo (dependiendo del ensamblador).

---
## Inherente

No necesita operandos.

`INCA`

Opera únicamente sobre un registro implícito (A en este caso). Su uso se da en operaciones internas simples o en control de estado.

---
## Relativo

Usado en saltos (branches)

`BEQ LABEL`

La CPU toma el valor de [[Contador de Programa]], suma un nuevo desplazamiento (offset) y salta a esa nueva dirección
$$
Direccion = CP + offset
$$
El salto depende de la posición actual, por o que es un código relocatable.

---

| Modo      | Dirección calculada | Flexibilidad | Velocidad |
| --------- | ------------------- | ------------ | --------- |
| Inmediato | No aplica           | Baja         | Muy alta  |
| Directo   | 8 bits              | Media        | Alta      |
| Extendido | 16 bits             | Alta         | Media     |
| Indexado  | IX + offset         | Muy alta     | Media     |
| Relativo  | CP + offset         | Alta         | Alta      |
| Inherente | Implícito           | Baja         | Muy alta  |

