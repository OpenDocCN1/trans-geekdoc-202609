
Table 6 illustrates that the car controlled by the aggregated policy passes the test tracks successfully. It demonstrates that the learned aggregated policy from BAMDDPG achieves a good generalization performance.

## CONCLUSIONS

This paper proposed a deep reinforcement learning algorithm, by aggregating multiple deep deterministic policy gradient algorithm and an m-out-of-n bootstrap sampling method. /is method is effective to the sequential and iterative training data, where the data exhibit long-tailed distribution, rather than the norm distribution implicated by the i.i.d. data assumption. The method can learn the optimal policies with much less training time for tasks with continuous space of actions and states.

Experiment results on the 2D robot arm game show that the reward gained by the aggregated policy is 10%Ң50% better than those gained by the nonaggregated subpolicies. Experiment results on TORCS demonstrate the proposed method can learn successful control policies with less training time by 56.7%, compared to the normal sampling method and nonaggregated subpolicies.

本书版权归 Arcler 所有

![Image 302](img/index-77_1.png)

![Image 303](img/index-77_2.png)

![Image 304](img/index-77_3.png)

Deep Ensemble Reinforcement Learning With Multiple Deep ...

51

## REFERENCES

1\. R. S. Sutton and A. G. Barto, Reinforcement Learning: An Introduction, MIT press, Cambridge, MA, USA, 1998.

2\. K. Arulkumaran, M. P. Deisenroth, M. Brundage, and A. A. Bharath, “深度增强学习：简要综述”，IEEE 信号处理杂志，第 34 卷，第 6 期，第 26–38 页，2017 年。

3\. ! ¯ £ with deep convolutional neural networks”，在第 25 届神经信息处理系统国际会议论文集中，第 1097–1105 页，美国内华达州湖塔希 oe，2012 年 3 月。

4\. Y. LeCun, Y. Bengio, and G. Hinton, “Deep learning”，Nature，第 521 卷，第 7553 期，第 436–444 页，2015 年。

5\. V. Mnih, K. Kavukcuoglu, D. Silver et al., “Human-level control through deep reinforcement learning”，Nature，第 518 卷，第 7540 期，第 529–533 页，2015 年。

6\. H. Van Hasselt, A. Guez, and D. Silver, “Deep reinforcement learning with double Q-Learning”，在第 30 届 AAAI 会议论文集中。

'°~{

7\. T. Schaul, J. Quan, I. Antonoglou et al., “Prioritized experience replay”，2015 年，`https://arxiv.org/abs/1511.05952`。

8\. Z. Wang, T. Schaul, M. Hessel et al., “Dueling network architectures for deep reinforcement learning”，在第 33 届机器学习国际会议论文集中，第 2 卷，第 2939–2947 页，美国纽约，2016 年。

9\. D. Silver, G. Lever, N. Heess et al., “Deterministic policy gradient algorithms”，在第 31 届机器学习国际会议论文集中，第 387–395 页，中国北京，2014 年 6 月。

10\. T. P. Lillicrap, J. J. Hunt, A. Pritzel et al., “Continuous control with deep reinforcement learning”，计算机科学，第 8 卷，第 6 期，第 A187 页，2015 年。

11\. Z. Zheng, C. Yuan, Z. Lin et al., “Self-adaptive double bootstrapped DDPG”，第 27 届国际联合会议论文集。

