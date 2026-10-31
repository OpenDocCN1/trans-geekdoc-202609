
## 13.14 Lemma. If A is independent of S, then A + j is independent of S, for every j.

PROOF Consider the matrix with rows indexed by i ∈ A, columns indexed by u ∈ S and entries u^i. The fact that A and S are independent is equivalent to this matrix having rank |A| (the rows are independent). Replacing A by A + j has the effect of multiplying column u by u^j. The rank remains unchanged.

Choose S to be the support of a codeword of C(A) of minimum weight d, so |S| = d. Let I ⊆ Z/nZ.

## 13.15 Lemma. If I is contained in an interval J ⊆ Ã of length at most d, then I is independent with respect to S.

PROOF As J is an interval, the projection from P(J) to B_S(J) has trivial kernel. If we restrict to the subspace P(I), this is still true.

The following recursive constructions are used to find large independent sets (with respect to any nonzero codeword of the cyclic code). If I is independent with respect to every support S, then |I| is a lower bound on the minimum distance d of C(A). If, moreover, I ⊆ Ã, then d ≥ |I| + 1. This follows from the fact that B_S(I) is contained in a proper subspace of F^S in this case. The recursive construction is based on the following two lemmas.

## 13.16 Lemma (shifting).

dim(B_S(I)) = dim(B_S(I + j))

for every S, I and j. Here I + j = {i + j | i ∈ I}.

In particular: if I is independent with respect to S, then I + j has that same property.

PROOF The mapping p(X) ↦ X^j p(X) induces an isomorphism between B_S(I) and B_S(I + j) for every S.

## 13.17 Lemma. Let I ⊆ Ã, j ∉ Ã. If S is the support of a codeword of C(A) but not the support of a codeword in C(A ∪ {j}), then

dim(B_S(I ∪ {j})) = 1 + dim(B_S(I)).

In particular, if I is independent with respect to S, then so is I ∪ {j}.

PROOF Clearly dim(B_S(I ∪ {j})) ≤ 1 + dim(B_S(I)). The tuple of B_S(I ∪ {j}) defined by polynomial X^j is not orthogonal (with respect to the dot product) to codeword $v \in \mathcal{C}(A)$ with support $S$. This follows from the assumption of the lemma. As the elements of $\mathcal{B}_S(I)$ are orthogonal to $v$, we see that the dimension does increase.

As an illustration, consider the binary Golay code, the binary cyclic code of length 23 with defining set $A = \{1\}$. The cyclotomic cosets in the case $n = 23$ are $C(0) = \{0\}$,

$$C(1) = \{1,2,3,4,6,8,9,12,13,16,18\} \text{ and } C(-1) = -C(1).$$

The dimension is $23 - 11 = 12$. We want to show that $\mathcal{C}(A)$ has minimum distance $\ge 7$. Observe that, for every $j \ne 0$, $j \notin A$, we have that $\mathcal{C}(A \cup \{j\})$ is the repetition code of minimum distance 23 (this follows formally from the BCH bound, as this code has as defining set an interval of length 22). It follows that one condition of Lemma 13.17 will always be satisfied.

Let $S$ be the support of a codeword of weight $d$. Start from the interval $\{1,2\} \subset C(1)$, which shows $d \ge 3$ by the BCH bound. We have $5 \notin C(1)$. Lemma 13.17 shows that $\{1,2,5\}$ is independent of $S$. The shift lemma shows that $\{8,9,12\}$ is independent of $S$ as well. As $\{8,9,12\} \subset C(1)$, we have $d \ge 4$. We continue in this way, using alternately Lemma 13.17 and Lemma 13.16:

$$\{8,9,12\} \longrightarrow \{8,9,12,14\} \longrightarrow \{12,13,16,18\} \longrightarrow$$

$$\{12,13,16,18,5\} \longrightarrow \{2,3,6,8,18\} \longrightarrow \{2,3,6,8,18,5\}.$$

This shows $d \ge 6$. Assume $d = 6$. A codeword $v$ of weight 6 is in the sum zero subcode $\mathcal{C}(A \cup \{0\})$. Application of the method to this code yields

