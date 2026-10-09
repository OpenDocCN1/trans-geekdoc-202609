The Laplacian eigenmap is characterised by the following. It is a local non-linear method, and the spectrum theory is very closely related. There are only two parameters $k$ and $d$ in the algorithm, and the global optimal solution is obtained by solving the eigenvalue problem of the sparse matrix. The algorithm makes very close points in the original space too close to the low-dimensional space, so it can be used for clustering.

# 17.3.5 Local tangency space arrangement (LTTSA)

The basic idea of the LTSA algorithm is to use the tangent space of the sample point neighbourhood to represent the local geometric properties and then to arrange the local tangent space to construct the global coordinates of the manifold. The algorithm is described as follows:

```
Algorithm 17.5: LTSA algorithm
Input: Sample input $X = \{x_1, x_2, \ldots, x_n \in \mathbb{R}^D\}$ sample true dimension $d$, neighbourhood parameter $k$
Output: low-dimensional embedding $Y = \{y_1, y_2, \ldots, y_n \in \mathbb{R}^d\}$
(1) Calculate the nearest neighbour point of each point (using $K$ nearest neighbour or $\epsilon$ sphere neighbourhood).
(2) Local linear projection. For the neighbourhood of each sample point, the right singular vector corresponding to the maximum $d$ singular values of the centralised matrix $X_i - \bar{x}_j I_1^k$ is calculated and the $d$ singular vectors are composed of the matrix $V_i$.
(3) Local coordinate system arrangement. Construct the permutation matrix $\Phi = \sum_{i=1, \ldots, N} S_i W_i W_i^T S_i^T$, and calculate the smallest $d+1$ eigenvalues corresponding to the eigenvector $u_1, \ldots, u_d$. Then, $T = \{u_2, \ldots, u_{d+1}\}^T$ is the calculated embedding result.
```

The LTSA algorithm can effectively study the overall embedding coordinates that represent the low-dimensional manifold structure of the data set. However, the order of the matrix for eigenvalue decomposition in the algorithm is equal to the number of samples, and the sample set cannot be processed when the data set is large. It handles new sample points effectively.

# 17.4 Basic concept and nature of symplectic group

> Definition 17.11. Let $V$ and $W$ be two vector spaces. Map $f: V \to W$, so that for any $X$, $Y \in V$, $a \in R$, we have

$$f(X + Y) = f(X) + f(Y) \ , \quad af(X) = af(X)$$

Then, we call $f$ a linear mapping or homomorphism of vector spaces from $V$ to $W$.

$$\mathrm{Ker}\ f = \{X \in V \mid f(X) = 0\}$$