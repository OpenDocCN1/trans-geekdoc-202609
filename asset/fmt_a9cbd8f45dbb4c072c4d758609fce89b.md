
![](img/image-4dvzdpr6.jpg) 图 11.6 判别器的训练图。

在训练 GAN 期间，每次迭代生成器产生越来越真实的样本，而判别器变得越来越擅长区分它们，如图所示。当判别器无法再次区分真实样本和生成样本时，过程达到平衡。

![](img/image-70t06h40.jpg) 图 11.7 生成器在不同训练迭代次数后的输出结果变化。

## 11.2 WGAN-GP 简介

在本节中，我们将分析原始 GAN [1] 和 Wasserstein 生成对抗网络 (WGAN) 的缺点。然后，我们将介绍 WGAN 的一个改进版本——带有梯度惩罚的 Wasserstein 生成对抗网络 (WGAN-GP)，它应用了梯度惩罚技术来实现 GAN 的稳定训练。

### 11.2.1 生成对抗网络的缺点

原始 GAN 最大的缺点是训练存在不稳定性，这是由于以下原因导致的：

- 判别器训练得太完美，这意味着判别器可以很容易区分出真实数据分布和生成数据分布。如图所示，判别器预测的，在通过 `sigmoid` 激活函数后，其输出值接近 0。判别器预测并在发送到 `sigmoid` 激活函数后，其输出值接近 1。然而，如第 5 章表 5.1 所示，当 `sigmoid` 的输出值接近 0 或 1 时，其导数趋于 0。由于梯度消失问题，生成器在训练过程中很难更新权重。

![](img/image-w0ya5dg1.jpg) 图 11.8 判别器训练的情况。

- 判别器训练不充分，意味着它无法正确判断真实和生成之间的区别。这可能导致真实和生成的被预测为相似。如图所示，真实和生成的重叠了，这意味着判别器无法区分真实和生成。判别器的错误判断还会导致生成器在错误方向上更新。

为了避免图 11.8A 所示的问题并获得如图所示的训练良好的模型，在训练期间需要仔细监控判别器损失（discriminator loss），这样生成器才有机会产生更接近真实数据的结果。

GAN [1] 的损失函数为：

![](img/image-jmqe4iyi.jpg) (11.1)

对于固定的生成器，可以通过以下方式获得最优判别器：
(11.2)

因此，公式 (11.1) 可以重写为：
(11.3)

![](img/image-sxkv4uvy.jpg) ![](img/image-b9jr804v.jpg) ![](img/image-kn178cee.jpg)
真实数据分布。
生成数据分布。
判别器。
优化后的判别器。

Kullback–Leibler 散度（KL 散度），也称为相对熵，用于衡量同一概率空间上两个概率分布 `ℙ` 和 `ℚ` 之间的差异，定义为：
(11.4)

Jensen–Shannon 散度（JS 散度）基于 Kullback–Leibler 散度来衡量两个概率 `ℙ` 和 `ℚ` 之间的相似性，定义为：
![](img/image-9puwzyi4.jpg) (11.5)

公式中使用 JS 散度，因此当使用最优判别器最小化 GAN 损失函数时，它被称为最小化 JS 散度。如果 `ℙ = ℚ`，则意味着训练模型达到了值为 `-2log2` 的全局最小值，且生成器完美地复制了数据分布。

### 11.2.2 Wasserstein 距离简介

如所述，训练 GAN 是困难且不稳定的。为了解决这个问题，Wasserstein GAN (WGAN) [5] 提出了一种使用 Wasserstein 距离的新型损失函数，该距离在处处都具有平滑的梯度。Wasserstein 距离是指将一个数据分布移动到另一个数据分布时搬运质量的最小成本。对于真实数据分布和生成器生成的数据分布，Wasserstein 距离为：
![](img/image-2jur9xmi.jpg) (11.6)

所有可能的传输计划集合，其中联合分布的边缘分布分别为 `ℙ` 和 `ℚ`
`x` 与 `y` 之间的距离
: 传输计划 `γ` 的预期搬运成本
`inf`: 任何传输计划 `γ` 的下确界或最大下界

根据 Kantorovich–Rubinstein 对偶性，公式 (11.6) 的 Wasserstein 距离可以转换为以下形式：
![](img/image-c8rp.jpg) (11.7)

真实数据分布
生成数据分布
判别器
Lipschitz 约束：对于判别器

### 补充说明

与 GAN 不同，WGAN [5] 不采用 `sigmoid` 激活函数，它输出一个标量分数。如果 `ℙ = ℚ`，则判别器的输出接近 `+∞`；如果 `ℙ ≠ ℚ`，则输出接近 `-∞`，如图所示。
![](img/image-22ki.jpg) (11.8)

为了强制判别器的 Lipschitz 约束，WGAN 使用简单的权重裁剪（weight-clipping）方法将权重限制在某个范围内。特别是，如果权重大于 `c`，则将其设置为 `c`；如果小于 `c`，则保持不变。

然而，使用权重裁剪方法会遇到问题：工作 [6] 显示，模型对裁剪阈值 `c` 非常敏感。如果 `c` 稍微增大，通过网络层的梯度增大，会导致梯度爆炸。相反，如果 `c` 稍微减小，通过网络层的梯度变小，会导致梯度消失。

为了解决 WGAN 的问题，提出了 WGAN-GP [6]，它使用梯度惩罚方法代替权重裁剪来强制判别器的 Lipschitz 约束。在 WGAN-GP 中，通过直接约束判别器输出相对于输入的梯度范数来应用梯度惩罚技术。WGAN-GP 的目标函数为：
![](img/image-th8tp.jpg) (11.9)

真实数据分布
生成数据分布
从这些采样的点之间沿点对的直线进行均匀采样
判别器
惩罚系数；该参数在原始工作 [6] 中被设置为 10

### 11.2.3 WGAN-GP 训练

WGAN-GP 的训练过程与原始 GAN 相同，但生成器和判别器的损失函数都经过了改进以提升性能。训练生成器的目的是最小化生成器损失。生成器损失越小，生成器产生接近真实样本的能力越强。例如，将一组随机向量 `z` 输入生成器，产生一张图像 `()`。然后，将此生成的图像发送到判别器进行预测。判别器的输出越大，生成器损失越小。在训练生成器期间，判别器的权重需要固定。生成器的目标函数为：
![](img/image-wxl6rp.jpg) (11.10)

判别器
生成器
生成器的输入样本
N: 数量

训练判别器的目的是最小化判别器损失。判别器损失越小，判别器区分生成样本和真实样本的能力越强。在训练判别器期间，生成器的权重需要固定。判别器的损失函数公式为：
![](img/image-sfk314.jpg) (11.11)

判别器
来自数据集的真实样本
: 生成器生成的样本
惩罚系数；通常设置为 10
N: 数量

# 11.3 实验：WGAN-GP 的实现

本节介绍了如何构建用于图像生成的 WGAN-GP 模型。为了进行实验，我们使用了大规模的 CelebFaces Attributes (CelebA) 数据集 [14] 对模型进行训练和测试。图 11.10 显示了 WGAN-GP 在不同训练迭代后生成的一些图像。

![](img/image-42je15td.jpg) ![](img/image-31l2g8y1.jpg) ![](img/image-q9t6tu7u.jpg)
图 11.10 WGAN-GP 在不同训练迭代后的生成图像。

## 11.3.1 创建项目

由于本章中的 WGAN-GP 示例程序比第 1-9 章中的模型更为复杂，因此我们采用 PyCharm IDE 作为编译器来编写源代码并训练模型。接下来，我们概述了创建项目的过程。

- **一个新项目**：点击“File”（文件）→“New Project”（新建项目），如图 ![](img/image-shq79v9e.jpg) 所示。
图 11.11 在 PyCharm 上创建新项目。
- **新项目的目录**，如图![](img/image-yb9gly54.jpg) 所示。
图 11.12 设置新项目目录。
- **一个 Python 解释器**：打开“Project Interpreter: Python 3.6”，选择“Existing interpreter”（现有解释器），并设置 Python Interpreter，如图![](img/image-dwfkmn2m.jpg) 所示。
图 11.13 解释器设置。
- **一个项目**：点击“Create”（创建）按钮创建一个新项目，如图![](img/image-il1pgzlw.jpg) 所示。
图 11.14 创建项目。

### 补充说明
本章 WGAN-GP 的源代码可以通过图![](img/image-avwr3y28.jpg)所示地址下载
图 11.15 GitHub 上的 WGAN-GP 源代码。

### 11.3.2 数据集介绍

CelebA 数据集 [14] 包含 202,599 张尺寸为 218 × 178 × 3 的图像，分为三个部分，包括训练集中的 162,770 张图像、验证集中的 19,962 张图像以及测试集中的 19,867 张图像。图 11.16 显示了 CelebA 数据集的一些示例图像。可以通过 TensorFlow datasets 如下所示加载数据集。

![](img/image-2r4vqk1v.jpg)
图 11.16 来自 CelebA 数据集的图像。
![](img/image-hsdnjinv.jpg)

## 11.3.3 构建 WGAN-GP 模型和文件

### 文件
WGAN-GP 项目的 Python 文件如图所示。文件如下：
- 训练 WGAN-GP 模型的源代码
- WGAN-GP 模型的源代码
- 自定义损失函数的源代码
- 数据预处理的源代码

