
# Example: Rabies 107

2 2 3 3 3 3 2 2 2 2 2 1 1 1

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_125_0.png)

Figure 7.5 Cross-Validation Optimal Lambda

Then, fitting the final model with the selected best lambda, we can predict and evaluate the model.

```r
final_model <- glmnet(predictors,
  response,
  family = "gaussian",
  lambda = best_lambda)

# Predict using the final model
predictions <- predict(final_model,
  # values of the penalty parameter lambda
  s = best_lambda,
  # matrix of new values for x
  newx = predictors
)

# Calculate Mean Squared Error
rmse <- sqrt(mean((response - predictions)^2))
paste("Root Mean Squared Error:", rmse)
# [1] "Root Mean Squared Error: 0.224850403214572"
```

By incorporating glmnet and using lambda selection via cross-validation, we introduce a machine learning—parameter calibration into our analysis. This approach not only in minimising overfitting but also enhances model performance by selecting the most effective regularisation parameter. The cross-validation process used here is crucial for confirming that our model's parameters are optimally tuned for the given data, embodying a key aspect of machine learning methodologies.

## Techniques for Machine Learning Applications

## Predictions vs Truth

## DALYs due to Rabies Predictions vs Truth

by Year

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_126_0.png)

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_126_1.png)

(a) Predictions vs. Truth

(b) Predictions vs. Truth by Year

**Figure 7.6** Predictions vs. Truth

## 7.4.7 Testing Multiple Models

In the example above, we used two models to predict DALYs due to rabies, a random forest with {tidymodels} and a generalised linear model with {glmnet} with a Root Mean-Square Error of 0.448 and 0.257 respectively. The Random Forest model has a higher RMSE, which means it has a higher prediction error compared to the GLM model. However, we haven't applied any of the preprocessing steps, and there are many other models that could be used to predict DALYs as:

- 1. **Support Vector Machines (SVM)**: SVMs are a powerful machine learning algorithm that can be used for both classification and regression tasks. They work by finding the hyperplane that best separates the data into different classes or groups.

- 2. **Extreme Gradient Boosting (XGBoost)**: Known for its high performance in various prediction tasks, XGBoost can handle missing values and is effective for large datasets.

- 3. **K-Nearest Neighbours (KNN)** models are a type of instance-based learning algorithm that stores all available cases and classifies new cases based on a similarity measure.

- 4. **Long Short-Term Memory (LSTM) Networks**: For temporal or sequential health data, LSTM networks can capture dependencies over time, making them suitable for time-series prediction of disease progression and outcomes.

Each of these models has its own strengths and weaknesses, and the choice of model will depend on the specific characteristics of the data and the goals of the analysis. By testing multiple models and comparing their performance, we can identify the best model for the given data and task.

Let's use the {parsnip} package and the {workflow_set()} function to fit a set of models to the rabies data. We will fit a **Support Vector Machine (SVM)**, and a **K-Nearest neighbours (KNN)** model to the data and compare their performance.

```r
linear_reg_spec <-
  linear_reg(penalty = tune(),
    mixture = tune()) %%
```

## Example: Rabies

```r
set_engine("glmnet")
svm_p_spec <-
svm_poly(cost = tune(),
  degree = tune()) %%
set_engine("kernlab") %%
set_mode("regression")
```

```r
knn_spec <-
nearest_neighbor(neighbor = tune(),
  dist_power = tune(),
  weight_func = tune()) %%
set_engine("knkn") %%
set_mode("regression")
```

```r
library(rules)
library(baguette)
# Combine workflows into a workflow set
workflow_set <- workflow_set(preproc = list(scaled = rec1,
  yeo_johnson = rec2),
  models = list(linear_reg = linear_reg_spec,
  svm = svm_p_spec,
  knn = knn_spec))
```

```r
grid_ctrl <- -control_grid(save_pred = TRUE,
  parallel_over = "everything",
  save_workflow = TRUE)
```

```r
# Fit and evaluate the models with hyperparameter tuning
grid_results <- workflow_set %>(seed = 1503)
workflow_map(resamples = folds,
  grid = 5,
  control = grid_ctl)
```

```r
# Show the results
grid_results %>%
collect_metrics() %>%
arrange(mean) %>%
select(1, 5, 7,
```

## Techniques for Machine Learning Applications

```r
autoplot(grid_results,
  metric = "rmse",
  select = "best") +
theme_minimal() +
legend.position = "none")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_128_0.png)

Figure 7.7 Model Performance

The integration of machine learning into our analysis can significantly enhance our understanding of metrics. By following best practices in machine learning, we can

**Best Practices for Machine Learning in Public Health:**

- Conduct exploratory data analysis to understand the structure and relationships between variables.
- Apply feature engineering techniques to create new variables and enhance model performance.
- Select machine learning models that are contextually appropriate and robust for analysis, such as Random Forest and Generalised Linear Models.
- Use parameter calibration techniques such as cross-validation, regularisation, monte carlo, and grid search to optimize models.
- Evaluate model performance using appropriate metrics and visualization tools.

```r
# A tibble: 6 x 4
# workflow_id      mean std_err
# <chr>            <dbl> <dbl>
#1 yeo_johnson_svm 0.148  0.033
#2 yeo_johnson_knn 0.150  0.031
#3 yeo_johnson_reg 0.173  0.027
#4 linear_reg_svm   0.175  0.029
#5 linear_reg_knn  0.178  0.044
#6 linear_reg_reg  0.179  0.043
```

## Essential R Packages for Machine Learning

Learning Objectives

- Gain an overview of essential R packages for modelling and data analysis
- Apply various modelling frameworks using appropriate tools
- Learn how to discover and evaluate new R packages for specific tasks

This chapter provides an overview of the most suitable R-packages for machine learning. It also discusses the combination of packages and functions to achieve the desired results. Additionally, it explores how to find new R-packages and evaluate their suitability.

## 8.1 Inside and Outside of the Library Boxes

When comes to R, the possibilities are endless. With over 15,000 packages available on CRAN (Comprehensive R Archive Network) and countless others on GitHub and other repositories, the universe of available packages is vast. Who to untangle all of them? Which one to choose? Sometimes it is rather favourable to start by working out of the library boxes, which means using functions provided in the built-in packages inside a fresh installation.

However, the vast majority of time, the best way to start is by using the packages that are already available in the R ecosystem. These packages are designed to make your life easier by providing pre-built functions for common tasks.
