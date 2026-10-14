```
kernel_size=4,
strides=2,
padding="same",
use_bias = False,
activation = 'tanh'
)(x)
generator = models.Model(generator_input, generator_output)
```

+   1. Define the Input layer of the generator—a vector of length 100.
+   2. We use a Reshape layer to give a 1 × 1 × 100 tensor, so that we can start applying convolutional transpose operations.
+   3. We pass this through four Conv2DTranspose layers, with BatchNormalization and LeakyReLU layers sandwiched in between.
+   4. The final Conv2DTranspose layer uses a tanh activation function to transform the output to the range [−1, 1], to match the original image domain.
+   5. The Keras model that defines the generator—a model that accepts a vector of length 100 and outputs a tensor of shape [64, 64, 1].

Notice how we use a stride of 2 in some of the Conv2DTranspose layers to increase the spatial shape of the tensor as it passes through the network (1 in the original vector, then 4, 8, 16, 32, and finally 64), while decreasing the number of channels (512 then 256, 128, 64, and finally 1 to match the grayscale output).

# Upsampling Versus Conv2DTranspose

An alternative to using Conv2DTranspose layers is to instead use an UpSampling2D layer followed by a normal Conv2D layer with stride 1, as shown in Example 4-6.

*Example 4-6. Upsampling example*

```
x = layers.UpSampling2D(size = 2)(x)
x = layers.Conv2D(256, kernel_size=4, strides=1, padding="same")(x)
```

The UpSampling2D layer simply repeats each row and column of its input in order to double the size. The Conv2D layer with stride 1 then performs the convolution operation. It is a similar idea to convolutional transpose, but instead of filling the gaps between pixels with zeros, upsampling just repeats the existing pixel values.

It has been shown that the Conv2DTranspose method can lead to artifacts, or small checkerboard patterns in the output image (see Figure 4-4) that spoil the quality of the output. However, they are still used in many of the most impressive GANs in the