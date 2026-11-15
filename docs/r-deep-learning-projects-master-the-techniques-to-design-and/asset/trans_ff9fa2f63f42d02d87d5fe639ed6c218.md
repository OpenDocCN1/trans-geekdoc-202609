

## 深度学习如何成为一种最先进的解决方案？

- 雷达系统利用来自其他交通参与者、行人或障碍物的距离信息
- 计算机视觉算法从摄像头中识别交通标志、交通信号灯和其他地标，并提供预先通知
- 算法驱动的软件分析所有感官数据，结合来自其他来源的输入，并控制转向和制动等操作，模拟人类感知周围环境并做出决策的方式

可以看到，强大的目标识别对于实现驾驶自动化至关重要。为避免事故并确保安全，有必要关注周围环境、交通标志和信号灯。通常来说，自动驾驶汽车中的目标识别可以总结为四项任务：

- 目标检测，例如障碍物、行人、交通标志和信号灯。
- 目标识别与分类。例如，如果前置摄像头捕获的图像中检测到交通信号灯，则将其标记为（红、黄、绿和关闭）。然后，我们将交通参与者分为自行车、摩托车、汽车、卡车和公共汽车，当然还要对交通标志进行分类（本章的主要讨论重点）。
- 目标定位，将地面级图像映射到航空图像。
- 运动预测，例如，理解目标的速度或根据其姿态估计行人的行为和意图。

在过去二十年中，各种机器学习算法已被应用于解决智能车辆中的目标识别问题。

例如，在《基于运动与外观模式的行人检测》（Viola et al.，发表于《国际计算机视觉杂志》，63(2)）中，采用了 AdaBoost（自适应增强的缩写，按顺序纠正分类错误）分类器来检测行走中的行人。

在《面向人体检测的定向梯度直方图》（Dalal 和 Triggs，2005 年发表于 IEEE 计算机视觉与模式识别会议 (CVPR) 上），使用**定向梯度直方图（HOG）**技术提取了高效特征，并将其输入**支持向量机（SVM）**分类器进行人体检测。此后，开发了诸如梯度场 HOG (GF-HOG) 等更复杂的变体，以及其他更复杂的特征提取方法。举几例，我们有分区 + 投影、投影 + HOG，等等。

常规目标识别方法（显式特征提取 + 机器学习分类）严重依赖手工制作的特征，例如 HOG 的梯度方向直方图、**加速稳健特征（SURF）**中的局部关键点，或**尺度不变特征变换（SIFT）**。尽管它们在某些任务中表现良好，但设计这些特征描述子很困难，需要大量的手动调整和实验。

还记得上一章关于手写数字分类的内容吗，我们求助于 CNN。它首先推导低级表示，如局部边缘和曲线，然后通过一系列低级表示组合出更高级的表示，如整体形状和轮廓。我们还得出结论，CNN 非常适合利用强大且独特的特征。

