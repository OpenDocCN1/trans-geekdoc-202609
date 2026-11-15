and are often harder to interpret and generalize outside of the training manifold.

# 8.2.2 Free Energy Surfaces

Given the Cartesian coordinates of a molecule with N atoms, x ∈ R^{3N}, we define the collective coordinates by the encoding

```
$$\mathbf{y} = E(\mathbf{x}),$$ \( (5) \)
```

where y ∈ R^m and m is a small number. In ML terms, the coordinates y define a latent space. In molecular simulations, the collective coordinates are often defined to describe the slowest processes of the system (63). In general, the mapping (or encoding) of E can be highly nonlinear. If the energy function U (x) associated with the atomistic representation is known, an important quantity to compute—for instance, to connect with experimental measurements—is the free energy of the system as a function of the collective variables. The free energy is defined as

```
$$F(\mathbf{y}) = -\log \mu_Y(\mathbf{y}) + \text{const},$$ \( (6) \)
```

where μ_Y (y) is the marginal distribution on y of the equilibrium distribution μ(x) given by Equation 1:

```
$$\mu_Y(\mathbf{y}) = \int_{\mathbf{x}|E(\mathbf{x})=\mathbf{y}} \mu(\mathbf{x}) \mathrm{d}\mathbf{x}.$$ \( (7) \)
```

The integral in Equation 7 is in practice impossible to compute analytically for high-dimensional systems, and several methods have been developed for its numerical estimation by enhancing the sampling of the equilibrium distribution in MD simulations of the system.

The definition of the free energy can also be formulated as a learning problem: The aim is to optimize the parameters θ of a free energy function model F̂(y, θ) such that Equations 6 and 7 are satisfied to a good approximation. Fulfilling these equations is usually referred to as enforcing thermodynamic consistency.

Using methods that estimate the free energy F^λ (or its gradient F^λ) at a given set of points in the collective variables space y^λ (λ = 1, ... , M), one can use the free energy loss,

```
$$L_\text{ene} = \sum_{\lambda=1}^M \| F^\lambda - \hat{F}(\mathbf{y}^\lambda, \theta) \|^2,$$
```