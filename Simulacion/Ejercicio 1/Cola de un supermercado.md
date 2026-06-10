Imaginá una caja de supermercado con un solo cajero. Los clientes van llegando de a uno, en momentos aleatorios. Si el cajero está libre, el cliente es atendido de inmediato. Si está ocupado, el cliente se pone en la cola y espera su turno.

Querés responder una pregunta concreta: ¿cuánto tiempo espera un cliente en promedio antes de ser atendido?

---
# Datos

- Tiempo medio de llega de clientes: 3 min
- Tiempo de atención uniforme: 2 a 5 min
- Longitud temporal de la simulación: 480 min (8 horas)

---
# Objetivo

Calcular y mostrar el tiempo promedio de espera y la cantidad de clientes atendidos en ese intervalo de tiempo.

---
Distribución exponencial:
$$f(x)=\lambda e^{-\lambda x}$$
Para este caso, $\lambda=1/3$, pero también hay que sumar el tiempo uniforme que tardan en la atención. Para simplificar las cosas, tomaremos que esto es un número aleatorio entre 2 y 5 (minutos).

---

```
import simpy, random

def cliente(env, cajero, tiempo_espera, cantidad):

    llegada = env.now

    print(f'Cliente llega a las {llegada:.2f}')

    cantidad[0] += 1  # Incrementar la cantidad de clientes atendidos

    with cajero.request() as request:

        yield request

        tiempo_espera.append(env.now - llegada)

        yield env.timeout(random.uniform(2, 5))  # Tiempo de servicio entre 2 y 5 minutos

def generar_clientes(env, cajero, tiempo_espera,cantidad):

    while True:

        yield env.timeout(random.expovariate(1/3))  # Llegada de clientes cada 3 minutos en promedio

        env.process(cliente(env, cajero, tiempo_espera, cantidad))

env = simpy.Environment()

cajero = simpy.Resource(env, capacity=1)  # Un solo cajero

tiempos = []

cantidad = [0]  # Lista para almacenar la cantidad de clientes atendidos

env.process(generar_clientes(env, cajero, tiempos, cantidad))

env.run(until=480)  # Simular por 480 minutos


print("El tiempo promedio de espera es:", f"{sum(tiempos)/len(tiempos):.2f}" if tiempos else 0)

print("Cantidad total de clientes atendidos:", cantidad[0])
```

