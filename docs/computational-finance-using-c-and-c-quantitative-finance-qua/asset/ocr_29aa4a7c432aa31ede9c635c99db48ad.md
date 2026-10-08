# Appendix B: Barrier option integrals

gives

```
$I_D = \left(\frac{B}{S}\right)^{2(r-q-\sigma^2/2)/\sigma^2} E \exp(-r\tau) \int_{u=k5}^{k6} \exp\left(-\frac{u^2}{2}\right) du \quad (B.2.3)$
```

where

```
$k_5 = \frac{\log(E/S) - (r-q-\sigma^2/2)\tau - 2\log(B/S)}{\sigma\sqrt{\tau}} = \frac{\log(ES/B^2) - (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

and

```
$k_6 = \frac{\log(B/S) - (r-q-\sigma^2/2)\tau - 2\log(B/S)}{\sigma\sqrt{\tau}} = \frac{\log(S/B) - (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

and so

```
$I_D = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2-1} \exp(-r\tau)\{N_1(k_6) - N_1(k_5)\}$
```

This can be re-expressed as:

```
$I_D = \left(\frac{B}{S}\right)^{2(r-q)/\sigma^2} \exp(-r\tau)\{N_1(d_5) - N_1(d_6)\}$ \quad (B.2.4)$
```

where

```
$d_5 = \frac{\log(B^2/ES) - (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}} \n d_6 = \frac{\log(B/S) + (r-q-\sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

We now consider the term:

```
$I_C = -\frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}} \int_{\log(E/S)}^{\log(B/S)} \exp\left(-\frac{[X-(r-q-\sigma^2/2)\tau]^2}{2\sigma^2\tau}\right) \n \times \exp\left(\frac{2\log(B/S)(X-\log(B/S))}{\sigma^2\tau}\right)dX$
```

In a similar manner to Section B1 we let

```
$u = \frac{X-(r-q-\sigma^2/2)\tau-\sigma^2\tau-2\log(B/S)}{\sigma\sqrt{\tau}}$
```

which gives:

```
$I_C = -S\exp(-r\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1} \{N_1(k_8) - N_1(k_7)}$
```