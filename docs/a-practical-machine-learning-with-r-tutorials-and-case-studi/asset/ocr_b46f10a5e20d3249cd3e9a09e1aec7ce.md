# 8 Logistic Regression — Handling Imbalanced Data

```
$P_{rob i} = \beta_1 Inc_i + \beta_2$\nP_{rob i} = 0.0023 Inc_i + 0.1418 \quad (8.1)$
```

![](bbox=[0.231, 0.246, 0.763, 0.51])

**FIGURE 8.1** Linear Function for Binary Classification

As you can see from the regression line in Figure 8.1, the underlying regression assigns continuous numbers to different income levels rather than signing values such as 1 (yacht owner: yes) or 0 (yacht owner: no). Therefore, we interpret the continuous predictions from the regression as being a yacht owner ($P^{rob i}$). Consequently, the methodology used is the Linear Probability Model (LPM)$^2$.

The linear regression in Figure 8.1 as well as the underlying prediction Equation (8.1) from the LPM can be used to predict the probability of a person being a yacht owner based on their income.

For example, a person with an income of 300 ($300,000) has a probability of nearly 80% (0.0023·300 + 0.1418) to own a yacht. In comparison, a person with an income of 100 ($100,000) has a probability of about 35% (0.0023·100 + 0.1418) to be a yacht owner (see Figure 8.1 as well as Equation (8.1)).

Whenever the outcome variable (the probability) of the prediction equation is greater than 0.5,$^3$ we predict "yacht owner: yes" otherwise, "yacht owner:

> $^2$Wooldridge (2020), Section 7.5.

> $^3$We neglect the problem of a probability being precisely 0.5.