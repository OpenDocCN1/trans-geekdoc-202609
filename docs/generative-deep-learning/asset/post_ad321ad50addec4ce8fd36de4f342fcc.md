
- 3. The second input to the U-Net is the noise variance (a scalar).
- 4. This is encoded using a sinusoidal embedding.
- 5. This embedding is copied across spatial dimensions to match the size of the input image.
- 6. The two input streams are concatenated across channels.
- 7. The `skips` list will hold the output from the `DownBlock` layers that we wish to connect to `UpBlock` layers downstream.
- 8. The tensor is passed through a series of `DownBlock` layers that reduce the size of the image, while increasing the number of channels.
- 9. The tensor is then passed through two `ResidualBlock` layers that hold the image size and number of channels constant.
- 10. Next, the tensor is passed through a series of `UpBlock` layers that increase the size of the image, while decreasing the number of channels. The skip connections incorporate output from the earlier `DownBlock` layers.
- 11. The final `Conv2D` layer reduces the number of channels to three (RGB).
- 12. The U-Net is a Keras `Model` that takes the noisy images and noise variances as input and outputs a predicted noise map.

To understand the U-Net in detail, we need to explore four more concepts: the sinusoidal embedding of the noise variance, the `ResidualBlock`, the `DownBlock`, and the `UpBlock`.

## Sinusoidal embedding

*Sinusoidal embedding* was first introduced in a paper by Vaswani et al.⁶ We will be using an adaptation of that original idea as utilized in Mildenhall et al.’s paper titled “NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis.”⁷

The idea is that we want to be able to convert a scalar value (the noise variance) into a distinct higher-dimensional vector that is able to provide a more complex representation, for use downstream in the network. The original paper used this idea to encode the discrete position of words in a sentence into vectors; the NeRF paper extends this idea to continuous values.

Specifically, a scalar value x is encoded as shown in the following equation:

$\gamma(x) = \left( \sin\left(2\pi e^{0}f x\right), \dots, \sin\left(2\pi e^{(L-1)}f x\right), \cos\left(2\pi e^{0}f x\right), \dots, \cos\left(2\pi e^{(L-1)}f x\right) \right)$

where we choose L = 16 to be half the size of our desired noise embedding length and f = \frac{\ln(1000)}{L-1} to be the maximum scaling factor for the frequencies.

This produces the embedding pattern shown in Figure 8-9.

![](img/f0f0f5d89818fdddf117bbe758ac8143_246_0.png)

Figure 8-9. The pattern of sinusoidal embeddings for noise variances from 0 to 1

We can code this sinusoidal embedding function as shown in Example 8-7. This converts a single noise variance scalar value into a vector of length 32.

### Example 8-7. The sinusoidal_embedding function that encodes the noise variance

```
def sinusoidal_embedding(x):
    frequencies = tf.exp(
        tf.linspace(
            tf.math.log(1.0),
            tf.math.log(1000.0),
            16,
        )
    )
    angular_speeds = 2.0 * math.pi * frequencies
    embeddings = tf.concat(
        [tf.sin(angular_speeds * x), tf.cos(angular_speeds * x)], axis=3
    )
    return embeddings
```

## ResidualBlock

Both the DownBlock and the UpBlock contain ResidualBlock layers, so let's start with these. We already explored residual blocks in Chapter 5, when we built a PixelCNN, but we will recap here for completeness.

A residual block is a group of layers that contains a skip connection that adds the input to the output. Residual blocks help us to build deeper networks that can learn more complex patterns without suffering as greatly from vanishing gradient and degradation problems. The vanishing gradient problem is the assertion that as the network gets deeper, the gradient propagated through deeper layers is tiny and therefore learning is very slow. The degradation problem is the fact that as neural networks become deeper, they are not necessarily as accurate as their shallower counterparts—accuracy seems to become saturated at a certain depth and then degrade rapidly.

![](img/f0f0f5d89818fdddf117bbe758ac8143_247_0.png)

### Degradation

The degradation problem is somewhat counterintuitive, but observed in practice as the deeper layers must at least learn the identity mapping, which is not trivial—especially considering other problems deeper networks face, such as the vanishing gradient problem.

