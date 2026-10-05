# Recursive Solutions to Large Eigenproblems

![](bbox=[0.285, 0.098, 0.715, 0.538])

**Figure 3** Absolute values of the elements of the Lanczos eigenvectors of the ground state of HOCI. Adapted with permission from Ref. 38.

Several observations in Figure 3 are worth noting. First, the first copying of the eigenvector consists primarily of the first 160 Lanczos vectors, whereas the second copy is composed largely of the 160 latter vectors, implying regeneration of some recurring vectors after the convergence of the first copy. Starting to appear at $K=300$, the second eigenvector has an extremely small first element $|z_1|$, indicating that in loose sense this copy is not contained in the initial vector (cf. Eq. [35]). In other words, this copy is generated from round-off errors. Indeed, the Lanczos algorithm routinely generates eigenpairs that are not contained in the initial vector. Second, once converged, copies tend to mix with each other because they are practically degenerate. Nonetheless, a closer look at the curves in Figure 3 reveals that each copy still has its distinct contributions from different $k$ ranges.

The Cullen-Williborough test, $^{27,37}$ on the other hand, was designed to identify the so-called "spurious" eigenvalues, rather than the converged eigenvalues. In particular, the tridiagonal matrix $T^{(K)}$ and its submatrix, obtained