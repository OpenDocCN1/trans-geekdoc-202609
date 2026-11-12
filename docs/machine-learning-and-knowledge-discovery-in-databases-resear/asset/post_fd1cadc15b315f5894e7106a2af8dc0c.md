
that smoother trajectories are easier to predict and, hence, easier to generate.
Next, we show several examples of RWTs.

### Example 1 (Erdos-Renyi Graphs)

Suppose $\mathcal{G}$ contains Erdos-Renyi random
graphs with connection probability $p$. In other words, the \(j^{th}\) graph has \(n^{(j)}\)
nodes, and each node pair is linked with probability \(p\). For simplicity, we ignore
smoothing \((\alpha=0)\). Then, all nodes in the \(j^{th}\) graph have degree \(\approx n^{(j)}p\) if
\(n^{(j)}\) is large enough. Hence, for smooth \(f(\cdot)\), every entry of this graph's starting
vector is \(\approx 1\). In other words, all Erdos-Renyi graphs, irrespective of their sizes,
start their RWTs close to the all-ones vector \(\mathbf{1}\). Furthermore, we can show that
\(L^{(j)}\mathbf{1} \approx \mathbf{1}\) for the normalized adjacency matrices \(L^{(j)}\) of such graphs. So, the
RWTs of random graphs start near \(\mathbf{1}\), fluctuate around that point, and eventually
converge.

### Example 2 (Stochastic Blockmodel (SBM))

Suppose $\mathcal{G}$ contains graphs sampled
from an SBM with the following parameters. There are two communities with
sizes in the ratio \(\beta:1-\beta\). The probability of an edge between two nodes is \(p\) if
they are from the same community and $q$ otherwise. Suppose we choose \(f(x)=1\)
for all \(x\). Then, the starting vectors \(\boldsymbol{v}^{(j)}\) equal \(\mathbf{1}\) for all graphs. We can show that
for large enough \(k\), the random walk vector \((L^{(j)})^k\boldsymbol{v}^{(j)}\) converges to a vector \(\boldsymbol{w}\)
with clustered entries. Specifically, let

\(\kappa_1:=\beta p+(1-\beta)q,\qquad \kappa_2:=p+q-\kappa_1,\qquad \nu:=\frac{\beta\sqrt{\kappa_1}+(1-\beta)\sqrt{\kappa_2}}{\beta\kappa_1+(1-\beta)\kappa_2}.\)

Then, \(\boldsymbol{w}_i=\sqrt{\kappa_1}/\nu\) if node \(i\) belongs to the first community, and \(\sqrt{\kappa_2}/\nu\) otherwise
(via Theorem 1 proved later). Thus, the RWT evolves from \(\mathbf{1}\) to the vector \(\boldsymbol{w}\)
with clustered entries, irrespective of the graph's size.

### Example 3 (Preferential Attachment)

Suppose $\mathcal{G}$ contains graphs created from
the Barabasi-Albert model [1]. Then, for any graph, the distribution of node
degrees follows a power-law with exponent 3. As in the SBM example, take
\(f(x)=1\) for all \(x\), so the starting vectors equal \(\mathbf{1}\). The ending vectors of the
random walks are proportional to the square roots of the degrees (Theorem 1
later). These follow a power-law distribution with exponent 5.

### Example 4 (Expected-degree Random Graphs)

Suppose $\mathcal{G}$ contains random
graphs whose expected degrees match those of SBMs. Then, the starting and
ending vectors will be the same as in Example 2, but the intermediate vectors
will be different.

The above examples show that graphs from different families have different
RWT signatures. In all cases, the RWTs started from the all-ones vector. But,
they traced trajectories with different ending vectors. For other choices of \(f(\cdot)\),
RWTs can explore (say) high-degree nodes and their neighborhoods. GRAPH-WEAVE
automatically exploits such patterns to generate new graphs from the
same family.

**Main Idea:** GRAPHWEAVE has three steps. First, we construct RWTs from the graphs in $\mathcal{G}$. From these, we learn to reverse RWTs. In other words, given a vector from an RWT, GRAPHWEAVE learns to predict the previous vector. Second, we use this reverse predictor to generate new RWTs. To do this, we need an “ending” vector. All the generated RWTs share the same ending vector but trace different trajectories. We show how to construct a realistic ending vector, and why we can think of the generated RWTs as being from the same graph. Third, from the generated RWTs, GRAPHWEAVE infers the underlying graph. Crucially, we infer all edges of this graph jointly. We can generate multiple graphs by repeating the second and third steps from different ending vectors. Next, we provide details for each of the three parts of GRAPHWEAVE.

## 2.1 Learning to Reverse RWTs

Given a set $\mathcal{G} = \{A_i\}$ of graphs and a set $\mathcal{F} = \{f_\ell(\cdot)\}$ of functions, we construct the set of all RWTs $\mathcal{R} := \{RWT(A, f, \alpha, k)\}_{A \in \mathcal{G}, f \in \mathcal{F}}$. Recall that each RWT is a sequence of vectors $\boldsymbol{v}_1, \boldsymbol{v}_2, \dots, \boldsymbol{v}_k$, where a pair $(\boldsymbol{v}_j, \boldsymbol{v}_{j+1})$ represents one step of a random walk on some graph in $\mathcal{G}$.

