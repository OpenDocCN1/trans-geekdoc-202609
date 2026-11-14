
**Second phase**: The feed backward pass process is executed in which the input layer `v` is reconstructed to `v'` using the activated hidden state. Following this, the input is reconstituted by activating the hidden state. Consequently, the inaccuracy `E` is calculated and used to modify the weight `W[adjusted]` as follows (Equations 16.26 and 16.27):

```
E = v' - v
```

```
W[adjusted] = v * E * 0.1
```

where, 0.1 is the learning rate.

After completing all the steps, the pattern responsible for activating the hidden neurons is obtained.

RBM is trained using Gibbs sampling and contrastive divergence. Gibbs sampling is a Markov chain Monte Carlo approach for getting a sequence of observations approximating a defined multivariate probability distribution in statistics when direct sampling is impossible.

If the input is represented by `v` and the hidden value by `h`, then the prediction is `p(h|v)`. With knowledge of the hidden values, `p(v|h)` is utilised to anticipate the regenerated input values. Suppose this procedure is performed `k` times, and after `k` iterations, the initial input value `v0` is transformed into `vk`.

Contrastive divergence is an approximation maximum-likelihood learning approach used to approximate the gradient, which is the graphical slope depicting the link between a network’s weights and its error. In situations where we cannot directly evaluate a function or set of probabilities, an inference model is used to approximate the algorithm’s learning gradient and determine the direction in which to move. In contrastive divergence, updated weights are utilised. After calculating the gradient from the reconstructed input, delta is added to the previous weights to create the new weights.

### 16.8.2 Advantages and Drawbacks of RBM

RBM benefits are that they are expressive and computationally efficient. Due to connectivity restrictions, this Boltzmann machine is faster. Hidden layer activations can improve the performance of other models.

RBM drawbacks are that in RBM energy gradient function calculation makes training harder and contrastive divergence `k` is a less-known RBM algorithm than backpropagation. Also weight adjustments are a mentionable drawback of RBM.

## 16.9 Deep Belief Networks (DBNs)

A deep belief network is a type of DNN which is made of multiple layers of hidden units, in which the layers are well connected but not the hidden units. DBNs were developed to overcome the slow learning, local minima pitfalls in a typical neural network. DBNs were first presented as probabilistic generative models in ([Larochelle, Erhan, Courville, Bergstra, & Bengio, 2007](#ch16.xhtml#ref16_1)) as an alternative to the discriminative character of conventional neural networks.

A DBN is made up of several layers of neural networks, commonly known as Boltzmann machines. Let’s examine the example below. Each layer of the restricted Boltzmann machine (RBM) in this interconnects with both the layers before it and the layers after it. It implies that the nodes of a single layer will not be able to communicate horizontally. It is obvious that there can only be one visible layer and one hidden layer for each Boltzmann machine.

A belief network is a directed acyclic graph with stochastic variables. A schematic overview of a deep belief net is as shown in the following diagram ([Figure 16.25](#ch16.xhtml#fig16_25)).

![Figure 16.25 Schematic overview of a DBN.](images/fig16_25_B.jpg)

[Figure 16.25 Schematic overview of a DBN.](#ch16.xhtml#R_fig16_25)

There are two types of problems that can be solved by DBN: (1) the inference problem: determining the states of unobserved variables; and (2) the learning problem: modifying the interactions between variables so that the network is more likely to produce the observed data.

### 16.9.1 Creation of a Deep Belief Network

Each record type includes the restricted Boltzmann machines (RBMs) that compose the layers of the network, the vector representing the size of the layers or the number of classes that are included in the representative data set in the case of classification DBN.

The DBN record merely reflects a model that is comprised of stacked RBMs. Because of this, it is possible to train the top layer to generate class labels corresponding to the input data vector as well as to classify data vectors that have not yet been entered.

Learning a deep belief network (DBN) is made significantly easier by the fact that it is constructed up of RBMs that are taught in an unsupervised fashion. The amount of time spent on RBM training accounts for the vast majority of the total time spent on DBN training.

During the training session the bottom layer is trained first. Then propagation of the data set happens through learned RBM. At last, the newly transformed data set is used as the training data for the next RBM. CDBNs, which stands for convolutional deep belief networks, need the observation labels to be available during the training of the top layer.

The training session continues until the data set has been propagated through the last but one trained RBM. The altered data set is created after this point by concatenating the labels generated so far, and the top-layer associative memory will be trained using the altered dataset.

### 16.9.2 Benefits and Drawbacks of Deep Belief Networks

#### 16.9.2.1 Benefits

Utilizing hidden layers in a productive manner is easy with DBN (higher performance gain by adding layers compared to multilayer perceptron). DBN has a particular strength in classification resilience (size, position, color, view angle—rotation). The neural network approach developed by DBN can be applied to a variety of different applications and kinds of data. DBN continues to produce the greatest performance results despite the enormous volume of data being processed. DBN’s features are routinely gathered, and their settings are fine-tuned to provide the best possible results. DBN avoids time taking procedures.

#### 16.9.2.2 Drawbacks

There are certain hardware requirements for DBN, and DBN demands vast data to conduct better approaches. Because of its intricate data models, DBN requires a significant investment to train. There must be hundreds of different machines. Classifiers are necessary for DBN in order to comprehend the output.

#### 16.9.2.3 Applications of DBN

DBN is widely used for object detection. The DBN is able to identify occurrences of specific classes of things. Image creation is another application for DBN. DBN is also used commonly for image classification. DBN also detects video. It is able to capture motion. DBN is capable of understanding natural language, also known as speech processing, in order to provide a complete description. DBN estimates human poses. DBN is utilised extensively throughout data sets.

## 16.10 Applications

### 16.10.1 Deep Learning for Vision

Computer vision is a subfield of machine learning concerned with the interpretation and comprehension of images and videos. It helps computers to view and perform visual tasks similar to human beings. Computer vision models translate visual data into contextful features which allow models to evaluate images and videos. Such interpretations are then used for decision-making tasks. In computer vision, deep learning approaches are delivering on their promise. Computer vision is not “solved,” but deep learning is required to solve many difficult challenges in the field at the cutting edge. Let’s have a look at three instances to illustrate the results that deep learning may achieve in the field of computer vision:
