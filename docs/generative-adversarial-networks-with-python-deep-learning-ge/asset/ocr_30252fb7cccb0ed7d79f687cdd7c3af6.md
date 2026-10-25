# 22.4 How to Implement the U-Net Generator Model

The generator model for the Pix2Pix GAN is implemented as a U-Net. The U-Net model is an encoder-decoder model for image translation where skip connections are used to connect layers in the encoder with corresponding layers in the decoder that have the same sized feature maps. The encoder part of the model is comprised of convolutional layers that use a 2 × 2 stride to downsample the input source image down to a bottleneck layer. The decoder part of the model reads the bottleneck output and uses transpose convolutional layers to upsample to the required output image size.

> ... the input is passed through a series of layers that progressively downsample, until
> a bottleneck layer, at which point the process is reversed.
> 
> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

![](bbox=[0.303, 0.375, 0.678, 0.558])

Figure 22.2: Architecture of the U-Net Generator Model. Taken from Image-to-Image Translation
With Conditional Adversarial Networks.

Skip connections are added between the layers with the same sized feature maps so that the
first downsampling layer is connected with the last upsampling layer, the second downsampling
layer is connected with the second last upsampling layer, and so on. The connections concatenate
the channels of the feature map in the downsampling layer with the feature map in the upsampling
layer.

Specifically, we add skip connections between each layer i and layer n - i, where n
is the total number of layers. Each skip connection simply concatenates all channels
at layer i with those at layer n - i.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

Unlike traditional generator models in the GAN architecture, the U-Net generator does not
take a point from the latent space as input. Instead, dropout layers are used as a source of
randomness both during training and when the model is used to make a prediction, e.g. generate
an image at inference time. Similarly, batch normalization is used in the same way during