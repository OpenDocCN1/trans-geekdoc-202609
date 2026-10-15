$$ = \begin{vmatrix}2&0&1&2&0\\0&-1&-1&-1&1\\0&0&1&0&3\\0&0&0&1&-7\\0&0&0&-1&4\end{vmatrix} = \begin{vmatrix}2&0&1&2&0\\0&-1&-1&-1&1\\0&0&1&0&3\\0&0&0&1&-7\\0&0&0&0&-3\end{vmatrix}=6.$$

Alternatively, we can apply the Laplace expansion and arrive at the same solution:

$$\begin{vmatrix}2&0&1&2&0\\2&-1&0&1&1\\0&1&2&1&2\\-2&0&2&-1&2\\2&0&0&1&1\end{vmatrix}= \begin{vmatrix}2&0&1&2&0\\0&-1&-1&-1&1\\0&1&2&1&2\\0&0&3&1&2\\0&0&-1&-1&1\end{vmatrix}$$

$$\stackrel{1\text{st col.}}{=}(-1)^{1+1}2\cdot\begin{vmatrix}-1&-1&-1&1\\1&2&1&2\\0&3&1&2\\0&-1&-1&1\end{vmatrix}.$$

If we now subtract the fourth row from the first row and multiply (−2) times the third column to the fourth column we obtain

$$2\begin{vmatrix}-1&0&0&0\\1&2&1&0\\0&3&1&0\\0&-1&-1&3\end{vmatrix}\stackrel{1\text{st row}}{=}-2\begin{vmatrix}2&1&0\\3&1&0\\-1&-1&3\end{vmatrix}\stackrel{3\text{rd col.}}{=}(-2)\cdot3(-1)^{3+3}\cdot\begin{vmatrix}2&1\\3&1\end{vmatrix}=6.$$

# 4.3 Compute the eigenspaces of

+   a.

$$A := \begin{bmatrix}1&0\\1&1\end{bmatrix}$$

+   b.

$$B := \begin{bmatrix}-2&2\\2&1\end{bmatrix}$$

+   a. For

$$A = \begin{bmatrix}1&0\\1&1\end{bmatrix}$$

+   (i) Characteristic polynomial: $p(\lambda)=|A-\lambda I_2|=\begin{vmatrix}1-\lambda&0\\1&1-\lambda\end{vmatrix}=(1-\lambda)^2$. Therefore $\lambda=1$ is the only root of $p$ and, therefore, the only eigenvalue of $A$

+   (ii) To compute the eigenspace for the eigenvalue $\lambda=1$, we need to compute the null space of $A-I$: $(A-1\cdot I)x=0 \iff \begin{bmatrix}0&0\\1&0\end{bmatrix}x=0 \Rightarrow E_1=\begin{bmatrix}0\\1\end{bmatrix}$