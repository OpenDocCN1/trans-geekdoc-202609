
- Using adaptive learning rate in backpropagation can help accelerate the algorithm convergence or prevent oscillation. Commonly used strategies include setting the learning rate to be in reverse proportion to the epoch number or the magnitude of the accumulated historical gradients.

- Dropout is an effective strategy to improve the generalization performance of backpropagation algorithm. At each epoch, it randomly drops some nonoutput units and uses the remaining network to update the model parameters.

- Pretraining presets the initial model parameters of a deep neural network in a suitable region. It helps accelerate the backpropagation algorithm convergence and improves the generalization performance. A commonly used pretraining strategy is supervised greedy pretraining, which gradually adds hidden layers and pretrains the parameters of the newly added layers while fixing the parameters of the previously added layers.

- For classification tasks, it is more common to use cross-entropy as the loss function to train a deep neural network. Cross-entropy can help alleviate the gradient vanishing problem even when the unit is saturated.

- Convolutional neural networks (CNNs) are effective deep learning models for grid-like data, such as images. The key operation in CNNs is convolution. Given an input and a kernel, the convolution generates a feature map, where the kernel is shared across different entries of the input. A convolution layer consists of a set of kernels, often followed up with a nonlinear activation and a pooling operation. A CNN model is the neural network with at least one convolutional layer.

- Recurrent neural networks (RNNs) are effective deep learning models for sequential data, such as text. There are three main types of units in an RNN model, including input unit, hidden unit, and output unit. The three input-to-hidden weight matrix, hidden-to-hidden weight matrix, and hidden-to-output weight matrix are shared across different time stamps. A major challenge of RNNs is long-term dependence. The long short-term memory (LSTM) is one of the most successful techniques to address the long-term dependence. The key component of LSTM is the cell state in each LSTM cell, which is designed to accumulate the information in the past for a long time and meanwhile use the current information to update the cell state. LSTM achieves these design objectives through three gates, including the forget gate, the input gate, and the output gate. Attention mechanism is another effective way to address long-term dependence.

- The goal of graph neural networks (GNNs) is to use neural networks to map nodes of a graph to low-dimensional vectors called node embeddings. An effective type of GNNs is graph convolutional networks (GCNs). Given an input graph with node attributes, a GCN model uses a set of weight matrices, one weight matrix for each layer, to produce the node embeddings. The key operations in each layer of GCNs include propagation, linear transformation, and nonlinear activation.

## 10.7 Exercises

### 10.1
The following table consists of training data from an employee database. The data have been generalized. For example, “31 ... 35” for age represents the age range of 31 to 35. For a given row entry, count represents the number of data tuples having the values for department, status, age, and salary given in that row.

| department | status | age | salary | count |
|---|---|---|---|---|
| sales | senior | 31 ... 35 | 46K ... 50K | 30 |
| sales | junior | 26 ... 30 | 26K ... 30K | 40 |
| sales | junior | 31 ... 35 | 31K ... 35K | 40 |
| systems | junior | 21 ... 25 | 46K ... 50K | 20 |
| systems | senior | 31 ... 35 | 66K ... 70K | 5 |
| systems | junior | 26 ... 30 | 46K ... 50K | 3 |
| systems | senior | 41 ... 45 | 66K ... 70K | 3 |
| marketing | senior | 36 ... 40 | 46K ... 50K | 10 |
| marketing | junior | 31 ... 35 | 41K ... 45K | 4 |
| secretary | senior | 46 ... 50 | 36K ... 40K | 4 |
| secretary | junior | 26 ... 30 | 26K ... 30K | 6 |

Let status be the class-label attribute.

- a. Design a multilayer feed-forward neural network for the given data. Label the nodes in the input and output layers.

- b. Using the multilayer feed-forward neural network obtained in (a), show the weight values after one iteration of the backpropagation algorithm, given the training instance “(sales, senior, 31 ... 35, 46K ... 50K).” Indicate your initial weight values and biases and the learning rate used.

### 10.2
- a. Derivatives of various activation functions. Show how the derivatives of activation functions, including sigmoid, tanh, and ELU in Table 10.6, are derived in mathematical details.

- b. Backpropagation algorithm. Consider a multilayer feed-forward neural network as shown in Fig. 10.5 with sigmoid activation and mean-squared loss function L. Prove (1) Eq. (10.3) for computing the error in the output unit (δ10); (2) Eq. (10.4) for computing the errors in hidden units δ9 and δ6; (hint: consider the chain rule); and (3) Eq. (10.5) for updating weights (hint: consider the derivative of the loss with respect to weights).

