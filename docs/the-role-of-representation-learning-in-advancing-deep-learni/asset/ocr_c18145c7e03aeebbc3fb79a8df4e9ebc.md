# 2. Second stage operations:

+   (a) Flattening: This reshaping operation has complexity of O(1).

+   (b) Neighborhood-based transformer encoding: Similar to the window-based attention analysis, the complexity is O(H_l W_l (2n_l + 1)^4). This is because we perform self-attention within each group of (2n_l + 1)^2 nodes, and we have H_l W_l such groups. Assuming a constant n_l, the overall complexity of this step: O(H_l W_l).

+   (c) Selection of refined nodes: This involves selecting the refined embedding of the central node in each group, which is an indexing operation with a complexity of O(1).

Therefore, the complexity of constructing a single tree level T_{l+1} is O(H_l W_l), linear in the number of nodes from the previous level.

Now, let's determine the complexity of constructing the entire tree. Without loss of generality, we only consider operations associated with the attention mechanism. This is not a problem, since the complexity of the attention mechanism dominates that of the other operations. Attention operations are repeated L - 1 times, where L is the number of tree levels. The total number of operations is then proportional to:

\sum_{l=0}^{L-2}(K_h K_w)^2 \frac{H_l W_l}{K_h K_w} + (2n_l + 1)^4 H_l W_l \le (K_h K_w + (2n_{max} + 1)^4) \sum_{l=0}^{L-2} \frac{H_0 W_0}{K_h^l K_w^l}
\le H_0 W_0 (K_h K_w + (2n_{max} + 1)^4) \sum_{l=0}^{L-2} (\frac{1}{K_h K_w})^l
\le H_0 W_0 (K_h K_w + (2n_{max} + 1)^4) \frac{1 - (\frac{1}{K_h K_w})^{L-1}}{1 - \frac{1}{K_h K_w}}
\le H_0 W_0 K_h K_w (K_h K_w + (2n_{max} + 1)^4) \frac{1 - (\frac{1}{K_h K_w})^{L-1}}{K_h K_w - 1}
\le H_0 W_0 \frac{K_h K_w (K_h K_w + (2n_{max} + 1)^4)}{K_h K_w - 1}

The first inequality comes from n_{max} = \max_{0 \le l < L} n_l. The last inequality comes from the fact that K_h K_w > 1 and L \ge 1.

We conclude that the complexity of constructing the entire tree is O \left( H_0 W_0 \frac{K_h K_w (K_h K_w + (2n+1)^4)}{K_h K_w - 1} \right) = O(H_0 W_0) = O(N_E), linear in the number of input (encoder) tokens.