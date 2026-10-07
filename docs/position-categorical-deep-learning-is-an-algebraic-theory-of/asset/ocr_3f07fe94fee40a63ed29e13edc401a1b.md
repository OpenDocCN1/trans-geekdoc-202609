# Categorical Deep Learning

| Folding recurrent neural network | Unfolding recurrent neural network | Recursive neural network | Full recurrent neural network | 'Moore machine' neural network |

```
$1 + A \times S \quad S \quad A + S^2 \quad S \quad S$$
$$\downarrow \quad \downarrow \quad \downarrow \quad \downarrow \quad \downarrow$$\$
$$(P,cell^{S}) \quad (P,(cell_{i},\cell_{i,1})) \quad (P,cell^{S}) \quad (P,cell^{S}) \quad (P,cell^{more})$$$
$$S \quad O \times S \quad S \quad (I \to O \times S) \quad O \times (I \to S)$
```

![](bbox=[0.096, 0.237, 0.903, 0.303])

Figure 1. (cat)algebras provide a high-level framework for describing computation in neural networks.

the lax algebras are sufficient to derive recursive, recurrent, and similar neural networks from first principles. Notably, morphisms of lax algebras are also expressive enough to capture 1-ocycles, which follow asynchronous neural networks in (Dudzik et al., 2024)—Appendix H.1.

This 2-category is one of the key components in the categorical picture of gradient-based learning (Crutwell et al., 2022). We hypothesize that this is more than true (Appendix I):

Interestingly, this is how any idempotent, recurrent, or strict neural network can generate a full recursive, recurrent neural network is a particular 2-categorical analogue to the story of freely monads on endofunction which we briefly mentioned in Remark 2.3.

It is possible that the 2-category Para provide a formal theory of neural network architectures, establish formal criteria for correctness and design of new architectures.

# 3.2. Dimensional Categorical Algebra

For all examples of construction in Section 2.2, a lax algebra of free algebras(F) is equivalent to a lax algebra for the original endofunction. We obtain Freead(F) by iterating F until it stabilizes, meaning further application of the endofunction does not change the composition. Functional programmers may recognise this from the freedom of free monads in Haskell, while using colimits (Appendix B). One can define a morphism mapping an algebra (A, a) to the Freead(F)-algebra (A, α) where α: F(A) → A.

2-category theory is much richer than 1-categorical. In a 1-category either commute or do not, in which case they serve as a 1-skeleton to 2-morphisms. Any 2-category may have: pseudo-commutative, lax-commutative, or orthomorphic, meaning respectively, that relevant paths are equal, isomorphic, or there is a 2-morphism from one to the other or in one direction. The diagrams below present these four options, with 2-morphisms denoted by double arrows.

![](bbox=[0.118, 0.623, 0.382, 0.703])

In the bi-dimensional case, the relationship between Lax-AlgFreead(F) and Lax-AlgMonad(F) remains and the structure map, not only generating the 1-dimensional monad, but also the 2-cells of the lax algebra for a monad.

To reconcile this with concrete applications, we do not need to study 2-endofunctions and 2-monads on Para. Rather, examples which arise from 1-categorical algebras (group action monads, inductive types, etc.), which are augmented into 2-monads on Para. We prove in G.10, that lax cells of such algebras are actually commonly monads. The fact that we can duplicate or delete entries in vectors—the essence of fitting weights—is the informa

In the long run, we expect that all of these notions will apply to either explaining or specifying, aspects of neural architecture past, present and future. Focusing on just one of them,

> 8 precisely, the construction of Para(.). See Appendix G.

> 9 also called colax.