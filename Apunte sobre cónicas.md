Una cónica es una curva que se obtiene al cortar un cono con un plano. Según como se corte ese cono aparecen distintos entes geométricos. Es como hacer una **sección** en dibujo técnico.

Los distintos entes geométricos son:
- Circunferencia
- Elipse
- Hipérbola
- Parábola

Cada uno de estos tiene una ecuación característica, elementos notables, propiedades y una forma típica.

---
# Circunferencia

Es el conjunto de todos los puntos que están a la misma distancia de un punto fijo llamado centro. La ecuación de la circunferencia está dada de la forma:
$$(x-x_0)^2+(y-y_0)^2=r^2$$
Elementos notables:
- Centro: $C=(x_0,y_0)$
- Radio: $r$

Para identificarla basta con ver que los cuadrados tienen el mismo coeficiente, ambos son positivos y no aparece uno restando.

Ejemplo 1: 
$$(x-2)^2+(y+1)^2=16$$
Es una circunferencia con centro $(2,-1)$ y radio $r=4$

Ejemplo 2:
$$x^2+y^2-4x+6y-12=0$$
Es la ecuación de una circunferencia de forma desarrollada, por lo que para llevarla a canónica hay que completar cuadrados.

# Intersección con una recta

Supongamos que tenemos una recta $y=ax+b$ y una circunferencia de ecuación $x^2+Ax+y^2+By+F=0$. Lo que tenemos que hacer es lo siguiente:

- Reemplazo el valor de $y$ en la ecuación de la circunferencia con el de la recta
$$x^2+Ax+(ax+b)^2+B(ax+b)+F=0$$
- Desarrollo las ecuaciones:
$$x^2+Ax+(ax)^2+2ax+b^2+Bax+Bb+F=0$$
$$x^2+Ax+a^2x^2+2ax+b^2+Bax+Bb+F=0$$
- Reordeno los términos:
$$x^2+a^2x^2+Ax+2ax+Bax+Bb+F=0$$
$$(1+a^2)x^2+(A+2a+Ba)x+(Bb+F)=0$$
> [!NOTE] Concepto de discriminante
> Ahora tenemos que recordar un concepto visto en el **modulo cero**: El discriminante ($\Delta=b^2-4ac$ )
> - Si $\Delta>0$ entonces, la ecuación tiene exactamente dos soluciones
> - Si $\Delta=0$ entonces, la ecuación tiene exactamente una solución
> - Si $\Delta<0$ entonces, la ecuación no tiene solución en los reales

- Aplicando estos conceptos, entonces:
$$b^2-4ac=(A+2a+Ba)^2-4(1+a^2)(Bb+F)$$
Como dijimos antes, el discriminante determina cuantas soluciones tiene la ecuación. Sin embargo, falta determinar que significan esas soluciones.

- Si $\Delta>0$ entonces, la recta corta a la circunferencia exactamente en dos puntos **siempre** (secante).
- Si $\Delta=0$ entonces, la recta toca a la circunferencia exactamente en un punto (tangente).
- Si $\Delta=0$ entonces, la recta no toca a la circunferencia en ningún punto (exterior).

---
# Elipses

La suma de las distancias desde cualquier punto de la elipse hasta dos puntos fijos llamados focos es constante. La ecuación canónica de la elipse está dada de la forma:

$$\frac{(x-x_0)^2}{a^2}+\frac{(y-y_0)^2}{b^2}=1$$
- Si $a>b$ entonces el semieje mayor de la elipse va a ser el eje x (elipse horizontal)
- Si $a<b$ entonces el semieje mayor de la elipse va a ser el eje y (elipse vertical)

Elementos notables:
- Centro: $C=(x_0,y_0)$
- Semieje mayor: $a$ o $b$ dependiendo de como se desarrolle la elipse
- Relación fundamental: $c^2=a^2-b^2$
- Focos: $F_{1,2}=(x_0\pm c,y_0)$ si $a>b$, $F_{1,2}=(x_0,y_0\pm c)$ si $a<b$
- Vértices: $V_{1,2}=(x_0\pm a, y_0)$ si $a>b$, $V_{1,2}=(x_0,y_0\pm a)$ si $a<b$

Ejemplo:
$$\frac{x^2}{9}+\frac{y^2}{16}=1$$
# Intersección con una recta

Es lo mismo que hacerlo con una circunferencia dado que una circunferencia es un caso particular de una elipse, entonces como ya está el desarrollo arriba no lo voy a hacer devuelta.

---
# Hipérbolas