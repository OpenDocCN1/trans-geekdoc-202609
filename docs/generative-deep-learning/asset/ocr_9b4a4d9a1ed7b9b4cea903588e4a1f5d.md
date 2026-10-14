# Equalized learning rates

All dense and convolutional layers in ProGAN use *equalized learning rates*. Usually, weights in a neural network are initialized using a method such as *He initialization*—a Gaussian distribution where the standard deviation is scaled to be inversely proportional to the square root of the number of inputs to the layer. This way, layers with a greater number of inputs will be initialized with weights that have a smaller deviation from zero, which generally improves the stability of the training process.

The authors of the ProGAN paper found that this was causing problems when used in combination with modern optimizers such as Adam or RMSProp. These methods normalize the gradient update for each weight, so that the size of the update is independent of the scale (magnitude) of the weight. However, this means that weights with a larger dynamic range (i.e., layers with fewer inputs) will take comparatively longer to adjust than weights with a smaller dynamic range (i.e., layers with more inputs). It was found that this causes an imbalance between the speed of training of the different layers of the generator and discriminator in ProGAN, so they used *equalized learning rates* to solve this problem.

In ProGAN, weights are initialized using a simple standard Gaussian, regardless of the number of inputs to the layer. The normalization is applied dynamically, as part of the call to the layer, rather than only at initialization. This way, the optimizer sees each weight as having approximately the same dynamic range, so it applies the same learning rate. It is only when the layer is called that the weight is scaled by the factor from the He initializer.

# Pixelwise normalization

Lastly, in ProGAN *pixelwise normalization* is used in the generator, rather than batch normalization. This normalizes the feature vector in each pixel to a unit length and helps to prevent the signal from spiraling out of control as it propagates through the network. The pixelwise normalization layer has no trainable weights.

# Outputs

In addition to the CelebA dataset, ProGAN was also applied to images from the Large-scale Scene Understanding (LSUN) dataset with excellent results, as shown in Figure 10-7. This demonstrated the power of ProGAN over earlier GAN architectures and paved the way for future iterations such as StyleGAN and StyleGAN2, which we shall explore in the next sections.