
![](img/f5b5b8709fc3a81631262f22d3552c5e_673_0.png)

Figure 6.32. Phase velocities of MHD modes. Wave diagram for fast, slow and pure Alfvén waves in the x − z plane. The magnetic field, B, is in the z-direction. This diagram is known as Friedrichs diagram. The angle θ describes the direction of propagation with respect to B0. The parameter β is the ratio of plasma pressure to magnetic pressure.

So these magnetosonic waves with the dispersion relations in (6.134) are longitudinal and always perturb the density of the plasma. They become degenerate when θ = 0.

Since both sound and Alfvén speeds are involved, it is obvious that the key parameter demarcating different physical regimes will be their ratio, or, conventionally, the ratio of the thermal to magnetic energies in the MHD medium, known as plasma beta:

$$\beta = \frac{p_0}{B_0^2/\mu_0} = \frac{c_s^2}{c_A^2}.$$ (6.141)

The magnetosonic waves can conveniently be summarized by the so-called Friedrichs diagram in Figure 6.32.

> Lab: Rayleigh-Taylor instability can be produced by injecting hot colored water into a glass of cold water as illustrated in Figure 6.34; we are dealing with two immiscible fluids of different density. Initially, this configuration is stable but as the colored water cools down and becomes denser than the water below, it becomes unstable. Rayleigh-Taylor instability produces the “mushrooms” falling. Reproduce the results in Figure 6.34.

## Seismology of plasma.

