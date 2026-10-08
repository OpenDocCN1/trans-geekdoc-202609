# Advanced Deep Learning Techniques in Computational Physics

# TABLE 5.1
Matrix representation of difference operators.

| | $
abla$ | | $
abla^2$ |
|---|---|---|---|---|---|---||
| First order | 0 | 1 | 0 | 0 | -1 | 0 |
| $rac{1}{2}$ | -1 | 0 | 0 | 1 | -4 | 1 |
| | | 0 | -1 | 0 | 0 | 1 | 0 |
| Second order | 0 | -1 | 0 | 0 | 0 | 0 |
| $rac{1}{12}$ | 0 | 8 | 0 | 0 | 16 | 0 |
| | | 0 | -8 | -1 | -16 | -60 | -1 |
| | | 0 | -8 | 0 | 0 | 16 | 0 |
| | | 0 | 0 | 0 | 0 | -1 | 0 |

Similar to the network FCNN, the convolution-based loss function can also include two parts, supervision loss and the PDE loss. The supervision loss is the MSE error between the field value of the known space point and the output of the network, while the equation loss is defined as the 2-norm of the convolution of the output physical field and the fixed operator. The total training loss can be defined as the weighted sum of the two:

```
$$\mathcal{L} = \lambda_1\mathcal{L}_{pde} + \lambda_2\mathcal{L}_{data} \quad (5.20)$
$\mathcal{L}_{pde} = ||\mathbf{u} \otimes \mathbf{K}||^2 \quad (5.21)$
$\mathcal{L}_{data} = \sum_{i,j}^{N_s, N_t} |u(i,j) - u_0(i,j)||^2 \quad (5.22)$
```

where $N_s$ and $N_t$ is the number of the known points in space and time, respectively. The research of using convolution based PINN to solve physical problems is also fairly extensive, for Chen et al. [26] presents a converged data-driven Wave-Net, which is able to predict electromagnetic fields with remarkably results and high precision for various dielectric photonic structures. The framework not only serves as physical constraints in the PINN, but also as an approach to compute electric fields from magnetic fields. Raise [27] developed the DiscretizationNet implementing the CNN to solve the 3D unsteady immersed NS equation. The proposed method is demonstrated to obtain accurate, stable solutions with fast convergence. GeoNet, capable of solving parameterized steady-state PIN on irregular domain. It is noted that the presented architecture offers higher efficiency and accuracy over traditional fully connected PINN.

In this chapter, a Helmholtz equation solver is constructed using the convolution based PINN, which can reconstruct the electric field of the whole region using the boundary electric field value and the input dielectric constant information. The network structure is an efficientnet (based convolution).