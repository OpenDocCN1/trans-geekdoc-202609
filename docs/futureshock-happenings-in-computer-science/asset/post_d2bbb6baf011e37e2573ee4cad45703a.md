
## Example 3.

Suppose that 𝔞 consists of three atoms p, q and r and 𝓜 is the set of all interpretations over 𝔞. Define nine (positive) formulas as follows.

- φ₀ = p ∧ q ∧ r
- φ₁ = p ∧ q
- φ₂ = p ∧ (q ∨ r)
- φ₃ = p
- φ₄ = p ∨ (q ∧ r)
- φ₅ = p ∨ q
- φ₆ = p ∨ q ∨ r
- φ₇ = ∧ ∅
- φ₈ = (p ∧ q) ∨ (p ∧ r) ∨ (q ∧ r).

For all i ≤ 8, define Mᵢ as Mod(φᵢ). Set C₁ = {Mᵢ | i < 8} and C₂ = {M₀, M₈, M₆, M₇}. Then C₁ and C₂ are both in ℭ.

Given a chain of models, the member of the chain that is most specific while being consistent with the information at hand is naturally of particular interest. In plain terms, this observation is captured by the notation that follows.

## Notation 4.

Let C ∈ ℭ and 𝔐 ∈ 𝓜 be given. We denote by min_C(𝔐) the ⊆-least member of C that contains 𝔐.

Figure 7.3 illustrates Notation 4.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_139_0.png)

Figure 7.3

## Example 5.

Recall the convention and notation in Example 3. For all 𝔐 ∈ 𝓜, min_{C₁}(𝔐) and min_{C₂}(𝔐) are determined as shown in Figure 7.4.

| ℳ | min_{C₁}(ℳ) | min_{C₂}(ℳ) |
|---|---|---|
| {p, q, r} | M₀ | M₀ |
| {p, q, ¬r} | M₁ | M₈ |
| {p, ¬q, r} | M₂ | M₈ |
| {p, ¬q, ¬r} | M₃ | M₆ |
| {¬p, q, r} | M₄ | M₈ |
| {¬p, q, ¬r} | M₅ | M₆ |
| {¬p, ¬q, r} | M₆ | M₆ |
| {¬p, ¬q, ¬r} | M₇ | M₇ |

Figure 7.4

## 7.4 GRADATION TREES AND GRAPHS

The condition of an RDR tree can be considered semantically, as the set of possible worlds where it holds, or syntactically, as a description in some language meant to be appropriately interpreted. To account for both points of view and avoid formalising concepts twice, we define the notion of an ℳ-embedding, to trivially map an interpretation to itself or to map a syntactic representation to its interpretation. It is natural to abstract interpretations as Boolean algebras (for readers keen to extend the setting and make it first-order, a bounded distributive lattice would be the natural choice). There is also a need to distinguish between the language that lets us work with a whole RDR tree, and the language of conditions of an RDR tree. The former should be naturally closed under negation, disjunction and conjunction—that is the very reason why a Boolean algebra is an appropriate—, while the latter could be much more restricted—for instance, one could naturally demand that conditions be atoms, or positive conjuncts. In the definition that follows, B targets the language of whole RDR trees, whereas A targets the language of conditions of RDR trees.

**Definition 6.** We call ℳ-embedding a pair of the form (h,A) with the following properties.

- h is a homomorphism from a Boolean algebra (B, ∨, ∧, ¬, 0, 1) into 2^ℳ;
- A is a subset of B.

In contexts where there is no risk of confusion, we identify A with (h,A) and use ∨, ∧, ¬, 0 and 1 being tacitly understood that they denote the second to the last members of (B, ∨, ∧, ¬, 0, 1). We also use ≤, <, > and ≥ in reference to the induced partial order on dom(h).

We identify 2^ℳ with the ℳ-embedding (h,2^ℳ) where dom(h) is identical to (2^ℳ, ∪, ∩, ¬, ∅, ℳ) and h is the identity function. Given a set L of formulas, denoting by Ĺ the closure of L under ∨, ∧ and ∼, we identify L with the ℳ-embedding (h,Ĺ) where dom(h) = (Ĺ, ∨, ∧, ∼, ∨∅, ∧∅) and h maps each φ ∈ Ĺ to the set of members of ℳ in which φ is true.

The notation that follows will be used to aggregate the conditions found along the branch of an RDR tree, an except-node introducing a conjunction, an elif-node introducing a disjunction, resulting in a condition for the branch itself. More precisely, a branch of what will be defined as an ℰ-gradation tree, with ℰ an ℳ-embedding, will be a sequence σ of the kind defined in Notation 7; with σ̂ as defined in that notation, the set of models ℰ(σ̂) will be associated to that branch.

## Notation 7. Given a Boolean algebra (B,∨,∧,¬,0,1), we inductively map each finite sequence of members of {∨,∧}×B to a member σ̂ of B, as follows.

- (\widehat{}) = 1.
- For all 𝕏 ∈ {∨,∧} and 𝕧 ∈ B, \widehat{(𝕏,𝕧)} = 𝕧.
- Let 𝕏,𝕏' ∈ {∨,∧}, 𝕧,𝕧' ∈ B, and a finite sequence σ of members of {∨,∧}×B be given. Set σ' = ((𝕏,𝕧),(𝕏',𝕧'))·σ. Then \widehat{σ'} = 𝕧 𝕏' \widehat{((𝕏',𝕧'))·σ}.

## Example 8. Let a Boolean algebra (B,∨,∧,¬,0,1) and members b1,…,b9 of B be given. Set

