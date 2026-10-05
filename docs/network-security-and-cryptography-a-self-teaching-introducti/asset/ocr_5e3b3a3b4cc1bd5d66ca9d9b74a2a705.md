# 180 • NETWORK SECURITY AND CRYPTOGRAPHY

TABLE 4.23 Calculation of $x = \text{ind}_g(y)$ for $n = 7$ and $g = 5$

| y | $x = \text{ind}_g(y)$ |
| 1 | 6 |
| 2 | 4 |
| 3 | 5 |
| 4 | 2 |
| 5 | 1 |
| 6 | 3 |

# 4.12.2 Algorithm to Determine the Primitive Roots of a Number $n$

+   Step 1: Determine $\phi(n)$
Step 2: Determine the prime factors of $\phi(n)$. Let these be $p_1, p_2, \dots, p_k$.
Step 3: For each $m \in \{2, 3, \dots, n-1\}$ do

> { \text{Determine}(m)^{\phi(n)/p_1}, (m)^{\phi(n)/p_2}, \dots, (m)^{\phi(n)/p_k} \pmod n) }

If none of the $k$ values determined previously is 1, then $m$ is a primitive root of $n$, else it is not.

# Example 4.36

Determine the primitive roots of $n = 7$.

# Solution

$n = 7, \phi(n) = 6$. The prime factors of $\phi(n)$ are $p_1 = 2$ and $p_2 = 3$.

Table 4.24 shows the primitive roots of the $n = 7$ calculation.

TABLE 4.24 Calculation of Primitive Roots of $n = 7$

| M | 2 | 3 | 4 | 5 | 6 |
| $M^1$ mod 7 | 2 | 6 | 1 | 6 | 6 |
| $M^2$ mod 7 | - | 2 | - | 4 | 1 |
| Is Primitive Root? | No | Yes | No | Yes | No |

Thus, the Primitive Roots of 7 are 3 and 5.

# Example 4.37

Determine the primitive roots of $n = 11$.