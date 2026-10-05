# 4.7.3 Galois Finite Fields of Order 2ⁿ

+   - A Galois Field GF (2ⁿ) is a finite field of order 2ⁿ. It comprises 2ⁿ distinct integers {0,1,2,...(2ⁿ-1)}.

+   - There exists 2ⁿ distinct polynomials of degree ≤ n-1 that are used to represent the integers in the finite GF (2ⁿ).

# Example 4.18

If n=3, the integers 0 through 7 can be represented by 8 distinct polynomials of degree ≤ 7 as shown in Table 4.13.

| Integer | 3-bit binary value | Equivalent Polynomial |
|---|---||
| 0 | 000 | 0 |
| 1 | 001 | 1 |
| 2 | 010 | x |
| 3 | 011 | x + 1 |
| 4 | 100 | x² |
| 5 | 101 | x² + 1 |
| 6 | 110 | x² + x |
| 7 | 111 | x² + x + 1 |

Each integer in the range 0...(2³-1) is represented by a distinct polynomial.

# 4.7.4 Arithmetic Operations within GF (2ⁿ)

+   - The arithmetic operations like addition, subtraction, multiplication, and division are performed within the finite field GF (2ⁿ), using the usual polynomial arithmetic, with the following additional rules:

+   1. The coefficients of the polynomials are reduced (mod 2). Thus, the additive inverse of an integer “w” belonging to GF (2ⁿ) will be “w” itself.