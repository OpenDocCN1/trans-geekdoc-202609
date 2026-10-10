
- 模型定义可以从 `https://github.com/tensorflow/tensorflow/tree/r1.4/tensorflow/python/keras/impl/keras/applications` 获取。模型中的每一层都已定义，并提供了在 ImageNet 数据集上的预训练权重。

## SqueezeNet 模型

SqueezeNet 模型由 Iandola 等人（`https://arxiv.org/pdf/1602.07360.pdf`）引入，旨在减小模型尺寸和参数数量。

## 图像分类

通过将 3 x 3 过滤器替换为 1 x 1 过滤器，网络变得更小，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_78_0.png)

3 x 3 过滤器的输入数量也减少了，下采样发生在更高层级，提供了较大的激活图：

![](img/48c861eac4dc634fbf2a09fdbe884beb_78_1.png)

### 空间变换网络 (Spatial transformer networks)

Jaderberg 等人（`https://arxiv.org/pdf/1506.02025.pdf`）提出的空间变换网络尝试对传递给 CNN 的图像进行变换。这与其他网络不同，因为它尝试在卷积之前修改图像。该网络学习变换图像的参数。这些参数是针对仿变换学习的。通过应用仿变换，实现了空间不变性。在之前的网络中，空间不变性是通过最大池化层实现的。空间变换网络的位置如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_79_0.png)

### DenseNet 模型

DenseNet 是 Huang 等人（`https://arxiv.org/pdf/1608.06993.pdf`）提出的 ResNet 扩展。在 ResNet 块中，前层通过求和合并到后续层。在 DenseNet 中，前层通过拼接合并到后续层。DenseNet 将所有层与前几层连接，并将当前层与后续层连接。

在接下来的图中，可以看到特征图是如何作为输入提供其他层的：

![](img/48c861eac4dc634fbf2a09fdbe884beb_80_0.png)

通过这种方式，它提供了许多优势，例如更平滑的梯度、特征变换等。这还减少了参数数量：

| 输入 | Dense Block 1 | | Dense Block 2 | | Dense Block 3 | | 预测 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| ![horse] | 卷积 | 池化 | 卷积 | 池化 | 卷积 | 池化 | 线性 | "horse" |

我们已经涵盖了图像分类任务的所有最新算法。任何架构都可以用于图像分类任务。在下一节中，我们将看到如何使用这些先进架构训练一个模型来预测宠物并提高准确率。

### 训练一个猫狗分类模型

在本节中，我们将准备准备并训练一个用于预测猫狗分类的模型，并理解一些提高准确率的技术。大多数图像分类问题都属于这种范式。本节涵盖的技术（如数据增强和迁移学习）对许多问题都有用。

## 准备数据

为了进行分类，我们将从 kaggle 下载数据并以适当的格式存储。在 `www.kaggle.com` 注册并登录，访问 `https://www.kaggle.com/dogs-vs-cats/data`。从该页面下载 `train.zip` 和 `test1.zip` 文件。`train.zip` 包含 25000 张宠物数据图像。我们将只使用部分数据来训练模型。具有更强计算能力（如图形处理器单元 GPU）的读者可以使用比建议的更多数据。运行以下脚本来重新排列图像并创建必要的文件夹：

```python
import os
import shutil

work_dir = ' ' # 给你的正确目录
image_names = sorted(os.listdir(os.path.join(work_dir, 'train')))

def copy_files(prefix_str, range_start, range_end, target_dir):
    image_paths = [os.path.join(work_dir, 'train', prefix_str + '.' + str(i) + '.jpg')
    for i in range(range_start, range_end)]
    dest_dir = os.path.join(work_dir, 'data', target_dir, prefix_str)
    os.makedirs(dest_dir)
    for image_path in image_paths:
        shutil.copy(image_path, dest_dir)

copy_files('dog', 0, 1000, 'train')
copy_files('cat', 0, 1000, 'train')
copy_files('dog', 1000, 1400, 'test')
copy_files('cat', 1000, 1400, 'test')
```

## 图像分类

## 第2 章

对于我们的实验，我们只使用 1000 张猫的图像。因此，将下载文件夹中的 0–999 复制到新创建的 train 文件夹下。同样，将 1000–1400 复制到 data/test/cat，10–999 复制到 train/dogs，1000–1400 复制到 data/test/dog，这样我们每个类都有 1000 个训练示例和 400 个验证示例。

## 使用 simple_cnn 进行基准测试

通过将 3 x 3 过滤器替换为 1 x 1 过滤器，网络变得更小，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_78_0.png)

3 x 3 过滤器的输入数量也减少了高层的下采样，提供了较大的激活图：

![](img/48c861eac4dc634fbf2a09fdbe884beb_78_1.png)

对于我们的实验，我们只使用 1000 张猫的图像。因此，将下载文件夹中的 0–999 复制到新创建的 train 文件夹下。同样，将 1000–1400 复制到 data/test/cat，10–999 复制到 train/dogs，1000–1400 复制到 data/test/dog，这样我们每个类都有 1000 个训练示例和 400 个验证示例。

