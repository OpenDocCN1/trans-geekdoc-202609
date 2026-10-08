
![](img/c6c76bf52016db7e78a5e30d4766ef81_130_0.png)

Figure 4.9: Objective function, constraints and gradients.

**Figure 4.9** illustrates the quadratic programming problem. The circles are the isolines of $||\mathbf{w}\|^2/2$, that is, lines where it takes a constant value. In the white region, no constraints are satisfied, in the light gray region, one constraint is satisfied, while in the medium gray region, two constraints are satisfied. In the dark gray region, all constraints are satisfied. This is known as the **feasible** set. The minimum value subject to the constraints lies at the point where the gradient of the feasible set is closest to the circles. At this point, the gradient of $||\mathbf{w}\|^2/2$ is a linear combination of the gradients of the active constraints. In the illustration of **Figure 4.9**, these constraints are active and one is inactive.

The **Lagrangian function** combines the objective function and the constraints into one. Its form is given by

```
L(\mathbf{w}, \alpha) = \frac{1}{2}\|\mathbf{w}\|^2 - \sum_{n} \alpha_n (c_n\mathbf{w}^T\mathbf{v}_n - 1),
```

where $\alpha = (\alpha_1, \dots, \alpha_n)^T$ are known as **Lagrange multipliers** which are required to be non-negative. For a particular $\mathbf{w}$, if the constraint $c_n\mathbf{w}^T\mathbf{v}_n - 1 \geq 0$ is satisfied as a strict inequality, it is zero and does not contribute to the sum. If it is satisfied as a strict inequality, we subtract from the objective function, but if it is not satisfied, we add to it. Thus, if $\mathbf{w}$ lies outside the feasible set, it is penalized by increasing the objective function which needs to be minimized.

In **Figure 4.9** the arrows perpendicular to the constraints are the gradients of the constraints multiplied by $\alpha_n$. The dotted lines illustrate that these add to form the gradient vector of the objective function at the constrained minimum.

![](img/c6c76bf52016db7e78a5e30d4766ef81_131_0.png)

Figure 4.10: Weighing the relationships of training samples to a new sample.

The function

$L(\boldsymbol{\alpha})=\min_w L(\mathbf{w}, \boldsymbol{\alpha})$

is the *dual* function of the primal optimization problem. Note that in the feasible set, $L(\boldsymbol{\alpha})$ is always a lower bound of $\|\mathbf{w}\|^2/2$. We find the largest lower bound by maximizing the minimization problem with respect to $\alpha$.

We recover the original minimization problem when the multiplier $\alpha_n$ is zero if the constraint is inactive, and otherwise positive. Formally, this is written as

$\alpha_n(c_n^T\mathbf{v}_n - 1) = 0$.

This property is known as *complementarity*. If this is the case, the maximum lower bound and the constrained minimum are the same. The solution is a stationary point of $L(\mathbf{w}, \boldsymbol{\alpha})$, whose derivatives vanish. Using A.2.1 and A.2.2, the derivative of $L(\mathbf{w}, \boldsymbol{\alpha})$ with respect to $\mathbf{w}$ is

```
$$\frac{d}{d\mathbf{w}}L(\mathbf{w}, \boldsymbol{\alpha}) = \sum_{n=1}^N \alpha_n c_n\mathbf{v}_n.$$
```

Setting this to zero is equivalent to the gradient of the objective function being a linear combination of the gradients of the constraints.

Inserting

