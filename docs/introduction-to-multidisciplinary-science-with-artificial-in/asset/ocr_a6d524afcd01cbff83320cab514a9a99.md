Momentum equation : $\frac{\partial \delta \mathbf{v}}{\partial t} + \rho_0 \nabla (\delta \Psi) + \nabla \delta p + \underbrace{2\Omega \times \delta \mathbf{v}}_{\text{Coriolis}} + \underbrace{\Omega \times (\Omega \times \mathbf{x})}_{\text{centrifugal}} = 0$

Poisson’s equation : $\nabla^2 \delta \Psi = 4\pi G_0 \delta \rho$

where $\rho_0 = \text{constant}$, $\mathbf{v}_0 = 0$, and $p_0 = 0$, $\mathbf{\Omega}$ is the rotation vector. The second and third terms on the left-hand side of the latter which represent the Coriolis effect and centrifugal force, respectively, due to the rotation. $\mathbf{\Omega} = [0,\Omega_y,\Omega_z]^T$, and $\nabla \delta p = [0,0,\partial p/\partial p]^T$. By assuming that perturbations propagate only along the $z-$ axis. We then get the perturbation equations and that

$\frac{\partial \delta \rho}{\partial t} + \rho_0 \frac{\partial \delta v_z}{\partial z} = 0 \Longleftrightarrow \omega \delta \rho - \rho_0 k \delta v_z = 0$

$\frac{\partial \delta v_x}{\partial t} + 2\Omega_y v_z - 2\Omega_z v_y = 0 \Longleftrightarrow \omega v_x - 2i\Omega_z v_y + 2i\Omega_y v_z = 0$

$\frac{\partial \delta v_y}{\partial t} + 2\Omega_z v_x \Longleftrightarrow 2i\Omega_y v_x + \omega v_y$

$\frac{\partial \delta v_z}{\partial t} + \frac{1}{\rho_0} \frac{\partial \delta p}{\partial z} + \frac{\partial \delta \Psi}{\partial z} - 2\Omega_y v_x = 0 \Longleftrightarrow -2i\Omega_y v_x + \omega v_z - \frac{c^2 k}{\rho_0} v_z + k \delta \rho = 0$

$\frac{\partial^2 \delta \Psi}{\partial z^2} = 4\pi G_0 \delta \rho = 0 \Longleftrightarrow 4\pi G_0 \delta p - k^2 \delta \Psi$

or in a matrix form as

$\begin{pmatrix} \omega & -2i\Omega_z & 2i\Omega_y & 0 & 0 \\ 2i\Omega_z & \omega & 0 & 0 & 0 \\ 2i\Omega_y & 0 & \omega & -(c^2 k_z)/\rho_0 & k_z \\ 0 & 0 & -\rho_0 k_z & \omega & 0 \\ 0 & 0 & 0 & 4\pi G_0 & -k_z^2 \end{pmatrix} \begin{pmatrix} v_x \\ v_y \\ v_z \\ \delta \rho \\ \delta \Psi \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \\ 0 \\ 0 \end{pmatrix}$

Setting the determinant of the 5 x 5 coefficient matrix for the system of constants equal to zero to satisfy their nontriviality property, we obtain the secular equation We are looking for non-trivial solutions. This means that the determinant must be zero. This leads to a bi-quadratic equation in $\omega$ for the dispersion relation

$\omega^4 - (4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0) \omega^2 + 4\Omega^2 (c^2 k_z^2 - 4\pi G_0 \rho_0) \cos^2 \theta = 0 , \qquad (B.14)$

where $\theta$ is the angle between the direction of propagation of the perturbation $\mathbf{k}$ and the rotation axis $\mathbf{\Omega}$. Using Vieta’s relation, we can get the following two equations for the $\omega$ solving the equation:

$\omega_1^2 + \omega_2^2 = 4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0 \quad \text{and} \quad \omega_1^2 \omega_2^2 = 4\Omega^2 (c^2 k_z^2 - 4\pi G_0 \rho_0) \qquad (B.15)$

The second case is the important special case where $\theta = 90^\circ$, i.e. where the rotation axis and the perturbation are perpendicular to each other. The dispersion relation takes the simple form:

$\omega^2 - (4\Omega^2 + c^2 k_z^2 - 4\pi G_0 \rho_0) \omega^2 = 0 , \qquad (B.16)$