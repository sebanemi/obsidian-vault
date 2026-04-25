# Introducción

Tecnologías que “no pasan de moda”, siempre son útiles.

**Terminal boba**: “Pantalla y teclado” que se conecta a una computadora más grande para hacer sus propios procesos.

Al aparecer las PCs se cambia el paradigma de terminal boba y comienza la arquitectura [[Arquitectura Cliente-Servidor]].

[[Ethernet]]: cable coaxial, 10Mb/s

## Evaluaciones

- 2 parciales (1 primer cuatri, 1 segundo cuatri)
- 1 trabajo de investigación de a 2
- Guía de ejercicios
- Trabajo aparte con Buscaglia ([[Electrónica]])

---

# Unidad 1

## Telecomunicaciones

Telecomunicaciones: Tele de lejano, communicatio de comunicación. Son las técnicas que permiten comunicarnos más allá de la simple presencia de las personas.

- [[LAN]]
- [[WAN]]

En su momento las redes estaban separadas dependiendo de si eran de mensajes escritos, voz, imágenes o entre computadoras.

## Historia

En el siglo 19 estaba transmisor y receptor unidos por un conductor metálico.

En el siglo 20 se dan enlaces inalámbricos mediante radio.

## Teleinformática

Teleinformática: El vínculo entre telecomunicaciones e informática.

- Permite el procesamiento distribuido
- Permite el procesamiento digital de las señales
- Aparecen nuevos servicios como telefonía IP, TV/IP
- Aparece la convergencia de servicios
- Todas las señales se transmiten por la misma red
- Un solo proveedor de servicios (Competencia)
- Permite la globalización
- Pasó de los monopolios a la desregulación

> [!NOTE]
> Hoy, las casas normales tienen en un mismo dispositivo un [[Router]], un [[Modem]], un [[Access Point]] y un [[Switch]].

## Conmutación

[[Conmutación]]: Almacenar y reenviar en la dirección que corresponda.

## Infocomunicaciones

Infocomunicaciones: Las comunicaciones como medio de transporte de información. La informática como forma de comunicación.

## Comunicación de datos

Comunicación de datos: Permite el intercambio de información entre usuarios del sistema.

Me interesa que sea:

### Confiable

- confidencialidad (que otro no vea los datos que envío)
- autenticación (que al que se le comunique sea realmente quien dice ser)
- no repudio (registros de enviar datos)

### Sin errores

- no tener malos componentes

### En tiempo real

Un tiempo tal en el que yo pueda interactuar con un equipo y en base a la respuesta tomar acción pero depende de la aplicación.

### Flexible

- Que haya varios caminos para llegar al mismo destino

### Segura

- Que esté disponible cuando yo la quiera usar

## Equipos terminales

Una computadora es un [[Equipo Terminal de Datos]].

La computadora trabaja como emisor y como receptor, la cual tiene un [[Controlador de comunicaciones]].

Entre dos [[ETD]] la comunicación se da gracias al [[Enlace de datos]].

Los ETD se conectan al [[Equipo de Comunicación de Datos]], los cuales se conectan entre sí mediante las [[Líneas de comunicación]], formando un [[Circuito de datos]].

## Modem

[[Modem banda base]]: Convierte la tensión recibida a una aceptada.

## Tipos de red

[[Red Half-Duplex]]: Sólo puede comunicarse uno de los dispositivos. El que ocupa el canal ya está, el otro no lo puede usar.

## Switch

[[Switch]]: Aprende las direcciones madres de cada una de las bocas y sabe a donde mandar la información correcta.

## Regenerador

[[Regenerador de pulso]]

## Red

Red: Conjunto de recursos de comunicaciones y de informática que forman un sistema, para el transporte de información.

Hoy hay redes integradas, multimediales y convergentes.

## Arquitectura de comunicaciones

### Conectividad

Conectividad: Posibilidad de interconectar equipos de diferentes marcas y proveedores, integrándose en redes armónicas con normas comunes.

Las redes de telecomunicaciones necesitan:

- Establecer el enlace
- Se controla el flujo de datos a través del enlace
- Liberar el enlace

Es una red orientada a la conexión.

La red es un modelo de interconexión y un conjunto de reglas para comunicar los terminales.

## Arquitecturas propietarias

### [[SNA]]

SNA (System Network Architecture): Inteconexión de redes de computadoras con una fuerte centralización. Un procesador central importante (mainframe), computadores medianos y estaciones bobas.

### [[DNA]]

DNA (Distributed Network Architecture): Basa en siete capas. Permite que en el desarrollo de cada capa haya equipos de gente trabajando al mismo tiempo.

Aparece la modularización.

## Arquitecturas abiertas

### [[OSI]]

OSI (Open Systems Interconnection)
Desarrollada por la UIT. 
La **ISO** hizo el modelo **OSI**.
Este es un "mapa" o guía
Usa 7 capas, donde capa capa le agrega una cabecera donde están los campos de control según la misión que tiene la capa. Ambas cosas forman la unidad de protocolo de datos:
1. Física: Señalización y transmisión binaria. Establece las especificaciones mecánicas, eléctricas y lógicas para ejecutar los procedimientos necesarios para comenzar a mantener y finalizar la conexión física.
2. Enlace de datos: Direccionamiento físico
3. Red: Determinación de ruta y direccionamiento lógico
4. Transporte: Conexión de extremo a extremo y confiabilidad
5. Sesión: Comunicación entre dispositivos de red
6. Presentación: Representación de datos y encriptación
7. Aplicación: Servicios de red a aplicaciones. 

El modelo distribuye entre las capas las funciones que se necesitan cumplir para lograr una comunicación segura y eficiente. Los protocolos de cada capa deben proporcionar servicios a la capa inmediata superior mediante funciones.
### [[DARPA]]

DARPA (Defense Advanced Research Project Agency): Incluye los protocolos conocidos como [[TCP/IP]]
Conmutación de paquetes + TCP/IP (Tecnologías aplicadas)
TCP trabaja en capa de transporte e IP trabaja en capa de red.
La capa par del TCP es la misma terminal a la que se envía.
Usa 4 capas:
1. Interfase de red: Capa de enlace + física. Utiliza una sub-capa para poder subdividir la tarea.
	- IEEE 802.3: Protocolo contencioso, "*me peleo por el medio*".
	- IEEE 802.4: Protocolo determinístico, Token Bus. 
	- IEEE 802.5: Red Token Ring
	- X25: Protocolo WAN
	- FRAME RELAY / PPP / ATM: Conmutación de paquetes, circuitos virtuales
2. Internet: Capa de red
    - IP
    - ARP
    - RARP
    - ICMP: Para ver como están las conexiones. Ej: Comando `ping` o `tracert`.
    - RP
3. Transporte: Capa de transporte
    - TCP: Muy seguro, servicio orientado a la conexión. Antes de la comunicación de datos hace un *apretón de manos*. Mensajes secuenciales. Para no tener bits erróneos.
    - UDP: No orientado a la conexión. No le importa si el receptor está despierto o no. Es sensible al tiempo. 
4. Aplicación: Capa de sesión + presentación + aplicación

---

La comunicación entre capas es entre capas pares. 

## [[La red Internet]]

Red internacional por un conjunto de varias redes independientes operadas en forma autónoma, interconectadas por medio de protocolos y procedimientos normalizados como estándares de internet que permiten comunicaciones entre 2 equipos terminales de cualquier red si se identifican con una dirección numérica única (**IP**). 

DNS: Sistema de nombres de dominio que utiliza nombres separados por puntos. Su jerarquia es de **DERECHA A IZQUIERDA**. 

El responsable primario es la Internet Society, pero delega la administracion y organizacion en:
- Internet Architecture Board
- Internet Engineering Task Group

**Normalización**: Consenso documentado con especificaciones técnicas u otros criterios a ser usado como regla, guia o definicion de características para asegurar que determinado material, producto, proceso o servicio sea el ideal para su propósito. 
Cada vez que saco un protocolo, saco un grupo de trabajo para ir mejorando ese protocolo.

