where **v** ∈ ℝⁿ is the set of n unknown parameters, **c**ᵀ **v** is the linear objective function we want to minimize, and **a**ᵢᵀ **v** ≤ bᵢ is a set of m linear constraints we must satisfy. To apply this to our problem, let us define **v** = (w₁, …, w_D, e₁, …, e_N) ∈ ℝ^{D+N}, where e_i = |y_i - ŷ_i| is the residual error for example i. We want to minimize the sum of the residuals, so we define **c** = (0, …, 0, 1, …, 1) ∈ ℝ^{D+N}, where the first D elements are 0, and the last N elements are 1.

We need to enforce the constraint that e_i = |ŷ_i - y_i|. In fact it is sufficient to enforce the constraint that |**w**ᵀ **x**_i - y_i| ≤ e_i, since minimizing the sum of the e_i's will “push down” on this constraint and make it tight. Since |a| ≤ b ⟹ -b ≤ a ≤ b, we can encode |**w**ᵀ **x**_i - y_i| ≤ e_i as two linear constraints:

e_i ≥ **w**ᵀ **x**_i - y_i   (11.82)
 e_i ≥ -(**w**ᵀ **x**_i - y_i)   (11.83)

We can write Eq. (11.82)–Eq. (11.83) as

(**x**_i, 0, …, 0, -1, 0, …, 0)ᵀ **v** ≤ y_i   (11.84)

where the first D entries are filled with **x**_i, and the -1 is in the (D + i)‘th entry of the vector. Similarly we can write Eq. (11.83) as

(-**x**_i, 0, …, 0, -1, 0, …, 0)ᵀ **v** ≤ -y_i   (11.85)

We can write these constraints in the form **A v** ≤ **b** by defining **A** ∈ ℝ^{2N × (N+D)} as follows:

**A** = 
⎛ **x**₁  -1  0  0 … 0 ⎞
⎜ -**x**₁ -1  0  0 … 0 ⎟
⎜  **x**₂  0 -1  0 … 0 ⎟
⎜ -**x**₂  0 -1  0 … 0 ⎟
⎜            ⋮          ⎟
⎝                     ⎠   (11.86)

and defining **b** ∈ ℝ^{2N} as

**b** = (y₁, -y₁, y₂, -y₂, …, y_N, -y_N)   (11.87)

# 11.4.3 Robust regression using Huber loss

An alternative to minimizing the NLL using a Laplace or Student likelihood is to use the Huber loss, which is defined as follows:

ℓ_huber(r, δ) = { r²/2   if |r| ≤ δ
                  δ|r| - δ²/2   if |r| > δ }   (11.88)

This is equivalent to ℓ₂ for errors that are smaller than δ, and is equivalent to ℓ₁ for larger errors. See Fig. 8.3 for a plot.

The advantage of this loss function is that it is everywhere differentiable. Consequently optimizing the Huber loss is much faster than using the Laplace likelihood, since we can use standard smooth