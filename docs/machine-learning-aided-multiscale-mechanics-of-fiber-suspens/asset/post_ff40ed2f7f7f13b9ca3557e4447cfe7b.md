
volume of the $k$-th phase, and the phases do not intersect, i.e.,

$$Y_j \cap Y_k = \varnothing \quad \text{if} \quad j \neq k,$$ (5.2)

and form the volume $Y$, such that

$$Y = \bigcup_{j=1}^K Y_j.$$ (5.3)

Let the operator $\langle \cdot \rangle_Y$ denote volume averaging of a quantity over a volume $Y$, i.e.,

$$\langle \cdot \rangle_Y \equiv \frac{1}{|Y|} \int_Y (\cdot) \, \mathrm{d}Y(\boldsymbol{x}) \quad \text{with} \quad |Y| \equiv \int_Y \, \mathrm{d}Y(\boldsymbol{x}).$$ (5.4)

Then, we express the velocity field $\boldsymbol{v} : Y \to \mathbb{R}^3$ as

$$\boldsymbol{v} = \bar{\boldsymbol{L}} \boldsymbol{x} + \hat{\boldsymbol{v}}, \quad \text{with} \quad \langle \nabla \hat{\boldsymbol{v}} \rangle_Y = \mathbf{0},$$ (5.5)

where $\bar{\boldsymbol{L}} \in (\mathbb{R}^3)^{\otimes 2}$ stands for the prescribed effective velocity gradient and $\hat{\boldsymbol{v}}$ is the velocity fluctuation field. Accordingly, the periodic dissipation potential function $\Psi : Y \times (\mathbb{R}^3)^{\otimes 2} \to \mathbb{R}$ of the emulsion is defined through

$$\Psi(\boldsymbol{x}, \nabla^s \boldsymbol{v}) = \sum_{k=1}^K \chi_k(\boldsymbol{x}) \Psi_k(\boldsymbol{x}, \nabla^s \boldsymbol{v}),$$ (5.6)

where $\chi_k : Y \to \{0, 1\}$ refers to the characteristic function of the sub volume $Y_k$, and $\nabla^s$ stands for the symmetrized gradient. Let the flow inside the emulsion be governed by Stokes flow, i.e., the advectorial forces in the layered emulsion are small in contrast to the viscous forces, then the steady state balance of mass

$$\operatorname{div}(\rho \boldsymbol{v}) = 0,$$ (5.7)

where \(\rho : Y \rightarrow \mathbb{R}\) denotes the mass density field, is satisfied. Additionally, the stress field

$$\boldsymbol{\sigma} = \mathcal{S}(\cdot, \bar{\boldsymbol{D}} + \nabla^s \hat{\boldsymbol{v}}) \tag{5.8}$$

in terms of the effective strain rate tensor \(\bar{\boldsymbol{D}} = (\bar{\boldsymbol{L}} + \bar{\boldsymbol{L}}^{\mathsf{T}})/2\), and the associated stress operator \(\mathcal{S}\) on the space of symmetric second order tensors \(\mathrm{Sym}(3) \subset (\mathbb{R}^3)^{\otimes 2}\) (Edelen, 1973)

$$\mathcal{S} : Y \times \mathrm{Sym}(3) \rightarrow \mathrm{Sym}(3), \tag{5.9}$$

$$(\boldsymbol{x}, \boldsymbol{D}) \mapsto \frac{\partial \Psi}{\partial \boldsymbol{D}}(\boldsymbol{x}, \boldsymbol{D}), \tag{5.10}$$

satisfies the balance of linear momentum without inertial effects and volume forces

$$\text{div }(\boldsymbol{\sigma}) = \boldsymbol{0}. \tag{5.11}$$

Therefore, the effective response of the emulsion is obtained from the minimization problem

$$\langle \Psi(\boldsymbol{x}, \bar{\boldsymbol{D}} + \nabla^s \hat{\boldsymbol{v}}) \rangle_Y \longrightarrow \min_{\hat{v} \in \mathcal{A}}, \tag{5.12}$$

where \(\mathcal{A}\) stands for the admissible set

$$\mathcal{A} = \big\{ \hat{v} : Y \rightarrow \mathbb{R}^3 \mid \text{div }(\rho v) = 0 \text{ and } \langle \nabla \hat{v} \rangle_Y = \boldsymbol{0} \big\} \tag{5.13}$$

Hence, assuming there is no slip between the phases, the proof by Kabel et al. (2016b, §2) extends to layered emulsions with finite material contrast. Therefore, if the dissipation potentials \(\Psi_k\) are strictly rank-one convex, there exists a unique minimizer \(\hat{v}\) in the class of phase-wise affine velocity fields. As a special case, this is also true for incompressible Stokes flows, for which the balance of mass simplifies to

