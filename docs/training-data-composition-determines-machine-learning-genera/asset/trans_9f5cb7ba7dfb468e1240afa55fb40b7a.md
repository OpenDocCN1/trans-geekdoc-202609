
PyTorch的Transformer构建模块，其代码可在GitHub上获取。所使用的训练循环与SN10所用的相同。对于基于蛋白质语言模型（PLM）的SN10，我们利用ESM2b蛋白质语言模型<sup>74</sup>生成CDRH3的1,280维嵌入，以及使用AntiBERTa2（简称为AntiBERTa2）生成1,024维嵌入<sup>75,76</sup>。在实现方面，我们使用了本实验室开发的EmbedAIRR工具（https://github.com/csi-greifflab/embedairr）。这些嵌入被用作SN10的输入，将其架构转换为一个前馈神经网络，输入维度为1,280，10个隐藏单元和1个输出单元——最后2层与原始SN10设计保持一致。在确认针对SN10的训练方案不会导致基于PLM的SN10模型过拟合后，我们采用了上述相同训练方案。基于Transformer和基于PLM的SN10的汇总结果见补充表4和补充表5。

## 基于信息论的计算

JSD是衡量两个概率分布之间不相似性的度量。它源自Kullback–Leibler（KL）散度，并通过以下公式计算：

JSD(P||N) = sqrt( [KL(P||M) + KL(N||M)] / 2 ),

KL(P||M) = sum_{x in X} P(x) log [ P(x) / M(x) ],

M = (P + N) / 2.

在我们的研究中，P和N分别表示正数据和负数据序列的概率分布。作为衡量正数据集与负数据集边际分布总体差异（即不包括统计相互作用差异）的指标，我们使用了PWM（位置权重矩阵），它表示每个氨基酸在结合序列或非结合序列中特定位置出现的概率。这里，X指PWM位置的集合，x对应于PWM中的一列，代表特定序列位置。在我们的设定中，JSD是每个位置上JSD的总和。JSD使用scipy.spatial.distance包计算。PWM使用Biopython的bio.motifs包计算<sup>77</sup>。

## 归因分析

为了更好地理解SN10学到的规则，我们采用可解释性技术并将其应用于测试集示例，以评估每个序列输入特征的重要性；这里的重要性指对预测的贡献。我们使用来自Captum库v.0.5.0（参考文献78）的DeepLIFT<sup>48</sup>实现，作为一种近似积分梯度<sup>79</sup>的快速方法。该计算需要基线序列，基线序列通过对输入序列进行随机重排获得，这种技术在文献中被称为洗牌方法<sup>80</sup>。尽管在某些应用中使用零输入向量作为基线是常见且合理的，但在序列的情况下，这是有问题的，因为零输入向量不代表任何序列，也就是说，不存在一个序列会被独热编码为零输入向量。洗牌方法基于随机序列，并且是近期文献中生物序列的首选方法<sup>80,81</sup>。

我们为每个CDRH3序列生成了十个洗牌版本，并对每个序列运行了十次DeepLIFT，每次分别对应一个洗牌基线。最终归因值通过对这十次运行结果求平均获得。归因是针对预测的logits（而非输出）进行估计的。我们使用局部归因<sup>82</sup>，因为我们感兴趣的是每个序列中每个氨基酸对预测的影响。在Captum<sup>78</sup>中实现此计算涉及将multiply_by_inputs设置为‘True’。归因分析应用于合成数据和实验数据。然而，由于实验数据集中没有每个氨基酸的结合能数据，我们只能在合成数据集中将归因与每个残基的实际能量进行比较。归因在所有重复中计算，但‘vs1’除外，由于数据集数量多得多，我们限制每个数据集计算一次。

## 基于表位的分析

