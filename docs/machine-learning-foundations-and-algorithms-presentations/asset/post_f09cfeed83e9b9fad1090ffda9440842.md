
# Agenda for Today

Recap: Linear Discriminators

Support Vector Machines:

- Maximum Margin
- Optimization Problem
- Soft-Margin
- Hinge-Loss
- Comparison to Bernoulli likelihood

Basics:

- Sub-gradients

## Binary Classification: Previous Definition

![](img/f01928df50903c99ce023dd3c527a33d_181_0.png)

Given the training data $(x_i, y_i)$, $i = 1\dots N$, with $x_i \in \mathbb{R}^d$ and $y_i \in \{0, 1\}$ , learn a classifier $f(\boldsymbol{x})$ such that:

```
$f(\boldsymbol{x}_i) = \begin{cases} > 0, & \text{if } y_i = 1 \\ < 0, & \text{if } y_i = 0 \end{cases}$
```

## Binary Classification: New Definition

**For SVMs, it simplifies notation to use +1 and -1 as class labels**

**New definition:** Given the training data $(x_i, y_i)$, $i = 1..N$, with $x_i \in \mathbb{R}^d$ and $y_i \in \{-1, 1\}$ learn a classifier $f(x)$ such that:

$f(x_i) = \begin{cases} > 0, & \text{if } y_i = 1 \\ < 0, & \text{if } y_i = -1 \end{cases}$

**Or:** $f(x_i)y_i > 0$ for a correct classification

## Recap: Linear Classifiers

A linear classifier is given in the form:

$f(\mathbf{x}) = \mathbf{w}^T\mathbf{x} + b$

In 2D, the classifier is a line

- $w$ is the normal to the line
- $b$ is the bias

![](img/f01928df50903c99ce023dd3c527a33d_183_0.png)

## Basics: Projections of vectors

The scalar product of 2 vectors can be used to compute the projection of vector a on vector b:

- Geometric definition of scalar product
$a^T b = ||a||||b|\cos\theta$

- Angle between 2 vectors
$\cos\theta = \frac{a^T b}{||a||||b||}$

- Scalar projection of a on b
$a_b = ||a||\cos\theta = \frac{a^T b}{||b||}$

![](img/f01928df50903c99ce023dd3c527a33d_184_0.png)

**Observation:** If 2 vectors are normal to each other, the projection is 0

## Recap: Geometrical inspection

**Observations:**

- The decision boundary is normal to w
- Without b, it goes through the origin

![](img/f01928df50903c99ce023dd3c527a33d_185_0.png)

## Recap: Geometrical inspection

**Observations:**

- **b shifts the decision boundary** along (negative) direction of **w**
- The shift corresponds to adding $\frac{b}{\|\mathbf{w}\|}$ to the projection

$\mathbf{w}^T\mathbf{x} + b = 0 \Rightarrow \frac{\mathbf{w}^T\mathbf{x}}{\|\mathbf{w}\|} + \frac{b}{\|\mathbf{w}\|} = x_w$

- i.e. in order for $\mathbf{x}$ to be on the decision boundary, the projection has to be

$x_w = -\frac{b}{\|\mathbf{w}\|}$

![](img/f01928df50903c99ce023dd3c527a33d_186_0.png)

## Optimal Separation

Which is the optimal line?

![](img/f01928df50903c99ce023dd3c527a33d_187_0.png)

## Maximum Margin

- **Support Vectors:** Data points close to the decision boundary
  - Other examples can be ignored

- **Margin $\rho$ is the distance between the support vectors and the decision boundary

- **Margin should be maximized**
- i.e. minimum distance between decision boundary and examples should be maximized

![](img/f01928df50903c99ce023dd3c527a33d_188_0.png)

## Maximum Margin

- **Maximize distance** between hyper-plane and "difficult examples"
  - Examples next to decision boundary
  - Also called **Support Vectors**

- **Intuition:**
  - Less examples close to decision boundary -> more robust

- **Statistical Learning:**
  - Maximum Margin Classifier has smaller complexity (VC-dimension)
  - And generalizes better

![](img/f01928df50903c99ce023dd3c527a33d_189_0.png)

## Geometric Inspection

Distance between point $\mathbf{x}_i$ and line: $r = \frac{\mathbf{w}^T\mathbf{x}_i+b}{\|\mathbf{w}\|}$

![](img/f01928df50903c99ce023dd3c527a33d_190_0.png)

## Mathematical Formulation

**Observation:**

- $w^T x + b = 0$ and $c(w^T x + b) = 0$ define the same hyperlane
- Scaling $c$ can be chosen freely

Choose scaling such that:

- For positive support vectors $w^T x_+ + b = 1$
- For negative support vectors $w^T x_- + b = -1$

Margin is then given by

$$\frac{w^T x_+ + b - w^T x_- + b}{\|w\|} = \frac{2}{\|w\|}$$

