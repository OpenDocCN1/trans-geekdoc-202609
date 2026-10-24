
to edges of the input image.¹ The output (i.e., the learned feature from the edges of the first hidden layer) of the second hidden layer might correspond to contours or corners of the input image. The output (i.e., the learned feature from the edges and contours of the second hidden layer) of the third hidden layer might correspond to parts of the objects (e.g., nose, car wheel) of the input image. Finally, the output layer can easily learn a classifier to recognize different objects based on the object parts at the output layer. For text mining, we can build a type of deep neural network called recurrent neural networks (it will be introduced in Section 10.4) to classify text documents into different categories. The first layer might take the raw characters as input and output the tokens (e.g., words, punctuation); the second layer might take the tokens as input and output phrases; and the final output layer might take the phrases as input and output category that the input document belongs to. While it is very difficult to directly train a classifier (e.g., logistic regression for object recognition or document categorization) based on the raw features of the input data (e.g., the raw pixels of images, the characters of documents), a deep neural network decomposes this task into a sequence of interdependent subtasks (one at each hidden or output layer), each of which learns a semantically more meaningful feature from the feature at the previous layer).

On the one hand, the core algorithmic framework to train a deep neural network, namely **backpropagation** algorithm, has largely remained the same as for the traditional feed-forward neural networks with only a few hidden layers. Therefore we will first introduce this algorithm in Section 10.1.2. On the other hand, it becomes significantly more challenging to train a deep neural network due to its increased number of layers. We will introduce such challenges in Section 10.1.3 and the solutions to handle these challenges in Section 10.2.

Deep learning is closely related to **representation learning**, which aims to automatically learn effective representation (i.e., features, attributes) from the input data to facilitate data mining tasks (e.g., classification, clustering). Notice that the scope of representation learning is broader than deep learning, in that there exist nonneural network methods to automatically learn representation from the input data. An example is principal component analysis (introduced in Chapter 2), where each principal component, a linear combination of the input attributes, can be viewed as a learned new feature.

## 10.1.2 Backpropagation algorithm

For the example in Fig. 10.3, the weights and bias values are given. However, how can we automatically learn such parameters, including the weight vectors and the bias scalars, from the training tuples? A foundational technique is called **backpropagation** algorithm. Backpropagation learns by iteratively processing a data set of training tuples, comparing the network’s prediction for each tuple with the actual known *target* value. The target value may be the known class label of the training tuple (for classification problems) or a continuous value (for numeric prediction). For each training tuple, the weights as well as the bias values are modified so as to minimize the difference or the disagreement (e.g., mean-squared loss) between the network’s prediction and the actual target value. These modifications are made in the “backward” direction (i.e., from the output layer) through each hidden layer down to the first hidden layer (hence the name *backpropagation*). Although it is not guaranteed, in general, the weights will often eventually converge, when the learning process stops. The algorithm is summarized

### Algorithm: Backpropagation. Neural network learning for classification or numeric prediction, using the backpropagation algorithm.

- Input:
  - D, a data set consisting of the training tuples and their associated target values;
  - η, the learning rate;
  - network, a multilayer feed-forward network.

Output: A trained neural network (i.e., the weights w<sub>ij</sub> and bias b<sub>j</sub> for each hidden or output unit).

