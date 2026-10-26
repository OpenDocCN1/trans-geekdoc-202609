# 19.4. How to Perform Bayesian Optimization

We can fit a GP regression model using the GaussianProcessRegressor scikit-learn implementation from a sample of inputs ($X$) and noisy evaluations from the objective function ($y$). First, the model must be defined. An important aspect in defining the GP model is the kernel. This controls the shape of the function at specific points based on distance measures between actual data observations. Many different kernel functions can be used, and some may offer better performance for specific datasets. By default, a Radial Basis Function, or RBF, is used that can work well.

```
```python
...
# define the model
model = GaussianProcessRegressor()
```
```

Listing 19.9: Example defining the Gaussian Process model.

Once defined, the model can be fit on the training dataset directly by calling the `fit()` function. The defined model can be fit again at any time with updated data concatenated to the existing data by another call to `fit()`.

```
```python
...
# fit the model
model.fit(X, y)
```
```

Listing 19.10: Example fitting the Gaussian Process model.

The model will estimate the cost for one or more samples provided to it. The model is used by calling the `predict()` function. The result for a given sample will be a mean of the distribution at that point. We can also get the standard deviation of the distribution at that point in the function by specifying the argument `return_std=True`; for example:

```
```python
...
yhat = model.predict(X, return_std=True)
```
```

Listing 19.11: Example making predictions with the Gaussian Process model.

This function can result in warnings if the distribution is thin at a given point we are interested in sampling. Therefore, we can silence all of the warnings when making a prediction. The `surrogate()` function below takes the fit model and one or more samples and returns the mean and standard deviation estimated costs whilst not printing any warnings.

```
```python
# surrogate or approximation for the objective function
def surrogate(model, X):
    # catch any warning generated when making a prediction
    with catch_warnings():
        # ignore generated warnings
        simplefilter("ignore")
        return model.predict(X, return_std=True)
```
```

Listing 19.12: Example of the surrogate function for approximating the objective function.

We can call this function any time to estimate the cost of one or more samples, such as when we want to optimize the acquisition function in the next section. For now, it is interesting to see what the surrogate function looks like across the domain after it is trained on a random sample. We can achieve this by first fitting the GP model on a random sample of 100 data points and their real objective function values with noise. We can then plot a scatter plot of these points. Next, we can perform a grid-based sample across the input domain and estimate