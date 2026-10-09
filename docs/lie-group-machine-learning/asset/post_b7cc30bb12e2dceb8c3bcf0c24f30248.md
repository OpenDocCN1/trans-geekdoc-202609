
## 9.5.1 Principle of the SVM algorithm

A support vector machine (SVM) [55, 56] is a machine learning method based on statistical theory proposed by Vapnik. The basic classification idea can be summarised as follows: (i) SVM aims at analysing linearly separable situation cases. For the linear indivisible case, the low-dimensional input samples are mapped into the high-dimensional feature space by the nonlinear mapping function, which makes it linearly separable, so that the samples are classified by using the linear algorithm in this high-dimensional space. (ii) Based on the theory of structural risk minimisation, the optimal segmentation hyperplane is constructed according to the maximum classification interval in the feature space, so that the learner is globally optimised. The expectation risk of the whole sample space satisfies a certain upper bound.

The goal of SVM is to construct an objective function to distinguish two types of patterns or samples as much as possible according to the principle of structural risk minimisation. Next, we analyse the SVM in the linearly separable and linearly inseparable cases.

### 9.5.1.1 Analysis of SVM in linearly separable cases

The $n$-dimensional sample set in the linearly separable case means that there is always a hyperplane so that the training samples are completely separated, which can be described as $v \cdot x + b = 0$, where $v$ is the $n$-dimensional vector and $b$ is the offset. The optimal segmentation hyperplane maximises the distance between the hyperplane and the vector of a class of data closest to this hyperplane. This problem can be solved by solving the following quadratic optimisation problem:

$$\min \Phi(v)=\frac{1}{2} \|v\|^{2} \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.45)$$

satisfying the constraints $y_{i}\left(v \cdot x_{i}+b\right) \geq 1, i=1,2, \ldots, n$. In the case of a large number of features, this quadratic programming problem can be transformed into its dual problem

$$\max V(\alpha)=\sum_{i=1}^{n} \alpha_{i}-\frac{1}{2} \sum_{i, j=1}^{n} \alpha_{i} \alpha_{j} y_{i} y_{j}\left(x_{i} \cdot x_{j}\right) \qquad \qquad \qquad \qquad \qquad \qquad (9.46)$$

satisfying constraints

$$\sum_{i=1}^{n} \alpha_{i} y_{i}=0, \alpha_{i} \geq 0, \quad i=1,2, \ldots, n \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.47)$$

$$v^{*}=\sum_{i=1}^{n} \alpha_{i} y_{i} x_{i} \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.48)$$

$$b^{*}=y_{i}-v \cdot x_{i} \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (9.49)$$

where $\alpha=\left(\alpha_{1}, \ldots, \alpha_{n}\right)$ is the Lagrange multiplier, $v^{*}$ is the normal vector of the optimal hyperplane, and $b^{*}$ is the offset of the optimal hyperplane. In (9.49), the solution must satisfy

$\alpha_i \{y_i (v \cdot x + b) - 1\} = 0, \quad i = 1, 2, \dots, n \quad (9.50)$

From (9.47), the samples of $\alpha_i = 0$ have no effect on the classification, and only the samples of $\alpha_i > 0$ can affect the classification. These samples support the optimal segmentation hyperplane, and these samples are called support vectors. At this point, we can get the final classification function as

$f(x) = \sum_{i=1}^{n} y_i \alpha_i (x \cdot x_i) + b^* \quad (9.51)$

The category attribution of the unknown sample is determined according to the symbol of $f(x)$.

### 9.5.1.2 Analysis of SVM in linearly inseparable cases

When the sample set is linearly inseparable, the sample set can be mapped to the high-dimensional feature space $F$, and the inner product can be realised by using the function satisfying a certain condition of the original space in $F$. The nonlinear classification problem of the original space is transformed into the linear classification problem of the target space. According to the relevant theory of functional analysis, as long as a kernel function satisfies the Mercer condition [59], it corresponds to the inner product in a certain space. Therefore, simply selecting the appropriate inner product function can solve this linearly inseparable problem. The objective function at this time is

$\max V(\alpha) = \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i,j=1}^{n} \alpha_i \alpha_j y_i y_j K(x_i \cdot x_j) \quad (9.52)$

and its corresponding classification function is

$f(x) = \sum_{i=1}^{n} y_i \alpha_i K(x \cdot x_i) + b^* \quad (9.53)$

## 9.5.2 The principle of KFDA

The kernel method [54] is a very useful computational theory that was originally used in SVM [55, 56]. It is widely used in existing linear algorithms, such as the kernel-based KPCA algorithm [57], kernel-based KICA algorithm [58], and KFDA algorithm. Next, we focus on the KFDA algorithm [31].

Because the FDA algorithm can only deal with linearly separable data, the classification performance is greatly degraded for other non-linear distributions or unknown complex distributions. For example, for the classification of the six distribution samples in Figure 9.8, the linear FDA algorithm cannot handle separating the asterisk sample from the plus sample, because it can never find a straight line to these samples after projection to the line while maintaining a good distinction.

