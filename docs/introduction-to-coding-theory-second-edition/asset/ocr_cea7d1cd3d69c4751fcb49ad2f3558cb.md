# 14.2 Covering radius

and its relation to lengthening. Applications of covering codes.

# Lengthening and the covering radius

The following parameter is important in its own right:

14.6 Definition. The covering radius ρ(C) of the code C is the smallest number ρ such that every n-tuple in the ambient space 𝔽_q^n has distance ≤ ρ from some codeword.

Expressed in different words: the covering radius is the smallest number ρ such that the balls of radius ρ centered at the codewords cover all 𝔽_q^n. Yet another way of expressing this: each coset C + x of C contains a vector of weight ≤ ρ. It follows that ρ is the maximum among the weights of coset leaders (compare Section 3.7).

Yet another description of the covering radius involves the check matrix H of C, a matrix with n − k rows and n columns. Recall that the syndrome vector σ is defined by σ(x) = x H^t ∈ 𝔽_q^{n−k}, where we think of x ∈ 𝔽_q^n as a row vector. The coordinates of σ(x) are the dot products with the rows of H. All these dot products vanish if and only if x ∈ C. We have σ(x) = σ(x') if and only if x, x' are in the same coset (we know all this from Section 3.7). How can we read off the covering radius after applying σ? Let z ∈ 𝔽_q^{n−k}; write z = σ(x). We can find x' of weight ≤ ρ such that z = σ(x'). This shows that z is a linear combination of at most ρ columns of H. It is clear that the reverse is also true.

# 14.7 Theorem. For an [n,k]_q code C, the following are equivalent:

+   - The balls of radius i cover all 𝔽_q^n.
+   - Each coset of C contains a vector of weight ≤ i.
+   - Each vector in 𝔽_q^{n−k} can be written as a linear combination of at most i columns of a check matrix of C.

The covering radius ρ is the smallest number i satisfying the equivalent conditions in Theorem 14.7. The concept of the covering radius represents an idea which is different from what we have seen thus far. It is not an intrinsic parameter of the code, like the dimension, minimum distance and strength.