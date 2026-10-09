
## 参考文献

9. F. Maestri et al., “A multicenter study of the early detection of synaptic dysfunction in mild cognitive impairment using magnetoencephalography-derived functional connectivity,” NeuroImage Clin., vol. 9, pp. 103–109, 2015.
10. J. P. Amezquita-Sanchez, A. Adeli, and H. Adeli, “A new methodology for automated diagnosis of mild cognitive impairment (MCI) using magnetoencephalography (MEG),” Behav. Brain Res., vol. 305, pp. 174–180, 2016.
11. S. Yang and F. Deravi, “Novel HHT-based features for biometric identification using EEG signals,” 2014 22nd Int. Conf. Pattern Recognit., pp. 1922–1927, Aug. 2014.
12. H. Aghajani, E. Zahedi, M. Jalili, A. Keikharavi, and B. V. Vahdat, “Diagnosis of early Alzheimer’s disease based on EEG source localization and a standardized realistic head model,” IEEE J. Biomed. Heal. Informat., vol. 17, no. 6, pp. 1039–1045, 2013.
13. J. A. Pineda-Pardo et al., “Guiding functional connectivity estimation by structural connectivity in MEG: An application to discrimination of conditions of mild cognitive impairment,” Neuroimage, vol. 101, pp. 765–777, 2014.
14. J. Guillon et al., “Loss of brain inter-frequency hubs in Alzheimer’s disease,” Sci. Rep., vol. 7, no. 1, pp. 1–14, 2017.
15. S. I. Dimitriadis et al., “How to build a functional connectomic biomarker for mild cognitive impairment from source reconstructed MEG resting-state activity: The combination of ROI representation and connectivity estimator matters,” Front. Neurosci., vol. 12, no. JUN, pp. 1–21, 2018.
16. C. Babiloni et al., “Functional cortical source connectivity of resting state electroencephalographic alpha rhythms shows similar abnormalities in patients with mild cognitive impairment due to Alzheimer’s and Parkinson’s diseases,” Clin. Neurophysiol., vol. 129, no. 4, pp. 766–782, 2018.
17. S. Yang and F. Deravi, “On the usability of electroencephalographic signals for biometric recognition: A survey,” IEEE Trans. Human-Machine Syst., vol. 47, no. 6, pp. 958–969, 2017.

## 第9章 机器学习在医学影像中的一些实际挑战及其可能的解决方案

Naimul Khan, Nabila Abraham, Anika Tabassum, and Marcia Hon
Ryerson University
Toronto, Canada

### 目录

9.1 引言 147
9.2 利用自然图像进行迁移学习 149
9.3 用于类别不平衡的Focal Tversky损失函数 152
9.4 用于置信度调整的贝叶斯神经网络 156
9.5 结论 161
笔记 161
参考文献 162

### 9.1 引言

机器学习的最新进展已在医学影像和计算机辅助诊断领域催生了广泛的应用。最近，由于用于部署先进模型的软件易于获取，深度学习方法变得非常流行。虽然研究表明，利用卷积神经网络（CNN）的深度模型在准确性方面甚至超越了人类专家，但存在一些实际问题阻碍了此类机器学习系统在实践中的广泛部署。本章重点讨论其中的三个问题：

1. 对训练数据规模的显著依赖：现代机器学习方法，尤其是深度学习，依赖于可用的训练数据量。对于医疗应用而言，这构成了一个问题，因为在医疗保健中获取大量标记训练数据成本高昂。此外，对大量训练数据的依赖导致了对昂贵计算资源的依赖，使得该技术对于资金不足的医疗中心而言难以普及。

2. 类别不平衡：标签类别中样本数量显著减少会导致监督学习中的类别不平衡。类别不平衡在计算机辅助诊断或分割应用中非常常见。例如，在分割中，通常只有少量像素被标记为前景（如肿瘤或病变），而其余像素为背景。这导致了严重的类别不平衡，传统机器学习算法 [1] 难以处理。

3. 置信度调整：大多数机器学习方法及其在计算机辅助诊断中的应用仅报告准确率/F1分数作为性能指标。然而，对于医疗应用，置信度度量会使领域专家对系统感到更加放心，而一个简单的用于调整置信度-准确率权衡的工具将非常有用 [2]。

在本章中，我们强调了Ryerson多媒体研究实验室在过去3年内开展的三项处于前沿水平的研究工作。这三个项目通过应用新颖的方法、架构和算法，解决了上述三个问题。

