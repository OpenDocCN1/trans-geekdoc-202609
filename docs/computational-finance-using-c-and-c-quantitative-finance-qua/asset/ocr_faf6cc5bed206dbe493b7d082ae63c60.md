Up and in call: A knockin vanilla call option, value $c_{ui}$, which comes into existence when the asset price reaches or goes above the barrier level.

The following expressions must be true:

```
$c = c_{uo} + c_{ui} \quad (4.5.1)$
$c = c_{do} + c_{di} \quad (4.5.2)$
```

where $c$ is the value of a vanilla call option. We then need only use derive expressions for both the knockout options, and then use the above equations to calculate the value of the corresponding knockout options.

The notation that we will use is as follows: The symbol $t$ represents the current time, $T$ represents the time at which the option matures, and $	au = T - t$, the symbol $s$, with constraint $t \le s \le T$, is any intermediate time during which the option is alive.

# 4.5.2 Analytic pricing of down and out call options

If we consider Brownian motion (with zero drift) $X_s \sim N(0, (s-t)\sigma^2)$, $t \le s \le T$, which starts at $X = 0$, and after time $	au = T - t$, ends at the point $X_s = X$ then (for example, Freedman, 1983) the probability density function for this motion not exceed the value $X = b$ (where $b > 0$) during time $	au$ is given:

> $f(b \ge X_{max}^s, X) = \Omega \sqrt{\frac{2}{\pi}} \exp\left(-\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(-\frac{X^2}{2\sigma^2\tau}\right) \quad (4.5.3)$

where for convenience have used $\Omega = (2b-X)/(\sigma^3\tau^{3/2})$, and $X^{max}=max(X_s, t \le s \le T)$. Since $X_s$ is Brownian motion without drift and volatility $\sigma$, $-X_s$ is identical Brownian motion. Therefore by substituting $X \to -X$, and $b \to -b$ in the equation we obtain

> $f(b \ge X_{min}^s, X) = \Omega \sqrt{\frac{2}{\pi}} \exp\left(-\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(-\frac{X^2}{2\sigma^2\tau}\right) \quad (4.5.4)$

where we have used $X_{min}^s=min(X_s, t \le s \le T)$. Equation (4.5.4) is the probability density function of $-X_s$ staying above the value $X=b$, where $b<0$. These results can be generalized to include drift (Musiela and Rutkowski, 1998, p. 212), by $N((r-q-\\sigma^2/2)(s-t), \sigma(s-t))$, for $t \le s \le T$. We now have the following results:

> $f(b \ge X_{max}^s, X) = \Omega \sqrt{\frac{2}{\pi}} \exp\left(-\frac{2b(X-b)}{\sigma^2\tau}\right)\exp\left(-\frac{(X-(r-q-\\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) \quad (4.5.5)$