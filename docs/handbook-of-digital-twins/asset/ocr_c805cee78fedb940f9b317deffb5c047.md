the SGBEM-FEM method has been systematically verified in our two-part paper in 2013 [17,18], where there are many examples of 2D through-thickness cracks and 3D embedded/surface cracks.

# 43.2.4 Nodal Spacing Equalization

In the parametric crack-surface modeling process, the generated number of nodes at the crack front may be different for various cracks, and the nodal spacing may also be non-uniform. Therefore, to establish the relation between nodal coordinates and the SIFs at crack fronts for different cracks, a nodal spacing equalization procedure in Ref. [5] is used here to set the same number of equidistant nodes along the crack front for a consistently parameterized representation of the crack fronts between different cracks.

The node spacing equalization aims to set the same number of equidistant nodes on the front curve to generate a consistently parameterized representation of the crack fronts between different cracks. In this paper, the method in Ref. [5] is used, but corresponding improvements are made for specific problems.

For a crack-front curve with non-equispaced nodes, we can represent the nodes with coordinates:

\(\mathbf{X} = \{\mathbf{X}_1, \mathbf{X}_2, \dots, \mathbf{X}_m\}\) (43.1)

where _m_ is the number of the nodes and \(\mathbf{X}_i\) is the location vector for the _i_ th node.

A cubic spline interpolation is used to generate a spline representation \(f_l(\xi)\) of the crack front, where \(\xi \in [0,1]\) is the spline’s natural parameter. Assuming that _p_ + 1 equispaced nodes along the crack front are to be generated, the spline parameter for these nodes are:

\(\mathbf{s} = \{0, \frac{1}{p}, \frac{2}{p}, \dots, \frac{p-1}{p}, 1\}\) (43.2)

and the location vector of the generated equispaced nodes along the crack-front can be calculated by \(\mathbf{x} = f_l(\xi)\):

\(\mathbf{x} = \{\mathbf{x}_0, \mathbf{x}_2, \dots, \mathbf{x}_p\}\) (43.3)

For each node \(\mathbf{x}_i\), we can have two representations: Cartesian coordinate and corresponding spline parameter.

Meanwhile, the spline parameter values corresponding to the original non-equispaced nodes \(\mathbf{X}_i\) can be obtained by \(\xi = f_l^{-1}(\mathbf{X})\), which can be expressed as:

\(\mathbf{S} = \{0, \xi_1, \xi_2, \dots, \xi_{m-1}, 1\}\) (43.4)