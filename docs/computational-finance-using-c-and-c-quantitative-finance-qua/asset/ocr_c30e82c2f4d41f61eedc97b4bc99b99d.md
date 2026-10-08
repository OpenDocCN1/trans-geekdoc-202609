Computational Finance Using C and C#

On rearranging we have:

```
$$\frac{\partial f}{\partial t}+S\frac{\partial f}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 f}{\partial S^2}}=rf$$
```

which is-Black–Scholes partial differential equation. See Appendix I concerning the Feynman–Kac formula.

Let us consider put and call options on the same underlying asset. If we let c be the value of a European call option and p that of a European put option then we have the following equations:

```
$$\frac{\partial p}{\partial t}+S\frac{\partial p}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 p}{\partial S^2}}=rp$
```

and

```
$$\frac{\partial c}{\partial t}+S\frac{\partial c}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 c}{\partial S^2}}=rc$
```

If we now a linear combination of put and call options, $\psi=a_1c+a_2p$, where $a_1$ and $a_2$ are constants, then $\psi$ obeys the Black-Scholes equation:

```
$$\frac{\partial \psi}{\partial t}+S\frac{\partial \psi}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 \psi}{\partial S^2}}=r\psi$
```

We will prove that $\psi$ satisfies Eq. (4.4.12).

First rewrite Eq. (4.4.12):

```
$$\frac{\partial(a_1c+a_2p)}{\partial t}+S\frac{\partial(a_1c+a_2p)}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2(a_1c+a_2p)}{\partial S^2}}=r(a_1c+a_2p)$
```

and use the following results from elementary calculus:

```
$$\frac{\partial(a_1c+a_2p)}{\partial t}}=a_1\frac{\partial c}{\partial t}+a_2\frac{\partial p}{\partial t}$
$\frac{\partial(a_1c+a_2p)}{\partial S}}=a_1\frac{\partial c}{\partial S}+a_2\frac{\partial p}{\partial S}$
```

and

```
$$\frac{\partial^2(a_1c+a_2p)}{\partial S^2}}=a_1\frac{\partial^2 c}{\partial S^2}+a_2\frac{\partial^2 p}{\partial S^2}$
```

If we define the left-hand side of Eq. (4.4.12) as $LHS$, then we have:

```
$LHS=a_1\left[\frac{\partial c}{\partial t}+S\frac{\partial c}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 c}{\partial S^2}\right]+a_2\left[\frac{\partial p}{\partial t}+S\frac{\partial p}{\partial S}+\frac{1}{2}\sigma^2S^2\frac{\partial^2 p}{\partial S^2}\right]$
```

64