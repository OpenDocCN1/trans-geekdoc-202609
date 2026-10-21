+   2. From Q construct the transition matrix P of equation (46.2) of the associated jump chain.
+   3. Set an initial probability vector ψ over S, and compute the probability vector π₀ᴶ = ψ (P+P²+P³)/3.
+   4. The computation proceeds recursively. At step n, compute πₙᴶ = πₙ₋₁ᴶ P³.
+   5. The computation stops when two successive vectors, πₖ₋₁ᴶ and πₖᴶ are “sufficiently close” in some sense, yielding the approximation π̂ᴶ = πₖᴶ for the equilibrium pmf πᴶ of the jump chain.
+   6. Compute an approximate equilibrium pmf π̂ of the equilibrium pmf π by substituting π̂ᴶ into equation (46.13).

A number of implementation details for Algorithm 46.1 are worth mentioning: (1) the transition matrix Q is typically a sparse matrix, and thus the implementation can use sparse matrix techniques; (2) in trying out initial probability vectors in Step 3 of Algorithm 46.1, we settled on ψ = (1,0,...,0) which had the best computational performance; (3) the stopping criterion in Algorithm 46.1 was to stop when the maximum norm of πₖᴶ − πₖ₋₁ᴶ dropped below 10⁻⁶ for the first time.

# 46.5 Cash Conversion Cycle

In our model, the CCC is the sojourn time of a PEMU from the moment it transitions from the available funds node to the inventory node up until the same PEMU transitions from the receivables node back to the available funds node. Thus, the CCC is the duration random variable T_C, defined by

T_C = T_I + T_R,  (46.15)

where T_I is the random sojourn time of the PEMU in the inventory node and T_R is the random sojourn time of the PEMU in the receivables node. We assume that PEMUs are queued FIFO in the inventory node and move sequentially in that order to the receivables node, while in the receivables node, PEMUs move independently in parallel. We now proceed to obtain the equilibrium densities f_{T_I} and f_{T_R}, and then derive the statistics of T_C.

To compute f_{T_I}, we need to derive the equilibrium pmf of the embedded inventory size just after a replenishment. In our case, the cash conversion process {(I(t),C(t),R(t)) : t ≥ 0} is embedded at the occurrence times {τ_i^Θ : i ≥ 1} of transitions of the form (u,s) = ((n−1,k+1,j),(n,k,j)). Accordingly, define the corresponding transition set by

Θ = {((n−1,k+1,j),(n,k,j)) : (n−1,k+1,j),(n,k,j) ∈ S},  (46.16)