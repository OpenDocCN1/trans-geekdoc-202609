# Corollary 7.2.

Let ε > 0, T > 0, d ∈ ℕ, k > 6(3d + 8) := γ, let (u, p) ∈ H^k(𝕋^d × [0, T]) be the classical solution of the Navier–Stokes equation (2.8), let the hypothesis space consist of PINNs for which the upper bound on the weights is at least R ≥ ε^{-1/(k-γ)} ln(1/ε), the width is at least W ≥ ε^{-(d+1)/(k-γ)} and the depth is at least L ≥ 3, let (u_{θ*(S)}, p_{θ*(S)}) be the PINN that solves (2.69) and let the training set S satisfy N_t ≥ ε^{-d(1+γ/(k-γ))}, N_int ≥ ε^{-2(d+1)(1+γ/(k-γ))} and N_s ≥ ε^{-2d(1+γ/(k-γ))}. It holds that

‖u − u_{θ*(S)}‖_{L^2(D×[0,T])} = O(ε).  (7.5)

*Proof.* The results follow from combining results on the approximation error (Theorem 4.9), the stability (Theorem 5.7) and the generalization error (Theorem 6.5).

# Example 7.3 (Poisson’s equation).

We revisit Poisson’s equation with the variation residual, as previously considered in Example 4.30 (Question 1) and Example 5.11 (Question 2). Recall that if f ∈ ℬ^0(Ω) (see Definition 4.28) satisfies ∫_Ω f(x) dx = 0, then the corresponding unique solution u to Poisson’s equation −Δu = f with zero Neumann boundary conditions is u ∈ ℬ^2(Ω).

Now, assume that the training set S consists of N i.i.d. randomly generated points in Ω, and we optimize over a subset of shallow softplus neural networks of width m, corresponding to parameter space Θ* ⊂ Θ; a more precise definition can be found in Lu et al. (2021c, eq. 2.13). As usual, we then define u_{θ*(S)} as the minimizer of the discretized energy residual 𝒥(θ, S). In this setting, one can prove the following a priori generalization result (Lu et al. 2021c, Remark 2.1).

# Theorem 7.4.

Assume the setting defined above. If we set m = N^{1/3}, then there exists a constant C > 0 (independent of m and N) such that

𝔼[‖u − u_{θ*(S)}‖_{H^1(Ω)}^2] ≤ C (log(N))^2 / N^{1/3}.  (7.6)

In the above theorem, we can see that the convergence rate is independent of d, such that the curse of dimensionality is mitigated. The constant C might depend on the Barron norm of u, and its dependence on d might therefore not be exactly clear.

# Example 7.5 (scalar conservation law).

Using Theorem 5.10 and the above bound on the generalization gap, we can prove the following rigorous upper bound (De Ryck et al. 2024c, Corollary 3.10) on the total L^1-error of the weak PINN, which we denote as

ℰ(θ) = ∫_D |u_θ(x,T) − u(x,T)| dx.  (7.7)