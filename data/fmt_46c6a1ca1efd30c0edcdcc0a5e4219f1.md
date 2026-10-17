
在此过程中，我们旨在解决医学图像分析和诊断中的核心问题：无需从零训练深度 CNN 即可实现该任务；预训练模型和从零训练的 CNN 将证明这一核心问题的真实性和准确性。

## Data

本文使用的两个模型通过来自尼日利亚 Aminu Kano 教授医院的正常和患病脑计算机断层扫描 (CT) 图像进行训练和测试 \[34\]。需要注意的是，从该数据库收集的异常图像包含多种出血类型，但所有图像均被标记为出血，因为本工作旨在判断 CT 切片是否包含出血，无论出血的病理类型如何，出血识别在图像集合中均可实现 \[35\]。

## Data Augmentation

深度网络是数据贪婪的系统 \[36\]，因此提供的数据越多，模型越强大且准确。因此，本文决定使用数据增强技术来增加数据库中的图像数量，这有助于在训练过程中防止可能出现的过拟合 \[37\]。

< $ {

and 270 degrees. Overall, a total number of 12635 normal and haemorrhage CT brain images are obtained. Note that 70% of the data are used for training the employed networks while 30% are used for testing, i.e., 8855 and 3790

images, respectively. Table 1 shows the learning scheme that is used in this work.

本书版权归 Arcler 所有

![Image 979](img/index-225_1.png)

![Image 980](img/index-225_2.jpg)

![Image 981](img/index-225_3.png)

![Image 982](img/index-225_4.png)

![Image 983](img/index-225_5.png)

### Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

199

**Table 1**. 网络的学习方案。

图 2 展示了用于训练和测试深度网络的正常和出血脑 CT 切片的部分样本。

**Figure 2**. 数据库训练和验证图像的样本。(a) 出血图像；(b) 正常图像。

该数据库中的图像原始尺寸为 1024 1024 1 像素；

227 227 3。

我们决定使用相同的输入图像尺寸用于从零训练的 CNN，仅用于性能比较；尽管可以使用其他尺寸。此外，数据库中的图像为灰度类型，由于 AlexNet 模型要求 3 通道输入数据，因此将所有灰度图像重复三次拼接为 RGB 图像，得到 227 227 3 维。

## Training the Network Models

本文使用 MATLAB 环境模拟两个深度模型。

网络在配备 Intel Core i7 4770 处理器和 16 GB 内存的 64 位 Windows 桌面计算机上进行训练。需要注意的是，所用桌面计算机没有图形处理单元 (GPU)。

本书版权归 Arcler 所有

![Image 984](img/index-226_1.jpg)

![Image 985](img/index-226_2.jpg)

![Image 986](img/index-226_3.png)

![Image 987](img/index-226_4.png)

![Image 988](img/index-226_5.png)

## Deep Learning Algorithms

200

网络的性能通过保留 30% 的数据作为独立测试集来评估。损失和准确率的计算如下：

(1)

`| ##`

图像数量，而 N 为训练和/或测试阶段的总图像数。

### CNN Training

用于脑出血分类的 CNN 模型架构和训练设置在本节中介绍。为确定优化神经网络的最佳学习参数，进行了广泛的测试。

注意，在检索的 12635 张脑 CT 图像中，8855 张用于训练，3790 张用于验证训练后的网络。

< #

图像显示于图 3 中，“Conv” 表示卷积层，“BN” 表示批量归一化，“FM” 表示特征图，“FC” 表示全连接层。

在本论文中，所有卷积操作均使用卷积

! »!

'! »

! ”

为设计拟议架构，我们考虑了可用的（即有限的）训练数据规模，以构建一个能够显著正则化的学习模型。

例如，我们采用了已被证明能提升模型泛化性能的批量归一化和 dropout 训练方案 \[38–40\]。

为优化拟议模型，我们采用小批量梯度下降；批量大小为 60。此外，我们使用学习率 0.001 并训练模型 100 个时代。训练后的 CNN 学习曲线如图 4 所示；验证准确率为 90.65%。

本书版权归 Arcler 所有

![Image 989](img/index-227_1.jpg)

![Image 990](img/index-227_2.png)

![Image 991](img/index-227_3.png)

![Image 992](img/index-227_4.png)

### Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

201

此外，当未使用 dropout 和批量归一化进行训练时，我们观察到验证性能略有下降；验证准确率为 87.33%。整体上，拟议模型的

\# < #

进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

![Image 1015](img/index-233_1.png)

![Image 1016](img/index-233_2.jpg)

![Image 1017](img/index-233_3.png)

![Image 1018](img/index-233_4.png)

![Image 1019](img/index-233_5.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

207

**Figure 7**. Learning curve for the trained CNN.

**Figure 8**. Learning curves of AlexNet.

<### #

提取从输入图像中提取的重要特征，这是由于用于训练它们的图像数量很少以及它们的深度。

总体而言，将预训练模型应用于解决出血结构问题，获得了强大的特征提取能力，因为本书版权归 Arcler 所有

![Image 1020](img/index-234_1.png)

![Image 1021](img/index-234_2.jpg)

![Image 1022](img/index-234_3.png)

![Image 1023](img/index-234_4.png)

![Image 1024](img/index-234_5.png)

Deep Learning Algorithms

208

使用如 ImageNet 等大型数据库训练的模型，本文中提出的 AlexNet-SVM、AlexNet 和 CNN 的应用效果表明，将深度 CNN 应用于脑出血问题上是

\# #

具有低误差率的网络。

**Figure 9**. Learning curves of AlexNet-SVM.

**Figure 10**. Learned kernels of CNN.

本书版权归 Arcler 所有

![Image 1025](img/index-235_1.jpg)

![Image 1026](img/index-235_2.png)

![Image 1027](img/index-235_3.png)

![Image 1028](img/index-235_4.png)

![Image 1029](img/index-235_5.png)

![Image 1030](img/index-235_6.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

209

**Figure 11**. Learned kernels of AlexNet

**Table 5**. 网络性能指标

**Table 6**. 与早期工作的结果比较

## Performance Evaluation Metrics

这些指标来源于对测试采样图像的分类，如表 6 所示，它们是基于混淆矩阵（contingency table）得出的。准确率表示正确分类的图像样本的百分比，不考虑其类别标签。对于二元分类，灵敏度是正确分类样本的百分比，特异性是正确负样本的数量：

本书版权归 Arcler 所有

![Image 1031](img/index-236_1.jpg)

![Image 1032](img/index-236_2.png)

![Image 1033](img/index-236_3.png)

![Image 1034](img/index-236_4.png)

Deep Learning Algorithms

210

(2)

### 模型比较

本节解释了传统的 AlexNet 与拟议的 AlexNet-SVM 之间的比较，旨在展示 AlexNet 与 SVM 融合的优势，以及 AlexNet-SVM 可能取得优越性的原因。如表 5 所示，AlexNet 与 SVM 的融合使准确率提高了 0.934。这种优越性主要归功于 SVM 使用的不同优化准则。该算法用于最小化神经网络训练集上的预测损失。然而，在实践中，这两个挑战：首先，凸性问题；它不是凸的，意味着可能存在许多局部最小值。其次，平滑性问题；它不平滑，意味着在实际中可能难以最小化。相比之下，SVM 通过利用结构风险最小化原则，在测试集上最小化泛化误差。因此，由于最大化边界，SVM 的泛化能力高于其他分类器。

### LIMITATIONS

深度学习在医疗应用中的有效性很大，并且随时间不断提升；然而，它仍面临一些缺点，特别是数据可用性。数据的变异性（例如对比度、噪声和分辨率）可能是深度学习在医学领域适应的主要障碍。这些智能模型如果数据包含噪声或来自不同模态时，可能会出现泛化能力差。此外，深度学习模型是数据驱动的系统；数据越多，它们越高效。问题是，医疗领域的数据非常少且不公开，因为隐私问题。大多数情况下，数据包含敏感信息。因此，我们和许多其他研究人员倾向于使用基于转移学习的模型，这些模型通常需要较少的数据来学习，因为它们已经使用大量数据进行预训练。因此，系统能够学习不同层次的特征，这有助于在数据不大的情况下准确适应新任务。

本书版权归 Arcler 所有

![Image 1035](img/index-237_1.png)

![Image 1036](img/index-237_2.png)

![Image 1037](img/index-237_3.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

211

### CONCLUSION

在这项研究中，利用神经网络解决脑出血在 CT 图像中的检测问题，结果稳健且前景可观。

这项研究的动机之一是解决放射科医生在诊断疑似脑出血图像时可能遇到的困难。因此，我们研究了一种潜在的深度卷积神经网络，以帮助医疗专家做出更准确的决策。结果，这可能会减少诊断错误，并提高医疗专家对出血的识别准确性。本文提出了一种预训练的修改网络“AlexNet-SVM”用于相同的分类任务。三个模型，包括拟议模型，在相对小的数据库上进行了训练，以考察网络性能。很明显，深度学习网络在医学图像分析中面临多种挑战。

最常见的挑战是训练数据集缺乏，这可能是一个障碍。本研究中的实验表明，即使深度网络最初是训练在自然图像上，知识转移到医学图像也是可能的。拟议模型使用 SVM 分类器有助于提高 AlexNet 的性能。此外，发现少量数据足以微调预训练模型，而从零开始训练的 CNN 需要大量数据。因此，拟议模型的性能表明，基于转移学习的网络可以在脑出血识别中被考虑。

本书版权归 Arcler 所有

![Image 1038](img/index-238_1.png)

![Image 1039](img/index-238_2.png)

![Image 1040](img/index-238_3.png)

Deep Learning Algorithms

212

### REFERENCES

1\. U. Balasooriya and M. S. Perera, “Intelligent brain haemorrhage

¥

Business Engineering and Industrial Applications Colloquium (BEIAC), pp. 128–133, IEEE, Kuala Lumpur, Malaysia, September 2012.

2\. R. Badenes and F. Bilotta, “Neurocritical care for intracranial haemorrhage: a systematic review of recent studies,” British Journal of Anaesthesia, vol. 115, no. 2, pp. 68–74, 2015.

3.

L. B. Morgenstern, J. C. Hemphill, C. Anderson et al., “Guidelines for the management of spontaneous intracerebral haemorrhage: a guideline for healthcare professionals from the American Heart Association/

American Stroke Association,” Stroke, vol. 46, pp. 2032–2060, 2010.

4\. R. H. Abiyev and M. K. S. Ma’aitah, “Deep convolutional neural networks for chest diseases detection,” Journal of Healthcare Engineering, vol. 2018, Article ID 4168538, 11 pages, 2018.

5\. A. Helwan and R. Abiyev, “Shape and texture features for the

\# ¥ ¨

on Engineering and Computer Science, 

A. Helwan and D. Uzun Ozsahin, “Sliding window based machine learning system for the left ventricle localization in MR cardiac images,” Applied Computational Intelligence and Soft Computing, vol. 2017, Article ID 3048181, 9 pages, 2017.

8.

O. K. Oyedotun, E. O. Olaniyi, A. Helwan, and A. Khashman, “Hybrid auto encoder network for iris nevus diagnosis considering potential malignancy,” in Proceedings of the 2015 International Conference on Advances in Biomedical Engineering (ICABME), pp. 274–277, Beirut, Lebanon, September 2015.

9.

A. Mnih and G. E. Hinton, “Ascalable hierarchical distributed language model,” in Proceedings of the Advances in Neural Information Processing Systems, pp. 1081–1088, Vancouver, Canada, December 2009.

本书版权归 Arcler 所有

![Image 1041](img/index-239_1.png)

![Image 1042](img/index-239_2.png)

![Image 1043](img/index-239_3.png)

Application Of Deep Learning In Neuroradiology: Brain Hemorrhage ...

213

10\. ! ^¯£

with deep convolutional neural networks,” in Proceedings of the Advances in Neural Information Processing Systems, pp. 1097–1105, Lake Tahoe, NV, USA, December 2012.
