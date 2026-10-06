# 3 Basic parametric models and a statistical perspective on learning

![](bbox=[0.338, 0.076, 0.66, 0.258])

**Figure 3.2:** A graphical explanation of the squared error loss function: the goal is to choose the model (blue line) such that the sum of the squares (light red) of each error $\epsilon$ is minimized. That is, the blue line is be chosen so that the amount of red color is minimized. This motivates the name least squares. The black dots, the training data, are fixed.

# Loss functions and cost functions

A principled way to define the learning problem is to introduce a loss function $L(\hat{y}, y)$ which measures how close the model's prediction $\hat{y}$ is to the observed data $y$. If the model fits the data well, so that $\hat{y} \equiv y$, then the loss function should take a small value, and vice versa. Based on the chosen loss function we also define the *cost function* as the average loss over the training data. Learning a model amounts to finding the parameter values that minimize the cost

```
$$\hat{	heta} = \arg \min_{i=1}^{n} L(\hat{y}(x_i; \theta), y_i). \quad (3.9)$
```

Note that each term in the expression above corresponds to evaluating the loss function for the prediction $\hat{y}(x_i; 	heta)$, given by (3.4), for the training point index $i$ and the true output value $y$ at that point. To emphasize that the prediction depends on the parameters $	heta$, we have included $\hat{y}$ as an argument for $y$ to ensure clarity. The $\arg \min$ means the *value of $	heta$ for which the cost function attains its minimum*. The relationship between loss and cost functions (3.9) is general for all cost functions in this book.

# Least squares and the normal equations

For regression, a commonly used loss function is the *squared error* loss

```
$L(\hat{y}(x; \theta), y) = (\hat{y}(x) - y)^2. \quad (3.10)$
```

This loss function is 0 if $\hat{y}(x) = y$, and grows fast (quadratically) as the difference between $y$ and $\hat{y}(x) = \theta^T x$. The corresponding cost function for the linear regression model (3.7) can be written with matrix notation

```
$J(\theta) = \frac{1}{n} \sum_{i=1}^{n}(\hat{y}(x_i; \theta) - y_i)^2 = \frac{1}{n} ||\hat{y} - y||_2^2 = \frac{1}{n} ||X\theta - y||_2^2. \quad (3.11)$
```

Note that $||\cdot||_2$ denotes the Euclidean vector norm, and $||\cdot||_2^2$ its square. Due to the square, this particular cost function is also commonly referred to as the *least squares* cost. It is illustrated in Figure 3.2. We will discuss other functions in Chapter 5.

Draft (April 30, 2021) of Machine Learning – A First Course for Engineers and Scientists. http://mmlbook.org
And Andreas Linden, Michael Wahlsner, Frederik Strkroth, and Thomas B. Schön. 2021.