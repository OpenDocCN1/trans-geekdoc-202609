to match the output classes to the number of feature maps, global average pooling was often used right before the final classification layer.

Reduction of computational complexity: Pooling layers decrease the dimensionality of feature maps and thus require a smaller number of parameters and computations in subsequent levels. The reduction in computational complexity means there are faster times for both inference and training.

![](bbox=[0.2, 0.24, 0.55, 0.57])

Figure 13: Pooling layers and their functions.

Control overfitting: Hence, pooling layers serve as a kind of regularization, which makes the model more general. As prerequisites of the subsequent evaluation, downsampling makes little changes in the input insignificant for the network and introduces translational invariance, which in turn minimizes overfitting.

Feature extraction: This means that necessary characteristics from the input data were retained and extracted with the help of pooling layers. The network was capable of rejecting components of an input image that are less useful for segmentation, yet it was able to focus on the primary values inside each pooling window.

The use of pooling layers shrinks the dimensions of feature maps, thus losing the spatial resolution of the data. Taking into account the positive impact that lower computing costs and better feature representation bring, this compromise is often justified. In order to develop various increasingly abstract representations of input data for achieving high performance in tasks such as object recognition and picture categorization, pooling layers play a significant role.