### WGAN-GP 模型
![](img/image-6ftos5dq.jpg)
图 11.17 WGAN-GP 项目。

图 11.18 显示了构建 WGAN-GP 模型源代码的流程图。

### 辅助函数
用于构建 WGAN-GP 模型的函数
![](img/image-t54g14dd.jpg)
图 11.18 构建 WGAN-GP 模型源代码的流程图。

WGAN-GP 的网络架构定义在 `models.py` 文件中。图 11.19 显示了生成器和判别器的架构。

![](img/image-j04akwua.jpg)
图 11.19 WGAN-GP 模型架构。

创建生成器和判别器的函数。
![](img/image-65loq4xi.jpg) ![](img/image-kk3ifj0.jpg)

### 损失函数
- **损失**:此损失函数的目的是训练生成器产生与真实图像无法区分的图像（在使用判别器时）。
![](img/image-9qzbm8j.jpg)
- **判别器**
- **生成器**
- **生成器的输入**
- **数据**

生成器损失函数在 `losses.py` 文件中描述。
![](img/image-8z30ff6b.jpg)
- **损失**:降低 `real_loss` 值可以让判别器更容易预测真实图像，降低 `fake_loss` 值可以让判别器更容易识别虚假图像，而梯度惩罚（gradient penalty）则让判别器满足 1-Lipschitz 约束。

判别器损失函数在 `losses.py` 文件中描述。
![](img/image-eq13cemv.jpg)
- **判别器**
- **来自中的真实图像**
- **生成器生成的图像**
- **惩罚系数**:通常置为 10
- **数据**

`real_loss` 和 `fake_loss` 的函数。
![](img/image-fo1kiojz.jpg)
- **惩罚**
![](img/image-hgnhiouz.jpg) ![](img/image-ejhrlzjy.jpg)
- **判别器**
- **真实图像和生成图像的 `t` 在 0 和 1 之间均匀采样**
- **数据**
- **梯度惩罚函数**
![](img/image-3z0tph1v.jpg)

### 预处理
数据处理：使用尺寸为 64 × 64 的输入图像，并将输入图像的每个像素归一化到范围 [-1, 1]。该代码写在 `dataset.py` 文件中。
数据处理函数
![](img/image-i523zob.jpg)

### 训练 WGAN-GP 模型
训练 WGAN-GP 模型这部分代码写在 `train.py` 文件中。
- **必要的包**
![](img/image-5v712c0.jpg)
- **训练参数**
- **数据**
![](img/image-xuwd8j.jpg)
- **WGAN-GP 模型**
![](img/image-wt0kc3dc.jpg)

### 优化器和损失函数
- **优化器**
![](img/image-t41lfqt.jpg)
- **训练生成器的函数**
![](img/image-sit7651c.jpg)
- **训练判别器的函数**
![](img/image-g8dw4y9j.jpg) ![](img/image-dumeyj82.jpg)
- **显示图像**:![](img/image-sbf6yipl.jpg)
- **WGAN-GP**:![](img/image-w9t6p1tp.jpg) ![](img/image-5ltkmdo.jpg)

### 结果
可以通过 TensorBoard 观察生成器输出图像的变化，如图 11.21 和 11.22 分别显示生成器损失、判别器损失以及梯度惩罚。
![](img/image-mxn5lnq.jpg)
图 11.20 TensorBoard 上的生成器图像。
![](img/image-6zklnit.jpg)
图 11.21 生成器损失和判别器损失。
![](img/image-x99telv.jpg)
图 11.22 梯度惩罚。

通过命令行打开 TensorBoard：![](img/image-4yq5cnh.jpg)

### 参考文献
1. Goodfellow I., Pouget-Abadie J., Mirza M., Xu B., Warde-Farley D., Ozair S., Courville A., Bengio Y. Generative adversarial. Neural Inf. Syst. 2014;2672–2680.
2. Radford A., Metz L., Chintala S. Unsupervised representation learning with deep convolutional generative adversarial In International Conference on Learning 2016:1–16.
3. Salimans T., Goodfellow I., Zaremba W., Cheung V., Radford A., Chen X. Improved techniques for training Adv. Neural Inf. Syst. 2016;2226–2334.
4. Lin Z., Khetan A., Fanti G., Oh S. PacGAN: the power of two samples in generative adversarial Adv. Neural Inf. Syst. 2018;1503–1512.
5. Arjovsky M., Chintala S., Bottou L. Wasserstein In Proc. 34th International Conference on Machine 2017;214–223.
6. Gulrajani I., Ahmed F., Arjovsky M., Dumoulin V., Courville A. Improved training of wasserstein Adv. Neural Inf. Syst. 2017;5767–5777.
7. Zhu J.-Y., Park T., Isola P., Efros A.A. Unpaired image-to-image translation using cycle-consistent adversarial In International Conference on Computer 2017;2223–2232.
8. Karras T., Aila T., Laine S., Lehtinen J. Progressive growing of GANs for improved quality, stability, and In International Conference on Learning 2018:1–26.
9. Zhang H., Xu T., Li H., Zhang S., Huang X., Wang X., Metaxas D. Stackgan: text to photo-realistic image synthesis with stacked generative adversarial In Proceedings of the International Conference on Computer 2017:5907–5915.
10. Wang T.-C., Liu M.-Y., Zhu J.-Y., Liu G., Tao A., Kautz J., Catanzaro B. Video-to-video In Advances in Neural Information Processing 2018.
11. Brock A., Donahue J., Simonyan K. Large scale GAN training for high fidelity natural image In 7th International Conference on Learning, ICLR 2019, New Orleans, LA, USA, May 2019. [Online]. Available:
12. Karras T., Laine S., Aila T. A style-based generator architecture for generative adversarial In Proceedings of the IEEE Conference on Computer Vision and Pattern 2019:4401–4410.
13. Villani C. Optimal Transport: Old and Springer Science & Business Media; 2008;vol. 338.
14. Liu Z., Luo P., Wang X., Tang X. Large-scale celebfaces attributes (celeba) Retrieved August 15 2018.

# 第 12 章：目标检测

## 摘要
目标检测是计算机视觉中最重要的任务之一。它不仅对物体类别进行分类，还能确定它们在图像中的位置。在本章中，我们将讨论基于 CNN 的先进目标检测方法。然后，我们将展示一个在 PASCAL VOC 2007 数据集上构建、训练和测试 `YOLO-v3` 示例程序。

**关键词**：R-CNN; YOLO; SSD; RetinaNet; CFF-SSD; DSNet

## 目录
- 计算机视觉
- 先进的基于 CNN 的目标检测方法
- YOLO-v3 检测模型

## 12.1 计算机视觉
计算机视觉是一个交叉科学领域，专注于解决计算机如何理解图像或视频内容，以实现类似于人类视觉系统的自动化任务。计算机视觉应用广泛，如视频监控、人脸识别、人脸标注、图像检索、生物识别、交通监控、可见性恢复、目标检测等。计算机视觉的四个主要任务是：

- **分类**：识别图像的类别，如图所示。用于图像分类的常用网络模型包括 `GoogLeNet`、`ResNet` 等。
![](img/image-5yvt21yk.jpg)
图 12.1 计算机视觉的四个主要任务。

- **检测**：找出给定图像中物体类别及其位置，如图所示。用于目标检测的常用网络模型包括 `Faster R-CNN`、`YOLO-v3` 等。
- **分割**：为图像中的每个像素分配标签，如图所示。用于语义分割的常用网络模型包括 `FCN`、`DeepLab-v3` 等。
- **分割**：在图像的详细像素级识别每个物体的边界，如图所示。用于实例分割的常用网络模型包括 `FCIS`、`Mask R-CNN` 等。

由于目标检测广泛应用于计算机视觉的各个领域，本章重点介绍目标检测方法，特别是先进的基于 CNN 的模型。

## 12.2 目标检测简介
目标检测是计算机视觉中最重要的任务之一。它不仅对物体类别进行分类，还能确定它们在图像中的位置。如图所示，网络接收图像作为输入，然后对该图像输入预测多个类别和边界框。最后，它在输出图像上为每个预测的物体框框并标记标签。
![](img/image-ekcux8kf.jpg)
图 12.2 目标检测框图。

### 补充说明
有许多边界框格式，如图所示的 `(x1, y1, x2, y2)`，其中 `(x1, y1)` 和 `(x2, y2)` 分别是物体在图像上的左上角和右下坐标。另一种常见格式是 `(x, y, w, h)`，其中 `(x, y)` 是左上坐标，`w` 和 `h` 分别是边界框的宽度和高度。每个目标检测方法可以使用不同的边界框格式进行物体位置预测。

基于卷积神经网络（CNN）的目标检测近年来受到了广泛关注并取得了优目的性能。它可以分为两类：(1) 基于区域建议的方法和(2) 基于回归/分类的方法。

- **基于建议的方法**：遵循这种方法，目标检测方法分两步进行预测。在第一步中，使用 `selective search` 等区域建议方法创建给定图像中物体的感兴趣区域 (`RoIs`)。在第二步中，将 `RoIs` 馈入 `CNN` 以对物体进行分类并精炼边界框。虽然由于分两个独立阶段预测物体，基于区域建议的方法运行时间可能较慢，但它们在检测物体方面通常能获得高性能。第一类的代表性网络模型包括 `R-CNN`、`Fast R-CNN`、`Faster R-CNN` 等。
- **方法**：属于这一类的目标检测方法仅使用一步来预测物体，直接从整个输入图像映射到边界框和类别概率。这些方法可以实现实时速度，使其适用于现实系统；然而，准确性并不理想。已经提出了许多方法来提高检测性能，如 `SSD`、`YOLO-v2` 和 `YOLO-v3` 等。

