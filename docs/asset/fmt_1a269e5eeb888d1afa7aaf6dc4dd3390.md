
```
inputs = layers.Input(shape=(16, 16, 1)) ①
x = MaskedConv2D(mask_type="A"
    , filters=128
    , kernel_size=7
    , activation="relu"
    , padding="same")(inputs)②

for _ in range(5):
    x = ResidualBlock(filters=128)(x) ③

for _ in range(2):
    x = MaskedConv2D(
        mask_type="B",
        filters=128,
        kernel_size=1,
        strides=1,
        activation="relu",
        padding="valid",
    )(x) ④

out = layers.Conv2D(
    filters=4, kernel_size=1, strides=1, activation="softmax", padding="valid"
)(x) ⑤

pixel_cnn = models.Model(inputs, out) ⑥

adam = optimizers.Adam(learning_rate=0.0005)
pixel_cnn.compile(optimizer=adam, loss="sparse_categorical_crossentropy")

pixel_cnn.fit(
    input_data
  , output_data
  , batch_size=128
  , epochs=150
) ⑦
```

1. 模型输入是一个大小为 16 × 16 × 1 的灰度图像，输入值在 0 到 1 之间进行缩放。

2. 第一个核大小为 7 的 Type A `MaskedConv2D` 层使用来自 24 个像素的信息——焦点像素上方三行中的 21 个像素以及左侧 3 个像素（焦点像素本身未使用）。

3. 五个 `ResidualBlock` 层组按顺序堆叠。

4. 两个核大小为 1 的 Type B `MaskedConv2D` 层充当每个像素在通道数上的 Dense 层。

5. 最终的 `Conv2D` 层将通道数减少到四个——这是本示例中像素级的数量。

6. 模型构建为接受一张图像并输出尺寸相同的图像。

7. 拟合模型——`input_data` 的缩放范围为 [0, 1]（浮点数）；`output_data` 的缩放范围为 [0, 3]（整数）。

## Analysis of the PixelCNN

我们可以在第 3 章中遇到的 Fashion-MNIST 数据集的图像上训练 `PixelCNN`。生成新图像时，我们需要让模型一次一个像素地根据所有先前的像素预测下一个像素。相比于变分自编码器等模型，这是一个非常缓慢的过程！对于一张 32 × 32 的灰度图像，我们需要使用模型按顺序进行 1,024 次预测，而 `VAE` 只需要一次预测。这就是自回归模型（如 `PixelCNN`）的主要缺点之一——由于采样过程的顺序性，它们采样速度很慢。

因此，我们使用 16 × 16 的图像尺寸，而不是 32 × 32，以加快新图像的生成速度。生成回调类在示例 5-15 中展示。

### Example 5-15. Generating new images using the PixelCNN

```
class ImageGenerator(callbacks.Callback):
    def __init__(self, num_img):
        self.num_img = num_img

    def sample_from(self, probs, temperature):
        probs = probs ** (1 / temperature)
        probs = probs / np.sum(probs)
        return np.random.choice(len(probs), p=probs)

    def generate(self, temperature):
        generated_images = np.zeros(
            shape=(self.num_img,) + (pixel_cnn.input_shape)[1:]
        ) ①
        batch, rows, cols, channels = generated_images.shape

        for row in range(rows):
            for col in range(cols):
                for channel in range(channels):
                    probs = self.model.predict(generated_images)[
                        :, row, col, :
                    ] ②
                    generated_images[:, row, col, channel] = [
                        self.sample_from(x, temperature) for x in probs
                    ] ③
                    generated_images[:, row, col, channel] /= 4 ④
        return generated_images

    def on_epoch_end(self, epoch, logs=None):
        generated_images = self.generate(temperature = 1.0)
        display(
            generated_images,
            save_to = "./output/generated_img_%03d.png" % (epoch)
        )

img_generator_callback = ImageGenerator(num_img=10)
```

1. 从一批空图像（全零）开始。

2. 遍历当前图像的行、列和通道，预测下一个像素值的分布。

3. 从预测的分布中采样一个像素级（对于我们的示例，范围在 [0, 3] 内的等级）。

4. 将像素级转换为 [0, 1] 范围并覆盖当前图像中的像素值，为循环的下一次迭代做好准备。

在图 5-15 中，我们可以看到来自原始训练集的几张图像，以及由 `PixelCNN` 生成的图像。

### Images from the training set

![](img/f0f0f5d89818fdddf117bbe758ac8143_187_0.png)

### Generated images

![](img/f0f0f5d89818fdddf117bbe758ac8143_187_1.png)

Figure 5-15. Example images from the training set and generated images created by the PixelCNN model

图 5-15. 来自训练集的示例图像以及由 PixelCNN 模型创建的生成图像

该模型在重现原始图像的整体形状和风格方面做得非常好！令人惊讶的是，我们可以将图像视为一系列标记（像素值），并应用 `PixelCNN` 等自回归模型来生成逼真的样本。

如前所述，自回归模型的一个缺点是采样速度慢，这就是为什么本书中只展示了它们应用的简单示例。然而，正如我们在第 10 章中将看到的那样，更复杂的自回归模型形式可以应用于图像以产生最先进的输出。在这种情况下，缓慢的生成速度是为了换取卓越质量的输出而必须付出的代价。

自原始论文发表以来，`PixelCNN` 的架构和训练过程已进行了多项改进。以下部分介绍其中一项改进——使用混合分布——并演示如何使用内置 TensorFlow 函数训练具有此改进的 `PixelCNN` 模型。

