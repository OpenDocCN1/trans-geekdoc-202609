Observe that for all T > 0

0 ≤ 1/√(2π) x̂ exp { -1/2 ( x̂/√T + ĉ√T )² } 1/T^{3/2} ≤ C exp { - x̂/(2T) } 1/T^{3/2}

for some constant C > 0 independent of T > 0. This implies that (110.19) holds.

We prove (110.20). Let n ∈ N. Then, by L’Hospital’s rule,

lim_{T→0+} P[min_{s≤t} x + cs + σW_s < 0] / T^n ≤ lim_{T→0+} ∂/∂T P[min_{s≤t} x + cs + σW_s < 0] / (n T^{n-1}) ≤ lim_{T→0+} C exp { - x̂/(2T) } 1/(η T^{(n-1)+3/2}) = 0.

We have completed the proof.

# Theorem 110.8. Let D(V0,T) be the bond price as defined in (110.6) and set x = log(V0/K0). We have the following analytical properties of bond prices:

+   (a) For all T > 0, we have lim_{V0→∞} D(V0,T) = e^{-rT}.
+   (b) For all V0 > K0, lim_{T→0+} P_x[τ(T) ≤ T] = 0.
+   (c) Assume that the writedown function ψ is continuous and 0 ≤ ψ ≤ 1. Then
+   λ ≥ lim sup_{T→0+} { s(V0,T) } ≥ lim inf_{T→0+} { s(V0,T) } ≥ λ ∫_{y>x} ψ(x - y) dF(y). (110.21)

In particular, if ψ > 0 and P[Y1 > x] > 0, we have a strictly positive credit spread for zero maturity.

# Proof. We prove (a) first. Since the writedown function ψ is bounded, by (110.6) and (110.7), it suffices to show that lim_{x→∞} P_x[τ(T) ≤ T] = 0.