
# Article

https://doi.org/10.1038/s41556-025-01070-2

![](img/d057769f0d49aabde85e4a59e009e9ea_3_0.png)
![](img/d057769f0d49aabde85e4a59e009e9ea_3_1.png)

**Fig. 3** The disentangling cost of two real-world networks by different disentangling algorithms. **a– d**. The horizontal axis represents the cost of node fraction and the vertical axis represents the residual node cost each node in the sequence incurs a cost. We consider two scenarios: the cost of each node equals, that is, the cost of a node equals the edges that are removed together with the node, that is, degree cost. We relax these layers to identify nodes taken at random from the normal or uniform distributions. This allows us to test the generalizability of our algorithms to cases where edges are removed. The size of the LMCER provides a measure to monitor the formation of the network into non-mutually exclusive components and typically decreases with the cumulative cost of the removed nodes. The area under the curve (ADC), which is the relative size of the LMC, provides a measure to quantify the quality of a specific sequence of nodes or whether a disentangling is given by the cost required to make the LMC non-existent. The disentangling cost, is given by the sum of the costs of the removed nodes, is essential for increasing the diversity of real-world networks with synthetic networks, increasing the generalizability of MultiDisrainer. The Homo and Sanremo2016 networks under unit cost (a) and under degree cost

## Proposed approach to the disentangling of interdependent networks

MultiDisrainer is the first approach to integrate multilayer network representation with deep reinforcement learning (DRL) to solve optimization problems on multilayer interdependent networks. We ensure to address the three main challenges faced by MultiDisrainer:

- (1) MultiDisrainer trained on synthetic graphs constructed via a generative network model to accurately reproduce the structure of real-world interdependent networks. and
- (2) MultiDisrainer operates on an encoding framework designed to effectively capture and preserve both intra-layer and inter-layer network structures and properties. This high-quality representation enables effective learning and generalization to unseen networks.
- (3) MultiDisrainer appropriately bridges multilayer representation with DRL components. This involves defining the network state, node deletion actions, designing the environment and establishing evaluation methods to guide learning.

A schematic illustration of the MultiDisrainer framework is provided in Fig. 1, and details on its implementation are reported in 'MultiDisrainer' Methods. We describe its structure here.

GNN generates synthetic multilayer networks with cross geometric correlations. GMM has been widely used to capture the properties of real multilayer networks. The model has several parameters that control both intra-layer and inter-layer properties of generators by aggregating information across layers.

Traditional learning for multilayer networks using graph neural network architectures, such as path-based or generative layers. These frameworks independently learn representations in each layer and combine using deep learning techniques such as multilayer attention; however, they fail to fully capture the complexity of the interlayer topology. Here, we propose a new multilayer graph neural network (MGNN), which uses a layer-specific graph

Nature Intelligence | Volume 7 | 2025 | 1266–1277

1269

# Article

https://doi.org/10.1038/s41466-025-01070.2

![](img/d057769f0d49aabde85e4a59e009e9ea_4_0.png)
![](img/d057769f0d49aabde85e4a59e009e9ea_4_1.png)
![](img/d057769f0d49aabde85e4a59e009e9ea_4_2.png)
![](img/d057769f0d49aabde85e4a59e009e9ea_4_3.png)

**Fig. 4** Preventing spread and maintaining robustness with MultiDismantler, a. MultiDismantler in reducing the outbreak spread of size offline and online networks. We simulate dynamics on the remaining network after the removal of nodes. Different dismantling strategies is considerably simpler than that other comparison. d. Simulations of robustness of the Homo network under targeted and random attack. We show the size of the LMCC as a function of the cost of the removed nodes. Multiplexes are more robust against random failure, and MultiDismantler has a slight advantage in maintaining robustness.

After interaction, MGNN applies multiple linear transformation to map layer projectors into a shared representation space. Incorporating feature from cross-layer neighbors represents each node representations; the impact of layer interplay on different nodes varies dramatically. Some nodes are influenced primarily by intracellular clusters, which rely only on interlayer edge information. MGNN incorporates an attention mechanism to learn weights for each node. The final representation of a node in a given layer is a weighted combination of its neighbors' representations from both interlayer and intracellular.

predicted Q and the target Q, which includes the cumulative reward and the maximum future Q. The agent removes nodes around the predicted Q. As the agent removes nodes and the topology of the multiplex network changes, the embeddings of state and action are continuously updated. The node removal process continues until the interdependent network is fully

## Comparison with FINDER

In work using DRL, the agent is trained to learn the strategy that maximizes disconnectivity across nodes. The DARN approach addresses this problem by using a value function with a deep neural network. The Q network estimates the expected reward of taking action a in state s. Here, the agent selects a selection of nodes to remove, and we use node vectors from multiplex representation as action embeddings. The state represents the current configuration of the multiplex network, where all nodes are neighbors of the unit state. The reward r is designed to quantify the impact of node removal on the network connectivity: measured rewards using the decrease in the size of the LMCC.

MultiDismantler builds on foundational ideas of FINDER. Both methods use a deep learning for network dismantling; also, they use techniques such as neural representation, reconstruction and loss for cost-action interaction. However, FINDER aims at finding the cost of removing the target connected component in a single network. MultiDismantler aims to solve radically different dismantling problems, they differ in key aspects. For example, MultiDismantler uses the GAN-based version of FINDER. MultiDismantler operates on a GNN, whereas FINDER targets with an advantage on a single-layer graph. For a detailed discussion on differences and similarities between MultiDismantler and FINDER, see Supplementary Section.

