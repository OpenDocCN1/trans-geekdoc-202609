The construction idea may be described as randomization or uniformization, similar to the construction of the Justesen codes (the idea is also used in the family of Theorem 16.30). Each codeword x ∈ C is blown up to a qn-tuple x̃ whose coordinates are indexed by pairs (i, α), where i is a coordinate of x and α ∈ F_q, the entry being x_i + α. Our hash family is the (qn, q^k)_q array whose columns are the x̃. It is clear that each field element occurs n times as entry in each column. This verifies the first axiom of Definition 16.26

As for the second axiom of Definition 16.26, fix two different columns (codewords) x, y, two not necessarily different entries a, b and count rows (i, α) such that x̃ has entry a and ỹ has entry b in this row. This means x_i + α = a, y_i + α = b, equivalently, (x − y)_i = a − b. The number of such rows is therefore bounded by n − d. It follows that we have an ε-SU array, where ε = 1 − d/n. This proves the following:

# 16.31 Theorem.

Assume there exists a linear [n, k + 1, d]_q code containing the all-1 word. We can construct a (qn, q^k)_q hash family which is (1 − d/n) SU.

Apply Theorem 16.31 to Reed-Solomon codes. As these are [q, k + 1, q − k]_q codes containing 1, we can construct (q^2, q^k)_q hash families, which are q−k/q-SU, for every k ≤ q − 1. However, these parameters are not new to us. They correspond to the special case a = b = 1 of Theorem 16.30.

# Stinson composition

Here is another construction principle for ε-SU hash families, Stinson composition. It is best understood using the language of mappings.

# 16.32 Theorem.

Let A1 be an (N1, n)_m hash family which is ε1 U and A2 an (N2, m)_q hash family which is ε2 SU. The composition A = A2 ∘ A1 is defined as the multiset of compositions f = f2 ∘ f1, where f_i ∈ A_i. Then A is an (N1 N2, n)_q hash family which is ε − SU, where ε = ε1 + ε2 − ε1 ε2 < ε1 + ε2.

# PROOF

As A_i is a multiset of N_i mappings (i = 1,2), it is clear that the multiset A of all compositions consists of N1 N2 mappings. We have that A is an (N1 N2, n)_q hash family. The first condition of Definition 16.26 is satisfied. In order to prove the main condition, we use the language of probabilities. So let x1, x2 in the ground set (x1 ≠ x2) and z1, z2 in the q-set be given. Write f ∈ A as f = f2 ∘ f1, let y1 = f1(x1), y2 = f1(x2) and P = Prob(f(x1) = z1 | f(x2) = z2). We want to show that P ≤ ε1 + ε2 − ε1 ε2. Consider at first the case z1 ≠ z2. We have P ≤ Prob(y1 ≠ y2) ε2 < ε2. The case z1 = z2 is harder:

P ≤ Prob(y1 ≠ y2) ε2 + Prob(y1 = y2).