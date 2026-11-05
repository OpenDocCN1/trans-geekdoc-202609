
## 1.5.1 MULTILAYER PERCEPTRON

A feedforward neural network (`FFNN`) is a directed acyclic graph (`DAG`) with an input layer, an output layer, and one or more layers in between called hidden layers. The nodes in the input layer have no parent nodes, and the nodes in the output layer have no children nodes. The inputs are either learned or extracted from the data. These models are the most widely used by hyperscalers, in particular (but not exclusively), for recommender systems.

An `MLP` is a vanilla `FFNN` with affine layers, also called fully connected layers, with each layer followed by an activation function. An affine layer is composed of units that linearly combine the weighted outputs or activations from the previous layer plus a bias (the bias is considered another weight). Using multiple layers enables the `MLP` model to represent complex nonlinear functions \[HSW89\]. Geometrically, an `MLP` model attempts to map one vector space to another vector space, where the data is linearly separable, via multiple nonlinear transformations, as shown in [Figure 1.2](#11_Chapter01.xhtml#fig1-2). In this new manifold, the last `FFNN` layer is a linear classifier that separates most of the data from different classes.

[Figure 1.6](#11_Chapter01.xhtml#fig1-6) shows a four-layer `MLP` used for digit classification with Layer 0 having `D^((0)) = 784` units corresponding to each pixel (the input image has 28 × 28 pixels), Layers 1 and 2 are hidden units having `D^((1)) = 128` and `D^((2)) = 32` units, and Layer 3 having `D^((3)) = 10` units corresponding to the 10 possible digits, where `D^((l))` is the number of units or dimensions of Layer `l`. In [Section 1.6](#11_Chapter01.xhtml#sub1-6), we detail how to train this model. In practice, a `CNN` model is a better choice for digit classification; we use an `MLP` model to introduce this type of topology with a simple example.

![image](images/fig1_6.png)

Figure 1.6: An `MLP` with four layers: the input layer, two hidden layers, and the output layer. This model maps the 784 pixel values to a probability distribution over 10 possible classes.

## 1.5.2 CONVOLUTIONAL NEURAL NETWORK

A `CNN` is a special type of `FFNN` widely used for computer vision applications, such as image classification, image detection, image similarity, semantic segmentation, human pose estimation, action recognition, and image feature extraction. Commercial applications include facial recognition, visual search, optical character recognition for document scanning, X-ray tumor detection, drug discovery, and MRI analysis. [Figure 1.7](#11_Chapter01.xhtml#fig1-7) shows the input to a `CNN` and the output activations at each layer. Convolutional units are explained in detail in [Section 2.3](#12_Chapter02.xhtml#sub2-3), and various `CNN` models used in production are discussed in [Section 3.2](#13_Chapter03.xhtml#sub3-2).

`CNN`s are also used as image feature extractors; the output of one of the last layers (usually the second-to-last layer) is used as a feature vector representing the image. This vector becomes the input to other algorithms, such as an `RNN` to generate a textual description of the image, or to a reinforcement agent learning to play a video game, or to a recommender system that uses visual similarity.

## 1.5.3 RECURRENT NEURAL NETWORK

An `RNN` is a directed graph with nodes along a temporal or contextual sequence to capture the temporal dependencies. `RNN` models are used with sequential data common in language tasks and time-series forecasting. Commercial applications include stock price forecasting, text summarization, next-word recommendation, language translation, simple chatbot tasks, image description generation, speech recognition, and sentiment analysis.

![image](images/fig1_7.png)

Figure 1.7: A `CNN` model with several layers maps the input image to a probability distribution across multiple possible labels. Source: \[Wik15\] (CC BY-SA 4.0).

![image](images/fig1_8.png)

Figure 1.8: An `RNN` topology can be represented as an `FFNN` topology with the same weights `W` across all the layers.

The `RNN`s inputs and outputs can vary in length, unlike in `MLP` and `CNN` models. For instance, in machine translation, the input and output sentences have a different number of words. An `RNN` can be unrolled and represented as an `FFNN` sharing the same weights across the layers, as shown in [Figure 1.8](#11_Chapter01.xhtml#fig1-8).

`RNN` models can be stacked with multiple layers and also bidirectional, as shown in [Figure 1.9](#11_Chapter01.xhtml#fig1-9). The main building block of an `RNN` model is a recurrent unit that captures a representation or “memory” of the aggregated relevant data from previous steps. There are three main types of `RNN` models depending on the type of recurrent units they use: vanilla `RNN`, `LSTM`, and `GRU` units, detailed in [Section 2.5](#12_Chapter02.xhtml#sub2-5). In the literature, the term `RNN` denotes either a `vanilla RNN` or, more broadly, these three types of models. In this book, when referring to a vanilla `RNN` model, we explicitly use the term vanilla `RNN` to prevent confusion. `LSTM` and `GRU` models are usually favored over vanilla `RNN` models for their superior statistical performance.

`RNN` models have two significant challenges: (1) capturing the dependencies in long sequences and (2) parallelizing the computation (due to the sequential nature where the output at a given timestep depends on the previous timestep). Using attention layers, detailed in [Section 2.8](#12_Chapter02.xhtml#sub2-8), mitigates these challenges. Concatenating multiple sequential outputs from the first layer in the stack and passing those as inputs to the second layer in the stack improves the computational efficiency in a model with multiple layers \[HSP+19\].

![image](images/fig1_9.png)

Figure 1.9: A bidirectional `RNN` model with two layers.

## 1.5.4 TRANSFORMER NETWORKS

A transformer model learns how various parts of the input affects the output using an attention module. These models are also called attention-based models and have gained wide adoption for language tasks with similar applications to `RNN`s. They mitigate the challenges with `RNN`s discussed in the previous section at the expense of additional computations. The attention module can capture dependencies across long sequences. A transformer model consumes the entire sequence at once and uses multiple `FFNN`s in parallel together with attention modules to learn a set of weights corresponding to the influence between inputs and outputs \[VSP+17\]. For instance, in machine translation, the attention weights capture how each word in the output (target) language is influenced by both the neighboring words and the words in the input (source) language. The attention module is explained further in [Section 2.8](#12_Chapter02.xhtml#sub2-8), and various transformer-based models used in production are discussed in [Section 3.3](#13_Chapter03.xhtml#sub3-3).

## 1.5.5 GRAPH NEURAL NETWORK