```
$$\mathbf{w} = \sum_{n=1}^N \alpha_n c_n\mathbf{v}_n,\quad(4.4)$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_132_0.png)

Figure 4.11: Support Vector Machine Classification.

into the Lagrangian function, we seek $\alpha$ that maximizes the dual function given by

$L(\alpha) = \sum_{n=1}^N \alpha_n - \frac{1}{2}\sum_{i=1}^N\sum_{j=1}^N \alpha_i \alpha_j c_i \mathbf{v}_i^T \mathbf{v}_j,$ subject to the constraints $\alpha_n \geq 0$ and $\alpha_n(\mathbf{w}^T\mathbf{v}_n - 1) = 0, n = 1, \dots, N.$ This is the **dual representation** of the maximum margin problem. The samples for $\alpha_n \neq 0$ in the linear combination to form the weight vector $\mathbf{w}$ are called support vectors. This shaped the name under which the technique is known. Vapnik & Lerner (1963) invented this as the *Generalized Primal Method* refers to the centre of a sphere which contains patterns belonging to a certain class, but no other. That is, it is a representation of this class. Recall that $\mathbf{w} = \sum_{n=1}^N \alpha_n c_n \mathbf{v}_n$. 

Inserting this into (4.4) and (4.5), the bias $b$ is given by the dual maximization problem becomes

$L(\alpha) = \sum_{n=1}^N \alpha_n - \frac{1}{2}\sum_{i=1}^N\sum_{j=1}^N \alpha_i \alpha_j c_i c_j (1 + \mathbf{v}_i^T \mathbf{v}_j).$

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets
from sklearn import svm

n = datasets.load_iris()
# We consider length and width, the first two features.
# Iris setosa in the first 50 entries.
# Iris versicolor in the next 50 entries.

# Create a classification instance of the SVM
s = svm.SVC(kernel="linear", tol=1e-3) # Stopping criterion.
# We consider length and width, the first and second features.
# We train on the entire data.
s.fit(n.data[:100, 0:2], n.target[:100])

# Support vectors:
v = s.support_vectors
# Lagrange multipliers:
lm = s.dual_coef_
# Calculate weight vector.
w = s.coef_

print("Weight vector:", w)
```

Listing 4.3: Support Vector Machine in Python. For MATLAB to go https://github.com/ACFaul/Linear-Classification-Matlab.

Its solution depends solely on the inner product between samples. The classification is according to the sign of

$\mathbf{w}^T \mathbf{v} = \sum_{n=1}^N \alpha_n c_n \mathbf{v}_n^T = \sum_{n=1}^N \alpha_n c_n (1 + \mathbf{v}_n)^T = -b + \mathbf{w}^T\mathbf{v}.$

Again, this only depends on the inner products between the training samples and the new sample weighted by $\alpha_n$. The inner product can be viewed as measuring the relationship between the two samples. Through the multiplication by $c_n$, the inner products from one class are added, and the others are subtracted. Depending on where the samples are (Figure 4.10), the new sample is deemed more related to the samples of one class than the other, and classified accordingly.

Since $c_n$ is only non-zero for the support vectors, it is important how the new sample relates to the support vectors. This is a major advantage of the Support Vector Machine, since it results in a *sparse* model of the classes. Only the support vectors are necessary for future classifications.

We will see the advantages of casing the problem by examining the relationships between samples when considering non-linear classification and the *kernel*. Here the inner product between samples assigns a numeric value to the relationship. The inner product is a counterintuitive measure. For a given fixed sample, samples lying on the line orthogonal to it are given the value zero in this relation. Samples lying on the same side of this line as the given sample are a positive value, while samples on the other side are a negative value. The absolute values increase with the distance from this line. So the numeric value assigned to the relationship increases with the distance.

As we will later, different measures for the relationship can be chosen. Listing 4.3 uses the Support Vector Machine implementation to calculate the support vectors and plot the separation line. The result can be seen in Figure 4.11.

# Exercises

**Exercise 4.1.** How do the formula for the sample mean and covariance of $c_0$ need to be updated, if a new, so far unseen $\mathbf{v}$ arrives? Can a fast learning technique be developed from this?

**Exercise 4.2.** For $\alpha = 1$ and $x^{(1)} = (0,1)^T, x^{(2)} = (1,0)^T$ and $x^{(3)} = (1,-1)^T$ with $c_1=1, c_2=1$ and $c_3=-1$, perform the first iterations of the perceptron until all samples are classified correctly.

**Exercise 4.3.** In the text, the species iris setosa and iris virginica were classified throughout and all samples were used in training. Explore the performance of the algorithms for different pairs of species and smaller sets of data used for training.
