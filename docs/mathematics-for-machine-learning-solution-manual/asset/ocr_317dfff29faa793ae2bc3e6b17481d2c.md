E3 has dimension 1 (it could not be anything else anyway, as justified above) and

$E_1 = \text{span}\begin{bmatrix}-1\\-1\\-1\end{bmatrix}.$

(iv) Therefore, we can find a new basis $P$ as the concatenation of the spanning vectors of the eigenspaces. If we identify the matrix

$\boldsymbol{P} = \begin{bmatrix}-1 & 1 & 1\\-1 & -1 & 0\\-1 & 0 & -1\end{bmatrix},$

whose columns are composed of the basis vectors of basis $P$, then our endomorphism will have the diagonal form: $\boldsymbol{D} = \text{diag}[3, 0, 0]$ with respect to this new basis. As a reminder, $\text{diag}[3, 0, 0]$ refers to the $3 \times 3$ diagonal matrix with $3, 0, 0$ as values on the diagonal. Note that the diagonal form is not unique and depends on the order of the eigenvectors in the new basis. For example, we can define another matrix $\boldsymbol{Q}$ composed of the same vectors as $\boldsymbol{P}$ but in a different order:

$\boldsymbol{Q} = \begin{bmatrix}1 & -1 & 1\\-1 & -1 & 0\\0 & -1 & -1\end{bmatrix}.$

If we use this matrix, our endomorphism would have another diagonal form: $\boldsymbol{D}' = \text{diag}[0, 3, 0]$. Sceptical students can check that $\boldsymbol{Q}^{-1} \boldsymbol{A} \boldsymbol{Q} = \boldsymbol{D}'$ and $\boldsymbol{P}^{-1} \boldsymbol{A} \boldsymbol{P} = \boldsymbol{D}$.

c.

$\boldsymbol{A} = \begin{bmatrix}5 & 4 & 2 & 1\\0 & 1 & -1 & -1\\-1 & -1 & 3 & 0\\1 & 1 & -1 & 2\end{bmatrix}$

$p(\lambda) = (\lambda - 1)(\lambda - 2)(\lambda - 4)^2$

$E_1 = \text{span}\begin{bmatrix}-1\\1\\0\\0\end{bmatrix},\quad E_2 = \text{span}\begin{bmatrix}1\\-1\\0\\1\end{bmatrix},\quad E_4 = \text{span}\begin{bmatrix}1\\0\\-1\\1\end{bmatrix}.$

Here, we see that $\dim(E_4) = 1 \neq 2$ (which is the algebraic multiplicity of the eigenvalue 4). Therefore, $\boldsymbol{A}$ cannot be diagonalized.

d.

$\boldsymbol{A} = \begin{bmatrix}5 & -6 & -6\\-1 & 4 & 2\\3 & -6 & -4\end{bmatrix}$