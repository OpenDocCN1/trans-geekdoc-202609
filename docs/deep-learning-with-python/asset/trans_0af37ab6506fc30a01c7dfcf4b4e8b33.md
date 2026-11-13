

首先，你需要创建一个 Kaggle API 密钥并将其下载到本地机器。只需在网络浏览器中打开 Kaggle 网站，登录，然后进入 My Account 页面。在账户设置中，你会找到 API 部分。点击“创建新的 API 令牌”按钮将生成一个 kaggle.json 密钥文件并将其下载到你的机器上。

其次，进入你的 Colab 笔记本，在笔记本单元格中运行以下代码，将 API 的密钥 JSON 文件上传到你的 Colab 会话中：

```
from google.colab import files
files.upload()
```

运行此单元格时，你会看到出现一个“选择文件”按钮。点击它并选择你刚才下载的 kaggle.json 文件。这会将文件上传到本地 Colab 运行时。

最后，创建一个 ~/.kaggle 文件夹（mkdir ~/.kaggle），并将密钥文件复制到其中（cp kaggle.json ~/.kaggle/）。作为安全最佳实践，你还应确保该文件仅对当前用户（即你自己）可读（chmod 600）：

```
!mkdir ~/.kaggle
!cp kaggle.json ~/.kaggle/
!chmod 600 ~/.kaggle/kaggle.json
```

现在你可以下载我们即将使用的数据：

```
!kaggle competitions download -c dogs-vs-cats
```

初次尝试下载数据时，你可能会遇到“403 Forbidden”错误。这是因为在下载数据集之前，你需要接受与该数据集相关的条款——你需要在登录 Kaggle 账户的情况下访问 www.kaggle.com/c/dogs-vs-cats/rules，并点击“我理解并接受”按钮。你只需执行此操作一次。

最后，训练数据是一个名为 train.zip 的压缩文件。确保你以静默模式（-qq）解压缩它（unzip）：

```
!unzip -qq train.zip
```

我们数据集中的图片是中分辨率彩色 JPEG 图片。图 8.8 展示了一些示例。

![](img/ab452ecf572a1f1372915be13bd8088f_238_0.png)

图 8.8 猫狗数据集的样本。未修改尺寸：样本的大小、颜色、背景等各不相同。

毫不奇怪，早在 2013 年的原始猫狗大战 Kaggle 竞赛中，使用卷积网络的参赛者获胜。最佳参赛作品的准确率高达 95%。在本示例中，我们将接近这一准确率（将在下一节介绍），尽管我们将在竞赛者可用数据的不到 10% 上训练模型。

该数据集包含 25,000 张猫和狗的图片（每类 12,500 张），大小为 543 MB（压缩后）。下载并解压数据后，我们将创建一个包含三个子集的新数据集：一个训练集，每类 1,000 个样本，

![](img/ab452ecf572a1f1372915be13bd8088f_238_0.png)

一个验证集，每类 500 个样本，以及一个测试集，每类 1,000 个样本。为什么要这样做？因为你在职业生涯中遇到的许多图像数据集只包含几千个样本，而不是成千上万个。拥有更多数据会使问题更容易，因此在小型数据集上学习是良好的实践。

我们将使用的子采样数据集将具有以下目录结构：

```
cats_vs_dogs_small/
...train/
...cat/ ... Contains 1,000 cat images
...dog/ ... Contains 1,000 dog images
...validation/
...cat/ ... Contains 500 cat images
...dog/ ... Contains 500 dog images
...test/
...cat/ ... Contains 1,000 cat images
...dog/ ... Contains 1,000 dog images
```

让我们通过几次 shutil 调用来实现它。

### 列表 8.6 将图像复制到训练、验证和测试目录

```
import os, shutil, pathlib
original_dir = pathlib.Path("train")
new_base_dir = pathlib.Path("cats_vs_dogs_small")

def make_subset(subset_name, start_index, end_index):
    for category in ("cat", "dog"):
        dir = new_base_dir / subset_name / category
        os.makedirs(dir)
        fnames = [f"{category}.{i}.jpg"
                  for i in range(start_index, end_index)]
        for fname in fnames:
            shutil.copyfile(src=original_dir / fname,
                            dst=dir / fname)

make_subset("train", start_index=0, end_index=1000)
make_subset("validation", start_index=1000, end_index=1500)
make_subset("test", start_index=1500, end_index=2500)
```

使用每个类别的前 1,000 张图像创建训练子集。

使用每个类别的接下来的 500 张图像创建验证子集。

使用每个类别的接下来的 1,000 张图像创建测试子集。

用于从索引 start_index 复制猫（和狗）图像到索引 end_index 的实用函数，目标子目录为 new_base_dir/{subset_name}/cat（和 /dog）。"subset_name" 将是 "train"、"validation" 或 "test" 之一。

我们现在有 2,000 张训练图像、1,000 张验证图像和 2,000 张测试图像。每个划分包含每个类别相同数量的样本：这是一个平衡的二分类问题，这意味着分类准确率将是衡量成功的适当指标。

## 8.2.3 构建模型

我们将重用第一个示例中看到的相同一般模型结构：卷积网络将是交替的 Conv2D（带 relu 激活）和 MaxPooling2D 层的堆叠。

但是，由于我们处理的是更大的图像和更复杂的问题，我们将相应地增大模型：它将包含两个额外的 Conv2D 和 MaxPooling2D 阶段。这样做既能增加模型容量，又能进一步减小特征图的大小，使其在到达 Flatten 层时不会过大。在这里，由于我们从 180 像素 x 180 像素的输入开始（这是一个有些任意的选择），我们最终会在 Flatten 层之前得到大小为 7 x 7 的特征图。

**注意** 模型中特征图的深度会逐渐增加（从 32 到 256），而特征图的大小会减小（从 180 x 180 到 7 x 7）。这是你在几乎所有卷积网络中都会看到的模式。

由于我们处理的是二分类问题，我们将使用一个单元（一个大小为 1 的 Dense 层）和 sigmoid 激活来结束模型。该单元将对模型正在查看哪个类别的概率进行编码。

最后一个小区别是：我们将以一个 Rescaling 层开始模型，该层将图像输入（其值原本在 [0, 255] 范围内）重新缩放到 [0, 1] 范围。

### 列表 8.7 实例化用于猫狗分类的小型卷积网络

```
from tensorflow import keras
from tensorflow.keras import layers

inputs = keras.Input(shape=(180, 180, 3))
x = layers.Rescaling(1./255)(inputs)
x = layers.Conv2D(filters=32, kernel_size=3, activation="relu")(x)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=64, kernel_size=3, activation="relu")(x)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=128, kernel_size=3, activation="relu")(x)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=256, kernel_size=3, activation="relu")(x)
x = layers.MaxPooling2D(pool_size=2)(x)
x = layers.Conv2D(filters=256, kernel_size=3, activation="relu")(x)
x = layers.Flatten()(x)
outputs = layers.Dense(1, activation="sigmoid")(x)
model = keras.Model(inputs=inputs, outputs=outputs)
```

通过将输入除以 255，将其重新缩放到 [0, 1] 范围。

让我们看看特征图的尺寸如何随每个连续层的变化：

>>> model.summary()
Model: "model_2"

| Layer (type) | Output Shape | Param # |
|---|---|---|
| input_3 (InputLayer) | [(None, 180, 180, 3)] | 0 |
| rescaling (Rescaling) | (None, 180, 180, 3) | 0 |
| conv2d_6 (Conv2D) | (None, 178, 178, 32) | 896 |
| max_pooling2d_2 (MaxPooling2D) | (None, 89, 89, 32) | 0 |
| conv2d_7 (Conv2D) | (None, 87, 87, 64) | 18496 |
| max_pooling2d_3 (MaxPooling2D) | (None, 43, 43, 64) | 0 |
| conv2d_8 (Conv2D) | (None, 41, 41, 128) | 73856 |
| max_pooling2d_4 (MaxPooling2D) | (None, 20, 20, 128) | 0 |
| conv2d_9 (Conv2D) | (None, 18, 18, 256) | 295168 |
| max_pooling2d_5 (MaxPooling2D) | (None, 9, 9, 256) | 0 |
| conv2d_10 (Conv2D) | (None, 7, 7, 256) | 590080 |
| flatten_2 (Flatten) | (None, 12544) | 0 |
| dense_2 (Dense) | (None, 1) | 12545 |

Total params: 991,041
Trainable params: 991,041
Non-trainable params: 0

