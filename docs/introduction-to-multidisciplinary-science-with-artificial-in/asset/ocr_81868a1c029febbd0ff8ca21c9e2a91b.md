We can rotate the coordinate system so that $k_x = 0$ so that we choose the displacement of this form

$\boldsymbol{\xi}(\boldsymbol{x}, t) = \left[ \hat{\xi}_x(z; k_x, k_y), 0, \hat{\xi}_z(z; k_x, k_y) \right]^T \exp(i k_x x + i k_y y - i \omega t), \quad (6.167)$

where the quantities with hat are Fourier amplitudes. Because we assume incompressibility, the two components are related as follows:

$\nabla \cdot \boldsymbol{\xi} = \frac{d \hat{\xi}_z}{dz} + i k_x \hat{\xi}_x = 0. \quad (6.168)$

In other words, only one component is needed because the other can be deduced from incompressibility. Let us focus on vertical displacement which we will denote $\hat{\xi} = \hat{\xi}_z$. Let us start with the case $\boldsymbol{B} = \mathbf{0}$. After a lengthy algebra, we can verify that (6.164) becomes (e.g., Goedbloed and Poedts, 2004; and Goedbloed et al., 2019)

$\frac{d}{dz} \left[ \frac{\gamma \rho_0 \rho_0 \omega^2}{\rho \omega^2 - k_0^2 \gamma \rho_0} \frac{d \hat{\xi}}{dz} \right] + \left[ \rho_0 \omega^2 - \frac{k_0^2 \rho_0^2 g^2}{\rho_0 \omega^2 - k_0^2 \gamma \rho_0} - \frac{d}{dz} \left( \frac{k_0^2 \gamma \rho_0 \rho_0 g}{\rho \omega^2 - k_0^2 \gamma \rho_0} \right) \right] \hat{\xi} = 0. \quad (6.169)$

For incompressible plasmas (i.e., $\gamma \longrightarrow \infty$), we can assume that $\rho |\omega^2| \ll k_0^2 \gamma \rho_0$ in addition to the assumption we have already made that $B_0^2 = B B_0 \cdot \boldsymbol{B}_0 = 0$. We also assume that gravity is constant. We can verify that (6.169) reduces to

$\frac{d}{dz} \left[ \rho_0 \omega^2 \frac{d \hat{\xi}}{dz} \right] - k_0^2 \rho \left( \omega^2 - N_B^2 \right) \hat{\xi} = 0, \quad (6.170)$

where

$N_B^2 = -\frac{1}{\rho_0} \left( \frac{\rho_0' g^2}{\gamma \rho_0} + g \frac{d \rho_0}{dz} \right) = -g \left( \frac{1}{\rho_0} \frac{d \rho_0}{dz} - \frac{1}{\gamma \rho_0} \frac{d p_0}{dz} \right) = -g \left( \frac{d \ln(\rho_0)}{dz} - \frac{1}{\gamma} \frac{d \ln(p_0)}{dz} \right) = \frac{g}{\gamma} \frac{d \ln \left( p_0 \rho_0^{-\gamma} \right)}{dz} \quad (6.171)$

is the so-called Brunt-Väisälä frequency. In (6.171), we use the equilibrium equation, $d p_0 / d z = -g$. For an isothermal gas $\gamma = 1$ and the temperature gradient is zero. Thus, in an isothermal celestial body the Brunt-Väisälä frequency is zero. An atmosphere with a steep temperature gradient is likely to be convective (with negative $N_B^2$ and not satisfying the Schwarzschild criterion for stability, as described in Chapter 2) whereas one with a shallow temperature gradient should be stable (and