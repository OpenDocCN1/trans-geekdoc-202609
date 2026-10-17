```
mae
#> [1] 119
```

```
mse <- mean((nhanes_df$SBP - pred_y)^2)
mse
#> [1] 14502
```

# 13.6 Stepwise Selection

So far we have ignored the other variables in the data frame. When performing variable selection, there are multiple methods to use. We conclude this chapter by demonstrating how to implement one such method, **stepwise selection**, in R. Chapter 15 expands upon this model selection technique by showing how to implement regularized models in R.

The step() function takes in an initial model along with a direction (“forward”, “backward”, or “both”), and a scope. The scope specifies the lower and upper model formulas to consider. In the following example, we use forward selection so the lower formula is the formula for our current model, and the upper formula contains the other covariates we are considering adding in. These two formulas must be nested, that is, all terms in the lower formula must be contained in the upper formula.

By default, the step() function prints each step in the process and uses AIC to guide its decisions. We can set trace=0 to avoid the print behavior and update the argument k to log(n) to use BIC, where n is the number of observations. In the output, we see that the algorithm first adds in race, then BMI, then income, then education, and then smoking status. In fact, all variables were added to the model! The final output is an lm object that we can use just like the ones earlier in this chapter. We get the summary of the final model and see that the adjusted R-squared has improved to 0.2479.

```
lower_formula <- "log(SBP) ~ log(LEAD) + AGE + SEX:log(LEAD)"
upper_formula <- "log(SBP) ~ log(LEAD) + AGE + SEX:log(LEAD) + SEX +
RACE + EDUCATION + SMOKE + INCOME + BMI_CAT"
mod_step <- step(model_interaction, direction = 'forward',
scope = list(lower = lower_formula,
upper = upper_formula))
#> Start: AIC=-125048
```