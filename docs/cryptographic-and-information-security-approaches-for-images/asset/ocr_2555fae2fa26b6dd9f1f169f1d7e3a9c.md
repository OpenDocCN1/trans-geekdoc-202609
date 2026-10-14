# Theorem 4.30: A Boolean function on ℤ₂ⁿ satisfies

Ω̂(r)(t) = Ω̂(g)²(t),  (4.21)

for all t ∈ ℤ₂ⁿ.

# Definition 4.31 The spectral radius of a Boolean function g : ℤ₂ⁿ → ℤ₂ is defined by

R_g = max{|Ω̂(g)(u)| : u ∈ ℤ₂ⁿ}  (4.22)

This definition provides a measure for linearity. Obviously, the linearity is upper bounded by 2ⁿ ≥ R_g by. The upper bound is only attainable if g is affine.

# Theorem 4.32: For a Boolean function g : ℤ₂ⁿ → ℤ₂ the spectral radius is

R_g ≥ 2^{n/2},  (4.23)

and the equality is holds if and only if Ω̂(g)² = 2ⁿ is constant.

# Theorem 4.33: The nonlinearity N_g of a Boolean function g is determined by the Walsh transform of Ω̂(g)(u)=H_{2ⁿ} ĝ, that is,

N_g = 2^{n-1} - 1/2 max_{u ∈ ℤ₂ⁿ} |Ω̂(g)(u)|.  (4.24)

Thus, it is possible to achieve high nonlinearity if the maximal Walsh coefficient is of small value.

# Example 4.34: Let us calculate a nonlinearity N_g of Boolean function g: ℤ₂² → ℤ₂ by using above definition (Table 4.3):

where

H₄ = [[1, 1, 1, 1], [1, -1, 1, -1], [1, 1, -1, -1], [1, -1, -1, 1]],

N_g = 2^{2-1} - 1/2 max|Walsh spectrum| = 2 - 1/2 (2) = 1.