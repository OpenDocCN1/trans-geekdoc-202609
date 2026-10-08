$\Gamma\left(\frac{3}{2}\right) = \frac{\sqrt{\pi}}{2}$\n$\Gamma\left(\frac{5}{2}\right) = \frac{3\sqrt{\pi}}{4}$\n$\frac{\partial}{\partial x}\log(\Gamma(x)) = \psi(x)$

For $0 \leqslant x \leqslant 1$ we have:

$\Gamma(1+x) = 1 + a_1x + a_2x^2 + a_2x^3 + a_4x^4 + a_5x^5$

where $a_1 = -0.5748, a_2 = 0.9512, a_3 = -0.6994, a_4 = 0.2425$ and $a_5 = -0.0110$.

# E.3 cumulative normal distribution function

In this section we show that the cumulative normal distribution function, $N_1(x)$, is related to the complementary error function, $erfc(x)$, by the following equation:

$N_1(x) = \frac{1}{2}erfc\left(-\frac{x}{\sqrt{2}}\right) \quad (E.3.1)

If we let the error function be represented by $erf(x)$ then we have:

$erf(x) = \frac{2}{\sqrt{\pi}}\int_0^{\infty}exp(-t^2)dt$

We now have the following:

$erfc(x) = 1 - erf(x), \quad erfc(-x) = -erf(x)\nerf(\infty) = 1 \quad and erfc(-x) = 2 - erfc(x)$

We will consider the integral

$I(x) = \frac{2}{\sqrt{\pi}}\int_{-\infty}^{\infty}exp(-t^2)dt\n= \frac{2}{\sqrt{\pi}}\int_{-\infty}^{0}exp(-t^2)dt + \frac{2}{\sqrt{\pi}}\int_0^{\infty}exp(-t^2)dt$

Since

$\frac{2}{\sqrt{\pi}}\int_{-\infty}^{0}exp(-t^2)dt = 1$

we therefore have

$I(x) = 1 + erf(x) = 1 + {1 - erfc(x)} = 2 - erfc(x)$