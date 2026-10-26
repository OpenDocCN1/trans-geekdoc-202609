a model. Then the following error bound holds:

$$\mathcal{E}(\theta)^2 := \int_{\Omega} \|u(x,t)-u_\theta(x,t)\|_2^2\,dx\,dt \leq \mathcal{O}\left(\mathcal{E}_T(\theta,\mathcal{S}) + N_{\mathrm{int}}^{-2/d} + N_{\mathrm{int}}^{-1/(d+1)} + N_s^{-1/d}\right). \tag{6.6}$$

The exact constant implied in the $\mathcal{O}$-notation depends on $(u_\theta,\rho_\theta)$ and $(u,\rho)$ and their derivatives (De Ryck *et al.* 2024a, Theorem 3.10). There are two interesting observations to be made from equation (6.6).

+   - When the training set is large enough, the total error scales with the square root of the training error, $\mathcal{E}(\theta) \sim \sqrt{\mathcal{E}_T(\theta,\mathcal{S})}$. This sublinear relation is also observed in practice; see Figure 6.1.
+   - The bound (6.6) reveals different convergence rates in terms of the training set sizes $N_{\mathrm{int}}$, $N_t$ and $N_s$. In particular, we need relatively many training points in the interior of the domain compared to its boundary. We will see that these ratios will be different for other PDEs.

De Ryck *et al.* (2024a) verified the above result by training a PINN to approximate the Taylor–Green vortex in two space dimensions, the exact solution of which is given by

$$u(t,x,y)=-\cos(\pi x)\sin(\pi y)\exp(-2\pi^2\nu t), \tag{6.7}$$
$$v(t,x,y)=\sin(\pi x)\cos(\pi y)\exp(-2\pi^2\nu t), \tag{6.8}$$
$$p(t,x,y)=-\frac{\rho}{4}[\cos(2\pi x)+\cos(2\pi y)]\exp(-4\pi^2\nu t). \tag{6.9}$$

The spatio-temporal domain is $x,y \in [0.5,4.5]^2$ and $t \in [0,1]$. The results are reported in Figure 6.1. As one can see, all error types decrease with increasing number of quadrature points. In particular, the relationship $\mathcal{E}(\theta) \sim \sqrt{\mathcal{E}_T(\theta,\mathcal{S})}$ is (approximately) observed as well.

In the next example we show that Theorem 6.2 can be used to show that the curse of dimensionality can also be overcome in the training set size.

# Example 6.6 (high-dimensional heat equation).

We consider the high-dimensional (linear) heat equation (Example 2.1), which is an example of a linear Kolmogorov equation, for which we have proved that the CoD can be overcome in the approximation error in Example 4.23. In this example, we show that the training set size only needs to grow at most polynomially in the input dimension $d$ to achieve a certain accuracy. Applying Theorem 6.2 to every term of the right-hand side of the stability result for the heat equation (Theorem 5.3) then gives us the following result.

# Theorem 6.7.

Under the assumptions of Theorem 6.2 and given a training set of size $N_{\mathrm{int}}$ on $D \times [0,T]$, size $N_t$ on $D$ and size $N_s$ on $\partial D \times [0,T]$, we find that there