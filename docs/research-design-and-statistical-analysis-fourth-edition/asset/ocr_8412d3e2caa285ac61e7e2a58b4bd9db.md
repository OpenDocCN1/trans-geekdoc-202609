# Additional Topics in Multiple Regression 589

then, the given regression assumptions, the bs can be shown to be unbiased estimators of the βs. However, as we pointed out in Chapter 20, if the bs are obtained from a regression equation that omits important predictors in the population model, or adds variables that are not in the model, they will generally be biased estimators of the β in the true population model.

Considering the consequences of mis-specification is important because in non-experimental research, we rarely work with "true" models. In developing explanations, we start with crude, incomplete models, and then attempt to extend and refine them. As we conduct our analyses, questions may arise that lead us to collect more data and perform additional analyses, so that we modify our models in ways that help us focus our thinking about the research question. Although we must be aware of their limitations, regression analyses can play a very useful role in enhancing our understanding, even when the equations we produce are specific and cannot be thought of as representing true models.

In many contexts, the most useful models are not "true" population models. Box (1979, p. 209; see also discussions in Berk, 2004; King, 1991) has stated, "All models are correct, but some are useful." Problems in the social sciences are often too complex to be represented by any specific theory or model, especially one that can be expressed as a single regression equation. Relatively simple models with predictors that capture the essence of a research problem may contribute more to scientific discourse; or have more direct practical applications than cumbersome models even if the larger models are more correct. However, when we work with models that do not match the true underlying population model, we must be aware of how regression coefficients may be affected when variables are left out of, or added to, a regression equation.

# 22.2.1 Omitting Relevant Variables

We pointed out in Chapter 20 that if an important variable in the true population model is omitted from a regression equation and if this omitted variable is correlated with one or more variables that are included in the equation, the coefficients of the variables in the equation will reflect not only the effects of the corresponding predictors, but also the effects of the omitted variable.

Let's illustrate this point in more detail. Suppose that the true model in the population is

```
Y = β012 + βY1,2X1 + βY2,1X2 + ε
```

where we use the notation βY1,2 to emphasize that the coefficient of X1 comes from a model that includes X1 and X2. If we regress Y only on X1, thereby mis-specifying the model by omitting X2 from the regression, we obtain the sample regression equation

```
Ŷ = b01 + bY1,1X1
```

In Appendix 22.1, we show that the expected value of bY1 is not βY1,2, the coefficient of X1 in the true model, but rather βY1,2 + βY2,1β21 = βY1,2 + βY2,2ρ12 σ2/σ1. This expression contains βY1,2 plus an additional term that depends on βY2,1 as well as the regression of X2 on X1, reflecting the fact that if X2 is omitted from the regression, its effects on Y are partially expressed through X1. Although things get more complicated when there are more predictors,