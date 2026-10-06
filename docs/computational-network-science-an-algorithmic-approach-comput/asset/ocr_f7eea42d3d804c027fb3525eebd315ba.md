Many types of data studied in the physical and social sciences can be approximated with a Zipf distribution (Li, 1992), which is one of the families of discrete power-law probability distributions. An implication of the Zipf law is that the most frequent word will occur approximately twice as often as the second frequent word, which occurs twice as often as the fourth frequent word, etc.

Unlike the growth model of Barabasi, Epstein and Wang's (2002) steady-state model uses a rewiring scheme that results in power-law distribution. This model evolves an initial graph according to Markov process, while maintaining constant size and density.

Epstein and Wang's algorithm has two major steps: (1) initialize a sparse graph and (2) edit Markov edges. To generate the sparse graph $G$, they randomly add an edge between vertices with probability $2m/[n(n-1)]$, where $m$ is the number of edges added and $n$ is the number of vertices. If the number of edges in $G$ is still less than $m$, they start adding edges with a probability of 0.5 until the graph $G$ has $m$ edges. The second step is to reiterate the algorithm in Figure 1.2 $r$ times on $G$, where $r$ is a parametric value.

# 1.4.3 Trade-Off Model

A trade-off model of network formation is the highly optimized tolerance (HOT) class of models. In a simple model, nodes are allowed to reason about their connections to other nodes. A node $i$'s connection cost to a node $j$ is denoted by $c_{ij}$. The node $i$ will consider centrality of potential nodes $j$ for attachments denoted by $cen$. The node $i$ will consider sister nodes that minimize the value of $\alpha 	imes c_{ij} + cen$, where $\alpha$ is a positive weighing factor dependent on the network size $n$.

1. Pick a vertex v at random.
2. If there is no edge incident on v, we pick another one.
3. Pick an edge $(u, v) \in G$ at random.
4. Pick a vertex x at random.
5. Pick a vertex y with probability proportional to degree.
6. If $(u, v)$ is not an edge in $G$ and $x$ is not equal to $y$, then remove edge $(u, v)$ and add edge $(x, y)

Fig 1.2. Epstein and Wang's (2002) algorithm.