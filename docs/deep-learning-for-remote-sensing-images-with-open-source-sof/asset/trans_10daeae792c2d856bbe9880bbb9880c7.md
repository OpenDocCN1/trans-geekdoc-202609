

最后，我们使用默认参数训练一个随机森林（RF）分类器。

```bash
# Train a Random Forest classifier with validation
otbcli_TrainVectorClassifier \
-io.vd terrain_truth_epsg32654_A_pixelvalues.shp \
-valid.vd terrain_truth_epsg32654_B_pixelvalues.shp \
-feat "value_0" "value_1" "value_2" "value_3" \
-cfield "class" \
-classifier "rf" \
-io.out randomforest_model.yaml
```

注意 kappa 指数：应该在 0.5 左右，即比我们的 CNN 模型低约 20%。

> **重要提示**
>
> 与 RF 相比，CNN 使用了更多信息进行训练。事实上，CNN 学习的是多光谱图像的 16 × 16 像元块，而 RF 仅学习多光谱像元（可理解为多光谱图像的 1 × 1 像元块）。我们这里的目标不是比较 RF 与 CNN，而是展示 CNN 处理的上下文信息在分类任务中的有用性。一个更公平的对比对象可以是使用纹理、局部傅里叶变换、SIFT 等空间特征的 RF。

## 5.7 推理

在 5.3 节中，我们成功训练了 CNN 模型。现在，我们将该模型应用于 Sentinel-2 影像，以生成土地覆盖图。优化器不再使用，我们仅使用训练后权重固定的模型。这一部分称为*推理*。为了执行推理，我们使用 **TensorflowModelServe** 应用程序。我们知道，CNN 输入的感知野为 16 × 16 像元，占位符名为 **“x.”**。模型的输出是估计的类别，即 **Argmax** 算子的张量结果，名为 **“prediction.”**。我们不再使用优化器节点，因为它属于训练过程的一部分：我们只使用模型中从 **“x”** 计算 **“prediction”** 的子集，如图 *5.4* 所示。

现在，将生成的影像导入 QGIS，参见图 5.5。您可以更改栅格的样式：在**图层面板**（窗口左侧）中，右键单击影像，选择**属性**，转到**符号系统**选项卡，并将**渲染类型**选择为**单波段伪彩色**。然后，您可以为每个类别值选择颜色、添加标注等。您还可以通过单击**样式**按钮（窗口底部）并打开 `tokyo/terrain-truth` 目录中名为 *legend-style.qml* 的文件来加载预定义样式。

![](img/f70619500c7a30b0babf83918d56ad93_55_0.png)

**图 5.5**  
在 QGIS 中导入输出分类图。

> **重要提示**  
> 我们刚刚以**基于块**的模式运行了 CNN，这意味着应用程序在规则间隔处独立提取和处理块。这很耗时，因为采样策略要求我们复制大量重叠的块并独立处理它们。

## 6 全卷积神经网络

在上一节中，我们使用深度卷积神经网络执行了逐像元分类。我们以基于块的模式执行了推理，这意味着对于每个输出像元，我们在输入影像上的一个以输出像元位置为中心的小块上运行模型。虽然这种网络架构易于实现，但在处理效率方面不高。由于块重叠，数据会被多次复制，每次都采用不同的内存对齐方式（针对不同的块），然后传递给模型。深度网络中最耗时的操作是卷积，这些操作高度并行，并且可以实现为中间结果可被其他块处理重用（例如中间和，参见公式 1.2 和 1.3）。然而，基于块的模式禁止了中间结果的可能重用，因为每个新块都需要重新计算，效率不高。我们将介绍全卷积神经网络（FCNN，或 FCN），它只是可以处理整个影像区域而非局限于小块的 CNN。

### 6.1 将现有模型用作 FCN

从我们在 5.4 节中使用的简单 CNN 的组成可以看出，该模型可以充当 FCN。其属性总结如下：

- **感知野**（16 × 16 像元），
- **表达野**（1 × 1 像元），
- **缩放因子**（总共 2 个大小为 2 的连续池化算子，意味着缩放因子为 2 × 2 = 4）。

