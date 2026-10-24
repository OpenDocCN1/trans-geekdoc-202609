
使网络在保持高精度的同时，在计算资源方面更高效。

EfficientNetV2B0 架构由一系列 EfficientNetV2 块堆叠而成，每个块中的滤波器数量和层数各不相同。

该模型的输入为 224 × 224 的图像，输出为一个 1000 维的向量，表示图像的类别概率。模型还包括最后的全连接层以及一个全局平均池化层。

仅用少量参数，EfficientNet-V2B0 在多种任务上表现良好，包括语义分割、目标识别和图像分类。它适用于资源受限的场景，例如便携设备或边缘计算环境。

### 11.4.2 EfficientNetV2B1

EfficientNet-V2B1 是该系列中的一种模型，是 EfficientNet-V2 模型的变体。

EfficientNet-V2B1 模型的架构基于 MobileNetV2 模型，后者是一种为高效图像分类而开发的 CNN。它采用深度可分离卷积和残差连接来减少所需参数和计算量，同时保持高性能（Subhashini & Khang, 2023）。

EfficientNet-V2B1 架构由一系列卷积层组成，其后接批归一化层和修正线性单元（ReLU）激活函数。

全局平均池化层将特征图的空间维度降低为每个通道的一个数值，而仅带有 Softmax 激活函数的全连接层输出最终的类别概率。模型训练使用交叉熵损失函数。

EfficientNet-V2B1 是一个相对较小的模型，仅有 3.2 百万个参数，但仍能在图像分类任务上取得良好性能。它非常适合在移动设备和其他资源受限平台上使用，在这些平台上计算效率很重要。

EfficientNetV2B1 的一些关键特性如下：

- 它是一种高效的架构，设计上比其他模型更小更快，同时仍能取得良好性能。
- 它使用复合缩放方法来缩放网络的维度，有助于提高模型的效率和准确性。
- 它具有均衡的参数数量和计算成本，使其成为各种应用的良好选择。
- 它采用深度可分离和逐点卷积的混合方式，降低了模型的参数数量并提高了其有效性。
- 它还包含其他设计创新，例如倒残差块和线性瓶颈，有助于进一步提高模型的效率和准确性。

### 11.4.3 EfficientNetV2B2

EfficientNetV2B2 模型是 EfficientNetV2 架构的变体，深度为 2（因此名称中为“B2”）。它是一个相对较小的模型，参数约为 0.5 百万。它非常适合在计算资源有限的图像分类任务中使用，例如移动设备。

EfficientNet V2B2 架构基于 EfficientNet 架构，后者使用复合缩放方法来扩大网络规模和容量，同时提高其效率。

V2B2 架构的具体细节可能有所不同；然而总体而言，它可能比 EfficientNet 家族中较小的模型具有更多层和每层更多的滤波器。它还可能使用深度可分离卷积和挤压-激励（SE）块等技术来提高模型的效率。

### 11.4.4 EfficientNetV2B3

EfficientNet V2B3 是 EfficientNet 家族的特定成员，以其使用“B3”尺寸配置为特征。

EfficientNet 架构基于通过仔细平衡网络的宽度、深度和分辨率来扩展神经网络模型这一思想。所使用的模型超参数，包括层数、每层滤波器的总数以及输入图像的分辨率，被称为“B3”尺寸配置。

EfficientNet-V2 B3 变体是一个更大、计算复杂度更高的模型，以获得更好的性能。它由 10 个块组成，这些块交替使用卷积层和最大池化层，数据维度必须为 224 × 224 像素，并在全局平均池化层后进行全连接。

随着网络的深入，卷积层包含更多滤波器，模型采用跳跃连接来增强网络中的信息流动。

B3 变体经常用于图像分类、目标识别和语义分割等任务。它包含超过 25 百万个参数。

### 11.4.5 EfficientNetV2S

EfficientNetV2S 是 EfficientNet 家族的成员。它是 EfficientNet 的较小版本，参数更少、计算复杂度更低。它专为模型尺寸和计算资源受限的场景而设计，例如移动设备或边缘设备。

EfficientNet V2S 架构的一个关键方面是其使用复合缩放，即以复合方式缩放网络维度（宽度、深度和分辨率）以实现更好的性能。这使得网络即使在输入尺寸减小时仍能保持良好的性能。

深度可分离卷积层的实现以及网络末端使用全局平均池化层是 EfficientNet V2S 设计的另外两个关键组成部分。这些设计决策有助于减少网络内部的参数数量，提高效率并简化训练过程。

EfficientNet-V2S 的架构基于 MobileNetV2 架构，后者使用具有线性瓶颈和宽度乘数的倒残差块来控制模型复杂度。

EfficientNet-V2S 模型还包括额外的增强，例如 SE 块，通过自适应地重新校准通道级特征响应来帮助提高模型的表征能力，以及 Swish 激活函数，有助于提高模型的性能和训练速度。

总之，EfficientNet-V2S 的架构由一系列具有线性瓶颈和 SE 块的倒残差块组成，其后接分类头。模型设计为灵活，可以通过调整宽度乘数和输入图像的分辨率来实现性能与效率之间的权衡（Khanh & Khang, 2021）。

### 11.4.6 EfficientNet-V2M

为提高 CNN 在计算机视觉应用中的有效性而创建的 EfficientNet 架构有一个名为 EfficientNet-V2M 的变体。研究“EfficientNet: Rethinking Model Scaling for Convolutional Neural Networks”提出了 EfficientNet-V2，后者在此基础上进行了扩展。

出版物“EfficientNet-EdgeTPU: Hardware-aware Neural Network Design for Edge TPUs”首次发布了 EfficientNet 的 V2M 版本。由于它在计算和张量处理单元（TPU）的内存需求方面更高效，因此特别适合在资源有限的边缘设备上使用，例如 Google’s Edge Tensor Processing Units。

EfficientNet-V2M 与 EfficientNet-V2 的主要区别如下：

- EfficientNet-V2M 每层的滤波器数量少于 EfficientNet-V2。
- EfficientNet-V2M 在中间层使用深度可分离卷积而不是常规卷积，从而减少了所需参数和计算量。
- EfficientNet-V2M 使用 Swish 激活函数的修改版本，其计算效率高于 ReLU。

总体而言，EfficientNet-V2M 是一种高效的 CNN 架构，非常适合部署在资源有限的边缘设备上。
