# Getting ready

This section provides the requirements for TensorFlow.

+   * The dataset is loaded and set up
+   * The TensorFlow package is set up and loaded

# How to do it...

This section covers the steps for setting up a feed-forward backpropagation Neural Network:

+   1. Let's define the input parameters of the neural network as function parameters.
+   The following table describes each parameter:

| Parameter name | Parameter description |
|---|---|
| Xdata | Matrix of train input MNIST data |
| Ydata | Matrix of train output MNIST data |
| Xtestdata | Matrix of test input MNIST data |
| Ytestdata | Matrix of test output MNIST data |
| input_size | Number of attributes (or pixels) in train data |
| learning_rate | Learning rate for updating weight matrix |
| momentum | Increment in size of steps to jump out of local minima |
| epochs | Number of iterations |
| batchsize | Number of observations per batch run |
| rbm_list | List of outcomes of stacked RBM |
| dbn_sizes | Vector of sizes of hidden layers in stacked RBM |

The neural network function will have a structure as shown in the following script:

```
NN_train <- function(Xdata, Ydata, Xtestdata, Ytestdata, input_size,
learning_rate=0.1,momentum = 0.1,epochs=10,
batchsize=100,rbm_list,dbn_sizes) {
library(stringi)
```