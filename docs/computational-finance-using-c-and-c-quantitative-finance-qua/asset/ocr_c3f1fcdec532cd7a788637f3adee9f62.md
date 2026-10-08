# 104 Computational Finance Using C and C#

where as usual S is the set price, r is the continuously compounded interest rate, q is the continuously compounded dividend, $\sigma$ is the volatility, and time t increases from the time to the expiry T.

We will now introduce the variable $h(t) = 1 - \exp(-r t)$ and use the factorization $v(S, E, 	au) = h(t)g(S, E, h)$. From standard calculus we obtain:

```
$\frac{\partial v}{\partial t} = g\frac{\partial h}{\partial t} + h\frac{\partial g}{\partial t} = rg(h-1) + h\frac{\partial^2 g}{\partial h}\frac{\partial h}{\partial t} = rg(h-1) + lr(h-1)\frac{\partial g}{\partial h}$
```

and also

```
$\frac{\partial v}{\partial S} = h\frac{\partial g}{\partial S}$ and $\frac{\partial^2 v}{\partial S^2} = h\frac{\partial^2 g}{\partial S^2}$
```

Substituting these results into Eq. (5.20) yields the transformed Black-Scholes equation:

```
$S^2\frac{\partial^2 g}{\partial S^2} + (r-q)Sh\frac{\partial g}{\partial S} + rg(h-1) + rh(h-1)\frac{\partial g}{\partial h} = rgh$ (5.2.11)
```

which can be further simplified to give:

```
$S^2\frac{\partial^2 g}{\partial S^2} + \frac{2(r-q)S}{\sigma^2}\frac{\partial g}{\partial S} - \frac{2rg}{h\sigma^2} - \frac{2r(1-h)}{\sigma^2}\frac{\partial g}{\partial h} = rgh$ (5.2.12)
```

or

```
$S^2\frac{\partial^2 g}{\partial S^2} + \beta S\frac{\partial g}{\partial S} - \frac{\alpha}{h}\frac{\partial g}{\partial h} - g - (1-h)\frac{\alpha}{\partial h} = 0$ (5.2.13)
```

where $\alpha = 2r/\sigma^2$ and $eta = 2(r-q)/\sigma^2$.

We now consider the last term of Eq. (5.2.13) and note that when $	au$ is large, $1-h(t) \sim 0$. Also when $	au \to 0$ the option is close to maturity, and the value of both European and American options converge, this means that $v(S, E, \tau) \sim 0$ and $\frac{\partial v}{\partial t} \sim 0$. It can then be seen that the last term is generally small and the Macmillan-Barone-Deese-Whaley approximation assumes that it can be integrated. This results in the following equation:

```
$S^2\frac{\partial^2 g}{\partial S^2} + \beta S\frac{\partial g}{\partial S} - \frac{\alpha}{h}\frac{\partial g}{\partial h} = 0$ (5.2.14)
```

which is a second-order differential equation with two linearly independent solutions of the form $aS^\gamma$. They can be found by substituting $g(S, E, h) = aS^\gamma$ into Eq. (5.2.14) as:

```
$\frac{\partial g}{\partial S} = a\gamma S^{\gamma-1}$, $\frac{\partial^2 g}{\partial S^2} = a\gamma(\gamma-1)S^{\gamma-2} = a\gamma^2 S^{\gamma-2} - a\gamma S^{\gamma-2}$
```

so

```
$S^2\frac{\partial^2 g}{\partial S^2} = a\gamma^2 S^{\gamma} - a\gamma S^{\gamma} = a\gamma^2 g - a\gamma g$
```

and

```
$\beta S\frac{\partial g}{\partial S} = \beta a\gamma S^{\gamma} = \beta \gamma g = \beta S\gamma g$
```