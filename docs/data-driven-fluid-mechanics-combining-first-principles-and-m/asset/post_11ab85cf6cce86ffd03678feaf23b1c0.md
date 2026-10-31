
![](img/ddadb1d3eaa6f9576eea68f95d453bca_283_0.png)

Figure 13.4 Stability formalisms for a temporally evolving perturbation (top), a spatially evolving disturbance (middle), and a general spatio-temporal evolution from a point source (bottom).

have been necessary, since the mathematical tools have been restricted to analytical, approximate, or asymptotic methodology, such as, for example, perturbation and asymptotic methods. With the advent of computational and data-driven techniques, we are now in a position to address directly – with few imposed restrictions and forced assumptions – the hydrodynamic stability behavior of complex flows. The analysis of unsteady, separated, and multiscale flows are now within our range, as is the nonlinear evolution of disturbances in these configurations.

For this reason, we will advocate a reverse route of exposition: starting from the general, unrestricted stability problem to the more confined, but perhaps more familiar setup. We will describe a rather general computational framework for hydrodynamic stability problems based on the optimization of a cost functional subject to constraints, among them our nonlinear partial differential equation governing the fluid motion. This formalism is very flexible in describing and quantifying the perturbation dynamics under minimal restrictions and limitations. After having established this general framework, we will then make progressive assumptions – either about the base flow or the perturbation dynamics – to find reduced descriptions of the general formulation. This will naturally introduce familiar techniques for the analysis of a fluid system's stability characteristics.

The general framework for hydrodynamic stability analysis relies on a mathematical formalism that uses calculus of variations, optimization techniques, and concepts from linear algebra. A basic knowledge of these disciplines is helpful in understanding the derivations later; it can be gained from excellent textbooks, monographs, and review articles, such as Kot (2015) and Cassel (2013) for calculus of variations, Gunzburger (2003) and Magri (2019) for adjoint techniques, Kochenderfer and Wheeler (2019) and Nocedal and Wright (2006) for optimization, and Trefethen and Bau (1997) for linear algebra, among many other resources.

## An Optimization Formulation for Hydrodynamic Stability

We assume a general form of the governing equations according to

$$\frac{d}{dt}\mathbf{q} = \mathrm{N}(\mathbf{q},\mathbf{f}) \tag{13.3}$$

where the components of the state vector $\mathbf{q} \in \mathbb{C}^{n_q}$ represent all variables required to fully describe the flow state. The vector $\mathbf{f} \in \mathbb{C}^{n_f}$ stands for the control variable. The exact form of the governing equations is given by the operator $\mathrm{N}$, where we additionally have assumed an appropriate spatial discretization of the state vector $\mathbf{q}$. We consider $n_q$ degrees of freedom for the state vector, comprising the product of the total number of grid points (for example, $n_x \times n_y \times n_z$ in three Cartesian dimensions) and the number of tracked variables (for example, three velocities and pressure for three-dimensional incompressible flow). The control vector has $n_f$ degrees of freedom, indicating the number of grid points and variables we have chosen to manipulate. Boundary conditions are enforced within the spatial discretization schemes, and the initial condition will be imposed via the control variable $\mathbf{f}$ (see below for details).

Next, we introduce a cost functional $\mathcal{J}(\mathbf{q},\mathbf{f})$, consisting of a real scalar that depends, in a yet unspecified way, on the variables $\mathbf{q}$ and $\mathbf{f}$. We recall that a functional is a mapping of functions onto a (generally complex) scalar. Thus, $\mathcal{J}$ takes the time-dependent input functions $\mathbf{q}$ and $\mathbf{f}$ and assigns a scalar value to them. More specifically, this cost functional represents the objective of the optimization, for example, a maximization of energy amplification (for stability analyses) or a minimization of instabilities (for flow control applications; see also the control framework developed in Chapter 9). During the optimization, the governing equations (13.3) have to be satisfied, which renders our optimization setup as a constrained optimization problem. Invoking standard techniques, we convert this constrained optimization problem into an unconstrained equivalent by adding the constraints via Lagrange multipliers to the cost functional; this results in the augmented Lagrangian:

$$\mathcal{L}(\mathbf{q},\mathbf{q}^\dagger,\mathbf{f}) = \mathcal{J}(\mathbf{q},\mathbf{f}) - \left\langle \mathbf{q}^\dagger, \frac{d}{dt}\mathbf{q} - \mathrm{N}(\mathbf{q},\mathbf{f}) \right\rangle \tag{13.4}$$

