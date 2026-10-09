
## 12.4.1 Topological Invariance of Manifold

P-surface topology is a very popular two-dimensional topological manifold, e.g., the Swiss roll and S-curve. Nearly all manifold learning algorithms are based on P-surfaces for experimental comparison. The $S^2$ spherical surface is a very important two-dimensional topological manifold.

Differential geometry indicates that it is possible to obtain topological invariance information of manifolds by adding proper geometric conditions and topological conditions to manifolds, such as curvature, diameter, compactness, connectivity, and homeomorphism [22]. Here, it is assumed that the diameter of a compact manifold is

$$d(M)= \max_{p, q \in M} \rho(p, q)$$

where $p, q \in M$, and $\rho$ is the distance function induced by $g$.

**Theorem 12.2.** (Bonnet-Myers theorem) [22]: Let $\gamma(t)$, $a \leq t \leq b$, be a geodesic. If there exists a conjugate point $\gamma(c)$ of $\gamma(a)$ along $\gamma$, $a < c < b$, then $\gamma$ is not the shortest geodesic line connecting $\gamma(a)$ and $\gamma(b)$, i.e., the length of $\gamma$ is greater than the distance between $\gamma(a)$ and $\gamma(b)$.

From the compactness of $M$ and the Bonnet-Myers theorem, we can see that $d(M) < \frac{\pi}{\sqrt{1/4}} = 2\pi$. Then, from the Klingenberg theorem, we can see that $i(M) \geq \pi$. Hence, $i(M) \geq \pi > \frac{1}{2}d(M)$.

For $\forall x \in M$, if $\rho(x, p) \geq i(M)$, then $\rho(x, q) < i(M)$. Let $\gamma_1$ be the shortest geodesic of $p$ to $x$. Then, $L(\gamma_1) = \rho(x, p) \geq i(M)$.

Since $p, q$ are the farthest apart ($\rho(p, q) = d(M)$ is the diameter), there is a shortest geodesic $\gamma_2$ that connects $p$ to $q$, which makes the angle between $\gamma_1'$ and $\gamma_2$ satisfy $\theta \leq \pi/2$. Then, take the shortest geodesic $\chi$ connecting $x$ and $q$. As $R(P) > 1/4$ and from the compactness of $M$, we can get

$$R(P) \geq \frac{1}{r^2} > \frac{1}{4}$$

where $r < 2$ is a positive constant.

Consider a known sphere $S^2(r)$ with radius $r$ in $R^3$, whose Riemann sectional curvature is $1/r^2$. Geodesic triangle $ABC$ is formed in $S^2(r)$ such that the lengths of $AB$ and $AC$ are $L(\gamma_1)$ and $L(\gamma_2) = d(M)$, respectively. The angle is $\angle \theta = \angle A$, as shown in Figure 12.9.

![](img/456a7a56403cbb2b5f1a261793529a51_390_0.png)

Applying the Toponogov comparison theorem [22], we can obtain

$$d(x, q) = L(\chi) \leq BC < i(M)$$

This indicates that $M$ is the union of two open sets that are homologous to $\mathbb{R}^n$. According to Brown's theorem, $M$ is homologous to $S^n(1)$.

**Theorem 12.3.** (Topological spherical theorem) [22]: Let $M$ be an $n$-dimensional compact simply-connected Riemannian manifold, and suppose that the Riemann sectional curvature $R(P)$ of any two-dimensional plane $P$ of the tangent space satisfies

$$\frac{1}{4} < R(P) \leq 1$$

Then, $M$ is homologous to the $n$-dimensional unit sphere $S^n(1)$.

## 12.4.2 Polarisation theorem of image feature manifolds

