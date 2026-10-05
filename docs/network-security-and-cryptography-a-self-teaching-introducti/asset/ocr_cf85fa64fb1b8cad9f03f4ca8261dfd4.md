#  7.5.3 Strength of Diffie-Hellman Key-Exchange Scheme

+   - An adversary will have access to global parameters $p$ and $g$. Also, it can intercept $Y_A$ and $Y_B$ from the communication media.

+   - But, for determining $K$, the previous parameters are not sufficient. The adversary needs either $X_A$ or $X_B$. But these parameters are kept secret by "A" and "B" respectively. And, if $p$ is sufficiently large, then determining $X_A$ from $Y_A$ or determining $X_B$ from $Y_B$ is considered computationally infeasible.

+   - Thus, it is considered computationally infeasible for an adversary to compute the main key $K$ without knowledge of either $X_A$ or $X_B$.

# Example 7.4

Let

```
$p = 7, g = 3$ (a primitive root of 7).
```

Let

```
$X_A = 3, X_B = 5$
$= (g)^{X_A} \bmod p$
$= (3)^3 \bmod 7$
$= 6$
$= (g)^{X_B} \bmod p$
$= (3)^5 \bmod 7$
$= 5$
```

```
$K_A = (Y_B)^{X_A} \bmod p = (5)^3 \bmod 7 = 125 \bmod 7 = 6$
$K_B = (Y_A)^{X_B} \bmod p = (6)^5 \bmod 7 = (1 \times 1 \times 6) \bmod 7 = 6$
```

# 7.5.4 Types of Attacks against Diffie-Hellman

+   - Clogging Attack

+   - Man-in-the-Middle Attack