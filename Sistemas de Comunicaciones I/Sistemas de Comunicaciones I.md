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
