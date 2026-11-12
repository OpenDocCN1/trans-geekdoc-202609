+   - Skip connections: Connect corresponding encoder and decoder layers directly to preserve spatial information and aid in precise segmentation of small structures.

# 11.3.2.3 Convolutional Neural Networks (CNNs)

CNNs are a type of deep neural network design that work particularly well with image data. These are skilled in capturing spatial characteristics and relationships within an image. CNNs are a broad category of architectures that use convolutional layers to extract features from images. They can be utilized for a variety of segmentation tasks. A complete image processing is shown in Figure 11.2.

The key components are as follows (Gudhe et al. 2023):

+   - Input layer: Receives the pre-processed image data, typically a 3D tensor representing the image width, height, and color channels (e.g. RGB).

+   - Convolutional layer: Applies filters (kernels) that slide across the input, extracting local features like edges, shapes, and textures.

+   - Pooling layer: Downsampling the feature maps created by the convolutional layer reduces data size and processing expense while keeping critical information. Maximum and average pooling are two common pooling operations.

+   - Activation layer: This introduces non-linearity to the network, allowing it to learn complex patterns. Popular activation functions include ReLU and sigmoid.

+   - Fully connected layer: Flattens the output from the previous layers into a vector and performs traditional neural network operations for classification or regression tasks.

# 11.3.2.4 Fully Convolutional Network (FCN)

The FCNs are a type of CNN where all layers depend on convolutional function, which enables end-to-end segmentation. The end-to-end segmentation is a cluster of pixel-wise selection of images. The participating components of FCN are as follows:

+   - Encoder: Similar to a general CNN encoder, extracting features.

+   - Upsampling layers: Increase the feature map resolution to match the input image size.

+   - Output layer: Produces a probability map for each pixel belonging to a specific class.

# 11.3.2.5 SegNet

SegNet is an encoder–decoder architecture similar to U-Net, but utilizes pooling indices for upsampling instead of DE convolutions. Table 11.1 contains a detailed description of CNN layers. The components of SegNet are as follows:

+   - Encoder: Similar to U-Net's encoder, extracting features.