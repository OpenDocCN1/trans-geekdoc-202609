
sufficient for our purposes. Assume that for constant temperature and density a twice continuously differentiable dissipation potential density \(\Psi : \text{Sym}_0(3) \to \mathbb{R}\) is given, which furthermore satisfies the condition

\(\frac{\partial \Psi}{\partial \mathbf{D}}(\mathbf{0}) = \mathbf{0}.\)

Then, the non-equilibrium viscous stress \(\boldsymbol{\tau}\) is governed by the relationship

\(\boldsymbol{\tau} = \frac{\partial \Psi}{\partial \mathbf{D}}(\mathbf{D}),\)

and by the fundamental theorem of calculus, we may write

\(\frac{\partial \Psi}{\partial \mathbf{D}}(\mathbf{D}) = \int_0^1 \frac{\mathrm{d}}{\mathrm{d}s} \left[ \frac{\partial \Psi}{\partial \mathbf{D}}(s\mathbf{D}) \right] \mathrm{d}s = \int_0^1 \frac{\partial^2 \Psi}{\partial \mathbf{D}^2}(s\mathbf{D}) \mathrm{d}s \, [\mathbf{D}] \equiv \mathbb{V}(\mathbf{D})[\mathbf{D}].\)

Thus, the viscosity tensor

\(\mathbb{V}(\mathbf{D}) \equiv \int_0^1 \frac{\partial^2 \Psi}{\partial \mathbf{D}^2}(s\mathbf{D}) \mathrm{d}s\)

has major symmetries, as a consequence of Schwarz’ theorem on the commutativity of the second partial derivatives of a twice continuously differentiable function. Thus, for any given dissipation potential density, the associated viscosity tensor (3.8) automatically has the major symmetry. For compactness, we will refer to *dissipation potential densities* as *dissipation potentials* throughout this thesis.

It is not difficult to construct dissipation potentials both for the Newtonian (3.1) and the Cross model (3.2), i.e.,

\(\Psi(\mathbf{D}) = \left( \eta_\infty + (\eta_0 - \eta_\infty) \, {}_2F_1 \left( 1, \frac{2}{m}, \frac{2+m}{m}, -(k\dot{\gamma})^m \right) \right) \frac{\dot{\gamma}^2}{2}\) involving the hypergeometric function \(_2F_1\). In the Newtonian case, it holds that \(\eta = \eta_0 = \eta_\infty\), and thus

\(\Psi(\boldsymbol{D}) = \eta \ \boldsymbol{D} \cdot \boldsymbol{D}\) (3.10)

The advantage of using the representation by a dissipation potential is that this potential form is preserved under a change of scales, i.e., by homogenization (Suquet, 1985; 1987). Subsequently, the viscosity tensor is accessible via a postprocessing step, see equation (3.8).

Actually, due to the presence of infinitely viscous inclusions, it is more convenient to work with the complementary potential \(\Phi\) which arises as the Legendre-Fenchel dual

\(\Phi(\boldsymbol{\tau}) := \sup \{ \boldsymbol{\tau} \cdot \boldsymbol{D} - \Psi(\boldsymbol{D}) \mid \boldsymbol{D} \in \text{Sym}_0(3) \}\) (3.11)

of the dissipation potential \(\Psi\). The potential \(\Psi\) must grow superlinearly and be non-negative for \(\Phi\) to be a proper function, i.e., not infinite everywhere. Then, as a consequence of the Fenchel-Moreau identity (Chambolle and Pock, 2016, Eq. (3.8)), the constitutive law (3.6) may be written in dual form

\(\boldsymbol{D} = \frac{\partial \Phi}{\partial \boldsymbol{\tau}}(\boldsymbol{\tau}).\) (3.12)

From this, similar to the viscosity \(\mathbb{V}\), the fluidity tensor \(\mathbb{F}\) follows as

\(\mathbb{F}(\boldsymbol{\tau}) \equiv \int_0^1 \frac{\partial^2 \Phi}{\partial \boldsymbol{\tau}^2}(s\boldsymbol{\tau}) \ ds.\) (3.13)

In the Newtonian case, the viscosity \(\mathbb{V}\) and the fluidity \(\mathbb{F}\) constitute the kinetic coefficients (Šilhavý, 1997). In addition to the presented context, the aforementioned potential framework can also be applied in the context of the rigid-viscoplastic modeling of polycrystals. See, e.g., Böhlke and Bertram (2003) and Böhlke (2004), where the viscoplastic behavior of single crystals and polycrystals is modeled via a non-linear viscous approach.

### 3.2.2 Scale transition in non-linear viscosity

Locally, the balance of linear momentum

div \( (\boldsymbol{\tau}) - \nabla p = \mathbf{0} \quad \text{(3.14)}\)

results from a split of the stress \(\boldsymbol{\sigma}\) inside the material into an unknown, periodic pressure field \(p: Y \rightarrow \mathbb{R}\) and the local viscous stress field

\(\boldsymbol{\tau} = \mathcal{T}(\cdot, \bar{\mathbf{D}} + \nabla^s \boldsymbol{v}), \quad \text{(3.15)}\)

and needs to be satisfied. Here, the pressure \(p\) acts as a reaction stress due to incompressibility. We consider a rectangular volume \(Y \subseteq \mathbb{R}^3\), and suppose that a heterogeneous dissipation potential \(\Psi: Y \times \text{Sym}_0(3) \rightarrow \mathbb{R}\) is given which satisfies the conditions discussed in the previous section pointwise. The associated stress operator reads

