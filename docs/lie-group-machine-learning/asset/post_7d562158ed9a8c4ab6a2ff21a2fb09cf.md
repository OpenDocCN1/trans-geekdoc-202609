
In this way, we can project the new sample $x$ into $v$ as follows:

$$
(v\cdot \Phi(x)) = \sum_{i=1}^{l} a_{i} k(x_{i}, x) \quad . \tag{9.62}
$$

Estimating the covariance matrix of $l$ dimension from $l$ samples may make the matrix $N$ ambiguous. For this reason, a multiple of the unit matrix can be simply added, e.g., replacing $N$ with $N_{\mu}$:

$$
N_{\mu} = N + \mu I \quad . \tag{9.63}
$$

The above problem can also be considered in one of the following different forms.

- (i) It makes the numericalisation of the problem more stable, and for a sufficiently large $\mu$, $N_{\mu}$ will become positive definite.
- (ii) This method is similar to the method in [60], reducing the number of bases based on the sample eigenvalue estimates.
- (iii) It re- forces the normalisation of $\|a\|^{2}$, which is a suitable solution with a small expansion coefficient. Although the real impact on the normalisation problem is unknown, there is indeed a link in the SVM [55].

In addition, there is a method for normalising $N$, i.e., using the penalty term $\|v^{2}\|$, which is similar to SVM (plus the full kernel matrix $K_{ij} = k(x_{i}, x_{j})$).

## 9.5.4 Kernel of the Lie group

For the sample sets of the Lie group matrix, the matrix itself does not have the dot product. However, the result of matrix multiplication in the group operation is still a matrix. Therefore, the vector-based kernel function cannot be used for samples of the Lie group matrix, and we need to design new kernel functions.

### 9.5.4.1 RBF kernel of the Lie group

The Gaussian RBF kernel function is one of the most frequently used kernel functions. It is also called a radial basis function because it performs a good high- dimensional spatial linear mapping for the nonlinear data set of Figure 9.8. The vector-based RBF kernel function is of the form

$$
k(x, y) = \exp \left( - \frac{\|x - y\|^{2}}{2 \sigma^{2}} \right) \quad . \tag{9.64}
$$

In the above equation, the difference between the two vectors $x$ and $y$ is modulo, and there is no matrix subtraction for the general matrix Lie group. However, in the manifold space where the Lie group is located, the component that subtracts another element from one element can be achieved by the group operation and the inverse of the group element, e.g., $x^{-1}y$, $x, y \in G$. However, in addition to the exchange of the Lie group, the general group of the Lie group is not exchangeable, i.e., $\|x^{-1}y\| \neq \|y^{-1}x\|$. Moreover, for the matrix Lie group, we have $\|\log (x^{-1}y)\| = \|\log (y^{-1}x)\|$. From another point of view, $\lVert \boldsymbol{x}-\boldsymbol{y}\rVert$ is the Euclidean distance between two points $\boldsymbol{x}$ and $\boldsymbol{y}$ in the linear space, and $\lVert \log \left(\boldsymbol{x}^{-1}\boldsymbol{y}\right) \rVert$ is the geodesic distance between two points in the Lie group manifold space. The geodesic distance $\lVert \log \left(\boldsymbol{x}^{-1}\boldsymbol{y}\right) \rVert$ from $\boldsymbol{x}$ to $\boldsymbol{y}$ is equal to the geodesic distance $\lVert \log \left(\boldsymbol{y}^{-1}\boldsymbol{x}\right) \rVert$ from $\boldsymbol{y}$ to $\boldsymbol{x}$. In addition, the geodesic distance between any two Lie group elements is nonnegative, which satisfies the requirement that kernel matrix $K$ is a symmetric positive definite matrix.

According to the above analysis, we can get the Lie group matrix RBF kernel function

$$
k(\boldsymbol{x}, \boldsymbol{y})=\exp \left(\frac{-\left\lVert\log\left(\boldsymbol{x}^{-1}\boldsymbol{y}\right)\right\rVert^2}{2 \sigma^2}\right). \tag{9.65}
$$

In the above equation, the nonlinear Lie group samples are mapped into infinite-dimensional space and the dot product is calculated. If the distribution of the samples in the original Lie group manifold space is in accordance with the radial characteristics, then using the kernel function will result in an ideal sample linearization result. For the fractional molecular part of (9.65), approximation of the RBF kernel function can be obtained by using the first-order BCH formula:

$$
k(\boldsymbol{x}, \boldsymbol{y})=\exp \left(\frac{-\left\lVert\log\boldsymbol{y}-\log(\boldsymbol{x})\right\rVert^2}{2 \sigma^2}\right). \tag{9.66}
$$

### 9.5.4.2 Lie group polynomial kernel

The form of the polynomial kernel in the vector feature space is $k(\boldsymbol{x}, \boldsymbol{y})=(\boldsymbol{x} \cdot \boldsymbol{y}+1)^d$. The vector dot product is exchangeable, but the matrix multiplication is not exchangeable. Therefore, the vector-based polynomial kernel function cannot be used directly for matrix Lie group samples.

From matrix theory, we can define an inner product in the space of an $n \times n$ matrix.

$$
\langle\boldsymbol{x}, \boldsymbol{y}\rangle=\operatorname{tr}\left(\boldsymbol{y}^{H} \cdot \boldsymbol{x}\right) \tag{9.67}
$$

where $tr$ is a matrix trace operator and $\boldsymbol{y}^{H}=\overline{\boldsymbol{y}}^{T}$, which means that $\boldsymbol{y}^{H}$ is the conjugate transpose matrix of $\boldsymbol{y}$:

