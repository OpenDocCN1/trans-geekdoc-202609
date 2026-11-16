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

arises dual to the primal relationship (3.20). To obtain the effective viscosity, a strategy based on the effective complementary potential requires to invert the effective law (3.23). To avoid this difficulty, we use