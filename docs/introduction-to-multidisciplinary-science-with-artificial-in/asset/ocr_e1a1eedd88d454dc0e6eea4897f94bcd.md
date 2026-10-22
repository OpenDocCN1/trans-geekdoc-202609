where \tilde{\omega}(z) = \omega - \Omega_0(z), \Omega_0(z) = \boldsymbol{k}_0 \cdot \boldsymbol{v}(z), \boldsymbol{k}_0 = [k_x, k_y, 0]^T is the horizontal wave vector, and Alfvén angular frequency is \omega_A = \boldsymbol{k}_0 \cdot \boldsymbol{B}_0 / \sqrt{\rho_0 \mu_0}. opens up the possibility of new flow-driven (Kelvin–Helmholtz) instabilities as we will discuss later. When the density is constant and \rho_0^2 g_0^2 \ll k_0^2(\gamma p_0 + B_0^2), (6.176) further reduces

$$\frac{d^2 \hat{\xi}}{dz^2} - k_0^2 \hat{\xi} = 0 \ .$$\n(6.178)

For the case of two half spaces, with the upper half-space representing the interval [0, +\infty] and the lower half-space representing the interval [0, -\infty], there are two boundary conditions describing the continuity the normal velocity and the pressure balance at z = 0; i.e.,

$$\left[ \boldsymbol{n} \cdot \hat{\boldsymbol{\xi}} \right]_1^2 = 0 \quad \text{and} \quad \left[ \Pi + \boldsymbol{n} \cdot \boldsymbol{\xi} \, \boldsymbol{n} \cdot \nabla \left( p + \frac{B^2}{2\mu_0} \right) \right]_1^2 = 0 \ ,$$\n(6.179)

where \boldsymbol{n} represents the normal vector to the interface of the half spaces. Note that celestial bodies are generally in hydrostatic equilibrium which implies that the profiles: p(z), B_x(z), and B_y(z) are related as follows:

$$\frac{d}{dz} \left[ p(z) + \frac{B^2(z)}{2\mu_0} \right] = -\rho g \ .$$\n(6.180)

# **Example: stratified MHD in cylindrical coordinates.**

Let us consider the Frieman-Rotenberg formalism in cylindrical coordinates \boldsymbol{r} = [r, \theta, z]^T in a one-dimensional cylindrical equilibrium, described by the density \rho(r), the pressure p(r), the magnetic field components B_\theta(r) and B_z(r) or \boldsymbol{B} = [0, B_\theta(r), B_z(r)]^T and the velocity components v_\theta(r) and v_z(r) or \boldsymbol{v} = [0, v_\theta(r), v_z(r)]^T. The equilibrium is restrained by just a single differential equation in the radial coordinate r. The gravitational potential \Psi(r) is considered to be due to a compact object centered on the axis r = 0. Because of the cylindrical symmetry, we consider Fourier components of the normal modes of the form

$$\boldsymbol{\xi}(r, \theta, z) = [\xi_r(r), \xi_\theta(r), \xi_z(r)]^T \exp[ i (m\theta + kz - \omega t)] \ .$$\n(6.181)

The spectral equation for cylindrical plasmas is (e.g., Bondeson et al., 1987)

$$\boldsymbol{F}(\boldsymbol{\xi}) - \underbrace{\left[ \left( \frac{\rho_0 v_\theta^2}{r} \right) \nabla \cdot \boldsymbol{\xi} + r \frac{d}{dr} \left( \frac{\rho_0 v_\theta^2}{r^2} \right) \xi_r \right] \boldsymbol{i}_r}_{\sim \text{centrifugal force}} + 2 i \rho \tilde{\omega} \left( \frac{v_\theta}{r} \right) \boldsymbol{i}_z \times \boldsymbol{\xi} + \rho \tilde{\omega}^2 \boldsymbol{\xi} = \boldsymbol{0},$$\n(6.182)

where

$$\tilde{\omega} = \omega - \Omega_0 = \omega - \underbrace{\frac{m v_\theta}{r}}_{\text{Coriolis}} - k v_z \ .$$\n(6.183)