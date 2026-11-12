tory datasets mentioned above, we first trained the model on the sparse graph, then made predictions on it, and finally obtained the final prediction result by combining the predicted paths with the shortcut dataset. Finally, we conduct extensive experiments using real-world city dataset to validate our approach. our contributions within this paper are as follows:

+   - Maintained Prediction Accuracy: We employed appropriate embedding techniques and probabilistic prediction models, enabling us to sustain high levels of prediction accuracy and reachability.

+   - Accelerated the Prediction Process: We proposed Shortcut-Edge Differential Contraction to generate a sparse graph, then applied historical path merging and bidirectional Dijkstra’s algorithm on graph weighted by transition probabilities based on model training results to obtain shortcut dataset, accelerating subsequent query processes.

+   - Refined Dual-Level Model Design: Our model is trained on both the original and sparse graphs, allowing for more effective acquisition of shortcut and final prediction data.

+   - Experimental Validation: Extensive experiments conducted on real-world city dataset validate the effectiveness of our model and a substantial enhancement in prediction efficiency.

# 2 Related Work

# 2.1 Path Prediction Algorithm

**Shortest Path-Based Route Prediction.** The shortest path is the simplest approach for route prediction, widely used in existing studies [10,11,16]. [10] proposes the spMM model, leveraging geometric and topological road network features, while [16] incorporates traffic signal delays and left turns into a heuristic cost function. Building on this, [11] constructs a candidate graph favoring straighter paths. However, these methodologies do not adequately account for driver preferences in route selection. In reality, drivers consider various factors beyond the length and straightness of the route. Consequently, the most likely route frequently diverges from the shortest path, as shown in the Fig. 2. This suggests that a singular focus on distance is insufficient for accurately predicting the most likely route.

**Route Prediction Based on RNN.** To address the challenges associated with route prediction using the shortest path, several existing methods have been proposed that utilize RNNs based on historical trajectories: In the realm of route prediction, several notable models have emerged, each with distinct principles and limitations. DEEPST [8] uses variational autoencoders to capture trajectory and traffic relationships but struggles with poor reachability for unseen points. CSSRNN [15] leverages RNNs and road network constraints but suffers from long query times, low reachability, and data dependency.