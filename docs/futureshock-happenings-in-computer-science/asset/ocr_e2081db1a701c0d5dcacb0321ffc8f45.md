+   - If there exists a (unique) $j \le k$ with $p_0 + \cdots + p_j = i$ then add $\mathfrak{v}_j^{n_j}$ to $D_i$.
+   - If $j \le k$ is largest with $p_0 + \cdots + p_j \le i$, then add $\mathfrak{v}_{p_0}, \dots, \mathfrak{v}_{p_j}$ to $D_i$.

We let DNF$(\sigma)$ denote $\bigvee_{i\le\Sigma_{j\le k} n_j} \bigwedge C_i$, and CNF$(\sigma)$ denote $\bigvee_{1\le i\le\Sigma_{j\le k} p_j} \bigwedge D_i$.

# Proposition 42. For all gradation trees $T$ and members $\sigma$ of $T$, $\hat\sigma$ is equal to both DNF$(\sigma)$ and CNF$(\sigma)$.

Proof. This is easily verified by induction on the length of the members of $T$, using the fact that a Boolean algebra is distributive.

# Example 43. Figures 7.14 and 7.15 represent a nonempty member $\sigma$ of a gradation tree and illustrate DNF$(\sigma)$ and CNF$(\sigma)$ defined in Proposition 42.

+   - Figure 7.14 illustrates the value of DNF$(\sigma)$, that is, $\bigvee_{i\le\Sigma_{j<k} n_j} \bigwedge C_i$, as defined in Notation 41. It is the particular case where $k = 3$, $p_0 = 2$, $n_0 = 3$, $p_1 = 0$, $n_1 = 1$, $p_2 = 2$, $n_2 = 2$, $p_3 = 0$, and $n_3 = 0$. So $\Sigma_{j<k} n_j = 6$. The sets $C_0$ to $C_6$ are represented with $C_0$ in the middle of the top row, and $C_6$ in the bottom right corner, reading row by row, and on a given row from left to right. For all $i \le 6$, the members of $C_i$ are shown as black dots.

![](bbox=[0.08, 0.73, 0.95, 0.88])

Figure 7.14