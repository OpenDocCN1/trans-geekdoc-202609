# 158 6 Multiple Regression

UN_data_ch6 |
select(life_exp, fert_rate, income) |
tidy_summary()

| column | n | type | min | Q1 | mean | median | Q3 | max | sd |
|---|---|---|---|---|---|---|---|---|-|
| life_exp | 182 | numeric | 53.6 | 69.4 | 73.67 | 75.2 | 78.4 | 86.4 | 6.86 |
| fert_rate | 182 | numeric | 0.9 | 1.6 | 2.49 | 2.0 | 3.2 | 6.6 | 1.16 |
| income | 25 | factor | | | | | | | | |
| income | 52 | factor | | | | | | | | |
| income | 56 | factor | | | | | | | | |

Recall that each row in UN_data_ch6 represents a particular country or UN member state. The tidy_summary() function shows a summary for the numerical lives expectancy (life_exp), fertility rate (fert_rate), and the categorical variable group (income). When the variable is numerical, the tidy_summary() function provides the total number of observations in the data frame, the five-number summary, the mean, and the standard deviation.

For example, the first row of our summary refers to life expectancy as life_exp. There are 182 observations for this variable, it is a numerical, and the first quartile, Q1, is 69.4; this means the life expectancy of 25% of the UN member states is less than 69.4. When a variable in a dataset is categorical, also called a factor, the summary shows all the categories or factor levels and the number of observations for each level. For example, income group (income) is a factor with four-level factors: Low income, Lower middle income, Upper middle income, and High income. The summary also provides the number of states for each factor level; observe, for example, that the dataset has 55 UN member states that are considered High Income states.

Furthermore, we can compute the correlation coefficient between our two numerical variables: life_exp and fert_rate. Recall from Subsection 5.1.1 that correlation coefficients only exist between numerical variables. We observe that they are “strongly correlated”.

UN_data_ch6 |
get_correlation(formula = fert_rate ~ life_exp)

```
# A tibble: 1 x 1
cor
<dbl>
1 -0.815
```

We are ready to create data visualizations, the last of our exploratory data analysis. Given that the outcome variable fert_rate and explanatory variable life_exp are both numerical, we can create a scatterplot to display their relationship, as we in