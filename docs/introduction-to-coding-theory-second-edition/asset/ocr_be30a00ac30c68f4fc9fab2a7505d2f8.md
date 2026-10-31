![](bbox=[0.12, 0.12, 0.88, 0.38])

# FIGURE 14.1: Construction X

Then φ(x) is a nonzero codeword of ℰ, therefore of weight ≥ δ. It follows that wt(̃x) ≥ wt(x) + δ ≥ d + δ in this case.

The best-known application of construction X is the parity check bit for binary codes, Theorem 5.3. It is easy to see that this is indeed an application of construction X; see Exercise 14.1.1. The auxiliary code is the truly trivial code [1,1,1]₂.

The following construction, essentially due to Alltop [1], uses knowledge of a code, two of its subcodes and their intersection:

# 14.2 Theorem (construction XX). Let the following be given:

+   - A code 𝒞 with parameters [n,k,d]q,
+   - two subcodes 𝒞i ⊂ 𝒞, i = 1,2 with parameters [n, k − κi, di]q,
+   - with 𝒞1 ∩ 𝒞2 of minimum distance ≥ D,
+   - auxiliary codes ℰi, i = 1,2 with parameters [li, κi, δi]q.

Then there is a code with parameters

[n + l1 + l2, k, min{D, d2 + δ1, d1 + δ2, d + δ1 + δ2}]q.

**PROOF** Apply Theorem 14.1 to the pair 𝒞 ⊃ 𝒞1. The lengthened codes are 𝒞̃ ⊃ 𝒞̃2. The larger of these has minimum distance ≥ min{d1, d + δ1}. A codeword in 𝒞2 \ (𝒞1 ∩ 𝒞2) obtains a nontrivial lengthening. The corresponding word in the lengthened code has then weight ≥ d2 + δ1. It follows that the minimum weight of 𝒞̃2 is ≥ min{D, d2 + δ1}. We apply Theorem 14.1 again, this time to the pair 𝒞̃ ⊃ 𝒞̃2, with ℰ2 as auxiliary code. This yields the desired code.