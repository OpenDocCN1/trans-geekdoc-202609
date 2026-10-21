To find the adjoint of a matrix, take the transpose of the cofactor. The cofactor of $C^{-1}B - E_1 I$ is

Cofactor of
$C^{-1}B - E_1 I = \begin{bmatrix}1+1 & 1+2 \\ (-1)(-0.4007) & (-1)(2.071) \\ 2+1 & 2+2 \\ (-1)(0.0268) & (-1)(-0.1384)\end{bmatrix}$

$= \begin{bmatrix}-0.4007 & -2.071 \\ -0.0268 & -0.1384\end{bmatrix}$

and the transpose is
$\begin{bmatrix}-0.4007 & -0.0268 \\ -2.071 & -0.1384\end{bmatrix}'$

hence the eigenvector of $C^{-1}B$, with larger elements set equal to unity, is
$A_1 = \begin{bmatrix}-0.4007 / -2.071 \\ 1\end{bmatrix} = \begin{bmatrix}0.1935 \\ 1\end{bmatrix}$

when the vector of regression weights obtained earlier is similarly rescaled, we find
$a = \begin{bmatrix}0.63697065 / 3.2359 \\ 1\end{bmatrix} = \begin{bmatrix}0.1968 \\ 1\end{bmatrix}$

This agrees, within rounding errors, with the $A_1$ just obtained by the general method of discriminant analysis mentioned above. Alternatively, the non-zero root, $E_1 = 0.5391$, can be substituted into equation (77.11), yielding
$\begin{bmatrix}-0.4007 - 0.5391 & -0.0268 \\ -2.071 & -0.1384 - 0.5391\end{bmatrix} \begin{bmatrix}a_1 \\ a_2\end{bmatrix} = 0.$
(77.16)

Equation (77.12) implies that
$-0.1384 a_1 + 0.0268 a_2 = 0,$
$2.071 a_1 - 0.4007 a_2 = 0,$

that is,
$2.071 a_1 - 0.4007 a_2 = 0.$