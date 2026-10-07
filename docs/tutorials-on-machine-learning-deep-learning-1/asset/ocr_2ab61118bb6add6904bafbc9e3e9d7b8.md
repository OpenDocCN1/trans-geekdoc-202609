+   STEP 2: Input the first observation of your dataset in the input layer, each feature in one input node. That is the first row into input layer and each feature in one input node.

+   STEP 3: Forward-Propagation: from left to right, the neurons are activated in a way that the impact of each neuron's activation is limited by the weights (the weights basically determine how important activation is). Propagate the activations until getting the predicted result Y.

+   STEP 4: Compare the predicted result Y to the actual result y. Measure the generated ERROR.

+   STEP 5: Back-Propagation: from left to right, the Error is Back-Propagated. Update the weights according to how much they are responsible for error. The learning rate decides by how much you update the weights. The learning rate, as a parameter you control in your network.

+   STEP 6:

+   SGD: Repeat Steps 1 to 5 and update the weights after each observation (this is called reinforcement learning and in our case that stochastic gradient descent).

+   BGD/Mini-BGD: Repeat Steps 1 to 5 update the weights only after a batch of observations (Batch Learning).

+   STEP 7: When the whole training set passed through the ANN, that makes an Epoch. Redo more Epochs. Just keep doing that to allow your NN to train better and constantly adjust itself until you minimize the cost function.

Those are the steps you need to take to build your artificial neural networks (ANN) and train it.

STEP 1: Randomly initialise the weights to small numbers close to 0 (but not O).

STEP 2: Input the first observation of your dataset in the input layer, each feature in one input node.

STEP 3: Forward-Propagation: from left to right, the neurons are activated in a way that the impact of each neuron's activation is limited by the weights. Propagate the activations until getting the predicted result y.

STEP 4: Compare the predicted result to the actual result. Measure the generated error.

STEP 5: Back-Propagation: from left to right, the error is back propagated. Update the weights according to how much they are responsible for the error. The learning rate decides by how much we update the weights.

STEP 6: Repeat Steps 1 to 5 and update the weights after each observation (Reinforcement Learning). Or:
Repeat Steps 1 to 5 update the weights only after a batch of observations (Batch Learning).

STEP 7: When the whole training set passed through the ANN, that makes an epoch. Redo more epochs.