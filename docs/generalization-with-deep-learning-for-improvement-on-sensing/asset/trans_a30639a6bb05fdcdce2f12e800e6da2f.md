

我们的方法在两个公开的视频异常检测数据集上进行了评估，即上海科技大学 [[17](#chap6.xhtml#fsr17)] 和 CUHK Avenue [[16](#chap6.xhtml#fsr16)]。我们将我们提出的 Normal Graph 与利用 RNN 预测未来关节并重建当前关节的 MPED-RNN [[24](#chap6.xhtml#fsr24)] 进行比较。所有实验均在帧级 AUC 指标上进行评估。

### 4.1 数据集

**上海科技大学数据集** [[17](#chap6.xhtml#fsr17)] 是一个新的大规模异常检测数据集，记录于校园内的多个地点。该数据集中定义的异常可由人类和车辆引起。之前的工作 [[24](#chap6.xhtml#fsr24)] 从上海科技大学中划分出一个仅包含与人类相关异常的子集，命名为 HR-ShanghaiTech，将在本文中使用。我们也在该子集上评估我们的方法。

**CUHK Avenue 数据集** [[16](#chap6.xhtml#fsr16)] 也是一个流行的异常检测数据集，记录于地铁的一个单一视角。我们也提取其中与人类相关的异常并命名为 HR-Avenue。

### 4.2 实现细节

我们利用 Alpha-Pose [[19](#chap6.xhtml#fsr19)] 为视频中的每一帧提取骨架。我们遵循参考文献 [[24](#chap6.xhtml#fsr24)] 中使用的跟踪算法，该算法将稀疏光流与骨架相结合。对于 ST-GCN 的配置，我们遵循参考文献 [[8](#chap6.xhtml#fsr8)] 中的设置，由 9 个 ST-GCN 层组成。前三层、接下来的三层和最后三层分别具有 64、128 和 256 个通道。Resnet 机制应用于每个 ST-GCN。

### 4.3 与最先进方法的比较

在本节中，我们将 Normal Graph 与基于外观的方法 [[1](#chap6.xhtml#fsr1), [2](#chap6.xhtml#fsr2), [17](#chap6.xhtml#fsr17), [32](#chap6.xhtml#fsr32)] 以及基于骨架的方法 [[24](#chap6.xhtml#fsr24)] 进行比较。图 [Table 1](#chap6.xhtml#tab1) 所示的结果表明，基于骨架的方法在 AUC 上优于基于外观的方法，尤其是在 HR-ShanghaiTech 数据集上，其中异常仅与人类相关。我们认为基于外观的方法会在重建 [[1](#chap6.xhtml#fsr1), [17](#chap6.xhtml#fsr17)] 或预测 [[2](#chap6.xhtml#fsr2)] 过程中引入背景噪声。此外，我们的方法优于使用 RNN 建模骨架关系的 MPED-RNN，而我们的方法利用时空图卷积网络在图上建模关系。总之，我们提出的方法在上海科技大学 (ST)、HR-ShanghaiTech (HR-ST) 和 CUHK Avenue 上实现了最先进的 AUC 和 EER，这证明了我们方法的有效性。

**Table 1:** The performance of different baselines on ShanghaiTech (ST), Human-Related ShanghaiTech (HR-ST) and CUHK HR-Avenue.

![figure](images/p148-1.jpg)

### 4.4 ST-GCN 的数量

我们进一步对 ST-GCN 的数量进行消融研究，以探索 ST-GCN 的机制。9 个 ST-GCN 的输出通道设置为 64、64、64、64、128、128、128、256、256，分别。ST-GCN 的数量逐渐增加，并且始终使用全连接层进行预测。如 [Fig. 3](#chap6.xhtml#fig3) 所示，随着 ST-GCN 数量的增加，CUHK Avenue 数据集上的性能逐渐提高。尤其是，当 ST-GCN 的数量为 9 时，在 CUHK Avenue 数据集上达到最佳性能。我们假设更深的 ST-GCN 模型会造成优化困难，其中一些工作 [[33](#chap6.xhtml#fsr33)] 提出了残差机制来增加 GCN 的层数，这超出了本文的范围。

### 4.5 ST-GCN 的有效性

为了进一步研究我们提出方法的有效性，我们引入了一个仅包含 9 个全连接层的基线，以及另一个仅包含空间 GCN 的基线。为了公平比较，9 个全连接层的维度与 9 个基于 ST-GCN 的 Normal Graph 相同。如 [Table 2](#chap6.xhtml#tab2) 所示，仅堆叠几个全连接层会导致性能急剧下降。这证明全连接层无法显式表征人体关节的时空关系，而 GCN 能够通过特定的邻接矩阵对这种复杂关系进行建模。此外，仅具有空间连接而没有时间连接的 GCN 无法很好地表征跨时间的关系，导致性能略有下降。

![figure](images/p149-1.jpg)

**Figure 3:**The performance of Normal Graph on the CUHK Avenue dataset when changing the number of ST-GCNs.

**Table 2:** The demonstration of the effectiveness of our proposed normal graph.

|  || **CUHK Avenue** |
| --- | --- |
| 9 Fully connected layers || 0.802 |
| --- | --- |
| Normal Graph without temporal connection || 0.857 |
| Normal Graph || 0.873 |

![figure](images/p150-1.jpg)

**Figure 4:**The visualization on the HR–ST dataset.

### 4.6 Normal Graph 的演示

为了进一步分析我们的方法，我们在 HR-ST 数据集上可视化从视频片段中分数归一化后的分数。如 [Fig. 4](#chap6.xhtml#fig4) 所示，我们提出的 Normal Graph 可以很好地检测 HR 异常。此外，我们发现失败案例通常发生在一些细微动作和遮挡场景中，这些场景无法通过关节很好地捕捉。

### 4.7 异常检测的可视化

我们还在 HR-ST 数据集和 HR-Avenue 数据集上可视化了一些成功检测的结果，如 [Figs. 5](#chap6.xhtml#fig5) 和 [6](#chap6.xhtml#fig6) 所示。可视化显示，异常行为的行人无法在关节位置方面得到很好预测，而正常情况则预测良好。

![figure](images/p151-1.jpg)

**Figure 5:**The detection results on the HR–ST dataset. The red boxes denote the abnormal regions. Best viewed in color.

![figure](images/p152-1.jpg)

**Figure 6:**The detection results on the HR Avenue dataset. The red boxes denote the abnormal regions. Best viewed in color.

### 4.8 真阳性率和假阴性率的分析

除了对 AUC 的测量外，我们还提供了在设定一定阈值 (0.5) 以确定帧是否正常或异常时，真阳性率 (TPR) 和假阳性率 (FPR) 的分析。我们在 HR-ST 数据集上进行此类实验，发现 TPR 为 0.76，FPR 为 0.37。

我们还发现，骑自行车的人很容易被我们提出的基于骨架的方法遗漏，因为他们看起来与行走的行人非常相似。因此，可以通过结合基于图像的解决方案和基于骨架的解决方案来处理此类问题。我们将其留待未来研究。

## 5. 结论

用于视频异常检测的基于图像级重建或预测的方法可能会引入背景噪声。为了最小化背景的影响，我们通过结合多个时空图卷积网络和预测模块的基于骨架的预测网络来解决这个问题。通过仅在训练集上的正常数据上训练模型，异常事件将以骨架表示自动被发现。据我们所知，这是首次将图卷积网络应用于基于骨架的视频异常检测。实验表明，与基于图像级重建的方法、基于图像级预测的方法和基于骨架级 RNN 的方法相比，我们提出的 normal graph 实现了最先进的性能。

## References

[1](#chap6.xhtml#fs1).M. Hasan, J. Choi, *et al*., “Learning temporal regularity in video sequences,” in *CVPR*, 2016.

