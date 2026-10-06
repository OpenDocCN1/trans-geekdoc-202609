
Figure 9. 2D Convolution operation between source image and kernel (Goodfellow et al., 2016)

# Cost

![](img/c5cbbc72cd5e7b9be32079eac36d685c_97_0.png)

analysis, these two functions are the source image tensor and the filter (also called kernel) tensor. The result generated is called a feature map.

Figure 9 depicts how a convolutional operation is applied between an image and a kernel to create a feature map. The kernel slides through the image, and the corresponding pixel value of the kernel is multiplied with the corresponding pixel value of the image in a boundary of kernel size. These values are then added together to create a single value of the feature map. The kernel strides through all the windows, and this process is repeated for all windows. This results in the formation of the feature map.

Figure 10. Detecting different edges

![](img/c5cbbc72cd5e7b9be32079eac36d685c_97_1.png)

# Deep Learning With PyTorch

In 10, the first filter can detect vertical edges, and the other detects horizontal edges.
There can be different filters to detect edges at different angles. If these filters are assigned as weights to the neural networks, then the neural network can learn these weights and identify edges at different angles. A combination of learning several filters helps in identifying patterns that are specific to a particular category of images.

This is essentially what a Convolutional Neural Network does. By learning filters, it can identify patterns that are specific to a class of image and correctly identify it.

But, why is a CNN better than a simple feedforward network?
In a feedforward architecture, each pixel is an input to the network. This leads to a considerable number of weights the model has to learn. Consider an example of an image resolution of 28*28 which is the size of a single image in the MNIST dataset. Consider the hidden layer size of a single feedforward neural network to be h = 300. The number of weights to be trained would be (28*28)*300, which is 235,200 weights. In a CNN if there are 6*6 there are 360 weights. This property of a CNN is called a sparse connection as the input nodes do not interact with all the output nodes, leading to sparse interactions.

The small filter scans through the entire image and detects edges in these small portions by one, eventually scanning the whole image. This means that the same weights are shared among several inputs. This property is called parameter sharing.

These two properties help in making a CNN much more efficient for image analysis compared to a vanilla feedforward network.

# Padding

In a CNN, as the filter strides through the image, it encounters pixels several times, with most encounters towards the center of the image, and least in the corners. If an object of interest is in the corner of the image then CNN may not be able to detect it as it was not trained to consider corners.

To solve this problem, the image is padded with empty pixels so that the corner pixels are encountered by a filter several times, and the CNN classifier is trained well to classify objects at the corner.

# Stride

Stride is used to define how the filter should shift every time during scanning. By default, stride is 1, which means that the filter will shift through one row or column in every. A stride of 2 means that the filter will shift through two rows or columns.

# Pooling

A convolutional neural network architecture typically involves a pooling layer that is to generalize the patterns learned by the filters. Our classifier does not need to learn specific features of an image but rather general features to classify unseen cases correctly too. This pooling helps in generalizing the classification task.

The most widely used form of pooling is max pooling. In max-pooling, the maximum pixel value is chosen from a grid of pixels.

# Transfer Learning (Pan et al., 2009)

In the real world, it is not always possible to train a model for image analysis from scratch due to a lack of data. A good classifier requires a dataset in the order of 10s of millions. Such large datasets are not easily available for every task. So to train an image classifier? The answer is transfer learning.

How do pre-trained models produce good results? It was shown in the paper “Visualizing and understanding convolutional networks” (Zeiler et al., 2014), the early layers in CNN models start identifying some fundamental patterns that are common in all types of objects. The first layer identifies lines and edges at various angles. The second layer identifies some basic shapes like circles, gradients, and slightly complicated features. By the third layer, it starts identifying patterns of specific objects like tires, people, etc. This pattern recognition becomes more sophisticated and starts identifying objects of interest as the layers progress.

As lines and basic shapes are common to every object, one can use the early layers of a pre-trained model and train the further layers to our requirements using the small dataset.

Figure 11. Visualizing patterns detected by different layers of a CNN (Zeiler et al., 2014)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_99_0.png)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_99_1.png)

# Pneumonia Detection (Shounou et al., 2015)

Image classification has made a big impact in healthcare by detecting several features. (Note: OCR text seems fragmented/corrupted here in original, maintaining context).

[Note: The provided OCR text for pages 100-101 appears highly fragmented/corrupted in the source prompt. I have processed the coherent sections above.]
