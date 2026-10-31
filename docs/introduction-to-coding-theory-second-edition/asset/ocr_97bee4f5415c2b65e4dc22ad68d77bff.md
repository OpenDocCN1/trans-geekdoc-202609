with a factor of (M − 1)/M = 20/21 on the right side. If you think about it, also the last inequality z ≤ 1 can be strengthened. As M is odd, it cannot be that all codewords have a partner at distance 8, so in fact z ≤ 20/21. The right sides of the inequalities pick up a factor of 20/21. The same is true of the objective value: the contradiction M ≤ 1 + 20·61/63 < 21 is obtained.

# 15.3 Some explicit LP bounds

The easiest way to derive an explicit bound from the general LP bound of Theorem 15.30 is to use polynomials of small degree. Degree 1 leads to the Plotkin bound: recall K₁(X) = (v − 1)n − vX. We must have p(X) = 1 + cX where c ≥ 0. The second condition to satisfy is then p(r) ≤ 0. This is possible only if K₁(r) < 0. The optimal choice is then c = −1/K₁(r) and the bound is p(0) = 1 + c(v − 1)n = vr/(vr − (v − 1)n). In the case of codes, this is the Plotkin bound. As for OA, the following is obtained:

15.36 Theorem (dual Plotkin bound). Let M be the number of rows of a v-ary OA of strength t. Then

$$\frac{v^n}{M} \le \frac{v(t+1)}{v(t+1)-n(v-1)}$$ 

provided the expression on the right is > 0.

This is a strong bound on OA of large strength ((t+1)/n > (v−1)/v) just as the Plotkin bound on codes is useful for codes of large minimum distance. Reconsider the family of additive codes and OA from Theorem 16.29. They have length n = q^a, are q^b-ary (where a ≥ b > 0) and have M = q^{a+b} codewords. The minimum distance is d = q^a − q^{a−b}, and the strength is 2. We encountered them again in Section 18.1 (see Theorem 18.3), where they were called C(a,b) and used in the Bose-Bush construction. The minimum distance is rather large but not large enough to apply the Plotkin bound (the Plotkin bound would require \frac{q^a − q^{a−b}}{q^a} > \frac{q^b − 1}{q^b}, which is not satisfied: we have equality instead of strict inequality). This motivates us to generalize the Plotkin bound, applying Theorem 15.30 not to linear but to quadratic polynomials.

Choose p(X) = a(X − r)(X − n) for a > 0. The nonpositivity condition of Theorem 15.30 is then satisfied. As p(0) = arn, we want to minimize a. Let p(X) = c₀ + c₁K₁(X) + c₂K₂(X). We have to choose a such that c₀ = 1, c₁, c₂ ≥ 0. Recall the value of K₁(X) given above and observe that

$$K₂(X) = \frac{v^2}{2}X - v\big[(v-1)(n-1)+v/2\big]X + \binom{n}{2}(v-1)^2.$$