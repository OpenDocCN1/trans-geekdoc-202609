![](bbox=[0.293, 0.093, 0.545, 0.241])

**Figure 58: Sample complexity of clustering with $L = 3$.** Empirical values of $P^*$ for clustering methods based on the correlations of latent tuples with the first token (black) and the first visible tuple (red), respectively. The scaling $P^* \sim m^{L+1}$ aligns with theoretical predictions.

Figure57 shows the relative sensitivity of each layer as a function of the number of training points $P$. As $P$ increases, the sensitivities $S_{k,l}$ decrease sequentially across levels, following the same staged learning process in Figure 17. Deep encoder layers become invariant to synonym substitutions at lower levels, confirming that the network learns to encode the hierarchical structure of the grammar. In contrast, decoder layers gradually regain sensitivity to specific low-level symbols as the output is approached. This behavior aligns with high-level representations. Crucially, the network begins to satisfy rules at level $\ell$ when it becomes insensitive to synonym variations at level $\ell-1$. This suggests that the U-Net learns to collapse lower-level synonyms into shared latent representations and to compose these latents into the production rules at level $\ell$.

# E.4.2 Sample complexity of deep clustering algorithm

In 58, we test our theoretical prediction for the hierarchical clustering algorithm with $L=3$. Specifically, we examine how tuples of latent variables at depth $\ell=2$ are clustered based on their correlations with either a single visible s-tuple (black points) or an entire visible s-tuple (red points) in the context. As predicted in Section 6.3, the sample complexity of both approaches scales as $m^4$, confirming our theoretical result.

# E.4.3 Perplexity of the generated text

Figure59 presents an alternative measure to correlations in the generated text for quantifying the longer and longer coherence as training progresses. Specifically, we extract sentences from the gener