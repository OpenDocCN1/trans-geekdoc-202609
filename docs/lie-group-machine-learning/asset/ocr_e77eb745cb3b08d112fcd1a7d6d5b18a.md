descending order, i.e., $\sigma_1 = \lambda_{\max}, \dots, \sigma_n = \lambda_{\min}$ ($n$ is the dimension of $X$). Let vector $\omega = (\omega_1, \omega_2, \dots, \omega_n)^T$ satisfy $\|\omega\|_2 = 1$. Then, matrix

$H(\omega) = I - 2\omega\omega^T = \begin{bmatrix} 1 - 2\omega_1^2 & -2\omega_1\omega_2 & \dots & -2\omega_1\omega_n \\ -2\omega_2\omega_1 & 1 - 2\omega_2^2 & \dots & -2\omega_2\omega_n \\ \vdots & \vdots & \vdots & \vdots \\ -2\omega_n\omega_1 & -2\omega_n\omega_2 & \dots & 1 - 2\omega_n^2 \end{bmatrix}\ .$

The matrix is an elementary reflection matrix. It is easy to prove that the elementary reflection matrix $H$ is a symmetric matrix ($H^T = H$), an orthogonal matrix ($H^T H = I$), and an involution matrix ($H^2 = I$). $\square$

**Theorem 3.10.** Let $x$ and $y$ be two unequal $n$-dimensional vectors, and $\|x\|_2 = \|y\|_2$. Then, the primary reflection matrix $H = I - \omega\omega^T$ can make $Hx = y$, where $\omega = x - y/\|x - y\|_2$ [22].

> From Theorem 3.10, it is not difficult to see that for a nonzero $n$-dimensional vector $x = (x_1, \dots, x_n)^T$, where $a = \|x\|_2$, the elementary reflection array $H = I - \omega\omega^T$ can make $Hx = ae_1$, where $e_1 = (1, 0, \dots, 0)^T$, $\rho = \|x - ae_1\|_2$.

> The following describes how the real matrix $A$ seeks the orthogonal matrix $H$ so that $HMH^T$ is the upper triangular matrix. Let

$A = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \vdots & \vdots \\ a_{n1} & a_{n2} & \dots & a_{nn} \end{bmatrix} = \begin{bmatrix} a_{11} & A_{12}^{(1)} \\ \Lambda_{21}^{(1)} & A_{22}^{(1)} \end{bmatrix}\ .$

> In the first step, we may wish to set $\lambda_{21}^{(1)} \neq 0$. Otherwise, this step will not be reduced. Set the first column vector of $A$ as

$V^{(1)} = (a_{11}^{(1)}, a_{21}^{(1)}, \dots, a_{n1}^{(1)})^T = (a_{11}, a_{21}, \dots, a_{n1})\ .

> Select the elementary reflection matrix $H^{(1)}$ as

$H^{(1)} = I - 2\omega^{(1)}(\omega^{(1)})^T$

> where

$\begin{cases} \lambda_1 = \|V^{(1)}\|_2 \\ E^{(1)} = (1, 0, \dots, 0)^T \\ \rho_1 = \|V^{(1)} - \lambda_1 E^{(1)}\| \\ \omega^{(1)} = \frac{(V^{(1)} - \lambda_1 E^{(1)})}{\rho_1} \end{cases}\ .

> Then, with $A$ after $H^{(1)}$ transformation, we get

$H^{(1)} A = \begin{bmatrix} \sigma_1 & a_{12}^{(2)} & \dots & a_{1n}^{(2)} \\ 0 & a_{22}^{(2)} & \dots & a_{2n}^{(2)} \\ \vdots & \vdots & \ddots & \vdots \\ 0 & a_{n2}^{(2)} & \dots & a_{nn}^{(2)} \end{bmatrix} = A^{(2)}\ .