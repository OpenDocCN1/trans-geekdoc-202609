
## Definition 13.

Let a gradation graph $G = (V,E)$ be given. We call *path of $G$* any sequence of the form $(v_0, ..., v_n)$, $n \in \mathbb{N}$, $v_0, ..., v_n \in V$, such that there exists no $v \in V$ with $(v, v_0) \in E$ and for all $i < n$, $(v_i, v_{i+1}) \in E$. We denote by $\mathrm{Paths}(G)$ the set of paths of $G$.

## Property 14.

Let a gradation graph $G = (V,E)$ be given.

- *The multiplicity of 1 in V is equal to 1.*
- *Every member of Paths(G) starts with 1.*
- *Every member of V occurs in some member of Paths(G).*

A gradation graph can be “unfolded” and turned into at least one gradation tree, with Figures 7.6 and 7.5 as an example (for this specific example, the “unfolding” is unique). This is what is expressed in the proposition and definition that follow.

## Definition 15.

Let a gradation graph $G = (V,E)$ be given. Set $|E| = n$. We call *presentation of $G$* any enumeration of $E$ such that for all $v, w, w' \in V$ with $(v, w) \in E$ and $(v, w') \in E$, if there exists a member of $\mathrm{Paths}(G)$ that ends in $(w, w')$ then $(v, w)$ occurs before $(v, w')$ in the enumeration.

## Proposition 16.

Let an $\mathscr{M}$-embedding $\mathfrak{E}$, an $\mathfrak{E}$-gradation graph $G = (V,E)$, and a presentation of $G$ be given. Map each $\sigma \in \mathrm{Paths}(G)$ to a finite sequence $[\sigma]$ of members of $\{\vee, \wedge\} \times V$, as follows. Set $[(\wedge, \emptyset)] = ()$. Given $\sigma \in \mathrm{Paths}(G)$ of the form $(v_0, ..., v_n)$, $n > 0$, define $[\sigma]$ as

$((\wedge, w_1^0), (\vee, w_1^1), ..., (\vee, w_1^{k_1}), ..., (\wedge, w_n^0), (\vee, w_n^1), ..., (\vee, w_n^{k_n}))$,

$k_1, ..., k_n \in \mathbb{N}$, where for all nonzero $i \le n$, $(w_i^0, ..., w_i^{k_i})$ is the longest sequence of members of $V$ such that $w_i^{k_i} = v_i$ and $(v_{i-1}, w_i^0), ..., (v_{i-1}, w_i^{k_i})$ all occur in $E$, in this order in the given presentation of $G$. Then $\{ [\sigma] \mid \sigma \in \mathrm{Paths}(G) \}$ is an $\mathfrak{E}$-gradation tree.

## Proof.

This is easily verified using the left-child, right-sibling representation of the tree defined by the closure of $\mathrm{Paths}(G)$ under subsequences.

## Definition 17.

Let a gradation graph $G$ be given.

Given a presentation $\mathscr{R}$ of $G$, we say of the gradation tree defined in Proposition 16 from $G$ and $\mathscr{R}$ that it is *determined by $G$ and $\mathscr{R}$*.

We say of a gradation tree that it is *determined by $G$* if it is determined by $G$ and one of $G$'s presentations.

## Example 18.

Recall the convention and notation in Examples 10 and 12. The gradation graph $G$ defined in the latter determines a unique gradation tree $T$, which is the one defined in the former. Based on the unique presentation of $G$, Proposition 16 maps each $\sigma \in \mathrm{Paths}(G)$ to a member $[\sigma]$ of $T$. Figure 7.7 shows $\sigma$ and $\widehat{[\sigma]}$ for all $\sigma \in \mathrm{Paths}(G)$.

| σ | [σ̂] |
|---|---|
| (∧ ∅) | ∧ ∅ |
| (∧ ∅, r) | p ∨ q ∨ r |
| (∧ ∅, q) | p ∨ q |
| (∧ ∅, q, r) | p ∨ (q ∧ r) |
| (∧ ∅, p) | p |
| (∧ ∅, p, r) | p ∧ (q ∨ r) |
| (∧ ∅, p, q) | p ∧ q |
| (∧ ∅, p, q, r) | p ∧ q ∧ r |

### Figure 7.7

## Definition 19.

Given a gradation tree T, the depth of T is defined as the largest integer n such that there exists a member σ of T that has n + 1 elements of the form (∧, v).

Given a gradation graph G, the depth of G is defined as max_{σ ∈ Paths(G)} |σ|.

## Property 20.

Given a gradation graph G and a gradation tree T that is determined by G, the depth of G equals the depth of T.

Except-nodes shrink a set of models, elif-nodes expand it. It turns out that the branches of an RDR tree are associated with sets of models that make up a chain under inclusion (that is, the sets ℰ(σ) with σ ranging over an ℰ-gradation tree form a chain under inclusion). The strict order relation defined in Lemma 21 is designed to order the branches of a gradation tree accordingly, from the branch associated with the smallest set of models, to the branch associated with the largest set of models. Such is the contents of Proposition 29—a consequence of Lemma 27.

## Lemma 21.

Let a gradation tree T be given. Let ≺ be the binary relation on T such that for all σ, τ ∈ T, σ ≺ τ iff σ ≠ τ and

