| flatten (Flatten) | (None, 3136) | 0 | conv2d_1[0][0] |
| dense (Dense) | (None, 16) | 50192 | flatten[0][0] |
| z_mean (Dense) | (None, 2) | 34 | dense[0][0] |
| z_log_var (Dense) | (None, 2) | 34 | dense[0][0] |
|============================================================================|
| Total params: 69,076 |
| Trainable params: 69,076 |
| Non-trainable params: 0 |

Next is the code for using z_mean and z_log_var, the parameters of the statistical distribution assumed to have produced input_img, to generate a latent space point z.

# Listing 12.25 Latent-space-sampling layer

```
import tensorflow as tf

class Sampler(layers.Layer):
    def call(self, z_mean, z_log_var):
        batch_size = tf.shape(z_mean)[0]
        z_size = tf.shape(z_mean)[1]
        epsilon = tf.random.normal(shape=(batch_size, z_size))
        return z_mean + tf.exp(0.5 * z_log_var) * epsilon
```

The following listing shows the decoder implementation. We reshape the vector z to the dimensions of an image and then use a few convolution layers to obtain a final image output that has the same dimensions as the original input_img.

# Listing 12.26 VAE decoder network, mapping latent space points to images

```
latent_inputs = keras.Input(shape=(latent_dim,))
x = layers.Dense(7 * 7 * 64, activation="relu")(latent_inputs)
x = layers.Reshape((7, 7, 64))(x)
x = layers.Conv2DTranspose(64, 3, activation="relu", strides=2, padding="same")(x)
x = layers.Conv2DTranspose(32, 3, activation="relu", strides=2, padding="same")(x)
decoder_outputs = layers.Conv2D(1, 3, activation="sigmoid", padding="same")(x)
decoder = keras.Model(latent_inputs, decoder_outputs, name="decoder")
```

Its summary looks like this:

```
>>> decoder.summary()
```

Model: "decoder"

| Layer (type) | Output Shape | Param # |
|=============================================================|
| input_2 (InputLayer) | [(None, 2)] | 0 |
| dense_1 (Dense) | (None, 3136) | 9408 |