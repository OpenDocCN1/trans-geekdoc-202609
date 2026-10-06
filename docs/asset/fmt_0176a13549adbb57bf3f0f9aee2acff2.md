
![Figure 12.16 Applications of reinforcement learning.](img/fig12_16_B.jpg)

图 12.16 Applications of reinforcement learning.

### 12.6.4.3 Markov Decision Process

贝尔曼方程为动态编程奠定了基础，而马尔可夫决策过程（MDP） formalizes RL 相关问题。如果环境是完全可观测的，马尔可夫过程可以用来建模环境的动态，这意味着代理可以观察环境中的所有元素。

我们可以看到，图 12.17 中的 RL 模型的简单工作流程现在已经包含了之前的状态。状态会跟踪代理在某一时刻的位置。MDP 需要四个元素：有限数量的状态、有限数量的动作、在状态之间转移时的奖励或惩罚，以及下一个状态和动作的概率。代理从反馈中学习哪些状态是好的（给予正向反馈），哪些是坏的（给予负向反馈），并开始学习避免坏的状态以最大化回报。MDP 的优化目标是选择最佳策略以最大化累计奖励，如数学公式 Eq. 12.5 所示。

![Figure 12.17 RL with Markov decision process workflow.](img/fig12_17_B.jpg)

图 12.17 RL with Markov decision process workflow.

(12.5)

```
E\left\lbrack {\sum\limits_{t = 0}^{\infty}\gamma^{t}}R_{at}\left( s_{t}\rightarrow s_{t + 1} \right) \right\rbrack
```

### 12.6.4.4 Reinforcement Learning Algorithms

基于 RL 的算法侧重于教会计算机玩像国际象棋这样的智力游戏，但受游戏启发的其他应用（如漫游器着陆）也已出现。Q-learning 是最著名的算法之一，也是最早利用强化学习的算法。Q-learning 是一种 `off-policy` 算法，可以用于时差学习，算法可以比较连续的预测。图 12.18 展示了 Q-learning 算法的工作流程。

![Figure 12.18 Workflow of the Q-learning algorithm.](img/fig12_18_B.jpg)

图 12.18 Workflow of the Q-learning algorithm.

### 12.6.4.5 SHMMS

在本节中，我们将以智能健康监测与管理系统为使用案例场景进行评估。我们的 SHMMS 被泛化为三层结构，如图 12.19 所示。每一层都具有其功能。我们在前面的章节中简要讨论了使用强化学习算法进行训练的 agent。为了保持使用案例的简洁和有效，我们在强化学习框架下使用神经网络作为模型。一个典型的神经网络驱动的强化学习模型是 Actor 2 Critic（A2C）。A2C 现在已有更高级的版本 A3C。神经网络模型的任务是识别可穿戴设备数据中的任何异常。可穿戴设备数据来自次要和主要来源，用于评估强化学习模型的有效性。

![Figure 12.19 Abstract framework SHMMS.](img/fig12_19_B.jpg)

图 12.19 Abstract framework SHMMS.

区块链层包含数据库和矿工节点，负责计算可穿戴设备数据的加密哈希。该层是去中心化的，但为了与第四层通信，区块链需要一些中央管理系统来执行智能合约，以及 agent 和 MIoT 层。

Agent 层由多个通过强化学习训练的 Agent 组成，用于检测数据中的任何异常。如果检测到异常，Agent 将停止通信，从而防止数据到达矿工，避免在错误数据上计算加密哈希导致成本增加。矿工的成本本身就不低，而计算错误数据是不可取的。在第二种情况中，当 Agent 检测到医疗紧急异常时，Agent 会提前通知相应的权威部门。如果没有异常且数据一致，Agent 将依据智能合约规则执行，该规则规定了在区块链上记录每一次观测的必要性或严重程度。医疗情况会因条件而异，智能合约和 Agent 可以防止矿工处理不可用的数据，从而节省区块链数据库的存储容量。

第三且最后一层是 MIoT 层。该层负责生成数据。在我们的使用案例中，数据是通过持续监测每分钟心跳的可穿戴设备生成的。

