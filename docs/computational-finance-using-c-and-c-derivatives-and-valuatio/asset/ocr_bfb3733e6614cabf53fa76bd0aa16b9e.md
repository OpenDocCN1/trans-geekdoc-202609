# The Variance and Covariance of Random Variables Section | C.3 319

As before all the $X$ variables are $IID$, then the covariance terms are zero and we have

```
$Var[Z] = \sum_{i=1}^{n} b_i^2 Var[x_i]$$
```

If in all the $b_i$ terms are one and all the $X$ variable have variance $\sigma^2$, we obtain

```
$Var[Z] = \sum_{i=1}^{n} Var[x_i] = n\sigma^2$.
```

# C.3.2 Covariance

```
$Cov[X,Y] = E[(X-E[X])(Y-E[Y])] = E[XY-E[X]Y-YE[X]+E[X]E[Y]]
= E[XY]-E[X]E[Y]-E[X]E[Y]+E[X]E[Y]
= E[XY]-E[X]E[Y].$.
```

By symmetry, it can be seen that $Cov[X,Y] = Cov[Y,X]$.

# Two Variables

Let $Z_1 = a+bX$ and $Z_2 = c+dY$, where $a, b, c$, and $d$ are constants. We have

```
$Cov[Z_1, Z_2] = Cov[a+bX, c+dY]
= E[(a+bX)(c+dY)]-E[a+bX]E[c+dY]
= E[ac+bcX+adY+bdXY]-\{(a+bE[X])(c+dE[Y])\}\n= ac+bcE[X]+adE[Y]+bdE[XY]-ac
= bcE[X]-adE[Y]-bdE[X]E[Y]
= bdE[XY]-E[X]E[Y],$.
```

$.. Cov[Z_1, Z_2] = bdCov[X,Y].$.

# Three Variables

Let $Z_1 = a+b_1X_1+b_2X_2$ and $Z_2 = c+dY$, where $a, b_1, b_2, c$, and $d$ are constants. We have

```
$Cov[Z_1, Z_2] = Cov[a+b_1X_1+b_2X_2,c+dY]
= E[(a+b_1X_1+b_2X_2)(c+dY)]-E[a+b_1X_1+b_2X_2]E[(c+dY)]
= E[(a+b_1X_1)(c+dY)+b_2X_2(c+dY)]
= \{E[(a+b_1X_1)]+E[b_2X_2]E[c+dY]\}$.
```