
![](img/f5b5b8709fc3a81631262f22d3552c5e_706_0.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_706_1.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_706_2.png)

![](img/f5b5b8709fc3a81631262f22d3552c5e_706_3.png)

Figure 6.45. (a) Nebula houses baby stars in every spiral arm of the galaxy. (b) A zoom of a baby star. (c) The cloud wants to dissipate due to internal cloud pressure (here p_cloud) and gravity wants to pull it together. Collapse occurs if the inward directed gravitational force is bigger than the outward directed pressure force. Material crunches down into a disk which is the beginning of an eventual star. As gravity pulls more gas toward the center of the disk it gets denser and stiffer until it reaches about 15 or so million degrees Kelvin. (d) Hydrogen atoms fuse together to form helium and the star shines.

same techniques, the key differences in the parameters that govern overall force balance should not be lost sight of.

For example, the parameter β = 2μ0ρ/B² is small for tokamak plasmas and usually large for astrophysical plasmas. So plasma dynamics in tokamaks is always dominated by magnetic fields whereas this may not be the case for astrophysical plasmas.

## The properties and observables of accretion disks.

Infalling matter powers the central gravitating object with its gravitational energy. This process includes the gradual loss of angular momentum by infalling matter. This allows matter to progressively move inwards, toward the central gravitating object. Therefore, infalling matter on the disk follows a round path until it loses angular momentum before falling into the central object. As material falls into the central object, gravitational potential energy is released. This energy release heats the plasma. The hot plasma radiates away the energy, providing an observational signature of accretion. Note that black holes themselves do not shine, but accretion disks do.

## Table 6.11. A short summary of the accretion disk properties. PPS stands for proto-planetary systems, WD for white dwarfs, BH for black holes, and NS for neutron stars.

| Central object | Disk size (km) | T (K) | Luminosity | Disk thickness | Example |
|---|---|---|---|---|---|
| • 1-3 m_sun | 10^4 – 10^10 | 10 – 10^5 | L << L_Edd | Thin | PPS WD |
| •3-20 m_sun | 10 – 10^6 | 10^3 – 10^7 | L < L_Edd | Thin | BH, NS Binary stars |
| • 10^6 – 10^9 m_sun | 10 – 10^6 | 10^3 – 10^7 | L > L_Edd L >> L_Edd | Thick | BH, AGN neutron star |

Table 6.11 summarizes the accretion disk properties. During star formation, the central part of a dense molecular cloud collapses into a proto-star with a gaseous envelope that eventually settles on a rotating proto-planetary accretion disc. Accretion in such disks triggers planet and planetary system formation. Proto-stars are heavily embedded in gas and dust. They are visible only in the infrared, millimetre or sub-millimetre wavelength bands. Most galaxies have supermassive (millions to billions of solar masses) black holes at their centres (nuclei). In AGN, black hole accretion generates radiative power that usually outshines its host galaxy. The accretion disk is surrounded by hot gas clouds. King (2015) shows that there might be a limit of about 50 billion times the mass of the Sun to how massive the biggest supermassive black holes in the Universe can get. At some point in their size, their accretion disk might get so immense that the friction and other forces between infalling matter might create instability. This might lead to the whole accretion disk collapsing into a multitude of stars.

**Quiz:** Determine the amount of energy released by 1 kg of infalling matter onto (1) White dwarf with m_wd = 0.85 m_sun and r_wd = 6.6 × 10^6 m = 0.0095 r_sun and (2) neutron star with m_ns = 1.5 m_sun and r_ns = 10 km.

## Magnetorotational Instability (MRI) Criterion.

The three fundamental phenomena behind accretion disks are gravity, angular momentum conservation, and dissipation. Dissipation is a crucial part of this process because, without it, a disk would conserve angular momentum and, hence, rotate forever without change. However the idea of rotating material losing its angular momentum is the most challenging. Remember that the specific angular momentum (i.e. the angular momentum per unit mass) is an increasing function of orbital radius, r; i.e.,

