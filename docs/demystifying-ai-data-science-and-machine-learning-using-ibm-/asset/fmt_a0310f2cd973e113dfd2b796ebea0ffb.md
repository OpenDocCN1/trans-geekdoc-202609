
## 263. Stepwise Process and Omnibus Tests

Notably, the stepwise process took 14 steps to reach the final model. [Table 7.23](#chapter7.xhtml#tbl7_23) presents the Omnibus test results for all 14 steps, showing whether there is a significant difference between the −2LL of the baseline model and each new model. The results indicate that the Chi-square test is significant (p < 0.05) at each step, confirming that the final model has improved significantly over the baseline model.

### TABLE 7.23 Omnibus Tests of Model Coefficients [Return to text.⏎](#chapter7.xhtml#b7tbl7_23)

| Models | Chi-Square | df | Sig. |
| --- | --- | --- | --- |
| Step 1 | 24,762.613 | 2 | < .001 |
| Step 2 | 4,976.427 | 3 | < .001 |
| Step 3 | 619.043 | 1 | < .001 |
| Step 4 | 428.218 | 1 | < .001 |
| Step 5 | 358.937 | 1 | < .001 |
| Step 6 | 310.529 | 1 | < .001 |
| Step 7 | 81.18 | 2 | < .001 |
| Step 8 | 37.04 | 1 | < .001 |
| Step 9 | 35.013 | 1 | < .001 |
| Step 10 | 32.755 | 1 | < .001 |
| Step 11 | 26.204 | 1 | < .001 |
| Step 12 | 15.521 | 1 | < .001 |
| Step 13 | 9.542 | 1 | 0.002 |
| Step 14 | 71.825 | 51 | 0.029 |

We can also review the Pseudo R² values for the final model as follows:

*   **Cox and Snell R²** = 0.346
*   **Nagelkerke R²** = 0.462

As mentioned earlier, a Pseudo R² value between 0.2 and 0.4 is considered indicative of a good model fit. Therefore, in this case, we have achieved a good fit for the logistic regression model.

Next, we will perform a comprehensive assessment of this model using common classification model fit metrics based on the results of the validation sample. [Table 7.24](#chapter7.xhtml#tbl7_24) presents the results for the champion model, along with an evaluation based on the suggestions from [Chapter 6](#chapter6.xhtml).

### TABLE 7.24 Model Fit Evaluation of the Champion Model—Logistic 1 [Return to text.⏎](#chapter7.xhtml#b7tbl7_24)

| Metrics | Validation Sample | Evaluation |
| --- | --- | --- |
| ACC | 76.80% | Not good |
| MR | 23.20% | Not good |
| Sensitivity or TPR | 0.893 | Good |
| Specificity or TNR | 0.630 | Not good |
| F1 | 0.802 | Acceptable |
| AUC (Area under curve) | 0.833 | Acceptable |
| Gini | 0.667 | Good |

## Model Fit Assessment

### 264. Validation Results Analysis

Based on the validation results, the prediction accuracy seems slightly low at 76.8%, with a misclassification rate (MR) of around 23.2%. However, examining sensitivity and specificity provides more insight. The model demonstrates relatively strong sensitivity at 89.3%, indicating it can effectively predict positive cases (i.e., recommending the airline). On the other hand, specificity is moderate at 63%, suggesting the model struggles to predict negative cases (i.e., not recommending the airline).

The confusion matrix shows that false positives (FP) are higher than false negatives (FN). The F1 score, which balances sensitivity and precision, is 80.2%, which is acceptable. Lastly, the Gini coefficient of 0.667 is considered good.

Overall, while MR and ACC alone may indicate a lower model fit, examining other metrics, such as sensitivity, specificity, F1 score, and Gini coefficient, gives a clearer understanding of the model's performance.

Before making a final conclusion about model fit, we should review the ROC and Lift charts for confirmation. Using the validation sample:

*   The ROC chart ([Figure 7.14](#chapter7.xhtml#fig7_14)) shows that the model lies between the baseline (diagonal line) and the perfect-fit model (upper left corner). With an AUC index of 0.833, the model's performance is acceptable (an ROC index of 0.9 or higher indicates a strong model fit).
*   The Lift chart ([Figure 7.15](#chapter7.xhtml#fig7_15)) shows that with 20% of the dataset, the Lift value is 1.6, meaning the model captures 32% of positive cases (1.6 times more than using no model), which is also considered an acceptable fit.

### Conclusion

These charts confirm the earlier results. If the objective is to predict positive cases (airline recommendations), this model performs well with a sensitivity of 89.3%. However, it does a poorer job of predicting non-recommendations (negatives).

Ultimately, when faced with mixed results, the decision on whether the model is acceptable depends on the business context. Alternatively, further refinements can be made by reconfiguring the algorithm or selecting a different one.

## Logistic Regression Result Interpretation

Assuming the model fit is acceptable, the next step is to interpret the logistic regression results. [Table 7.25](#chapter7.xhtml#tbl7_25) presents the detailed regression results (coefficient values) extracted from the Advanced tab of the model nugget for Logistic 1.

### TABLE 7.25 Coefficient Results of the Champion Model—Logistic 1 [Return to text.⏎](#chapter7.xhtml#b7tbl7_25)

| Fields | B | S.E. | Wald | Df | Sig. | Exp(B) |
| --- | --- | --- | --- | --- | --- | --- |
| Age | −0.013 | 0.001 | 370.319 | 1 | < .001 | 0.987 |
| Price sensitivity | −0.101 | 0.016 | 39.135 | 1 | < .001 | 0.904 |
| Number of years flying | −0.012 | 0.003 | 16.12 | 1 | < .001 | 0.988 |
| Average number of flights per year | −0.012 | 0.001 | 303.08 | 1 | < .001 | 0.988 |
| Number of other loyalty cards | −0.047 | 0.009 | 27.092 | 1 | < .001 | 0.954 |
| Shopping amount at airport | 0.001 | 0 | 9.199 | 1 | 0.002 | 1.001 |
| Departure delay (in minutes) | 0.005 | 0.001 | 34.961 | 1 | < .001 | 1.005 |
| Arrival delay (in minutes) | −0.011 | 0.001 | 161.538 | 1 | < .001 | 0.989 |
| Airline status_t | | | 4,004.021 | 3 | < .001 | |
| Airline status_t(1) | 0.448 | 0.05 | 81.217 | 1 | < .001 | 1.566 |
| Airline status_t(2) | 0.832 | 0.034 | 601.802 | 1 | < .001 | 2.297 |
| Airline status_t(3) | 1.651 | 0.027 | 3,759.086 | 1 | < .001 | 5.213 |
| Gender_t(1) | 0.39 | 0.019 | 417.081 | 1 | < .001 | 1.477 |
| Travel purpose_t | | | 11,450.006 | 2 | < .001 | |
| Travel purpose_t(1) | −0.359 | 0.031 | 133.121 | 1 | < .001 | 0.698 |
| Travel purpose_t(2) | −2.865 | 0.027 | 11,426.678 | 1 | < .001 | 0.057 |
| Passenger class_t | | | 75.68 | 2 | < .001 | |
| Passenger class_t(1) | 0.299 | 0.034 | 75.573 | 1 | < .001 | 1.349 |
| Passenger class_t(2) | 0.037 | 0.031 | 1.414 | 1 | 0.234 | 1.037 |
| Destination state_t | | | 71.538 | 51 | 0.03 | |
| Destination state_t(1) | −0.122 | 1.204 | 0.01 | 1 | 0.919 | 0.885 |
| Destination state_t(2) | 0.047 | 0.828 | 0.003 | 1 | 0.955 | 1.048 |
| … | 0.136 | 0.385 | 0.125 | 1 | 0.724 | 1.146 |
| Flight cancellation_t(1) | −0.435 | 0.072 | 36.316 | 1 | < .001 | 0.647 |
| Constant | 1.451 | 0.058 | 628.038 | 1 | < .001 | 4.269 |

First, we examine the p-values for the Wald Chi-square test. Since these p-values are lower than 0.01, it indicates that the corresponding predictors are significant in predicting the target field, which is the recommendation to use the airline.

### 265. Coefficient Interpretation

The `B` column shows the logistic coefficients, and the `S.E.` column provides the standard errors.

As mentioned earlier, the sign of the `B` coefficient indicates the direction of the effect (positive or negative). For example:

*   **Price sensitivity** has a negative effect on the likelihood of recommending the airline.
*   **Airline status** has a positive effect on the target field.

However, to understand the effect size, we must interpret the results using the odds ratio. In the output, `Exp(B)` represents the odds ratio.
