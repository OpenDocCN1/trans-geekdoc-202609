
`filters=filters`,

`kernel_size=kernel_size`,

`activation=activation`,

`kernel_regularizer=tf.nn.l2_loss`,

`bias_regularizer=None`

)

`add_variable_summary(layer, 'convolution')`

`return layer`

```
接下来，我们将使用以下代码定义一个 `transpose_convolution_layer`，它是带有正则化的 `convolution_layer` 的相反操作：
```python
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
接下来，我们将使用以下代码定义一个带有非线性激活的全连接层：
```python
def dense_layer(input_layer,
    units,
    activation=tf.nn.relu):
    layer = tf.layers.dense(
        inputs=input_layer,
        units=units,
        activation=activation
    )
    add_variable_summary(layer, 'dense')
    return layer
```
现在，我们将定义一个接收噪声作为输入并转换为图像的生成器。生成器由几个全连接层组成，后面跟转置卷积层以对噪声进行上采样。最后，通过一个卷积层使噪声变为单通道。在每层之间都有批归一化层，以便梯度平滑流动。我们将使用以下代码定义生成器：
```python
def get_generator(input_noise, is_training=True):
    generator = dense_layer(input_noise, 1024)
    generator = tf.layers.batch_normalization(generator,
        training=is_training)
    generator = dense_layer(generator, 7 * 7 * 256)
    generator = tf.layers.batch_normalization(generator,
        training=is_training)
    generator = tf.reshape(generator, [-1, 7, 7, 256])
    generator = transpose_convolution_layer(generator)
    generator = tf.layers.batch_normalization(generator,
        training=is_training)
    generator = transpose_convolution_layer(generator)
    generator = tf.layers.batch_normalization(generator,
        training=is_training)
    generator = convolution_layer(generator, 3)
    generator = convolution_layer(generator, 1, activation=tf.tanh)
    return generator
```
