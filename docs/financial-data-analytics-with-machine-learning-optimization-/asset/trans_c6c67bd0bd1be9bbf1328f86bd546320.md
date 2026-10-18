

同时，`f̂ₓ(x)` 的方差为：

`Var(f̂ₓ(x)) = 1/(n hₙ²) Var(K((x - x̄)/hₙ))`
`           = 1/(n hₙ²) (∫ K²((x - x̄)/hₙ) - O(hₙ²))`
`           = 1/(n hₙ²) (∫ K²(z) fₓ(x + hₙz) hₙ dz - O(hₙ²))`
`           = 1/(n hₙ) (∫ K²(z) fₓ(x) dz + O(∫ K²(z) z dz · hₙ)) - O(hₙ)`
`           = 1/(n hₙ) fₓ(x) ∫ K²(z) dz + O(1/n)`

