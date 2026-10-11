
# 参考文献

*   [[35]](#Chp011_199-217_B978044319037700020X.xhtml#cf0035) Chang Sun, Lianne Ippel, Johan van Soest, Birgit Wouters, Alexander Malic, Onaopepo Adekunle, Bob van den Berg, Ole Mussmann, Annemarie Koster, Carla van der Kallen, 等, 用于垂直分区场景下分析个人健康数据的隐私保护基础设施, *Studies in Health Technology and Informatics* 2019;264:373–377.

*   [[36]](#Chp011_199-217_B978044319037700020X.xhtml#cf0036) Tao Sun, Robert Hannah, Wotao Yin, 在更现实假设下的异步坐标下降法, *Proc. Advances in Neural Info. Process. Syst.*. *Long Beach, CA*. 2017年12月:6183–6191.

*   [[37]](#Chp011_199-217_B978044319037700020X.xhtml#cs0035_1) Latanya Sweeney, *k*-匿名性: 一种隐私保护模型, *International Journal of Uncertainty, Fuzziness and Knowledge-Based Systems* 2002;10(05):557–570.

*   [[38]](#Chp011_199-217_B978044319037700020X.xhtml#cs0025_3) Jianyu Wang, Gauri Joshi, 协作式 SGD: 用于设计和分析通信高效 SGD 算法的统一框架, [arXiv:1808.07576](http://www.arxiv.org/abs/1808.07576); 2018年8月.

*   [[39]](#Chp011_199-217_B978044319037700020X.xhtml#cf0254) Tianyu Wu, Kun Yuan, Qing Ling, Wotao Yin, Ali H. Sayed, 具有异步性和延迟的去中心化共识优化, *IEEE Transactions on Signal and Information Processing over Networks* 2017年4月;4(2):293–307.

*   [[40]](#Chp011_199-217_B978044319037700020X.xhtml#cf0255) Zhirong Wu, Shuran Song, Aditya Khosla, Fisher Yu, Linguang Zhang, Xiaoou Tang, Jianxiong Xiao, 3D ShapeNets: 体积形状的深度表征, *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*. 2015:1912–1920.

*   [[41]](#Chp011_199-217_B978044319037700020X.xhtml#cs0050_2) Yangyang Xu, Wotao Yin, 一种用于正则化多凸优化的分块坐标下降法, 并应用于非负张量分解与补全, *SIAM Journal on Imaging Sciences* 2013;6(3):1758–1789.

*   [[42]](#Chp011_199-217_B978044319037700020X.xhtml#cf0256) Yangyang Xu, Wotao Yin, 用于凸与非凸优化的分块随机梯度迭代, *SIAM Journal on Optimization* 2015;25(3):1686–1716.

*   [[43]](#Chp011_199-217_B978044319037700020X.xhtml#cf0257) Qiang Yang, Yang Liu, Tianjian Chen, Yongxin Tong, 联邦机器学习: 概念与应用, *ACM Transactions on Intelligent Systems and Technology* 2019年1月;10(2).

*   [[44]](#Chp011_199-217_B978044319037700020X.xhtml#cs0035_2) Andrew C. Yao, 安全计算协议, *Annual Symposium on Foundations of Computer Science*. *Chicago, Illinois*. 1982:160–164.

*   [[45]](#Chp011_199-217_B978044319037700020X.xhtml#cs0050_3) Bicheng Ying, Kun Yuan, Ali H. Sayed, 分布式特征下的监督学习, *IEEE Transactions on Signal Processing* 2018年11月;67(4):977–992.

*   [[46]](#Chp011_199-217_B978044319037700020X.xhtml#cs0025_4) Hao Yu, Sen Yang, Shenghuo Zhu, 并行重启 SGD: 更快的收敛与更少的通信: 揭秘模型平均为何在深度学习中有效, *Proc. AAAI Conf. Artificial Intell.*. 2019;vol. 33:5693–5700.

# 第12章：联邦学习中的超参数调优——系统与实践

Syed Zawad^[a](#Chp012_219-235_B9780443190377000211.xhtml#aff0010); Feng Yan^[b](#Chp012_219-235_B9780443190377000211.xhtml#aff0015)

^a^ 内华达大学雷诺分校, 内华达州雷诺, 美国

^b^ 休斯顿大学, 德克萨斯州休斯顿, 美国

## 摘要

超参数调优是一项耗时且消耗资源的任务。与传统的集中式训练相比, 联邦学习面临着几个独特的挑战。首先, 在联邦学习中(尤其是跨设备范式), 训练通常在不可靠(例如, 客户端在训练期间经常掉线)且资源受限的设备上进行。此外, 联邦学习通常会引入额外的超参数, 例如本地轮数, 这需要更多的调优时间和资源。再者, 数据和资源异质性带来了额外的挑战, 因为在平衡的集中式学习中获得的经验法则可能不再奏效。在本章中, 我们将讨论上述挑战, 并从系统设计和优化的角度介绍为应对这些挑战所做的最新努力。我们首先列出 FL 训练过程中涉及的相关可量化资源。然后讨论客户端和服务器端的单独超参数, 并简要解释所有这些超参数如何单独影响整体训练效率和资源消耗。接着, 我们将广泛讨论跨设备 FL 的系统特性, 这为超参数调优带来了独特的挑战及其对系统资源的影响。随后, 我们将讨论最先进的超参数调优方法如何尝试克服这些挑战, 它们对资源效率的影响及其局限性。这引出了未来的研究机会, 最后我们通过讨论开放问题来结束本章。

### 关键词

联邦学习; 超参数调优; 跨设备

## 12.1 简介

机器学习模型有两类直接影响模型性能的参数。第一类参数直接集成在模型本身中(例如神经网络中神经元的权重和偏置), 并通过称为拟合模型参数的数据学习过程进行初始化和更新。另一类参数称为超参数, 无法通过学习直接更新。这些超参数主要用于配置模型以进行训练。在深度学习设置中最常讨论的是 `batch size`、`optimizer` 和 `learning rate` 参数, 但也存在其他参数, 如 `momentum` 和 `dropout ratios`。构建有效机器学习模型的主要挑战之一是调整超参数以获得最佳的模型参数。超参数的值在不同模型和数据集间差异巨大, 它们之间极少有可迁移的直觉, 这使得超参数调优(或超参数优化, 简称 HPO)成为一个主要基于试错的耗时过程。

对于传统的集中式模型训练, 超参数的调优旨在实现单一目标——尽可能高的模型性能。虽然资源消耗和收敛时间仍是关注点, 但它们是次要目标, 因为人们预期硬件能力会随时间提升, 且 ML 工程师对它们拥有完全控制权 [[25]](#Chp012_219-235_B9780443190377000211.xhtml#br0125), [[35]](#Chp012_219-235_B9780443190377000211.xhtml#br0175)。因此, 文献中有大量工作专注于提供调优指南 [[17]](#Chp012_219-235_B9780443190377000211.xhtml#br0085), [[23]](#Chp012_219-235_B9780443190377000211.xhtml#br0115), [[31]](#Chp012_219-235_B9780443190377000211.xhtml#br0155), [[36]](#Chp012_219-235_B9780443190377000211.xhtml#br0180), 另一个大的研究领域是调优过程的自动化 [[35]](#Chp012_219-235_B9780443190377000211.xhtml#br0175)。这两个领域都在超参数调优的范围内取得了重大进展。
