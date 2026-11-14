

![](img/5dae57f4a1241884c6422f3e85bf87af_2_0.png)

![](img/5dae57f4a1241884c6422f3e85bf87af_2_1.png)

被困在危险空间中。IUSs 与多样化机器人代理可以相互合作，为搜索和救援任务提供有前景的解决方案。这里，我们将各种机器人代理视为不同的功能角色。携带传感器的小型代理负责观察，其感知能力可以收集环境状态信息。下一步，此信息被发送到具有计算决策能力的代理，该代理可以从低维信息中抽象高维知识，例如事件类型、位置和目标大小，用于定向和决策。最后，不同事件应由不同类型的代理执行。例如，当检测到生命迹象时，救援机器人代理应到达目的地营救人类。当检测到火源时，消防机器人应扑灭火灾。具有不同角色的代理能够各尽其职，形成灵活且强健的基于角色的 Co-OODA 循环。在群体中，不同的功能角色需要共同完成 Co-OODA 循环，以最大化 IUS 的潜力。值得注意的是，我们强调群体的 OODA 循环。此外，完成 IUS 的 Co-OODA 循环的单个功能节点内部的代理个体也有一个 OODA 循环，这两者不可混淆。

## IV. 基于角色的 Co-OODA 系统中的深度强化学习框架和信息共享机制

基于角色的 Co-OODA 可以从两个方面加速 OODA 循环。一方面，Fig. 2 显示 IUSs 由具有不同任务角色的多个代理组成以执行任务。OODA 循环不再是顺序和线性的，而是包含多个相互关联和嵌套程序的高度集成结构。观察节点、定向节点、决策节点和动作节点可以并行执行各自的角色任务，从而加速 OODA 循环。在 Fig. 3 中，假设个体执行 OODA 循环子步骤的时间间隔为 τ，可以是实数或整数。这里我们假设 τ 为单位时间。在基于角色的 OODA 系统中，观察节点在时间 t 观察环境并向定向节点提供观察信息流。在时间 t+2，定向节点处理接收到的信息。此时，观察节点可以在 t+2 进入下一个 OODA 循环的观察阶段，并继续感知环境。使用基于角色的 Co-OODA 循环可以加速任务执行，整个 Co-OODA 循环更加集成。另一方面，适当的人工智能技术被应用于每个角色层，以加速 Co-OODA 子元素的运行，从而推动整个 Co-OODA 循环的运行。

无人系统的智能体现在利用人工智能技术（AI）在复杂环境中加速 OODA 循环速度，缩短对未知威胁的响应时间。在基于角色的 IUSs 中，代理根据 OODA 循环的子步骤承担不同的角色任务，因此在任务执行期间需要多个角色节点合作以完成 Co-OODA 循环。代理需要根据其角色和任务，从不同的时间抽象中学习其策略。多智能体深度强化学习（MADRL）是实现无人系统智能的基础技术之一，而信息共享是不同角色节点之间高效信息交换的基础。目前，MADRL 无法使代理在不同时间学习与角色相关的信息共享策略和行为决策策略。因此，研究创新的学习框架和信息共享机制以充分利用这一基于角色的系统非常重要。

为了充分利用基于角色的 Co-OODA 系统的特性，设计基于角色的 DRL 框架是基于角色的 Co-OODA 系统的学习和训练基础。角色节点需要各种 AI 来完成其任务。因此，需要将不同的 AI 方法添加到 DRL 框架中。在此框架上，每个个体学习其角色任务策略。目前，分层强化学习（HRL）方法可以将任务分解为不同抽象层级的若干子任务，以学习每个子任务的策略，并将多个子任务的策略组合起来形成有效的全局策略。学习过程可以基于不同的时间抽象来抽象和扩展动作集，代理通过在不同时间尺度级别上学习来实现分层控制。学习过程可以基于不同的时间抽象来抽象和扩展动作集，代理通过在不同层级上学习来实现分层控制。HRL 的任务分层思想可以应用于基于角色的 Co-OODA 系统的新 DRL 框架。不同节点根据其角色任务描述其动作集，并在不同时间尺度上执行策略学习。

如图 Fig. 4 所示，我们提出一个初步的基于角色的 DRL 框架。我们将完成基于角色的

![](img/5dae57f4a1241884c6422f3e85bf87af_3_0.png)