## 12.3 目标检测方法

过去的几十年里已经出现了许多目标检测方法。在本节中，我们将介绍一些基于深度 CNN 的方法。图 12.3 显示了目标检测方法的历史演进。

![](img/image-2n1dcn0e.jpg)
图 12.3 基于 CNN 的目标检测方法的历史演进。

### 12.3.1 R-CNN

Girshick 等人 [20] 在 2014 年提出了具有 CNN 特征的区域（`R-CNN`），它被称为第一个基于 CNN 的检测模型。这种基于区域提议（region proposal）的方法 `R-CNN` 通过两个阶段完成目标检测，如图所示。在第一阶段，采用选择性区域搜索（selective search）方法 [21] 从输入图像中生成约 2000 个可能包含对象的区域提议。在第二阶段，将这些区域提议变形（warped）为固定大小，然后分别通过 `CNN` 进行特征提取。最后，将每个区域提取的特征发送到全连接层，以对物体进行分类并精炼边界框。`R-CNN` 采用类别特定的线性支持向量机（`SVM`）进行物体分类。如果模型需要预测 `n` 个类，则使用 `n` 个 `SVM` 分类器。

![](img/image-lx5otgmm.jpg)
图 12.4 `R-CNN` 的示意图。

尽管 `R-CNN` 在性能上优于以前的方法 [42]，但由于该方法需要对每张图像的大量区域提议进行单独分类，在训练和推理过程中仍然消耗大量时间。

### 12.3.2 Fast R-CNN

Girshick 等人 [22] 在 2015 年提出了具有 CNN 特征的快速区域（`Fast R-CNN`），它是 `R-CNN` 的改进版本，如图所示。

![](img/image-zyqq0tzy.jpg)
图 12.5 `Fast R-CNN` 的架构。

基于 `R-CNN`，`Fast R-CNN` 结合了三个主要改进以提高目标检测性能：
- 使用 `CNN` 从整个图像提取特征，而不是从头开始提取每个图像块，这有助于显著缩短处理时间。
- 采用选择性搜索方法从输入图像中生成 `RoIs`（感兴趣区域），将它们与相应的特征图结合，并发送到 `ROI pooling` 层生成固定长度的特征向量，如图所示。这些生成的特征向量被输入到全连接层用于物体分类和定位。

![](img/image-dfngzbbj.jpg)
图 12.6 `Fast R-CNN` 中的 `RoI pooling`。
- 采用带有 `softmax` 函数的 `SVM` 进行分类。

在 `Fast R-CNN` 中，应用 `ROI pooling` 将不同尺寸的 `ROIs` 变形为固定大小。例如，将一个 8 × 8 的特征图转换为大小为 2 × 2 的固定长度特征，如图所示。

![](img/image-36i9hn9q.jpg)
图 12.7 `RoI Pooling`：(A) 一个 8 × 8 的特征图，(B) 将 `RoI`（红色）与特征图结合，(C) 将 `RoI` 分分为 2 × 2 的目标区域，其中四个区域的大小相等也可以不同，(D) 对每个区域取 `max`，得到一个大小为 2 × 2 的固定长度特征图。

### 12.3.3 Faster R-CNN

Ren 等人 [23] 在 2015 年提出了具有 CNN 特征的快速区域（`Faster R-CNN`），它是 `Fast R-CNN` 的改进版本。`Faster R-CNN` 采用了与 `Fast-CNN` 相似的设计，但将选择性搜索方法替换为区域提议网络（`RPN`），用于在特征图上生成区域提议，如图所示。

![](img/image-npiwm60.jpg)
图 12.8 区域提议网络 (`RPN`)。

