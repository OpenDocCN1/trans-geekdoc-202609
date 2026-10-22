
radial, $\boldsymbol{v} = v(r)\hat{\boldsymbol{i}}_r$, $\rho = \rho(r)$, and the gravitational acceleration $-\nabla\Psi = \boldsymbol{g} = g\hat{\boldsymbol{i}}_r$ obeys the inverse square law, $g = G_0 m_{\text{sun}}/r^2$. Assuming that the spherical coordinates are $(r,\theta,\phi)$, the components of $\boldsymbol{v}$ along $\theta$ and $\phi$ are zero. The temperature is constant and, consequently, the sound speed is $c_s^2 = p/\rho$ as $\gamma = 1$. The mass-continuity and momentum-conservation equations become

$$\frac{d(r^2 \rho v)}{dr}=0\ \text{(or }r^2\rho v=\text{cst)}\ \Longleftrightarrow\ \frac{1}{\rho}\frac{d\rho}{dr}= -\frac{1}{r^2 v}\frac{d(r^2 v)}{dr}\tag{6.105}$$

$$\rho v\frac{dv}{dr}= -\frac{dp}{dr} -\frac{G_0 m_{\text{sun}}\rho}{r^2}\ \underset{c_s^2=p/\rho}{\Longleftrightarrow}\ v\frac{dv}{dr}= -c_s^2\frac{1}{\rho}\frac{d\rho}{dr} -\frac{G_0 m_{\text{sun}}}{r^2}.\tag{6.106}$$

In these derivations, we used differential operators in spherical coordinates; i.e.,

$$\nabla a = \frac{da}{dr}\quad\text{and}\quad \nabla\cdot\boldsymbol{A}= \frac{1}{r^2}\frac{d(r^2 A_r)}{dr},\tag{6.107}$$

where $a$ is an arbitrary scalar function of $r$ and $\boldsymbol{A}$ is an arbitrary vector with only a radial component that depends on $r$. By substituting (6.105) into (6.106), we arrive at

$$v\frac{dv}{dr}= \frac{c_s^2}{r^2 v}\frac{d(r^2 v)}{dr} -\frac{G_0 m_{\text{sun}}}{r^2}\ \Longleftrightarrow\ \left(v-\frac{c_s^2}{v}\right)dv = 2\frac{c_s^2}{r^2}(r-r_c)dr,$$

where $r_c = G_0 m_{\text{sun}}/(2c_s^2)$ is the critical radius showing the position where the wind speed reaches the sound speed, $v = c_s$. This last equation can readily be integrated to obtain the Parker equation; i.e.,

$$\left(\frac{v}{c_s}\right)^2 -\log\left(\frac{v}{c_s}\right)^2 = 4\log\left(\frac{r}{r_c}\right)+4\frac{r_c}{r}+C.\tag{6.108}$$

where $C$ is the constant of integration that can be determined from boundary conditions. There are a number of mathematically admissible classes of solutions to this equation that depend on $C$. These solutions are illustrated in Figure 6.29.

We can see that if the flow makes a transition from subsonic to supersonic or vice versa (transonic waves), it must pass at $r = r_c$ in order for the velocity gradient to remain finite. We basically have six classes of solutions with different behavior at small $r$ values and at $r \to \infty$. There are some that are unphysical, such as classes 5 and 6, which predict two wind speeds at a given radius. There is also no wind speed over significant ranges of $r/r_c$, including $r = r_c$. Solutions of class 4 suggest the wind speed is supersonic, irrespective of $r$. The idea that at the base of the Corona, particles move faster than the speed of sound is inconsistent with measurements. Although solutions of class 3 are transonic, they also suffer from the fact that particles streaming from the Corona move faster than the speed of sound. This is inconsistent with the measurements. Solutions of class 1 suggest that the wind speed is subsonic, irrespective of $r$. They are called the solar breeze solutions. Before the advent of direct measurements, this solution was considered seriously.

![](img/f5b5b8709fc3a81631262f22d3552c5e_662_0.png)

Figure 6.29. The six mathematical classes of solutions to the Parker solar wind model.

Parker (1958) predicted that the physical solutions would be those of class 2. For solar wind, he predicted that the smallest speed of solar wind is at $r = r_{\text{sun}}$, which is the base of the Corona layer (see Figures 6.2 and 6.3). He also found that the wind speed becomes supersonic as we move away from the Corona. His conclusions were met with skepticism until the first sporadic measurements of solar wind speed by Soviet Lunik 3 and Venus 1 in 1959 and later continuous measurements by Mariner 2 in 1962 between 0.3 AU and 1 AU from the sun center.

