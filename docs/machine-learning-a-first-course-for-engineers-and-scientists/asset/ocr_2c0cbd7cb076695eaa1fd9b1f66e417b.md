# 4.4 The bias-variance decomposition of $E_{new}$

We will now introduce decomposition of $E_{new}$ into a squared (bias) and a variance term, as well as an unavoidable component of irreducible noise. This decomposition is somewhat abstract than the training-generalization gap, which provides some additional insights into $E_{new}$ and how different models behave.

Let us make a short reminder of the general concepts of bias and variance. Consider an experiment with an unknown constant $z_0$, which we would like to estimate. For our help in estimating $z_0$ we have a random variable $z$. For example, of $z_0$ as the (true position) of an object, and of $z$ as being noisy GPS measurements of point. Since $z$ is a random variable, it has mean $E[z]$ which we denote by $ar{z}$. We now define

```
Bias: $\hat{z} - z_0$
```

```
Variance: $E[(z - ar{z})^2] = E[(\hat{z} - ar{z})^2]$. (4.12b)
```

The variance describes how much the error varies each time we perform it (the amount of noise in the GPS measurements), the bias describes the systematic error in $z$ that remains no how many times we repeat the experiment (a possible shift or offset in the GPS measurements). If we consider the expected error between $z$ and $z_0$ as a metric of how good the estimator $z$, we can re-write it in terms of variance and the squared bias,

```
$E[(z - z_0)^2] = E[(z - ar{z}) + (ar{z} - z_0)]^2 =
 E[(z - ar{z})^2] + 2E[(z - ar{z})(ar{z} - z_0)] + (ar{z} - z_0)^2$, (4.13)
variance bias
```

In words, the average error between $z$ and $z_0$ is the sum of the squared bias and the variance. A small bias or little variance in the estimator is not enough, but both aspects are important.

We will now apply the bias and variance concept to supervised machine learning setting. For mathematical simplicity we solve the regression problem with the squared error function. The intuition, carries over also to the classification problem. In this setting, $z_0$ corresponds to the true relationship between input and output, and the random variable $z$ corresponds to the model learned from training data. Note that, since the training data collection includes randomness, the model learned from it will be random.

We first make the assumption that the true relationship between x and y can be described by some (possibly complicated) function $f(x) + \epsilon$, with $E[\epsilon] = 0$ and $var(\epsilon) = \sigma^2$.

```
$y = f(x) + \epsilon$, (4.14)
```

In our notation, $\hat{f}(\mathcal{T})$ represents the model when it is trained on data $\mathcal{T}$. This is our random variable, corresponding to $z$ above. We also introduce the average trained model, corresponding to $ar{z}$.

```
$ar{f}(x) 	riangleq E_{\mathcal{T}}[\hat{f}(\mathcal{T})]$, (4.15)
```

As before, $E_{\cdot}$ denotes the expected value over training data points from $p(x, y)$. Thus, $ar{f}(x)$ is the (hypothetical) average model we would achieve, if we re-train the model an infinite number of different training datasets, each one of size $n$, and compute the average. Remember that the definition of $E_{new}$ (for regression with squared error) is

```
$E_{new} = E_{\mathcal{T}} \left[ (\hat{f}(\mathcal{T}) - y^*)^2 ight].$, (4.16)
```

We can change the order of integration and write (4.16) as

```
$E_{new} = E_{\cdot} \left[ E_{\mathcal{T}} (\hat{f}(\mathcal{T}) - f(x_0) - \epsilon)^2 ight]$, (4.17)
```