为了评估模型的表现，我们设计了一项实验。在实验中，我们固定了集数为 49，并在第七次会话中运行模型七次。奖励是第一个观察变量，因为它表明模型正在做出良好的政策和决策。如果模型持续累积奖励，则在终止点后会被重置。这是一个连续场景，因此我们的终止点在每集结束时累积最高奖励。Figure 12.20 为模型在奖励方面提供了洞察。在图中，我们可以看到奖励从较低端开始，随着集数增加而上升。这种坡度表明我们的模型在每集结束前累积奖励并逐步学习，直到终止点。另一个事实是，所有会话的奖励起点并不相同。在强化学习中，这很正常，因为在开始时模型或 Agent 一无所知，会采取随机动作。随着集数推进，Agent 学习得更多，直到超参数得到最高可能的调整。

![Figure 12.20 Episodic and average reward.](img/fig12_20_B.jpg)

Figure 12.20 Episodic and average reward.

为了确认模型正在学习，我们还可以检查损失指标。Figure 12.21 提供了关于损失指标的信息。损失函数在图中呈现出杂乱的直线，这可能是由于初始的随机动作，或者在集数结束后重新开始时的随机性。从上述图中可以明显看出，训练正在进行良好，模型正在学习。强化学习需要广泛的训练过程，因此 49 集可能不足以提供深入的信息。根据我们的假设，我们可以进行另一次实验，检查每次会话的第一次奖励。这可以告诉我们模型在每集的第一步是否犯错，或者是否利用了前一集的知识。为此，我们取了某个点的奖励平均值并尝试构建趋势线。Figure 12.22 展示了趋势线以及一步和两步对平均奖励的预测。斜率不高，但这归因于强化学习需要大量训练，在 49 集后获得此斜率已属不错。

![Figure 12.21 Episodic and average loss.](img/fig12_21_B.jpg)

Figure 12.21 Episodic and average loss.

![Figure 12.22 Trend line for the average reward with one and two step prediction.](img/fig12_22_B.jpg)

Figure 12.22 Trend line for the average reward with one and two step prediction.

Figure 12.23 提供了关于模型损失的信息。我们可以看到损失呈下降趋势。趋势线的斜率也相当不错；因此，通过这些评估我们可以断言模型正在学习并能够在可穿戴设备的数据中检测异常。

![Figure 12.23 Trend line for average loss.](img/fig12_23_B.jpg)

Figure 12.23 Trend line for average loss.

总体框架主要依赖于 Agent 和区块链的安全性，以在医疗行业提供强大的框架。机器学习概念与 MIoT 结合，结合区块链，在训练完成后表现更好。我们也可以看到模型的短 coming——学习率较慢，可以进一步优化。

## 12.7 Chapter Summary

In this chapter, we discuss the challenges faced by the health sector and the importance of developing a framework where MIoT can work alongside blockchain and ML concepts. The chapter started with an example of an existing framework, but most of them are either using ML or blockchain. Moreover, we gather brief information about IoT, MIoT, blockchain, and ML concepts before going toward our use case. We discussed IoT, how IoT communicates in depth, and how more IoT-related domains are emerging. We covered the ML concept from starch and then studied reinforcement learning and its application. We also learned about blockchain and its properties and why it is more secure. The concept of mining is also presented in this chapter but up to a level so it remains more user readable as cryptography can lead to another mature domain to understand the functionality of the blockchain.

## References

