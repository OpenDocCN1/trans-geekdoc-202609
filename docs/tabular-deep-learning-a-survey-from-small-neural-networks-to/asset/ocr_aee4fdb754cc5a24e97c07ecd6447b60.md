# A) B) C)

![](bbox=[0.196, 0.135, 0.804, 0.253])

Figure 8: We can group regularization methods into three groups: A. Training data modifications such as data augmentation, label modification, and so on. B. Neural network structure modifications, such as reducing the magnitude of weights, force sparsity at both neuron and layer levels. C. Changes in training, loss function, or training objective

| Approach | Main Features |
| --- | --- |
| Alternatives to MLPs PNNs | Enhances feature interaction modeling by incorporating both additive and multiplicative interactions, providing better interpretability, expressiveness, and reduced bias for tabular data. |
KANs | Uses B-splines for activation functions |
GANDALF | Utilizes Gated Feature Learning Units (GFLUs) to mitigate vanishing/exploding gradients and dynamically select important features |
ANets | Introduces Abstract Layers (AbsLay) to cluster correlated features and capture higher-level abstractions |
| MLP-enhancement Leaky Mechanism | Modifies MLPs by introducing a Leaky Gate mechanism, allowing each feature to scale and independently parallelized |
XNet | Introduces a new class of neural networks with the Cauchy activation function |
RealMP | Enhances MLPs with hyperparameter optimization, one-hot encoding, categorical embeddings, scaling layers, and ReLU activation |
sTabNet | Forced sparsity and attention mechanism for improving performance and interpretability. |

Table 6: Specialized architectures: MLP enhancements and alternatives

propagation. The advantage of this architecture is that it allows multiple layers to be created, can be easily parallelized, categorical variables, and [93] shows that NODE has good performance, requires more than complex preprocessing. [99] shows that GComb and NODE gives superior performance on different datasets. DOF [1] implements a fully different ensemble of relaxed decision objects, where split conditions for feature column are randomly generated. These features are aggregated through a two-level mechanism, forming a deep structure that captures complex interactions. It extends NODE by using more flexible tree construction and enhancement, resulting in improved performance and better modeling of feature dependencies. GRANDE [234] implements an ensemble of decision trees in a differentiable format using gradient-based optimization. Unlike NODE, GRANDE enables end-to-end training via backpropagation and is fully differentiable. In addition, GRANDE uses regularization and instance-based weighting, and is more interpretable than NODE. It has been proposed to decompose a neural network into soft decision trees (SDTs) [148, 96], first train a neural network and then train with mini-batch gradient descent, a decision tree that mimics the output function of the neural network. This approach has the advantage of being more interpretable, can be visualized, more efficient in inference. However, it should be considered that the trained tree has better performance than the original network. SDTR extends the concept of trees to tasks with heterogeneous tabular data [226]. In this paper, we note that a decision tree is a Boolean formula and can be rewritten as a disjoint normal form (DNF). A disjoint normal form (DNN) translates this into a neural network, where the first layer learns features (such as literals in a DNN) that are affine, and the second layer implements