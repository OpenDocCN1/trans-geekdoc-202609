
## Modeling Techniques

Let's go over some basic terminology in neural networks that you might see in exam questions.

### Artificial Neural Network

Artificial neural networks (ANNs) are the simplest type of neural network; they have one hidden layer. A feedforward neural network is a classic example of an ANN. They are mainly used for supervised learning where the data is mostly numerical and structured, such as, for example, regression problems. See [Figure 7.4](#c07.xhtml#c07-fig-0004).

![FIGURE 7.4 Artificial or feedforward neural network](images/c07f004.png)

**FIGURE 7.4** Artificial or feedforward neural network

### Deep Neural Network (DNN)

Deep neural networks (DNNs) can be defined as ANNs with additional depth—that is, an increased number of hidden layers between the input and the output layers. A neural network with usually at least two layers qualifies as a DNN, or `deep net` for short. See [Figure 7.5](#c07.xhtml#c07-fig-0005) to understand DNN.

![FIGURE 7.5 Deep neural network](images/c07f005.png)

**FIGURE 7.5** Deep neural network

### Convolutional Neural Network

Convolutional neural networks (CNNs) are a type of DNN network designed for image input. CNNs are most well‐suited to image classification tasks, although they can be used on a wide array of tasks that take images as input.

### Recurrent Neural Network

Recurrent neural networks (RNNs) are designed to operate upon sequences of data. They have proven to be very effective for natural language processing problems where sequences of text are provided as input to the model. RNNs have also seen some modest success for time‐series forecasting and speech recognition. The most popular type of RNN is the long short‐term memory (LSTM) network. LSTMs can be used in a model to accept a sequence of input data and make a prediction, such as to assign a class label or predict a numerical value like the next value or values in the sequence.

Neural networks are trained using stochastic gradient descent and require that you choose a loss function when designing and configuring your model. A loss is a number indicating how bad the model's prediction was on a single example. If the model's prediction is perfect, the loss is zero; otherwise, the loss is greater. The goal of training a model is to find a set of weights and biases that have low loss, on average, across all examples. The loss function is one of the important components of neural networks. Loss is nothing but a prediction error of neural net. And the method to calculate the loss is called loss function. In simple words, the loss is used to calculate the gradients. And gradients are used to update the weights of the neural net.

### What Loss Function to Use

Importantly, the choice of loss function is directly related to the activation function used in the output layer of your neural network. These two design elements are connected. [Table 7.2](#c07.xhtml#c07-tbl-0002) summarizes the loss functions based on ML problems.

**TABLE 7.2** Summary of loss functions based on ML problems

| | Output | Output Layer Configuration or Activation Function | Loss Functions |
|---|---|---|---|
| Regression problem | Numerical output | One node with a linear activation unit | Mean squared error (MSE) |
| Binary classification problem | Binary outcome | Sigmoid activation unit | Binary cross‐entropy, categorical hinge loss, and squared hinge loss (Keras) |
| Multiclass classification problem | Single label multiclass | Softmax activation function | Categorical cross‐entropy (on one‐hot encoded data) and sparse categorical cross‐entropy (apply on integers) |

The following is an example code snippet of TensorFlow multiclass classification. The model must have one node for each class in the output layer and use the softmax activation function. The loss function `sparse_categorical_crossentropy` is appropriate for integer encoded class labels (e.g., 0 for one class, 1 for the next class, etc.).

```
# define model
model = Sequential()
model.add(Dense(10, activation='relu', kernel_initializer='he_normal', input_shape=(n_features,)))
model.add(Dense(8, activation='relu', kernel_initializer='he_normal'))
model.add(Dense(3, activation='softmax'))

# compile the model
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])
```

### Gradient Descent

The gradient descent algorithm calculates the gradient of the loss curve at the starting point. The gradient of the loss is equal to the derivative (slope) of the curve. The gradient has both magnitude and direction (vector) and always points in the direction of the steepest increase in the loss function. The gradient descent algorithm takes a step in the direction of the negative gradient in order to reduce loss as quickly as possible.

### Learning Rate

As we know, the gradient vector has both a direction and a magnitude. Gradient descent algorithms multiply the gradient by a scalar known as the learning rate (also sometimes called `step size`) to determine the next point. For example, if the gradient magnitude is 2.5 and the learning rate is 0.01, then the gradient descent algorithm will pick the next point 0.025 away from the previous point.

### Batch

In gradient descent, a batch is the total number of examples you use to calculate the gradient in a single iteration. So far, we've assumed that the batch has been the entire dataset. A very large batch may cause even a single iteration to take a very long time to compute.

### Batch Size

Batch size is the number of examples in a batch. For example, the batch size of SGD is 1, while the batch size of a mini‐batch is usually between 10 and 1,000. Batch size is usually fixed during training and inference; however, TensorFlow does permit dynamic batch sizes.

### Epoch

An epoch means an iteration for training the neural network with all the training data. In an epoch, we use all of the data exactly once. A forward pass and a backward pass together are counted as one pass. An epoch is made up of one or more batches.

### Hyperparameters

We covered loss, learning rate, batch size, and epoch. These are the hyperparameters that you can change while training your ML model. Most machine learning programmers spend a fair amount of time tuning the learning rate.

*   If you pick a learning rate that is too small, learning will take too long.
*   Conversely, if you specify a large batch size, the model might take more time to compute.

#### Tuning Batch Size

The following are the best practices for tuning batch size:

*   A smaller mini‐batch size (not too small) usually leads not only to a smaller number of iterations of a training algorithm than a large batch size but also to a higher accuracy overall; that is, a neural network that performs better, in the same amount of training time. Our parallel coordinate plot also makes a key trade‐off very evident: larger batch sizes take less time to train but are less accurate.
*   If batch size is too small, training will bounce around; if it's too large, training will take a very long time.
*   However, using a smaller batch size lets your gradient update more often per epoch, which can result in a larger decrease in loss per epoch. Furthermore, models trained using smaller batches generalize better.

#### Tuning Learning Rate

It is important to achieve a desirable learning rate for the following reasons:

*   Both low and high learning rates result in wasted time and resources.
