
![](img/ca72c1626f4850f058a9edc138c1ac73_230_0.png)

Each such latent variable root node induces a dependence between its two children. We can represent this with a directed arc. The resulting graph is called an **acyclic directed mixed graph** or **ADMG**. See Figure 4.43 for an example. (A **mixed graph** is one with undirected, unidirected, and bidirected edges.) One can determine CI properties of ADMGs using a technique called **m-separation** [Ric03]. This is equivalent to d-separation in a graph where every bidirected edge \(Y_i \leftrightarrow Y_j\) is replaced by \(Y_i \leftarrow X_{ij} \rightarrow Y_j\), where \(X_{ij}\) is a hidden variable for that edge. The most common example of ADMGs is when everything is linear-Gaussian. This is known as a structural equation model and is discussed in Section 4.7.2.

## 4.5.5 Comparing directed and undirected Gaussian PGMs

In this section, we compare directed and undirected Gaussian graphical models. In Section 4.2.3, we saw that directed GGMs correspond to sparse regression matrices. In Section 4.3.5, we saw that undirected GGMs correspond to sparse precision matrices. The advantage of the DAG formulation is that we can make the regression weights \(\mathbf{W}\), and hence \(\boldsymbol{\Sigma}\), be conditional on covariate information [Pou04], without worrying about positive definite constraints. The disadvantage of the DAG formulation is its dependence on the order, although in certain domains, such as time series, there is already a natural ordering of the variables. It is actually possible to combine both directed and undirected representations, resulting in a model known as a (Gaussian) **chain graph**. For example, consider a discrete-time, second-order Markov chain in which the observations are continuous, \(\boldsymbol{x}_t \in \mathbb{R}^D\). The transition function can be represented as a (vector-valued) linear-Gaussian CPD:

```
\(p(\boldsymbol{x}_t|\boldsymbol{x}_{t-1},\boldsymbol{x}_{t-2},\boldsymbol{\theta})=\mathcal{N}(\boldsymbol{x}_t|\mathbf{A}_1\boldsymbol{x}_{t-1}+\mathbf{A}_2\boldsymbol{x}_{t-2},\boldsymbol{\Sigma})\) (4.157)
```

This is called a **vector autoregressive** or **VAR** process of order 2. Such models are widely used in econometrics for time series forecasting.

The time series aspect is most naturally modeled using a DPGM. However, if \(\boldsymbol{\Sigma}^{-1}\) is sparse, then the correlation amongst the components within a time slice is most naturally modeled using a UPGM.

![](img/ca72c1626f4850f058a9edc138c1ac73_231_0.png)

Figure 4.44: A VAR(2) process represented as a dynamic chain graph. From [DE00]. Used with kind permission of Rainer Dahlhaus.

For example, suppose we have

```
\(\mathbf{A}_1 = \left(\begin{array}{ c c c c c }
\frac{3}{5} & 0 & \frac{1}{5} & 0 & 0 \\
0 & \frac{3}{5} & 0 & -\frac{1}{5} & 0 \\
\frac{2}{5} & \frac{1}{3} & \frac{3}{5} & 0 & 0 \\
0 & 0 & 0 & -\frac{1}{2} & \frac{1}{5} \\
0 & 0 & \frac{1}{5} & 0 & \frac{2}{5}
\end{array}\right), \mathbf{A}_2 = \left(\begin{array}{ c c c c c }
0 & 0 & -\frac{1}{5} & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 \\
0 & 0 & \frac{1}{5} & 0 & \frac{1}{3} \\
0 & 0 & 0 & 0 & -\frac{1}{5}
\end{array}\right)\)
```

and

```
\(\Sigma = \left(\begin{array}{ c c c c c }
1 & \frac{1}{2} & \frac{1}{3} & 0 & 0 \\
\frac{1}{2} & 1 & -\frac{1}{3} & 0 & 0 \\
\frac{1}{3} & -\frac{1}{3} & 1 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 1
\end{array}\right), \Sigma^{-1} = \left(\begin{array}{ c c c c c }
2.13 & -1.47 & -1.2 & 0 & 0 \\
-1.47 & 2.13 & 1.2 & 0 & 0 \\
-1.2 & 1.2 & 1.8 & 0 & 0 \\
0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 1
\end{array}\right)\)
```

The resulting graphical model is illustrated in Figure 4.44. Zeros in the transition matrices \(\mathbf{A}_1\) and \(\mathbf{A}_2\) correspond to absent directed arcs from \(\mathbf{x}_{t-1}\) and \(\mathbf{x}_{t-2}\) into \(\mathbf{x}_t\). Zeros in the precision matrix \(\Sigma^{-1}\) correspond to absent undirected arcs between nodes in \(\mathbf{x}_t\).

### 4.5.5.1 Covariance graphs

Sometimes we have a sparse covariance matrix rather than a sparse precision matrix. This can be represented using a bi-directed graph, where each edge has arrows in both directions, as in Figure 4.45(a). Here nodes that are not connected are unconditionally independent. For example in Figure 4.45(a) we see that \(Y_1 \perp Y_3\). In the Gaussian case, this means \(\Sigma_{1,3} = \Sigma_{3,1} = 0\). (A graph representing a sparse covariance matrix is called a **covariance graph**, see e.g., [Pen13]). By contrast, if this were an undirected model, we would have that \(Y_1 \perp Y_3 | Y_2\), and \(\Lambda_{1,3} = \Lambda_{3,1} = 0\), where \(\Lambda = \Sigma^{-1}\).

