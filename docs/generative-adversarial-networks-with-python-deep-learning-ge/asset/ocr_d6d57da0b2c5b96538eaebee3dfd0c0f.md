A plot of the model architecture is also created to help get an idea of the inputs, outputs, and transitions of the image data through the model.

![](bbox=[0.33, 0.15, 0.67, 0.77])

Figure 25.1: Plot of the PatchGAN Discriminator Model for the CycleGAN.

# ## 25.4 How to Implement the CycleGAN Generator Model

The CycleGAN Generator model takes an image as input and generates a translated image as output. The model uses a sequence of downsampling convolutional blocks to encode the input