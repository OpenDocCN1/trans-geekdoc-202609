In terms of the current placement \(\boldsymbol{x}\), the material time derivative of a tensor \(\Lambda_{\mathrm{E}}(\boldsymbol{x}, t)\) is given by (Haupt, 2002)

\(\dot{\Lambda}_{\mathrm{E}}(\boldsymbol{x}, t) = \frac{\partial \Lambda_{\mathrm{E}}}{\partial t}(\boldsymbol{x}, t) + \frac{\partial \Lambda_{\mathrm{E}}}{\partial \boldsymbol{x}}(\boldsymbol{x}, t) \cdot \boldsymbol{v}_{\mathrm{E}}(\boldsymbol{x}, t),\quad (2.8)\)

where the Eulerian velocity \(\boldsymbol{v}_{\mathrm{E}}(\boldsymbol{x}, t)\) is related to the Lagrangian velocity

\(\boldsymbol{v}_{\mathrm{L}}(\boldsymbol{X}, t) = \frac{\partial \boldsymbol{\chi}}{\partial t}(\boldsymbol{X}, t)\quad (2.9)\)

through equations (2.6). In the following, we omit the explicit declaration of Eulerian and Lagrangian quantities, and instead define the parameterization through the arguments of the discussed quantities. Eulerian quantities are defined through the argument \(\boldsymbol{x}\) and Lagrangian quantities are defined through the argument \(\boldsymbol{X}\). To capture local changes in the motion of the material body's points, we use the first spatial derivative of the motion \(\boldsymbol{\chi}\), defined as the deformation gradient field \(\boldsymbol{F}\) (Steinmann, 2015)

\(\boldsymbol{F}: Y_0 \times [0, T] \rightarrow (\mathbb{R}^d)^{\otimes 2},\quad (\boldsymbol{X}, t) \mapsto \frac{\partial \boldsymbol{\chi}}{\partial \boldsymbol{X}}(\boldsymbol{X}, t).\quad (2.10)\)

Abusing notation and setting \(\boldsymbol{F} = \boldsymbol{F}(\boldsymbol{X}, t)\), the relations (Steinmann, 2015)

\(\mathrm{d}\boldsymbol{x} = \boldsymbol{F} \, \mathrm{d}\boldsymbol{X},\quad \mathrm{d}a = \det(\boldsymbol{F})\boldsymbol{F}^{-\top} \mathrm{d}A,\quad \text{and} \quad \mathrm{d}v = \det(\boldsymbol{F}) \, \mathrm{d}V,\quad (2.11)\)

describe the mapping of the infinitesimal line \(\mathrm{d}\boldsymbol{X}\), the infinitesimal area \(\mathrm{d}A\), and the infinitesimal volume \(\mathrm{d}V\) from the reference placement \(Y_0\) to the current placement \(Y_t\). We may split a deformation gradient \(\boldsymbol{F}(\boldsymbol{X}, t)\) into the symmetric positive definite tensors \(\boldsymbol{U}(\boldsymbol{X}, t) \in \text{Sym}^+(d)\) and \(\boldsymbol{V}(\boldsymbol{X}, t) \in \text{Sym}^+(d)\), as well as a proper orthogonal tensor \(\boldsymbol{R}(\boldsymbol{X}, t) \in SO(d)\), such that (Steinmann, 2015)

\(\boldsymbol{F}(\boldsymbol{X}, t) = \boldsymbol{U}(\boldsymbol{X}, t)\boldsymbol{R}(\boldsymbol{X}, t) = \boldsymbol{R}(\boldsymbol{X}, t)\boldsymbol{V}(\boldsymbol{X}, t).\quad (2.12)\)