# C.3 The variance and covariance of random variables

# C.3.1 Variance

One variable

Let $X$ be a variate from a given distribution, and $Z$ be the following linear function of this variate:

```
$Z = a + bX$
```

where $a$ and $b$ are constants. Then

```
$E[Z] = E[a] + E[bX] = a + bE[X]$
```

and

```
$Var[Z] = E[(Z - E[Z])^2]
$= E[(a + bX - a - bE[X])^2]
$= E[(bX - bE[X])^2]
$= E[b^2(X - E[X])^2]
$= b^2E[(X - E[X])^2]$
```

Therefore the mean is $a + bE[X]$, and the variance is $Var[X]$.

Two variables

Let $Z = a + b_1X_1 + b_2X_2$, where $a, b_1$ and $b_2$ are constants.
Then the mean is $E[Z] = E[a] + E[b_1X_1] + E[b_2X_2] = a + b_1E[X_1] + b_2E[X_2]$.
The variance $Var[Z]$ is computed as follows:

```
$Var[Z] = E[(a + b_1X_1 + b_2X_2 - a - b_1E[X_1] - b_2E[X_2])^2]
$= E[(b_1(X_1 - E[X_1]) + b_2(X_2 - E[X_2]))^2]
$= b_1^2E[(X_1 - E[X_1])^2] + b_2^2E[(X_2 - E[X_2])^2]
$ + 2b_1b_2E[(X_1 - E[X_1]])E[(X_2 - E[X_2])]
$= b_1^2Var[X_1] + b_2^2Var[X_2] + 2b_1b_2Cov(X_1, X_2),$
```

$Cov[X_1, X_2]$ is the covariance between $X_1$ and $X_2$. If $X_1$ and $X_2$ are identical independently distributed random variables (IID) $Cov[X_1, X_2] = 0$, and we have:

```
$Var[Z] = b_1^2Var[X_1] + b_2^2Var[X_2]$
```