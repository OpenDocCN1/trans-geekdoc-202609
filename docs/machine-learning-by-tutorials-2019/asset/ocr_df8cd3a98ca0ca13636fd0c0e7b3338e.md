The first Dense layer connects all flattened 3,072 input pixel values to 500 intermediate hidden neurons, and the second Dense layer connects these 500 neurons to the 20 outputs. This kind of neural network is called a two-layer feedforward network.

The first half of this neural network, from the input to the output of the first Dense layer is the logistic regression. The second half of the network, from the second Dense to the end is the second regression. So all you've done is stick two logistic regression models together.

The activation function at the end of the model is still the softmax that converts the outputs into probabilities. The new Dense layer also has an activation function. This is not a softmax but a ReLU, called ReLU or rectified linear unit.

In most neural networks every layer is followed by an activation function. This is usually a very simple mathematical operation that transforms the output of the layer in some non-linear way.

Such non-linearities are necessary because otherwise the model can only learn linear relationships between their inputs (the pixels) and their outputs (the classes) and gives very limited results.

Remember the goal is to transform the input data in such a way that the model can draw an imaginary straight line or hyperplane between the classes. Without these non-linear activation functions, you'd only be able to do that if you could already draw that straight line between the original input data points — in which case you wouldn't need to train a model at all. It is the non-linearities that allow the model to learn all kinds of interesting data transformations.