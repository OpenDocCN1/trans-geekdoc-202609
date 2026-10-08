# # Appendix D:

# # Statistical distribution functions

# ## D.1 The normal (Gaussian) distribution

Here we describe some properties of the normal distribution. If $x$ comes from a normal distribution, the associated moment generating function, $M_x(t)$, is given by:

```
$M_x(t) = E[e^{tx}]$$
$= \frac{1}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\infty} exp(tx)exp\left(\frac{(x-\mu)^2}{2\sigma^2}\right)dx$\n$= \frac{1}{\sigma\sqrt{2\pi}} \int_{-\infty}^{\infty} exp\left(-\frac{(x-\mu)^2-2\sigma^2tx}{2\sigma^2}\right)dx$
```

Now completing the square we have:

```
$$\frac{1}{2\sigma^2}\{(x-\mu)^2-2t\sigma^2x\=\frac{1}{2\sigma^2}\{x^2+\mu^2-2\mu x-2t\sigma^2\$\n=-\frac{1}{2\sigma^2}\{(x-\sigma^2t-\mu)^2-2\mu t\sigma^2-\sigma^4t^2\$
$= \mu t+\frac{\sigma^2t^2}{2}-\frac{1}{2\sigma^2}\{(x-\sigma^2t-\mu)^2\$
```

We thus have:

```
$E[e^{tx}] = \frac{1}{\sigma\sqrt{2\pi}}exp\left(\mu t+\frac{\sigma^2t^2}{2}\right)\int_{x=-\infty}^{x=\infty} exp\left(\frac{(x-\sigma^2t-\mu)^2}{2\sigma^2}\right)dx$
```

Now letting $y=x-\sigma^2t-\mu$, $dx=dy$

```
$E[e^{tx}] = \frac{1}{\sigma\sqrt{2\pi}}exp\left(\mu t+\frac{\sigma^2t^2}{2}\right)\int_{y=-\infty}^{y=\infty} exp\left(-\frac{y^2}{2\sigma^2}\right)dy$\n$= \frac{1}{\sigma\sqrt{2\pi}}\sigma\sqrt{2\pi}exp\left(\mu t+\frac{\sigma^2t^2}{2}\right$\n$=exp\left(\mu t+\frac{\sigma^2t^2}{2}\right)$
```