As far as the feature vectors are selected to reduce the dimensionality, the detailed proof of their feasibility has been given in the study of spectral graph theory. When the eigenvectors corresponding to the smaller eigenvalues are ignored, the curvature (the correlation between the vectors and the correlation between the vectors) between the high similarities of the manifolds is hardly distorted, and the localities of the manifolds effectively maintain the geometric structure [20]. For example, consider the same person at different stages of the two face images, one of which has a scar. Then, in choosing the feature vector, we can ignore the scar and select only the eyes, nose, mouth, and other characteristics. The manifold polarisation theorem given here is the theoretical basis for choosing feature vectors.

Suppose that the nonnegative semi-definite symmetric matrix $A \in \mathbb{R}^{D \times D}$ can be denoted by its eigenvectors $A = V \Lambda V^{T}$, where $\Lambda$ is a diagonal matrix consisting of eigenvalues whose diagonal entries are in descending order. Define $X = \Lambda^{1/2} V^{T}$, and let $X_{(d)}$ be the matrix of the first $d$ rows of $X$. Further, $A_{(d)} = X_{(d)}^{T} X_{(d)}$ is the approximate representation of $A$, whose rank is $d$.

Meanwhile, $Y_{(d)}$ is the conormal matrix of the column vectors of $X_{(d)}$, mapped to the $d$-dimensional hypersphere surface, and it is transformed into an identity matrix by unitary transformation. For $\forall x_{i}, x_{j} \in X_{(d)}$ (corresponding to $y_{i}, y_{j} \in Y_{(d)}$), the included angle is

$$\theta_{ij} = \angle(x_{i}, x_{j}) = \arccos \frac{x_{i}^{T} x_{j}}{\|x_{i}\| \cdot \|x_{j}\|}$$

For $\forall x_{i}, x_{j} \in X_{(d)}$ (corresponding to $y_{i}, y_{j} \in Y_{(d)}$), the correlation is expressed as

$$\operatorname{corr}(x_{i}, x_{j}) = y_{i}^{T} y_{j} = \cos \theta_{ij}$$

**Theorem 12.4.** (Polarisation theorem) [20]: If the positive (nonnegative) symmetric matrix $A$ can be expressed as a continuous reduced order form $A_{(D-1)}, A_{(D-2)}, \dots, A_{(2)}, A_{(1)}$, then $\sum_{i \neq j} (\cos \theta_{ij})^2$ (corresponding to $\| Y_{(d)}^T Y_{(d)} \|_F^2$) is also strictly decreasing (non-increasing).

The inference obtained from Theorem 12.3 is the theoretical basis of the spectral estimation algorithm for generating the topological invariance of image feature manifolds.

**Inference 12.1.** (Manifold embedding principle) [20]: The similarity matrix $A$ is replaced by the matrix $A_{(d)}$, whose rank is $d$. The resulting low-dimensional manifolds are similar to the inner structures of high-dimensional manifolds of data samples, and the curvature of the manifolds has almost no distortion.

The theorem and inference above are similar to those of PCA. In this algorithm, as the cosine of the angle between the vectors contains a strong energy in the similarity matrix, the data points are distributed over the hypersphere surface and precisely maintain the smaller vector angle [20]. This shows that the geometric features between adjacent points are completely preserved by vector angles.

## 12.4.3 Manifold dimensionality reduction algorithm

Theorem 12.1 shows that $Y_{(d)}$ is a low-dimensional nonlinear embedding of data sample manifolds over hypersphere surfaces. The arc length between two points is inversely proportional to their similarity [20]. First, the local dimension $d$ of the low-dimensional manifold is chosen to ensure that the low-dimensional manifold can effectively maintain the geometric characteristics of the high-dimensional manifold. In the PCA algorithm, $d$ is usually chosen by artificial estimation without prior knowledge or the influence of noise on data.