`Faster R-CNN` 在速度和精度上均优于 `R-CNN` 和 `Fast-CNN`。该方法相对于之前的版本有两个主要变化：
- 提议网络 (`RPN`）：`Faster R-CNN` 使用 `CNN` 代替了 `R-CNN` 和 `Fast-CNN` 使用的选择性搜索方法。如图所示，在每个滑动位置，`RPN` 同时预测多个区域提议，并输出 `4k` 个坐标和 `2k` 个估计是否目标的得分，其中 `k` 是 anchor 的数量。

![](img/image-s7609wj.jpg)
图 12.9 区域提议网络 (`RPN`)。

`Anchor` 是一个参考框，与尺度和宽高比有关`Faster R-CNN` 在每个位置使用了 9 个 anchor 框（3 种尺度和 3 种宽高比）。这些 anchor 被预先选择以覆盖各种尺寸的物体。

补充说明：
`RPN` 不直接输出边界框（`x, y, w, h`）；它采用以下四个坐标参数化：

![](img/image-6c7nwh2l.jpg)(image-7nroz3h.jpg)
其中 `x` 和 `y` 代表预测中心的坐标，`w` 和 `h` 分别代表其宽度和高度。`Anchors` 框代表真值框（ground-truth）。

### 12.3.4 YOLO-v1

Redmon 等人 [24] 在 2016 年提出了一眼检测（`YOLO`）。它是首个基于回归/分类的目标检测方法，如图所示。与基于区域提议的方法不同，`YOLO` 通过单个 `CNN` 直接从整个图像推断物体分类和定位。这种策略有助于 `YOLO` 达到每秒 45 帧的运行速度，使其成为实时检测器。

![](img/image-5cj9jhy.jpg)
图 12.10 `YOLO` 的架构。

为了，`YOLO` 模型将输入图像划分为 S × S 网格。如果一个网格包含物体的中心，则负责检测该物体。每个网格有 `B` 个边界框，并预测这些框的得分。每个预测的边界框包含五个预测值（`x, y, w, h`）和一个得分，其中 `x` 和 `y` 代表相对于网格边界的中心坐标，`w` 和 `h` 代表相对于整个图像的宽度和高度，得分反映是否存在物体。边界框得分越高，网格预测包含物体的概率越大。类别概率基于预测类别的数量。如果有 20 个类，则输出 20 个类别概率。

![](img/image-uyu5np3m.jpg)
图 12.11 `YOLO` 的预测过程。

`YOLO` 模型的输出尺寸计算如下：
`Output size = S × S × (B × 5 + C)`
- `S`: 网格的宽度和高度。
- `B`: 每个网格预测的边界框数量。
- `5`: 网格中每个预测边界框包含五个预测值：`y, w` 和框得分。
- `C`: 类别概率的数量；如果有 20 个类别，则输出 20 个类别概率。

例如，`YOLO` 在 PASCAL VOC 数据集上的 `S = 7`, `B = 2`  `C = 20`。`YOLO` 模型的输出尺寸为 `7 × 7 × (2 × 5 + 20) = 7 × 7 × 30` 张量。

补充说明：
`YOLO` 在每个网格上预测两个边界框，因此总共预测了 `7 × 7 × 2 = 98` 个物体框。然而，这 98 个边界框并不是最终预测。为了给最终答案保留最佳边界框，`YOLO` 使用非极大值抑制（`NMS`）方法移除冗余边界框，如图所示。

![](img/image-583pkf4y.jpg)
图 12.12 使用非极大值抑制 (`NMS`) 选择最佳边界框。

`NMS` 方法如下：
- 得分太小，意味着预测边界框内没有物体，因此首先移除得分小于阈值的边界框。
- 将剩余的边界框按照得分从大到小排序，并放入“物体框列表”，标记为 `L`。
- 从 `L` 中取出得分最高的边界框，并放入“过滤后的物体框列表”，标记为 `F`。
- 分别计算 `F` 中边界框与 `L` 中所有边界框的交并比（`IoU`）。如果计算出的 `IoU` 值大于 `IoU` 阈值，则从 `L` 中移除该边界框，直到 `L` 为空。

### 12.3.5 SSD

Wei Liu 等人 [25] 在 2016 年提出了单次预测检测器（`SSD`）。它是一种基于 CNN 的实时检测模型，通过将所提出的跨分辨率融合（`CFF`）方法应用于基础检测器 `SSD` 来提高目标检测性能，尤其是对小目标的检测。`SSD` 有两个版本：用于快速检测的 `1CFF-SSD` 和用于更准确检测的 `2CFF-SSD`，如图所示。

![](img/image-so34oi5w.jpg)
图 12.22 `SSD` 的架构。

空洞空间金字塔池化（`N-ASPP`）模块
它使用浅层特征图作为输入，通过四个不同速率的并行空洞卷积提取多尺度上下文信息。

![](img/image-x2i5qwn.jpg)
图 12.23 跨分辨率融合 (`CFF`)

在 `1CFF-SSD` 架构中，采用一种 `CFF`，即使用不同速率的空洞卷积来增强语义信息。在 `2CFF-SSD` 中，为了产生检测，`SSD` 使用来自六层不同卷积的特征图。在 `SSD` 模型中，特征图中的每个网格预测多个边界框，深层负责检测大物体，而浅层负责检测小物体。由六层卷积预测的边界框数量计算如下：
`Total box: 5776 + 216 + 150 + 36 + 4 = 8732`
每个预测框包含 `N` 个类别得分和四个偏移。默认框被预先选择以覆盖各种尺寸的物体。`SSD` 使用不同层具有不同的默认框，每个框位于相应的网格。

### 12.3.6 YOLO-v2

Redmon 等人 [26] 在 2017 年提出了 `YOLOv2`，也称为 `YOLO9000`，它是 `YOLO` 的改进版本，比 `YOLO` 和 `SSD` 都更快更强。`YOLOv2` 包含了以下重要变化：
- 归一化：在卷积层中加入批归一化（`Batch normalization`），这有助于在训练过程中避免过拟合问题并提高约 2% 的平均精度`mAPAP）。
- 分类器：在 `YOLOv2` 中，分类器首先使用 224 x 224 的输入分辨率训练，然后返回 480 x 480 的分辨率，利用更少的 epoch。这有助于提高模型 4% 的精度`mAP`。
- anchor 框：`YOLO-v2` 使用 anchor 框的预测取代了 `YOLO` 中的任意边界框。虽然使用 anchor 框使精度略有下降，但增加了检测所有真值目标的概率。
- 聚类：为了找到最适合数据集的 top-K 边界框，采用了 `K`-means 聚类方法来定位 top-K 聚类的中心。对于最佳设计，为训练 `YOLO-v2` 模型选择了 5 个 anchor。
- 位置预测：由于 `YOLO` 对位置预测没有加约束，导致训练不稳定。使用 `sigmoid` 函数将模型的输出预测限制在 0 到 1 之间，使得 `YOLO-v2` 在训练过程中更稳定。在输出特征图中，`YOLO-v2` 在每个网格预测五个边界框；每个边界框有五个坐标，相应的预测定义为：
`Pr(object) * IOU(predicted box, ground truth box) = 预测框的中心、宽度和高度；图像的左上角；sigmoid 激活函数；anchor 框的宽度和高度；预测框的得分`

![](img/image-4p68ml3j.jpg)
图 12.14 使用 `YOLO-v2` 的细粒度特征。

补充说明：
- 重组层：与减少输入信息的 `max pooling` 层不同，图 14 中的 `reorganization layer` 在操作后保留了输入的原始原始信息，如图所示。

![](img/image-abbpa0c.jpg)
图 12.15 重组层操作。
- 训练：在 `YOLO-v2` 模型训练期间，输入图像的大小每 10 个 batch 改变一次。通过取 32 的倍数（如 320, 352, 384, 416, 448, 480, 512, 544 和 576），`YOLO-v2` 使用 320 x 320 的最小输入大小和 608 x 608 的最大大小。这种策略有助于 `YOLO-v2` 在以实时速度运行的同时克服多尺度目标检测的问题。

### 12.3.7 特征金字塔网络

Lin 等人 [27] 在 2017 年引入了特征金字塔网络（`FPN`）。`FPN` 采用带有横向连接的金字塔架构来在不同尺度上检测物体。使用 `CNN` 进行特征提取时，深层具有低分辨率和语义特征，而浅层包含高分辨率和弱语义信息。为了创建一个包含所有层丰富语义特征的金字塔，在 `FPN` 中通过自上而下的路径构建高分辨率层。由于重构层具有强语义特征但缺乏位置信息，这些层与相应的特征图之间添加了横向连接以更好地预测物体，如图所示。

![](img/image-m0xb5tcb.jpg)
图 12.16 特征金字塔网络 (`FPN`) 的架构。

图中总结了四种常用的目标检测架构的特征：
- 17A 显示了 `FPN` 的架构。在这种网络架构中，特征在每个尺度上独立计算。虽然这种方法是有效的，但运行时间非常慢。`YOLO` [24] 是这种架构的代表。
- 17B 显示了单尺度特征的网络架构。这种方法使用单一尺度的特征进行预测。它可以实现实时预测速度，但由于使用缺乏语义信息的浅层来预测小物体，精度不理想。
- 17C 显示了架构。`SSD` 使用不同尺度的特征图来做出预测。这种方法的优点是不需要额外的计算。
- 17D 显示了 `FPN` 架构。类似于图中的层次，`FPN` [27] 也从较低层级预测小物体，并从更高层级预测大物体。在 `FPN` 中，高层语义信息在所有尺度上扩散，因此比图中网络更有效。

![](img/image-js7oh5hk.jpg)
图 12.17 用于目标检测常用的架构。

### 12.3.8 RetinaNet

Lin 等人 [28] 在 2017 年提出了用于密集目标检测的 Focal Loss（`RetinaNet`）。为了提高目标检测性能，`RetinaNet` 采用 `ResNet` [35] 作为主干网络，采用 `FPN` 架构 [27] 构建多尺度特征金字塔，并在每个金字塔层级添加两个子网络，即分类子网络和回归子网络，分别用于物体分类和定位，如图所示。分类子网络和回归子网络具有相同的架构，包括四个 3x3 卷积层带有 `ReLU` 激活，每个层有 256 个滤波器，随后是用于预测的 3x3 卷积层。两个子网络的区别在于分类子网络的最后一层使用 `A * K` 个滤波器后接 `sigmoid` 激活函数，而回归子网络利用 `4 * A` 个滤波器。`A` 和 `K` 分别代表 anchor 的数量和物体类别。注意的是，`RetinaNet` 中提出的 focal loss 用于训练物体分类以解决类别不平衡问题并提高目标检测精度。

![](img/image-xyl92tgd.jpg)
图 12.18 `RetinaNet` 的架构。

`Focal loss` 是交叉熵损失（`CE`）的改进版本，定义如下：

![](img/image-85lgxi8l.jpg)
其中是权重因子 `γ` 是一个可调的聚焦参数，定义如下：

![](img/image-rp9a6ghe.jpg)
这里，`y` 是真值类别，`p` 是模型预测的类别概率。如果 `γ = 0`，则等于 `CE`；如果设置 `γ > 0`，网络在训练过程中可以更多关注分类错误的示例而不是分类良好的示例。例如：
- 模型输出一个高概率值，例如 = 0.8，意味着预测结果接近真值（分类良好的示例）。
- 当 `γ = 0` 时，`FL = 0.32192`
- 当 `γ = 2` 时，`FL = 0.01287`
- 模型输出一个低概率值，例如 = 0.2，意味着预测结果与真值差异很大（分类错误的示例）。
- 当 `γ = 0` 时，`FL = 0.32192`
- 当 `γ = 2` 时，`FL = 0.48603`
如所示，如果 `γ > 0`，分类良好的示例的损失为 `FL = 0.01287`，模型关注分类错误的示例 `FL = 0.48603`。在实验中，`RetinaNet` 在 `γ = 2` 时效果最好。

### 12.3.9 YOLO-v3

Redmon 在 2018 年提出了 `YOLO-v2` 的优化版本—— `YOLO-v3`。`YOLO-v3` 通过三个主要改进获得了惊人的检测效果：
(1) 改变主干网络以提取更好的特征
(2) 增加 anchor 框的数量以实现精确预测
(3) 应用 `FPN` 概念进行多尺度检测，如图所示。

主干网络：所有检测方法的第一步都是训练一个主干网络。例如，`SSD` 的主干是 `VGG-16`，`YOLO-v2` 的主干是 `DarkNet-19`，`RetinaNet` 的主干是 `ResNet-101`，而 `YOLO-v3` 的主干是 `Darknet-53`。`Darknet-53` 在 `Darknet-19` 架构上通过添加快捷连接构建了 53 个卷积层。`Darknet-53` 在精度和每秒操作次数上比 `DarkNet-19`、`ResNet-101` 和 `SSD` 更高效。

![](img/image-hyugn0g.jpg)
图 12.20 `Darknet-19` 和 `Darknet-53` 的架构。

框和多尺度预测：`YOLO-v2` 使用 5 个 anchor 框预测物体位置，而 `YOLO-v3` 将 anchor 框的数量从 5 增加到 9。这 9 个具有不同尺度的 anchor 被分配给三个不同的输出层，如表 12.1 所示。

表 12.1
| | | |
|---|---|---|
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |
| | | |

![](img/image-jnxzqrq.jpg)
图 12.19 `YOLO-v3` 的架构。

`YOLO-v3` 的三个输出分别是 `52 × 52`、`26 × 26` 和 `13 × 13` 网格，对应于输出图 `52 × 52`、`26 × 26` 和 `13 × 13`。输出图越小，相应网格的感受野越大。如图所示，`4 × 4` 特征图的感受野比 `2 × 2` 特征图 小，因此使用小 anchor 框 (a) 比使用 anchor boxes (c) 好。相反，`2 × 2` 特征图的每个网格感受野更大，因此使用大 anchor 框 (d) 比使用小 anchors (b) 好。

![](img/image-zclbpti9.jpg)
图 12.21 anchor 框的配置。

由于每个输出层分配了三个不同的 anchor 框，且每个网格预测三个边界框，`YOLO-v3` 的每个输出层形状可以表示为 4 个边界框偏移、1 个物体性预测和 `c` 个类别预测。例如，使用 `YOLO-v3` 在包含 80 类的 COCO 数据集上检测物体（`c = 80`）。三个预测层的输出形状分别为 `(13,13,3,85)`、`(26,26,3,85)` 和 `(52,52,3,85)`，对应的预测框数量分别为 507、2028 和 8112，所示。

为了训练 `YOLO-v3`，目标损失函数由三部分组成：偏移损失、边界框损失以及分类损失，定义如下：

- 每个真值边界框的四个坐标
- 每个预测边界框的四个坐标
- 网格 `i` 中框的预期得分
- 网格 `i` 中框的预测得分
- 网格 `i` 中类别 `c` 的预期类别概率
- 网格 `i` 中类别 `c` 的预测类别概率
`S`: 网格的宽度和高度；`YOLO-v3` 有三种尺寸的网格，包括 `13 × 13`、`26 × 26` 和 `52 × 52`
`B`: 如果网格 `i` 中的边界框负责检测物体，则每个网格预测的边界框数量；否则，如果网格 `i` 中没有物体，则为 0
交叉熵

### 12.3.10 CFF-SSD

Le 等人 [31] 在 2019 年提出了跨分辨率融合单检测器（`CFF-SSD`）。`CFF-SSD` 通过将提出的跨分辨率融合（`CFF`）方法应用于基础检测器 `SSD` 来提高目标检测性能，尤其是对小目标的检测。`CFF-SSD` 有两个版本：用于快速检测的 `1CFF-SSD` 和用于更准确检测的 `2CFF-SSD`，如图所示。

![](img/image-so34oi5w.jpg)
图 12.22 `CFF-SSD` 的架构。

空洞空间金字塔池化（`N-ASPP`）模块
`N-ASPP` 模块使用浅层特征图作为输入，通过四个不同速率的并行空洞卷积提取多尺度上下文信息。

![](img/image-x2i5qwn.jpg)
图 12.23 跨分辨率融合 (`CFF`)

在 `1CFF-SSD` 架构中，采用一种 `CFF`，即使用不同速率的空洞卷积来增强语义信息。在 `2CFF-SSD` 中，为了产生检测，`SSD` 使用来自六层不同卷积的特征图。在 `SSD` 模型中，特征图中的每个网格预测多个边界框，深层负责检测大物体，而浅层负责检测小物体。由六层卷积预测的边界框数量计算如下：
`Total box: 5776 + 216 + 150 + 36 + 4 = 8732`
每个预测框包含 `N` 个类别得分和四个偏移。默认框被预先选择以覆盖各种尺寸的物体。`SSD` 使用不同层具有不同的默认框，每个框位于相应的网格。

## 12.4 实验：YOLO-v3 的实现

本节介绍了如何构建用于目标检测的 `YOLO-v3` 模型。为了进行实验，我们使用了 `PASCAL VOC 2007` 数据集对模型进行训练和测试。

## 12.4.1 加载 YOLO-v3 项目

由于本章 `YOLO-v3` 模型的示例程序比第 1-9 章中的之前的示例更复杂，我们使用 `PyCharm` IDE 作为编译器来编写和训练模型。加载 `YOLO-v3` 项目的过程如下。

- `YOLO-v3` 项目：请访问 `https://github.com/taipeitechmmslab/MMSLAB-DL/tree/master` 下载源码，如图![](img/image-rwie3eg6.jpg)图 12.28 GitHub 上的`YOLO-v3` 项目 (Lab12)所示。
- 使用 `PyCharm` 打开项目，如图![](img/image-rdro5kwk.jpg)图 12.29 在 PyCharm 上打开项目。
- 加载项目的路径，如图![](img/image-kbvx2m5z.jpg)图 12.30 `YOLO-v3` 项目路径。
- 编译环境（注意：如果此步骤已设置，则省略）：点击 `File` → `Settings` → `Project` “项目名称” → `Project Interpreter` → `Add` → `Virtualenv Environment` → `Existing environment` → 选择虚拟机，如图 12.31 和 ![](img/image-vwibgmtx.jpg)图 12.31 新解释器、 ![](img/image-9nw2s6k6.jpg)图 12.32 选择现有的虚拟环境。

## 12.4.2 数据集介绍

在本节中，我们使用 `PASCAL Visual Object Classes 2007` (`PASCAL VOC 2007`) 数据集来训练和测试 `YOLO-v3` 模型。这是一个基准数据集，已用于评估许多目标检测方法，如 `R-CNN`、`SSD`、`YOLO` 等。可以通过 `TensorFlow` 数据集加载该数据集，如下所示![](img/image-otn3e3f6.jpg) `PASCAL VOC 2007` 数据集由三部分组成，包括 2501 张图像的训练集、2510 张图像的验证集和 4952 张图像的测试集。该数据集有 20 类，可以使用以下命令显示![](img/image-ijkf7c43.jpg)显示数据集：显示数据集中的图像以及目标的地面真边界框![](img/image-8amjblnu.jpg) ![](img/image-65182mxv.jpg)

## 12.4.3 构建 YOLO-v3 模型

图 12.33 显示了 `YOLO-v3` 项目，包含以下文件和文件夹：
- 训练 `YOLO-v3` 模型的源码文件
- 多尺度训练的源码文件
- 测试模型的源码文件
- 设置模型参数、训练参数和权重路径的源码文件
- 将 `YOLO-v3` 训练权重转换为 `TensorFlow` 格式的源码文件
- 存储自定义网络层源码文件的文件夹
- 存储自定义网络模型源码文件的文件夹
- 存储自定义损失函数源码文件的文件夹
- 存储工具包的文件夹，例如用于加载数据集的 `dataset.py`、用于评估模型的 `evaluation.py` 等
- 存储输出结果的文件夹![](img/image-ewipp1dd.jpg)图 12.33 `YOLO-v3` 项目 ![](img/image-2fmp3n0j.jpg)图 12.34 `YOLO-v3` 模型源码流程图。

运行 `YOLO-v3` 项目需要执行两个文件：用于训练模型的 `train.py`（或 `train-multi-scale.py`）和用于测试训练模型的 `test.py`。`train.py` 和 `train-multi-scale.py` 的区别在于 `train.py` 使用固定尺寸训练模型，而 `train-multi-scale.py` 采用多尺度训练，输入图像的大小按 32 的倍数进行变化，如 320、352、384、416、448、480、512、544、576 和 608，每 10 个 epoch 变化一次。最小输入尺寸为 320×320，最大输入尺寸为 608×608。使用 `train-multi-scale.py` 的训练结果优于 `train.py`，但耗时更长。

### YOLO-v3 模型

图 12.34 是构建 `YOLO-v3` 模型的流程图。

### 辅助函数
- **backbone (骨干网络)**：`Darknet-53` 的源码写在 `model → darknet.py`。`YOLO-v3` 使用 `Darknet-53` 作为特征提取的骨干网络。图 12.35 和 12.36 显示了 `Darknet-53` 的架构![](img/image-mptzu1or.jpg)图 12.35 `Darknet-53` 架构 (1) ![](img/image-65ldwtal.jpg)图 12.36 `Darknet-53` 架构 (2)。`Darknet-53` 代码如下![](img/image-y6djff28.jpg)Darknet Convolution 和 `Darknet Residual Block` 的源码 ![](img/image-bjponje8.jpg) ![](img/image-8ftwtbc.jpg)
- **architecture (架构)**：`YOLO-v3` 模型源码写在 `model → yolo.py`。`YOLO-v3` 使用三个不同的卷积层检测目标。图 12.37 和 12.38 显示了 `YOLO-v3` 的架构![](img/image-ehbq6lr.jpg)图 12.37 `YOLO-v3` 架构 (1) ![](img/image-56gp8zy9.jpg)图 12.38 `YOLO-v3` 架构 (2)。`YOLO-v3` 模型源码如下![](img/image-zeq381r.jpg) ![](img/image-myhqcs6.jpg)
- **setting of convolutional layer of YOLO-v3 (YOLO-v3 卷积层设置)**：![](img/image-e46dd7p.jpg) ![](img/image-sfk1xvlm.jpg)此自定义层用于将输出尺寸重塑为 `(act, grid_h, grid_w + 5)` ![](img/image-pqkt0q84.jpg)，通过以下公式将模型预测坐标转换为边界框 `(x, y, w, h)` ![](img/image-0g2f0qil.jpg) ![](img/image-amz6i8ap.jpg) ![](img/image-yr4zp9x.jpg)，对应预测边界框的中心、宽度和高度。
- **top corner of the image (图像顶角)**：![](img/image-e1vg9shu.jpg) ![](img/image-vm4kh118.jpg) `sigmoid` 激活函数。此自定义层用于移除冗余边界框预测![](img/image-3spdkfox.jpg) ![](img/image-sdup0ngz.jpg)
- **loss function (损失函数)**：目标损失函数的源码如下![](img/image-jbf65o0t.jpg) ![](img/image-1d4t7ve.jpg) ![](img/image-s15ba0gu.jpg) 计算 IoU 的函数 ![](img/image-4o37oa7.jpg) ![](img/image-1
- **preprocessing (预处理)**：数据预处理源码存储在 `utils → dataset.py`。`YOLO-v3` 模型训练的数据预处理分为两个步骤：(1) 数据增强和(2) 训练目标转换。
- **augmentation (增强)**：颜色转换、水平翻转、图像缩放和图像旋转 image-m0ovxqp8.jpg) ![](img/-0hokggtb.jpg)
- **target transformation (目标转换)**：将数据格式 `(batch size, 100, [x1, y1, x2, y2, classes])` 转换为 `(batch size, grid, grid, anchors, [x, y, w, h, obj, class])`image-70e46b2p.jpg) ![](img/ey3hmt03.jpg) ![](img/we9ukf1r.jpg)
- **pre-trained model (预训练模型)**：使用 `convert.py` 文件将原始预训练的 `YOLO-v3` 模型转换为 `Keras` 使用的 HDF5 格式 image-2c3va4a9.jpg
- **hyperparameters for training (训练超参数)**：`config.py` 文件用于存储 `YOLO-v3` 模型训练的超参数 image-xscejl60.jpg) ![](img/8whn5rrv.jpg)
- **training the YOLO-v3 model (训练 YOLO-v3 模型)**：训练 `YOLO-v3` 模型，首先加载转换后的 `YOLO-v3` 模型权重 (`yolov3.h5`)，然后在 `PASCAL VOC 2007` 数据集上对模型进行微调。代码写在 `train.py` 文件中。
- **packages (包)**:image-ik5zyhxr.jpg
- **hyperparameter for training YOLO-v3 (YOLO-v3 训练超参数)**:image-ci2kiue.jpg)
- **YOLO-v3 model and load weights (YOLO-v3 模型及加载权重)**:image-zqf00t.jpg)
- **callback (回调)**:image-e4t53q.jpg)
- **function for training (训练函数)**:image-s2721t.jpg) ![](img/alk75u.jpg) ![](img/wtkevb1.jpg)
- **YOLO-v3 (Step 1) (YOLO-v3 步骤 1)**：冻结模型的所有层；仅更新输出权重 image-jhcgy6l.jpg)
- **YOLO-v3 (Step 2) (YOLO-v3 步骤 2)**：训练整个网络 image-hjrscyt.jpg)
- **predictions (预测)**：训练后，在 `Pascal2007` 训练集上训练的 `YOLO-v3` 权重用于在 `VOC2007` 测试集上进行预测。代码写在 `test.py` 文件中 image-271f9jd9.jpg) ![](img/dxawmi.jpg)
- **packages (包)**
- **test data and data information (测试数据和数据信息)**:yh86zuci.jpg
- **YOLO-v3 model and load weights (YOLO-v3 模型及加载权重)**:image-k7262ve.jpg
- **of YOLO-v3 (YOLO-v3 的)**:image-j9ipiole.jpg
- **results (结果)**：运行预测函数；图 12.39 显示了 `YOLO-v3` 模型的一些结果 image-l2vtx2y.jpg
- **Detection results of the YOLO-v3 model on Pascal test set (YOLO-v3 模型在 Pascal 测试集上的检测结果)**:image-cy36fyw.jpg

