
- iv. **TIMIT 语音数据库** [38] 包含来自 8 种不同方言的 630 个音频（192 名女性和 438 名男性）。每个说话人提供了 5 分钟的演讲，并以 16 kHz 录制。在法医环境中，这些演讲异常长且充满噪声。此外，困惑的语音和嫌疑人的语音是通过大量通道获取的。对于每个说话人，在 8 kHz 下采样了三次演讲，在 16 kHz 下采样了惊人的七次演讲。这从几个通道之一生成了模拟语音。为了创建 10 dB、20 dB 和 30 dB 的噪声模式，我们将这些模式应用于这些演讲中以模拟总噪声。为了教育性别模式，使用了所有女性演讲和所有男性演讲。我们的实验结果编译在具有 2.5 GHz Core i5 处理器和 8 GB 内存的笔记本电脑上。实验平台为 `MATLAB R2012b`。

- v. **NIST SRE-2010 评估数据库** 用于表征 i-vector 机器的平均。尽管我们的设备已经进化到处理更广泛的录音、语音模式和声道条件 [9]，但这项工作重点是手机试验，这种情况似乎与法医案例最相关。使用 NIST 分发的专家截止日期扩展中心测试，它产生了比完美测试记录具有更高的错误维度记录，后者包含较少的测试。如果使用 NIST SRE-2008 存档进行排名校准会更好。然而，由于这用于 i-vector 系统的开发，他们将 SRE-2010 扩展列表一分为二，其自有的 24 个说话人。说话人识别数据集如表 10.2 所示。

### 10.7.2 数据集

研究人员提供了各种数据集和方法来提供问题的解决方案，我们将在下面讨论其中一些。

- i. **NSDSEA**：使用来自噪声库的 4620 个 TIMIT 语音文件训练神经网络。在常用的目标上进行了比较，特别是感知语音质量 (`PESQ`)、短时目标可懂度 (`STOI`) 以及井田村-Saito (`IS`)。语音的保护在法医中至关重要，因此我们也在 NSDSEA 上对 3035 个语音文件使用了 `WER`，测试集覆盖 1.2 小时。

- ii. **REVERB** 用于训练来自 REVERB 数据集的双通道模拟文件，以及来自 REVERB 数据集的八通道集和来自 DIH-WSJ 数据集的六通道阵列。研究人员在使用 `ESP` 工具包进行多通道 ASR 时使用了著名的设置。作为特征，基线 E2E ASR 采用八维对数滤波器系数 [28]。

#### 表 10.2 说话人识别数据集

| 任务 | 引用 | 数据集 | 方法 | 结果 |
| :--- | :--- | :--- | :--- | :--- |
| 说话人识别 | [35] | IITG 多变性说话人数据库用于十个说话人 [32] | `MFCC`, `SOFM`, `MLP-BR` | 准确率 93.33%，没有 `SOFM` 的 `MLP-BR` 准确率为 46.6% |
| | [36] | Kaggle 和乌尔德语语料库、巴基斯坦地区语言语料库 (`CRP`) 和法医说话人语料库 | 使用的技术包括 `MFCC`、频谱、`DNN`、`x-vectors-GMM-UBM`、`i-vectors-GMM-CNN`、`GMM-SVM`、`VGGVox` | ISR 准确率 90.4%。AC 准确率 35.4%，LI 准确率 90.2%，结合 AC 和 LI 的准确率为 95.1% |
| | [23] | KSU 语音数据库 [13] | `MFCCs`, `GMM-UBM` | 识别率 97.8% `EER` 1.98% |
| | [38] | TIMIT 语音数据库 [35]，630 个音频（192 名女性和 438 名男性），采样率为 16 kHz | `WCC`, `i-vector` 和 `CDS`。 | `WCCIDCS` = 95.48% 准确率 |
| | [39] | NIST SRE-2010, 2008 SER, `Foacal` 工具包 | `i-vector` | `EER` = 24.23% |

# 社交媒体中的网络犯罪

# 表 10.3 语音增强数据集

