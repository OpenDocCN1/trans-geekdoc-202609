The developed GMDH models for prediction of the shear strength of members without stirrups are as follows:

# Layer 1:

```
L_1 = 52.39 + 0.05163A_F - 19.62\left(\frac{a}{d}\right) + 0.1712b - 0.002753\left(\frac{a}{d}\right)A_F
- 1.619 \times 10^{-6}bA_F - 0.02226b\left(\frac{a}{d}\right) - 2.352 \times 10^{-6}A_F^2
+ 1.613\left(\frac{a}{d}\right)^2 + 7.584 \times 10^{-5}b^2
(18.7a)
```

# Layer 2:

```
L_2 = 14.51 - 0.06667L_1 + 0.01931A_F + 0.02435b - 0.001208A_F L_1 - 0.002139bL_1
+ 7.231 \times 10^{-5}bA_F + 0.02188L_1^2 + 1.673 \times 10^{-5}A_F^2 + 5.242 \times 10^{-5}b^2
(18.7b)
```

# Layer 3:

```
L_3 = 39.54 + 0.1569L_2 - 0.08429f_{FU} + 0.8584E_F + 0.0003209f_{FU}L_2
+ 0.000393E_F L_2 - 0.0003528E_F f_{FU} + 0.002545L_2^2 + 2.528 \times 10^{-5}f_{FU}^2
+ 0.0006065E_F^2
(18.7c)
```

# Layer 4:

```
L_4 = 8.036 + 0.4288L_3 + 0.01035A_F + 0.02742b - 0.0004398A_F L_3
- 0.0008504bL_3 + 3.693 \times 10^{-5}bA_F + 0.007928L_3^2 + 5.776 \times 10^{-6}A_F^2
+ 3.757 \times 10^{-6}b^2
(18.7d)
```

# Layer 5:

```
V (KN) = -18 + 0.9005L_4 + 0.008982L + 0.02835d - 1.856 \times 10^{-5}LL_4
- 0.0003146dL_4 + 8.801 \times 10^{-6}dL + 0.0008526L_4^2 - 7.976 \times 10^{-7}L^2
- 1.322 \times 10^{-5}d^2
(18.7e)
```