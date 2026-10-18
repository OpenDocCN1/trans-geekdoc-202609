

再次，K. H. Leung *et al.* \[10\] 提出了一种混合方法，用于基于“第 0 年”和“第 1 年”数据预测“第 4 年”的“MDS-UPDRS-III”评分。该特征从“DAT-SPECT”图像中提取，使用适合医疗数据 \[41–43\] 的“Google InnceptionnV3”模型 \[40\]。然后，开发了一种基于“LSTM”的架构，用于从“第 0 年”和“第 1 年”的“MDS-UPDRS-III”中提取特征。然后，这些特征向量与患者详细信息（如“age”和“gender”）相连接，并转发到“Fully Connected Layer”以预测最终结果。所提 \[10\] 方法的高级架构如 [Figure 9.16](#c09.xhtml#fig9-16) 所示。

![Figure 9.15 Architecture of deep learning technique for Parkinson’s \[9\].](images/fig9-15.jpg)

[**Figure 9.15**](#c09.xhtml#rfig9-15) Architecture of deep learning technique for Parkinson’s \[9\].

该方法作为三项研究进行实验，并使用“10-fold cross validation”进行评估。研究一在图像数据上使用“InceptionV3”，获得了“MAE”为 4.33 ± 3.36，研究二在“MDSUPDRS-III”数据上使用“LSTM”，获得了“MAE”为 3.71 ± 2.91，研究三同时使用两者，获得了“MAE”为 3.22 ± 2.71 \[10\]。该模型的基于图像的方法已被非基于图像的方法取代，但可以清楚地看出，结合图像和非基于图像数据的混合方法优于任何单一方法。

Veronica Munoz Ramırez *et al.* \[11\] 提出了一种深度学习方法，使用自动编码器和一种称为“anomaly scoring”的技术，基于“quantitative Magnetic Resonance Imaging”数据对 PD 患者进行分类。

数据从“Parkinson Progression Markers Initiative database”导入。从该数据中提取了两个特征，即“mean diffusivity”和“fractional anisotropy”。该方法实现了三种基于自动编码器的模型，即“Spatial Auto encoder”（缩写为“sAE”）、“Spatial Variational Autoencoder”（缩写为“sVAE”）和“Dense Variational Autoencoder”（缩写为“dVAE”），并使用 ROC 曲线作为性能指标进行评估。该模型获得了最佳结果，分别为“sAE”、“sVAE”和“dVAE”的“Area Under Curve”或“AUC”为 0.83、0.80 和 0.74 \[11\]。

![Figure 9.16 Architecture of MDS-UPDRS \[10\].](images/fig9-16.jpg)

[**Figure 9.16**](#c09.xhtml#rfig9-16) Architecture of MDS-UPDRS \[10\].

### 9.6.3 Detection of Attacks on Deep Brain Stimulation

Jonathan Pugh *et al.* \[12\] 提出了一项关于深部脑刺激（DBS）中脑劫持及其自主性的概念性研究。作者绘制了三个假设性案例研究，以解释脑机接口（BCI）中脑劫持的可能性。该研究还讨论了在开发先进的 BCI 应用程序（如神经植入物，如 DBS）时必须遵循的责任和伦理。

Heena Rathore *et al.* \[13\] 提出了一种算法，用于预测第三方对 DBS 的不同攻击。该方法使用 LSTM（LSTM-RNN）来预测和预测 RTV，RTV 是一种有助于评估神经系统疾病强度的特征。该模型的开发理念是识别 DBS 中电极电荷的重复模拟与真实模拟之间的差异。在对 PD 患者各种类型攻击的检测进行测试时，该模型能够完成检测，并能够通知患者可能发生攻击的情况。所提方法包括两项研究，其中研究 1 使用均方根误差作为性能指标进行评估，获得了 0.095 的 RMSE 分数，研究 2 分析了模型在不同攻击下的性能，基于训练损失、验证损失和训练持续时间，其中，它获得了最佳结果。

## 9.7 Results and Discussion

阿尔茨海默病（AD）领域的大多数研究工作都使用基于计算机视觉的方法。最常用的数据集是 ADNI，在某些情况下，它作为独立数据集使用，在某些情况下，它与其他标准数据集（如 OASIS 和 BIOCARD）结合使用。最常用的深度学习算法是基于 CNN 的算法。有些工作中，CNN 用于分类，而在某些混合方法中，特征提取任务由 CNN 架构处理，然后传递给分类算法（如 SVM 或 AdaBoost）来处理分类问题。[Table 9.2](#c09.xhtml#tab9-2) 显示了基于准确率的 AD 检测所提算法的比较。

对于 PD 检测，已实现了各种方法；然而，我们又可以看到，迁移学习方法在少量数据下表现出良好的准确率。\[10\] 中提出的工作使用了一种并行混合方法来检测 PD，使用神经影像数据和临床数据。PD 检测中各种算法的比较如 [Table 9.3](#c09.xhtml#tab9-3) 所示。

[Table 9.4](#c09.xhtml#tab9-4) 列出了一个用于预测 DBS 攻击的检测模型的最终结果。该研究领域仍在不断发展，有许多创新空间。这类模型不仅可以用于 DBS，还可以用于确保 BCI 设备的安全性。这种新型架构在检测 DBS 过程中的各种模拟攻击时能够实现最小误差值。

## 9.8 Conclusion

神经系统疾病每年影响着全球大量人口 \[44\]。由于早期检测对治疗至关重要，也是一项非常具有挑战性的任务，因此智能系统与医学专家的结合在检测中发挥着至关重要的作用。在本章中，回顾了一些在检测和治疗协议安全强制执行方面的先进深度学习模型。在 AD 检测方面，大多数工作都使用了基于 CNN 的方法，并且与其他深度学习模型相比，报告了更好的准确率。一些先进的新方法（非基于图像的方法，如 \[6\] 以及在移动加速度计数据上应用 1D CNN）显示出有希望的结果，并为尚未探索的新研究领域开辟了道路。在 PD 分类中，用于 PD 检测的常用数据集是 PPMI 数据库。很明显，基于并行方法 \[10\] 的模型已显示出卓越的性能。我们也可以说，迁移学习方法有助于在最少数据下实现最大准确率。尽管 DBS 为 PD 治疗带来了希望，但它也带来了自身的重大威胁。必须重视使用此类设备引发的安全问题，因为它可能直接影响患者的身体和精神定向。此外，我们还回顾了一种新型架构 \[13\]，用于检测深部脑刺激器的攻击，该架构能够高效地检测不同的攻击模式。这类方法对于确保 BCI 的安全使用至关重要。总之，本研究回顾了一些与 AD 和 PD 相关的重要数据集、先进深度学习算法在检测中的应用，以及在使用 BCI 的先进神经退行性疾病治疗中确保安全的问题。

[**Table 9.2**](#c09.xhtml#rtab9-2) Comparison of various algorithms on detection of AD.

| **S. no.** | **Proposed algorithm** | **Dataset** | **Results** |
| --- | --- | --- | --- |
| 1 | 1D – Convolutional Neural Network \[3\] | AFAC Daycare Dataset | ACCURACY - 91% |
| 2 | ResNet50 and Support Vector Machine \[4\] | ADNI | ACCURACY - 78.64% |
| | | OASIS | ACCURACY - 86.81% |
| 3 | V-Net and 3D DenseNet \[5\] | ADNI | ACCURACY 88.9% (AD vs. NC) and 76.2% (MCI vs. NC) |
| 4 | DCssCDBM \[6\] | Bejing Easy Monitor Technology Dataset | ACCURACY - 95.04% |

