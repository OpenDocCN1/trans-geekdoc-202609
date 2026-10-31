22.2.3. Let S be the semigroup of the preceding exercise. Order its elements: u1 = 0, u2 = q, u3 = q + 1, u4 = 2q, u5 = 2q + 1, u6 = 2q + 2, u7 = 3q, ... Show that u_{(i+1 choose 2)+1} = i q provided that i ≤ q.

# 22.3 Examples of function fields and projective equations

Back to the hyperelliptic equation y² = f(x) in characteristic ≠ 2. We saw in Section 20.4 that the following can be assumed without restriction: f(x) is a polynomial, product of different irreducibles. Let deg(f(x)) = n = 2m + 1 or = 2m + 2. We showed g ≤ m and promised to prove g = m.

We want to determine the genus, using the Riemann-Hurwitz formula and Dedekind’s different theorem. Let f(x) = ∏_{i=1}^r f_i(x), where f_i(x) is irreducible of degree n_i. Denote by Q_i the place of K(x) defined by f_i(x), P_i an extension place and e_i, f_i, v_i as usual. Then 2v_i(y) = e_i. It follows e_i = 2, f_i = 1 and P_i is the unique place above Q_i. As there is precisely one rational place P_∞ | Q_∞ (e = 2, f = 1) when n is odd and there are two rational places over Q_∞ when n is even, it follows that the different degree is n when n + 1 is odd and n when n is even. The Riemann-Hurwitz formula is 2g − 2 = 2(0 − 2) + 2m + 2 in both cases, hence g = m. In fact, it would not have been necessary to know the situation at the place at infinity. It would have sufficed to observe that the corresponding contribution is ≤ 1. It is uniquely determined by this information, as the different degree is even.

# 22.5 Theorem. Let char(K) ≠ 2 and F = K(x, y) defined by

y² = f(x)

where f(x) ∈ K[x] a square-free monic polynomial of degree n. Write n = 2m + 1 if n is odd, n = 2m + 2 if n is even. Then F has genus m. The constant field of F is K. The place at infinity of K(x) is ramified if and only if n is odd. The places of K(x) corresponding to divisors of f(x) are ramified.

# The relation between solutions and rational points

As an illustration, we consider the case of the hyperelliptic equation y² = f(x) in characteristic ≠ 2. What is the relation between the number N(y² − f(x)) of solutions of the corresponding homogeneous equation and the number N(F) of rational places of the corresponding hyperelliptic function field F | K(x)? Where the equation is concerned, we have

N(y² − f(x)) = 1 + 1 × |{α ∈ K | f(α) = 0}| + 2 × |{α ∈ K | 0 ≠ f(α) a square in K}|