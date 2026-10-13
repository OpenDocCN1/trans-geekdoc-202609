
where `f : ℝˡ ↦ ℝˡ` is an *invertible* (vector) function. That is, given `y`, `x = f⁻¹(y)` can be uniquely obtained. We are given the joint PDF, `pₓ(x)`, of `x` and the task is to obtain the joint PDF, `pᵧ(y)`, of `y`.

The Jacobian matrix of the transformation is defined as

```
J(y; x) := ∂(y₁,y₂,…,yₗ)/∂(x₁,x₂,…,xₗ) := 
[ ∂y₁/∂x₁ … ∂y₁/∂xₗ ]
[ ⋮       ⋱ ⋮       ]
[ ∂yₗ/∂x₁ … ∂yₗ/∂xₗ ].
```

Then, it can be shown (e.g., [6]) that

```
pᵧ(y) = pₓ(x) / |det(J(y; x))| |_{x = f⁻¹(y)}.
```

where `|det(⋅)|` denotes the absolute value of the determinant of a matrix. For real random variables, as in `y = f(x)`, Eq. (2.45) simplifies to

```
pᵧ(y) = pₓ(x) / |dy/dx| |_{x = f⁻¹(y)}.
```
