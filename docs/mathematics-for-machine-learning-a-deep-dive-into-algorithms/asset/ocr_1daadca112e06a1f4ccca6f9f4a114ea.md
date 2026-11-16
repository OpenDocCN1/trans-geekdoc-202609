modules, which used multiple filter sizes within a single layer.

+   This architecture significantly reduced the number of parameters while maintaining network depth and performance.

+   GoogLeNet won the 2014 ILSVRC and showcased the advantages of parallel processing.

[189]

# ResNet (Residual Networks):

+   ResNet, also by researchers at Microsoft, introduced residual connections to address vanishing gradient issues.

+   Residual connections allow information to bypass certain layers, enabling training of extremely deep networks (e.g., ResNet-152).

+   ResNet's skip connections revolutionized the training of deep networks and became a standard architecture.

# DenseNet (Densely Connected Convolutional Networks):

+   DenseNet, proposed in 2017, introduced dense connections where each layer is connected to every other layer in a feedforward fashion.

+   These connections encouraged feature reuse and enhanced gradient flow, improving information flow across layers.

+   DenseNet achieved state-of-the-art performance with fewer parameters.

# EfficientNet:

+   EfficientNet, introduced in 2019, focuses on achieving high performance with constrained resources.

[190]

+   It uses a compound scaling method to balance network depth, width, and resolution to optimize efficiency and accuracy.

+   EfficientNet models have become popular for mobile and resource-constrained applications.

# Applications and Impact:

+   These architectures have been applied in various tasks like image classification, object detection, image segmentation, and more.

+   They have led to remarkable advances in areas like medical imaging, self-driving cars, and