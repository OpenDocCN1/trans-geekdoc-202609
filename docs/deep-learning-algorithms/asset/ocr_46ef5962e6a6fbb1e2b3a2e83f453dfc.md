There are no closed form solutions to minimize the cost function Equation (43) at present. Therefore, we use the iterative optimization algorithm (for example, gradient descent method or L-BFGS). After derivation we get gradient formula is as following:

\(\nabla_{\phi_j} J(\phi) = -\frac{1}{L} \sum_{l=1}^L \left[ X^{(i)} \left( \{ 1( y^{(i)} = j ) - p( y^{(i)} = j | X^{(i)}; \phi ) \} \right) \right]\)

Then make the following update operation:

\(\phi_j := \phi_j - \alpha \nabla_{\phi_j} J(\phi), j=1, \cdots, k\)

where, \(\alpha\) denotes learning rate.

# 3) Deep belief network embedded with Softmax regress (DBNESR):-

DBN uses a Markov random field Restricted Boltzmann Machine (RBM) [52] [53] of unsupervised learning networks as building blocks for the multi-layer learning systems and uses a supervised learning algorithm named BP (back propagation) for fine-tuning after pre-training. Its architecture is shown in Figure 7. The deep architecture is a fully interconnected directed belief nets with one input layer v^1, W = {W^1, W^2, ..., W^h} hidden layers h^1, h^2, ..., h^h and one labeled layer at the top. The input layer v^1 has D units, equal to the number of features of samples. The label layer has C units, equal to the number of classes of label vector Y. The numbers of units for hidden layers, currently, are pre-defined according to the experience or intuition. The seeking of the mapping function, here, is transformed to the problem of finding the parameter space W = {W^1, W^2, ..., W^h} for the deep architecture [54].

The semi-supervised learning method based on DBN architecture can be divided into two stages: First, DBN architecture is constructed by greedy layer-wise unsupervised learning using RBM as building blocks. All samples are utilized to find the parameter space W with N layers. Second, DBN architecture is trained according to the log-likelihood using gradient descent method. As it is difficult to optimize a deep architecture using supervised learning directly, the unsupervised learning stage can abstract the hierarchical representations feature effectively, and prevent over-fitting of the supervised training. The algorithm BP is used pass the error top-down for fine-tuning after pre-training.