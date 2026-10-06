# # Chain rule with tensors

For weight matrices: $\frac{\partial W\mathbf{x}+b}{\partial \mathbf{W}} = \mathcal{T}_{ijd} \text{ with } \mathcal{T}_{[\cdot,\.]d} = \frac{\partial z_d}{\partial \mathbf{W}} = egin{bmatrix} 0^T \ \vdots \ \mathbf{x}^T \ \vdots \ 0^T \end{bmatrix}$ Matrix with zeros, d-th row contains x^T

Tensor vector product: $\mathcal{T}_{ijd}\mathbf{u} = \sum_d \mathcal{T}_{[\cdot,\.]d}u_d = \sum_d \mathbf{X}_d u_d = egin{bmatrix} x_1u_1 & x_2u_1 & \dots & x_nu_1 \ \vdots & \vdots & & \vdots \ x_1u_d & x_2u_d & \dots & x_nu_d \end{bmatrix} = \mathbf{u}\mathbf{x}^T$

+   - Which is the outer product!

Hence: $
abla_{\mathbf{W}}f = \frac{\partial f(z)}{\partial \mathbf{W}}(\mathbf{W}x+b)\frac{\partial f(z)}{\partial \mathbf{z}} = \frac{\partial f(z)}{\partial \mathbf{z}}\mathbf{x}$