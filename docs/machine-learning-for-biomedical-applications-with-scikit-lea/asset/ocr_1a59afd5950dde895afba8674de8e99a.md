# Machine Learning for Biomedical Applications

![](bbox=[0.125, 0.073, 0.812, 0.245])

Figure 2.9 Bias and variance of a set of models fitted to a set of random samples.

+   - **Bias error**: how much, on average, the predicted target values differ from the true model;
- **Variance error**: how much the predicted target values from models using different samples vary from each other;
- **Noise**: How much the sample target values differ from the true model. As the model complexity increases, the bias error will decrease because the model will be flexible enough to capture the true trends in data. On the other hand, the variance will increase because the increased flexibility of the model also has the potential to overfit to the noise. There is therefore a trade-off between bias and variance, and the optimal model complexity balances both. Noise error is always present in the data and is therefore called irreducible error.

Let’s demonstrate these concepts using our example. We generate 10 different datasets from the true model and fit polynomial models of degree M to each of them. The fitted models are depicted in Fig. 2.9 by the green lines. Next, we can calculate the average of the fitted models, by the red line. The true model is depicted by the black line. Bias error is the root-mean-squared error between the average predicted (red line) and true (black line), and we see that it increases with increasing model complexity, in our case the polynomial degree. Variance error, the average squared difference between the individual models (the green lines) and the average model (the red line), increases with the polynomial degree. The optimal model complexity is achieved when the variance is still low, but the bias has already decreased, such as in the case of second-degree polynomial fit.

# 2.3.5 Training models in scikit-learn

In this section we will show how to train machine learning models in the scikit-learn library on an example of a **univariate polynomial regression**. We will use the simulated artinya dataset described at the beginning of Sect. 2.3 and depicted in Fig. 2.6, top left. We will learn how to:

+   - Split the data into training set and test set;