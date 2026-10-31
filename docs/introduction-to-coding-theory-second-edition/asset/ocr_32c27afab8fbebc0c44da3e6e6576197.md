in the permutation sense (see Proposition 18.13). In the case when u = 3, Proposition 18.39 shows that the code is a quaternary linear constacyclic code.

This shows that, in the quaternary case, the full theory of additive constacyclic codes does not produce anything useful, as in each case we are reduced to a more elementary theory, either quaternary linear constacyclic or additive and cyclic in the permutation sense.

# 18.3 Additive quaternary codes: The geometric approach

The geometric approach to linear codes was used in Chapter 17, where we saw that a linear q-ary k-dimensional code of length n may be equivalently described by a multiset of n points in the projective geometry PG(k − 1, q). The minimum distance and in fact the weights of codewords are determined by the distribution of the points on hyperplanes.

Consider now a q-linear q^m-ary code [n,k]_{q^m} as in Definition 18.1. It is obvious that this may be equivalently described by a multiset of n subspaces PG(m − 1, q) in PG(k − 1, q). Here it is to be observed that those subspaces may also degenerate to subspaces of smaller dimension. In the present section we specialize to the quaternary case.

# 18.41 Theorem. The following are equivalent:

+   - a quaternary additive [n,k]₄ code.
+   - a multiset of n lines (the codelines, which may degenerate to points) in PG(2k − 1,2).

Here the codewords are in bijection with the hyperplanes, and a codeword has weight w if and only if the corresponding hyperplane contains all but w of the codelines.

**PROOF** This is harder to state than to prove. Start from the code and describe it by a generator matrix. Observe that the code has binary dimension 2k. Each of the n coordinate pairs yields a pair of points in PG(2k − 1,2). Consider the multiset of lines thus obtained. These are the codelines. A hyperplane H yields a codeword with zero entry in the section described by codeline L_i if and only if L_i ⊂ H.

The strength of this code (equal to the minimum distance of the dual minus 1) is the largest number t such that each t codelines is in general position,