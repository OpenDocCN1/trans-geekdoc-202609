4.37 Assume without loss of generality that μ = 1. Represent ||Ax||₂² − 1 as a quadratic form ⟨Rx, x⟩ where R = AᵀA − Iₙ. Use Exercise 4.36 to compute the maximum of this quadratic form on a net.

4.38 Use the ε-net expansion (Exercise 4.34).

4.39 Fix an ε/2-net ℳ of RB₂ⁿ with good size. It is enough to show that each point y ∈ ℳ is within distance ε/2 from some point gᵢ/√n ∈ RB₂ⁿ. For each y ∈ ℳ, fix a ball B_y with radius r = ¼ min(ε, R) satisfying y ∈ B_y ⊂ RB₂ⁿ. Find a lower bound on the probability that g₁/√n lands in a given ball B_y. Use independence to show that at least one of the N vectors gᵢ/√n does so with high probability. Finally, apply a union bound over ℳ.

4.40 Use Exercise 4.39 to show that the scaled random vectors gᵢ/√n, i > 1, form an good net of ball of radius 10. Use Exercise 4.38 to show that the convex hull of these points contains a ball of radius 5. Meanwhile, with high probability, the first vector g₁/√n falls in the radius 5 ball, and thus in the convex hull of the other vectors.

4.41 Use the integrated tail formula (Lemma 1.6.1).

4.42 Bound the operator norm of A below by the Euclidean norm of the first column and first row. Use concentration of the norm (3.2) to complete the proof.

4.43 The proof of Theorem 4.4.3 only relies on one property of A: that ⟨Ax, y⟩ = ⟨A, xyᵀ⟩ is subgaussian for any unit vectors x, y.

4.44 (a) Combine Exercise 4.19(a) with (2.22). (b) Combine Exercise 4.19(b) with Exercise 3.13.

4.45 The challenge is that, if q is small, the second eigenvalue of the expected adjacency matrix D = 𝔼A might not be well separated from the first, making it hard to use Davis-Kahan inequality. To fix this, modify the algorithm to consider both top eigenvectors of D and A will still be close, thanks to a higher-dimensional version of Davis-Kahan (Lemma 4.1.16, Exercise 4.13).

4.47 Using the min-max theorem (Corollary 4.1.7), reduce the problem to the smallest singular value of a m × k random matrix. (Pick E to be a coordinate subspace.)

4.48 Rewrite the quantity in question as ||Σ̄_m − I_n|| where Σ̄_m is the sample covariance matrix of the standard score of X.

4.50 (b) The idea is to use SVD to approximate a matrix A = UΣVᵀ ≈ U₀Σ₀V₀ᵀ by replacing one factor at a time. Construct an (ε/3)-net to approximate U using (b), an (ε/3)-net to approximate V (similarly) and (ε/3)-net to approximate Σ. You will find Exercise 4.4 helpful. (c) Consider m × n matrices with Frobenius norm ≤ 1 and with only r first nonzero columns.

4.51 (b) Make a quantitative conclusion for 99.5% points: not just that the signs of ⟨X_i, u⟩ and θ_i agree, but that ⟨X_i, u⟩ is well separated from zero, e.g. |⟨X_i, u⟩ − θ_i β| ≤ β/2 where β = ||μ||₂. (e) Now that you know from (d) that v ≈ u, conclude that 99.5% of the points X_i satisfy |⟨X_i, v⟩ − ⟨X_i, u⟩| ≤ 0.1β. (To do this, write the sum of the squares of these quantities, and express it in terms of Σ_m and u − v.) Now combine with (b).

5.3 If the conclusion of the first part fails, the complement B := (A_s)^c satisfies σ(B) ≥ 1/2. Apply the blow-up Lemma 5.1.6 for B.

5.6 For the upper bound, assume that ||Z − 𝔼Z||_{ψ₂} ≤ K and use the definition of the median to show that |M − 𝔼Z| ≤ CK.

5.7 First replace the expectation by the median using Exercise 5.6. Then apply the assumption for the function f(x) := dist(x, A) = inf{d(x, y) : y ∈ A} whose median is zero.

5.8 The ε-neighborhood of a half-space is still a half-space, and its Gaussian measure should be easy to compute.

5.9 (a) Use Gaussian concentration for f(x) = max_i x_i. (b) Argue that we can express X_i = μ_i + ⟨g, v_i⟩ for some non-random μ_i, v_i and g ∈ N(0, I_n). Then use Gaussian concentration.