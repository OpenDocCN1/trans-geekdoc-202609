
![](img/b122213aed28c1888de83a894123323e_78_0.png)

**Figure 3.6** A convex body $K$ (left) is transformed into an isotropic convex body $T(K)$ (right). The preconditioner is $T=\Sigma^{-1/2}$, where $\Sigma$ is the covariance matrix of $K$.

## 3.3.5 Frames

The notion of a frame, widely used in signal processing, extends the concept of a basis but drops the requirement of linear independence. Frames are intimately connected to discrete isotropic distributions:

**Proposition 3.3.11** (Parseval frames). *For any vectors* $u_1,\ldots,u_N\in\mathbb{R}^n$, *the following are equivalent:*

- (i) (Parseval identity) $\|x\|^2=\sum_{i=1}^N\langle u_i,x\rangle^2$ for each $x\in\mathbb{R}^n$.
- (ii) (Frame expansion) $x=\sum_{i=1}^N\langle u_i,x\rangle u_i$ for each $x\in\mathbb{R}^n$.
- (iii) (Decomposition of identity) $I_n=\sum_{i=1}^N u_i u_i^\mathsf{T}$.
- (iv) (Isotropy) The random vector $X\sim\operatorname{Unif}\{\sqrt{N}u_1,\ldots,\sqrt{N}u_N\}$ is isotropic.

A set of vectors satisfying these equivalent properties is called a Parseval frame.

*Proof.* **(i)$\Rightarrow$(iv)** The identity in (i) can be written as

$$\|x\|^2=\frac{1}{N}\sum_{i=1}^N\langle\sqrt{N}u_i,x\rangle^2=\mathbb{E}\langle X,x\rangle^2.$$

Since this holds for all $x\in\mathbb{R}^n$, the random vector $X$ is isotropic by (3.9).

**(iv)$\Rightarrow$(iii)** because isotropy of $X$ means that

$$I_n=\mathbb{E}XX^\mathsf{T}=\frac{1}{N}\sum_{i=1}^N(\sqrt{N}u_i)(\sqrt{N}u_i)^\mathsf{T}=\sum_{i=1}^N u_i u_i^\mathsf{T}.$$

**(iii)$\Rightarrow$(ii)** follows by multiplying on both sides by $x$. Finally, **(ii)$\Rightarrow$(i)** comes from taking the inner product with $x$.

**Example 3.3.12** (Coordinate distribution). The standard basis $\{e_1,\ldots,e_n\}$ in $\mathbb{R}^n$ is a Parseval frame. Therefore, a *coordinate random vector*

$$X\sim\operatorname{Unif}\{\sqrt{n}e_1,\ldots,\sqrt{n}e_n\},$$

is isotropic. Among all high-dimensional distributions, Gaussian is often the easiest to work with—think of it as “the best.” The coordinate distribution, being highly discrete, is often “the worst.”

**Example 3.3.13** (The Mercedes-Benz frame). An iconic example of a Parseval frame that is not linearly independent is the set of $N$ equispaced points on the circle of radius $\sqrt{2/N}$, such as the one in Figure 3.7 (try Exercise 3.30).

## 1.2 矩阵及其运算

由 $m \times n$ 个数 $a_{ij}$（$i=1,2,\ldots,m;\ j=1,2,\ldots,n$）排成的 $m$ 行 $n$ 列的数表，称为 $m$ 行 $n$ 列矩阵，简称 $m \times n$ 矩阵。为表示它是一个整体，总是加一个括弧，并用大写黑体字母表示它，记作

$$A = (a_{ij})_{m \times n}$$

这 $m \times n$ 个数称为矩阵 $A$ 的元素，简称为元，数 $a_{ij}$ 位于矩阵 $A$ 的第 $i$ 行第 $j$ 列，称为矩阵 $A$ 的 $(i,j)$ 元。

元素是实数的矩阵称为实矩阵，元素是复数的矩阵称为复矩阵。

行数与列数都等于 $n$ 的矩阵称为 $n$ 阶矩阵或 $n$ 阶方阵。

