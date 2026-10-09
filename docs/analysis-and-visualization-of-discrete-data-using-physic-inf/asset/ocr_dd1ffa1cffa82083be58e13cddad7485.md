In the constitutive equations, *E* and *\nu* denote Young’s modulus and Poisson’s ratio. Using the equations of balance, the relationship between strain and displacement, and the constitutive equation, a second-order PDE for the displacement *\vec{u}* can be obtained.

```
```\begin{aligned}&\nabla^{*T}(D \nabla^{*} \vec{u}) + \vec{f} = 0 \\&\vec{u} = \bar{u} \text{ on } \Gamma_u \\&N_x D \nabla^{*} \vec{u} = \bar{t} \text{ on } \Gamma_t\end{aligned} \tag{4.26}```
```

By writing this equation in matrix form and transforming it, we can obtain two partial differential equations regarding the displacement vector component \begin{bmatrix}u\\v\end{bmatrix}.

```
```\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial}{\partial x} & 0 & \frac{\partial}{\partial y} \\ 0 & \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}1 & \nu & 0 \\ \nu & 1 & 0 \\ 0 & 0 & \frac{1 - \nu}{2}\end{bmatrix} \begin{bmatrix}\frac{\partial}{\partial x} & 0 \\ 0 & \frac{\partial}{\partial y} \\ \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\vec{u}\\\vec{f}\end{bmatrix} = 0```
```

```
```\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial}{\partial x} & 0 & \frac{\partial}{\partial y} \\ 0 & \frac{\partial}{\partial y} & \frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\frac{\partial}{\partial x} & \nu\frac{\partial}{\partial y} \\ \nu\frac{\partial}{\partial x} & \frac{\partial}{\partial y} \\ \frac{1 - \nu}{2}\frac{\partial}{\partial y} & \frac{1 - \nu}{2}\frac{\partial}{\partial x}\end{bmatrix} \begin{bmatrix}\vec{u}\\\vec{f}\end{bmatrix} = 0```
```

```
```\frac{E}{1 - \nu^{2}} \begin{bmatrix}\frac{\partial^{2}}{\partial x^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2}}{\partial y^{2}} & \frac{1 + \nu}{2}\frac{\partial^{2}}{\partial y \partial x} \\ \frac{1 + \nu}{2}\frac{\partial^{2}}{\partial y \partial x} & \frac{\partial^{2}}{\partial y^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2}}{\partial x^{2}}\end{bmatrix} \begin{bmatrix}u\\v\end{bmatrix} + \begin{bmatrix}f_x\\f_y\end{bmatrix} = 0```
```

```
```\frac{E}{1 - \nu^{2}} \left(\frac{\partial^{2} u}{\partial x^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2} u}{\partial y^{2}} + \frac{1 + \nu}{2}\frac{\partial^{2} u}{\partial y \partial x}\right) + f_x = 0
\frac{E}{1 - \nu^{2}} \left(\frac{\partial^{2} v}{\partial y^{2}} + \frac{1 - \nu}{2}\frac{\partial^{2} v}{\partial x^{2}} + \frac{1 + \nu}{2}\frac{\partial^{2} v}{\partial y \partial x}\right) + f_y = 0```
```