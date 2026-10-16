
Feature 采矿在基于机器学习的算法中处理 3D 图像时较为复杂，因为系统试图捕获 3D 平移、取向和异构缩放中的特征/参数。因此，特征采矿的最终搜索空间为 9D，这在当代模型中难以考虑。针对这一点，提出了一种边缘空间深度学习模型（MSDLM）\[[43](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib43)\]，该模型能够递增学习特征从而确定左心室（LV）轮廓的形状。MSDLM 包含两个阶段，第一阶段用于检测感兴趣区域（ROI），第二阶段用于划分 LV 边界。ROI 的定位采用基于深度学习的分类器（DLCs）实现。DLC 通过最大化利用平移、取向和尺度空间来迭代学习 LV 轮廓的位置、取向和尺度，以提高局部概率。公式如下：

``` 
$$\\left( \\hat{\\overset{\\rightarrow}{\\mathbf{T}},\\ }\\hat{\\overset{\\rightarrow}{\\mathbf{R}}},\\ \\hat{\\overset{\\rightarrow}{\\mathbf{S}}} \\right) = {\\arg\\ }\\max\_{\\overset{\\rightarrow}{\\mathbf{T}},\\overset{\\rightarrow}{\\mathit{R}},\\overset{\\rightarrow}{\\mathbf{S}}}\\left( {\\overset{\\rightarrow}{\\mathbf{T}},\\overset{\\rightarrow}{\\mathbf{R}},\\overset{\\rightarrow}{\\mathbf{S}} \\mid \\mathbf{I}} \\right),$$  

(2.13)graphic style="width:38.8125em;" xlink:href="bk978-0-7503-2244-7ch2eqn45.gif" position="float"/

where *T* 表示平移，*R* 表示取向，*S* 表示尺度空间。训练了三个 DLC 来预测位置、取向和尺度。第一个 DLC 负责预测位置，第二个 DLC 通过输入第一个 DLC 的结果来预测取向，第三个 DLC 通过输入前两个 DLC 的结果来预测尺度。在第二阶段，采用基于深度学习的主动形状模型对 LV 形状进行变形。为防止过拟合，采用了 dropout。数据集由 869 名患者的 2891 个 3D 体积组成。所提深度学习 MSDLM 模型在与未使用深度学习组件的传统系统相比表现更好。比较结果如表 [2.1](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t1) 所示。相应的过程模型和生成的图像分别显示在图 [2.12](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig12) 和 [2.13](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig13)。

**Table 2.1.** Comparison of the MSDLM and the conventional MSM model.

| Accuracy parameters || DL based MSDLM || Conventional MSM |
| --- | --- | --- |
| Position error || 1.47 mm || 3.12 mm |
| --- | --- | --- |
| Corner error || 2.80 mm || 0.42 m |

![Figure 2.12. Deep classifier based 3D LV segmentation model.](images/bk978-0-7503-2244-7ch2f12_online.jpg)

**Figure 2.12.** Deep classifier based 3D LV segmentation model.

![Figure 2.13. Deep classifier based 3D LV segmentation model outputs. The auto-detected bounding box is shown in green while the ground truth bounding box is shown in yellow. (Reproduced with permission from \[43\]. Copyright 2016 IEEE.)](images/bk978-0-7503-2244-7ch2f13_online.jpg)

**Figure 2.13.** Deep classifier based 3D LV segmentation model outputs. The auto-detected bounding box is shown in green while the ground truth bounding box is shown in yellow. (Reproduced with permission from \[[43](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib43)\]. Copyright 2016 IEEE.)

##### 2.3.1.4 Vessel mining from x-ray angiograms

全球范围内，心血管疾病（CVD）每年导致超过 1700 万人死亡。冠状动脉疾病（coronary artery disease）是主要 CVD 之一，也是死亡的主要原因（见图 [2.14](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig14)）。传统方法，即跟踪和滤波方法，因分辨率低、噪声存在以及与感兴趣区域相近的类似强度器官增加复杂度，无法提供更高的准确性。本文采用基于深度学习的卷积神经网络（CNN）模型对 X 射线血管造影图像中的血管区域进行检测\[[44](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib44)\]。实验中收集了 44 张图像。图像通过顶帽变换预处理以提升对比度。采用补丁采矿方法，从训练和测试 CNN 时共采集了 1 040 000 个补丁。CNN 包含两层卷积、两层最大池化以及两层全连接层（500 个神经元），输出 vessel 和 not‑vessel 两类的概率。模型实现了 93.5% 的准确率，显著优于以往方法。即使在噪声、低分辨率和复杂背景的条件下，结果仍然优秀。然而，所使用的 CNN 仅有六层，建议在更深层的模型上进行训练/测试，以获得更好的结果、可靠性以及临床应用。分割结果如图 [2.15](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig15) 所示。

![Figure 2.14. Segmentation of x-ray images using CNNs.](images/bk978-0-7503-2244-7ch2f14_online.jpg)

**Figure 2.14.** Segmentation of x-ray images using CNNs.

![Figure 2.15. Row one shows five input images. Row two shows the corresponding ground truth of the row one images. Row three shows analogous images for segmentation outputs using CNN. (Reproduced with permission from \[44\]. Copyright 2016 IEEE.)](images/bk978-0-7503-2244-7ch2f15_online.jpg)

**Figure 2.15.** Row one shows five input images. Row two shows the corresponding ground truth of the row one images. Row three shows analogous images for segmentation outputs using CNN. (Reproduced with permission from \[[44](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib44)\]. Copyright 2016 IEEE.)

##### 2.3.1.5 Plaque characterization

脆性斑块识别是 CVD 检测的重要环节，有助于早期风险评估和治疗方案制定。但斑块检测面临多项挑战：体积小、形态多样、伴随斑点噪声，导致分割困难，使得斑块表征成为复杂任务。为解决此问题，提出了一种自动化深度学习 CNN 模型用于斑块表征\[[45](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib45)\]。该 CNN 包含四层卷积、四层 ReLu 激活以及三层全连接层，采用 softmax 分类技术。训练时使用交叉熵损失函数，并将模型结果与单尺度和多尺度支持向量机（SVM）进行比较。

实验使用了 56 例超声心动图（CCA）图像。采用补丁采矿策略，从超声图像中共采集了 90 000 个补丁，并将其标注为三类：脂肪核、纤维和钙化，作为 CNN 学习的真值。表 [2.2](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2t2) 列出了 DL 模型与传统机器学习模型的对比结果，显示 DL 模型在准确率上大幅超越了传统模型。模型的处理流程及分割结果分别展示在图 [2.16](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig16) 和 [2.17](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2fig17)。

**Table 2.2.** Comparison of the DL and conventional models for plaque characterization \[[45](#Chapter_2.xhtml#bk978-0-7503-2244-7ch2bib45)\].

| Model || Accuracy |
| --- | --- |
| --- | --- |
| DL based CNN || 78.5% |
| --- | --- |
| Single-scale SVM || 14.3% |
| Multi-scale SVM || 7.2% |

![Figure 2.16. Global diagram for plaque characterization.](images/bk978-0-7503-2244-7ch2f16_online.jpg)

**Figure 2.16.** Global diagram for plaque characterization.

