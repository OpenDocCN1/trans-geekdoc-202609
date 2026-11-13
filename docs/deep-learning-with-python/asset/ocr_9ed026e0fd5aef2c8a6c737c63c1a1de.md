# 12.5.5 The generator

Next, let's develop a generator model that turns a vector (from the latent space— during training it will be sampled at random) into a candidate image.

# Listing 12.35 GAN generator network

```
latent_dim = 128
generator = keras.Sequential(
    [
        keras.Input(shape=(latent_dim,)),
        layers.Dense(8 * 8 * 128),
        layers.Reshape((8, 8, 128)),
        layers.Conv2DTranspose(128, kernel_size=4, strides=2, padding="same"),
        layers.LeakyReLU(alpha=0.2),
        layers.Conv2DTranspose(256, kernel_size=4, strides=2, padding="same"),
        layers.LeakyReLU(alpha=0.2),
        layers.Conv2DTranspose(512, kernel_size=4, strides=2, padding="same"),
        layers.LeakyReLU(alpha=0.2),
        layers.Conv2D(3, kernel_size=5, padding="same", activation="sigmoid"),
    ],
    name="generator",
)
```

Revert the Flatten layer of the encoder.

Revert the Conv2D layers of the encoder.

The output ends up with shape (28, 28, 1).

The latent space will be made of 128-dimensional vectors.

Produce the same number of coefficients we had at the level of the Flatten layer in the encoder.

We use LeakyReLU as our activation.

This is the generator model summary:

```
>>> generator.summary()
Model: "generator"
```

| Layer (type) | Output Shape | Param # |
| --- | --- | --- |
| dense_1 (Dense) | (None, 8192) | 1056768 |
| reshape (Reshape) | (None, 8, 8, 128) | 0 |
| conv2d_transpose (Conv2DTran | (None, 16, 16, 128) | 262272 |
| leaky_re_lu_3 (LeakyReLU) | (None, 16, 16, 128) | 0 |
| conv2d_transpose_1 (Conv2DTr | (None, 32, 32, 256) | 524544 |
| leaky_re_lu_4 (LeakyReLU) | (None, 32, 32, 256) | 0 |
| conv2d_transpose_2 (Conv2DTr | (None, 64, 64, 512) | 2097664 |
| leaky_re_lu_5 (LeakyReLU) | (None, 64, 64, 512) | 0 |
| conv2d_3 (Conv2D) | (None, 64, 64, 3) | 38403 |

Total params: 3,979,651
Trainable params: 3,979,651
Non-trainable params: 0