### References
1. Zhu X., Wang Y., Dai J., Yuan Y. Flow-guided feature aggregation for object In 2017 International Conference on Computer Vision, Venice; 2017:408–417.
2. Huang S.C. An advanced motion detection with video quality analysis for surveillance Trans. Circuits Syst. Video. 2011;21(1):1–14.
3. Huang S.C., Do B.H. Radial function based neural network for motion detection in dynamic Cybern. 2014;44(1):114–125.
4. Taigman Y., Yang M., Ranzato M., Wolf L. Deepface: closing the gap to human-level performance in face IEEE Conf. Comput. Vis. Pattern Recognit. 2014;1701–1708.
5. Schroff F., Kalenichenko D., Philbin J. Facenet: a unified embedding for face recognition and Proc. IEEE Conf. Comput. Vis. Pattern Recognit. 2015;815–823.
6. Huang S.C., Jiau M.K., Hsu C.A. A high-efficiency and high-accuracy fully automatic face annotation for distributed online social Trans. Circuits Syst. Video. 2014;24(10):1810–1813.
7. Zheng L., Yang Y., Tian Q. SIFT meets CNN: a decade survey of instance Trans. Pattern Anal. Mach. Intell. 2018;40(5):1224–1244.
8. Gordo A., Almazan J., Revaud J., Larlus D. Deep image retrieval: learning global representations for image In: European Conference on Computer 2016:241–257.
9. Cao K., Jain A.K. Automated latent fingerprint Trans. Pattern Anal. Mach. Intell. 2019;41(4):788–800.
10. Gangwar A., Joshi A. DeepIrisNet: deep iris representation with applications in iris recognition and cross-sensor iris In: 2016 International Conference on Image Processing, Phoenix, AZ; 2016:2301–2305.
11. Huang S., Chen B. Highly accurate object detection in variable bit rate video-based traffic monitoring Trans. Neural Netw. Syst. 2013;24(12):1920–1931.
12. Huang S., Chen B. Automatic moving object extraction through a real-world variable-bandwidth network for traffic monitoring Trans. Ind. Electron. 2014;61(4):2099–2112.
13. Liu Y., Jaw D., Huang S., Hwang J. DesnowNet: context-aware deep network for snow Trans. Image Process. 2018;27(6):3064–3073.
14. Chen B., Huang S., Li C., Kuo S. Haze removal using radial basis function networks for visibility restoration Trans. Neural Netw. Syst. 2018;29(8):3828–3838.
15. Huang S., Chen B., Wang W. Visibility restoration of single hazy images captured in real-world weather Trans. Circuits Syst. Video. 2014;24(10):1814–1824.
16. Le T.-H., Lin P.-H., Huang S.-C. LD-Net: an efficient lightweight denoising model based on convolutional neural network, IEEE J. Comput. Soc. 2020;1:173–181.
17. Huang S., Ye J., Chen B. An advanced single-image visibility restoration algorithm for real-world hazy Trans. Ind. Electron. 2015;62(5):2962–2972.
18. Chen B., Huang S. Edge-based Dehazing algorithm for visibility in real Disp. Technol. 2016;12(9):964–970.
19. Chen B., Huang S. Error-optimized sparse representation for single image Trans. Ind. Electron. 2017;64(8):6573–6581.
20. Girshick R., Donahue J., Darrell T., Malik J. Rich feature hierarchies for accurate object detection and Proc. IEEE Conf. Vis. Pattern Recognit. 2014;580–587.
21. Uijlings J., van de Sande K., Gevers T., Smeulders A. Selective search for object Int. J. Comput. Vis. 2013.
22. Girshick R. Fast Proceedings of the IEEE Conference on Vision 2015:1440–1448.
23. Ren S., He K., Girshick R., Sun J. Faster R-CNN: towards real-time detection with region proposal In Neural Information Processing 2015:91–99.
24. Redmon J., Divvala S., Girshick R., Farhadi A. You look once: unified, real-time detection. IEEE Conf. Vis. Pattern Recognit. 2016;79–88.
25. Liu W., Anguelov D., Erhan D., Szegedy C., Reed S. Ssd: single shot multibox In: European Conference on Computer 2015:21–37.
26. Redmon J., Farhadi A. YOLO9000: better, faster, Proc. IEEE Conf. Vis. Pattern Recognit. 2017;7263–7271.
27. Lin T.-Y., Dollár P., Girshick R., Hariharan B., Belongie S. Feature pyramid networks for object Proc. IEEE Conf. Vis. Pattern Recognit. 2017;2117–2125.
28. Lin T.-Y., Goyal P., Girshick R., He K., Dollar P. Focal loss for dense Proceedings of the IEEE International Conference on Vision 2017:2999–3007.
29. He K., Gkioxari G., Dollar P., Girshick R.B. Mask: Proceedings of the IEEE Conference on Vision 2017;2980–2988.
30. Redmon J., Farhadi A. YOLOv3: An incremental improvement, arXiv 2018.
31. Le T., Huang S., Jaw D. Cross-resolution feature fusion for fast detection in intelligent Sensors J. 2019;19(12):4696–4704.
32. S. Huang, T. Le and D. Jaw, DSNet: joint semantic learning for object detection in inclement weather, in IEEE Transactions on Pattern Analysis and Machine Intelligence.
33. Le T.-H., Jaw D.-W., Lin I.-C., Liu H.-B., Huang S.-C. An efficient hand detection method based on convolutional neural In: 2018 7th International Symposium on Next Generation Electronics; 2018:1–2.
34. Szegedy C., et al. Going deeper with IEEE Conference on Computer Vision and Pattern 2015:1–9.
35. He K., Zhang X., Ren S., Sun J. Deep residual learning for image Proc. IEEE Conf. Vis. Pattern Recognit. 2016;770–778.
36. Long J., Shelhamer E., Darrell T. Fully convolutional networks for semantic Proc. IEEE Conf. Vis. Pattern Recognit. 2015;3431–3440.
37. Chen L.-C., Papandreou G., Schroff F., Adam H. Rethinking atrous convolution for semantic image segmentation, arXiv 2017.
38. Li Y., Qi H., Dai J., Ji X., Wei Y. Fully convolutional instance-aware semantic Proc. IEEE Conf. Vis. Pattern Recognit. 2017;2359–2367.
39. Zhao Z.-Q., Zheng P., Xu S.-t., Wu X. Object detection with deep learning: a IEEE Trans. Neural Netw. Syst. 2019;30(11):3212–3232.
40. Uijlings J.R., Van De Sande K.E., Gevers T., Smeulders A.W. Selective search for object Int. J. Comput. Vis. 2013;104(2):154–171.
41. Fidler S., Mottaghi R., Yuille A., Urtasun R. Bottom-up segmentation for top-down In: Proceedings of the IEEE Conference on Computer Vision and Pattern 2013:3294–3301.
42. Sermanet P., Eigen D., Zhang X., Mathieu M., Fergus R., LeCun Y. Overfeat: Integrated recognition, localization and detection using convolutional networks, arXiv 2013.
43. Zeiler M.D., Fergus R. Visualizing and understanding convolutional In: European Conference on Computer 2014:818–833.
44. Simonyan K., Zisserman A. Very deep convolutional networks for large-scale image In: International Conference on Learning 2015:1–14.
45. Chen L., et al. DeepLab: Semantic image segmentation with deep convolutional nets, atrous convolution, and fully connected IEEE Trans. Pattern Anal. Mach. Intell. 2018;40(4):834–848.

