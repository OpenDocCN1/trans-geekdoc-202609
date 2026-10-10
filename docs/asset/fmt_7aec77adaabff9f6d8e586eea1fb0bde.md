
```python
gt_bb[:, :, :, 1] + gt_bb[:, :, :, 3] / 2.0)
gt_bb = tf.transpose(gt_bb, [1, 2, 3, 0])
pred_bb = tf.stack(
pred_bb[:, :, :, 0] - pred_bb[:, :, :, 2] / 2.0,
pred_bb[:, :, :, 1] - pred_bb[:, :, :, 3] / 2.0,
pred_bb[:, :, :, 0] + pred_bb[:, :, :, 2] / 2.0,
pred_bb[:, :, :, 1] + pred_bb[:, :, :, 3] / 2.0)
pred_bb = tf.transpose(pred_bb, [1, 2, 3, 0])
area = tf.maximum(0.0,
tf.minimum(gt_bb[:, :, :, 2], pred_bb[:, :, :, 2]) - 
tf.maximum(gt_bb[:, :, :, 0], pred_bb[:, :, :, 0]), 0) * 1)
intersection_area = area[:] * \
ggt_bb_area = (gt_bb[:, :, :, 2] - gt_bb[:, :, :, 0]) * \
(gt_bb[:, :, :, 3] - gt_bb[:, :, :, 1]) / 2
pred_bb_area = (pred_bb[:, :, :, 2] - pred_bb[:, :, :, 0]) * \
(pred_bb[:, :, :, 3] - pred_bb[:, :, :, 1]) / 2
union_area = tf.maximum(gt_bb_area + pred_bb_area - intersection_area, 1e-10)
iou = tf.clip_by_value(intersection_area / union_area, 0.0, 1.0)
return iou
```

将真值和预测边界框进行堆叠。然后计算面积，同时处理负面积的情况。当边界框坐标不正确时可能会出现负面积。框的右侧坐标可能出现在左侧坐标左。由于边界框的结构没有保持，负面积会发生。在计算并集和交集面积后，进行最终的 IoU 计算，即真值与预测区域重叠面积占总面积的比例。IoU 的计算可以通过训练定位问题的算法来实现。

## 平均平均精度

`mAP` 用于评估检测算法。`mAP` 指标是检测到的边界框的精确率（precision）和召回率（recall）的乘积。`mAP` 的值范围从 0 到 100。数值越高越好。`mAP` 可以通过分别计算每个类的平均精度（AP）来计算，然后对类别取平均值。只有当 `mAP` 高于 0.5 时，检测才被视为真正例。测试图像中的所有检测可以通过为每个类绘制检测/召回率曲线来合并。曲线下的最终面积可用于算法比较。`mAP` 是衡量网络灵敏性的良好标准，且不会产生许多误报。我们已经学习了数据集的评估算法。接下来，我们将查看定位任务的算法。

### 定位算法

定位算法是第 2 章图像分类和第 3 章图像检索中所学内容的扩展。在图像分类中，图像会通过几层 `CNN`（卷积神经网络）。`CNN` 的最后一层输出属于每个标签的概率值。这可以扩展到定位对象。我们将在接下来的章节中介绍这些思想。

### 使用滑动窗口进行定位

定位的一种直观方法是使用不同尺寸的裁剪图像进行预测。滑动窗口通过对图像进行裁剪并预测来实现。通过在图像上移动窗口，可以检测到物体。这种对图像的裁剪方法被称为滑动窗口。

- 这种方法在物体大小大于窗口时会漏掉目标。如果目标比窗口大，则需要使用多尺度。为了克服这个问题，我们将使用尺度空间。
- 另一个问题是移动窗口可能会导致漏检。在像素上移动窗口会导致大量的计算。为了避免这种情况，我们将在卷积层中引入技巧。

### 尺度空间概念

尺度空间是使用不同尺寸图像的概念。图像被缩小到较小尺寸，因此可以使用相同尺寸的窗口检测物体。图像可以调整大小。通过删除像素或插值来调整图像可能会留下伪影。图像是迭代地平滑和调整的。通过平滑和调整得到的图像是尺度。

