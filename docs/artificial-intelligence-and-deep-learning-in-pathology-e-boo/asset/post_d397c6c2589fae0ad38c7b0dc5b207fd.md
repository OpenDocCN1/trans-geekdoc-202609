
![](img/ec668102bd6cbe5645156f246a7c2e8b_36_0.png)

**FIGURE 2.9**  
An artificial neuron (which is an abstraction in a computer program, rather than a physical entity) is diagrammed in 9A. Each of the inputs *x* is modified by a weight *w* and then summed just as the synaptic inputs would be in a real neuron. This sum **Σ** is passed to an activation function, φ and if it exceeds the value of the function’s threshold θ it is passed on as an output 1. In this schematic, (Σ and φ) together are the analogs to a biological neuron. Chrislb, Creative Commons. For comparison, a biological neuron is shown in 9B.  
*(NickGorton-commonswiki).*

This artificial neuron, which is the basic building block of most of the artificial networks of deep learning, is a great oversimplification in the following ways. Since the mathematical analysis of pulse-based coding is difficult, the model neuron receives as input a single steady value at each dendrite that is connected to an upstream neuron (there are spiking artificial neural networks (ANNs), but they are not in widespread use). The signal variability during learning is represented by a set of weights associated with the signals, and these weights change as the neural network learns. Another important difference between a biological and a modern ANN is that in the former, the threshold is based upon a simple off-on ramp, whereas in the latter, a smooth curve such as a sigmoid or similar kind of function is used.

Initially, sigmoid functions were used as the transfer function. The curve for a typical sigmoid function is shown in Fig. 2.10. The sigmoid’s value ranges from zero to one. The sigmoid is a continuous, nonlinear differentiable function. Note that, unlike the Heaviside, the activation threshold can be any value we choose in its range. Current ANNs often use other functions, such as the hyperbolic tangent function or the rectified linear function (ReLU) as well. As we shall see, in a neural network weights are adjusted by a process that involves finding the minimum of a loss function through the use of calculus, and so the threshold must be a continuous function. Additionally, the function must allow the network to deal with nonlinear relationships. One of the criticisms of the earlier neural networks shortly after they were published was related to their inability to deal with nonlinear relationships. Although there was a great deal of hype surrounding the Rosenblatt perceptron, in 1969, Minsky [10] published a book that not only showed how limited Rosenblatt’s perceptron (and indeed, any single layer perceptron) actually is but also led to an intellectual climate change among the “artificial intelligentsia,” namely

![](img/ec668102bd6cbe5645156f246a7c2e8b_37_0.png)

**FIGURE 2.10**

Plot of a sigmoid function. The slope of the curve can be adjusted by the choice of the multiplier for x in the equation. The curve’s bounds on the x-axis are from 0 to 1, thus making it a reasonable substitute for a ramp activation.

*M. Thoma, Wikimedia Commons.*

so-called AI winter in the 1980s. However, major contributions by many investigators brought back ANNs into the forefront of AI research, based on the multilayer concept, nonlinear activations, backpropagation, and convolution. The beauty of a modern ANN and its many advanced variants that will be covered in the next chapter is that it can represent the output of any continuous bounded function, and thus can mimic the output of any algorithmic structure that uses mathematics for its underlying implementation (i.e., most, if not all of them). Thus, in addition to its own unique abilities, an ANN can do anything a shallow learning network can do, but for data that are not too complex, shallow learning can be more computationally efficient. However, these modern artificial networks, in evolving beyond these humble beginnings, have become truly sophisticated models employing concepts from linear algebra, multivariate calculus, mathematical statistics, game theory, reinforcement learning, and evolutionary theory. In order to emphasize how much further we have to go to achieve true general intelligence in an artificial substrate, it is humbling to note that the human brain contains many billion neurons and rather than being merely passive devices, each function as an independent small computer in the way that it processes data. If we think of the brain as a set of giant interacting networks, the number of possible connections is literally astronomically large.

## The basic ANN

A typical neural net is composed of several layers of nodes, as shown in *Fig. 2.11*. Each neuron in the net has the properties described for perceptrons. However, in addition to the input and output layers, there are a variable number of “hidden” layers that connect the input to the output layers. They are called hidden layers

![](img/ec668102bd6cbe5645156f246a7c2e8b_38_0.png)

**FIGURE 2.11**

The multilayer construction of a neural network. Each colored circle represents a neuron (which passes the aggregated signal through an activation function) and the lines are the inputs and output connecting them. In this example, only a single hidden layer is shown. In practice, multiple hidden layers are used.

> From SciForce: white paper on Top Algorithms for Health", by permission of M. Ved, "Top Algorithms for Healthcare" SciForce-Medium.

for the following reason: since we know the inputs and receive output data, both these layers are known to us. In contrast, the layers in between are not readily accessible to the observer. Since the computer has no cognition, each run of the algorithm is, in essence, a double-blind experiment. This has raised philosophical issues about the explainability of deep learning models.

The basic features of an ANN are as follows:

- Each input neuron gets only one input, directly from outside; those of the hidden layers get many.
- Neurons in a layer do not connect to each other.
- Each neuron in one layer connects to all the neurons in the next layer.
- The ANN is a synchronous model; all nodes in a given layer receive their inputs and calculate their activities at the same time. This means that all the calculations in the n layer must be calculated before we can start the calculations for the (n+1) layer.

Thus, the output of one layer becomes the inputs of the next. Because of the summing process, each layer receives increasingly complex inputs. At any given layer, the network creates an internal representation of the data that incorporates relationships among the feature vectors of each sample. Basically, a neural network utilizes multiple levels of representation to model both simple and complex relationships among data. They are powerful classifiers and can extract relations, predict outcomes, and make inferences from data, all without the need to manually define the feature vectors for that set. For example, instead of inputting the eye-snout ratios and other defining characteristics of dogs versus cats to classify an unknown image as to its dog-ness or cat-ness, one can simply present multiple known examples of each to the program.

## The weights in an ANN

As was the case for the Rosenblatt perception, every input within an ANN is associated with a weight that represents the relative importance of that input with respect to its contribution to the sum of signals received by the neuron. For a node receiving input from two nodes of the previous layer, the total input is the sum of the output of the first node times its weight plus the output of the second node times its weight. This is the product of two vectors. In general, one can set up the computation of each layer of nodes as a single matrix-vector product. Basically, there is a matrix of weights multiplied by the input vector, which produces the aggregated output when acted upon by the activation function. When these calculations are generalized to multilayer networks with many nodes, they are seen to be the result of simple multiplicative steps in linear algebra. In some ANNs a bias term is also added; this is a scalar that is added to the input to ensure that a few nodes per layer are activated regardless of signal strength. It is because the weighted inputs summed is a linear function that a nonlinear activation function must act upon them so that the ANN is not restricted to linear problems. Both weights and biases are modified throughout the training of an ANN.

## Learning from examples; Backprop and stochastic gradient descent.

The traditional learning method for feed-forward networks such as the ANN is to take a fixed network architecture and then use the examples to find appropriate values for the weights that lead to correct performance. The fact that each node in a layer has an incoming connection from every node in the previous layer does not interfere with this adjustment, since any unnecessary connection can be set to zero during this process.

The network learns the proper weights from the training set using a gradient-descent algorithm based upon The Error Back-Propagation algorithm (Backprop). The basics of backpropagation were derived in the context of control theory by multiple researchers in the 1960s. Subsequently, in the 1980s, a number of investigators proposed that it could be used for neural networks. Thus, it is difficult to assign
