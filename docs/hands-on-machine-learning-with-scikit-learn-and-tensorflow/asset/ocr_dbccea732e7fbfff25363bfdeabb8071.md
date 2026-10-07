+   • Third, repeat step two until there are no bounding boxes to get rid of.

This simple approach to object detection works pretty well, but it requires running the CNN many times, so it is quite slow. Fortunately, there is a much faster way to slide a CNN across an image using a Fully Convolutional Network.

# # Fully Convolutional Networks (FCNs)

The idea of FCNs was first introduced in a 2015 paper³ by Jonathan Long et al., for semantic segmentation (the task of classifying every pixel in an image according to the class of object it belongs to). They pointed out that you could replace the dense layers at the top of a CNN by convolutional layers. To understand this, let's look at an example: a dense layer with 200 neurons on top of a convolutional layer that outputs 100 feature maps, each of size 7 x 7 (this is the feature map size, the kernel size). Each neuron will compute a weighted sum of all 100 x 7 activations from the convolutional layer (plus a bias term). Now we see what happens if we replace the dense layer with a convolutional layer using 200 filters, 7 x 7, and with VALID padding. This layer will output 200 feature maps, each 1 x 1 (since the kernel is exactly the size of the input features and we are VALID padding). In other words, it will output 200 numbers, just like the dense layer, and if you look closely at the computations performed by a convolutional layer, you will notice that these numbers will be precisely the same as the dense layer produced. The only difference is that the dense layer's output was a tensor of shape [batch size, 200] while the convolutional layer will output a tensor of shape [batch size, 1, 200].

To convert a dense layer to a convolutional layer, the number of filters in the convolutional layer must be equal to the number of units in the dense layer, the filter size must be equal to the size of the input feature maps, and you must use VALID padding. The stride may be set to 1 or more, and we will see shortly.

![](bbox=[0.162, 0.563, 0.243, 0.636])

Why is this important? Well, while a dense layer expects a specific input size (since it has one weight per input feature), a convolutional layer will happily process images of any size⁴(however, it does expect its inputs to have a specific number of channels, since each kernel contains a different set of weights for each input channel). Since an FCN contains only convolutional layers can be trained and executed on images of any size!

> ²³ "Fully Convolutional Networks for Semantic Segmentation," J. Long, E. Shelhamer, T. Darrell (2015).
⁴ There is one small exception: a convolutional layer using VALID padding will fail if the input size is smaller than the kernel size.