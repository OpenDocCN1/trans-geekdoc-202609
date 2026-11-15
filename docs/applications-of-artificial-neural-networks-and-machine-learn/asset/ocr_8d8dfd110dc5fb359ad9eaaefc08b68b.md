In Eq. (14.2) each matrix A[1] has entries only in the principle submatrix corresponding to the variables in element l and represents contributions from this element. This principle submatrix is assumed to be dense. The matrix A may be non-symmetric but the form (2) implies that it has a symmetric pattern.

With reference to Eq. (14.1), column j is said to be active at stage i, if j >= i and there is a non-zero entry in column j with a row index, k, such that k <= i. Letting f_i denote the number of columns that are active at stage i, the maximum frontwidth of A is given by

F_{max} = max {f_i} 1 <= i <= n

The root-mean-squared (r.m.s.) wavefront is defined to be

F_{rms} = \left( \frac{1}{n} \sum_{i=1}^n f_i^2 \right)^{\frac{1}{2}}

Assuming that n and the average value of f_i are reasonably large, it can be shown that a complete profile or front factorization requires approximately O(n F_{rms}^2) operations.

# 14.3 Graph Model of a Finite Element Mesh

At least ten different graph models can be employed for transforming the connectivity properties of finite element meshes into those of graphs [9]. In this chapter, the element clique graph is used as defined in the following section.

# 14.3.1 Element Clique Graph

The element clique graph (ECG) of a FEM, is a graph whose nodes are the same as those of the FEM and two nodes n_i and n_j of ECG are connected with a member if n_i and n_j share an element of the FEM. A simple FEM and the corresponding ECG are shown in Fig. 14.1. This graph has the same nodes as that of the corresponding FEM and provides a direct approach for nodal ordering of the FEM. An additional advantage lies in the simplicity of constructing this graph for 2D and 3D meshes, compared to the other graph models.