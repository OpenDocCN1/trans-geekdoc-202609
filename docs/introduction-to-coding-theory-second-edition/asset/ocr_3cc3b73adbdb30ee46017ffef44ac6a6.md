We will have to choose |C| linearly independent among these vectors. If this is done for each cyclotomic coset avoiding Ã, the corresponding words v(l, −i) form the rows of a generator matrix.

# 13.19 Theorem.

Let v(l, i) ∈ 𝔽_q^n be the word with entry tr(ε^l β^i) in coordinate β ∈ W.

For each cyclotomic coset C, choose a representative i ∈ C and a set S(i) ⊆ {0,1,…,r−1} of |C| indices l such that the v(l,i), l ∈ S(i) are linearly independent. The v(l,i), l ∈ S(i) are a basis of tr(ℬ(C)).

The v(l,−i), l ∈ S(−i) where i varies over representatives of cyclotomic cosets C avoiding Ã, form the rows of a generator matrix of 𝒞(A).

Again, the generator matrices as described in Theorem 13.19 are close to being canonically determined. There is the choice of the representatives of cyclotomic cosets, but this does not really matter. When C has full length r, and this is the generic case, we have S(i) = {0,1,…,r−1}. A difficulty arises only when C is shorter.

# Check matrices of cyclic codes

It is important to have a concrete representation of a check matrix H of 𝒞(A), equivalently a generator matrix of tr(ℬ(A)) = tr(ℬ(Ã)). Strictly speaking, we know this standard form, as the dual of a cyclic code is cyclic, so H is a generator matrix of a cyclic code and we can apply Theorem 13.19. We are redoing the work of the previous section from a slightly different perspective. The main difference is that we view the entries in each section corresponding to a cyclotomic coset of length s not as s-tuples but as elements of 𝔽_{q^s}.

The Galois closure Ã is a union of cyclotomic cosets. Let R be a set of representatives for the cyclotomic cosets contained in Ã. We know that tr(ℬ(A)) is the direct sum of the tr(ℬ(C_n(i))), where i ∈ R, and dim(tr(ℬ(C(i)))) = |C_n(i)|; in other words, each cyclotomic coset C_n(i) ⊆ Ã contributes s = |C_n(i)| rows of H. It is proved in Exercise 13.2.9 that s can also be described as the degree of 𝔽_q(α^i) over 𝔽_q, equivalently 𝔽_q(α^i) = 𝔽_{q^s}. In particular, α^i ∈ 𝔽_{q^s}. It is now obvious how a check matrix H of 𝒞(A) can be described:

+   1. The columns of H are indexed by β = α^j ∈ W, j = 0,1,…,n−1.
+   2. Choose representatives i ∈ R for the cyclotomic cosets C_n(i) ⊆ Ã. Let s = s(i) = |C_n(i)|. Each i ∈ R contributes a section of s rows to H.
+   3. For each 𝔽_{q^s} ⊆ F, choose a basis over 𝔽_q.
+   4. The section of column β ∈ W corresponding to i ∈ R is β^i, where β^i ∈ 𝔽_{q^s} is represented by a column vector of length s, whose entries are the coefficients of the representation of β^i in terms of the fixed basis.