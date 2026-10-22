
where $R_c = |R_c|$ and the equation of charged particles in (6.31) becomes

$$m\frac{d\boldsymbol{v}(\boldsymbol{x},t)}{dt}=q\left(\frac{\boldsymbol{F}_{\text{cent}}}{q}+\boldsymbol{v}\times\boldsymbol{B}\right).\tag{6.47}$$

This force can be directly inserted into (6.32) to obtain the centrifugal drift velocity as follows:

$$\boldsymbol{v}_{\text{drift}}=\frac{\boldsymbol{F}_{\text{cent}}\times\boldsymbol{B}}{qB^2}=\frac{mv_{\parallel}^2}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right)=\frac{2U_{\parallel}}{qR_c^2}\left(\frac{\boldsymbol{R}_c\times\boldsymbol{B}}{B^2}\right),\tag{6.48}$$

where $U_{\parallel}=(mv_{\parallel}^2)/2$. Drift is therefore into or out of the page depending on the sign of $q$. Figure 6.14 shows an example of the guiding center trajectory of a charged particle in a non-homogeneous magnetic field with a toroidal geometry. The particles drift around the curvature of the magnetic field lines.

Because $B$ is proportional to $1/R_c$ as we can see in (6.48), we can verify that $\nabla B/B=\boldsymbol{R}_c/R_c^2$ [i.e., $\nabla(R_c^{-1})=-\boldsymbol{R}_c/R_c^3$]. Thus, we can alternatively write the drift velocity as follows:

$$\boldsymbol{v}_{\text{drift}}=\frac{2U_{\parallel}}{q}\left(\frac{\boldsymbol{B}\times\nabla\boldsymbol{B}}{B^3}\right).\tag{6.49}$$

In this form, we can directly compare grad-B and curvature drifts. To summarize, gradient and curvature drifts are in the same direction and are proportional to particle energies. Finally we can write the total guiding center drift as

