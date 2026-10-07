

# 机器学习第 4 章：Python 与 Turi Create 入门

`head()` 函数显示前 10 行：

| path | image |
|---|---|
| snacks/train/healthy/appl/007a0aec009a066.jpg ... | Height: 341 Width: 256 |
| snacks/train/healthy/appl/007e5c6b529e036.jpg ... | Height: 256 Width: 341 |
| snacks/train/healthy/appl/01ec03a12e21e39.jpg ... | Height: 256 Width: 446 |
| snacks/train/healthy/appl/02e1d569c62aa93.jpg ... | Height: 256 Width: 341 |
| [10] 行 x 2 列 | |

SFrame 中的前几行

即使 SFrame 在表格中只显示图像的高度和宽度，但它实际上包含了完整的图像。运行以下命令查看图像：

```
train_data.explore()
```

这会打开一个带有图像缩略图的新窗口（可能需要几秒钟加载）。将鼠标悬停在某行上查看更大版本的图像。

![](img/5720be5c3cca252e12448e68d25607b5_146_0.png)

探索训练图像

这种交互式可视化对于快速查看训练数据非常有用。`explore()` 命令在 Mac 上的 Turi 上有效，不支持 Linux 或 Docker 容器。

输入此命令，使用 Matplotlib 的 `imshow()` 命令直接在笔记本中查看单个图像：

```
plt.imshow(train_data[0]["image"].pixel_data)
```

在这里，`train_data[0]` 获取写入 SFrame 的第一行，`["image"]` 获取该行列中的对象，而 `pixel_data` 将此图像对象转换为 matplotlib 可以通过 `plt.imshow()` 识别的内容。

```
In [6]: plt.imshow(train_data[0]["image"].pixel_data)
Out[6]: matplotlib.AxeImage at 0x1aldcd2f60
```

![](img/5720be5c3cca252e12448e68d25607b5_147_0.png)

### 使用 matplotlib 查看图像

你的笔记本显示的图像可能与插图不同，因为 Turi Create 加载图像的顺序不同。你可以随意更改行索引来查看几张图像（使用 0 到 4,857 之间的任何值）。

在开始训练之前，还有最后一条数据需要收集——每个类的名称。图像存储在以类名命名的子目录中——如“apple”（苹果）、“hot dog”（热狗）等。SFrame 知道加载图像的路径，但这些路径看起来如下：

```
snacks/train/hot dog/8ace0a9a1ed2ff6.jpg
```

对于类别图像 `8ace0a9a1ed2ff6.jpg`，类别是 "hot dog"，但它隐藏在长路径中。为了让这一点而易见，你需要编写一些代码从路径中提取类名。运行以下命令提取第一个类文件夹的名称：

```python
# 获取第一个训练示例的完整路径
path = train_data[0]["path"]
print(path)
```

### 查找类标签
```python
import os
os.basename(os.path.split(path)[0])
```

你正在获取第一张图像的完整路径，然后使用 `os.path` Python 包来处理名称。首先，`os.path.split()` 将路径切分为两部分：文件名（8ace0da8a912ed2f6.jpg）和它之前的所有内容。然后 `os.path.basename()` 获取最后一个文件夹的名称，即包含类名的文件夹。由于第一张训练图像是苹果，你得到的是 `""`

> 注意：`#` 字符在 Python 中开始注释。请注意你需要导入 `os` 包，否则 Python 将无法识别 `os.path` 是什么。

### 获取类标签

好了，现在你知道如何提取单个图像的类名了，但数据集中有 4,800 多图像。作为一名 Swift 程序员，你的初始直觉可能是使用循环，如果你非常习惯 Swift 风格，你会急于于使用 `map` 函数。SFrame 有一个 `apply()` 方法，类似于 Swift 的 `forEach`，允许你对帧中的每一行运行函数：

```python
train_data["path"].apply(lambda path: ...对 path 进行某些操作...)
```

在 Python 中，`lambda` 类似于 Swift 中的闭包（closure）——这是一个没有名的函数。`train_data["path"].apply(lambda)` 对 path 列中的每一行执行此操作。上面的 `lambda` 提供了从路径中提取类名的代码片段：

```python
train_data["Label"] = train_data["path"].apply(lambda path: os.basename(os.path.split(path)[0]))
```

运行单元格，SFrame 将拥有一个新列 "label"。要验证这一点，运行 `train_data.head()`——在新的单元格中执行此操作，或者向上滚动事实并按 Control-Enter。

| path | image | label |
|---|---|---|
| snacks/train/healthy/appl/e07a0e550683b.jpg | Height: 341 Width: 256 | apple |
| snacks/train/healthy/appl/0088165726886.jpg | Height: 256 Width: 384 | apple |

SFrame 现在有一个新列，你也可以使用 `train_data.explore()` 进行视觉检查。运行此命令查看摘要：

```python
train_data["label"].summary()
```

打印关于 SFrame label 的一些统计信息：

| item | value | exact |
|---|---|---|
| Length | 4838 | Yes |
| Missing Values | 0 | Yes |
| unique values | 20 | No |
| value | banana | hot dog | ice cream |
| count | 260 | 250 | 250 |
| value | muffin | salad |
| count | 250 | 250 | - |

### label 列摘要

你可以看到，每个类的元素大致相同。由于某种原因，`summary()` 只显示前 10 个类，但总共有 20 类。查看所有类的行，运行以下命令：

```python
train_data["label"].value_counts().print_rows(20)
```

好了，这就是你目前需要对数据执行的所有。你已经将图像加载到 SFrame，并给了每个标签，所以 Turi 知道它们属于哪个。

### 开始训练

一旦数据进入 SFrame，使用 Turi Create 训练模型只需要一行代码（好了，我们需要适配它）：

```python
model = tc.image_classifier.create(train_data, target="label", model="VisionPrint_Scene", verbose=True, max_iterations=50)
```

或者，如果在你的 Mac 上训练太久，你可以直接从当前文件夹加载 Turi 模型：

```python
model = tc.load_model("HealthySnacks.model")
```

此命令从 train_data 创建一个新的图像分类器。`target` 参数告诉 Turi Create 类名所在的 SFrame 中的列。默认情况下，Turi 只进行 10 次迭代，但将其增加到 50，这样逻辑回归将训练 50 次。

第一次运行时，Turi 会下载一个预训练的神经网络。`model` 参数包含了该神经网络的名称，在这种情况下为 `VisionPrint_Scene`。该模型被 Apple 的 Vision 框架使用，也是 Create ML 的默认模型。

编写时，Turi 支持三种模型架构：另外两个是 ResNet-50 和 SqueezeNet 版本 1.1。ResNet-50 输出一个 90MB 的模型，并不适用于移动设备。SqueezeNet 输出一个 4.7MB 的模型，是一个更好的选择。VisionPrint_Scene 构建在 iOS 12 中，产生一个小得多（（41 KB）。

Turi Create 像 ML 一样对图像进行特征提取。花费的时间与 Create 相似——在我的 MacBook Pro 上花了 22 秒。然后是逻辑回归：

logistic regression:

| Number of examples : 4590 |
| Number of classes : 20 |
| Number of feature columns : 1 |
| Number of unpacked features : 2040 |
| Number of coefficients : 38931 |
| Starting L-BFGS |

| Iteration | Passes | Elapsed Time | Training | Validation Accuracy |
|---|---|---|---|---|
| 5 | 8 | 3.42915 | 0.815468 | 0.850006 |
| 10 | 13 | 5.857664 | 0.884532 | 0.875000 |
| 15 | 18 | 8.315392 | 0.925000 | 0.903126 |
| 20 | 24 | 11.08811 | 0.944227 | 0.895161 |
| 25 | 29 | 13.513964 | 0.982353 | 0.880365 |
| 30 | 34 | 15.985396 | 0.995533 | 0.879502 |
| 35 | 39 | 18.329717 | 0.998911 | 0.875000 |
| 40 | 44 | 20.812458 | 1.000000 | 0.850006 |
| 45 | 49 | 23.216806 | 1.000000 | 0.854639 |
| 50 | 55 | 26.213560 | 1.000000 | 0.866935 |

完成（达到迭代限制）。
这可能不是最优的。要改进它，请考虑增加 `max_iterations'`。

