Here, i = h0 ; P(hk-1|hk) is a conditional distribution of reconstructed visible units on the hidden layers of the RBM at level k; P(hm-1, hm) is the joint distribution of hidden and visible units (reconstructed) at the final RBM layer of the DBN. The following image illustrates a DBN of four hidden layers, where W represents the weight matrix:

![](bbox=[0.244, 0.202, 0.757, 0.528])

DBNs can also be used to enhance the robustness of DNNs. DNNs face an issue of local optimization while implementing backpropagation. This is possible in scenarios where an error surface features numerous troughs, and the gradient descent, due to backpropagation occurs inside a local deep trough (not a global deep trough). DBNs, on the other hand, perform pretraining of the input features, which helps the optimization direct toward the global deep trough, and then use backpropagation, to perform a gradient descent to gradually minimize the error rate.

**Training a stack of three RBMs:** In this recipe, we will train a DBN using three stacked RBMs, where the first hidden layer will have 900 nodes, the second hidden layer will have 500 nodes, and the third hidden layer will have 300 nodes.