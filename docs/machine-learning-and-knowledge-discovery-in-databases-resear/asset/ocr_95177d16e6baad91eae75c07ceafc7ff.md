# 4.1 Sampling Uniformly from the Null Model

Our MCMC algorithm DiNGHY draws uniform samples from $\mathcal{D}$ by running a Markov Chain (MC) whose set of states is $\mathcal{D}$ and whose stationary distribution is uniform. We start by describing the directed graph $\mathcal{G}$ of the states, i.e., for which ordered pairs $(G, G') \in \mathcal{D} \times \mathcal{D}$ the transition probability from $G$ to $G'$ is strictly positive, and we show that this graph is strongly connected (Theorem 1). We then present an algorithm to draw the next state of the MC from the current state, and we prove that the resulting transition probabilities lead to a uniform stationary distribution for the MC. Before these steps, we introduce an equivalent representation of EODs that we use throughout this section.

**EODs as Ordered Pairs of Bipartite Graphs.** Any EOD $G = (N, E)$ can be represented as an ordered pair $(\text{B}_{\text{t}}(G), \text{B}_{\text{h}}(G))$ of bipartite graphs $\text{B}_{\text{t}}(G) = (N, E, \text{E}_{\text{t}}(G))$ and $\text{B}_{\text{h}}(G) = (N, E, \text{E}_{\text{h}}(G))$, where $N$ and $E$ are the two sets of *vertices* of these bipartite graphs.$^\text{5}$ There is an edge $(n, e) \in \text{E}_{\text{t}}(n)$ in the bipartite graph $\text{B}_{\text{t}}(G)$ iff $n$ is in the *tail* of $e$, for $n \in N$ and $e \in E$, and similarly for $\text{E}_{\text{h}}(G)$ and the head. Formally, $\text{E}_{\text{t}}(G) \doteq \{(n, e) \in N \times E : n \in \text{t}(e)\}$ and $\text{E}_{\text{h}}(G) \doteq \{(n, e) \in N \times E : n \in \text{h}(e)\}.$

**Fact 1.** An EOD $G$ has a unique representation as an ordered pair $(\text{B}_{\text{t}}(G), \text{B}_{\text{h}}(G))$ of bipartite graphs.

On the other hand, not every pair of bipartite graphs $(T, H)$ with the same sets of vertices is a representation of a *non-degenerate* EOD: the edge sets of $T$ and $H$ must be disjoint for the corresponding EOD to be non-degenerate.

We can transform the set of properties $\mathcal{P}$ that define $\mathcal{D}$ into a set of properties $\mathcal{P}'$ over pairs $(T, H)$ of bipartite graphs which have $\dot{N}$ and $\dot{E}$ as their sets of left and right vertices:

+   - for every $n \in \dot{N}$, the degree of $n$ in $T$ (resp. in $H$) is $\text{odeg}_{\dot{G}}(n)$ (resp. $\text{ideg}_{\dot{G}}(n)$); and
+   - for every $e \in \dot{E}$, the degree of $e$ in $T$ (resp. in $H$) is $\text{hdim}_{\dot{G}}(n)$ (resp. $\text{tdim}_{\dot{G}}(n)$); and
+   - the EOD corresponding to $(T, H)$ must be non-degenerate, meaning there are no $n \in \dot{N}, e \in \dot{E}$ such that $(n, e)$ is an edge of both $T$ and $H$.

We can then define the set $\mathcal{D}_{\text{B}}$ of pairs of bipartite graphs as

$\mathcal{D}_{\text{B}} \doteq \{(\text{B}_{\text{t}}(G), \text{B}_{\text{h}}(G)) : G \in \mathcal{D}\} \ .$

There is a bijection between $\mathcal{D}_{\text{B}}$ and $\mathcal{D}$. In the rest of this section we define an MC on $\mathcal{D}_{\text{B}}$ whose stationary distribution is uniform, since a uniform sample from $\mathcal{D}_{\text{B}}$ corresponds to a uniform sample from $\mathcal{D}$.