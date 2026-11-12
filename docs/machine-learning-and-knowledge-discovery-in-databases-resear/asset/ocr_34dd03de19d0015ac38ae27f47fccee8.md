nodes $D$ with $L \cup D = N$. A leaf node $l \in L$ contains a class label $c \in \{-1, +1\}$. We describe a decision node $d_i \in D$ as triple $d_i = (\sigma_i, n_i^+, n_i^-)$, where $\sigma_i$ is a condition based on a feature in $\mathcal{F}$, while $n_i^+$ and $n_i^-$ are child nodes of $d_i$ in the tree.

# Building Conjunctive DL Concepts.

When classifying a given individual, the decision tree algorithm starts at the root node and traverses the tree. The traversal depends on whether the current node is a leaf node or a decision node. If it is a leaf node, the node’s class is assigned to the example. If it is a decision node, the example is tested against the node’s condition. If the example fulfills the condition, the algorithm traverses to the $n_i^+$ child node. Otherwise, the traversal continues with the $n_i^-$ child node. We consider each node as a class expression; hence, for a given positive individual, we construct a conjunctive class expression from all nodes seen along the respective traversal. For a given $e \in E^+$, let $\pi = \{n_1, \dots, n_{|\pi|} | n_{|\pi|} \in L, \forall i < |\pi| : n_i \in D\}$ denote a sequence of qualifying nodes starting from the root node and ending with a leaf node. From $\pi$, a conjunctive class expression can be obtained as

$$C_\pi = \prod_{i=1} \sigma_i, \tag{7}$$

where $C_\pi(e)$ is the observed explainable features of $e$ at inference by the decision tree classifier. Let $\Pi$ denote a set of conjunctive class expressions constructed for $E^+$. For the running example shown in Fig. 2, $\Pi$ contains the following three class expressions:

+   Female \(\sqcap (\exists \text{hasSibling.Father})\) (8)
+   Female \(\sqcap (\neg(\exists \text{hasSibling.Father})) \sqcap (\exists \text{married.Brother})\) (9)
+   Female \(\sqcap (\neg(\exists \text{hasSibling.Father}))) \sqcap (\neg(\exists \text{married.Brother}))) \sqcap (\exists \text{hasSibling.Mother})\) (10)

Note that since $\Pi$ is a set, only distinct sequences of decision tree nodes are transformed into class expressions. By this, we aim to reduce redundancy, i.e., the length of generated concepts.

# Disjunction of Conjunctive DL Concepts.

A final prediction for a given class expression learning problem is then computed as

$$H = \bigsqcup_{C_\pi \in \Pi} C_\pi. \tag{11}$$

For the running example, $H$ corresponds to the disjunction of Equations (8) to (10). Hence, $\tau$DL can tackle a class expression learning problem **without a single retrieval operation**. Recall that as the size of the input knowledge base grows, performing retrieval operations to compute the quality of a class expression becomes a computational bottleneck.