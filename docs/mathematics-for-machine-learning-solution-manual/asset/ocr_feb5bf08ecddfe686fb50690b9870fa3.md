# 4.10 Find the rank-1 approximation of

**A** = $\begin{bmatrix}3 & 2 & 2 \\ 2 & 3 & -2\end{bmatrix}$

To find the rank-1 approximation we apply the SVD to **A** (as in Exercise 4.7) to obtain

**U** = $\begin{bmatrix}\frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}}\end{bmatrix}$

**V** = $\begin{bmatrix}\frac{1}{\sqrt{2}} & -\frac{1}{3\sqrt{2}} & -\frac{2}{3} \\ \frac{1}{\sqrt{2}} & \frac{1}{3\sqrt{2}} & \frac{2}{3} \\ 0 & -\frac{2\sqrt{2}}{3} & \frac{1}{3}\end{bmatrix}$.

We apply the construction rule for rank-1 matrices

**A**$_i$ = **u**$_i$**v**$_i^\top$.

We use the largest singular value ($\sigma_1$ = 5, i.e., $i$ = 1 and the first column vectors of the **U** and **V** matrices, respectively):

**A**$_1$ = **u**$_1$**v**$_1^\top$ = $\begin{bmatrix}\frac{1}{\sqrt{2}} \\ \frac{1}{\sqrt{2}}\end{bmatrix}$ $\begin{bmatrix}\frac{1}{\sqrt{2}} & \frac{1}{\sqrt{2}} & 0\end{bmatrix}$ = $\frac{1}{2}$ $\begin{bmatrix}1 & 1 & 0 \\ 1 & 1 & 0\end{bmatrix}$.

# 4.11 Show that for any **A** $\in \mathbb{R}^{m\times n}$ the matrices **A**$^\top$ **A** and **A** **A**$^\top$ possess the same nonzero eigenvalues.

Let us assume that $\lambda$ is a nonzero eigenvalue of **A** **A**$^\top$ and $x$ is an eigenvector belonging to $\lambda$. Thus, the eigenvalue equation

(**A** **A**$^\top$) $x$ = $\lambda x$

can be manipulated by left multiplying by **A**$^\top$ and pulling on the right-hand side the scalar factor $\lambda$ forward. This yields

**A**$^\top$ (**A** **A**$^\top$) $x$ = **A**$^\top$ ($\lambda x$) = $\lambda$ (**A**$^\top$ $x$)