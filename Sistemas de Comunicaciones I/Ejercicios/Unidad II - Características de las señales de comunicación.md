13. Dada una transmisión en banda base de 100 baudios, FRP 33.33 pps y en la cual se utiliza un codificador unipolar positivo de + 10 volts, calcular los valores medio y eficaz de dicha transmisión.

- 100 baudios representa 100 símbolos por segundo.
- FRP = 33,33pps representa la cantidad de pulsos positivos por segundo
- Codificador unipolar positivo de +10V representa que los bits "1" se transmiten con +10V

Si hay 100 símbolos por segundo y 33,33pulsos positivos por segundo:
$$
P(1)= \frac{33.33}{100} \implies P(1)=0.3333
$$
Entonces:
$$
P(0) = 1-P(1) = 1-0.3333 \implies P(0)=0.6667
$$

Para una señal unipolar,  el valor medio se calcula como:
$$
V_{medio}=V\cdot P(1)
$$
Entonces:
$$V_{medio} = 10\cdot0.3333$$
$$V_{medio}=3.33V$$

El valor eficaz se calcula como:

$$V_{ef}=\sqrt{P(1)\cdot V(1)^2 + P(0)\cdot V(0)^2}$$
$$V_{ef}=\sqrt{P(1)\cdot V^2+P(0)\cdot 0^2}$$
$$V_{ef}=\sqrt{0.3333\cdot 10^2}$$
$$V_{ef}=\sqrt{33.33}$$
$$V_{ef}\approx5.77V$$
**Resultado final:**
- Valor medio:
$$\boxed{3.33V}$$
- Valor eficaz:
$$\boxed{5.77V}$$
---
14. Demostrar que un dbm es igual a un dbu cuando la impedancia sobre la cual se mide es de 600 ohms.

Parimos de que $dBm=10\log{(\frac{P}{1mW})}$ y de que $dBu = 20\log{(\frac{V}{0.775})}$.

Sabemos que $P=\frac{V^2}{R} \implies P=\frac{V^2}{600\Omega}$

Por lo tanto:
$$dBm=10\log({\frac{V^2/600\Omega}{1\cdot 10^{-3}mW})}$$
$$dBm=10\log({\frac{V^2}{0.6}})$$
$$dBm =10\log{(\frac{V}{\sqrt{0.6}})^2}$$
[^1]: $\sqrt{0.6}\approx 0.775$
$$dBm=2\cdot 10\log{\frac{V}{0.775}}$$
$$dBm=20\log{\frac{V}{0.775}}=dBu$$
$$\boxed{dBm =dBu\Leftrightarrow R=600\Omega}$$