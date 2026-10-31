![](bbox=[0.05, 0.12, 0.95, 0.66])

# FIGURE 5.1: Shortening and puncturing

$\mathcal{E} = \{(x_1,x_2,\dots,x_{n-1}) \mid \text{there is } x \in \mathbb{F}_q \text{ such that } (x_1,x_2,\dots,x_{n-1},x) \in \mathcal{C}\}.$

This means we project the codewords of $\mathcal{C}$ onto the first $n-1$ coordinates. The number of codewords of $\mathcal{E}$ is the same as in $\mathcal{C}$ (if two different words in $\mathcal{C}$ agreed in all but one coordinate, their distance would be 1). In particular, $\mathcal{E}$ has dimension $k$. This time we cannot expect the minimum distance to remain unchanged. However, as only one coordinate has been removed, the minimum distance will decrease by at most 1.

# 5.2 Theorem. If there is a code $[n,k,d]_q$, where $d > 1$, then puncturing (projection) yields a code $[n-1,k,d-1]_q$.

For example, given a code $[24,12,8]_2$ (it is known as the binary extended Golay code), we can construct by repeated shortening and puncturing $[23,12,7]_2$, $[23,11,8]_2$, $[22,12,6]_2$, $[22,11,7]_2$, $[22,10,8]_2,\dots$