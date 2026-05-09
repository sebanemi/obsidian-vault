# Análisis de Amplificador BJT en Base Común (Explicación Completa)

---

## 🧠 1. Idea Fundamental del Circuito

Un amplificador en configuración de **base común** tiene como objetivo:

> Convertir pequeñas variaciones de corriente en el emisor en grandes variaciones de tensión en el colector.

Este es el concepto más importante de todo el análisis.

### 🔑 Estructura del circuito

- **Base**: fija (tierra en AC)
    
- **Entrada**: por el emisor
    
- **Salida**: por el colector

---

## ⚙️ 2. Rol del Transistor en Base Común

El transistor BJT en esta configuración cumple una función muy específica:

> Transporta la corriente desde el emisor hacia el colector.

Matemáticamente:

$$  
I_C \approx I_E  
$$

Esto significa que cualquier variación en la corriente de emisor se refleja casi directamente en el colector.

---

## 🔥 3. Origen de la Amplificación

El transistor no amplifica por sí solo. La amplificación surge de esta combinación:

- Una **corriente pequeña** que entra por el emisor
    
- Una **resistencia grande** en el colector (( R_C ))

Por ley de Ohm:

$$  
V = I \cdot R  
$$

Entonces:

> Una corriente pequeña atravesando una resistencia grande genera una tensión grande.

### 🧠 Interpretación

El circuito convierte:

- corriente → en tensión
    

---

## 🔬 4. Concepto de Pequeña Señal y ( r_e )

El transistor real tiene una relación exponencial:

$$ 
I_E \sim e^{V_{BE}}  
$$

Pero para señales pequeñas, esta curva se puede aproximar como una recta (linealización).

### 📌 Definición

$$ 
r_e = \frac{26mV}{I_E}  
$$

---

### 🧠 Interpretación física

- ( r_e ) representa la **resistencia interna del emisor**
    
- Mide cuánto cambia la corriente ante pequeños cambios de tensión
    

---

### 🔥 Consecuencia clave

- Si ( I_E ) aumenta → ( r_e ) disminuye
    
- Si ( r_e ) es pequeño → la corriente cambia mucho con poca tensión
    

👉 Esto implica mayor capacidad de amplificación

---

## 🔽 5. Impedancia de Entrada

$$  
Z_i = R_E || r_e  
$$

Dado que:

- ( R_E ) es grande
    
- ( r_e ) es pequeño
    

Entonces:

$$  
Z_i \approx r_e  
$$

---

### 🧠 Interpretación

> El circuito tiene una impedancia de entrada muy baja.

Esto ocurre porque:

- La señal entra por el emisor
    
- El emisor presenta poca oposición al paso de corriente
    

---

### 🔥 Consecuencia

- El circuito “absorbe” corriente fácilmente
    
- Es ideal para señales donde la corriente es importante
    

---

## 🔼 6. Impedancia de Salida

$$  
Z_o \approx R_C  
$$

---

### 🧠 Interpretación

Desde el colector:

- El transistor actúa como una fuente de corriente
    
- La resistencia dominante es ( R_C )
    

---

### 🔥 Consecuencia

> La impedancia de salida es alta

Esto significa que el circuito no entrega fácilmente corriente a cargas externas.

---

## 🔊 7. Ganancia de Tensión

$$  
A_v = \frac{R_C}{r_e}  
$$

---

### 🧠 Derivación conceptual paso a paso

1. Una señal de entrada genera una variación de tensión ( v_e )
    
2. Esto produce una corriente:
    

$$  
i_e = \frac{v_e}{r_e}  
$$

3. Esa corriente pasa al colector:
    

$$ 
i_c \approx i_e  
$$

4. En ( R_C ), se genera una tensión:
    

$$  
v_o = i_c \cdot R_C  
$$

---

### 🔗 Resultado final

$$  
v_o = \frac{v_e}{r_e} \cdot R_C  
$$ $$
A_v = \frac{v_o}{v_e} = \frac{R_C}{r_e}  
$$

---

### 🔥 Interpretación

> La ganancia depende de:
> 
> - cuán fácil es generar corriente ( ( r_e ) )
>     
> - cuánto se transforma en tensión ( ( R_C ) )
>     

---

## 🔁 8. Fase de la Señal

En esta configuración:

> La señal de salida NO está invertida respecto a la entrada.

---

### 🧠 Explicación

- Aumenta la señal en el emisor → aumenta la corriente
    
- Aumenta la corriente en ( R_C ) → cambia la tensión de salida
    

La relación entre entrada y salida mantiene la fase.

---

## ⚠️ 9. Efecto de la Resistencia ( r_o )

El modelo ideal ignora ( r_o ), pero en la práctica existe.

---

### 📌 Nuevo modelo

$$
Z_o = R_C || r_o  
$$

---

### 🧠 Consecuencias

- Disminuye la impedancia de salida
    
- Disminuye la ganancia
    

---

### 🔥 Interpretación

> El transistor deja de ser una fuente de corriente ideal.

---

## 🔌 10. Reglas del Análisis en AC

### 🔹 Fuentes DC → 0

- Fuente de tensión → cortocircuito
    
- Fuente de corriente → circuito abierto
    

---

### 🧠 Justificación

> Se analizan solo variaciones, no valores constantes.

---

### 🔹 Capacitores → cortocircuito

Porque:

$$  
X_C = \frac{1}{\omega C}  
$$

- A frecuencias medias/altas → ( $X_C \approx 0$ )
    

---

### 🧠 Interpretación

> El capacitor deja pasar la señal AC como si fuera un cable.

---

## 🎯 11. Relación entre Análisis DC y AC

### 🔹 DC

- Define el punto de operación (Q)
    
- Determina ( I_E ), ( V_{CE} )
    

---

### 🔹 AC

- Analiza variaciones alrededor de Q
    
- Usa el modelo lineal (pequeña señal)
    

---

### 🧠 Idea clave

> Sin un buen análisis en DC, el análisis en AC no tiene sentido.

---

## 🧠 12. Conclusión Conceptual Final

El amplificador en base común funciona mediante:

- Un transistor que transporta corriente del emisor al colector
    
- Una resistencia de colector que convierte esa corriente en tensión
    
- Un modelo de pequeña señal que permite analizar el circuito como si fuera lineal
    

---

### 💬 Forma ideal de explicarlo oralmente

> El circuito amplifica señales convirtiendo pequeñas variaciones de corriente en el emisor en grandes variaciones de tensión en el colector. Esto se logra gracias a la resistencia de colector, mientras que el comportamiento del transistor se modela mediante su resistencia dinámica ( r_e ), la cual depende del punto de operación definido en el análisis en DC.

---

## 🧾 Justificación de todo el enfoque

Todo lo explicado se basa en:

- Ley de Ohm
    
- Modelo exponencial del transistor
    
- Aproximación lineal (pequeña señal)
    
- Análisis de circuitos clásicos
    

No hay fórmulas aisladas:  
cada una surge de un modelo físico y tiene interpretación concreta.

---