$$\text{div }(\boldsymbol{v}) = 0. \tag{5.14}$$

In the following, we use the term *layered emulsion* only for the type of emulsion defined above.

## 5.2.2 Two-phase layered emulsions with Newtonian phases

Similar to two-phase laminates of linear elastic solid materials, we wish to find a convenient closed form expression for the linear homogenization function of two-phase layered emulsions. With the goal of using layered emulsions as building blocks of an FDMN, we dedicate this section to deriving such a closed form expression for two-phase layered emulsions with kinematically unconstrained or incompressible Newtonian phases. For this purpose, we employ the results of the previous section 5.2.1, and extend an existing homogenization approach for two-phase laminates of linear elastic phases by Milton (2002, §9). To emphasize the link between the linear homogenization of laminates and layered emulsions we define the class of linear materials $\mathcal{M}$, and study layered materials of solids and fluids in parallel. A material $m_k$ in the class of linear materials $\mathcal{M}$ is characterized by the primal material tensor $\mathbb{M}_k$ or its dual tensor $\mathbb{K}_k \equiv \mathbb{M}_k^{-1}$, such that

$$(\mathbb{M}_k, \mathbb{K}_k) \in \{(\mathbb{M}^+)^2, (\mathbb{M}_0^+)^2\}. \tag{5.15}$$

Here, the convex cones $\mathbb{M}^+ \subset (\mathbb{R}^3)^{\otimes 4}$ and $\mathbb{M}_0^+ \subset (\mathbb{R}^3)^{\otimes 4}$ comprise all fourth order tensors $\mathbb{X} \in (\mathbb{R}^3)^{\otimes 4}$, which are positive definite on the vector spaces of symmetric second order tensors $\text{Sym}(3)$ and traceless symmetric second order tensors $\text{Sym}_0(3) \subset \text{Sym}(3)$, respectively. Additionally, a tensor $\mathbb{X} \in \{\mathbb{M}^+, \mathbb{M}_0^+\}$ has minor and major symmetries

$$\mathbb{X} = \mathbb{X}^{\text{Th}} = \mathbb{X}^{\text{Tl}} = \mathbb{X}^{\text{Tr}}, \tag{5.16}$$

and a tensor \(\mathbb{X} \in \mathsf{M}_0^+\) maps the second order unit tensor \(\boldsymbol{I}\) to zero, such that

$$\ker \mathbb{X} = \boldsymbol{I}, \quad \text{i.e.,} \quad \mathbb{X}[\boldsymbol{I}] = \boldsymbol{0}. \tag{5.17}$$

Here, we define the map \(\mathbb{T}[\boldsymbol{Y}]\) in component form and in the standard basis of \(\mathbb{R}^3\) as

$$\mathbb{T}[\boldsymbol{Y}] \hat{=} T_{ijkl} Y_{kl}, \quad \text{for some} \quad \boldsymbol{Y} \in (\mathbb{R}^3)^{\otimes 2}, \mathbb{T} \in (\mathbb{R}^3)^{\otimes 4}. \tag{5.18}$$

Any material \(m_k \in \mathcal{M}\) follows the linear constitutive equations

$$\boldsymbol{\sigma}^{co} = \mathbb{M}_k[\nabla^s \boldsymbol{w}] \quad \text{and} \quad \nabla^s \boldsymbol{w} = \mathbb{K}_k[\boldsymbol{\sigma}^{co}], \tag{5.19}$$

if the material \(m_k\) is not subjected to kinematic constraints, or the constitutive equation

$$\boldsymbol{\sigma}^{ico} = \boldsymbol{\tau} - p \boldsymbol{I} = \mathbb{M}_k[\nabla^s \boldsymbol{w}] - p \boldsymbol{I}, \quad \text{and} \quad \nabla^s \boldsymbol{w} = \mathbb{K}_k[\boldsymbol{\tau}], \tag{5.20}$$

if the material \(m_k\) is incompressible. Here, \(\boldsymbol{w}\) denotes the field associated with the type of material \(m_k\), i.e., the displacement field \(\boldsymbol{u}\) for linear elastic solids or the velocity field \(\boldsymbol{v}\) for linearly viscous fluids. For the constitutive equation (5.20) we use an additive split of the stress field \(\boldsymbol{\sigma}\)

$$\boldsymbol{\sigma} = \boldsymbol{\tau} - p \boldsymbol{I}, \tag{5.21}$$

