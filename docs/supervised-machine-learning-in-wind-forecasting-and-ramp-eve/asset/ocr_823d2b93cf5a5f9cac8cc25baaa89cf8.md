![](bbox=[0.306, 0.103, 0.735, 0.285])

# Figure 8.3 Bilateral Gaussian wake model.

holds, which can be mathematically expressed as

\(\int_{r_2}^\infty \rho u_0 2\pi r dr + \int_0^{r_2} \rho u_2 2\pi r dr = \int_0^\infty \rho u 2\pi r dr,\) (8.9)
\(u_2 = (1 - 2a)u_0,\) (8.10)

where \(r_2\) is the radial distance from the wake centerline at downstream distance \(x_1\), \(\rho\) is the density of incompressible fluid (air), and \(u_2\) is the wind speed just after the rotor. According to actuator disk theory, \(a\) is the induction factor. Substituting (8.10) and (8.7) into (8.9), we get

\(A(x) = \frac{a}{(\sigma/r_2^2)},\) (8.11)

where \(\sigma\) is a linear function of \(x\), and its estimation [29] is

\(\sigma = \frac{r}{\sqrt{2}} = \frac{r_0 + \alpha x}{\sqrt{2}}.\) (8.12)

Thus Jensen's Gaussian distribution wake model is given as

\(u = u_0 \left( 1 - \frac{a}{(\sigma/r_2^2)} e^{\frac{-r^2}{2\sigma^2}} \right).\) (8.13)

Further, Frandsen's Gaussian version of wake model assumes that the mass flow rate through the control tube \(Y_1 Y_3\) is not constant. Based on the principle of conservation of momentum, we get

\(T = \int_0^\infty \rho (u_0 - u) 2\pi r dr = \frac{1}{2} \rho A_0 (u_0^2 - u^2),\) (8.14)