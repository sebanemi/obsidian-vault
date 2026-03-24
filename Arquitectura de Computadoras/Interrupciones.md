Una interrupción es básicamente pausar el programa actual, atender algo y volver al programa. Para que esto funcione, la CPU debe guardar el estado actual en registros (como el [[Puntero de Pila]]), saltar a una rutina especial (**ISR: Interrupt Service Routine**), ejecutar esa rutina y restaurar el estado para continuar. En el motorola MC6800, las interrupciones permiten que la CPU deje lo que está haciendo y atienda un evento, para después continuar como si nada.

---
## Software Interrupt (SWI)
Es una interrupción provocada por el propio programa.

Cuando se ejecuta `SWI`, la CPU guarda en la pila el [[Contador de Programa]], registros y banderas. Activa la bandera de interrupciones para evitar otras y salta a una dirección fija (vector de SWI).

Este tipo de interrupción sirve para llamar rutinas del sistema, hacer debugging y para simular interrupciones de hardware. Entonces, es como una "*llamada especial*" pero más poderosa.

Se usa porque permite el control total del sistema, separa código de usuario y código de sistema, y es una forma estandarizada de invocar servicios.

---
## Non-Maskarable Interrupt (NMI)
Es una interrupción de hardware que **NO se puede ignorar**.

Non-maskarable significa que no depende de la bandera de interrupciones y la CPU siempre la atiende.

La CPU, exactamente igual que en otras interrupciones, guarda el estado en la pila, salta a su vector específico y ejecuta la ISR.

Este tipo de interrupciones se utiliza en eventos críticos, como fallas de energía, errores graves de hardware o situaciones donde no responder sería peligroso.

Si esta interrupción pudiera bloquearse el sistema podría ignorar eventos críticos, por eso está diseñada para ser imposible de desactivar.

---
## Interrupt Request (IRQ)
Es una interrupción de hardware normal (enmascarable).

Maskarable significa que se puede habilitar o deshabilitar usando la bandera I (Interrupt Mask):
- I = 1 -> interrupciones deshabilitadas
- I = 0 -> Interrupciones habilitadas

La CPU, si IRQ está habilitada, termina la instrucción actual, guarda el estado en la pila, salta al vector de IRQ y ejecuta la ISR.

Este tipo de interrupción es muy usada en ingreso de datos por teclado, para timers o para dispositivos externos. Básicamente: eventos "normales" del sistema.

Permite controlar cuando atender interrupciones, evitar interrupciones en secciones críticas y mejorar la consistencia del programa.