Still, these high-fidelity simulations are rich in information that could help decode the complexity of turbulence–chemistry interactions and guide the development of filtered and lower-fidelity modeling approaches for faster evaluations.

The objective of the present chapter is to demonstrate the potential of data-driven modeling in the context of combustion simulations. In particular, we present:

+   - The application of principal component analysis (PCA) and other linear and nonlinear techniques to identify low-dimensional manifolds in high-fidelity combustion data sets, and to reveal the key features of complex nonequilibrium phenomena. Different techniques are compared to PCA, including nonnegative matrix factorization (NMF), autoencoders, and local PCA in Section 15.3.
+   - The development of reduced-order models (ROMs), to be used in conjunction with, or to replace high-fidelity simulation tools, to reduce the burden associated with the large number of species in detailed chemical mechanisms. First, the use of transport models based on PCA is presented in Section 15.4. Finally, the application of the data-driven adaptive-chemistry approach based on the combination of classification and chemical mechanism reduction is discussed in Section 15.5.

# 15.2 Combustion Data Sets

The structure of combustion data sets differs from the one seen in pure fluid mechanics applications (presented in Chapter 6). The data set encountered in multicomponent reactive flows is stored in the form of a matrix X ∈ ℝ^{N×Q}. Each column of X is tied to one of the Q thermochemical state-space variables: temperature T, pressure p, and N_s−1 chemical species⁶ mass (or mole) fractions, denoted by Y_i for the i th species. For open flames and atmospheric burners the pressure variable can be omitted. Each of the N rows of X contains observations of all Q variables at a particular point in the physical space and/or time (and sometimes, a point in the space of other independent parameters, as briefly discussed later). This structure of the data matrix is presented below:

X = ⎡ ⋮ ⋮ ⋮ ⋮ ⋯ ⋮ ⎤
    ⎢ T p Y₁ Y₂ … Y_{N_s−1} ⎥
    ⎣ ⋮ ⋮ ⋮ ⋮ ⋯ ⋮ ⎦ . (15.2)

For such a data set, Q = N_s + 1. We denote the i th row (observation) in X as x_i ∈ ℝ^Q and the j th column (variable) in X as X_j ∈ ℝ^N. When the data set is only resolved in space and not resolved in time, N represents the number of points on a spatial grid, and X can be thought of as a data snapshot (a notion much like the one discussed in Chapters 6–9). Typically, we can expect N ≫ Q. However, the magnitude of Q will strongly depend on the number of species, N_s, involved in the chemical reactions, and can even reach the order of thousands for more complex fuels (Lu & Law 2009).

⁶ Since mass (or mole) fractions sum up to unity for every observation, out of N_s species only N_s − 1 are independent.