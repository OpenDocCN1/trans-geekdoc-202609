![](bbox=[0.27, 0.09, 0.76, 0.24])

# Figure 8.2 Wind turbine layout for Jensen's single wake model.

The choice of value of \(\alpha\) depends on the wind farm terrain (surface roughness, hub height) and atmospheric conditions (air turbulence). An empirical estimation of wake expansion constant \(\alpha\) is

\(\alpha = \kappa \left[ \log_e \left( \frac{h}{z_0} \right) - \psi_m(h/L) \right]^{-1}, \quad (8.2)\)

where \(\kappa = 0.4\) is the von Karman constant, and \(h\) and \(z_0\) are the hub height of turbine and surface roughness length. The factor \(\psi_m(h/L)\) determines the local atmospheric stability correction at a given hub height [26]. The effective wind speed \(u_j\) at the downwind turbine located at a distance \(x\) due to wake effect of a single upwind turbine as per Jensen's model is given as

\(u_j = u_0 \left( 1 + (\sqrt{1 - C_t} - 1) \left( \frac{r_0}{r_x} \right)^2 \right), \quad (8.3)\)

where \(C_t = a(2 - a)\) is the thrust coefficient with induction factor \(a = 1 - \frac{u_j}{u_0}\) as per Actuator disk theory.

Frandsen et al. [8] have described the wake expansion immediately after rotor as rectangular profile compared to trapezoidal profile in Jensen's model. The wind speed \(u_f\) at a downwind distance \(x\) as per Frandsen's model is given as

\(u_f = u_0 \left( \frac{1}{2} \pm \frac{1}{2} \sqrt{1 - 2 C_t \left( \frac{r_0}{r_x} \right)^2} \right). \quad (8.4)\)

An empirical result was obtained to estimate the relationship between \(r_x\) and \(C_t, \alpha\), and \(r_0\), which is given as

\(r_x = r_0 (\beta + \alpha x / 2 r_0)^{1/2}, \quad (8.5)\)