Co-OODA 循环的策略视为 $\pi$。策略 $\pi$ 可以定义为角色节点子策略的集合：$\pi = \{ \pi_1, \pi_2, \dots, \pi_i \}$，其中 $\pi_i$ 是每个角色层的策略。在学习过程中，不同的角色层需要不同的 AI 技术来学习其目标策略。观察层需要图像识别算法、自然语言处理及其他技术来处理感知到的环境信息。定向层需要利用大数据分析和知识图谱技术，对多维环境观察进行数据分析、知识提取、知识融合和知识处理，以获取聚合信息。决策层需要智能推理和规划算法，以完成聚合信息到动作的映射。动作层作用于环境以获取反馈到各层节点的奖励。因此，IUSs 需要一个新的 RL 框架，使用不同的 AI 来学习子策略并提供反馈以训练策略。在后续工作中，改进有效的基于角色的深度强化学习算法非常重要，该算法使每个角色节点能够使用各种 AI 方法分别学习其任务子策略，从而构建能够完成基于角色的 Co-OODA 系统的全局策略。

在基于角色的 Co-OODA 系统中，各角色层之间存在明显的信息依赖。在 Fig. 4 中，虚线表示节点之间的信息流。节点依赖高级数据链路来传输高保真、高质量的信息流，以保证持续的 OODA 循环。因此，节点之间高效的信息共享也是支持和加速 Co-OODA 循环的重要因素。基于角色的 Co-OODA 系统的信息共享机制也是亟待解决的问题之一。在信息共享层面，相同角色和不同角色的节点需要在不同方面制定信息通信协议。

我们提出一种初步的信息共享机制。对于相同角色层，节点需要使用分层通信拓扑，通过增强互补的本地信息来共享信息。节点被分为不同的组，每个组需要动态选举组长。同一组的节点需要学习发送什么消息以及何时向组长通信。例如，Fig. 4 显示观察层中有多个观察节点，这些节点形成不同的组。

子中心节点收集其他节点的信息，并整合需要在不同层之间传输的信息。子中心节点是不同角色层之间信息传输的桥梁。不同角色层的信息共享：观察节点在特定单位时间内感知环境状态后，需要学习识别和提炼重要信息，并确定是否需要发送到哪个定向节点。定向节点需要学习解释、排序、聚合和评估接收到的信息，将信息转换为聚合信息，以获取决策节点可使用的多维环境感知。决策节点基于定向节点获得的环境情况信息做出决策，并将信息指令传输给需要被激活以执行任务的动作节点。因此，在后续研究中，我们需要进一步优化有效的信息共享机制，以实现基于角色的 Co-OODA 系统的连续循环运行。

## V. 结论

本文分析了智能无人系统的发展趋势，并描述了基于角色的 Co-OODA 系统。为了更好地利用智能算法解决 IUS 的合作问题，我们初步提出了基于角色的 DRL 框架和信息共享机制。它们保证了每个角色节点的学习和信息流，以确保 OODA 的连续循环执行。

## 致谢

本工作部分得到中国国家重点研发计划（No. 2017YFB1001900）、中国国家自然科学基金（No. 61876151, 62032018）和中央高校基本科研业务费（No. 3102019DX1005）的支持。

## 参考文献

- [1] Silver, D., Schrittwieser, J., Simonyan, K., Antonoglou, I., Huang, A., Guez, A., Hubert, T., Baker, L., Lai, M., Bolton, A. et al. (2017). Mastering the game of Go without human knowledge. Nature, 550 354.
- [2] Kober, J., Bagnell, J. A. and Peters, J. (2013). Reinforcement learning in robotics: A survey. International Journal of Robotics Research, 32 1238–1274.
- [3] Bhalla S. Subramanian S G, Crowley M. Deep multi agent reinforcement learning for autonomous driving[C]//Canadian Conference on Artificial Intelligence. Springer, Cham, 2020: 67-78.
- [4] Zhang K. Yang Z, Basar T. Multi-agent reinforcement learning: A selective overview of theories and algorithms[J]. Arxiv preprint arXiv:1911.10635, 2019.
- [5] Xuan P. Lesser V, Zilberstein S. Communication decisions in multi-agent cooperation: Model and experiments[C]//Proceedings of the fifth international conference on Autonomous agents. 2001: 616-623.
- [6] S. Sukhbaatar, R. Fergus et al., "Learning multiagent communication with backpropagation," in Advances in neural information processing systems, 2016, pp. 2244–2252.
- [7] J. Jiang and Z. Lu, "Learning attentional communication for multiagent cooperation," in Advances in neural information processing systems, 2018, pp. 7254–7264.
- [8] Ioniţă C C. THE "MOSAIC" WARFARE: A NEW AMERICAN STRATEGY FOR THE FUTURE[J]. Strategic Impact, 2020, 75(2): 25-42.

