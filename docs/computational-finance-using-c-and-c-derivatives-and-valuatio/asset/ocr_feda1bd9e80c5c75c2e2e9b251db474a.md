# 312 APPENDIX | B Barrier Option Integrals

where $c$ is the value of a vanilla call and

```
$d_1 = \frac{\log(S/E) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}},\quad d_2 = \frac{\log(S/B) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}\n$$d_3 = \frac{\log(S/E) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}},\quad d_4 = \frac{\log(S/B) + (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

Letting $I_B = I_C + I_D$

```
$I_C = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int_{X=\log(E/S)}\log(B/S)\exp(X)\exp\left(\\[\{X - (r - q - \sigma^2/2)\tau\\}/2\sigma^2\tau\right)\right)\times\exp\left(\\frac{2\log(B/S)(X - \log(B/S))}{\sigma^2\tau}\right)dX$
```

and

```
$I_D = \frac{S\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int_{X=\log(E/S)}\log(B/S)\exp\left(\\\[\{X - (r - q - \sigma^2/2)\tau\\}/2\sigma^2\tau\right)\right)\times\exp\left(\\frac{2\log(B/S)(X - \log(B/S))}{\sigma^2\tau}\right)dX$
```

In a similar manner to that in Appendix B.1, we have

```
$I_D = \left(\\frac{B}{S}\right)^{2(r-q-\sigma^2)/\sigma^2}\frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int_{X=\log(E/S)}\log(B/S)\exp\left(\\\[\{X - (r - q - \sigma^2/2)\tau - 2\log(B/S)\\}/2\sigma^2\tau\right)\right)dX.$
```

Letting $u = [X - (r - q - \sigma^2/2)\tau - 2\log(B/S)]/\sigma$ gives

```
$I_D = \left(\\frac{B}{S}\right)^{2(r-q-\sigma^2)/\sigma^2}\frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int_{u=k_5}^{k_6}\exp\left(-\frac{u^2}{2}\right)du.,\quad(B.2.3)
```

where

```
$k_5 = \frac{\log(E/S) - (r - q - \sigma^2/2)\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}\n=\frac{\log(ES/B^2) - (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

and

```
$k_6 = \frac{\log(B/S) - (r - q - \sigma^2/2)\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}\n=\frac{\log(S/B) - (r - q - \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```