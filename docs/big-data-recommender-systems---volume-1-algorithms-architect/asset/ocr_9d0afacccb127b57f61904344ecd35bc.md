# Deep learning architecture for big data analytics in URL detection 317

the connection records belong to Normal, DoS and Probe. For improving the performance, the number of hidden layers has been increased from two to five. It has been empirically found that a six-layer neural network (five hidden and one output layer) with the following number of neurons: 1024, 768, 512, 256, 128, 5 in the first, second, third, fourth, fifth and output layer, respectively, gave the best performance. A learning rate of 0.01 was used for the experiments, and a lower learning rate demands more epochs. We have used adam as the optimizer, categorical cross entropy as the loss function. Using a six-layer neural network has improved the detection rate of L2L and U2R.

DNN network structures We have used the following network structures for our experiments:

+   - Two-layer DNN
- Three-layer DNN
- Four-layer DNN
- Five-layer DNN
- Six-layer DNN

# 14.4.4 Proposed architecture for KDD-Cup-99 data set

It was empirically found through the experiments that six-layer neural network gave the best performance. By six-layer neural network, we mean five hidden layers and one output layers. The number of neurons in the proposed architecture is the following: 1,024, 768, 512, 256, 128 and 5 in first, second, third, fourth, fifth and the output layer, respectively. A default learning rate of 0.01 was used for the experiments. We have used adam as the optimizer and categorical cross entropy as the loss function. The activation function used is ReLU since ReLU overcomes the problem of vanishing gradient in DNNs.

+   1. Fully connected layers
There is a connection from the neurons in the current layer to the neurons in the succeeding layer. That is why it is fully connected layers. These hidden layers help to learn the complex features. All the hidden layer uses ReLU as the activation function.

+   2. Batch normalization and regularization
The problem of overfitting the model is avoided by introducing a dropout of 0.01 between the fully connected layers. Dropout removes the connections so that the model does not overfit the training samples. We used batch normalization to speed up the training of DNN.

+   3. Classification
We framed two problems, one for binary classification and the other for multi-class classification. In the binary classification problems, all connections are grouped as one-connection record and benign as the other connection