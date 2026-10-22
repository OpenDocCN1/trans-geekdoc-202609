
## 6.5.2. Three-fluid Ohm’s Law

The three-fluid model considers electrons, ions, and neutral particles as three fluids—that is, a plasma does not have to consist only of electrons and ions. Neutral particles can also be present in plasmas, especially in partially ionized plasmas. It also takes into account their collisions, that is, electron-ion, electron-neutral, and ion-neutral collisions. This model is particularly useful in describing the interaction between the magnetosphere, ionosphere, and thermosphere (see Figure 6.7). The corresponding equations of motion are

$$m_e\left[\frac{\partial}{\partial t}+\mathbf{v}_e\cdot\nabla\right]\left(n_e\mathbf{v}_e\right)= -\nabla p_e - n_e e\left(\mathbf{E}+\mathbf{v}_e\times\mathbf{B}\right)$$ $$+ m_e n_e \nu_{ei}\left(\mathbf{v}_i-\mathbf{v}_e\right)$$ $$+ m_e n_e \nu_{en}\left(\mathbf{v}_e-\mathbf{v}_n\right),\tag{6.262}$$ $$m_i\left[\frac{\partial}{\partial t}+\mathbf{v}_i\cdot\nabla\right]\left(n_i\mathbf{v}_i\right)= -\nabla p_i + n_i e\left(\mathbf{E}+\mathbf{v}_i\times\mathbf{B}\right)$$ $$- m_e n_i \nu_{ei}\left(\mathbf{v}_i-\mathbf{v}_e\right)$$ $$+ m_i n_i \nu_{in}\left(\mathbf{v}_i-\mathbf{v}_n\right),\tag{6.263}$$ $$m_n\left[\frac{\partial}{\partial t}+\mathbf{v}_n\cdot\nabla\right]\left(n_n\mathbf{v}_n\right)= -\nabla p_n + m_n n_n \nu_{ni}\left(\mathbf{v}_n-\mathbf{v}_i\right)$$ $$+ m_n n_n \nu_{ne}\left(\mathbf{v}_n-\mathbf{v}_e\right),\tag{6.264}$$

where the subscripts e, i, and n are associated with electrons, ions, and neutrals, respectively, $\nu_{ei}$ is the electron-ion collision frequency, $\nu_{ni}$ is the neutral-ion collision frequency, and $\nu_{ne}$ is the neutral-electron collision frequency. Compared to (6.252) and (6.253), we now have added the effects of neutrals on charged particles to the collision terms, in (6.262) and (6.263). Notice that equation (6.264) can be ignored in the derivations of the generalized Ohm’s law because it does not include the electric current density or electromagnetic fields. The derivations are the same for two fluids. We multiply equation (6.262) by $-(e\nu_{in})/m_e$ and add it to equation (6.263) multiplied by $(e\nu_{en})/m_i$, and neglect the inertia terms. We eliminate $v_n$ in this process. We then arrive at the generalized Ohm’s law by using the fact that $m_i \gg m_e$ neglects the small terms of the order of the ratio $m_e/m_i$. However, the coefficients associated with the electric current-density and electromagnetic-field vectors, in (6.258), for example, include ion-neutral and electron collision frequencies. The physical benefits of the three fluid models are gained from the examination of these different coefficients. For the particular case of partially ionized plasmas (i.e., electron-ion collisions are rare), the generalized Ohm’s law pertaining to these three fluid models is

$$\mathbf{J}=\sigma_P\left[\mathbf{E}+(\mathbf{v}\times\mathbf{B})\right]-\alpha_H\frac{\mathbf{J}\times\mathbf{B}}{B},\tag{6.265}$$

with

$$\sigma_P = \frac{e^2 n_e}{m_e} \frac{m_i \nu_{in} + m_e \nu_{en}}{m_i \nu_{in} \nu_{en}} \quad \text{and} \quad \alpha_H = \frac{e}{m_e} \frac{m_i \nu_{in} - \frac{m_e}{m_i} m_e \nu_{en}}{m_i \nu_{in} \nu_{en}},$$

assuming pressure $p_e$ is constant and current density, $J$, is smooth, $\nu_{in} \neq 0$, and $\nu_{en} \neq 0$. One can verify that the solution to (6.265) is

$$\boldsymbol{J} = \sigma_P \boldsymbol{E}_\parallel^{(\text{eff})} + \sigma_\perp \boldsymbol{E}_\perp^{(\text{eff})} + \sigma_H \boldsymbol{b} \times \boldsymbol{E}_\perp^{(\text{eff})} \tag{6.266}$$

where

$$\sigma_\perp = \sigma_P (1 + \alpha_H^2)^{-1} \quad \text{and} \quad \sigma_H = \sigma_P \alpha_H (1 + \alpha_H^2)^{-1}.$$

## 6.5.3. Magnetic Reconnection: A Departure from the Ideal MHD

