‖P − Q‖_{TV}^2 = [ 1/2 ∫ |p(z) − q(z)| dμ(z) ]^2
= 1/4 [ ∫ |√p(z) − √q(z)| · |√p(z) + √q(z)| dμ(z) ]^2
≤ 1/4 ∫ |√p(z) − √q(z)|^2 dμ(z) · ∫ |√p(z) + √q(z)|^2 dμ(z)
≤ 1/4 ∫ |√p(z) − √q(z)|^2 dμ(z) · ∫ 2[p(z) + q(z)] dμ(z)
= ∫ |√p(z) − √q(z)|^2 dμ(z) = H(P‖Q)^2.

The first inequality used the Cauchy–Schwarz inequality. The second inequality used (√a + √b)^2 ≤ 2(a + b). The last two equations used the definition of Hellinger distance and the fact that each density p(z) and q(z) integrates to 1.

We can also derive an upper bound of Hellinger distance by the square root of TV norm. However, in general, this bound is not tight when the norms are small.

# Proposition B.10  We have

H(P‖Q)^2 ≤ 2‖P − Q‖_{TV}.

Proof  We note that

H(P‖Q)^2 = ∫_Ω |√p(z) − √q(z)|^2 dμ(z)
≤ ∫_Ω |√p(z) − √q(z)| · |√p(z) + √q(z)| dμ(z)
= ∫_Ω |p(z) − q(z)| dμ(z).

This implies the result.

The following result is also useful.

# Proposition B.11  Let ρ = sup_z ln(p(z)/q(z)). Then

H(P‖Q)^2 ≤ KL(P‖Q) ≤ (3 + ρ) H(P‖Q)^2.