The class 2 solutions correspond to $C = -3$ in equation (6.108), as can be verified by substituting $v = c_s$ and $r = r_c$. Parker’s solution passes through the critical point (the model places the critical point at about $11.5 r_{\text{sun}}$ for a million degree Corona) and the wind is supersonic for $r > r_c$. For example, assuming a typical Coronal temperature is $T = 10^6$ degrees Kelvin (one million degrees Kelvin), the sound speed is

$$c_s = \sqrt{RT} = (8.3 \times 10^7 \times 10^6)^{1/2} \approx 10^7 \ \mathrm{cm/s} = 100 \ \mathrm{km/s},$$

and the critical radius is

$$r_c = \frac{G_0 m_{\text{sun}}}{2 c_s^2} = 7 \times 10^9 \ \mathrm{m} \approx 10 r_{\text{sun}}.$$

To put this into context, the radius of Earth’s orbit is $214 r_{\text{sun}}$. Thus, the solar wind is highly supersonic by the time it reaches Earth. To calculate the actual wind speed from Parker’s model we set $r = 214 r_{\text{sun}}$ and solve for $v$. Hence,

$$\left(\frac{v}{c_s}\right)^2 - \log \left(\frac{v}{c_s}\right)^2 = 4\log \left(\frac{214}{10}\right) + 4\frac{10}{214} - 3 = 9.44$$

By using the Newton-Raphson method (e.g., Matlab), we obtain $v = 3.45 c_s = 310$ km/s. Observations at 1 AU give the quiet solar wind as $v = 320$ km/s. Thus, Parker’s solar wind model gives quite an accurate estimation of the velocity. If $T = 2 \times 10^6$ degrees Kelvin, the wind speed is about 600 km/s. As we will discuss later, in the context of wave propagation in plasma, the fact that Parker (1958) ignored the magnetic field in his derivation of solar wind speed does not change his results in any significant way.

Figure 6.30 shows the solar wind speeds measured by the joint ESA/NASA Ulysses mission. Ulysses was launched on October 6, 1990. Its probe was equipped with scientific instruments capable of detecting and measuring solar wind ions and electrons, magnetic fields, radio and plasma waves, dust and gas, X-rays, and gamma rays. In addition to determining that particles of solar wind usually travel at speeds of 300–700 km/s, this mission helped determine that the Sun’s magnetic field reverses direction every 11 or so years. High-speed solar wind originates from coronal holes in the sun’s polar regions, while slow-speed solar wind originates from streamers. The north and south poles of the Sun have large, persistent coronal holes, so high latitudes are filled with fast solar wind (generally greater than 500 km/s). In the equatorial plane, where the Earth and the other planets orbit, the most common state of the solar wind is the slow speed wind, with speeds less than 400 km/s. This portion of the solar wind forms the equatorial current sheet. In other words, the solar wind at the poles is typically faster than in the ecliptic plane.

As one might expect, the solar wind is always directed away from the Sun, and it carries with it magnetic clouds. The heliospheric magnetic field (HMF), also known as the interplanetary magnetic field (IMF), is a part of the Sun’s magnetic field that is carried into interplanetary space by the solar wind. The IMF is considered to be "frozen in" solar wind plasma as described earlier; that is, the IMF is embedded in the plasma and flows outward with the solar wind. Because of the Sun’s rotation, the IMF, like the solar wind, travels outward in a spiral pattern. The low-speed wind is denser than the high-speed wind ($n \approx 10^7$ cm$^{-3}$ as opposed to $n \approx 10^6$ cm$^{-3}$). Thus, the Sun constantly loses mass, through particles carried away from the Sun by the solar wind, at a rate of about $2.5 \times 10^{-14}$ solar mass per year. Note that the solar wind does not come from the whole of the sun’s surface but only from the regions where the magnetic field is open—that is, where field lines emerge. This is only about 20 percent of the whole surface. About 80 percent of the magnetic field is closed, effectively holding in the hot Corona.

The fast wind from the polar coronal holes carries magnetic fields of opposite polarity into the heliosphere, which are then separated by the heliospheric current sheet (HCS) embedded in the slow wind. Measurements over a range of latitudes far from the Sun show that this boundary is not symmetric around the Sun’s equator, but is on average displaced southward. This offset must reflect an asymmetry on the Sun; but since there cannot be a mismatch between the inward and outward magnetic flux on the Sun, its origin is unclear. In situ, the HCS is warped and
