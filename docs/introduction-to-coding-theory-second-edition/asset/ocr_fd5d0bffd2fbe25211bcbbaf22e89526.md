1.5.5. Use the subset interpretation of the binomials to prove the binomial formula

$$(a + b)^n = \sum_{i=0}^n \binom{n}{i} a^i b^{n-i}.$$

1.5.6. Prove

$$(1 - b)^n = \sum_{i=0}^n (-1)^i \binom{n}{i} b^i.$$

# 1.6 The sphere-packing bound

and the ternary Hamming code; the football pool problem.

As in all mathematical optimization problems, the problem of finding the maximum number $M$, such that a code $(n,M,d)_q$ exists, splits into two parts: we have to construct good codes (with high $M$), and we have to prove upper bounds showing that a higher value of $M$ is impossible. In this section we will prove our first upper bound. It is a direct consequence of the basic idea of error correction.

As a preparation, we need a counting argument (this is a typical problem of elementary combinatorics) of the same type as the argument in Section 1.5. Given a vector $x \in \mathcal{A}^n$ (recall that $\mathcal{A}$ is our alphabet of size $q$), how many vectors are there at distance $\le i$ from $x$? We call this set of vectors the **ball of radius $i$ with center $x$.**

**1.11 Definition.** *Consider the space $\mathcal{A}^n$ of vectors of length $n$, with the Hamming metric, where $|\mathcal{A}| = q$. This is also called a **Hamming space**. The number of vectors at distance $\le i$ from a given vector is denoted $V_q(i,n)$. We call $V_q(i,n)$ the **volume** of a ball of radius $i$.*

Fix some distance $j$ and count the vectors at distance precisely $j$ from the given vector. There are $\binom{n}{j}$ choices for the set of coordinates where the entries are different. Once this set is fixed, there are $q - 1$ possibilities for the possible entries in each of these $j$ coordinates. We count $\binom{n}{j}(q - 1)^j$. The volume $V_q(i,n)$ is obtained by adding up these numbers, for $j \le i$. We have seen the following: