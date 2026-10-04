DFT can be seen as a linear transform $F$ taking the column vector $\alpha$ to a column

$$\begin{matrix} \omega_1 & -e^{-2\pi i(0)/n} & -e^{-2\pi i(0)/n} & \dots & \alpha_1 \ \omega_2 & -e^{-2\pi i(1)/n} & -e^{-2\pi i(1)/n} & \dots & \alpha_2 \ & = \frac{1}{\sqrt{n}} & & \vdots & :vdots & :vdots & :vdots \ \omega_n & -e^{-2\pi i(n-1)/n} & -e^{-2\pi i(n-1)/n} & \dots & \alpha_n \end{matrix}$ $$ (19.5)$

and the DFT can be seen as a linear transform talking the column vector $\omega$ to a column vector $\alpha$

$$\begin{matrix} \alpha_1 & e^{2\pi i(0)/n} & e^{2\pi i(0)/n} & \dots & \omega_1 \ \alpha_2 & e^{2\pi i(1)/n} & e^{2\pi i(1)/n} & \dots & \omega_2 \ & = \frac{1}{\sqrt{n}} & & \ \vdots & :vdots & :vdots & :vdots \ \alpha_n & e^{2\pi i(n-1)/n} & e^{2\pi i(n-1)/n} & \dots & \omega_n \end{matrix}$ $$ (19.6)$

An $n$th root of unity is a complex number $\zeta$ satisfying the equation

$$\zeta^n = 1$ (19.7)$

with $n=1, 2, 3, \dots, n-1$ being a positive integer, for example

$$\zeta_n = e^{-2\pi i n/n} = \cos(2\pi \cdot n/n) - i \cdot sin(2\pi \cdot n/n)$ (19.8)$

Using the $n$th root of unity, the matrix can be represented as a Vandermonde matrix

$$\begin{matrix} F = \frac{1}{\sqrt{n}} & 1 & 1 & 1 & \dots & 1 \ & \zeta_n & \zeta_n^2 & \zeta_n^3 & \dots & \zeta_n^{(n-1)} \ & \zeta_n^2 & \zeta_n^4 & \zeta_n^6 & \dots & \zeta_n^{2(n-1)} \ & \zeta_n^3 & \zeta_n^6 & \zeta_n^9 & \dots & \zeta_n^{3(n-1)} \ & \vdots & \vdots & \vdots & \vdots & \vdots \ & \zeta_n^{(n-1)} & \zeta_n^{2(n-1)} & \zeta_n^{3(n-1)} & \dots & 1 \end{matrix}$ $$ (19.9)$

The matrix $F$, also called DFT matrix is unitary

$F^{-1} = F^* = IF.$ (19.10)$

Because $F$ is unitary it implies that the length of a vector is preserved as stated in Parseval's theorem

$|\omega|| = ||F \cdot \alpha|| = ||\alpha||.$ (19.11)$

# 19.2 QUANTUM FOURIER TRANSFORM

QFT can be used to determine the period of a periodic function in polynomial time, see Figure 19.1. This exponentially faster than a conventional computer. It is used in the framework for the factorization algorithm on which famous Shor's algorithm is