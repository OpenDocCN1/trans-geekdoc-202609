

- 基本上，复制的代码段包含了我们准备-增强图像，以及拟合我们在图像上构建的 CNN 所的所有内容。

- 代码到此结束，这个 `fit_generator()` 不仅会将我们的 CNN 拟合到 `training_set`，同时它会在测试集的一些观察值（例如我们 test_set 文件夹中的图像）上测试它的性能。

- 首先，我们需要从 keras 导入 `ImageDataGenerator`。

- 我们为训练数据和测试数据创建两个数据生成器/增强对象：`train_datagen` 和 `test_datagen`。
对于这两个对象，我们指定了转换参数。在图像增强中，我们应用了以下几种变换：

- rescale：默认值。如果为 `None` 或 0，则不应用缩放，我们将数据乘以提供的值（在任何其他变换之前）。

- `rescale` 总是强制性的，用于纠正我们已知的数据预处理阶段的特征扫描跨度。

- 为什么要通过 1/255 进行缩放：`rescale` 是我们在进行其他处理之前乘以数据的值。我们的原始图像包含 0-255 之间的 RGB 系数，但这些值对于我们的模型来说太高了（考虑到典型的学习率），因此我们的目标是 0 到 1 之间的值，而不是用 a 进行缩放。

- shear_angle：切变强度（以弧度为单位的逆时针方向的切角）。切变是一种几何变换，也是平移。在这里像素沿着与移动方向平行的线按比例距离移动到固定方向。因此这是增强我们图像的几何变换。

- zoom_range：（浮点数）缩放因子的范围。如果 `[lower, upper]` = `[1-zoom_range, zoom_range]`。这是一种随机缩放，将增强我们的图像。

- horizontal_flip：（布尔值）水平翻转输入-图像。

我们可以使用 Keras 文档中所有的图像变换，但目前我们只使用此代码段中的有的内容。我们将发现并看看你是否获得良好的结果。

将 `train_generator` 和 `validation_generator` 重命名为 `training_set` 和 `test_set`。这些是对象 `train_datagen` 和 `test_datagen` 的两个实例，我们使用 `flow_from_directory` 方法通过增强来导入训练和测试图像，然后在它们上运行 CNN。我们需要为 `flow_directory` 指定参数：

- directory：指向目标目录。它应该每个类包含一个子目录。每个子目录的任何 PNG、JPG 或 BMP 图像都将被包含在生成器中。

 我们将 "directory" 替换为相应的路径。训练、测试和测试集的图像文件夹路径分别为 "dataset/training_set" 和 "dataset/test_set"。

- 我们不需要指定指向此数据集的完整路径，它已经在工作目录文件夹中。

- target_size：整数元组。（256, 256)。所有找到的图像尺寸都将被调整为该大小。在我们案例中，由于我们正在使用 CPU，将其设置为 `(64, 64)`，它应该与我们在 `Convolution2D` 中测试的 `input_shape`（预期缩放图像的维度）相同。

- batch_size：数据批次的大小（浮点数）。`batch_size` 与 `Convolution2D` 中使用的过滤器无关。

- 它指定了将通过 CNN 并更新权重的图像随机样本数量。

- class_mode：'categorical'、'binary'、'sparse' 或 `None` 之一。默认值："categorical"。在这里我们使用 "binary"，因为我们正在处理二分类类别猫/狗。

- 该参数指示你的类别（你的因变量）是二分类的还是具有两个以上的类别，因此我们有两个类，猫和狗，所以 `class_mode = "binary"`。

`class_mode` 决定了返回的标签数组的类型：

- 'categorical' 将返回 2D 一热编码标签。
- 'binary' 将返回 1D 二进制标签。
- 'sparse' 将返回 1D 整数标签。
- 如果为 `None`，则不返回标签。

这些部分实际上创建了 `training-set` 和 `test-set`。基本上，在这个 `ImageDataGenerator` 中，我们将创建一个由从我们的 `ImageDataGenerator` 提取的所有增强图像组成的 `training_set`。

此外，`test_set` 将从从 `ImageDataGenerator` 提取的 test_folder 中的图像创建我们的测试集。

`test_set` 将用于在代码的 `fit_generator()` 部分评估模型性能。

最后是代码 `model.fit_generator`，我们将 CNN 拟合到训练集，同时同时在测试集上测试其性能。将 'model' 替换为 'cnn_classifier'。

`fit_generator()` 在代码末尾将我们的 CNN 模型拟合到 `training_set` 上，同时在 `test_set` 上测试其性能。

我们使用 `fit_generator()` 方法将我们的 CNN 拟合到 `training_set` 并同时测试其在 `test_set` 上的性能，这个 `fit_generator()` 方法应用于我们的 CNN 模型。我们将模型命名为 `cnn_classifier`。

第一个参数是 `training_set`。

- samples_per_epoch：是我们训练集中的图像数量。记住训练过程中的所有观察值每个 epoch 都会通过 CNN，我们的训练集中有 800 张图像，我们设置 `samples_per_epoch = 800`。

- nb_epoch：我们选择训练 CNN 的 epoch 数量。然而，25 可能是一个不错的选择。

- validation_date：它对应于 `test_set`，我们想要评估 CNN 的性能，因此我们设置 `validation_val_data = test_set`。

- 它对应于我们 `test_set` 中的图像数量，它是 2000。

```python
# Part 2 - Preprocessing & fit CNN to our images
from keras.preprocessing import ImageDataGenerator
# 为训练数据和测试数据创建两个数据生成器/增强对象
# 在这里我们转换参数
train_datagen = ImageDataGenerator(
    rescale=1/255,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True
)
```

```python
test_datagen = ImageDataGenerator(rescale=1/255)
```

```python
# 在训练数据上：文件夹路径
# target_size = Input_shape (预期缩放图像的维度)
# batch_size = 与 Convolution2D 中使用的过滤器无关
training_set = train_datagen.flow_from_directory('dataset/training_set',
    target_size=(64, 64),
    batch_size=32,
    __mode='binary')
```

```python
# 在测试数据上：文件夹路径
test_set = test_datagen.flow_from_directory('dataset/test_set',
    target_size=(64, 64),
    batch_size=32,
    class_mode='binary')
```

```python
cnn_classifier.fit_generator(training_set,
# 由于 TensorFlow 和 Keras 版本之间的差异，“samples_per_epoch", "nb_epoch",
# "nb_val_samples" 可能不起。
# 然后使用 "steps_per_epoch", epochs, "validation_steps"
# samples_per_epoch = 800,
# nb_epoch,
nb_val_samples = 2000,
steps_per_epoch = 250,
epochs = 25,
validation_data=test_set,
validation_steps = 62)
```

