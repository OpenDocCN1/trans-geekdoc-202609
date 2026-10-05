# 320 Recursive Solutions to Large Eigenproblems

“look-ahead” algorithm is often used.184 QMR is applicable to both complex-symmetric and non-Hertitian matrices.

The GMRES and QMS methods are completely equivalent in exact arithmetic, but they have different convergence behaviors in finite-precision arithmetic. GMRES typically converges faster and more smoothly than QMR, but the latter is much more efficient computationally as it avoids storing and orthogonalizing the recurring vectors.93 Thus, QMR is often the method of choice for constructing filtered linear equations. The use of QMR to construct filtered systems was introduced by Karlsson,99 and its implementation in the framework was advanced by several authors for obtaining eigenvalues of complex-symmetric matrices.78,82,159,163 A powerful feature of these recurring solvers is the possibility to institute preconditioners, which can accelerate the convergence significantly.91-94,183

It should be pointed out that a low-storage version of the Lanczos-FD can also be formulated without explicit recourse to the filtered vectors.77,164 Such a low-storage version is preferred if only eigenvalues are needed. For example, Yu and Smith have shown that the overlap and Hamiltonian matrices in a prespecified energy range can be directly obtained as:77

```
S = Y^TY
H = Y^THY
```

where the (L×K) Y matrix contains all the expansion coefficients in Eq. [88]. As the Chebyshev-based LSFD, the error of an eigenvalue can be determined from the dispersion ||(H^2 - E^2S)||, in which the H^2 matrix can also be constructed with T. For long recursions, the large size of Y may cause problems. To avoid problems, Zhang and Smith recently proposed a new LSFD method on solving homogeneous linear equations in the Lanczos subspace.164 These authors showed that the S and H matrices can be built recursively along the Lanczos recursion, avoiding the storage of Y. Nonetheless, it is not entirely if significant numerical savings can be achieved compared with the original Lanczos algorithm.

# SYMMETRY ADAPTATION

Because many physical systems possess certain types of symmetry, its adaptation has an important issue in theoretical studies of molecules. For example, symmetry facilitates the assignment of energy levels and determines selection rules in optical transitions. In direct diagonalization, symmetry adaptation, often performed on a symmetrized basis, significantly reduces the numerical costs in diagonalizing the Hamiltonian matrix because the resulting block-diagonal structure of the Hamiltonian matrix allows for the separate