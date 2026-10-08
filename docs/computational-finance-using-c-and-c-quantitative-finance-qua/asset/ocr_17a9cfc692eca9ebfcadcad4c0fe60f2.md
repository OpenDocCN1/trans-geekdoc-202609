# Appendix B: Barrier option integrals

Letting $d_3=-k_3$ we have:

```
$d_3 = \frac{\log(B^2/SE) + (r-q-\sigma^2/2)\tau}{\sigma\sqrt{	au}}$$
```

and

```
$I_D = \left(\frac{B}{S}\right)^{2(r-\sigma^2-1)} E\exp(-r\tau)N_1(d_3) \quad (B.1.5)$
```

Now consider the term:

```
$I_C = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{X=\log(E/S)}^{\infty} \exp(X) \exp(\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right) \n\times \exp(\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right))dX$
```

Now we have

```
$\exp(X)\exp(\left(-\frac{(X-(r-\sigma^2/2)\tau)^2}{2\sigma^2\tau}\right)\exp(\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)) \n= \exp(-\{{(X-(r-\sigma^2/2)\tau)^2-2\sigma^2\tau X\} \n-4\log(B/S)X+4(\log(B/S))^2)/(2\sigma^2\tau)) \n= \exp(((\sigma^2)\tau+2(r-q-\sigma^2/2)\tau^2\sigma^2 \n+4(r-q-\sigma^2/2)\log(B/S)+4\sigma^2\log(B/S))/(2\sigma^2\tau) \n\times \exp(-\\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau)) \n= \exp((r-q)\tau)\exp(\left(\frac{2(r-q)}{\sigma^2}+1\right)\log(\left(\frac{B}{S}\right)) \n\times \exp(-\\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau)) \n= \exp((r-q)\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1} \n\times \exp(-\\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/2\sigma^2\tau))$
```

So we have:

```
$I_C = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1} \frac{S\exp(-q\tau)}{\sigma\sqrt{2\pi}} \n\times \int_{X=\log(E/S)}^{\infty} \exp(-\\{X-(r-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S))^2\}/(2\sigma^2\tau)^{-1})dX$
```