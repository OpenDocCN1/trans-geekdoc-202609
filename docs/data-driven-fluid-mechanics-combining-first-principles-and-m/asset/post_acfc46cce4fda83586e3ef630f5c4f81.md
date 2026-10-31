
energy-based control has a kinematic relation to phasor control and an energetic relation to opposition control.

The growth rate σ^μ is assumed positive and small enough so that the timescale of amplitude growth is small compared to the timescale of oscillation. In this case, the state can be approximated by the polar coordinates r, θ with a₁ = r cos θ, a₂ = r sin θ. Here, r and ω = dθ/dt are slowly varying functions of time. The energy equation is given by

$$\frac{dr^2}{dt} = 2a_1\frac{da_1}{dt} + 2a_2\frac{da_2}{dt} = 2\sigma^\mu r^2 + 2g a_2 b.$$

The control goal is an exponential decay of the amplitude with σ^c < 0, that is,

$$\frac{dr^2}{dt} \doteq 2\sigma^c r^2.$$

Eliminating the time derivative in both equations yields

$$\frac{dr^2}{dt} = 2\sigma^c r^2 = 2\sigma^\mu r^2 + 2g a_2 b.$$

The control command b increases (decreases) the energy r²/2 if it has the same (different) sign as a₂. To prevent wasting actuation energy with the wrong phase, the linear ansatz b = -k a₂ is made. The gain k > 0 is determined by substituting a₂ = r cos θ in the energy equation and averaging over one period. The resulting control law reads

$$b = 2\frac{\sigma^c - \sigma^\mu}{g}a_2.\tag{17.6}$$

The gain increases with the difference between the natural and design growth rate σ^c − σ^μ and decreases with the forcing constant g in the linear dynamics. The factor 2 arises from the fact that the actuation is only effective in the [0,1]^T direction. The control design is very simple and immediately reveals the physical mechanism. The method is easy to generalize for nonlinear systems, particularly if the fluctuation is composed of clean frequency components. Related approaches are the Lyapunov control design (Khalil 2002) and harmonic balance (Jordan & Smith 1988).

## 17.3.2 Weakly Nonlinear Dynamics

As a refinement to the linearization, mean-field theory is recapitulated (Stuart 1958, Stuart 1971), providing an important nonlinear amplitude selection mechanism. The onset of vortex shedding behind a cylinder is one well-investigated example fitting this description (Schumm et al. 1994). This section and Section 17.3.2 outline the dynamical model and the corresponding control design, respectively.

Qualitatively, mean-field theory describes the feedback mechanism between the fluctuations and the base flow. The fluctuation gives rise to a Reynolds stress, which changes the base flow. The base-flow deformation generally reduces the production of fluctuation energy with increasing fluctuation level until an equilibrium is reached. The resulting evolution equations are also referred to as weakly nonlinear dynamics, as they describe a mild form of nonlinearity.

The fluctuation has the same representation as in Section 17.3.1. However, the base flow is allowed to vary by another mode $u_3$, called the 0th, base deformation, or shift mode (Noack et al. 2003). This mode can be derived from the (linearized) Reynolds equation and is assumed to be slaved to the fluctuation level. The resulting velocity field ansatz reads

$$\mathbf{u}(\mathbf{x},t)=\mathbf{u}_s(\mathbf{x})+\mathbf{u}^u(\mathbf{x},t)+\mathbf{u}^\Delta(\mathbf{x},t),\tag{17.7a}$$ $$\mathbf{u}^u(\mathbf{x},t)=a_1(t)\mathbf{u}_1(\mathbf{x})+a_2(t)\mathbf{u}_2(\mathbf{x}),\tag{17.7b}$$ $$\mathbf{u}^\Delta(\mathbf{x},t)=a_3(t)\mathbf{u}_3(\mathbf{x}).\tag{17.7c}$$

The evolution equation is given by

$$\frac{d}{dt}\begin{bmatrix}a_1\\a_2\end{bmatrix}=A(a_3)\begin{bmatrix}a_1\\a_2\end{bmatrix}+B\mathbf{b},\quad A(a_3)=A_0+a_3A_3,\tag{17.8a}$$ $$a_3=\alpha^u\left(a_1^2+a_2^2\right),\tag{17.8b}$$

where

$$A_0=\begin{bmatrix}\sigma^u&-\omega^u\\\omega^u&\sigma^u\end{bmatrix},\quad A_3=\begin{bmatrix}-\beta^u&-\gamma^u\\\gamma^u&-\beta^u\end{bmatrix},\quad B=\begin{bmatrix}0\\g\end{bmatrix}.\tag{17.9}$$

Without loss of generality, $\alpha^u>0$. Otherwise, the sign of the mode $\mathbf{u}_3$ must be changed. A nonlinear amplitude saturation requires the constant $\beta^u>0$ to be positive.

For $a_3\equiv0$, (17.8) is equivalent to (17.5). However, (17.8) has a globally stable limit cycle with radius $r^\infty=\sqrt{\sigma^u/\alpha^u\beta^u}$ in the plane $a_3=a_3^\infty=\sigma^u/\beta^u$, and with center $[0,0,a_3^\infty]$.

