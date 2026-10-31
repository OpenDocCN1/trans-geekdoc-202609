energy-based control has a kinematic relation to phasor control and an energetic relation to opposition control.

The growth rate σ^μ is assumed positive and small enough so that the timescale of amplitude growth is small compared to the timescale of oscillation. In this case, the state can be approximated by the polar coordinates r, θ with a₁ = r cos θ, a₂ = r sin θ. Here, r and ω = dθ/dt are slowly varying functions of time. The energy equation is given by

$$\frac{dr^2}{dt} = 2a_1\frac{da_1}{dt} + 2a_2\frac{da_2}{dt} = 2\sigma^\mu r^2 + 2g a_2 b.$$

The control goal is an exponential decay of the amplitude with σ^c < 0, that is,

$$\frac{dr^2}{dt} \doteq 2\sigma^c r^2.$$

Eliminating the time derivative in both equation yields

$$\frac{dr^2}{dt} = 2\sigma^c r^2 = 2\sigma^\mu r^2 + 2g a_2 b.$$

The control command b increases (decreases) the energy r²/2 if it has the same (different) sign as a₂. To prevent wasting actuation energy with the wrong phase, the linear ansatz b = -k a₂ is made. The gain k > 0 is determined by substituting a₂ = r cos θ in the energy equation and averaging over one period. The resulting control law reads

$$b = 2\frac{\sigma^c - \sigma^\mu}{g}a_2.\tag{17.6}$$

The gain increases with the difference between the natural and design growth rate σ^c − σ^μ and decreases with the forcing constant g in the linear dynamics. The factor 2 arises from the fact that the actuation is only effective in the [0,1]^T direction. The control design is very simple and immediately reveals the physical mechanism. The method is easy to generalize for nonlinear systems, particularly if the fluctuation is composed of clean frequency components. Related approaches are the Lyapunov control design (Khalil 2002) and harmonic balance (Jordan & Smith 1988).

# 17.3.2 Weakly Nonlinear Dynamics

As a refinement to the linearization, mean-field theory is recapitulated (Stuart 1958, Stuart 1971), providing an important nonlinear amplitude selection mechanism. The onset of vortex shedding behind a cylinder is one well-investigated example fitting this description (Schumm et al. 1994). This section and Section 17.3.2 outline the dynamical model and the corresponding control design, respectively.

Qualitatively, mean-field theory describes the feedback mechanism between the fluctuations and the base flow. The fluctuation gives rise to a Reynolds stress, which changes the base flow. The base-flow deformation generally reduces the production of fluctuation energy with increasing fluctuation level until an equilibrium is reached. The resulting evolution equations are also referred to as weakly nonlinear dynamics, as they describe a mild form of nonlinearity.