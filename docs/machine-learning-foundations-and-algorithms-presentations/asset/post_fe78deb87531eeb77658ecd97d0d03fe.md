
## 10. Motion Planning via Variational Inference
Supervisor: Denis Blessing, Onur Celik

Motivation:

- Motion Planning: Generate trajectory to reach a goal position
- What if we don't have expert data to learn from but instead access to a cost function?
- Use variational inference (VI) + movement primitives!

![](img/f01928df50903c99ce023dd3c527a33d_59_0.png)

Praktikum:

- Extend existing prior work with movement primitives
- Design different tasks (contextual and non-contextual)
- Benchmark state-of-the-art methods on your tasks

## Thesis

Interested in a Master-Thesis or Bachelor Thesis?

- Have a look at https://alr.anthropomatik.kit.edu/
- Cutting edge research in RL, imitation learning and machine learning fundamentals
- Topics spanning from applied RL on challenging robot tasks to fundamental machine learning problems and theory
- Use real robot hardware and realistic physics simulators
- Write and publish a paper 🙂

![](img/f01928df50903c99ce023dd3c527a33d_60_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_60_1.png)

We are also hiring Hiwis :)

![](img/f01928df50903c99ce023dd3c527a33d_60_2.png)

## The end...

- Any further questions?

## Linear Methods for Regression

Machine Learning – Foundations and Algorithms

Prof. Gerhard Neumann

Autonomous Learning Robots

KIT, Institut für Anthroposphatik und Robotik

![](img/f01928df50903c99ce023dd3c527a33d_62_0.png)

## Announcements

- Date for the exam: Fr. 27.9, 08:00 bis 10:00
- First exercise will be released on today or tomorrow

## Learning Outcomes

- Understand the regression problem
- What do we mean with “linear representation”?
- Be able to derive the least squares solution
- What is regularization in regression?
- How to extend linear regression to non-linear functions?
- Understand a probabilistic interpretation of linear regression using maximum likelihood
- Understand the probabilistic interpretation of regularization

## Supervised Learning - Regression

Training data includes targets

- Today: Regression
- Learn continuous function
- Example: line

![](img/f01928df50903c99ce023dd3c527a33d_65_0.png)

- Next Lecture: Classification
- Learn class labels
- Example: Digit recognition

![](img/f01928df50903c99ce023dd3c527a33d_65_1.png)

## Today’s Agenda!

### Linear Regression

- Recap on Matrices and Matrix Calculus
- Least-Squares Solution
- Generalized Linear Regression Models
- Regularization - Ridge Regression

### Probabilistic Formulation

- Probability basics and Maximum Likelihood Estimates (MLE)
- MLE for linear regression models
- Regularization - Maximum a-posteriori estimates

## Linear Regression

- Recap on Matrices and Matrix Calculus
- Regression Objective and Derivation
- Generalized Linear Regression Models
- Regularization - Ridge Regression

## Matrices in Machine Learning

- In many cases, our data set can be represented as matrix, where single samples are vectors
  Joe: $x_1 = \begin{bmatrix} 37 \\ 72 \\ 175 \end{bmatrix}$ Mary: $x_2 = \begin{bmatrix} 10 \\ 30 \\ 61 \end{bmatrix}$ Carol: $x_3 = \begin{bmatrix} 25 \\ 65 \\ 121 \end{bmatrix}$ Brad: $x_4 = \begin{bmatrix} 66 \\ 67 \\ 175 \end{bmatrix}$

- Most typical representation:
  - Each row represent a data sample (e.g. Joe)
  - Each column represents a data entry (e.g. feature)
  $X = \begin{bmatrix} 37 & 10 & 25 & 66 \\ 72 & 30 & 65 & 67 \\ 175 & 61 & 121 & 175 \end{bmatrix}$ $X$ is samples $\times$ entries matrix

## Notation

- Scalar: $x \in \mathbb{R}$
- Vector: $x \in \mathbb{R}^m$
- Matrix: $X \in \mathbb{R}^{n \times m}$

## Multiplication of a matrix with a matrix

- Dimensions: $m \times n \cdot n \times j = m \times j$ $\overbrace{W} \cdot \overbrace{V}$
- Number of columns of left matrix must match number of rows of right matrix
- Non-commutative (in general): $VW \neq WV$
- Associative: $V(WX) = (VW)X$
- Transpose Product: $(VW)^T = V^T W^T$

## Important special case

- Scalar (Inner) product: $\mathbf{w}^T \mathbf{v} = [w_1, \dots, w_n] \begin{bmatrix} v_1 \\ \vdots \\ v_n \end{bmatrix} = w_1v_1 + \cdots + w_nv_n = \langle \mathbf{w}, \mathbf{v} \rangle$
- The scalar product can be written as vector-vector product