在第9.1节中，我们强调了如何通过利用迁移学习 [3,4] 来减少 against 大训练集的依赖。我们表明，使用基准数据集中的自然图像来学习低级特征，并使用智能数据过滤机制通过医疗数据仅训练深度网络的高层，可以替代使用大型医疗训练数据集。我们在先进的ADNI数据集 [5] 上展示了结果。我们的结果表明，迁移学习仅通过通常需要的一小部分训练数据即可帮助提高阿尔茨海默病诊断的准确性。

在第9.2节中，我们展示了如何通过一种新颖的损失函数 [6] 来解决类别不平衡问题，在该函数中，我们利用Tversky指数 [7] 在精确率和召回率之间取得平衡。我们将Tversky指数纳入焦点损失函数 [1] 中。实验结果表明，我们在乳腺超声病变分割方面达到了最先进的结果。

最后，在第9.3节中，我们提出了一种用于乳腺癌诊断的可调贝叶斯神经网络，其中两个可调参数可以调整以达到令人满意的置信度-准确率权衡。我们提供了可调参数如何影响置信度和准确度的分析。

### 9.2 利用自然图像进行迁移学习

在本节中，我们表明，在医学领域中，我们可以简单地使用现有的大型自然图像数据集来学习低级特征，从而减少对大型训练数据集的依赖。然后，通过一种基于熵的智能数据过滤技术，我们可以减少对大型医疗数据集的依赖 [1]。为了展示迁移学习的应用，我们选择了阿尔茨海默病诊断领域，该领域最近应用机器学习时显示出有希望的结果 [8]。

在2010年代初，统计机器学习方法在阿尔茨海默病诊断方面已显示出有希望的结果 [9]。深度学习方法（如CNN和自编码器）的近期普及将注意力转向了深度学习。然而，大多数现有的深度学习方法是从零开始训练架构的。这种从头开始训练在应用于医疗应用时存在几个问题 [10]：(1) 深度网络通常具有数百万个可学习参数，需要大量的标记数据才能正确优化。在医疗领域，获取如此大量的标记数据成本高昂。(2) 拥有数百万个参数带来了另一个问题，模型可能会过拟合/欠拟合，导致在训练数据上表现良好，但在未见数据上表现不佳。(3) 使用如此大量的数据训练深度网络需要大量昂贵的GPU，这对于资金不足的医疗中心来说是不可持续的。

通过迁移学习对深度CNN进行微调是一种最近流行的方法，可以替代从头训练 [11]。

尽管在医疗领域获取标注数据很难，但在自然图像领域中，有许多带有标注对象的基准数据集可用于解决计算机视觉问题。一个这样的例子是ImageNet数据集 [12]。迁移学习的基本思想是不从头开始训练。相反，我们训练一个CNN，其参数已经从自然图像数据集（如ImageNet）中学习。该网络仅仅是重新训练以获得来自不同领域的新知识（例如阿尔茨海默病的计算机辅助诊断）。研究表明，CNN在学习低级特征方面非常优秀，并可以在大型训练集上泛化图像特征。如果我们始终从头开始训练网络，那么关于自然图像的广泛研究和为此类问题创建的稳健架构就没有得到适当的利用。

在本节中，我们研究如何将自然图像中学到的知识转移到阿尔茨海默病诊断问题上。重用自然图像中所学知识的动机是减少对训练集大小的过度依赖。由于CNN的流行，研究人员在过去的几年中精心设计了许多用于解决视觉分类问题的既定架构。视觉分类领域最流行的基准之一是ImageNet大规模视觉识别挑战（ILSVRC）。在该挑战中，提供了超过100万张带有1,000种不同对象标注的图像 [12]。由于该挑战的流行，该挑战的获胜网络架构通常经过精心设计并经过彻底测试。对于这项研究，我们仔细探索了上述挑战的获胜者，以挑选最适合当前问题的架构。我们决定利用VGG [13]。选择VGG是因为其易于复用的架构，由多个卷积层组成，后接全连接层 [13]。通常，网络利用ImageNet等自然图像数据集从头开始训练。然后，卷积层被冻结。仅全连接层针对新的问题域重新训练。

然而，随机缩小训练数据的大小将无助于捕获数据中最好的可能变化，这是避免过拟合/欠拟合所必需的。为了选择最好的训练集，我们利用图像熵，它为我们提供了包含在一个图像（在我们的情况下是体积MRI图像的一个切片）中的信息量的相对度量。

通常，对于具有概率 $p_{1}, p_{2}, \dots, p_{M}$ 的 $M$ 个符号集合，熵可以计算如下：
