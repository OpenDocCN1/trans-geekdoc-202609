other techniques, better optimizers (such as AdaGrad or Adam), or using Batch Normalization.

+   - More: go ahead and play with the other parameters to get a feel of what they do. In fact, you should definitely play with this UI for at least one hour, it will grow your intuitions about neural networks significantly.

+   Draw an ANN using the original artificial neurons (the ones in Figure 10-3) that computes $A \oplus B$ (where $\oplus$ represents the XOR operation). Hint: $A \oplus B = (A \wedge B) \vee (A \wedge A)$.

+   Why is it generally preferable to use a Logistic Regression classifier than a Perceptron (i.e., a single layer of threshold units trained using the Perceptron training algorithm)? How can you tweak a Perceptron to make it equivalent to a Logistic Regression classifier?

+   Why is the activation function a key ingredient in training the first MLPs?

+   Name three popular activation functions. Can you draw them?

+   Suppose you have an MLP composed of one input layer with 10 passthrough neurons, followed by one hidden layer with 50 artificial neurons, and finally one output layer with 3 artificial neurons. All artificial neurons use the ReLU activation.

+   - What is the shape of the input matrix X?

+   - What about the shape of the hidden layer's weight vector $W_{hj}$ and the shape of its bias vector $b_j$?

+   - What is the shape of the output layer's weight vector $W_{io}$ and its bias vector $b_i$?

+   - What is the shape of the network's output matrix Y?

+   - Write the equation that computes the network's output matrix $Y$ as a function of $X, W_{hj}, b_j$ and $b_i$.

+   How many neurons do you need in the output layer if you want to classify into spam or ham? What activation function should you use in the output layer? If you want to classify MNIST, how many neurons do you need in the output layer, using what activation function? Answer the same questions for your network to predict housing prices in Chapter 2.

+   Is backpropagation and how does it work? What is the difference between backpropagation and reverse-mode autodiff?

+   Can you list all the hyperparameters you can tweak in an MLP? If the MLP fits the training data, how could you tweak these hyperparameters to solve the problem?