| 任务 | 引用 | 数据集 | 方法 | 结果 |
| --- | --- | --- | --- | --- |
| 语音增强 | [27] | NSDSEA 数据集，4,620 个 TIMIT 语库语音文件 [31]，Hu 语库，Libri Speech 语库。`REVERB`, `DIRHA-WS`, `ESPNet` 工具包 [34] | `MFCC`, `DNN` | 20.34% |
| | [28] | | `CD`, `LLR`, `FWEegSNR`, `PESQ`, `STOL`, `WER` 和 `SRMR` | 0.78 和 0.77 |
| | [40] [24] | TIMIT 数据库 [31] 资源管理（可用 `LDC` [40]），Aurora4 基准数据库 [41] | `DNN` `MFCC` | 2.545 准确率 = 95.12% |
| | [43] | TIMIT 语库 | `DNN` | 78% |

- **iii. TIMIT [40]:** 他们在学习阶段使用了 115 种噪声分类，以提高对未见环境的泛化能力。同样在 2015 年，Yong Xu 等使用了相同的 TIMIT 数据集 [41–43]，与传统的基于最小矩形误差的降噪技术相比，他们支持一种监督方法，通过使用深度神经网络（`DNN`）基于噪声语音与易读语音之间的位置映射特征来对语音进行装饰。需要注意的是，尖端的平滑语音指令集是仅使用 TIMIT 语库创建的。

- **iv. 资源管理 (`RM`) 数据库 [26]:** 这用于被认为无故障的且经过人工多样化的数据 [22]。研究人员检查了子空间滤波的基本原理，作为最常见优化标准的典型整体性能。对于每种白噪声和彩色噪声情况，他们开发了一个理论估计器，通过实验证实了任何基于子空间的方法都能实现的性能峰值。这被研究人员识别为最好的估计器。语音增强数据集列表如表 10.3 所示。

# 10.7.3 语音合成数据集

- **LJ Speech 数据集**：利用了两类语库。一种是常用的 LJ Speech 数据集语库，另一种是 VCTK 语库 [33]。在实验没有足够的说话者训练数据的情况下，VCTK 曾被用于检查基于卷积的端到端语音合成社区的典型性能。随后将语音合成软件应用于这些语库中，以确认计算机在小规模语库上的典型平均性能。两个语库中的语音合成缩写为 LJ Speech 和 Nancy。在这里进行了一些对比实验，以查看最合适的语音合成生成结果。

- **ii.ii.** 他们收集了一个包含 1,845 条人类和合成语音录音的记录集 [44]。人类语音获取自九个人（五男四女）。这些中 1,004 条录音是从许多精彩的播客中提取的。每条录音的平均长度为 10.5 秒。在这里完全基于 8-D 总结不相关记录测试区分人类语音与合成语音的性能。

- **iii. Vocal-ID 技术** 从动机说话者的供应属性中提取韵律属性，并将这些点应用于替代说话者的数据库中 [30]，产生具有意图说话者人声识别和替代说话者可读性的人工语音。

- **iv.** 记录了来自 11 名男性和 11 名女性母语音频结构的正常和喊叫语音。每个句子都使用标准发音和喊叫进行了记录。12 个句子包含关键情绪，范围从 1 到 4 个短语。这些语义句子代表了人类在潜在危险情况下可能使用的语音信息。十二个表达欲望的句子每个包含三个单词的无偏总结信息，并为陈述句。语音合成数据集列表如表 10.4 所示。

# 表 10.4 语音合成数据集

| 任务 | 引用 | 数据集 | 方法 | 结果（秒） |
|---|---|---|---|---|
| 语音合成 | [33] | LJ Speech, VCTK | `CNN` | 训练效率：1.18 语音合成：17.3 秒. |
| | [44] | 1,845 条人类语音，人类语音获取自九个人（五男四女）。 | `DNN` | 0.99 |
| | [30] | `PSOLA` 周期替代说话者 | `LPC`, `Vocal ID` 方法 | 范围 0.027–0.044 |
| | [45] | 记录自 11 名男性和 11 名芬兰语母语者。 | 频谱估计 | 匹配 20% |