只有一行的矩阵

$$A = [a_1, a_2, \ldots, a_n]$$

称为行矩阵，又称行向量。

只有一列的矩阵

$$B = [b_1; b_2; \ldots; b_m]$$

称为列矩阵，又称列向量。

两个矩阵行数相等、列数也相等时，就称它们是同型矩阵。

如果 $A = (a_{ij})$ 与 $B = (b_{ij})$ 是同型矩阵，并且它们的对应元素相等，即

$$a_{ij} = b_{ij} \quad (i=1,2,\ldots,m;\ j=1,2,\ldots,n)$$

那么就称矩阵 $A$ 与矩阵 $B$ 相等，记作

$$A = B$$

元素都是零的矩阵称为零矩阵，记作 $O$。注意不同型的零矩阵是不同的。

Equivalently, consider a random vector

$$X = \theta \mu + g$$

where $\theta$ is a Rademacher random variable, $g \sim N(0, I_n)$, and $\theta$ and $g$ are independent. Draw a sample $X_1,\dots,X_m$ of independent random vectors identically distributed with $X$. Then the sample is distributed according to the Gaussian mixture model; see Figure 4.5 for illustration.

![](img/b122213aed28c1888de83a894123323e_134_0.png)

**Figure 4.5** $m = 3000$ points drawn from the Gaussian mixture model with means $-\mu$ and $\mu$ shown as two big black dots, for $\mu = (-1.6, 0)$.

Given $m$ sample points from the Gaussian mixture model, our goal is to figure out which points belong to which cluster. To do this, we can use a variant of the *spectral clustering* algorithm we introduced for networks in Section 3.2.2.

To see why a spectral method might work here, notice that the distribution of $X$ is not isotropic, but rather stretched along $\mu$ (the horizontal direction in Figure 4.5). Thus, we can approximately find $\mu$ by computing the first principal component of the data — the eigenvector corresponding to the largest eigenvalue of the sample covariance matrix. Next, we can project the data points onto the principal component and classify them based on which side of the origin they lie on. Here is the algorithm:

### Spectral Clustering Algorithm

- **Input:** points $X_1, \dots, X_m$ in $\mathbb{R}^n$
- **Output:** a partition of the points into two clusters

1. Compute the sample covariance matrix $\Sigma_m = \frac{1}{m} \sum_{i=1}^m X_i X_i^\top$.
2. Compute the top eigenvector $v = v_1(\Sigma_m)$.
3. Split the points $X_i$ into two communities based on the sign of $\langle X_i, v \rangle$.

**Theorem 4.7.5** (Spectral clustering for the Gaussian mixture model). *Take points $X_1,\dots,X_m \in \mathbb{R}^n$ from the Gaussian mixture model with means $\mu$ and $-\mu$. If $m \ge C n$ and $\|\mu\|_2 \ge C$, then with probability at least 0.99, the spectral*

- (c) Conversely, show for every $\varepsilon > 0$:

  $$\mathcal{N}(\mathcal{M}_{m,n,r},\|\cdot\|_F,\varepsilon)\geq\left(\frac{c}{\varepsilon}\right)^{\frac{1}{2}(m+n)r}.$$

### 4.51 ☕☕☕☕ (Spectral clustering of the Gaussian mixture model)

Prove Theorem 4.7.5, which guarantees that spectral clustering learns the Gaussian mixture model. Here is how:

- (a) Compute the covariance matrix $\Sigma$ of $X$ and note that the top eigenvector $u$ is collinear with $\mu$.
- (b) Conclude that the signs of $\langle X_i,u\rangle$ classify most points $X_i$ correctly.
- (c) Use results about covariance estimation to show that the sample covariance matrix $\widehat{\Sigma}_m$ approximates $\Sigma$.
- (d) Use the Davis-Kahan inequality (Theorem 4.1.15) to deduce that the top eigenvector $v=v_1(\widehat{\Sigma}_m)$ approximates $u$.
- (e) Using (b), conclude that the signs of $\langle X_i,v\rangle$ classify most points $X_i$ correctly.
