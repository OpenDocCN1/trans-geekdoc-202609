# 5.3 LEAST SQUARES ESTIMATION

Least Squares Estimation is a fundamental method used in linear regression to find the coefficients that define the best-fitting line or hyperplane to the data. It aims to minimize the sum of the squared differences between the observed dependent variable values and the values predicted by the model. This method is widely used to fit linear models and forms the core of many regression algorithms. Let's delve into how Least Squares Estimation contributes to the machine learning landscape:

**Basic Idea:** Least Squares Estimation seeks to find the coefficients that minimize the sum of squared differences between the observed dependent variable values (Y) and the values predicted by the linear model.

**Residuals:** The residuals are the differences between the observed Y values and the values predicted by the linear model. The goal is to minimize the sum of the squared residuals.

[111]

**Objective Function:** The objective is to find coefficients that minimize the objective function, which is typically the sum of squared residuals: Σ(yᵢ - ŷᵢ)², where yᵢ is the observed Y value and ŷᵢ is the predicted Y value for the i-th data point.

**Matrix Formulation:** In matrix form, the objective is to find the coefficient vector β that minimizes the squared Euclidean norm of the residual vector: ||Y - Xβ||².

**Closed-Form Solution:** In the case of linear regression, the coefficients that minimize the objective function can be found analytically using the closed-form solution: β = (XᵀX)⁻¹XᵀY.

**Gradient Descent:** In more complex regression settings or when dealing with large datasets, gradient-based optimization techniques like gradient descent can be used to iteratively update coefficients and minimize the objective function.

**Regularization:** Regularization techniques like Lasso (L1 regularization) and Ridge (L2 regularization) can be applied to prevent overfitting and control the complexity of the model.

[112]

**Advantages:** Least Squares Estimation provides a straightforward and interpretable way to estimate the coefficients of a linear model. It has a closed-form solution for simple linear regression and is well-understood.