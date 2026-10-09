First, to prove it, just prove that

```
M(m − 1, n) ⊂ L_R(m, n) . (2.20)
```

Let P ∈ M(m − 1, n), where P is an m − 1-dimensional subspace. Taking v 1 , v 2 , . . . , v m −1 , v m , . . . , v n as a base of F n q , where v 1 , v 2 , . . . , v m −1 is a base of P, because m < n, there are two different m-dimensional subspaces in F n q

```
$\begin{pmatrix} P \\ v_m \end{pmatrix}$ and $\begin{pmatrix} P \\ v_{m+1} \end{pmatrix}$
```

makes

```
$P = \begin{pmatrix} P \\ v_m \end{pmatrix} \cap \begin{pmatrix} P \\ v_{m+1} \end{pmatrix} \in \mathrm{L}_R(m, n)$ .
```

Therefore, (2.20) is established.

The following proves (2.18). When m = m 1 , (2.18) is established naturally. Under m > m 1 , by (2.19),

```
L_R(m, n) > L_R(m − 1, n) > · · · > L_R(m 1 , n) .
```

Thus, (2.18) is established.

Necessity: From M(m 1 , n) ⊂ L_R(m 1 , n) ⊂ L_R(m, n), we can see that L_R(m, n) contains an m 1 -dimensional subspace Q, and Q is the intersection of the m-dimensional subspace in M(m, n). Therefore, there exists an m-dimensional subspace P in L_R(m, n), which makes P ⊃ Q. Therefore, m ≥ m 1 ≥ 0.

# Inference 2.1. [8] Set n > m ≥ 0. Then,

```
{0} ∈ L_R(m, n) .
```

Thus, the maximal element of L_R(m, n) is $\cap_{X \in \mathrm{M}(m,n)} X = \{0\}$.

Now, give the condition of a subspace in F n q as the elements in L_R(m, n).

# Theorem 2.8. Given n > m ≥ 0, L_R(m, n) consists of F n q and all subspaces of the dimension ≤ m in F n q .

Proof: According to the definition of lattice L_R(m, n), F n q ∈ L_R(m, n). As each subspace in L_R(m, n) is the intersection of finite m-dimensional subspaces, each subspace dimension in L_R(m, n) that is not equal to F n q is ≤ m. Conversely, suppose that P is a k-dimensional subspace of F n q , 0 ≤ k ≤ m. Then, P ∈ M(k, n) ⊂ L_R(k, n). From Theorem 2.7, L_R(k, n) ⊂ L_R(m, n). Therefore, P ∈ L_R(m, n).

# Inference 2.2. Set L_R($\begin{pmatrix} \mathbb{F}_q^n \end{pmatrix}$). Then,

```
L_R(n − 1, n) = L(n, F q ) .
```