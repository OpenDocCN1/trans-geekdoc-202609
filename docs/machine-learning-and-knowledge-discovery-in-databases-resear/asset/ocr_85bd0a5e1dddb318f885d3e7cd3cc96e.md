in each iteration [2,17]. While this approach is very flexible, predicting what patterns will result from a series of complex changes is difficult. This affects the interpretability of such methods.

> How can we generate graphs matching multi-scale patterns in an interpretable way?

We make two design choices to achieve this goal. First, we focus on _patterns that can be learned from random walks_ on graphs. Specifically, we construct Random Walk Trajectories (RWTs) that track how vectors evolve over random walks. We show that several standard graph families have unique RWT signatures. Hence, RWTs can intuitively capture helpful patterns. Also, many applications are based on random walks. So, graphs generated with the right RWT signatures can immediately positively impact such applications.

Our second design choice is to generate graphs via _optimization_ on RWTs. In other words, we generate RWTs and find the optimal graph that fits these RWTs. Our approach separates the matching of patterns (via RWTs) from the graph construction (by optimization). This “division of labor” offers many benefits. RWTs are easier to generate than graphs since RWTs are naturally in a vector space. Graph construction via optimization increases flexibility. For instance, we can impose constraints (e.g., sparsity) or add regularization for robustness.

**Our contributions:** Our proposed method, named GRAPHWEAVE, generates Random Walk Trajectories (RWTs) and then optimally weaves them together into a coherent graph. We discuss GRAPHWEAVE’s advantages below.

+   1. **Formulation:** We cast graph generation as a two-step problem: generate realistic patterns and then optimize a graph to fit them. The patterns we track are derived from random walk trajectories (RWTs). The optimized graph is then helpful for any downstream tasks that rely on random walks. GRAPHWEAVE’s separation of pattern generation from graph optimization simplifies the generative process. To our knowledge, GRAPHWEAVE is _the first to demonstrate this optimization-based approach_.

+   2. **Interpretability:** RWTs track how random walks affect vectors. This basic process underlies many graph-theoretic problems. For example, the vector could represent people’s opinions in a social network. Then, the RWT would show how opinions evolve dynamically. Hence, RWTs are easily interpretable.

+   3. **Multi-scale structure:** We show that RWTs can capture large-scale graph structures. These include communities, flows, cut sizes, and degree distributions. By varying the RWT initializations, we can also explore local structures, such as the neighborhoods of high-degree nodes. Hence, the set of RWTs of a graph can capture multi-scale structures.

+   4. **Robustness:** GRAPHWEAVE jointly optimizes all edges of the generated graph. The optimization’s inputs come from multiple RWTs. Hence, the resulting graph is robust to occasional errors in the RWT generation process.