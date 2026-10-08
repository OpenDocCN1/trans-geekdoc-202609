# Image Classification

The summaries will be written to a folder that is interpretable to TensorFlow. Let's define a
 to write the summaries so that TensorFlow can be used to visualize them:

```
def add_variable_summary(tf_variable, summary_name):
    with tf.name_scope(summary_name + '_summary_name'):
        mean = tf.reduce_mean(tf_variable)
        tf.summary.scalar('Mean', mean)
        with tf.name_scope('standard_deviation'):
            standard_deviation = tf.sqrt(tf.reduce_mean(
                tf.square(tf_variable - mean)))
        tf.summary.scalar('StandardDeviation', standard_deviation)
        tf.summary.scalar('Maximum', tf.reduce_max(tf_variable))
        tf.summary.scalar('Minimum', tf.reduce_min(tf_variable))
        tf.summary.histogram('Histogram', tf_variable)
```

The variable function writes the summaries for several variables. There are five statistics
added to the summaries: mean, standard deviation, maximum, minimum and histogram.
Summaries can be either a scalar or a histogram. We will see how these values are
visualized in TensorFlow when logged for several variables. Unlike the previous model,
will resize the MNIST data into a square and use it like a two-dimensional image.
The following is to reshape the image into 28 image pixels by 28 image pixels:

```
x_input_reshape = tf.reshape(x_input, [-1, 28, 28, 1],
name='input_reshape')
```

The dimension -1 denotes that the batch size can be any number. Note that there is
an argument called name that will be reflected in the TensorFlow graph for ease of
understanding. We will define a 2D convolution layer where the input, filters, kernels, and
activations are defined. This method can be called anywhere for further examples and is
useful when the activation function has Rectified Linear Unit (ReLU) activation.
The convolution function layer is defined as:

```
def convolution_layer(input_layer, filters, kernel_size=[3, 3],
    layer = tf.layers.conv2d(
        inputs=input_layer,
        filters=filters,
        kernel_size=kernel_size,
        activation=activation,
    )
n    add_variable_summary(layer, 'convolution')
    return layer
```