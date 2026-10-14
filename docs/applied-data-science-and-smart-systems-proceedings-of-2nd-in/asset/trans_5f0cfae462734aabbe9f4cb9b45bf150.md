
在特征提取过程中，预处理后的牛鼻梁图像被输入到卷积神经网络（CNN）模型中，每一层执行数学运算，包括卷积、池化和非线性激活函数。这些运算逐步提取层次化特征，识别图像中的模式和结构。选取的中间层输出随后被收集，代表了不同细节水平的高维图像抽象。这些中间输出随后组合，生成特征向量，是一个数值表示，能够概括CNN 所识别的关键模式。通常特征向量维度很高，向量的每个维度对应于特定的鼻梁模式特征，如皱纹图案和纹理细节。这些从CNN 提取的特征随后用于牛只识别，将其与数据库中存储的模板进行比对，通过相似度评分或分类技术判断输入图像是否与已识别的牛只相匹配。该过程将视觉信息转化为全面的特征表示，从而实现对个体牛只的精确、高效识别。

### 存储与检索

提取出的特征存储在数据库中。借助相似度评分，我们可以判断两张图像是否匹配。相似度评分的计算是许多机器学习和计算机视觉应用（如图像识别、目标检测）中的重要步骤。相似度评分是一个量化指标，表示两张图像、物体或特征之间的相似程度。[Figure 48.3](#ch48.xhtml#fig48_3) 展示了牛鼻梁图像的注册和验证过程。

![Figure 48.3 Flow diagram of proposed system](images/fig48_3_C.jpg)

[Figure 48.3 Flow diagram of proposed system](#ch48.xhtml#R_fig48_3)

### 结果与讨论

#### VGG16 模型

实验结果表明，YOLOV5 和 VGG16 模型在基于鼻梁图案的牛只准确识别方面表现出色。使用这些模型显著提升了牛只识别的准确率，有助于农民和研究人员监测牲畜的健康和生产力。

YOLOV5 是 You Only Look Once 算法的一个变体，已在物体检测任务中表现出色，包括基于鼻梁图案的牛只识别。其能够实时检测目标并保持高精度的特性，使其成为可靠的牛只识别模型。实验表明，YOLOV5 的平均精度（MAP）为 58.1%。MAP 指标衡量物体检测模型在多类任务（如牛只识别）中的整体精度。

另一方面，VGG16 是一种卷积神经网络，在图像分类任务中表现优异。其深层结构能够学习复杂的特征和模式，适合基于鼻梁图案识别牛只。实验显示，VGG16 实现了 95% 的分类准确率，并伴随如 [Figures 48.4](#ch48.xhtml#fig48_4) 和 [48.5](#ch48.xhtml#fig48_5) 所示的损失曲线。

![Figure 48.4 Plot of accuracy](images/fig48_4_C.jpg)

[Figure 48.4 Plot of accuracy](#ch48.xhtml#R_fig48_4)

![Figure 48.5 Plot of loss](images/fig48_5_C.jpg)

[Figure 48.5 Plot of loss](#ch48.xhtml#R_fig48_5)

#### 移动应用

拟议系统已集成到移动应用中，以便于使用。移动应用帮助农民在数据库中登记牲畜，并可通过应用进行身份验证。[Figure 48.6](#ch48.xhtml#fig48_6) 展示了农民通过注册手机号并使用一次性密码（OTP）完成注册的界面。

![Figure 48.6 Register page](images/fig48_6_C.jpg)

[Figure 48.6 Register page](#ch48.xhtml#R_fig48_6)

注册登录后，应用会询问牲畜的详细信息，包括耳标编号、品种以及鼻梁图像。[Figure 48.7](#ch48.xhtml#fig48_7) 显示了牲畜详情的仪表盘。这些信息存储在数据库中，可在查找匹配时使用。

![Figure 48.7 Dashboard for details](images/fig48_7_C.jpg)

[Figure 48.7 Dashboard for details](#ch48.xhtml#R_fig48_7)

为验证牲畜，需使用相机拍摄鼻梁图像。[Figure 48.8](#ch48.xhtml#fig48_8) 展示了匹配结果。拍摄的图像随后输入模型，最终结果显示。如果在数据库中找到匹配的特征，则提供匹配结果；若无相关数据，则不返回结果，如 [Figure 48.9](#ch48.xhtml#fig48_9) 所示。

![Figure 48.8 Matched result](images/fig48_8_C.jpg)

[Figure 48.8 Matched result](#ch48.xhtml#R_fig48_8)

![Figure 48.9 Not matched result](images/fig48_9_C.jpg)

[Figure 48.9 Not matched result](#ch48.xhtml#R_fig48_9)

所有参与者随后获得了一份问卷，以评估移动应用的使用情况。40 名用户在使用了应用的全部功能后完成了调查。为量化整体反馈，所有问题均采用 5 点 Likert 量表（强烈不同意：1，不同意：2，中立：3，同意：4，强烈同意：5）。问卷仅包含五个简短句子，用于分析模型和移动应用的效率与实用性。反馈通过 Microsoft Excel 工具进行分析。[Table 48.1](#ch48.xhtml#tab48_1) 展示了反馈响应的描述性统计。整体平均分为 4.3 分（满分 5 分），如 [Table 48.1](#ch48.xhtml#tab48_1) 所示，该产品在各方面均表现突出。

[Table 48.1. Descriptive statistics of feedback responses.](#ch48.xhtml#R_tab48_1)

| Questions || N || Mean |
| --- | --- | --- |
| Q1. User experience with the mobile application? || 40 || 4.54 |
| Q2. How well did the mobile application capture and store the details of your cattle? || 40 || 4.7 |
| Q3. How efficient the process is to capture the muzzle image with the mobile camera? || 40 || 3.8 |
| Q4. How reliable were the matched cattle results displayed by the application? || 40 || 4.2 |
| Q5. Will you recommend this product to others? || 40 || 4.3 |

反馈的最低分出现在使用移动相机拍摄鼻梁图像的便利性上。平均评分为 3.8（满分 5 分），说明参与者在使用移动相机捕获鼻梁图像时遇到了困难，可能是因为各类手机摄像头像素水平差异较大。通过使用更多样化的像素图像进行模型训练，可能会解决此问题。[Figure 48.10](#ch48.xhtml#fig48_10) 展示了产品在 0–5 评分尺度上的反馈。

![Figure 48.10 Feedback responses](images/fig48_10_C.jpg)

[Figure 48.10 Feedback responses](#ch48.xhtml#R_fig48_10)

### 结论与未来展望

