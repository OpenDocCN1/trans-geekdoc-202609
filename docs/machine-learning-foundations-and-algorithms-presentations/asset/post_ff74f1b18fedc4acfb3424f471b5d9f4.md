
# Example: Computation Graph

![](img/f01928df50903c99ce023dd3c527a33d_348_0.png)

# Example: Computation Graph

- * Forward Pass:

![](img/f01928df50903c99ce023dd3c527a33d_349_0.png)

# Example: Computation Graph

- - Backward Pass:

![](img/f01928df50903c99ce023dd3c527a33d_350_0.png)

# Example: Computation Graph

- - Backward Pass:

![](img/f01928df50903c99ce023dd3c527a33d_351_0.png)

# Neural Networks: Practical Course

Machine Learning – Foundations and Algorithms

SS 2024

Ge Li | IAR-ALR

![](img/f01928df50903c99ce023dd3c527a33d_352_0.png)

# Computation graph (example)

## Can we find an algorithm to do it more systematically?

- - The goal isn't to obtain closed-form solutions...
- but to be able to write a program that efficiently computes the derivatives.

We can diagram out the computations using a computation graph:

![](img/f01928df50903c99ce023dd3c527a33d_353_0.png)

- - The nodes represent all the inputs and computed quantities
- The edges represent which nodes are computed directly as a function of which other nodes.

# Computation graph (example)

Computing the loss:
forward pass

Computing the derivative:
backward pass

$z = wx + b$
$y = \sigma(z)$
$\mathcal{L} = \frac{1}{2}(y - t)^2$

![](img/f01928df50903c99ce023dd3c527a33d_354_0.png)

$$\frac{\partial L}{\partial y} = y - t$$
$$\frac{\partial L}{\partial z} = \frac{\partial L}{\partial y}\sigma'(z) \frac{\partial y}{\partial z}$$
$$\frac{\partial L}{\partial w} = \frac{\partial L}{\partial z}x$$
$$\frac{\partial L}{\partial b} = \frac{\partial L}{\partial z} \cdot 1$$

# Computation graph (example)

Lets simplify notation: $\frac{\partial\mathcal{L}}{\partial y}$ (also called error signals)

- Use $\bar{y}$ to denote the derivative - Emphasizes that error signals are just values (rather than mathematical operations)

# Computing the loss:

# Computing the derivative:

- forward pass
- backward pass

![](img/f01928df50903c99ce023dd3c527a33d_355_0.png)

# General computation graphs

**Problem:** what if the computation graph has **fan-out > 1**?

- This requires the multivariate Chain Rule!

# Regularized Regression:

$z = wx + b$
$y = \sigma(z)$
$\mathcal{L} = \frac{1}{2}(y - t)^2$
$\mathcal{R} = \frac{1}{2}w^2$
$\mathcal{L}_{reg} = \mathcal{L} + \lambda\mathcal{R}$

![](img/f01928df50903c99ce023dd3c527a33d_356_0.png)

# Softmax classification:

$z_l = \sum_j w_{lj}x_j + b_l$
$y_k = \frac{\exp(z_k)}{\sum_l \exp(z_l)}$
$\mathcal{L} = -\sum_k t_k \log y_k$

![](img/f01928df50903c99ce023dd3c527a33d_356_1.png)

# Multivariable chain rule

Suppose we have a function $f(x,y)$ and functions $x(t)$ and $y(t)$ (All the variables here are scalar-valued.) Then

$\frac{d}{dt}f(x(t), y(t)) = \frac{\partial f}{\partial x}\frac{dx}{dt} + \frac{\partial f}{\partial y}\frac{dy}{dt}$

![](img/f01928df50903c99ce023dd3c527a33d_357_0.png)

# Example:

# Plug in Chain Rule:

$f(x,y) = y + \exp(xy)$
$x(t) = \cos t$
$y(t) = t^2$

$\frac{d}{dt}f(x(t),y(t)) = \frac{\partial f}{\partial x}\frac{dx}{dt} + \frac{\partial f}{\partial y}\frac{dy}{dt} = (y \exp(xy))(-\sin t) + (1 + x \exp(xy))(2t)$

# Multivariable chain rule

In the context of back-propagation:

![](img/f01928df50903c99ce023dd3c527a33d_358_0.png)

Using our notation:
$$\bar{t} = \bar{x}\frac{dx}{dt} + \bar{y}\frac{dy}{dt}$$

# Backpropagation

Full backpropagation algorithm:

- Let $v_1, \dots, v_N$ be a topological ordering of the computation graph (i.e. parents before children).
- $v_N$ denotes the variable we’re to compute derivatives of (e.g. loss).

![](img/f01928df50903c99ce023dd3c527a33d_359_0.png)

> forward pass
For $i = 1, \dots, N$
Compute $v_i$ as function of $Pa(v_i)$

> backward pass
$\bar{v}_N = 1$
For $i = N - 1, \dots, 1$
$\bar{v}_i = \sum_{j \in Ch(v_i)} \bar{v}_j \frac{\partial v_j}{\partial v_i}$

# Backpropagation

Example: univariate least squares

![](img/f01928df50903c99ce023dd3c527a33d_360_0.png)

**Backward pass:**