我们可以验证它们与模型中实现的算子是一致的。令 n 为输入影像的大小，我们可以看看模型如何将影像区域传播到大小为 m 的输出：

1. 使用 5 × 5 卷积核进行卷积：输出大小为 n − 4，
2. 步长为 (2,2) 的 2× 池化：输出大小为 (n − 4)/2 = n/2 − 2，
3. 使用 3×3 卷积核进行卷积：输出大小为 (n/2 − 2) − 2 = n/2 − 4，
4. 步长为 (2,2) 的 2× 池化：输出大小为 (n/2 − 4)/2 = n/4 − 2，
5. 使用 2×2 卷积核进行卷积：输出大小为 (n/4 − 2) − 1 = n/4 − 3。

总之，我们有 m = n/4 − 3，这与模型的属性（感知野、表达野、间距因子）相当一致：模型从 16 × 16 的输入影像生成 1 × 1 的输出。其输出像元的物理间距等于输入像元间距乘以 4。将参数 `model.fullyconv` 设置为 on 以启用全卷积处理，从而运行 CNN 模型。

```bash
otbcli_TensorflowModelServe \
-source1.il Sentinel-2_B4328_10m.tif \
-source1.rfieldx 16 \
-source1.rfieldy 16 \
-source1.placeholder "x" \
-model.dir model1 \
-model.fullyconv on \
-output.names "prediction" \
-output.spcscale 4 \
-out "classif_model1_fcn.tif?&box=1000:1000:250:250"
```

在 QGIS 中打开结果影像，并与原始 CNN 生成的分类图进行比较。打开 **属性 > 元数据** 选项卡，检查新地图的物理间距是否比原始地图大 4 倍。

### 6.2 逐像元全卷积模型

全卷积网络比基于块的方式运行更快，足以在合理时间内处理完整影像（要测试，只需移除上一条命令中的扩展文件名即可）。然而，池化完全破坏了输出的分辨率（输出影像间距是输入像元间距的 4 倍）。我们可以稍微修改原始模型，以创建一个保持输入影像间距的逐像元全卷积网络。

我们移除池化算子，并添加一些具有单位步长的卷积层。我们的目标是保持与之前架构相同的感知野和表达野（这样，我们可以重用 5.2 节中生成的影像块）。图 6.1 总结了我们的新架构。

![](img/f70619500c7a30b0babf83918d56ad93_59_0.png)

**图 6.1**  
新的全卷积神经网络。已移除池化算子，并添加了卷积算子。注意，卷积中无步长，保持了空间维度上的物理间距。

让我们实现新的 FCN 架构。我们将使用资源仓库中提供的 `create_model2.py` Python 代码。[^1]

```python
#
# Do not forget to add the otbtf/python directory to your PYTHONPATH.
# Else "tricks" can’t be imported.
# In the OTBTF Docker image, tricks.py is located in the following
# path: /work/otb/otb/Modules/otbtf
#
# Works with OTBTF 1.7
#
from tricks import *
import sys

nclasses=6

def myModel(x):

    # input patches: 16x16x4
    conv1 = tf.layers.conv2d(inputs=x, filters=16, kernel_size=[5,5],
                             padding="valid", activation=tf.nn.relu)
    # conv1 out size: 12x12x16
    conv2 = tf.layers.conv2d(inputs=conv1, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv2 out size: 10x10x16
    conv3 = tf.layers.conv2d(inputs=conv2, filters=16, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv3 out size: 8x8x16
    conv4 = tf.layers.conv2d(inputs=conv3, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv4 out size: 6x6x32
    conv5 = tf.layers.conv2d(inputs=conv4, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv5 out size: 4x4x32
    conv6 = tf.layers.conv2d(inputs=conv5, filters=32, kernel_size=[3,3],
                             padding="valid", activation=tf.nn.relu)
    # conv6 out size: 2x2x32
```

[^1]: https://github.com/remicres/otbtf_tutorials_resources

