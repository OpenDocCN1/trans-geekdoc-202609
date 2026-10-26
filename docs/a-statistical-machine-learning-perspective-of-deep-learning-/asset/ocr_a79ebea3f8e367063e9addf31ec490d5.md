# Convergence Guarantee

+   - Assumptions
+     - Bridging model
+       - Staleness Synchronous Parallel (SSP) with staleness parameter s
+       - Bulk Synchronous Parallel is a special case of SSP when s = 0
+     - Communication methods
+       - Partial broadcast (PB): sending messages to a subset of Q (Q < P − 1) machines
+       - Full broadcast is a special case of PB when Q = P − 1
+     - Assumption 1. (1) For all j, f_j is continuously differentiable and F is bounded from below; (2) ∇F, ∇F_p are Lipschitz continuous with constants L_F and L_p, respectively, and let L = Σ_{p=1}^P L_p; (3) There exists G, σ² such that for all p and c, we have (almost surely) ||U_p(W_p^c, I_p^c)|| ≤ Gη and 𝔼|| |S_p| Σ_{j∈I_p} ∇f_j(W) − ∇F_p(W) ||_2² ≤ σ².