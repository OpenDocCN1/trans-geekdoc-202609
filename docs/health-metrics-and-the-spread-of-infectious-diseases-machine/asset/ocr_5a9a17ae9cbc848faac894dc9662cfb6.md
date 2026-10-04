# Example: Rabies 107

2 2 3 3 3 3 2 2 2 2 2 1 1 1

![](bbox=[0.109, 0.113, 0.823, 0.365])

Figure 7.5 Cross-Validation Optimal Lambda

Then, fitting the final model with the selected best lambda, we can predict and evaluate the model.

```
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