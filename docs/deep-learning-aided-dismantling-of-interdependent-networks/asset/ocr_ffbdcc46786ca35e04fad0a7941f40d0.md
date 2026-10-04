# # Article

https://doi.org/10.1038/s41556-025-01070-2

![](bbox=[0.165, 0.065, 0.835, 0.245])

![](bbox=[0.165, 0.265, 0.835, 0.435])

**Fig. 3** The disentangling cost of two real-world networks by different disentangling algorithms. **a– d**. The horizontal axis represents the cost of node fraction and the vertical axis represents the residual node cost

each node in the sequence incurs a cost. We consider two scenarios: the cost of each node equals, that is, the cost of a node equals the edges that are removed together with the node, that is, degree cost. We relax these layers to identify nodes taken at random from the normal or uniform distributions. This allows us to test the generalizability of our algorithms to cases where edges are removed. The size of the LMCER provides a measure to monitor the formation of the network into non-mutually exclusive components and typically decreases with the cumulative cost of the removed nodes. The area under the curve (ADC), which is the relative size of the LMC, provides a measure to quantify the quality of a specific sequence of nodes or whether a disentangling is given by the cost required to make the LMC non-existent. The disentangling cost, is given by the sum of the costs of the removed nodes,

is essential for increasing the diversity of real-world networks with synthetic networks, increasing the generalizability of MultiDisrainer. The Homo and Sanremo2016 networks under unit cost (a) and under degree cost

Proposed approach to the disentangling of interdependent networks

MultiDisrainer is the first approach to integrate multilayer network representation with deep reinforcement learning (DRL) to solve optimization problems on multilayer interdependent networks. We ensure to address the three main challenges faced by MultiDisrainer:

+   (1) MultiDisrainer trained on synthetic graphs constructed via a generative network model to accurately reproduce the structure of real-world interdependent networks. and

+   (2) MultiDisrainer operates on an encoding framework designed to effectively capture and preserve both intra-layer and inter-layer network structures and properties. This high-quality representation enables effective learning and generalization to unseen networks.

+   (3) MultiDisrainer appropriately bridges multilayer representation with DRL components. This involves defining the network state, node deletion actions, designing the environment and establishing evaluation methods to guide learning.

A schematic illustration of the MultiDisrainer framework is provided in Fig. 1, and details on its implementation are reported in 'MultiDisrainer' Methods. We describe its structure here.

GNN generates synthetic multilayer networks with cross geometric correlations. GMM has been widely used to capture the properties of real multilayer networks. The model has several parameters that control both intra-layer and inter-layer properties of generators by aggregating information across layers.

Traditional learning for multilayer networks using graph neural network architectures, such as path-based or generative layers. These frameworks independently learn representations in each layer and combine using deep learning techniques such as multilayer attention; however, they fail to fully capture the complexity of the interlayer topology. Here, we propose a new multilayer graph neural network (MGNN), which uses a layer-specific graph

Nature Intelligence | Volume 7 | 2025 | 1266–1277

1269