# 索引
注：页码后的后的 `f` 表示图表，`t` 表示表格，`b` 表示文本框。

## A
- `激活 (Activation)` 29
- `激活 (Activation)`
- `AdaGrad`
- `Adam`
- `AE 模型` 参见 `自动编码器 (AE) 模型`
- `锚点框 (Anchor boxes)`
- `应用程序接口 (Application programming interfaces)`
- `高级的 (advanced)`
- `自定义 API 和高级 Keras API`
- `自定义回调函数 (custom callback)`
- `自定义损失函数 (custom loss)`
- `自定义指标 (custom metric)`
- `自定义网络 (custom network)`
- `Keras` 225
- `TensorBoard` 参见 `TensorBoard`
- `数据流 (data flow)`
- `数据 (data)`
- `深层 (deep)`
- `部署 (deployment)`
- `即时模式 (eager)`
- `改进 (improvement)`
- `训练 (training)`
- `人工智能 (Artificial intelligence)`
- `人工神经网络 (Artificial neural networks)`
- `大气散射 (Atmospheric scattering)`
- `空洞的 (Atrous)`
- `自动编码器 (AE)` 也参见`变分自动编码器 (VAE) 模型`

## B
- `反向传播 (Backpropagation)` 117–121
    - `单层神经网络`
    - `双层神经网络`