$\bar{L}_{reg} = 1$
$\bar{R} = \bar{L}_{reg} \frac{\partial\mathcal{L}}{\partial\mathcal{R}}$
$\bar{z} = \bar{y} \frac{dy}{dz}$
$\bar{L}_{reg} = \bar{y}\sigma'(z)$
$\bar{w} = \bar{z} \frac{\partial z}{\partial w} + \bar{R} \frac{\partial\mathcal{R}}{dw}$
$\bar{L}_{reg} = \bar{L}_{reg} \frac{\partial\mathcal{L}}{\partial\mathcal{L}} = \bar{z}x + \bar{R}w$
$\bar{y} = \bar{L}_{reg} \frac{d\mathcal{L}}{dy}$
$\bar{b} = \bar{z} \frac{\partial z}{\partial b} = \bar{z}$

**Forward pass:**

$z = wx + b$
$y = \sigma(z)$
$\mathcal{L} = \frac{1}{2}(y-t)^2$
$\mathcal{R} = \frac{1}{2}w^2$
$\mathcal{L}_{reg} = \mathcal{L} + \lambda\mathcal{R}$

# Backpropagation

**Example**: Multi-layer Perceptron (multiple outputs)

Backward pass:

![](img/f01928df50903c99ce023dd3c527a33d_361_0.png)

Forward pass:
$$\bar{\mathcal{L}} = 1$$
$$\bar{y}_k = \bar{\mathcal{L}}(y_k - t_k)$$
$$\bar{w}_{ki}^{(2)} = \bar{y}_k h_i$$
$$\bar{b}_k^{(2)} = \bar{y}_k$$
$$\bar{h}_i = \sum_k \bar{y}_k w_{ki}^{(2)}$$
$$\bar{z}_i = \bar{h}_i \sigma'(z_i)$$
$$\bar{w}_{ij}^{(1)} = \bar{z}_i x_j$$
$$\bar{b}_i^{(1)} = \bar{z}_i$$

$$z_i = \sum_j w_{ij}^{(1)}x_j + b_i^{(1)}$$
$$h_i = \sigma(z_i)$$
$$y_k = \sum_k w_{ki}^{(2)}h_i + b_k^{(2)}$$
$$\mathcal{L} = \frac{1}{2} \sum_k (y_k - t_k)^2$$

Can we also do this in **matrix form**?

# Recap: Matrix Calculus

![](img/f01928df50903c99ce023dd3c527a33d_362_0.png)

The computational graph works for matrix and vector too!

As a result:
The gradient of the loss (a scalar) w.r.t. a scalar is a scalar w.r.t. a vector is a vector w.r.t. a matrix is a matrix.

But, to achieve the final results, the back-propagation algorithm needs intermediate calculation of derivatives of:
vector w.r.t vector → a matrix
vector w.r.t matrix → a 3rd-order Tensor

![](img/f01928df50903c99ce023dd3c527a33d_362_1.png)

# Recap: Matrix Calculus

Derivatives of a scalar function w.r.t a vector...

By default, we use column vector representation

- Yields the gradient vector: $\nabla_{\mathbf{x}}f = \frac{\partial f(x)}{\partial \mathbf{x}} = \left[ \frac{\partial f(x)}{\partial \mathbf{x}_1}, \dots, \frac{\partial f(x)}{\partial \mathbf{x}_n} \right]^T$
- Example: Quadratic form $\nabla_{\mathbf{x}}x^T\mathbf{x} = 2\mathbf{x}$

Derivatives of a vector-valued function w.r.t a vector...

- Yields a matrix (the Jacobian $\nabla_{\mathbf{x}}f = \frac{\partial f(x)}{\partial \mathbf{x}} = \begin{bmatrix} \frac{\partial f_1(x)}{\partial \mathbf{x}_1} & \dots & \frac{\partial f_1(x)}{\partial \mathbf{x}_n} \\ \vdots & \vdots & \vdots \\ \frac{\partial f_k(x)}{\partial \mathbf{x}_1} & \dots & \frac{\partial f_k(x)}{\partial \mathbf{x}_n} \end{bmatrix}$
- Example: Linear form $\nabla_{\mathbf{x}}\mathbf{A}\mathbf{x} = \mathbf{A}^T$

# Recap: Matrix Calculus

Derivatives of a scalar function w.r.t a matrix...

- ... is again a matrix $\nabla_W f = \begin{bmatrix} \frac{\partial f(W)}{\partial W_{11}} & \dots & \frac{\partial f(W)}{\partial W_{1d}} \\ \vdots & \vdots & \vdots \\ \frac{\partial f(W)}{\partial W_{k1}} & \dots & \frac{\partial f(W)}{\partial W_{kd}} \end{bmatrix}$

Derivatives of a vector-valued function w.r.t a matrix...

- ... is a 3D tensor! $\nabla_W f = \frac{\partial f(W)}{\partial W} \in \mathcal{R}^{m \times n \times d} \text{ with } f: \mathcal{R}^{m \times n} \to \mathcal{R}^d$

- Why do we need this?
  - Compute derivative w.r.t weight matrix $\frac{\partial Wx+b}{\partial W}$
  - Luckily there will be a simplification of this...

# Chain rule

With vectors:

```
$u = u(x), \frac{\partial g(u)}{\partial x} = \frac{\partial u(x)}{\partial x} \frac{\partial g(u)}{\partial u}$
```

- Note: Swapped order

- Special case (scalar->-> vector -> scalar):

```
$u = u(x), \frac{\partial g(u)}{\partial x} = \frac{\partial u(x)}{\partial x}_{1 \times d} \frac{\partial g(u)}{\partial u}_{d \times 1} = \sum_{i=1}^{d} \frac{\partial u_i(x)}{\partial x} \frac{\partial g(u)}{\partial u_i}$
```