在基于表位的分析中，我们生成了新的数据集，并在每种情况下将正数据集限制为仅包含与抗原的主要（即最常见）表位结合的序列。对于此分析，我们选择了包含足够数量表位特异性序列的抗原，以便训练集大小与基于抗原的分析相同（Ntrain = 30,000）。然而，由于序列可用性较低，测试集大小不得不相对于基于抗原的分析进行缩减（Ntest = 6,000）。由于训练集大小的限制，我们不得不将基于表位的分析限制在三个抗原：1HOD、1WEJ和1OBL。在我们所有的工作流程和结果中，为了区分基于抗原和基于表位的分析，我们用相同的抗原ID后跟‘E1’（表示最常见表位）来标示基于表位的数据集：1HODE1、1WEJE1和1OBLE1。为了生成训练集和测试集，我们过滤并调整了正数据集，仅保留只与主要表位结合的序列，并保持与相应基于抗原分析相同的负数据集。生成相应数据集后，我们执行了与正文中所示基于抗原分析相同的计算。

## Absolut!结合能计算

关于结合能计算的详细说明，我们请读者参考Absolut!<sup>77</sup>。简而言之，在三维晶格中，只有非共价结合的相邻氨基酸才被认为发生相互作用。然后通过将Miyazawa–Jernigan势能对每个相互作用的残基对求和来计算结合能。通过对CDRH3残基参与的所有相互作用的Miyazawa–Jernigan势能求和，计算该残基对CDRH3–抗原结合能的能量贡献。

## 实验性抗体-抗原结合数据集

### 实验数据集

我们确定了一个公开可用的实验数据集<sup>49</sup>，该数据集是为使用下一代测序、核糖体展示和亲和力筛选技术进行高通量抗体发现而生成的，在本文中称为‘Porebski数据集’或‘实验数据集’。该技术生成抗体文库的结合动力学数据，可用于推导抗体亲和力的度量，从而进行筛选。荧光标记的抗原在高亲和力结合物周围积累，并处理在不同抗原浓度下获取的图像，以根据荧光强度推导出每个序列的空间积分信号，该信号与亲和力相关。该研究的作者对两个抗HER2抗体文库进行了筛选，一个文库（HER2affmat）通过G98A（一种低亲和力抗HER2单链可变区片段，scFv）的亲和力成熟产生，另一个文库（HER2mllib）具有更高亲和力抗体，是使用在HER2affmat上训练的蛋白质语言模型生成的。为了处理更高亲和力的抗体，我们使用了HER2mllib。

## 参考文献

- 71. Izmailov, P., Podoprikhin, D., Garipov, T., Vetrov, D. & Wilson, A.G. Averaging weights leads to wider optima and better generalization. Preprint at https://arxiv.org/abs/1803.05407 (2018).
- 72. Athiwaratkun, B., Finzi, M., Izmailov, P. & Wilson, A.G. There are many consistent explanations of unlabeled data: why you should average. Preprint at https://arxiv.org/abs/1806.05594 (2018).
- 73. Paszke, A. et al. PyTorch: an imperative style, high-performance deep learning library. Preprint at https://arxiv.org/abs/1912.01703 (2019).
- 74. Lin, Z. et al. Evolutionary-scale prediction of atomic-level protein structure with a language model. Science 379, 1123–1130 (2023).
- 75. Leem, J., Mitchell, L. S., Farmery, J. H. R., Barton, J. & Galson, J. D. Deciphering the language of antibodies using self-supervised learning. Patterns 3, 100513 (2022).
- 76. Barton, J., Galson, J.D. & Leem, J. Enhancing antibody language models with structural information. Preprint at bioRxiv https://doi.org/10.1101/2023.12.12.569610 (2024).
- 77. Cock, P. J. A. et al. Biopython: freely available Python tools for computational molecular biology and bioinformatics. Bioinformatics 25, 1422–1423 (2009).
- 78. Kokhlikyan, N. et al. Captum: a unified and generic model interpretability library for PyTorch. Preprint at https://arxiv.org/abs/2009.07896 (2020).
- 79. Sundararajan, M., Taly, A. & Yan, Q. Axiomatic attribution for deep networks. In Proc. 34th International Conference on Machine Learning (eds Precup, D. & Teh, Y. W.) 3319–3328 (PMLR, 2017).
- 80. Novakowski, G., Dexter, N., Libbrecht, M. W., Wasserman, W. W. & Mostafavi, S. Obtaining genetics insights from deep learning via explainable artificial intelligence. Nat. Rev. Genet. 24, 125–137 (2023).
- 81. Huang, D. et al. Weakly supervised learning of RNA modifications from low-resolution epitranscriptome data. Bioinformatics 37, i222–i230 (2021).
- 82. Ancona, M., Ceolini, E., Öztireli, C. & Gross, M. Towards better understanding of gradient-based attribution methods for deep neural networks. Preprint at https://arxiv.org/abs/1711.06104 (2017).
- 83. Ursu, E. & Minnegalieva, A. Training data composition determines machine learning generalization and biological rule discovery. Zenodo https://doi.org/10.5281/zenodo.11191740 (2024).
- 84. Porebski, B. Rapid discovery of high-affinity antibodies via massively parallel sequencing, ribosome display and affinity screening. Zenodo https://doi.org/10.5281/zenodo.8241732 (2023).

