

2. *可扩展性：*由于大多数防御方法无法抵御自适应白盒攻击，研究人员已开始关注可证明性防御，这类防御能够在某种程度上保证防御的性能，无论攻击者采用何种方法。但迄今为止，可扩展性是当前大多数可证明性防御普遍面临的问题。例如，区间边界分析是近年来流行的一种基于证明的防御方法，但它无法扩展到非常深的神经网络和大规模数据集。

## 9.5 结论

随着深度学习研究的进一步发展以及深度学习技术在现实场景中的广泛应用，深度学习的安全与隐私已成为一个新兴且前景广阔的研究领域，吸引了来自学术界和工业界的大量学者进行深入研究，并取得了许多令人瞩目的研究成果。然而，迄今为止，深度学习安全与隐私研究仍处于起步阶段，许多关键的科学问题仍有待解决。

本章总结了针对深度学习模型的对抗防御策略。首先，我们介绍了不同对抗攻击的目标，并据此将所有防御策略分为三类：修改训练或修改输入、修改网络架构以及网络附加模块。在不同类别中，我们还详细阐述了不同的防御算法，每种算法各有其优势。然而，深度学习对抗防御的研究仍处于起步阶段，我们仍面临两大难题：如何对抗白盒攻击以及对抗防御的普遍性问题。我们尚没有有效的算法来防御潜在有害的白盒攻击。

## 参考文献

1. Ian Goodfellow, Yoshua Bengio, and Aaron Courville. 2016. *Deep Learning*. Vol. 1.
- 2. Goodfellow, I. J., Shlens, J., & Szegedy, C. (2014). Explaining and harnessing adversarial examples. arXiv preprint arXiv:1412.6572.
- 3. Das, N., Shanbhogue, M., Chen, S. T., Hohman, F., Li, S., Chen, L., ... & Chau, D. H. (2018, July). Shield: Fast, practical defense and vaccination for deep learning using jpeg compression. In Proceedings of the 24th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining (pp. 196–204).
- 4. Guo, C., Rana, M., Cisse, M., & Van Der Maaten, L. (2017). Countering adversarial images using input transformations. arXiv preprint arXiv:1711.00117.
- 5. Xu, W., Evans, D., & Qi, Y. (2017). Feature squeezing: Detecting adversarial examples in deep neural networks. arXiv preprint arXiv:1704.01155.
- 6. Dziugaite, G. K., Ghahramani, Z., & Roy, D. M. (2016). A study of the effect of jpg compression on adversarial images. arXiv preprint arXiv:1608.00853.
- 7. Kang, D., Khot, T., Sabharwal, A., & Hovy, E. (2018). Adventure: Adversarial training for textual entailment with knowledge-guided examples. arXiv preprint arXiv:1805.04680.
- 8. Goodfellow, I. J., Pouget-Abadie, J., Mirza, M., Xu, B., Warde-Farley, D., Ozair, S., ... & Bengio, Y. (2014). Generative adversarial networks. arXiv preprint arXiv:1406.2661.
- 9. Wang, Q., Guo, W., Zhang, K., Ororbia II, A. G., Xing, X., Liu, X., & Giles, C. L. (2016). Learning adversary-resistant deep neural networks. arXiv preprint arXiv:1612.01401.
- 10. Lee, H., Han, S., & Lee, J. (2017). Generative adversarial trainer: Defense to adversarial perturbations with gan. arXiv preprint arXiv:1705.03387.
- 11. Hinton, G., Vinyals, O., & Dean, J. (2015). Distilling the knowledge in a neural network. arXiv preprint arXiv:1503.02531.
- 12. Papernot, N., McDaniel, P., Wu, X., Jha, S., & Swami, A. (2016, May). Distillation as a defense to adversarial perturbations against deep neural networks. In 2016 IEEE symposium on security and privacy (SP) (pp. 582–597). IEEE.
- 13. Miyato, T., Dai, A. M., & Goodfellow, I. (2016). Adversarial training methods for semi-supervised text classification. arXiv preprint arXiv:1605.07725.
- 14. Akhtar, N., Liu, J., & Mian, A. (2018). Defense against universal adversarial perturbations. In *Proceedings of the IEEE conference on computer vision and pattern recognition* (pp. 3389–3398).
- 15. Meng, D., & Chen, H. (2017, October). Magnet: a two-pronged defense against adversarial examples. In *Proceedings of the 2017 ACM SIGSAC conference on computer and communications security* (pp. 135–147).

