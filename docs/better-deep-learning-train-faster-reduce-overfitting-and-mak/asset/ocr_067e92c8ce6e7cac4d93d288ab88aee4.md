Traditionally, LSTMs use the tanh activation function for the activation of the cell state and the sigmoid activation function for the node output. Given their careful design, ReLU were thought to not be appropriate for Recurrent Neural Networks (RNNs) such as the Long Short-Term Memory Network (LSTM) by default.

At first sight, ReLUs seem inappropriate for RNNs because they can have very large outputs so they might be expected to be far more likely to explode than units that have bounded values.

> > — *A Simple Way to Initialize Recurrent Networks of Rectified Linear Units*, 2015.

Nevertheless, there has been some work on investigating the use of ReLU as the output activation in LSTMs, the result of which is a careful initialization of network weights to ensure that the network is stable prior to training. This is outlined in the 2015 paper titled *A Simple Way to Initialize Recurrent Networks of Rectified Linear Units*.

# Try a Smaller Bias Input Value

The bias is the input on the node that has a fixed value. The bias has the effect of shifting the activation function and it is traditional to set the bias input value to 1.0. When using ReLU in your network, consider setting the bias to a small value, such as 0.1.

> > ... it can be a good practice to set all elements of [the bias] to a small, positive value, such as 0.1. This makes it very likely that the rectified linear units will be initially active for most inputs in the training set and allow the derivatives to pass through.
> >
> > — Page 193, *Deep Learning*, 2016.

There are some conflicting reports as to whether this is required, so compare performance to a model with a 1.0 bias input.

# Use *He* Weight Initialization

Before training a neural network, the weights of the network must be initialized to small random values. When using ReLU in your network and initializing weights to small random values centered on zero, then by default half of the units in the network will output a zero value.

> > For example, after uniform initialization of the weights, around 50% of hidden units continuous output values are real zeros
> >
> > — *Deep Sparse Rectifier Neural Networks*, 2011.

There are many heuristic methods to initialize the weights for a neural network, yet there is no best weight initialization scheme and little relationship beyond general guidelines for mapping weight initialization schemes to the choice of activation function. Prior to the wide adoption of ReLU, Xavier Glorot and Yoshua Bengio proposed an initialization scheme in their 2010 paper titled *Understanding the difficulty of training deep feedforward neural networks* that quickly became the default when using sigmoid and tanh activation functions, generally referred to as *Xavier initialization*. Weights are set at random values sampled uniformly from a range