窗口在每个尺度上滑动以对物体进行。运行多个尺度等同于使用更大的窗口运行图像。运行多个尺度的计算复杂度很高。可以通过权衡准确性来加速定位。复杂度使得该方案在生产环境中不可用。滑动窗口的想法可以通过全卷积实现来实现高效。

### 将全连接层训练为卷积层

滑动窗口的问题在于计算复杂度。这种复杂度是因为对每个窗口都进行了预测。深度学习特征已经在每个重叠区域进行了计算。重叠区域的特征计算是可以减少的。

### 滑动窗口的卷积实现

在这种技术中，不再是进行滑动，而是将最终目标制成某些深度所需的目标，并将一定数量的框作为窗口。Sermanet 等人（https://arxiv.org/pdf/1312.6229.pdf）使用了全卷积实现来解决滑动窗口的问题。以下是此类卷积实现的插图：

![](img/48c861eac4dc634fbf2a09fdbe884beb_128_0.png)

在示例的顶部，普通的分类被表示为全卷积层。在插图的下部，相同的内核被应用于更大的图像，最后产生 2x2 个输出而不是 1 个。最后一层表示了这些边界框的四个输出。使用预测的张量（volume）来提高预测可以提高效率，但边界框在精确定位上仍然存在问题。因此，滑动窗口是不必要的，在这里它解决了复杂性。长宽比不断变化，必须在多个尺度上观察。通过全卷积方法生成的边界框并不准确。额外的计算仅针对额外的区域进行。正如我们可以想象的，框进一步被限制为与训练时相同的框数量。接下来，我们将看到一种更准确地检测边界框位置的方法。

## 将定位视为回归问题

思考定位的一种基本方法是将问题建模为回归问题。边界框是四个数字，因此可以通过设置回归以直接的方式进行预测。我们还需要预测标签，这是一个分类问题。

有不同的参数可用来定义边界框。边界框通常有四个数字。其中一种表示方法是坐标的中心点加上边界框的高度和宽度。可以通过移除全连接层并将其替换为回归编码器来使用预训练模型。回归必须用 L2 损失进行正则化，该损失在面对离群值时表现差。L1 损失比 L1 更好（注：此处原文可能笔误，应为 L2）。将回归替换为平滑版本的正则化仅能带来微小的性能提升，而训练整个网络可以获得良好的准确性。这是训练时间和准确性之间的权衡。接下来，我们将看到使用卷积网络回归的不同应用。

### 将回归应用于其他问题

回归图像坐标适用于许多其他应用，例如姿态检测和特征点检测。姿态检测是在人体中寻找关节位置，如图所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_129_0.png)

在之前的图像中，检测到了头部、颈部、肩膀、脚踝和手等多个位置。这可以扩展到人体部位。我们学到的回归可以用于此应用。这里是特征点检测的示例：

![](img/48c861eac4dc634fbf2a09fdbe884beb_130_0.png)

特征点（fiducial points）是相对于眼睛、鼻子和嘴部位置的面部标记。找到这些标记对于基于脸的增强现实应用至关重要。脸上有更多标记，将在第 6 章“相似性学习”的人脸识别部分详细介绍。

## 将回归与滑动窗口结合

在滑动窗口方法或全卷积方法中，为每个窗口计算分类得分，以知道该窗口存在什么物体。与其预测每个窗口的分类得分来检测物体，每个窗口本身都可以用分类得分进行预测。将滑动窗口、尺度空间、全卷积和回归的所有思想结合起来可以比任何单一方法产生更优的结果。以下是各种网络使用回归方法在 ImageNet 数据集上实现的前五个定位错误率：

## 物体检测

## 第 4 章

![](img/48c861eac4dc634fbf2a09fdbe884beb_131_0.png)

前述图显示，网络越深，结果越好。VGG 使用了多尺度进行定位。这些收益归功于深层特征。ResNet 使用了回归编码器。边界边界框使用归一化坐标进行训练。可能会存在一些图像坐标之外的建议，因此在训练和推理时对其归一化。在下一节中，我们将更有效地处理检测问题。