==VER CURSO DE CISCO==

¿Cómo conmutan las redes?
Conmutación (NODOS):
- De circuitos: Enlace físico permanente. Requiere señalización. Orientado a la conexión. No conmutación de paquetes
- De paquetes o circuitos virtuales: Se le da una etiqueta a cada bloque de datos y tiene definido el circuito que debe tomar. No se toma decisión de encaminamiento. Si se cae un nodo, se pierde la comunicación. Orientado a la conexión. No es segura. 
- De mensajes o datagrama: Bloques de datos. Cada nodo toma una decisión de encaminamiento. Red de mejor esfuerzo. Red segura, pero lenta

---
# Redes de Backbone

## Fibra óptica

La fibra optica no nació en los medios de comunicaciones sino que nació en la medicina. Se dieron cuenta que la fibra optica servia para transmitir señales de dato. 

Las fibras opticas basan su funcionamiento en las letes de la reflexion y la refraccion de la luz (Ley de Snell). Se trata de la relacion existente entre la velocidad de la luz en el vacio ($C=3*10^8 m/s$) y su velocidad en un medio material, lo que da lugar al **indice de refracción** del medio.
$$
n =C/v
$$
**Reflexión**: es el fenómeno por el cual un rayo de luz rebota al incidir sobre una superficie, permaneciendo en el mismo medio.

**Refracción**: es el cambio de dirección que experimenta un rayo de luz al pasar de un medio a otro con distinto índice de refracción debido a la variación de su velocidad.

(FISICA II - Óptica)

Componente de fibra óptica:
- Núcleo: Por donde viaja la luz
- Cladding: rodea al núcleo y tiene un índice de refracción menor, lo que permite la **reflexión interna total** para mantener la luz confinada.

Los haces de luz (modos) cuando entran como pulso de onda cuadrada, salen como onda tipo "distribución normal" porque los haces llegan de manera diferente, a tiempo diferente. [[Dispersión moderna]]. Directamente proporcional a la distancia. Fenómenos más importantes de la fibra óptica multimodo.

**Longitud de onda**: Distancia real que recorre una perturbación en un determinado intervalo de tiempo. $v=\lambda*f$ .
- La frecuencia solo depende de la fuente que produzca la luz, entonces podemos suponer un f = cte independientemente del medio.

**Ventanas**: son rangos específicos de longitudes de onda en los que la transmisión de luz presenta mínima atenuación y dispersión, permitiendo una comunicación más eficiente. La luz se "frena" menos. Hay un pico aprox a los 1400 nm que es la absorción producida por el ion hidroxilo $OH^{-}$ (Pico de agua).
### Conformación de una fibra óptica
Fibras ópticas son un compuestas de hilos finos de cristal en acoda, llamada el corazón (core) y el revestimiento, que puede transmitir la luz en aproximadamente dos terceras partes la velocidad de la luz en el vacío.

**Multimodo**: es aquella en la que la luz se propaga por múltiples trayectorias o modos dentro del núcleo, lo que puede generar dispersión y limitar la distancia de transmisión. Menos ancho de banda y menos distancia.

**Monomodo**: es aquella en la que la luz se propaga en un único modo o trayectoria, permitiendo menor dispersión y mayores distancias de transmisión. No hay dispersión normal, sino dispersión cromática.
- NZ-DSF: Fibra con dispersión desplazada no nula. Para redes de grandes transmisiones de datos. DWDM: Multiplexación de señal pero longitud de onda transmitida.

Código de colores: Amarillo, monomodo. Naranja, multimodo

Fibra óptica pasiva

**Atenuación**
- Factores internos: Efecto de fabricación
- Factores externos: Efecto de instalación o de acciones internas
**Dispersión**: Espaciamiento de los pulsos de luz mientras esta viaja por la fibra.
- Cromática
- Normal
- por modo de polarización
**No linealidades**: Efectos acumulativos

Dentro de una red de fibra optica encontramos diferentes componentes que son los encargados de generar, trnamsitir y recibir las señales optimas
- Emisores y receptores de luz
	- LEDs
	- Láser

