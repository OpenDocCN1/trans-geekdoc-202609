| Variable | Level | Group 1 | Group 2 |
|---|---:|---:|---:|
|  | 1 | 186 (26%) | 371 (53%) |
| Diabetes | 0 | 683 (97%) | 677 (96%) |
|  | 1 | 22 (3.1%) | 25 (3.6%) |
| Ever Smoked | 0 | 492 (70%) | 419 (60%) |
|  | 1 | 213 (30%) | 283 (40%) |
| Past TB Diagnosis | 0 | 613 (87%) | 574 (82%) |
|  | 1 | 92 (13%) | 128 (18%) |
| Male | 0 | 395 (56%) | 275 (39%) |
|  | 1 | 310 (44%) | 427 (61%) |
| < HS Education | 0 | 73 (10%) | 46 (6.6%) |
|  | 1 | 632 (90%) | 656 (93%) |
| Symptoms for Two Weeks | 0 | 258 (37%) | 106 (15%) |
|  | 1 | 447 (63%) | 596 (85%) |
| Number of TB Symptoms | 1 | 427 (61%) | 174 (25%) |
|  | 2 | 181 (26%) | 163 (23%) |
|  | 3 | 67 (9.5%) | 199 (28%) |
|  | 4 | 30 (4.3%) | 166 (24%) |

¹n (%)

# 16.1 Model Selection

Our goal is to predict TB diagnosis. We compare two risk models: a logistic regression model and a lasso logistic regression model. For both of these models, we fit our model on the training data. For the lasso model, we use 5-fold cross-validation to choose the penalty parameter. In the following code, we create a table with the estimated exponentiated coefficients.

```
```r
# fit logistic model
mod_logistic <- glm(tb ~ ., data = tb_train, family = binomial)

# fit lasso model with CV
X_train <- model.matrix(tb~., data = tb_train)[, -1]
y_train <- tb_train[,1]
```
```