![](bbox=[0.168, 0.096, 0.796, 0.258])

Figure 11.3 Diagram of an example CNN in LeNet style.

At this point fully-connected layer (also called a dense layer) is applied to produce a vector of 128 features. A second fully connected layer produces 10 outputs, which could correspond to 10 output classes of objects, as digits.

The key strength of CNNs compared to the classical filtering techniques is that they learn the filters to extract the most salient features. This is achieved by fitting the CNN model to the data where learnable parameters are the filters. The fitting is performed using backpropagation, similarly to the fully connected networks, as we have seen in Sect. 10.2.3.

# 11.1.3 Exercises

+   1. Describe the concept of translation invariance in convolutional layers.
2. Explain why convolutional layers have fewer parameters than fully connected layers.
3. What is the difference between convolutional neural networks and traditional filtering techniques?

# 11.2. Building blocks of convolutional neural networks

In this section we will describe the essential components of a CNN, namely,

+   * the convolutional layers for feature extraction;
* the activations to support learning of non-linear interactions;
* the downsampling operations (pooling or striding).

Optional components of CNNs are batch normalization to speed up training and dropout to prevent overfitting. Additionally, CNNs often contain fully connected layers to transform the network output to the required shape (Fig. 11.3).

Fig. 11.4 shows a typical convolutional block, composed of a convolutional layer, batch normalization, activation (in this case ReLU) and pooling.