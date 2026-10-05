Figure 8.2: Comparison of MLP and CNN architectures

# Key building blocks of CNNs

The following are the key building blocks of CNNs, each playing a crucial role in feature extraction and decision-making:

+   - **Convolutional layers**: These layers use learnable filters (kernels) to detect patterns such as edges, textures, and shapes by sliding across the input. Each filter produces a feature map, revealing specific spatial characteristics.
- **Pooling layers**: Pooling (often max pooling) reduces the spatial dimensions of the feature maps, making the network computationally efficient and translation-invariant. This helps in down-sampling while retaining important features.
- **Fully connected (dense) layers**: After several convolution and pooling operations, the output is flattened and passed to dense layers to perform final decision-making, such as classifying an image or regressing to a value.
- **Activation functions**: ReLU is typically used in hidden layers to introduce non-linearity. For the output layer:

+   - Use sigmoid for binary classification.
- Use softmax for multi-class classification.

# Dropout

Randomly drops a fraction of neurons during training, forcing the network to learn more robust features preventing over-reliance on specific nodes. Dropout is a regularization technique that enhances generalization by randomly deactivating neurons during training, with the following best practices:

+   - Common values: 0.2–0.5, depending on dataset size and