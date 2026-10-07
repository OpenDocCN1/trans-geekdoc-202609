

## 机器学习第 6 章：使用 Keras 控制训练

但请记住，此时的预测仍然完全是随机的。尽管如此，在训练之前运行 `model.predict()` 仍然很有用，可以确保你的模型预测结果符合预期——在这种情况下，类似于每个类的平均概率。如果模型在此处返回了其他内容（例如全零），说明模型出了问题——你不想浪费时间去训练一个根本上就有错误的模型。

## 使用生成器

你已经见过如何将图像加载到张量以及如何在 notebook 中绘制它。这对于验证训练数据是否正确非常有帮助。在训练期间，你不需要手动加载图像。Keras 有一个名为 `ImageDataGenerator` 的辅助类，它可以从文件夹自动加载图像。

```
from keras.preprocessing.image import ImageDataGenerator
datagen = ImageDataGenerator(
    preprocessing_normalize_pixels)
```

数据生成器将 `normalize_pixels` 函数作为其预处理函数，因此它在加载图像时会自动归一化。数据生成器还可以执行其他操作，你将在下一节讨论数据增强时看到。使用这个 `ImageDataGenerator`，你可以创建另外三个生成器，每个生成器对应一个图像子集：

```
batch_size = 64
train_generator = datagen.flow_from_directory(
    train_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=True)

val_generator = datagen.flow_from_directory(
    val_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)

test_generator = datagen.flow_from_directory(
    test_data_dir,
    target_size=(image_width, image_height),
    batch_size=batch_size,
    class_mode="categorical",
    shuffle=False)
```

## 机器学习
# 第 6 章：使用 Keras 控制训练

`train_generator` 用于 train 文件夹中的图像，`val_generator` 用于 val 文件夹中的图像，而 `test_generator` 用于 test 文件夹中的图像。

Python 中的生成器是一个可以产生其他对象的对象。在这种情况下，你正在创建一个可以通过从给定文件夹加载图像来生成图像的生成器。之所以需要使用生成器是因为你不可能一次性将所有图像加载到内存中，因为这将需要许多 GB 甚至 TB 的内存——处理此类数据的唯一方法是按需加载图像。这正是 Keras 生成器允许你做到的。

这三个生成器执行相同的操作——从它们各自的文件夹加载图像——但 `train_generator` 设置了 `shuffle=True`，而其他两个的 `shuffle=False`。在训练期间，你希望随机选取图像，这样模型就不会尝试学习图像的顺序。然而，在测试期间，你希望以固定的顺序选取图像，这样更容易匹配到正确的顺序。

`class_mode="categorical"` 参数告诉 Keras 每个图像都有一个子文件夹。Keras 将使用子文件夹的名称作为该文件夹图像的类别标签。批大小（batch size）为 64，因此生成器将尝试一次加载 64 张图像。当你运行上述代码时，Jupyter notebook 显示：

```
Found 4838 images belonging to 20 classes.
Found 955 images belonging to 20 classes.
Found 952 images belonging to 20 classes.
```

这些分别是训练、验证和测试图像的数量。要查看生成器的输出内容，你可以对它调用 `next()`：

```
x, y = next(train_generator)
print(x.shape)
print(y.shape)
```

在训练期间你永远不需要调用 `next()`，但了解你的生成器正在正常工作是有用的。它获取下一批图像及其对应的标签 `y`。张量 `x` 的形状为 `(64, 32, 3)`，因为它包含了 64 张 32 像素的 RGB 图像。由于你每次训练 64 张图像，因此该批次（batch）也包含了这些图像的标签。回想一下这些标签（也称为真值，ground-truths）用于计算损失或模型预测有多大“错”。

![](img/5720be5c3cca252e1244e68d25607b5_223_png)

## 机器学习第 6 章：使用 Keras 控制训练

因为模型产生 20 个输出值——每个类一个概率——所以给定图像的真值标签需要 20 个值。这就是为什么张量的形状是 `(64, 20)`。看看这些标签中的第一个 `y[0]`：

```
array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 0., 1., 0., 0., 0., 0., 1], dtype=float32)
```

（注：你可能期望看到如 'apple' 或 'cake' 的标签，但你得到的是一个向量。当你这样做时，你得到的标签可能与打印出的不同，因为训练是随机洗乱的。无论你得到什么标签，它都应该由 19 个零和一个单独的1 组成。这被称为独热编码（one-hot encoding）。1 的位置对应类别名称。在这种情况下，1 是第 15 个位置，属于 pineapple。你可以通过执行以下单元格看到这一点：

```
train_generator.class_indices
```

输出：

```
'apple': 0,
'banana': 1,
'cake': 2,
'carrot': 3,
'cookie': 4,
'doughnut': 5,
'grape': 6,
'hot dog': 7,
'ice cream': 8,
'juice': 9,
'muffin': 10,
'orange': 12,
'pineapple': 13,
'popcorn': 14,
'pretzel': 15,
'salad': 16,
'strawberry': 17,
'waffle': 18,
'watermelon': 19
```

要打印 `y[0]` 的标签名称，你可以这样做：

```
index2class = {v:k for k,v in train_generator.class_indices.items()}
```

![](img/5720be5c3cca252e1244e68d25607b5_224_png)

## 机器学习第 6 章：使用 Keras 控制训练

这是一个 Python 字典推导式。它获取 `class_indices` 字典中所有的键值对，并创建一个翻转了键值顺序的新字典。你可以通过独热编码向量中元素 1 的索引来查找类别名称。要找到类别名称，你使用 `np.argmax(y)` 找到 1 的索引，然后在新字典中查找：

```
index2class[np.argmax(y)] 将打印 'pineapple'。
```

对于书中的 `y[]`，为什么这么麻烦？大多数机器学习算法只能处理数字，不能处理字符串。文本标签 'pineapple' 对逻辑回归没有任何意义。因此，你首先将此字符串转换为数值；独热编码向量可以区分类别，因为每个类都有自己的独热编码向量：

| 'apple' | [1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0] |
| 'banana' | [0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0] |
| 'cake' | [0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0,0] |
| 'candy' | [0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,0,0] |
| 'waffle' | [0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,0,1] |
| 'watermelon' | [0,0,0,0,0,1,0,0,0,0,0,0,0,0,0,0,1] |

