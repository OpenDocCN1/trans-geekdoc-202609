
where

```
$$A_{xx}, B_{xx}, D_{xx}, E_{xx}, F_{xx} = b \int \frac{h}{2} E(x,z)(1, z^1, z^2, z^3, z^4) dz$$
```

```
$$A_{xz}, D_{xz}, F_{xz} = b \int \frac{h}{2} G(x,z)(1, z^2, z^4) dz$$
```

(6.26)

As mentioned above, it is assumed that all porosity distributions are symmetric about the middle plane of the beams, because $B_{xx}=E_{xx}=0$. In addition, it is shown in Ref. [29] that for flexural, in-plane ($u$) and rotary ($\phi$) inertia can be neglected. Thus governing equations in terms of the reference plane can be obtained by substituting stress results (Eq. 6.25) into the governing equations (Eqs. 6.21–6.23) as:

```
$$\delta u_{ic}: \frac{\partial A_{xx}}{\partial x}\frac{\partial u}{\partial x} + \frac{1}{2}\frac{\partial D_{xx}}{\partial x^2} + A_{xx}\frac{\partial A_{xu}}{\partial x}\frac{\partial \phi}{\partial x} + B_{xx}\frac{\partial B_{xu}}{\partial x}\frac{\partial \phi}{\partial x} = 0$$
```

(6.27)

```
$$\delta \phi: \frac{\partial F_{xx}}{\partial x}\frac{\partial \phi}{\partial x} + F_{xx}\frac{\partial^2 \phi}{\partial x^2} + \frac{\partial F_{xu}}{\partial x}\frac{\partial u}{\partial x} + F_{xu}\frac{\partial^2 u}{\partial x^2} - c_1\frac{\partial H_{xx}}{\partial x}\frac{\partial \phi}{\partial x} - c_1H_{xx}\frac{\partial^2 \phi}{\partial x^2} + c_3\frac{\partial^3 \phi}{\partial x^3} = 0$$
```

```
$$-ADF_{xz} \left(\phi + \frac{\partial w}{\partial x}\right)\frac{\partial A_{xz}}{\partial x} - c_1l_4\frac{\partial w}{\partial x}\frac{\partial \phi}{\partial x} = 0$$
```

(6.28)

```
$$\delta w: \frac{\partial A_{xz}}{\partial x}\frac{\partial w}{\partial x} + \frac{1}{2}\frac{\partial D_{xz}}{\partial x^2} + A_{xz}\frac{\partial A_{xw}}{\partial x}\frac{\partial \phi}{\partial x} + B_{xz}\frac{\partial B_{xw}}{\partial x}\frac{\partial \phi}{\partial x} + A_{xx}\frac{\partial A_{xu}}{\partial x}\frac{\partial w}{\partial x} + \frac{1}{2}\frac{\partial D_{xx}}{\partial x^2}\frac{\partial w}{\partial x} = 0$$
```

```
$$\frac{\partial F_{xz}}{\partial x}\frac{\partial w}{\partial x} + F_{xz}\frac{\partial^2 w}{\partial x^2} + c_1F_{xz}\frac{\partial \phi}{\partial x}\frac{\partial w}{\partial x} - c_1H_{xx}\frac{\partial^2 w}{\partial x^2}\frac{\partial \phi}{\partial x} - 2c_1^2\frac{\partial^2 \phi}{\partial x^2}\frac{\partial w}{\partial x} = 0$$
```

```
$$-c_1^2H_{ss}\frac{\partial^4 w}{\partial x^4} - p_z P_s \frac{\partial^2 w}{\partial x^2} = I_0\ddot{w} - c_1I_0\ddot{\phi} - c_1^2I_0\frac{\partial^2 \phi}{\partial x^2}$$
```

(6.29)

Improving buckling and vibration response of porous beams

where

```
$$DF_{xz} = D_{xx} - c_1F_{xx}FH_{xx} = F_{xx} - c_1H_{xx}$$
AD_{xz} = A_{xz} - 2c_2D_{xx} + c_2^2F_{xx}DF_{xx} = D_{xx} - 2c_1F_{xx} + c_1^2H_{xx}$$
```

## 6.4 Solution methodology

In this section, the Galerkin technique is implemented to reduce the governing nonlinear partial differential equations (Eq. 6.27–6.29) to a set of nonlinear ordinary differential equations (ODEs) in time. Here, the primary resonance of the system is inspected when the beam is under a combination of a harmonic vertical load and a compressive constant axial load. The HBM is implemented to develop closed-form approximate solutions for the nonlinear fundamental natural frequency and frequency response of the system.

## 6.4.1 Galerkin technique

To solve the nonlinear equations of motion, first the Galerkin method is used to convert the set of nonlinear partial differential equations to a set of nonlinear ordinary differential equations. The following expansion form of generalized displacements is:

```
$$u = \sum_{n=1}^{\infty} \hat{u}_n(x)\hat{w}_n(t)$$
```

```
$$\phi = \sum_{n=1}^{\infty} \hat{\phi}_n(x)\hat{\phi}_n(t)$$
```