Wave motion occurs in solids, liquids, gases, and as we have described above in plasmas. Wave type can be determined by looking at the changes in shape and volume in a medium when it is subjected to sudden deformation. A change in shape in a medium produces shear-wave (also known

P- and S-wave propagation through Earth is the principal tool that scientists have used over the last 100 years or so to develop our current knowledge of Earth’s interior, including its main layers, its oil, gas, and water reserves. Similarly, Alfvén and magnetoacoustic waves represent nowadays one of the principal tools in understanding and transporting energy around our solar system, characterizing the solar atmosphere, and predicting space weather, which has become central to communication and the functioning of electrical grids on Earth. In other words, the existence of MHD waves allows us to understand the elastic and compressible nature of the plasma in the presence of a frozen-in external magnetic field. The forces driving these waves are the gradients of the magnetic and gas pressures, and the magnetic tension.

Lab: Kelvin-Helmholtz instability. Acquire a tank as illustrated in Figure 6.35. Fill the tank half full with fresh water (ρ = 0.998 g/cm³) dyed red. Then fill the other half with salt water (ρ = 1.075 g/cm³) dyed blue. There is no mixing between the two types of water. Fresh water stays on top because it has a lower density than salt water. Seal the tank and make sure that there are no air bubbles inside. Then tilt the tank to ensure that two fluids move at different speeds to obtain the results in Figure 6.35.

## 6.4. MHD Instabilities and Accretion

A plasma, in a steady state (i.e., ∂/∂t = 0), is by definition in a state of equilibrium. If a small perturbation is applied to the plasma and the small perturbation decays with time or just oscillates around the equilibrium configuration we will still consider our configuration stable. In contrast, if this configuration grows with time, the system will become unstable with respect to perturbations. Important phenomena in our universe are caused by unstable configurations, including wave clouds in the Earth’s atmosphere described in Chapter 2, mantle convection as described in Chapter 2, sand dunes, particle accelerations, the nature of Jupiter and Saturn’s atmospheres, the red spots on Jupiter, solar/stellar eruptions, the interaction of the solar wind with the Earth’s magnetosphere, star and galaxy formations, including their spiral arms, accretion disks that we will discuss later and spiral arms, the multiphase nature of the interstellar medium, and supernova explosions in the interstellar medium. In other words, there are several reasons for studying plasmatic instabilities. Actually fluid and plasma instabilities are all around us at all scales. A large portion of nature is made up of fluid and plasma instability, including the process of accretion in the universe which is analogous to Earth’s assembly processes. Figures 6.34 and 6.35 illustrate how instability works in certain situations. Our objective in this subsection is to establish the criteria for five such instabilities, namely, convective instability, Jeans instability, magnetorotational (accretion) instability, Rayleigh-Taylor instability, and Kelvin-Helmholtz instability.

Convective instability is concerned with the stability of hydrostatic equilibrium, as described in Chapter 2. Jeans instability is concerned with the stability of a self-gravitational fluid against gravitational collapse. Magnetorotational instability is concerned with the stability of a plasma in orbit around a central object.

![](img/f5b5b8709fc3a81631262f22d3552c5e_676_0.png)

Figure 6.34. Rayleigh-Taylor (or heavy over light) instability with t₂ > t₁ > t₀; a heavy fluid over a light fluid (heavy/light). These two fluids are immiscible. The density difference drives the Rayleigh-Taylor instability.

Rayleigh-Taylor instability and Kelvin-Helmholtz instability are concerned with the stability of an interface with tangential velocity and/or density that continuously changes to zero with respect to the mass flux. We start by introducing the Lagrangian and Eulerian formalisms of small perturbations. These formalisms are essential for the derivation of criteria for these instabilities.

### 6.4.1. Eulerian versus Lagrangian Formalisms

The Eulerian formalism uses fixed positions that do not change over time, as we did in the previous subsection. The Lagrangian formalism considers medium and position to be co-moving. Specifically, we are interested in establishing the differences between mathematical Eulerian and Lagrangian differentiation and between the Lagrangian and Eulerian formulations of small perturbation models. We will limit ourselves to non-relativistic formulation. See for example, Fiedler and Burton, 2021 and Burton and Noble, 2014,

### Eulerian and Lagrangian time derivatives.

Consider, for example, the plasma density, ρ(x,t) at position x and time t. At time t + δt the element will be at position x + δx. The change in quantity ρ of the plasma element is

Dρ/Dt = lim_{δt→0} [ (ρ(x+δx, t+δt) - ρ(x,t)) / δt ] = lim_{δt→0} [ ∂ρ/∂t + (δx/δt)·∇ρ + O(δt, |δx|) ] , (6.142)

where
ρ(x+δx, t+δt) = ρ(x,t) + ∂ρ/∂t δt + δx·∇ρ + O(δt², |δx|², δt|δx|),

and where D/Dt is the Lagrangian derivative and ∂/∂t is the Eulerian derivative, respectively, of the density. So we have the following relation between the Lagrangian and Eulerian derivatives:

Dρ/Dt ≈ ∂ρ/∂t + (δx/δt)·∂ρ/∂x = ∂ρ/∂t + v·∇ρ . (6.143)
Lagrangian    Eulerian    convective    Eulerian    convective

![](img/f5b5b8709fc3a81631262f22d3552c5e_679_0.png)

where $v_0$ is the background velocity. Because $\Delta v = \delta v + \xi \cdot \nabla v_0$, we can use (6.148) to obtain

```
\delta v = \frac{\partial \xi}{\partial t} + v_0 \cdot \nabla \xi - \xi \cdot \nabla v_0 . (6.149)
```

Note the additional $\xi \cdot \nabla v_0$ term (Figure 6.36), representing a measurement of the background fluid.

### Formulations of Eulerian MHD perturbation.

Let us seek solutions to ideal MHD equations in the form $\rho = \rho_0 + \delta \rho$, $p = p_0 + \delta p$, $\Psi = \Psi_0 + \delta \Psi$, and $B = B^{(0)} + \delta B$, and $v = 0 + \delta v$, where $\rho_0$ is the equilibrium mass density, $v_0$ is the flow velocity, $p_0$ is the equilibrium pressure and $B_0$ is the equilibrium magnetic field. By inserting these quantities into the ideal MHD equation and assuming that the amplitudes of perturbations are considerably smaller, the Eulerian perturbations $\delta \rho$, $\delta v$, $\delta p$, $\delta B$ can be written as follows: equations:

```
\frac{\partial \delta \rho}{\partial t} + \nabla \cdot (\rho_0 \delta v) = 0 \quad (6.150)

\frac{\partial \delta v}{\partial t} + \rho_0 \nabla (\delta \Psi) + \delta p \nabla \Psi_0 + \nabla \delta p + B_0 \times (\nabla \times \delta B) - (\nabla \times B_0) \times \delta B = 0 \quad (6.151)

\frac{\partial \delta p}{\partial t} + \delta v \cdot \nabla p_0 + \gamma p_0 \nabla \cdot \delta v = 0 \quad (6.152)

\frac{\partial \delta B}{\partial t} - B_0 \cdot \nabla \delta v + B_0 \nabla \cdot \delta v + v_1 \cdot \nabla B_0 = 0 \quad (6.153)
```
