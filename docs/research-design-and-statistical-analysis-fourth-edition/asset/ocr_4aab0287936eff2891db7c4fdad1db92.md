# Table 10.1 Means and variances of the data in Table 8.1 with contrast weights

| | Control | Loci | Image | Rhyme |
|---|---|---|---||
| Mean | 6.5 | 12.1 | 10.7 | 10.5 |
| Variance | 10.056 | 19.433 | 25.567 | 16.722 |
| n | 10 | 10 | 10 | 10 |
| Weight | 0 | .5 | .5 | -1 |
| Weight × 2 | 0 | 1 | 1 | -2 |

Given the information in Table 10.1, we can now proceed to calculate the $t$ statistic. The formula is

```
$t = \frac{\hat{\psi}}{s_{\psi}} = \frac{\sum w_j \hat{Y}_j}{\sqrt{MS_{S/A} \sum \frac{w_j^2}{n_j}}} \quad (10.5)$
```

Note that the denominator enumerates $MS_{S/A}$, an average of all four within-group variances. Even though the control group is not included in the contrast, including the variance of the control group in the calculation of the error is justified if we assume homogeneous variances. The advantage of using $MS_{\psi}$ is that the estimate of error variance will be more precise and our test will be more powerful because the error degrees of freedom are based on groups rather than three.

For the example of Table 10.1, we will assume homogeneity of variance. Therefore, given Equation 10.5 and the statistics in Table 10.1, we calculate

```
$\hat{\psi} = \frac{1}{2}(12.1 + 10.7) - (1)(10.5) = 0.9$\n$MS_{S/A} = (10.056 + 19.433 + 25.567 + 16.722) / 4 = 17.644$
```

and the standard error of the contrast is

```
$s_{\psi} = \sqrt{\frac{0^2}{10} + \frac{.5^2}{10} + \frac{.5^2}{10} + \frac{(-1)^2}{10}} = \sqrt{2.6916} = 1.6406$
```

Finally,

```
$t = \frac{\hat{\psi}}{s_{\psi}} = \frac{0.9}{1.6406} = 0.548$
```