Next, we learn to reverse the RWTs, that is, to predict $\boldsymbol{v}_j$ given $\boldsymbol{v}_{j+1}$ and $f(\cdot)$. The predictor must know $f(\cdot)$ since two different RWTs may arrive at the same $\boldsymbol{v}_{j+1}$ via different paths. Each path is determined by its starting vector, which depends on $f(\cdot)$. To build the predictive model, we face two challenges.

- **Arbitrary length input/outputs:** The length of the vectors $\boldsymbol{v}_j$ and $\boldsymbol{v}_{j+1}$ is the number of nodes in the graph. Since the graphs in $\mathcal{G}$ can have different sizes, the lengths of vectors in $\mathcal{R}$ can vary.

- **Permutation invariance:** The model must be invariant to permutations of the components of $\boldsymbol{v}_j$ and $\boldsymbol{v}_{j+1}$ since a permutation is just a reordering of the nodes. Such reordering should not affect the model’s predictions.

Our solution is simple and elegant: we use a transformer. Transformers can adapt to inputs of arbitrary context length. In our case, the input vector is $\boldsymbol{v}_{j+1} \in \mathbb{R}^n$, where the graph size $n$ varies between the graphs in $\mathcal{G}$. For a transformer, this means a context of length $n$, where each item in the context is one-dimensional. Given such an input, the transformer’s output is also of length $n$, like the desired output vector $\boldsymbol{v}_j$. So, the same transformer can work for input/output vector pairs of all sizes. Also, a transformer without position embeddings or causal masking is invariant under permutations. Thus, a vanilla transformer matches our desiderata.

However, we can significantly improve this transformer using embeddings. Formally, we construct a binning function $B : \mathbb{R}_+ \to [K]$ and an embedding $\mathcal{E} : [K] \to \mathbb{R}^m$. For vectors, we apply these functions elementwise. In other words, $B(\boldsymbol{v})$ is the vector formed by applying $B(\cdot)$ to each element of $\boldsymbol{v}$; $\mathcal{E}(\boldsymbol{v})$ is defined similarly. The user chooses the number of bins $K$ and the embedding dimension $m$. Higher values for $K$ and $m$ lead to more flexibility in the transformer.

Now, we preprocess the data to use these embeddings. Specifically, in the RWTs, we replace each vector $\boldsymbol{v}$ with $\boldsymbol{v} \otimes \mathcal{E}(B(\boldsymbol{v}))$. We further augment each

![](img/f56761e6196132d5b74909d98468408f_263_0.png)

Fig. 2. Training the reverse predictor: For every pair of successive vectors \((v_j, v_{j+1})\) from a path \(i\) of an RWT, we compare \(v_j\) against a predicted vector \(\hat{v}_j\) obtained from \(v_{j+1}\). To create \(\hat{v}_j\), the elements of \(v_{j+1}\) are first converted into a sequence of embeddings. Then, we add embeddings reflecting the function \(f\) used for the starting vector of path \(i\), and the step \(j+1\) within path \(i\). Finally, we transform these embeddings and project them to generate \(\hat{v}_j\).

input vector with an embedding that encodes the choice of \(f(\cdot)\) and the current step in the RWT. Specifically, we define an embedding \(\mathcal{E}'\) such that \(\mathcal{E}'(f, j) \in \mathbb{R}^m\), for all functions \(f \in \mathcal{F}\) and steps \(j \in [k]\). Given an input vector \(v_{j+1}\) at step \(j+1\) for function \(f(\cdot)\), we define

\(T_\Phi(v_{j+1}, f, j+1) := \text{Transformer}_\Phi(v_{j+1} \otimes \mathcal{E}(B(v_{j+1})) + 1 \otimes \mathcal{E}'(f, j+1)),\)

where \(\Phi\) represents the transformer's parameters. The transformer's input is now a length-\(n\) sequence of \(m\)-dimensional embeddings, as is the output. Finally, we add a linear projection layer to convert the output back to \(\mathbb{R}^n\):

\(P_{\Phi, \Psi}(v_{j+1}, f, j+1) := \text{Project}_\Psi(T_\Phi(v_{j+1}, f, j+1)) \text{ to } \mathbb{R}^n,\)

where \(\Psi\) are the projection parameters. Given an input \(v_{j+1}\), this projected output is our prediction for \(v_j\). We train the transformer to minimize the mean-squared error between the predicted and actual values of \(v_j\).

\(\Phi, \Psi, \mathcal{E}, \mathcal{E}' = \arg \min \sum_{(v_j, v_{j+1})} (P_{\Phi, \Psi}(v_{j+1}, f, j+1) - v_j)^2.\)

Figure 2 illustrates this process. After training, we have a reverse predictor \(P_{\Phi, \Psi}\) (henceforth, \(P\)) such that

\(P(v_{j+1}, f, j+1) \approx v_j \text{ for all } v_j \to v_{j+1} \text{ in the RWTs of } \mathcal{G}. \quad (2)\)

## 2.2 Generating RWTs

Suppose we have learned an accurate reverse predictor. Then, given an “ending” vector \(\bar{v}_k\) and a choice of \(f(\cdot)\), we can work backward by repeatedly predicting the
