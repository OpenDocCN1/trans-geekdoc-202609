# 3.2.2 Scale transition in non-linear viscosity

Locally, the balance of linear momentum

div \( (\boldsymbol{\tau}) - \nabla p = \mathbf{0} \quad \text{(3.14)}\)

results from a split of the stress \(\boldsymbol{\sigma}\) inside the material into an unknown,
periodic pressure field \(p: Y \rightarrow \mathbb{R}\) and the local viscous stress field

\(\boldsymbol{\tau} = \mathcal{T}(\cdot, \bar{\mathbf{D}} + \nabla^s \boldsymbol{v}), \quad \text{(3.15)}\)

and needs to be satisfied. Here, the pressure \(p\) acts as a reaction stress due
to incompressibility. We consider a rectangular volume \(Y \subseteq \mathbb{R}^3\), and sup-
pose that a heterogeneous dissipation potential \(\Psi: Y \times \text{Sym}_0(3) \rightarrow \mathbb{R}\) is
given which satisfies the conditions discussed in the previous section
pointwise. The associated stress operator reads

\(\mathcal{T}: Y \times \text{Sym}_0(3) \rightarrow \text{Sym}_0(3), \quad \text{(3.16)}\)

\((x, \mathbf{D}) \mapsto \frac{\partial \Psi}{\partial \mathbf{D}}(x, \mathbf{D}). \quad \text{(3.17)}\)

The effective dissipation potential is defined as

\(\bar{\Psi}(\bar{\mathbf{D}}) = \inf \left\langle \Psi(\cdot, \bar{\mathbf{D}} + \nabla^s \boldsymbol{v}) \right\rangle_Y \quad \text{for } \bar{\mathbf{D}} \in \text{Sym}_0(3), \quad \text{(3.18)}\)

where the infimum is taken over all periodic velocity fields \(\boldsymbol{v}: Y \rightarrow \mathbb{R}^3\)
with vanishing divergence and the operator \(\langle \cdot \rangle_Y\) denotes the spatial
average

\(\langle \cdot \rangle_Y \equiv \frac{1}{|Y|} \int_Y (\cdot) \, \mathrm{d}Y(\boldsymbol{x}) \quad \text{with} \quad |Y| \equiv \int_Y \, \mathrm{d}Y(\boldsymbol{x}). \quad \text{(3.19)}\)