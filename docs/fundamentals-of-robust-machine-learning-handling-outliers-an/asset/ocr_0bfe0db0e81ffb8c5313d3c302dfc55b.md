+   a) Plot the loss function and the gradient function for the dataset $\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}$. Choose values of $\theta$ between 0 and 30.
+   b) What is the value of $\theta$ at the minimum, referred to as $\hat{\theta}^{LS}$.

# 2.4 The $L_1$ loss function for the location problem is given by

$L_1(\theta) = \sum_{i=1}^n |x_i - \theta|.$

The gradient function is

$L'_1(\theta) = -\sum_{i=1}^n \text{sgn}(x_i - \theta).$

+   a) Plot the loss function and the gradient function for the dataset $\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}$. Choose values of $\theta$ between 0 and 10.
+   b) What is the value of $\theta$ at the minimum, referred to as $\hat{\theta}^{LAD}$.

# 2.5 The Huber loss function for the location problem is given by

$H(\theta) = \sum_{i=1}^n \rho_H(x_i - \theta),$

where

$\rho_H(\theta) = \begin{cases} (x_i - \theta)^2 / 2 & \text{if } |(x_i - \theta)| \le \delta \\ \delta(|x_i - \theta| - \frac{\delta}{2}) & \text{if } |(x_i - \theta)| > \delta \end{cases}$

The gradient function is

$H'(\theta) = \sum_{i=1}^n \psi_H(x_i - \theta).$

where

$\psi_H(\theta) = \begin{cases} (x_i - \theta) & \text{if } |(x_i - \theta)| \le \delta \\ -\delta & \text{if } (x_i - \theta) > +\delta \\ +\delta & \text{if } (x_i - \theta) < -\delta \end{cases}$

+   a) Set $\delta = 1$ and plot the functions $\rho_H(\theta)$, $\psi_H(\theta)$ and $\psi'_H(\theta)$ as a function of $r_i = x_i - \theta$. Is the function convex?
+   b) Plot $H(\theta)$ as a function of $\theta$ for the dataset $\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}$. Choose values of $\theta$ between 0 and 10.
+   c) Plot $H'(\theta)$ as a function of $\theta$ for the dataset $\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}$. Choose values of $\theta$ between 0 and 10.
+   d) Compute the Huber estimate of the location parameter $\hat{\theta}^H$ for the dataset $\boldsymbol{x} = \{1, 2, 3, 4, 5, 6, 7, 100\}$.
+   e) Repeat part (d) with $\delta = 10$ and $\delta = 0.1$. Which is the most suitable value of $\delta$ for this dataset among $\delta = 1$, $\delta = 10$, and $\delta = 0.1$.