b. For

$\boldsymbol{A}=\begin{bmatrix}1&1&0&0\\0&0&0&0\\0&0&0&0\\0&0&0&0\end{bmatrix}$

(i) Compute the eigenvalues as the roots of the characteristic polynomial

$p(\lambda)=\det(\boldsymbol{A}-\lambda\boldsymbol{I})=(1-\lambda)\lambda^{3}$
$=\begin{vmatrix}1-\lambda&1&0&0\\0&-\lambda&0&0\\0&0&-\lambda&0\\0&0&0&-\lambda\end{vmatrix}=-(1-\lambda)\lambda^{3}$.

It follows that the eigenvalues are 0 and 1 with algebraic multiplicities 3 and 1, respectively.

(ii) We compute the eigenspaces $E_{0}$ and $E_{1}$, which requires us to determine the null spaces $\boldsymbol{A}-\lambda_{i}\boldsymbol{I}$, where $\lambda_{i}\in\{0,1\}$.

(iii) We compute the eigenspaces $E_{0}$ and $E_{1}$, which requires us to determine the null spaces $\boldsymbol{A}-\lambda_{i}\boldsymbol{I}$, where $\lambda_{i}\in\{0,1\}$. For $E_{0}$, we compute the null space of $\boldsymbol{A}$ and obtain

$E_{0}=\operatorname{span}\left[\begin{bmatrix}1\\-1\\0\\0\end{bmatrix},\begin{bmatrix}0\\0\\1\\0\end{bmatrix},\begin{bmatrix}0\\0\\0\\1\end{bmatrix}\right]$

To determine $E_{1}$, we need to solve $(\boldsymbol{A}-\boldsymbol{I})\boldsymbol{x}=\boldsymbol{0}$

$\begin{bmatrix}0&1&0&0\\0&-1&0&0\\0&0&-1&0\\0&0&0&-1\end{bmatrix}\xrightarrow{+R_{1}|\text{move to }R_{4}\atop\cdot(-1)\atop\cdot(-1)}\begin{bmatrix}0&1&0&0\\0&0&1&0\\0&0&0&1\\0&0&0&0\end{bmatrix}$

From here, we see that $E_{1}=\operatorname{span}\left[\begin{bmatrix}1\\0\\0\\0\end{bmatrix}\right]$.

(iv) Since $\dim(E_{0})+\dim(E_{1})=4=\dim(\mathbb{R}^{4})$, it follows that a diagonal form exists.

# 4.7 Are the following matrices diagonalizable? If yes, determine their diagonal form and a basis with respect to which the transformation matrices are diagonal. If no, give reasons why they are not diagonalizable.

a.

$\boldsymbol{A}=\begin{bmatrix}0&1\\-8&4\end{bmatrix}$