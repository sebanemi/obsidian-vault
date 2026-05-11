Ecuación de error de campo magnético B:
$$B=0,775\cdot \mu_0\cdot\frac{n}{R}\cdot I$$
Donde asumimos que:
- 0,775 es una constate
- $\mu_0$ es la permeabilidad del vacío (constante)
- n es la cantidad de espiras en la bobina (constante)
- *I*(corriente) y *R*(radio) son las variables con incertidumbre $\Delta I$ y $\Delta R$

$$\Delta B=\sqrt{(\frac{\partial B}{\partial I}\cdot\Delta I)^2+(\frac{\partial B}{\partial R}\cdot\Delta R)^2}$$
Cálculos de derivadas parciales:
$$\frac{\partial B}{\partial I} = 0,775\cdot\mu_0\cdot\frac{n}{R}$$
$$\frac{\partial B}{\partial R}=-0,775\cdot\mu_0\cdot n\cdot I\cdot\frac{1}{R^2}$$
Lo que resulta en:

$$\Delta B=\sqrt{(0,775\cdot\mu_0\cdot\frac{n}{R}\cdot\Delta I)^2+(-0,775\cdot\mu_0\cdot\frac{n\cdot I}{R^2}\cdot\Delta R)^2}$$
