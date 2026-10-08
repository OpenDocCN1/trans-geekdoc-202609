Current time will be denoted by $t_0$, and the option maturity time by $T$. The money market account has value $B_{t_0}=1$ at time $t_0$ and $B_T = \exp(r(T - t_0))$ at time $T$.

We will now consider the process by the relative value $\phi(S_t, B_t) = S_t/B_t$.

Using the Ito quotient rule as described in Section 2.6.2 and substituting $X_1 = S_t$ and $X_2 = B_t$ in Eq. (2.6.8) we have:

```
$d\left(\frac{S_t}{B_t}ight) = \left(\frac{S_t}{B_t}ight)(\mu - r)dt + \left(\frac{S_t}{B_t}ight)\sigma dW^P$
```

So finally we can write

```
$dS_t^* = S_t^*(\mu - r)dt + S_t^*\sigma dW^P$ (4.4.27)
```

where $S_t^* = S_t/B_t$. Referring toirsanov's theorem in Section 2.4, we can choose a probability measure $Q$

```
$dW^P = dW^Q - \left(\frac{\mu - r}{\sigma}ight)dt$ (4.4.28)
```

In Eq. (2.4.3) we thus have $k(t) = -((\mu - r)/\sigma)$ and

```
$\frac{dQ}{dP} = \exp\left\{-\left(\frac{\mu - r}{\sigma}ight)W^P - \frac{1}{2}\left(\frac{\mu - r}{\sigma}ight)^2 tight\}$ (4.4.29)
```

See p. 114 of Musiela (1998). Substituting for $dW^P$ in Eq. (4.4.27) yields

```
$dS_t^* = S_t^*(\mu - r)dt + S_t^*\sigma\left(\frac{\mu - r}{\sigma}ight)dW^Q$
```

which simplifies to

```
$dS_t^* = S_t^*\sigma dW^Q$ (4.4.30)
```

Equation (4.4.30) means that the process for $S_t^*$ is a martingale under probability $Q$.

Replacing $dW^P$ in (4.4.26) with the value in Eq. (4.4.28) yields

```
$dS_t = \mu_t S_t dt + S_t\sigma dW^P$
$= \mu_t S_t dt + S_t\sigma\left\{dW^Q - \left(\frac{\mu - r}{\sigma}ight)dtight\}$
$= \left\{S_t\mu_t dt - S_t\sigma\left(\frac{\mu - r}{\sigma}ight)dtight\} + S_t\sigma dW^Q$
```

So in the risk neutral measure $Q$ the dynamics of $S_t$ are

```
$dS_t = r_t dt + S_t\sigma dW^Q$ (4.4.31)
```

Comparing Eq. (4.4.31) with the original Eq. (4.4.26) we see that changing from the real-world measure to the risk neutral measure simply involves substituting $dW^P$ for $dW^Q$ and $r$ for $\mu$.