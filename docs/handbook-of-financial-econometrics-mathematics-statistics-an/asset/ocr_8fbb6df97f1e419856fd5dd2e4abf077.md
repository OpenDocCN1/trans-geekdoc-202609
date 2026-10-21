Therefore, it is possible to premultiply both sides of the matrix equation of (80.13), A W = K, by the inverse of A (denoted A⁻¹) and solve for the W column. This is possible because all values in the A and K matrices are known or arbitrarily set.

The first problem is the inversion of the matrix of coefficients. First, derive the determinant of matrix A. Next, after developing the signed, inverted matrix of cofactors for A, divide the cofactors by the determinant, resulting in the inversion of the original matrix. Finally, premultiply the column vector for the investment weights.

# Example 80.4.

This example focuses on the returns and risk of the first three industrial companies, International Business Machines Corp. (IBM), Johnson & Johnson (JNJ), and JP Morgan (JPM), for the period July 2013 to June 2018. The data used are tabulated in Table 80.3.

Plugging the data listed in Table 80.3 and E* = 0.00193 into the matrix above yields

⎡ 0.0451  0.0006  0.0014  −1   0.0013 ⎤   ⎡ W₁ ⎤   ⎡ 0     ⎤
⎢ 0.0019  0.0808  0.0019  −1  −0.0079 ⎥ × ⎢ W₂ ⎥ = ⎢ 0     ⎥
⎢ 0.0014  0.0019  0.1163  −1  −0.0137 ⎥   ⎢ W₃ ⎥   ⎢ 0     ⎥
⎢    1       1       1     0     0    ⎥   ⎢ λ₁ ⎥   ⎢ 1     ⎥
⎣ −0.0013 0.0079  0.0137   0     0    ⎦   ⎣ λ₂ ⎦   ⎣ 0.00193⎦ (80.14)

When matrix A is properly inverted and postmultiplied by K, the solution vector A⁻¹K is derived as

W      A⁻¹K
⎡ W₁ ⎤   ⎡ 0.7014 ⎤
⎢ W₂ ⎥   ⎢ 0.2168 ⎥
⎢ W₃ ⎥ = ⎢ 0.0818 ⎥
⎢ λ₁ ⎥   ⎢ 0.0301 ⎥
⎣ λ₂ ⎦   ⎣ −1.4005⎦ (80.15)

# Table 80.3: Data for three securities.

| Company | E(r_i) | σ_i² | Cov(R_i, R_j) |
|---|---|---|---|
| IBM | −0.0013 | 0.0005 | σ₁₂ = 0.0003 |
| JNJ | 0.0079 | 0.0016 | σ₂₃ = 0.0009 |
| JPM | 0.0137 | 0.0034 | σ₁₃ = 0.0007 |