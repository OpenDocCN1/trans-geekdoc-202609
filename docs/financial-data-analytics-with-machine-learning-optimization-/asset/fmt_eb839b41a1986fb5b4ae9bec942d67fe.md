
*Proof.* Suppose that the inverse `(A + uv^T)^{-1}` exists, which is equivalent to the solvability of the system `(A + uv^T)x = b`, for every `b ∈ R^n`. If `x` is a solution of this system, then

(4.26) `x = A^{-1}b - A^{-1}uv^Tx.`

Putting `r = v^Tx ∈ R`, we have `r = v^T(A^{-1}b - A^{-1}ur)`, hence

`r(1 + v^TA^{-1}u) = v^TA^{-1}b.`

As `b` is arbitrary, `1 + v^TA^{-1}u ≠ 0`. Conversely, one can directly check that

`(A + uv^T)(A^{-1} - (A^{-1}uv^TA^{-1}) / (1 + v^TA^{-1}u)) = I_n,`

thus ([4.25](#c04.xhtml#c04-disp-0071)) holds true.

**Proposition 4.2** Define the error vector by `e_(K) := p̂_(K) - p_(K)`. Then as sample size `n` goes to infinity, the Pearson's goodness-of-fit test [\[35\]](#c04.xhtml#c04-bib-0035) statistic
