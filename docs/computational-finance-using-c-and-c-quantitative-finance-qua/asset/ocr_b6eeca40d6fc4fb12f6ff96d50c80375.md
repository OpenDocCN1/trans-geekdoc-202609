# Computational Finance Using C and C#

Therefore

```
$f''_{i+1,j} = \frac{\Delta X_j^+ f_{i+1,j-1} + \Delta X_{j-1}^+ f_{i+1,j-1} - \Delta X_j^- f_{i+1,j} - \Delta X_j^+ f_{i+1,j}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+}$
```

So

```
$f''_{i+1,j} = \frac{2[\Delta X_j^+ f_{i+1,j-1} + \Delta X_j^- f_{i+1,j+1} - f_{i+1,j}(\Delta X_j^+ + \Delta X_j^-)]}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+}$
\n$(5.4.34)$
```

To calculate $f'_{i+1,j}$ we rearrange Eq. (5.4.33) to obtain

```
$-f'_{i+1,j} \Delta X_j^- = f_{i+1,j-1} - f_{i+1,j} - \frac{1}{2} f''_{i+1,j}(\Delta X_j^-)^2$
```

and

```
$f'_{i+1,j} = \frac{f_{i+1,j} - f_{i+1,j-1}}{\Delta X_j^-} + \frac{1}{2} f''_{i+1,j} \Delta X_j^-$
\n$(5.4.35)$
```

If we now substitute for $f''_{i+1,j}$, from Eq. (5.4.34), into Eq. (5.4.35) we have

```
$f'_{i+1,j} = \frac{f_{i+1,j} - f_{i+1,j-1}}{\Delta X_j^-} + \frac{[\Delta X_j^+ f_{i+1,j-1} - (\Delta X_j^- + \Delta X_j^+)f_{i+1,j} + \Delta X_j^- f_{i+1,j+1})\Delta X_j^-]}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+}$
```

which simplifies to give

```
$f'_{i+1,j} = \frac{(\Delta X_j^+)^2 (f_{i+1,j-1} - f_{i+1,j}) - (\Delta X_j^-)^2 f_{i+1,j} + (\Delta X_j^-)^2 f_{i+1,j+1}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+}$
```

so that we finally have

```
$f''_{i+1,j} = \frac{(\Delta X_j^-)^2 f_{i+1,j+1} + ((\Delta X_j^+)^2 - (\Delta X_j^-)^2)f_{i+1,j} - (\Delta X_j^+)^2 f_{i+1,j-1}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+}$
\n$(5.4.36)$
```

In Section 5.4, we can substitute the expressions for $f'_{i+1,j}$ and $f''_{i+1,j}$ given in Eqs. (5.4.36) and (5.4.34), into Eq. (5.4.7) the discretized Black-Scholes equation. If we let $D = (\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+$ we then obtain

```
$r \Delta t(\theta_m f_{i+1,j} + \theta_m^* f_{i,j}) = \frac{(r-q)S_j \Delta t A_1}{D} f_{i,j} + \frac{\sigma^2 S_j^2 \Delta t A_2}{D}$
\n$(5.4.37)$
```

*