# Example 7.2 (Common Modulus Attack on RSA)

Let $p = 7$ and $q = 11$

RSA modulus $n = p 	imes q = 77$

The two RSA exponents be $e = 13$ and $f = 17$

$GCD(13, 17) = 1$

Let message $M = 2$

$C_e = M^e \equiv (2)^{13} \mod {77} = ((2)^{10} \times 8) \mod {77} = (23 \times 8) \mod {77} = 30$

$C_f = M^f \equiv (2)^{17} \mod {77} = ((2)^{10} \times 128) \mod {77} = (23 \times 128) \mod {77} = 18$

$r \times e + s \times f = 1$

For some integers $r$ and $s$

$r \times e = 1 (\mod {f})$

$r \times 13 = 1 (\mod {17})$

Determine “$r$”, that is, the multiplicative inverse of $13$ (mod 17) using the Extended Euclidean Algorithm.

| (0, 17) | (0, 13) | (1, -1, 4) | 4 |
|---|---|---|--|
| (0, 13) | (1, -1, 4) | (-3, 4, 1) | 3 |

$.: r = 4$

Substituting the value of “$r$” in (7.1)

$4 \times 13 + s \times 17 = 1$

$.: s = (-51)/17 = -3$

Now computing $M = ((C_e)^r (C_f)^s) \mod n$

$= ((30)^4 (18)^{-3}) \mod {77}$

$= ((30)^4 ((18)^{-1})^3) \mod {77}$

Determine $(18)^{-1} \mod {77}$ using the “Extended Euclidean Algorithm.”

| (0, 77) | (0, 18) | (1, -4, 5) | 4 |
|---|---|---|--|
| (0, 13) | (1, -4, 5) | (-3, 13, 3) | 3 |
| (1, -4, 5) | (-3, 13, 3) | (4, -17, 2) | 1 |
| (-3, 13, 33) | (4, -17, 2) | (-7, 30, 1) | 1 |