As described in Biskamp (2000), Yamada et al. (2010), and Ikelle (2020), magnetic reconnection is about two magnetic fields that point in opposite directions. As they move closer to each other, they break apart such that the field lines are rearranged into a pair of two U shapes. This is illustrated in Figure 6.51. At their core, magnetic reconnections are explosions that affect magnetic fields and plasmas in the vicinity of explosions. These explosions release large amounts of energy in a very small space. Magnetic field topology changes suddenly. Field lines break and reconnect.

Magnetic reconnection is a key phenomenon in astrophysical, space, and fusion plasmas. This process is observed in a variety of space and astrophysical situations, including solar flares (Giovanelli, 1946), coronal mass ejections and the aurora borealis (see Ikelle, 2024), the Earth’s magnetopause and magnetotail (Dungey, 1961), etc. Already in the 1950s, observations of solar flare reconnection were well established. In less than 20 minutes, they would flake and then die off. People could see them from a distance. It is also frequent in laboratory plasmas, such as tokamaks, spheromaks, and reversed-field pinches, although they are undesirable in these cases.

![](img/f5b5b8709fc3a81631262f22d3552c5e_722_0.png)

Figure 6.51. Illustration of the phenomenon of reconnection in which two magnetic field lines break and connect. Field lines’ directions are critical to reconnection. The two magnetic field lines must be opposites. As they get close to each other (from left to right), they break and reconnect. Two U-shaped field lines are reconnected to one another.

It cannot happen according to the ideal MHD. We need to add additional terms to Ohm’s law to allow reconnection. In the generalized Ohm’s law, there are factors such as resistivity, Hall current, electron inertia and pressure, and ambipolar diffusion that are related to weakly collisional or collisionless plasma. Since the generalized Ohm is one of the equations of the non-ideal MHD model, the non-ideal MHD can be used to model magnetic reconnection in space. Note that we return to this phenomenon in Ikelle (2024) because it plays a crucial role in the understanding of the Sun and magnetosphere interaction. Magnetic reconnection is the key mechanism for energy release in solar Corona and solar flares (see Figure 6.3).

### Another review of the differences between ideal and non-ideal MHD.

The difference between ideal and non-ideal MHD resides in the magnetic induction equation. In more general terms, this equation can be written as follows:

$$\boldsymbol{E} = -\boldsymbol{v} \times \boldsymbol{B} + \boldsymbol{R} \ , \qquad (6.267)$$

where $\boldsymbol{R}$ is the operator that differentiates the two MHD formulations. For ideal MHD, $\boldsymbol{R} = \mathbf{0}$. For non-ideal MHD, we can have

$$\boldsymbol{R} = \frac{1}{\sigma} \boldsymbol{J} + \frac{\boldsymbol{J} \times \boldsymbol{B}}{e n_e} - \frac{1}{n_e e} \nabla p_e + \frac{m_e}{n_e e^2} \frac{\partial \boldsymbol{J}}{\partial t} \qquad (6.268)$$

as defined in (6.259). Classical electromagnetism generally teaches us that magnetic field lines do not break; they are always continuous. The missing caveat is that this statement is only true when matter obeys the ideal MHD, as in Figure 6.27—that is, $\boldsymbol{E} = -\boldsymbol{v} \times \boldsymbol{B}$. The ideal MHD plasma behaves like a perfectly conducting fluid. All the examples in the third section of this chapter are limited to ideal MHD. To prove this theorem, we consider the following flux:

$$\Phi = \iint_{S(t)} \boldsymbol{B} \cdot \boldsymbol{n} dS \qquad (6.269)$$

across a moving surface with velocity $\boldsymbol{u}_\perp$. Flux can change due to $\boldsymbol{B}$ changing in time and/or the surface $S$ moving/distorting as the fluid moves. Similar to equation (6.89), we can verify that

$$\begin{aligned}
\frac{\partial \Phi}{\partial t} &= \iint_{S(t)} \frac{\partial \boldsymbol{B}}{\partial t} \cdot \boldsymbol{n} dS - \oint_{\partial S(t)} \boldsymbol{u}_\perp \times \boldsymbol{B} \cdot d\boldsymbol{l} \\
&= \iint_{S(t)} \nabla \times (\boldsymbol{v} \times \boldsymbol{B}) \cdot \boldsymbol{n} dS - \oint_{\partial S(t)} \boldsymbol{u}_\perp \times \boldsymbol{B} \cdot d\boldsymbol{l} \\
&= \oint_{\partial S(t)} (\boldsymbol{v} - \boldsymbol{u}_\perp) \cdot d\boldsymbol{l} \\
&= 0 \quad \text{if} \quad \boldsymbol{u}_\perp = \boldsymbol{v} \ .
\end{aligned} \qquad (6.270)$$

where $\boldsymbol{S} = S \boldsymbol{n}$, with $\boldsymbol{n}$ a unit vector normal to $S$, and dS the surface element of S. As a result, the plasma is connected to the field lines. We use in these derivations
