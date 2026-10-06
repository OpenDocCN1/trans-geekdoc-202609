
# Maximum a-posteriori solution

MAP solution: $\theta_{\text{MAP}} = \arg \max_{\theta} (\log p(\mathcal{D}|\theta) + \log p(\theta))$

- Prior has similar role than a regularization loss

# Example: Regression

- Gaussian likelihood $p(\mathcal{D}|\theta) = p(\mathbf{Y}|\mathbf{X},\theta) = \prod_{i} \mathcal{N}(y_i|f_{\theta}(\mathbf{x}_i), \sigma^2)$
- Gaussian prior $p(\theta) = \mathcal{N}(\theta|\mathbf{0}, \lambda^{-1}I)$
- Corresponding objective: $\arg \max_{\theta} \sum_{i} \frac{1}{2\sigma^2}(y_i - f_{\theta}(\mathbf{x}_i))^2 - \frac{\lambda}{2}\theta^T\theta + c(\sigma^2,\lambda) \text{Sum of squared errors only interested in } \theta$

- Gaussian prior corresponds to a L2 regularization loss!
- Gaussian likelihood corresponds to squared loss!

## MAP for Linear Regression

**Remember:** In linear regression $f_w(\mathbf{x}) = w^T \phi(\mathbf{x})$

**Objective:** $w_{\text{MAP}} = \arg \max_{\mathbf{w}} \sum_{i} -\frac{1}{2\sigma^2}(y_i - \mathbf{w}^T \phi(\mathbf{x}_i))^2 - \frac{\lambda}{2}\mathbf{w}^T \mathbf{w} + c(\sigma^2, \lambda) \text{ only interested in } w$

Sum of squared errors
$=\arg \min_{\mathbf{w}} \sum_{i} (y_i - \mathbf{w}^T \phi(\mathbf{x}_i))^2 + \lambda\sigma^2\mathbf{w}^T \mathbf{w} + c(\sigma^2, \lambda)$

- The **MAP objective** for Linear Regression is equivalent to **Ridge Regression**!
- with $\lambda_{\text{ridge}} = \lambda\sigma^2$

## MAP for Linear Regression

Objective: $w_{MAP} = \arg \min_{w} \sum_{i} (y_i - w^T \phi(x_i))^2 + \lambda\sigma^2 w^T w$

Result: $w_{MAP} = (\mathbf{\Phi}^T \mathbf{\Phi} + \lambda\sigma^2 I)^{-1}\mathbf{\Phi}^T y$

- We have now 2 parameters:
  - $\lambda$ ... sets the importance of the prior
  - $\sigma^2$ ... uncertainty of the training data
- Can be set by optimizing log likelihood + log prior on test set

- Comparison:
- Ridge Regression $w_{Ridge} = (\mathbf{\Phi}^T \mathbf{\Phi} + \lambda I)^{-1}\mathbf{\Phi}^T y$

# Conclusion

- Probabilistic formulation and “optimization view” yield the same algorithms
  - No real benefits as of now
  - Just parameter interpretation differs
- Yet, you can do a lot more starting out with the probabilistic view (second + third part of the lecture)

# Takeaway messages

What have we learned today?

- Refresher on probability theory and maximum likelihood
- Relation between maximum likelihood and least squares
- A probabilistic interpretation of regularization
- There is a strong duality between squared loss functions and Gaussian log-likelihood
  - Squared loss ⇔ Gaussian likelihood
  - L2 regularization ⇔ Gaussian prior

![](img/f01928df50903c99ce023dd3c527a33d_124_0.png)

# Probability Basics and Linear Classification

Machine Learning – Foundations and Algorithms

Prof. Gerhard Neumann
Autonomous Learning Robots
KIT, Institut für Anthropomatik und Robotik

# Learning Outcomes

- Understand the classification problem
- What is a linear classifier?
- What is the loss function of linear classification?
- What is gradient descent?

# Today’s Agenda!

## Linear Classification:

- Generative vs. Discriminative Classification
- Linear Classifiers
- Maximum Likelihood Objective
- Logistic Regression

# Basics: Gradient Descent

# Supervised Learning

Training data includes targets

- Regression:
  - Learn continuous function
  - Example: line

![](img/f01928df50903c99ce023dd3c527a33d_128_0.png)

- Classification:
  - Learn class labels
  - Example: Digit recognition

# Example 1: Image classification

![](img/f01928df50903c99ce023dd3c527a33d_129_0.png)
![](img/f01928df50903c99ce023dd3c527a33d_129_1.png)
![](img/f01928df50903c99ce023dd3c527a33d_129_2.png)
![](img/f01928df50903c99ce023dd3c527a33d_129_3.png)
![](img/f01928df50903c99ce023dd3c527a33d_129_4.png)
![](img/f01928df50903c99ce023dd3c527a33d_129_5.png)

