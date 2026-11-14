```
ALGORITHM 8.1 MULTILINESEARCH
MLS (W, x^4, x^-, C_0^+, C_0^-, ε)
x* ← x^-
t ← 0
while C_t^- / C_t^+ > 1 + ε do begin
    C_t ← √(C_t^- · C_t^+)
    for all w ∈ W do begin
        Query: f_t^w ← f(x^4 + C_t · w)
        if f_t^w == "-" then begin
            x* ← x^4 + C_t · w
            Prune i from W if f_i^t == "+"
            break for-loop
        end if
    end for
    C_{t+1}^+ ← C_t^+ and C_{t+1}^- ← C_t^-
    if ∀w ∈ W f_t^w == "+" then C_{t+1}^+ ← C_t
    else C_{t+1}^- ← C_t
    t ← t + 1
end while
return: x*
```

```
ALGORITHM 8.2 CONVEX X_f^+ SEARCH
ConvexSearch (x^4, x^-, c, ε, C^+)
D ← dim (x^4)
C^- ← A^(e) (x^- - x^4)
W ← ∅
for i = 1 to D do begin
    w_i^1 ← (1/c_i) · e^(i)
    W ← W ∪ { ±w_i^1 }
end for
return: MLS (W, x^4, x^-, C^+, C^-, ε)
```

Figure 8.3 Algorithms for multi-line search. Algorithm 8.1 is a generic procedure for performing simultaneous binary searches along multiple search directions emanating from x^4; each direction, w ∈ W, must be a unit-cost direction. Algorithm 8.2 uses this MultiLineSearch procedure to minimize weighted l_1 costs when the positive class of a classifier is convex. For this procedure, every weight, c_i, must be on the range (0, ∞), although extensions are discussed in Section 8.2.1.3.

# 8.2.1.1 K-step Multi-line Search

Here we present a variant of the multi-line search algorithm that better exploits pruning to reduce query complexity of Algorithm 8.1. The original MultiLineSearch algorithm is 2 · |W| simultaneous binary searches (i.e., a breadth-first search simultaneously along all search directions). This strategy prunes directions most effectively when the convex body is asymmetrically elongated relative to x^4, but fails to prune for symmetrically round bodies. The algorithm could instead search sequentially (i.e., a depth-first search of L_ε steps along each direction sequentially). This alternative search strategy also obtains a best case of O(L_ε + |W|) queries (for a body that is symmetrically round about x^4, it uses L_ε queries along the first direction to establish an upper and lower bound within a factor of 1 + ε, and then D queries to verify the lower bound) and a worst case of O(L_ε · |W|) queries (for asymmetrically elongated bodies, in the worst case, the strategy would require L_ε queries along each of the D search directions). Surprisingly, these two alternatives have opposite best-case and worst-case convex bodies, which inspired a hybrid approach called K-step MultiLineSearch. This algorithm