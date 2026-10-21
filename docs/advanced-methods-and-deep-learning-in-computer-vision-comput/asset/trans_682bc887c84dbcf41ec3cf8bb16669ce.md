
![](img/fe161b7f6e96e35e7e853eece52c6dce_134_0.png)

图 2.17 不同 γ 的 Focal Loss 可视化。设置 γ > 0 会降低良好分类样本（p_t > 0.5）的损失，更加关注难以分类的样本。

$$CE(p, y) = \begin{cases} -\log(p) & \text{if } y = 1 \\ -\log(1 - p) & \text{otherwise,} \end{cases}\tag{2.14}$$

其中 $y \in \{\pm1\}$ 是真实标签，$p = p(y = 1|x) \in [0, 1]$ 是类别 $y = 1$ 的概率。定义 $p_t$ 为

$$p_t = \begin{cases} p & \text{if } y = 1 \\ 1 - p & \text{otherwise.} \end{cases}\tag{2.15}$$

这可以表示为 $CE(p, y) = CE(p_t) = -\log(p_t)$，并在图 2.17 中绘制（顶部蓝色曲线，$\gamma = 0$）。可以观察到，容易分类的样本（例如 $p_t \gg 0.5$）仍然具有非平凡的损失幅度。当训练样本大部分较容易时，它们会主导总体损失，压倒困难样本的贡献。

Focal Loss 通过插入可调参数 $\gamma \ge 0$ 的调制因子 $(1 - p_t)^\gamma$ 来泛化 CE 损失，

$$FL(p_t) = -(1 - p_t)^\gamma \log(p_t).\tag{2.16}$$

该因子改变损失，如图 2.17 所示。对于较小的 $p_t$（困难样本），损失变化不大，而对于较大的 $p_t$（简单样本），损失会更快衰减至零，尤其是在 $\gamma$ 值较大时。因此，简单样本对总体损失的贡献更小。例如，当 $\gamma = 2$ 时，$p_t = 0.9$ 的简单样本在 focal 下的贡献比在交叉熵损失下低 100 倍。降权速率由超参数 $\gamma$ 控制，$\gamma$ 越大，降权越重，如图 2.17 所示。实践中发现 $\gamma = 2$ 通常效果最佳。

一般来说，focal loss 由另一个超参数 $\alpha$ 平衡，$$FL(p_t) = -\alpha_t (1 - p_t)^\gamma \log(p_t).\tag{2.17}$$

表示方法、数据增强技术、损失函数等。虽然如表 2.1 所示，这些贡献使得性能得到大幅提升，但目标检测器仍然远非完美。大量文献也存在于本综述未涵盖的主题中，例如实例分割、域适应或低复杂度深度学习架构等。最后，目标检测经常被用作许多其他视觉任务的初步阶段，包括姿态估计、图像和视频描述，或视觉问答等。总之，虽然当前的目标检测器比十年前有效数个数量级，但在这个对计算机视觉至关重要的问题上仍有大量研究工作需要完成。

## 参考文献

Cai, Z., Fan, Q., Feris, R.S., Vasconcelos, N., 2016. A unified multi-scale deep convolutional neural network for fast object detection. In: ECCV, pp. 354–370.
Cai, Z., Vasconcelos, N., 2021. Cascade R-CNN: high quality object detection and instance segmentation. IEEE Transactions on Pattern Analysis and Machine Intelligence 43 (5), 1483–1498.
Dalal, N., Triggs, B., 2005. Histograms of oriented gradients for human detection. In: CVPR, pp. 886–893.
Dollár, P., Appel, R., Belongie, S.J., Perona, P., 2014. Fast feature pyramids for object detection. IEEE Transactions on Pattern Analysis and Machine Intelligence 36 (8), 1532–1545.
Everingham, M., Gool, L.J.V., Williams, C.K.I., Winn, J.M., Zisserman, A., 2010. The Pascal visual object classes (VOC) challenge. International Journal of Computer Vision 88 (2), 303–338.
Felzenszwalb, P.F., Girshick, R.B., McAllester, D.A., Ramanan, D., 2010. Object detection with discriminatively trained part-based models. IEEE Transactions on Pattern Analysis and Machine Intelligence 32 (9), 1627–1645.
Girshick, R.B., 2015. Fast R-CNN. In: ICCV, pp. 1440–1448.
Girshick, R.B., Donahue, J., Darrell, T., Malik, J., 2014. Rich feature hierarchies for accurate object detection and semantic segmentation. In: CVPR, pp. 580–587.
He, K., Zhang, X., Ren, S., Sun, J., 2014. Spatial pyramid pooling in deep convolutional networks for visual recognition. In: ECCV, pp. 346–361.
He, K., Zhang, X., Ren, S., Sun, J., 2016. Deep residual learning for image recognition. In: CVPR, pp. 770–778.
Krizhevsky, A., Sutskever, I., Hinton, G.E., 2012. Imagenet classification with deep convolutional neural networks. In: NIPS, pp. 1106–1114.
Lazebnik, S., Schmid, C., Ponce, J., 2006. Beyond bags of features: spatial pyramid matching for recognizing natural scene categories. In: CVPR. IEEE Computer Society, pp. 2169–2178.
Lin, T., Dollár, P., Girshick, R.B., He, K., Hariharan, B., Belongie, S.J., 2017a. Feature pyramid networks for object detection. In: CVPR. IEEE Computer Society, pp. 936–944.
Lin, T., Goyal, P., Girshick, R.B., He, K., Dollár, P., 2017b. Focal loss for dense object detection. In: ICCV. IEEE Computer Society, pp. 2999–3007.
Lin, T., Maire, M., Belongie, S.J., Hays, J., Perona, P., Ramanan, D., Dollár, P., Zitnick, C.L., 2014. Microsoft COCO: common objects in context. In: ECCV, pp. 740–755.
Liu, W., Anguelov, D., Erhan, D., Szegedy, C., Reed, S.E., Fu, C., Berg, A.C., 2016. SSD: Single Shot Multibox Detector. ECCV, vol. 9905. Springer, pp. 21–37.
Lowe, D.G., 1999. Object recognition from local scale-invariant features. In: ICCV. IEEE Computer Society, pp. 1150–1157.
Lowe, D.G., 2004. Distinctive image features from scale-invariant keypoints. International Journal of Computer Vision 60 (2), 91–110.
Papageorgiou, C., Oren, M., Poggio, T.A., 1998. A general framework for object detection. In: ICCV. IEEE Computer Society, pp. 555–562.
Redmon, J., Divvala, S.K., Girshick, R.B., Farhadi, A., 2016. You only look once: unified, real-time object detection. In: CVPR, pp. 779–788.
Ren, S., He, K., Girshick, R.B., Sun, J., 2017. Faster R-CNN: towards real-time object detection with region proposal networks. IEEE Transactions on Pattern Analysis and Machine Intelligence 39 (6), 1137–1149.

