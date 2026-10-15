
## Linear Behavior

The rectifier function mostly looks and acts like a linear activation function. In general, a neural network is easier to optimize when its behavior is linear or close to linear.

> Rectified linear units [...] are based on the principle that models are easier to optimize if their behavior is closer to linear.

— Page 194, *Deep Learning*, 2016.

Key to this property is that networks trained with this activation function almost completely avoid the problem of vanishing gradients, as the gradients remain proportional to the node activations.

> Because of this linearity, gradients flow well on the active paths of neurons (there is no gradient vanishing effect due to activation non-linearities of sigmoid or tanh units).

— *Deep Sparse Rectifier Neural Networks*, 2011.

## Train Deep Networks

Importantly, the (re-)discovery and adoption of the rectified linear activation function meant that it became possible to exploit improvements in hardware and successfully train deep multilayered networks with a nonlinear activation function using backpropagation. In turn, cumbersome networks such as Boltzmann machines could be left behind as well as cumbersome training schemes such as layer-wise training and unlabeled pre-training.

> ... deep rectifier networks can reach their best performance without requiring any unsupervised pre-training on purely supervised tasks with large labeled datasets. Hence, these results can be seen as a new milestone in the attempts at understanding the difficulty in training deep but purely supervised neural networks, and closing the performance gap between neural networks learnt with and without unsupervised pre-training.

— *Deep Sparse Rectifier Neural Networks*, 2011.

## 7.1.5 Tips for Using the Rectified Linear Activation

In this section, we'll take a look at some tips when using the rectified linear activation function in your own deep learning neural networks.

### Use ReLU as the Default Activation Function

For a long time, the default activation to use was the sigmoid activation function. Later, it was the tanh activation function. For modern deep learning neural networks, the default activation function is the rectified linear activation function.

Prior to the introduction of rectified linear units, most neural networks used the logistic sigmoid activation function or the hyperbolic tangent activation function.

— Page 195, Deep Learning, 2016.

Most papers that achieve state-of-the-art results will describe a network using ReLU. For example, in the milestone 2012 paper by Alex Krizhevsky, et al. titled *ImageNet Classification with Deep Convolutional Neural Networks*, the authors developed a deep convolutional neural network with ReLU activations that achieved state-of-the-art results on the ImageNet photo classification dataset.

> ... we refer to neurons with this nonlinearity as Rectified Linear Units (ReLUs).
> Deep convolutional neural networks with ReLUs train several times faster than their equivalents with tanh units.

If in doubt, start with ReLU in your neural network, then perhaps try other piecewise linear activation functions to see how their performance compares.

> In modern neural networks, the default recommendation is to use the rectified linear unit or ReLU

— Page 174, Deep Learning, 2016.

### Use ReLU with MLPs, CNNs, but Probably Not RNNs

The ReLU can be used with most types of neural networks. It is recommended as the default for both Multilayer Perceptron (MLP) and Convolutional Neural Networks (CNNs). The use of ReLU with CNNs has been investigated thoroughly, and almost universally results in an improvement in results, initially, surprisingly so.

> ... how do the non-linearities that follow the filter banks influence the recognition accuracy. The surprising answer is that using a rectifying non-linearity is the single most important factor in improving the performance of a recognition system.

— What is the best multi-stage architecture for object recognition?, 2009.

Work investigating ReLU with CNNs is what provoked their use with other network types.

> [others] have explored various rectified nonlinearities [...] in the context of convolutional networks and have found them to improve discriminative performance.

— Rectified Linear Units Improve Restricted Boltzmann Machines, 2010.

When using ReLU with CNNs, they can be used as the activation function on the filter maps themselves, followed then by a pooling layer.

> A typical layer of a convolutional network consists of three stages [...] In the second stage, each linear activation is run through a nonlinear activation function, such as the rectified linear activation function. This stage is sometimes called the detector stage.

— Page 339, Deep Learning, 2016.

Traditionally, LSTMs use the tanh activation function for the activation of the cell state and the sigmoid activation function for the node output. Given their careful design, ReLU was thought to not be appropriate for Recurrent Neural Networks (RNNs) such as the Long Short-Term Memory Network (LSTM) by default.

