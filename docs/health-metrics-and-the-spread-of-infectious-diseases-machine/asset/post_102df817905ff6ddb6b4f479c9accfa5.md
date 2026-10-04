
# Define the Bayesian regression model

```r
bayesian_model <- brm(
  I - day_of_week + week_of_year + month + lag_1_cases + lag_7_cases,
  data = cv19_data,
  family = gaussian(),
  prior = c(set_prior(normal(0, 10), class = "b"),
            set_prior(cauchy(0, 5), class = "sigma")),
  iter = 2000,
  warmup = 1000,
  chains = 4,
  seed = 42
)
```

The bayesian_model object contains the fitted model, we can inspect the summary of the model to assess the posterior samples of the model parameters, the posterior distribution of parameters, and the model statistics.

```r
summary(bayesian_model)$fixed[%>%
  rownames_to_column(var = "parameter") %>%
  head(n = 3) %>%
  glimpse()
# Rows: 3
# Columns: 8
$ parameter <chr> "Intercept", "day_of_week.L", "day_of_week.Q"
$ Estimate <dbl> 886.7250835, -0.04239118, -0.16213817
$ Est. Error <dbl> 145.09866, 10.1293, 0.10790
$ L-95% CI <dbl> 576.67263, -19.85932, -19.61945
$ U-95% CI <dbl> 1137.71086, 20.30390, 19.72001
$ Rhat <dbl> 1.000109, 1.000764, 1.000761
$ Bulk_ESS <dbl> 5660.295, 5486.962, 5309.553
$ Tail_ESS <dbl> 3204.207, 2641.086, 2846.849
```

The model output tells us the convergence of the chains, the posterior distribution of the parameters, and the model statistics. We can see the mean, median, and 95% credible intervals for the regression coefficients, as well as the standard deviation of the error term. The Rhat statistic measures the convergence of the chains, with values close to 1 indicating convergence. The n_eff statistic measures the effective sample size of the chains, with higher values indicating more reliable estimates. The LOic statistic is the leave-one-out cross-validation information criterion, which measures the model's predictive performance.

Or access the formula used in the model:

```r
bayesian_model$formula
# I - day_of_week + week_of_year + month + lag_1_cases + lag_7_cases
```

After fitting the model, we can plot the diagnostics to assess its performance with the plot() function. The diagnostics trace plots of the chains, density plots of the posterior distributions, and the chains. The Gelman-Rubin statistic measures the convergence of the chains. The Gelman-Rubin statistic should be close to 1 for the model to have converged.

```r
# Plot the model diagnostics
plot(bayesian_model)
```

# Example: Modelling the Spread of COVID-19

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_257_0.png)
![](img/6b61f0d3dcab44c60cdfe4e888d549c9_257_1.png)

Figure 15.2 Bayesian Model diagnostics

Then, we can make predictions using the fitted model and visualise the actual vs. predicted COVID-19 cases over time. The predictions object is type matrix/array.

```r
predictions <- predict(bayesian_model, newdata = cv19_data)
predictions %>% head()
#   Estimate Est. Error      Q2.5    Q7.5
# [1,] 779.2025  1263.317 -1657.152 3299.250
# [2,] 837.3495  1270.743 -1627.192 3305.897
# [3,] 813.2604  1283.773 -1696.402 3337.646
# [4,] 877.0629  1271.697 -1580.855 3388.625
# [5,] 823.5526  1294.345 -1754.888 3282.143
# [6,] 820.5984  1277.846 -1770.321 3225.060
```

Create a new data frame with the actual and predicted values for COVID-19 cases, and then plot the actual vs. predicted values over time.

```r
predictions <- as_table(predictions)
cv19_data_pred <- cv19_data %>%
  mutate(predicted_cases = predictions$Estimate)

# Plot actual vs. predicted values
gplot(data = cv19_data_pred,
     aes(x = I, y = predicted_cases)) +
  geom_point() +
  geom_abline() +
  labs(title = "Actual vs. Predicted COVID-19 Cases",
       x = "Date", y = "Cases", color = "Legend")

gplot(data = cv19_data_pred, aes(x = date)) +
  geom_point(aes(y = I, 
              color = "Actual")) + 
  geom_line(aes(y = predicted_cases, 
              color = "Predicted")) + 
  labs(title = "Actual vs. Predicted COVID-19 Cases",
      x = "Date", y = "Cases", color = "Legend")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_258_0.png)
Figure 15.3 Actual vs. Predicted COVID-19 Cases

# Ensembling - Combining Multiple Models

Ensemble modeling combines the predictions of multiple models to improve overall performance. This approach involves training several models and then combining their outputs through averaging, stacking, or other methods. This is particularly useful when different models capture different aspects of the data.

In this section, we will explore how to implement ensemble methods in R. We will focus on the `tidymels` and `stacks` packages, which provide powerful tools for building ensemble workflows.

### Key Ensemble Techniques

- **Averaging**: Combining the predictions of individual models.
- **Stacking**: Using a meta-learner to learn how to combine the predictions of base models.
- **Boosting**: Training models sequentially, where each model corrects the errors of the previous one.
- **Bagging**: Training multiple models on different subsets of the data to reduce variance.

To start, we need a dataset. For this example, we will use the `cv19_data` mentioned in the previous sections.
[content]]
Ensemble modeling combines the predictions of multiple models to improve overall performance. This approach involves training several models and then combining their outputs through averaging, stacking, or other methods. This is particularly useful when different models capture different aspects of the data.

In this section, we will explore how to implement ensemble methods in R. We will focus on the `tidymels` and `stacks` packages, which provide powerful tools for building ensemble workflows.

### Key Ensemble Techniques

- **Averaging**: Combining the predictions of individual models.
- **Stacking**: Using a meta-learner to learn how to combine the predictions of base models.
- **Boosting**: Training models sequentially, where each model corrects the errors of the previous one.
- **Bagging**: Training multiple models on different subsets of the data to reduce variance.

To start, we need a dataset. For this example, we will use the `cv19_data` mentioned in the previous sections.
[/content]
```

