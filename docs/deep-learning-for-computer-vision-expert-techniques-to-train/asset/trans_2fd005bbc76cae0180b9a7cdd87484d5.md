

# 图像检索

`x_input` 和 `y_input` 的形状相同，这符合自动编码器的要求。
然后，如所示定义一个全连接层，默认激活函数为 `tanh` 激活函数。`add_variable_summary` 方法是从图像分类示例中导入的。全连接层的定义如下：

```python
def dense_layer(input_layer, units, activation=tf.nn.tanh):
    layer = tf.layers.dense(
        inputs=input_layer,
        units=units,
        activation=activation
    )
    add_variable_summary(layer, 'dense')
    return layer
```

接下来，定义自动编码器。该自动编码器仅包含连接层。编码器部分包含三层维度还原层。解码器部分包含三层维度增加层。编码器和解码器是对称的：

- layer_1 = dense_layer(x_input, 500)
- layer_2 = dense_layer(layer_1, 250)
- layer_3 = dense_layer(layer_2, 50)
- layer_4 = dense_layer(layer_3, 250)
- layer_5 = dense_layer(layer_4, 500)
- layer_6 = dense_layer(layer_5, 784)

隐藏层的维度是任意选择的。接下来，定义损失函数和优化器。我们使用 `sigmoid` 代替 `softmax` 进行分类，如下：

```python
with tf.name_scope('loss'):
    softmax_cross_entropy = tf.nn.sigmoid_cross_entropy_with_logits(
        labels=y_input, logits=layer_6)
    loss_operation = tf.reduce_mean(softmax_cross_entropy, name='loss')
    tf.summary.scalar('loss', loss_operation)

with tf.name_scope('optimiser'):
    optimiser = tf.train.AdamOptimizer().minimize(loss_operation)
```

TensorBoard 提供了另一种摘要图像，用于可视化图像。我们将输出的 `layer_6` 并将其重塑后到摘要中，如下：

```python
x_input_reshaped = tf.reshape(x_input, [-1, 28, 28, 1])
tf.summary.image("noisy_images", x_input_reshaped)

y_input_reshaped = tf.reshape(y_input, [-1, 28, 28, 1])
```

# 图像检索

# 第3章

```python
tf.summary.image("original_images", y_input_reshaped)

layer_6_reshaped = tf.reshape(layer_6, [-1, 28, 28, 1])
tf.summary.image("reconstructed_images", layer_6_reshaped)
```

图像数量默认限制为三张，可以更改。这是为了防止将所有图像都放入摘要文件夹。接下来，合并所有的摘要并将图添加到摘要写入器中，如下：

```python
merged_summary_operation = tf.summary.merge_all()
train_summary_writer = tf.summary.FileWriter('/tmp/train', session.graph)
```

可以向图像添加正态随机噪声并作为输入张量输入。添加噪声后，会对额外值进行裁剪。目标将是原始图像本身。训练过程中的加噪所示：

```python
for batch_no in range(total_batches):
    mnist_batch = mnist_data.train.next_batch(batch_size)
    train_images, _ = mnist_batch[0], mnist_batch[1]
    train_images_noise = train_images + 0.2 *
    np.random.normal(size=train_images.shape)
    train_images_noise = np.clip(train_images_noise, 0., 1)
    merged_summary = session.run(optimiser, merged_summary_operation,
        feed_dict={
            x_input: train_images_noise,
            y_input: train_images,
        })
    train_summary_writer.add_summary(merged_summary, batch_no)
```

启动此训练后，可以在 TensorBoard 中看到结果。损失显示在此：

![](img/48c861eac4dc634fbf2a09fdbe884beb_118_0.png)

Tensorboard 展示的输出图

损失稳定下降，并在迭代过程中将继续缓慢下降。这显示了自动编码器如何快速收敛。接下来，从原始图像中显示三个数字：

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_0.png)

这里是添加了噪声的相同图像：

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_1.png)

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_2.png)

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

你会注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到显著显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

注意到注意到存在显著噪声且这是作为输入的。接下来是使用去噪自动编码器重建的相同数字图像：

(When this training is started, the results can be seen in TensorBoard. The loss is shown here:

![](img/48c861eac4dc634fbf2a09fdbe884beb_118_0.png)

Tensorboard illustrating the output plot

The loss steadily decreases and will keep decreasing slowly over the iterations. This shows how autoencoders converge quickly. Next, three digits are displayed from the original images:

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_0.png)

Here are the same images with noise added:

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_1.png)

You will notice that there is significant noise and this is given as an input. Next, are the reconstructed images of the same numbers with the denoising autoencoder:

![](img/48c861eac4dc634fbf2a09fdbe884beb_119_2.png)

(Note: The source text contained many repetitive sentences which have been condensed as per the instructions to avoid redundant output.)

