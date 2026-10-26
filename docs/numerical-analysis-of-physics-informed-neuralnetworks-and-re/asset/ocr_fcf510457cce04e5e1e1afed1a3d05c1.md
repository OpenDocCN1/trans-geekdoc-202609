Based on this result one can prove that u is Sobolev-regular, that is, u ∈ H^k(D × [0,T]) for some k ∈ ℕ, provided that r is large enough (De Ryck, Jagtap and Mishra 2024a).

# Corollary 4.8.

If k ∈ ℕ and u0 ∈ H^r(T^d) with r > d/2 + 2k and div u0 = 0, then there exist T > 0 and a classical solution u to the Navier–Stokes equation such that u ∈ H^k(T^d × [0,T]), ∇p ∈ H^{k-1}(T^d × [0,T]) and u(t = 0) = u0.

Combining this regularity result with Theorem 4.4 then gives rise to the following approximation result for the Navier–Stokes equations (De Ryck et al. 2024a, Theorem 3.1).

# Theorem 4.9.

Let n ≥ 2, d,r,k ∈ ℕ, with k ≥ 3, and let u0 ∈ H^r(T^d) with r > d/2 + 2k and div u0 = 0. Let T > 0 be the time from Corollary 4.8 such that the classical solution of u exists on T^d × [0,T]. Then, for every N > 5, there exist tanh neural networks \widehat{u}_j, 1 ≤ j ≤ d, and \widehat{p}, each with two hidden layers, of widths

3⌈(k + n - 2)/2⌉\binom{d + k - 1}{d} + ⌈TN⌉ + dN  and  3⌈(d + n)/2⌉\binom{2d + 1}{d}⌈TN⌉N^d,

such that

‖(\widehat{u}_j)_t + \widehat{u}·∇\widehat{u}_j + (∇\widehat{p})_j - νΔ\widehat{u}_j‖_{L^2(Ω)} ≤ C1 ln^2(βN) N^{-k+2},  (4.6)
‖div \widehat{u}‖_{L^2(Ω)} ≤ C2 ln(βN) N^{-k+1},  (4.7)
‖(u0)_j - \widehat{u}_j(t = 0)‖_{L^2(T^d)} ≤ C3 ln(βN) N^{-k+1},  (4.8)

for every 1 ≤ j ≤ d, and where the constants β, C1, C2, C3 are explicitly defined in the proof and can depend on k, d, T, u and p but not on N. The weights of the networks can be bounded by O(N^γ ln(N)), where γ = max{1, d(2 + k^2 + d)/n}.

# 4.2. Second general result

Combining results such as Theorem 4.3 or Theorem 4.4 with Assumption 4.1 thus allows us to prove that the generalization error ℰ_G can be made arbitrarily small, thereby answering Question 1. There is, however, still room for improvement.

+   - For many model classes the main results available only state that the error ‖u - u_θ‖_{L^q} can be made small. Is there a way to infer that if ‖u - u_θ‖_{L^q} is small then ‖u - u_θ‖_{W^{k,q}} is also small (under some assumptions)?
+   - Both Theorem 4.3 and Theorem 4.4 suffer from the curse of dimensionality (CoD), meaning that the number of parameters needed to reach an accuracy of ε scales exponentially with the input dimension d, namely as ε^{-(s - k)/d}. Unless s ≈ k + d, this will mean that an infeasibly large number of parameters is needed to guarantee a sufficiently small generalization error. Experimentally, however, we have observed for many PDEs that the CoD can be overcome. This raises the following question: Can we improve upon the approximation results stated in this section?