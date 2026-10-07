# One Factor Between-Participants Designs 215

# 8.9 Summary

This chapter introduced the analysis of variance in the simplest possible context, the one-factor between-participants design. The developments in this chapter will be relevant in the analyses of data from other designs. These developments included:

+   * The analysis of variance. We illustrated the idea of a structural model that underlies the data and directs the partitioning of variability in the data. The structural model is the basis for determining what variance calculations in terms of population variance parameters. The expected mean squares (EMS), in turn, justify the error terms for tests of the null hypothesis and involve in estimating the magnitude of effects.
* Measures of importance. We defined and applied to data several statistics that indicate the importance of the independent variable. Confidence intervals were also presented to provide a range of values of the parameter being estimated.
* A priori power and sample size. We illustrated how sample size for a multi-group study can be determined, once the values of $\alpha$, the desired power, and the effect size are of selected.
* Assumptions underlying the significance test and the estimates of importance. We reviewed these assumptions, discussed the consequences of their violation, and described several solutions to violations.

# Appendix 8.1

# Partitioning the Total Variability in the One-Factor Design

The following developments involve two indices of summation: $i$ indexes a value from 1 to $n$ within each group, where $n$ is the number of individuals in a group; $j$ indexes a value from 1 to $a$, where $a$ is the number of groups. Appendix A provides an explanation of the use of this notation, using several examples.
Squaring both sides of Equation 8.1

```
$(\tilde{Y}_i - \tilde{Y}_j)^2 = (\tilde{Y}_i - \tilde{Y}_i)^2 + (\tilde{Y}_j - \tilde{Y}_j)^2 + 2(\tilde{Y}_i - \tilde{Y}_j)(\tilde{Y}_i - \tilde{Y}_j)$
```

Summing over $i$ and $j$, and applying the rules of Appendix A, we have

```
$$\sum_{i=1}^n \sum_{j=1}^a (\tilde{Y}_i - \tilde{Y}_j)^2 = \sum_{i=1}^n \sum_{j=1}^a (\tilde{Y}_i - \tilde{Y}_i)^2 + n\sum_{j=1}^a (\tilde{Y}_j - \tilde{Y}_j)^2 + 2\sum_{i=1}^n \sum_{j=1}^a (\tilde{Y}_i - \tilde{Y}_j)(\tilde{Y}_i - \tilde{Y}_j)$
```

Rearranging terms, we find that the right-most (cross-product) term equals 0:

```
$$\sum_{i=1}^n \sum_{j=1}^a (\tilde{Y}_i - \tilde{Y}_j)(\tilde{Y}_i - \tilde{Y}_j) = 2\sum_{j=1}^a (\tilde{Y}_j - \tilde{Y}_j)\sum_{i=1}^n (\tilde{Y}_i - \tilde{Y}_i)$$\n$\sum_{j=1}^a (\tilde{Y}_j - \tilde{Y}_j)(0) = 0$
```

The last result follows because the sum of deviations of scores about their mean is zero.