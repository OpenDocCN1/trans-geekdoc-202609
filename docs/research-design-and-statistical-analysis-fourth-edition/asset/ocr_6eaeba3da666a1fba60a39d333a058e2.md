# Notation and Summation Operations 691

# A.1.2 Applying the summation Rules

We can apply the rules of summation to prove the properties of means and variances stated in Chapter 2 (Section 2.3.1). Throughout this section it should be clear that we are summing over $i$ from 1 to $n$ even though the index and limits are not explicitly presented in each expression.

Properties of the Mean

+   1. $\Sigma(Y - \bar{Y}) = 0$; the sum of all deviations of scores about their mean is zero. Applying Rule 3, we get

```
$\Sigma(Y - \bar{Y}) = \Sigma Y - \Sigma \bar{Y}$
```

Therefore, $\bar{Y}$ is a constant; its value is the same regardless of the value of the index of summation. Therefore, applying Rule 2, we rewrite the last equation as

```
$\Sigma(Y - \bar{Y}) = \Sigma Y - n\bar{Y}$
```

Because $\bar{Y} = \Sigma Y/n$, we can rewrite this as

```
$\Sigma(Y - \bar{Y}) = \Sigma Y - n\bar{Y} = \Sigma Y - \frac{\Sigma Y}{n} = \Sigma Y - \Sigma Y = 0$
```

+   2. $\Sigma(Y + k)/n = \bar{Y} + k$; if a constant is added to all scores, the mean is increased by that constant. Applying Rule 3 gives

```
$\frac{\Sigma(Y + k)}{n} = \frac{\Sigma Y + \Sigma k}{n} = \frac{\Sigma Y}{n} + \frac{\Sigma k}{n}$
```

Applying Rule 2 and noting that $\Sigma Y/n = \bar{Y}$, we have

```
$\frac{\Sigma(Y + k)}{n} = \bar{Y} + \frac{\Sigma k}{n}$
```

+   3. $\Sigma kY/n = k\bar{Y}$; if all scores are multiplied by a constant, the mean is multiplied by that constant. Applying Rule 1, we have

```
$\frac{\Sigma kY}{n} = k\bar{Y}$
```

+   4. $\Sigma(Y - \bar{Y})^2$ is a minimum. Assume that there is some value $\bar{Y} + d$ such that the sum of squared deviations of all scores is smaller than the sum about any other value. This sum of squared distances is $\Sigma[Y - (\bar{Y} + d))^2$. Expanding in accord with Rule 3, we have

```
$\Sigma[Y - (\bar{Y} + d))^2 = \Sigma[(Y - \bar{Y}) - d]^2 = \Sigma(Y - \bar{Y})^2 + \Sigma d^2 - 2\Sigma d(Y - \bar{Y})$
```

Applying Rule 1, we rewrite the last term as

```
$2\Sigma d(Y - \bar{Y}) = 2d\Sigma(Y - \bar{Y}) = (2d)(0)$
```