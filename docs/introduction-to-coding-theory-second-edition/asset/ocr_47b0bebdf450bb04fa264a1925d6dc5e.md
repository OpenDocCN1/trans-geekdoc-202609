**PROOF** It may be easiest to work with $\mathbb{F}_q$ generator matrices. Choose such a generator matrix (with $Km$ rows) for $\mathcal{C}$ such that the first $km$ rows form a generator matrix for $\mathcal{R}$. Lengthen this generator matrix by a generator matrix of the auxiliary code in the last $m(K - k)$ rows, and by a $0$ matrix in the first rows. The result is a generator matrix of a code with the right dimension, clearly of strength $2$.

The generator matrix of the code resulting from Proposition 18.4 has the form $G = \begin{pmatrix} A & 0 \\ C & D \end{pmatrix}$, where the left part generates $\mathcal{C}$, $A$ generates $\mathcal{R}$ and $D$ generates the strength $2$ auxiliary code. Should the auxiliary code possess a strength $1$ subcode again, it will, together with $\mathcal{R}$, generate a strength $1$ subcode of the resulting code. It is then possible to apply Proposition 18.4 again.

Start with code $\mathcal{C}_q(a,b)$. As it contains a $b$ dimensional strength $1$ subcode ($\mathbb{F}_q$ dimensions), we can apply Proposition 18.4 with $\mathcal{C}_q(a - b, b)$ as auxiliary code (provided $a - b \ge b$). The resulting code has a $2b$ dimensional subcode of strength $1$. Apply Proposition 18.4 again, with $\mathcal{C}_q(a - 2b, b)$ as auxiliary code. Proceed inductively in this fashion. The last inductive step occurs when $a - lb \ge b$, but $a - (l + 1)b < b$. Clearly $l = \lfloor a/b \rfloor - 1$. In this last step there is no need to use a strength $2$ code with a strength $1$ subcode. Instead of $\mathcal{C}_q(a - lb, b)$ we use the code of length $q^{a - lb} + 1$ (see Exercise 18.1.4) and obtain as end product a code of length $1 + \sum_{i=0}^{l} q^{a - ib}$.

# **18.5 Theorem.** Let $a \ge b$ be integers, $l = \lfloor a/b \rfloor - 1$. Then there is a $q$-linear $q^b$-ary code of strength $2$, dimension $(a + b)/b$ and length

$n = 1 + \sum_{i=0}^{l} q^{a - ib} = 1 + \left(q^{a + b} - q^{a - lb}\right)/\left(q^{b} - 1\right).$

The OA parameters of Theorem 18.5 are due to Bose and Bush [36], see also Hedayat, Sloane and Stufken [109]. The approach used in our proof of Theorem 18.5 is due to Y. Edel; see [17].

How much better is the Bose-Bush construction of strength $2$ orthogonal arrays than the linear construction? Only when $a$ is a multiple of $b$ is a direct comparison possible. We leave it to the reader to verify that, in these cases, the length in Theorem 18.5 equals the maximum length of linear OA. We gain nothing in these situations. What Theorem 18.5 does: it embeds the linear construction in a vaster family of strength $2$ OA where the index $\lambda$ and the alphabet are powers of the same prime. In OA notation we have

$OA_{\lambda}(2, n, Q), \text{ where } Q = q^{b}, \ \lambda = q^{a - b}$

and $n$ is the length from Theorem 18.5.

Let $b < a < 2b$. Write $a = b + i$, where $i < b$. Then $l = 0$, $n = q^{b + i} + 1$ and $\lambda = q^{i}$. We obtain $OA_{q^{i}}(2, q^{b + i} + 1, q^{b})$, for example, $OA_{2}(2, 9, 4)$, $OA_{4}(2, 17, 8)$.