![](bbox=[0.13, 0.1, 0.87, 0.43])

# Figure 8.21: The architecture of stack GAN

The idea behind this model is very similar to the painting approach used by the painters where the painter draws a sketch first and then adds fine details to it. Stack GAN generates images using this sketch refinement process, and it has achieved some of the GAN highest quality images among other GANs, as shown in figure 8.22:

![](bbox=[0.13, 0.59, 0.87, 0.81])

# Figure 8.22: The output of the two stages of the stack GAN

Stack GAN is conditioned on the text description. The Stage-I generator generates low-resolution images with rough shapes and basic colors based on the input text descriptions. The output of Stage-I, which is a low-resolution image, is fed to the