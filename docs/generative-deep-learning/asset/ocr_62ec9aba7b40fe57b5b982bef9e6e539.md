+   3. The second input to the U-Net is the noise variance (a scalar).
+   4. This is encoded using a sinusoidal embedding.
+   5. This embedding is copied across spatial dimensions to match the size of the input image.
+   6. The two input streams are concatenated across channels.
+   7. The `skips` list will hold the output from the `DownBlock` layers that we wish to connect to `UpBlock` layers downstream.
+   8. The tensor is passed through a series of `DownBlock` layers that reduce the size of the image, while increasing the number of channels.
+   9. The tensor is then passed through two `ResidualBlock` layers that hold the image size and number of channels constant.
+   10. Next, the tensor is passed through a series of `UpBlock` layers that increase the size of the image, while decreasing the number of channels. The skip connections incorporate output from the earlier `DownBlock` layers.
+   11. The final `Conv2D` layer reduces the number of channels to three (RGB).
+   12. The U-Net is a Keras `Model` that takes the noisy images and noise variances as input and outputs a predicted noise map.

To understand the U-Net in detail, we need to explore four more concepts: the sinusoidal embedding of the noise variance, the `ResidualBlock`, the `DownBlock`, and the `UpBlock`.

# Sinusoidal embedding

*Sinusoidal embedding* was first introduced in a paper by Vaswani et al.⁶ We will be using an adaptation of that original idea as utilized in Mildenhal et al.’s paper titled “NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis.”⁷

The idea is that we want to be able to convert a scalar value (the noise variance) into a distinct higher-dimensional vector that is able to provide a more complex representation, for use downstream in the network. The original paper used this idea to encode the discrete position of words in a sentence into vectors; the NeRF paper extends this idea to continuous values.