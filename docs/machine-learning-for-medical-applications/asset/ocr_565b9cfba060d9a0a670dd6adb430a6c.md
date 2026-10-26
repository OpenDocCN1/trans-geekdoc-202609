It was observed that the choice of pooling method and kernel size significantly affects the performance of deep learning models. Designers must carefully select these parameters based on the specific requirements of the task and the characteristics of the data being analyzed. While average pooling and global average pooling offer alternative approaches that are more suitable for certain applications, max pooling was frequently preferred due to its effectiveness in preserving dominant features.

Pooling layers play a crucial role in deep learning models by enhancing the network’s ability to generalize across various visual tasks. They also contribute to reducing computational complexity and simplifying the feature extraction process.

# 4.5 Fully connected layers and their role

The fully connected layer is a basic characteristic of deep learning structure and is notable specifically for neural network architectures. These layers are crucial for transforming the characteristics, which are extracted by the layers previous to them, into final predictions.

A fully connected layer contains all neurons of the layer that are connected to neurons in the layer above. Thanks to the deep connection to the layer, which helps the model find patterns and correlations in the data, it is also possible to take features from each of the previous layers. Each neuron in the fully connected layer computes the weighted sum of its inputs before using an activation function, which in turn adds more nonlinearity to the model.

![](bbox=[0.177, 0.558, 0.646, 0.775])

**Figure 14:** Fully connected layers and their role.

The fully connected layers made it possible to aggregate and then integrate other features that were retrieved by the convolutional layers. To summarize, fully connected layers generate high-level representations of the input data by using the property pro-