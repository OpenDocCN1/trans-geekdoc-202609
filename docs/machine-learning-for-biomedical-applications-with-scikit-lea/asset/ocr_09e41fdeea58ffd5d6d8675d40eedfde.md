![](bbox=[0.252, 0.095, 0.794, 0.235])

**Figure 5.2** Left: a 4D movie of a chest CT is collected as a series of 2D+ time slices through the volume. The original reconstruction is corrupted by motion. Middle: The image can be sharply reconstructed by identifying which neighboring slices were acquired during the same state of motion. Right: the correct slices can be found through nonlinear (manifold) embedding of the points using manifold learning [8].

scans of the chest (heart and lungs) where manifold learning (described in Sect. 5.6) can similarly be used to reconstruct high-resolution 4D volumes (3 space + 1 time dimension) from dynamically acquired 2D slices (Fig. 5.2).

# ## 5.3. Linear transforms

Before we consider nonlinear manifolds, let us start by considering linear embeddings constructed from linear transforms. Mathematically, a linear transform is a function that satisfies the properties of additivity and scalar multiplication, while preserving the origin

+   additivity: $T(\mathbf{x}_1 + \mathbf{x}_2) = T(\mathbf{x}_1) + T(\mathbf{x}_2)$ (5.1)
scalar multiplicity: $T(\alpha\mathbf{x}) = \alpha T(\mathbf{x})$ (5.2)

In simple terms, this means that linear transforms preserve the linear properties of the vector space. In other words, they map data points from one Euclidean domain to Euclidean subspace. Practically, the action of any matrix on a vector is a linear transform. For example, the action of $\mathbf{A} = \begin{pmatrix} 3 & 0 \ 0 & 1 \end{pmatrix}$ represents a scale along the x-axis by a factor of 3 (see Fig. 5.3), as follows:

```
$$\begin{pmatrix} x' \ y' \end{pmatrix} = \begin{pmatrix} 3 & 0 \ 0 & 1 \end{pmatrix} \begin{pmatrix} x \ y \end{pmatrix}$ (5.3)$
```

```
$= \begin{pmatrix} 3x + 0y \ 0x + 1y \end{pmatrix}$ (5.4)$
```

```
$= \begin{pmatrix} 3x \ 1y \end{pmatrix}$ (5.5)$
```