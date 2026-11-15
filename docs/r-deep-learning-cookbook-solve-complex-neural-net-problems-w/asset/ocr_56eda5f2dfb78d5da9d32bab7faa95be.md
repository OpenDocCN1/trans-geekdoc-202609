# Getting ready

This section provides the requirements for TensorFlow.

+   - The dataset is loaded and set up
+   - Load the TensorFlow package using the following script:

```
require(tensorflow)
```

# How to do it...

This recipe covers the steps for setting up Deep belief network (DBM):

+   1. Define the number of nodes in each hidden layer as a vector:

```
RBM_hidden_sizes = c(900, 500 , 300 )
```

+   2. Generate an RBM function leveraging the codes illustrated in the Setting up a Restricted Boltzmann Machine for Bernoulli distribution input recipe with the following input and output parameters mentioned:

| Type of Parameter | Parameter name | Parameter description |
|---|---|---|
| Input (Pre RBM) | input_data | Matrix of train MNIST data |
| Input (Pre RBM) | num_input | Number of independent variables |
| Input (Pre RBM) | num_output | Number of nodes in the corresponding hidden layer |
| Input (Pre RBM) | epochs | Number of iterations |
| Input (Pre RBM) | alpha | Learning rate for updating weight matrix |
| Input (Pre RBM) | batchsize | Number of observations per batch run |
| Output (Post RBM) | output_data | Matrix of reconstructed output |
| Output (Post RBM) | error_list | List of reconstruction errors for every run of 10 batch |
| Output (Post RBM) | weight_list | List of weight matrices for every run of 10 batch |
| Output (Post RBM) | weight_final | Matrix of final weights obtained after all epochs |
| Output (Post RBM) | bias_final | Vector of final biases obtained after all epochs |

Here is the function for setting up up the RBM:

```
RBM <- function(input_data, num_input, num_output, epochs = 5,
alpha = 0.1, batchsize=100){
# Placeholder variables
```