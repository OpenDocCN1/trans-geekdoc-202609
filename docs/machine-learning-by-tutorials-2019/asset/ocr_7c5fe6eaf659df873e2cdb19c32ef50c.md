# Feeling hot hot hot

Back to that very convolution layer that outputs a 28×28×256 tensor. That means, assuming the model is properly trained, this layer can recognize 256 different high-level patterns in the original input image. Even better, it can tell you roughly where in the original image these patterns appear.

For example, let's say the first filter from this final convolution layer has learned to detect the high-level pattern for “round shape with a hole in it” and the original RGB input image has a donut in the top-right corner, the 28×28 feature map for channel 0 might look like this:

![](bbox=[0.373, 0.323, 0.626, 0.526])

A channel from the final tensor represented as a heatmap

You're looking at just one of the 256 output channels, or feature maps, contained in this tensor. Displayed like this, it's also often called a heatmap because it's “hot” (yellow) where the pixels responded to a pattern but not “cold” elsewhere (dark blue). In this example, the pixels in the top-right corner are hot, meaning that the pattern from this filter was detected in position in the original RGB input image.

Each of the 256 channels from this tensor will have a similar 28×28-pixel map that indicates where filter's pattern was detected in the original image. Of course, the location is only an approximation because the image was scaled down by a factor of 8 (three max pooling layers). If a pattern was not found in the input image, its heatmap will contain only very small values.

Unfortunately for us, the patterns that the final convolution layer actually learns will not be as easy to understand as “round shape with a hole in it.” Exactly what the convnet learns can be hard for humans to interpret.