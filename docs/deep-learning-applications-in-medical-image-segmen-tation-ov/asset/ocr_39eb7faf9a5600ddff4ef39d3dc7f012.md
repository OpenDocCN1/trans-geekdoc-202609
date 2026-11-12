![](bbox=[0.14, 0.11, 0.93, 0.42])

Figure 9.3 Four-level data integration operation on cell imaging sample.

![](bbox=[0.14, 0.475, 0.85, 0.64])

Figure 9.4 Max-pooling operation.

Figure 9.4, where input features (4*4) are downsampled to a (2*2) feature map dimension. This is achieved by selecting the maximum value from each 2*2 block. The convolution operation is iterated multiple times within the network; as we progress deeper into the neural network, the size of the data matrix decreases. This reduction enables the filters of deeper layers to perceive a larger context of the data. While the height and width of the input data gradually diminish in convolution, the number of data filters increases, facilitating the extraction of complex patterns from the data.

The process of downsampling focuses on contextual features of the data and does not address spatial features. However, for medical cell segmentation, both contextual and spatial features are necessary. This requirement is met by the