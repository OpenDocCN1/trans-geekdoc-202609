# TABLE 4.10 Multiplicative Inverse of 18 mod 1761

| $(A_1, A_2, A_3)$ | $(B_1, B_2, B_3)$ | $(T_1, T_2, T_3)$ | $Q = A_3, 	ext{DIV } B_3$ |
|---|---|---|--|
| (0,1761) | (0,18) | (1,-97,15) | 97 |
| (0,18) | (1,-97,15) | (-1,-98,3) | 1 |
| (1,-97,15) | (-1,-98,3) | (6,-587,0) | 5 |
| (-1,-98,3) | (6,-587,0) | | - |

$GCD(18,1761) = A_3 = 3$

Since $B_3 = 0$, Therefore, $18^{-1} \pmod{1761}$ does not exist

# Example 4.15

Determine the multiplicative inverse of 18 mod 557.

# Solution

For 18 mod 557, $x=18; m=557$.

Table 4.11 illustrates the multiplicative inverse of 18 mod 557.

# TABLE 4.11 Multiplicative Inverse of 18 mod 557

| $(A_1, A_2, A_3)$ | $(B_1, B_2, B_3)$ | $(T_1, T_2, T_3)$ | $Q = A_3, 	ext{DIV } B_3$ |
|---|---|---|--|
| (1,557) | (0,18) | (1,-30,17) | 30 |
| (0,18) | (1,-30,17) | (-1,-331,1) | 1 |
| (-1,-30,17) | (-1,-31,1) | | - |

$B_3 = 31 = 18^{-1} \pmod{557}$

$	herefore 18^{-1} \pmod{557} = 31$

# Verification

$31 	imes 18 \pmod{557} = 558 \pmod{557} = 1$

$	herefore 18^{-1} \pmod{557} = 31$, stands verify.