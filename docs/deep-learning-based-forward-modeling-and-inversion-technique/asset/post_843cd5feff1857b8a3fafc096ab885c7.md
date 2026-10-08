
# Deep Learning-Based Forward Modeling and Inversion Techniques

and the corresponding FEM algorithm introduces, followed by the detailed architecture of the related Fourier network. Next, multiphysics process in three different scenarios are discussed. A series of the testing examples are utilized to demonstrate the performance of the DL framework.

## 5.3.1 Methods

In this part, the cascaded Fourier network and each module are introduced in detail. Beside, the physical models as well as the corresponding PDEs are mentioned. In addition, the data generation procedure along with the FEM algorithm are displayed. At last, the training process is discussed in the end.

### 5.3.1.1 Framework Architecture

Here, the architecture of the proposed DL framework is shown in Figure 5.10 (a), which consists of two parts, the input module and the Fourier modules. Here, the input module extracts valuable characteristics from the boundaries to obtain the immediately dependent fields. The main structure of the input framework is based on the onetnet, which is made up of several of fully connection layers, transpose convolutional layers and a convolution layer. In order to normalize the output and add nonlinearity of each layer, batch norm layers and activation function are attached. The Fourier module is the core of the network, performing the operator learning from one physics field to another.

This architecture is formulated by Liu et al., which parameterizes the integral kernel deeply in Fourier space. Unlike traditional DL frameworks or PINNs [12] which merely learns how to solve the equation, the Fourier network learns the operator itself, demonstrates high generalization capability. As displayed in Figure 5.10 (b), the Fourier architecture can be further divided into two parts. One contains a Fourier transform; a Hadamard matrix product layer followed by an inverse Fourier transform layer. The other is a Hadamard matrix product layer. The input is split into the upper and lower part and the output of the two parts are added first and then activated by a nonlinear function.

It can be verified that the input and output of each Fourier module completes with:

```
$u_o(x) = \sigma\left(Bu_u(x) + \mathcal{F}^{-1}\{AF[u_u(x)]}\right)\quad(5.27)$
```

where $\mathcal{F}$ and $\mathcal{F}^{-1}$ indicate the forward and inverse Fourier transform operator,

```
$$\mathbf{X}(u,v) = \sum_{m=0}^{M-1} \sum_{n=0}^{N-1} \chi(m,n) e^{-2\pi i(\frac{mu}{M} + \frac{nv}{N})}\quad(5.28)$$
```

```
$$\chi(m,n) = \frac{1}{MN} \sum_{u=0}^{M-1} \sum_{v=0}^{N-1} \mathbf{X}(u,v) e^{2\pi i(\frac{mu}{M} + \frac{nv}{N})}\quad(5.29)$$
```

![](img/020125e0e698f9771fbbd32f2ace1e80_177_0.png)

FIGURE 5.10

The architecture of the Fourier network: (a) The overall network composition, including the input module and Fourier modules; (b) The Fourier network, utilizing to approximate the nonlinear orders; (c) the attention mechanism in the skip connection, strengthening the data of high correlation regions.

where $M$ and $N$ are the number of rows and columns of the corresponding matrix, respectively. In fact, the Fourier transform operator turns the convolution to the product, which is able to be accelerated by FFT. These techniques diminish the calculation complexity and enable large scale computation.

In the proposed method, certain advanced techniques are employed to enhance the performance. Enlightened by the skip connection structure of the Resnet [60], [62] is contrast between the two corresponding input/output Fourier modules [60, 62]. The skip connection structure contacts the characteristics extracted by low-level modules. Nevertheless, the price for skip modules for maintaining high-resolution is that they diminish the intrinsic logic in deep networks. Actually, diverse physical fields emerge spatial relationships. Therefore, the attention mechanism is introduced in the network, which diminishes the resolution of some trifling domains while magnifying the information of highly related regions. The specific architecture of the skip connection is exhibited in Figure 5.10, which is elaborate devised as a weighted selector to accomplish attention mechanism. Here, attention module can be expressed as

```
$Attention(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V \quad (5.30)$
```

where $Q, K$, and $V$ are the query, key and value matrix, while $d_k$ is the scaling factor. In fact, the detailed procedures of the attention mechanism are as follows. At first, the query and key matrices are utilized to obtain the weight coefficient. Next, the field are added together in the light of the weight to acquire the final output. It is worth noting that this mechanism enables the network to connect on a tiny number of crucial parts with large weight, and abandon the majority of the superfluous one. In view of the confined computing resources in some extreme scenarios, the attention mechanism is able to ensure the performance of the framework.