- `批次 (Batch)` 291
- `神经网络 (neural network)`
- `验证 (verification)`
- `伯克利人工智能 (Berkeley Artificial Intelligence)`
- `二分类 (Binary classification)` 92
    - `输入 (input)`
    - `损失 (loss)`
    - `网络 (network)`
    - `输出 (output)`
- `二分类 (Binary classification)`
- `二分类 (binary classification)`
- `机器学习 (machine learning)`
- `宝可梦战斗预测 (Pokemon combat prediction)`
- `代码 (code)`
- `宝可梦大针虫洞 (Pokémon-Weedle's cave)`
- `二交叉熵 (BCE)` 238
- `边界框置信度 (Bounding box confidence)`

## C
- `回调函数 (Callback)`
    - `的自定义 API 和高级 Keras API`
- `类别的 (Categorical)`
- `分类交叉熵 (CCE) 损失` 153
- `CelebFaces 属性 (CelebA)` 270
- `中央处理单元 (Central processing units)`
- `CIFAR-10 图像分类 (CIFAR-10 image classification)`
    - `架构 (architecture)`
    - `CIFAR-10` 188–189
    - `代码 (code)`
    - `流程图 (flowchart)`
    - `TensorFlow`
- `分类 (Classification)`
- `分类 (Classification)`
- `二元的 (binary)` 参见`二分类问题`
- `聚类 (Clustering)`
- `CNNs` 参见`卷积神经网络 (CNNs)`
- `COCO` 297
- `Jupyter 命令模式 (Command mode, Jupyter)`
- `公共块 (Common block)`
- `计算机 (Computer)`
- `混淆矩阵 (Confusion matrix),`
    - `带有 (with)`
- `卷积的 (Convolutional)` 147
- `卷积神经网络 (Convolutional neural networks)` 220
    - `用于图像 (for image)`
    - `物体 (object)`
    - `更快的 (faster)`
    - `快速 (fast)`
    - `特征金字塔 (feature pyramid)`
    - `单阶段多框检测 (single shot multibox)` 302–329
    - `操作 (operation)`
- `卷积 (Convolution)`
- `交叉熵 (Cross-entropy)`
- `损失 (loss)`
- `跨分辨率特征融合 (Cross-resolution feature fusion)`
- `跨分辨率特征融合单阶段多框检测 (Cross-resolution feature fusion single shot multibox detector)`
- `CUDA`
- `自定义回调函数 (Custom callback)`
- `自定义损失函数 (Custom loss)`
- `自定义指标 (Custom metric)`
- `自定义网络 (Custom network)`

## D
- `Darknet-53`
- `Darknet`
- `Darknet 残差 (Darknet Residual)`
- `数据增强 (Data augmentation)`
    - `多类别分类 (multi-category classification)`
- `数据 (Data)`
- `数据预处理 (Data preprocessing)`
    - `数据处理, Keras`
- `深度卷积的 (Deep convolutional)`
- `深度学习 (Deep learning)`
- `深度学习 GPU 训练系统 (Deep Learning GPU Training System)`
- `DeepLearning4J`
- `深度神经网络 (Deep neural networks)` 118
- `检测子网络 (Detection subnetwork),`
- `维度 (Dimension)`
- `降维 (Dimension reduction)`
- `直接定位 (Direct location)`
- `判别器 (Discriminators)`
    - `损失 (loss)`
    - `训练方法 (training method)`
    - `生成对抗 (generative adversarial)`
- `分布 (Distributions)`
- `DISTRIBUTIONS 工具`
- `Glorot`
- `He`
- `正态分布 (normal distribution)`
- `分布 (Distribution)`
- `猫狗大战 (Dogs vs. Cats)`
- `丢弃 (Dropout)`
- `双子网络 (Dual-Subnet Network)`

## E
- `即时模式 (Eager)`
- `Jupyter 编辑模式 (Edit mode, Jupyter)`
- `环境安装 (Environment installation)`
    - `Ubuntu 环境`
- `Jupyter`
    - `Windows 环境`
    - `Jupyter`

## F
- `更快的 (Faster)`
- `快速 (Fast)`
- `特征提取 (Feature extraction)`
    - `骨干网络 (backbone)` 308
    - `CNN` 293
- `特征 (Feature)`
    - `特征图 (Feature map)`
    - `N-ASPP`
    - `区域提议 (region proposal)`
    - `感兴趣区域 (regions of interest)`
    - `RM`
    - `单阶段多框检测 (single shot multibox)`
    - `YOLO` 参见`You Only Look Once (YOLO)`
- `特征金字塔网络 (Feature pyramid networks)`
- `特征恢复 (Feature recovery (FR))`
- `细粒度特征 (Fine-grained features)`
- `焦点 (Focal)`
- `去雾 (Fog removal)`
- `FPNs` 参见`特征金字塔网络 (FPNs)`
- `全连接 (Fully connected)`
- `全连接神经网络 (Fully connected neural network)`
- `函数模型 (Functional model), in`

## G
- `生成对抗网络 (Generative adversarial network)`
    - `生成器和判别器 (generator and discriminator)`
    - `损失 (loss)`
    - `训练 (training)`
    - `判别器 (discriminator)`
    - `生成器 (generator)`
- `生成器 (Generators)`
    - `损失 (loss)` 274
    - `训练方法 (training method)`
    - `生成对抗 (generative adversarial)`
- `GitHub`
    - `下载源 (download source)`
    - `打开并运行 (open and run)`
- `VAE 模型`
    - `Glorot 初始化 (Glorot initialization)` 23–125
    - `基于梯度的优化 (Gradient-based optimization)`
    - `梯度下降 (Gradient descent)` 17
    - `梯度 (Gradient)`
    - `图形单元 (Graphic units)`
    - `显卡 (Graphics card)`

## H
- `去雾 (Haze removal)`
- `He 初始化 (He initialization)` 25–26
- `隐藏的 (Hidden)` 27–29
- `高分辨率 (High-resolution)`
- `直方图 (Histograms)`
    - `直方图工具 (HISTOGRAM tool)`
    - `Glorot`
    - `He`
    - `正态分布 (normal distribution)`
    - `房价预测 (House price-prediction)`
    - `HParams`
    - `精度范围 (with accuracy range)`
    - `平行坐标 (with Parallel Coordinates)`
    - `特定的 (specific)`
    - `散点图 (Scatter Plot)`
- `人脸识别 (Human face recognition)`

## I
- `图像 (Image)`
- `图像 (Image)`
- `图像增强 (Image enhancement)` 220
- `ImageNet 大规模视觉识别 (Image Large Scale Recognition)`
- `图像生成 (Image production)`
- `图像 (Image)`
- `图像到图像 (Image-to-image)`
- `图像变换 (Image transformations)`
- `Inception 块 (Inception blocks)`
    - `原生 inception (Naïve inception)`
    - `Keras`
    - `TensorFlow`
- `输入 (Input)` 28–29
- `实例 (Instance)`
- `编码 (Integer-encoding)` 63
- `集成环境 (Integrated environments)`
- `交并比 (Intersection over union)` 318–1

## J
- `Jensen–Shannon 散度 (Jensen–Shannon divergence (JS))`
- `Jupyter`
    - `键盘 (keyboard)`
    - `导航 (navigation)`
    - `项目 (project)`
    - `Ubuntu`
    - `Windows`

