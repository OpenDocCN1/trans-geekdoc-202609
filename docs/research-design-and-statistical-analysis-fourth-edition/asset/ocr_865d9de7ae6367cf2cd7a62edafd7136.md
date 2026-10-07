# 200 Research Design and Statistical Analysis

We have estimates of the numerator and denominator of $\omega^2$, therefore, substituting into Equation 8.10, we estimate of $\omega^2$ for the one-factor-between-participants design:

```
$$\omega^2 = \frac{(a-1)/a(n)MS_{SA} - MS_{S/A}}{[(a-1)/a(n)MS_{SA} - MS_{S/A}) + MS_{S/A}]} \;quad (8.15)$
```

Okada (2013) has shown that $\omega^2$ very slightly underestimates $\omega^2$, with good efficiency and consistency.

We write Equation 8.15 in a different form, which allows us to calculate $\omega^2$ from knowledge of the $F$ ratio, $a$, and $n$. The advantages are that the expression is simpler and, more importantly, most research reports contain this, we can estimate the strength of association for data calculated other investigators. By defining $F = MS_{SA}/MS_{S/A}$, multiplying the numerator and denominator of Equation 8.15 by $a$, and dividing by $MS_{S/A}$, we have

```
$$\omega^2 = \frac{(a-1)(F_A-1)}{(a-1)(F_A-na)} \;quad (8.16)$
```

Let's review Equations 8.15 and 8.16 represent. If we replicate the experiment many times, the average value of the right-hand term will approximately equal $\omega^2$, the portion of the total variance is attributable to the variance of their means. We say "approximately equal" because the expected value of a ratio is not the same as the expected values. The expression is reasonably accurate and the expression is much simpler than for the exact experiment.

One other equation 8.16 should be noted. Because the numerator and denominator of the $F$ reflect two independent estimates of the population error variance, the null hypothesis is true or the effects of $A$ are very small, the $F$ may be less than 1. Then, $\omega^2$ would be less than 0. Since a variance cannot be negative, we conclude that $\omega^2 = 0$; that is, none of the total variance is attributable to the independent variable.

We can apply Equation 8.16 to the memory data in Table 8.1. In this experiment, $a=4$, $n=10$, and (from Table 8.3) $F=3.220$, then, inserting these values into Equation 8.16,

```
$$\omega^2 = \frac{(3)(2.23)}{(3)(2.23)+40} = .143$$
```

This is very close to the value of 0.146 noted earlier for adjusted $R^2_{adj}$. That values of $R^2_{adj}$ and $\omega^2$ are close is no unusual; Maxwell et al. (1981) reported that the two rarely differ by more than .02. With respect to assessing the importance of each measure, Cohen (1988) suggested that values of .01, .06, and .14 may be viewed as small, medium, and large, respectively. According to those guidelines, the proportion of variability accounted for the study method may be judged to be large. Again, however, we caution that the importance attached to each value must be assessed in the context of the research problem and the investigator's knowledge of the research literature.

# 8.5.3 Cohen's f

In Chapter 6, we presented Cohen's $d$, a measure of the standardized effect for designs in which two means are compared. Cohen's f (1988) is a similar measure for situations