$$\{2,3,6,8,18,5\} \longrightarrow \{0,1,4,6,16,3\} \subset C(0) \cup C(1)$$

which shows that $\mathcal{C}(\{0,1\})$ has $d > 6$, a contradiction.

We have shown that $\mathcal{C}(\{1\})$ is a $[23,12,7]_2$ code. This is the famous binary Golay code, which we constructed in Chapter 7 without any theoretical backing. This application is from the original paper [212].

The following family of cyclic codes of minimum distance 6 was described by Danev and Olsson [63]. Let $q \ge 4$ and $n = q^2 - q + 1$. As $q^3 + 1 = (q + 1)(q^2 - q + 1)$ and $(q^3 + 1) \mid q^6 - 1$, we have $F = \mathbb{F}_{q^6}$ and consequently all cyclotomic cosets have as lengths divisors of 6. We use the cyclotomic cosets

$$C(1) = \pm\{1, q - 1, q\} \text{ and } C(q - 2) = \pm\{q - 2, q + 1, 2q - 1\}.$$

Consider

$$\mathcal{C} = \mathcal{C}(\{0\} \cup C(1)) \supset \mathcal{D} = \mathcal{C}(\{0\} \cup C(1) \cup C(q - 2)).$$

As $\{0\} \cup C(1) \cup C(q - 2) \supset \{-1,0,1\} + \{-(q - 1),0,q - 1\}$ contains the sum of two intervals of length 3, it follows from the Roos bound Theorem 13.10

that $\mathcal{D}$ has minimum distance $\ge 6$. We want to show that the same is true of the $(n-7)$-dimensional cyclic code $\mathcal{C}$. Let $d$ be the minimum distance of $\mathcal{C}$ and assume $d<6$. In each application of Lemma 13.17 we choose $j\in C(q-2)$. The condition on $j$ from Lemma 13.17 is then satisfied. We start with $\{q-1,q\}\longrightarrow\{q-1,q,2q-1\}$ and continue

$\{0,1,q\}\longrightarrow\{0,1,q,q+1\}\longrightarrow\{-1,0,q-1,q\}\longrightarrow\{-1,0,q-1,q,2q-1\}\longrightarrow\{-q,-(q-1),0,1,q\}.$

The resulting independent set of size 5 is contained in $\{0\}\cup C(1)$. We have proved the following:

## 13.18 Theorem.

Let $q\ge4$. The cyclic $q$-ary code of length $q^2-q+1$ with $A=\{0,1\}$ is a $[q^2-q+1,q^2-q-6,6]_q$-code.

Short examples are $[13,6,6]_4$, $[21,14,6]_5$, $[43,36,6]_7$.

## Generator matrices of cyclic codes

In order to be able to work with cyclic codes, we have to determine generator matrices for them. It turns out that we can find an almost canonical form.

Recall the situation: we have $n\mid q^r-1$, $F=\mathbb{F}_q(\epsilon)$, where $\epsilon$ is a primitive element of $F$. Further, $W$ consists of all elements whose $n$-th power is 1 and $W=\{1,\alpha,\alpha^2,\dots,\alpha^{n-1}\}$. Our $q$-ary cyclic code is $\mathcal{C}(A)$. Its dimension is $|B|$, where $-B$ is the union of the cyclotomic cosets, which are disjoint from $\tilde A$. Let $C$ be a cyclotomic coset disjoint from $\tilde A$. Then $\operatorname{tr}(\mathcal{B}(-C))\subset\mathcal{C}(A)$ and $\mathcal{C}(A)$ is the direct sum of all those codes. In other words, $\mathcal{C}(A)$ is the direct sum of the codes $\operatorname{tr}(\mathcal{B}(C))$, where $C$ varies over the cyclotomic cosets contained in $B$. Each such code has dimension $|C|$. We have $\operatorname{tr}(\mathcal{B}(C))=\mathcal{B}(C)_{\mathbb{F}_q}$, but the expression using the trace is handier: it may be hard to find a systematic way to write down the words of an $F$-linear code all of whose entries happen to be in the subfield $\mathbb{F}_q$, whereas there is no problem in applying the trace mapping.