## K
- `内核 (Kernel)`
- `快捷键 (Keyboard shortcuts)`
- `Keras` 25
- `Keras` 225
- `函数 (functional)`
- `keras.callbacks.TensorBoard`
- `keras.Sequential`
- `K-means 聚类 (K-means clustering)`
- `Kullback–Leibler (KL)` 260

## L
- `潜的 (Latent)`
- `学习 (Learning)`
- `线性 (Linear)`
- `线性回归 (Linear regression)`
- `Lipschitz 性 (Lipschitz)`
- `对数损失 (Log loss)`
- `损失 (Loss)` 41
    - `自定义 API 和高级 Keras API 的` 278
    - `生成对抗 (generative adversarial)` 274
    - `多类别分类 (multi-category classification)`
    - `神经 (neural)`
    - `变分自动编码器 (variational auto-encoder)` 248
    - 316

## M
- `机器学习 (Machine learning)` 57–58
- `平均误差 (Mean absolute error)`
- `平均精度 (Mean precision)`
- `均方误差 (Mean squared error)`
- `合并 (Merge)`
- `指标 (Metric)`
    - `自定义 API 和高级 Keras API 的`
- `微软认知工具包 (Microsoft Cognitive Toolkit)`
- `MNIST 手写数字` 243
- `model.summary()`
- `动量 (Momentum)`
- `Jupyter 鼠标导航 (Mouse navigation, Jupyter)`
- `多分类 (Multi-category classification)`
    - `损失 (loss)`
    - `网络 (network)`
- `多类分类 (Multiclass classification)`
- `多尺度映射 (Multiscale mapping)`
- `多尺度预测 (Multiscale prediction),`
- `多尺度 (Multi-scale)`

## N
- `原生 inception (Naïve inception)`
- `窄空洞金字塔池化 (Narrow Atrous Pyramid Pooling (N-ASPP))`
- `网络 (Network)`
- `网络 (Network)`
- `神经网络 (Neural network)`
    - `架构 (architecture)`
    - `历史 (history)`
    - `房价预测 (house price-prediction)`
    - `构建训练网络 (building and training network)`
    - `数据集 (dataset)`
    - `显示训练 (display training)`
    - `超参数 (hyperparameters)`
    - `Kaggle`
    - `美国国王县房价 (House Sales in King County, USA)`
    - `过拟合 (overfitting)`
    - `原理 (principle)`
    - `问题 (problems)` 169–171
    - `可视化 (visualization)`
    - `可视化训练 (visualizing training)`
    - `训练与测试 (training and test)`
    - `训练 (training)`
    - `迁移学习 (transfer learning)` 参见`迁移学习`
    - `类型 (types)`
    - `隐藏 (hidden)`
    - `输入 (input)`
    - `输出 (output)`
- `非极大值抑制 (Non-maximum suppression (NMS))`
- `正态分布 (Normal distribution)`
    - `初始化 (initialization)`
    - `变分自动编码器 (variational auto-encoder)`
- `归一化过程 (Normalization process)`
    - `批 (batch)` 291
    - `神经网络 (neural network)`
    - `验证 (verification)`
    - `混淆矩阵 (confusion matrix)`
    - `数据 (data)`

## O
- `物体 (Object)`
- `块 (block)`
- `边界框 (bounding box)`
- `卷积神经 (convolutional neural)`
    - `更快的 (faster)`
    - `快速 (fast)`
    - `特征金字塔 (feature pyramid)`
    - `单阶段多框检测 (single shot multibox detector)`
    - `网络架构 (network architectures)`
    - `选择性搜索 (selective search)` 288
- `偏移 (offset)`
- `独热编码 (One-hot encoding)`
- `优化 (Optimization)` 41
- `输出 (Output)` 28–29
- `过拟合 (Overfitting)`
    - `丢弃 (dropout)`
    - `缩小尺寸 (reduce the size of)`
    - `权重 (weight)`

## P
- `参数线性整流单元 (Parametric rectified linear unit (PReLU))`
- `PASCAL 视觉对象类别 2007`
- `峰值噪比 (Peak signal-to-noise ratio)`
- `宝可梦战斗预测 (Pokémon combat prediction)`
    - `架构 (architecture)`
    - `流程图 (flowchart)`
    - `宝可梦大针虫洞 (Pokémon-Weedle's cave)`
- `池化 (Pooling)` 147
- `预训练 (Pre-trained)`
    - `Keras`
    - `TensorFlow`
    - `迁移学习 (transfer learning)` 参见`迁移学习`
- `PyCharm`
    - `帮助 (help)`
    - `快捷键 (keyboard)`
    - `项目 (project)`
    - `执行 (execution)`
    - `Python`
    - `主题 (theme)`
    - `Python`
    - `扩展 (extension)`
    - `Ubuntu`
    - `Windows`

## R
- `重建 (Reconstruction)` 249
- `修正线性单元 (Rectified linear unit (ReLU))` 202
- `递归 (Recurrent)`
    - `数据处理, Keras`
    - `深度卷积 (Deep convolutional)`
    - `深度学习 (Deep learning)`
    - `深度学习 GPU 训练系统 (Deep Learning GPU Training System)`
    - `DeepLearning4J`
    - `深度神经网络 (Deep neural networks)` 118
    - `检测子网络 (Detection subnetwork),`
    - `维度 (Dimension)`
    - `降维 (Dimension reduction)`
    - `直接定位 (Direct location)`
    - `判别器 (Discriminators)`
    - `损失 (loss)`
    - `训练方法 (training method)`
    - `生成对抗 (generative adversarial)`
- `分布 (Distributions)`
    - `DISTRIBUTIONS 工具`
- `Glorot`
- `He`
- `正态分布 (normal distribution)`
- `分布 (Distribution)`
    - `猫狗大战 (Dogs vs. Cats)`
- `丢弃 (Dropout)`
- `双子网络 (Dual-Subnet Network)`

## S
- `相同 (Same)`
- `标量 (Scalars)`
- `语义 (Semantic)`
- `半监督学习 (Semi-supervised learning)`
- `Sigmoid` 17
- `Sigmoid 交叉熵 (Sigmoid cross-entropy)`
- `单层神经网络 (Single-layer neural)`
- `单阶段多框检测 (single shot multibox)` 302–329
- `挤压-激励 (Squeeze-Excitation (SE))`
- `静态 (Static)`
- `随机梯度下降 (Stochastic gradient descent (SGD))`
- `结构相似性 (Structural similarity)`
- `监督学习 (Supervised learning)`
- `支持向量机 (Support vector machine)` 285

## T
- `tanh`
- `优点 (advantages)`
- `回调 (callback)`
- `缺点 (disadvantages)`
- `图形 (graph)`
- `超参数 (hyperparameter)`
- `测试数据 (Test data, neural)`
- `迁移 (Transfer)`
    - `训练 (training)`
- `TensorFlow`
    - `TensorBoard`
    - `单元 (processing units)`

## U
- `Ubuntu`
- `Jupyter`
- `无监督学习 (Unsupervised learning)`
- `上采样 (Upsampling)`
- `use_backend()`

## V
- `VAE 模型` 参见`变分自动编码器 (VAE) 模型`
- `验证数据 (Validation data, neural)`
- `有效填充 (Valid padding)`
- `梯度消失 (Vanishing gradient)` 118–121
- `变分自动编码器 (Variational auto-encoder (VAE))` 参见`自动编码器 (AE) 模型`
    - `自动编码器 (auto-encoder)`
    - `二交叉熵 (binary cross-entropy)`
    - `概念 (conceptual)`
    - `create_vae_model` 244
    - `构建和 (building and)`
    - `创建辅助 (creating helper)`
    - `MNIST 手写数字`
    - `项目 (project)`
    - `源 (source)`
    - `可视化 (visualization)`
    - `损失 (loss)` 248
    - `重建 (reconstruction)` 249
    - `采样 (sampling)`
- `Virtualenv` xv
- `可视化工具 (Visualization tools)`
    - `分布 (The distributions)`
    - `直方图 (The histograms)`
    - `图像 (The images)`
    - `文本 (The text)`

## W
- `Wasserstein`
- `带梯度惩罚的瓦瑟斯坦生成对抗网络 (Wasserstein generative adversarial network with gradient penalty)` 272
    - `CelebA`
    - `目录和 (directory and)`
    - `训练后生成的图像 (generated face images after training)`
    - `项目 (project)`
    - `损失 (loss)`
    - `源 (source)`
    - `训练 (training)` 279
    - `可视化 (visualization)`
- `权重 (Weight)`
- `权重初始化 (Weight initialization)`
    - `He`
    - `损失 (loss)`
    - `正态分布 (normal distribution)`
    - `验证 (verification)`
    - `Xavier 或 Glorot (Xavier or Glorot)` 123–125
- `权重 (Weight)`
- `Windows`
- `Jupyter`

## X
- `Xavier 初始化 (Xavier initialization)`

## Y
- `You Only Look Once`
    - `锚点 (anchor)`
    - `数据 (data)`
    - `数据 (data)`
    - `目录和 (directory and)`
    - `用于...的超参数 (hyperparameters for)`
    - `交并比 (intersection over)`
    - `最后层卷积 (last convolutional)`
    - `加载 (loading)`
    - `路径 (path)`
    - `源 (source)` 311
    - `虚拟 (virtual)`

## Z
- `零填充 (Zero padding)`
