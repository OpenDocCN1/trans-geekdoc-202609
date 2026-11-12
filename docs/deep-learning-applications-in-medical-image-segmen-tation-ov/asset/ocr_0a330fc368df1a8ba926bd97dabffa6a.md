cross-entropy loss. To minimize the loss function, optimization algorithms such as stochastic gradient descent (SGD) or its variants are employed.

# ## 5.3.1.7 Backpropagation

The computation of gradients with respect to the network parameters is performed using backpropagation, which efficiently propagates errors backward through the network. These gradients are then utilized to update the weights of the network through the chosen optimization algorithm.

CNNs achieve state-of-the-art performance on various computer vision tasks by learning hierarchical representations of input data through the repeated application of convolution, activation, pooling, and fully connected layers. This process enables CNNs to capture increasingly complex features and patterns, allowing them to excel in tasks such as image classification, object detection, and semantic segmentation.

As the domain of deep learning is continuously evolving, the classical version of CNN has gone through a number of modifications and upgrades. Some of the variations widely used in medical image segmentation are AlexNet (Chen et al. 2021b; Priya and Vasudevan 2024).

# ## 5.3.2 U-Net

U-Net is a CNN architecture developed by Ronneberger et al. (2015) as depicted in figure 5.4. It is a widely used architecture for biomedical image segmentation and semantic segmentation tasks. U-Net is based on the FCN.

U-Net has an encoder–decoder network architecture in the shape of a U. It has four encoder and decoder blocks joined by a bridge. The encoder and decoder networks’ information flow is completed by the bridge. At every block, the encoder network doubles feature channels and cuts spatial dimensions in half, functioning as a feature extractor by activating convolutional layers before ReLU. The skip connections improve gradient flow and conserve information for improved semantic features, and the max-pooling lowers computing costs. By upscaling and concatenating skip connection feature maps, the decoder network creates segmentation masks. Convolutions and sigmoid activation are then used for pixel-wise classification. The researcher found U-Net found a wide range of applications in the domain of brain tumor detection. Akter et al. proposed a deep CNN and U-Net for image classification and segmentation of brain tumor images and they could achieve accuracy of 90.8% (Akter et al. 2024). Cheng et al. proposed a deep network incorporating VGG-19 network in the coding stage of U-Net for edge detection in brain tumor images. They also added an edge detection module to enhance the