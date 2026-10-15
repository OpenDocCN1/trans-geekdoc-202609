
[Deuschel et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0205) 研究了性别和肤色对面部表情识别的影响，并使用分类准确率和热图进行定量和定性评估。[Krishnan et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0450) 研究了不同深度模型和训练集不平衡对不同性别-种族群体中性别分类的影响。他们使用了UTKFace和FairFace数据库，并指出训练集不平衡会加剧性能准确率的差距。作者进一步使用面部关键点检测研究了不同种族子群的面部形态，并获得了关于差异可能原因的有趣洞察。为了进一步研究不同肤色对性别分类的影响，[Muthukumar (2019)](#Ch007_169-221_S0169716123000020.xhtml#bb0565) 使用了亮度模式移动和最优传输技术来改变肤色。他们报告说，肤色本身并不是观察到的偏见的驱动因素，必须考虑更广泛的种族差异。在面部属性预测的对抗公平性背景下，[Nanda et al. (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0585) 提出了一个新颖的想法。在对抗公平性中，如果分类器对所有子群的对抗攻击具有同等的鲁棒性，则该分类器被认为是无偏的。他们进一步展示了在Adience和UTKFace数据库等数据集中存在这一不公平现象。最近，[Jain et al. (2022)](#Ch007_169-221_S0169716123000020.xhtml#bb0345) 展示了使用流行的GAN网络生成的面部图像存在偏见。他们进一步指出，工程师的合成面部图像中具有更男性化的面部特征和更浅的肤色。这一点在[Fig. 7](#Ch007_169-221_S0169716123000020.xhtml#f0040)中突出显示。[Joo and Karkkainen (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0375) 展示了在护士或工程师等职业的人物图像中，性别属性分类器的性能存在明显差异。

![Fig. 7 Illustrative test set of transformations on female celebrity faces. These examples highlight how the generator learns to transform the feminine facial features to appear more masculine so as to fool the discriminator into thinking the transformed celebrity face portrays an engineering professor (Jain et al., 2022).](images/S0169716123000020/f07-07-9780443184307.jpg)

[Fig. 7](#Ch007_169-221_S0169716123000020.xhtml#B-f0040) 说明性测试集中对女性名人脸部进行的转换示例。这些示例突出了生成器如何学习将女性面部特征转变为更男性化的特征，以欺骗判别器，使其误以为转换后的名人脸呈现出工程师的特征（[Jain et al., 2022](#Ch007_169_169716123000020.xhtml#bb0345)）。

####  5.2.3: Counterfactual analysis

[Joo and Karkkainen (2020)](#Ch007_169-221_S0169716123000020.xhtml#bb0375) 提出了一种通过反事实来理解偏见的方法，他们合成了性别和种族群体的反事实面部图像，同时保持其他信号不变。利用这些样本，他们分析了不同下游任务的性能，并评论了系统中不同的隐藏偏见。同样，[Denton et al. (2019)](#Ch007_169_169716123000020.xhtml#bb0200) 基于生成的反事实样本对深度模型的性能进行敏感性分析。这些反事实样本是通过在CelebA数据库（[Liu et al., 2015](#Ch007_169_169716123000020.xhtml#bb0495)）上使用渐进式GAN生成的潜向量进行操纵得到的。虽然反事实方法能够明确控制性别和肤色等属性的变化，但生成的样本可能不代表真实世界的分布。[Quadrianto et al. (2019)](#Ch007_169_169716123000020.xhtml#bb0645) 将输入域的数据翻译到公平目标域。他们观察到模型在预测中会调整男性的眼睛和嘴唇区域以强制公平性。进一步研究导致模型预测偏差的因素之间的相互依赖关系，[Barlas et al. (2021)](#Ch007_169_169716123000020.xhtml#bb0095) 分析了五个专有图像标记算法中上下文与性别之间的相关性。

####  5.2.4: Role of latent factors during model training

模型公平性通常被认为是子群间性能差异的结果。在另一种方向上，[Serna et al. (2021)](#Ch007_169_169716123000020.xhtml#bb0725) 提出了InsideBias，他们研究了模型如何表示信息，而不是模型如何表现。他们在偏向数据集的背景下分析了训练过程中模型所学习的特征。[Serna et al. (2022b)](#Ch007_169_169716123000020.xhtml#bb0730) 展示了分析模型权重如何提供关于其偏向行为的洞察。[Li and Xu (2021)](#Ch007_169_169716123000020.xhtml#bb0490) 提出了一种变异损失，该损失优化潜空间中的超平面，以获取偏向属性信息。在一次有趣的分析中，[Qiu et al. (2021)](#Ch007_169_169716123000020.xhtml#bb0640) 研究了性别分类与面部验证性能之间的关系。他们发现，对于假冒图像对，当两张图像都导致性别分类错误时，面部识别模型会给出高相似度评分，从而导致假匹配错误。

研究人员继续研究预测中的偏见（[Fig. 4D](#Ch007_169_169716123000020.xhtml#f0025)），以及它可能如何在数据和算法层面被纳入（[Fig. 4A and C](#Ch007_169_169716123000020.xhtml#f0025)）。大量工作集中在分析流行的深度模型架构和商用算法。流行的工具包括特征图可视化、子群间公平性和性能评估指标、生成的反事实样本以及偏向训练。然而，自动化地识别偏见仍然是一个开放问题，需要引起研究界的关注。少数研究尝试自动检测导致偏见的因素，如UDIS（[Krishnakumar et al., 2021](#Ch007_169_169716123000020.xhtml#bb0445)）。UDIS利用层次聚类技术对类似的数据嵌入进行聚类。基于聚类的轮廓分数，可以识别可能的偏向模型。UDIS的有效性结果在[Fig. 8](#Ch007_169_169716123000020.xhtml#f0045)中展示。然而，自动化识别偏见仍然是一个开放问题，需要引起研究界的关注。分析技术总结在[Table 5](#Ch007_169_169716123000020.xhtml#t0030)。

![Fig. 8 Heatmaps showcasing the regions utilized by the model for prediction of the “smiling” attribute through the UDIS algorithm. The heatmaps highlight highly relevant “mouth” region being used for prediction (Krishnakumar et al., 2021).](images/S0169716123000020/f07-08-9780443184307.jpg)

[Fig. 8](#Ch007_169-221_S0169716123000020.xhtml#B-f0045) 说明性热图展示了通过UDIS算法预测“微笑”属性时模型所利用的区域。热图突出了高度相关的“口部”区域用于预测（[Krishnakumar et al., 2021](#Ch007_169_169716123000020.xhtml#bb0445)）。

[Table 5](#Ch007_169_169716123000020.xhtml#B-t0030)

不同研究分析面部识别和属性预测任务中的偏见。

| Face detection and recognition | Attribute prediction |
| --- | --- |
