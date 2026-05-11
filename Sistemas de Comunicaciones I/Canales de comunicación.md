Se estudian de dos formas:
- **Físico**: Características físicas y eléctricas del medio
	- Atenuación, distorsión, el ruido.
- de **Información**: Especificación técnica y lógica en la transmisión de información.
	- Evaluar y permitir administrar recursos del canal físico de manera adecuada

| Canal Ideal      | Canal Real    |
| ---------------- | ------------- |
| Notación teórica | Notación real |
Relación señal-ruido: $S/N(dB)=10*\log(S/N)$
- Relación entre potencia de la señal y potencia de ruido
- S es la potencia media de la señal, N es la potencia media del ruido

Para los canales de comunicaciones se usa el factor de ruido:
- $F=\frac{S_{in}/N_{in}}{S_{out}/N_{out}}$

**ECO**: Señal no deseada a causa de de la desadaptación de impedacias a lo largo del canal

---
# Teoría de la información
La teoría se basa en la probabilidad de ocurrencia de eventos.

==Un suceso contendrá mayor cantidad de información cuanto menor sea la probabilidad de que se produzca==

Sea S un suceso que se puede presentar con una probabilidad de ocurrencia *P(S)*
$I(S)=log_2{\frac{1}{P(S)}} [Shannon]$
$I(S)=log_10{\frac{1}{P(S)}} [Hartley]$
$I(S)=log_e{\frac{1}{P(S)}} [Nat]$

**Fuente de memoria nula:** Me dice que tengo sucesos independientes.

Cuando los sucesos son equiprobables, la entropía de la fuente es máxima, osea que se entrega el máximo de información. 

$Entropia=H = -\sum_{k=1}^{n}\log_2{P(X_k)}P(X)$ 
$[Entropia]=[H]=Shannon/Simbolo$

Tasa de información ( $\Gamma$ ): *Shannon/segundo*:
$$\Gamma = \frac{H(X)}{\tau}$$
- $\tau$ : duración media de los pulsos, $[\tau]=segundo/simbolo$
---
# Teorema de Nyquist
Determina la cantidad de muestras por unidad de tiempo, o frecuencia de muestreo, que es necesario tomar para que una señal se reconstruya en forma unívoca.

$\boxed{f_n>2f_{max}}$ -> Señal limitada en banda con una $f_{max}$
$\boxed{f_N=2\Delta f}$  -> Señal definida en un ancho de banda $\Delta f$

Un canal de comunicaciones se comporta como un filtro pasabajo. 
$C = V_{tmax}=2\Delta f[bps]$ -> Capacidad de un canal sin ruido $\Delta f$
$C = V_{tmax}^M=2\Delta f\log_2{n} [bps]$ -> HARTLEY. Capacidad de un canal s. multinivel.

---
# Teorema de Shannon-Hartley
Planteo ante canales reales  con ruido aditivo.
Existe límite de incremento de velocidad con los niveles, por la probabilidad de que se puedan distinguir los distintos niveles.
$$C=V_{tmax}^M\log_2({n_{max}})[bps]$$
$$n_{mac}=(1+\frac{S}{N})^{\frac{1}{2}}$$
$$C=2\Delta f\log_2{(1+\frac{S}{N})^{\frac{1}{2}}}[bps]$$
$$\boxed{C=\Delta f\log_2(1+\frac{S}{N}) [bps]}$$







