
![](img/f5b5b8709fc3a81631262f22d3552c5e_774_0.png)

Figure A.5. (left) A snapshot of wave propagation through a medium containing a free surface. We have used the staggered finite-difference modeling technique for these computations. (right) The same snapshot with an absorbing boundary condition instead of a free surface. We have used the PML’s absorbing boundary condition. The dotted lines here indicate the interfaces.

$$\frac{\partial e_{33}(\mathbf{x},t)}{\partial t} = \frac{\partial}{\partial t}\left[\frac{\partial v_3(\mathbf{x},t)}{\partial x_3}\right] + d_1(x_1)\left[\frac{\partial v_3(\mathbf{x},t)}{\partial x_3}\right]\tag{A.135}$$

$$\frac{\partial \tau_{jk}(\mathbf{x},t)}{\partial t} + d_k(x_k)\tau_{jk}(\mathbf{x},t) = c_{jkpq}(\mathbf{x})e_{pq}(\mathbf{x},t)\tag{A.136}$$

Ikelle and Amundsen (2018) provides the Matlab implementation of these equations in a Madariaga-Virieux scheme. Figure A.5 shows the application of the PML scheme based on this code. The absorbing length is only 10 gridpoints. We can see how accurate the PML boundary conditions are, even for a strip of 10 gridpoints, especially when they are compared to the results of damping boundary conditions in Figure A.4. The key steps in the 3D finite-difference staggered-grid modeling algorithms described in this section are given in Figure A.6. The large size of the 3D models is still one of the impediments in the running of 3D FDM.

## A.5. Modeling of the Schrödinger Equation

### A.5.1. Finite-Difference Scheme

As described in Chapter 4, the time evolution of a particle of mass $m$, described by a wave function $\Psi(\mathbf{x},t)=\Psi_R(\mathbf{x},t)+i\Psi_I(\mathbf{x},t)$, is

$$-\frac{\hbar^2}{2m}\nabla^2\Psi(\mathbf{x},t)+V(\mathbf{x})\Psi(\mathbf{x},t)=i\hbar\frac{\partial\Psi(\mathbf{x},t)}{\partial t}\tag{A.137}$$

$\hbar\frac{[\Psi_I]_{i,j,k}^{n+1/2} - [\Psi_I]_{i,j,k}^{n-1/2}}{\Delta t} = \frac{\hbar^2}{2m}\left[\frac{[\Psi_R]_{i+1,j,k}^n - 2[\Psi_R]_{i,j,k}^n + [\Psi_R]_{i-1,j,k}^n}{(\Delta x)^2} + \frac{[\Psi_R]_{i,j+1,k}^{n+1/2} - 2[\Psi_R]_{i,j,k}^n + [\Psi_R]_{i,j-1,k}^n}{(\Delta y)^2} + \frac{[\Psi_R]_{i,j,k+1}^n - 2[\Psi_R]_{i,j,k}^n + [\Psi_R]_{i,j,k-1}^n}{(\Delta z)^2}\right] - [V]_{i,j,k}[\Psi_R]_{i,j,k}^n \quad (A.139)$

Using the same derivation as the previous section, we ensure that the scheme is stable by selecting the time step as follows:

$\Delta t < 2\left[\frac{2\hbar}{m}\left(\frac{1}{(\Delta x)^2} + \frac{1}{(\Delta y)^2} + \frac{1}{(\Delta z)^2}\right) + \frac{\max_{i,j,k}[[V]]_{i,j,k}}{\hbar}\right]^{-1}. \quad (A.140)$

We can again apply the PML boundary condition.

### A.5.2. Time-Space Solution in 1D Case

The Schrödinger equation for a one-dimensional quantum system is given as

$-\frac{\hbar^2}{2m}\frac{d^2\psi}{dx^2} + V(x)\psi(x) = U\psi(x). \quad (A.141)$

For simplicity, we choose our system of units such that the particle mass $m$ is the unit of mass, and $\hbar$ is also the unit of angular momentum. Furthermore, we assume that the potential $V$ does not depend on time. The reduced Schrödinger equation is

$-\frac{1}{2}\frac{d^2\Psi(x,t)}{dx^2} + V(x,t)\Psi(x,t) = i\frac{\partial\Psi(x,t)}{\partial t}. \quad (A.142)$

