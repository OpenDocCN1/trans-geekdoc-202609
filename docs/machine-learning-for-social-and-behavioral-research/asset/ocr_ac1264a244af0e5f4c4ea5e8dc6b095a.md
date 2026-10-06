# Ensembles

**TABLE 6.3.** Results from Using LIME to Explain the Predictions from Random Forests with Linear Regression. Only the first two cases, using a maximum of five predictors are given.

| case | model_r2 | model_intercept | model_prediction | feature_value | feature_weight |
| 1 | read | 0.87 | 32.98 | 102.97 | 206.63 | 0.25 |
| 1 | knowledge | 0.87 | 32.98 | 102.97 | 38.15 | 0.27 |
| 1 | math | 0.87 | 32.98 | 102.97 | 1.56 | 1.01 |
| 1 | income | 0.87 | 32.98 | 102.97 | 128000.00 | 0.00 |
| 2 | read | 0.87 | 32.15 | 82.36 | 163.26 | 0.26 |
| 2 | knowledge | 0.87 | 32.15 | 82.36 | 18.73 | 0.27 |
| 2 | math | 0.87 | 32.15 | 82.36 | 19.65 | 0.12 |
| 2 | SES | 0.87 | 32.15 | 82.36 | 0.62 | 1.02 |
| 2 | income | 0.87 | 32.15 | 82.36 | 55800.00 | 0.00 |

# 6.6 Empirical Example

To explain the usage of bagging, random forests, and boosting, we apply all three algorithms to the NSDUH dataset, with all 43 predictors to predict suicidal thoughts (SUICTHNK). The original sample of 55,271, we subset the dataset into a training dataset with 1,000 observations, and a test dataset with 1,000 observations. These two new datasets were created so they have equal proportions of yes and no responses on suicidal thoughts, with the original sample being heavily skewed in favor of responses. We covered the application of machine learning to balanced datasets in Chapter 3, however, our focus here is solely on the application of ensemble algorithms. Nominal features were recorded to dummy coded variables to facilitate the usage of logistic regression (used as a comparison).

We assessed the use of five different methods: logistic regression, bagging, random forests, gradient boosting, and extreme gradient boosting. Logistic regression serves as a baseline approach for comparison to identify nonlinearity and interaction effects when creating a prediction model². For all of the methods, we used 200 bootstrap sampling to calculate AUC, facilitated through the use of the caret package. For both bagging and random forests, we used the RandomForest package (method="rf" in the caret package). Bagging in setting $m$ to the number of predictors (53 with dummy codes). For random forests, we tested values of 3, 10, 20, and 35 for $m$, the number of variables available for partitioning. For each, we used 500 trees. In gradient boosting, we tested the following parameters with the gbm package (method="gbm" in

> ²It would work just well to use a form of regularized logistic regression in this example.