
-   [系统性能在诸多方面均可提升，这将作为未来工作。此处仅使用轴向（axial）视图的 T2W MRI。多视图（轴向、矢状、冠状）和多协议 MRI（T1W、T2W、FLAIR）可提供更系统的肿瘤特征。因此，通过引入多视图和多协议 MRI，系统的性能可以得到提升。此外，代谢和遗传学数据以及大脑的解剖学属性也可以纳入系统，以实现更准确的肿瘤分级。

*Benchmarking*

本小节对我们提出的方法与已有的先前技术进行对比。文献调查表明，针对脑肿瘤分级的方法非常有限。这主要是由于脑肿瘤分类的困难、缺乏适当的医学数据集以及缺乏金标准（ground truth）信息所致。因此，我们将本方法与表 `Table 4.5` 中列出的有限的现有专注研究进行比较。

**Table 4.5.** Benchmarking: a comparison between existing state-of-the-art techniques.

| C1  || C2 || C3 || C4 || C5 || C6 || C7 || C8 || C9 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| RF || DS || C || P || PP || CT || TPar || ES || HP |
| Pan *et al* (2015) \[[54](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4t5)\] || BRATS 2014 || 2 || NA || Augmentation || 
*   CNN
*   ANN
 || NA || 
*   H/W: NA
*   TP: 5-NA
*   P&V: NA
 || 
*   SE = NA,
*   SP = NA
 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Mohsen *et al* (2018) \[[90](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib90)\] || Harvard Medical School website || 4 || T2W || 
*   Segmentation (fuzzy C-means)
*   feature reduction (PCA)
 || 
*   DNN (seven-layer)
 || NA || 
*   H/W: NA
*   TP: K7 CV
*   P&V: NA
 || 
*   ACC = 96.97%
*   Recall = 97%
*   Precision = 97%
*   F-measure = 97%
*   AUC = 98.4%
 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ari and Hanbay (2018) \[[16](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib16)\] || Kwan R K S *et al* \[[4](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib4)\] || 2 || NA || Image enhanced || 
*   ELM
*   CNN
*   GW
*   SF
 || NA || 
*   H/W: CPU
*   TP: NA
*   P&V: NA
 || 
*   ACC = 97.18%,
*   SE = 96.80%,
*   SP = 97.12%
 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Ge *et al* (2018) \[[57](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib57)\] || 
*   BraTS 2017
*   Mayo Clinic in the USA
 || 3 || 
*   T1W
*   T2W
*   FLAIR
 || Augmentation image enhanced || CNN (seven-layer) || 
*   Epochs = 50
*   LR = 0.0001
*   BS = NA
 || 
*   H/W: CPU,
*   GPU
*   TP: NA
*   P&V: NA
 || ACC = 90.87% |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Anaraki *et al* (2018) \[[58](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib58)\] || REMBRAND TTCGA || 2 || T1W || Raw image || 
*   CNN-1 (seven-layer)
*   CNN-2 (eight-layer)
 || 
*   Epochs = 100
*   LR = 0.0001
*   BS = NA
 || 
*   Study 1 ACC = 90.9%
*   Study 2 ACC = 94.2%
 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Yang *et al* (2018) \[[28](#Chapter_4.xhtml#bk978-0-7503-2244-7ch4bib28)\] || REMBRANDT || 3 || T1W || ROI patching || 
*   Alxnet (eight-layer)
*   GoogLeNet (22-layer)
 || 
*   Epochs = 30
*   LR = 0.1
*   BS = 50
 || 
*   H/W: CPU
*   TP: K5 CV
 || 
*   V. ACC = 86.7%
*   T. ACC = 90.9%
*   AUC = 93.9%
 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Proposed method || REMBRANDT || 2 || T2W || Skull stripping || 
*   CNN
*   AlexNet (eight-layer)
 || 
*   Epochs = 1000
*   LR = 0.0001
*   BS = 128
 || 
*   H/W: CPU
*   TP: K5/K10 CV
*   P&V: Yes
 || 
*   ACC = 99.71% ± 0.93%,
*   SE = 98.75% ± 3.95%,
*   SP = 100.00% ± 0.00%,
*   PPV = 100.00% ± 0.00%,
*   NPV = 99.63% ± 1.17% and
*   AUC = 99.38% ± 1.98%
 |

RN: row no; RF: reference; DS: data source; C: classes; P: MRI protocol; N: no. of patients; PP: pre-processing; CT: classification technique; ES: experimental set-up; HP: highest performance; R#: row no.; C#: column no.; T1W: T1 weighted; T2W: T2-weighted; FLAIR: fluid-attenuated inversion recovery; ACC: accuracy; SE: sensitivity; SP: specificity; AUC: area under curve; DSC: Dice coefficient; ANN: artificial neural network; DWT: discrete wavelet transform; DNN: deep neural network; GW: Gabor wavelets; SF: statistical, feature-based method; NA: not available; H/W: hardware; TP: training protocol; P&V: performance and validation; TPar: training parameters.

### 4.8 Conclusion

本研究提出了一种基于深度学习模型（CNN）的自动脑肿瘤分级工具的新方法。采用转移学习实现了卓越性能。预训练模型使我们能够在样本较少的新问题上重用已学习的特征图，并提高了准确率。此外，转移学习通过在早期任务中获得的知识（权重）使模型更具泛化性。本章选用了预训练的 CNN 模型 AlexNet 进行肿瘤分类。本文使用的脑部 MRI 数据集包含 79 名患者，涉及三种脑肿瘤类型：胶质瘤（AST）、奥利戈细胞瘤（OLI）以及多形性胶质母细胞瘤（GBM）。AST 和 OLI 可分为二级（g2）和三级（g3），而 GBM 仅提供四级（g4）样本。本章进行了三项肿瘤分类实验，包括（i）AST（g2 与 g3）分类，（ii）OLI（g2 与 g3）分类，以及（iii）低级别胶质瘤（LGG）与高级别胶质瘤（HGG）分类。分类性能在 K5 和 K10 交叉验证方案上进行了测试。模型在 K10 方案下对 OLI（g2 与 g3）分类表现最佳，结果如下：ACC（99.71% ± 0.93%）、SE（98.75% ± 3.95%）、SP（100.00% ± 0.00%）、PPV（100.00% ± 0.00%）、NPV（99.63% ± 1.17%）以及 AUC（99.38% ± 1.98%），且 *p* < 0.0001。此外，CNN 分类器的性能还与使用相似数据的第一阶和第二阶统计特征的不同机器学习分类器进行了比较。CNN 分类器在准确率上比 SVM（支持向量机）分类器提升了 13.86%。模型还通过肿瘤分离指数（TSI）和面部生物特征进行了验证。

**Funding:** 本研究未获得外部资金。

**Conflicts of interest:** 作者声明没有利益冲突。

###### Appendix A

**Table A1.** AlexNet architecture.

| Layer # || Layer initial || Layer || Remarks |
| --- | --- | --- | --- |
| 1 || Data || Image input || 227 × 227 × 3 images with ‘zero center’ normalization |
| --- | --- | --- | --- |
| 2 || ‘conv1’ || Convolution-1 || 96 11 × 11 × 3 convolutions with stride \[4 4\] and padding \[0 0 0 0\] |
| 3 || Relu1 || ReLu-1 ||  |
| 4 || Normal1 || Normal-1 || Cross-channel normalization with five channels per element |
| 5 || Pool1 || Max-pooling-1 || 3 × 3 max-pooling with stride \[2 2\] and padding \[0 0 0 0\] |
| 6 || Conv2 || Convolution || 256 5 × 5 × 48 convolutions with stride \[1 1\] and padding \[2 2 2 2\] |
| 7 || Relu2 || ReLu ||  |
| 8 || Normal2 ||  || Cross-channel normalization with five channels per element |
| 9 || Pool2 || Max-pooling || 3 × 3 max-pooling with stride \[2 2\] and padding \[0 0 0 0\] |
| 10 || Conv3 || Convolution || 384 3 × 3 × 256 convolutions with stride \[1 1\] and padding \[1 1 1 1\] |
| 11 || Relu3 || ReLu ||  |
| 12 || Conv4 || Convolution || 384 3 × 3 × 192 convolutions with stride \[1 1\] and padding \[1 1 1 1\] |
| 13 || Relu4 || ReLu ||  |
| 14 || Conv5 || Convolution || 256 3 × 3 × 192 convolutions with stride \[1 1\] and padding \[1 1 1 1\] |
| 15 || Relu5 || ReLu ||  |
| 16 || Pool5 || Max-pooling || 3 × 3 max-pooling with stride \[2 2\] and padding \[0 0 0 0\] |
| 17 || fc6 || Fully connected || 4096 fully connected layers |
| 18 || Relu6 || ReLu ||  |
| 19 || drop6ʹ || Dropout || 50% dropout |
| 20 || fc7 || Fully connected || 4096 fully connected layers |
| 21 || Relu7 || ReLu ||  |
