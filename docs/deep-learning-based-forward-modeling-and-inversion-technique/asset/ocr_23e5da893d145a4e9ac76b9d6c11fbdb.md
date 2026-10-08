# Deep Learning-Based Forward Modeling and Inversion Techniques

![](bbox=[0.193, 0.085, 0.803, 0.255])

FIGURE 3.6
The changing curve in the experimental temperature range of a typical model.

# 3.3.2 3D Transient Forward Solver Based on Joint Simulation

The inversion algorithm in this chapter is data driven, it is necessary to generate a large number of forward data. The joint simulation solver based on COMSOL and MATLAB is used to obtain sufficient heat flow temperature data combination. COMSOL is an efficient commercial software based on the finite element method [22]. Its rich add-modules provide professional analysis tools in the field of electromagnetism, structure, acoustics, fluid flow, heat transfer and chemical engineering. In addition, it provides convenient tools for interaction with CAD and other third-party software. This chapter mainly uses the finite element solver of this software to obtain the time domain temperature field. The basic steps are as follows:

First, the whole space is discretized into multiple elements, each element contains p nodes. In each element, the temperature can be approximately represented by the interpolation of node temperature:

```
T = \sum_{i=1} N_i(x,y,z)T_i^{(e)} = [N]\{T\}^{(e)}  (3.20)
```

where Ni represents the weight of each node. In each cell, the submatrix

```
K_{1ij}^{(e)} = \int_{V^{(e)}} (k_x \frac{\partial N_i}{\partial x}\frac{\partial N_j}{\partial x} + k_y \frac{\partial N_i}{\partial y}\frac{\partial N_j}{\partial y} + k_z \frac{\partial N_i}{\partial z}\frac{\partial N_j}{\partial z})dV  (3.21)
```

```
K_{2ij}^{(e)} = \int_{S_3^{(e)}} h N_i N_j dS_3  (3.22)
```

```
K_{3ij}^{(e)} = \int_{V^{(e)}} \rho c_p N_i N_j dV  (3.23)
```

```
Q_{ij}^{(e)} = \int_{V^{(e)}} \hat{q} N_i dV + \int_{S_2^{(e)}} q_N N_i dS_2 + \int_{S_3^{(e)}} h T_f N_i dS_3  (3.24)
```