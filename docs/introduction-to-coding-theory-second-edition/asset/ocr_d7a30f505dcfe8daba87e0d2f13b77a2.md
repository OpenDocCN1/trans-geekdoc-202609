+   1. The ingredients: ground field $\mathbb{F}_q$, extension field $F = \mathbb{F}_{q^r}$, divisor $n \mid (q^r - 1)$, the multiplicative subgroup $W = \langle \alpha \rangle$ of order $n$ in $F^*$, defining set $A$ of exponents (mod $n$).
+   2. The Galois group $G$ acts on the exponents (integers mod $n$) by multiplication with $q$. The orbits are cyclotomic cosets.
+   3. The Galois closure $\tilde{A}$ is the union of all cyclotomic cosets nontrivially intersected by $A$.
+   4. $\mathcal{B}(A)$ is an $[n, |A|]_F$-code with basis: the monomials $X^i, i \in A$, evaluated at the elements of $W$.
+   5. The cyclic code $\mathcal{C}(A) = \mathcal{C}(\tilde{A}) = tr(\mathcal{B}(A))^{\perp}$ is an $[n, n - |\tilde{A}|, t + 1]_q$ code, where $t$ is the size of the largest interval contained in $\tilde{A}$ (BCH bound).
+   6. The dual of $\mathcal{C}(A)$ has defining set $B = -\tilde{A}$.
+   7. A special case of the Roos bound: if $I_1, I_2$ are intervals, $I_1 + I_2 \subseteq \tilde{A}$, then $\mathcal{C}(A)$ has $d \ge |I_1| + |I_2|$.
+   8. There is an essentially canonically determined generator matrix of $\mathcal{C}(A)$.
+   9. There is an application of binary primitive cyclic codes of minimum distance 5 to fingerprinting.

# Exercises 13.2

13.2.1. Determine the cyclotomic cosets in the case $q = 2, n = 31$.

13.2.2. Determine the parameters of binary cyclic codes of length 31 in cases $A = \{1,3,5\}$ and $A = \{-1,0,1\}$.

13.2.3. Determine the parameters of the binary cyclic code of length 63 with $A = \{1,3,5,7,9\}$.

13.2.4. Determine the cyclotomic cosets in the case $q = 3, n = 26$.

13.2.5. Show that the binary primitive cyclic code (length $2^r - 1$) with defining set $A = \{1\}$ is equivalent to the binary Hamming code.