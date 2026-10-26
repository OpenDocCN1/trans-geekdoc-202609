may have multiple accepting paths. In some applications, the score for the input is aggregated across all such paths. Such aggregate scores can be computed by generalizing WFSAs with **semiring notation**, first introduced in § 7.7.3.

Let d(π) represent the total score for path π = t₁, t₂, …, tₙ, which is computed as,

d(π) = λ(from-state(t₁)) ⊗ δ(t₁) ⊗ δ(t₂) ⊗ ⋯ ⊗ δ(tₙ) ⊗ ρ(to-state(tₙ)).  [9.8]

This is a generalization of Equation 9.5 to semiring notation, using the semiring multiplication operator ⊗ in place of addition.

Now let s(ω) represent the total score for all paths Π(ω) that consume input ω,

s(ω) = ⨁₍π∈Π(ω)₎ d(π).  [9.9]

Here, semiring addition (⊕) is used to combine the scores of multiple paths.

The generalization to semirings covers a number of useful special cases. In the log-probability semiring, multiplication is defined as log p(x) ⊗ log p(y) = log p(x) + log p(y), and addition is defined as log p(x) ⊕ log p(y) = log(p(x) + p(y)). Thus, s(ω) represents the log-probability of accepting input ω, marginalizing over all paths π ∈ Π(ω). In the **boolean semiring**, the ⊗ operator is logical conjunction, and the ⊕ operator is logical disjunction. This reduces to the special case of unweighted finite state acceptors, where the score s(ω) is a boolean indicating whether there exists any accepting path for ω. In the **tropical semiring**, the ⊕ operator is a maximum, so the resulting score is the score of the best-scoring path through the WFSA. The OpenFST toolkit uses semirings and polymorphism to implement general algorithms for weighted finite state automata (Allauzen et al., 2007).

# **Interpolated n-gram language models**

Recall from § 6.2.3 that an **interpolated n-gram language model** combines the probabilities from multiple n-gram models. For example, an interpolated bigram language model computes the probability,

p̂(wₘ | wₘ₋₁) = λ₁p₁(wₘ) + λ₂p₂(wₘ | wₘ₋₁),  [9.10]

with p̂ indicating the interpolated probability, p₂ indicating the bigram probability, and p₁ indicating the unigram probability. Setting λ₂ = (1 − λ₁) ensures that the probabilities sum to one.

Interpolated bigram language models can be implemented using a non-deterministic WFSA (Knight and May, 2009). The basic idea is shown in Figure 9.4. In an interpolated bigram language model, there is one state for each element in the vocabulary — in this