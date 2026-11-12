![](bbox=[0.12, 0.11, 0.895, 0.335])

Figure 11.1 Gradient descent with backpropagation.

# 11.3.1.3 Gradient Descent with Backpropagation

Gradient descent is an optimization approach for training the CNN model. It iteratively modifies the network's weights and biases to reduce the loss function, as shown in Figure 11.1.

+   • Forward pass: The input data is passed through the network layers, resulting in a prediction.
+   • Loss calculation: The loss function compares the predicted output with the ground truth label.
+   • Backpropagation: The mistake (loss) is propagated backward through the network, calculating the gradients (slopes) for each weight and bias.
+   • Weight update: The gradients are used to adjust the weights and biases in a way that minimizes loss.

# 11.3.2 Common Architectures

# 11.3.2.1 U-Net

U-Net is a fully convolutional network (FCN) developed exclusively for medical image segmentation. It uses an encoder-decoder architecture with skip connections.

# 11.3.2.2 Components

+   • Encoder: Extracts features from the input image through repeated convolutional and pooling operations.
+   • Decoder: Upsamples the extracted features and combines them with corresponding features from the encoder path (via skip connections) for precise localization.