{¢ {

12\. < ° £²+ policy gradient with an off-policy critic”，国际学习表示会议论文集。

13\. V. Mnih, A. P. Badia, M. Mirza et al., “Asynchronous methods for deep reinforcement learning”，第 33 届机器学习国际会议论文集，第 1928–1937 页，美国普里兰斯，2016 年 5 月。

14\. B. Efron and R. J. Tibshirani, An Introduction to the Bootstrap，CRC Press，美国佛罗里达州博卡拉顿，1994 年。

15\. I. Osband, C. Blundell, A. Pritzel et al., “Deep exploration via bootstrapped DQN”，第 33 届神经信息处理系统会议论文集，第 4026–4034 页，西班牙巴塞罗那，2016 年 12 月。

16\. Z. Yang, K. E. Merrick, H. A. Abbass et al., “Multi-task deep reinforcement learning for continuous action control”，第 3301–3307 页，澳大利亚墨尔本，2017 年 8 月。

17\. R. Lowe, Y. Wu, A. Tamar et al., “Multi-agent actor-critic for mixed cooperative-competitive environments”，神经信息处理系统进展，2017 年。

18\. W. Shi, S. Song, and C. Wu, “Soft policy gradient method for maximum entropy deep reinforcement learning”，2019 年，`https://arxiv.org/abs/1909.03198`。

19\. R. Davidson and E. Flachaire, “Asymptotic and bootstrap inference for inequality and poverty measures”，经济学杂志，第 141 卷，第 1 期，第 141–166 页，2007 年。

20\. H. Ishwaran, L. F. James, and M. Zarepour, “An alternative to the out of bootstrap”，统计规划与推断杂志，第 139 卷，第 3 期，第 788–801 页，2009 年。

21\. J. Wu and H. Li, “Aggregated multi-deep deterministic policy gradient for self-driving policy”，第 5 届车辆物联网国际会议论文集，第 11253 卷，第 179–192 页，法国巴黎，2018 年 11 月。

22\. A. M. F. Mood, Introduction to the 5eory of Statistics，麦格劳-希尔教育，美国纽约，2015 年。

23\. A. Dvoretzky, J. Kiefer, and J. Wolfowitz, “Asymptotic minimax character of the sample distribution function and of the classical multinomial estimator”，第 5e《数学统计学报》，第 27 卷，第 3 期，第 642–669 页，1956 年。

24\. B. Wymann, E. Espie, C. Guionneau et al., ´ Torcs: 5e Open Racing Car Simulator，SourceForge，2015 年。

本书版权归 Arcler 所有

![Image 308](img/index-79_1.png)

![Image 309](img/index-79_2.png)

![Image 310](img/index-79_3.png)

Deep Learning Algorithms

52

13\. V. Mnih, A. P. Badia, M. Mirza et al., “Asynchronous methods for deep reinforcement learning”，第 33 届机器学习国际会议论文集，第 1928–1937 页，美国普里兰斯，2016 年 5 月。

14\. B. Efron and R. J. Tibshirani, An Introduction to the Bootstrap，CRC Press，美国佛罗里达州博卡拉顿，1994 年。

15\. I. Osband, C. Blundell, A. Pritzel et al., “Deep exploration via bootstrapped DQN”，第 33 届神经信息处理系统会议论文集，第 4026–4034 页，西班牙巴塞罗那，2016 年 12 月。

16\. Z. Yang, K. E. Merrick, H. A. Abbass et al., “Multi-task deep reinforcement learning for continuous action control”，第 3301–3307 页，澳大利亚墨尔本，2017 年 8 月。

17\. R. Lowe, Y. Wu, A. Tamar et al., “Multi-agent actor-critic for mixed cooperative-competitive environments”，神经信息处理系统进展，2017 年。

18\. W. Shi, S. Song, and C. Wu, “Soft policy gradient method for maximum entropy deep reinforcement learning”，2019 年，`https://arxiv.org/abs/1909.03198`。

19\. R. Davidson and E. Flachaire, “Asymptotic and bootstrap inference for inequality and poverty measures”，经济学杂志，第 141 卷，第 1 期，第 141–166 页，2007 年。

20\. H. Ishwaran, L. F. James, and M. Zarepour, “An alternative to the out of bootstrap”，统计规划与推断杂志，第 139 卷，第 3 期，第 788–801 页，2009 年。

21\. J. Wu and H. Li, “Aggregated multi-deep deterministic policy gradient for self-driving policy”，第 5 届车辆物联网国际会议论文集，第 11253 卷，第 179–192 页，法国巴黎，2018 年 11 月。

22\. A. M. F. Mood, Introduction to the 5eory of Statistics，麦格劳-希尔教育，美国纽约，2015 年。

23\. A. Dvoretzky, J. Kiefer, and J. Wolfowitz, “Asymptotic minimax character of the sample distribution function and of the classical multinomial estimator”，第 5e《数学统计学报》，第 27 卷，第 3 期，第 642–669 页，1956 年。

24\. B. Wymann, E. Espie, C. Guionneau et al., ´ Torcs: 5e Open Racing Car Simulator，SourceForge，2015 年。

本书版权归 Arcler 所有

![Image 308](img/index-79_1.png)

![Image 309](img/index-79_2.png)

![Image 310](img/index-79_3.png)

Deep Learning Algorithms

53

25\. D. Loiacono, L. Cardamone, and P. L. Lanzi, Simulated Car Racing Championship: Competition Software Manual，Politecnico di Milano，Dipartimento di Elettronica, Informazione e Bioingegneria，Milan，Italy，2013 年。

26\. R. Liu and J. Zou, “/e effects of memory replay in reinforcement learning”，第 ICML 2017 工作坊论文集，澳大利亚悉尼，2017 年，`https://arxiv.org/pdf/1710.06574.pdf`。

本书版权归 Arcler 所有

![Image 311](img/index-311)

![Image 312](img/index-312)

![Image 313](img/index-313)

本书版权归 Arcler 所有

![Image 314](img/index-81_1.png)

![Image 315](img/index-81_2.png)

![Image 316](img/index-81_3.png)

# CHAPTER 3 DYNAMIC DECISION-MAKING FOR STABILIZED DEEP LEARNING SOFTWARE PLATFORMS

Soohyun Park1, Dohyun Kim2 and Joongheon Kim1

1Korea University, Seoul, Republic of Korea

2Naver Webtoon Corporation, Seongnam, Republic of Korea

## ABSTRACT

本章介绍了一种动态且低复杂度的决策算法，旨在实现深度学习平台的时间平均效用最大化，灵感来自 Lyapunov 优化。在深度学习计算中，由于计算成本高昂，可能会出现大延迟。因此，处理延迟是深度学习算法商业化的重要问题。本文提出的算法首先观察系统延迟，并在此基础上动态地在效用（即深度学习性能）和系统延迟之间进行权衡。为了评估所提算法的性能，本文在超分辨率框架的应用下，展示了真实数据的评估结果。最后，本文总结说 Lyapunov 优化算法可以应用于各种新兴应用。

**Keywords:-** Lyapunov optimization, stochastic optimization, real-time computing, deep learning platforms, computer vision platforms

## INTRODUCTION

当今，各种机器学习和深度学习算法已在计算机视觉、自然语言处理等众多应用中得到发展。此外，这些算法的性能不断提升。因此，机器学习和深度学习算法的发展已趋于成熟。然而，专注于算法在现实世界中实现的研究贡献相对较少，相比之下，算法本身的发展更为丰富。为了在现实世界中运行深度学习算法，必须考虑实时计算的问题。

因此，延迟处理是必要的，因为深度学习算法的计算通常会引入大延迟。在通信和网络研究文献中，存在一种著名的随机优化算法，用于在保持系统稳定的同时最大化效用函数。

这里，稳定性以队列建模，而该算法旨在在稳定队列动态的同时优化计算。