EDFA

EMPALME DE FUSIÓN

---
WDM: Wavelength Division Multiplexing. Consiste en utilizar las dos ventanas de transmision a la vez.

DWDM: Dense Wavelength Division Multiplexing. 

**Demultiplexaje por prisma**: Se hace pasar un rayo de luz policromático por un prisma y las diferentes longitudes de onda son refractadas en ángulos diferentes. Estos rayos luego son enfocados por un lente hasta el punto de entrada a una nueva fibra. El mismo proceso puede ser usado a la inversa para multiplexar. 

**Demultiplexaje por difracción**: Se basa en el principio de difracción de la luz y lo que se hace es que se hace incidir un rayo policromático de luz sobre un arreglo de líneas finas que reflejan o transmiten la luz, cada longitud de onda se refracta de manera diferente en la rejilla.

**Demultiplexaje por filtrado**

Componentes de una red DWDM:
- Transmisión
- Amplificación
- Gestión de servicios
- Red de administración
- ETC

OADM: Dispositivos que permiten insertar o remover una o varias señales ópticas en un determinado punto de la fibra.

---
## Par trenzado
Se trenzan para cancelar los campos magnéticos generados por la corriente que pasa por cada cable, y que no generen ruido.
- UTP: Sin protección.
- STP: Con protección.

---

Conexion UTP:
	Nosotrs usamos la norma A

---
# Unidad II - Transmisión de señales
Vamos a ver la parte física de las señales.

Dijimos que teniamos redes convergentes, osea que brindan cualquier tipo de servicio. Hay señales eléctricas, ópticas o electromagnéticas.

**Señales analógicas**: Pueden ser presentadas por funciones que toman un numero infinto de valores en cualquier intervalo de la variable. La inteligencia está en la onda, entonces si cambias la forma de la onda, cambias la información.

**Señales digitales**: Pueden ser representadas por funciones que toman un numero finito de valores en cualquier intervalo de la variable. La inteligencia está en la codificación y no en la forma.

Un **CODEC** es un codificador y decodificador de señales. Transmiten señales analógicas por redes digitales. El CODEC generalmente no está en mi casa, sino en las instalaciones del prestador de servicio. 

Un **MODEM** es un modulador y demodulador de señales. Agarra la señal digital, la modula y permite que se pueda transmitir un señal digital por una red analógica.

El MODEM y el CODEC son equipos simétricos pero que usan técnicas distintas.

No existen canales ideales, por lo que las señales se modifican en el viaje. En el medio hay fenómenos que afectan a la señal:
- Atenuación: Debilitación de señal
- Distorsión: Deformación de la señal debido a la disposición del circuito si es resistivo o capacitivo
- Ruido: Generado por el flujo de electrones. Siempre presente
- Retardos: Cuando debo esperar demasiado para recuperar todo el pulso.

Siempre que tengo una señal analógica uso un amplificador, pero no lo puedo usar infinititas veces porque además de amplificarse la señal, se amplifica el ruido y distorsión.

Las señales digitales se deforman a lo largo del canal. Para aumentar el alcance se debe repetir y regenerar los pulsos en punto intermedias. Se usan repetidores regenerativos que regeneran cada pulso y vuelven a armar la señal original. Las señales que entran están deformadas y con ruido, las señales que salen son digitales y de la misma forma que la original.

Aparece un concepto nuevo en las señales digitales, que es la duración del pulso, representado por $\tau$ (Tau)

Longitud de onda:  $\lambda = c/f$, entonces $[\lambda]=(m/s)/(1/s) => [\lambda]=m$

La serie de Fourier permite analizar el comportamiento de las señales digitales que atraviesan un canal analógico. 

$\tau = T*1/2$ 

En la transformada de fourier quiero saber cuanto energía aporta cada término para determinar si es "importante" o no.

¿Ancho de banda de que? Ancho de banda de la señal, el que sale con fourier

El ancho de banda de canal es arbitrario, porque se suelen definir donde la atenuacion disminuye el valor de la señal a la mitad del centro del canal. 

