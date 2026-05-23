1. Determinar que transistor actúa como interruptor principal

En este caso el MOSFET es el componente que actua como interruptor principal de potencia para el motor. Aunque hay otro transistor BJT, la carga principal está conectada en serie con el Drain del MOSFET.

2. Determinar que condiciones encienden y apagan el MOSFET. 

Al ser un MOSFET tipo P, el encendido se activa cuando la tensión en el Gate es significativamente menor que la tensión en el Source ($V_G\approx 0$) y se apaga cuando $V_G$ es igual o muy cercana a $V_S$ ($V_G\approx 9V$).

3. Determinar que valores aproximador deberían tener $V_S$ , $V_G$ , y $V_D$ en estado ON y OFF

$V_S$ : Siempre va a ser 9V, tanto en estado ON como estado OFF.

Para que el MOSFET esté apagado, la diferencia de tensión entre Gate y Source ($V_{GS}$) debe ser cercana a 0.
$$V_{GS} = V_G-V_S$$
$$V_{GS}=V_G-9V=0\Rightarrow V_G=9V$$
Además, como no hay conducción, el terminal Drain queda desconectado de la fuente de alimentación. La única conexión es a través del motor hacia tierra, por lo que $V_D\approx 0V$

Para que el MOSFET esté prendido, la diferencia de tensión entre Source y Gate debe ser máxima, entonces:
$$V_{GS}=V_G-V_S$$
$$V_{GS}=V_G-V_S$$
$$V_{GS}=V_G-9V\Rightarrow V_G=0$$
Al estar el interruptor cerrado, el Drain se conecta eléctricamente al Source. En un MOSFET ideal, $V_D=9V$ pero en la realidad existe una resistencia interna $R_{DS(on)}$ por lo que el valor podría variar un poco.

$V_G$ : Cuando está apagado el motor, $V_G=9V$ y cuando está prendido $V_G=0V$
$V_D$ : Cuando está apagado el motor, $V_D=0V$ y cuando está prendido $V_D=9V$

4. Al utilizar un PMOS como interruptor de "lado alto" (conectado directamente al positivo), el motor recibe prácticamente los 9V totales de la batería cuando el transistor está en ON. El motor alcanza 17,450 RPM. A diferencia de otras configuraciones donde el transistor podría quedarse con parte del voltaje (como en el caso de usar un NMOS en la parte alta), aquí el PMOS se satura por completo porque su Gate (VG) baja hasta 0V mientras su Source (VS) se mantiene en 9V.
5. Determinar qué error podría aparecer si se cambió el MOSFET por otro circuito.

Si, por ejemplo, cambiamos el MOSFET por un BJT, entonces se aumentaría la corriente que le llega al motor, por lo que el motor se quemaría y además, estaríamos ante un riesgo de temperatura/calor producida por la cantidad de corriente que maneja el BJT.