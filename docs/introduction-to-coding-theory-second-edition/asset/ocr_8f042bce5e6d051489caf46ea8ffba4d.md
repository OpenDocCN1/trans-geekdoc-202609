# A binary example

Consider the primitive binary BCH-code $\mathcal{C}(A)$ of length 15 and $A = \{1,2,\dots,6\}$ again (of designed distance 7). This is one of the pair of dual codes considered in Section 13.1. The cyclotomic cosets avoiding $A$ are $\{0\}$ and $C(7) = \{7,14,13,11\}$. We have $-C(7)=C(1)$, and clearly we choose representatives 0 from $C(0)$ (no choice here) and 1 from $C(1)$. The rows of a generator matrix of $\mathcal{C}(A)$ are $v(3,0)$, $v(0,1)$, $v(1,1)$, $v(2,1)$, $v(3,1)$. There is no choice for the last four of these rows, as $C(1)$ has length $r = 4$, hence $S(1) = \{0,1,2,3\}$ in the terminology of Theorem 13.19. Also $\{0\}$ contributes only one row. We will always choose it to be the all-1 word. The following generator matrix is obtained:

```
index : 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
v(3,0) : 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
v(0,1) : 1 1 1 1 0 1 0 1 1 0 0 1 0 0 0
v(1,1) : 0 1 1 1 1 0 1 0 1 1 0 0 1 0 0
v(2,1) : 0 0 1 1 1 1 0 1 0 1 1 0 0 1 0
v(3,1) : 0 0 0 1 1 1 1 0 1 0 1 1 0 0 1
```

Here the column index $j$ corresponds to $\alpha^{j} \in W = \mathbb{F}_{16}^*$. Let us check that we understand how this matrix was calculated. Rows $v(l,1)$, $l = 0,1,2,3$ correspond to the monomials $\alpha^{l} X$. Consider the column indexed by 6, say. The corresponding entries are $tr(\alpha^{l}\alpha^{6})$, $l = 0,1,2,3$, concretely $tr(\alpha^{6}) = 1$, $tr(\alpha^{7}) = 1$, $tr(\alpha^{8}) = 0$ and $tr(\alpha^{9}) = 1$. This explains the entries in column $j = 6$. We know that $\mathcal{C}(A)$ is a $[15,5,7]_{2}$ code.

# A ternary example

Consider the case $q = 3$, $r = 4$, $n = 20$. As 20 divides $3^{4} - 1$, we have $r = 4$, so the field $F = \mathbb{F}_{81}$ needs to be described before we can work with ternary cyclic codes of length 20.

We choose $X^{4} - X - 1$ as an irreducible polynomial over $\mathbb{F}_{3}$. This leads to a description $\mathbb{F}_{81} = \mathbb{F}_{3}(\epsilon)$, where $\epsilon^{4} = \epsilon + 1$. Here are the elements of the field: