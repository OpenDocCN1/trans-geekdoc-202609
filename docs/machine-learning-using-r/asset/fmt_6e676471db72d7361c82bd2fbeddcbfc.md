
### Iteration 1
– `ODI_SR_BL`: This builds a model with `ODI_SR_BL` variable removed from the model and retaining all other variables. The AIC value with `ODI_SR_BL` removed from the model is 2700.8. Let us reproduce this AIC value manually using `lm()` method.

![](images/page160-02.png)

### Iteration 1 Continued
– `WKTS`: This builds a model with `WKTS` variable removed from the model and retaining all other variables. The AIC value with `WKTS` removed from the model is 2701.1. We suggest you check this manually by modifying the code chunk above.
– Step 1 is complete after all variables are individually removed and the model is built with the remaining variables.
– The resulting table in iteration 1 has AIC corresponding to each model.
– In this case, we see that the model with `PLAYING_ROLE` excluded from the variable list gives the minimum AIC value (2699.7).

Let’s see Iteration 2.

### Iteration 2
– The AIC for the starting model is 2699.7. This is the model with `PLAYING_ROLE` variable excluded from the model as the starting point.
– ‘none’ category corresponds to a model that would include all variables but `PLAY-ING_ROLE`.
– `ODI_SR_BL`: This builds a model with `ODI_SR_BL` variable removed from the model and retaining all other variables. The AIC value with `ODI_SR_BL` removed from the model is 2697.7. Let us reproduce this AIC value manually.

![](images/page161-01.png)

### Iteration 2 continued
– `WKTS`: This builds a model with `WKTS` variable removed from the model and retaining all other variables. The AIC value with `WKTS` removed from the model is 2698.7. We suggest you check this manually by modifying the code chunk above.
– Iteration 2 is complete after all variables are individually removed and the model is built with the remaining variables.
– The resulting table in Step 2 has AIC corresponding to each model. The model which has the lowest AIC value is picked for the third step.
– In this case, we see that the model with `ODI_SR_BL` excluded from the variable list had the lowest AIC value (2697.7).

The model with the minimum AIC value from the previous step becomes the starting model for the subsequent step every sing time. The logic explained in iteration 1 and iteration 2 follows for iteration 3 as well. So, we go to the last iteration, that is, iteration 4.

### Iteration 4
– The AIC for the starting model is 2696.7. This is the model with `WKTS` variable excluded from the model as the starting point.
– ‘none’ category corresponds to a model that would include all variables except `WKTS`.
– `CAPTAINCY_EXP`: This builds a model with `CAPTAINCY_EXP` variable removed from the model and retaining all other variables. The AIC value with `CAPTAIN-CY_EXP` removed from the model is 2696.8. We suggest you check this manually by modifying the code chunk above.
– Iteration 4 is complete after all variables are individually removed and the model is built with the remaining variables.
– The resulting table in iteration 4 has AIC corresponding to each model. The model which has the lowest AIC value is picked for the next step.
– However, in this case, we see that there is no model with a lower AIC value compared to the initial model (AIC: 2697.7)

Thus, the best model is found at iteration 4. The starting point for `stepAIC()` was a full model and at each step, the model was built using all the variables barring one and the AIC value was calculated for each of these models. The model with the minimum AIC value was selected for the subsequent step.

### 5.9.8 Model Summary
The object `ipl_aic_reg_model` has the final model. The `summary()` of this model object shows some of the statistics saved in it.

![](images/page162-01.png)

From the summary output show, we can infer the following:
The model adjusted *R*-square value is 0.3987, adjusted *R*-square value is calculated by normalizing `SSE` and `SST` by corresponding degrees of freedom. As can be seen from the summary of the `ipl_aic_reg_model` object, the variables retained in the final model are:
**1.** `COUNTRY`
**2.** `ODI_WKTS`
**3.** `ODI_RUNS_S`
**4.** `SIXERS`

However, the point to note is that the variables retained in the model may still have insignificant variables. This is so because `lmstepAIC()` selects the model based on AIC, not *p*-values. The goal is to find the model with the smallest AIC by removing or adding variables in the scope. If AIC has been used for model selection, it is better to consider all the variables retained in the final model even if the *p*-values are greater than 0.05.

One of the parameters which controls the variables’ selection is a penalizing factor which is set by default to 2 (`k` = 2 in the parameter settings of `stepAIC()` in `MASS` package). Since each variable in the model is penalized with a factor of 2, we have some of the variables with *p*-value > 0.05 in the final model. In order to report only the variables with *p*-value < 0.05 in the final model, we have to set the *k* parameter in step function to 3.84 (~ 4). However, this change in the value of *k* is generally not done. The sample code change is given below:

```
ipl_aic_k_3.84_reg_model = train(ipl_train_df[new_predictors], ipl_train_df [response], method = "lmStepAIC", k = 3.84, trControl = obj_control, metric = "Rsquared")
summary(ipl_aic_k_3.84_reg_model$finalModel)
```

### 5.10 Model Diagnostic
It is important to validate the multiple linear regression model to ensure its validity and goodness of fit before it can be used for practical applications. The following measures are used to validate simple linear regression models:
**1.** Co-efficient of determination (R-square).
**2.** Hypothesis test for the regression coefficient.
**3.** Analysis of variance (ANOVA) for overall model validity (relevant more for multiple linear regression).
**4.** Residual analysis to validate regression model assumptions.
**5.** Outlier analysis.

We discussed the above points in simple linear regression. All the validation checks for simple linear regression model metrics hold good for multiple linear regression as well. We can augment the `ipl_train_df` data to add fitted values and residuals by using `augment()` from `broom` package. The resultant data.frame, say `diagnostic_metrics`, contains several metrics useful for model diagnostics. The `plot()` function when used on the regression object model actually uses `diagonstic_metrics` to give various plots useful for residual analysis and outlier analysis.

![](images/page163-01.png)

`.outcome` is the `SOLD_PRICE` in the `ipl_train_df`. The `diagonstic_metrics` also contains all features which are a part of the final model. However, not all the columns and rows are shown in **[Table 5.21](#13_Chapter05.xhtml#tab5.21)** (to maintain readability). The other columns in the `diagonstic_metrics` are as follows:

![](images/page164-01.png)
**1.** `.fitted`: fitted values (predicted values)
**2.** `.resid`: residual errors (`.outcome` - fitted)
**3.** `.hat`: to detect high leverage points (or extreme values in the predictors `X` variables)
**4.** `.cooksd`: Cook’s distance, used to detect influential values, which can be an outlier or a high leverage point. A Cook’s distance of 0.013 for observation *X*[6] suggests that removing this observation from the training data would have changed the predicted value of *Y* by 0.013 (on an average).
**5.** `.std.resid`: Standardized residuals. This is arrived at by dividing residuals by their standard errors. `.std.resid` is used to detect outliers (or extreme values in the outcome *y* variable).

#### 5.10.1 Linearity Assumption
**[Figure 5.4](#13_Chapter05.xhtml#fig5.4)** shows the linearity assumption.

![](images/page164-02.png)

If the red line is approximately horizontal at zero, then the functional form can be assumed to be correctly specified. The presence of a pattern may indicate a problem with some aspect of the linear model.