The Schrödinger equation is effectively a reaction-diffusion equation. Using the central difference for the second order derivative, the Laplace operator can be calculated as

$\nabla^2\Psi(x,t) \approx \frac{\Psi(x+\Delta x,t) - 2\Psi(x,t) + \Psi(x-\Delta x,t)}{\Delta x^2} \quad (A.143)$

Now let’s turn our attention to time-evolution. Then Ψ(x,t+Δt) can be computed on each point of the grid using a Runge Kutta of 4th order method; i.e.,

$$\Psi(x,t+\Delta t)=\Psi(x,t)+\frac{\Delta t}{6}(k_1+2k_2+2k_3+k_4)\ ,\tag{A.146}$$

where

$$k_1=f(x,\Psi)\ ,\ k_2=f\left(\Psi+\frac{\Delta t}{2}k_1\right)\ ,$$

$$k_3=f\left(\Psi+\frac{\Delta t}{2}k_2\right)\ ,\ \text{and}\ k_4=f(\Psi+\Delta t\,k_3)\ .\tag{A.147}$$

One can use the Matlab function ode45 for numerical implementation. For cases where the Hamiltonian is space independent, the algorithm reduces to the Runge Kutta application.

### A.5.3. Time-Independent Solution in the 1D Case

As discussed in Chapter 4, in this case Schrödinger equation reduces to an eigen-function equation

$$\hat H\psi(x)=U\psi(x)\ .\tag{A.148}$$

After sampling, ψ(x) becomes an eigenvector and U becomes an eigenvalue. More explicitly, we have

$$-\frac{\hbar^2}{2m}\frac{d^2\psi}{dx^2}+V(x)\psi(x)=U\psi(x)\ .\tag{A.149}$$

For simplicity, we use units like m=1 and ħ=1. Hence our equation becomes

$$-\frac{1}{2}\frac{d^2\psi}{dx^2}+V(x)\psi(x)=U\psi(x)\ .\tag{A.150}$$

Using the second-order centered derivative formula, we can discretize (A.150) as follows:

$$-\frac{1}{2}\left(\frac{\psi_{j+1}-2\psi_j+\psi_{j-1}}{\Delta x^2}\right)+V_j\psi_j=U\psi_j\tag{A.151}$$

or

$$\left[\hat T_{ij}+\hat V_{ij}\right]\psi_j=U\psi_i\ ,\tag{A.152}$$

where

$$\hat T=-\frac{1}{2(\Delta x)^2}\begin{pmatrix}-2&1&0&\dots&\dots&0\\1&-2&1&\dots&\dots&0\\0&1&-2&\dots&\dots&0\\\vdots&\vdots&\vdots&\ddots& &\vdots\\\vdots&\vdots&\vdots& &\ddots&1\\0&0&0&\dots&1&-2\end{pmatrix}\ ,\tag{A.153}$$

\hat{V} = \begin{pmatrix} V(x_1) & 0 & \cdots & \cdots & \cdots & 0 \\ 0 & V(x_2) & 0 & \cdots & \cdots & 0 \\ \vdots & 0 & \ddots & & & \vdots \\ \vdots & \vdots & & \ddots & & \vdots \\ \vdots & \vdots & & & \ddots & 0 \\ 0 & 0 & \cdots & \cdots & 0 & V(x_N) \end{pmatrix}. \quad (A.154)

## Appendix B

### Answers to Some of the Quizzes and Exercises

### Chapter 1:

- Suppose it takes a planet 3.09 days to make one orbit (assumed to be circular) around the Sun. The distance of this planet from our Sun is 6.433 × 10⁶ km. (1) How fast is this planet moving? (2) What is the mass of the planet?

(1) The orbital speed of the planet is

$T = \frac{2\pi r}{v} \Longrightarrow v = \frac{2\pi r}{T} = \frac{2\pi \times 6.433 \times 10^9\ \text{m}}{3.09 \times 86400\ \text{s}} = 151\ \text{km/s}.$

(2) Using the fact that

$v = \sqrt{\frac{G m_1}{r}} \Longrightarrow m_1 = \frac{4\pi^2 r^3}{G T^2}$

