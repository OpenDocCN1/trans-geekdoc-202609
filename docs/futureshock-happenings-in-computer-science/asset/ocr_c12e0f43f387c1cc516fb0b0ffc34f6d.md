# Definition 9.

Let an 𝓜-embedding ℰ = (h,A) be given. An ℰ-gradation tree is a nonempty finite set T of sequences with the following properties.

+   - T is closed under subsequences.
+   - For all σ ∈ T, every member of σ is of the form (∨, v) or (∧, v) for some v ∈ A.
+   - For all σ ∈ T, there is at most one v ∈ A with σ · ((∨, v)) ∈ T, and there is at most one v ∈ A with σ · ((∧, v)) ∈ T.
+   - {ℰ(ρ̂) | ρ ∈ T} \ {∅} has cardinality |T|.

A gradation tree (over 𝓜) is an ℰ-gradation tree for some 𝓜-embedding ℰ.

# Example 10.

Recall the convention and notation in Example 3. The closure of

(( (∧,p), (∧,q), (∧,r) ), ((∧,p),(∧,q),(∨,r)),
((∧,p),(∨,q),(∧,r)), ((∧,p),(∨,q),(∨,r)))

under subsequences is an 𝓐-gradation tree. It can be depicted as in Figure 7.5, with vertical links for pairs of the form (∨, v) and horizontal links for pairs of the form (∧, v).

![](bbox=[0.35, 0.55, 0.75, 0.75])

# Figure 7.5

The evaluation of the conditions of the visited nodes of an RDR tree proceeds deterministically. Indeed, the nodes of a chain of elif nodes (a chain of possible alternatives) are to be evaluated in sequence. Evaluation stops at the first node in the chain, if any, whose condition evaluates to True. Usually, order matters; the order of alternatives cannot be changed, or at the very least it cannot be changed arbitrarily. It is interesting to consider the case where any chain of alternatives can be shuffled, in any way. This amounts to a non-deterministic RDR framework: it allows one to, at a given node, evaluate in parallel all possible alternatives and move to the node, if any, whose condition has first been found out to evaluate to True. This non-deterministic RDR framework starts with the definition that follows, that introduces the key concept of a gradation graph. We will then see how a gradation graph can be transformed into one or more gradation trees. Intuitively, the more gradation trees can be obtained