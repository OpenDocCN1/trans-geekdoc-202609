
After partitioning the input graph into multiple subgraphs, we run in parallel a sequential MAX-DICUT algorithm on each subgraph to compute a local cut for each subgraph. We can compute cuts with higher quality when we use algorithms with better performance guarantees. Since these algorithms are also slower, we have to consider which algorithm achieves the best trade-off between the quality of the cut and the runtime of the framework.

We have implemented the randomized algorithm with an expected performance guarantee of and its derandomized variant, the algorithm with a performance guarantee of that was introduced by Buchbinder [\[90\]](#backmatter-001.xhtml#b_9783110785944-010_ref_090), and the algorithm with an expected performance guarantee of 0.79607 by Goemans and Williamson [\[256\]](#backmatter-001.xhtml#b_9783110785944-010_ref_256). As an example, we show in [Figure 4.17](#9783110785937_013188.xhtml#b_9783110785944-004_fig_017) the optimal MAX-DICUT for all subgraphs that were computed in Figure 4.16.

#### 4.4.3.3 Merging

In a final step, we have to merge the computed local cuts into a global cut. A naive approach is to define `S = ⋃[i] S[i]` and `T = ⋃[i] T[i]` as the trivial cut. The problem with this approach is that it does not consider the edges between the subgraphs. It might be possible that it is more advantageous to swap the subsets `S[i]` and `T[i]` in the global graph or even to put `S[i]` and `T[i]` into the same partition. To consider each possible combination of merging the cuts, we reduce the problem of merging the local solutions to another MAX-DICUT instance. We build a complete graph `H` with `2*k` nodes in which each node represents a locally computed partition `S[i]` or `T[i]`. Let `X` and `Y` be two nodes of `H`. We add an edge `(X, Y)` to `H` with weight `Σ[i∈X][,j∈Y] w(i, j)`. Then, we can run a MAX-DICUT algorithm on `H`. Since the graph has only `2*k` nodes, we can use an expensive algorithm to compute an exact solution. In our framework we implemented a simple brute-force algorithm and an algorithm that solves the formulation of MAX-DICUT as an Integer Program. We can also use the approximation algorithm with a performance guarantee of 0.79607 by Goemans and Williamson. In [Figure 4.18](#9783110785937_013188.xhtml#b_9783110785944-004_fig_018) we see how the local cuts that were computed in [Figure](#9783110785937_013188.xhtml#b_9783110785944-004_fig_017) 4.17 are merged into a new MAX-DICUT instance. Then, we compute the global solution on this instance.

![Fig. 4.18 We compute a new MAX-DICUT instance with 8 nodes (Fig. 4.18a) by merging the nodes that are in the same partition after Fig. 4.17. We run an exact MAX-DICUT algorithm on this instance and compute the global MAX-DICUT in Fig. 4.18b. The nodes that are in S are colored in white and the nodes that are in T are colored in gray.](graphic/b_9783110785944-004_fig_018.png)

Fig. 4.18 We compute a new MAX-DICUT instance with 8 nodes (Fig. 4.18a) by merging the nodes that are in the same partition after [Fig. 4.17.](#9783110785937_013188.xhtml#b_9783110785944-004_fig_017) We run an exact MAX-DICUT algorithm on this instance and compute the global MAX-DICUT in Fig. 4.18b. The nodes that are in `S` are colored in white and the nodes that are in `T` are colored in gray.

Tab. 4.3 A summary of our used input graphs.

| **Graph** | **|V|** | **|E|** |
| --- | --- | --- |
| recomp_dna1GB_5 | 28 245 | 1 439 986 |
| road-luxembourg-osm | 114 600 | 239 332 |
| rt-retweet-crawl | 1 112 703 | 4 557 704 |

### 4.4.4 Evaluation

In this section we evaluate our framework. We conducted our experiments on the LiDO3-Cluster of the Technical University of Dortmund[^(18)](#fn18)

We evaluate our framework on the input graphs that are summarized in [Table 4.3](#9783110785937_013188.xhtml#b_9783110785944-004_tab_003). The graph `recomp_dna1GB_5` was generated from a `recompression` tool [\[342\]](#backmatter-001.xhtml#b_9783110785944-010_ref_342) by using the 1 GiB prefix of the text dna.txt from the Pizza & Chili text corpus.[^(19)](#fn19)

#### 4.4.4.1 Experiments

For our experiments, we evaluate each part of our framework separately. First, we compare our partitioning algorithms `KaHIP`, `NodeSlice`, and `EdgeSlice`. Then, we compare our local MAX-DICUT algorithms `Derandomization`, `Buchbinder`, and `Goemans`. For the `Goemans` algorithm, we compare two variants: one solves the SDP exactly, which we call `Goemans`, the other solves the SDP with a small error where we set `ϵ = 0.01`, which we will call `Goemans(ϵ = 0.01)`. For our merging algorithms, we compare the `Buchbinder` algorithm, the two `Goemans` variants described above, and an exact algorithm that solves an `integer linear program` (ILP). When we evaluate the algorithms of one part of our framework, all other parts are fixed, i.e. for the partitioning we use `KaHIP`, as the local MAX-DICUT algorithm we use `Buchbinder`, and as merging algorithm we use `Goemans (ϵ = 0.01)`. We conducted all of our experiments five times and took the average of each result for the computed cut as well as the runtime for each step in the framework. We divide the graphs into as many as 2048 parts. Up until 16 parts, we use the same amount of cores as the number of parts. For more than 16 parts, we constantly use 16 cores.

![Fig. 4.19 The computed cut and the runtime for our partitioning algorithms while the other steps of the framework are fixed algorithms. Missing data points indicate either that the runtime of the whole framework exceeded the time limit or that the memory exceeded the RAM.](graphic/b_9783110785944-004_fig_019.png)

Fig. 4.19 The computed cut and the runtime for our partitioning algorithms while the other steps of the framework are fixed algorithms. Missing data points indicate either that the runtime of the whole framework exceeded the time limit or that the memory exceeded the RAM.

In [Figure 4.19](#9783110785937_013188.xhtml#b_9783110785944-004_fig_019), we can see our results for our partitioning algorithms. We see that using `KaHIP` as a partitioner results in an almost constant cut quality for each number of subgraphs for the graph `road-luxembourg-osm` and `rt-retweet-crawl` while the cut quality when using the naive partitioning algorithms `NodeSlice` and `EdgeSlice` gets worse when we partition the graph into more subgraphs. However, on the graph `recomp_dna1GB_5` the cut quality when using `NodeSlice` and `EdgeSlice` scales better than `KaHIP`. The runtime of `KaHIP` is on all inputs significantly slower than `NodeSlice` and `EdgeSlice` and does not scale as well as the naive algorithms.

![Fig. 4.20 The computed cut and the runtime for our local MAX-DICUT algorithms while the other steps of the framework are fixed algorithms. Missing data points indicate either that the running time of the whole framework exceeded the time limit or the memory exceeded the RAM.](graphic/b_9783110785944-004_fig_020.png)

Fig. 4.20 The computed cut and the runtime for our local MAX-DICUT algorithms while the other steps of the framework are fixed algorithms. Missing data points indicate either that the running time of the whole framework exceeded the time limit or the memory exceeded the RAM.

In [Figure 4.20](#9783110785937_013188.xhtml#b_9783110785944-004_fig_020), we can see our results for the local MAX-DICUT algorithms. We can see that by using the variants of the `Goemans` algorithm our framework produces the overall best cut quality. However, these algorithms only compute a solution when we partition the graph into a large number of subgraphs or when we have smaller subgraphs. For larger subgraphs, the `Goemans` algorithm either takes too long or consumes too much memory. The runtime of the `Goemans` algorithms is significantly larger than the linear-time algorithms but it gets faster the smaller the subgraphs get.
