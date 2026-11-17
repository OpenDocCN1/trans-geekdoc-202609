The $L_1$ loss function requires the use of special optimization techniques in the form of linear programming, such as the simplex method (for small datasets) or an interior point method (for large problems). However, the $L_2$ loss can be minimized with gradient descent. This difference is crucial in machine learning since gradient descent techniques are routinely used to minimize convex loss functions, while linear programming is rarely used. Therefore, the $L_1$ loss function is not ideally suited for machine learning applications for this reason, along with a host of other reasons.

With the details of $L_1$ and $L_2$ established, the next step is to explore methods of obtaining a robust estimator that does not have the inherent limitations of the $L_1$ or $L_2$ loss functions but instead exploits the advantages of both. In particular, we will examine the Huber loss function.

# ## 2.10 Huber's Method

One way to create a more effective robust estimator is to try to combine the $L_1$ and $L_2$ loss functions. The advantage of the $L_1$ loss is that it is robust to outliers. The disadvantage is that it has continuity problems in the first and second derivatives, and it requires the use of elaborate methods such as the simplex algorithm or interior point methods to obtain accurate estimates. The $L_2$ loss is continuously differentiable and can be solved using gradient descent but it is highly sensitive to outliers.

# ### 2.10.1 Huber Loss Function

Referring back to Figure 2.5, Huber proposed a method that uses $L_2$ in the vicinity of the origin (where the kink in $L_1$ resides) and then switches to $L_1$ a certain distance away from the origin (see Huber and Ronchetti 2009). The method is quite straightforward. We first define a small interval around the origin given by \([-\delta, +\delta]\). Inside this region, we use the $L_2$ loss function since it does not have a kink. Outside this region, we use the $L_1$ loss but we take great care to match the function and its first derivative at the interface between the different regions. Therefore, the Huber loss term \(\rho_H(r_i)\) and its derivative \(\psi_H(r_i)\) are both continuous in all regions. The resulting Huber loss function is given by

```
\text{Huber loss} = \sum_{i=1}^n \rho_H(y_i - \mathbf{x}_i^\top \boldsymbol{\beta}) = \sum_{i=1}^n \rho_H(r_i), \tag{2.10.1}
```

where the loss term is

```
\rho_H(r_i) = \begin{cases} r_i^2 / 2 & \text{if } |r_i| \le \delta \\ \delta(|r_i| - \frac{\delta}{2}) & \text{if } |r_i| > \delta \end{cases}, \tag{2.10.2}
```

The derivative of the Huber loss function is given by

```
\psi_H(r_i) = \rho_H'(r_i) = \begin{cases} r_i & \text{if } |r_i| \le \delta \\ +\delta & \text{if } r_i > +\delta \\ -\delta & \text{if } r_i < -\delta \end{cases}. \tag{2.10.3}
```

Further, the Huber loss can be used to define the Huber estimator as

```
\hat{\boldsymbol{\beta}}^H = \underset{\boldsymbol{\beta} \in \mathbb{R}^{k+1}}{\text{argmin}} \sum_{i=1}^n \rho_H(y_i - \mathbf{x}_i^\top \boldsymbol{\beta}). \tag{2.10.4}
```