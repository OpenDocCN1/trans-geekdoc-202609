```
4
7
16
34
70
```

# Listing 22.2: Example output from calculating the receptive field for a PatchGAN.

The authors of the Pix2Pix paper explore different PatchGAN configurations, including a 1 × 1 receptive field called a PixelGAN and a receptive field that matches the 256 × 256 pixel images input to the model (resampled to 286 × 286) called an ImageGAN. They found that the 70 × 70 PatchGAN resulted in the best trade-off of performance and image quality.

The 70 × 70 PatchGAN [...] achieves slightly better scores. Scaling beyond this, to the full 286 × 286 ImageGAN, does not appear to improve the visual quality of the results.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

The configuration for the PatchGAN is provided in the appendix of the paper and can be confirmed by reviewing the `defineD_n_layers()` function in the official Torch implementation. The model takes two images as input, specifically a source and a target image. These images are concatenated together at the channel level, e.g. 3 color channels of each image become 6 channels of the input.

Let Ck denote a Convolution-BatchNorm-ReLU layer with k filters. [...] All convolutions are 4 × 4 spatial filters applied with stride 2. [...] The 70 × 70 discriminator architecture is: C64-C128-C256-C512. After the last layer, a convolution is applied to map to a 1-dimensional output, followed by a Sigmoid function. As an exception to the above notation, BatchNorm is not applied to the first C64 layer. All ReLUs are leaky, with slope 0.2.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

The PatchGAN configuration is defined using a shorthand notation as: C64-C128-C256-C512, where C refers to a block of Convolution-BatchNorm-LeakyReLU layers and the number indicates the number of filters. Batch normalization is not used in the first layer. As mentioned, the kernel size is fixed at 4 × 4 and a stride of 2 × 2 is used on all but the last 2 layers of the model. The slope of the LeakyReLU is set to 0.2, and a sigmoid activation function is used in the output layer.

Random jitter was applied by resizing the 256 × 256 input images to 286 × 286 and then randomly cropping back to size 256 × 256. Weights were initialized from a Gaussian distribution with mean 0 and standard deviation 0.02.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.