\(\mathcal{T}: Y \times \text{Sym}_0(3) \rightarrow \text{Sym}_0(3), \quad \text{(3.16)}\)

\((x, \mathbf{D}) \mapsto \frac{\partial \Psi}{\partial \mathbf{D}}(x, \mathbf{D}). \quad \text{(3.17)}\)

The effective dissipation potential is defined as

\(\bar{\Psi}(\bar{\mathbf{D}}) = \inf \left\langle \Psi(\cdot, \bar{\mathbf{D}} + \nabla^s \boldsymbol{v}) \right\rangle_Y \quad \text{for } \bar{\mathbf{D}} \in \text{Sym}_0(3), \quad \text{(3.18)}\)

where the infimum is taken over all periodic velocity fields \(\boldsymbol{v}: Y \rightarrow \mathbb{R}^3\) with vanishing divergence and the operator \(\langle \cdot \rangle_Y\) denotes the spatial average

\(\langle \cdot \rangle_Y \equiv \frac{1}{|Y|} \int_Y (\cdot) \, \mathrm{d}Y(\boldsymbol{x}) \quad \text{with} \quad |Y| \equiv \int_Y \, \mathrm{d}Y(\boldsymbol{x}). \quad \text{(3.19)}\)

The effective shear stress \(\bar{\boldsymbol{\tau}} \in \text{Sym}_0(3)\) then arises from the relationship

\(\bar{\boldsymbol{\tau}}(\bar{\boldsymbol{D}}) = \frac{\partial \bar{\Psi}}{\partial \bar{\boldsymbol{D}}}(\bar{\boldsymbol{D}}),\)
(3.20)

which is similar to equation (3.6). Equivalently, the effective stress may be computed by averaging the local shear stress

\(\bar{\boldsymbol{\tau}}(\bar{\boldsymbol{D}}) = \left\langle \mathcal{T}(\cdot, \bar{\boldsymbol{D}} + \nabla^{\text{s}}\boldsymbol{v}) \right\rangle_{Y},\)
(3.21)

where the periodic velocity field \(\boldsymbol{v}\) solves the Euler-Lagrange equation of the variational problem (3.18)

\(\text{div } (\boldsymbol{\tau}) - \nabla p = \mathbf{0},\)
(3.22)

which equals the balance of linear momentum (3.14). The described procedure permits to compute the effective viscosity of a mixture of viscous materials. However, we are interested in the effective viscosity of a suspension, i.e., of a mixture involving rigid inclusions. Because the viscosity inside these inclusions is infinite, the differential equation (3.14) is not, constitutively, well-defined. To handle this issue, we transfer to a dual formulation. Inside the infinitely viscous inclusions, the fluidity, i.e., the inverse of the viscosity, vanishes identically. Consequently, the associated equations are, constitutively, well-defined.

Instead of the effective dissipation potential (3.18) one may consider the effective complementary potential \(\bar{\Phi}\), a function of the effective shear stress \(\bar{\boldsymbol{\tau}}\), from which the constitutive law

\(\bar{\boldsymbol{D}}(\bar{\boldsymbol{\tau}}) = \frac{\partial \bar{\Phi}}{\partial \bar{\boldsymbol{\tau}}}(\bar{\boldsymbol{\tau}}),\)
(3.23)

arises dual to the primal relationship (3.20). To obtain the effective viscosity, a strategy based on the effective complementary potential requires to invert the effective law (3.23). To avoid this difficulty, we use mixed "boundary conditions" (Kabel et al., 2016a), i.e., we consider the dual variational principle, but prescribe the effective shear rate tensor \(\bar{D}\). The convex dual of the variational problem (3.18) reads

$$\langle \Phi(., \tau) - \tau \cdot \bar{D} \rangle_Y \longrightarrow \inf, $$ (3.24)

where the infimum is taken over all stress fields \(\tau : Y \to \text{Sym}_0(3)\) which satisfy the equilibrium equation (3.14) for a suitable pressure field, see Wicht et al. (2020b, §4 and Appendix B).

### 3.2.3 Computational aspects and setup

After discussing theoretical aspects in the previous section, this section is dedicated to selected computational aspects concerning the fiber suspension microstructure and FFT-based procedure, starting with a solution scheme for the convex dual variational problem (3.24). The Euler-Lagrange equation of the convex dual variational problem (3.24) reads

$$\mathbb{P}_{\mathcal{E}} \left[ \frac{\partial \Phi}{\partial \tau} (\tau_k) - \bar{D} \right] = \mathbf{0}, $$ (3.25)

where \(\mathbb{P}_{\mathcal{E}}\) denotes the \(L^2\)-projector onto the shear stresses satisfying the equilibrium equation (3.14). In terms of an arbitrary stepsize \(\alpha\), minimizers of the Euler-Lagrange equation (3.25) are fixed points of the gradient descent scheme

$$\tau_{k+1} = \tau_k - \alpha \mathbb{P}_{\mathcal{E}} \left[ \frac{\partial \Phi}{\partial \tau} (\tau_k) - \bar{D} \right], $$ (3.26)

which has a unique fixed point, provided the optimization problem (3.24) is strictly convex. For a closed form expression of the action of \(\mathbb{P}_{\mathcal{E}}\) in Fourier space, and an analogous derivation of a fixed point scheme in the linear case, we refer to Bertóti et al. (2021). Numerical schemes based on the gradient descent iteration (3.26) require computing a strain rate