## Experimental setup

We train two MultiDismantler agents with identical architecture; but distinct rules to handle dismantling tasks with unit and degree costs. Also, we use cost varying

Nature Intelligence | 7 | August 2025 | 1266–1277

1270

## Table 1 | Real-world network robustness under different strategies

| Dataset | HDA | CI | MinSum | FINDER | NIRM | CoreHDA | EMD | MultiDisant |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| USir | 0.421±0.032 | 0.366±0.034 | 0.377±0.046 | 0.437±0.039 | 0.419±0.024 | 0.402±0.054 | 0.408±0.038 |
| FAQ | 0.410±0.007 | 0.408±0.008 | 0.406±0.004 | 0.408±0.003 | 0.413±0.009 | 0.410±0.006 | 0.408±0.006 | 0.411±0.007 |
| Citizens | 0.379±0.012 | 0.389±0.008 | 0.377±0.011 | 0.384±0.010 | 0.391±0.012 | 0.395±0.010 | 0.391±0.012 | 0.395±0.013 |
| Drosophila | 0.279±0.011 | 0.271±0.023 | 0.276±0.016 | 0.289±0.016 | 0.287±0.022 | 0.283±0.017 | 0.291±0.023 | 0.284±0.011 |
| FbTw | 0.436±0.063 | 0.460±0.031 | 0.462±0.033 | 0.463±0.025 | 0.462±0.041 | 0.458±0.043 | 0.463±0.048 | 0.465±0.003 |
| NetSi | 0.327±0.036 | 0.398±0.017 | 0.315±0.023 | 0.324±0.025 | 0.317±0.021 | 0.322±0.039 | 0.327±0.012 | 0.327±0.009 |
| Sachpemb | 0.237±0.021 | 0.235±0.023 | 0.295±0.016 | 0.236±0.042 | 0.239±0.044 | 0.243±0.024 | 0.246±0.021 | 0.246±0.042 |
| Homo | 0.211±0.021 | 0.201±0.027 | 0.218±0.051 | 0.215±0.032 | 0.203±0.023 | 0.213±0.021 | 0.214±0.027 | 0.217±0.001 |
| Sanremo | 0.206±0.021 | 0.201±0.027 | 0.218±0.034 | 0.202±0.031 | 0.201±0.028 | 0.219±0.025 | 0.219±0.010 | 0.217±0.001 |

The results are averaged over various runs, errors denote the standard deviation over the mean. These results are best with confidence (with the highest AUC values).

We evaluate MultiDisant on real-world networks from different dimensions. Figure 2c shows that MultiDisant outperforms other methods in both unity and degree costs. MultiDisant’s cumulative AUC is 8.4% lower than the second-best algorithm for degree cost, and the cumulative value of 7.5% is lower than the second-best for unit cost.

Figure 3 illustrates the performance of diminishing two real multilayer networks. MultiDisant consistently achieves the LMMC compared to other diminishing methods in terms of removal node costs and identifies most relevant nodes, indicating that MultiDisant is more effective in identifying diminishing structures (see Supplementary Section 4 for the results and discussion). In addition, for some real-world networks, MultiDisant’s diminishing strategy is better than others but decreases more rapidly. This shows that the methods predict a longer subgraph but a smaller network size, which is essential in revealing the network vulnerability, making it prone to rapid breakdown of the other nodes.

## Results on synthetic networks

Diminishing performance on various networks. To demonstrate the advantages of our algorithm across various networks, we use the GMM model to generate synthetic networks with different structures and layer correlation levels. Figure 2b shows MultiDisant’s diminishing performance on synthetic networks with unit cost and degree cost. Supplementary Tables 10 and 11 show that our algorithm outperforms the second-best diminishing algorithm in the AUC and C values by 5.9% and 2.6% under degree cost.

Predicting the greedy-truth optimal diminishing. In small networks, we evaluate all permutations to determine the diminishing sequence with minimal AUC in the unit-cost version of the formula. Since we cannot evaluate all permutations in scale, Supplementary Table 6 uses the 1-normalized distance to quantify the similarity between the diminishing sequences identified by different algorithms and the optimal diminishing sequence found by brute-force search. Supplementary Table 6 shows the diminishing sequence closest to the optimal sequence and achieves the maximum diminishing AUC values.

## Results on real-world networks

Diminishing performance and inductive learning capacity. MultiDisant is trained on larger sets of synthetic networks and then applied to real-world networks.

We apply MultiDisant, trained on multilayer networks, to multilayer network task. Supplementary Table 8 shows that MultiDisant achieves the best diminishing performance. This can be attributed to the algorithm to effectively leverage the diminishing features learned from multilayer networks (see Supplementary Section 3.5 for more details).

Analyzing the key components of MultiDisant. To determine the elements that contribute to the outstanding performance of MultiDisant, we successfully analyzed its three main components: cost, the attention mechanism in IGNN, and the interlayer similarity in the GMM. Supplementary Table 44 evaluates the effectiveness of the attention mechanism. In the first case, we disable the interlayer message-passing mechanism, resulting in MultiDisant’s inability to fuse information from different layers, which leads to worse diminishing quality. Next, we replace the corpus for the GMM with the BA model with randomly selected independent nodes. The first column in
