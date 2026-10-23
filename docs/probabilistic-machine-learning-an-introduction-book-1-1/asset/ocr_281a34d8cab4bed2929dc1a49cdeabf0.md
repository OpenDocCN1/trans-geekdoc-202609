GRAPHEDM, skip-gram graph embedding methods use an outer product (Equation 23.13) as their decoder function and a graph reconstruction term computed over random walks on the graph.

In more detail, DeepWalk trains node embeddings to maximize the probability of predicting context nodes for each center node. The context nodes are nodes appearing adjacent to the center node, in simulated random walks on A. To train embeddings, DeepWalk generates sequences of nodes using truncated unbiased random walks on the graph—which can be compared to sentences in natural language models—and then maximize their log-likelihood. Each random walk starts with a node v_{i1} ∈ V and repeatedly samples the next node uniformly at random: v_{i,j+1} ∈ {v ∈ V | (v_{ij}, v) ∈ E}. The walk length is a hyperparameter. All generated random-walks can then be encoded by a sequence model. This two-step paradigm introduced by [PARS14] has been followed by many subsequent works, such as node2vec [GL16].

We note that it is common for underlying implementations to use two distinct representations for each node, one for when a node is center of a truncated random walk, and one when it is in the context. The implications of this modeling choice is studied further in [AEHPAR17].

To present DeepWalk in the GRAPHEDM framework, we can set:

s(W) = E_q [ (D^{-1} W)^q ] with q ~ P(Q) = Categorical([1,2,...,T_max]) (23.17)

where P(Q = q) = T_max^{-1+q} / T_max (see [AEH+18] for the derivation).

Training DeepWalk is equivalent to minimizing:

L_{G,RECON}(W, \widehat{W}; Θ) = log Z(Z) - sum_{v_i ∈ V, v_j ∈ V} s(W)_{ij} \widehat{W}_{ij}, (23.18)

where \widehat{W} = Z Z^T, and the partition function is given by Z(Z) = ∏_i ∑_j exp(\widehat{W}_{ij}) can be approximated in O(N) time via hierarchical softmax (see Sec. 19.5.2). (It is also common to model \widehat{W} = Z_out Z_in^T for directed graphs using embedding dictionaries Z_out, Z_in ∈ R^{N×L}.)

As noted by [LG14b], Skip-gram methods can be viewed as implicit matrix factorization, and the methods discussed here are related to those of Matrix Factorization (see Sec. 23.3.4). This relationship is discussed in depth by [Qiu+18], who propose a general matrix factorization framework, NetMF, which uses the same underlying graph proximity information as DeepWalk, LINE [Tan+15], and node2vec [GL16]. Casting the node embedding problem as matrix factorization can inherit benefits of efficient sparse matrix operations [Qiu+19b].

# 23.3.6 Supervised embeddings

In many applications, we have labeled data in addition to node features and graph structure. While it is possible to tackle a supervised task by first learning unsupervised representations and then using them as features in a secondary model, this is not the ideal workflow. Unsupervised node embeddings might not preserve important properties of graphs (e.g., node neighborhoods or attributes), that are most useful for a downstream supervised task.

In light of this limitation, a number of methods combining these two steps, namely learning embeddings and predicting node or graph labels, have been proposed. Here, we focus on simple shallow methods. We discuss deep, nonlinear embeddings later on.