$=\arg \min_{W} \sum_{i=1}^{n} H(P_i, Q_i)$

Just like logistic regression, we can justify the loss function with MLE as well:

```
$W_{MCLR} = \arg \max_{W} \prod_{i=1}^{n} P(Y_i = y_i)$
$= \arg \max_{W} \prod_{i=1}^{n} \prod_{j=1}^{K} P(Q_i = j)^{y_i[j]}
$= \arg \max_{W} \sum_{i=1}^{n} \sum_{j=1}^{K} y_i[j] \ln P(Q_i = j)$
$= \arg \max_{W} \sum_{i=1}^{n} \sum_{j=1}^{K} y_i[j] \ln \left( \frac{e^{w_j^T x_i}}{\sum_{k=1}^{K} e^{w_k^T x_i}} \right)$
$= \arg \min_{W} \sum_{i=1}^{n} \sum_{j=1}^{K} y_i[j] \ln \left( \frac{\sum_{k=1}^{K} e^{w_k^T x_i}}{e^{w_j^T x_i}} \right)$
```

We conclude that the loss function for logistic regression is

```
$L(W) = -\sum_{i=1}^{n} \sum_{j=1}^{K} y_i[j] \cdot \ln P(Q_i = j)$
```

# 6.10 Training Logistic Regression

The logistic regression loss function has no known actual closed-form solution. Therefore, in order to minimize it, we can use gradient descent, either in batch form or stochastic form. Let's examine the case for batch gradient descent.

# Binary Logistic Regression

Recall the loss function

```
$L(w) = -\sum_{i=1}^{n} y_i \ln p_i + (1 - y_i) \ln(1 - p_i)$
```

where

```
$p_i = s(w^T x_i) = \frac{1}{1 + e^{-w^T x_i}}$
```

```
$\nabla_w L(w) = \nabla_w \left( -\sum_{i=1}^{n} y_i \ln p_i + (1 - y_i) \ln(1 - p_i) \right)$
```