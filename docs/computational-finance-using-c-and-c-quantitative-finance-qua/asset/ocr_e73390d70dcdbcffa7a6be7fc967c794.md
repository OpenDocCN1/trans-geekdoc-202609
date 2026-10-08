We will now consider the situation when $\epsilon_t$ either jumps up or down by an amount $
u = \sigma\sqrt{\Delta t}$. For an up jump:

```
$\log\left(\frac{S_{t+\Delta t}}{S_t}ight) = \sigma\sqrt{\Delta t}$
```

and therefore $S_{t+\Delta t} = S_t \exp(\sigma\sqrt{\Delta t})$.
While a down jump we have

```
$\log\left(\frac{S_{t+\Delta t}}{S_t}ight) = -\sigma\sqrt{\Delta t}$
```

and therefore $S_{t+\Delta t} = S_t \exp(-\sigma\sqrt{\Delta t})$.
The reader will notice that these expressions are the same as those for the CCR rate of Chapter 5. For an up jump $S_{t+\Delta t} = S_t u$, for a down jump $S_{t+\Delta t} = S_t d$, and $u = 1/d = \exp(\sigma\sqrt{\Delta t})$.
The probability of undergoing either an up or down jump can be found by matching the mean and variance of $\epsilon_t$.
From the:

```
$E[\epsilon_t] = 
u(p_u - p_d) = \mu\Delta t$ (6.4.1)
```

and the variance:

```
$Var[\epsilon_t] = 
u^2(p_u + p_d) = \sigma^2\Delta t$ (6.4.2)
```

So combining Eqs. (6.4.1) and (6.4.2) we obtain:
$\mu\Delta t + \sigma^2\Delta t = 2
u^2p_u$

so

```
$p_u = \frac{1}{2}\left(\frac{\sigma^2\Delta t}{
u^2} + \frac{\mu\Delta t}{
u}ight)$
```

Substituting $
u = \sigma\sqrt{\Delta t}$ we obtain:

```
$p_u = \frac{1}{2}\left(1 + \frac{\mu\sqrt{\Delta t}}{\sigma}ight)$ (6.4.3)
```

and using the fact that $p_d = 1 - p_u$ gives:

```
$p_d = \frac{1}{2}\left(1 - \frac{\mu\sqrt{\Delta t}}{\sigma}ight)$ (6.4.4)
```

We shall now show that this is equivalent to the Cox-Rubinstein–Ross binomial model.
For the CRR model (Chapter 5, Eq. (5.3.19)) we have:

```
$p_u = \frac{\exp(r\Delta t) - d}{u - d}$
```

expanding $\exp(r\Delta t)$, $u$ and $d$ to order $\Delta t$ we obtain: