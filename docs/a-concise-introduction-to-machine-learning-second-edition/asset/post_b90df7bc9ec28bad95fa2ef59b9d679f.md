
![](img/c6c76bf52016db7e78a5e30d4766ef81_125_0.png)

(a)

(b)

(c)

![](img/c6c76bf52016db7e78a5e30d4766ef81_125_1.png)

(d)

(e)

(f)

Figure 4.6: Classification using different features.

class means

$\mu = \frac{1}{K} \sum_{i=1}^{K} \mu_i.$

The **between-class scatter** is defined as

$\Sigma_b = \frac{1}{K} \sum_{i=1}^{K} (\mu_i - \bar{\mu})(\mu_i - \bar{\mu})^T$

The separation between classes in the direction of **w** is given

$s(\mathbf{w}) = \frac{\mathbf{w}^T \Sigma_b \mathbf{w}}{\mathbf{w}^T \Sigma_w \mathbf{w}}$

To separate $K$ classes we need to find directions $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ for which $s(\mathbf{w})$ is maximal. This is equivalent to maximizing

$\mathbf{S}(\mathbf{W}) = \frac{[\mathbf{W}^T \Sigma_b \mathbf{W}]}{[\mathbf{W}^T \Sigma_w \mathbf{W}]}$

where $\mathbf{W}$ denotes the matrix whose columns are the vectors $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ and $|\cdot|$ denotes the determinant of the matrix. If the number of features $M$ is greater or equal to the number of classes $K$, it can be shown that $S(\mathbf{W})$ is maximal if $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ are the generalized eigenvectors corresponding to the $K-1$ largest generalized eigenvalues of the generalized eigenvalue problem

$\Sigma_B \mathbf{w} = \lambda \Sigma_W \mathbf{w}.$

This is implemented in MATLAB as `ClassificationDiscriminant.fit`. While `sklearn.discrimin_analysis.LinearDiscriminantAnalysis` is the implementation in Python.

As can be seen in Figure 4.6 some features are more useful than others. We examine this further when discussing feature selection. Where classes overlap, it needs to be considered whether the samples straying into the region of another class are outliers, or whether the classes cannot be separated using these features.

## 4.5 Online Learning and the Perceptron

So far we considered learning tasks where the training data is available upfront. This is known as batch learning or offline learning. In contrast, in online learning the training data becomes available sequentially.

Recall that we seek a direction vector $\mathbf{w}$ and separation threshold $b$ such that for sample $\mathbf{v}$

- $\mathbf{w}^T\mathbf{v} < b \Rightarrow$ $\mathbf{v} \in C_0$,
- $\mathbf{w}^T\mathbf{v} > b \Rightarrow$ $\mathbf{v} \in C_1$.

By extending the vectors $\mathbf{w}$ to $\mathbf{\hat{w}}=\mathbf{w}-b$ and to $\mathbf{\hat{v}}=(1,\mathbf{v})$ this can be rephased to

- $\mathbf{\hat{w}}^T\mathbf{\hat{v}} - b < 0 \Rightarrow$ $\mathbf{\hat{v}} \in C_0$,
- $\mathbf{\hat{w}}^T\mathbf{\hat{v}} - b > 0 \Rightarrow$ $\mathbf{\hat{v}} \in C_1$.

This way the bias $b$ becomes part of the vector of weights.
We define the function

```
sgn(x) = \begin{cases} -1 & \text{if } x < 0 \\ 0 & \text{if } x = 0 \\ 1 & \text{if } x > 0 \end{cases}
```

## Hard Limit

| Input | | Output |
|---|---|---|
| 2 | W, b | 3 |

Figure 4.7: Perceptron.

Then sample $v$

```
$$sgn(w^T v) = -1 \Rightarrow v \in C_0,$$
sgn(w^T v) = 1 \Rightarrow v \in C_1. \quad (4.3)
```

Rosenblatt (1958) invented the perceptron. It was a physical machine for image recognition. It contained 400 photo cells, and the weights were implemented by potentiometers which were updated by electric motors.
Specifically, the perceptron initializes $w_0 = 0$, and updates the weights $w_{i-1}$ with each new training sample $v_i$

```
$$\mathbf{w}_i = \mathbf{w}_{i-1} + (c_i - sgn(\mathbf{w}_{i-1}^T v_i)) \mathbf{v}_i.$$
```

