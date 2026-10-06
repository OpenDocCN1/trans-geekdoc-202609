
# CHAPTER 3

## Regression

In Chap. 2 we have seen examples of univariate linear regression (Sect. 2.2.1) and univariate polynomial regression (Sect. 2.3). The word **univariate** refers to having only a single feature to predict the target values. In machine learning problems, we often wish to combine multiple features to achieve more accurate predictions. Regression that involves multiple features is called **multivariate**.

In this chapter we will demonstrate various multivariate regression models using the example of **predicting the age of preterm babies from volumes of brain structures** calculated from MRI scans, see Fig. 3.1. The dataset consists of brain volume calculated from 164 MRI scans of preterm babies between 27 and 45 weeks GA gathered by the Developing Human Connectome Project [13,29]. We will have a detailed look at the algorithms for the segmentation of brain structures in Chap. 6. We will first describe the multivariate linear regression (Sect. 3.1). Next, we will show how we prevent overfitting using regularization (Sect. 3.2). Finally, we will look at nonlinear multivariate regression (Sect. 3.3).

### 3.1. Regression basics

In this section we will look at a basic regression technique called multivariate regression. First, we describe this regression model in detail (Sect. 3.1.1), and then explain how we train it (Sect. 3.1.2), and finally we investigate its performance in Sect. 3.1.3.

### 3.1.1 Multivariate linear regression

**Multivariate linear regression model** is defined as

```
$\hat{y} = w_0 + w_1x_1 + \dots + w_Dx_D,$
```

where $x = (x_1, \dots, x_D)^T$ is a feature vector, weight vector $w = (w_0, w_1, \dots, w_D)^T$ forms parameters of the model, and $\hat{y}$ is a predicted target value.

We wish to fit the model (find the weight vector **w**) to $N$ training samples $x_i = (X_{i1}, \dots, X_{iD})$ with associated target values $y_i$, where $i = 1, \dots, N$. This can be done by minimizing the loss function that measures a **sum of squared errors between** and predicted target values

![](img/d219b4c20ff50f4b97845dec7a9acecb_86_0.png)

**Figure 3.1** Brain volumes for predicting the age of preterm babies from MRI scans. Left: whole brain volume as a single feature; middle: six main structures; right: detailed segmentation resulting in 86 features.

```
$L(w) = \frac{1}{2}\sum_{i=1}^{N}(y_i - \hat{y}_i)^2, \quad (3.1)$
```

where

$\hat{y}_i = w_0 + w_1x_1 + ... + w_Dx_i$.

In our biomedical example, each sample denoted by index $i$ is a brain MRI scan, and the feature vector $\mathbf{x}_i$ is composed of volumes of brain structures calculated from that scan. Each feature, denoted by index $k$, represents a volume of a particular brain structure, and the target value $y_i$ is the true GA of the baby at the time of the scan.

#### Matrix representation

Next, we will construct a feature matrix for regression. Note that we have $D$ features but $D+1$ weights. The weight $w_0$ is not multiplied by a feature and is often called a **bias** or **intercept**. In order to simplify the equations, we will define a new feature $x_0 = 1$. The model will simplify to

```
$\hat{y} = \sum_{k=0}^{D} w_kx_k$.
```

Construction of a feature matrix is described in Sect. 2.1.3. If we add the feature $x_0$, the feature matrix will become

```
$$\mathbf{X} = \begin{pmatrix} x_{11} & \dots & x_{1D} \\ \vdots & \ddots & \vdots \\ x_{N1} & \dots & x_{ND} \end{pmatrix}. \quad (3.2)$$
```

Recollect that in Sect. 2.1.3 we defined the target vector $\mathbf{y} = (y'_1, \dots, y'_N)^T$. We can now also define a **predicted target vector $\hat{\mathbf{y}} = (\hat{y}_1, \dots, \hat{y}_N)^T$** in a matrix as

```
$$\hat{\mathbf{y}} = \mathbf{X}\mathbf{w}. \quad (3.3)$$
```

The sum of squared errors loss (Eq. (3.1)) can be expressed

```
$$L(\mathbf{w}) = \frac{1}{2}(\mathbf{y} - \hat{\mathbf{y}})^T(\mathbf{y} - \hat{\mathbf{y}}). \quad (3.4)$$
```

Substituting $\hat{\mathbf{y}}$ according to Eq. (3.3) results in

```
$$L(\mathbf{w}) = \frac{1}{2}(\mathbf{y} - \hat{\mathbf{y}})^T(\mathbf{y} - \hat{\mathbf{y}}). \quad (3.5)$$
```

### 3.1.2 Training regression models

