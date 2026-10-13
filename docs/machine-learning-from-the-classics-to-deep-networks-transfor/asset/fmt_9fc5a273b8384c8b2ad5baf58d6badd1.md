
$$
\mathbf{p}_{n} = A\Lambda^{n}A^{-1}\mathbf{p}_{0} = A\begin{bmatrix} 1 & & & \\ & \lambda_{2}^{n} & & \text{O} \\ \text{O} & & \ddots & \\ & & & \lambda_{K}^{n} \\ \end{bmatrix}A^{-1}\mathbf{p}_{0},
$$

![Equation](images/B9780443292385000202/si187.png)

with $\lambda_{k}^{n} \to 0,\ k = 2,\dots,K$ ![Equation](images/B9780443292385000202/si188.png).

Hence,

$$
\mathbf{p}_{\infty} := \lim_{n\to\infty}\mathbf{p}_{n} = P_{\infty}\mathbf{p}_{0},
$$

![Equation](images/B9780443292385000202/si189.png) (14.43)

where

$$
P_{\infty} = A\begin{bmatrix} 1 & & & \\ & 0 & & \text{O} \\ \text{O} & & \ddots & \\ & & & 0 \\ \end{bmatrix}A^{-1} = \mathbf{a}_{1}\mathbf{b}_{1}^{T},
$$

![Equation](images/B9780443292385000202/si190.png) (14.44)

with $\mathbf{a}_{1}$ ![Equation](images/B9780443292385000202/si191.png) being the first eigenvector (first column of $A$), corresponding to $\lambda = 1$ ![Equation](images/B9780443292385000202/si48.png), and $\mathbf{b}_{1}^{T}$ ![Equation](images/B9780443292385000202/si192.png) the first row of $A^{-1}$ ![Equation](images/B9780443292385000202/si193.png). In other words, $P_{\infty}$ ![Equation](images/B9780443292385000202/si194.png) is a rank one matrix. However, it is straightforward to see from Eq. [(14.42)](#Chp014_717-754_B9780443292385000202.xhtml#deq72) ($A^{-1}P = \Lambda A^{-1}$) ![Equation](images/B9780443292385000202/si195.png) that $\mathbf{b}_{1}^{T}$ ![Equation](images/B9780443292385000202/si192.png) is a left eigenvector of $P$, that is,
