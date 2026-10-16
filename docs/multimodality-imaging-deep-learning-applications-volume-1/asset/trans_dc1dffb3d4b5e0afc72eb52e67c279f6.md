
-   [提议的TL架构的性能与一种新型DL架构SivaSuriNet进行了比较。SivaSuriNet使用可分离卷积神经网络，并在每个层组合后使用最大池化层。最初使用32个滤波器，随后增加到256个。架构形状像漏斗，如图[5.10](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig10)所示。SivaSuriNet的训练参数详情见表[5.1](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5t1)。

![Figure 5.10. SivaSuriNet architecture.](images/bk978-0-7503-2244-7ch5f10_online.jpg)

**Figure 5.10.** SivaSuriNet architecture.

**Table 5.1.** SivaSuriNet architecture parameters.

| Layer type  || Shape || Parameter # |

| --- | --- | --- |

| Convolution 2D || 128 × × 128 × 32 || 896 |

| --- | --- | --- |

| Batch normalization || 128 × 128 × 32 || 128 |

| Separable convolution 2D || 128 × 128 × 64 || 2400 |

| Batch normalization || 128 × 128 × 64 || 256 |

| Max-pooling 2D || 64 × 64 × × 64 || 0 |

| Separable convolution 2D || 64 × 64 × 128 || 8896 |

| Batch normalization || 64 × 64 × 128 || 512 |

| Max-pooling 2D || 32 × 32 × 128 || 0 |

| Separable convolution 2D || 32 × 32 × 256 || 34176 |

| Batch normalization || 32 × 32 × 256 || 1024 |

| Max-pooling 2D || 16 × 16 × 256 || 0 |

| Separable convolution 2D || 16 × 16 × 64 || 18752 |

| Batch normalization || 16 × 16 × 64 || 256 |

| Max-pooling 2D || 8 × 8 × × 64 || 0 |

| Separable convolution 2D || 8 × 8 × 128 || 8896 |

| Batch normalization || 8 × 8 × 128 || 512 |

| Max-pooling 2D || 4 × 4 × 128 || 0 |

| Separable convolution 2D || 4 × 4 × 256 || 34176 |

| Batch normalization || 4 × 4 × 256 || 1024 |

| Max-pooling 2D || 2 × 2 × 256 || 0 |

| Flatten || 1024 || 0 |

| Dense || 1024 || 1049600 |

| Dropout || 0.5 || 0 |

| Dense || 512 || 524800 |

| Dropout || 0.5 || 0 |

| Dense (softmax) || 2 || 1026 |

| **Total trainable parameters** || **1** **687** **330** |

### 5.5 Results

*TL optimization*

我们通过使用六种TL架构，并对增强折叠从1×到6×进行优化，实现了TL框架的性能优化，并在IV3中取得了最佳准确率。图[5.11](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig11)展示了TL和SivaSuriNet的3D优化及对应数值，详情见表[5.2](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5t2)。我们对所有AI架构采用了K10交叉验证协议（90%训练，10%测试），在IV3中实现了最佳准确率97.82%± 1.52%，平均准确率为91.83% ± 2.23%。

![Figure 5.11. Optimization of TL and SivaSuriNet with augmentation.](images/bk978-0-7503-2244-7ch5f11_online.jpg)

**Figure 5.11.** Optimization of TL and SivaSuriNet with augmentation.

**Table 5.2.** 3D optimization of TL architectures and SivaSuriNet (asterisks represent the highest and second highest accuracy values).

| Model || Balanced || Aug 2× || Aug 3× || Aug 4× || Aug 5× || Aug 6× || Mean ± SD |

| --- | --- | --- | --- | --- | --- | --- | --- |

| AlexNet || 79.98 ± 4.18 || 71.10 ± 32.60 || 67.21 ± 63.63 || 69.81 ± 47.52 || 62.49 ± 4.10 || 68.05 ± 3.25 || 71.94 ± 2.71 |

| --- | --- | --- | --- | --- | --- | --- | --- |

| DenseNet121 || 89.36 ± 17.76 || 75.766 ± 33.29 || 68.39 ± 46.16 || 81.41 ± 40.50 || 74.47 ± 15.50 || 72.39 ± 25.12 || 78.74 ± 4.70 |

| XceptionNet || 69.30 ± 17.78 || 65.33 ± 42.60 || 62.1 ± 35.01 || 61.87 ± 30.04 || 57.81 ± 15.56 || 52.72 ± 25.52 || 64.67 ± 3.05 |

| InceptionV3 || 85.98 ± 4.06 || **91.83 ± 2.23\*** || 89.40 ± 2.53 || 85.41 ± 2.13 || 86.23 ± 1.13 || 79.51 ± 3.25 || 88.16 ± 1.74 |

| ResNet50 || 50.86 ± 4.18 || 46.35 ± 2.70 || 48.24 ± 3.41 || 53.90 ± 2.48 || 50.34 ± 5.35 || 51.55 ± 5.45 || 49.84 ± 1.79 |

| SivaSuriNet || 83.57 ± 4.03 || 90.79 ± 2.76 || 85.23 ± 6.35 || **90.96 ± 4.63\*** || 87.49 ± 5.35 || 89.58 ± 2.58 || 87.64 ± 2.28 |

| Mean+SD || 76.45 ± 7.71 || 73.53 ± 8.90 || 70.10 ± 8.11 || 73.89 ± 8.51 || 67.81 ± 8.56 || 67.52 ± 6.25 ||  |

我们使用K10交叉验证协议比较了TL性能与SivaSuriNet，SivaSuriNet实现了98.43% ± 1.45%的最佳准确率，平均准确率为90.96% ± 4.63%。SivaSuriNet在最佳准确率组合中提高了0.62%，且平均准确率相当。我们还计算了所有AI架构的曲线下面积（AUC），结果如图[5.12](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig12)所示。

![Figure 5.12. ROC analysis of six AI models.](images/bk978-0-7503-2244-7ch5f12_online.jpg)

**Figure 5.12.** ROC analysis of six AI models.

### 5.6 Characterization

我们假设白质高信号（WMH）在WD中高于对照组，为验证该假设，我们使用了两种策略：(i) AI基于的特征强度（MFS）和(ii)基于更高阶谱（HOS）的信号处理技术，即双谱（bispectrum）。

#### 5.6.1 Mean feature strength

AI基于的MFS \[[37](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib37)\]是一种新颖的技术，用于计算DL模型在每一层学习到的特征的强度。MFS仅从DL模型中计算，因为TL模型在初始和中间层使用ImageNet特征，因此不适合计算特征强度。因此，我们使用了经过训练的SivaSuriNet权重来计算MFS。这里我们对最佳准确率组合的所有训练图像进行处理，并在每一层计算每张图像的特征强度。计算完特征强度后，我们计算了所有训练图像在每一层的特征强度的平均值。图[5.13](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig13)展示了SivaSuriNet的MFS，并表明WD的MFS高于对照组21.57%，因此我们得出结论 MFS (WD) > MFS (control)。

![Figure 5.13. Mean feature strength of SivaSuriNet.](images/bk978-0-7503-2244-7ch5f13_online.jpg)

**Figure 5.13.** Mean feature strength of SivaSuriNet.

#### 5.6.2 Higher-order spectrum

为验证MFS，我们选择了一种非AI技术，即通过计算相同的组合（用于计算MFS的组合）的bispectrum（B）来进行信号处理。这里我们对每张图像在0°到180°之间以15°的步长随机旋转，计算了每张图像的平均B值。图[5.14](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig14)(a)展示了训练图像在0°到180°之间每个角度的平均B值，步长为15°。图[5.14](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig14)(b)展示了WD在最佳角度60°时的HOS。HOS的结果与MFS类似，WD的双谱高于对照组9.24%。

![Figure 5.14. (a) Mean bispectrum analysis. (b) Higher-order spectra of WD.](images/bk978-0-7503-2244-7ch5f14_online.jpg)

**Figure 5.14.** (a) Mean bispectrum analysis. (b) Higher-order spectra of WD.

### 5.7 Discussion

在本节中，我们讨论了与现有工作的对比。首先介绍了WD的特征描述，然后讨论我们的主张、所提工作的优势和劣势，最后给出结论和未来工作。

我们的研究是首个在WD分类中使用优化的TL范式并结合增强学习进行的工作。我们将其性能与新型架构SivaSuriNet进行了比较。两种架构的性能相似，但IV3的表现比SivaSuriNet高0.94%。

*Benchmarking*

