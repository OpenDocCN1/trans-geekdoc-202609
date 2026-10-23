It can be shown that if {x₁, …, xₙ} is a set of n linearly independent vectors, where each xᵢ ∈ ℝⁿ, then span({x₁, …, xₙ}) = ℝⁿ. In other words, any vector v ∈ ℝⁿ can be written as a linear combination of x₁ through xₙ.

A basis ℬ is a set of linearly independent vectors that spans the whole space, meaning that span(ℬ) = ℝⁿ. There are often multiple bases to choose from, as illustrated in Fig. C.3b. The standard basis uses the coordinate vectors e₁ = (1,0,…,0), up to eₙ = (0,0,…,0,1). This lets us translate back and forth between viewing a vector in ℝ² as an either an "arrow in the plane", rooted at the origin, or as an ordered list of numbers (corresponding to the coefficients for each basis vector).

# C.1.2.3 Linear maps and matrices

A linear map or linear transformation is any function f : 𝒱 → 𝒲 such that f(v + w) = f(v) + f(w) and f(a v) = a f(v) for all v, w ∈ 𝒱. Once the basis of 𝒱 is chosen, a linear map f : 𝒱 → 𝒲 is completely determined by specifying the images of the basis vectors, because any element of 𝒱 can be expressed is expessed uniquely as a linear combination of them.

Suppose 𝒱 = ℝⁿ and 𝒲 = ℝᵐ. We can compute f(vᵢ) ∈ ℝᵐ for each basis vector in 𝒱, and store these along the rows of an m × n matrix A. We can then compute y = f(x) ∈ ℝᵐ for any x ∈ ℝⁿ as follows:

y = (∑_{j=1}^n a_{1j} x_j, …, ∑_{j=1}^n a_{mj} x_j)   (C.15)

This corresponds to multiplying the vector x by the matrix A:

y = A x   (C.16)

See Appendix C.2 for more details.

If the function is invertible, we can write

x = A⁻¹ y   (C.17)

See Appendix C.3 for details.

# C.1.2.4 Range and nullspace of a matrix

Suppose we view a matrix A ∈ ℝ^{m×n} as a set of m vectors in ℝⁿ. The range (sometimes also called the column space) of this matrix is the span of the columns of A. In other words,

range(A) ≜ {v ∈ ℝᵐ : v = A x, x ∈ ℝⁿ}.   (C.18)

This can be thought of as the set of vectors that can be "reached" or "generated" by A; it is a subspace of ℝᵐ whose dimensionality is given by the rank of A (see Sec. C.1.4.3). The nullspace of a matrix A ∈ ℝ^{m×n} is the set of all vectors that get mapped to the null vector when multiplied by A, i.e.,

nullspace(A) ≜ {x ∈ ℝⁿ : A x = 0}.   (C.19)

The span of the rows of A is the complement to the nullspace of A.

See Fig. C.4 for an illustration of the range and nullspace of a matrix. We shall discuss how to compute the range and nullspace of a matrix numerically in Sec. C.5.4 below.