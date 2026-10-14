| Layer (type) | Output shape | Param # |
|---|---|---|
| BatchNormalization | (None, 8, 8, 128) | 512 |
| LeakyReLU | (None, 8, 8, 128) | 0 |
| Conv2DTranspose | (None, 16, 16, 128) | 147,584 |
| BatchNormalization | (None, 16, 16, 128) | 512 |
| LeakyReLU | (None, 16, 16, 128) | 0 |
| Conv2DTranspose | (None, 32, 32, 128) | 147,584 |
| BatchNormalization | (None, 32, 32, 128) | 512 |
| LeakyReLU | (None, 32, 32, 128) | 0 |
| Conv2DTranspose | (None, 32, 32, 3) | 3,459 |

Total params 700,803
Trainable params 698,755
Non-trainable params 2,048

After around five epochs of training, our VAE should be able to produce novel images of celebrity faces!

# Analysis of the Variational Autoencoder

First, let's take a look at a sample of reconstructed faces. The top row in Figure 3-16 shows the original images and the bottom row shows the reconstructions once they have passed through the encoder and decoder.

![](bbox=[0.13, 0.55, 0.85, 0.68])

Figure 3-16. Reconstructed faces, after passing through the encoder and decoder

We can see that the VAE has successfully captured the key features of each face—the angle of the head, the hairstyle, the expression, etc. Some of the fine detail is missing, but it is important to remember that the aim of building variational autoencoders isn't to achieve perfect reconstruction loss. Our end goal is to sample from the latent space in order to generate new faces.

For this to be possible we must check that the distribution of points in the latent space approximately resembles a multivariate standard normal distribution. If we see any dimensions that are significantly different from a standard normal distribution,