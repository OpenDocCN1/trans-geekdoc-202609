![](bbox=[0.12, 0.15, 0.92, 0.6])

FIGURE 17.1: The hexacode as point set

Check that 1 + 45 + 18 = 64 = 4³ is the number of codewords, as it has to be.

What can we say about C^⊥? Clearly it is a [6,3]₄ code. The reader was asked in Exercise 4.3 to prove that the dual of a linear MDS code is MDS again. It follows that C^⊥ has parameters [6,3,4]₄, the same as C.

Here is a geometric argument: As C is projective, we have d' = d(C^⊥) ≥ 3. A codeword of weight 3 in C^⊥ would mean that some three of the P_i are linearly dependent, hence on a line. This is not the case. We have d' ≥ 4. Because of the Singleton bound (or because any four columns of the generator matrix are linearly dependent), d' cannot be larger yet, so d' = 4.

Because of duality, the hexacode has strength 3. It is an OA₁(3,6,4).

# Extended RS-codes and normal rational curves

Reconsider Reed-Solomon codes (Chapter 4) from a geometric point of view. As generator matrices we used Vandermonde matrices. The columns of a generator matrix of RS(k,q) generate the points P_u = (1 : u : u² : … : u^{k-1}), where u ∈ F_q. As RS(k,q) is a [q,k,q−k+1]_q code, it follows from Theorem 17.1 that we find at least q − (k − 1) of the points P_u outside each hyperplane. This means that each hyperplane of PG(k−1,q) contains at most k − 1 of these points. On the other hand, any k − 1 points in PG(k − 1,q)