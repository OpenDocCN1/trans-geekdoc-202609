
We have learnt that recurrent neural networks (RNNs) support the processing of sequential data to output the next possible element in the sequence. Since RNNs are prone to vanishing gradient and exploding gradient problems, LSTMs are applied by handling the importance of each of the prior data in the sequence by using different gates. Generally, NAS uses RNNs to handle sequential data, by decoding the sequential outputs to produce more suitable models iteratively. The controllers are designed to navigate the search space more intelligently using convolutional blocks and stacking some of them to design the learning model. A search space with basic convolutions, depth-separable convolutions with different kernel sizes and pooling layers is used to design cells. Here, the convolutional cells that output a feature map of the same size and half-size of the input are defined as normal cells and reduction cells, respectively.

The NAS can be explained in three terms as follows.

1.  **Search space**: set of neural network architectures that solve a given problem.
2.  **Search strategy**: the mechanism used to explore the defined search space for candidate architectures.
3.  **Performance strategy**: evaluate the effectiveness of the architectures that are generalizable or perform well in unseen data.

In the NAS process, a search strategy selects a model from the search space and evaluates the selected architecture’s performance and passes it to the search strategy. NAS predicts hyperparameters, such as the height and width of filters and strides, the number of filters, and skip connections. Each prediction is performed using a `Softmax` activation and passed to the next layer. Additionally, NAS models have been developed with reinforcement learning. Here, also an RNN is used as the controller to sample the search space. After training and evaluating the performance of the sampled architecture, the result is utilized to update the controller using gradient-based methods and the process is iterated until convergence or timeout.

The process of NAS is shown in [Figure 6.13](#ch13.xhtml#f99) and can be listed as follows.

![Figure 6.13 Process of NAS.](html/images/9781032473246_C006_013.jpg)

[Figure 6.13](#ch13.xhtml#f99b) Process of NAS.

1.  Process the search space consists of possible models with predefined operations such as convolutional, fully connected, pooling, and recurrent layers and their connections.
2.  Use a controller to select possible architecture from the search space.
3.  Train the selected architecture for a few epochs.
4.  Evaluate the candidate model and rank them by considering the performance on the validation set.
5.  Use the obtained ranking to rearrange the search and update the controller accordingly to identify new possible models.
6.  Repeat the procedure until the optimal architecture is found to preserve a given condition.
7.  Evaluate the best model on the test dataset.

Neural networks discard some features from the model based on their importance to make decisions. The NAS process discards features from the search pipeline training with hidden layers to identify their importance. Further, it is important to consider model compression when designing NAS. Approaches, such as quantization, pruning, and knowledge distillation, have been used to compress the models.

## 6.7.3 Search Space

This defines a set of feasible solutions for a NAS method. Search space can be configured with the properties gained from prior knowledge of the type of problem to be solved. Thus, although this may lead to human bias, it can simplify the search process and deliver timely results. NAS includes a reinforcement learning-based approach, which is in the discrete space and a gradient-based approach in the continuous space.

The search space can be considered in different types as follows.

### Global Search Space

This covers graphs that represent an entire neural architecture. This search for all possible combinations of operations results in an expensive search space. It combines operations to form a chain or sequence of architectures. The associated parameters are the number of layers, operation type, and the associated hyperparameters. Skip connections are also added to allow multi-branch architectures.

### Cell Search Space / Modular Search Space

The search space is modularized by combining a set of modules that consists of various layers and blocks. The modularization via cells discovers the cell architecture that can be merged to create the neural model as in `ENAS` (efficient NAS). Also, the block diversity can be emphasized by changing the optimizing blocks while holding the remaining blocks fixed as in `FPNAS` (fast and practical NAS). Further, a layer-based search space can be utilized as in `FBNet` (Facebook-Berkeley-Nets). Here, a unique block can be selected by each searchable layer across the search space.

### Stochastic NAS (SNAS) Space

A collection of one-hot random variables from a fully factorizable joint distribution make up stochastic NAS (SNAS) space. By loosening the architecture distribution with concrete distribution, gradient optimization is made possible, making this search space differentiable.

Generally, we assume that the possible architectures are in a discrete space. Differentiable architecture search (`DART`) is utilized to convert the space into a continuous and differentiable form. It represents each node in a directed acyclic graph (`DAG`) to convert the module-based space into a continuous space. Here, each `DAG` has two input nodes and one output node and is created by sequentially connecting *N* nodes. The transformation is performed by representing the discrete set of operations as a `Softmax` that gives a sequential set of probabilities. As another method, neural architecture optimization (`NAO`) can be used. Here, by mapping a discrete search space to a continuous space, an optimal embedded encoding can be obtained utilizing gradient optimization. The best continuous representation is then discretized into the final architecture using a decoder. These one-shot techniques, `DARTS` and `NAO`, use supermodels to determine the ideal designs.

The search space can be designed in different architectures as shown in [Figure 6.14](#ch13.xhtml#f100). For instance, chained-structured neural networks have convolution and pooling layers chained up. Modern implementations use more elements such as separable convolutions and dilated convolutions where the parameters determine the conditional space. Multi-branch networks and cell-based search are widely used in image classification applications.

![Figure 6.14 Sample architectures in the search space.](html/images/9781032473246_C006_014.jpg)

[Figure 6.14](#ch13.xhtml#f100b) Sample architectures in the search space.

The search space can be either coarsely granular, where a block consists of many layers, or more finely granular, where one layer with a given kernel size. The architectural search is more adaptable with the finer-grained procedures, enabling the generation of more complex designs. However, the search results will take longer to converge as a result, and preliminary results might not be ideal. As long as the search strategy starts with a sound initial architecture, a coarser search space can leverage ‘neural blocks’ based on the domain’s current knowledge to get better predictions with fewer iterations. However, in the long term, applying finer-granular search space is more flexible than the neural blocks, as the finer-granular process can independently find such neural blocks and subsequently enhance them.

## 6.7.4 Search Strategies of NAS
