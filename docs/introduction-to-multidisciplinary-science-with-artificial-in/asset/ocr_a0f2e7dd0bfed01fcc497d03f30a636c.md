**Computational exercise:** We now use the differential equation solvers in Table 6.4 to predict particle motions in the presence of nonuniform magnetic fields. (1) Validate this code by reproducing the results in Figure 6.8b. (2) These codes contain four examples of nonuniform magnetic fields. Modify this code as necessary to reproduce the results in Figures 6.13, 6.14, and 6.15.

Magnetic bottles can be used to temporarily trap charged particles. It is easier to trap electrons than ions, because electrons are so much lighter (they have a lower mass). This technique is used to confine the high energy of plasma in fusion experiments, as we will discuss later. Magnetic confinement is actually the general principle of magnetic confinement fusion. However, magnetic bottles are leaky. Particles that make up a loss cone will leak out of the magnetic bottle.

# 6.2.4. Charged Particles in Earth-like Magnetic Fields and Van Allen Radiation Belts

Our objective in this subsection is to study the trajectory and dynamics of charged particles (electron, proton, alpha particles, and ionospheric oxygen ions) in the presence of the earth-like’s magnetic field. We approximate the Earth’s magnetic field as a giant dipole field. In other words, we consider an approximate model of charged particle motion in a strong dipole magnetic field (see also Table 6.5). In the Cartesian coordinate system, this dipole can be expressed as follows (Öztürk, 2012):

$\boldsymbol{B}=\frac{\mu_0}{4\pi|\boldsymbol{x}|^3}\left[3\left(\boldsymbol{M}\cdot\frac{\boldsymbol{x}}{|\boldsymbol{x}|}\right)\frac{\boldsymbol{x}}{|\boldsymbol{x}|}-\boldsymbol{M}\right]=-\frac{B_{\mathrm{eq}}R_{\mathrm{earth}}^3}{|\boldsymbol{x}|^5}\left[3xz,\ 3yz,\ 2z^2-x^2-y^2\right]^T$, (6.62)

with

$\boldsymbol{M}=-M_0\boldsymbol{i}_z\quad\text{and}\quad M_0=(4\pi/\mu_0)B_{\mathrm{eq}}R_{\mathrm{earth}}^3$, (6.63)

where $B_{\mathrm{eq}}=3.07\times10^{-5}$ Tesla is the magnetic field strength at the Earth’s surface measured at magnetic equator (i.e., at $x=R_{\mathrm{earth}}$, $y=0$, and $z=0$) and $R_{\mathrm{earth}}$ is the Earth’s radius, $|\boldsymbol{x}|^2=x^2+y^2+z^2$, and $\boldsymbol{M}$ is the dipole moment. For Earth, we conventionally take $\boldsymbol{M}$ to be anti-parallel to the $z$-axis because the magnetic north pole is near the geographic south pole, as we will discuss later in this chapter. The trajectory and dynamics of charged particles (electron, proton, alpha particles) in this magnetic field configuration can be obtained by solving this system of six ordinary differential equations:

$\frac{d\boldsymbol{x}}{dt}=\boldsymbol{v}\quad\text{and}\quad\frac{d\boldsymbol{v}}{dt}=\frac{q}{m}(\boldsymbol{v}\times\boldsymbol{B})$, (6.64)

where $m=\gamma m_0$, where $m_0$ is the rest mass and $\gamma=(1-v^2/c_0^2)^{1/2}$ is the relativistic factor. Notice that $\gamma=1$ for non relativistic motions. The velocity vector is $\boldsymbol{v}=[v_x,v_y,v_z]^T$ and its magnitude is estimated from the kinetic energy, $\mathcal{U}_k$ of particle using the following equation:

$v=c_0\left[1-\left(\frac{m_0c_0^2}{m_0c_0^2+\mathcal{U}_k}\right)^2\right]^{1/2}$. (6.65)