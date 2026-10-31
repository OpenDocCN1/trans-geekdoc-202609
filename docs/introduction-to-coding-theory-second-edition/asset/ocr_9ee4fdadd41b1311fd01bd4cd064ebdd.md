elements of the vector space F_q^m). Observe that the dimension k need not be an integer. It can have m in the denominator. This is a natural notation, as it facilitates the comparison with q^m-ary linear codes, which form a subfamily.

One way of thinking of a q^m-ary q-linear code of length n is to see it as a linear code over F_q of length nm, whose coordinates have been grouped into n blocks of m each. One advantage of this point of view is that it shows the use of duality. Define the dual with respect to the dot product on F_q^{nm}. The dual of a k-dimensional q^m-ary q-linear code has complementary dimension n − k.

A generator matrix G of a q-linear [n,k]_q^m code is a (km, n) matrix with entries from E = F_q^m whose rows form an F_q basis of the code (the codewords are the F_q-linear combinations of the rows of G). A check matrix is a generator matrix of the dual code. Observe here that km is of course an integer, but k need not be integer.

So far the main features of the theory of linear codes generalize smoothly to additive codes. This is true of the principle of duality as well. Let C be a q-linear [n,k]_q^m code. The same argument as in the case of linear codes shows that C is an OA of strength t if and only if C^⊥ has minimum weight > t.

In the category of additive codes, it is much easier to go down to smaller alphabets than in the category of linear codes. In the case of linear codes, we are restricted to subfields, and those are rare. For example, a field with 2^p elements, where p is a prime, has only one proper subfield, the prime field F2. In the case of additive codes, the alphabet forms a vector space over the ground field. We can go down to vector spaces of an arbitrary smaller dimension. Here is a simple construction due to C. L. Chen [49] which makes use of this additional degree of liberty:

Let C be a q^m-ary q-linear code [n, k, d]. Application of an arbitrary regular (m, m) matrix in each coordinate yields a code which is equivalent to C. We can therefore assume that C^⊥ contains a word which in each coordinate has as entry either (1,0,...,0) or (0,...,0,0). The q-ary dimension of C is km. Consider the subcode D ⊂ C consisting of those words which vanish in the first position of each coordinate. As there are n conditions to satisfy, we would expect D to have codimension n in C. However, due to the presence of our special word in C^⊥, the last of these n conditions is automatically satisfied. We have dim_q(D) ≥ km − (n − 1). Clearly we can omit this last position in each coordinate and obtain a q^{m−1}-ary q linear code of q^{m−1}-ary dimension ≥ [km−(n−1)]/(m−1) = k − [n−1−k]/(m−1).

# 18.2 Theorem (Chen projection).

If there is a q^m-ary q-linear code [n, k, d] with m > 1, there is a q^{m−1}-ary q-linear code [n, k − (n − k − 1)/(m − 1), d].

Observe that the proof of Theorem 18.2 uses the same argument as construction Y1 for linear codes (see Exercise 5.1.8).

Theorem 18.2 allows us to start from a good q^m-linear code and to derive q^{m−1}-ary, q^{m−2}-ary ... q-linear codes by repeated application of Chen projec-