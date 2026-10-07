# Categorical Deep Learning

**Corollary G.11.** The functor Lax-AlgMnd(Para(T)) → CoMon(C) × Lax(→, C) which takes algebras for Para(T) to the pair of the underlying comonoid and the C-morphism which interprets the parametric structure map is full-and-faithful.

*Proof.* The proof is formal and left to the reader.

**Conjecture G.12.** Given a cartesian category (M, ×1), an M-category (C, ►), and a strong endofunctor F on C such that F and C satisfy the hypotheses of Theorem B.16, then the assignment of a algebra (X, (P, f)) to

```
X, (P,f): P → 1, A: P → P × P, laxlim ∘ Para(F,f) ∘∘ Para(Fⁿ)(P,f) : FⁿX → X)
```

defines an equivalence of categories Lax-AlgMnd(Para(F)) → Lax-AlgMnd(Fⁿ)

# H. Tying Examples from Geometric Deep Learning

# H.1. Examples Linear equivariant for pair of pixels.

**Example H.1** (Linear equivariant for a pair of pixels). Consider the category Vect of finite-dimensional vector spaces and linear maps. For simplicity, we assume that the carrier for our data is R², which is a pair of pixels. It is well known that this function can be represented as a multiplication with a 2x2 matrix W

| w1 w2 |
| w3 w4 |

Now consider the induction (Z₂, +, 0)—which can be made to cover this pixel swaps—and the induced action on R², if f : R² → R² is equivariant with respect to →, then for any [x1, x2] ∈ R² it must hold that

| w1x2 + w2x1 | | w3x1 + w4x2 |
| w3x2 + w4x1 | | w1x1 + w2x2 |

(11)

This implies that w3 = w2 and w4 = w1, meaning W is of the form

| w1 w2 |
| w2 w1 |

where the weights make the matrix a symmetric. Any one neural network fw satisfying this constraint will be a linear translation equivariant layer over Z₂, which can be used as a building block to construct geometric deep learning architectures.

**Remark H.2** (Circulants and Nodes). Note that this can be used to generate larger inputs (e.g. Rᵏ for k > 2). Generally, it is a well-known fact in signal processing, for fw to satisfy a linear translation equivariant constraint, W must be a circulant matrix. Circulant matrices are known in neural networks as convolutional layers, the essence of modern CNNs (Fukushima et al., 2013; LeC et al., 1998).

**Example H.3** (Invariant maps) are also (G × X)-algebrahomomorphisms where the codomain is a trivial group action. Specifically, sending to the domain of any of the examples from Example 2, the corresponding induced commutative diagram is:

```
G × Rⁿ××A  Gf  G × Rⁿ××A
|               |
|               |
Rⁿ××A f Rⁿ××A
```

Elementwise, the commutativity of that diagram equals the equation

```
f(g ► x) = f(x)
```

The translation example, for instance, recovers the equation f((i',j') ► x(i,j)) = (i',j') ► f(i,j) which reduces to f(i-i', j-j') = f(i,j). Intuites that, for any displacement (i',j'), the result of translating the input by (i',j') and then applying the function f is the same as just f.

25