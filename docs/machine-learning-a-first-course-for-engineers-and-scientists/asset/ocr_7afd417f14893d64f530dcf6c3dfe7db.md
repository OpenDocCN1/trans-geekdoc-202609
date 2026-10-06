# #3 Basic parametric models and a statistical perspective on learning

In the previous chapter we introduced the supervised machine learning problem, as well as two methods for solving it. In this chapter we will consider a generic approach to learning referred to as parametric modeling. In particular, we will introduce linear regression and logistic regression which are two such parametric models. The key point of a parametric model is that it contains some parameters $	heta$, which are learned from training data. However, once the parameters are learned, the training data may be discarded, since the prediction only depends on $	heta$.

# ## 3.1 Linear regression

Regression is one of the two fundamental tasks of supervised learning. We will now introduce the linear regression model, which might (at least historically) the most popular method for solving regression problems. Despite its simplicity, it is surprisingly useful and is an important stepping stone for advanced methods, such as deep learning, see Chapter 6.

As discussed in the previous chapter, regression amounts to learning the relationships between input variables $x = [x_1, x_2, \dots, x_p]^T$ and a numerical output $y$. The inputs can be categorical or numerical, but we will be assuming that all $p$ inputs are numerical as well, and discuss categorical inputs later. In a more mathematical framework, regression is learning a model $f$

```
$y = f(x) + \varepsilon, \quad (3.1)$
```

mapping the output, where $\varepsilon$ is an error term that describes everything about the input-output relationship that cannot be captured by the model. With a statistical perspective, we consider $\varepsilon$ as a random variable, referred to as a noise, that is independent of $x$ and has mean value of zero. As a running example we use the car stopping distance regression problem in the previous chapter Example 2.2.

# ## The linear regression model

The linear regression model assumes that the output variable $y$ (a scalar) can be described as an affine combination of the $p$ input variables $x_1, x_2, \dots, x_p$ plus a noise term $\varepsilon$.

```
$y = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_px_p + \varepsilon, \quad (3.2)$
```

We refer to the coefficients $	heta_0, \theta_1, \dots, \theta_p$ as the parameters of the model, and sometimes we refer to $\theta_0$ specifically as the intercept (or offset) term. The noise term $\varepsilon$ accounts for errors in the data not captured by the model. The noise is assumed to have mean zero and to be independent of x. The zero-mean assumption is nonrestrictive, so any (constant) non-zero can be incorporated into the offset term $\theta_0$.

To have a more compact notation, we introduce the parameter vector $\theta = [\theta_0, \theta_1, \dots, \theta_p]^T$ and extend the vector $x$ with a constant in its first position, so that we can write the linear regression model (3.2)

> ^An affine function is a linear function plus a constant offset.