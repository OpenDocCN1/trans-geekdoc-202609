![](bbox=[0.2, 0.1, 0.82, 0.42])

# FIGURE 16.5: Stinson composition

Let α = Prob(y₁ = y₂). We have P ≤ α + (1 − α)ε₂, which we denote by h(α). As h′(α) = 1 − ε₂ ≥ 0 and α ≤ ε₁ by the defining property of 𝒜₁, we obtain P ≤ h(ε₁), which is our claim.

This construction technique can be used to obtain rather efficient authentication codes. It turns out that, by increasing the security parameter ε only slightly above its theoretical minimum, ε-SU hash families can be obtained with a dramatically smaller number of mappings (keys). We call this effect as the Wegman-Carter effect, as it was first observed in their joint papers [43, 218].

Let us apply Stinson composition Theorem 16.32 with the OA of Theorem 16.29 in the role of 𝒜₂. We know that 𝒜₁, an ε₁-U hash family, is equivalent to an error-correcting code. In particular, the Reed-Solomon code ℛ𝒮(k, q) yields a (q, qᵏ)q hash family which is (k − 1)/q universal.

Stinson composition, using as ingredients Reed-Solomon codes and the OA from Theorem 16.29 (which are themselves very closely related to Reed-Solomon codes), yields interesting strongly universal hash families:

# 16.33 Theorem.

Let q be a prime-power and a ≥ b. There is a (q^{2a+b}; q^{a q^{a-b}})_{q^b} hash family which is 2q^{-b} SU.

**PROOF** ℛ𝒮(q^{a-b}, q^{a}) yields a (q^{a}, q^{a q^{a-b}})_{q^{a}} hash family which is ε₁-U. Here ε₁ = (q^{a-b} − 1)/q^{a} < q^{-b}. An OA from Theorem 16.29 yields a (q^{a+b}, q^{a})_{q^{b}} hash family which is q^{-b}-U. The composition has q^{2a+b} members. Its ε-value as a strongly universal family is ε ≤ ε₁ + q^{-b} < 2q^{-b}.

Here is an example to illustrate: