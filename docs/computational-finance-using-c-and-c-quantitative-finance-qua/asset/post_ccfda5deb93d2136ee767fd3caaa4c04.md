
# Computational Finance Using C and C#

![](img/603dc31da1bd8dca364a8fe29abcaeaa_160_0.png)

**Figure 5.5** An uniform grid, which could be used to estimate the value of a vanilla option which matures in two years' time. The grid parameters are: $n_t=10$, $\Delta t = 0.2$, $\Delta S = 5$, and $S_{max} = 50$. The option parameters are $E = 25$, $S_0 = 20$, and $\tau = 2.0$. As usual we denote the grid node values by $f_{i,j}$, where $i$ is the time index and $j$ is the asset index. The option values of grid nodes for maturity for a vanilla put are thus labelled as $val.f_{i,j}=0\dots,10$, where $val$ is the value of the option on the node; since $E = 25$ only those nodes with $j < 5$ have nonzero option values.

Now that we know how to solve the Black–Scholes equation it is possible to include, without much difficulty, many exotic features such as lock out periods, barriers, rebates, etc. routine `opt_gfd` solves the Black-Scholes equation using a uniform grid. The asset price is set to one of the grid lines, which means that interpolation is not required.

## 5.4.3 Nonlinear grids

In the previous section we showed how to solve the Black-Scholes equation using a uniform grid. Although this approach will provide satisfactory solutions to many option pricing problems, there are situations in which it is important to place grid nodes at locations that do not correspond to those available in a uniform grid. Increasing the density of grid lines in regions of interest can lead to improved accuracy in the estimated option values and also the estimates of the hedge strategies (the Greeks).

Here we provide an example that illustrates the benefits of using the nonuniform grids in the evaluation of down and out call barrier. Later on in

## Single asset American options

Section 5.4.6 we give a further example which shows the use of nonuniform grids to evaluate barrier options.

The purpose of this section is to show how to discretize the Black–Scholes equation using a nonuniform grid, and to derive an expression (see Eq. (5.4.39)) that is equivalent to Eq. (5.4.14). Although the tridiagonal system of equations we have to solve in this section will be different from that in Section 5.4, the solution method is exactly the same. That matters once we have derived Eq. (5.4.39) all the other information we require to evaluate both European and American options is available in Section 5.4 under the headings:

- The boundary conditions
- Computation of the option values at a given time instant
- Backwards iteration and early exercise.

We will now consider the finite-difference approximation for a nonuniform grid, and then show how to value the down and call barrier option.

## The finite-difference approximation

Here we consider how to discretize the Black–Scholes equation using a nonuniform grid, with both the price interval $\Delta S$ and the time step $\Delta t$ are not constant but can vary throughout the grid.

Allowing for a nonconstant time step is quite simple. The time step occurs in both the first derivative $f_{i,j}$ (see Eq. (5.4.4)) and in the option value equations (see Eqs. (5.4.14)-(5.4.21)) as the constant $\Delta t$. To incorporate a varying time step, $\Delta_{i,j}=0$, thus only requires setting $\Delta t=\Delta_{i,j}$ at the ith step and then continuing with the solution method outlined in Section 5.4.

The incorporation of nonconstant asset price intervals requires more work. This is because the finite-difference approximations to the second derivatives $f'_{i,j}$ and $f''_{i,j}$ in Eqs. (5.4.10) and (5.4.11) are based on a Taylor expansion about the point $f_{i,j}$.

We will now derive expressions for these derivatives.

If we let $\Delta X_j=S_j-S_{j-1}$ and $\Delta X^+j=S_{j+1}-S_j$ and then use a Taylor expansion about $f_{i+1,j}$ we have

```
f_{i+1,j+1}=f_{i+1,j}+f'_{i+1,j}\Delta X^+j+\frac{1}{2}f''_{i+1,j}(\Delta X^+j)^2 \quad (5.4.32)
```

and also

```
f_{i,j-1}=f_{i,j}-f'_{i,j}\Delta X^+j+\frac{1}{2}f''_{i,j}(\Delta X^+j)^2 \quad (5.4.33)
```

Multiplying Eq. (5.4.32) by $\Delta X^+j$ and adding it to $\Delta X^+j$ times Eq. (5.4.33), gives