```
$$w = \sum_{n=1}^{\infty} \hat{w}_n(x)\hat{w}_n(t)$$
```

where $\hat{u}_n$, $\hat{\phi}_n$, and $\hat{w}_n$ are the eigen-functions which need to satisfy the boundary condition of the problem, which here is hinged-hinged support. Meanwhile, $\hat{u}_n$, $\hat{\phi}_n$, and $\hat{w}_n$ are the unknown generalized coordinates. Inserting $u$, $\phi$, and $w$ into the governing equations and applying the Galerkin method yields a set of nonlinear ODEs as:

```
$$(k_{1,1} + k_{1,2})\hat{u}_n + (k_{1,3} + k_{1,4})\hat{w}_n^2 = 0$$
```

$(k_{2,1} + k_{2,2} - k_{2,3})\dot{\phi}_n - (k_{2,4} + k_{2,5} + k_{2,6})\ddot{w}_n = -m_{2,1}\frac{d^2\hat{w}_n}{dt^2} \quad (6.35)$

$k_{3,1}\hat{u}_n\hat{w}_n + (k_{3,2} + k_{3,3} + k_{3,4} + k_{3,5})\dot{\phi}_n + (k_{3,7} + k_{3,8} - k_{3,9}) - k_{3,10} - k_{3,11})\hat{w}_n + k_{3,12}\frac{d^2\hat{w}_n}{dt^2} = (m_{3,1} - m_{3,2})\ddot{P}_z + \dot{P}_z\dot{w}_n \quad (6.36)$

where stiffness (k) and mass (n) coefficients are defined in the [Appendix]. For Eq. (6.34) and (6.36), $u_n$ and $\phi_n$ can be substituted into the governing equations, respectively. Subsequently, by inserting $u_n$ and $\phi_n$ into the governing equations, a reduced order ODE is obtained:

```
$$M\frac{d^2w_n}{dt^2} + (K_i + K_{it})w_n = p_z\ddot{P}_z + \dot{P}_z\dot{w}_n \quad (6.37)$$
```

where $K_i, K_{it}$ and $M$ are the linear stiffness, nonlinear stiffness, and mass of the system, respectively. For Eq. (6.37), the linear frequency can be obtained:

```
$$\omega_n = \sqrt{\frac{K_i}{M}} \quad (6.38)$$
```

## 6.4.2 Harmonic balance method

Since the external load is periodic, HBM, which is widely used for obtaining a periodic solution of nonlinear motion, can be applied as follows:

```
$$\hat{w}_n = \sum_{i=1}^{\infty} A_i\cos(i\omega t) + B_i\sin(i\omega t) \quad (6.39)$$
```

By inserting Eq. (6.39) into Eq. (6.37) and separating the harmonic components, the nonlinear natural frequency of the system can be obtained:

```
$$\Omega = \sqrt{\frac{K_i}{M} \left(1 + \frac{3K_{it}}{4(K_i - P_s)}\right)} \quad (6.40)$$
```

Improving buckling and vibration response of porous beams

```
$$DF_{xz} = D_{xx} - c_1F_{xx}FH_{xx} = F_{xx} - c_1H_{xx}$$
AD_{xz} = A_{xz} - 2c_2D_{xx} + c_2^2F_{xx}DF_{xx} = D_{xx} - 2c_1F_{xx} + c_1^2H_{xx}$$
```

## 6.5 Numerical results and discussions

First, comparative studies are presented for the cases available in literature to ensure the accuracy of the current solution methodology. Subsequently, numerical examples are presented to investigate the effect of the porosity distributions on buckling load and free and forced response of porous beams with bidirectional and unidirectional distributions. It is assumed that the porous beam is made of aluminum with $E_0=702GPa, \nu_0=0.33, \rho_0=2700kg/m3$. In addition, hindered boundary condition is considered. For the case of forced vibration, all figures are drawn for the first mode of vibration.

### 6.5.1 Comparative studies

To show the accuracy of the current approach, the fundamental frequency of porous beams with UPDs are compared with the results reported by Chen et al. [10] in Table 6.1. Furthermore, frequency response curves of beams under axial load are compared with those reported by Shojaei et al. [46] in Fig. 6.3. Material properties, dimensions of the beams, and nondirectional parameters can be found in the aforementioned references. The presented comparison studies show excellent accuracy of the current approach in obtaining linear and nonlinear natural frequencies and frequency response curves of the beams when they are under a combination of harmonic transverse load and constant axial load.

### 6.5.2 Parametric studies

Change of the natural frequency with the axial load considering different types of porosity distribution is illustrated in Fig. 6.4. Generally, increasing the

**Table 6.1** Comparing the natural frequency of functionally porous beams based on the current approach and those reported by Chen et al. [10].

| L/h | Porosity distribution 1 | Porosity distribution 2 |
|---|---|---|---|
| | Chen et al. [10] | Current approach | Chen et al. [10] | Current approach |
| 10 | 0.2798 | 0.2807 | 0.2599 | 0.2622 |
| 20 | 0.1422 | 0.1423 | 0.1318 | 0.1325 |
| 50 | 0.0571 | 0.0571 | 0.0529 | 0.0532 |