$$
\boldsymbol{y}^{H}=\left(\begin{array}{ccc} \overline{a_{11}} & \cdots & \overline{a_{1 n}} \\- & \ddots & \\ \overline{a_{n 1}} & \cdots & \overline{a_{n m}}\end{array}\right)=\boldsymbol{y}^{T}. \tag{9.68}
$$

The inner product of the matrix defined by (9.67) can be used to derive geometric quantities of many matrix spaces. For example, the angle of two matrix vectors in the matrix space can be defined as $\theta=\arccos \left(\operatorname{tr}\left(\boldsymbol{y}^{H} \cdot \boldsymbol{x}\right) /\left(\|\boldsymbol{x}\| \cdot \|\boldsymbol{y}\|\right)\right)$. At the same time, the inner product of the matrix conforms to all the properties of the inner vector product. Therefore, it also satisfies $\langle\boldsymbol{x}, \boldsymbol{y}\rangle=\operatorname{tr}\left(\boldsymbol{y}^{H} \cdot \boldsymbol{x}\right)=\operatorname{tr}\left(\overline{\boldsymbol{x}}^{T} \cdot \boldsymbol{y}\right)=\langle\boldsymbol{y}, \boldsymbol{x}\rangle$. With this property, it is easy to derive the polynomial kernel function based on the matrix Lie group:

$$
k(\boldsymbol{x}, \boldsymbol{y})=\left(\operatorname{tr}\left(\boldsymbol{y}^{H} \cdot \boldsymbol{x}\right)+1\right)^{d}. \tag{9.69}
$$

In the above equation, $d$ is any positive real number, usually a positive integer.

### 9.5.4.3 Lie group linear kernel

The linear kernel function of the vector space is $k(x, y) = x \cdot y$. According to the matrix inner product defined by (9.67), the Lie group linear kernel function can be obtained directly:

$$
k(x, y) = \operatorname{tr}\left(y^H \cdot x\right) \text {. \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(9.70)}
$$

### 9.5.4.4 Lie group perceptron kernel

The most widely used perceptron functions are the sigmoid function and hyperbolic tangent function (tanh). The form of the hyperbolic tangent function is $\operatorname{tanh}(b \cdot (x \cdot y + c)), b > 0, c < 0$. Corresponding to (9.67), we get the Lie group perceptron kernel function:

$$
k(x, y) = \operatorname{tanh}\left(b\left(\operatorname{tr}\left(y^H \cdot x\right)\right) + c\right) \text {. \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(9.71)}
$$

Similarly, the sigmoid function is $1 / 1 + e^{-x}$, and we can get the Lie group kernel function in sigmoid form:

$$
k(x, y) = \frac{1}{1 + e^{c(\operatorname{tr}(y^H.x))}} \text {. \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad(9.72)}
$$

In addition to (9.66), using the Lie group geodesic distance, (9.67) and subsequent kernel functions can be used not only for the matrix Lie group but also for general matrix samples.

## 9.5.5 KlieDA algorithm based on the Lie group kernel function

The KlieDA algorithm based on the Lie group kernel function can be designed using some Lie group kernel functions deduced in Section 9.5.4. The derivation of multi-class questions is similar to the Lie–Fisher algorithm. We present a two-class KlieDA algorithm, i.e., Algorithm 9.6.

**Algorithm 9.6**: Two-class Lie group KlieDA classification algorithm

- **Input**: $\{x_{ij}\}_{i=1,2}^{j=1...n_i} \in \mathcal{G}, x_{ij}$ represents the $j$-th sample of the $i$-th category, $n_i$ represents the number of training samples in the $i$-th category.

- **Output**: Output the category attribution for each unknown sample.

**Procedure:**

- (1) For each Lie group sample $x_{ij}$, find the means $\mu_1$ and $\mu_2$ of the two classes of Lie group samples. Use Algorithm 9.3 for the general Lie group, and use (9.25) to find the log-Euclidean mean of the covariance sample.
- (2) Choose the specific Lie group kernel functions, and then obtain $M_i = 1/n_i \sum_{k=1}^{n_i} k\left(x_{ji}, x_{i}^k\right)$ of two types Lie group samples. Then, set $M = (M_1 - M_2) \left(M_1 - M_2\right)^T$.
- (3) Calculate $N = \sum_{i=1,2} K_i \left(I - 1_n\right) K_i^T$, where $K_i$ is an $n \times n_i$ matrix and $\left(K_i\right)_{nm} = k\left(x_n, x_m^i\right)$.
- (4) Calculate $\alpha = N^{-1} \left(M_1 - M_2\right).$
- (5) Calculate the projection of the two classes of means $\mu_1$ and $\mu_2$ on the vector $v$ in space $F$: $\tilde{\mu}_1 = \langle v \cdot \Phi\left(\mu_1\right)\rangle = \sum_{i=1}^c \sum_{j=1}^{n_i} a_{i}k\left(x_{ij}, \mu_1\right)$, $\tilde{\mu}_2 = \langle v \cdot \Phi\left(\mu_2\right)\rangle = \sum_{i=1}^c \sum_{j=1}^{n_i} a_{i}k\left(x_{ij}, \mu_2\right)$
- (6) For unknown $\boldsymbol{x}$, project it on the vector $v$ in space $F$: $\boldsymbol{x} = \langle v \cdot \Phi(\boldsymbol{x})\rangle = \sum_{i=1}^c \sum_{j=1}^{n_i} a_{i}k\left(x_{ij}, \boldsymbol{x}\right)$. Then, the category attribution is obtained by $i^* = \operatorname{argmin}_{i=1,2} |\boldsymbol{x} - \tilde{\mu}_i|.$
