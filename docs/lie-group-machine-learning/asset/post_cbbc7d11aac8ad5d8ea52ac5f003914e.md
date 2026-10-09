
![](img/456a7a56403cbb2b5f1a261793529a51_340_0.png)

matically a linear function that is associated with multiple vector spaces, its complexity and high-order characteristic make the problem difficult to understand. For solving this problem, many researchers have studied the visualisation of tensor fields [30, 32] (Figure 10.2).

In summary, tensor fields have been widely applied to many research fields. However, in computer information processing, it is still in the preliminary exploration stage. There are many problems that need to be studied further. This chapter takes full advantage of the characteristics of tensor fields and combines them with the tensor decomposition technique and tensor field theory to construct the tensor learning model. We proposed the data reduction algorithm based on tensor fields to provide examples for machine learning applications.

## 10.2 Data reduction model based on tensor fields

Combined with the related theory of tensor fields, this section discusses the data reduction model and algorithm based on tensor fields. First, we introduce the concept of tensor field in manifolds. Then, we give the data reduction model in tensor fields and discuss the simplified form of data in tensor fields. Next, we describe the design processing of the data reduction algorithm based on tensor fields. Finally, we give an experimental example.

### 10.2.1 Tensor field on a manifold

Contemporary tensor fields are divided into two steps. First, there is the vector bundle, which is a vector space depending on the parameters, and the parameters constitute a manifold. Second, there is the introduction of the tensor bundle. The concept of the vector bundle is not related to the choice of any base. The usual procedure is to multiply two vector bundles and obtain the tensor bundle. The handling mechanism performs well, and its coordinates are irrelevant. Finally, the tensor field is similar to the vector field that is a cross section of the tensor bundle [23, 24].

For the data objects in data reduction analysis, we abstract them to elements in tensor space to utilise the handling method in tensor fields. The concept of tensor space is as follows:

**Definition 10.1.** Set $V_1, V_2$ and $W$ as the vector space. If there is a vector space $W$ and a bilinear map $\otimes: V_1 \times V_2 \rightarrow W$, we have $W = \langle \text{Im}\,\otimes \rangle = \langle (V_1, V_2) \rangle$. For any vector space $Z$ and bilinear map $f: V_1 \times V_2 \rightarrow Z$, there is a linear map $g: W \rightarrow Z$ that makes $f = g \circ \otimes$. Then, we can call $W$ the tensor space built by the tensor product of $V_1, V_2$.

$M$ is an $n$-dimensional differentiable manifold ($C^{\infty}$ manifold). $F(M)$ represents the set of differentiable functions on $M$ and can be regarded as an associative algebra in the mathematics domain.

$D^{1}(M)$ represents the set of all differentiable vector fields on $M$, which means that $X \in D^{1}(M)$ is a transform of $F(M)$. $X$ satisfies the following two conditions:

$$
\begin{aligned}
X(\alpha f + \beta g) &= \alpha X(f) + \beta X(g), \quad \forall \alpha, \beta \in \mathbf{R}; f, g \in F(M) \\
X(f \cdot g) &= f \cdot X(g) + g \cdot X(f) \quad (10.9)
\end{aligned}
$$

Here, $X$ is a derivative of $F(M)$. We can define addition in $D^{1}(M)$ and the product of numbers in $\mathbf{R}$. Then, $D^{1}(M)$ becomes a linear space in $\mathbf{R}$.

From the perspective of geometry, if $M_p$ represents the tangent space in point $p$, the value in point $p$ will be a tangent vector. By setting a coordinate system on manifold $M$, the element in $D^{1}(M)$ can be represented by the analytic expression of the coordinate. It is certainly true that the element in $D^{1}(M)$ can be represented by the analytic expression of the coordinates.

**Definition 10.2.** $Y(t)$ is a tangent vector of point $y(t)$ on the manifold $M$, $Y(t) \in T(M)$. If $Y(t)$ relies on $t$, it will be called the vector field of point $y(t)$.

$M$ is an $m$-dimensional $C^k$ manifold, $p \in M$, and $T_p \subset M$ is the tangent space of point $p$ on $M$. The $(r, s)$ tensor space in vector space $T_p(M)$ can be represented by $T_{s,p}^r(M)$, and we have:

$$
T_{s}^{r}(M) = \bigcup_{p \in M} T_{s,p}^{r}(M) \quad (10.10)
$$

$(U, \phi, x^{i})$ is a coordinate graph on $M$. $\{(dx^{i})_{p}\}$, $1 \leqslant i \leqslant m$, is a set of dual basis of $T_{p}(M)$. Then, $\Phi_{p} \in T_{s,p}^{r}(M)$ can be represented as:

$$
\Phi_{p} = \Phi_{i_{1}...i_{r}}^{j_{1}...j_{s}}\left(\frac{\partial}{\partial x^{i_{1}}}\right)_{p} \otimes \cdots \otimes\left(\frac{\partial}{\partial x^{i_{r}}}\right)_{p} \otimes (dx^{j_{1}})_{p} \otimes \cdots \otimes (dx^{j_{s}})_{p} \quad (10.11)
$$

