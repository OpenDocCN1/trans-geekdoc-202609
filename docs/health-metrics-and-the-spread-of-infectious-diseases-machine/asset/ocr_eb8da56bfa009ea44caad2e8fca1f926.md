# 13

# Advanced Data Visualisation Techniques

Learning Objectives

+   - Learn advanced data visualisation techniques
- Create contour plots to visualise interaction effects
- Create a pyramid plot to envisage population distribution

In this chapter, we will learn how to create advanced data visualisation techniques using **ggplot2**. We will create contour plots to visualise interaction effects and pyramid plots to envisage population distribution.

# 13.1 Example: Detecting Interaction Effects with Contour Plots

Interaction effects can cause predictors to act together on the response variable, leading to additional variation in the response. Interaction effects occur when the combined effect of two or more predictors is different from what would be expected if the impact of each predictor were considered alone. For instance, in the case of **cardiovascular disease (CVD)** risk prediction, the interaction between age and cholesterol levels can have a significant impact on the risk of developing heart disease. In addition, if smoke is added to the model, the effect of cholesterol levels on CVD may change depending on whether the individual is a smoker or non-smoker. So, smoke is said to interact with cholesterol levels in predicting CVD risk, as well as age, but in what way?

```
$y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \beta_3x_3 + \epsilon$
```

where $y$ is the result of developing heart disease, $eta_0$ is the intercept, $eta_1$ and $eta_2$ are the coefficients for the predictors $x_1$ and $x_2$, respectively, and $eta_3$ is the coefficient for the **interaction term** $x_1 * x_2$. The error term $\epsilon$ accounts for the variability in the response variable that is not explained by the predictors.

There are four types of interaction:

+   - additive is when $\beta_3 \approx 0$
- antagonistic is when $\beta_3 < 0$
- synergistic is when $\beta_3 > 0$
- atypical is when $\beta_3 \neq 0$

In order to simulate the interaction effects for each type of interaction, we cannot simulate random values for $y$, we need to simulate different levels of interactions between