Then, we can get Adjoint $A$ as follows:

Adj $A$ = $\begin{bmatrix} -9 & -17 & 28 \\ 3 & 7 & -12 \\ 2 & 2 & -4 \end{bmatrix}$, (77A.17)

The determinant of $A$ we have calculated in Cramer's rule is as follows:

Det $A$ = $\begin{bmatrix} 1 & 3 & -2 \\ 3 & 5 & 6 \\ 2 & 4 & 3 \end{bmatrix}$ = $-4$,

$A^{-1} = \frac{1}{(-4)} \times \begin{bmatrix} -9 & -17 & 28 \\ 3 & 7 & -12 \\ 2 & 2 & -4 \end{bmatrix} = \begin{bmatrix} \frac{9}{4} & \frac{17}{4} & -\frac{28}{4} \\ -\frac{3}{4} & -\frac{7}{4} & 3 \\ -\frac{1}{2} & -\frac{1}{2} & 1 \end{bmatrix}$, (77A.18)

Therefore,

$\begin{bmatrix} x \\ y \\ z \end{bmatrix} = \begin{bmatrix} \frac{9}{4} & \frac{17}{4} & -\frac{28}{4} \\ -\frac{3}{4} & -\frac{7}{4} & 3 \\ -\frac{1}{2} & -\frac{1}{2} & 1 \end{bmatrix} \times \begin{bmatrix} 5 \\ 7 \\ 8 \end{bmatrix} = \begin{bmatrix} \frac{9}{4}\times5+\frac{17}{4}\times7+\left(-\frac{28}{4}\right)\times8 \\ \left(-\frac{3}{4}\right)\times5+\left(-\frac{7}{4}\right)\times7+3\times8 \\ \left(-\frac{1}{2}\right)\times5+\left(-\frac{1}{2}\right)\times7+1\times8 \end{bmatrix} = \begin{bmatrix} -15 \\ 8 \\ 2 \end{bmatrix}$. (77A.19)

# *Method 4: Excel matrix inversion and multiplication*

+   1. Use minverse () function to get the $A$ inverse. By typing “Ctrl + Shift + Enter” together, you will get the inverse of $A$.