### 增强技术

有多种增强图像的方法，如下所示：

- **翻转 (Flipping)**：在水平或垂直方向上进行镜像或翻转

- **随机裁剪 (Random Cropping)**：随机裁剪部分，因此模型可以处理遮挡问题

- **剪切 (Shearing)**：对图像进行变形以影响对象的形状

- **缩放 (Zooming)**：对图像的缩放部分进行训练，以处理不同比例的图像

- **旋转 (Rotation)**：旋转物体以处理物体在不同角度的变化

- **白化 (Whitening)**：通过主成分分析（PCA）进行白化，只保留重要数据

- **归一化 (Normalization)**：通过标准化均值和方差对像素进行归一化

- **通道偏移 (Channel shifting)**：移动颜色通道以使模型对各种伪影引起的颜色变化具有鲁棒性

所有这些技术都在 `ImageDataGenerator` 中实现以增加数据集的大小。以下是之前讨论过的某些增强技术的 `generator_train` 修改版本：

```python
generator_train = tf.keras.preprocessing.image.ImageDataGenerator(
    rescale=1. / 255,
    horizontal_flip=True,
    zoom_range=0.3,
    shear_range=0.3,)
```

替换前代码中的 `generator_train` 将准确率提高到 90%。更改增强参数并观察变化。我们将在下一节中讨论一种名为**迁移学习 (transfer learning)**的技术，它有助于用更少的数据训练更大的模型。

### 模型的迁移学习或微调

迁移学习是从在更大数据集上训练的预训练模型中学习的过程。使用随机初始化训练模型需要一些时间和精力的才能获得结果。使用预训练模型初始化模型可以获得更快的收敛，节省时间和精力。这些预训练模型通常是经过仔细调优超参数训练的。

## 图像分类

## 第 2 章

可以直接不修改地使用预训练模型的几层，也可以对其进行训练以适应变化。在本节中，我们将学习如何对在 ImageNet 数据集（包含数百万类）上训练的模型进行微调或迁移学习。

### 在瓶颈特征 (bottleneck features) 上训练

前几节涵盖的模型非常简单，因此准确率可能较低。应该从它们构建更复杂的模型。它们不能从零开始。因此，提取瓶颈特征并在其上训练分类器。瓶颈特征是复杂架构在训练数百万张图像时产生的特征。对图像进行前向传播并存储倒数第二层的特征。基于这些特征，训练一个简单的逻辑回归分类器进行分类。提取瓶颈特征的方法如下：

```python
generator = tf.keras.preprocessing.image.ImageDataGenerator(rescale=1 / 255)

model = tf.keras.applications.VGG16(include_top=False)

train_images = generator.flow_from_directory(
    train_dir,
    batch_size=batch_size,
    target_size=(image_width, image_height),
    class_mode=None,
    shuffle=False
)
train_bottleneck_features = model.predict_generator(train_images, epoch_steps)

test_images = generator.flow_from_directory(
    test_dir,
    batch_size=batch_size,
    target_size=(image_width, image_height),
    class_mode=None,
    shuffle=False
)
test_bottleneck_features = model.predict_generator(test_images, test_steps)
```

## 图像分类

## 第 2 章

采用 VGG 模型来预测图像。标签分配如下所示：

```python
train_labels = np.array([0] * int(no_train / 2) + [1] * int(no_train / 2))
test_labels = np.array([0] * int(no_test / 2) + [1] * int(no_test / 2))
```

使用提供的代码可以实现一个带有几层的顺序模型（Sequential model），并在瓶颈特征上编译和训练：

```python
model = tf.keras.models.Sequential()
model.add(tf.keras.layers.Flatten(input_shape=train_bottleneck_features.shape[1:]))
model.add(tf.keras.layers.Dense(1024, activation='relu'))
model.add(tf.keras.layers.Dropout(0.3))
model.add(tf.keras.layers.Dense(1, activation='softmax'))
model.compile(loss=tf.keras.losses.categorical_crossentropy,
    optimizer=tf.keras.optimizers.Adam(),
    metrics=['accuracy'])
```

使用如下所示的代码用模型训练这些瓶颈特征：

```python
model.fit(
  train_bottleneck_features,
  train_labels,
  batch_size=batch_size,
  epochs=epochs,
  validation_data=(test_bottleneck_features, test_labels))
```

这提供了一种训练模型的不同方法，在训练数据较少时非常有用。这通常是训练模型的更快方法。只使用预训练模型的最终激活值来适应新任务。这种思想可以扩展到微调几层，如下所示：

### 深度学习中的层微调

可以加载预训练模型并只训练几层。当给定的问题与模型训练时的图像差异很大时，这种方法效果更好。微调是深度学习中的常见做法。这在……具有优势。

### 选择合适的模型