本页特意留空

## 有限监督下的学习

### 静态和动态任务

Sujoy Paul a,c and Amit K. Roy-Chowdhury b

aGoogle Research, Bangalore, India bUniversity of California, Riverside, Electrical and Computer Engineering, Riverside, CA, United States

- 降低计算机视觉模型的监督对于可扩展性和适应性很重要。
- 我们回顾了为有限监督学习提出的各种方法，并提供了证明这些方法的实验结果。

最近计算机视觉的成功大多围绕使用大量精细标注的数据来训练识别模型。然而，在现实世界中，获取这样的大型数据集需要大量的人工标注，这可能很费力、超出预算，甚至容易出错。然而，每天产生的大量真实数据可以以低成本或零标注成本获取。此类数据可以是未标注的，也可以包含标签/元数据信息，称为弱标注。我们的目标是开发能够从此类数据中学习识别模型的方法，其中涉及有限的人工监督。在本章中，我们将探讨有限监督学习的两个维度——首先，减少学习识别模型所需的人工标注数据量，其次，减少

c 这项工作是在作者在 UC Riverside 时完成的。

监督水平从强到弱，该监督可以从网络中挖掘、从预言机中轻松查询，或作为从领域知识推导的基于规则的标签施加。

在有限监督学习的第一个维度中，我们表明，自然数据中经常存在的上下文信息可用于减少所需的标注数量。在第二个维度——减少监督水平——我们使用弱标签代替密集强标签，用于学习密集预测任务。我们讨论了使用弱标签学习视频中动作检测和图像上语义分割模型域适应的框架。所有这些讨论的任务在本质上都是静态的。继续沿着从弱标签学习的方向，我们探索了序列决策问题，其中下一个输入取决于当前输出。我们研究了通过将复杂任务分解为子目标，使用少量专家人类演示学习机器人任务的问题。这些方法的详细解释如下。

## 3.2 上下文感知的积极学习

近年来，由于技术的进步，每天产生大量视觉和文本数据，这些数据大多未标注用于学习机器学习模型。此外，机器学习算法在人类生活中变得越来越普遍。这些算法很大一部分基于监督学习，需要大量数据进行标注。此外，随着新数据的可用，这些模型需要随着时间的推移进行更新，以便动态适应可能随时间漂移的不同语义概念。手动标注这种连续的数据流不仅对人类来说是一项繁琐的任务，而且容易出现错误标注。在这种情况下，可能更有优势只标注信息丰富的数据点，而不标注携带冗余信息的数据点。这种直觉在作品（Lapedriza et al., 2013）中得到支持，该作品表明并非所有数据点都携带相同数量的信息，选择最具信息量的数据点甚至可能比标注未标注数据集中的所有数据点带来更好的性能。主动学习在文献中研究了几十年，已显示出在选择信息丰富的数据点和减少人工标注工作方面具有巨大潜力。

### 3.2.1 主动学习

主动学习（Settles, 2012）被提出为减少人工标注量而不损害识别性能的解决方案。主动学习的图示概述见图 3.1。给定一个大型未标注数据集，主动学习方法首先选择一小部分随机数据并查询人类专家以获得其标签。这些数据点用于学习手头的任务的预测模型。这是初始模型。下一步是从未标注集合中仅选择一小部分数据点，以获得尽可能多的信息。基于当前模型的 불确定性、数据密度等，在这些未标注样本上定义信息效用分数。这些分数用于选择要标注的样本。一般来说，主动学习方法具有人类在环的迭代特性，即计算信息分数、查询人类以获得标签，然后用新的标注