### 5.3.1.2 Physics Model

In the first model, the temperature and electrical potential are the physical fields to be calculated. It is noticed that there is a strong coupling between the two fields for the electrical conductivity changes with temperature. Here, the current continuity equation with the heat conduction equation is employed:

```
$\nabla \cdot (-\sigma\nabla\phi) = 0$
```

```
$\rho_C \frac{\partial T}{\partial t} - \nabla \cdot (k\nabla T) = Q$
```

where $\sigma$ and $\phi$ are the electrical conductivity and electrical potential, while $\rho, C_p, k$ and $Q$ are the density, the constant pressure heat capacity, the thermal conductivity and the heat power density respectively.

In the second model, the potential and the electron concentration are the related fields while the corresponding equations are the electrical current continuity equation and the transport equation:

```
$\nabla \cdot (-\sigma\nabla\phi) = 0$
```

```
$\frac{\partial n}{\partial t} + \nabla \cdot (D\nabla n + n\nu) = 0$
```

where $n, \nu$, and $D$ are the electron concentration, drift velocity and diffusion velocity.

In the third model, the velocity field and the temperature field are analyzed, complies with the convection-conduction equation and the Navier Stokes (N-S) equation:

```
$\rho_C \mathbf{u} \cdot \nabla T - \nabla \cdot k\nabla T = 0$
```

```
$\rho \left( \frac{\partial \mathbf{u}}{\partial t} + \mathbf{u} \cdot \nabla\mathbf{u} \right) = -\nabla p + \nabla \cdot \left[ \mu\mathbf{u} + \mu(\mathbf{u})^T \right] - \frac{2}{3}\mu\nabla\mathbf{u} \cdot \mathbf{u} + \rho\mathbf{g}$
```

where $\mathbf{u}, p, \mu$, and $\mathbf{g}$ are the velocity, the intensity of pressure, the dynamic viscosity and gravity constant.

### 5.3.1.3 Data Generation

In this part, the training data is acquired by implementing MATLAB with COMSOL. This software is on the basis of the finite element method (FEM). Here, the detailed procedure of utilizing the FEM to resolve the coupled electrothermal model is presented as follows:

First of all, the solving domain is divided into $E$ cells, each of $p$ nodes. The temperature and potential of each cell can be expressed by the interpolation of the field at the nodes:

```
$T = \sum_{i=1}^{r} N_i(x, y, z) T_i^{(e)} = [N]{e)}$
```

```
$\phi = \sum_{i=1}^{r} N_i(x, y, z) \phi_i^{(e)} = [N]{\phi^{(e)}
```

The weak form of the heat conduction and electrical continuity continuity can be expressed

```
$\int_{\Omega} \rho_c \phi \frac{\partial T}{\partial t} d\Omega + \int_{\Omega} k \nabla T \cdot \nabla T d\Omega = \int_{\Omega} \omega_i |\nabla \phi|^2 d\Omega$
```

```
$\int_{\Omega} \omega_i |\nabla \phi|^2 d\Omega = 0$
```

Each of the component can be formulated as

```
$K_{Tij}^{(e)} = \int_{\Omega} (k_x \frac{\partial N_j}{\ x} \frac{\partial N_i}{\ x} + k_y \frac{\partial N_j}{\ y} \frac{\partial N_i}{\ y}) dV$
```

```
$K_{Tij}^{(e)} = \int_{\Omega} k \nabla N_j \cdot \nabla N_i dV$
```

```
$Q_i^{(e)} = \int_{\Omega} \omega_i |\nabla \phi|^2 d\Omega$
```

```
$K_{\phi ij}^{(e)} = \int_{\Omega} (\sigma_x \frac{\partial N_j}{\ x} \frac{\partial N_i}{\ x} + \sigma_y \frac{\partial N_j}{\ y} \frac{\partial N_i}{\ y}) dV$
```

Where $K_{Tij}$, $K_{\phi ij}$ are the conduction and time-varying items. The heat source is denoted as $Q$. The assembled matrix is as:

```
$[K_T]{T}=\{P\}$
```

```
$[K_{\phi}]{\phi}=\{Q\}$
```

where $T$, $\phi$ and $P$ represent the vector of the temperature, the potential and the load. By imposing the boundary condition on the PDE, the physical fields can be acquired by resolving the corresponding equation. A total number of 6000 specimens for each physics model are generated by specifying various boundary conditions. Here, 2/3 of the data sets are used for training.
