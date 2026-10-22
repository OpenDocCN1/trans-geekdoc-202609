search, or neural architecture search (NAS) for neural networks, as it searches for the optimal model architecture.

A NAS setup consists of three components:

# A search space

Defines possible model architectures—i.e., building blocks to choose from and constraints on how they can be combined.

# A performance estimation strategy

To evaluate the performance of a candidate architecture without having to train each candidate architecture from scratch until convergence. When we have a large number of candidate architectures, say 1,000, training all of them until convergence can be costly.

# A search strategy

To explore the search space. A simple approach is random search—randomly choosing from all possible configurations—which is unpopular because it’s prohibitively expensive even for NAS. Common approaches include reinforcement learning (rewarding the choices that improve the performance estimation) and evolution (adding mutations to an architecture, choosing the best-performing ones, adding mutations to them, and so on).28

For NAS, the search space is discrete—the final architecture uses only one of the available options for each layer/operation,29 and you have to provide the set of building blocks. The common building blocks are various convolutions of different sizes, linear, various activations, pooling, identity, zero, etc. The set of building blocks varies based on the base architecture, e.g., convolutional neural networks or transformers.

In a typical ML training process, you have a model and then a learning procedure, an algorithm that helps your model find the set of parameters that minimize a given objective function for a given set of data. The most common learning procedure for neural networks today is gradient descent, which leverages an optimizer to specify how to update a model’s weights given gradient updates.30 Popular optimizers are, as you probably already know, Adam, Momentum, SGD, etc. In theory, you can include optimizers as building blocks in NAS and search for one that works best. In practice, this is difficult to do, since optimizers are sensitive to the setting of

28 Barret Zoph and Quoc V. Le, “Neural Architecture Search with Reinforcement Learning,” arXiv, November 5, 2016, https://oreil.ly/FhsuQ; Esteban Real, Alok Aggarwal, Yanping Huang, and Quoc V. Le, “Regularized Evolution for Image Classifier Architecture Search,” AAAI 2019, https://oreil.ly/FWYjn.

29 You can make the search space continuous to allow differentiation, but the resulting architecture has to be converted into a discrete architecture. See “DARTS: Differentiable Architecture Search” (Liu et al. 2018).

30 We cover learning procedures and optimizers in more detail in the section “Basic ML Reviews” in the book’s GitHub repository.