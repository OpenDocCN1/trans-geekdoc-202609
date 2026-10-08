
# Bibliography

Fisher, R. A. (1936), ‘The Use of Multiple Measurements in Taxonomic Problems’, *Annals of Eugenics* **7**(2), 179–188.

Rosenblatt, F. (1958), ‘The Perceptron: A Probabilistic Model for Information Storage and Organization in the Brain.', *Psychological Review* **65**(6), 386–408.

Vapnik, V. & Lerner, A. (1963), ‘Pattern Recognition using Generalized Portrait Method’, *Automation and Remote Control* **24**, 774–780.

## Non-Linear Classification

So far we assumed that the data can be separated by a straight line. However, this assumption made for linear classification is very restrictive. Before we go into this however, we need to recall the subtle difference between two key concepts: *probability* and *likelihood*. Probability answers the question: How probable is it that a sample of class $C_i$ has these features? Likelihood, on the other hand, answers the question: How likely is it a sample with these features belongs to class $C_i$?

There are $M$ features. Let the features of samples in class $C_i$ be normally distributed with mean $\mu_i$, and variance $\Sigma_i$, $i=0, 1$. Let $\mathbf{v}$ be a feature vector. The probability density of $\mathbf{v}$ given that it is in class $C_i$ is

```
$p(\mathbf{v} \in C_i) = \frac{1}{\sqrt{(2\pi)^M|\Sigma_i|}} \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_i)^T\Sigma_i^{-1}(\mathbf{v}-\mu_i)\right)$
```

The likelihood of $\mathbf{v}$ given that its features is

```
$L(\mathbf{v} \in C_i) = \frac{1}{\sqrt{(2\pi)^M|\Sigma_i|}} \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_i)^T\Sigma_i^{-1}(\mathbf{v}-\mu_i)\right)$
```

It is the same formula, but a different interpretation.

A classifier can be built by assigning $\mathbf{v}$ to class $C_0$ if the likelihood of belonging to $C_0$ is larger than the likelihood of belonging to $C_1$. The boundary between classes is given by

```
$L(\mathbf{v} \in C_0) = L(\mathbf{v} \in C_1)$
```

This is expressed as likelihood ratio

