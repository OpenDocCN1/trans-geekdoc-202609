viewed as a down-sampling process that reduces the data dimension. The FC layer performs a liner transformation between the weights and 1-D vectors formed from the final CONV layer by a flatten way. A network with only FC layers commonly can be called a multilayer perceptron (MLP).

CONV operation is generally followed by BN operation, which can normalize the distribution of input of each layer to reduce the training time and improve the generalization ability of the network. Then the activation function comes closely after BN, which introduces the ability to fit nonlinearity to network through some special functions such as ReLU, sigmoid, etc.

# ## 6.2.2 Binary neural network

Complex CNN can extract complex feature information for difficult machine learning tasks. Nevertheless, the more complex the network model, the more difficult the deploying it on an embedded mobile device due to the huge memory and power consumption. The binary neural network (BNN) is the most extreme scheme that constrains both weights and activations to ±1, and its quantification method is implemented as either probabilistic or deterministic sign function [5].

To store weights within only 1 bit on hardware, we convert −1 to 0 and 1 to 1 by affine transformation, respectively, which can transform MAC operations to XNOR and popcount operations, i.e., performing bitwise XNOR between weights and inputs, and counting the number of 1s in the intermediate result after XNOR operation. The convolution of BNN is formulated as

\(\mathbf{Y} = \mathbf{B}_x \otimes \mathbf{B}_w + \mathbf{b},\quad (6.1)\)

where \(\otimes\) indicates XNOR-POPCOUNT operation, \(\mathbf{B}_x\) is the binary input, \(\mathbf{B}_w\) is a binary weight associated with that input, and \(\mathbf{b}\) is the neuron bias.

The BN operation and binarized activation function come closely after CONV layer. The sign activation function of BNN [5] is defined as

\(\mathbf{B}_y = sign(\mathbf{Y}) = \begin{cases} +1, & \mathbf{Y} \ge 0, \\ -1, & \mathbf{Y} < 0. \end{cases}\quad (6.2)\)

This implies that we only need to take out the sign bit of the intermediate result to implement the nonlinear activation. Further, we combine