# 10.8 讨论与未来方向

根据目前的调查机构，最重要的子领域是用于识别犯罪案件的法医语音处理。它可能被用于检测那些曾听过但几千年来未曾目睹犯罪的嫌疑人。在更多情况下，有很多在法庭上使用说话人身份作为证据的记录。

本章探讨了用于法医的各种语音处理任务。由于语音处理难以分析犯罪调查，因此在该领域进行了大量研究工作，涵盖了各个方面。在本章中，系统地回顾了用于法医应用的处理和分析语音的各种方法技术。

在回顾该领域的之前的研究并与其进行比较时，我们还对法医进行了调查。虽然执行了不同的任务，如说话人识别 [46]、语音增强 [47] 和语音合成 [48]，但在许多法医语音处理任务中，仍有各种方法待实验。

# 10.9 结论

在本文述中，法医语音处理的未来技术方法得到了法。。。。。法。法法未来未来未来。

法语音语音的的未来未来。

法医语音未来的未来方向。

法医语音处理的未来方向。

法医语音处理的未来方向。

法医语音处理的未来方向。

。

法医领域领域将获益。

## 参考文献

- 1. D. Boss, “Visualization of Magnetic Features on Analogue Audio Tapes”, In IEEE Proceedings of the 39th International Conference on Audio Forensics: Practices and Challenges held at Bayerisches Landamt, Munich, Germany, pp. 1–2, 2010.

- 2. S. Narang and M. Gupta, “Speech Extraction Techniques: A Review”, International Journal of Computer Science and Mobile Computing, volume 4, issue 3, pp. 107–114, 2015.

- 3. A. Pangotra, “Review On Speech Processing & Its Techniques”, European Journal of Molecular & Clinical Medicine, volume 7, issue 7, pp. 3049–3052, 2020.

- 4. B.H. Yap, “Development of Speech Recognition System for Forensics”, UG Uem, Melaka, Malaysia, 2015.

- 5. J. Schroefter “Fifty Years of Progress in Speech Synthesis”, In Springer Proceedings of the 148th Meeting held at San Diego, USA published in the journal of the Acoustic Society of America, volume 116, issue 4, pp. 2497, 2004.

- 6. N.G. E and P. Melih, “Forensic Audio Authentication Technique of First or Higher Generation Copies of Analog Magnetic Audio Tapes”, Medicine Science International Medical Journal, volume 7, issue 2, pp. 295–298, 2018.

- 7. T-S Ester, R. Renáta, V. Veronika and P. Csaba, “The Effect of Alcohol on Speech Production”, Journal of Psycholinguistic Research, volume 43, issue 6, pp. 737–748, 2014.

- 9. R. Garrison Tull and J.C. Routledge, “自动说话人识别的‘冷语音’”, 美国声学学会第131次会议普通语言论文, 1996.

- 10. S. Singh, R. Bucks, and J.M. Cuerdan, “阿尔茨海默症中的语音”, SST 1996会议论文集, 第9卷, pp. 227–232, 1996.

- 11. T. Kutub, H. Haier and T. Jason, “社交媒体中的网络安全：挑战与未来展望”, IEEE 计算机学会, 第21卷, pp. 41–49, 2018.

- 12. B. Koenig, “声谱语音识别：一项法医调查”, Springer版美国声学学会期刊, 第79卷, 第6期, pp. 2088–2090, 1986.

- 13. H.F. Hollien, “法医语音识别”, 学术出版社, 2002.

- 14. L. Yount, “法医科学：从纤维到指纹”, Infabase 出版, 2007.

- 15. J.P. Campbell, W. Shen, M.W. Campbell, R. Schwartz, J.F. Bonastre, and D. Matouf, “法医说话人识别”, IEEE信号处理杂志, 第26卷, 第2期, pp. 95–103, 2009.

- 16. A.N. Jhadhav and N.V. Dharwad, “基于高斯混合模型、EM算法和K-Means聚类的说话人识别系统”, 国际现代教育与计算机科学期刊, 第11卷, 第ip 19–28, 2018.
