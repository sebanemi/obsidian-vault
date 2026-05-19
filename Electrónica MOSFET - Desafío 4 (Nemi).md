# INFORME TÉCNICO: DISEÑO E IMPLEMENTACIÓN DE COMPUERTA LÓGICA XOR

**Asignatura:** Electrónica / Técnicas Digitales

**Desafío N°:** 4

**Integrantes:** Nemi Scarano Sebastián Andrés

**Fecha:** 19 de mayo de 2026

---

## 1. Introducción y Objetivo

El presente informe detalla el diseño, simulación e implementación de una compuerta lógica XOR (OR Exclusiva) de dos entradas utilizando tecnologías de estado sólido basadas en transistores MOSFET y etapas de acoplamiento bipolares (BJT). El objetivo principal del desafío consiste en validar el comportamiento lógico de la compuerta y analizar su respuesta frente a las diferentes combinaciones de tensión en sus terminales de entrada.

---

## 2. Plataforma Utilizada

Para el desarrollo, simulación y análisis del circuito se utilizó la herramienta de simulación circuital interactiva Falstad SPICE. Esta plataforma permite evaluar en tiempo real los niveles de tensión (nodos en verde para alta impedancia/tensión y gris para niveles bajos) y la conducción de corriente a través de los componentes semiconductores.

---

## 3. Tabla de Verdad teórica de la compuerta XOR

La compuerta XOR entrega un nivel lógico alto ($1$ o $H$) únicamente cuando sus entradas presentan estados lógicos opuestos entre sí.

|**Entrada A**|**Entrada B**|**Salida Y (Esperada)**|
|---|---|---|
|0 (L)|0 (L)|**0 (L)**|
|0 (L)|1 (H)|**1 (H)**|
|1 (H)|0 (L)|**1 (H)**|
|1 (H)|1 (H)|**0 (L)**|

---

## 4. Explicación Técnica del Circuito

![[Pasted image 20260519100624.png|349]]

El diseño implementado destaca por ser una arquitectura híbrida que optimiza el uso de componentes para lograr la función lógica XOR mediante la combinación de subetapas:

### A. Bloques Complementarios con MOSFETs (Inversores / Conmutadores)

El circuito cuenta con dos bloques idénticos compuestos por pares de MOSFETs de canal P (superior) y canal N (inferior) conectados en una configuración similar a un inversor CMOS tradicional.

- Cuando la entrada conectada a sus compuertas (_Gates_) está en alto ($+5\text{ V}$), el MOSFET de canal N conduce, poniendo el nodo de drenador a masa ($0\text{ V}$).
    
- Cuando la entrada está en bajo ($0\text{ V}$), el MOSFET de canal P se activa, vinculando el nodo a la línea de alimentación de $+5\text{ V}$.

### B. Red de Lógica de Diodos (DTL)

A la salida de estos bloques de transistores se acopla una red de diodos que realiza la función de interconexión lógica. Los diodos actúan bloqueando o permitiendo el paso de corriente hacia las bases de los transistores de salida según la combinación de las entradas directas ($H$ / $L$) y los estados invertidos por los MOSFETs. Esto evita cortocircuitos entre las ramas y asegura que las corrientes fluyan en un solo sentido.

### C. Etapa de Salida y Buffer con Transistores BJT

Para asegurar la correcta definición de los niveles lógicos de salida y otorgar capacidad de carga (_Fan-out_), se utilizaron dos transistores bipolares (BJT) NPN configurados en paralelo hacia el nodo de salida común ($L$), junto con una resistencia de pulso a tierra (_Pull-down_) de $47\text{ k}\Omega$.

- **Conmutación:** Si alguna de las ramas de diodos permite el paso de corriente hacia la base de uno de los BJTs (a través de las resistencias de base de $10\text{ k}\Omega$), dicho transistor entra en saturación, elevando el potencial del emisor hacia los $+5\text{ V}$ (Salida en $H$).
    
- **Estado de Reposo:** Si ambos transistores se encuentran en corte, la resistencia de $47\text{ k}\Omega$ asegura que el nodo de salida se descargue por completo a potencial de tierra (Salida en $L$).

---

## 5. Evidencia de Funcionamiento

- **Caso A=0, B=0:** Los transistores de salida permanecen en corte debido a la falta de polarización en sus bases. La salida se mantiene firmemente en $0\text{ V}$ ($L$).

![[Pasted image 20260519100358.png|381]]

- **Caso A=1, B=0:** _(Es la captura de pantalla provista)_ Al estar una entrada en alto y la otra en bajo, las ramas de diodos conducen de tal forma que inyectan corriente en la base de la etapa BJT activa. Se observa el camino verde ($+5\text{ V}$) polarizando la salida a un estado alto ($H$). El nivel en el pin de salida efectivamente responde a la condición lógica esperada.

![[Pasted image 20260519100442.png|379]]

- **Caso A=0, B=1:** Condición simétrica a la anterior. El segundo bloque activa el transistor BJT correspondiente, manteniendo la salida en nivel alto.

![[Pasted image 20260519100500.png|381]]

- **Caso A=1, B=1:** Ambas señales en alto provocan la conmutación de la lógica de diodos bloqueando la corriente hacia las bases de los BJTs. Ambos transistores van al corte y la salida cae a $0\text{ V}$ ($L$).

![[Pasted image 20260519100520.png|375]]

---
## 6. Conclusión

El circuito diseñado cumple de manera óptima con los requisitos de la compuerta XOR del Desafío 4. La utilización de MOSFETs permitió un control eficiente por tensión en las etapas intermedias, mientras que los BJTs en la etapa final garantizaron una conmutación limpia y definida para la señal de salida. La simulación valida el diseño teórico y demuestra la factibilidad de la implementación práctica de lógica digital con componentes discretos.

