+   - *A pure [[n, n − r, t + 1]]₂ quantum code, and*
+   - *a set of n lines (the codelines) in PG(r − 1, 2) any t of which are in general position and such that, for every secundum S, the number of codelines skew to S is even.*

Recall that a secundum in PG(r − 1, 2) is a subspace of codimension 2 (a hyperplane of a hyperplane).

# **PROOF**

Start from the coding theoretic description. The smaller code Q⊥ has quaternary dimension r/2 and binary dimension r, and can therefore be described by a binary generator matrix H with r rows and n pairs of columns. See the columns as elements in PG(r − 1, 2) and let the codelines be the lines determined by coordinate pairs. The quantum distance is > t if and only if Q⊥ has strength t, equivalently, the projection to any set of t column pairs has binary rank 2t, equivalently, the corresponding t codelines are in general position.

It remains to express the quantum condition (Q⊥ ⊂ Q) in geometric terms. An equivalent condition is: any two rows of the generator matrix H have symplectic product 0. Consider two codewords v₁, v₂ and the hyperplanes H₁, H₂ corresponding to them. Let S = H₁ ∩ H₂ be the corresponding secundum. The coordinate sections corresponding to codelines L that intersect S nontrivially give no contribution to the symplectic product of v₁ and v₂; the others do.

As a first application, use Proposition 18.44 again. A repeated application shows that the points in V_{f+2} \ V_{f−2i} can be partitioned into lines as long as 2i < f. The number of lines in this partial spread is (2^{f+2} − 2^{f−2i})/3. Proposition 18.44 shows that the quantum condition of Theorem 18.59 is satisfied. The strength is 2. Letting l = f+2, we arrive at quantum parameters as follows:

# **18.60 Corollary.**

*Let g_{l,i} = (2^{l} − 2^{l−2i})/3. If l − 2i = 0 or l − 2i ≥ 3, there is a pure [[g_{l,i}, g_{l,i} − l, 3]]₂-quantum code.*

This family contains the so-called quantum Hamming codes and Gottesman codes; see [39], Theorems 10 and 11. Some small examples are

[[5, 1, 3]]₂, [[8, 3, 3]]₂, [[21, 15, 3]]₂, [[40, 33, 3]]₂.

A recursive construction using Corollary 18.46 is also possible; see [32].

In order to simplify further, let us consider the situation when the quaternary code is 𝔽₄ linear. It is, after all, not forbidden for the additive quaternary code to be in fact linear over 𝔽₄. The following characterization is obtained:

# **18.61 Theorem.** *The following are equivalent:*