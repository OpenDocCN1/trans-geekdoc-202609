
和多样性。为了检查使用所提出 GAN 模型生成的图像质量，使用 TensorFlow-GAN (TF-GAN) 库计算 IS。

以下是除 inception 分数之外用于评估 GAN 生成图像的最有效指标之一。本文采用了 Müller 等人 [50] 给出的以下三个参数的实现。

## 11.4.2.3 峰值信噪比 (PSNR)
该比率表示生成的图像与原始图像相比的质量。它是原始图像的最大像素功率与原始图像和生成图像之间噪声的比率。

## 11.4.2.4 结构相似性指数度量 (SSIM)
SSIM 是一种评估指标，用于计算两幅图像之间的相似度。它基于亮度、对比度和结构这三个关键特征来比较图像。

## 11.4.2.5 均方根误差 (RMSE)
RMSE 显示观测数据点与模型预测值之间的接近程度。它基于值之间的偏差进行评估。

## 11.4.3 结果
在数字和字符数据集上对上述架构进行训练和测试后，获得了以下结果。

### 11.4.3.1 特征编码
数字和字符数据集的 EEG 信号特征使用 CNN 进行编码，如第 11.3.1 节所述。训练好的 EEG 分类器在数字和字符的测试数据集上进行了测试。本工作实现了数字的 EEG 分类准确率为 75.06%，字符数据集为 73.09%。

本工作将数字和字符数据集的 EEG 分类准确率与 Kumar 等人 [49] 和 Tirupattur 等人 [18] 模型的 EEG 分类准确率进行了比较。如表 11.2 所示，所提出的 EEG 分类器在准确率上有所提升。

## 表 11.2
### EEG 分类准确率比较
| 数据集 | Kumar et al. [49] | Tirupattur et al. [18] | 拟议方法 |
|---|---|---|---|
| 数字 | 68.45 | 72.88 | 75.06 |
| 字符 | 66.91 | 71.18 | 73.09 |

## 表 11.3
### 不同数据集的图像分类准确率
| 数据集 | 精度 (%) |
|---|---|
| 数字 | 99.44 |
| 字符 | 99.46 |

### 11.4.3.2 图像分类
图像分类器使用深度卷积神经网络进行训练，如第 11.3.2 节所述，并实现了数字数据集的图像分类准确率为 99.44%，而字符数据集的准确率为 99.46%，如表 11.3 所述。

### 11.4.3.3 图像生成
第 11.3.2 节中训练的图像分类器与 GAN 的判别器一起使用。通过利用此训练好的 GAN，从其 EEG 信号为数字和字符数据集生成图像。所提出 GAN 的输出图像如图 11.9 所示。

![](img/a2fc2296b12812e9151e817bff1de16d_222_0.png)

图 11.9 由拟议 GAN 生成的 EEG 信号图像 – (a) 数字 (b) 字符

对于数字数据集，使用 TF-GAN 库使用额外评估指标——即 IS——对生成的数字图像进行评估，得到的值为 9.88。生成的图像使用第 11.4.2 节中讨论的不同评估指标进行评估。数字和字符数据集的这些指标所得值见表 11.4。

本工作使用从相应 EEG 记录中提取的特征生成了数字和字符的图像。EEG 特征编码器使用 CNN 架构开发以对 EEG 信号进行分类。该 EEG 特征编码器实现了更高的分类准确率，有助于从 EEG 信号中捕获更好的特征。之后，深度卷积神经网络被训练并用于对图像进行分类。判别器使用此图像分类器以实现更好的学习。所提出的 GAN 生成了数字和字符的逼真图像。然而，本工作仅限于数字和字符类别。

## 表 11.4
### 拟议 GAN 的不同评估指标
| 数据集 | PSNR | SSIM | RMSE |
|---|---|---|---|
| 数字 | 34.41 | 0.6481 | 0.0194 |
| 字符 | 32.66 | 0.7266 | 0.0237 |

## 11.5 结论与未来工作
本工作提出了一种从脑信号生成逼真图像的方法。在该方法中，从 EEG 信号中提取特征以获取重要信息，这些提取的特征和原始图像被用作训练 GAN 的输入。训练好的 GAN 模型使用 EEG 信号作为输入生成逼真图像，从而正确地解释人类思想。EEG 编码器的准确性在生成逼真图像方面发挥了重要作用。所提出的模型在数字和字符数据集上分别实现了 75.06% 和 73.09% 的 EEG 分类准确率。该模型在 EEG 分类准确率方面取得了成功。

