We then explored how the Wasserstein loss function remedied many of these problems and made GAN training more predictable and reliable. The WGAN-GP places the 1-Lipschitz requirement at the heart of the training process by including a term in the loss function to pull the gradient norm toward 1.

We applied the WGAN-GP to the problem of face generation and saw how by simply choosing points from a standard normal distribution, we can generate new faces. This sampling process is very similar to a VAE, though the faces produced by a GAN are quite different—often sharper, with greater distinction between different parts of the image.

Finally, we built a CGAN that allowed us to control the type of image that is generated. This works by passing in the label as input to the critic and generator, thereby giving the network the additional information it needs in order to condition the generated output on a given label.

Overall, we have seen how the GAN framework is extremely flexible and able to be adapted to many interesting problem domains. In particular, GANs have driven significant progress in the field of image generation with many interesting extensions to the underlying framework, as we shall see in Chapter 10.

In the next chapter, we will explore a different family of generative model that is ideal for modeling sequential data—autoregressive models.

# References

+   1. Ian J. Goodfellow et al., “Generative Adversarial Nets,” June 10, 2014, https://arxiv.org/abs/1406.2661
+   2. Alec Radford et al., “Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks,” January 7, 2016, https://arxiv.org/abs/1511.06434.
+   3. Augustus Odena et al., “Deconvolution and Checkerboard Artifacts,” October 17, 2016, https://distill.pub/2016/deconv-checkerboard.
+   4. Martin Arjovsky et al., “Wasserstein GAN,” January 26, 2017, https://arxiv.org/abs/1701.07875.
+   5. Ishaan Gulrajani et al., “Improved Training of Wasserstein GANs,” March 31, 2017, https://arxiv.org/abs/1704.00028.
+   6. Mehdi Mirza and Simon Osindero, “Conditional Generative Adversarial Nets,” November 6, 2014, https://arxiv.org/abs/1411.1784.