- Method:
  - (1) Initialize all weights and biases in network;
  - (2) while terminating condition is not satisfied {
  - (3) for each training tuple X with target output T in D {
  - (4) // Propagate the inputs forward:
  - (5) for each input layer unit j {
  - (6) O<sub>j</sub> = I<sub>j</sub>; // output of an input unit is its actual input value
  - (7) for each hidden or output layer unit j {
  - (8) I<sub>j</sub> = Σ<sub>i</sub> w<sub>ij</sub> O<sub>i</sub> + b<sub>j</sub>; // compute the net input of unit j with respect to the units of the previous layer, i
  - (9) O<sub>j</sub> = 1 / (1 + e<sup>-I<sub>j</sub></sup>); // compute the output of each unit j (sigmoid activation)
  - (10) // Backpropagate the errors:
  - (11) for each unit j in the output layer
  - (12) δ<sub>j</sub> = O<sub>j</sub>(1 − O<sub>j</sub>)(T<sub>j</sub> − O<sub>j</sub>); // compute the error (mean-squared loss)
  - (13) for each unit j in the hidden layers, from the last to the first hidden layer
  - (14) δ<sub>j</sub> = O<sub>j</sub>(1 − O<sub>j</sub>)(Σ<sub>l</sub> δ<sub>l</sub>w<sub>jl</sub>); // compute the error with respect to the next higher layer, l
  - (15) for each weight w<sub>ij</sub> in network {
  - (16) Δw<sub>ij</sub> = ηδ<sub>j</sub>O<sub>i</sub>; // weight increment
  - (17) w<sub>ij</sub> = w<sub>ij</sub> − Δw<sub>ij</sub>; // weight update
  - (18) for each bias b<sub>j</sub> in network {
  - (19) Δb<sub>j</sub> = ηδ<sub>j</sub>; // bias increment
  - (20) b<sub>j</sub> = b<sub>j</sub> − Δb<sub>j</sub>; // bias update
  - (21) }

### FIGURE 10.4 Backpropagation algorithm.

in Fig. 10.4. The steps involved are expressed in terms of inputs I<sub>i</sub>, outputs O<sub>i</sub>, and errors δ<sub>i</sub> and may seem awkward if this is your first look at neural network learning. However, once you become familiar with the process, you will see that each step is inherently simple. The steps are described next. Note that the algorithm described in Fig. 10.4 uses the mean-squared loss and sigmoid activation function. We can generalize the algorithm in Fig. 10.4 with other types of loss functions or activation functions.

Initialize the weights: The weights in the network are initialized to small random numbers (e.g., ranging from –1.0 to 1.0 or –0.5 to 0.5). Each unit has a bias associated with it, which are similarly initialized to small random numbers. An important aspect for initializing the model parameters is to break symmetry. For the example in Fig. 10.5, both U<sub>3</sub> and U<sub>4</sub> are connected to the same input units (U<sub>1</sub> and U<sub>2</sub>). Therefore it is critical to make sure that the initial weights for U<sub>3</sub> are different from those for U<sub>4</sub>, i.e., w<sub>13</sub> ≠ w<sub>14</sub> and w<sub>23</sub> ≠ w<sub>24</sub>. Otherwise, U<sub>3</sub> and U<sub>4</sub> become unidentifiable; that is, their weights will be updated in the same way and thus will always be the same. Other than random initialization, in the next section, we will introduce an effective strategy, called “pretraining,” which presets the weights and scalars in a certain way.

Each training tuple, X, has a target output T, which could be the actual class label for the classification task or the numerical value for the regression task. It is processed by the following steps. See Fig. 10.5 for a pictorial illustration.

**Propagate the inputs forward:** First, the training tuples are fed to the network’s input layer. The inputs pass through the input units, unchanged. That is, for an input unit, j, its output, O<sub>j</sub>, is equal to its input value, I<sub>j</sub>. Next, the net input and output of each unit in the hidden and output layers are computed. The net input to a unit in the hidden or output layers is computed as a linear weighted sum of its inputs. To help illustrate this point, a hidden layer or output layer unit is shown in Fig. 10.2. Each such unit has a number of inputs to it that are, in fact, the outputs of the units connected to it in the previous layer. Each connection has a weight. To compute the net input to the unit, each input connected to the unit is multiplied by its corresponding weight, and this is summed. Given a unit, j in a hidden or output layer, the net input, I<sub>j</sub>, to unit j is

```
I_j = \sum_i w_{ij} O_i + b_j,
```

where w<sub>ij</sub> is the weight of the connection from unit i in the previous layer to unit j; O<sub>i</sub> is the output of unit i from the previous layer; and b<sub>j</sub> is the bias of the unit. The bias acts as a threshold to adjust the net input of the unit.<sup>2</sup>

Each unit in the hidden and output layers takes its net input and then applies an activation function to it, as illustrated in Fig. 10.2. The function symbolizes the activation of the neuron represented by the unit. Here, the sigmoid function is used. (Recall that in Chapter 6, we have used the sigmoid function to train the logistic regression classifier.) Given the net input I<sub>j</sub> to unit j, then O<sub>j</sub>, the output of unit j, is computed as

```
O_j = \frac{1}{1 + e^{-I_j}}.
```

This function is also referred to as a squashing function, because it maps a large input domain onto the smaller range of 0 to 1. The sigmoid function is nonlinear and differentiable, allowing the backpropagation algorithm to model classification problems that are linearly inseparable.

We compute the output values, O<sub>j</sub>, for each hidden layer, up to and including the output layer, which gives the network’s prediction. In practice, it is a good idea to cache (i.e., save) the intermediate output values at each unit as they are required again later when backpropagating the error. This trick can substantially reduce the amount of computation required.

**Backpropagate the error:** The error is propagated backward to reflect the accuracy of the current network’s prediction, which in turn is used to update the weights and biases. For a unit j in the output layer, the error \delta_j is computed by

```
\delta_j = O_j(1 - O_j)(O_j - T_j),
```

To see this, we can conceptually think of the bias b<sub>j</sub> as the bias scalar in a linear regression model. In other words, it tells the default (i.e., biased) value of the net input I<sub>j</sub>, without any output from the previous layer (i.e., O<sub>i</sub> = 0).
