# 1.2.1 Configuration and Direct Numerical Simulation

The two-dimensional viscous, incompressible wake behind a circular cylinder is computed. This flow is characterized by the Reynolds number Re = UD/ν where D represents the cylinder diameter, U the oncoming velocity, and ν the kinematic viscosity of the fluid. The reference Reynolds number is set to Re = 100, which is significantly above the onset of vortex shedding at Re = 47 (Jackson 1987, Zebib 1987) and also far below the onset of three-dimensional instabilities around Re = 160 (Zhang et al. 1995, Barkley & Henderson 1996).

In the following, all quantities are assumed to be normalized with the cylinder diameter D, the oncoming velocity U, and the density of the fluid ρ. The two-dimensional cylinder wake is described by a Cartesian coordinate system (x,y) with the origin in the cylinder center, the x-axis pointing in streamwise, and the y-axis in the transverse direction. The incompressibility condition and Navier–Stokes equations read

$$\nabla \cdot \boldsymbol{u} = 0, \tag{1.1a}$$ $$\partial_t \boldsymbol{u} + \boldsymbol{u} \cdot \nabla \boldsymbol{u} = -\nabla p + \frac{1}{Re} \Delta \boldsymbol{u}, \tag{1.1b}$$

where p represents the pressure, “∂ₜ” partial differentiation with respect to time, “∇” the Nabla operator, “Δ” the Laplace operator, and “·” an inner product or contraction in tensor algebra.

The rectangular computational domain Ω_DNS has a length and width of 50 and 20 diameters, respectively. The cylinder center has a distance of 10 diameter to the front and lateral sides. Summarizing,

$$\Omega_{\mathrm{DNS}} = \{ (x,y) \in \mathcal{R}^2 : x^2 + y^2 \ge 1/4 \cap -10 \le x \le 40 \cap |y| \le 10 \}.$$

On the cylinder, the no-slip condition u = 0 is enforced. At the front x = -10 and lateral sides of the domain y = ±10, a uniform oncoming flow u_∞ = (1,0) is assumed. A vanishing stress condition is employed at the outflow boundary x = 40.

Simulations are performed with a finite-element method on an unstructured grid with implicit time integration. This solver is third-order accurate in time and second-order accurate in space. Details about the Navier–Stokes and stability solvers are described in Morzyński et al. (1999) and Noack et al. (2003). The triangular mesh consists of 59 112 elements.

The employed initial conditions are based on the unstable steady solution u_s and a small disturbance with the most unstable eigenmode f₁. The steady solution is computed with a Newton gradient solver. The eigenmode computation is described in our earlier work (Noack et al. 2003). The disturbance is the real part of the product of the eigenmode and unit phase factor e^{jφ}. Here, “j” denotes the imaginary unit and φ the phase. The amplitude ε is chosen to create a perturbation with a fluctuation energy of 10⁻⁴. The resulting initial condition reads

$$\boldsymbol{u}(\boldsymbol{x},t=0) = \boldsymbol{u}_s(\boldsymbol{x}) + \varepsilon \mathbb{R}\{ \boldsymbol{f}_1(\boldsymbol{x}) e^{j\phi} \}. \tag{1.2}$$

Sixteen initial conditions are considered. These correspond to equidistantly sampled phases φ ∈ [22.5°,45°,…,337.5°,360°]. Integration is performed from t = 0