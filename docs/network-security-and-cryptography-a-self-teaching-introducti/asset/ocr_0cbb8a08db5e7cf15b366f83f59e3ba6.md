# Solution

Table 4.9 demonstrates the computational of GCD (1044, 216) as follows:

Table 4.9 Computation of GCD (1044, 216)

| A | B | R = A mod B |
|---|---|---|
| 1044 | 216 | 180 |
| 216 | 180 | 36 |
| 180 | 36 | 0 |
| 36 | 0 | - |

When B = 0, A = 36. Therefore, GCD (1044, 216) = 36.

# 4.6 EXTENDED EUCLID'S ALGORITHM

+   - The Extended Euclid's Algorithm is used to determine the Multiplicative Inverse of a positive integer $x$ modulus $m$, that is, $x^{-1} (bmod m)$ to exist, $GCD(x,m)$ must be equal to zero, that is, $x$ and $m$ must be relatively prime to each other.

# Pseudo Algorithm

Determine\_Mult\_Inv(x,m) /* Determine $x_1 \bmod m$*/