Here, $\tilde{U} = \{\Phi_p \in T_{s,p}^{r}(M) \mid p \in U\}$ and $\tilde{\phi}: \tilde{U} \rightarrow \phi(U \times R^{m^{s+r}})$.

Hence, we have:

$$
\Phi_{p} \mapsto (x^{i}(p)\Phi_{i_{1},...,i_{r}}^{j_{1},...,j_{s}}), 1 \leqslant i, i_{1},...,i_{r}, j_{1},...,j_{s} \leqslant m. \quad (10.12)
$$

For arbitrary open set $A \subset \phi(U)$, $B \subset R^{m^{s+r}}$, we define $\tilde{\phi}^{-1}(A \times B) \subset T_{s}^{r}(M)$. Naturally, we have a map:

$$
\pi: T_{s}^{r}(M) \rightarrow M, \quad \Phi_{p} \mapsto p. \quad (10.13)
$$

**Theorem 10.1.**

M is an m-dimensional $C^k$ manifold. There is a topological structure in $T_s^r(M)$ that makes each coordinate graph $(U, \mathbf{p}) : \tilde{U} = \pi^{-1}(U)$ be the open set in $T_s^r(M)$, and $\phi : \tilde{U} \rightarrow \phi(U) \times R^{m^{s+r}}$ be a homeomorphic structure. The coordinate graphs $(\{\tilde{U}, \phi\})$ determine a $C^{k-1}$ differential structure in $T_s^r(M)$ and makes $T_s^r(M)$ an $m+m^{s+r}$ dimensional differential manifold.

$(T_s^r(M), \mathbf{x}, M)$ is a $(r, s)$ tensor bundle on M, $T_s^r(M)$ is called a full space, M is called a bottom space, $\pi$ is called a projection, and $T_s^r(M)$ is called a fibre or the $(r, s)$ tensor bundle on M.

In particular, $\Lambda^r T_p^*(M)$ is the r-order antisymmetric covariant tensor space, and we have:

$$
\Lambda^r T^*(M) = \bigcup_{p \in M} \Lambda^r T_p^*(M) \quad (10.14)
$$

Here, we have a naturally $C^{k-1}$ differential structure to build a $m+(m/s)$ dimensional $C^{k-1}$ manifold. $\Lambda^r T^*(M)$ is the exterior derivative form bundle of degree r, or form bundle of degree r.

The concept of the generalised vector field is as follows:

**Definition 10.3.**

There is an $(r, s)$ tensor field $\Phi$ on $C^k$ manifold M, and the tensor field is a map: $\Phi : M \rightarrow T_s^r(M)$. The tensor flow has $\pi \circ \Phi = I$, where I represents the identity mapping, $\Phi : \mathbf{p} \mapsto \Phi_{\mathbf{p}} \in T^r_{s,p}(M)$. A $(r, s)$ tensor field can be called a cross section on the tensor bundle $T_s^r(M)$.

$(U, \phi, \mathbf{x}')$ is a coordinate graph on M, and the $(r, s)$ tensor field can be locally represented as

$$
\Phi(\mathbf{x}) = \Phi^{i_1 ... i_r}_{j_1 ... j_s}(\mathbf{x}) \frac{\partial}{\partial \mathbf{x}^{i_1}} \otimes ... \otimes \frac{\partial}{\partial \mathbf{x}^{i_r}} \otimes d\mathbf{x}^{j_1} \otimes ... \otimes d\mathbf{x}^{j_s} \quad (10.15)
$$

If $\Phi^{i_1 ... i_r}_{j_1 ... j_s}(\mathbf{x})$ is $C^k$ in each coordinate graph, $1 \leq i, i_1, \dots, i_r, j_1, \dots, j_s \leq m$, we can call $\Phi$ the $C^k$ tensor field. Obviously, the character of $\Phi$ is not related to the local coordinate system. The transformation formula of the component parts of $\Phi$ is

$$
\Phi^{i_1 ... i_r}_{j_1 ... j_s}(\mathbf{x}') = \Phi^{h_1 ... h_r}_{k_1 ... k_s} \frac{\partial \mathbf{x}^{i_1}}{\partial \mathbf{x}^{h_1}} ... \frac{\partial \mathbf{x}^{i_r}}{\partial \mathbf{x}^{h_r}} \frac{\partial \mathbf{x}^{k_1}}{\partial \mathbf{x}^{j_1}} ... \frac{\partial \mathbf{x}^{k_s}}{\partial \mathbf{x}^{j_s}} \quad (10.16)
$$

Here the set of smooth $(r, s)$ on M is $F_s^r(M)$.

### 10.2.2 Reduction model based on the tensor field

In many specific problems, the real data can be obtained easily. However, the hidden information of the data cannot be obtained easily, which means that we need to analyse the data or extract the effective information. The image sample includes multiple concept hierarchies, from texture to abstract semantics. The images are usually represented by points in high-dimensional space, which makes it difficult to extract useful
