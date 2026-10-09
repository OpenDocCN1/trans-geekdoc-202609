is created as the number of cell phone subscribers in each year, measured in terms of phones per five people so that it lives in the same range as the abortion variable. Figure 6.1 shows both treatments.

![](bbox=[0.18, 0.17, 0.88, 0.45])

FIGURE 6.1: U.S. abortion and cell phone rates (per ten births and five people, respectively) during the sample.

Swapping the phone variable for abortion rates in a regression that otherwise matches the one from earlier, we do indeed find that cell phones lead to fewer murders:

```
```
> tech <- glm(y ~ phone + t + s + .., data=controls)
> summary(tech)$coeff["phone",]
  Estimate  Std. Error t value Pr(>|t|)
-3.729846e-01 6.927458e-02 -5.384148e+00 1.068929e-07
```
```

Adding one cell phone per every five Americans results in a 31% drop in the murder rate.

```
```
> 1 - exp(-3.729846e-01)
[1] 0.3113242
```
```

The effect is similar in magnitude and more statistically significant than the estimated abortion effect.