$$\boldsymbol{v}_D=\underbrace{\frac{\boldsymbol{E}\times\boldsymbol{B}}{B^2}}_{E\times B\text{ drift}}+\underbrace{\frac{\boldsymbol{F}\times\boldsymbol{B}}{B^2}}_{\text{Ext--force drift}}+\underbrace{\frac{U_{\perp}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{Grad--B drift}}+\underbrace{\frac{2U_{\parallel}}{qB^3}[\boldsymbol{B}\times\nabla\boldsymbol{B}]}_{\text{Curvature drift}}.$$

These are just examples of particle drift, which is the motion of the particle's guiding center. There are a variety of known as well as unknown drifts caused by a combination of magnetic fields and external forces. The last exercise of this chapter along with the codes in Tables 6.4 and 6.6 provide readers with opportunities to experiment with the drifts described here and to explore possible new drifts. Note that particle drifts can be used to explain and describe many phenomena, such as planetary fields, coronal loops, and tokamaks.

## 6.2.3. Magnetic Mirrors

Let us stay with the case of charged particle motion in a nonuniform magnetic field with zero electric field. We can see in Figure 6.15 that as particles move in regions of strong magnetic fields, they can reflect because these regions act like mirrors. The bounce motion of a charged particle is the motion up and down along (parallel to) the magnetic field between mirrors. Our objective here is to explain this mirror effect behind bounce motion. We will start by introducing the second constant of charged particle motion, known as the magnetic moment. The other constant introduced in (6.6) is the conservation of the kinetic energy of charged particles.

## Table 6.5. Some properties of various plasmas in nature. L is the macroscopic length scales of interest or system size, B_eq is the magnetic field, and t0 is the observation time.

|  | L (km) | B_eq (T) | t0 (s) |
|---|---|---|---|
| Tokamak | 0.020 | 3 | 3 × 10⁻⁶ |
| Magnetosphere Earth | 4 × 10⁴ | 3 × 10⁻⁵ | 6 |
| Solar coronal loop | 10⁵ | 3 × 10⁻² | 15 |
| Magnetosphere neutron star | 10³ | 10¹¹ | 10⁻² |
| Accretion disc YSO | 1.5 × 10⁶ | 10⁻⁴ | 7 × 10⁵ |
| Accretion disc AGN | 4 × 10¹⁵ | 10⁻⁴ | 2 × 10¹² |
| galactic plasma | 10¹⁸ | 10⁻⁸ | 10¹⁵ |

## Table 6.6. A Matlab code for simulating single particle motion in the presence of a magnetic dipole (Earth-like magnetic dipole). The outcome is the trajectory and dynamics of charged particles (here protons).

```
close all; clear all;
e = 1.602176565e-19; mp = 1.672621777e-27; me = 9.10938291e-31;
c = 299792458; Re = 6378137 ; U = 15e6; % kinetic energy in eV
m = mp; vabs = c/sqrt(1-(m*c^2)/(U*e)); pitcha = 30.0; vx0 = 0.0;
vy0 = vabs*sin(pitcha*pi/180); vz0 = vabs*cos(pitcha*pi/180);
tf = 100; time = 0:0.01:tf;
[t,xx] = ode45(@Lorenz,time,[4*Re ;0; 0; vx0; vy0; vz0]); % solve eqn
plot3(xx(:,1)/Re,xx(:,2)/Re,xx(:,3)/Re,'r'); % trajectory in 3D
xlabel('x[Re]'); ylabel('y[Re]'); zlabel('z[Re]')
%plot(xx(:,1)/Re,xx(:,2)/Re,'r'); % trajectory in 2D
hold on; sphere(30); hold off;grid on
```

```
function xxf = Lorenz(t,xxin)
xxf = zeros(6,1); Beq = 3.07e-5; Re = 6378137; e = 1.602176565e-19;
mp = 1.672621777e-27; me = 9.10938291e-31; c = 299792458;
qem = e/mp; % qom=e/mp for proton & qom=-e/me for electron
usB00 = -Beq*Re^3/(xxin(1)^2 + xxin(2)^2 + xxin(3)^2)^2.5;
Bx = 3*xxin(1)*xxin(3)*usB00; By = 3*xxin(2)*xxin(3)*usB00;
Bz = (2*xxin(3)^2 -xxin(1)^2 -xxin(2)^2)*usB00;
xxf(1) = xxin(4); xxf(2) = xxin(5); xxf(3) = xxin(6); % (dx/dt,dy/dt,...)
xxf(4) = qem*(xxin(5)*Bz - xxin(6)*By); % dvx/dt = qem*(v x B)-x
xxf(5) = qem*(xxin(6)*Bx - xxin(4)*Bz); % dvy/dt = qem*(v x B)-y
xxf(6) = qem*(xxin(4)*By - xxin(5)*Bx); % dvz/dt = qem*(v x B)-z
end
```

where

μ_mag = (m v_⊥²)/(2B) = |q| v_⊥²/(2Ω₀) = U_⊥/B = (perpendicular kinetic energy)/(magnetic field strength). (6.51)

We are using the component of particle velocity along the magnetic field created by the grad-B drift. Quantity μ_mag is known as the magnetic moment, and because it is constant, it is conserved during particle motion. Let us prove that μ_mag is indeed

![](img/f5b5b8709fc3a81631262f22d3552c5e_631_0.png)

Figure 6.15. An illustration of a magnetic mirror with a snapshot of a charged particle motion at t = 8000 dt, t = 19000 dt, t = 29000 dt, and t = 39000 dt. The nonuniform magnetic field used here is B = Br0 i_r + Bz i_z = [Br0 cos(Ωg t), Br sin(Ωg t), Bz]^T, where Bz = Bz0 + x dBx/dx + y dBy/dy, Ωg = mq/Bz0, Br0 = 1100 nT, and Bz0 = 30 nT. More details can be found in Table 6.4. The gyroradius is larger where the field is weaker and smaller where the field is stronger. Notice that particles can reflect (bounce) on the magnetic mirror.

a constant during particle motion. Note that one can alternatively introduce the magnetic moment by using current flowing along a closed loop that encloses an area A. The current loop with area A and current I has magnetic moment μ_mag = I A / c0, where c0 is the speed of light. A charged particle moving along its Larmor radius is such a loop with A = π r_g^2 and I = q(Ω/2π) with Ω = v⊥/r_g, we obtain the result in (6.51). Note also that the magnetic moment is an adiabatic invariant, which means that it is conserved under slow changes in an external variable. Our next task is to prove this result.

If we take the dot product of both sides of (6.50) with v∥, we obtain

d/dt (1/2 m v∥^2) = - μ_mag v∥ dB/dz = - μ_mag dz/dt dB/dz = - μ_mag dB/dt . (6.52)

By using the conservation of kinetic energy, we can construct a second independent equation with μ_mag as follows:

d/dt (1/2 m v∥^2 + 1/2 m v⊥^2) = d/dt (1/2 m v∥^2 + μ_mag B) = 0 . (6.53)

We used the definition of the magnetic moment, ½mv⊥² = μmag B. By equating (6.52) and (6.53), we arrive at

```
d(μmag B)/dt − μmag dB/dt = 0 ⇔ dμmag/dt = 0 ,
```

which is satisfied for constant values of μmag with respect to time. We used, in the above derivations, the fact that the magnetic field slowly varies in time.

Conservation of the magnetic moment is basically conservation of angular momentum about the guiding center. As we defined in Ikle (2023b), the angular momentum is L = m x0 × v and its magnitude is

```
|L| = m |x0| v sinθ = m r0 v⊥ = 2m / |q| μmag ,
```

where θ is the angle between x0 and v, as defined in Ikle (2020), and v⊥ = v sinθ. As L is constant, μmag is constant as well.

## The mirror force.

Now consider the magnetic field in Figure 6.16. When the field is uniform, field lines run parallel, the particle moves along the ellipse, and the Lorentz force is perpendicular to both B and v⊥ and points toward the guiding center. When the field is nonuniform (Figure 6.16) field lines converge toward the right in this case, the magnetic field now makes an angle with respect to the magnetic field line, and thus the Lorentz force now has a non-zero component in the z-direction. Hence, the particle will be accelerated away from the direction in which the field strength increases. The particle will be reflected back, and the region of increasing magnetic field thus acts as a reflector, known as a magnetic mirror. To make this result quantitative, let us compute the Lorentz force in the z-direction in a cylindrical coordinate system:

```
Fz = q (v × B)z / c0 = q v⊥ Br / c0 ,
```

where B = Br r + Bz z , Br is the magnetic field component in the cylindrical r direction, in which the z-direction is as indicated in Figure 6.16. We assume that our magnetic field is axisymmetric (i.e., ∂B/∂θ = 0). Using the Maxwell equation ∇ · B = 0 and, again, working in cylindrical polar coordinates, we have

```
1/r ∂(r Br)/∂r + ∂Bz/∂z = 0 ⇒ ∂(r Br)/∂r = -r ∂Bz/∂z .
```

If ∂Bz/∂z is given at r = 0 and does not vary much with r, then

```
r Br ≈ -1/2 r² [∂Bz/∂z ]_{r=0} ⇒ Br = -1/2 r [∂Bz/∂z ]_{r=0} .
```

We obtain the vertical component of the Lorentz force

```
∇ · B = 1/r ∂(r Br)/∂r + ∂Bz/∂z = 0
```
