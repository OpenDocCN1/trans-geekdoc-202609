process (take logarithms, divide by 2m, take the limit) shows (for large m) h(\binom{r}{2m}) = 1/2 or r = 2m h^{-1}(1/2), and d ≥ r q (1-2R) ≈ 2m q (1-2R) h^{-1}(1/2), hence δ ≥ (1-2R) h^{-1}(1/2). We conclude:

# 9.14 Theorem.

*Let 0 < R < 1/2. The Justesen codes 𝒥(K,2^m), where K is minimal such that K/2^{m+1} ≥ R, form a family of binary linear codes of length m2^{m+1}, rate ≥ R and relative minimum distance δ asymptotically not inferior to (1-2R)h^{-1}(1/2). Here h^{-1}(1/2) ≈ 0.11.*

In the asymptotic picture this gives a line from (0,1/2) on the R-axis to (0.11,0) on the δ-axis.

+   1. (δ, R) is **asymptotically reachable** by linear q-ary codes if there is a family of such codes with lengths n → ∞ and rate ≥ R, relative distance ≥ δ in the limit.
+   2. The **Gilbert-Varshamov bound** is an elementary nonconstructive existence theorem for linear codes.
+   3. Most of the bounds on codes derived earlier yield asymptotic upper bounds (nonexistence theorems).
+   4. The Gilbert-Varshamov bound yields a nonconstructive asymptotic existence theorem.
+   5. The **Plotkin bound** on codes of large lengths is based on quadratic counting.
+   6. The **Bose-Bush bound** on q-ary strength 2 orthogonal arrays: the number of rows is ≥ (q-1)n + 1, where n is the number of columns.
+   7. The **Justesen codes** use concatenation and Reed-Solomon codes. They yield a constructive asymptotic lower bound.
+   8. The **channel coding theorem** guarantees the existence of good long codes: if p is the symbol error probability of the binary symmetric channel, there exist long codes of all rates R < 1−h(p) with arbitrarily small decoding error probability.