This mathematical step required the introduction of Lagrange multipliers $\mathbf{q}^\dagger$ and the choice of a scalar product. It follows from expression (13.4) (more specifically, from term with the scalar product) that the Lagrange multipliers $\mathbf{q}^\dagger$ have the same dimensionality as $\mathbf{q}$, that is, $\mathbf{q}^\dagger \in \mathbb{C}^{n_q}$. We thus realize that the Lagrange multipliers represent time-dependent “flow fields.” At this stage, however, we do not yet have an equation governing their temporal evolution. Proceeding, we define a scalar product as

$$\langle \mathbf{a},\mathbf{b} \rangle \equiv \int_{0}^{\tau} \mathbf{a}^H \mathbf{b} \, dt \tag{13.5}$$

The superscript $^{H}$ stands for the transpose conjugate operation. In the previous definition, we have introduced the time horizon $\tau$, which has to be user-specified and adapted to the relevant timescales of the flow under consideration. In what follows, it will prove mathematically advantageous to recast the cost functional $\mathcal{J}$ in terms of the scalar product (13.5). We write

$\mathcal{J}(\mathbf{q},\mathbf{f}) = \langle w(t), j(\mathbf{q},\mathbf{f}) \rangle,$  (13.6)

where we included a weight function $w(t)$ that is responsible for the enforcement of $j$ within the time interval $[0, \tau]$. As an example, specifying a cost functional $j$ over the entire time horizon, we choose $w = 1$; for focusing only on the value of $j$ at the end of the time horizon, we choose $w = \delta(t - \tau)$.

With the augmented Lagrangian $\mathcal{L}$ fully specified, we seek an optimum of $\mathcal{L}$ with respect to all independent variables, that is, $\mathbf{q}, \mathbf{q}^{\dagger}, \mathbf{f}$. This mathematical problem requires calculus of variations: we determine three time-dependent functions $(\mathbf{q}, \mathbf{q}^{\dagger}, \mathbf{f})$ that optimize a scalar value (our augmented Lagrangian $\mathcal{L}$). Analogous to computing an optimum for a function of three independent variables $f(x, y, z)$ by setting the first-order partial derivatives with respect to the three variables to zero, $f_x = f_y = f_z = 0$, we have to take the first-order variations of the scalar $\mathcal{L}$ (see (13.4)) with respect to the three functions $\mathbf{q}, \mathbf{q}^{\dagger}, \mathbf{f}$ and set them to zero simultaneously (see, e.g., Cassel (2013) or Kot (2015)). The resulting three conditions are referred to as the Karush–Kuhn–Tucker (KKT) system. Formally, we have

$\frac{\delta \mathcal{L}}{\delta \mathbf{q}^{\dagger}} = 0, \qquad \frac{\delta \mathcal{L}}{\delta \mathbf{q}} = 0, \qquad \frac{\delta \mathcal{L}}{\delta \mathbf{f}} = 0,$  (13.7)

where each of the above conditions furnishes a governing equation.

The first condition reads, more explicitly,

$\left\langle \delta \mathbf{q}^{\dagger}, \underbrace{\frac{d}{dt}\mathbf{q} - \mathrm{N}(\mathbf{q},\mathbf{f})}_{=0} \right\rangle = 0,$  (13.8)

a condition that has to hold true for all variations $\delta \mathbf{q}^{\dagger}$. This expression thus recovers our original governing equation for $\mathbf{q}$. The second condition is slightly more involved, as the state variable $\mathbf{q}$ appears in the governing equation as well as in the cost functional. We have

$\left\langle w, \frac{\partial j}{\partial \mathbf{q}} \delta \mathbf{q} \right\rangle - \left\langle \mathbf{q}^{\dagger}, \frac{d}{dt}\delta \mathbf{q} - \frac{\partial \mathrm{N}}{\partial \mathbf{q}} \delta \mathbf{q} \right\rangle = \left\langle \underbrace{\left(\frac{\partial j}{\partial \mathbf{q}}\right)^{H} w + \frac{d}{dt}\mathbf{q}^{\dagger} + \left(\frac{\partial \mathrm{N}}{\partial \mathbf{q}}\right)^{H} \mathbf{q}^{\dagger}}_{=0}, \delta \mathbf{q} \right\rangle = 0,$  (13.9)

where integration by parts (in time) is required to transfer the $d/dt$-operator onto the adjoint variable $\mathbf{q}^{\dagger}$. After isolating the first variation $\delta \mathbf{q}$ in the scalar products, we can extract an evolution equation for the adjoint variable $\mathbf{q}^{\dagger}$.
