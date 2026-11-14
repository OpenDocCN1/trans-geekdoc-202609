
Consider an input set with the dimensions (`m`, `n`), where `m` represents the number of training examples and `n` represents the number of features present in each example. The weights of size (`n`, `C`), where `C` is the number of clusters, are first initialized. The winning vector (the weight vector with the shortest distance from the training example, for example, the Euclidean distance) is then updated after iterating over the input data for each training example. Weight update is decided by the following (Equation 16.25):

```
**W**[**i****j**] = **W**[**i****j**](**o****l****d**) + *α*(**T**)(**X**[**i****k**] - **O****l****d**)**W**[**i****j**]
```

where `i` stands for the `i`th feature of the training example, `j` is the winning vector, `α` is the learning rate at time `t`, and `k` is the `k`th training example from the input data. The SOM network is trained, and trained weights are utilised to cluster new examples. A new example is included in the collection of successful vectors.

Thus the various steps explained previously are summarized as follows:

1. Initialization of weight
2. For epochs ranging from 1 to `N`
3. Pick a training instance
4. Determine the winning vector
5. A winning vector update
6. For each training example, repeat steps 3, 4, and 5
7. Creating a test sample cluster

#### 16.7.2.1 An Illustration of the Training of a Self-Organizing Map

The small white disc represents the current training datum, which is taken from the distribution of the training data represented by the blue blob. The SOM nodes are initially placed in the data space at random (seen on the left side of [Figure 16.23](#ch16.xhtml#fig16_23)). The node that is closest to the training datum is chosen (grey shaded concentric circle in first figure). It has been relocated toward the training datum, along with (to a lesser extent) its grid neighbours. The grid usually approximates the data distribution after several rounds (right).

![Figure 16.23 Illustration of SOM working.](images/fig16_23_B.jpg)

[Figure 16.23 Illustration of SOM working.](#ch16.xhtml#R_fig16_23)

### 16.7.3 Options for Initialization

For all iterative artificial neural network techniques, including self-organizing maps, choosing beginning weights that are good approximations of the final weights is a well-known difficulty. The initial idea for random weight initiation came from Kohonen. Principal component initialization, in which the initial map weights are selected from the space of the first principal components, has gained popularity more recently since the results can be precisely replicated.

However, it was discovered that the benefits of principle component initialization are not always the case when random initialization and principal component initialization were carefully compared for a one-dimensional map. The shape of the particular data set determines which initialization technique is appropriate. When the principal curve fitting the data set could be univalently and linearly projected on the first principal component, principle component initialization was preferred (for a one-dimensional map) (quasi linear sets). Random initiation, however, fared better for nonlinear data sets.

A SOM can be interpreted in many different ways. Similar items frequently fire nearby neurons because in the training phase, the weights of the entire neighbourhood are moved in the same direction. In order to create a semantic map, SOM places similar samples together and dissimilar samples away.

The alternative interpretation is to consider neuronal weights as pointing devices to the input region. They represent a discrete approximation of the training sample distribution. Whereas fewer neurons point when there are few training examples, more neurons point where there are more training samples.

Principal components analysis may be thought of as a nonlinear generalization in the context of SOM (PCA). SOM was not developed at first as an answer to an optimization issue. However, there have been numerous attempts to alter the SOM description and create an optimization problem that yields comparable outcomes.

#### 16.7.3.1 Drawbacks to Kohonen Maps

Model preparation takes a long time, and training against slowly changing data is challenging. The model does not grasp how data is formed because it does not create a generative model for the data. When utilizing categorical data, it does not behave well, and when using mixed-type data, it behaves even worse.

## 16.8 Restricted Boltzmann Machines (RBMs)

The restricted Boltzmann machine, which belongs to the domain of unsupervised learning algorithms, was invented in 1985 by Geoffrey Hinton. RBM is a network of symmetrically connected neuron-like units that generate stochastic decisions.

To ahead understand RBM, we must be aware of Boltzmann machines. A Boltzmann machine is a type of neural network in which each neuron is linked to each and every other neuron in the network. RBM is composed of two layers: the visible layer (`v`), also known as the input layer, and the concealed layer (`h`). A layer for output is not present in the Boltzmann machine. Boltzmann machines are a type of neural network that is both random and generative. They are capable of learning internal representations, modelling complex combinatory problems, and solving such problems, provided that they are given enough time. The Boltzmann distribution (Gibbs distribution) of thermodynamics explains the effect of factors such as entropy and temperature on quantum states, and hence these models based on Boltzmann distribution are also referred to as energy-based models (EBMs) ([Figure 16.24](#ch16.xhtml#fig16_24)).

![Figure 16.24 Restricted Boltzmann machine with three visible units and four hidden units (no bias units).](images/fig16_24_B.jpg)

[Figure 16.24 Restricted Boltzmann machine with three visible units and four hidden units (no bias units).](#ch16.xhtml#R_fig16_24)

The restricted Boltzmann machine, a variant of the Boltzmann machine, is a stochastic two-layered neural network that belong to a class of energy-based models that may automatically find intrinsic data patterns by reconstructing input. It has two apparent and concealed layers. The visible layer consists of input nodes (nodes that receive input data), while the hidden layer is composed of nodes that extract feature information from the data, and the output at the hidden layer is a weighted sum of the input layers. They have no output nodes and no usual binary output via which patterns are learned, which may seem peculiar. The learning process occurs without the capability that differentiates them. We are just concerned with input nodes and are not concerned with hidden nodes. RBMs automatically record all patterns, parameters, and correlations between data once input is provided.

Important characteristics of the Boltzmann machine are as follows.

1. The structure is recurrent and symmetric.
2. In their learning process, RBMs attempt to link low energy states with high likelihood and vice versa.
3. No intra layer connections exist.
4. It is an unsupervised learning algorithm, meaning it draws conclusions from unlabeled input data.

### 16.8.1 Working of Restricted Boltzmann Machine

There are two phases in RBM via which the entire RBM process operates:

* **First phase**: The input layer (`v`) is utilised to activate the hidden layer (`h`) utilizing the concepts of weights and bias. This method is known as the feed forward pass. In this phase any positive and negative associations between the `v` and `h` are discovered.
