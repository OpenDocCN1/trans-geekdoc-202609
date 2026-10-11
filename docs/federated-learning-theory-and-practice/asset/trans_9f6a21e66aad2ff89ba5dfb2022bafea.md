
我们迭代地训练 `G`、`T[1]`、…、`T[I]` 和 `S`，其中 `G` 的每次迭代包含首先对所有教师模型执行梯度更新，然后对学生模型执行梯度更新。所提 PATE-AAE 与 PATE-GAN [[32]](#Chp020_353-368_B9780443190377000302.xhtml#br0160) 的主要区别在于生成过程。所提 AAE 方法使用回归自编码器架构来重构输入样本，并使用一个随机变量作为细化后的潜在空间，将其作为解码器（生成器）的输入以生成新的合成样本。相反，PATE-GAN 直接在样本生成器上采用判别器，以细化从随机噪声到合成数据的学习过程，根据与 GAN 收敛性质 [[35]](#Chp020_353-368_B9780443190377000302.xhtml#br0175) 相关的先前研究 [[9]](#Chp020_353-368_B9780443190377000302.xhtml#br0045)、[[10]](#Chp020_353-368_B9780443190377000302.xhtml#br0050)，这会在高维数据上产生更差的测试似然。为了构建隐私保护语音处理框架，在没有任何可用非敏感音频数据集的条件下，我们在研究中选择 PATE-GAN [[32]](#Chp020_353-368_B9780443190377000302.xhtml#br0160) 和 DP-GAN [[66]](#Chp020_353-368_B9780443190377000302.xhtml#br0330) 作为基线。先前的工作 [[69]](#Chp020_353-368_B9780443190377000302.xhtml#br0345) 仔细地基于文献 [[13]](#Chp020_353-368_B9780443190377000302.xhtml#br0065)、[[55]](#Chp020_353-368_B9780443190377000302.xhtml#br0275)、[[60]](#Chp020_353-368_B9780443190377000302.xhtml#br0300) 中提出的基于 WaveNet 的自编码器构建了我们的编码器-解码器，该自编码器在语音合成任务上表现出了有竞争力的性能，如 [(20.6)](#Chp020_353-368_B9780443190377000302.xhtml#f0035) 所示。PATE-AAE 解码器从判别器的输出应用了一个随机 Dropout 层，该输出是从潜在向量 (`z`) 或随机向量 (`η`) 中选择的。先前的工作 [[69]](#Chp020_353-368_B9780443190377000302.xhtml#br0345) 遵循 `μ`-law 压缩变换 [[44]](#Chp020_353-368_B9780443190377000302.xhtml#br0220)、[[53]](#Chp020_353-368_B9780443190377000302.xhtml#br0265)，使用 256 个量化电平来生成原始 16k Hz 音频。对于语音指令分类任务，使用分类准确率来评估学生模型。

![Figure 20.6 A privacy-preserving joint voice synthesis architecture introduced in [69].](OEBPS/images/B9780443190377000302/gr006_u5.jpg)

[图 20.6](#Chp020_353-368_B9780443190377000302.xhtml#cf0445) 文献 [[69]](#Chp020_353-368_B9780443190377000302.xhtml#br0345) 中介绍的一种隐私保护联合语音合成架构。

## 20.3 结论

在本章中，我们讨论了在部署必须遵守关键数据保护指南和公共法规（如欧盟的《通用数据保护条例》（GDPR）和《加州消费者隐私法案》（CCPA））的语音识别系统时，应采用的一些设计策略。事实上，语音信号中包含的性别、口音、说话环境和其他说话人特征等丰富信息，可能会被复杂的机器学习技术（如模型反演攻击）恢复。因此，需要特定的机制来保护嵌入在语音数据中的关键信息。

本文介绍了用于语音识别和通用声学处理中数据保护的水平和垂直联邦学习策略。特别地，我们描述了主要的垂直联邦声学建模 (AM) 方案之一，该方案基于去中心化特征提取模块和量子编码卷积神经网络。在 Google Speech Commands 数据集上报告的实验结果（包含来自量子计算机的机器噪声）有助于证明，基于联邦的去中心化量子 ASR 框架能够达到 95.12% 的有竞争力的准确率。另一方面，水平联邦学习的一大优势是可以直接连接到设备端语音助手服务器，通过大规模去中心化加快学习进程。

接下来，受近期数据保护需求回顾的驱动，我们还回顾了*差分隐私* (DP) 的基本要素，以及联邦学习结合 DP 如何提供定量的隐私度量。最后，我们提出了 (i) 一种新颖的私有聚合教师集成 (PATE)，用于通过差分隐私训练端到端联邦 ASR，以及 (ii) 一种利用对抗自编码器获得的合成数据的联邦语音识别系统。

## 参考文献

*   [[1]](#Chp020_353-368_B9780443190377000302.xhtml#cs0080_1) Martin Abadi, Andy Chu, Ian Goodfellow, H. Brendan McMahan, Ilya Mironov, Kunal Talwar, Li Zhang, Deep learning with differential privacy, *Proceedings of the 2016 ACM SIGSAC Conference on Computer and Communications Security*. 2016:308–318.

*   [[2]](#Chp020_353-368_B9780443190377000302.xhtml#cs0070_1) Janet M. Baker, Li Deng, James Glass, Sanjeev Khudanpur, Chin-Hui Lee, Nelson Morgan, Douglas O'Shaughnessy, Developments and directions in speech recognition and understanding, part 1 [dsp education], *IEEE Signal Processing Magazine* 2009;26(3):75–80.

*   [[3]](#Chp020_353-368_B9780443190377000302.xhtml#cs0080_1) Ville Bergholm, Josh Izaac, Maria Schuld, Christian Gogolin, Carsten Blank, Keri McKiernan, Nathan Killoran, PennyLane: automatic differentiation of hybrid quantum-classical computations, [arXiv:1811.04968](http://www.arxiv.org/abs/1811.04968); 2018.

*   [[4]](#Chp020_353-368_B9780443190377000302.xhtml#cs0100_1) Jacob Biamonte, Peter Wittek, Nicola Pancotti, Patrick Rebentrost, Nathan Wiebe, Seth Lloyd, Quantum machine learning, *Nature* 2017;549(7671):195–202.

*   [[5]](#Chp020_353-368_B9780443190377000302.xhtml#cs0055_1) Ferdinand Brasser, Tommaso Frassetto, Korbinian Riedhammer, Ahmad-Reza Sadeghi, Thomas Schneider, Christian Weinert, VoiceGuard: secure and private speech processing, *Interspeech*. 2018;vol. 18:1303–1307.

*   [[6]](#Chp020_353-368_B9780443190377000302.xhtml#cs0160_2) John S. Bridle, Michael D. Brown, An experimental automatic word recognition system, *JSRU Report* 1974;1003(5):33.

*   [[7]](#Chp020_353-368_B9780443190377000302.xhtml#cf0310) Nicholas Carlini, Florian Tramer, Eric Wallace, Matthew Jagielski, Ariel Herbert-Voss, Katherine Lee, Adam Roberts, Tom Brown, Dawn Song, Ulfar Erlingsson, Alina Oprea, Colin Raffel, Extracting training data from large language models, *USENIX Security Symposium*. 2021.

*   [[8]](#Chp020_353-368_B9780443190377000302.xhtml#cs0065_1) Yevgen Chebotar, Austin Waters, Distilling knowledge from ensembles of neural networks for speech recognition, *Interspeech*. 2016:3439–3443.

*   [[9]](#Chp020_353-368_B9780443190377000302.xhtml#cs0160_2) Dingfan Chen, Tribhuvanesh Orekondy, Mario Fritz, GS-WGAN: a gradient-sanitized approach for learning differentially private generators, *Neural Information Processing Systems (NeurIPS)* 2020.

*   [[10]](#Chp020_353-368_B9780443190377000302.xhtml#cs0065_1) Dingfan Chen, Ning Yu, Yang Zhang, Mario Fritz, GAN-Leaks: a taxonomy of membership inference attacks against generative models, *Proceedings of the 2020 ACM SIGSAC Conference on Computer and Communications Security*. 2020:343–362.

*   [[11]](#Chp020_353-368_B9780443190377000302.xhtml#cs0065_1) Mingqing Chen, Ananda Theertha Suresh, Rajiv Mathews, Adeline Wong, Cyril Allauzen, Françoise Beaufays, Michael Riley, Federated learning of n-gram language models, [arXiv:1910.03432](http://www.arxiv.org/abs/1910.03432); 2019.

*   [[12]](#Chp020_353-368_B9780443190377000302.xhtml#cs0065_1) Samuel Yen-Chi Chen, Shinjae Yoo, Federated quantum machine learning, *Entropy* 2021;23(4):460.

*   [[13]](#Chp020_353-368_B9780443190377000302.xhtml#cs0065_1) Jan Chorowski, Ron J. Weiss, Samy Bengio, Aäron van den Oord, Unsupervised speech representation learning using wavenet autoencoders, *IEEE/ACM Transactions on Audio, Speech and Language Processing* 2019;27(12):2041–2053.
