explaining the mean-field parabola shape in the figure. Equation (1.18) in (1.17a), (1.17b) and the introduction to polar coordinates $a_1 = r \cos \theta$, $a_2 = r \sin \theta$ lead to the famous Landau equation (Landau & Lifshitz 1987) for a supercritical instability,

$$dr/dt = \sigma_1 r - \beta' r^3, \quad d\theta/dt = \omega_1 + \gamma' r^2. \tag{1.19}$$

These equations show an exponential growth by linear instability and a cubic damping by Reynolds stress and mean-field deformation. The frequency changes as well. The nonlinearity parameters $\beta'$ and $\gamma'$ can easily be derived from (1.17). Intriguingly, this equation is found to remain accurate even far from the onset of vortex shedding.

The resulting Landau model does not include higher harmonics. Even worse, we have assumed fixed modes $\boldsymbol{u}_1$, $\boldsymbol{u}_2$. Yet, the prominent stability mode near the steady solution is distinctly different from the POD modes characterizing the limit cycle. $a_3$-dependent modes can cure this shortcoming (Morzyński et al. 2006), but the model is still blind to higher harmonics. A more accurate model is based on the LLE feature coordinates $\gamma_1 = r \cos \theta$ and $\gamma_2 = r \sin \theta$ and an identified Landau equation for the dynamics of $r$ and $\theta$. The LLE autoencoder incorporates the mode deformation and higher harmonics (Ehlert et al. 2020). Loiseau et al. (2018) has derived such a model based on similar premises. The mean-field Galerkin model can be generalized for two (and more) frequencies (Luchtenburg et al. 2009).

# 1.6 Control: Model-Based and Model-Free Approaches

This section previews two flow control approaches. Section 1.6.1 follows the classical paradigm of model-based control design, while Section 1.6.2 outlines a model-free machine-learned control optimization.

# 1.6.1 Model-Based Control

As a control benchmark (Hinze & Kunisch 2000), we aim to stabilize the cylinder wake with a transversal volume force in the near wake (see Figure 1.8). This admittedly academic volume force actuator is surprisingly often used in the computational flow control literature and significantly simplifies the discussion. As added complexity, experimental conditions are emulated by the hot-wire measurement of the streamwise velocity component $s$. The goal is stabilizing sensor-based control law (see, again, Figure 1.8).

The volume force can be shown to lead to an extra term $g b$ in the mean-field system (Gerhard et al. 2003),

$$da_1/dt = \sigma a_1 - \omega a_2 + g b, \quad \sigma = \sigma_1 - \beta a_3, \tag{1.20a}$$ $$da_2/dt = \sigma a_2 + \omega a_1, \quad \omega = \omega_1 + \gamma a_3, \tag{1.20b}$$ $$a_3 = a' \left(a_1^2 + a_2^2\right), \quad a' = \alpha / |\sigma_1|. \tag{1.20c}$$