## Mixture Distributions

对于之前的示例，我们将 `PixelCNN` 的输出减少到仅 4 个像素级，以确保网络不必学习 256 个独立像素值的分布，这会减慢训练过程。然而，这远非理想——对于彩色图像，我们不希望画布仅限于少数几种可能的颜色。

为了解决这个问题，我们可以使网络的输出成为混合分布，而不是 256 个离散像素值上的 softmax，遵循 Salimans 等人⁴ 提出的思想。混合分布很简单就是两种或多种其他概率分布的混合。例如，我们可以有五个逻辑分布的混合分布，每个分布具有不同的参数。混合分布还要求一个离散的分类分布，表示选择混合中包含的每个分布的概率。示例见图 5-16。

![](img/f0f0f5d89818fdddf117bbe758ac8143_188_0.png)

Figure 5-16. A mixture distribution of three normal distributions with different parameters—the categorical distribution over the three normal distributions is [0.5, 0.3, 0.2]

图 5-16. 三个参数不同的正态分布的混合分布——三个正态分布上的分类分布为 [0.5, 0.3, 0.2]

从混合分布中采样时，我们首先从分类分布中采样以选择特定的子分布，然后以通常的方式从中采样。这样，我们就可以用相对较少的参数创建复杂的分布。

例如，图 5-16 中的混合分布仅需要八个参数——分类分布的两个参数，以及三个正态分布各自的均值和方差。相比之下，定义整个像素范围上的分类分布需要 255 个参数。

方便的是，TensorFlow Probability 库提供了一个函数，允许我们在一行代码中创建具有混合分布输出的 `PixelCNN`。示例 5-16 说明了如何使用此函数构建 `PixelCNN`。

![](img/f0f0f5d89818fdddf117bbe758ac8143_189_0.png)

### Running the Code for This Example

本示例的代码可以在书库中的 `notebooks/05_autoregressive/03_pixelcnn_md/pixelcnn_md.ipynb` Jupyter notebook 中找到。

### Example 5-16. Building a PixelCNN using the TensorFlow function

```
import tensorflow_probability as tfp

dist = tfp.distributions.PixelCNN(
    image_shape=(32, 32, 1),
    num_resnet=1,
    num_hierarchies=2,
    num_filters=32,
    num_logistic_mix=5,
    dropout_p=.3,
)

image_input = layers.Input(shape=(32, 32, 1))
log_prob = dist.log_prob(image_input)

model = models.Model(inputs=image_input, outputs=log_prob)
model.add_loss(-tf.reduce_mean(log_prob))
```

1. 将 `PixelCNN` 定义为分布——即输出层是由五个逻辑分布组成的混合分布。

2. 输入是大小为 32 × 32 × 1 的灰度图像。

3. 模型以灰度图像作为输入，并输出在 `PixelCNN` 计算的混合分布下图像的对数似然。

4. 损失函数是输入图像批次上的平均负对数似然。

The model is trained in the same way as before, but this time accepting integer pixel values as input, in the range [0, 255]. Outputs can be generated from the distribution using the `sample` function, as shown in Example 5-17.

### Example 5-17. Sampling from the PixelCNN mixture distribution

```
dist.sample(10).numpy()
```

Example generated images are shown in Figure 5-17. The difference from our previous examples is that now the full range of pixel values is being utilized.

![](img/f0f0f5d89818fdddf117bbe758ac8143_190_0.png)

Figure 5-17. Outputs from the PixelCNN using a mixture distribution output

## Summary

In this chapter we have seen how autoregressive models such as recurrent neural networks can be applied to generate text sequences that mimic a particular style of writing, and also how a `PixelCNN` can generate images in a sequential fashion, one pixel at a time.

We explored two different types of recurrent layers—long short-term memory (LSTM) and gated recurrent unit (GRU)—and saw how these cells can be stacked or made bidirectional to form more complex network architectures. We built an LSTM to generate realistic recipes using Keras and saw how to manipulate the temperature of the sampling process to increase or decrease the randomness of the output.

We also saw how images can be generated in an autoregressive manner, using a `PixelCNN`. We built a `PixelCNN` from scratch using Keras, coding the masked convolutional layers and residual blocks to allow information to flow through the network so that only preceding pixels could be used to generate the current pixel. Finally, we discussed how the TensorFlow Probability library provides a standalone `PixelCNN` function that implements a mixture distribution as the output layer, allowing us to further improve the learning process.

In the next chapter we will explore another generative modeling family that explicitly models the data-generating distribution—normalizing flow models.

## References

1. Sepp Hochreiter and Jürgen Schmidhuber, "Long Short-Term Memory," *Neural Computation* 9 (1997): 1735–1780, https://www.bioinf.jku.at/publications/older/2604.pdf.

2. Kyunghyun Cho et al., "Learning Phrase Representations Using RNN Encoder-Decoder for Statistical Machine Translation," June 3, 2014, https://arxiv.org/abs/1406.1078.

3. Aaron van den Oord et al., "Pixel Recurrent Neural Networks," August 19, 2016, https://arxiv.org/abs/1601.06759.

4. Tim Salimans et al., "PixelCNN++: Improving the PixelCNN with Discretized Logistic Mixture Likelihood and Other Modifications," January 19, 2017, http://arxiv.org/abs/1701.05517.

## Normalizing Flow Models

### Chapter Goals