At first sight, ReLUs seem inappropriate for RNNs because they can have very large outputs so they might be expected to be far more likely to explode than units that have bounded values.

> — *A Simple Way to Initialize Recurrent Networks of Rectified Linear Units*, 2015.

Nevertheless, there has been some work on investigating the use of ReLU as the output activation in LSTMs, the result of which is a careful initialization of network weights to ensure that the network is stable prior to training. This is outlined in the 2015 paper titled *A Simple Way to Initialize Recurrent Networks of Rectified Linear Units*.

### Try a Smaller Bias Input Value

The bias is the input on the node that has a fixed value. The bias has the effect of shifting the activation function and it is traditional to set the bias input value to 1.0. When using ReLU in your network, consider setting the bias to a small value, such as 0.1.

> ... it can be a good practice to set all elements of [the bias] to a small, positive value, such as 0.1. This makes it very likely that the rectified linear units will be initially active for most inputs in the training set and allow the derivatives to pass through.

— Page 193, *Deep Learning*, 2016.

There are some conflicting reports as to whether this is required, so compare performance to a model with a 1.0 bias input.

### Use *He* Weight Initialization

Before training a neural network, the weights of the network must be initialized to small random values. When using ReLU in your network and initializing weights to small random values centered on zero, then by default half of the units in the network will output a zero value.

> For example, after uniform initialization of the weights, around 50% of hidden units continuous output values are real zeros

— *Deep Sparse Rectifier Neural Networks*, 2011.

There are many heuristic methods to initialize the weights for a neural network, yet there is no best weight initialization scheme and little relationship beyond general guidelines for mapping weight initialization schemes to the choice of activation function. Prior to the wide adoption of ReLU, Xavier Glorot and Yoshua Bengio proposed an initialization scheme in their 2010 paper titled *Understanding the difficulty of training deep feedforward neural networks* that quickly became the default when using sigmoid and tanh activation functions, generally referred to as *Xavier initialization*. Weights are set at random values sampled uniformly from a range proportional to the size of the number of nodes in the previous layer (specifically +/- $\frac{1}{\sqrt{n}}$ where $n$ is the number of nodes in the prior layer). Kaiming He, et al. in their 2015 paper titled *Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification* suggested that Xavier initialization and other schemes were not appropriate for ReLU and extensions.

Glorot and Bengio proposed to adopt a properly scaled uniform distribution for initialization. This is called “Xavier” initialization [...]. Its derivation is based on the assumption that the activations are linear. This assumption is invalid for ReLU

— *Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification*, 2015.

They proposed a small modification of Xavier initialization to make it suitable for use with ReLU, now commonly referred to as *He initialization* (specifically +/- $\frac{2}{\sqrt{n}}$ where $n$ is the number of nodes in the prior layer). In practice, both Gaussian and uniform versions of the scheme can be used.

### Scale Input Data

It is good practice to scale input data prior to using a neural network. This may involve standardizing variables to have a zero mean and unit variance or normalizing each value to the scale 0-to-1. Without data scaling on many problems, the weights of the neural network can grow large, making the network unstable and increasing the generalization error. This good practice of scaling inputs applies whether using ReLU for your network or not.

### Use Weight Penalty

By design, the output from ReLU is unbounded in the positive domain. This means that in some cases, the output can continue to grow in size. As such, it may be a good idea to use a form of weight regularization, such as an L1 or L2 vector norm.

Another problem could arise due to the unbounded behavior of the activations; one may thus want to use a regularizer to prevent potential numerical problems. Therefore, we use the L1 penalty on the activation values, which also promotes additional sparsity

— *Deep Sparse Rectifier Neural Networks*, 2011.

This can be a good practice to both promote sparse representations (e.g. with L1 regularization) and reduced generalization error of the model.

## 7.1.6 Extensions and Alternatives to ReLU

The ReLU does have some limitations. Key among the limitations of ReLU is the case where large weight updates can mean that the summed input to the activation function is always negative, regardless of the input to the network. This means that a node with this problem will forever output an activation value of 0.0. This is referred to as a *dying ReLU*.
