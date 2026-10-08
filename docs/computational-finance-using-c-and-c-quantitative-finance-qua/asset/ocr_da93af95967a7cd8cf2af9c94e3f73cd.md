# Other financial derivatives

As $\Delta T ightarrow 0, H(t, T+\Delta T) ightarrow h(t, T)$, where $h(t, T)$ is the continuous hazard rate between times $t$ and $T$.

We observe that $\Delta T ightarrow 0$ Eq. (7.4.2) becomes:

```
$h(t, T) = \frac{\partial S(t, T)}{\partial \Delta T} \frac{1}{S(t, T)} \quad (7.4.3)$
```

Now Eq. (7.4.3) can be re-expressed as:

```
$h(t, s) = \frac{\partial S(t, s)}{\partial s} \frac{1}{S(t, s)} = -\frac{\partial \ln(S(t, s))}{\partial s} \quad (7.4.4)$
```

where $s > t$, and we have used:

```
$$\frac{1}{S(t, T)} = \frac{\partial \ln(S(t, T))}{\partial T}$
```

Integrating Eq. (7.4.4) yields:

```
$\int_{s=t}^{T} h(t, s) ds = \int_{s=t}^{T} d\ln(S(t, s)) \n = -{\ln(S(t, T)) - \ln(S(t, t))}\\n = -\ln(S(t, T)) \quad (7.4.5)$
```

where we used $S(t, t) = 1$ and $\ln(S(t, t)) = 0$.
Using Eq. (7.4.5) the survival probability can be expressed as:

```
$S(t, T) = \exp\left\ -\int_{s=t}^{T} h(t, s) ds\right\right\ \quad (7.4.6)$
```

or

```
$S(t, T) = \exp\I(t, T)\} \quad (7.4.7)$
```

where $I(t, T)$ is the cumulative hazard rate from time $t$ to time $T$.
It is usual to approximate $I(t, T)$ as follows:

```
$I(t, T) \sim I(t, t_k) = \sum_{i=1}^{k} h(t_{i-1}, t)(t_i - t_{i-1}) \quad (7.4.8)$
```

where $t_0 = t, t_k = T$, and the following section details on how to estimate $h(t_{i-1}, t)$ from market observables.
One way of representing the hazard rates is to use a *hazard rate curve* which is defined as:

```
${	_i, I(t_i)\}, \ i = 0, \dots, n \quad (7.4.9)$
```

If we define $t_0 = t$ and $t_n = T$, then Eq. (7.4.9) becomes:

```
$\{(0, 0), \{t_1, I(0, t_1)\}, \{t_2, I(0, t_2)\}, \dots, \{t_n, I(0, t_n)\} \quad (7.4.10)$
```

where we have used the fact that $I(t_0, t_0) = I(0, 0) = 0$.