![](bbox=[0.12, 0.1, 0.88, 0.65])

Figure 1.2 Flowchart of MSVD.

e. Further, a modal matrix, $M$, comprising the eigenvector, is computed by diagonalizing $S$.

$M^{\top} \times S \times M = A^{2}$

(1.8)

Here, $A^{2} = \text{diagonal}\(a(1)^{2},\ a(2)^{2}......\ a(mn)^{2})$ have the square of singular values of $S$.

f. Finally, compute the matrix $\bar{I}$ using Eq. (1.9).

$\bar{I} = M^{\top} \times \bar{E}$

(1.9)

Since the first row of $\bar{I}$ contains the largest singular values, it is considered as the approximation sub-band, $\Phi$. The remaining rows are treated as the detailed part of the input image, $\Psi$ [26].