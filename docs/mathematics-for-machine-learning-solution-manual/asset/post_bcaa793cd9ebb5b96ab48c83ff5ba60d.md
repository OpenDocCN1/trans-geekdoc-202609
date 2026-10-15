
Adding and subtracting both equations gives us

$$
\begin{cases}
\Phi(b_1 + b_2) + \Phi(b_1 - b_2) = 2c_1 + 4c_3\\
\Phi(b_1 + b_2) - \Phi(b_1 - b_2) = -2c_1 + 2c_2 - 2c_3
\end{cases}
$$

As Φ is linear, we obtain

$$
\begin{cases}
\Phi(2b_1) = 2c_1 + 4c_3\\
\Phi(2b_2) = -2c_1 + 2c_2 - 2c_3
\end{cases}
$$

And by linearity of Φ again, the system of equations gives us

$$
\begin{cases}
\Phi(b_1) = c_1 + 2c_3\\
\Phi(b_2) = -c_1 + c_2 - c_3
\end{cases}.
$$

Therefore, the transformation matrix of A_Φ with respect to the bases B and C is

$$A_\Phi = \begin{bmatrix}1 & -1\\0 & 1\\2 & -1\end{bmatrix}.$$

- e. Determine A', the transformation matrix of Φ with respect to the bases B' and C'.

We have:

$$A' = P_2 A P_1 = \begin{bmatrix}1 & 0 & 1\\2 & -1 & 0\\-1 & 2 & -1\end{bmatrix}\begin{bmatrix}1 & -1\\0 & 1\\2 & -1\end{bmatrix}\begin{bmatrix}4 & 0\\6 & -1\end{bmatrix}=\begin{bmatrix}0 & 2\\-10 & 3\\12 & -4\end{bmatrix}.$$

- f. Let us consider the vector x ∈ ℝ² whose coordinates in B' are [2,3]ᵀ. In other words, x = 2b₁' + 3b₂'.

- (i) Calculate the coordinates of x in B. By definition of P₁, x can be written in B as
$$
P_1\begin{bmatrix}2\\3\end{bmatrix}=\begin{bmatrix}4 & 0\\6 & -1\end{bmatrix}\begin{bmatrix}2\\3\end{bmatrix}=\begin{bmatrix}8\\9\end{bmatrix}
$$

- (ii) Based on that, compute the coordinates of Φ(x) expressed in C. Using the transformation matrix A of Φ with respect to the bases B and C, we get the coordinates of Φ(x) in C with
$$
A\begin{bmatrix}8\\9\end{bmatrix}=\begin{bmatrix}1 & -1\\0 & 1\\2 & -1\end{bmatrix}\begin{bmatrix}8\\9\end{bmatrix}=\begin{bmatrix}-1\\9\\7\end{bmatrix}
$$

- (iii) Then, write Φ(x) in terms of c₁', c₂', c₃'. Going back to the basis C' thanks to the matrix P₂ gives us the expression of Φ(x) in C'
$$
P_2\begin{bmatrix}-1\\9\\7\end{bmatrix}=\begin{bmatrix}1 & 0 & 1\\2 & -1 & 0\\-1 & 2 & -1\end{bmatrix}\begin{bmatrix}-1\\9\\7\end{bmatrix}=\begin{bmatrix}6\\-11\\12\end{bmatrix}
$$

In other words, Φ(x) = 6c₁' − 11c₂' + 12c₃'.

- (iv) Use the representation of x in B' and the matrix A' to find this result directly.

We can calculate Φ(x) in C directly:

$A' \begin{bmatrix}2\\3\end{bmatrix} = \begin{bmatrix}0 & 2\\ -10 & 3\\ 12 & -4\end{bmatrix} \begin{bmatrix}2\\3\end{bmatrix} = \begin{bmatrix}6\\ -11\\ 12\end{bmatrix}$

## Analytic Geometry
## Exercises

### 3.1 Show that $\langle\cdot,\cdot\rangle$ defined for all $\boldsymbol{x} = [x_1, x_2]^\top \in \mathbb{R}^2$ and $\boldsymbol{y} = [y_1, y_2]^\top \in \mathbb{R}^2$ by

$\langle\boldsymbol{x}, \boldsymbol{y}\rangle := x_1 y_1 - (x_1 y_2 + x_2 y_1) + 2(x_2 y_2)$

is an inner product.

We need to show that $\langle\boldsymbol{x}, \boldsymbol{y}\rangle$ is a symmetric, positive definite bilinear form.

- Let $\boldsymbol{x} := [x_1, x_2]^\top$, $\boldsymbol{y} = [y_1, y_2]^\top \in \mathbb{R}^2$. Then,

$\langle\boldsymbol{x}, \boldsymbol{y}\rangle = x_1 y_1 - (x_1 y_2 + x_2 y_1) + 2 x_2 y_2$
$= y_1 x_1 - (y_1 x_2 + y_2 x_1) + 2 y_2 x_2 = \langle\boldsymbol{y}, \boldsymbol{x}\rangle$,

where we exploited the commutativity of addition and multiplication in $\mathbb{R}$. Therefore, $\langle\cdot,\cdot\rangle$ is symmetric.
- It holds that

$\langle\boldsymbol{x}, \boldsymbol{x}\rangle = x_1^2 - (2 x_1 x_2) + 2 x_2^2 = (x_1 - x_2)^2 + x_2^2$.

This is a sum of positive terms for $\boldsymbol{x} \neq \mathbf{0}$. Moreover, this expression shows that if $\langle\boldsymbol{x}, \boldsymbol{x}\rangle = 0$ then $x_2 = 0$ and then $x_1 = 0$, i.e., $\boldsymbol{x} = \mathbf{0}$. Hence, $\langle\cdot,\cdot\rangle$ is positive definite.
- In order to show that $\langle\cdot,\cdot\rangle$ is bilinear (linear in both arguments), we will simply show that $\langle\cdot,\cdot\rangle$ is linear in its first argument. Symmetry will ensure that $\langle\cdot,\cdot\rangle$ is bilinear. Do not duplicate the proof of linearity in both arguments.
Let $\boldsymbol{z} = [z_1, z_2]^\top \in \mathbb{R}^2$ and $\lambda \in \mathbb{R}$. Then,

$\langle\boldsymbol{x} + \boldsymbol{y}, \boldsymbol{z}\rangle = (x_1 + y_1)z_1 - ((x_1 + y_1)z_2 + (x_2 + y_2)z_1) + 2(x_2 + y_2)z_2$
$= x_1 z_1 - (x_1 z_2 + x_2 z_1) + 2(x_2 z_2) + y_1 z_1 - (y_1 z_2 + y_2 z_1) + 2(y_2 z_2)$
$= \langle\boldsymbol{x}, \boldsymbol{z}\rangle + \langle\boldsymbol{y}, \boldsymbol{z}\rangle$
$\langle\lambda\boldsymbol{x}, \boldsymbol{y}\rangle = \lambda x_1 y_1 - (\lambda x_1 y_2 + \lambda x_2 y_1) + 2(\lambda x_2 y_2)$
$= \lambda(x_1 y_1 - (x_1 y_2 + x_2 y_1) + 2(x_2 y_2)) = \lambda \langle\boldsymbol{x}, \boldsymbol{y}\rangle$

Thus, $\langle\cdot,\cdot\rangle$ is linear in its first variable. By symmetry, it is bilinear. Overall, $\langle\cdot,\cdot\rangle$ is an inner product.

### 3.2

Consider ℝ² with ⟨·,·⟩ defined for all x and y in ℝ² as
⟨x, y⟩ := xᵀ [[2,0],[1,2]] y  :=: A

Is ⟨·,·⟩ an inner product?
Let us define x and y as
x = [1;0], y = [0;1].

We have ⟨x, y⟩ = 0 but ⟨y, x⟩ = 1, i.e., ⟨·,·⟩ is not symmetric. Therefore, it is not an inner product.

### 3.3

Compute the distance between
x = [1;2;3], y = [-1;-1;0]
using

- a. ⟨x, y⟩ := xᵀ y
- b. ⟨x, y⟩ := xᵀ A y, A := [[2,1,0],[1,3,-1],[0,-1,2]]

The difference vector is
z = x - y = [2;3;4].

- a. ||z|| = √(zᵀ z) = √29
- b. ||z|| = √(zᵀ A z) = √55

### 3.4

Compute the angle between
x = [1;2], y = [-1;-1]
using

- a. ⟨x, y⟩ := xᵀ y
- b. ⟨x, y⟩ := xᵀ B y, B := [[2,1],[1,3]]

It holds that
cos ω = ⟨x, y⟩ / (||x|| ||y||),
where ω is the angle between x and y.

- a. cos ω = -3 / (√5 √2) = -3 / √10 ≈ 2.82 rad = 161.5°
- b. cos ω = (xᵀ B y) / (√(xᵀ B x) √(yᵀ B y)) = -11 / (√18 √7) = -11 / √126 ≈ 1.66 rad = 95°

### 3.5 Consider the Euclidean vector space $\mathbb{R}^5$ with the dot product. A subspace $U \subseteq \mathbb{R}^5$ and $x \in \mathbb{R}^5$ are given by

