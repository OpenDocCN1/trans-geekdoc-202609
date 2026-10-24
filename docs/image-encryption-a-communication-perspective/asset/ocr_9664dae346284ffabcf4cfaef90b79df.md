![](bbox=[0.18, 0.08, 0.45, 0.35])

![](bbox=[0.5, 0.08, 0.78, 0.35])

![](bbox=[0.18, 0.32, 0.45, 0.6])

![](bbox=[0.5, 0.32, 0.78, 0.6])

Figure 8.15 Chaotic-encrypted image with DWT-OFDM over a fading channel.

of course slightly increases the hardware cost. In simulation experiments, compression is performed according to the well-known μ-law. The compression process can be expressed as follows [164,165]:

```
x_c = V_max [ln[1 + μ|x̄_m| / V_max] / ln[1 + μ]] sgn[x̄_m]   (8.26)
```

where

```
V_max = max(|x̄_m|)   m = 0,1,...,N - 1
```

where μ is the companding coefficient, x_c is the companded sample, and x_m is the original sample. The expansion process is simply the inverse of Equation (8.26):

```
x̂_m = V_max / μ [exp(|x_c| ln(1 + μ) / V_max - 1)] sgn(x_c)
```