![](img/f01928df50903c99ce023dd3c527a33d191_0.png)

## SVM Optimization

Optimization problem:

```
$\arg\max_w \frac{2}{\|\mathbf{w}\|}$
$\text{s.t.} \quad \mathbf{w}^T\mathbf{x}_i + b \begin{cases} \geq 1, & \text{if } y_i = 1 \\ \leq -1, & \text{if } y_i = -1 \end{cases}$
```

Maximize margin

Condition for margin

**Observations:**

- If the constraints are not satisfied, our definition of the margin would be wrong:
$\min_{\mathbf{x}_+\in\mathbf{x}_+} (\mathbf{w}^T\mathbf{x}_+ + b) = 1 \quad \max_{\mathbf{x}_-\in\mathbf{x}_-} (\mathbf{w}^T\mathbf{x}_- + b) = -1 \quad \mathbf{x}_-: \text{negative examples}$
$\text{Positive support vectors} \quad \mathbf{x}_+: \text{positive examples}$
- Support vectors have the smallest distance to the decision boundary
- There is at least one positive and one negative point that satisfy the support vector condition exactly (i.e. equality) from above
- Why? Because of the argmax! Norm of weight vector could be reduced

## SVM Optimization

Optimization problem:

```
$\arg\max_w \frac{2}{\|\mathbf{w}\|}$
$\text{s.t.} \quad \mathbf{w}^T\mathbf{x}_i + b \begin{cases} \geq 1, & \text{if } y_i = 1 \\ \leq -1, & \text{if } y_i = -1 \end{cases}$
```

Maximize margin

Condition for margin

## Reformulation: Easier to solve, same solution

```
$\arg\min_w \|\mathbf{w}\|^2,$
$\text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \geq 1$
```

- Quadratic optimization problem
- Linear Constraints
- Convex, single optimum

Can be solved with Lagrangian optimization (not important for now...)

# Agenda for Today

Recap: Linear Discriminators

Support Vector Machines:

- Maximum Margin
- Optimization Problem
- Soft-Margin
- Hinge-Loss
- Comparison to Bernoulli likelihood

Basics:

- Sub-gradients

## Back to linear Separability

### What is the best w?

- Linear separable but: small margin

![](img/f01928df50903c99ce023dd3c527a33d_195_0.png)

- Large margin but error in classification

We have to choose a trade-off between margin and classification accuracy!

## Soft Max-Margin

Introduce slack-variables:
$\xi_i \ge 0$

Allows violating the margin conditions
$y_i(w^T x_i + b) \ge 1-\xi_i$

- $0 \le \xi_i \le 1$ sample is between margin and decision boundary: margin violation
- $\xi_i > 1$ sample is on the wrong side of the decision boundary: misclassified

![](img/f01928df50903c99ce023dd3c527a33d_196_0.png)

## Soft Max-Margin

Optimization problem:

$$\text{argmin}_{\mathbf{w},\xi} \quad ||\mathbf{w}||^2 + C\sum_{i}^N \xi_i,$$
$\text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \ge 1-\xi_i, \quad \xi_i \ge 0$$

Punish slack variables

- C is an (inverse) regularization parameter
- Small C: Constraints have little influence -> large margin -> large regularization
- Large C: Constraints have large influence -> small margin -> small regularization
- C infinite: Constraints are enforced -> hard margin -> no regularization

## Illustration

# Hard Margin

# Soft Margin

![](img/f01928df50903c99ce023dd3c527a33d_198_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_198_1.png)

Gerhard Neumann | Machine Learning – Foundations and Algorithms | KIT | SS 2023 22

# Agenda for Today

Recap: Linear Discriminators

Support Vector Machines:

- Maximum Margin
- Optimization Problem
- Soft-Margin
- Hinge-Loss
- Comparison to Bernoulli likelihood

Basics:

- Sub-gradients

## Reformulation into an unconstrained problem

Constrained optimization: Slack variables

```
$\text{argmin}_{\mathbf{w},\xi} \quad ||\mathbf{w}||^2 + C\sum_{i=1}^{N} \xi_i,\quad \text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \geq 1-\xi_i, \quad \xi_i \geq 0$
Regularization parameter
```

SVMs can be reformulated into an unconstrained optimization problem

- Rewrite constraints: $\xi_i \geq 1-y_i(\mathbf{w}^T \mathbf{x}_i + b) = 1-y_i f(\mathbf{x}_i)$
- Together with $\xi_i \geq 0$ this results in $\xi_i = \max(0, 1-y_i f(\mathbf{x}_i))$ (Why?)

Unconstrained optimization (over w):

```
$\text{argmin}_{\mathbf{w}} ||\mathbf{w}\|^2 + C \sum_{i=1}^{N} \max(0, 1-y_i f(\mathbf{x}_i))$
regularization loss function
```