$= \frac{4\pi^2 \times (6.433 \times 10^9\ \text{m})^3}{(6.67 \times 10^{-11}\ \text{N m}^2\text{kg}^{-2}) \times (3.09 \times 86400\ \text{s})^2} = 2.21 \times 10^{30}\ \text{kg}$

- What is the force of Earth's gravity on a 100-kg man at the top of Mount Everest (h = 8850 m)?

$F = \frac{G m_{\text{earth}} m_{\text{human}}}{(r_{\text{earth}} + h)^2} = \frac{(6.67 \times 10^{-11})(6 \times 10^{24}\ \text{kg})(100\ \text{kg})}{(6.4 \times 10^6 + 8850)^2\ \text{m}^2} = 974.354\ \text{N}$

- The distances from the Sun to the planets and the orbital periods of planets with respect to the Sun are the key parameter in the analysis of our solar system. These parameters increase with the planet distance to the Sun (e.g., orbital periods of Mercury, Venus, Mars, Jupiter, Saturn, Uranus, and Neptune compared with that of the Earth are 0.241, 0.615, 1.88, 11.9, 29.4, 83.80, 164, 248, respectively). However, the gravities, masses, and radii of the planets do not increase or decrease with the planet distance to the Sun (e.g., gravities at surface of Mercury, Venus, Mars, Jupiter, Saturn, Uranus, and Neptune compared with that of the Earth are 0.378, 0.894, 0.379, 2.54, 1.07, 0.8, 1.2, and 0.059, respectively), why?

Because there is no relationship between orbital distance and density; the order of our planets, from densest to lightest is Earth, Mercury, Venus, Mars, Neptune, Jupiter, Uranus, and Saturn. The current planetary positions are not necessarily where they were formed, so there might have been a more orderly sorting in the early solar system. The planetary composition of the gas giants is clearly different from the rocky planets. Their size is also dramatically different for two reasons. First, the original planetary nebula contained more gasses and ices than metals and rocks. There was abundant hydrogen, carbon, oxygen, nitrogen, and less silicon and iron, giving the outer planets more building material. Second, the stronger gravitational pull of these giant planets allowed them to collect large quantities of hydrogen and helium, which could not be collected by weaker gravity of the smaller planets. Jupiter's massive gravity further shaped the solar system and growth of the inner rocky planets. As the nebula started to coalesce into planets, Jupiter's gravity accelerated the movement of nearby materials, generating destructive collisions rather than constructively gluing material together. These collisions created the asteroid belt, located between Mars and Jupiter (see Chapter 1). This asteroid belt is the source of most meteorites that currently impact the Earth. Study of asteroids and meteorites help us to determine the age of Earth and the composition of its core, mantle, and crust. Jupiter's gravity may also explain Mars's smaller mass, with the larger planet consuming material, as it migrated from the inner to outer edge of the solar system. The rarity of the heavy elements partly explains the limited size of the terrestrial planets.

- (a) What is the eccentricity of the Earth's orbit? (b) Show that the equation of an ellipse can be also written as

$$r = \frac{a(1 - e^2)}{1 + e \cos \theta}.$$

where r and θ are the distance and angle, respectively, as defined in Figure 1.12.

The measured distances semi-major and semi-minor axes give for the eccentricity of the Earth's orbit e = √(a² - b²)/a = 0.01674. Use x = r cos θ and y = r sin θ to obtain the above equation of an ellipse.

- The apparent weight w of an object depends on the latitude θ at which it is measured. In contrast, the true weight is entirely due to the Earth's gravity and its magnitude equals w = m g_e and is the same everywhere (m is the mass of the object). (a) If the tangential speed of a point on the surface of the Earth at the equator is v_θ, then find the apparent weight of the object at the equator. (b) What is the apparent gravitational acceleration at the equator?

(a) Remember that

$$\boldsymbol{v} = \frac{d\boldsymbol{x}}{dt} = \frac{dr}{dt}\boldsymbol{i}_r + r\frac{d\boldsymbol{i}_r}{d\theta}\frac{d\theta}{dt} = \frac{dr}{dt}\boldsymbol{i}_r + r\frac{d\theta}{dt}\boldsymbol{i}_\theta$$

At the equator v_θ is the component of velocity along i_θ; i.e.,

$$v_\theta = R \frac{d\theta}{dt}$$
