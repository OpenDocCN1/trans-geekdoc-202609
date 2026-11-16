

D resulting from a shear stress \(\tau\) at every continuum point \(\boldsymbol{x}\) and for every iteration. Treating fibers is particularly simple: the strain rate \(\mathbf{D}\) vanishes since the inclusions are rigid.

To solve the equation

\[
\tau = 2\eta(\dot{\gamma}) \mathbf{D} \tag{3.27}
\]

for the strain rate \(\mathbf{D}\), compare equation (3.1), we first take norms on both sides to arrive at the equation

\[
\|\boldsymbol{\tau}\| = 2\eta(\dot{\gamma}) \|\mathbf{D}\| \equiv \sqrt{2}\eta(\dot{\gamma})\dot{\gamma}. \tag{3.28}
\]

We use Newton's method to find a root of the function

\[
g(\dot{\gamma}) = \|\boldsymbol{\tau}\| - \sqrt{2}\eta(\dot{\gamma})\dot{\gamma}, \tag{3.29}
\]

and thus compute iteratively

\[
\dot{\gamma}_{n+1} = \dot{\gamma}_n - s_n \frac{g(\dot{\gamma}_n)}{g'(\dot{\gamma}_n)}. \tag{3.30}
\]

Using backtracking for the step size \(s_n\) to ensure that the Armijo-Goldstein inequality (Armijo, 1966; Goldstein, 1965) holds. For the Cross fluid (3.2), the derivative of the function \(g\) computes as

\[
g'(\dot{\gamma}) = -\sqrt{2} \left( \eta(\dot{\gamma}) - \frac{m(\eta_0 - \eta_\infty)(k\dot{\gamma})^m}{(1+(k\dot{\gamma})^m)^2} \right). \tag{3.31}
\]

Once the scalar shear rate \(\dot{\gamma}\) is identified, we compute the strain rate tensor \(\mathbf{D}\) via

\[
\mathbf{D} = \frac{\boldsymbol{\tau}}{2\eta(\dot{\gamma})}. \tag{3.32}
\]

The fiber suspension microstructures were generated with the sequential addition and migration method (Schneider, 2017), and discretized on a staggered grid (Harlow and Welch, 1965) to ensure stability for incompressible material models. The resulting equation system was solved with the Barzilai-Borwein method (Barzilai and Borwein, 1988; Bertóti et al., 2021) in the Newtonian case, while a non-linear Newton-CG approach (Dembo et al., 1982; Schneider, 2020a) was used in the Cross-type case. For validation purposes, we compared computational results of the presented FFT-based approach with computational results from literature (Traxl et al., 2020), see section 3.3.1. For a detailed overview on solvers for the non-linear Lippmann-Schwinger equation in the closely related case of solid mechanics (3.26), see Schneider (2020b). For proofs on the existence and uniqueness of solutions to the considered non-linear homogenization problem (3.24), we refer to Schneider (2016). Further details on the employed FFT-based homogenization approach including solvers and discretization, we refer to Bertóti et al. (2021) and Schneider (2020a).

To numerically obtain an effective viscosity or fluidity with the integral equations (3.8) and (3.13), the respective integral, and the derivatives occurring in the integrand need to be discretized. In combination with the costly computation of the effective stresses or strains this renders the required computational effort to obtain an effective viscosity prohibitively large. Instead, we employ equation (3.7) to estimate an effective, viscosity-like quantity solely from computationally obtained effective stresses \(\bar{\tau}\), by using the following equation in Mandel's notation (Bertóti et al., 2021)

\[
\bar{\tau} = \underline{\underline{V}} \bar{\bar{D}}, \quad \text{i.e.,} \quad \underline{\underline{V}} = \bar{\bar{\tau}} \bar{\bar{D}}^\dagger.
\]

Here, \((\cdot)^\dagger\) denotes the Moore-Penrose pseudoinverse which is equal to an inversion on \(\text{Sym}_0(3)\), \(\underline{\overline{\tau}}\) collects the computed effective stresses

\[
\underline{\overline{\tau}} = \begin{bmatrix} \bar{\bar{\tau}}_{11}^{(1)} & \bar{\bar{\tau}}_{11}^{(2)} & \bar{\bar{\tau}}_{11}^{(3)} & \bar{\bar{\tau}}_{11}^{(4)} & \bar{\bar{\tau}}_{11}^{(5)} & \bar{\bar{\tau}}_{11}^{(6)} \\ \bar{\bar{\tau}}_{22}^{(1)} & \bar{\bar{\tau}}_{22}^{(2)} & \bar{\bar{\tau}}_{22}^{(3)} & \bar{\bar{\tau}}_{22}^{(4)} & \bar{\bar{\tau}}_{22}^{(5)} & \bar{\bar{\tau}}_{22}^{(6)} \\ \bar{\bar{\tau}}_{33}^{(1)} & \bar{\bar{\tau}}_{33}^{(2)} & \bar{\bar{\tau}}_{33}^{(3)} & \bar{\bar{\tau}}_{33}^{(4)} & \bar{\bar{\tau}}_{33}^{(5)} & \bar{\bar{\tau}}_{33}^{(6)} \\ \sqrt{2}\bar{\bar{\tau}}_{23}^{(1)} & \sqrt{2}\bar{\bar{\tau}}_{23}^{(2)} & \sqrt{2}\bar{\bar{\tau}}_{23}^{(3)} & \sqrt{2}\bar{\bar{\tau}}_{23}^{(4)} & \sqrt{2}\bar{\bar{\tau}}_{23}^{(5)} & \sqrt{2}\bar{\bar{\tau}}_{23}^{(6)} \\ \sqrt{2}\bar{\bar{\tau}}_{13}^{(1)} & \sqrt{2}\bar{\bar{\tau}}_{13}^{(2)} & \sqrt{2}\bar{\bar{\tau}}_{13}^{(3)} & \sqrt{2}\bar{\bar{\tau}}_{13}^{(4)} & \sqrt{2}\bar{\bar{\tau}}_{13}^{(5)} & \sqrt{2}\bar{\bar{\tau}}_{13}^{(6)} \\ \sqrt{2}\bar{\bar{\tau}}_{12}^{(1)} & \sqrt{2}\bar{\bar{\tau}}_{12}^{(2)} & \sqrt{2}\bar{\bar{\tau}}_{12}^{(3)} & \sqrt{2}\bar{\bar{\tau}}_{12}^{(4)} & \sqrt{2}\bar{\bar{\tau}}_{12}^{(5)} & \sqrt{2}\bar{\bar{\tau}}_{12}^{(6)} \end{bmatrix} . \tag{3.34}
\]

and \(\underline{\overline{D}}\) collects the investigated load cases

\[
\underline{\overline{D}} = \dot{\gamma}\sqrt{\frac{2}{3}} \begin{bmatrix} 1 & -\frac{1}{2} & -\frac{1}{2} & 0 & 0 & 0 \\ -\frac{1}{2} & 1 & -\frac{1}{2} & 0 & 0 & 0 \\ -\frac{1}{2} & -\frac{1}{2} & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & \sqrt{\frac{3}{2}} & 0 & 0 \\ 0 & 0 & 0 & 0 & \sqrt{\frac{3}{2}} & 0 \\ 0 & 0 & 0 & 0 & 0 & \sqrt{\frac{3}{2}} \end{bmatrix} . \tag{3.35}
\]

The \(i\)-th column in the matrix \(\underline{\overline{\tau}}\) contains the effective shear stress corresponding to the particular applied shear rate that is listed in the \(i\)-th column of the matrix \(\underline{\overline{D}}\). In the Newtonian case, the matrix \(\underline{\overline{V}}\) encodes the components of the viscosity tensor because of superposition. Since superposition is not generally valid in the non-Newtonian case, the matrix \(\underline{\overline{V}}\) acts as an interpolation between the six calculated effective stresses \(\underline{\overline{\tau}}\). Additionally, the load cases \(\underline{\overline{D}}\) are not uniquely defined and interpolation between the effective stresses \(\underline{\overline{\tau}}\) is qualitative in nature. However, the matrix \(\underline{\overline{V}}\) provides quantitatively robust information in the load cases collected in \(\underline{\overline{D}}\), and its interpolating property allows us to draw intuition for the results in between. Thus, even in the non-Newtonian case, the matrix \(\underline{\overline{V}}\) may be used to investigate the viscous suspension behavior. We will refer to \(\bar{\underline{V}}\) as the suspension viscosity throughout the article.

## 3.2.4 A model for the fiber suspension viscosity

Typically, it is not feasible to take the large amount of information contained in the fiber orientation distribution function (2.29) into account at every spatial element of component-scale simulations. To reduce the necessary computational effort in treating fiber orientation states, it is common to use the fiber orientation tensors of second and fourth order (Advani and Tucker III, 1987; Kanatani, 1984)

\[
\bar{\boldsymbol{N}} = \int_{S^2} \boldsymbol{n} \otimes \boldsymbol{n} \, \rho(\boldsymbol{n}) \, \mathrm{d}S(\boldsymbol{n}), \quad (3.36)
\]

\[
\bar{\tilde{\boldsymbol{N}}} = \int_{S^2} \boldsymbol{n} \otimes \boldsymbol{n} \otimes \boldsymbol{n} \otimes \boldsymbol{n} \, \rho(\boldsymbol{n}) \, \mathrm{d}S(\boldsymbol{n}). \quad (3.37)
\]

Both tensors \(\boldsymbol{N}\) and \(\mathbb{N}\) are completely symmetric, positive semi-definite, and contract with the second-order unity tensor \(\mathbf{1}\) such that

\[
\bar{\boldsymbol{N}} \cdot \mathbf{1} = 1, \quad (3.38)
\]

\[
\bar{\tilde{\boldsymbol{N}}}[\mathbf{1}] = \boldsymbol{N}. \quad (3.39)
\]

With these two descriptors at hand, a large variety of anisotropic mean-field models has been built to model material behavior (Karl and Böhlke, 2022). In the case of a transversely isotropic fluid with constant viscosity, a convenient approximation of the popular Mori-Tanaka model is

\[
\mathbb{V}_{MT} = 2\eta_{MF} \left( \mathbb{P}_2 + N_p^{MF} \mathbb{P}_2 \mathbb{N} \mathbb{P}_2 \right),
\]
\[
\eta_{MF} = \frac{1 + c_F}{1 - c_F} \eta,
\]
\[
N_p^{MF} = \frac{c_F}{1 + c_F} \frac{r_a^2}{2(\ln(2r_a) - 3/2)}.
\]

Here, \(\eta_{MF}\) is the effective scalar viscosity, and \(N_p^{MF}\) is the particle number. This model is derived by decomposing the microstructure into \(m\) transversely isotropic pseudo domains containing a single fiber and the matrix material. In a first step, the unidirectional effective viscosities \(\mathbb{V}_{UD}^m\) of these \(m\) pseudodomains are approximated with the Mori-Tanaka method by

\[
\mathbb{V}_{UD}^m = 2\eta \mathbb{P}_2 + \frac{c_F}{1 - c_F} \mathbb{P}_m^{-1},
\]

where \(\mathbb{P}_m\) is the polarization tensor depending on the matrix material properties and the fiber geometry. The expression equals the lower Hashin-Shtrikman bound (Willis, 1977). In a second step, the effective viscosity of the volume element is calculated by orientation averaging the unidirectional effective viscosities \(\mathbb{V}_{UD}^m\) via

\[
\mathbb{V}_{MT} = \frac{1}{M} \sum_{m=1}^M \boldsymbol{V}_{UD}^m.
\]

The Voigt-type average yields an upper bound on the dissipation (Bertóti and Böhlke, 2017). However, this model is only applicable for fluids with constant viscosity, since it does not depend on the shear rate \(\dot{\gamma}\). One possible extension to incorporate shear rate dependency in the case of rigid fibers is (Karl and Böhlke, 2022)

\[
\eta_{MF} = \frac{1 + c_F}{1 - c_F} \eta \left( \frac{\dot{\gamma}}{1 - c_F} \right),
\]

