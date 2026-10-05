# Learning check

(LC6.5) Compute the observed response values, fitted values, and residuals for the model without interactions.

(LC6.6) What is the main benefit of visualizing the fitted values and residuals of a multiple regression model?

+   - A. To find errors in the dataset.
- B. To check the assumptions of the regression model, such as linearity and homoscedasticity.
- C. To always improve the model's accuracy.
- D. To increase the complexity of the model.

# 6.2 Two numerical explanatory variables

We now consider regression models with two numerical explanatory variables. To illustrate this situation we explore the ISLR2 package for the first time in this book using its Credit dataset. This dataset contains simulated information for 400 customers. For the regression model we use the credit card balance (Balance) as the response variable; and the credit limit (Limit), and the income (Income) as the numerical explanatory variables.

# 6.2.1 Exploratory data analysis

We load the Credit data frame and to ensure the type of behavior we have become accustomed to using the tidyverse, we also convert this data frame to a tibble using as_tibble(). We construct a new data frame credit_ch with only the variables needed. We do this using the select() verb as we did in Subsection 3.8.1 and, in addition, we save the selecting variables with different names: Balance becomes debt, Limit becomes credit_limit, and Income becomes income:

```
library(ISLR2)
credit_ch6 <- Credit |> as_tibble() |>
select(debt = Balance, credit_limit = Limit,
income = Income, credit_rating = Rating, age = Age)
```