
In the following section of this chapter, the relationship between `DL`, machine learning (`ML`), and `AI` has been discussed. A brief introduction to artificial neural network (`ANN`) with its classification and its different learning techniques has been specified in Section 1.3. As part of classification of `ANN`, feedforward neural networks (`FFNNs`) and recurrent neural networks (`RNNs`) with their uses have been discussed. While in the section of learning techniques, supervised, unsupervised, and reinforcement learning are briefly considered. Section 1.4 has been reserved to discuss about `DL`. It has been stated clearly in this section why the term “deep” has been used. Multiple points have been identified, which makes `DL` as state of the art. In Section 1.6, different activation functions such as sigmoid activation function, hyperbolic tangent activation function, rectified linear unit (`ReLU`) activation function, and softmax activation function are described in detail. There are many `DL` architectures available in literature. Few of them became very popular and offers high accuracy resulting in better performance. The concepts of restricted Boltzmann machine (`RBM`), deep belief network (`DBN`), autoencoder (`AE`), and convolutional neural network (`CNN`) are deliberated in this section. In Section 1.6, multiple `ML` platforms from different organizations have been furnished. All of them provide cloud infrastructures with high-performance graphics processing units (`GPUs`) to quicken the training of `DL` network with the huge volumes of data, which lessens the training time from weeks to hours. The last section of this chapter is dedicated for describing different steps of using IBM `ML` platform – IBM Watson Studio (formerly, Data Science Experience or `DSX`).

## 1.2 AI versus ML versus DL

`AI` is a subcategory of computer science that handles the simulation of intelligent activities in computers. `AI` is a computer system, which can accomplish responsibilities that usually need human acumen. Generally, a rule engine leads the `AI` system and a good `AI` system should have an intelligent rule engine, which is based on a series of meaningful IF–THEN statements. Since the 1950s, `AI` has been successfully used in visual perception, speech recognition, decision-making, and translation between languages. `AI` and `ML` are often used interchangeably, especially in the realm of big data.

As shown in [Figure 1.1](#bodymatter-001.xhtml#b_9783110670905-001_fig_001), `DL` is considered as a subcategory of `ML` and again `ML` is a subcategory of `AI`. In other words, all `DL` is `ML`, but not all `ML` is `DL`, and so forth.

![Figure 1.1: Relationship between AI, ML, and DL.](graphic/converted/b_9783110670905-001_fig_001.png)

Figure 1.1: Relationship between AI, ML, and DL.

`ML`, flourished since the 1980s, is a subset of `AI` but dynamic in nature and does not require human intervention to make certain changes. Symbolic logic is an example of `AI` but not considered as `ML`. As per the definition given by Tom Mitchel \[[6](#bodymatter-001.xhtml#b_9783110670905-001_ref_006)\], “A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P if its performance at tasks in T, as measured by P, improves with experience E.” In `ML` programs, there is no need of following IF–THEN rule engine, rather they can adjust themselves in response to the data they are exposed to, which has been termed as learning. Learning can be of three types, as explained in the subsequent section.

As `DL` is the subset of both `AI` and `ML`, all the characteristics of `AI` and `ML` are propagated to `DL` inherently. It deals with the large amount of data applying on `ANN`. Statistics propose that the accrued volume of data will grow from 4.4 zettabytes to roughly 44 zettabytes in 2020. That is why sometimes it has been called as deep neural network.

## 1.3 Artificial neural network

An `ANN` is an information processing system that has several performance features in common with biological neurons. An `ANN` is characterized by \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]

1. its design pattern between the neurons, called architecture;

2. its technique of determining the weights on the connections, called learning algorithm;

3. its activation functions.

The artificial neuron as shown in [Figure 1.2](#bodymatter-001.xhtml#b_9783110670905-001_fig_002) is the basic building block or processing unit of an `ANN`.

![Figure 1.2: An artificial neuron.](graphic/converted/b_9783110670905-001_fig_002.png)

Figure 1.2: An artificial neuron.

### 1.3.1 Classification of ANN

Primarily, `ANN`s can be classified into two categories \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]: `FFNN`s and `RNN`s.

#### 1.3.1.1 Feedforward neural network

The movement of signals in `FFNN` is in the forward pathway only. As there is no feedback loop, its behavior is independent of historical input and responds only to its current involvement. There are primarily two types of `FFNN`, as depicted below.

##### 1.3.1.1.1 Single-layer feedforward network

This is the simplest form of a layered network ([Figure 1.3](#bodymatter-001.xhtml#b_9783110670905-001_fig_003)) which has only one input layer of source nodes that portrays onto an output layer of computation nodes. Its inputs are associated with the outputs through a sequence of single-layer weights. Adaptive linear neuron, Hopfield network, and learning vector quantization are common examples of single-layer feedforward network.

![Figure 1.3: Single-layer feedforward network.](graphic/converted/b_9783110670905-001_fig_003.png)

Figure 1.3: Single-layer feedforward network.

##### 1.3.1.1.2 Multilayer feedforward network

This type of feedforward network has one input layer, one output layer, and one or more hidden layers. By connecting these neurons as shown in [Figure 1.4](#bodymatter-001.xhtml#b_9783110670905-001_fig_004), the network is empowered to evaluate higher order information.

![Figure 1.4: Multilayer feedforward network.](graphic/converted/b_9783110670905-001_fig_004.png)

Figure 1.4: Multilayer feedforward network.

#### 1.3.1.2 Recurrent neural network

In the architecture of an `RNN` ([Figure 1.5](#bodymatter-001.xhtml#b_9783110670905-001_fig_005)), it should have minimum one feedback loop (can also be self-feedback). There are numerous varieties of recurrent networks based on the pattern of the feedback. In a specific situation, the network can have a single layer of neurons with each neuron feeding its output signal back to the inputs of all other neurons. Other types of recurrent networks may have self-feedback loops with hidden neurons. Hopfield network, bidirectional associative memory, brain state in a box, and adaptive resonance theory are few examples of `RNN`.

![Figure 1.5: Recurrent network.](graphic/converted/b_9783110670905-001_fig_005.png)

Figure 1.5: Recurrent network.

### 1.3.2 ANN learning

To acquire knowledge from environment and to improve the network’s performance through learning is the most significant property of a neural network (`NN`). This process indicates the subsequent order of actions \[[7](#bodymatter-001.xhtml#b_9783110670905-001_ref_007)\]:

* Stimulation by an environment

* Changing free parameters as an outcome of stimulation

* Responding in a better means to the environment

#### 1.3.2.1 Unsupervised learning