In particular, each cyclotomic coset $C$, $C\cap\tilde A=\emptyset$ contributes $|C|$ rows to a generator matrix of $\mathcal{C}(A)$.

To fix notation, denote $v(l,i)\in\mathbb{F}_q^n$ the vector with entry $\operatorname{tr}(\epsilon^l\beta^i)$ in coordinate $\beta\in W$. If $i\in C$, then $v(l,i)\in\operatorname{tr}(\mathcal{B}(C))$. Observe that $v(l,i)$ is the codeword in $\operatorname{tr}(\mathcal{B}(C))$ corresponding to the monomial $\epsilon^l X^i$. As $1,\epsilon,\dots,\epsilon^{r-1}$ is a basis of $F$ over $\mathbb{F}_q$, we can choose $0\le l\le r-1$.

Let $C$ be a cyclotomic coset, $C\cap\tilde A=\emptyset$. Choose $i\in C$. In the generic case when $|C|=r$, there is no problem: the words $v(0,i)$, $v(1,i),\dots v(r-1,i)$ form a basis of $\operatorname{tr}(\mathcal{B}(C))$. When $|C|<r$, these vectors still generate $\operatorname{tr}(\mathcal{B}(C))$.

We will have to choose |C| linearly independent among these vectors. If this is done for each cyclotomic coset avoiding Ã, the corresponding words v(l, −i) form the rows of a generator matrix.

## 13.19 Theorem.

Let v(l, i) ∈ 𝔽_q^n be the word with entry tr(ε^l β^i) in coordinate β ∈ W.

For each cyclotomic coset C, choose a representative i ∈ C and a set S(i) ⊆ {0,1,…,r−1} of |C| indices l such that the v(l,i), l ∈ S(i) are linearly independent. The v(l,i), l ∈ S(i) are a basis of tr(ℬ(C)).

The v(l,−i), l ∈ S(−i) where i varies over representatives of cyclotomic cosets C avoiding Ã, form the rows of a generator matrix of 𝒞(A).

Again, the generator matrices as described in Theorem 13.19 are close to being canonically determined. There is the choice of the representatives of cyclotomic cosets, but this does not really matter. When C has full length r, and this is the generic case, we have S(i) = {0,1,…,r−1}. A difficulty arises only when C is shorter.

## Check matrices of cyclic codes

It is important to have a concrete representation of a check matrix H of 𝒞(A), equivalently a generator matrix of tr(ℬ(A)) = tr(ℬ(Ã)). Strictly speaking, we know this standard form, as the dual of a cyclic code is cyclic, so H is a generator matrix of a cyclic code and we can apply Theorem 13.19. We are redoing the work of the previous section from a slightly different perspective. The main difference is that we view the entries in each section corresponding to a cyclotomic coset of length s not as s-tuples but as elements of 𝔽_{q^s}.

The Galois closure Ã is a union of cyclotomic cosets. Let R be a set of representatives for the cyclotomic cosets contained in Ã. We know that tr(ℬ(A)) is the direct sum of the tr(ℬ(C_n(i))), where i ∈ R, and dim(tr(ℬ(C(i)))) = |C_n(i)|; in other words, each cyclotomic coset C_n(i) ⊆ Ã contributes s = |C_n(i)| rows of H. It is proved in Exercise 13.2.9 that s can also be described as the degree of 𝔽_q(α^i) over 𝔽_q, equivalently 𝔽_q(α^i) = 𝔽_{q^s}. In particular, α^i ∈ 𝔽_{q^s}. It is now obvious how a check matrix H of 𝒞(A) can be described:

- 1. The columns of H are indexed by β = α^j ∈ W, j = 0,1,…,n−1.
- 2. Choose representatives i ∈ R for the cyclotomic cosets C_n(i) ⊆ Ã. Let s = s(i) = |C_n(i)|. Each i ∈ R contributes a section of s rows to H.
- 3. For each 𝔽_{q^s} ⊆ F, choose a basis over 𝔽_q.
- 4. The section of column β ∈ W corresponding to i ∈ R is β^i, where β^i ∈ 𝔽_{q^s} is represented by a column vector of length s, whose entries are the coefficients of the representation of β^i in terms of the fixed basis.