- either τ is the empty sequence, or
- σ is of the form τ · ((∧, v)) · τ', or
- τ is of the form ((𝔛₀, 𝔳₀),..., (𝔛ₙ, 𝔳ₙ)), n ∈ ℕ, and there exists m < n with 𝔛_{m+1} = ∨ such that σ is of the form ((𝔛₀, 𝔳₀),..., (𝔛_m, 𝔳_m)) · σ' with σ' being either empty or of the form ((∧, v)) · σ''.

Then ≺ is a total strict order on T.

*Proof.* Let nonempty σ₁, σ₂, σ₃ ∈ T be such that σ₁ ≺ σ₂ ≺ σ₃. Write σ₃ as ((𝔛₀, 𝔳₀),..., (𝔛ₙ, 𝔳ₙ)), n ∈ ℕ.

- Suppose that σ₂ is of the form σ₃ · ((∧, v)) · σ.
- If σ₁ is of the form σ₂ · ((∧, v)) · σ' then there exists a sequence σ'' such that σ₁ is σ₃ · ((∧, v)) · σ'', hence σ₁ ≺ σ₃.

- Write σ₂ as ((𝕏'₀,𝕧'₀),..., (𝕏'ₚ,𝕧'ₚ)), p > n. If there exists m < p with 𝕏'ₘ₊₁ = ∨ and a sequence σ' such that σ₁ is ((𝕏'₀,𝕧'₀),..., (𝕏'ₘ,𝕧'ₘ))·σ' with σ' being either empty or of the form ((∧, v'))·σ'', then either m > n, in which case there exists a sequence τ such that σ₁ is σ₃·((∧, v))·τ, hence σ₁ ≺ σ₃, or m < n, in which case σ₁ is ((𝕏₀,𝕧₀),..., (𝕏ₘ,𝕧ₘ))·σ', hence σ₁ ≺ σ₃ again.
- Suppose that there exists m < n with 𝕏ₘ₊₁ = ∨ and there exists a sequence σ being either empty or of the form ((∧, v))·σ' such that σ₂ is ((𝕏₀,𝕧₀),..., (𝕏ₘ,𝕧ₘ))·σ.
- If σ₁ is of the form σ₂·((∧, v))·τ then there exists a sequence τ' of the form ((∧, v'))·τ'' such that σ₁ is ((𝕏₀,𝕧₀),..., (𝕏ₘ,𝕧ₘ))·τ', hence σ₁ ≺ σ₃.
- Write σ₂ as ((𝕏'₀,𝕧'₀),..., (𝕏'ₚ,𝕧'ₚ)), p ≥ m. If there exists k < p with 𝕏'ₖ₊₁ = ∨ and a sequence τ such that σ₁ is ((𝕏'₀,𝕧'₀),..., (𝕏'ₖ,𝕧'ₖ))·τ with τ being either empty or of the form ((∧, v'))·τ', then either k ≥ m, in which case there exists a sequence γ being either empty or of the form ((∧, v))·γ' such that σ₁ is ((𝕏₀,𝕧₀),..., (𝕏ₘ,𝕧ₘ))·γ, hence σ₁ ≺ σ₃, or k < m, in which case σ₁ is ((𝕏₀,𝕧₀),..., (𝕏ₖ,𝕧ₖ))·τ, hence σ₁ ≺ σ₃ again.

We conclude that in all cases, σ₁ ≺ σ₃, hence ≺ is transitive.

Let distinct σ, τ ∈ T be given.

- If σ is of the form τ·((∧, v))·τ' then σ ≺ τ.
- If τ is of the form σ·((∨, v))·σ' then σ ≺ τ.
- If there exists a sequence γ such that σ and τ are of the form γ·((∧, v))·σ' and γ·((∨, v))·τ', respectively, then σ ≺ τ.

We conclude that for all distinct σ, τ ∈ T, either σ ≺ τ or τ ≺ σ, thereby completing the proof of the lemma.

The notation that follows won’t be used before Section 7.5 but Example 23, first meant to illustrate the strict order relation defined in Lemma 21, illustrates that notation as well.

## Notation 22.

Let a gradation tree T and σ ∈ T be given. Let X be the set of all elements v such that some initial segment τ of σ ends in (∨,v) or (∧,v) and τ ⊀ σ with ≺ as defined in Lemma 21. We let σ̂ denote ∧X.

## Example 23.

Figure 7.8 represents a member τ of a gradation tree T, as the path that ends at the blue dot.

- With ≺ defined as in Lemma 21, the members σ of T such that σ ≺ τ correspond to the paths that end at a green dot as well as the strict extensions to the right, if any, of the paths that end at a green or blue dot.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_147_0.png)

### Figure 7.8

- σ̂, defined in Notation 22, is a conjunction over a set whose members correspond to the red and blue dots.

## Notation 24.

Given a gradation tree T, we denote by ρ_T the mapping of domain {1,...,|T|} that maps each i ∈ dom(ρ_T) to the i-th member of T w.r.t. the total strict order on T defined in Lemma 21. We sometimes tacitly assume that dom(ρ_T) is rather {0,...,|T|}, in which case ρ_T(0)=0.

## Definition 25.

Given a gradation tree T, we refer to (ρ_T(i))_{1≤i≤|T|} as T's standard enumeration.

## Example 26.

Figure 7.9 represents the standard enumeration of a gradation tree T of size 16. Each number refers to ρ_T^{-1}(σ), as defined in Notation 24, for the corresponding member σ of T.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_147_1.png)

### Figure 7.9
