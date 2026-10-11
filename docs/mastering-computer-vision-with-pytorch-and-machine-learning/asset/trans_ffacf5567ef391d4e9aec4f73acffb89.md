

# MNIST 数据集与图像分类项目工具准备

## MNIST 数据集简介

MNIST (Modified National Institute of Standards and Technology) 是计算机视觉领域最著名的数据库 (LeCun *et al* [1998](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib4))，常用作测试机器学习算法的基准。需注意 MNIST 是一个非常简单的数据集，即使只有两个全连接神经层的模型也能达到 98% 的准确率。在 MNIST 上表现良好的模型不代表在其他数据集上也能表现良好。MNIST 常作为开发和测试机器学习模型的起点。

MNIST 数据集包含训练集和测试集，分别拥有 60,000 和 10,000 张黑白图像。所有图像分辨率均为 28 × 28。训练集用于训练模型，测试集用于检查训练好的模型是否存在“过拟合”问题。过拟合会导致模型在训练集上预测准确率高，但在测试集上准确率低。这可能是因为计算机过于强大地记住了训练集中详细的结构（噪声），而这些结构在不同图像中可能各不相同。为避免过拟合，我们甚至将 MNIST 训练集切分为包含 50,000 张图像的较小训练集和包含 10,000 张图像的验证集用于模型训练。

## 项目工具准备：Python 与 PyTorch

正如古埃及人建造金字塔前须备好测量、切割和搬运巨石的工具，我们在项目 [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2ueqn1) 的 MNIST 图像分类代码中也需要准备工具。这些工具是 `Python` 和 `PyTorch` 库。借助它们，我们可以从互联网加载数据集到计算机，将数据集切片为 `DataLoader`，并在屏幕上显示。以下项目的 `Cell 01` 代码提供了这些工具。

在这些工具中，`Torchvision` 对我们来说是新的。`Torchvision` 是 `PyTorch` 的一部分库。该库包含许多用于下载的流行数据集、许多可用的预训练模型，以及许多用于减少过拟合问题的图像变换操作。`Torchvision` 在 `VS Code` 中随 `PyTorch` 安装后一同安装。许多超参数（如 `batch size` 和 `learning rate`）也在 `Cell 01` 中设置。

我们的模型如何被训练以识别 MNIST 图像中的数字？模型并不像人眼那样“阅读”二维图像。在本项目中，模型包含两个全连接层。每张图像的 28 × 28 像素被展平为一个包含 784 个元素的一维张量。该简单模型仅从这些数据中提取统计信息（概率）。凭借这些统计信息，模型的预测准确率将超过 98%。

## 数据集下载与预处理

通过 `Cell 02` 的代码，如果硬盘上的数据路径为空且第 01 行和第 04 行将 MNIST 选项设置为 `download = True`，则可以从互联网下载 MNIST 数据库。从 MNIST 数据集源下载的压缩图像文件总大小约为 116 MB。如果数据库已下载到计算机上，应将下载选项设置为 `False`，随后图像数据将从 `Cell 01` 最后一行设置的文件路径读取。`Cell 01` 最后一行数据路径字符串中的点 (`.`) 代表 `VS Code` 的当前工作目录。可通过在额外单元格运行 `import os; os.getcwd()` 来查找。也可使用绝对数据路径。

当 `train` 选项为 `True` 时，压缩文件内的训练集图像会被加载；若 `train = False`，则加载测试集图像。MNIST 图像中的每个像素均为 8 位整数 (0–255)。通过 `Cell 02` 第 02 行和第 05 行的 `transform` 函数，每张图像的像素值被转换为范围在 `[0.0, 1.0]` 的 `float32` 张量。

![](images/bk978-0-7503-6244-3ch2uf1_pr.gif)

## 数据集切片与 DataLoader 构建

使用 `Cell 03` 的代码，我们利用 `PyTorch` 的 `DataLoader` 类将两个数据集分别切片为两个 `DataLoader`。较小的 `batch size` 意味着更长的模型训练时间，但能获得更好的训练结果。遇到 GPU 内存不足 (out of memory) 问题时，减小 `batch size` 参数是一种解决方案。

为减少模型训练的“过拟合”问题，我们在 `Cell 03` 第一行将 `shuffle` 选项设为 `True`，使训练 `DataLoader` 由从数据集中随机选取的样本构建。测试 `DataLoader` 用于验证训练模型是否过拟合，无需随机打包。从 `Cell 04` 的输出可见，训练 `DataLoader` 的一个批次包含 32 张图像，每张图像有 1 个通道，分辨率为 28 × 28。单通道图像为黑白图像，三通道图像为彩色图像。此外，数据集中每张图像均有一个标签，即照片显示的数字。

可使用 `Cell 04` 后额外单元格中的代码显示测试数据集的最后一张图像：`img, _ = test_dataset[−1]; plt.imshow(img.permute(1,2,0))`。

## 图像批次可视化

`Cell 04` 中定义了名为 `show_images` 的函数。该函数输入为来自 `DataLoader` 的一个批次图像。在 `Cell 03` 的 `for` 循环中，仅挑选第一批图像用于显示。利用 `torchvision.utils` 模块的 `make_grid`，将批次中的所有小图像合并为一张大图像。大图像每行包含的小图像数量由 `Cell 04` 第 03 行的 `nrow` 选项设定。每个小图像周围的间距由参数 `padding` 设定，默认 `padding` 等于 2 像素。

由于 `Cell 02` 中训练 `DataLoader` 设置了 `shuffle = True`，每次运行 `show_images` 函数都会看到不同的大图像（如图 [2.1](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2fig1) 所示）。若使用测试 `DataLoader` 作为输入，则大图像不会改变。

![Figure 2.1. MNIST images in a batch of the train dataloader with a batch size of 32. Reproduced from Deng (2012) CC BY 3.0.](images/bk978-0-7503-6244-3ch2f1_online.jpg)

**Figure 2.1.** MNIST images in a batch of the train dataloader with a batch size of 32. Reproduced from Deng ([2012](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2bib5)) CC BY 3.0.

## 扩展实验：理解 make_grid 与 permute

运行 `Cell 04` 后的两个额外单元格，可进一步了解用于显示图像的 `make_grid` 和 `permute` 操作。

在 `Extra Cell ONE` 中，名为 `my_imgs` 的张量由 0 到 15 的 16 个整数生成。这 16 个整数被打包成形状为 `4 × 1 × 2 × 2` 的张量。可理解为该张量有 4 行 1 列，`4 × 1` 张量的每个元素是一个 `2 × 2` 张量。在计算机视觉术语中，该图像张量包含 4 张图像，每张图像有 1 个通道，分辨率为 2 × 2。

令人惊讶的是，`Extra Cell ONE` 中名为 `big_img` 的大图像拥有相同的 3 个通道，且形状为 `3 × 4 × 4`。若将 `padding` 参数改为 1 或 2，大图像的形状将变为 `3 × 7 × 7` 或 `3 × 10 × 10`。那些额外行和列中每个元素的值均为零。保持 `padding` 为零并将 `nrow` 参数从 1 改为 5，你会看到一些意想不到的现象。

![](images/bk978-0-7503-6244-3ch2uf2_pr.gif)