$$U=\operatorname{span}\left\{\begin{bmatrix}0\\-1\\2\\0\\2\end{bmatrix},\begin{bmatrix}1\\-3\\1\\-1\\2\end{bmatrix},\begin{bmatrix}-3\\4\\1\\2\\1\end{bmatrix},\begin{bmatrix}-1\\-3\\5\\0\\7\end{bmatrix}\right\},\qquad x=\begin{bmatrix}-1\\-9\\-1\\4\\1\end{bmatrix}.$$

a. Determine the orthogonal projection $\pi_U(x)$ of $x$ onto $U$

First, we determine a basis of $U$. Writing the spanning vectors as the columns of a matrix $A$, we use Gaussian elimination to bring $A$ into (reduced) row echelon form:

$$\begin{bmatrix}1&0&0&1\\0&1&0&2\\0&0&1&1\\0&0&0&0\\0&0&0&0\end{bmatrix}$$

From here, we see that the first three columns are pivot columns, i.e., the first three vectors in the generating set of $U$ form a basis of $U$:

$$U=\operatorname{span}\left\{\begin{bmatrix}0\\-1\\2\\0\\2\end{bmatrix},\begin{bmatrix}1\\-3\\1\\-1\\2\end{bmatrix},\begin{bmatrix}-3\\4\\1\\2\\1\end{bmatrix}\right\}.$$

Now, we define

$$B=\begin{bmatrix}0&1&-3\\-1&-3&4\\2&1&1\\0&-1&2\\2&2&1\end{bmatrix},$$

where we define three basis vectors $b_i$ of $U$ as the columns of $B$ for $1\leq i\leq 3$.

We know that the projection of $x$ on $U$ exists and we define $p:=\pi_U(x)$. Moreover, we know that $p\in U$. We define $\lambda:=[\lambda_1,\lambda_2,\lambda_3]^T\in\mathbb{R}^3$, such that $p$ can be written as $p=\sum_{i=1}^{3}\lambda_i b_i=B\lambda$.

As $p$ is the orthogonal projection of $x$ onto $U$, then $x-p$ is orthogonal to all the basis vectors of $U$, so that

$$B^T(x-B\lambda)=0.$$

Therefore,

$$B^TB\lambda=B^Tx.$$

Solving in $\lambda$ the inhomogeneous system $B^TB\lambda=B^Tx$ gives us a single

solution

$$\lambda=\begin{bmatrix}-3\\4\\1\end{bmatrix}$$

and, therefore, the desired projection

$$p=B\lambda=\begin{bmatrix}1\\-5\\-1\\-2\\3\end{bmatrix}\in U.$$

b.  Determine the distance $d(x,U)$

The distance is simply the length of $x-p$:

$$\|x-p\|=\left\|\begin{bmatrix}2\\4\\0\\-6\\2\end{bmatrix}\right\|=\sqrt{60}$$

### 3.6 Consider $\mathbb{R}^3$ with the inner product

$$\langle x,y\rangle:=x^T\begin{bmatrix}2&1&0\\1&2&-1\\0&-1&2\end{bmatrix}y.$$

Furthermore, we define $e_1,e_2,e_3$ as the standard/canonical basis in $\mathbb{R}^3$.

a.  Determine the orthogonal projection $\pi_U(e_2)$ of $e_2$ onto

$$U=\operatorname{span}[e_1,e_3].$$

Hint: Orthogonality is defined through the inner product.

Let $p=\pi_U(e_2)$. As $p\in U$, we can define $\Lambda=(\lambda_1,\lambda_3)\in\mathbb{R}^2$ such that $p$ can be written $p=U\Lambda$. In fact, $p$ becomes $p=\lambda_1e_1+\lambda_3e_3=[\lambda_1,0,\lambda_3]^T$ expressed in the canonical basis.

Now, we know by orthogonal projection that

$$p=\pi_U(e_2)\ \Longrightarrow\ (p-e_2)\perp U$$

$$\Longrightarrow\begin{bmatrix}\langle p-e_2,e_1\rangle\\\langle p-e_2,e_3\rangle\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}$$

$$\Longrightarrow\begin{bmatrix}\langle p,e_1\rangle-\langle e_2,e_1\rangle\\\langle p,e_3\rangle-\langle e_2,e_3\rangle\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}$$

We compute the individual components as

$$\langle p,e_1\rangle=\begin{bmatrix}\lambda_1&0&\lambda_3\end{bmatrix}\begin{bmatrix}2&1&0\\1&2&-1\\0&-1&2\end{bmatrix}\begin{bmatrix}1\\0\\0\end{bmatrix}=2\lambda_1$$