## Calculus

We also need to talk about derivatives...

“The derivative of a function of a real variable **the sensitivity to change of a quantity** (a function value or dependent variable) is determined by another quantity (the independent variable)” (Wikipedia)

![](img/f01928df50903c99ce023dd3c527a33d_72_0.png)

Function: $f(x)$

Derivative: $\frac{\partial f(x)}{\partial x}$

Minimum/Maximum: $\frac{\partial f(x)}{\partial x} = 0$

## Matrix Calculus - Denominator-layout notation

Derivatives of a scalar function w.r.t a vector...

- Yields the gradient vector: $\nabla_{\mathbf{x}}f = \begin{bmatrix} \frac{\partial f(x)}{\partial x_1} \\ \vdots \\ \frac{\partial f(x)}{\partial x_d} \end{bmatrix}$
- Example: Quadratic form $\nabla_{\mathbf{x}}\mathbf{x}^T \mathbf{x} = 2\mathbf{x}$

Derivatives of a vector-valued function w.r.t a scalar...

- Yields a matrix (the Jacobian) $\nabla_{\mathbf{x}}\mathbf{f} = \begin{bmatrix} \frac{\partial f_1(\mathbf{x})}{\partial x} & \dots & \frac{\partial f_k(\mathbf{x})}{\partial x} \end{bmatrix}$
- Example: Linear form $\nabla_{\mathbf{x}}\mathbf{a} = \mathbf{a}^T$

## Matrix Calculus - Denominator-layout notation

Derivatives of a vector-valued function w.r.t a vector...

- Yields a matrix (the Jacobian) $\nabla_x f = \frac{\partial f(x)}{\partial x} = \begin{bmatrix} \frac{\partial f_1(x)}{\partial x_1} & \dots & \frac{\partial f_k(x)}{\partial x_1} \\ \vdots & \ddots & \vdots \\ \frac{\partial f_1(x)}{\partial x_d} & \dots & \frac{\partial f_k(x)}{\partial x_d} \end{bmatrix}$
- Example: Linear form $\nabla_x Ax = A^T$

## Matrix Calculus

Derivatives of a scalar function w.r.t a matrix...

- ... is again a matrix $\nabla_{\mathbf{W}} f = \begin{bmatrix} \frac{\partial f(\mathbf{W})}{\partial W_{11}} & \dots & \frac{\partial f(\mathbf{W})}{\partial W_{1d}} \\ \vdots & \ddots & \vdots \\ \frac{\partial f(\mathbf{W})}{\partial W_{k1}} & \dots & \frac{\partial f(\mathbf{W})}{\partial W_{kd}} \end{bmatrix}$

Derivatives of a vector-valued function w.r.t a matrix...

- ... is a 3D tensor!
- So that gets a bit tricky... luckily we (almost) do not need that

## Matrix Calculus

We need to know some rules from **Matrix Calculus** (see wikipedia)

| | scalar | vector | matrix |
| --- | --- | --- | --- |
| **Linear:** | $\frac{\partial ax}{\partial x} = a$ | $\nabla_x Ax = \mathbf{A}^T$ | $\nabla_x a^Tb = ab^T$ |
| **Quadratic:** | $\frac{\partial x^2}{\partial x} = 2x$ | $\nabla_x x^T Ax = (\mathbf{A}^T + \mathbf{A})x = 2\mathbf{Ax}$ if $\mathbf{A}$ is symmetric | |

**Reference:** https://en.wikipedia.org/wiki/Matrix_calculus

## Linear Regression

- Recap on Matrices and Matrix Calculus
- Regression Objective and Derivation
- Generalized Linear Regression Models
- Regularization - Ridge Regression

## Regression

# Regression:

- Learn continuous function

$y = f(x) + \epsilon$

# Linear Regression:

- “just” fit a line

$y = f(x) + \epsilon = w_0 + w_1x + \epsilon$

We assume that the outputs are affected by (typically) Gaussian noise:

$\epsilon \sim \mathcal{N}(0, 1)$

## Objective of Regression

We want to minimize the summed (or mean) squared error
$$SSE = \sum_{i=1}^{N} (y_i - f(\boldsymbol{x}_i))^2$$

- ... where the input **x** is a d-dimensional vector

## Why do we use the squared error?

- It is fully differentiable
- Easy to optimize
- It also makes sense as it can be shown that:

$$f^*(boldsymbol{x}) = \text{argmin}_{f(\boldsymbol{x})}SSE \Rightarrow f^*(boldsymbol{x}) = \mathbb{E}[y|\boldsymbol{x}]$$

- Hence, we always estimate the mean of the target function!
