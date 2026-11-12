MLE for a dice roll is given by the following:

{1, 1, 6, 3, 2, 5, 4, 3}

t(n, k) = 1, if we rolled K on the nth roll as follows:

t(1, 1) = 1
t(2, 1) = 1
t(3, 6) = 1

PMF of categorical distributions is as follows:

L = \prod_{n=1}^N \prod_{k=1}^6 w_k^{t_{nk}} (3.11)
L = \prod_{n=1}^N \prod_{K=1}^6 w_k y_{nk} t_{nk}

Categorical cross-entropy loss is given by the following:

L = \sum_{n=1}^N \sum_{k=1}^k t_{nk} \log y_{nk} (3.12)
Loss = - \sum_{k=1}^k t_k \log y_k (3.13)

For (1, 1)

Loss = (-1) \log(1) = 0

For (1, 0.5)

Loss = (-1) \log(0.5) = 0.65

For (1, 0.25)

Loss = (-1) \log(0.25) = 1.356

For (1, 0)

Loss = (-1) \log(0) = \infty

# Gradient descent for linear regression

A problem is said to be a regression problem when the input variable is continuous or has real value. For example, weight, the salary of an employee, and so on.

Linear regression is a type of regression that fits information with the best suitable hyper-plane. It is defined as a linear approach for modeling the relationship between independent and dependent variables. Figure 3.21 shows the pattern obtained in linear regression: