![](bbox=[0.35, 0.11, 0.65, 0.2])

Figure 4.24: Relationship between Markov properties of UPGMs.

![](bbox=[0.2, 0.27, 0.8, 0.38])

Figure 4.25: (a) The ancestral graph induced by the DAG in Figure 4.23(a) wrt U = {X2, X4, X5}. (b) The moralized version of (a).

# 4.3.6.2 An undirected alternative to d-separation

We have seen that determining CI relationships in UPGMs is much easier than in DPGMs, because we do not have to worry about the directionality of the edges. That is, we can use simple graph separation, instead of d-separation.

In this section, we show how to convert a DPGM to a UPGM, so that we can infer CI relationships for the DPGM using simple graph separation. It is tempting to simply convert the DPGM to a UPGM by dropping the orientation of the edges, but this is clearly incorrect, since a v-structure \( A \rightarrow B \leftarrow C \) has quite different CI properties than the corresponding undirected chain \( A - B - C \) (e.g., the latter graph incorrectly states that \( A \perp C | B \)). To avoid such incorrect CI statements, we can add edges between the “unmarried” parents \( A \) and \( C \), and then drop the arrows from the edges, forming (in this case) a fully connected undirected graph. This process is called moralization. Figure 4.23 gives a larger example of moralization: we interconnect 2 and 3, since they have common child 5, and we interconnect 4, 5, and 6, since they have a common child 7.

Unfortunately, moralization loses some CI information, and therefore we cannot use the moralized UPGM to determine CI properties of the DPGM. For example, in Figure 4.23(a), using d-separation, we see that \( X_4 \perp X_5 | X_2 \). Adding a moralization arc \( X_4 - X_5 \) would lose this fact (see Figure 4.23(b)). However, notice that the 4-5 moralization edge, due to the common child 7, is not noticed if we do not observe 7 or any of its descendants. This suggests the following approach to determining if \( A \perp B | C \). First we form the ancestral graph of DAG \( G \) with respect to \( U = A \cup B \cup C \). This means we remove all nodes from \( G \) that are not in \( U \) or are not ancestors of \( U \). We then moralize this ancestral

deterministic constraints can result in independencies present in the distribution that are not explicitly represented in the graph. See e.g., [KF09a, p120] for some examples. Distributions with non-graphical CI properties are said to be unfaithful to the graph, so \( I(p) \neq I(G) \).