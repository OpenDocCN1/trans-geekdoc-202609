![](bbox=[0.1, 0.08, 0.85, 0.43])

Figure 1. Constructing force field models with machine learning. (a) Reference geometries are sampled from a molecular dynamics trajectory that is sufficiently long to ensure optimal coverage of the configuration space. (b) For a small subset of geometries, energy and force labels are then computed at a high level of theory to form the training, validation, and test data sets. A globally consistent atom–atom assignment across the whole training set enables the identification and reconstructive exploitation of relevant spatial and temporal physical symmetries of the molecular dynamics. (c) The resulting machine learning model of the potential energy surface is finally used to speed up sampling-intensive path-integral molecular dynamics simulations at the accuracy of the reference electronic structure method (10). (d) An interatomic distance distribution, sampled with classical and path-integral molecular dynamics, is shown. Abbreviations: CCSD (T), coupled-cluster single double (triple); DFT, density functional theory

```
**f(x)** = -∇**U**(x)
```

and minimize the loss function:

```
L_force = Σ_i || ∇Û(x_i, θ) + f_i ||^2
```

The existing ML PES models are based either on nonlinear kernel learning or on (deep) neural networks. Both approaches have advantages and limitations. The advantage of the kernel methods is that their convex nature yields a unique solution, whose behavior can be controlled outside of the training data. Neural networks are nonconvex ML models