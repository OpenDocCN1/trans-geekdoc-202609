# 22.4. How to Implement the U-Net Generator Model

training and inference, meaning that statistics are calculated for each batch and not fixed at the end of the training process. This is referred to as instance normalization, specifically when the batch size is set to 1 as it is with the Pix2Pix model.

At inference time, we run the generator net in exactly the same manner as during the training phase. This differs from the usual protocol in that we apply dropout at test time, and we apply batch normalization using the statistics of the test batch, rather than aggregated statistics of the training batch.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

In Keras, layers like Dropout and BatchNormalization operate differently during training and in inference model. We can set the training argument when calling these layers to True to ensure that they always operate in training-model, even when used during inference. For example, a Dropout layer that will drop out during inference as well as training can be added to the model as follows:

```
...
g = Dropout(0.5)(g, training=True)
```

Listing 22.4: Example of configuring a Dropout layer to operate during inference.

As with the discriminator model, the configuration details of the generator model are defined in the appendix of the paper and can be confirmed when comparing against the defineG_unet() function in the official Torch implementation3. The encoder uses blocks of Convolution-BatchNorm-LeakyReLU like the discriminator model, whereas the decoder model uses blocks of Convolution-BatchNorm-Dropout-ReLU with a dropout rate of 50%. All convolutional layers use a filter size of 4 x 4 and a stride of 2 x 2.

Let Ck denote a Convolution-BatchNorm-ReLU layer with k filters. CDk denotes a Convolution-BatchNormDropout-ReLU layer with a dropout rate of 50%. All convolutions are 4 x 4 spatial filters applied with stride 2.

> — Image-to-Image Translation with Conditional Adversarial Networks, 2016.

The architecture of the U-Net model is defined using the shorthand notation as:

+   • Encoder: C64-C128-C256-C512-C512-C512-C512-C512
+   • Decoder: CD512-CD1024-CD1024-C1024-C1024-C512-C256-C128

The last layer of the encoder is the bottleneck layer, which does not use batch normalization, according to an amendment to the paper and confirmation in the code, and uses a ReLU activation instead of leaky ReLU.

... the activations of the bottleneck layer are zeroed by the batchnorm operation, effectively making the innermost layer skipped. This issue can be fixed by removing batchnorm from this layer, as has been done in the public code