## 作者贡献

V.G.构思了这项研究。V.G.、A.M.和E.U.设计了分析和可视化。A.M.、E.U.、P.R.和P.A.R.执行了分析和可视化。M.C.在统计问题上提供咨询。V.G.、A.M.和E.U.撰写了论文初稿。所有作者均修改了手稿并批准其内容。鉴于贡献完全平等，A.M.和E.U.可自由在各自简历中将各自的名字列在首位。

## 利益冲突

V.G.在aiNET GmbH、Enpicom B.V、Absci、Omniscope和Diagonal Therapeutics担任顾问委员会成员。V.G.还担任Adaptive Biosystems、Specifica Inc、Roche/Genentech、immunai、LabGenius和FairJourney Biologics的顾问。其他作者声明无利益冲突。

## 补充信息

本文的扩展数据可在 https://doi.org/10.1038/s42256-025-01089-5 获取。

补充信息 在线版本包含补充材料，可在 https://doi.org/10.1038/s42256-025-01089-5 获取。

通讯和材料请求应联系Victor Greiff。

同行评审信息 《自然·机器智能》感谢Tianxu Lv和另一位匿名审稿人对本工作的同行评审所做的贡献。

重印和许可信息可在 www.nature.com/reprints 获取。

出版商注 施普林格·自然对已出版地图和机构隶属关系中的管辖权主张保持中立。

施普林格·自然或其许可方（例如协会或其他合作伙伴）根据与作者或其他权利持有人的出版协议拥有对本文的专有权；作者对本文接受手稿版本的自存档仅由该出版协议和适用法律的条款管辖。

© 作者，2025，根据与施普林格·自然有限公司的独家许可

## 致谢

我们感谢Leona M.和Harry B. Helmsley慈善信托基金（编号2019PG-T1D011，授予V.G.）、UiO世界领先研究社区（授予V.G.）、UiO：生命科学融合环境Immunolingo（授予V.G.和G.K.S.）、欧盟Horizon 2020 iReceptorplus（编号825821；授予V.G.）、挪威癌症协会基金（编号215817，授予V.G.）、挪威研究理事会项目（编号300740和331890，授予V.G.）、挪威研究理事会IKTPLUSS项目（编号311341，授予V.G.和G.K.S.）以及Kristian Gerhard Jebsen基金会（K.G. Jebsen乳糜泻研究中心，授予G.K.S.）。本项目从创新药物计划2联合事业（Innovative Medicines Initiative 2 Joint Undertaking）获得资金（授予V.G.），资助协议编号101007799（Inno4Vac）。该联合事业获得欧盟Horizon 2020研究与创新计划和EFPIA的支持。本通讯反映作者观点，IMI、欧盟、EFPIA或任何关联伙伴均不对其中所含信息的任何使用负责。由欧盟资助（ERC，AB-AG-INTERACT，101125630，授予V.G.）。本项目根据Marie Skłodowska-Curie资助协议编号801133（授予P.R.）从欧盟Horizon 2020研究与创新计划获得资金。
