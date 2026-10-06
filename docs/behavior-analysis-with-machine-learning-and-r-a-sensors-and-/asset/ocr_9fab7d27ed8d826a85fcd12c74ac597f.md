![](bbox=[0.158, 0.096, 0.843, 0.246])

Figure 8.29: Max pooling with a window of size 2x2 and stride = 2.

#  8.6.2 Pooling Operations

Pooling operations are typically applied after convolution layers. Their purpose is to reduce the size of the data and to emphasize important regions. These operations perform a fixed computation on the image and do no learnable parameters. Similar to kernels, we need to define a window size. Then, this window is moved throughout the image and a computation is performed on the pixels covered by the window. The difference with kernels is that this window is just a guide but do not have parameters to be learned. The most common pooling operation is max pooling which consists of selecting the highest value. Figure 8.29 shows an example of a max pooling operation on a 4x4 image. The window size is 2x2 and the stride is 2. The latter means that the window moves 2 places at a time.

The result of this operation is an image of size 2x2 which is half of the original one. Aside from max pooling, average pooling can be applied instead. In that case, it computes the mean value across all values covered by the window.

#  8.7 CNNs with Keras

```
keras_cnns.R
```

Keras provides several functions to define convolution layers and pooling operations. In TensorFlow, image dimensions are specified with the following order: height, width, and depth. In Keras, the layer_conv_2d() function is used to add a convolution layer to a sequential model. This function has several arguments but the 6 most common ones are: filters,kernel_size,strides,padding,activation, and input_shape.