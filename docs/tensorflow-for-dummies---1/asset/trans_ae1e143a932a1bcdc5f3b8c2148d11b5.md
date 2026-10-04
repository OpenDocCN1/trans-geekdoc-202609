

| `bias_ initializer` || `tf.zeros.initializer()` || 层的偏置的初始化器 |
| `kernel_ regularizer` || `None` || 过滤器值（权重）的正则化器 |
| `bias_ regularizer` || `None` || 层的偏置的正则化器 |
| `activity_ regularizer` || `None` || 层输出的正则化器 |
| `trainable` || `True` || 布尔值，用于标识是否将过滤器的元素添加到图的训练变量中 |
| `name` || `None` || 层的名称 |
| `reuse` || `False` || 布尔值，用于标识是否重用同名作用域的权重 |

应用程序必须将 `inputs` 设置为其形状取决于 `data_format` 参数的张量。如果将 `data_format` 设置为 `channels_last`（默认值），则 `inputs` 张量应具有等于 `[batch_size, height, width, channels]` 的形状。如果将 `data_format` 设置为 `channels_first`，则 `inputs` 张量应具有等于 `[batch_size, channels, height, width]` 的形状。

`filters` 参数标识卷积层使用的过滤器数量。`kernel_size` 参数标识每个过滤器的大小。如果将此参数设置为单个值 N，则每个过滤器的大小将为 NxN。如果将其设置为两个值，例如 `[M, N]`，则每个过滤器的大小将为 MxN。

之前的 “[Setting convolution parameters](#13_9788126592555-ch08.xhtml#c08-sec-0007)” 部分讨论了图像过滤器的步幅和扩张特性。在 `tf.layers.conv2d` 中，您可以使用 `strides` 和 `dilation_rate` 参数设置这些属性。

`padding` 参数告诉层如何处理图像的边界像素。如果将 `padding` 设置为 `valid`，层将忽略边界像素并返回比输入图像小的输出图像。如果将 `padding` 设置为 `same`，层将用零填充输入图像并生成与输入图像大小相同的输出图像。

`tf.layers.conv2d` 返回一个张量，其形状取决于输入图像的形状、过滤器数量和 `padding` 参数。例如，如果输入的形状为 `[N, height, width, num_channels]` 且 `padding` 设置为 `same`，则输出的形状将为 `[N, height, width, num_filters]`。

通道数不影响输出的形状。在执行卷积时，`tf.layers.conv2d` 将通道合并在一起，因此灰度输入图像和 RGB 输入图像会产生相同大小的输出图像。如果您想执行通道特定的过滤，应使用的函数是 `tf.nn.depthwise_conv2d`。

如果应用程序将 `padding` 设置为 `valid`，每个输出图像将小于输入图像。大小的减少取决于卷积过滤器的尺寸。例如，如果 `padding` 为 `valid`，过滤器大小等于 `[X, Y]`，且输入的形状为 `[N, height, width, num_channels]`，则每个输出图像的形状将为 `[N, height – (Y – 1), width – (X – 1), num_filters]`。

### Creating pooling layers

卷积层为每个过滤器生成一个输出图像，因此具有许多过滤器的 CNN 会生成许多图像。这些图像需要大量内存，因此开发人员通过在卷积层后跟随 *pooling layers* 来减小图像的大小。

池化层将图像的像素细分为矩形块并用单个像素替换每个块。[Figure 8-5](#13_9788126592555-ch08.xhtml#c08-fig-0005) 显示了此过程的工作方式。池化操作将 9-x-8 矩阵划分为 3-x-2 块并用单个值替换每个块。

![FIGURE 8-5: A pooling layer accepts an input image, splits it into blocks, operates on each block, and returns a condensed image.](images/9788126592555-fg0805.png)

[FIGURE 8-5:](#13_9788126592555-ch08.xhtml#rc08-fig-0005) 池化层接受输入图像，将其拆分为块，对每个块进行操作，并返回一个压缩的图像。

[Figure 8-5](#13_9788126592555-ch08.xhtml#c08-fig-0005) 描述了两种池化方法。第一种方法找到输入块中的最大值并将其存储在输出图像中。您可以通过调用 `tf.layers.max_pooling2d` 创建执行此操作的池化层。

第二种池化方法计算输入块中像素的平均值并将该值存储在输出图像中。您可以通过调用 `tf.layers.avg_pooling2d` 创建使用此方法的池化层。

在 `tf.layers` 包提供的池化函数中，`max_pooling2d` 是最受欢迎的。这种受欢迎是有道理的，因为较高的最大值清楚地表明了过滤器特征在图像中的存在。[Table 8-2](#13_9788126592555-ch08.xhtml#c08-tbl-0002) 列出了 `tf.layers.max_pooling2d` 的参数并提供了每个参数的描述。

[TABLE 8-2](#13_9788126592555-ch08.xhtml#rc08-tbl-0002) `tf.layers.max_pooling2d` 的参数

| **Parameter** || **Default** || **Description** |
| --- | --- | --- |
| `inputs` || `--` || 输入 4-D 张量 |
| --- | --- | --- |
| `pool_size` || `--` || 用于池化的块的大小 |
| `strides` || `--` || 从一次池化操作到下一次的移动 |
| `padding` || `'valid'` || 填充算法：`valid` 或 `same` |
| `data_format` || `'channels_last'` || 指定输入图像的形状 |
| `name` || `None` || 为层提供名称 |

与 `tf.layers.conv2d` 一样，输入张量的形状取决于 `data_format`。如果 `data_format` 为 `channels_last`，输入张量的形状应为 `[batch_size, height, width, channels]`。如果 `data_format` 为 `channels_first`，输入张量的形状应为 `[batch_size, channels, height, width]`。无论 `data_format` 如何，输入张量中的每个元素都必须是 `tf.float32`。

要设置用于池化的块的高度和宽度，您需要将 `pool_size` 分配给两个整数的列表或元组。对于 [Figure 8-5](#13_9788126592555-ch08.xhtml#c08-fig-0005) 中说明的池化，应用程序将 `pool_size` 设置为 `[3, 2]`。

`strides` 标识块从一次池化操作到下一次池化操作移动的像素数。如果水平移动等于垂直移动，您可以将 `strides` 设置为一个整数。如果不是，您可以将 `strides` 设置为两个整数的元组或列表，其中第一个设置垂直移动，第二个设置水平移动。对于 [Figure 8-5](#13_9788126592555-ch08.xhtml#c08-fig-0005) 中说明的池化，应用程序将 `strides` 设置为 `2`。

如果池化操作涉及图像边界附近的点，计算将取决于 `padding` 参数。如果将 `padding` 设置为 `valid`，池化将不考虑边界像素。如果将 `padding` 设置为 `same`，函数将在池化其值之前用零填充图像。

## Putting Theory into Practice

一旦您理解了卷积、卷积层和池化层，您就可以准备好检查一些代码了。本节介绍一个对图像进行分类的应用程序。但与对 MNIST 数据集的图像进行分类不同，该应用程序对名为 CIFAR-10 的数据集中的图像进行分类。

### Processing CIFAR images

为了测试实用的图像识别应用程序，加拿大高级研究所（CIFAR）提供了 CIFAR-10 和 CIFAR-100 数据集。与 MNIST 数据集一样，这些数据集包含图像及其分类标签。与 MNIST 图像不同，CIFAR 图像为彩色且大小等于 32-x-32 像素。此讨论解释了如何获取 CIFAR-10 数据集并在 TensorFlow 应用程序中访问其内容。

#### The CIFAR-10 dataset

