
## SVD Expansion and Geometric Implications

Let us now elaborate on the SVD expansion and investigate its geometric implications. By the definition of the pseudoinverse, `X†`, and assuming the `N × l` (`N > l`) data matrix to be full column rank (`r = l`), employing Eq. (6.14) in Eq. (6.5) we get (Problem 6.6):

```
ŷ = Xθ̂_LS = X(XᵀX)⁻¹Xᵀy = U_l U_lᵀ y = [u₁, ..., u_l] [u₁ᵀy; ⋮; u_lᵀy]
```

or

![Equation](images/B9780443292385000123/fx006.jpg) (6.19)

The latter represents the *projection* of **y** onto the column space of `X`, i.e., `span{x₁⁽ᶜ⁾, …, x_l⁽ᶜ⁾}` using a corresponding *orthonormal* basis, `{u₁, …, u_l}`, to describe the subspace (see Fig. 6.3). Note that each `u_i`, `i = 1, 2, …, l`, lies in the space spanned by the columns of `X` as suggested by Eq. (6.18). In other words, the SVD of matrix `X` provides an orthonormal basis that describes the respective column space.

![Figure 6.3 The eigenvectors u1,u2, lie in the column space of X, i.e., in the (shaded) plane \text{span}{\mathbf{x}_{1}^{c},\mathbf{x}_{2}^{c}}Equation, and form an orthonormal basis. Because \widehat{\mathbf{y}}Equation is the projection of y onto this subspace, it can be expressed as a linear combination of the two vectors of the orthonormal basis. The respective weights for the linear combination are \mathbf{u}_{1}^{T}\mathbf{y}Equation and \mathbf{u}_{2}^{T}\mathbf{y}Equation.](images/B9780443292385000123/gr003.jpg)