## 深度强化学习网络安全的防御方案

Jiamiao Zhao¹, Fei Hu¹, 和 Xiali Hei²

¹美国阿拉巴马大学电子与计算机工程系
²美国路易斯安那大学拉法叶分校信息学院

DOI: [10.1201/9781003187158-12](https://doi.org/10.1201/9781003187158-12)

## 目录

- 10.1 引言
- 10.2 背景
  - 10.2.1 无模型强化学习
  - 10.2.2 深度强化学习
  - 10.2.3 深度强化学习的安全性
- 10.3 对抗示例的认证验证
  - 10.3.1 鲁棒性认证
  - 10.3.2 系统架构
  - 10.3.3 实验结果
- 10.4 对抗状态观测下的鲁棒性
  - 10.4.1 确定性策略的状态对抗深度强化学习：DDPG
  - 10.4.2 基于Q学习的状态对抗深度强化学习：DQN
  - 10.4.3 实验结果
- 10.5 结论与挑战
- 致谢
- 参考文献

## 10.1 引言

机器学习（ML）可分为三类：监督学习、无监督学习和强化学习。在*监督*学习（如SVM、决策树等）中，训练样本被标记，以找到不同聚类之间的边界。另一方面，如果训练数据集没有真实标签，其机器学习算法被称为*无监督*学习，如KNN、K-means等。它们根据超平面中的距离对训练数据进行分类。*强化*学习（RL）利用智能体从历史状态/动作中学习，并可以使用最大累积奖励来生成动作，并与环境实时交互。

强化学习已被用于机器人、电网、传感器网络以及许多其他实际应用中的众多决策问题。然而，强化学习算法可能需要很长时间才能收敛到最优点（从几小时到几周，取决于状态空间的大小）[1]。近来，一种将深度学习（DL）与强化学习相结合的新算法——称为深度强化学习（DRL）——已被应用于处理高维输入，例如相机图像、大向量问题。DRL在许多复杂决策过程中展现出了出色的成果，例如机器人技术[2]、自动驾驶汽车、智慧城市以及围棋等游戏[3]等。DRL在处理关键的现实世界应用方面展示了其能力。亚马逊利用DRL设计了一款名为AWS DeepRacer的自动驾驶赛车。它使用摄像头观察赛道，并使用DRL模型对油门和方向做出决策。

因此，在将DRL部署到关键的现实世界系统之前，需要全面调查其安全性和隐私性。最近，DRL被证明容易受到对抗攻击[4]。攻击者将扰动插入DRL模型的输入中，导致DRL决策错误。DRL利用深度神经网络（DNN）模型来实现高精度预测，但它对输入扰动不够鲁棒。即使输入的微小变化也可能导致输出的剧烈波动。这使得全面了解对抗攻击的类型和特征成为必要。

本章旨在介绍DRL中的安全问题以及当前克服对抗攻击的防御方法。我们讨论了DRL的结构、其安全问题，以及DRL中现有的攻击目标和目的。

*本章组织：*第10.2节概述了RL和DRL，以及与之相关的隐私问题。第10.3节讨论了一种旨在实现鲁棒DRL以抵御对抗攻击的防御方法。第10.4节是第10.3节的扩展版本，它通过在学习过程中寻找鲁棒策略，提出了一种升级的DRL机制。我们在第10.5节总结本章，并讨论设计隐私保护和鲁棒DRL的研究挑战。

## 10.2 背景

在本节中，我们首先简要介绍强化学习，特别讨论无模型强化学习。然后，我们展示如何将强化学习与深度学习相结合，形成DRL过程[1]。我们总结了DRL技术及其在网络安全性方面的潜在弱点。

一般的强化学习问题可以描述为马尔可夫决策过程（MDP）。MDP包含智能体的状态、动作、奖励和策略。这里我们首先给出一些术语及其在强化学习中的功能的定义。

- *状态*：智能体与环境交互并学习状态。在每个时间步，智能体根据策略与状态空间交互，并获得一个决定动作质量的奖励。
- *策略*定义了智能体在环境中的行为方式，它将当前状态映射到一个动作。策略分为两种类型：确定性策略和随机性策略。当智能体采取的动作是*确定性*的，则策略是确定性的；如果动作针对不同状态遵循某个概率分布函数，则策略是*随机性*的。
- *同策略（on-policy）算法*评估探索价值。
- *异策略（off-policy）算法*不评估探索价值。Q学习是一种异策略方法。
- *动作*是智能体为与环境交互而执行的行为。

