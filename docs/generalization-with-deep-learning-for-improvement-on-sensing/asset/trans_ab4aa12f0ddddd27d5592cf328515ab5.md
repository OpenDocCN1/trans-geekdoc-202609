

`PT`、`PF`、`NT`、`NF` 来自 [表 5](#chap8.xhtml#tab5) 中所示的混淆矩阵。`PT` 表示正真，表示预测和真实值均为建成区的样本数量。`PF`、`NF` 和 `NT` 根据其预测和真实值具有与 `PT` 相似的含义。用户精度和生产者精度分别关注建成区对应的虚警率和漏警率。其他两个指标关注整体分割精度。总体而言，总体精度表示整幅图像的分割精度。平均 IOU 表示建成区和非建成区 IOU 的平均值。这些指标是图像分割任务中最常用的指标，前三个指标在分类任务中也很常用。

**表 5.** 混淆矩阵。

![](images/p195-2.jpg)

这些算法在大小为 `2048 × 2048` 的测试图像上进行了验证，该大小如上所述考虑了时间消耗。首先，FCN 模型与几种无监督建成区提取算法进行了比较，它们分别是 CGEO [[30](#chap8.xhtml#fsr30)]、基于 Harris 角点的 MHEC [[63](#chap8.xhtml#fsr63)]、各向异性旋转不变纹理度量 PanTex [[32](#chap8.xhtml#fsr32)]，以及 MBI [[33](#chap8.xhtml#fsr33)]。MBI 主要用于提取建筑物，因此添加了高斯平滑并用于提取建成区，其中尺度参数 `s` = 2 + `i` *5(`i` = 0−5)。PanTex、MHEC 和 MBI 均为基于阈值的算法，而 CGEO 为基于图的算法，利用超像素来降低复杂度。此外，根据实际测试遥感图像分辨率，所有算法的结果均去除了面积小于 2,500 像素的小区域。此外，FCN 模型的结果也以单输出形式展示，这意味着 FCN 模型仅输出一个通道。结果显示在 [图 10](#chap8.xhtml#fig10) 和 [表 6](#chap8.xhtml#tab6) 和 [7](#chap8.xhtml#tab7) 中。

其次，选择了几种有监督算法进行比较。Weizman 和 Goldberger [[38](#chap8.xhtml#fsr38)] 提出了一种基于视觉词 VW 的方法。Tao *et al*. [[35](#chap8.xhtml#fsr35)] 提出了一种结合多核学习和图割的城市区域检测方法 MKL+GC。Li *et al*. [[31](#chap8.xhtml#fsr31)] 采用多核学习、多场集成和多假设投票来完成该工作 MMM。所有三个模型均使用与深度模型相同的训练集进行训练。结果显示在 [图 11](#chap8.xhtml#fig11) 和 [表 8](#chap8.xhtml#tab8) 和 [9](#chap8.xhtml#tab9) 中。

根据实验结果，所提出的深度模型与无监督和有监督的传统算法相比具有明显优势。需要指出的是，结果统计为像素级，但所提出的深度模型本质上是块级检测。实际上，深度模型并非在每个测试图像的所有指标上都最优，例如，MMM 算法在图像 8 上获得了最高的 User.Acc，而 MKL + GC 算法在 Prod.Acc 方面几乎在整个测试集上胜出。然而，MMM 仅在图像 8 上表现最佳，其在两个测试图像上的 Overall.Acc 可能相差超过 10%，这反映了其不稳定性。对于 MKL + GC 算法，其在 Prod.Acc 上的胜利是以不可接受的虚警为代价的。总体而言，所提出的深度模型在保持稳定性的同时实现了高检测精度，表明其具有良好的泛化能力。另一方面，得益于 GPU 的强大性能，所提出的深度模型比传统算法快数十倍甚至数千倍，这对于大规模遥感图像处理至关重要。

![](images/p197-1.jpg)

**图 10:** 无监督算法与我们方法比较的结果，每行对应一幅 2048 × 2048 像素的测试图像。

**表 6:** 无监督算法与我们方法的评估指标。

![](images/p198-1.jpg)

**表 7.** 无监督算法与我们方法的时间消耗。

![](images/p199-1.jpg)

![](images/p200-1.jpg)

**图 11:** 有监督算法与 FCN 比较的结果，每行对应一幅 2048 × 2048 像素的测试图像。

**表 8:** 有监督算法与我们方法比较的评估指标。

![](images/p201-1.jpg)

**表 9:** 有监督算法与我们方法的时间消耗比较（s）。

![](images/p202-1.jpg)

## 9. 结论

如今，深度学习理论取得了巨大进展，并在机器学习的许多子领域占据主导地位，GPU 的快速发展使得利用深度模型快速处理大量遥感数据成为可能，因此深度学习技术将成为建成区提取的主流。在 FCN 模型与经典算法的对比实验中，无论是精度指标还是时间消耗指标，FCN 模型都占据绝对优势。

尽管深度模型性能优异，建成区提取仍面临诸多挑战。例如，深度模型的训练需要大量涵盖尽可能多情况的标注样本，因此小样本深度学习值得关注。此外，遥感数据来源众多，研究深度模型在不同数据源间的泛化能力具有价值。另一方面，一般应用深度方法于建成区提取时可获得块级结果，因此快速细化建成区边界需要更多关注。总之，将深度学习应用于建成区提取仍需更多研究。

## 参考文献

[1](#chap8.xhtml#fs1). L. Gueguen *et al*., “Urbanization detection by a region based mixed information change analysis between built-up indicators,” *IEEE J. Sel. Topics Appl. Earth Observ. Remote Sens*., vol. 6, no. 6, pp. 2410–2420, 2013.

[2](#chap8.xhtml#fs2). H. Khurshid and M. F. Khan, “Segmentation and classification using logistic regression in remote sensing imagery,” *IEEE J. Sel. Topics Appl. Earth Observ. Remote Sens*., vol. 8, no. 1, pp. 224–232, 2015.

[3](#chap8.xhtml#fs3). M. Pesaresi *et al*., “Toward global automatic built-up area recognition using optical VHR imagery,” *IEEE J Sel Top Appl Earth Obs Remote Sens*., vol. 4, pp. 923–934, 2011.

[4](#chap8.xhtml#fs4). M. Pesaresi *et al*., “A global human settlement layer from optical HR/VHR RS data: Concept and first results,” *IEEE J. Sel. Topics Appl. Earth Observ. Remote Sens*., vol. 6, no. 5, pp. 2102–2131, 2013.

[5](#chap8.xhtml#fs5). N. Li *et al*., “A novel technique based on the combination of labeled co-occurrence matrix and variogram for the detection of built-up areas in high-resolution SAR images,” *Remote Sens*., vol. 6, pp. 3857–3878, 2014.

[6](#chap8.xhtml#fs6). D. Xiang *et al*., “Built-up area extraction from PolSAR imagery with modelbased decomposition and polarimetric coherence,” *Remote Sens*., vol. 8, pp. 685–705, 2016.

[7](#chap8.xhtml#fs7). S. Bouzekri, A. A. Lasbet, and A. Lachehab, “A new spectral index for extraction of built-up area using Landsat-8 data,” *Ind J Remote Sens*., vol. 43, pp. 867–873, 2015.

8. D. Kaimaris and P. Patias, “Identification and area measurement of the built-up area with the built-up index (BUI),” *Int J Adv Remote Sens*., vol. 5, pp. 1844–1858, 2016.

[9](#chap8.xhtml#fs9). A. Varshney and E. Rajesh, “A comparative study of built-up index approaches for automated extraction of built-up regions from remote sensing data,” *Ind J Remote Sens*., vol. 42, pp. 659–663, 2014.

