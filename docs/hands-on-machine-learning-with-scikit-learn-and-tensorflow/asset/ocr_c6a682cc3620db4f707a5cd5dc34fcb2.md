much more efficiently than previous architectures: GoogLeNet actually has 10 times fewer parameters than AlexNet (roughly 6 million instead of 60 million).

**Figure 14-13** shows the architecture of an inception module. The notation "3 x 3 + 1(S)" means the layer uses a 3 x 3 kernel, stride 1, and SAME padding. The input signal is first copied and fed to four different layers. All convolutional layers use ReLU activation function. Note that the second of convolutional layers uses kernel sizes (1 x 1, 3 x 3, and 5 x 5), allowing them to capture patterns at different scales. Also that every single layer uses a stride of 1 and SAME padding (even the pooling layer), so their outputs have the same height and width as their inputs. This makes it possible to concatenate all the outputs along the depth dimension in the final depth concat layer (i.e., stack the feature maps from all four convolutional layers). This concatenation layer can be implemented in TensorFlow using the tf.concat() operation, with axis=3 (axis is the depth).

![](bbox=[0.153, 0.376, 0.846, 0.584])

Figure 14-13. Inception module

You may wonder why inception modules have convolutional layers with 1 x 1 convolutional layers. Surely these layers cannot capture any features since they look at one pixel at a time? In fact, these layers serve three purposes:

+   - First, although they cannot capture spatial patterns, they can capture patterns along the depth dimension.
- Second, they are configured to output fewer feature maps than their inputs, so they serve as bottleneck layers, meaning they reduce dimensionality. This cuts the computational cost and number of parameters, speeding up training and improving generalization.
- Lastly, each pair of convolutional layers ([1 x 1, 3 x 3] and [1 x 1, 5 x 5]) acts like a single, powerful convolutional layer, capable of capturing more complex patterns. Indeed, instead of sweeping a simple linear classifier across the image as a