```
\Delta X^+j_{i+1,j-1}=\Delta X^+j_{i+1,j}+\Delta X^+j_{i+1,j}+\frac{1}{2}f''_{i+1,j}(((\Delta X^+j)^2+(\Delta X^+j)^2)\Delta X^+j)
```

Therefore

```
$f''_{i+1,j} = \frac{\Delta X_j^+ f_{i+1,j-1} + \Delta X_{j-1}^+ f_{i+1,j} - \Delta X_j f_{i+1,j} - \Delta X_j^+ f_{i+1,j}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2}
```

So

```
$f''_{i+1,j} = \frac{2[\Delta X_j^+ f_{i+1,j-1} + \Delta X_j^- f_{i+1,j+1} - f_{i+1,j}(\Delta X_j^+ + \Delta X_j^-)]}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2}
(5.4.34)
```

To calculate $f'_{i+1,j}$ we rearrange Eq. (5.4.33) to obtain

```
$-f'_{i+1,j} \Delta X_j^- = f_{i+1,j-1} - f_{i+1,j} - \frac{1}{2}f''_{i+1,j}(\Delta X_j^-)^2
```

and

```
$f'_{i+1,j} = \frac{f_{i+1,j} - f_{i+1,j-1}}{\Delta X_j^-} + \frac{1}{2}f''_{i+1,j} \Delta X_j^-$
(5.4.35)
```

If we now substitute for $f''_{i+1,j}$, from Eq. (5.4.34), into Eq. (5.4.35) we have

```
$f'_{i+1,j} = \frac{f_{i+1,j} - f_{i+1,j-1}}{\Delta X_j^-} + \frac{[\Delta X_j^+ f_{i+1,j-1} - (\Delta X_j^+ + \Delta X_j^-)f_{i+1,j} + \Delta X_j^- f_{i+1,j+1}]\Delta X_j^-}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2}
```

which simplifies to give

```
$f'_{i+1,j} = \frac{(\Delta X_j^+)^2 (f_{i+1,j-1} - f_{i+1,j}) - (\Delta X_j^-)^2 f_{i+1,j} + (\Delta X_j^-)^2 f_{i+1,j+1}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2}
```

so that we finally have

```
$f''_{i+1,j} = \frac{(\Delta X_j^-)^2 f_{i+1,j+1} + ((\Delta X_j^+)^2 - (\Delta X_j^-)^2)f_{i+1,j} - (\Delta X_j^+)^2 f_{i+1,j-1}}{(\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2}
(5.4.36)
```

In Section 5.4, we can substitute the expressions for $f'_{i+1,j}$ and $f''_{i+1,j}$ given in Eqs. (5.4.36) and (5.4.34), into Eq. (5.4.7) the discretized Black-Scholes equation. If we let $D = (\Delta X_j^+)^2 \Delta X_j^- + (\Delta X_j^-)^2 \Delta X_j^+$ we then obtain

```
$r \Delta t(\theta_m f_{i+1,j} + \theta_m^* f_{i,j}) = \frac{(r-q)S_j \Delta t A_1}{D} f_{i,j} + \frac{\sigma^2 S_j^2 \Delta t A_2}{D}$
(5.4.37)
```

where $\Theta_m^* = 1 - \Theta_m$, and

```
$A_1 = \Theta_m[f_{i,j+1}(\Delta X_j^+)^2 - f_{i+1,j-1}(\Delta X_j^+)^2 - f_{i+1,j}\{(\Delta X_j^+)^2 - (\Delta X_j^-)^2\} + \Theta_m^*[f_{i,j+1}(\Delta X_j^+)^2 - f_{i,j-1}(\Delta X_j^+)^2 - f_{i,j}\{(\Delta X_j^+)^2 - (\Delta X_j^-)^2\}]$
```

and

```
$A_2 = \Theta_m[f_{i,j+1}\Delta X_j^+ + f_{i,j-1}\Delta X_j^- - f_{i+1,j}\{\Delta X_j^+ + \Delta X_j^-\}] + \Theta_m^*[f_{i,j+1}\Delta X_j^+ + f_{i,j-1}\Delta X_j^- - f_{i+1,j}\{\Delta X_j^+ + \Delta X_j^-\}]$
```

Collecting like terms, we obtain:

