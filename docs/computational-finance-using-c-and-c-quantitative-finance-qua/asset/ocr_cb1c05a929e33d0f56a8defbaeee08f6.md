# # Appendix B:
Barrier option integrals

# B.1 The down and out call

We will now derive the formula for the value $c_{do}$ of a European down and out call option with dividend yield $q$ when the strike, $E$, satisfies $E > B$.

```
$c_{do} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\f(X > B)dX$ (B.1.1)
```

Substituting for $f(X > B)$ we have $c_{do} = I_A + I_B$ where:

```
$I_A = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}$
\times exp\(-\{X - (r - q - \sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)dX
```

and

```
$I_B = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\infty} \{exp(X) - E\}$
\times exp\(-\{X - (r - q - \sigma^2/2)\tau)^2 / 2\sigma^2\tau\right)\n\times exp\(-\{2\log(B/S)(X - \log(B/S)) / \sigma^2\tau\right)dX
```

Now comparing $I_A$ with Eq. (4.454) we can identify $I_A$ as $c$, the price of a European call. That is:

```
$I_A = S\exp(-q\tau)N_1(d_1) - E\exp(-r\tau)N_1(d_2)$ (B.1.2)
```

where:

```
$d_1 = \frac{\log(S/E) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

```
$d_2 = \frac{\log(S/E) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

We now consider the term $I_B$, and let $I_B = I_C + I_D$ where: