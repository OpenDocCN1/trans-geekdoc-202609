
我们首先解释了基于表格的 Q-learning 的使用，这是一种流行的 RL 实现，用于在认知无线网络（CRN）中遵循跨层方法分配资源；在此之后，我们指出，如果不加以解决，这种方法存在出现长时间收敛的风险。然后，我们从多个方向扩展了介绍。我们解释了当前解决基于表格的 Q-learning 中长时间收敛问题的方法，即将 Q 值（预期奖励）与动作和环境状态变量的对应关系近似为函数。这种 Q 函数的近似是通过一种称为深度 Q 网络的人工神经网络完成的。我们还探索了遵循第五代无线系统开发原则的资源分配，该原则将终端用户置于设计的中心。在这种方法中，资源分配基于体验质量作为性能指标。我们强调，采用平均意见评分作为 QoE 指标能够在分布式资源分配期间实现异构流量的无缝集成。

在章节的后半部分，我们重新审视了如何加速学习的问题。我们注意到，在无线网络中，很少会看到所有节点在同一（初始）时刻加入网络；相反，节点会在不同时间单独进入和离开网络。由此预期，当一个节点加入网络时，它会发现其他已经在运行的节点，对于 CR 而言，这些节点已经经历了学习过程，使其成为经验丰富的智能体。然后，我们解释了如何通过让网络中已有的这些 CR 充当教师并分享其经验，来加速加入网络的 CR 的学习。这一想法体现为所描述的协作学习和迁移学习技术。

以更广阔的视角作结，我们指出，认知无线电的许多最新发展利用了 ML 的重大新进展，这些进展通常应用于无线通信之外的技术领域。可见的例子包括自动驾驶汽车、计算机视觉和自然语言处理。然而，将这些新的 ML 技术应用于认知无线电会带来独特的兴趣和挑战，这些兴趣和挑战对于本例中的环境，即无线网络而言是独一无二的。特定于无线网络环境的是智能体如何通过它们彼此产生的干扰而耦合，以及智能体寻求并能够相互通信。探索这些环境的独特特征如何影响 ML 技术，正是研究 ML 在这一独特环境中应用的挑战、潜力和吸引力所在。

## 参考文献
1. ITU Radiocommunication Assembly. *电视图像质量的主观评估方法学*. International Telecommunication Union, 2003.
2. Yanjiao Chen, Kaishun Wu, and Qian Zhang. 从 QoS 到 QoE：视频质量评估教程. IEEE Communications Surveys and Tutorials, 17 (2):1126–1165, 2015.
3. Ognjen Dobrijevic, Andreas J Kassler, Lea Skorin‐Kapov, and Maja Matijasevic. Q-point：面向 QoE 的多媒体服务路径优化模型. In Int. Conf. on Wired/Wireless Internet Comm., pages 134–147. Springer, 2014.
4. L. Giupponi, A. Galindo‐Serrano, P. Blasco, and M. Dohler. Docitive networks：动态频谱管理的新兴范式. Wireless Communications, IEEE, 17(4):47 –54, 2010.
5. Andrea Goldsmith, Syed Ali Jafar, Ivana Maric, and Sudhir Srinivasa. 利用认知无线电打破频谱僵局：信息论视角. Proceedings of the IEEE, 97(5):894–914, 2009.
6. Ian Goodfellow, Yoshua Bengio, and Aaron Courville. Deep Learning. Adaptive Computation and Machine Learning series. Cambridge, MA: MIT Press, 2016.
7. Zhu Han, Dusit Niyato, Walid Saad, Tamer Başar, and Are Hjørungnes. Game Theory in Wireless and Communication Networks: Theory, Models, and Applications. Cambridge University Press, 2012.
8. Philippe Hanhart and Touradj Ebrahimi. 基于主观质量评分的平均编码效率计算. Journal of Visual Communication and Image Representation, 25(3):555–564, 2014.
9. Shoaib Khan, Svetoslav Duhovnikov, Eckehard Steinbach, and Wolfgang Kellerer. Mos‐based multiuser multiapplication cross‐layer optimization for mobile multimedia communication. *《多媒体进展》*, 2007.
10. A. Kwasinski and K.J.R. Liu. Source‐channel‐cooperation tradeoffs for adaptive coded communications [transactions papers]. IEEE Transactions on Wireless Communications, 7(9):3347–3358, September 2008. ISSN 1536‐1276. https://doi.org/10.1109/TWC.2008.060286.
11. Volodymyr Mnih, Koray Kavukcuoglu, David Silver, Andrei A Rusu, Joel Veness, Marc G Bellemare, Alex Graves, Martin Riedmiller, Andreas K Fidjeland, Georg Ostrovski, et al. 通过深度强化学习实现人类水平的控制. Nature, 518(7540):529–533, 2015.
12. Byte Mobile. Mobile analytica report. June 2011.
13. Fatemeh Shah Mohammadi and Andres Kwasinski. Neural network cognitive engine for autonomous and distributed underlay dynamic spectrum access. *arXiv 预印本 arXiv:1806.11038*, 2018.
14. Kandaraj Piamrat, Cesar Viho, Jean‐Marie Bonnin, and Adlen Ksentini. Quality of experience measurements for video streaming over wireless networks. In Information Technology: New Generations, 2009. ITNG'09. Sixth International Conference on, pages 1184–1189. IEEE, 2009.
15. Xiaoxin Qiu and Kapil Chawla. On the performance of adaptive modulation in cellular systems. IEEE transactions on Communications, 47(6):884–895, 1999.
16. Hamid R Sheikh, Muhammad F Sabir, and Alan C Bovik. A statistical evaluation of recent full reference image quality assessment algorithms. IEEE Transactions on image processing, 15(11):3440–3451, 2006.
17. David Silver, Aja Huang, Chris J Maddison, Arthur Guez, Laurent Sifre, George Van Den Driessche, Julian Schrittwieser, Ioannis Antonoglou, Veda Panneershelvam, Marc Lanctot, et al. Mastering the game of go with deep neural networks and tree search. Nature, 529(7587):484–489, 2016.
18. Richard S. Sutton and Andrew G. Barto. Reinforcement Learning: An Introduction. Cambridge, MA: MIT Press, 2011.
19. W. Wang, A. Kwasinski, D. Niyato, and Z. Han. A survey on applications of model‐free strategy learning in cognitive wireless networks. IEEE Communications Surveys Tutorials, 18(3): 1717–1757, thirdquarter 2016. ISSN 1553‐877X. https://doi.org/10.1109/COMST.2016.2539923.
20. Yeqing Wu, Fei Hu, Sunil Kumar, Yingying Zhu, Ali Talari, Nazanin Rahnavard, and John D Matyjas. A learning‐based qoe‐driven spectrum handoff scheme for multimedia transmissions over cognitive radio networks. IEEE J. on Sel. Areas in Comm., 32(11):2134–2148, 2014.

# 3 毫米波蜂窝网络中频谱共享的机器学习
*Hadi Ghauch¹, Hossein Shokri‐Ghadikolaei², Gabor Fodor³, Carlo Fischione², and Mikael Skoglund⁴*
¹*COMELEC 部门，Telecom ParisTech，巴黎，法国*
²*网络与系统工程部，皇家理工学院 KTH，斯德哥尔摩，瑞典*
³*决策与控制系统部，皇家理工学院 KTH，斯德哥尔摩，瑞典*
⁴*信息科学与工程部，皇家理工学院 KTH，斯德哥尔摩，瑞典*
