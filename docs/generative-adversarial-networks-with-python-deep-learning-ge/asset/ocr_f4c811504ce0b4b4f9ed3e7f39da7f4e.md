When new layers are added to the networks, we fade them in smoothly [...] This avoids sudden shocks to the already well-trained, smaller-resolution layers.

> — Progressive Growing of GANs for Improved Quality, Stability, and Variation, 2017.

Further, all layers remain trainable during the training process, including existing layers when new layers are added.

All existing layers in both networks remain trainable throughout the training process.

> — Progressive Growing of GANs for Improved Quality, Stability, and Variation, 2017.

The phasing in of a new block of layers involves using a skip connection to connect the new block to the input of the discriminator or output of the generator and adding it to the existing input or output layer with a weighting. The weighting controls the influence of the new block and is achieved using a parameter alpha (α) that starts at zero or a very small number and linearly increases to 1.0 over training iterations. This is demonstrated in the figure below, taken from the paper. It shows a generator that outputs a 16 × 16 image and a discriminator that takes a 16 × 16 pixel image. The models are grown to the size of 32 × 32.

![](bbox=[0.24, 0.43, 0.75, 0.62])

Figure 28.2: Example of Phasing in the Addition of New Layers to the Generator and Discriminator Models. Taken from: Progressive Growing of GANs for Improved Quality, Stability, and Variation.

Let's take a closer look at how to progressively add layers to the generator and discriminator when going from 16 × 16 to 32 × 32 pixels.

# 28.4.1 Growing the Generator

For the generator, this involves adding a new block of convolutional layers that outputs a 32 × 32 image. The output of this new layer is combined with the output of the 16 × 16 layer that is upsampled using nearest neighbor interpolation to 32 × 32. This is different from many GAN generators that use a transpose convolutional layer.

... doubling [...] the image resolution using nearest neighbor filtering