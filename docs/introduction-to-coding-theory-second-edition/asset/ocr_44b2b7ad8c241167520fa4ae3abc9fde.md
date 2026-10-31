Now we obtain an upper bound on |S|. Let 0 ≠ λ ∈ 𝔽_q and 0 ≠ y ∈ V. Consider the complex number U(λ)_y = ∑_{a∈A} ζ^{T((λa)·y)}. Let u(λ)_y = |U(λ)_y|.

Define a real vector u(λ) of length Q − 1 whose coordinates are parametrized by the 0 ≠ y ∈ V, the corresponding entry being u(λ)_y. We have S = ∑_{y≠0} U(λ1)_y U(λ2)_y U(λ3)_y, in particular, |S| ≤ ∑_{y≠0} u(λ1)_y u(λ2)_y u(λ3)_y.

What do we know about the real vectors u(λ)? A calculation similar to the determination of S shows that we know the length of these vectors: ‖u(λ)‖² = |A|(Q − |A|).

The combinatorial information is in the following lemma, an upper bound on the entries u(λ)_y :

# 17.58 Lemma. Let 0 ≠ λ ∈ 𝔽_q and 0 ≠ y ∈ V. Then u(λ)_y ≤ q C_{k−1}(q) − |A| = c_{k−1}(q) Q − |A|.

PROOF As λA is a cap, we can assume λ = 1. Denote by ν_c the number of elements a ∈ A such that a·y = c. As the v ∈ V satisfying v·y = c form a subspace AG(k−1,q) (see Exercise 17.3.6), we have ν_c ≤ C_{k−1}(q). It follows that u(λ)_y = |∑_{c∈𝔽_q} ν_c ζ^{T(c)}| = |∑_{c∈𝔽_q} (C_{k−1}(q) − ν_c) ζ^{T(c)}| (here we use again that the sum of all powers of ζ vanishes) ≤ ∑_c (C_{k−1}(q) − ν_c) = q C_{k−1}(q) − |A|.

Now we can obtain an upper bound on |S|, using the bound from the preceding lemma and the classical Cauchy-Schwartz inequality. The best known version of this inequality states that for real vectors x = (x1,…,xn), y = (y1,…,yn), we have |x·y| ≤ ‖x‖‖y‖.

Recall that the proof of the Plotkin bound made use of a consequence of this inequality; see Chapter 9. We have |S| ≤ (c_{k−1}(q) Q − |A|)(|A|(Q − |A|)). Comparison of this upper bound and the precise value of |S| yields the following bound on C_k(q), which is the main result in this subsection.