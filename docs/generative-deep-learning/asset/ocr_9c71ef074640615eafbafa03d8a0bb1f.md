We can code a ResidualBlock in Keras as shown in Example 8-8.

# Example 8-8. Code for the ResidualBlock in the U-Net

```
def ResidualBlock(width):
    def apply(x):
        input_width = x.shape[3]
        if input_width == width:
            residual = x
        else:
            residual = layers.Conv2D(width, kernel_size=1)(x)
        x = layers.BatchNormalization(center=False, scale=False)(x)
        x = layers.Conv2D(
            width, kernel_size=3, padding="same", activation=activations.swish
        )(x)
        x = layers.Conv2D(width, kernel_size=3, padding="same")(x)
        x = layers.Add()([x, residual])
        return x
    return apply
```

+   1. Check if the number of channels in the input matches the number of channels that we would like the block to output. If not, include an extra Conv2D layer on the skip connection to bring the number of channels in line with the rest of the block.
+   2. Apply a BatchNormalization layer.
+   3. Apply two Conv2D layers.
+   4. Add the original block input to the output to provide the final output from the block.

# DownBlocks and UpBlocks

Each successive DownBlock increases the number of channels via block_depth (=2 in our example) ResidualBlocks, while also applying a final AveragePooling2D layer in order to halve the size of the image. Each ResidualBlock is added to a list for use later by the UpBlock layers as skip connections across the U-Net.

An UpBlock first applies an UpSampling2D layer that doubles the size of the image, through bilinear interpolation. Each successive UpBlock decreases the number of channels via block_depth (=2) ResidualBlocks, while also concatenating the outputs from the DownBlocks through skip connections across the U-Net. A diagram of this process is shown in Figure 8-11.