Advanced Technique: Regularization

proper application of statistical concepts. Online communities such as Kaggle provide complete notebooks with code examples and datasets. There is a wide array of books filled with detailed code on practical data analysis and applied machine learning. As you read through the books, implement and test out the code.

# Communication

Improving your communication skills can be done through regular practice and by asking for feedback. The practice might come through meetings, meetups, seminars, and both formal and informal events. Watch some skilled speakers and observe their habits and delivery. TED talks can be good sources of inspiration. Try to get experience presenting to both technical and non-technical audiences. Take note of the questions that each audience asks, so that you may better prepare in the future.

# 18.2 Advanced Technique: Regularization

One of the biggest risks faced by a machine learning model is overfitting. To mitigate this issue, we learned data splitting as a strategy. In this approach, the model performance is evaluated on a separately held out set of data. This provides an independent assessment of performance that is less likely to overfit the nuances of data.

Another powerful technique to prevent overfitting is regularization. Regularization takes the view that overfitting might be caused by model parameters that are too large. This may happen, for example, when the data sample is small and some of the observations are spurious. If you recall, OLS regression selects parameter estimates that minimize the sum of squared residuals. For a model with $p$ predictors, the loss function looks like:

```
$$SS_{res}(\beta) = \sum_{i=1}^{n}(y_i - (\beta_0 + \beta_1x_{i1} + \dots + \beta_px_{ip}))^2$$
```

To keep the parameter estimates small, regularization introduces a penalty term in this function. Its goal is to shrink the parameters toward zero. There are different penalty terms depending on the regularization technique used, and for implementation we consider Lasso regression. It is worth noting an important feature of Lasso regression: if multiple predictors are highly correlated, only one of them will be included in the model. The remaining predictors will have coefficients of zero. If this effect is not desired, then a different penalty term will be warranted.