本工作尝试生成数字和字符的逼真图像。它可以进一步改进以可视化整个单词或句子，而不仅仅是单个字符。通过尝试可以更准确地对 EEG 信号进行分类的不同模型，仍有进一步改进的空间。也可以尝试改进生成图像的质量。本工作可以进一步扩展以使用其相应的 EEG 信号生成各种物体的逼真图像以及场景。

## 致谢
我们感谢计算机工程与信息技术系，COEP Tech 为实施本工作提供 GPU 服务器设施。该设施是在 TEQIP-III（世界银行项目）下建立的。

## 参考文献
- 1. Yang, Delong, et al. “基于深度学习的 EEG 信号图像生成综述。” 收录于 2021 International Symposium on Biomedical Engineering and Computational Biology, 2021.
- 2. Seeliger, Katja, et al. “用于从脑活动重建自然图像的生成对抗网络。” NeuroImage 181 (2018): 775–785.
- 3. Essa, Almabrok, and Hari Kotte. “基于脑信号分析的深度学习方法：非侵入性脑信号研究最新进展。” arXiv preprint arXiv:2201.04229 (2021).
- 4. Kangassalo, Lauri, Michiel Spapé, and Tuukka Ruotsalo. “用于生成匹配感知类别图像的神经自适应建模。” Scientific Reports 10(1) (2020): 14719.
- 5. Ling, Shouyu, et al. “视觉词是如何表示的？基于 EEG 的视觉词解码、特征推导和图像重建的见解。” Human Brain Mapping 40(17) (2019): 5056–5068.
- 6. Qiao, Kai, et al. “基于 BigGAN 的人类脑活动自然图像贝叶斯重建。” Neuroscience 444 (2020): 92–105.
- 7. Hayashi, Ryusuke, and Hayaki Kawata “使用生成对抗网络从猕猴下颞皮层记录的神经活动重建图像。” 收录于 2018 IEEE International Conference on Systems, Man, and Cybernetics (SMC). IEEE, 2018.
- 8. Chaurasiya, R. K., S. K. Arvind, and Saket Garg. “用于从标准 EEG 特征生成图像的对抗自编码器。” 收录于 2020 First International Conference on Power, Control and Computing Technologies (ICPC2T). IEEE, 2020.
- 9. Lee, Yonggun, and Yufei Huang. “通过条件生成对抗网络从脑信号生成 RSVP 实验的目标/非目标图像。” 收录于 2018 IEEE EMBS international conference on Biomedical & Health Informatics (BHI). IEEE, 2018.
- 10. Hatipoglu, Bahar, Cagatay Murat Yilmaz, and Cemal Kose. “一种用于 EEG 和 MEG 信号分类的信号到图像转换方法。” Signal, Image and Video Processing 13(3) (2019): 483–490.
- 11. An, Yang, Hak Keung Lam, and Sai Ho Ling. “使用生成对抗网络对 EEG 信号进行自动去噪。” Sensors 22(5) (2022): 1750.
- 12. Rakhimberdina, Zarina, et al. “使用深度学习从 fMRI 重建自然图像：综述。” Frontiers in Neuroscience 15 (2021): 795488.
- 13. Brock, Andrew, Jeff Donahue, and Karen Simonyan. “用于高保真自然图像合成的大规模 GAN 训练。” arXiv preprint arXiv:1809.11096 (2018).
- 14. Odena, Augustus, Christopher Olah, and Jonathon Shlens. “使用辅助分类器 GAN 的条件图像合成。” 收录于 International Conference on Machine Learning. PMLR, 2017.
- 15. Shimizu, Hirokatsu, and Ramesh Srinivasan. “改进从 EEG 信号想象图像的分类和重建。” PLOS ONE 17(9) (2022): e0274847.
- 16. Wan, Zitong, et al. “EEG 信号分析中迁移学习的综述。” Neurocomputing 421 (2021): 1–14.
- 17. Merlin Praveena, D., D. Angelin Sarah, and S. Thomas George. “EEG 信号应用的深度学习技术综述。” IETE Journal of Research 68(4) (2022): 3030–3037.