- c. Relation between different activation functions. Given the sigmoid function σ(I) = 1/(1+e^-I) and hyperbolic tangent function tanh(I) = (e^I - e^-I)/(e^I + e^-I), show in mathematics how tanh(I) can be transformed from sigmoid through shifting and re-scaling.

### 10.3
Feed-forward neural networks. In this exercise, we implement a feed-forward neural network for a binary classification task. The goal is to predict whether the e-mail is spam (labeled as 1) or not (0) according to its attributes (e.g., word frequency, length of uninterrupted sequence of capital letters). The detailed description of the data set can be found at http://archive.ics.uci.edu/ml/datasets/Spambase. To complete this exercise, you are required to

- a. construct a multilayer feed-forward neural network for the spam prediction task and evaluate the model from the following perspectives, including prediction accuracy, F1 score, and AUC-ROC curve;

- b. compare the performance of the models with various activation functions and different depth/width.

### 10.4
Autoencoder. Autoencoder is a classic type of neural networks for unsupervised learning.

- a. Demonstrate that PCA is a special case of the autoencoder by showing that the loss function of PCA is equivalent to the mean-squared error of the autoencoder with linear activation, where the encoder and decoder share the same parameters.

- b. Implement an autoencoder with nonlinear activation, and use (1) mean-squared-error and (2) binary cross-entropy loss, each data point should be normalized into [0, 1]. Compare them with PCA on the MNIST data set, which can be found at http://yann.lecun.com/exdb/mnist/, in terms of classification accuracy and the visualization of reconstructed images. For the classification task, first use the autoencoder or PCA to obtain the features of the data and then train a linear SVM or logistic regression model using the features.

### 10.5
Dropout. (a) Explain why dropout can be used to mitigate the overfitting problem. (b) Suppose we have a simple two-layer neural network y = W2(W1x + b1) + b2 where x ∈ R3, W1 ∈ R2×3, b1 ∈ R2, W2 ∈ R2 and b2 ∈ R. How many possible dropout networks are there that are not disconnected?

### 10.6
Pretraining on autoencoder.

- a. Why pretraining helps the learning or converge?

- b. How to pretrain an autoencoder?

### 10.7
Loss functions. Consider the following two loss functions, including (1) mean-squared error Loss(T, O) = 1/2(T - O)^2, and (2) cross-entropy Loss(T, O) = -T log O - (1 - T) log (1 - O) for binary classification. Assume the activation function is sigmoid.

- a. Show the derivation of the error δ for the output unit in backpropagation process and compare the two loss functions (e.g., potential problems they might produce).

- b. Now, we wish to generalize the cross-entropy loss to the scenario of multiclass classification. The target output is a one-hot vector of length C (i.e., the number of total classes), and the index of nonzero element (i.e., 1) represents the class label. The output is also a vector of the same length O = [O1, O2, ..., OC]. Show the derivation of the categorical cross-entropy loss and the error δ of the output unit. (hint: there are two key steps, including (1) normalizing the output values by scaling between 0 and 1, and (2) deriving the cross entropy loss following the definition for the binary case where the loss can be represented as Loss(T, O) = - \sum_{i=1}^C T_i log(O_i).)

### 10.8
What are the key differences between CNNs and feed-forward neural networks? Why are CNNs widely used on grid-like data?

### 10.9
2-D convolution. Given the input and two kernels as shown in Fig. 10.43,

- a. compute the feature maps by applying kernel K1, K2 (stride is defined as 1, and zeros are padded around I), respectively;

- b. re-compute the feature maps if the stride is 2;

- c. compute the new feature maps after we apply a downsampling process, max pooling, and average pooling (filter size is 2 x 2), respectively, to the obtained feature maps in (a).

### 10.10
Training LSTM. It is usually hard to train LSTM on long sequences, answer the following questions:

- a. Why it is hard to train LSTM?

- b. How to mitigate the problem?

### 10.11
LSTM and GRU Compare LSTM with GRU, and answer the following questions:

- a. What are they have in common?

- b. What are the differences between them?

- c. What are the pros and cons of them?

### 10.12
Suppose we apply graph convolutional networks (GCNs) on grid-like graphs (e.g., images) without normalizing adjacency matrix (i.e., removing Steps 2–3 in Fig. 10.38). Explain why it is essentially a 2-D convolution with a special type of filters.
