Se aplica a señales digitales que se envían mediante cables de cobre. 

Son aquellas señales que, generadas por una fuente de información, no sufren ningún proceso de modulación o tratamiento a su salida. 

Un cable tiene parámetros eléctricos distribuidos que se pueden representar mediante un modelo con parámetros concentrados.
Los parámetros eléctricos de un cable de cobre más significativos en la banda de frecuencias telefónicas son:
- La resistencia del conductor, en serie con la señal
- La capacidad entre el conductor y la tierra, en derivación

Un cable inicialmente tiene descargado el capacitor. Cuando se aplica a la entrada una tensión fija comienza un proceso de carga hasta que a la salida aparece el valor de la entrada. Cuando la tensión de entrada pasa a cero comienza a descargarse el capacitor hasta que la tensión de salida llega a cero.

Los procesos de carga y descarga tienen una duración que depende del producto entre R y C ($\tau$).

El comportamiento de un cable en función de la frecuencia depende de su configuración.
- El cable de cobre se comporta como un filtro pasabajos, dejando pasar las señales hasta una frecuencia de corte
- El cable de cobre con transformadores se comporta como un filtro pasabanda dejando pasar las señales dentro de un intervalo de frecuencias.

# Códigos de línea o banda base
ABs (señal), ABI (línea)

- Importancia de las frecuencias bajas. Problema de acoplamiento o transformadores
- Envío de señal de sincronismo
- Umbral de decisión. Probabilidad de error
- Dependencia entre simbolos
- Potencia transmitido
- Ancho de pulsos. Ancho de banda

Clasificación de las señales:
- Según la **polaridad**: 
	- Unipolar +0 0-
	- Polar +-
	- Bipolar +0-
- Según el **ancho del pulso** ($\tau$)
	- No retorno a Zero (NRZ) -> $\tau = Is$
	- Retorno a Zero (RZ) -> $\tau < Is$

# Tipos de señal digital

**CUIDADO**: Las definiciones de los códigos no están totalmente normalizados, hay variantes.

- **Unipolares:** Tienen dos niveles, donde uno es cero y el otro es positivo o negativo.
- **Polares:** Utilizan dos niveles de diferente polaridad, típicamente positivo (+V) y negativo (-V).
- **Bipolares (pseudoternarias):** Utilizan tres niveles de amplitud (+, 0, -). Generalmente, el "0" lógico se representa con nivel cero y el "1" con polaridades alternadas para evitar la componente continua.

El uso de transmisiones banda base es frecuente porque:
- El costo de los equipos es más bajo que los modems.
- Permite extender el alcance de las interfaces digitales

La señal original es codificada para:
- Eliminar o disminuir la componente continua de la señal
- Transmitir una señal de sincronismo desde el transmisor hacia el receptor
- Detectar la presencia de la señal en la línea.
- Acomodar el espectro de la señal dentro de la banda pasante del medio.
**NO SEPUEDE TODO A LA VEZ**

- **NRZ**: La señal no retorna a cero durante todo el ancho del pulso, la transmisión del uno es la emisión de un pulso y la transmisión del cero es la no emisión de un pulso. Unipolar porque el 1 toma siempre la misma polaridad y el 0 no tiene polaridad. SEÑAL ON/OFF. Los bits están representados por pulsos que ocupan la totalidad del intervalo significativo (Is: ancho de pulso)
- **RZ**: Los bits se representan por pulsos que ocupan una parte (la mitad) del intervalo significativo

# Códigos usados para señales en banda base
- Unipolar sin retorno a cero
- Unipolar con retorno a cero
- Polar sin retorno a cero
- Polar con retorno a cero
- Bipolar con retorno a cero
- Bipolar sin retorno a cero
- Codificación diferencial
- Manchester
- Manchester diferencial
- MILLER
- HDB-3
- Codigo 4B3T

Los **códigos de línea** (o códigos de banda base) son técnicas para representar símbolos digitales mediante señales eléctricas equivalentes que se envían directamente por un medio físico sin modulación. Su objetivo es adaptar la señal a la línea eliminando la componente continua, transmitiendo sincronismo y permitiendo detectar la presencia de señal.

A continuación se detallan los códigos más usados según los criterios de **polaridad** y **ancho de pulso ($\tau$)**:

### 1. Clasificación por Pulso y Polaridad

- **Unipolar sin retorno a cero (NRZ):** Es la señal más simple (señal ON/OFF); un valor toma una polaridad fija (positiva o negativa) y el otro es cero. El pulso ocupa todo el intervalo significativo ($\tau = Is$). Posee componente continua y no tiene suficientes transiciones para sincronismo.
- **Unipolar con retorno a cero (RZ):** Los bits se representan con pulsos que retornan a nivel cero antes de finalizar el intervalo (usualmente a la mitad, $\tau < Is$). Requiere mayor ancho de banda que el NRZ pero facilita el sincronismo entre 1s consecutivos.
- **Polar sin retorno a cero (NRZ):** Asigna polaridad positiva a los "1" y negativa a los "0", ocupando todo el intervalo. No posee componente continua si los bits son equiprobables y requiere menor ancho de banda que la señal polar con retorno a cero.
- **Polar con retorno a cero (RZ):** Existe una corriente breve para los bits "1" (positiva) y "0" (negativa) que retorna a cero antes de terminar el intervalo. Es una **señal autosincronizante**.
- **Bipolar sin retorno a cero (AMI):** También conocido como **AMI (Alternate Mark Inversion)**. El "0" es nivel cero y el "1" toma valores de polaridad alternados (+ y -). No posee componente continua, pero pierde sincronismo ante largas cadenas de ceros.
- **Bipolar con retorno a cero (RZ):** Utiliza polaridad alternada para los "1" y nivel cero para los "0", pero el pulso del "1" retorna a cero a mitad del intervalo. Es autosincronizante e igual de eficiente que AMI en eliminar la componente continua.

### 2. Codificaciones Especiales y Estándares

- **Codificación Diferencial:** La información se representa por **cambios de estado** en lugar de niveles fijos. Al muestrear, un cambio de polaridad respecto a la muestra anterior representa un "1", y la ausencia de cambio un "0". Es robusto ante inversiones accidentales de los cables en la instalación.
- **Manchester (Bifase):** Garantiza una **transición en la mitad de cada intervalo**: positiva para un "1" y negativa para un "0". Es el estándar para redes **Ethernet 10Base-T**. Elimina la componente continua y es autosincronizante, aunque duplica el ancho de banda necesario respecto a NRZ.
- **Manchester Diferencial:** Siempre hay una transición en la mitad del intervalo para el reloj; la presencia de una transición adicional al **inicio** del intervalo representa un "0" y su ausencia un "1". Detectar transiciones es más fiable que comparar niveles respecto a tierra. Se usa en redes **Token Ring**.
- **MILLER (Modulación por retardo):** Para un "1" hay una transición en la mitad del intervalo. Para un "0" no hay transición, a menos que el bit siguiente sea también "0", en cuyo caso hay una transición al final del intervalo actual. Reduce el ancho de banda y posee menos componentes de baja frecuencia que Manchester.
- **HDB-3 (High Density Bipolar 3):** Es un código de alta densidad basado en AMI para sistemas europeos de 2 Mbps. Reemplaza cadenas de **cuatro ceros** por secuencias especiales con "violaciones" de polaridad (000V o B00V) para mantener el sincronismo sin añadir componente continua.
- **Código 4B3T (4 Binario - 3 Ternario):** Mapea bloques de 4 bits en 3 símbolos ternarios (+, 0, -). Se utiliza en sistemas de alta velocidad (hasta 140 Mbps sobre cable coaxial) porque **reduce el ancho de banda necesario en un 25%** al transmitir más información por cada elemento de señal.

**FILTROS**: Circuitos, sistemas o partes de redes que presentan características selectivas respecto de las frecuencias.