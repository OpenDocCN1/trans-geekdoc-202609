# Ito's Formula (or Lemma) Section | 2.3 11

In particular, if we consider the geometric Brownian process

```
$$dS = \mu S dt + \sigma S dW_t$$
```

where $\mu$ and $\sigma$ are constants then substituting $X = S, a = \mu S,$ and $b = \sigma S$ into equation (2.3.5) yields

```
$$df = \frac{\partial \phi}{\partial t} + \mu S \frac{\partial \phi}{\partial S} + \frac{\sigma^2 S^2}{2} \frac{\partial^2 \phi}{\partial S^2}} dt + \sigma S \frac{\partial \phi}{\partial S} dW_t. \quad (2.3.6)$
```

(2.3,6) describes the change of a function $\phi(S,t)$ over the time interval $dt$, when the stochastic variable $S$ follows GBM. The result has very important applications in the pricing of financial derivatives. Here, the function $\phi(S,t)$ is taken as the price of a financial derivative, $f(S,t)$, that depends on the value of an underlying asset $S$, which is assumed to follow GBM. In Chapter 4, we will use equation (2.3.6) to derive the (Black–Scholes) partial differential equation that is satisfied by the price of a financial derivative. We have

We also use equation (2.3.3) to derive the process by $\phi = \log(S)$.

```
$$\frac{\partial \phi}{\partial S_t} = \frac{\partial \log(S_t)}{\partial S_t} - \frac{\sigma^2}{S_t^2} \frac{\partial \log(S_t)}{\partial S_t} = \frac{\partial \log(S_t)}{\partial S_t} - \frac{\sigma^2}{S_t^2}.$$
```

```
$$\frac{\partial \phi}{\partial t} = \frac{\partial \log(S_t)}{\partial t} = 0.$$
```

So,

```
$$d(\log(S_t)) = vdt + \sigma dW_t, \quad \text{where } v = \mu - \frac{\sigma^2}{2}. \quad (2.3.7)$
```

Integrating (2.3.7) yields

```
$$\int_{t=0}^T d(\log(S_t)) = \int_{t=0}^T vdt + \int_{t=0}^T \sigma dW_t,$$
```

so

```
$$\log(S_T) - \log(S_0) = vT + \sigma W_T. \quad (2.3.8)$
```

where we used $t_0 = 0$ and $W_0 = 0$.

We obtain

```
$$\log(\frac{S_T}{S_0}) \sim N(vT, \sigma^2T). \quad (2.3.9)$
```

and so

```
$$\log(\frac{S_T}{S_0}) = vT + \sigma W_T. \quad (2.3.10)$
```

The solution to the GBM in equation (2.2.3) is

```
$$S_T = S_0 \exp(vT + \sigma W_T), \quad \nu = \mu - \frac{\sigma^2}{2}. \quad (2.3.11)$
```

The asset value at time $t + dt$ can therefore be generated from its value at time

```
$$S_{t+dt} = S_t \exp{vdt + \sigma dW_t\$$
```