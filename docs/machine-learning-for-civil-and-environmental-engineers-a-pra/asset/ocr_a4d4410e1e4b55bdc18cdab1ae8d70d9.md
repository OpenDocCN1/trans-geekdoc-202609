![](bbox=[0.09, 0.08, 0.89, 0.18])

Figure 8.7 Illustration of DAGs for mediators, confounders, and colliders (from left to right).

# 8.4.6 Assumptions Required to Establish Causality

There are several fundamental assumptions that are required to establish causal discovery and causal inference. Allow me to briefly describe these here.<sup>72</sup>

+   - The causal Markov assumption. This assumption states that a variable, X, is independent of each other variable (except X’s effects) conditional on its direct causes. Take a look at the left DAG in Figure 8.7. In this figure, X is independent of Y conditional on Z.
+     - The d-separation criterion is a close companion to the Markovian assumption [10]. This criterion establishes whether X is independent of Y, given Z (i.e., X || Y | Z), by associating independence with the separation of variables in a causal graph. For example, a path is d-separated if it contains 1) a chain or a fork such that the middle node is not in Z, or 2) a collider such that the middle node is not in Z, nor its descendants are in Z.

+   - The causal faithfulness assumption states that any population produced by a causal graph has the independence relations obtained by applying d-separation criterion, and hence eliminates all cases of unfaithfulness.<sup>73</sup> The causal Markov and faithfulness assumptions suggest that d-separation relationships in a causal DAG have a one-to-one correspondence with conditional independencies in the distribution of that particular graph [29].

+   - The causal sufficiency assumption<sup>74</sup> refers to the absence of hidden or latent parameters, i.e., our data contains measurements on all of the common causes of the selected variables [30].

# 8.4.7 Causal Graphs and Graphical Methods

So far, we have discussed the principles and the assumptions needed to identify causality and DGPs. We also know that a causal model has a causal structure to represent the DGP. While we may not know the true structure of a true DGP, we are likely to have some domain knowledge<sup>75</sup> and data that can get us close enough to a possible causal structure for a DGP<sup>76</sup>.

If you ask me, this sounds like a good spot to move into the graphical methods that can help us arrive at causal graphs and, by extension, causal models.<sup>77</sup>

Graphical methods span a variety of granularities – see Figure 8.8. For example, a directed graph (DG) is a graph without arrows and hence allows loop feedback. A partially directed graph (PDG) is a type of graph that may contain both directed and undirected edges. On the other hand, a DAG assumes acyclicity.

+   72. A rich example and corresponding mathematical details can be found elsewhere [25, 28, 30, 66].
+   73. Independences that are not a consequence of the causal Markov condition or d-separation. An example of unfaithfulness is where X is a cause of Y and Y is a cause of Z, but X and Z are independent of each other [52].
+   74. Other assumptions also exist such as Gaussianity of the noise distribution, one or several experimental settings, and linearity/nonlinearity, acyclicity – see [29].
+   75. **Domain knowledge**: information and concepts accepted by a domain.
+   76. Such a DGP may in fact turn out to be the ground truth or one that we are comfortable with labeling as a causal structure pending a series of assumptions arising from domain knowledge.
+   77. A thorough review on graphical models can be found in [52].