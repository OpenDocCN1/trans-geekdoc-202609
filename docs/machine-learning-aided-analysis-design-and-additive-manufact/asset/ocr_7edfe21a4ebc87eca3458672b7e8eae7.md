# 3.2.2 Constitutive relation and energy equation

On the basis of FSDT, the displacement field of any point on the FGP plate can be expressed with displacement components of relevant points on the middle plate of the established model in term of matrix:

```
$U = \begin{bmatrix} U \ V \ W \end{bmatrix} = \begin{bmatrix} 1 & 0 & 0 & z \ 0 & 1 & 0 & z \ 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} u \ w \ \phi_s \end{bmatrix} \quad (3.4)$
```

```
$u=[u, v, \phi_x, \phi_y]^T \quad (3.5)$
```

where $U, V, W$ represent the displacement components of the plate at any point in x, y, and z axes, respectively; $u, v,$ and $w$ are the displacements in the middle surface of the plate; $\phi_x$ and $\phi_y$ separately represent the transverse rotations about the x and y axes. The strain-displacement relations can be written as:

```
$\epsilon = \begin{bmatrix} \epsilon_{xx} \ \epsilon_{yy} \ \epsilon_{zz} \ \gamma_{xy} \ \gamma_{yz} \ \gamma_{zx} \end{bmatrix} = \begin{bmatrix} 0 & 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 & 0 \ 0 & 0 & 0 & 0 & 0 & 1 \ 0 & 0 & 0 & 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} u \ v \ w \ \phi_x \ \phi_y \end{bmatrix} = \mathbf{Ru} \quad (3.6)$
```

in which, symbols $\epsilon_{xx}, \epsilon_{yy}, \epsilon_{zz}, \gamma_{xy}$ and $\gamma_{yz}$ respectively indicate the normal strains and the shear strains related to the displacements $u, v, w, \phi_x$ and $\phi_y$. Then, the force and moments are represented as

```
$N = \begin{bmatrix} N_x \ N_y \ N_{xy} \ M_x \ M_y \ M_{xy} \ Q_x \ Q_y \end{bmatrix} = \begin{bmatrix} A_{11} & A_{12} & 0 & B_{11} & B_{12} & 0 & 0 & 0 \ A_{12} & A_{22} & 0 & B_{12} & B_{22} & 0 & 0 & 0 \ 0 & 0 & A_{66} & 0 & 0 & C_{66} & 0 & 0 \ B_{11} & B_{12} & 0 & D_{11} & D_{12} & 0 & 0 & 0 \ B_{12} & B_{22} & 0 & D_{12} & D_{22} & 0 & 0 & 0 \ 0 & 0 & C_{66} & 0 & 0 & D_{66} & 0 & 0 \ 0 & 0 & B_{66} & 0 & 0 & 0 & k_{A44} & 0 \ 0 & 0 & 0 & 0 & 0 & 0 & 0 & k_{A55} \end{bmatrix} \begin{bmatrix} \epsilon_x \ \epsilon_y \ \gamma_{xy} \ \theta_x \ \theta_y \ \theta_{xy} \ \gamma_{	heta x} \ \gamma_{	heta y} \end{bmatrix} \quad (3.7)$
```

where $N_x$ and $N_y$ represent the normal results; $N_{xy}$ is shear result; $M_x$ and $M_y$ denote the bending results; $M_{xy}$ indicates the twisting resultants; $Q_x$ and $Q_y$