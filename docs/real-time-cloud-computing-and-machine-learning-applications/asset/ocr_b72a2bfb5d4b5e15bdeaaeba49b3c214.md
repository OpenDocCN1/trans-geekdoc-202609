736 T. P. Fowdar, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoondom

# Table 7.20. (Continued)

| Layer | Function |
|---|---|
| FullyConnected Layer | The input to the fully connected layer is the output from the final Pooling or Convolutional Layer, which is flattened and fed into the fully connected layer. After passing through the fully connected layers, the final layers use the activation function to calculate the output. |
| Output Layer | The output layer has a loss function like categorical cross-entropy, compute the error in prediction. Once the forward pass is complete the backpropagation begins to update the weight and biases for error reduction |
| hiddenActivationFunction | Activation functions perform the final calculation of the layer's outputs, and determine the type of transformation performed by the layers. |
| lossFunction | The loss function is a component of a deep learning algorithm that calculates an error, as a difference of actual (predicted) and desired (target) output of a neural network. |
| randomSeed | Initializes the random number generator with seed to get the same random number sequences. |

Figure 7.12 below shows the architecture of the CNN network used [4][5]. The size of each layer's filter is explained in Table 7.21.

![](bbox=[0.105, 0.448, 0.895, 0.663])

Figure 7.12. CNN Architecture.

# Table 7.21. Network Size Explanation

| Layer | Size | Explanation |
|---|---|---|
| Input | {7,96,1} | The input consists of 96 rows of data for 7 weather parameters in a single channel. |
| Convolutional | {7,1,1} | The size of the convolutional layer filter is chosen as [7,1] so that features from each row can be extracted. |
| Max Pooling | {1,1,1} | Specifying the max-pooling filter as [1,1] allows all output of the convolutional layer to be passed directly to the FullyConnected layer. |
| FullyConnected | {96} | The fully connected layer can calculate the output based on the 96 values from the previous layer. |
| Output | {7} | A size of 7 is chosen since there are 7 weather parameters |