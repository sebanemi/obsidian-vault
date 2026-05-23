# INFORME TÉCNICO: DISEÑO E IMPLEMENTACIÓN DE COMPUERTA LÓGICA XOR

**Asignatura:** Electrónica / Técnicas Digitales

**Desafío N°:** 4

**Integrantes:** Nemi Scarano Sebastián Andrés

**Fecha:** 19 de mayo de 2026

---
## 1. Introducción y Objetivo

<div style="text-align: justify;">

El presente informe detalla el diseño, simulación e implementación de una compuerta lógica XOR (OR Exclusiva) de dos entradas utilizando tecnologías de estado sólido basadas en transistores MOSFET y etapas de acoplamiento bipolares (BJT). El objetivo principal del desafío consiste en validar el comportamiento lógico de la compuerta y analizar su respuesta frente a las diferentes combinaciones de tensión en sus terminales de entrada.

</div>

---

## 2. Plataforma Utilizada

<div style="text-align: justify;">

Para el desarrollo, simulación y análisis del circuito se utilizó la herramienta de simulación interactiva Falstad. Esta plataforma permite evaluar en tiempo real los niveles de tensión (nodos en verde para alta impedancia/tensión y gris para niveles bajos) y la conducción de corriente a través de los componentes semiconductores.

</div>

---

## 3. Tabla de Verdad teórica de la compuerta XOR

<div style="text-align: justify;">

La compuerta XOR entrega un nivel lógico alto (1 o H) únicamente cuando sus entradas presentan estados lógicos opuestos entre sí.

</div>

| **Entrada A** | **Entrada B** | **Salida Y (Esperada)** |
| ------------- | ------------- | ----------------------- |
| 0 (L)         | 0 (L)         | **0 (L)**               |
| 0 (L)         | 1 (H)         | **1 (H)**               |
| 1 (H)         | 0 (L)         | **1 (H)**               |
| 1 (H)         | 1 (H)         | **0 (L)**               |

---

## 4. Explicación Técnica del Circuito

<div style="text-align: justify;">

La implementación de la compuerta lógica XOR realizada se compone de una estructura híbrida que optimiza el uso de distintas tecnologías de semiconductores (CMOS, Lógica de Diodos y BJT) para resolver la función lógica fundamental:

</div>

$$XOR=(A\cdot\overline{B})+(\overline{A}\cdot B)$$
<div style="text-align: justify;">

A continuación, se detalla analíticamente el desarrollo y la interconexión de los tres componentes principales que integran el circuito:

</div>

<p align="center">
  <img src="Pasted image 20260519100624.png" width="349">
</p>

- **Compuertas NOT (Inversores CMOS):** El circuito dispone de dos inversores independientes, encargados de negar las señales de entrada principales. Cada inversor está desarrollado mediante el uso de dos transistores MOSFET complementarios: un canal P en la parte superior (fuente conectada a $+5\text{V}$) y un canal N en la parte inferior (fuente conectada a tierra). Las compuertas (gates) de ambos integran un nodo común que recibe la señal de entrada, mientras que la unión de sus drenajes conforma la salida invertida. Esta configuración minimiza drásticamente el consumo de potencia estática.

- **Compuertas AND (Lógica de Diodos - DL):** Se implementan dos etapas lógicas AND basadas en diodos y resistencias de pull-up de $1\text{ k}\Omega$ acopladas a la línea de alimentación de $+5\text{V}$. Los diodos se encuentran posicionados en contrafase respecto a las señales que controlan. Cada una de estas etapas se encarga de realizar el producto lógico entre una de las entradas directas y la señal complementaria proveniente del inversor CMOS opuesto (generando los términos lógicos $\text{A} \cdot \overline{\text{B}}$ y $\overline{\text{A}} \cdot \text{B}$ respectivamente).

- **Compuerta OR (Configuración de Seguidores de Emisor en Paralelo):** Para realizar la suma lógica final de las ramas anteriores sin sufrir la degradación de niveles de tensión que provocaría una compuerta tradicional de diodos, se optó por una etapa activa utilizando transistores de unión bipolar (BJT) de tipo NPN. Las salidas de las etapas AND se conectan a las bases de los BJT mediante resistencias limitadoras de $10\text{ k}\Omega$. Ambos transistores se encuentran dispuestos con sus colectores conectados directamente a $+5\text{V}$ y sus emisores unidos en paralelo hacia un nodo común de salida, referenciado a tierra a través de una resistencia de pull-down de $47\text{ k}\Omega$. Esta topología de "seguidores de emisor en paralelo" actúa como un búfer de corriente, asegurando que cuando cualquiera de los BJT entre en conducción, la salida refleje un nivel lógico alto estable, mitigando las caídas de tensión intrínsecas del circuito previo.

---

## 5. Evidencia de Funcionamiento

- **Caso A=0, B=0:** Los transistores de salida permanecen en corte debido a la falta de polarización en sus bases. La salida se mantiene firmemente en $0\text{ V}$ ($L$).

<p align="center">
  <img src="Pasted image 20260519100358.png" width="349">
</p>

- **Caso A=1, B=0:** _(Es la captura de pantalla provista)_ Al estar una entrada en alto y la otra en bajo, las ramas de diodos conducen de tal forma que inyectan corriente en la base de la etapa BJT activa. Se observa el camino verde ($+5\text{ V}$) polarizando la salida a un estado alto ($H$). El nivel en el pin de salida efectivamente responde a la condición lógica esperada.

<p align="center">
  <img src="Pasted image 20260519100442.png" width="349">
</p>

- **Caso A=0, B=1:** Condición simétrica a la anterior. El segundo bloque activa el transistor BJT correspondiente, manteniendo la salida en nivel alto.

<p align="center">
  <img src="Pasted image 20260519100500.png" width="349">
</p>

- **Caso A=1, B=1:** Ambas señales en alto provocan la conmutación de la lógica de diodos bloqueando la corriente hacia las bases de los BJTs. Ambos transistores van al corte y la salida cae a $0\text{ V}$ ($L$).

<p align="center">
  <img src="Pasted image 20260519100520.png" width="349">
</p>

---
## 6. Conclusión

<div style="text-align: justify;">

El circuito diseñado cumple de manera óptima con los requisitos de la compuerta XOR del Desafío 4. La utilización de MOSFETs permitió un control eficiente por tensión en las etapas intermedias, mientras que los BJTs en la etapa final garantizaron una conmutación limpia y definida para la señal de salida. La simulación valida el diseño teórico y demuestra la factibilidad de la implementación práctica de lógica digital con componentes discretos.

</div>
