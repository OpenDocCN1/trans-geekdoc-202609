and

\( B = \frac{3}{1 + \gamma_0/2} - e^{-\gamma_0/2} \. \) (8.38)

Using the above results and an integral table, the closed-form filter kernel h(n) can be obtained by performing 1D Fourier transform and sampling at the integer points:

\(\begin{aligned} h(n) &= \int_{-1/2}^{1/2} H(\omega) e^{2\pi i n \omega} d\omega \\ &= \frac{2}{3} \int_{0}^{1/2} \omega (e^{-\gamma_0 \omega} + e^{-\gamma_1 \omega} + e^{-\gamma_2 \omega}) \cos(2\pi m \omega) d\omega \\ &= \frac{-2}{3} \sum_{k=0}^{2} \frac{(-1)^n e^{-\frac{\gamma_k}{2}} (\gamma_k^3 + 4\gamma_k \pi^2 n^2 + 2\gamma_k^2 - 8\pi^2 n^2)}{(\gamma_k^2 + 4\pi^2 n^2)^2} \. \) (8.39)

Figure 8.7 illustrates that the approximation relationship (8.32) is fairly accurate. There are six curves in Figure 8.7: three cases of true curves and corresponding three cases of approximated curves. We can only see three curves in Figure 8.7. This is because the true and approximated curves match so well and on the top of each other.

![](bbox=[0.106, 0.498, 0.645, 0.785])

**Fig. 8.7:** Verification of the approximation expression (8.32) with different values of \(\gamma_0\).