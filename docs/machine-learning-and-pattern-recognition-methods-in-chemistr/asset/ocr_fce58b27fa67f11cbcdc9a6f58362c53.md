components. For calculating the requested plane, the loading vectors of M' have to be calculated by performing SVD:

```
$$\mathbf{M}'_{i j} = \mathbf{U}'_{i \times 2} \mathbf{S}'_{2 \times 2} \mathbf{V}'_{2 \times j} \quad (7.18)$
```

where $i$ is the number elution times of the green (gray in the printed version) and red (dark gray in the printed version) components (excluding the blue (light gray in the printed version) one) one and:

```
$$\mathbf{P}_{2 \times 3} = \mathbf{V}'_{2 \times j}^T \mathbf{V}_{j \times 3} \quad (7.19)$
```

The null space of matrix P is a vector, $n_v$, which will yield the coefficients of the demanded hyperplane:

```
$n_1 z_{v1} + n_2 z_{v2} + n_3 z_{v3} = 0 \quad (7.20)$
```

where $z_v$ is a general variable vector, which represents the coordinates of an arbitrary point in V-space.

Based on Eq. (7.20), the spectral subspace of the green (gray in the printed version) and red (dark gray in the printed version) components is fixed in V-space (shown with cyan (gray in the printed version) color in Fig. 7.8B and the data points associated with these components lie on it). These points are shown with blue (light gray in the printed version) stars in the score plot of the data. coefficients of the calculated plane correspond to a point in U-space. In fact, this point defines the coordinates related to the concentration profile of the blue (light gray in the printed version) component.

Since the elements of vector $n_v$ are the coefficients of the plane equation, $n_v$ can be transformed to the concentration profile of the blue (light gray in the printed version) component. Note that before transforming the coefficients of the plane, they have to be weighted by the corresponding singular values, i.e., the diagonal elements of the singular matrix of data.

```
$$\mathbf{n}_{w(1 \times 3)} = \mathbf{n}_{v(1 \times 3)} \mathbf{S}_{(3 \times 3)} \quad (7.21)$
```

```
$$\mathbf{c}_{(blue)(1 \times 3)} = \mathbf{U}_{(1 \times 3)} \mathbf{n}_{v(3 \times 1)}^T \quad (7.22)$
```

The geometric visualization presented here would help understand how the definition of the subspace related to the interfering compounds leads to the unique concentration profile of the analyte. The correct detection of the subspace (with the described features), which can specify the spectral subspace of the interferents (green (gray in the printed version) and red (dark gray in the printed version)), leads to the unique analyte