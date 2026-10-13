
Consider the graph of [Fig. 16.5](#Chp016_805-853_B9780443292385000226.xhtml#f0030), which is described in the seminal paper [44]. Smoking can cause lung cancer or bronchitis. A recent visit to Asia increases the probability of tuberculosis. Both tuberculosis and cancer can result in a positive X-ray finding. Also, all three diseases can cause difficulty in breathing (dyspnea). In the context of the current example, we are not interested in the values of the respective probability table, and our goal is to construct a join tree, following the previous algorithm. [Fig. 16.6](#Chp016_805-853_B9780443292385000226.xhtml#f0035) shows a triangulated graph that corresponds to [Fig. 16.5](#Chp016_805-853_B9780443292385000226.xhtml#f0030).

![Figure 16.5 The Bayesian network structure of the example given in [44].](images/B9780443292385000226/gr005.jpg)

Figure 16.5 The Bayesian network structure of the example given in [44].

![Figure 16.6 The graph resulting from the Bayesian network structure of Fig. 16.5, after having been moralized and triangulated. The inserted edges are drawn in red.](images/B9780443292385000226/gr006.jpg)

Figure 16.6 The graph resulting from the Bayesian network structure of [Fig. 16.5](#Chp016_805-853_B9780443292385000226.xhtml#f0030), after having been moralized and triangulated. The inserted edges are drawn in red.

The elimination sequence of the nodes in the triangulated graph is graphically illustrated in [Fig. 16.7](#Chp016_805-853_B9780443292385000226.xhtml#f0040). First, node `A` is eliminated from the clique `(A, T)` and the respective separator set comprises `T`. Because only one node can be eliminated (`i = 1`), we indicate the separator as `S[1]`. Next, node `T` is eliminated from the clique `(T, L, E)` and the `S[2]` (`i = i + 1`) separator comprises `L, E`. The process continues until clique `(B, D, E)` is the only remaining one. It is denoted as `V[8]`, as all three nodes can be eliminated sequentially (hence, `8 = 5 + 3`); there is no other neighboring clique. [Fig. 16.8](#Chp016_805-853_B9780443292385000226.xhtml#f0045) shows the resulting join tree. Verify the running intersection property.

![Figure 16.7 The sequence of elimination of nodes from the respective cliques of Fig. 16.6 and the resulting separators.](images/B9780443292385000226/gr007.jpg)

[Figure 16.7](#Chp016_805-853_B9780443292385000226.xhtml#cf0350) The sequence of elimination of nodes from the respective cliques of [Fig. 16.6](#Chp016_805-853_B9780443292385000226.xhtml#f0035) and the resulting separators.

![Figure 16.8 The resulting join tree from the graph of Fig. 16.6. A separator Si is linked to a clique Vj (j > i) so that Si ⊂ Vj.](images/B9780443292385000226/gr008.jpg)

Figure 16.8 The resulting join tree from the graph of [Fig. 16.6](#Chp016_805-853_B9780443292385000226.xhtml#f0035). A separator `S[i]` is linked to a clique `V[j]` (`j > i`) so that `S[i] ⊂ V[j]`.

### 16.2.2 Message passing in junction trees

By its definition, a junction tree is a join tree where we have associated a factor, say, `ψ[c]`, of a probability distribution, `p`, with each one of the cliques. Each factor may be the result of the product of all the potential functions, which are defined in terms of the variables associated with the nodes of the corresponding clique; hence, the domain of each one of these potential functions is a subset of the variables-nodes comprising the clique. Then, focusing on the discrete probability case, we can write

```
P(x) = (1/Z) ∏_c ψ_c(x_c),
```
(16.3)
