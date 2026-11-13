# A4.3.8 Artificial neural networks

Perceptron: the data structure at the heart of an artificial neural network; it represents a single artificial neuron that takes in multiple inputs and weights, and generates an output value.

An artificial neural network (ANN) is an algorithm that learns to make decisions by finding patterns in data using an approach modelled on the biological brain. Just as a biological brain consists of many neurons that are interconnected and send signals to each other via synapses, so too an artificial neural network is an algorithm that defines a series of nodes that transmit data between each other. These nodes are known as perceptrons, though they are also very commonly referred to as “neurons”.

![](bbox=[0.116, 0.22, 0.48, 0.44])

+   - The input layer receives the input values that the network is being asked to process. Each feature of your model requires its own input perceptron. The value given to each perceptron is numeric (either an integer or float, depending on the problem context).
+   - There are usually one or more hidden layers within an ANN. These are layers of perceptrons that identify patterns in the input data to make generalizations useful for the next layer. They receive the values from the previous layer, perform their calculations and then send their respective result to the next layer in the network.
+   - The output layer is where the ANN produces a final “answer” value or prediction.

The illustration in this case is also an example of a fully connected network, in that every perceptron from one layer is connected, and sends its output value to, every perceptron in the next layer. Fully connected networks are the norm.

# A single perceptron

Zooming in on a single perceptron, the following sketch outlines the different elements at work:

![](bbox=[0.283, 0.57, 0.882, 0.76])

+   - Input: The perceptron receives an input value from every perceptron in the layer before.
+   - Weight: Every input has a weight associated with it. The weight is a value indicating the importance this particular neuron places on the values from the respective input. Weights are usually initialized with a random number between –1.0 and 1.0 and then adjusted by the training process.