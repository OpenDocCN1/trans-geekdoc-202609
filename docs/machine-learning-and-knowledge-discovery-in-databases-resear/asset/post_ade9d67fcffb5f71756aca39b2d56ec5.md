
![](img/f56761e6196132d5b74909d98468408f_258_0.png)

Fig. 1. Overview of GRAPHWEAVE: (a) Given one or more training graphs, we generate random walk trajectories (RWTs) from various starting vectors. (b) We learn to predict the previous step of a trajectory. (c) To generate a new graph, we first apply the reverse predictor several times on an “ending” vector by ⊗. We show that the ending vectors are simple to generate (Theorem 1). (d) Second, we find the optimal graph that fits the generated RWTs. The process works even with one training graph. Indeed, we generated the three graphs on the right from the single graph on the left (colors are added for clarity).

Bots and regular users have different linkage patterns. However, we may have too few examples of bots to train a classifier. To augment the training data, we can generate synthetic graphs whose link patterns match those of the known bots. This can improve classification accuracy without increasing the cost.

In this paper, we tackle the problem of generating new graphs whose structure matches a set of training graphs. We do not consider node or edge features, which we can infer by a post-processing step. For instance, for molecule graphs, we can infer a node’s feature (what atom it is) from its degree (number of bonds), and this determines its edge feature (bond strengths). Now, even generating the graph structure is a complex problem. Small-scale patterns (e.g., a benzene ring) might be important for some cases. In other applications, large-scale patterns may matter more (e.g., the ratios of various atoms, i.e., the degree distribution). No method can match all possible patterns. Clarity about the patterns a method tries to match improves its interpretability.

However, existing methods rarely make their choices explicit. One class of methods creates graphs by diffusion on the space of graph embeddings. They start from a random embedding, iteratively change it, and map the final embedding to a graph [5,20]. But even simple changes in embedding space (e.g., adding noise) may mean complex and unintuitive modifications to the graph structure. Hence, the generative process is hard to interpret.

Another class of methods changes the graph structure instead of its embedding. For instance, some methods apply local changes to the graph in each iteration [16,19]. Each step might add or remove a few nodes and edges, so the changes are intuitive. However, these local changes must add up to the desired global patterns. The need for coordinated local changes makes the process sensitive to errors. Other approaches make global changes to the graph structure in each iteration [2,17]. While this approach is very flexible, predicting what patterns will result from a series of complex changes is difficult. This affects the interpretability of such methods.

> How can we generate graphs matching multi-scale patterns in an interpretable way?

We make two design choices to achieve this goal. First, we focus on *patterns that can be learned from random walks* on graphs. Specifically, we construct Random Walk Trajectories (RWTs) that track how vectors evolve over random walks. We show that several standard graph families have unique RWT signatures. Hence, RWTs can intuitively capture helpful patterns. Also, many applications are based on random walks. So, graphs generated with the right RWT signatures can immediately positively impact such applications.

Our second design choice is to generate graphs via *optimization* on RWTs. In other words, we generate RWTs and find the optimal graph that fits these RWTs. Our approach separates the matching of patterns (via RWTs) from the graph construction (by optimization). This “division of labor” offers many benefits. RWTs are easier to generate than graphs since RWTs are naturally in a vector space. Graph construction via optimization increases flexibility. For instance, we can impose constraints (e.g., sparsity) or add regularization for robustness.

**Our contributions:** Our proposed method, named GRAPHWEAVE, generates Random Walk Trajectories (RWTs) and then optimally weaves them together into a coherent graph. We discuss GRAPHWEAVE’s advantages below.

- 1. **Formulation:** We cast graph generation as a two-step problem: generate realistic patterns and then optimize a graph to fit them. The patterns we track are derived from random walk trajectories (RWTs). The optimized graph is then helpful for any downstream tasks that rely on random walks. GRAPHWEAVE’s separation of pattern generation from graph optimization simplifies the generative process. To our knowledge, GRAPHWEAVE is *the first to demonstrate this optimization-based approach*.

