Substituting these results into equation (5.2.10) yields the following transformed Black–Scholes equation:

```
$$S^2\sigma^2h\frac{\partial^2g}{\partial^2} + (r-q)Sh\frac{\partial g}{\partial} + rg(h-1) + rh(h-1)\frac{\partial g}{\partial} = rgh, \quad (5.2.11)$
```

which can be further substituted into

```
$$S^2\sigma^2\frac{\partial^2g}{\partial S^2} + \frac{2(r-q)}{\sigma^2}\frac{\partial g}{\partial S} - \frac{2rg}{h\^2} - \frac{2r(1-h)}{\sigma^2}\frac{\partial g}{\partial h} = rgh, \quad (5.2.12)$
```

or

```
$$S^2\frac{\partial^2g}{\partial S^2} + \beta S\frac{\partial g}{\partial S} - \frac{\alpha}{h}(h-1)\frac{\partial g}{\partial h} = 0, \quad (5.2.13)$
```

where $\alpha = \frac{2r}{\sigma^2}$ and $\beta = \frac{2(r-q)}{\sigma}$

We consider the last term of equation (5.2.13) and note that when $	au$ is large, $-h(\tau) \sim 0$. Also when $\tau \to 0$, the option is close to maturity, and the value $\nu(S,E,\tau) \sim 0$ and $\frac{\partial}{\partial h} \sim 0$. It can be seen that the last term is generally quite small, and the Macmillan, Barone-Adesi, and Whaley approximation assumes it can be ignored.

```
$$S^2\frac{\partial^2g}{\partial S^2} + \beta S\frac{\partial g}{\partial S} - \frac{\alpha}{h} = 0, \quad (5.2.14)$
```

which is a second order differential equation with two linearly independent solutions of the form $aS^\gamma$. They can be found by substituting $g(S,E,h) = aS^\gamma$ into equation (5.2.14) as follows:

```
$$\frac{\partial g}{\partial S} = \gamma aS^{\gamma-1}, \frac{\partial^2g}{\partial S^2} = \gamma(\gamma-1)aS^{\gamma-2} - \gamma^2 aS^{\gamma-2}$
```

so

```
$$S^2\frac{\partial^2g}{\partial S^2} = \gamma^2 aS^{\gamma} - \gamma aS^{\gamma} = (\gamma^2 - \gamma) aS^{\gamma}$
```

and

```
$$\beta S\frac{\partial g}{\partial S} = \beta S aS^{\gamma-1} = \beta \gamma aS^{\gamma} = \beta \gamma g.$
```

When the above results are substituted in equation (5.2.14), we obtain the quadratic equation

```
$$\gamma^2 g - \gamma g + \beta \gamma g - \alpha/h = g(\gamma^2 - \gamma + (\beta - 1)\gamma - \alpha/h) = 0$$
```

or

```
$$\gamma - \gamma + (\beta - 1)\gamma - \alpha/h = 0, \quad (5.2.15)$
```