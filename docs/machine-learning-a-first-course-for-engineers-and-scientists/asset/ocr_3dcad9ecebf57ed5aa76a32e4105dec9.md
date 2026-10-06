# 3 Basic parametric models and a statistical perspective on learning

![](bbox=[0.127, 0.083, 0.872, 0.313])

The second order polynomial (red line) appears sensible, and with a 2nd order polynomials seems to give some advantage over plain linear regression (blue line, from Example 3.2). However, using a 10th order polynomial (green line) seems to make the model less useful than even linear regression due to overfitting. In conclusion, there is merit to the ideal of polynomial regression, but it has to be applied carefully.

One way to avoid issues with overfitting when augmenting the input with nonlinear transformation is to carefully select which inputs (transforms) to include. There are various strategies for this, by adding instances one at a time (forward) or by starting with a large number of inputs and then gradually reducing the ones that are considered (backward elimination). Different candidate models can be evaluated and compared using cross-validation, as we discuss in Chapter 4. See also Chapter 11 where we discuss input selection.

An alternative approach to implicit selection can also be used to mitigate overfitting regularization. The idea of regularization can be described as 'keeping the parameters θ small unless the data reveals something otherwise', or alternatively 'if a model with small parameter values θ fits the data as well as a model with larger parameter values, the one with small parameter values should be preferred'. There are several ways to implement this mathematically, which leads to a more complete treatment of this in Section 5.3, and only discuss the so-called L² regularization for now. When paired with regularization, the use of nonlinear input transformations can be very powerful and enable firstly supervised learning methods that we will properly introduce and discuss in Chapter 8.

To add an extra term to the cost function using L² regularization, λ ≥ 0 is referred to as the regularization parameter, which is a hyperparameter chosen by the user who controls the strength of the regularization effect. The purpose of the penalty term is to prevent overfitting. The original cost function only rewards large parameter values at the cost of a slightly worse fit. It is important to choose the regularization parameter λ wisely, to obtain the right amount of regularization. With λ = 0 regularization has no effect, as λ ∞ will force all parameters θ to 0. A common approach is to use cross-validation (Chapter 4) to select λ.

If we add L² to the previously studied linear regression model with squared error loss (3.2), the resulting optimization problem becomes⁵

```
\theta = \argmin_{\theta} ||X\theta - y||_2^2 + \lambda|\theta||_2^2.  (3.48)
```

It turns out that, unlike the non-regularized problem, (3.48) has a closed-form solution which is

> ⁵In practice, it can be wise to exclude b₀, the intercept, from regularization.

Draft (April 30, 2021) of Machine Learning - A First Course for Engineers and Scientists. http://mlbook.org

* Andreas Lindholm, Nils Wahlström, Fredrik Lindsten, and Thomas B. Schön. 2021.

5