## 检测物体

有几种物体检测的变体。这里讨论了带有物体检测的几种算法。

### 卷积神经网络区域 (R-CNN)

该系列的第一个工作是由 Girshick 等人（https://arxiv.org/pdf/1311.2524.pdf）提出的 CNN。它提出了一些框并检查真值（ground truth）。**区域搜索（Selective search）**被用于这些区域建议。区域搜索通过分组颜色/纹理来提出建议。它从像素开始并产生更高尺度的 blob。它产生大约 2000 个区域建议。这些建议被调整大小并通过如 AlexNet/VGG/Inception/ResNet 等标准 CNN。CNN 的最后一层使用 SVM 进行训练。通过收紧图像周围的框进一步改进。这里是 R-CNN 的架构：

![](img/48c861eac4dc634fbf2a09fdbe884beb_132_0.png)

编码器可以是深度学习模型的预训练模型。为训练数据的所有区域计算特征。存储特征，然后训练 SVM。接下来，边界框使用归一化坐标进行训练。

该方法的缺点是：

- 建议是由区域搜索生成的，因此必须进行多次推理，通常为 2000 次
- 需要训练多个分类器，这增加了参数数量
- 没有进行端到端训练

## Fast R-CNN

Fast R-CNN 由 Girshick 等人（https://arxiv.org/pdf/1504.08083.pdf）提出仅运行 CNN 推理，因此减少了计算。CNN 的输出被用于提议网络并选择边界框。它引入了一种名为感兴趣区域池化（ROI pooling）的技术。感兴趣区域池化获取 CNN 特征并根据区域对其池化。使用 CNN 推理后获得的特征被池化并选择区域，如下所示：

![](img/48c861eac4dc634fbf2a09fdbe884beb_133_0.png)

通过这种方法，执行了端到端训练，避免了多个分类器。注意 SVM 被 softmax 层取代，边界框回归器被边界框回归器所取代。仍然存在的缺点是区域搜索，它需要时间。

### Faster R-CNN

Faster R-CNN 由 Ren 等（https://arxiv.org/pdf/1506.01497.pdf）提出。Faster R-CNN 与 Fast R-CNN 方法的区别在于，Faster R-CNN 使用如 VGG 和 Inception 等架构的 CNN 特征来生成建议（proposals），而不是使用选择搜索（selective search）。CNN 特征被传递到区域建议网络（region proposal network）。滑动窗口通过特征层并将潜在的边界框和得分作为输出，同时结合几个直观的宽高比例，模型会输出边界框和得分：

![](img/48c861eac4dc634fbf2a09fdbe884beb_134_0.png)

Faster R-CNN 比 Fast R-CNN 快，因为它通过只计算一次特征来节省计算量。

# 单次多框检测器

SSD（Single shot multi-box）由所有方法中最快的方法提出的。该方法同时预测物体并寻找边界框。在训练期间，存在大量的负样本，因此需要进行硬负样本挖掘（hard-negative mining）来解决类别不平衡问题。CNN 的输出具有各种尺寸的特征。这些特征被传递到 3x3 卷积滤波器以预测边界框。

此步骤预测物体和边界框：

![](img/48c861eac4dc634fbf2a09fdbe884beb_135_0.png)

经 Liu 等人许可复制。

这些是可用于目标检测的算法，我们将在下一节中学习如何实现它们。

# 目标检测 API

Google 发布了在 COCO 数据集上训练的各种算法的预训练模型供公开使用。该 API 构建在 TensorFlow 之，用于构建、训练和部署目标检测模型。API 同时支持目标检测和定位任务。预训练模型的可用性能够对新数据进行微调并加快训练速度。这些不同的模型在速度和准确性之间存在权衡。

### 安装与设置

使用以下命令安装 Protocol Buffers (protobuf) 编译器。为 protobuf 创建一个目录并直接下载库：

```
mkdir protoc_3.3
cd protoc_3.3
get https://github.com/google/protobuf/releases/download/v3.3.0/protoc-3.3.0-linux-x86_64.zip
```

