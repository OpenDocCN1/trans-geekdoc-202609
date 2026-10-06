
## Chapter 4: Machine Learning

- 3. Select the appropriate learning algorithm.
- 4. Define and tune hyperparameters during training.
- 5. Validate the results, making trade-offs and determining the readiness of the solution for deployment and production use.

Other than the core responsibility of training a model, these human tasks are integral and of great importance to the successful design, development, and deployment of an ML solution. In this section, we briefly discuss some of the key responsibilities in selecting the appropriate ML algorithm and defining the right hyperparameters during training. In the appendix of this book, we discuss the design of a multilayer perceptron neural network and a CNN algorithm, going through the steps discussed in this chapter.

Advances in the deep learning community have led to the innovation of new network architectures. Different architectures have developed specific use cases by better emulating biological processes for tasks like image and language understanding. As such, new techniques, coupled with the advances in computing technologies and big data, have proved to be highly successful when applied to specific tasks. For example, CNNs are primarily used for image processing, but they also can be used for other types of input such as audio. Composing a complete and comprehensive list of all existing network architectures is practically impossible, as new architectures are being developed all the time, and there is no comprehensive summary of all existing neural network architectures. Liu et al. discuss widely used deep learning architectures and their practical applications, providing a deeper discussion of autoencoders, CNNs, deep belief networks, and restricted Boltzmann machines [35]. While it is by no means comprehensive list, Leijen et al., from the Asimov Institute, also identify and describe some salient neural network architectures. These architectures are captured in figure 4 [36]. Our objective is to expose the reader to the variety of neural network architectures that exist today and the different functions they serve, not to give an exhaustive list.

One important advancement in neural networks (captured in figure 4.15) is the development of generative adversarial networks (GANs). GANs, introduced by Goodfellow et al. in 2014, are a class of ML frameworks in which two neural networks compete in a zero-sum game [37]. One network, called the "generator," creates new instances of data with the same statistics as the training set, while the other network, called the "discriminator," evaluates the authenticity of these new instances of data. The training objective of the discriminative network is to evaluate the data (i.e., belonging to the training set) or not, while the objective of the generative network is to increase the error rate of the discriminator. Both discriminator and generator seek to optimize different and opposing objective functions, which enables the model to learn in an unsupervised manner. GANs have many practical applications, such as image, video, and voice generation.

## A mostly complete chart of neural networks

![](img/3a09e5358d763329b6e01a25dd2312d4_131_0.png)

Figure 4.15 Neural network architectures. Source: Lejnen and van Veen (2020).

Similarly, the introduction of the transformer architecture has been revolutionary to the recent advancements in the fields of natural-language generation. The architecture was first introduced in 2017 by a team at Google in a paper titled “Attention Is All You Need,” and it has since become a state-of-the-art technique in the field of natural language processing (NLP) [38]. The transformer network has an encoder and decoder structure that uses a self-attention mechanism to capture long-term dependencies in the input data, making it possible to process longer sequences efficiently and effectively. This approach achieves superior quality and performance over previous models such as recurrent neural networks (RNNs) and short-term memory (LSTM) networks. Another benefit of this new transformer approach is that it lends itself to a parallel architecture, suitable for GPU architectures. The novel architecture for processing sequential data, such as natural-language text, has motivated many variants and extensions, such as BERT, GPT-3, and GPT-4 [39, 40].

Upon selecting a specific neural architecture for a given task, model owners have several “knobs” available to them that must be defined before the iterative process of training and validating the performance of the model. These knobs, formally known as “hyperparameters,” are the configuration variables that govern the training process; they include things like the number of layers, number of nodes, activation function, iterations, and batch size of your model. Decisions on these configuration variables will have a subsequent impact on how efficiently and effectively your model is able to learn. The process of training a model involves initializing and tuning these hyperparameters to ensure that the model learns the optimal parameters (i.e., weights and biases) that will allow it to achieve the desired predictive performance. “Tuning” refers to the process of adjusting these variables until the desired model performance is achieved. This will require an iterative process of running your training job, looking at the metrics, and adjusting the configuration variables to improve model performance and arrive at the optimal values.

It’s important to note the differences between parameters and hyperparameters. Hyperparameters are not learned by the model itself from the data, and they must be explicitly defined and iteratively tuned by the model owner before training. On the contrary, parameters are internal to the model and represent the attributes that are learned or estimated by the model from the training process, such as the weights and biases of the neural network.

## 4.5: Designing a Neural Network

### Table 4.3 Hyperparameters when designing a neural network

| Hyperparameter | Definition |
| --- | --- |
| Learning rate | The rate at which the gradient descent searches for a global minimum. |
| Epoch | A pass through the full training or validation data forward and backward. |
| Batch size | The subset of data used in the training or validation stages. The larger the batch size, the more the processing can be done in parallel using GPUs. |
| Iteration | The number of batches to complete one node. |
| Activation function | A function used to determine the output of a node given an input or set of inputs |
| Cost or loss function | A function used to determine the penalty for an error |
| Train/test split ratio | The split of data used for training and testing a model. A common split strategy might be 90% train, 10% test, but could vary (e.g., 70/30, 80/20, or 85/15). |
| Network depth | A measure of the number of hidden and visible layers in a neural network. |
| Dropout | Refers to the dropping-out of units (hidden and visible) in a neural network, usually done to prevent overfitting. |
| Initialized weights and biases | While weights and biases are parameters learned by the model during the training process, model owners must initialize weights and biases. It is common for weights to be initialized and biases to be set to 0. |

important general purposes hyperparameters that model owners should be mindful of when designing a neural network.

It's important to note that specific network architectures may introduce their own sets of additional hyperparameters that must be initialized and tuned. For example, we will see in the discussion of CNNs in section 4.6 that we will have to initialize and tune hyperparameters specific to the convolutional layer of the network, as the kernel size and stride. As the complexity of the network increases, the task of defining and tuning hyperparameters becomes more challenging. While there are best practices and guidelines that can help improve the tuning process, designing a neural network and tuning hyperparameters is a complex task that requires both scientific understanding and experience.