$$\hat{L}(r) = \frac{L}{\rho} = \sqrt{G m r}.$$ (6.246)

If angular momentum is conserved with r = constant, rotating material would orbit forever without accretion. To get closer to the central object, the rotating material must lose its angular momentum. The current solution to the accretion disk problem with angular momentum conservation is the MHD instability known as magnetorotational instability, where the accretion disk is described as a spinning disk with a central object in the presence of a magnetic field (Velikhov, 1959; Chandrasekhar, 1960; Balbus and Hawley, 1991; Hawley and Balbus, 1991; and Latter et al., 2015). Velikhov (1959) and Chandrasekhar (1961) demonstrated the existence of instability in magnetized rotating flows, but the importance of this instability for accretion disks was not recognized. Magnetorotational instability was rediscovered and applied to accretion disks in breakthrough work by Balbus and Hawley (1991). In equations (6.181) to (6.185), we describe the fundamental mathematics of magnetorotational instability. They are based on simple perturbations in cylindrical coordinates. We will focus only here on extracting from these derivations the dispersion equation that describes magnetorotational instability.

To describe a particle orbiting in a disk, cylindrical coordinates are the natural choice to take advantage of the cylindrical symmetry of this accretion disk configuration. By using the WKB approximation mentioned above the local dispersion equation associated with (6.185) is

$$ (\alpha^2 + k_0^2) \left(\omega^2 - \omega_A^2\right)^2 - k_0^2 \kappa^2 \left(\omega^2 - \omega_A^2\right) - 4 k_0^2 \omega_A^2 \Omega^2 = 0 \ , \qquad (6.247) $$

where $\kappa^2$ is the epicyclic frequency and $\Omega(r)$ is the angular frequency [not confused with $\Omega_0(r)$ introduced in KHI]. Basically, the epicyclic frequency indicates how much specific angular momentum (i.e., how much angular momentum per unit mass) will be measured, where $\kappa^2$ is the epicyclic frequency and $\Omega(r)$ is the angular frequency [not confused with $\Omega_0(r)$ introduced in KHI]. Epicyclic frequency is a measure of how much specific angular momentum (i.e., angular momentum per unit mass)

$$ \hat{L}(r) = \frac{L}{\rho} = r^2 \Omega \implies \frac{\partial \hat{L}(r)}{\partial t} = 0 \ , \text{if } \kappa^2 = 0 \ . \qquad (6.248) $$

The corresponding two solutions to are

$$ \omega^2 = \omega_A^2 + \frac{k_0^2}{2 \left(k_0^2 + \alpha^2\right)} \kappa^2 \pm \sqrt{\left(\frac{k_0^2}{2 \left(k_0^2 + \alpha^2\right)} \kappa^2\right)^2 + 4 \frac{k_0^2}{k_0^2 + \alpha^2} \omega_A^2 \Omega^2} \ . \qquad (6.249) $$

The expressions for the most global modes ($\alpha^2 \ll k_0^2$) yield the instability criteria,

$$ \omega^2 \approx \omega_A^2 + \frac{\kappa^2}{2} \pm \sqrt{\kappa^4 + 16 \omega_A^2 \Omega^2} \iff_{\omega^2 < 0} \begin{cases} \kappa^2 < 0 & \text{for } \omega_A = 0 \\ \kappa^2 - 4 \Omega^2 < -\omega_A^2 & \text{for } \omega_A \neq 0 \end{cases} \ . \qquad (6.250) $$

Equation (6.185) of $\kappa$ and the above equations allow us to differentiate between the stability of a hydrodynamic disk ($\omega_A^2 = 0$) and the stability of a magnetohydrodynamic disk ($\omega_A^2 \neq 0$).

## Keplerian disk configuration.

Let us start by recalling that if most of the mass of the system is concentrated at the center, as in the solar system, the speed of any orbiting body, such as a planet, is inversely proportional to the square root of its distance from the center. The fact that spiral galaxies do not have a rotation curve like this indicates that their overall mass distribution is different from the distribution of matter that can be seen. This is a significant piece of evidence
