# Detecting Breast Cancer

More generally, the same term in the numerator and denominator yields a multiplicative factor of 1.

Also recall the following property of exponentials:

$exp(a + b) = exp(a)exp(b)$

This allows for writing simple factors in the numerator and denominator, which can cancel. Returning to the odds ratio, the equation becomes

```
$p(X_A)/(1-p(X_A)) = exp(\beta_0 + \beta_1(v+1) + \beta_2w)\n$p(X_B)/(1-p(X_B)) = exp(\beta_0 + \beta_1v + \beta_2w)\n$= exp(\beta_0) \times exp(\beta_1(v+1)) \times exp(\beta_2w)\n$= exp(\beta_0) \times exp(\beta_1v) \times exp(\beta_2w)\n$= exp(\beta_1)$
```

The odds ratio has a very simple form and interpretation: increasing the value of predictor $j$ by one unit will multiply the odds of the event by factor $exp(\beta_j)$. Returning to the parameter estimate table, the coefficient on $x1$ is $1.1042$. Increasing $x1$ by one unit will multiply the odds of malignancy by a factor of $e^{1.1042} = 3.017$.

To understand the parameter estimate if the odds will increase, decrease, or remain unchanged, we can consider the case where the value is zero. In this case, $e^0 = 1$, which means that the odds are multiplied by a factor of one (it is unchanged). A positive parameter estimate will increase the odds of the odds of the event.

# 14.2.2 Revisiting Gradient Descent

Fitting the model with packages, we found the parameter estimates to be

```
$[-20.7540, 1.1042, 0.2289]$
```

Let's see if gradient descent produces a similar result. We will set a relatively small alpha and a large number of iterations:

```
betas, 11 = gradient_descent_logistic(x_tr,
y_tr,
alpha=1e-4,
n_iter=2e6)
```