where $c_i$ is the class label of $v_i$, that $c_i = -1$ if $v_i \in C_0$ and $c_i = 1$ if $v_i \in C_1$.
The parameter $0 < \alpha \leq 1$ is the learning rate and is set by the user. If the learning rate is chosen too big, any changes are radical and oscillations occur.
Note that $\mathbf{w}_i$ is the same as $\mathbf{w}_{i-1}$. If the class label was determined incorrectly, the separation line is pulled in direction such that it is more likely that the sample is labelled correctly. The sign of $c_i - sgn(\mathbf{w}_{i-1}^T v_i)$ determines in direction the separation line is pulled. At any stage, the vector of weights, $\mathbf{w}_i$, is a linear combination of samples seen so far.

The perceptron is implemented as a single layer network within the neural framework in MATLAB (Figure 4.7 and Listing 4.2). We take a closer look at neural networks, when considering non-linear classification.
The perceptron needs to see examples for the separation line to set. An epoch is one complete presentation of the data to the algorithm.
Figure 4.8 shows the different separation lines after a certain amount of data has been seen by the perceptron. The unseen data are marked with $\times$. The learning rate is set to 1. Because of this large value, the separation line position changes dramatically between seeing 90% and the complete dataset.
After 100 epochs the perceptron classifies all samples apart from one outlier. It takes several hundred epochs for the perceptron to also classify this sample correctly. Giving a different seed to random number

```
load fisheriris;
# meas contains the first species in rows 1 to 50, the second species
# in rows 51 to 100, and the third species in rows 101 to 150, while
# the columns give the measurements of sepal length, sepal width,
# petal length and petal width in this order.
# Extract two species and two attributes.
m = meas(1:100,1:2);
s = species(1:100);
# Plot data.
figure;
scatter(m(1,:),m(2,:),'rg','s','cs');
hold on;
# Generate binary true/false samples belong to
# class zero, next 50 to class 1
s = zeros(100)+ones(50);
# Generate random permutation matrix, so that the
P = randperm(100);
# Create a random stream.
st = randn(100);
# Permute data.
m = m(P);
PerceptronModel = perceptron;
# Use all samples to divide
s = s(P);
# Set learning rate to 1.
PerceptronModel.trainLr = 1;
# Specify maximum number of epochs.
PerceptronModel.train.epochs = 1000;
# Train the perceptron.
PerceptronModel = train(PerceptronModel,m,s);
# Plot separation line.
w = PerceptronModel.w(1);
b = PerceptronModel.b(1);
h = plot(w,b);\set(h,'Color','k');
# Label graph.
legend('Versicolor','Location','Northeast');
xlabel('Sepal length');
ylabel('Sepal width');
axis({4 7 1.5});
```

Listing 4.2: Perceptron in MATLAB. For Python to go to https://github.com/ACoul/Linear-Classification-Python.

![](img/c6c76bf52016db7e78a5e30d4766ef81_129_0.png)

(a) 70% of data seen.

(b) 80% of data seen.

(c) 90% of data seen.

(d) Complete data seen.

(e) Complete data seen a hundred times.

(f) Convergence.

> Figure 4.8: Perceptron classification (unseen data marked by ×).

generator and changing the order in which the data is presented leads to different separation lines.

## 4.6 Support Vector Machine

Letting the learning rate α be a choice of crude. All should be determined by the data. When all samples are correctly classified, that is $c_n = sgn(\mathbf{w}^T\mathbf{v}_n)$, the $margin$ from the separation line is defined as

```
$\min_{n=1,\dots,N} \frac{\mathbf{w}^T\mathbf{v}_n}{\|\mathbf{w}\|} > 0$
```

The Vector Machine (SVM) tries to maximize the margin between the two classes.

Note that the margin is independent of rescaling of $\mathbf{w}$, since we divide by the length of $\mathbf{w}$. We use the freedom to rescale $\mathbf{w}$ such that $c_n\mathbf{w}^T\mathbf{v}_n - 1 \ge 0$ for $n=1,\dots,N$ with equality for every one sample. Subject to these constraints, maximizing the margin is equivalent to maximizing $|\mathbf{w}\|^{-1}$. Here, the equivalent problem is: *Minimize the objective function* $|\mathbf{w}\|^2/2$ subject to the constraint $c_n\mathbf{w}^T\mathbf{v}_n - 1 \ge 0$ for all $n=1,\dots,N$. This is known as a *quadratic programming problem*. For reasons which will become clear below, this is called the *primal optimization problem*.
