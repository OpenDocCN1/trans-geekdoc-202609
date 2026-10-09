```
$$ A(i, j, k; i, j, k+1) = \frac{2k_{i, j, k+1}}{\Delta w_k (\Delta w_{k-1} + \Delta w_k)}; A(i, j, k; i, j, k-1) $$
$$ = \frac{2k_{i, j, k-1}}{\Delta w_{k-1}(\Delta w_{k-1} + \Delta w_k)} \quad\quad (4.20) $$
```

# 4.3.3.2 2D Irregular Grids

On 3D irregular grids, the CNN formulation of bio-heat transfer is achieved with an extension of the control areas in 2D to control volumes in 3-D [56]. In analogy to a control area in 2D triangular grids, a control volume in 3D tetrahedral grids is established by a dual mesh joining at the edge-midpoints, face-centroids and centroids of tetrahedrons adjacent to a computation point. Similar to the 2D irregular case, for the point $i$ enclosed by the control volume $\Omega_i$, the discrete form of the Pennes bio-heat transfer equation can be expressed as

```
$$ \rho_iC_i\frac{\partial T_i(t)}{\partial t} = -\left(\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_i\sum^n S_{j,n}}{l_{ij}} + w_{b,i}C_{b,i}\right)T_i(t) $$
$$ +\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_j\sum^n S_{j,n}}{l_{ij}}T_j(t) + w_{b,i}C_{b,i}T_{a,i} + Q_i + H_i \quad\quad (4.21) $$
```

where $\sum^n S_{j,n}$ denotes the sum of boundary surfaces [57] that are attached to the edge connecting $\mathbf{p}_i$ and $\mathbf{p}_j$.

The parameters of the autonomous CNN are associated with the parameters of the discrete Pennes bio-heat transfer equation, resulting in:

```
$$ C_x = \rho_iC_i; \nu_{xi} = T_i(t); \nu_{yj}(t) = T_j(t); I_i = w_{b,i}C_{b,i}T_{a,i} + Q_i + H_i $$
$$ A(i;i) = -\left(\frac{1}{\Omega_i}\sum_{j \in N_i(i)}\frac{k_i\sum^n S_{j,n}}{l_{ij}} + w_{b,i}C_{b,i}\right) + \frac{1}{R_x} $$
$$ A(i;j) = \frac{1}{\Omega_i}\frac{k_j\sum^n S_{j,n}}{l_{ij}} \quad\quad (4.22) $$
```