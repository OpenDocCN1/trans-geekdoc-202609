![](bbox=[0.18, 0.2, 0.62, 0.48])

Figure 10.3 Effect of applying proportional feedback control with K = 1 to the two systems, P1 and P2.

system using (10.3). We will explore two different input and output combinations. First, we have the case where the input uses a different state variable as the output (system P1), using the input and output matrices

$\boldsymbol{B}_1 = \begin{bmatrix}1\\0\end{bmatrix}, \quad \boldsymbol{C}_1 = \begin{bmatrix}0 & 1\end{bmatrix}, \tag{10.5}$

giving the transfer function (see (10.3))

$P_1(s) = \frac{0.7373}{s^2 - 0.09654 s + 0.5508}. \tag{10.6}$

Second, we use the input and output matrices

$\boldsymbol{B}_2 = \begin{bmatrix}0\\1\end{bmatrix}, \quad \boldsymbol{C}_2 = \begin{bmatrix}0 & 1\end{bmatrix}, \tag{10.7}$

giving the transfer function

$P_2(s) = \frac{s - 0.04381}{s^2 - 0.09654 s + 0.5508}. \tag{10.8}$

Note that the denominators of the transfer functions P1(s) and P2(s) are the same quadratic polynomial. This is as expected, since the roots of this polynomial are the poles of the system, which are in turn given by the eigenvalues of A, which is the same for both systems.

To begin with, and before doing any further analysis of this system, suppose that we try to control our systems with the simplest feedback control, where K from our schematic diagram being a multiplicative constant. This is known as proportional control. The results of applying this control to our system with K = 1 is shown in Figure 10.3, where we have the reference set at r = 0. Here, we allow the system to evolve without any inputs, before turning on control at a time t = 15. Note that here we are applying control to the unstable linearized system, rather than the full nonlinear system. We notice that the system P2 seems to be stabilized, while P1 remains unstable.