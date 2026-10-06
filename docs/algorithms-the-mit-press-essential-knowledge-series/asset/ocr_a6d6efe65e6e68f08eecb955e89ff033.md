With this we arrive at the heart of the learning process in neural networks: the backpropagation algorithm.⁶

For each input and desired output,

+   1. Calculate the output and loss of the neural network proceeding layer by layer, going forward from the input to the output layer.
2. Update the weights and biases of the neurons to minimize the loss, going backward from the output to the input layer.

Using the backpropagation algorithm, we can build complex neural networks and train them to perform different tasks. The building blocks of deep learning systems are simple. They are artificial neurons, with their limited computational capabilities: taking inputs, multiplying by weights, summing, adding a bias, and applying an activation function on the resulting value. Their power derives from connecting lots and lots of them in special ways, where the resulting networks can be trained to perform the task that we want them to perform.

# Recognizing Clothes

To render the discussion more concrete, let us assume that we want to build a neural network that recognizes items