The solution, first introduced in the ResNet paper by He et al. in 2015,8 is very simple. By including a skip connection highway around the main weighted layers, the block has the option to bypass the complex weight updates and simply pass through the identity mapping. This allows the network to be trained to great depth without sacrificing gradient size or network accuracy.

A diagram of a ResidualBlock is shown in Figure 8-10. Note that in some residual blocks, we also include an extra Conv2D layer with kernel size 1 on the skip connection, to bring the number of channels in line with the rest of the block.

![](img/f0f0f5d89818fdddf117bbe758ac8143_247_1.png)

Figure 8-10. The ResidualBlock in the U-Net

We can code a ResidualBlock in Keras as shown in Example 8-8.

### Example 8-8. Code for the ResidualBlock in the U-Net

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

- 1. Check if the number of channels in the input matches the number of channels that we would like the block to output. If not, include an extra Conv2D layer on the skip connection to bring the number of channels in line with the rest of the block.
- 2. Apply a BatchNormalization layer.
- 3. Apply two Conv2D layers.
- 4. Add the original block input to the output to provide the final output from the block.

## DownBlocks and UpBlocks

Each successive DownBlock increases the number of channels via block_depth (=2 in our example) ResidualBlocks, while also applying a final AveragePooling2D layer in order to halve the size of the image. Each ResidualBlock is added to a list for use later by the UpBlock layers as skip connections across the U-Net.

An UpBlock first applies an UpSampling2D layer that doubles the size of the image, through bilinear interpolation. Each successive UpBlock decreases the number of channels via block_depth (=2) ResidualBlocks, while also concatenating the outputs from the DownBlocks through skip connections across the U-Net. A diagram of this process is shown in Figure 8-11.

![](img/f0f0f5d89818fdddf117bbe758ac8143_249_0.png)

Figure 8-11. The DownBlock and corresponding UpBlock in the U-Net

We can code the DownBlock and UpBlock using Keras as illustrated in Example 8-9.

### Example 8-9. Code for the DownBlock and UpBlock in the U-Net model

```python
def DownBlock(width, block_depth):
    def apply(x):
        x, skips = x
        for _ in range(block_depth):
            x = ResidualBlock(width)(x) ①
            skips.append(x) ②
        x = layers.AveragePooling2D(pool_size=2)(x) ③
        return x

    return apply

def UpBlock(width, block_depth):
    def apply(x):
        x, skips = x
        x = layers.UpSampling2D(size=2, interpolation="bilinear")(x) ④
        for _ in range(block_depth):
            x = layers.Concatenate()([x, skips.pop()]) ⑤
            x = ResidualBlock(width)(x) ⑥
        return x

    return apply
```

- 1. The DownBlock increases the number of channels in the image using a Residual Block of a given width...
- 2. ...each of which are saved to a list (skips) for use later by the UpBlocks.
- 3. A final AveragePooling2D layer reduces the dimensionality of the image by half.
- 4. The UpBlock begins with an UpSampling2D layer that doubles the size of the image.
- 5. The output from a DownBlock layer is glued to the current output using a Concatenate layer.
- 6. A ResidualBlock is used to reduce the number of channels in the image as it passes through the UpBlock.

## Training the Diffusion Model

We now have all the components in place to train our denoising diffusion model! Example 8-10 creates, compiles, and fits the diffusion model.

### Example 8-10. Code for training the DiffusionModel

```
model = DiffusionModel() ①
model.compile(
    optimizer=optimizers.experimental.AdamW(learning_rate=1e-3, weight_decay=1e-4),
    loss=losses.mean_absolute_error,
) ②

model.normalizer.adapt(train) ③

model.fit(
    train,
    epochs=50,
) ④
```

- 1. Instantiate the model.
- 2. Compile the model, using the AdamW optimizer (similar to Adam but with weight decay, which helps stabilize the training process) and mean absolute error loss function.
- 3. Calculate the normalization statistics using the training set.
- 4. Fit the model over 50 epochs.
