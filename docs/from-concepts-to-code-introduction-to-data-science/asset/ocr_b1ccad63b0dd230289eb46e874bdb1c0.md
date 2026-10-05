# 13.3.4 Interpreting the Parameter Estimates

The sklearn package allowed for fitting the model and working with the parameter estimates, but it didn't tell us which estimates, if any, are statistically different from zero. The statsmodels package can fit the same linear regression model and run one-sample t-tests to answer this question. Since we have already done the work of preparing the data, the code is minimal:

```
# import statsmodels
import statsmodels.api as sm

# append column of 1 to design matrix for intercept term
X = sm.add_constant(x_train_s)

# fit the OLS model
results = sm.OLS(y_train, X).fit()

# print the model summary
print(results.summary())
```

Table 13.1 shows the parameter estimate table and confidence intervals indicate that all variables except x5 ('Population') are significant. For x5, the p-value is greater than 0.05, and zero is contained in the 95% confidence interval. The next step would be to drop this variable and refit the model.

TABLE 13.1: Housing Parameter Estimate Table

| coef | std err | t | P >|t| | 0.025 | 0.975 |
|---|---|---|---|---|---||
| const | 2.0601 | 0.007 | 315.640 | 0.000 | 2.047 | 2.073 |
| x1 | 0.8114 | 0.010 | 79.647 | 0.000 | 0.794 | 0.834 |
| x2 | 0.1188 | 0.007 | 16.417 | 0.000 | 0.105 | 0.133 |
| x3 | -0.2601 | 0.020 | -12.777 | 0.000 | -0.300 | -0.220 |
| x4 | 0.3103 | 0.019 | 16.379 | 0.000 | 0.273 | 0.347 |
| x5 | -0.0018 | 0.007 | -0.256 | 0.7998 | -0.015 | 0.012 |
| x6 | -0.0496 | 0.007 | -7.086 | 0.000 | -0.029 | 0.053 |
| x7 | -0.9169 | 0.026 | -46.580 | 0.000 | -0.955 | -0.878 |
| x8 | -0.8893 | 0.019 | -46.003 | 0.000 | -0.927 | -0.851 |

# 13.3.5 Model Performance Evaluation

Since we know the target values from the test set, y_test, we can compare them to our predictions to assess model performance. We will use R² as