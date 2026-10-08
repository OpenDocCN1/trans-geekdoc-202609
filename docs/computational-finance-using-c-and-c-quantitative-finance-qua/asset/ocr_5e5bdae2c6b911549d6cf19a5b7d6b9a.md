# 90 Computational Finance Using C and C#

or

```
$f(X < B) = \sqrt{rac{2}{\pi}} \exp\left(\frac{X - (r - q - \sigma^2/2)\tau}{2\sigma^2\tau}\right) \\times \int_{b=X}^{log(B/S)} \Omega \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) db \quadquad (4.5.12)$
```

where, in Section 4.5.2, we have used $\Omega = \frac{(2B-X)}{\sigma^3\tau^{3/2}}$ and have integrated over all possible values of $b$ (i.e., $B > b$) to keep the option alive. Recalling that:

```
$$\int_{b=X}^{log(B/S)} \Omega \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) db \\n \int_{b=X}^{log(B/S)} \frac{(2b - X)}{\sigma^3\tau^{3/2}} \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) db \quadquad (4.5.13)$
```

and noting:

```
$-\frac{\partial}{\partial b} \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) = \frac{2(X - 2b)}{\sigma^2\tau} \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) \quadquad (4.5.14)$
```

we have:

```
$$\int_{b=X}^{log(B/S)} \frac{2(B - X)}{\sigma^2\tau} \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right) db \\n - \exp\left(\frac{2b(X - b)}{\sigma^2\tau}\right)_{b=X}^{log(B/S)} \\n = \{\{1 - \exp\left(\frac{2log(B/S)(X - log(B/S))}{\sigma^2\tau}\right) \\}$
```

Therefore:

```
$f(X < B) = \frac{1}{\sigma\sqrt{2\pi}} \exp\left(\frac{X - (r - q - \sigma^2/2)\tau}{2\sigma^2\tau}\right) \\n \times \{\{1 - \exp\left(\frac{2log(B/S)(X - log(B/S))}{\sigma^2\tau}\right) \\}$ \quadquad (4.5.14)$
```

We will now derive the formula for an up and out call option when $E < B$. In fact if $E > B$ then the option is worthless, since at the current time $t$ the call option' payoff, $max(S_t - E, 0) = 0$, and if $S_t > E$ then the option will be knocked out.

```
$c_{uo} = \frac{\exp(-rt)}{\sigma\sqrt{2\pi}} \int_{X=log(E/S)}^{\infty} {S \exp(X) - E\ f(X < B) dX \quadquad (4.5.15)$
```

Taking into account fact the option becomes worthless when $S \exp(X) > B$, (i.e., $X > log(B/S)$): we

```
$c_{uo} = \frac{\exp(-rt)}{\sigma\sqrt{2\pi}} \int_{X=log(E/S)}^{\infty} {S \exp(X) - E\ f(X < B) dX \quadquad (4.5.16)$
```