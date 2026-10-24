If we define a product filter $P(z) = H_0(z)G_0(z)$ and substitute from Equation (7.10) into Equation (7.11), then the PR condition becomes [142]

$H_0(z)G_0(z) + H_1(z)G_1(z) = P(z) + P(-z) = 2 \quad (7.12)$

This needs to be true for all $z$, and because the odd powers of $z$ in $P(z)$ cancel with those in $P(-z)$, it requires that $p_0 = 1$ and $p_k = 0$ for all $n$ even and nonzero. The polynomial $P(z)$ should be a zero-phase polynomial to minimize distortion. In general, $P(z)$ is of the following form [142]:

$P(z) = \dots + p_5 z^5 + p_3 z^3 + p_1 z + 1 + p_1 z^{-1} + p_3 z^{-3} + p_5 z^{-5} + \dots (7.13)$

The design method for the PR filters can be summarized in the following steps [142]:

+   1. Choose $p_1, p_3, p_5, \dots$ to give a zero-phase polynomial $P(z)$ with good characteristics.
+   2. Factorize $P(z)$ into $H_0(z)$ and $G_0(z)$ with similar low-pass frequency responses.
+   3. Calculate $H_1(z)$ and $G_1(z)$ from $H_0(z)$ and $G_0(z)$.

To simplify this procedure, we can use the following relation:

$P(z) = P_r(Z) = 1 + P_{r,1} Z + P_{r,3} Z^3 + P_{r,5} Z^5 + \dots \quad (7.14)$

where

$Z = \frac{1}{2} \left(z + z^{-1}\right) \quad (7.15)$

# 7.3.4.2 Haar Wavelet Transform

The Haar wavelet is the simplest type of wavelet. In discrete form, Haar wavelets are related to a mathematical operation called the Haar transform. The Haar transform serves as a prototype for all other wavelet transforms. Like all wavelet transforms, the Haar transform decomposes a discrete signal into two subsignals of half its length. One subsignal is a running average or trend; the other subsignal is a running difference or fluctuation.