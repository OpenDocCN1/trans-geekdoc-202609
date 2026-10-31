
### 1.2.1 Configuration and Direct Numerical Simulation

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

Sixteen initial conditions are considered. These correspond to equidistantly sampled phases φ ∈ [22.5°,45°,…,337.5°,360°]. Integration is performed from t = 0 to t = 200, capturing the complete transient and post-transient state. The time step is Δt = 0.1, corresponding to roughly one 50th of the period.

### 1.2.2 Unforced Transients

In this section, the transients from the steady solution to periodic vortex shedding are investigated. The flow is analyzed in the observation domain

Ω := {(x,y) ∈ Ω_DNS : 5 ≤ x ≤ 15 ∧ -5 ≤ y ≤ 5}.  (1.3)

This domain is about twice as long as the vortex bubble of the steady solution. The streamwise extent is large enough to resolve over one wavelength of the initial vortex shedding as characterized by the stability eigenmode. A larger domain is not desirable, because a small increase in wavenumber during the transient will give rise to large phase differences in the outflow region, complicating the comparison between flow states. The domain is consistent with earlier investigations by the authors (Gerhard et al. 2003, Noack et al. 2003) and similar to the domains of other studies (Deane et al. 1991).

The analysis is based on the inner product of the Hilbert space of square-integrable functions over the observation domain Ω. This inner product between two velocity fields v and w is defined by

(v,w)_Ω = ∫_Ω d x v · w,  (1.4)

where “.” denotes the Euclidean inner product. The corresponding norm of the velocity field v reads

‖v‖_Ω = √((v,v)_Ω).  (1.5)

The flow u is decomposed into a slowly varying base flow u^D and an oscillatory fluctuation u′,

u = u^D + u′.  (1.6)

The short-term averaged flow is approximated as the projection of the flow on the one-dimensional affine space containing the steady solution u_s and the post-transient mean flow u_0. The superscript “D” comes from the term distorted mean flow of mean-field theory (Stuart 1958). In other words,

u^D(x,t) = u_s(x) + a_Δ(t) u_Δ(x),  (1.7)
with the shift-mode u_Δ = (u_0 − u_s)/‖u_0 − u_s‖_Ω and amplitude a_Δ = (u − u_s, u_Δ)_Ω. This definition approximates a short-term averaged flow and generalizes the notion in the stability literature where the steady solution is identified with the base flow.
The shift-mode amplitude a_Δ characterizes the mean-flow distortion while the fluctuation energy

𝓚 := ‖u′‖_Ω² / 2  (1.8)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_27_0.png)

Figure 1.1 Evolution of the turbulent kinetic energy $\mathcal{K}$ with time $t$ associated with an initial condition for $\phi = 22.5^\circ$. The values are normalized with the maximum value $\mathcal{K}_{\max}$. Red points indicate normalized fluctuation levels of 0%, 10%, 50%, and 100%. For details, see Ehlert et al. (2020).

parameterizes the fluctuation level. We also refer to $\mathcal{K}$ as *turbulent kinetic energy* (TKE) following the mathematical definition of statistical fluid mechanics, realizing that the flow is laminar, not turbulent.

Figure 1.1 displays the TKE evolution with time. The maximum TKE value $\mathcal{K}_{\max}$ is used for normalization. Three dynamic phases can be distinguished. Within the first 30 convective time units $D/U$, the flow exhibits *linear dynamics* or exponential growth in the neighborhood of the steady solution. This exponential growth can clearly be seen in a logarithmic plot (Noack et al. 2003). In the second, *nonlinear transient phase* for $50 < t < 100$ the flow transitions from the steady solution to the limit cycle with decreasing growth rate. In the *post-transient phase* for $t > 150$, a periodic vortex shedding or, equivalently, limit-cycle dynamics is observed. The figure marks four times for TKE levels near 0%, 10%, 50%, and 100%, corresponding to the linear dynamics phase, the beginning and middle of the nonlinear transient phase and the limit cycle.

In Figure 1.2, the vorticity for the four selected time instants is shown. Positive (negative) values of vorticity are shown in red (blue) bounded by solid (dashed) lines. The three dynamic phases can be distinguished based on the closeness of vortex shedding to the cylinder and on the formation of pronounced individual vortices.

This discussion provides a basis for the time interval $[t_{\min}, t_{\max}]$ for snapshot selection. A lower bound $t_{\min} = 40$ is chosen. This bound guarantees a TKE below 0.01% or, equivalently $10^{-4}$ of the asymptotic maximum value. The upper bound $t_{\max} = 110$ includes few periods on the limit cycle.

### 1.2.3 Wake Dynamics

Figure 1.3 foreshadows a state-space picture of the transient dynamics. Near the steady solution (bottom of the paraboloid), the flow spirals outward on a plane spanned by the real and imaginary part of the unstable stability mode (bottom right). With increasing fluctuation amplitude, the Reynolds stress deforms the short-term averaged flow in the direction of the shift mode depicted middle left. This deformation leads

![](img/ddadb1d3eaa6f9576eea68f95d453bca_28_0.png)

Figure 1.2 Vorticity snapshots corresponding to 0%, 10%, 50%, and 100% fluctuation level for the simulation displayed in Figure 1.1. The flow is visualized by iso-contours of vorticity with positive (negative) values marked by solid (dashed) lines and red (blue) background. The iso-contour levels and color scales are the same for all snapshots. For details, see Ehlert et al. (2020).

to a shortening of the vortex bubble and an upward motion of the fluctuation energy. The state moves outward and upward on a paraboloid until it converges against a limit cycle. The center of this limit cycle is characterized by the mean flow while the fluctuations are well approximated by the first two POD modes. In Chapters 14 and 17, this dynamics will be distilled from the data, dynamically modeled, and reversed by stabilizing control.

## 1.3 Cartographing the Data with Features

In this section, feature extraction is discussed. For the sake of concreteness, features are considered for an ensemble of M velocity snapshots u^m(x) = u(x,t^m), m = 1, ..., M. For an oscillatory flow, amplitude and frequencies are important features that can completely or, in case of slow drifts, partially characterize the state. For a turbulent flow, features are far more challenging to design. In case of skin friction reduction of a turbulent boundary layer, features might be the position and amplitude of sweeps and ejections. In the following, two feature extraction methods are presented. First (Section 1.3.1), proximity maps via classical multidimensional