#### Normal equation

The solution $\hat{\mathbf{w}}$ that minimizes the loss given in Eq. (3.5) can be found analytically using

```
$$\hat{\mathbf{w}} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y} \quad (3.6)$$
```

and is called the **normal equation**. It can be used if the $D+1 \times D+1$ square matrix $\mathbf{X}^T\mathbf{X}$ is invertible. We will discuss this condition in more detail in Sect. 3.1.3. Scikit-learn implements multivariate linear regression as the `Regression` object, which we have demonstrated in Sect. 2.2.1 and 2.3.

#### Gradient descent

If the number of features $D$ is very large, matrix inversion is impractical, and numerical algorithms, such as **gradient descent**, can be employed. In this case the solution $\hat{\mathbf{w}}$ can be found iteratively by

```
$$\hat{\mathbf{w}}^{(n+1)} = \hat{\mathbf{w}}^{(n)} + \eta\mathbf{X}^T(\mathbf{y} - \mathbf{X}\hat{\mathbf{w}}^{(n)}). \quad (3.7)$$
```

where $n$ is the iteration number, and $\eta$ is a learning rate that needs to be set correctly to converge, as demonstrated in Fig. 3.2. The gradient descent (GD) algorithm that uses all the samples at each iteration is **batch GD**. If there is a very large number of samples $N$, each GD iteration might be very slow to execute. To solve this problem, we can instead use one random sample per iteration, and such an algorithm is called **stochastic GD**. Obviously, this would be very fast, but the solution might become unstable. A good compromise is the **mini-batch GD**, where we use a small subset (mini-batch) of training samples at each iteration. Comparison of these three types of GD is presented in Fig. 3.3.

![](img/d219b4c20ff50f4b97845dec7a9acecb_88.png)

**Figure 3.2** Influence of the learning rate on gradient descent. Using normal equation; green square is the initial estimate of $w^{(0)}$; blue circles are estimates $w^{(n)}$ at each iteration. When learning rate is correct, the algorithm converges to the correct solution. If the learning rate is too small, the algorithm will need many iterations to reach the correct solution. If the learning rate is too large, the algorithm will oscillate rather than converge.

![](img/d219b4c20ff50f4b97845dec7a9acecb_88_1.png)

**Figure 3.3** Comparison of convergence properties of batch, stochastic, and mini-batch gradient descents.

#### Derivation of the normal equation

We will now have an in-depth look at the normal equation (Eq. (3.6)). The solution $\hat{\mathbf{w}}$ will be the minimum of the loss function $L(\mathbf{w})$. It is therefore necessary that the first derivative at the minimum is:

```
$\frac{\partial L(\mathbf{w})}{\partial \mathbf{w}} = 0$
```

To calculate the first derivative of Eq. (3.5), we will first use the product rule and then simplify the expression:

```
$\frac{\partial L(\mathbf{w})}{\partial \mathbf{w}} = \frac{\partial \frac{1}{2}(\mathbf{y}-\mathbf{Xw})^T(\mathbf{y}-\mathbf{Xw})}{\partial \mathbf{w}} = \frac{1}{2}(\mathbf{y}-\mathbf{Xw})^T(-\mathbf{X}) + \frac{1}{2}(-\mathbf{X})^T(\mathbf{y}-\mathbf{Xw}) = -\mathbf{X}^T(\mathbf{y}-\mathbf{Xw})$
```

We can now set the first derivative to zero and find the expression for $\mathbf{w}$:

```
$-\mathbf{X}^T(\mathbf{y}-\mathbf{Xw}) = 0$
$\mathbf{X}^T\mathbf{Xw}=\mathbf{X}^T\mathbf{y}$
$\mathbf{w} = (\mathbf{X}^T\mathbf{X})^{-1}\mathbf{X}^T\mathbf{y}$
```

#### Implementation of normal equation in NumPy

Let's assume that we have a feature $X$ and a target vector $y$. We first need to add the feature $x_0=1$ using `np.hstack` to create a new feature $x_1$ (Eq. (3.2)).

```
x0 = np.ones([X.shape[0],1])
x1 = np.hstack([x0,X])
```

We use a case of matrix multiplication using `np.matmul` and matrix inversion `np.linalg.inv` to implement Eq. (3.6).

```
XtX = np.matmul(X1.T,X1)
ty = np.matmul(X1.T,y)
w = np.matmul(np.linalg.inv(XtX),ty)
```

We can calculate predicted target values `y_pred` using the estimated weight vector $\mathbf{w}$ (Eq. (3.3)):

```
y_pred = np.matmul(X1,w)
```
