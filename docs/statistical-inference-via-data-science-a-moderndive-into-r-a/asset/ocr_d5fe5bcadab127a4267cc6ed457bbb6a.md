# TABLE 5.8: Regression points (first 10 out of 142 countries)

| country | life_exp | continent | life_exp_hat | residual |
| Afghanistan | 53.6 | Asia | 75.0 | -21.300 |
| Albania | 79.5 | Europe | 79.9 | -0.438 |
| Algeria | 78.0 | Africa | 66.3 | 11.720 |
| Andorra | 83.4 | Europe | 79.9 | 3.512 |
| Angola | 62.1 | Africa | 66.3 | -4.200 |
| Antigua and Barbuda | 77.8 | North America | 76.3 | 1.505 |
| Argentina | 78.3 | South America | 75.2 | 3.083 |
| Armenia | 76.1 | Asia | 75.0 | 1.180 |
| Australia | 83.1 | Africa | 74.4 | 8.674 |
| Austria | 82.3 | Europe | 79.9 | 2.362 |

Observe in Table 5.8 life_exp_hat contains the fitted values $\hat{y}$ = life exp. If you look closely, there are only 5 possible values for life_exp_hat. These correspond to the five mean life expectancies for the 5 continents that we displayed in Table 5.7 and computed using the regression coefficient values.

The residual column is $y - \hat{y}$ = life\_exp - life\_exp\_hat. These values can be interpreted as the deviation of a country's life expectancy from its continent's average life expectancy. For example, observe the first row of Table 5.8 corresponding to Afghanistan. The residual of $y - \hat{y} = 53.6 - 74.95 = -21.4$ refers to Afghanistan's life expectancy being 21.4 years lower than the mean life expectancy of all Asian countries. This is partially explained by the years of war that country has suffered.

# Learning check

(LC5.15) Which interpretation is correct for a positive coefficient in a regression model with a categorical explanatory variable?

+   - A. It indicates the baseline group.
- B. It represents the mean value of the baseline group.
- C. The corresponding group has a higher mean than the baseline's.
- D. The corresponding group has a lower response mean than the baseline's.

(LC5.16) Which of the following statements about residuals in regression is true?

+   - A. Residuals are the differences between the fitted and observed response values.
- B. Residuals are always positive.
- C. Residuals are not important for model evaluation.
- D. Residuals are the predicted values in the model.