```
$\frac{L(\mathbf{v} \in C_0)}{L(\mathbf{v} \in C_1)} = \frac{\sqrt{(2\pi)^M|\Sigma_1|}}{\sqrt{(2\pi)^M|\Sigma_0|}} \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_0)^T\Sigma_0^{-1}(\mathbf{v}-\mu_0)\right) / \exp\left(-\frac{1}{2}(\mathbf{v}-\mu_1)^T\Sigma_1^{-1}(\mathbf{v}-\mu_1)\right) = 1.$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_137_0.png)

Figure 5.1: Quadratic Discriminant Analysis.

Taking the logarithm, we arrive at

```
$$\mathcal{L}(v \in C_0(v)) = \frac{1}{2}\log|\Sigma_0|-\frac{1}{2}(v-\mu_0)^T\Sigma_0^{-1}(v-\mu_0)$$
$\mathcal{L}(v \in C_1(v)) = \frac{1}{2}(v-\mu_1)^T\Sigma_1^{-1}(v-\mu_1) +\frac{1}{2}(\log|\Sigma_1| + \mu_1^T\Sigma_1^{-1}\mu_1 - \mu_0^T\Sigma_0^{-1}\mu_0)$$
+v^T(\Sigma_0^{-1}-\Sigma_1^{-1}) + \frac{1}{2}v^T(\Sigma_1^{-1}-\Sigma_0^{-1})v = 0.$
```

Thus the boundary between classes is given by a quadratic form of

```
$$\mathbf{A} = \frac{1}{2}(\Sigma_1^{-1}-\Sigma_0^{-1})$$$
$\mathbf{b} = \Sigma_0^{-1}\mu_0-\Sigma_1^{-1}\mu_1$$
$c = \frac{1}{2}\log|\Sigma_0| + \mu_1^T\Sigma_1^{-1}\mu_1 - \mu_0^T\Sigma_0^{-1}\mu_0$$
```

```
$$\mathbf{v}^T\mathbf{A}\mathbf{v} + \mathbf{b}^T\mathbf{v} + c = 0.$$
```

This is the *Quadratic Discriminant Analysis* (QDA). In the special case of two features, the boundaries are conic sections, that is, a line, circle, ellipse, parabola or hyperbola. Listing 5.1 applies the Quadratic Discriminant Analysis to Fisher’s iris data and the result can be seen in Figure 5.1.

```matlab
load fisher;
% extract attributes
pl = mean(iris,:3); % petal length
pw = mean(iris,:4); % petal width
figure
h1 = scatter(pl,pw,iris(:,5),'os');
legend('Setosa', 'Versicolor', 'Virginica', 'Location')
hold on
X = [pl,pw];
cls = Discriminantfit(X,species,'quadratic');
% plot the classification boundaries
% retrieve the coefficients for the quadratic boundary between
% the first and second class (setosa and versicolor)
C = cls.Coefs(1,2).Const;
l1 = cls.Coefs(1,2).Linear;
q = cls.Coefs(1,2).Quadratic;
% plot the curve
f = @(x1,x2) c + [x1,x2]*l1 + [x1,x2]'*q + q(1,1)*x1.^2 + ...
(q(1,1)*x1.^2+q(1,2)*x1*x2+q(2,2)*x2.^2 = 0
h2 = plot(f,.9 1 0, 'k');
% retrieve the coefficients for the quadratic boundary between
% the second and third class (versicolor and virginica).
C = cls.Coefs(2,3).Const;
l2 = cls.Coefs(2,3).Linear;
q = cls.Coefs(2,3).Quadratic;
% plot the curve
f = @(x1,x2) c + [x1,x2]*l2 + [x1,x2]'*q + q(1,1)*x1.^2 + ...
(q(1,1)*x1.^2+q(1,2)*x1*x2+q(2,2)*x2.^2 = 0
h3 = plot(f,.5 7 2 5, 'k');
xlabel('Petal length');
ylabel('Petal width');
axis([0.8 7 0])
title('');
```

Listing 5.1: Quadratic Discriminant Analysis in MATLAB For Python go https://github.com/Faul/Non-Linear-Classification.

Recall that we arrived at the Linear Discriminant Analysis by assuming $\Sigma_0 = \Sigma$. In this case,

```
$$\begin{aligned} \mathbf{A} &= 0, \\ \mathbf{b} &= \Sigma^{-1}(\mu_0 - \mu_1), \\ \mathbf{c} &= \frac{1}{2}(\mu_0^T\Sigma^{-1}\mu_1 - \mu_0^T\Sigma^{-1}\mu_0) \end{aligned}$$
```

This is the equation of the line in the Linear Discriminant Analysis. In this section, we look at the Quadratic Discriminant Analysis from a different angle by introducing artificial features and extending the feature space this way.

## 5.2 Kernel Trick

In the quadratic

```
$$\mathbf{v}^T\mathbf{A}\mathbf{v} + \mathbf{v}^T\mathbf{b} + c = 0$$
```

the matrix $\mathbf{A}$ is symmetric, as $\mathbf{A}$ is the difference of covariance matrices which are symmetric. Assuming $M=2$ and writing

```
$$\mathbf{A} = \begin{pmatrix} A_{11} & A_{12} \\ A_{12} & A_{22} \end{pmatrix}, \mathbf{b} = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}$$
```

the boundary equation can be written as

```
$$A_{11}v_1^2 + 2A_{12}v_1v_2 + A_{22}v_2^2 + b_1v_1 + b_2v_2 + c = 0$$
```

Now we can rearrange this as

```
$$\begin{pmatrix} A_{11} & A_{12} & A_{22} & b_1 & b_2 \end{pmatrix} \begin{pmatrix} v_1^2 \\ v_2^2 \end{pmatrix} + c = 0$$
```

Let $\mathbf{w}^T = \begin{pmatrix} A_{11} & A_{12} & A_{22} & b_1 & b_2 \end{pmatrix}$ and $\mathbf{v} = \begin{pmatrix} v_1^2 \\ v_2^2 \\ v_1 \\ v_2 \end{pmatrix}$, this describes a linear boundary in a five-dimensional feature space.

```
$$\mathbf{w}^T\mathbf{v} + c = 0$$
```

In other words, we have augmented the feature space by three artificial features

```
$$v_1^2, v_2^2, v_1$$
```

![](img/c6c76bf52016db7e78a5e30d4766ef81_140_0.png)

Figure 5.2: Linearly inseparable data and their transformation to a higher dimensional space.
