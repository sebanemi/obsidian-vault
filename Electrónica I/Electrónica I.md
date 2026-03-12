Electrónica: Análisis de señales en cualquier tipo de sistemas.
## Libros

- Boylestad-Nashelsky (Para labo)
- Sedra-Smith (Física de semiconductores)
- Malvino (Implementación de circuitos electrónicos)

## Semiconductores

Cap 2 Malvino, Cap 1 Boylestad, Cap 3 Sedra.

Se estudian las propiedades fundamentales de los semiconductores, en especial el silicio, y como el dopado modifica de manera decisiva su conductividad eléctrica.

### Materiales

- [[Silicio]]: Abundante, económico y estable ante temperaturas
- [[Germanio]]: Sensible al calor y con alta corriente de fuga, pero posee un factor de movilidad excepcionalmente alto para aplicaciones de ultra alta velocidad
- [[Arseniuro de Galio]]: Un compuesto complejo donde los electrónicos se mueven cinco veces más rápido que en el silicio

## Cristal de silicio

En un cristal de silicio puro (Es un trozo de silicio que ha sido purificado de tal forma que todas las impurezas de la estructura cristalina solo queden silicios), los cuatro electrones de valencia de cada átomo se entrelazan con sus vecinos.

- Forman una red rígida y perfecta ([[Enlace covalente]])
- A temperatura ambiente, solo causas externas como calor logran liberar algunos electrones
- A nivel atómico, eso sigue siendo un aislante casi perfecto

## Bandas de energía

Para que la electricidad fluya, un electrón debe saltar de su órbita fija ([[Banda de Valencia]]) a un estado libre ([[Banda de Conducción]]).

La distancia de este salto se conoce como la [[Brecha de Energía]] (Eg) (Indica que tan aislante es un elemento).

- Germanio: 0,67 eV (un salto corto, sensible al entorno)
- Silicio: 1,1 eV (El equilibrio perfecto)
- Arseniuro de Galio: 1,43 eV (Un muro alto que requiere y libera gran cantidad de energía)

## Material intrínseco

Un material intrínseco puro es inútil para la electrónica de precisión.
El verdadero control se logra mediante el [[Dopado]].

## Dopado

**Dopado: Proceso mediante el cual se introducen impurezas controladas en un semiconductor para modificar sus propiedades eléctricas con el objetivo de aumentar la cantidad de portadores de carga y controlar el flujo de corriente eléctrica**

Se inyecta una impureza pentavalente que posee 5 electrones de valencia.

El material sigue siendo eléctricamente neutro, pero ahora está inundado de electrones listos para fluir al menor estímulo.

## Tipos de material

Materiales tipo N y materiales tipo P son semiconductores que fueron modificados artificialmente mediante dopado para que conduzcan electricidad de una forma específica.

**Material tipo N**: Se obtiene cuando se agregan al silicio átomos con más electrones de valencia que el silicio. Los portadores mayoritarios son los electrones y los minoritarios los huecos. Tiene carga dominante negativa. *Lo dopas con algo que lo hace más negativo que neutro*

**Material tipo P:** *Lo dopas con algo que lo hace más positivo que neutro*

==¿Cuándo se hace neutra?==

---
## Diodo

El diodo está formado por una juntura PN (Cuando se junta un material P con un material N).
En la unión, vamos a ver la mezcla de ambos materiales. Se va a formar una región con un poco de positivo y un poco de negativo. Esta zona es la **zona muerta** 

Simbolo de diodo (anodo (+) - catodo (-))

<svg width="200" height="100" xmlns="http://www.w3.org/2000/svg">
  <!-- Línea izquierda (ánodo) -->
  <line x1="0" y1="50" x2="50" y2="50" stroke="currentColor" stroke-width="2"/>
  <!-- Triángulo (cuerpo del diodo) -->
  <polygon points="50,20 50,80 95,50" fill="currentColor"/>
  <!-- Línea vertical (cátodo) -->
  <line x1="95" y1="20" x2="95" y2="80" stroke="currentColor" stroke-width="2"/>
  <!-- Línea derecha (cátodo) -->
  <line x1="95" y1="50" x2="145" y2="50" stroke="currentColor" stroke-width="2"/>

  <!-- Etiquetas ánodo -->
  <text x="22" y="18" text-anchor="middle" font-size="13" fill="currentColor">A</text>
  <text x="22" y="34" text-anchor="middle" font-size="13" fill="currentColor">(+)</text>

  <!-- Etiquetas cátodo -->
  <text x="122" y="18" text-anchor="middle" font-size="13" fill="currentColor">C</text>
  <text x="122" y="34" text-anchor="middle" font-size="13" fill="currentColor">(−)</text>
</svg>

Funciona como una válvula y es unidireccional. El estado de la válvula depende de su polarización. Hay dos tipos de polarización:
- Directa: Llave cerrada. Mayor potencial en el ánodo que en el cátodo. Menor zona muerta
- Inversa: Llave abierta. Menor potencial en el ánodo que en el cátodo. Mayor zona muerta

En un circuito electrónico, nuestro centro de referencia de 0V es la masa (!= tierra)

El led también es un diodo.

El diodo nos permite un montón de cosas.

%%Gráfico de diodo (I-V)%%


