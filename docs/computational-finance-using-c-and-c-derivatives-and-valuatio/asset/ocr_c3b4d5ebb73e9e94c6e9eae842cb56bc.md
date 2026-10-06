# Estimating the Hazard Rate from Market Observables

From equation (7.2.10), we know that the time $t$ forward rate between times $T_1$ and $T_2$ is given by

```
$F(t, T_1, T_2) = \frac{1}{T_2 - T_1} \left\{ \frac{DF(t, T_2)}{DF(t, T_1)} ight\}, \quad (7.4.11)$
```

where $DF(t, T_1)$ and $DF(t, T_2)$ are the prices of the non-defaltable zero coupon bonds with maturities $T_1$ and $T_2$ respectively.

Letting $T_1 = T$ and $T_2 = T + \Delta T$, we obtain

```
$F(t, T, \Delta T) = \frac{1}{\Delta T} \left\{ \frac{DF(t, T+\Delta T)}{DF(t, T)} ight\}, \quad (7.4.12)$
```

which can be re-expressed as

```
$F(t, T, \Delta T) = -\left\{ \frac{DF(t, T+\Delta T) - DF(t, T)}{\Delta T} ight\} \frac{1}{DF(t, T+\Delta T)}, \quad (7.4.13)$
```

If $\Delta T ightarrow 0$, then $F(t, T, \Delta T) ightarrow f(t, T)$, and from equation (7.4.13), we obtain

```
$f(t, T) = -\frac{\partial DF(t, T)}{\partial T} \frac{1}{DF(t, T)} \= -\frac{\partial \ln(DF(t, T))}{\partial T}, \quad (7.4.14)$
```

Using equation (7.4.14), the instantaneous forward rate computed using non-defaultable zero coupon bond prices is and the corresponding instantaneous forward rate computed from default zero coupon bond prices is

```
$f(t, T) = -\frac{\ln(DF(t, T))}{\partial T}, \quad (7.4.15)$
```

```
$ar{f}(t, T) = -\frac{\ln(\overline{DF}(t, T))}{\partial T}, \quad (7.4.16)$
```

Taking the survival probability $S(t,T)$ to be the ratio of the prices of defaultable and non-defaultable zero coupon bonds, and now from equations (7.4.15) and (7.4.16), we have

```
$S(t, T) = \frac{\overline{DF}(t, T)}{DF(t, T)}, \quad (7.4.17)$
```

```
$ar{f}(t, T) - f(t, T) = -\frac{\ln(\overline{DF}(t, T) - DF(t, T))}{\partial T} \= -\frac{1}{\partial T} \ln \left\{ \frac{\overline{DF}(t, T)}{DF(t, T)} ight\}, \quad (7.4.18)$
```