更改文件夹权限并解压内容，如下所示：

```
chmod 775 protoc-3.3.0-linux-x86_64.zip
unzip protoc-3.3.0-linux-x86_64.zip
```

Protocol Buffers (protobuf) 是 Google 一种语言无关、平台无关且可扩展的数据序列化机制。它支持多种语言，但 XML 要简单且快速得多。在 TensorFlow 中，模型通常导出为这种格式。人们可以定义一次数据结构，然后在多种语言中读取或写入。然后运行以下命令编译 protobufs。回到工作文件夹并从 https://github.com/tensorflow/models.git 克隆仓库，并将它们移动到以下文件夹：

```
git clone https://github.com/tensorflow/models.git
```

现在，使用以下代码将模型移动到研究文件夹：

```
cd models/research/
~/protoc_3.3/protoc object_detection/*.proto --python_out=.
```

TensorFlow 目标检测 API 使用 protobuf 导出模型权重和训练参数。通过以下命令将 TensorFlow、models 和 slim 目录添加到 PYTHONPATH：

```
export PYTHONPATH=../slim/
```

使用前一个命令添加到 python 路径仅对一次有效。下一次运行时，必须再次运行此命令。可以通过运行以下代码测试安装：

```python
python object_detection/builders/model_builder.py
```

此代码的输出如下：

Ran 7 tests in 0.22s

OK

可以从 https://github.com/tensorflow/models/master/research/object_detection/installation.md 获取更多关于安装的信息。现在安装完成了。

### 预训练模型

有几个预训练并供使用的模型。所有这些模型都是在 COCO 数据集上训练的，可用于检测 COCO 数据集中存在的物体，如人类和汽车。这些模型对于新任务（如交通检测）的迁移学习也很有用。这里显示了预训练模型表格，以及它们在 COCO 数据集上的相对速度和 mAP。名称中描述了使用不同 CNN 训练的算法：

| 模型名称 | 速度 | COCO mAP |
| :--- | :--- | :--- |
| ssd_mobilenet_v1_coco | fast | 21 |
| ssd_inception_v2_coco | fast | 24 |
| rcn_resnet101_coco | medium | 30 |
| faster_rcnn_resnet101_coco | medium | 32 |
| faster_rcnn_inception_resnet_v2_coco | slow | 37 |

根据需求，你可以从模型中进行选择。下载在其训练的 SSD 并进入工作目录进行解压，如下所示：

```
mkdir chapter4
cd chapter4
wget http://download.tensorflow.org/models/object_detection/ssd_mobilenet_v1_coco_1_06_2017.tar.gz
tar -xzv ssd_mobilenet_v1_coco_1_06_2017.tar.gz
```

### 使用 TensorBoard 监控损失和准确率

可以使用 TensorBoard 监控训练损失和准确率。使用以下命令运行 TensorBoard：

```
tensorboard --logdir=/home/ubuntu/Chapter04
```

训练和评估过程都可以在 TensorBoard 中可视化。

# 为自动驾驶汽车训练行人检测器

用于训练行人目标检测的数据集可以在 http://pascal.inralpes.fr/data/human/ 找到。检测行人的步骤可以在 https://github.com/diegocalca/machine-learning/blob/supervised/object.detection_tensorflow/simple.detection.ipynb 找到。用于训练交通标志检测器的数据集可以从 http://vision.ee.ethz.ch/timofter/traffic_signs/ 和 http://bitsd.ethz.ch/shareddata/ 处下载。对于自动驾驶汽车而言，图像中会有用于标记的类别：行人、汽车、摩托车和背景。当图像中没有出现任何类别时，必须检测出背景类。训练深度学习分类模型的假设是图像中至少会存在一个物体。通过添加背景类，我们解决了这个问题。神经网络还可以根据标签生成对象的边界框。

# YOLO 目标检测算法

最近的一种目标检测算法是“你一眼看”（YOLO）。图像被分为多个网格。图像的每个网格单元都运行相同的算法。让我们通过定义带有初始化器的层开始实现：
