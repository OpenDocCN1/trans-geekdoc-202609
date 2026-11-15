In this mode when the input vector is presented to the network, one weight vector or a combination of many weight vectors based on the number of winning nodes build the output. In the interpolation mode, more than one Kohonen unit has a non-zero activation with

![](bbox=[0.44, 0.17, 0.56, 0.22])

The activation of the output units is then given by

![](bbox=[0.41, 0.28, 0.59, 0.32])

In operation, for each Kohonen cluster unit, \(D_i\) value (\(i = 1, \dots, p\)) based on the Euclidean distance is computed, a set of \(N\) units (\(N = 1, \dots, N_{win}\)) with minimum \(D\), are selected. The winner nodes are ordered from minimum to maximum based on their \(D_N\) values. The unit with the smallest \(D_N\) which is closer to the input vector must have more share in the interpolation mode. To accomplish this, the following relation is suggested:

![](bbox=[0.39, 0.46, 0.61, 0.51])

Here \(z_j\) is the share of each winner unit which is used in Eq. (7.6). For the closer Kohonen units to the input vector, \(D_j\) has the smallest value which will result in a larger \(z_j\) in Eq. (7.7). \(D_j\) has been introduced in the denominator to amplify this effect.

# 7.3 Gradient Computations

The optimal design of structures requires the computation of the stress and displacement constraints. The gradient of constraints usually requires the intermediate calculation of the gradient of the displacement with respect to design variables, since most common constraints (i.e., stress limits) are directly related to the displacements [10]. Using the displacement method of analysis, the finite element technique requires the solution of the matrix equation

![](bbox=[0.45, 0.79, 0.55, 0.81])

where the global stiffness matrix K is the sum of the element stiffness matrices \(k_i\)