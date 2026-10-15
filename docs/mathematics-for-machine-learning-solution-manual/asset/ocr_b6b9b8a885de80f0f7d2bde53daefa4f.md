3.5 Consider the Euclidean vector space \(\mathbb{R}^5\) with the dot product. A subspace \(U \subseteq \mathbb{R}^5\) and \(x \in \mathbb{R}^5\) are given by

$$U=\operatorname{span}\left\{\begin{bmatrix}0\\-1\\2\\0\\2\end{bmatrix},\begin{bmatrix}1\\-3\\1\\-1\\2\end{bmatrix},\begin{bmatrix}-3\\4\\1\\2\\1\end{bmatrix},\begin{bmatrix}-1\\-3\\5\\0\\7\end{bmatrix}\right\},\qquad x=\begin{bmatrix}-1\\-9\\-1\\4\\1\end{bmatrix}.$$

a. Determine the orthogonal projection \(\pi_U(x)\) of \(x\) onto \(U\)

First, we determine a basis of \(U\). Writing the spanning vectors as the columns of a matrix \(A\), we use Gaussian elimination to bring \(A\) into (reduced) row echelon form:

$$\begin{bmatrix}1&0&0&1\\0&1&0&2\\0&0&1&1\\0&0&0&0\\0&0&0&0\end{bmatrix}$$

From here, we see that the first three columns are pivot columns, i.e., the first three vectors in the generating set of \(U\) form a basis of \(U\):

$$U=\operatorname{span}\left\{\begin{bmatrix}0\\-1\\2\\0\\2\end{bmatrix},\begin{bmatrix}1\\-3\\1\\-1\\2\end{bmatrix},\begin{bmatrix}-3\\4\\1\\2\\1\end{bmatrix}\right\}.$$

Now, we define

$$B=\begin{bmatrix}0&1&-3\\-1&-3&4\\2&1&1\\0&-1&2\\2&2&1\end{bmatrix},$$

where we define three basis vectors \(b_i\) of \(U\) as the columns of \(B\) for \(1\leq i\leq 3\).

We know that the projection of \(x\) on \(U\) exists and we define \(p:=\pi_U(x)\). Moreover, we know that \(p\in U\). We define \(\lambda:=[\lambda_1,\lambda_2,\lambda_3]^T\in\mathbb{R}^3\), such that \(p\) can be written as \(p=\sum_{i=1}^{3}\lambda_i b_i=B\lambda\).

As \(p\) is the orthogonal projection of \(x\) onto \(U\), then \(x-p\) is orthogonal to all the basis vectors of \(U\), so that

$$B^T(x-B\lambda)=0.$$

Therefore,

$$B^TB\lambda=B^Tx.$$

Solving in \(\lambda\) the inhomogeneous system \(B^TB\lambda=B^Tx\) gives us a single