1.  M. M. Kamruzzaman, “Architecture of smart health care system using artificial intelligence”, 2020 IEEE Int. Conf. Multimed. Expo Work. ICMEW 2020. 2020, doi: [10.1109/ICMEW46912.2020.9106026](https://dx.doi.org/10.1109/ICMEW46912.2020.9106026)

2.  W. Li *et al.*, “A comprehensive survey on machine learning-based big data analytics for IoT-enabled smart healthcare system”, Mob. Networks Appl. Volume 26(1), pp. 234–252, 2021, doi: [10.1007/S11036-020-01700-6/FIGURES/5](https://dx.doi.org/10.1007/S11036-020-01700-6/FIGURES/5)

3.  F. Ali *et al.*, “An intelligent healthcare monitoring framework using wearable sensors and social networking data”, Futur. Gener. Comput. Syst. Volume 114, pp. 23–43, 2021, doi: [10.1016/J.FUTURE.2020.07.047](https://dx.doi.org/10.1016/J.FUTURE.2020.07.047)

4.  J. Li and Y. Hu, “Employing edge computing to enhance self-defense capabilities of IoT devices”, 2022 IEEE World AI IoT Congr. pp. 604–610, 2022, doi: [10.1109/AIIOT54504.2022.9817368](https://dx.doi.org/10.1109/AIIOT54504.2022.9817368)

5.  H. Moudoud, Z. Mlika, L. Khoukhi, and S. Cherkaoui, “Detection and prediction of FDI attacks in IoT systems via hidden Markov model”, IEEE Trans. Netw. Sci. Eng. 2022, doi: [10.1109/TNSE.2022.3161479](https://dx.doi.org/10.1109/TNSE.2022.3161479)

6.  M. H. Panahi Rizi and S. A. Hosseini Seno, “A systematic review of technologies and solutions to improve security and privacy protection of citizens in the smart city”, Internet of Things. Volume 20 p. 100584, 2022, doi: [10.1016/J.IOT.2022.100584](https://dx.doi.org/10.1016/J.IOT.2022.100584)

7.  C. H. Liu, T. L. Chen, C. Y. Chang, and Z. Y. Wu, “A reliable authentication scheme of personal health records in cloud computing”, Wirel. Netw. pp. 1–11, 2021, doi: [10.1007/S11276-021-02743-7/TABLES/2](https://dx.doi.org/10.1007/S11276-021-02743-7/TABLES/2)

8.  A. D. Jurik and A. C. Weaver, “Remote medical monitoring”, Computer (Long. Beach. Calif). Volume 41(4), pp. 96–99, 2008, doi: [10.1109/MC.2008.133](https://dx.doi.org/10.1109/MC.2008.133).

9.  J. M. Ehrenfeld and M. A. Rehman, “Anesthesia information management systems: a review of functionality and installation considerations”, J. Clin. Monit. Comput. Volume 25(1), pp. 71–79, 2010, doi: [10.1007/S10877-010-9256-Y](https://dx.doi.org/10.1007/S10877-010-9256-Y).

10.  A. Milenković, C. Otto, and E. Jovanov, “Wireless sensor networks for personal health monitoring: Issues and an implementation”, Comput. Commun. Volume 29(13–14), pp. 2521–2533, 2006, doi: [10.1016/J.COMCOM.2006.02.011](https://dx.doi.org/10.1016/J.COMCOM.2006.02.011).

11.  Y. Yang, H. Wang, R. Jiang, X. Guo, J. Cheng, and Y. Chen, “A review of IoT-enabled mobile healthcare: Technologies, challenges, and future trends”, IEEE Internet Things J. Volume 9(12), pp. 9478–9502, 2022, doi: [10.1109/JIOT.2022.3144400](https://dx.doi.org/10.1109/JIOT.2022.3144400).

12.  A. Vaidyam, J. Halamka, and J. Torous, “Enabling research and clinical use of patient-generated health data (the mindLAMP platform): Digital phenotyping study”, JMIR Mhealth Uhealth. Volume 10(1), p. e30557, 2022, [https//mhealth.jmir.org/2022/1/e30557](https://mhealth.jmir.org/2022/1/e30557); doi: [10.2196/30557](https://dx.doi.org/10.2196/30557).

13.  K. B. Jyothilakshmi, V. Robins, and A. S. Mahesh, “A comparative analysis between hyperledger fabric and ethereum in medical sector: A systematic review”, Lect. Notes Data Eng. Commun. Technol. Volume 93 pp. 67–86, 2022, doi: [10.1007/978-981-16-6605-6\_5/COVER](https://dx.doi.org/10.1007/978-981-16-6605-6_5/COVER).
