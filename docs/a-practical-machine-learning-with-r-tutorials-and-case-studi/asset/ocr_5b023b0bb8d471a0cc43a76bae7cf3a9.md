# 260 9 Deep Learning — MLP Neural Networks Explained

![](bbox=[0.235, 0.175, 0.663, 0.447])

FIGURE 9.8 Plot and Predictions

+   * Neural Networks with many layers and hidden neurons are also prone to overfitting if not accompanied by large datasets (see Section 9.5 for details). Even datasets with hundreds or thousands of observations might not be big enough to avoid overfitting when using large(r) Neural Networks.

There is no rule on how many layers and how many hidden neurons a Neural Network should have. You can start with a reasonable architecture (number of hidden layers and hidden neurons) given the size of your dataset and then tuning to find the best performing Neural Network based on Cross-Validation.

+   * Neural Networks with one hidden layer like in this chapter, perform well to predict linear relationships between multiple predictor variables and one outcome variable. However, other machine learning algorithms such as Random Forest (see Chapter 10) should also be considered since they often perform similar or better.

+   * Neural Networks can also predict linear relationships. However, the β parameters cannot be interpreted as linear OLS models, OLS is better suited to predict linear relationships. It is good practice to first develop a linear model as a benchmark and then evaluate if a Neural Network (or other machine learning model) can outperform it.