# Applications of AI & ML in diagnostics and disease treatment 65

![](bbox=[0.213, 0.111, 0.756, 0.368])

Figure 3.1 Architecture of convolutional neural network.

filters are used, respectively, allowing the network to learn more complex features as it goes deeper.
After the convolutional layers extract the hierarchical features from the input images, the model uses the Flatten operation to obtain a 1D vector from the 2D output, which is then input into two dense layers. A dense layer comprises 128 neurons followed by Dropout(0.5), which helps to reduce overfitting by allowing 50% of the neurons to be randomly turned off at each round of training. Another dense layer containing 64 neurons is added, followed by Dropout(0.5). One neuron with a sigmoid activation function is included in the final output layer, which yields a probability of either presence or absence of autism, where what is in the parenthesis regarded as 1, while the opposite is 0. The framework's function of loss is designed for jobs involving binary classification and is based upon binary cross-entropy. The Adam optimiser is utilised with a learning rate of 0.0001 to ensure that the rate adapts well during the training, which is perfect for deep learning models such as CNN. The model is trained over 50 epochs while the batch size is set to 32, and at that time, training and validation accuracy are tracked to see whether the model is learning well or overfitting.

Figure 3.2 the autoencoder Architecture for Skin Cancer Detection.
in this particular work, an autoencoder type implementation for Skin Cancer Classification has neural network-based techniques using Keras, in this case, encoding cancer images of our data into a lower dimensional feature space and using those encodings only to classify the image as cancerous