- 2. **Interpretability:** RWTs track how random walks affect vectors. This basic process underlies many graph-theoretic problems. For example, the vector could represent people’s opinions in a social network. Then, the RWT would show how opinions evolve dynamically. Hence, RWTs are easily interpretable.

- 3. **Multi-scale structure:** We show that RWTs can capture large-scale graph structures. These include communities, flows, cut sizes, and degree distributions. By varying the RWT initializations, we can also explore local structures, such as the neighborhoods of high-degree nodes. Hence, the set of RWTs of a graph can capture multi-scale structures.

- 4. **Robustness:** GRAPHWEAVE jointly optimizes all edges of the generated graph. The optimization’s inputs come from multiple RWTs. Hence, the resulting graph is robust to occasional errors in the RWT generation process.

- 5. **Simplicity:** GRAPHWEAVE needs only a transformer to generate RWTs and a standard optimizer to find the best-fit graph. Both of these are off-the-shelf tools. Hence, GRAPHWEAVE’s implementation is simple and reliable.

- 6. **Strong experimental results:** On four simulated and five real-world datasets, GRAPHWEAVE outperforms state-of-the-art methods. GRAPHWEAVE is particularly strong in matching large-scale graph structures like PageRank, cuts, communities, degree distributions, and flows. Furthermore, GRAPHWEAVE is 10x faster than its closest competitor.

## 2 Proposed Method

We are given a set G of undirected graphs, possibly of different sizes. We want to generate new graphs that “look like” the graphs in G. For example, if G contains stochastic block model graphs, the generated graphs should match that family.

To generate such graphs, we must identify patterns from the graphs in G. Now, the space of all possible patterns is too large. So, we must choose a subset of intuitive and widely applicable patterns. We focus on random walk patterns since random walks underpin many graph applications. Specifically, GRAPHWEAVE constructs random walk trajectories, as defined below.

**Definition 1 (Smoothed Random Walk Trajectory (RWT)).** An RWT has four parameters: \((a)\) an adjacency matrix \(A \in \{0, 1\}^{n \times n}\) of an undirected graph on \(n\) nodes, \((b)\) a function \(f : \mathbb{R}_+ \rightarrow \mathbb{R}_+\), \((c)\) a smoothing parameter \(\alpha \in (0, 1)\), and \((d)\) the number of steps \(k\). Let \(d_i\) denote the degree of node \(i\), and \(d'_i := (1 - \alpha)d_i + \alpha\) the node’s smoothed degree. We assume that all nodes have positive degree. Also, define the smoothed normalized adjacency matrix \(L \in \mathbb{R}^{n \times n}\) and the “starting vector” \(\mathbf{v} \in \mathbb{R}^n\) as follows:

\(L_{ij} := \frac{(1 - \alpha)A_{ij} + \alpha \cdot \mathbb{1}_{i=j}}{\sqrt{d'_i \cdot d'_j}} \quad \mathbf{v}_i := n \frac{f(d_i)}{\sum_j f(d_j)}.\) (1)

> *Remark 1.* We use the normalized adjacency matrix \(L\) in Definition 1 instead of the random walk transition matrix \(D^{-1}A\) since the symmetry of \(L\) simplifies later steps. We note that both matrices have the same eigenvalues and closely related eigenvectors.

We can construct several RWTs for any graph by varying the function \(f(\cdot)\). For example, if \(f(d_i)\) increases with \(d_i\), the relative weight of high-degree nodes in the starting vector increases. Then, the RWT explores the neighborhood of such nodes in more detail.

The smoothing parameter \(\alpha\) in Definition 1 adds “self-loops” to all the nodes. The presence of self-loops slows down the random walk, leading to smoother trajectories. The higher the value of \(\alpha\), the smoother the trajectory. We find