into the deviatoric stress field \(\boldsymbol{\tau} : Y \to \text{Sym}_0(3)\) and the pressure field \(p : Y \to \mathbb{R}\). Here, we use \(Y \subset \mathbb{R}^3\) to denote the volume occupied by a two-phase layered material, i.e., a laminate or a layered emulsion, and \(Y_1, Y_2 \subset Y\) to denote the volume occupied by the two phases \(m_1, m_2 \in \mathcal{M}\) of the layered material. We define the effective properties \((\bar{\mathbb{M}}, \bar{\mathbb{K}}) \in \{(\mathsf{M}^+)^2, (\mathsf{M}_0^+)^2\}\) of the layered material in the sense of the Hill-Mandel condition (Hill, 1963; Mandel, 1966)

$$\langle \boldsymbol{\sigma} \cdot \nabla^s \boldsymbol{w} \rangle_Y = \langle \boldsymbol{\sigma} \rangle_Y \cdot \langle \nabla^s \boldsymbol{w} \rangle_Y \equiv \bar{\mathbb{M}} : (\langle \nabla^s \boldsymbol{w} \rangle_Y \otimes \langle \nabla^s \boldsymbol{w} \rangle_Y). \tag{5.22}$$

Then, for perfectly bonded laminates of linear solid materials without kinematic constraints, a closed form expression for the primal or dual effective properties of the laminate \(\bar{\mathbb{A}} \in [\mathbb{M}, \bar{\mathbb{K}}]\) can be derived using the procedure detailed by Milton (2002, §9), such that

$$\left( (\bar{\mathbb{A}} - \mathbb{A}_0)^{-1} + \Gamma_{\mathbb{A}_0}(\boldsymbol{n}) \right)^{-1} = \left\langle \left( (\mathbb{A}(\boldsymbol{x}) - \mathbb{A}_0)^{-1} + \Gamma_{\mathbb{A}_0}(\boldsymbol{n}) \right)^{-1} \right\rangle. \tag{5.23}$$

Here, the inverse is taken on the space \(\mathsf{M}^+\) in which \(\bar{\mathbb{A}} \in \mathsf{M}^+\) lives, \(\mathbb{A} : Y \to \mathsf{M}^+\) denotes the field of the phase wise primal or dual material properties

$$\mathbb{A} : Y \to \mathsf{M}^+, \quad \boldsymbol{x} \mapsto \begin{cases} \mathbb{A}_1 & \text{if } \boldsymbol{x} \in Y_1, \\ \mathbb{A}_2 & \text{if } \boldsymbol{x} \in Y_2, \end{cases} \tag{5.24}$$

and \(\mathbb{A}_0 \in \mathsf{M}^+\) refers to an arbitrary reference material tensor such that the term \((\mathbb{A}(\boldsymbol{x}) - \mathbb{A}_0)\) is invertible. Also, the operator \(\Gamma_{\mathbb{A}_0}(\boldsymbol{n}) \in (\mathbb{R}^3)^{\otimes 4}\) is defined as

$$\Gamma_{\mathbb{A}_0}(\boldsymbol{n}) = \Gamma_{\mathbb{I}}(\boldsymbol{n}) \left[ \Gamma_{\mathbb{I}}(\boldsymbol{n}) \mathbb{A}_0 \Gamma_{\mathbb{I}}(\boldsymbol{n}) \right]^{\dagger} \Gamma_{\mathbb{I}}(\boldsymbol{n}), \tag{5.25}$$

where \((\cdot)^\dagger\) stands for the Moore–Penrose pseudoinverse, and the operators \(\Gamma_{\mathbb{A}_0}(\boldsymbol{n})\) and \(\Gamma_{\mathbb{I}}(\boldsymbol{n})\) project onto the same subspace with respect to different inner products. More specifically, the operator \(\Gamma_{\mathbb{A}_0}(\boldsymbol{n})\) is an orthogonal projector with respect to the \(\mathbb{A}_0\)-weighted inner product

$$\langle \boldsymbol{X}, \boldsymbol{X} \rangle_{\mathbb{A}_0} = \boldsymbol{X} \cdot \mathbb{A}_0[\boldsymbol{X}], \quad \boldsymbol{X} \in \text{Sym}(3), \tag{5.26}$$

and the operator \(\Gamma_{\mathbb{I}}(\boldsymbol{n})\) is an orthogonal projector with respect to the Frobenius inner product

$$\langle \boldsymbol{X}, \boldsymbol{X} \rangle_{\text{F}} = \boldsymbol{X} \cdot \mathbb{I}[\boldsymbol{X}] = \boldsymbol{X} \cdot \boldsymbol{X}, \quad \boldsymbol{X} \in \text{Sym}(3). \tag{5.27}
