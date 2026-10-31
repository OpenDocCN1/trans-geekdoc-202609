olution product between the feature and each portion of the scanned image. A feature is then seen as a filter: the two terms are equivalent in this context.

# Pooling Layer

This is a subsampling operation typically applied after a convolutional layer. In particular, the most popular types of pooling are max and average pooling, where the maximum and average values are taken, respectively. Max-Pooling is a sample-based discretization process. Its objective is to subsample an input representation (image, hidden layer output matrix, etc.) by reducing its dimension. Moreover, its interest is that it reduces the computational cost by reducing the number of parameters to be learned and provides invariance by small translations (if a small translation does not modify the maximum of the scanned region, the maximum of each region will remain the same and thus the new matrix created will remain identical).

# Flatten Layer

The Flatten layer provides a connection between the convolution layers and the base layers of Deep Learning. It allows diffusing the data through the layers by reducing its dimension. The data finally reaches a prediction layer, such as the Dense layer, which provides the label detected by the Deep Learning model.

# Dense Layer

A Dense layer which is a classical neural layer, completely connected with the previous and the next layer. A dense output layer with one neuron per class, and a “softmax” activation function that gives an output probability for each neuron, with the output neuron with the highest probability then deciding that its associated class is the predicted class. Fig. (10) shows the architecture of the model used.

# Learning and Same Parameters

In classification tasks, it would be useful to have all outputs fall between 0 and 1. These values can then present probability assignments for each class. There are 2 main types of multi-class situations: non-exclusive and mutually exclusive Classes. We used a configuration for the case of a 10-class exclusive classification problem whose code is presented in Table 2.