```
$B_1 f_{i,j-1} + B_2 f_{i,j} + B_3 f_{i,j+1} + C_1 f_{i+1,j-1} + C_2 f_{i+1,j} + C_3 f_{i+1,j+1} = 0$
(5.4.38)
```

where

```
$B_1 = \frac{-\Theta_m^*(r-q)S_j\Delta t(\Delta X_j^+)^2}{D} + \frac{\sigma^2 S_j^2\Delta t\Delta X_j^+}{D}$
$B_2 = -1 - r\Delta t\Theta_m^* \frac{\Theta_m^*\sigma^2 S_j^2\Delta t(\Delta X_j^+ + \Delta X_j^-)}{D}$
$B_3 = \frac{\Theta_m^*(r-q)S_j\Delta t(\Delta X_j^+)^2}{D} + \frac{\Theta_m^*\sigma^2 S_j^2\Delta t\Delta X_j^-}{D}$
$C_1 = \frac{\Theta_m\sigma^2 S_j^2\Delta t\Delta X_j^+}{D} - \frac{\Theta_m(r-q)S_j\Delta t}{D}$
$C_2 = 1 - r\Delta t\Theta_m \frac{\Theta_m(r-q)S_j\Delta t(\Delta X_j^+)^2 - (\Delta X_j^-)^2}{D}$
$C_3 = \frac{\Theta_m\sigma^2 S_j^2\Delta t(\Delta X_j^+ + \Delta X_j^-)}{D} + \frac{\Theta_m(r-q)S_j\Delta t(\Delta X_j^-)^2}{D}$
```

Since we are solving the Black-Scholes equation backwards in time we will re-arrange Eq. (5.4.38) as:

```
$a_j f_{i,j-1} + b_j f_{i,j} + c_j = R_{i+1,j}$
(5.4.39)
```

where the right-hand side $R_{i+1,j}$ is:

```
$R_{i+1,j} = \tilde{a}_j f_{i+1,j-1} + \tilde{b}_j f_{i+1,j} + \tilde{c}_j f_{i+1,j+1}$
(5.4.40)
```

and the coefficients are

```
$a_j = \Theta_m^* \Delta t \left\{ \frac{(r-q)S_j(\Delta X_j^+)^2}{D} - \frac{\sigma^2 S_j^2 \Delta X_j^+}{D} \right\}$
(5.4.41)
```

```
$b_j = 1 + \Theta_m^* \Delta t \left[ r + \frac{\sigma^2 S_j^2(\Delta X_j^+)^2 + \Delta X_j^+}{D} + \frac{(r-q)S_j((\Delta X_j^+)^2 - (\Delta X_j^-)^2)}{D} \right]$
(5.4.42)
```

```
$c_j = \Theta_m^* \Delta t \left\{ \frac{-(r-q)S_j(\Delta X_j^+)^2}{D} - \frac{\sigma^2 S_j^2 \Delta X_j^-}{D} \right\}$
(5.4.43)
```

```
$\tilde{a}_j = \Theta_m \Delta t \left\{ \frac{\sigma^2 S_j^2 \Delta X_j^+}{D} - \frac{(r-q)S_j(\Delta X_j^+)}{D} \right\}$
(5.4.44)
```

```
$\tilde{b}_j = 1 - \Theta_m \Delta t \left[ \frac{(r-q)S_j((\Delta X_j^+)^2 - (\Delta X_j^-)^2)}{D} - \frac{\sigma^2 S_j^2[\Delta X_j^+ + \Delta X_j^-]}{D} \right]$
(5.4.45)
```

```
$\tilde{c}_j = \Theta_m \Delta t \left\{ \frac{(r-q)S_j(\Delta X_j^+)^2}{D} + \frac{\sigma^2 S_j^2 \Delta X_j^-}{D} \right\}$
(5.4.46)
```

Here Eq. (5.4.39), is the case for Eq. (5.4.14) in Section 5.4, the relationship between the three option values $f_{i+1,j-1}, f_{i+1,j}, f_{i+1,j+1}$ at time index $i+1$, and the three option values $f_{i,j-1}, f_{i,j}, f_{i,j+1}$ at time index $i$. It can also be seen that Eq. (5.4.39) is the nonuniform grid equivalent of Eq. (5.4.14) given in Section 5.4. We will now show that Eqs. (5.4.39) and (5.4.14) are identical when a uniform grid is used, that $\Delta X_j^+ = \Delta X_j^-$.
