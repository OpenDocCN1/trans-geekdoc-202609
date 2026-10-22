
The discretized version of equation (A.26) is given as follows:

$$T_{n+1,i,j,k}=T_{n,i,j,k}+\frac{D\Delta t}{\Delta x^{2}}\left[T_{n,i+1,j,k}-2T_{n,i,j,k}+T_{n,i-1,j,k}\right]$$ $$+\frac{D\Delta t}{\Delta y^{2}}\left[T_{n,i,j+1,k}-2T_{n,i,j,k}+T_{n,i,j-1,k}\right]$$ $$+\frac{D\Delta t}{\Delta z^{2}}\left[T_{n,i,j,k+1}-2T_{n,i,j,k}+T_{n,i,j,k-1}\right]+\frac{q'(i,j,k)\Delta t}{\rho c_{p}}.$$

These equations are explicit since the unknown nodal temperatures at time $n+1$ are determined by known temperatures at time $n$ in each time step. Initial conditions must be defined so that the temperature of each node is known at time $t=0$. Assuming that $\Delta x=\Delta y$, stability criterion for 2-D interior nodes is $\alpha=D\Delta t/(\Delta x)^{2}\le 1/4$.

Implicit method, obtained by evaluating all other temperatures at time $n+1$ instead of $n$. This gives a backward-difference method, which in two-dimensional form is

$$T_{n,i,j,k}=[1-4\alpha]T_{n+1,i,j,k}$$ $$-\alpha\left(T_{n+1,i+1,j,k}+T_{n+1,i-1,j,k}+T_{n+1,i,j+1,k}\right.$$ $$+T_{n+1,i,j-1,k}+T_{n+1,i,j,k+1}+T_{n+1,i,j,k-1}\right)+F(T_{n,i,j}),$$

where $F(T_{n,i,j})=q'(i,j,k)\Delta t/(\rho c_{p})$. Thus, the new temperature at node $i,j,k$ depends on the new unknown temperatures at the other adjacent nodes. Consequently, a simultaneous solution is required using Gauss-Seidel iteration or matrix inversion.

## A.3. Nonlinear Heat-Transfer Modeling

We now consider one-dimensional heat transfer in a media with temperature-dependent thermal conductivity; i.e.,

$$\rho c_{P}\left(\frac{\partial T}{\partial t}+u_{z}\frac{\partial T}{\partial z}\right)-\frac{\partial}{\partial z}\left[k(T)\frac{\partial T}{\partial z}\right]=q'(T)\qquad\text{(A.27)}$$

or

$$\rho c_{P}\left(\frac{\partial T}{\partial t}+u_{z}\frac{\partial T}{\partial z}\right)-\frac{\partial k(T)}{\partial T}\left(\frac{\partial T}{\partial z}\right)^{2}-k(T)\frac{\partial^{2}T}{dz^{2}}=q'(T).\qquad\text{(A.28)}$$

The finite-difference scheme for this equation is

$$\rho c_{P}\left[\frac{T_{n,j}-T_{n-1,j}}{\Delta t}\right]=-\rho c_{P}u_{z}\hat{T}_{n,j}+\frac{\partial k}{\partial T}(T_{n,j})\hat{T}_{n,j}^{2}+k(T_{n,j})\frac{\partial^{2}T_{n,j}}{dz^{2}}+q'(T).\qquad\text{(A.29)}$$

Solving (A.29) for the second spatial derivative of the temperature $T_{n,j}$, we get

$\frac{\partial^2 T_{n,j}}{dz^2} = \frac{T_{n,j+1} - 2T_{n,j} + T_{n,j-1}}{(\Delta z)^2} + f\left(T_{n,j}, \tilde{T}_{n,j}, T_{n-1,j}\right), \qquad (A.30)$

where

$f\left(T_{n,j}, \tilde{T}_{n,j}, T_{n-1,j}\right) = \frac{1}{k(T_{n,j})}\left\{\rho c_P \left[\frac{T_{n,j} - T_{n-1,j}}{\Delta t}\right] + \rho c_P u_z \tilde{T}_{n,j} - \frac{\partial k}{\partial T}(T_{n,j})\left(\tilde{T}_{n,j}\right)^2 - q'(T_{n,j})\right\}, \qquad (A.31)$

and

$\tilde{T}_{n,j} = \frac{T_{n,j+1} - T_{n,j-1}}{2\Delta z} = [\partial T / \partial z](n\Delta t, j\Delta z), \qquad (A.32)$

$T_{n,1} = T(t = n\Delta t, z = a) = \alpha(t = n\Delta t), \qquad (A.33)$

$T_{n,N} = T(t = n\Delta t, z = b) = \beta(t = n\Delta t), \qquad (A.34)$

where $\tilde{T}_{n,j}$ is the temperature gradient and $f$ is a nonlinear function. Starting from the initial condition $T_{0,j}$, we can solve successively (A.30) for $n = 1, 2, ..., N$ by using the Newton method. Our implementation of the Newton method requires the partial derivatives of $f\left(T_{n,j}, \tilde{T}_{n,j}, T_{n-1,j}\right)$ with respect to $T_{n,j}$ and $\tilde{T}_{n,j}$. Introducing the notation $f_{n,j} = f\left(T_{n,j}, \tilde{T}_{n,j}, T_{n-1,j}\right)$, we get

$q_{n,j} = \frac{\partial f}{\partial T}(n\Delta t, j\Delta z) = \frac{1}{k(T_{n,j})}\left[-f_{n,j}\frac{\partial k(T_{n,j})}{\partial T} + \frac{\rho c_P}{\Delta t} - \frac{\partial^2 k(T_{n,j})}{\partial T^2}\left(\tilde{T}_{n,j}\right)^2 - \frac{\partial q'}{\partial T}(T_{n,j})\right], \qquad (A.35)$

$p_{n,j} = \frac{\partial f}{\partial \tilde{T}}(n\Delta t, j\Delta z) = \frac{1}{k(T_{n,j})}\left\{\rho c_P u_z - 2\frac{\partial k(T)}{\partial T}\tilde{T}_{n,j}\right\}. \qquad (A.36)$

Introducing the column-vector $\boldsymbol{G}_n = [G_{n,1}, G_{n,2}, ..., G_{n,N}]^T$ with components

$G_{n,1} = T_{n,1} - T_a(t_n), \quad G_{n,N} = T_{n,N} - T_b(t_n), \qquad (A.37)$

and

$G_{n,j} = T_{n,j+1} - 2T_{n,j} + T_{n,j-1} - \Delta z^2 f_{n,j}, \qquad (A.38)$

the system of nonlinear equations (A.30) and the boundary conditions (A.33) and (A.34) can be written as one equation:

$\boldsymbol{G}_n(\boldsymbol{u}_n) = 0, \qquad (A.39)$

where

\boldsymbol{u}_n = [T_{n,1}, T_{n,2}, ..., T_{n,N}]^T . \quad (A.40)

Starting with some initial guess \boldsymbol{u}^{(0)}, the nonlinear system (A.39) can be solved by the Newton iterative method:

\boldsymbol{u}_n^{(k+1)} = \boldsymbol{u}_n^{(k)} - \left[\boldsymbol{L}^{(k)}\right]^{-1} \boldsymbol{G}\left(\boldsymbol{u}_n^{(k)}\right) , \quad (A.41)

where

\boldsymbol{L}^{(k)} = \frac{\partial \boldsymbol{G}_n}{\partial \boldsymbol{u}_n}\left(\boldsymbol{u}_n^{(k)}\right) . \quad (A.42)

Calculating the elements of the Jacobian, we get

L_n^{(k)}(1,1)=1 ; \quad L_n^{(k)}(N,N)=1 ; \quad L_n^{(k)}(i,i)= -2 - \Delta z^2 q_{n,i}^{(k)} ;

L_n^{(k)}(i,i-1)=1 + \frac{1}{2}\Delta z p_{n,i}^{(k)} ; \quad and \quad L_n^{(k)}(i,i+1)=1 - \frac{1}{2}\Delta z p_{n,i}^{(k)} .

In practice, the iteration process is usually ended when the difference between the solutions of two successive iterations is smaller than a predefined threshold.

## A.4. Madariaga-Virieux Staggered-grid Scheme

The fields involved in elastic wave equations are as follows: \boldsymbol{\tau}, stress tensor in Pa (Pascal = newton/meter²); \boldsymbol{v}, particle-velocity vector in m/s (meter/second); \boldsymbol{F}, volume-source density of external forces in N/m³ (newton/meter³); \boldsymbol{I}, volume-source density of the external stress-source rate in Pa/s. Using these quantities, the equations of the linear elastic wave propagation can be written as

\frac{\partial v_i(\boldsymbol{x},t)}{\partial t} - \sigma(\boldsymbol{x})\frac{\partial \tau_{ij}(\boldsymbol{x},t)}{\partial x_j} = F_i(\boldsymbol{x},t) \quad (momentum conservation) , \quad (A.43)

\frac{\partial \tau_{ij}(\boldsymbol{x},t)}{\partial t} - c_{ijpq}(\boldsymbol{x})\frac{\partial v_q(\boldsymbol{x},t)}{\partial x_p} = I_{ij}(\boldsymbol{x},t) \quad (stress - strain relations) , \quad (A.44)

To solve these equations, we need to specify the appropriate boundary and initial conditions. The initial conditions are that the stress and particle-velocity fields and their time derivatives are zero before the seismic source is fired; i.e.,

```
v = ∂ₜv = 0 ,  t ≤ 0 .  (A.45)
```

```
τ = ∂ₜτ = 0 ,  t ≤ 0 .  (A.46)
```

The boundary conditions for modeling seismic-wave propagation are essentially determined by the free-surface boundary: the air-solid interface in land seismics and the air-water interface in marine seismics. Throughout this section, we will assume a planar free-surface boundary. Let the free surface be at a depth of z = 0. Then the boundary conditions are

```
τₓz(x, y, z = 0, t) = τᵧz(x, y, z = 0, t) = τzz(x, y, z = 0, t) = 0 .  (A.47)
```

We consider that the rest of the medium is unbounded.

Our goal in this subsection is to numerically solve equations (A.43)-(A.44) under the boundary and initial conditions in (A.45)-(A.47) by using the Madariaga-Virieux staggered-grid finite-difference techniques that we will describe below. As in most finite-difference modeling, the first step in staggered-grid finite-difference modeling is to discretize the geological model and the quantities that characterize the wavefield—i.e., the particle velocity and stresses in this case. So we discretize both the time and space domains as follows:

```
t = nΔt ,  n = 0,1,2,...,N
x = iΔx ,  i = 0,1,2,...,I
 y = jΔy ,  j = 0,1,2,...,J
z = kΔz ,  k = 0,1,2,...,K  .  (A.48)
```

where Δt is the time interval (timestep), Δx is the spacing interval (grid size) in the x-direction, Δy is the spacing interval (grid size) in the y-direction, and Δz is the spacing interval (grid size) in the z-direction. The total time for the data length is NΔt. The size of the subsurface model is IΔx × JΔy × KΔz. We will call this discretization the reference grid (also as the unstagged grid or natural grid). This terminology will allow us to distinguish the discretization in (A.48) and other discretization associated with the staggered-grid techniques, which we will discuss later.

The standard finite-difference calculations are carried out on natural grid cells (Figure A.1). In these calculations, each quantity in the differential equations (A.43)-(A.44) is defined as a function of the indices n, i, j, and k, in accordance with the following two examples:

```
σ(x, y, z) = σ[iΔx, jΔy, kΔz] = σ_{i,j,k}
τₓz(x, y, z, t) = τₓz(iΔx, jΔy, kΔz, nΔt) = [τₓz]_{i,j,k}^n  .  (A.49)
```

Basically, all quantities in equations (A.43)-(A.44) share the same gridpoints, which are the cell vertices.