# Example 2: Spam Classification

| Email | Mr. | sale | ... | Spam? |
| :--- | :--- | :--- | :--- | :--- |
| Email 1 | 2 | 1 | | Yes |
| Email 2 | 0 | 1 | | No |
| Email 3 | 1 | 1 | | Yes |
| ... | | | | |
| Email n | 0 | 0 | | No |
| New email | 0 | 1 | | ?? |

# Definition

Given the dataset $\mathcal{D} = \{(\mathbf{x}_i, c_i)\}_{i=1N}$, where $\mathbf{x}_i \in \mathbb{R}^d$ are input samples and $c \in \{1 \dots K\}$ are class labels, we want to learn a classifier $f(\mathbf{x})$ that predicts the class label for unseen samples.

- $K=2$: Binary classification
- $K>2$: Multi-class classification

In difference to regression, the **output is now discrete!**

# Generative vs. discriminative modelling

## Generative

### Generative Models:

- Assume some functional form for class prior $p(c)$ and class densities $p(x|c)$
- Learn prior and densities from data
- This is a "generative" model, as we can create datapoints $x$ using $p(x|c)$
- Predict class label by computing posterior $p(c|x) = \frac{p(x|c)p(c)}{p(x)}$
- Often called Naive Bayes as it uses Bayes rule

![](img/f01928df50903c99ce023dd3c527a33d_132_0.png)

### Learn full distribution of the data (typically very hard)

- Our modelling assumptions, e.g. that $p(x|c)$ is Gaussian, might introduce big errors

### Discriminative Models:

![](img/f01928df50903c99ce023dd3c527a33d_133_0.png)

### Discriminative

![](img/f01928df50903c99ce023dd3c527a33d_133_1.png)

- Directly assume some functional form for $p(c|x)$ (or any other predictor $f(x)$ that returns the class label).
- This is a ‘discriminative’ model of the data!
- Estimate parameters of $p(c|x)$ directly from training data

### Modelling to consider only points on the border

- Typically much simpler than generative modelling
- We therefore concentrate on discriminative models

# (Discriminative) Binary Classification

![](img/f01928df50903c99ce023dd3c527a33d_134_0.png)

Given the training data $(x_i, c_i), i = 1...N$, with $x_i \in \mathbb{R}^d$ and $c_i \in \{0, 1\}$, learn a classifier $f(x)$ such that:

```
$f(x_i) = \begin{cases} > 0, & \text{if } c_i = 1 \\ < 0, & \text{if } c_i = 0 \end{cases}$
```

# Today’s Agenda!

## Linear Classification:

- Generative vs. Discriminative Classification
- Linear Classifiers
- Maximum Likelihood Objective
- Logistic Regression

# Basics: Gradient Descent

# Linear Separability

Linear Separable

![](img/f01928df50903c99ce023dd3c527a33d_136_0.png)

Non-Linear Separable

![](img/f01928df50903c99ce023dd3c527a33d_136_1.png)

# Linear Classifiers

A linear classifier is given in the form:

$f(\mathbf{x}) = \mathbf{w}^T\mathbf{x} + b$

In 2D, the classifier is a line

- $w$ is the normal to the line
- $b$ is the bias shifting the boundary

Lets try to understand why this is the case...

![](img/f01928df50903c99ce023dd3c527a33d_137_0.png)

# Basics: Projections of vectors

The scalar product of 2 vectors can be used to compute the projection of a on b:

- Geometric definition of scalar product
$a^T b = \|a\|\|b\|\cos \theta$

- Angle between 2 vectors
$\cos \theta = \frac{a^T b}{\|a\|\|b\|}$

- Scalar projection of a on b
$a_b = \|a\|\cos \theta = \frac{a^T b}{\|b\|}$

![](img/f01928df50903c99ce023dd3c527a33d_138_0.png)

**Observation:** If 2 vectors are normal to each other, the projection is 0

# Recap: Geometrical inspection

Observations:

- The decision boundary is normal to **w**
- Without b, it goes through the origin

![](img/f01928df50903c99ce023dd3c527a33d_139_0.png)

Gerhard Neumann | Machine Learning | KIT | SS 2024 15

# Recap: Geometrical inspection

**Observations:**

- b shifts the decision boundary along (negative) direction of **w**
- The shift corresponds to adding $\frac{b}{\|\mathbf{w}\|}$ to the projection
- $\frac{\mathbf{w}^T\mathbf{x}}{\|\mathbf{w}\|} + \frac{b}{\|\mathbf{w}\|} = 0$ (projection $x_w$)
- I.e. in order for **x** to be on the decision boundary, the projection has to be $x_w = -\frac{b}{\|\mathbf{w}\|}$
