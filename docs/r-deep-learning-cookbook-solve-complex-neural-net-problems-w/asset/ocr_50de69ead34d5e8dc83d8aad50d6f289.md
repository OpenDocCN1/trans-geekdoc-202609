To keep a track of optimization, the MSE is calculated after every batch of 10,000 rows. The following image shows the declining trend of mean squared reconstruction errors computed for 30 batches for three RBMs separately:

![](bbox=[0.145, 0.177, 0.853, 0.588])

# # Implementing a feed-forward backpropagation Neural Network

In this recipe, we will implement a willow neural network with backpropagation. The input of the neural network is the outcome of the third (or last) RBM. In other words, the reconstructed raw data (`trainX`) is actually used to train the neural network as a supervised classifier of (10) digits. The backpropagation technique is used to further fine-tune the performance of classification.