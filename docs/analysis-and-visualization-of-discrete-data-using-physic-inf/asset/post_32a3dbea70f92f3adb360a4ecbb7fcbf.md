
foundation of modern physics and engineering. In one-dimensional prob-lems, the wave equation can also be understood as an oscillation. When the definition domain and boundary conditions are set as follows,

$$(x, t) \in [0, 1] \times [0, 1]$$
$$u|_{t=0} = \sin(3\pi x); u|_{x=0} = 0$$

the exact solution is obtained as follows:

$$u = \cos(3\pi ct)\sin(3\pi x)$$

In the exact solution of the heat wave equation, the domain of definition of $x \in [0, 1]$ and $t \in [0, 1]$ is sampled, and $u(x, t)$ is computed based on their coordinates, which are considered pseudo-measurement data. The partial differential term candidate library is constructed as follows:

$$\Phi = [u_x, \boldsymbol{u}_{xx}; u_{xxx}]$$

The results are shown in the top color map diagram in Figure 4.23. First, derivation of the heat conduction equation is performed in N10. Results in which the NN has the minimum error are shown in the mid-dle color map diagram in Figure 4.23. The lower color map diagram in

![](img/fa57e7010b16a211d5cf69ebb17e416e_166_0.png)

Figure 4.23. Results of one-dimensional wave equation derivation with extended library.

![](img/fa57e7010b16a211d5cf69ebb17e416e_167_0.png)

| Correct PDE | $u_{t} = 0.25 u_{xx} = 0$ |
|-------------|---------------------------|
| Identified PDE (clean data) | $u_{t} - 0.001593 u_{xx} = 0$ |

Figure 4.24. Results of one-dimensional wave equation derivation with minimum library.

Figure 4.23 shows the error distribution $(\hat{u} - u)$ between the NN model and the exact solution. The data distribution $\{u(x, t)|t = 0.25, 0.5, 0.75\}$ at fixed time is also shown below the error distribution. In addition, the bottom row of Figure 4.23 shows the derived PDE, but the derivation error is not sufficient because of the large number of candidate partial derivative terms in the library.

The derivation error improves when the candidate partial differential terms in the library are minimized to only the exact ones. That is, if the partial differential term candidate library is configured as shown in $\Phi = [u_{xx}]$, Figure 4.24 shows the exact solution, NN model, error distribution, data distribution at fixed time, and derived PDE.

Figures 4.25 and 4.26 show the parallel coordinates of $E_{\mathrm{int}}$ when the approximate solution of the wave equation is computed in N10.

## 4.1.4.7. Two-dimensional linear stress analysis

In the PDEs discussed so far, the target physical phenomena were limited to those related to fluids. So, this section will cover the discussion of stress analysis in solids. Unlike fluid analysis, stress analysis often uses the

![](img/fa57e7010b16a211d5cf69ebb17e416e_168_0.png)

Figure 4.25. NN structure and $E_{int}$ using extended library.

![](img/fa57e7010b16a211d5cf69ebb17e416e_168_1.png)

Figure 4.26. NN structure and $E_{int}$ using minimum library.

displacement method and seems less likely to explicitly face PDEs. This section describes PDEs on stress analysis assuming a plane stress state.

Stress analysis is used to understand the elastic response of structures. Elasticity refers to the ability of a structure to return to its original state after being subjected to load or deformation. The linear stress analysis problem described here applies to cases where loads or strains applied to a structure increase gradually. It also assumes that the stresses and strains applied to the structure increase linearly. In contrast, it can be shown that as the stress and strain applied to a structure increase, the response also increases. The linear stress analysis problem can be used to determine the stress concentration in a structure which corresponds the loads applied to the structure. This allows analyses of structural vibration and fracture.

When solving linear stress analysis problems, the virtual work principle is often used in FEM [41]. FEM is a method for numerically analyzing physical systems on a computer. The physical system to be analyzed is divided into a finite number of elements, and the equilibrium state of the entire system is obtained by solving the local equilibrium equations for each element. In FEM, the virtual work method is used to find the equilibrium equations for each element. The equilibrium equation describes the equilibrium between the resultant and reaction forces in an element. The virtual work method is to find the forces applied to the element, compute the effect of those forces on the element, and check to see if the results of those computations are zero.

In FEM, the virtual work method is used to solve local equilibrium equations. By combining those local equilibrium equations, the equilibrium state of an entire system can be obtained. For this reason, the linear stress analysis problems have not addressed PDEs.

A linear stress analysis problem can be expressed as a PDE considering that it is described by three equations as follows:

Equilibrium equation:

$$ \begin{bmatrix} \frac{\partial}{\partial x} & 0 & \frac{\partial}{\partial y} \\ 0 & \frac{\partial}{\partial y} & \frac{\partial}{\partial x} \end{bmatrix} \begin{bmatrix} \sigma_x \\ \sigma_y \\ \sigma_{xy} \end{bmatrix} + \begin{bmatrix} f_x \\ f_y \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \end{bmatrix} $$

Relationship between strain and displacement:

$$\left\{\begin{array}{c} {\varepsilon_{x}} \\ {\varepsilon_{y}} \\ {\varepsilon_{xy}} \end{array}\right\}_{\vec{\varepsilon}} = \left\{\begin{array}{c} {\frac{\partial u}{\partial x}} \\ {\frac{\partial v}{\partial y}} \\ {\frac{\partial u}{\partial y} + \frac{\partial v}{\partial x}} \end{array}\right\} = \left\{\begin{array}{cc} {\frac{\partial}{\partial x}} & 0 \\ 0 & {\frac{\partial}{\partial y}} \\ {\frac{\partial}{\partial y}} & {\frac{\partial}{\partial x}} \end{array}\right\}_{\nabla^{*}}\left\{\begin{array}{c} {u} \\ {v} \end{array}\right\}_{\vec{u}}$$

Constitutive equation:

$$\left\{\begin{array}{c} {\sigma_{x}} \\ {\sigma_{y}} \\ {\sigma_{xy}} \end{array}\right\}_{\vec{\sigma}} = \frac{E}{1-\nu^2}\left\{\begin{array}{ccc} {1} & {\nu} & 0 \\ {\nu} & 1 & 0 \\ 0 & 0 & {\frac{1-\nu}{2}} \end{array}\right\}_{D}\left\{\begin{array}{c} {\varepsilon_{x}} \\ {\varepsilon_{y}} \\ {\varepsilon_{xy}} \end{array}\right\}_{\vec{\varepsilon}}$$

The equation of balance represents the PDE for the Cauchy stress tensor $\sigma_{ij}$. The Cauchy stress tensor is a tensor consisting of nine components, where the origin is a certain point O and a micro rectangle made of three coordinate planes and three parallel planes around it, and the surface force $(T_x, T_y, T_z)$ coordinate component acting on each plane perpendicular to the $x$, $y$, $z$ axis is written as $\{ (\sigma_x,\sigma_{xz},\sigma_{xz}), (\sigma_y,\sigma_y,\sigma_{yz}), (\sigma_{zy},\sigma_{zy},\sigma_z) \}$. This set of nine stress components is called the point stress or the Cauchy stress tensor. Here, $\sigma_{ii}$ is the vertical stress and $\sigma_{ij(i \neq j)}$ is the shear stress, the index in $\sigma_{ii}$ indicates the direction of action of the component (the same as the normal direction of the plane), the first index in $\sigma_{ij(i \neq j)}$ indicates the direction normal to the plane, and the second index the direction of action of the component. Also, $f_i$ here represents the volumetric force. The volumetric force is an important element in the equation for the forces to which a structure is subjected. The volumetric force represents the force created by the load applied to a structure. Loads applied to a structure include gravity, wind pressure, and earthquakes. These loads are called volumetric forces because they act equally on the entire volume of the structure.

In the relationship between strain and displacement, $\vec{u}$ represents the displacement vector. $\frac{\partial u}{\partial x}$ and others represent their partial derivatives. $\vec{\varepsilon}$ is the strain vector.

In the constitutive equations, *E* and $\nu$ denote Young’s modulus and Poisson’s ratio. Using the equations of balance, the relationship between strain and displacement, and the constitutive equation, a second-order PDE for the displacement $\vec{u}$ can be obtained.

$$\begin{aligned} & \nabla^{*T}(D \nabla^{*} \vec{u}) + \vec{f} = 0 \\ & \vec{u} = \bar{u} \text{ on } \Gamma_u \\ & N_x D \nabla^{*} \vec{u} = \bar{t} \text{ on } \Gamma_t \end{aligned} \tag{4.26}$$

By writing this equation in matrix form and transforming it, we can obtain two partial differential equations regarding the displacement vector component $\begin{bmatrix}u\\v\end{bmatrix}$.

$$\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial}{\partial x} & 0 & \frac{\partial}{\partial y} \\ 0 & \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}1 & \nu & 0 \\ \nu & 1 & 0 \\ 0 & 0 & \frac{1 - \nu}{2}\end{bmatrix} \begin{bmatrix}\frac{\partial}{\partial x} & 0 \\ 0 & \frac{\partial}{\partial y} \\ \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\vec{u}\\\vec{f}\end{bmatrix} = 0$$

$$\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial}{\partial x} & 0 & \frac{\partial}{\partial y} \\ 0 & \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\frac{\partial}{\partial x} & \nu\frac{\partial}{\partial y} \\ \nu\frac{\partial}{\partial x} & \frac{\partial}{\partial y} \\ \frac{1 - \nu}{2}\frac{\partial}{\partial y} & \frac{1 - \nu}{2}\frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\vec{u}\\\vec{f}\end{bmatrix} = 0$$

$$\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial^{2}}{\partial x^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2}}{\partial y^{2}} & \frac{1 + \nu}{2}\frac{\partial^{2}}{\partial y \partial x} \\ \frac{1 + \nu}{2}\frac{\partial^{2}}{\partial y \partial x} & \frac{\partial^{2}}{\partial y^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2}}{\partial x^{2}}\end{bmatrix} \begin{bmatrix}u\\v\end{bmatrix} + \begin{bmatrix}f_x\\f_y\end{bmatrix} = 0$$

$$\frac{E}{1 - \nu^{2}} \left(\frac{\partial^{2} u}{\partial x^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2} u}{\partial y^{2}} + \frac{1 + \nu}{2}\frac{\partial^{2} u}{\partial y \partial x}\right) + f_x = 0$$
$$\frac{E}{1 - \nu^{2}} \left(\frac{\partial^{2} v}{\partial y^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2} v}{\partial x^{2}} + \frac{1 + \nu}{2}\frac{\partial^{2} v}{\partial y \partial x}\right) + f_y = 0$$
