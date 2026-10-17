
在`Raspi`等边缘设备上运行这些模型的能力为 IoT 应用、自主系统和实时监控解决方案开启了无限可能。它能够降低延迟、提高隐私性，并能够在连接受限的环境中运行。

正如我们所见，即使边缘设备存在计算限制，在准确性和速度方面仍然可以取得令人印象深刻的结果。调整模型参数（如输入尺寸和 alpha 值）的灵活性允许进行精调以满足特定的项目需求。

展望未来，边缘 AI 和图像分类领域将继续快速演进。模型压缩技术、硬件加速以及更高效的神经网络架构的进步，有望进一步扩展边缘设备在计算机视觉任务中的能力。

该项目为更复杂的计算机视觉应用奠定了基础，并鼓励对边缘 AI 和 IoT 的奇妙世界进行进一步探索。无论是工业自动化、智能家居应用还是环境监测，这里涵盖的技能和概念为各种创新项目提供了一个坚实的起点。

## 资源

* [数据集示例](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/tree/main/IMG_CLASS/dataset)
* [在 Raspi 上设置测试 Notebook](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/IMG_CLASS/notebooks/setup_test.ipynb)
* [在 Raspi 上进行图像分类 Notebook](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/IMG_CLASS/notebooks/10_Image_Classification.ipynb)
* [在 CoLab 使用 CNN 分类 Cifar-10 数据集](https://colab.research.google.com/github/Mjrovai/UNIFEI-IESTI01-TinyML-2022.1/blob/main/00_Curse_Folder/2_Applications_Deploy/Class_16/cifar_10/CNN_Cifar_10_TFLite.ipynb#scrollTo=iiVBUpuHXEtw)
* [Cifar 10 - 在 Raspi 上进行图像分类](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/IMG_CLASS/notebooks/20_Cifar_10_Image_Classification.ipynb)
* [Python 脚本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/tree/main/IMG_CLASS/python_scripts)
* [Edge Impulse 项目](https://studio.edgeimpulse.com/public/510251/live)

# 目标检测

![DALL·E prompt - A cover image for an ‘Object Detection’ chapter in a Raspberry Pi tutorial, designed in the same vintage 1950s electronics lab style as previous covers. The scene should prominently feature wheels and cubes, similar to those provided by the user, placed on a workbench in the foreground. A Raspberry Pi with a connected camera module should be capturing an image of these objects. Surround the scene with classic lab tools like soldering irons, resistors, and wires. The lab background should include vintage equipment like oscilloscopes and tube radios, maintaining the detailed and nostalgic feel of the era. No text or logos should be included.](img/file955.jpg)

*DALL·E prompt - A cover image for an ‘Object Detection’ chapter in a Raspberry Pi tutorial, designed in the same vintage 1950s electronics lab style as previous covers. The scene should prominently feature wheels and cubes, similar to those provided by the user, placed on a workbench in the foreground. A Raspberry Pi with a connected camera module should be capturing an image of these objects. Surround the scene with classic lab tools like soldering irons, resistors, and wires. The lab background should include vintage equipment like oscilloscopes and tube radios, maintaining the detailed and nostalgic feel of the era. No text or logos should be included.*

## 概述

在对图像分类进行探索的基础上，我们现在将转向一个更高级的计算机视觉任务：目标检测。图像分类是为整张图像分配单个标签，而目标检测通过识别和定位单张图像中的多个物体更进一步。这种能力开启了许多新的应用和挑战，特别是在边缘计算和像树莓派这样的 IoT 设备上。

目标检测结合了分类和定位任务。它不仅能确定图像中存在哪些物体，还能通过例如在物体周围画边界框来精确确定它们的位置。这种增加的复杂性使目标检测成为理解视觉场景更强大的工具，但也需要更复杂的模型和训练技术。

# 引言

在边缘 AI 中，由于我们处理的计算资源受限，实现高效的目标检测模型至关重要。我们在图像分类中面临的挑战——平衡模型大小、推理速度和准确性——在目标检测中被放大了。然而，回报也更加显著，因为目标检测能够实现更细、更详细的视觉数据分析。

目标检测在边缘设备上的某些应用包括：

1. 监控与安全系统
2. 自主车辆和无人机
3. 工业质量控制
4. 野生动物监测
5. 增强现实应用

当我们开始接触目标检测时，将在之前图像分类中探索的概念和技术的基础上进行。我们将检查为效率设计的常用目标检测架构，例如：

* 单阶段检测器（Single Stage Detectors），如`MobileNet`和`EfficientDet`
* `FOMO`（Faster Objects, More Objects），以及
* `YOLO`（You Only Look Once）。

> 要了解更多关于目标检测模型的信息，请参考教程 [深度学习目标识别入门](https://machinelearningmastery.com/object-recognition-with-deep-learning/)。

我们将使用以下工具探索这些目标检测模型：

* `TensorFlow Lite Runtime`（现已改为 [LiteRT](https://ai.google.dev/edge/litert)）
* `Edge Impulse Linux Python SDK`
* `Ultralitics`

![](img/file956.png)

在整个实验过程中，我们将涵盖目标检测的基础以及它与图像分类的区别。我们还将学习如何使用从零开始的数据集来训练、微调、测试、优化和部署流行的目标检测架构。

## 目标检测基础

目标检测建立在图像分类的基础上，但大大扩展了其能力。要理解目标检测，首先必须识别它与图像分类的关键区别：

### 图像分类 vs 目标检测

**图像分类**：

* 为整张图像分配单个标签
* 回答问题：“这张图像的主要物体或场景是什么？”
* 输出整张图像的单个类别预测结果

**目标检测**：

* 识别并定位图像中的多个物体
* 回答问题：“这张图像中有哪些物体？它们在哪里？”
* 输出多个预测结果，每个结果包含一个类别标签和一个边界框（bounding box）

为了直观地展示这种差异，让我们来看一个例子：

![](img/file957.jpg)

此图说明了关键区别：图像分类为整张图像提供单个标签，而目标检测识别图像中的多个物体、它们的类别及其位置。

### 目标检测的核心组件

目标检测系统通常由两个主要部分组成：

1. **物体定位 (Object Localization)**：该组件识别物体在图像中的位置。它通常输出边界框，即包含每个检测物体的矩形区域。
2. **物体分类 (Object Classification)**：该组件确定每个检测物体的类别或种类，与图像分类类似，但应用于每个定位区域。

### 目标检测的挑战

目标检测面临比图像分类更多的许多挑战：

* **多个物体**：图像可能包含多个类别、尺寸和位置的物体。
* **尺度变化**：物体在图像中以不同的大小出现。
* **遮挡**：物体可能会被部分隐藏或重叠。
* **背景干扰**：从复杂的背景中区分物体可能是具有挑战性的。
* **实时性能**：许多应用需要实时性能。

### 目标检测的方法

有两种主要方法：

1. **两阶段检测器 (Two-stage detectors)**：它们首先提取感兴趣区域，然后对每个区域进行分类。示例包括`R-CNN`和`Fast R-CNN`。
2. **单阶段检测器 (Single-stage detectors)**：它们在一次通过中预测边界框和类别概率。示例包括`YOLO`、`SSD`和`FOMO`。

### 评估指标

目标检测使用的指标与分类不同：

* **交并比 (IoU)**：衡量预测值与真实值（ground truth）之间的重叠程度。
* **平均精度 (mAP)**：结合所有类的精确率和召回率。
* **每帧率 (FPS)**：衡量速度。

## 预训练模型概述

正如我们在引言所示，给定一张图像或视频流，目标检测模型可以识别可能存在的内容并提供它们位置的信息。

> 你可以通过访问 [Object Detection](https://mediapipe.google.com/studio/) 在线测试某些模型。

在实验的第一部分，我们将关注 300×300 的`SSD-Mobilenet V1`模型，并将其与 320×320 的`EfficientDet-lite`进行比较。两者都是使用`COCO`数据集训练的。

![](img/file958.png)

## 设置 TFLite 环境

我们应该确认上一个上上手实验“图像分类”中完成的步骤，如下：

* 更新树莓派
* 安装所需的库
* 设置虚拟环境（可选但推荐）
  * 安装`TensorFlow Lite Runtime`
  * 安装额外的 Python 库（在环境内部）

### 创建工作目录

考虑到我们在上一个实验中创建了`Documents/TFLITE`文件夹，现在为这个目标检测实验创建特定的文件夹：

## 推理与后处理

让我们开始一个新的[notebook](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OBJ_DETEC/notebooks/SSD_MobileNetV1.ipynb)，遵循在图像上检测物体的所有步骤：

导入所需的库：

```
```

加载 TFLite 模型并分配张量：

```
```

获取输入和输出张量：

```
```

**输入详细信息 (Input details)** 将告诉我们如何向模型输入图像。`(1, 300, 300, 3)`的形状配合`uint8`数据类型告诉我们，应该输入一个非归一化的（像素值范围从 0 到 255）、维度为 (300×300×3) 的图像，由一个（批维度: 1）输入。

`output details`不仅包含标签（“classes”）和概率（“scores”），还包含边界框（boxes）相对于物体在图像上位置的窗口位置，以及检测到的物体数量（`num_detections`）。输出详情还告诉我们，模型可以检测图像中`maximum of 10 objects`。

![](img/file959.png)

因此，对于上面的示例，使用与`Image Classification Lab`相同的猫图片来寻找输出结果，我们有`76% probability`的概率找到了一个`class ID 为 16`的对象，该对象所在的区域由`bounding box of [0.028011084, 0.020121813, 0.9886069, 0.802299]`界定。这四个数字与`ymin`、`xmin`、`ymax`和`xmax`（框坐标）有关。

考虑到`y`从顶部（`ymin`）到底部（`ymax`），而`x`从左侧（`xmin`）到右侧（`xmax`），实际上我们拥有了左上角和右下角的坐标。有了这两个边缘并知道图片的形状，我们可以在物体周围画一个矩形，如下图所示：

![](img/file960.png)

接下来，我们应该找到类 ID 等于 16 的含义。打开`coco_labels.txt`文件，作为一个列表，每个元素都有一个关联的索引，通过检查索引 16，我们如预期的那样得到了`cat`。概率是分数返回的值。

现在让我们上传一些带有多个物体的图像进行测试。

```
```

```
```

![](img/file961.png)

根据输入详情，让我们对图像进行预处理，更改其形状并扩展其维度：

```
```

新的`input_data`形状为`(1, 300, 300, 3)`，数据类型为`uint8`，这符合模型的预期。

使用`input_data`，让我们运行解释器，测量延迟并获取输出：

```
```

在约为 800 ms 的延迟下，我们可以得到 4 个不同的输出：

```
```

通过快速检查，我们可以看到模型检测到 2 个得分超过 0.5 的物体：

```
```

![](img/file962.png)

我们还可以可视化这些结果：

```
```

![](img/file963.png)

### EfficientDet

EfficientDet 在技术上并不是一个 SSD（单次检测器）模型，但它与 SSD 以及其他目标检测架构有很多相似之处，并基于它们构建：

1. **EfficientDet**：
   * 由 Google 研究人员于 2019 年开发
   * 使用`EfficientNet`作为骨干网络
   * 采用了一种新的双向特征金字塔网络（`BiFPN`）
   * 它使用复合尺度（compound scaling）来高效扩展骨干网络和目标检测组件。
2. **与 SSD 的相似之处**：
   * 两者都是单阶段检测器，这意味着它们在单次前向传播中完成物体定位和分类。
   * 两者都使用多尺度特征图来检测不同的物体。
3. **主要区别**：
   * **骨干网络 (Backbone)**：SSD 通常使用`VGG`或`MobileNet`，而 EfficientDet 使用`EfficientNet`。
   * **特征融合**：SSD 使用简单的特征金字塔，而 EfficientDet 使用更先进的`BiFPN`。
   * **缩放方法**：EfficientDet 为网络的所有组件引入了复合尺度。
4. **EfficientDet 的优势**：
   * 通常比 SSD 和许多其他目标检测模型具有更好的准确性与效率权衡。
   * 更灵活的缩放允许产生具有不同尺寸-性能权衡的模型族。

虽然 EfficientDet 不是一个 SSD 模型，但它可以被看作单阶段检测架构的演进，结合了更先进的技术来提高效率和准确性。在使用 EfficientDet 时，我们可以预期与 SSD 类似的输出结构（例如边界框和类别分数）。

> 在 GitHub 上，你可以找到另一个 [notebook](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OBJ_DETEC/notebooks/SSD_EfficientDet.ipynb)，探索我们使用 SSD MobileNet 做过的 EfficientDet 模型。

## 目标检测项目

现在，我们将开发一个从数据收集到训练和部署的完整图像分类项目。正如我们在图像分类项目中所做的那样，经过训练和转换的模型将用于推理。

我们将使用相同的数据集训练 3 个模型：SSD-MobileNet V2、FOMO 和 YOLO。

### 目标

所有的机器学习项目都需要从一个目标开始。假设我们在一个工业设施中，必须对`wheels`和特殊的`boxes`进行分类和计数。

![](img/file964.jpg)

换句话说，我们应该执行多标签分类，每张图像可能有三类：

* 背景（Background）
* 箱（Box）
* 轮（Wheel）

### 数据收集

一旦确定了机器学习项目目标，最关键的步骤就是收集数据集。我们可以使用手机、树莓派或混合方式创建原始数据集（无标签）。让我们使用树莓派上的简单 Web 应用在浏览器中查看`QVGA (320 x 240)`采集的图像。
