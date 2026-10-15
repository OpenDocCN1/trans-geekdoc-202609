
-   [除这些自由可用且易于使用的媒介外，深度神经网络模型也受到了显著关注。可能的原因是机器学习平台的先进基础设施，包括公开可用的平台，可供资金有限的研究人员免费使用或以极低费用使用。深度学习技术用于生成面部换脸视频始于2017年，当时一位Reddit用户在互联网上发布了深fake视频，震惊了全球。这些视频是基于[Korshunova et al. (2017)](#Ch008_223-241_S016971612200058X.xhtml#bb0135)所提议的深度神经网络架构的算法生成的。随后，多个基于深度神经网络的面部换脸或风格转移算法相继提出，以实现面部的有效操控。令人感兴趣或令人担忧的是，与开放式社交媒体应用类似乎一样，大多数基于深度神经网络的面部操控技术都是免费提供的。例如，DeepFaceLab ([Perov et al., 2020](#Ch008_223-241_S016971612200058X.xhtml#bb0230))提供多种面部操控选项，包括替换面部和头部、使人年轻化以及操控嘴唇。此外，作者声称该工具箱可以在无需专业知识的情况下轻松使用，即，只要有Internet和计算资源，任何人都可以生成和传播假数据。[Table 3](#Ch008_223-241_S016971612200058X.xhtml#t0020)列出了一些流行的基于深度学习的面部操控算法。

[Table 3](#Ch008_223-241_S016971612200058X.xhtml#B-t0020)

深fake生成技术基于深度神经网络架构。

| 算法 || 架构 || 链接 |
| --- | --- | --- |
| Face Swap || Encoder-Decoder || [`https://github.com/deepfakes/faceswap`](https://github.com/deepfakes/faceswap) |
| --- | --- | --- |
| DeepFaceLab ||  || [`https://github.com/iperov/DeepFaceLab`](https://github.com/iperov/DeepFaceLab) |
| Face Swap-GAN ||  || [`https://github.com/shaoanlu/faceswap-GAN`](https://github.com/shaoanlu/faceswap-GAN) |
| Face Shifter || Encoder-Decoder + Generator || [`https://lingzhili.com/FaceShifterPage/`](https://lingzhili.com/FaceShifterPage/) |
| FSGAN || Recurrent Neural Network || [`https://github.com/YuvalNirkin/fsgan`](https://github.com/YuvalNirkin/fsgan) |
| Style GAN || Generative Networks || [`https://github.com/NVlabs/stylegan`](https://github.com/NVlabs/stylegan) |
| Face2Face || Shape Deformation Model || [`https://justusthies.github.io/posts/face2face/`](https://justusthies.github.io/posts/face2face/) |
| Neural Texture || Convolutional Encoder Decoder || [`https://github.com/SSRSGJYD/NeuralTexture`](https://github.com/SSRSGJYD/NeuralTexture) |

[Fig. 3](#Ch008_223-241_S016971612200058X.xhtml#f0020) 展示了与相关但通常独立处理的主题在发表论文数量上的进展。统计数据是通过在“[https://app.dimensions.ai/discover/publication](https://app.dimensions.ai/discover/publication)”平台上输入关键词“face morphing”“face-swapping”和“deepfake”获得的。可以看出，随着深fake技术威胁的凸显，论文数量呈指数增长。同时，在面部变形和面部换脸等相似领域并行工作的研究领域也在出版世界中留下了显著印记。我们也想提醒您，并非所有为面部变形检测开发的技术都能用于深fake检测（[Agarwal et al., 2021b](#Ch008_223-241_S016971612200058X.xhtml#bb0030)）；但到目前为止，它们在不同操控场景中的探索仍然有限。

![Fig. 3 Progression in the number of papers appearing with the different identity manipulation technique names. The number of papers for the year 2022 reflects the published papers listed so far (till march) on the platform.](images/S016971612200058X/f08-03-9780443184307.jpg)

[Fig. 3](#Ch008_223-241_S016971612200058X.xhtml#B-f0020) 显示了不同身份操控技术名称下发表论文数量的增长趋势。2022年的论文数量反映了截至三月在该平台上已发表的论文。

##  3: Identity manipulation datasets

深fake研究的进展得益于各类研究者在创建大规模面部变形、换脸和深fake数据集方面的重要贡献。[Table 4](#Ch008_223-241_S016971612200058X.xhtml#t0025)展示了基于深度神经网络架构生成的多个深fake数据集，其中大多数数据集包含将目标身份与源身份替换的图像。该表是近期许多调查论文中缺失的一个全面数据集调查（[Mirsky and Lee, 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0205); [Venkatesh et al., 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0315)）。为推动深fake研究社区的发展，最早的数据集UADFV和TIMIT于2018年开发。这些数据集的主要局限性是视频数量较少且质量较低。随后，提出了多个高质量且大规模的数据集，以推动深fake检测研究。FF++是最早的大规模数据集之一，包含四种操作方式，其中两种属于身份操控，即面部换脸和深fake。数据集包含三种不同质量的视频，使深fake检测问题更具挑战性。鉴于深fake检测研究的流行度及其在社交媒体平台上的影响，多家公司也开始组织深fake检测竞赛。这些竞赛通常伴随新数据集的发布。例如，Google组织的深fake检测竞赛伴随了深fake检测挑战数据集（DFDC）。上述大多数数据集主要针对单一模态的修改，即面部。但最近一些数据集包含面部和音频的双重操控（[Khalid et al., 2021](#Ch008_223-241_S016971612200058X.xhtml#bb0115)）。唇同步是面部特征运动的重要部分，因此，这种多样化的操控能够显著提升身份操控研究。此外，研究工作已从在受控环境中生成的深fake视频转向获取或生成反映现实世界各种伪影的视频，包括分辨率、压缩、光照、宽高比、帧率、运动、姿态、化妆品和遮挡等变化。这些涵盖各种伪影的数据集统称为“野外”数据集，如DF（[Ciftci et al., 2020](#Ch008_223-241_S016971612200058X.xhtml#bb0035)）和Wilddeepfake（[Zi et al., 2020](#Ch008_223-241_S016971612200058X.xhtml#bb0350)）。

[Table 4](#Ch008_223-241_S016971612200058X.xhtml#B-t0025)

常用于深fake检测研究的基准数据集比较。

| 数据集 || 真实视频 || 假视频 || 总视频数 || 总主体数 || 方法 || 真实音频 || 深fake音频 || 多元种族 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| UADFV ([Yang et al., 2019](#Ch008_223-241_S016971612200058X.xhtml#bb0340)) || 49 || 49 || 98 || 49 || 1 || 否 || 否 || 否 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TIMIT ([Korshunov and Marcel, 2018](#Ch008_223-241_S016971612200058X.xhtml#bb0125)) || 640 || 320 || 960 || 32 || 2 || 否 || 是 || 否 |