However, it is very difficult to estimate the embedding dimension of spherical low-dimensional manifolds. Therefore, the goal of this section is to embed the data samples into the vector space as accurately as possible. Suppose that $\forall p \in Y$ and $[e_1, e_2, \dots, e_{d-1}]$ is the orthogonal basis of the tangent space of point $p$. We set $I = E^T E$, where $E = [e_1, \dots, e_{d-1}, p]$. For $\forall e_j$, it can be regarded as a projection axis of space $\mathbb{R}^a \times \Gamma^b$, where $\mathbb{R}^a$ is an $a$-dimensional vector space and $\Gamma^b$ is a $b$-dimensional torus space satisfying $a + b = d - 1$. If the sample point is completely surrounding the hypersphere surface along the $e_1$ direction, the projection axis in the $e_1$ direction is the ring. The projection axis $e_j$ is linear if the sample point only has an intermediate portion surrounding the hypersphere surface along the $e_j$ direction.

Similar to the idea of the PCA algorithm, the main axis of the PCA algorithm satisfies the Gaussian distribution. The tangent space of the sample point and its projection axis $E$ also satisfy the Gaussian distribution in the hypersphere surface [33]. When $\forall y \in CS^{d-1} \subset C^d$ is a unit vector and satisfies $y^*y = 1$, where $y^*$ is the conjugate transpose matrix of $y$, the complex Bingham distribution can be regarded as a multivariate Gaussian distribution [33]:

$$p(y|\Sigma) = \mathcal{C}(\Sigma)^{-1} \exp(y^*\Sigma y)$$

The Bingham distribution can be parameterised by the Hermitian matrix

$$\Sigma = E \operatorname{diag}([\kappa_1, \dots, \kappa_d])E^*$$

where $\kappa_1 < \kappa_2 < \dots < \kappa_{d-1} < \kappa_d = 0$ is the concentration parameter value corresponding to the distribution density, and $\kappa_i < 0$ indicates that the data is distributed in a smaller range along the direction of $e_i$. The normalised constant $\mathcal{C}(\Sigma)$ can be calculated by hypergeometric functions, and the calculation process is as follows [33]:

$$\mathcal{C}(\Sigma) = F_1\left(\frac{1}{2}, \frac{d}{2}, \operatorname{diag}[\kappa_1, \dots, \kappa_d]\right) = 2\pi^{d-1}\sum_{j=1}^{d-1}\frac{e^{\kappa_j}}{\prod_{i \neq j}(\kappa_j - \kappa_i)}$$

Jupp and Mardia et al. [34] demonstrated that the direction vector and concentration parameter $[\kappa_1, \dots, \kappa_d]$ in $E$ are correlated by the eigenvalue decomposition form $YY^T = E \operatorname{diag}([\lambda_1, \dots, \lambda_d])E^*$ of $Y$, where $0 < \lambda_1 < \lambda_2 < \dots < \lambda_d$ satisfies

$$\lambda_j = \frac{\partial \log \mathcal{C}(\Sigma)}{\partial \kappa_j}$$

For a larger sample space, there exists $N_c \pi^t$, where $c$ is a constant. Although it is feasible to solve the concentration parameter by a numerical method, it is only necessary to obtain the eigenvalue decomposition in the manifold dimension reduction problem, and the exact concentration parameter is not needed. Its feature vector can be estimated using the tangent space maximum likelihood estimation of the sample points: for $E$, the sample points are nearly linearly distributed along the direction of $e_i$. When $\lambda_i \approx \lambda_d$, the sample points are evenly distributed along the axis of the torus.

Mardia et al. [35] excluded the possibility that the direction axis of $e_i$ is a torus by means of normalised decomposition mapping. Therefore, the mapping matrix $Y$ can be projected respectively along the direction of $e_i$ and $p$, and the normalisation of the vector is then processed again. When the sample space is projected onto the hypersphere surface, the sample point $[0, \dots, 0, 1]$ is aligned with the Bingham axis.

## 12.5 Spectral estimation learning algorithm for topological invariance of image feature manifolds

The spectral estimation algorithm based on the topological invariance of image feature manifolds is based on the topological invariance theory of manifolds.
