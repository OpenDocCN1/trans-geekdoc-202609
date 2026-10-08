# Vanilla GAN

The original GAN is called a vanilla GAN. Before we construct the model, let's define a few layers that will be useful for the rest of the chapter. The following is the convolutional_layers with leaky activations and regularization added:

```
def convolution_layer(input_layer,
    filters,
    kernel_size=[4, 4],
    activation=tf.nn.leaky_relu):
    layer = tf.layers.conv2d(
        inputs=input_layer,
        filters=filters,
        kernel_size=kernel_size,
        activation=activation,
        kernel_regularizer=tf.nn.l2_loss,
        bias_regularizer=None
    )
    add_variable_summary(layer, 'convolution')
    return layer
```

Next, we will define a transpose_convolution_layer that is the opposite of a convolution_layer with regularization, using the following code:

```
def transpose_convolution_layer(input_layer,
    filters,
    kernel_size=[4, 4],
    activation=tf.nn.relu,
    strides=2):
    layer = tf.layers.conv2d_transpose(
        inputs=input_layer,
        filters=filters,
        kernel_size=kernel_size,
        activation=activation,
        strides=strides,
        kernel_regularizer=tf.nn.l2_loss,
        bias_regularizer=None
    )
    add_variable_summary(layer, 'convolution')
    return layer
```