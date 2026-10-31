# 3.3 Linear codes over finite fields

**Basic concepts:** Minimum distance, generator matrix. Linear combinations, linear independence, dimension, rank, determinant, Gauß elimination.

**3.8 Definition.** *Let* 𝔽_q *be the field with* q *elements. A* q*-ary linear code of length* n *and dimension* k *is a linear subspace* 𝒞 ⊆ 𝔽_q^n *of vector space dimension* k*. If its minimum distance is* d*, then we record the parameters of* 𝒞 *as* [n,k,d]_q*.*

Observe that a q-ary linear code of dimension k has q^k codewords. It contains the all-0 word 0 = (0,0,...,0).

For fixed q we wish to construct codes [n,k,d]_q with large d, large k and small n. Recall that a code with minimum distance d allows the correction of e transmission errors, when 2e < d.

All our basic facts concerning binary linear codes carry over to general linear codes. The first benefit we drew from linearity in the binary case was Proposition 2.5, the reduction from minimum distance to minimum weight.

**3.9 Proposition.** *The minimum distance* d *of a linear code* [n,k,d]_q *equals its minimum weight. Here the weight of a codeword is the number of coordinates with a nonzero entry and the minimum is taken over the nonzero words of the code.*

**PROOF** This is true because each distance between two different codewords is also the weight of some nonzero codeword: d(x,y)=wt(x−y), and x−y is a codeword because the code is linear.

A **generator matrix** G of an [n,k,d]_q-code 𝒞 is a (k,n)-matrix whose rows form a basis of 𝒞. The code 𝒞 is recovered from G by taking all linear combinations of rows. If we compare with the binary case, the sums that we used there have to be replaced by **linear combinations** in the general case. Here is a review of some important terms from linear algebra:

**3.10 Definition.** *Let V be a vector space defined over a field K and v₁,v₂,...,vₘ ∈ V. A linear combination of v₁,...,vₘ is an expression of the form* 

λ₁v₁ + λ₂v₂ + ⋯ + λₘvₘ,