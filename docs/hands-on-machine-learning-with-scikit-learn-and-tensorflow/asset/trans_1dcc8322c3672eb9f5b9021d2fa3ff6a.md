
就这些了！这将创建一个 ResNet-50 模型并下载在 ImageNet 数据集上预训练的权重。要使用它，你首先需要确保图像的尺寸正确。ResNet-50 模型期望 224 × 224 的图像（其他模型可能期望其他尺寸，例如 299 × 299），因此让我们使用 TensorFlow 的 `tf.image.resize()` 函数来调整我们加载的图像大小：

```python
images_resized = tf.image.resize(images, [224, 224])
```

`tf.image.resize()` 不会保持宽高比。如果这是一个问题，你可以尝试在调整大小之前将图像裁剪到适当的宽高比。这两个操作可以通过 `tf.image.crop_and_resize()` 一次完成。

![](img/0684d2da98e09085c0a622d4fd69aaad_491_0.png)

预训练模型假设图像是以特定方式进行预处理的。在某些情况下，它们可能期望输入被缩放到 0 到 1，或者 -1 到 1 等。每个模型都提供一个 `preprocess_input()` 函数，你可以用它来预处理图像。这些函数假设像素值范围从 0 到 255，因此你必须将其乘以 255（因为我们已经将它们缩到了 0-1）：

```python
inputs = keras.applications.resnet50.preprocess_input(images_resized * 255)
```

现在我们使用预训练模型进行预测：

```python
Y_proba = model.predict(inputs)
```

和往一样，`Y_proba` 是一个矩阵，每张图像一行，每个类别一列（在这种情况下，有 1,000 个类）。如果你想显示前 K 个预测结果，包括每个预测类别的名称和估计概率，你可以使用 `decode_predictions()` 函数。对于每张图像，它返回一个包含 K 个预测的数组，其中每个预测都表示为包含类别标识符¹、名称和相应置信度的数组：

```python
top_K = keras.applications.resnet50.decode_predictions(Y_proba, top=3)
for image_index in range(len(images)):
    print("{}")
    for class_id, name, y_proba in top_K[image_index]:
        print("{0}: {1} ({2:.2f})".format(class_id, name, y_proba * 100))
```

输出结果如下：

- Image #0
- n03878145 palace 42.87%
- n02825657 bell_cote 40.57%
- n038712444 monastery 14.56%

> ¹ 在 ImageNet 数据集中，每张图像都与 WordNet 数据中的一个单词关联：类别 ID 只是一个 WordNet ID。

Image #1 vase

- n04522168 46.83%
- n07930864 cup 7.78%
- n011939491 daisy 4.87%

正确的类别（monastery 和 daisy）都出现在两张图像的前 3 个结果中。考虑到模型必须从 1,000 个类中进行选择，这已经不错了。

如你所见，使用预训练模型创建一个非常好的图像分类器是非常简单的。keras.applications 中提供了其他视觉模型，包括多个 ResNet 变体、GoogLeNet 变体（如 InceptionV3 和 Xception）、VGGNet 变体、MobileNet 和 MobileNetV2（用于移动应用程序的轻量级模型）。

但如果你想针对不是 ImageNet 的类别怎么办？在这种情况下，你仍然可以利用预训练模型进行迁移学习。

# 用于迁移学习的预训练模型

如果你想构建图像分类器但没有足够的训练数据，那么正如我们在第 11 章讨论的，重用预训练模型的低层通常是一个好主意。例如，让我们训练一个模型来分类花，重用一个预训练的 Xception 模型。首先，使用 TensorFlow Datasets 加载数据集（见第 13 章）：tfds

```python
import tensorflow_datasets as tfds
dataset, info = tfds.load("tf_flowers", as_supervised=True, with_info=True)
daset_size = info.splits("train").num_examples # 3670
class_names = info.features["label"].name # ["dandelion", "daisy", ...]
n_classes = info.features["label"].num_classes # 5
```

注意，通过设置 `with_info=True` 可以获取数据集的信息。在这里，我们获取数据集的大小和类别的名称。遗憾的是，只有一个“train”数据集，没有测试集或验证集，因此我们需要划分训练集。TF Datasets 项目为此提供了 API。例如，让我们取数据集的前 10% 用于测试，接下来的 15% 用于验证，剩下的 75% 用于训练：

接下来我们必须预处理图像。CNN 期望 224x224 的图像，因此我们需要调整它们的大小。我们还需要通过 Xception 的 `preprocess_function()` 处理图像：

```python
def preprocess(image):
    resized_image = tf.image.resize(image, [224, 224])
    final_image = keras.applications.xception.preprocess_input(resized_image)
    return final_image
```

我们将此预处理函数应用到所有数据集：

```python
batch_size = 32
train_set = dataset.map(preprocess).shuffle(100).repeat().batch(batch_size).prefetch()
valid_set = valid_set.map(preprocess).batch(batch_size).prefetch()
test_set = test_set.map(preprocess).batch(batch_size).prefetch()
```

如果你想进行一些数据增强，可以使用 `tf.image.random_crop`、`tf.image.random_flip_left_right`、`tf.image.random_flip_up_down`、`tf.image.random_brightness`、`tf.image.random_contrast`、`tf.image.random_saturation` 和 `tf.image.random_hue`。这些应该只在训练期间应用于图像。

```python
def augment(image):
    image = tf.image.random_flip_left_right(image)
    image = tf.image.random_brightness(image, 0.2)
    return image
```

如果你想针对不是 ImageNet 的类别使用图像分类器？在这种情况下，你仍然可以从预训练模型中受益于迁移学习。

# 用于迁移学习的预训练模型

如果你想构建图像分类器但没有足够的训练数据，那么正如我们在第 11 章讨论的，重用预训练模型的低层通常是一个好主意。例如，让我们训练一个模型来分类花，重用一个预训练的 Xception 模型。首先，使用 TensorFlow Datasets 加载数据集（见第 13 章）：tfds

（此处由于原文存在大量重复 OCR 错误，已按要求进行逻辑处理）