σ = ((∧,b1),(∨,b2),(∨,b3),(∧,b4),(∧,b5),(∨,b6),(∧,b7),(∧,b8),(∨,b9)).

The ten initial segment τ of σ, considered from smallest to largest, are mapped to the following simplified members τ̂ of B:

- 1
- b1
- b1 ∨ b2
- b1 ∨ b2 ∨ b3
- b1 ∨ b2 ∨ (b3 ∧ b4)
- b1 ∨ b2 ∨ (b3 ∧ b4 ∧ b5)
- b1 ∨ b2 ∨ (b3 ∧ b4 ∧ (b5 ∨ b6))
- b1 ∨ b2 ∨ (b3 ∧ b4 ∧ (b5 ∨ (b6 ∧ b7)))
- b1 ∨ b2 ∨ (b3 ∧ b4 ∧ (b5 ∨ (b6 ∧ b7 ∧ b8)))
- b1 ∨ b2 ∨ (b3 ∧ b4 ∧ (b5 ∨ (b6 ∧ b7 ∧ (b8 ∨ b9))))

The notion of an ℳ-embedding, that, remember, lets us work either purely semantically or syntactically and semantically, with possible restrictions on conditions, is all what is needed to define RDR trees in full generality. We expect an except-node, introducing a conjunction, to truly bring an exception and restrict the set of models, and an elif-node, introducing a disjunction, to truly bring an alternative and broaden the set of models. This justifies the introduction of the last item in the definition that follows.

## Definition 9.

Let an 𝓜-embedding ℰ = (h,A) be given. An ℰ-gradation tree is a nonempty finite set T of sequences with the following properties.

- T is closed under subsequences.
- For all σ ∈ T, every member of σ is of the form (∨, v) or (∧, v) for some v ∈ A.
- For all σ ∈ T, there is at most one v ∈ A with σ · ((∨, v)) ∈ T, and there is at most one v ∈ A with σ · ((∧, v)) ∈ T.
- {ℰ(ρ̂) | ρ ∈ T} \ {∅} has cardinality |T|.

A gradation tree (over 𝓜) is an ℰ-gradation tree for some 𝓜-embedding ℰ.

## Example 10.

Recall the convention and notation in Example 3. The closure of

(( (∧,p), (∧,q), (∧,r) ), ((∧,p),(∧,q),(∨,r)),
((∧,p),(∨,q),(∧,r)), ((∧,p),(∨,q),(∨,r)))

under subsequences is an 𝓐-gradation tree. It can be depicted as in Figure 7.5, with vertical links for pairs of the form (∨, v) and horizontal links for pairs of the form (∧, v).

![](img/35d43ba1274e18d0f2f189e6392aa2e3_142_0.png)

Figure 7.5

The evaluation of the conditions of the visited nodes of an RDR tree proceeds deterministically. Indeed, the nodes of a chain of elif nodes (a chain of possible alternatives) are to be evaluated in sequence. Evaluation stops at the first node in the chain, if any, whose condition evaluates to True. Usually, order matters; the order of alternatives cannot be changed, or at the very least it cannot be changed arbitrarily. It is interesting to consider the case where any chain of alternatives can be shuffled, in any way. This amounts to a non-deterministic RDR framework: it allows one to, at a given node, evaluate in parallel all possible alternatives and move to the node, if any, whose condition has first been found out to evaluate to True. This non-deterministic RDR framework starts with the definition that follows, that introduces the key concept of a gradation graph. We will then see how a gradation graph can be transformed into one or more gradation trees. Intuitively, the more gradation trees can be obtained

from a gradation graph, the more nondeterminism the gradation graph encompasses. Some gradation graphs cannot be transformed in more than one gradation tree, so they are themselves deterministic. Still, they can prove valuable as gradation graphs allow us to get rid of the redundancy that is built into some gradation trees. The tree depicted in Figure 7.5 exhibits redundancy: the two subtrees rooted at q are the same. We will see that this tree is the unique transformation of a gradation graph, the latter offering a more compact representation. There is actually more than one possible way to interpret “redundancy” in a gradation tree. To make sure that the interpretation is general enough and does not require more than finding identical subtrees in an RDR tree, ignoring the “contexts” where those identical subtrees appear, we resort to graphs over multisets rather than sets of vertices. Using formulas (or more generally, members of the lattice that subsumes the ℳ-embedding under consideration) as labels, we could instead consider a set of labelled vertices and possibly label distinct vertices with the same formula, but it is more direct and simpler to work with a multiset of formulas as vertices.

## Definition 11.

Let an ℳ-embedding ℰ = (h,A) be given. An ℰ-gradation graph is a pair of the form (V,E) where V is a multisubset of A ∪ {1} and E is finite nonempty binary relation over V with the following properties.

- For all v ∈ V, v = 1 iff there is no v' ∈ V with (v', v) ∈ E.
- E is acyclic: there exists no n ∈ ℕ and v0,…,vn ∈ V such that (vn, v0) ∈ E and for all i < n, (vi, vi+1) ∈ E.

A gradation graph (over ℳ) is an ℰ-gradation graph for some ℳ-embedding ℰ.

## Example 12.

Recall the convention and notation in Example 3. Let V denote {∧∅, p, q, r} and set:

E = {(∧∅, p), (∧∅, q), (∧∅, r), (p, q), (p, r), (q, r)}.

Then (V,E) is an 𝒜-gradation graph. It can be depicted as in Figure 7.6.

![](img/35d43ba1274e18d0f2f189e6392aa2e3_143_0.png)

Figure 7.6