![](img/456a7a56403cbb2b5f1a261793529a51_318_0.png)

![](img/456a7a56403cbb2b5f1a261793529a51_318_1.png)

**Fig. 9.8:** 6 kinds of linear indivisible sample set.

From left to right at the top are the data sets of two concentric ring distributions, namely the Banana distribution and Heigleyman distribution. From left to right at the bottom are the data sets of the Lithuanian distribution, difficult distribution, and the ring distribution embedded Gaussian distribution.

Thus, these seemingly non-linear samples cannot be directly classified by the linear algorithms in the same dimension of space. Assuming that these samples are linear in a higher-dimensional space, we continue to use the linear algorithm for classification in this high-dimensional space. This is the motivation for the KFDA algorithm.

Suppose that $\Phi$ is a non-linear mapping that maps the sample to a higher-dimensional feature space $F$. To find the direction of projection by linear classification in $F$, it is necessary to maximise the following equation:

$$J(v)=\frac{v^{T}S_{B}^{\Phi}v}{v^{T}S_{W}^{\Phi}v}$$

where $v \in F$, and $S_{B}^{\Phi}$ and $S_{W}^{\Phi}$ are corresponding class scatter matrices and intra class scatter matrices in $F$. For example, in the problems of two category classification, they are defined as follows:

$$S_{B}^{\Phi}=\left(m_{1}^{\Phi}-m_{2}^{\Phi}\right)\left(m_{1}^{\Phi}-m_{2}^{\Phi}\right)^{T}$$

$$S_{W}^{\Phi}=\sum_{i=1,2}\sum_{x\in x_{i}}\left(\Phi(x)-m_{i}^{\Phi}\right)\left(\Phi(x)-m_{i}^{\Phi}\right)^{T}$$

where $m_{i}^{\Phi}=1/l_{i}\sum_{j=1}^{l_{i}}\Phi\left(x_{j}^{i}\right)$, $l_{i}$ is the number of *i*-th category samples, $x_{j}^{i}$ is the *j*-th sample of the *i*-th category, and $x_{i}^{i}$ is the set of *i*-th category samples.

The dimension of the target feature space $F$ described in Section 9.5.1 can be very high or even infinite, so it is impossible to solve directly. To overcome this difficulty, a similar approach to KPCA and SVM can be used, i.e., without explicitly mapping the data to high-dimensional space, instead of finding a function that directly obtains its dot product ($\Phi(x) \cdot \Phi(y)$) for the training sample. We can use the Mercer kernel to effectively calculate these dot products of points to solve the original problem. Kernel $k(x, y)$ is used to calculate the dot product of the eigenvector in space $F$, i.e., $k(x, y) = (\Phi(x) \cdot \Phi(y))$. Many of the choices for $k$ have proven to be effective, e.g., the Gaussian RBF kernel $k(x, y) = \exp(-\|x - y\|^2 / c)$ in SVM or KPCA, and the polynomial kernel $k(x, y) = (x \cdot y)^d$, where $c$ and $d$ are the corresponding positive numbers.

To calculate the Fisher discriminant projection in the feature space $F$, we first need a new formula corresponding to (9.55), which replaces the dot product of the input sample with the kernel function. From the theory of regenerative nuclei, any scheme $v \in F$ must be in the space of all training samples in feature space $F$. Therefore, $F$ has the following form:

$$v = \sum_{i = 1}^{l} \alpha_i \Phi(x_i).$$

Using the definition of (9.57) and $m_i^\Phi$, we have

$$v^T m_i^\Phi = \frac{1}{l_i} \sum_{j = 1}^{l_i} \sum_{k = 1}^{l_i} \alpha_{jk} \left( k_j(x_j, x_k^i) \right)$$

$$= \alpha^T M_i.$$

In the above formula, $M_i = \frac{1}{l_i} \sum_{k = 1}^{l_i} k(x_j, x_k^i)$, and the dot product is replaced by a kernel function. According to (9.55) and (9.58), we can get

$$v^T S_B^{c\Phi} v = \alpha^T M \alpha$$

In the above formula, $M = (M_1 - M_2)(M_1 - M_2)^T$. Similarly, using the definition of (9.57) and $m_i^\Phi$, we have

$$v^T S_W^{c\Phi} v = \alpha^T N \alpha$$

where $N = \sum_{j=1,2} K_j \left( I - I_{l_j} \right) K_j^T$, $K_j$ is an $1 \times l_j$ matrix, and $(K_j)_{nm} = k(x_n, x_m^j)$. Further, $(K_j)_{nm}$ is called the kernel matrix of class $j$, where $I$ is a unit matrix and $I_{lj}$ is a matrix whose all elements are $1/l_j$.

Combining (9.59) and (9.60), the Fisher linear discriminant can be obtained in $F$

$$J(\alpha) = \frac{\alpha^T M \alpha}{\alpha^T N \alpha}$$

where $\alpha = N^{-1}(M_1 - M_2)$.
