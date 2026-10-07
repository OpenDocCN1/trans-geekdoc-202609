# 610 Research Design and Statistical Analysis

variables and then centering the product). The multicolinearity problem is no longer present: agecent and BMicent have correlations of -.007 and .009 with the interaction term, and the VIFs are 1.01, 1.01, and 1.00.

Note that the algorithms built into the standard statistical packages were able to deal with the computational challenges presented by the regression with the uncentered variables, so that the coefficient of the product term is the same, -0.135, for all analyses. However, the coefficients of the lower-order terms are different and have more meaningful interpretations when the centered variables are used. Given centering, the coefficient of X represents the slope of predicted Y by X, with the values of the other predictors equal their means.

# 22.8.5 Do We Have an Interaction or Curvilarity or Both?

Because predictor variables are usually correlated, testing for an interaction or curvilinear is more complicated than we have so far discussed. Suppose the true model is

```
Y = β₀ + β₁X₁ + β₂X₂ + β₃X₁X₂ + ε
```

Because we know what the true model is, we may not test for curvilinear but instead decide to test for the presence of an interaction by regressing Y on X₁, X₂, and X₁ × X₂ If we have enough power, we may find that the coefficient of X₁ × X₂ is not significant, because the true model contains an interaction term, but because the product term in the regression is correlated with the squared term that is in the true model. Conversely, if the true model is

```
Y = β₀ + β₁X₁ + β₂X₂ + β₃X₁X₂ + ε
```

and we test for curvilinear by regressing Y on X₁, X₂, X², and X², if we have sufficient power, we may find that the coefficients of one or both of the squared terms are significant, not because the squared terms are present in the model but left out of the regression equation. with the product term that is present in the model but because of their correlations. Also, omitting terms from the regression can result in finding misleading interaction and curvilinear terms. We may find, example, a positive interaction even when the interaction is negative and we may find a negative quadratic component even when the coefficient of the squared term in the true model is positive. Suppose that the true model

```
Y = β₀ + β₁X₁ + β₂X₂ + β₃X₁X₂ + β₄X₁²X₂ + ε
```

β₁ is positive and β₃ is negative. If we decide to test for the presence of the interaction by regressing Y on X₁, X₂, and X₁ × X₂, but not on X², we may find that the coefficient of the product term is positive though it is not in the true model because of the correlation between the product term and the X² term not included in the model. Similarly, if we regress on X₁, X₂, and X², and omit X₁ × X₂ from the equation, we may find that the coefficient of the squared term is negative, despite being positive in the true model. Therefore, Ganzach (1997) recommends that we include both the interaction and the quadratic terms in the regression when either interaction or quadratic terms are evaluated. Not everyone agrees with Ganzach's recommendation because including the squared terms may