事实上，许多解决方案已证明，CNN 能够高效地自动化特征提取，同时显著提升性能。例如，在《基于无监督多阶段特征学习的行人检测》（Sermanet et al.，2013 年发表于 IEEE 计算机视觉与模式识别会议（**Computer Vision and Pattern Recognition (CVPR）**）中，CNN 首次被引入行人检测问题。在《用于精确目标检测和语义分割的丰富特征层次结构》（Girshick et al.，2014 年发表于 IEEE 计算机视觉与模式识别会议 (CVPR) 上），提出了一种区域 CNN 变体模型以提高性能。如今，许多最先进的目标识别方法都涉及深度学习技术，特别是 CNN。一个很好的见证就是它们在自动驾驶汽车的 KITTI 视觉基准排行榜顶部位置的普遍性（`http://www.cvlibs.net/datasets/kitti/eval_object.php?obj_benchmark=2d`）。

希望所有这些案例都能让你对 CNN 及其为智能车辆提供更好目标识别解决方案的能力感到兴奋。

我们还在等什么？让我们继续我们的项目，交通标志识别，因为这是自动驾驶汽车中最重要的主题之一！

## 使用 CNN 进行交通标志识别

和往常一样，我们首先探索德国交通标志识别基准（GTSRB）数据集，网址为 http://benchmark.ini.rub.de/?section=gtsrb&subsection=dataset。

### 开始探索 GTSRB

GTSRB 数据集由神经信息学研究所的实时计算机视觉研究小组编制并慷慨发布，最初用于交通标志单图像分类竞赛。它包含 39,209 张标记图像的训练集和 12,630 张未标记图像的测试集。训练数据集包含 43 个类别——43 种交通标志。我们将遍历所有类别，并为每个类别展示几个样本。

数据集可通过 http://benchmark.ini.rub.de/Dataset/GTSRB_Final_Training_Images.zip 下载（位于页面的 Downloads | Training dataset 部分）。解压下载的文件，会有一个名为 Images 的文件夹，包含 43 个文件夹（00000、00001 一直到 00042）；它们代表 43 个图像类别。这些图像的形式如下：

- 图像文件为 PPM（可移植位图的缩写）格式。
- 每个类别的图像数量从 210 到 2250 不等。因此这是一个不平衡的多类分类问题。
- 每张图像包含一个交通标志。
- 图像尺寸不统一，范围从 15*15 到 250*250 像素，图像不一定是正方形。
- 图像在实际标志周围包含高达 10% 的边框。因此标志不一定位于图像中心。

让我们先在 00000 文件夹中绘制一个样本 00000_00002.ppm。

我们使用 [pixmap 包](https://cran.r-project.org/web/packages/pixmap) 来读取 PPM 文件：

```
> library('pixmap')
> image <- read.pnm('GTSRB/Final_Training/Images/00000/00000_00002.ppm', cellres=1)
```

现在我们得到一个 pixmapRGB 对象，带有 red、green 和 blue 属性（分别是三个通道的像素），以及 size（图像的宽度和高度）。我们可以按如下方式访问 red、green 和 blue 通道：

```
> red_matrix <- matrix(image@red, nrow = image@size[1], ncol = image@size[2])
> green_matrix <- matrix(image@green, nrow = image@size[1], ncol = image@size[2])
> blue_matrix <- matrix(image@blue, nrow = image@size[1], ncol = image@size[2])
```

我们分别可视化原始图像及其三个通道：

```
> plot(image, main=sprintf("Original"))
> rotate <- function(x) t(apply(x, 2, rev))
> par(mfrow=c(1, 3))
> image(rotate(red_matrix), col = grey.colors(255), main=sprintf("Red"))
> image(rotate(green_matrix), col = grey.colors(255), main=sprintf("Green"))
> image(rotate(blue_matrix), col = grey.colors(255), main=sprintf("Blue"))
```

请注意，这里我们复用了上一章定义的 rotate 函数，以便更好地查看图像。这是一张原始图像：

![](img/da8fb67f2acf661518076e08b6ffd9b9_67_0.png)

以下图像分别显示了 red、blue 和 green 通道的输出：

![](img/da8fb67f2acf661518076e08b6ffd9b9_68_0.png)

这是一个 20 km/h 限速标志。

我们现在可以定义以下函数，遍历 43 个交通标志类别，并为每种类型显示三个样本：

```
> plot_samples <- function(training_path, class, num_sample){
>     classes <- c("Speed limit (20km/h)", "Speed limit (30km/h)",
>                 "Speed limit (50km/h)", "Speed limit (60km/h)",
>                 "Speed limit (70km/h)", "Speed limit (80km/h)",
>                 "End of speed limit (80km/h)",
>                 "Speed limit (100km/h)", "Speed limit (120km/h)",
>                 "No passing",
>                 "No passing for vehicles over 3.5 metric tons",
>                 "Right-of-way at the next intersection",
>                 "Priority road", "Yield", "Stop", "No vehicles",
>                 "Vehicles over 3.5 metric tons prohibited",
>                 "No entry", "General caution", "Dangerous curve to the left", "Dangerous curve to the right",
>                 "Double curve", " Bumpy road", "Slippery road",
>                 "Road narrows on the right", "Road work",
>                 "Traffic signals", "Pedestrians", "Children crossing", "Bicycles crossing",
>                 "Beware of ice/snow",
>                 "Wild animals crossing",
>                 "End of all speed and passing limits",
>                 "Turn right ahead", "Ahead only",
>                 "Turn left ahead", "Ahead only",
```
