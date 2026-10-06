![](bbox=[0.198, 0.073, 0.801, 0.235])

For the multiclass problem, we instead let the classifier return a vector-valued function g(x), where

```
$$\begin{aligned} p(y=1|x) &= g_1(x) \ p(y=2|x) &= g_2(x) \ \vdots &= = g(x). \ p(y=M|x) &= g_M(x) \end{aligned}$ (3.27)$
```

In words, each element $g_m(x)$ of g corresponds to the conditional class probability $p(y=m|x)$. Since g models a probability vector, we require that each element $g_m(x) \ge 0$ and $\|g(x)\|_1 = 1$ for any $x$.

# The logistic regression model for binary classification

We will now introduce the logistic regression model, which is one possible viewed as a method of modeling class probabilities. Logistic regression can be viewed as a linearization of the regression model so that it fits the classification (instead of the problem).

We start with binary classification. Wish to learn a function g(x) that approximates the probability of the positive class, see (3.26). To this end, we start with the logistic regression model which, with the noise term, is given by

```
$z = \theta_0 + \theta_1x_1 + \theta_2x_2 + \dots + \theta_px_p = \theta^Tx.$ (3.28)$
```

This is a mapping which takes x and returns z, which in this context is called the *logit*. z takes values on the entire real line, whereas we need a function that returns a value in the interval [0, 1]. The key idea of logistic regression is to 'squeeze' $z$ from (3.28) to the interval [0, 1] by using the logistic function $h(z) = \frac{e^z}{1+e^z}$, see Figure 3.4. This results in

```
$g(x) = \frac{e^z}{1+e^z}.$ (3.29a)$
```

which is restricted to [0, 1] and can be interpreted as a probability. This (3.29a) is the logistic regression model for $p(y=1|x)$.

```
$1-g(x) = 1-\frac{e^z}{1+e^z} = \frac{e^{-z}}{1+e^{-z}}$ (3.29b)$
```

In a nutshell, the logistic regression model is linear regression appended with the logistic function. This is for the reason (somewhat confusing name) but that logistic regression is a method for classification. The reason for why there is no noise term $\varepsilon$ in (3.28), as we had in the linear regression model (3), is that the randomness in classification is statistically modeled by the class probability construction $p(y=m|x)$ of an additive noise $\varepsilon$.