![](img/ca72c1626f4850f058a9edc138c1ac73_232_0.png)

Figure 4.45: (a) A bi-directed graph. (b) The equivalent DAG. Here the z nodes are latent confounders. Adapted from Figures 5.12-5.13 of [Cho11].

A bidirected graph can be converted to a DAG with latent variables, where each bidirected edge is replaced with a hidden variable representing a hidden common cause, or **confounder**, as illustrated in Figure 4.45(b). The relevant CI properties can then be determined using d-separation.

## 4.6 PGM extensions

In this section, we discuss some extensions of the basic PGM framework.

### 4.6.1 Factor graphs

A **factor graph** [KFL01; Loc04] is a graphical representation that unifies directed and undirected models. They come in two main “flavors”. The original version uses a bipartite graph, where we have nodes for random variables and nodes for factors, as we discuss in Section 4.6.1.1. An alternative form, known as a **Forney factor graphs** [For01] just has nodes for factors, and the variables are associated with edges, as we explain in Section 4.6.1.2.

#### 4.6.1.1 Bipartite factor graphs

A **factor graph** is an undirected bipartite graph with two kinds of nodes. Round nodes represent variables, square nodes represent factors, and there is an edge from each variable to every factor that mentions it. For example, consider the MRF in Figure 4.46(a). If we assume one potential per maximal clique, we get the factor graph in Figure 4.46(b), which represents the function

```
$$f(x_1, x_2, x_3, x_4) = f_{124}(x_1, x_2, x_4)f_{234}(x_2, x_3, x_4)$$ (4.160)
```

We can represent this in a topologically equivalent way as in Figure 4.46(c).

One advantage of factor graphs over UPGM diagrams is that they are more fine-grained. For example, suppose we associate one potential per edge, rather than per clique. In this case, we get the factor graph in Figure 4.46(d), which represents the function

```
$$f(x_1, x_2, x_3, x_4) = f_{14}(x_1, x_4)f_{12}(x_1, x_2)f_{34}(x_3, x_4)f_{23}(x_2, x_3)f_{24}(x_2, x_4)$$ (4.161)
```

We can also convert a DPGM to a factor graph: just create one factor per CPD, and connect that factor to all the variables that use that CPD. For example, Figure 4.47 represents the following

![](img/ca72c1626f4850f058a9edc138c1ac73_233_0.png)

Figure 4.46: (a) A simple UPGM. (b) A factor graph representation assuming one potential per maximal clique. (c) Same as (b), but graph is visualized differently. (d) A factor graph representation assuming one potential per edge.

![](img/ca72c1626f4850f058a9edc138c1ac73_233_1.png)

Figure 4.47: (a) A simple DPGM. (b) Its corresponding factor graph.

![](img/ca72c1626f4850f058a9edc138c1ac73_234_0.png)

Figure 4.48: A Forney factor graph. (a) Directed version. (b) Hierarchical version.

factorization:

$f(x_1, x_2, x_3, x_4, x_5) = f_1(x_1)f_2(x_2)f_{123}(x_1, x_2, x_3)f_{34}(x_3, x_4)f_{35}(x_3, x_5)$ (4.162)

where we define $f_{123}(x_1, x_2, x_3) = p(x_3|x_1, x_2)$, etc. If each node has at most one parent (and hence the graph is a chain or simple tree), then there will be one factor per edge (root nodes can have their prior CPDs absorbed into their children's factors). Such models are equivalent to pairwise MRFs.

### 4.6.1.2 Forney factor graphs

A Forney factor graph (FFG), also called a normal factor graph, is a graph in which nodes represent factors, and edges represent variables [For01; Loe04; Loe+07; CLV19]. This is more similar to standard neural network diagrams, and electrical engineering diagrams, where signals (represented as electronic pulses, or tensors, or probability distributions) propagate along wires and are modified by functions represented as nodes.

For example, consider the following factorized function:

$f(x_1, \dots, x_5) = f_a(x_1)f_b(x_1, x_2)f_c(x_2, x_3, x_4)f_d(x_4, x_5)$ (4.163)

We can visualize this as an FFG as in Figure 4.48a. The edge labeled $x_3$ is called a **half-edge**, since it is only connected to one node; this is because $x_3$ only participates in one factor. (Similarly for $x_5$.) The directionality associated with the edges is a useful mnemonic device if there is a natural order in which the variables are generated. In addition, associating directions with each edge allows us to uniquely name “messages” that are sent along each edge, which will prove useful when we discuss inference algorithms in Section 9.3.

In addition to being more similar to neural network diagrams, FFGs have the advantage over bipartite FGs in that they support hierarchical (compositional) construction, in which complex dependency structure between variables can be represented as a blackbox, with the input/output interface being represented by edges corresponding to the variables exposed by the blackbox. See Figure 4.48b for an example, which represents the function

$f(x_1, \dots, x_5) = f_{\text{prior}}(x_1, x_2, x_3, x_4)f_{\text{lik}}(x_4, x_5)$ (4.164)