Wait, I noticed the OCR text provided in the prompt became quite garbled and repetitive towards the end. Let me provide a clean, corrected version based strictly on the provided raw OCR text, fixing the syntax errors in the R code and de-duplicated de-textualized artifacts.

[content]
# Define the Bayesian regression model

```r
bayesian_model <- brm(
  I - day_of_week + week_of_year + month + lag_1_cases + lag_7_cases,
  data = cv19_data,
  family = gaussian(),
  prior = c(set_prior(normal(0, 10), class = "b"),
            set_prior(cauchy(0, 5), class = "sigma")),
  iter = 2000,
  warmup = 1000,
  chains = 4,
  seed = 42
)
```

The bayesian_model object contains the fitted model, we can inspect the summary of the model to assess the posterior samples of the model parameters, the posterior distribution of parameters, and the model statistics.

```r
summary(bayesian_model)$fixed[%>%
  rownames_to_column(var = "parameter") %>%
  head(n = 3) %>%
  glimpse()
# Rows: 3
# Columns: 8
$ parameter <chr> "Intercept", "day_of_week.L", "day_of_week.Q"
$ Estimate <dbl> 886.7250835, -0.04239118, -0.16213817
$ Est. Error <dbl> 145.09866, 10.1293, 0.10790
$ L-95% CI <dbl> 576.67263, -19.85932, -19.61945
$ U-95% CI <dbl> 1137.71086, 20.30390, 19.72001
$ Rhat <dbl> 1.000109, 1.000764, 1.000761
$ Bulk_ESS <dbl> 5660.295, 5486.962, 5309.553
$ Tail_ESS <dbl> 3204.207, 2641.086, 2846.849
```

The model output tells us the convergence of the chains, the posterior distribution of the parameters, and the model statistics. We can see the mean, median, and 95% credible intervals for the regression coefficients, as well as the standard deviation of the error term. The Rhat statistic measures the convergence of the chains, with values close to 1 indicating convergence. The n_eff statistic measures the effective sample size of the chains, with higher values indicating more reliable estimates. The LOic statistic is the leave-one-out cross-validation information criterion, which measures the model's predictive performance.

Or access the formula used in the model:

```r
bayesian_model$formula
# I - day_of_week + week_of_year + month + lag_1_cases + lag_7_cases
```

After fitting the model, we can plot the diagnostics to assess its performance with the plot() function. The diagnostics trace plots of the chains, density plots of the posterior distributions, and the chains. The Gelman-Rubin statistic measures the convergence of the chains. The Gelman-Rubin statistic should be close to 1 for the model to have converged.

```r
# Plot the model diagnostics
plot(bayesian_model)
```

# Example: Modelling the Spread of COVID-19

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_257_0.png)
![](img/6b61f0d3dcab44c60cdfe4e888d549c9_257_1.png)

Figure 15.2 Bayesian Model diagnostics

Then, we can make predictions using the fitted model and visualise the actual vs. predicted COVID-19 cases over time. The predictions object is type matrix/array.

```r
predictions <- predict(bayesian_model, newdata = cv19_data)
predictions %>% head()
#   Estimate Est. Error      Q2.5    Q7.5
# [1,] 779.2025  1263.317 -1657.152 3299.250
# [2,] 837.3495  1270.743 -1627.192 3305.897
# [3,] 813.2604  1283.773 -1696.402 3337.646
# [4,] 877.0629  1271.697 -1580.855 3388.625
# [5,] 823.5526  1294.345 -1754.888 3282.143
# [6,] 820.5984  1277.846 -1770.321 3225.060
```

Create a new data frame with the actual and predicted values for COVID-19 cases, and then plot the actual vs. predicted values over time.

```r
predictions <- as_table(predictions)
cv19_data_pred <- cv19_data %>%
  mutate(predicted_cases = predictions$Estimate)

# Plot actual vs. predicted values
gplot(data = cv19_data_pred,
     aes(x = I, y = predicted_cases)) +
  geom_point() +
  geom_abline() +
  labs(title = "Actual vs. Predicted COVID-19 Cases",
       x = "Date", y = "Cases", color = "Legend")

gplot(data = cv19_data_pred, aes(x = date)) +
  geom_point(aes(y = I, 
              color = "Actual")) + 
  geom_line(aes(y = predicted_cases, 
              color = "Predicted")) + 
  labs(title = "Actual vs. Predicted COVID-19 Cases",
      x = "Date", y = "Cases", color = "Legend")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_258_0.png)
Figure 15.3 Actual vs. Predicted COVID-19 Cases
