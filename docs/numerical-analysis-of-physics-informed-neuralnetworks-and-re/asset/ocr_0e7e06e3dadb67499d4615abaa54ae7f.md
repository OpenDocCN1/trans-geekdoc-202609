minimization problem (2.44) could therefore be

$$\min_{\theta\in\Theta}\left(\mathcal{E}_{\mathrm{PIL}}[u_\theta^2]+\lambda_d\int_{\Omega'}\mathcal{R}_d[u_\theta]^2+\lambda_r\|\theta\|_q^q\right). \tag{2.48}$$

# 2.3.2. *Weak formulation*

In the previous subsection we considered PDE residuals and physics-informed loss functions that are based on the strong formulation of the PDE. However, for various classes of PDEs there might not be a smooth classical solution $u$ for which it holds in every $x\in\Omega$ that $\mathcal{L}[u](x)=f(x)$. Fortunately, one can sometimes generalize the definition of ‘a solution to a PDE’ in a precise manner such that there are functions that satisfy this generalized definition after all. Such functions are called *weak solutions*. They are said to satisfy the *weak formulation* of the PDE, which can be obtained by multiplying the strong formulation of the PDE (2.1) with a smooth and compactly supported test function $\psi$ and then performing integration by parts:

$$\int_{\Omega}u\mathcal{L}^*[\psi]=\int_{\Omega}f\psi, \tag{2.49}$$

where $\mathcal{L}^*$ is the (formal) adjoint of $\mathcal{L}$ (if it exists). Consequently, a function $u$ is said to be a weak solution if it satisfies (2.49) for all (compactly supported) test functions $\psi$ in some predefined set of functions. Note that $u$ no longer needs to be differentiable but merely integrable.

Weak formulations such as (2.49) form the basis of many classical numerical methods, in particular the finite element method (FEM: Section 2.2.1). Often, however, there is no need to perform integration by parts until $u$ is completely free of derivatives. In FEM, the weak formulation for second-order elliptic equations is generally obtained by performing integration by parts only once. For the Laplacian $\mathcal{L}=\Delta$ we then have

$$\int_{\Omega}\Delta u\,\psi=-\int_{\Omega}\nabla u\cdot\nabla\psi$$

(given suitable boundary conditions), which is a formulation with many useful properties in practice.

Other than using spectral methods (as in Section 2.2.1), there are now different avenues one can follow to obtain a *weak physics-informed loss function* based on (2.49). The first method draws inspiration from the Petrov–Galerkin method (Section 2.2.1) and considers a finite set of $K$ test functions $\psi_k$ for which (2.49) must hold. The corresponding loss function is then defined as

$$\mathcal{E}_{\mathrm{VPIL}}[u_\theta]=\sum_{k=1}^{K}\left(\int_{\Omega}u_\theta\mathcal{L}^*[\psi_k]-\int_{\Omega}f\psi_k\right)^2. \tag{2.50}$$

where additional terms can be added to take care of any boundary conditions. This method was first introduced for neural networks under the name *variational*