架构有很多种选择。根据部署的灵活性，你可以选择模型。请记住，卷积层更小且运行速度较慢，而全连接层（dense layers）更大且速度更快。在尺寸、运行时间和准确性之间存在权衡。建议在最终决定之前测试所有架构。根据应用，某些模型的效果比其他模型更好。你可以减小输入尺寸来加快推理。可以根据下一节描述的指标来选择架构。

### 解决欠拟合和过拟合场景

模型对于某些问题来说有时太大或太小。这可以分别归类为欠拟合或过拟合。欠拟合发生在模型太小的情况下，可以通过训练准确率低来衡量。过拟合发生在模型太大的情况下，训练准确率和测试准确率之间存在巨大差距。可以通过以下方法解决欠拟合：

- 获取更多数据

- 尝试更大的模型

- 如果数据较少，使用迁移学习技术或进行数据增强

可以通过以下方法解决过拟合：

- 使用 dropout 和批归一化（batch normalization）等技术进行正则化

- 增强数据集

始终关注损失值（loss）。损失值应该随着迭代的增加而减少。如果损失值不再下降，表明训练已经停止。解决方案之一是尝试不同的优化器。可以通过加权损失函数来处理类别不平衡。始终使用 TensorBoard 查看摘要（summaries）。很难估计需要多少数据。本节是训练任何深度学习模型的最佳教程。接下来，我们将介绍某些特定应用的指导。

### 面部性别和年龄检测

应用可能需要从人脸进行性别和年龄检测。可以通过人脸检测器获取脸部图像。裁剪后的脸可以作为训练数据提供，推理时也提供类似的裁剪脸。根据所需的推理时间，可以选择 OpenCV 或 CNN 人脸检测器。在训练时，可以使用 Inception 或 ResNet。如果是因为视频导致所需推理时间较短，最好使用三个卷积层后接两个全连接层。注意，年龄数据集中通常存在巨大的类别不平衡，因此使用精确率（precision）和召回率（recall）等不同指标会有帮助。

### 微调模型

对服装模型进行微调是一个很好的选择。在这里，拥有多个分类属性的 softmax 层将很有用。这些属性可以是图案、颜色等。

## 品牌安全

使用支持向量机（SVM）训练瓶颈层是一个很好的选择，因为不同类别之间的图像可能非常不同。这通常用于内容审核，帮助避免显性图像。你已经学习了如何处理图像分类中的新问题。

## 总结

我们涵盖了用于分类任务的基础但实用的模型。我们看到了针对 MNIST 数据集的使用 Keras 和 TensorFlow API 实现的简单模型。我们还看到了如何利用 TensorBoard 监控训练过程。然后，我们讨论了具有某些特定应用的先进架构。还涵盖了增加准确率的几种方法，如数据增强、在瓶颈层上训练以及微调预训练模型。还介绍了为新模型训练模型的技巧和窍门。

在下一章中，我们将看到如何对深度学习模型进行可视化。我们将在本章中部署训练好的模型进行推理。我们还将看到如何将训练好的层用于通过应用程序进行图像搜索。然后，我们将理解自动编码器（autoencoders）的概念并将其用于特征的降维。

# 3 图像检索

深度学习也可以称为表示学习，因为模型中的特征或表示是在训练过程中学习的。在隐藏层训练过程中生成的视觉特征可以用于计算距离度量。这些模型根据分类任务，在不同层上学习如何检测边缘、模式等。在本章中，我们将将点：

- 如何从为分类训练的模型中提取特征

- 如何使用 TensorFlow Serving 在生产系统中实现更快的推理

- 如何使用这些特征计算查询图像与目标集之间的相似性

- 使用分类模型进行排序

- 如何提高检索系统的速度

- 查看整个系统的架构

- 当目标图像过多时，使用自动编码器学习紧凑的描述符

- 训练去噪自动编码器

## 理解视觉特征

深度学习模型经常因缺乏可解释性而受到批评。基于神经网络的模型通常被认为是黑箱，因为人类很难推理出深度学习模型的工作原理。由于激活函数的存在，深度学习模型跨层对图像转换是非线性的，因此无法轻易可视化。目前已经开发了一些方法，通过可视化深度神经网络的层来应对对不可解释性的批评。在本节中，我们将尝试对深层进行可视化，以理解模型是如何运作的。

可以使用模型的激活值（activation）和梯度（gradient）进行可视化。可以使用以下技术可视化激活值：

- **最近邻**：可以获取图像的层激活，并将激活最相似的图像在一起。

- **降维**：可以通过主成分分析（PCA）或 t-分布随机邻域嵌入（t-SNE）减少激活值的维度，以便在二维或三维中可视化。PCA 通过向最大方差方向投影值来减少维度。t-SNE 通过将最近的点映射到三维来减少维度。降维及其技术的使用超本书的范围。建议你参考基础机器学习材料以学习更多关于降维的知识。

Wikipedia 是降维的好来源。以下是一些链接：

- Dimensionality_reduction（降维）
