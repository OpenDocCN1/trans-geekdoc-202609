
> — A Tutorial on Bayesian Optimization of Expensive Cost Functions, with Application to Active User Modeling and Hierarchical Reinforcement Learning, 2010.

**Surrogate Function**: Bayesian approximation of the objective function that can be sampled efficiently.

The surrogate function gives us an estimate of the objective function, which can be used to direct future sampling. Sampling involves careful use of the posterior in a function known as the *acquisition* function, e.g. for acquiring more samples. We want to use our belief about the objective function to sample the area of the search space that is most likely to pay off, therefore the acquisition will optimize the conditional probability of locations in the search to generate the next sample.

**Acquisition Function**: Technique by which the posterior is used to select the next sample from the search space.

Once additional samples and their evaluation via the objective function $f()$ have been collected, they are added to data $D$ and the posterior is then updated. This process is repeated until the extrema of the objective function is located, a good enough result is located, or resources are exhausted. The Bayesian Optimization algorithm can be summarized as follows:

1. Select a Sample by Optimizing the Acquisition Function.
2. Evaluate the Sample With the Objective Function.
3. Update the Data and, in turn, the Surrogate Function.
4. Go To 1.

## 19.4 How to Perform Bayesian Optimization

In this section, we will explore how Bayesian Optimization works by developing an implementation from scratch for a simple one-dimensional test function. First, we will define the test problem, then how to model the mapping of inputs to outputs with a surrogate function. Next, we will see how the surrogate function can be searched efficiently with an acquisition function before tying all of these elements together into the Bayesian Optimization procedure.

### 19.4.1 Test Problem

The first step is to define a test problem. We will use a multimodal problem with five peaks, calculated as:

$$ y = x^2 \times \sin(5 \times \pi \times x)^6 \tag{19.5} $$

Where $x$ is a real value in the range $[0,1]$ and $\pi$ is the value of pi. We will augment this function by adding Gaussian noise with a mean of zero and a standard deviation of 0.1. This will mean that the real evaluation will have a positive or negative random value added to it, making the function challenging to optimize. The `objective()` function below implements this.

The complete example of reviewing the test function that we wish to optimize is listed below.

```python
# example of the test problem
from math import sin
from math import pi
from numpy import arange
from numpy import argmax
from numpy.random import normal
from matplotlib import pyplot

# objective function
def objective(x, noise=0.1):
    noise = normal(loc=0, scale=noise)
    return (x**2 * sin(5 * pi * x)**6.0) + noise

# grid-based sample of the domain [0,1]
X = arange(0, 1, 0.01)
# sample the domain without noise
y = [objective(x, 0) for x in X]
# sample the domain with noise
ynoise = [objective(x) for x in X]
# find best result
ix = argmax(y)
print('Optima: x=%.3f, y=%.3f' % (X[ix], y[ix]))
# plot the points with noise
pyplot.scatter(X, ynoise)
# plot the points without noise
pyplot.plot(X, y)
# show the plot
pyplot.show()
```

Listing 19.7: Example plotting samples of the objective function.

Running the example first reports the global optima as an input with the value 0.9 that gives the score 0.81.

```
Optima: x=0.900, y=0.810
```

Listing 19.8: Example output from the optima from sampling the objective function.

A plot is then created showing the noisy evaluation of the samples (dots) and the non-noisy and true shape of the objective function (line). Your specific dots will differ given the stochastic nature of the noisy objective function.

![](img/6ef657cfead7281442f755181c4f6e50_182_0.png)

Figure 19.1: Plot of The Input Samples Evaluated with a Noisy (dots) and Non-Noisy (Line) Objective Function.

Now that we have a test problem, let’s review how to train a surrogate function.

### 19.4.2 Surrogate Function

The surrogate function is a technique used to best approximate the mapping of input examples to an output score. Probabilistically, it summarizes the conditional probability of an objective function ($f$), given the available data ($D$) or $P(f|D)$. A number of techniques can be used for this, although the most popular is to treat the problem as a regression predictive modeling problem with the data representing the input and the score representing the output to the model. This is often best modeled using a random forest or a Gaussian Process. A Gaussian Process, or GP, is a model that constructs a joint probability distribution over the variables, assuming a multivariate Gaussian distribution. As such, it is capable of efficient and effective summarization of a large number of functions and smooth transition as more observations are made available to the model.

This smooth structure and smooth transition to new functions based on data are desirable properties as we sample the domain, and the multivariate Gaussian basis to the model means that an estimate from the model will be a mean of a distribution with a standard deviation; that will be helpful later in the acquisition function. As such, using a GP regression model is often preferred.

We can fit a GP regression model using the GaussianProcessRegressor scikit-learn implementation from a sample of inputs ($X$) and noisy evaluations from the objective function ($y$). First, the model must be defined. An important aspect in defining the GP model is the kernel. This controls the shape of the function at specific points based on distance measures between actual data observations. Many different kernel functions can be used, and some may offer better performance for specific datasets. By default, a Radial Basis Function, or RBF, is used that can work well.

```python
...
# define the model
model = GaussianProcessRegressor()
```

Listing 19.9: Example defining the Gaussian Process model.

Once defined, the model can be fit on the training dataset directly by calling the `fit()` function. The defined model can be fit again at any time with updated data concatenated to the existing data by another call to `fit()`.

```python
...
# fit the model
model.fit(X, y)
```

Listing 19.10: Example fitting the Gaussian Process model.

The model will estimate the cost for one or more samples provided to it. The model is used by calling the `predict()` function. The result for a given sample will be a mean of the distribution at that point. We can also get the standard deviation of the distribution at that point in the function by specifying the argument `return_std=True`; for example:

```python
...
yhat = model.predict(X, return_std=True)
```

Listing 19.11: Example making predictions with the Gaussian Process model.

This function can result in warnings if the distribution is thin at a given point we are interested in sampling. Therefore, we can silence all of the warnings when making a prediction. The `surrogate()` function below takes the fit model and one or more samples and returns the mean and standard deviation estimated costs whilst not printing any warnings.

```python
# surrogate or approximation for the objective function
def surrogate(model, X):
    # catch any warning generated when making a prediction
    with catch_warnings():
        # ignore generated warnings
        simplefilter("ignore")
        return model.predict(X, return_std=True)
```

Listing 19.12: Example of the surrogate function for approximating the objective function.

We can call this function any time to estimate the cost of one or more samples, such as when we want to optimize the acquisition function in the next section. For now, it is interesting to see what the surrogate function looks like across the domain after it is trained on a random sample. We can achieve this by first fitting the GP model on a random sample of 100 data points and their real objective function values with noise. We can then plot a scatter plot of these points. Next, we can perform a grid-based sample across the input domain and estimate