In the framework of weakly nonlinear stability theory, the growth rate is considered a linear function of the Reynolds number $\sigma_u=\kappa(Re-Re_c)$. Here, $Re_c$ corresponds to its critical value where the steady solution with damped oscillations ($\sigma_u<0$) becomes unstable ($\sigma_u>0$) in a Hopf bifurcation, giving rise to self-amplified oscillatory fluctuations. The other parameters are considered to be constant. This yields the famous Landau equation for the amplitude $dr/dt=\sigma^u r-\beta r^3$, $\beta=\alpha^u\beta^u$ and a corresponding equation for the frequency. The Landau equation explains the famous square root amplitude law $r\propto\sqrt{Re-Re_c}$ for supercritical Reynolds numbers assuming a soft bifurcation. We refer to the literature for a discussion of the hard subcritical bifurcation with quintic nonlinearity (Stuart 1971). Intriguingly, even turbulent flows with dominant periodic coherent structures may be described by (17.8) (Bourgeois et al. 2013).

The mean-field model and variants thereof have been successfully used for the model-based stabilization of the cylinder wake at $Re=100$ (Gerhard et al. 2003, Tadmor et al. 2011). In these studies, an energy-based control design as discussed in Section 17.3.1 has been used to prescribe a fixed decay rate of the model.

## 17.3.3 Moderately Nonlinear Dynamics

Some oscillatory flows may be tamed by direct mitigation with models and methods described in Sections 17.3.1 and 17.3.2. Not all plants, particularly turbulent flows, have the actuation authority for such a stabilization. However, periodic forcing at high frequency has mitigated periodic oscillations in a number of experiments. Examples are the wake stabilization with an oscillatory cylinder rotation (Thiria et al. 2006), suppression of Kelvin–Helmholtz vortices in transitional shear layers (Parezanovic et al. 2016), reduction of the separation zone in a high-lift configuration (Luchtenburg et al. 2009), and elongation of the dead-water region behind a backward facing step (Vukasinovic et al. 2010). Also a periodic frequency at 60–70% of the dominant shedding frequency may substantially delay the vortex formation in wall-bounded shear-layers¹ and D-shaped cylinders (Pastoor et al. 2008). Sections 17.3.1 and 17.3.2 outline a corresponding modeling and control strategy.

Here, a generalized mean-field model for such frequency cross-talk phenomena is reviewed from Luchtenburg et al. (2009). Let $\boldsymbol{u}^u$ denote the natural self-amplified oscillation represented by two oscillatory modes $\boldsymbol{u}_1$, $\boldsymbol{u}_2$. Analogously, the actuated oscillatory fluctuation $\boldsymbol{u}^a$ is described by two modes $\boldsymbol{u}_3$, $\boldsymbol{u}_4$. The base-flow deformation due to the unstable natural frequency $\omega^u$ and stable actuation frequency $\omega^a$ are described by the shift-modes $\boldsymbol{u}_5$ and $\boldsymbol{u}_6$, respectively. The resulting velocity decomposition reads

$$\boldsymbol{u}(\boldsymbol{x},t)=\boldsymbol{u}_s(\boldsymbol{x})+\boldsymbol{u}^\Delta(\boldsymbol{x},t)+\boldsymbol{u}^u(\boldsymbol{x},t)+\boldsymbol{u}^a(\boldsymbol{x},t),\tag{17.10a}$$ $$\boldsymbol{u}^u(\boldsymbol{x},t)=a_1(t)\boldsymbol{u}_1(\boldsymbol{x})+a_2(t)\boldsymbol{u}_2(\boldsymbol{x}),\tag{17.10b}$$ $$\boldsymbol{u}^a(\boldsymbol{x},t)=a_3(t)\boldsymbol{u}_3(\boldsymbol{x})+a_4(t)\boldsymbol{u}_4(\boldsymbol{x}),\tag{17.10c}$$ $$\boldsymbol{u}^\Delta(\boldsymbol{x},t)=a_5(t)\boldsymbol{u}_5(\boldsymbol{x})+a_6(t)\boldsymbol{u}_6(\boldsymbol{x}).\tag{17.10d}$$

Generalized mean-field arguments yield the following evolution equation:

$$\frac{d}{dt}\begin{bmatrix}a_1\\a_2\\a_3\\a_4\end{bmatrix}=\boldsymbol{A}(a_5,a_6)\begin{bmatrix}a_1\\a_2\\a_3\\a_4\end{bmatrix}+\boldsymbol{B}\,b,\tag{17.11a}$$ $$\boldsymbol{A}(a_5,a_6)=\boldsymbol{A}_0+a_5\boldsymbol{A}_5+a_6\boldsymbol{A}_6,\tag{17.11b}$$ $$a_5=\alpha^u\left(a_1^2+a_2^2\right),\qquad a_6=\alpha^a\left(a_3^2+a_4^2\right),\tag{17.11c}$$

where $\boldsymbol{A}_0=\begin{bmatrix}\sigma^u&-\omega^u&0&0\\\omega^u&\sigma^u&0&0\\0&0&\sigma^a&-\omega^a\\0&0&\omega^a&\sigma^a\end{bmatrix}$, $\boldsymbol{A}_5=\begin{bmatrix}-\beta^{uu}&-\gamma^{uu}&0&0\\\gamma^{uu}&-\beta^{uu}&0&0\\0&0&-\beta^{au}&-\gamma^{au}\\0&0&\gamma^{au}&-\beta^{au}\end{bmatrix}$, $\boldsymbol{B}=\begin{bmatrix}0\\0\\0\\g\end{bmatrix}$, $\boldsymbol{A}_6=\begin{bmatrix}-\beta^{ua}&-\gamma^{ua}&0&0\\\gamma^{ua}&-\beta^{ua}&0&0\\0&0&-\beta^{aa}&-\gamma^{aa}\\0&0&\gamma^{aa}&-\beta^{aa}\end{bmatrix}$. ¹ J.-L. Aider, Private communication.
