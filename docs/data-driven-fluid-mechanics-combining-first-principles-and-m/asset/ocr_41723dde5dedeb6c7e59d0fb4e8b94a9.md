is not assumed, the decomposition selects harmonic modes whose frequency is not necessarily a multiple of the observation time, and a DMD is recovered.

# 8.4.3 The Multiscale Proper Orthogonal Decomposition Algorithm

The pseudo-code for computing the mPOD listed in Algorithm 3. This is composed of eight steps.

**Algorithm 3: Algorithm for computing the multiscale POD.**
**Input:** D ∈ ℝ^{n_s×n_t}, F_V ∈ ℝ^{M×1}
**Output:** Ψ_M ∈ ℝ^{n_t×R}, Σ_M ∈ ℝ^{R×R}, and Φ_M ∈ ℝ^{n_s×R}
1 Compute temporal correlation matrix K = D^† D.
2 Prepare the filter bank H₁, H₂, …, H_M.
3 Decompose K into K₁, K₂, …, K_M contributions.
4 Compute the temporal structures of each scale K = Ψ_m Λ_m Ψ_m^T.
5 Assembly basis Ψ⁰ = [Ψ₁, …, Ψ_M] and λ⁰ = [diag(Λ₁), …, diag(Λ_M)].
6 Prepare permutation P_Λ, sorting λ⁰. Then shuffle columns Ψ¹ = Ψ⁰ P_Λ.
7 Enforce orthogonality Ψ¹ = Ψ_M R → Ψ_M = Ψ¹ R^{-1}.
8 Complete the decomposition using Algorithm 2 Φ_M → from D, Ψ_M.

The first step computes the temporal correlation matrix, as in the POD. The second step prepares the filter bank, according to the introduced frequency vector F_V. The third step computes the MRA of the temporal correlation matrix; the fourth step computes the eigenvectors of each.

At this stage, we can proceed with the preparation of a single basis. First, in step 5, all the temporal structures and associated eigenvalues are collected into a single matrix Ψ⁰ and a single vector of eigenvalues λ⁰. These eigenvalues give an estimation of the relative importance of each term. This is sorted in descending order and the information is used to permute the columns of Ψ⁰ using an appropriate permutation matrix P_Λ.

If the filters were ideal, the resulting temporal basis Ψ¹ = Ψ⁰ P_Λ would be completed. However, to compensate for the nonideal frequency response of the filters, a reduced QR factorization is used in step 7 to enforce the orthonormality of the mPOD basis. The result of the orthogonalization procedure is the matrix of the temporal structure of the mPOD. The final step is the projection to compute the spatial structures that is common to every decomposition and that can be computed using Algorithm 2.

Note that special attention should be given to the filtering process in the third step. If this is done as in Exercise 4, it is implicitly assumed that the matrix K is

> 23 Can we by-pass this step? Can we compute all the Ψ_m ’s from one single diagonalization (of a properly filtered matrix)? These were two brilliant questions by Bo B. Watz, development engineer at Dantec Dynamics, who attended the lecture series. The answer is that it is possible, in principle, to compute the basis from one clever diagonalization. However, the filtering is challenging: that was the starting point of new exciting developments toward the fast mPOD.

> 24 Observe that a simplified version could be used since the temporal structure is orthonormal!