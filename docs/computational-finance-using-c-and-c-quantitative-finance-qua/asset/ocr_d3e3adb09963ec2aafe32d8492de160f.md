# Letting

$u = \frac{X - (r - q - \sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}$

we have $dX = \sigma\sqrt{\tau} du$ and

```
$I_C = -S\exp(-q\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}N_1(-k_4) \quad (B.1.6)$
```

where

```
$k_4 = \frac{\log(E/S) - (r - q - \sigma^2/2)\tau - \sigma^2\tau - 2\log(B/S)}{\sigma\sqrt{\tau}}\\n= \frac{\log(ES/B^2) - (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

```
$$. I_C = -S\exp(-q\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}N_1(-k_4)$
```

or letting $d_4 = -k_4$ we have

```
$d_4 = \frac{\log(B^2/ES) + (r - q + \sigma^2/2)\tau}{\sigma\sqrt{\tau}}$
```

```
$I_C = -S\exp(-q\tau)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}N_1(d_4) \quad (B.1.7)$
```

The value for the down and out call option is:

$c_{do} = I_A + I_C + I_D = I_A - (-I_C - I_D)$

Since $c_{do} + c_{di} = c$, where $c$ is the value of vanilla call and $c_{di}$ is the value of down and in call, we can write:

$c_{do} = c - c_{di}$

where

```
$c_{di} = S\exp(-q\tau)N_1(d_4)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2+1}\\n E\exp(-r\tau)N_1(d_3)\left(\frac{B}{S}\right)^{2(r-q)/\sigma^2-2}$
```

# B.2 The up and out call

We will now derive the formula for a European up and out call option with dividend yield $q$ when the strike, $E$, satisfies $B > E$.

```
$c_{uo} = \frac{\exp(-r\tau)}{\sigma\sqrt{2\pi}}\int^{\log(B/S)}\{\exp(X)-E\}f(X < B)dX \quad (B.2.1)$
```