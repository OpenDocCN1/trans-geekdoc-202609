
在这项工作中，使用了一个基于深度学习（DL）的卷积神经网络（CNN）模型，用于在 Symtosis^(TM) 系统下自动检测低回声 FLD 并分类正常与异常的超声肝脏图像。这是首次尝试比较三种基于机器学习的分类方法：支持向量机（SVM）\[[11](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib11)\]、极端学习机（ELM）\[[12](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib12)\] 和 CNN 模型。此外，我们还研究了一种专门的操作——Inception。Inception 操作利用维度缩减原理，将不同尺寸的卷积核组合在一起，然后将这些卷积通道拼接，以降低 Symtosis^(TM) 系统的计算成本。Inception 使得深度学习（DL）的层数增加，更深的网络能够提取更高层次的特征，从而提高系统的准确率。最终，在我们的深度学习 CNN 模型中，用于组织分类和风险评估的 GPU 计算框架被研究。SVM、ELM 和 DL 的曲线下面积（AUC）分别为 0.79、0.92 和 1.0，使用 K10 交叉验证（CV）协议对优化的超声肝脏图像时，达到 100% 的准确率。图 [11.2](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig2) 展示了 DL 模型的整体架构。首先，对去除边框的超声肝脏图像进行预处理，以获得最佳的 DL 分层准确度，这为后续所有数据分析奠定了基础。此外，还使用了生物特征面部数据来验证我们的系统。

![Figure 11.2. Symtosis™ system using deep learning. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f2_online.jpg)

**Figure 11.2.** Symtosis™ system using deep learning. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

本章的结构如下。患者参数和采集在章节 [11.2](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-2) 中讨论，DL 系统的方法论和另外两种传统分类算法在章节 [11.3](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-3) 中阐述。章节 [11.4](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-4)、[11.5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-5) 和 [11.6](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-6) 分别展示结果、性能评估和讨论。最后，结论位于章节 [11.7](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11s11-7)。

### 11.2 患者人口学和采集

为此，我们从葡萄牙里斯本圣玛丽亚医院胃肠病科（已获得伦理批准）选取了 63 名患者 \[[13](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib13)\]，这些患者此前已在我们的早期研究中使用 \[[5](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib5), [7](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib7)\]。在美国使用 DICOM（数字成像与通信医学）格式的 Philips Medical Systems CX c 50 扫描仪获取了图像。扫描图像的位深为 8 位，尺寸为 1024 × 1024 像素。该设备使用曲阵探头 C5–1，包含 160 个压电元件，共振频率范围为 1–5 MHz。在 63 名患者中，36 名被诊断为 FLD，剩余 27 名为正常。医院的专业超声操作员采集了正常和脂肪肝的原始图像。根据实验室活检报告的指标，结果被分类为正常或异常。这些分类后的照片构成了我们实验的基准真值（GT）。肝脏由小左叶和大右叶组成，右叶的扫描使其成为主要组成部分。在超声图像中，肝脏实质的回声强度与皮质相似，而在脂肪肝的超声图像中，肝实质的回声强度显著高于肾皮质 \[[14](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib14), [15](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib15)\]。在每张图像的感兴趣区域（ROI）沿中轴方向去除了一个 128 × 28 像素的中间区域。图 [11.3](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig3) 展示了原始肝脏图像，第一行是正常图像，第二行是异常图像。

![Figure 11.3. Normal liver images (top row) and abnormal liver images (bottom row). (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f3_online.jpg)

**Figure 11.3.** Normal liver images (top row) and abnormal liver images (bottom row). (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

### 11.3 方法论

在 CNN 的训练过程中，如图 [11.1](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig1) 所示，低层特征被转化为高层特征。为了学习这些从原始图像中得到的特征集合，CNN 会反复应用卷积和池化操作。在简单的 CNN 模型中，第一个挑战是过拟合，导致分类测试精度和准确率下降。第二个挑战是需要更多的层，因为更多的层能够生成更好的特征图，但这也会增加深度学习系统的计算复杂度。dropout 策略通过随机限制隐藏层权重的数量来解决第一个挑战。Inception 模型则通过降低计算成本来解决第二个问题。这两种架构集成到 CNN 基本模型中，是本系统在肝脏病变分层方面的创新之处。图 [11.4](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11fig4) 展示了该架构。该深度学习架构包含两套、九个 Inception 点、五个池化层、一个 dropout 层、一个线性层和一个 softmax 层。

![Figure 11.4. The proposed CNN model. (Reproduced with permission from \[40\]. Copyright 2018 Elsevier.)](images/bk978-0-7503-2244-7ch11f4_online.jpg)

**Figure 11.4.** The proposed CNN model. (Reproduced with permission from \[[40](#Chapter_11.xhtml#bk978-0-7503-2244-7ch11bib40)\]. Copyright 2018 Elsevier.)

#### 11.3.1 风险分层模型

