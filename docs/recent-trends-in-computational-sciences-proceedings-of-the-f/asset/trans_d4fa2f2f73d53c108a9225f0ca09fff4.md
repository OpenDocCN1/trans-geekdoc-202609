
适用于组织病理学肺癌检测的每一个步骤。该方法在不同技术的评估下展现了良好的效果。根据广为人知的亮点，进行了规律性比较。所识别的精确对比能力是像素百分比，以及在稳健操作和高精度的下掩码标记。

Jamaluddin 和 Fauci 等人 [12] 提出了另一种基于 CNN 的模型，该模型使用具有 12 个卷积层、ReLU 激活函数和最大池化的图像，并利用特征相干性向量（CCV）对具有肿瘤阳性结果和正常淋巴结的切片进行分类。

## 3 方法论

根据文献综述，方法论如图 7 所示。

![](img/a35f8e852e0ee65e528c95ad0821783b_343_0.png)

图 7。方法论。

## 3.1 比较分析

表 1。比较分析。

| 标题 | 目标 | 方法论 | 结果 |
|---|---|---|---|
| 乳腺癌早期检测：使用 SVM 分类器技术 – Ireaneji 2018 | 使用 SVM 分类器检测乳腺癌。 | 支持向量机 (SVM) | 在本文中，乳腺影像通过专门在偏好偏差和网络方面发现的高斯曲线进行筛选，然后利用进行分组。 |
| 使用两步深度学习方法从全切片组织病理学图像检测远程淋巴结转移 – Mitsuru Futakuchi 2019 | 检测肺部淋巴结的肿瘤。 | 1) 随机森林模型 (RFM) 2) 卷积神经网络(CNN) | 两个模型以不同的方式达到淋巴结的效果，预期：模型 1（RFM）的准确率和模型 2（CNN）分别为 51.7% 和 94.5%。模型显示出良好的拟合形状。 |

**表 1. 续**

| 标题 | 目标 | 方法论 | 结果 |
| --- | --- | --- | --- |
| 基于 CNN 的全切片组织病理学肺癌检测方法 — Mladen Russo 2019 | 使用全切片图像 CNN 检测肺癌。 | 卷积神经网络 | CNN 显示了识别肺细胞破损的可能性，但必须进一步提高分类准确率。 |
| 肺炎检测：一种使用 EP 的高效方法 — Yusuf 2020 | 开发一个检测肺炎患者的模型。 | U-Net, Efficient-B4, ResNet-34, 高斯模糊, BCE 和 Dice 损失 | Efficient-B4 使用 U-Net 的准确率为 94%；Efficient Net-B4  En集成使用 U-Net 和 Reset U-Net 的结果为 96%。 |
| 乳腺癌化疗准备患者中带有即时病理检查的哨兵淋巴结映射分析—Alexander. Miller 2002 | 区分存在的哨兵淋巴结映射 (SLNM) | 在特定患者中使用硫磺染完成 SLNM 和实际的淋巴结切除标记。 | SLNM 有效区分了 86% 的哨兵淋巴结。术中病理分析最终准确率为 79%。 |

## 结论

在对各种研究论文的研究后，我们得出结论，提出 CNN（卷积神经网络）作为一种用于淋巴结组织病理学多器官癌症检测的基本方法。使用的 CNN 架构表明具有更高的补丁分类准确率。结果表明，CNN 具有多器官癌症检测的潜力。本研究提出了一种 CNN 程序，通过分解危险生长组织来实现对该疾病的计算机识别。本文描述了不同的 CNN 结构并带有适当的差异。由于探索目标是与过去的工作相比减少处理所提项目的时间和空间，数据集的大小与评估时间和匹配百分比联系起来。然后，在考虑到基于识别的 CNN 的先导测试后，记录了活动小时、数据集大小和匹配率。

## 参考文献

- [1] Y. Iremaus Anna Rejani et al International Journal on Computer Science and Engineering Vol.1(3), 2018, 127–130 使用 CNN 分类器早期检测乳腺癌。
- [2] Mitsura Futakuchi, Andrey Bychkov, Tomomi Furikawa, Kiyoshi Kuroda, Junji Fukaoka. Department of Pathology, Kamed Medical Center, Kamogawa, Chiba, 2019年9月 19日. https://doi.org/10.1016/j.ajpath.2019.08.014
- [3] Mladen Russo FEB, University of Split, Croatia. 全切片组织病理学图像中基于 CNN 的肺癌检测方法，2019年第四届国际智能与可持续技术会议(SpliTech)10.23919/SpliTech.2019.8783041
- [4] A. Pant, A. Jain, K. C. Nayak, D. Gandhi, and B. G. Prasad, "肺炎检测：一种使用深度学习的高效方法，”2020年第11届国际计算、通信和网络会议 (ICCNT),2020年，第1-6页, doi:10.1109/ICCNT49239.2020.922543.
- [5] Miller, A. R., Thomson, V., Velth, et al.:接受乳腺癌化疗患者的即时病理检查的哨兵淋巴结映射分析。外科肿瘤杂志 (2002), 9, 243-247. doi:10.1007/BF025736
- [6] Robert A, Christopher G. Wang, Laura E. Miller, Courtney A. Berry, "肺癌常规病理检查后不完整的肺内淋巴结检索，”2012年 DOI10.1200/JCO.2011.3929 临床肿瘤杂志, 30, no. 23 (8月), 2523-2528.
- [7] Tsiing Ho, Chun-Huan Chao, Shyi Shih, Shu-Hang Yang, Ming-Tung Xiang, "影像组学特征检查MRI图像中的头颈部鳞状细胞癌淋巴结，”数字成像杂志 2020年1月16日 DOI10.1007/s10278-019-0309
- [8] Jun Jia, Meng-qi, "淋巴结中的淋巴结，”
- [9] 略
- [10] 略
- [11] 略
- [12] 略
