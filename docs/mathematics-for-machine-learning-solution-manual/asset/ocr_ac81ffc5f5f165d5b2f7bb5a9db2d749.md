$$\begin{bmatrix}1&0&0&0&-1&|&3\\0&1&0&0&-2&|&0\\0&0&-1&0&0&|&0\\0&0&0&1&-1&|&-1\\0&0&0&0&-1&|&0\end{bmatrix}$$

The right-hand side of the system yields us a particular solution while the columns corresponding to the −1 pivots are the directions of the solution space. We then obtain the set of all possible solutions as

$\mathcal{S} := \{ x \in \mathbb{R}^6 : x = \begin{bmatrix}3\\0\\0\\-1\\0\end{bmatrix} + \lambda_1 \begin{bmatrix}0\\0\\-1\\0\\0\end{bmatrix} + \lambda_2 \begin{bmatrix}-1\\-2\\0\\-1\\-1\end{bmatrix} \mid \lambda_1,\lambda_2 \in \mathbb{R} \}$

# 2.6 Using Gaussian elimination, find all solutions of the inhomogeneous equation system $Ax = b$ with

$\boldsymbol{A} = \begin{bmatrix}0&1&0&0&1&0\\0&0&0&1&1&0\\0&1&0&0&0&1\end{bmatrix}, \quad \boldsymbol{b} = \begin{bmatrix}2\\-1\\1\end{bmatrix}$.

We start by determining the reduced row echelon form of the augmented matrix $[A|b]$.

$$\begin{bmatrix}0&1&0&0&1&0&|&2\\0&0&0&1&1&0&|&-1\\0&1&0&0&0&1&|&1\end{bmatrix} -R_1 \sim \begin{bmatrix}0&1&0&0&1&0&|&2\\0&0&0&1&1&0&|&-1\\0&0&0&0&-1&1&|&-1\end{bmatrix} +R_3 \sim \begin{bmatrix}0&1&0&0&0&1&|&1\\0&0&0&1&0&1&|&-2\\0&0&0&0&1&-1&|&1\end{bmatrix}$$

This augmented matrix is now in reduced row echelon form. Applying the “Minus-1 trick” gives us the following augmented matrix:

$$\begin{bmatrix}-1&0&0&0&0&0&|&0\\0&1&0&0&0&1&|&1\\0&0&-1&0&0&0&|&0\\0&0&0&1&0&1&|&-2\\0&0&0&0&1&-1&|&1\\0&0&0&0&0&-1&|&0\end{bmatrix}$$

The right-hand side of this augmented matrix gives us a particular solution while the columns corresponding to the −1 pivots are the span the solution