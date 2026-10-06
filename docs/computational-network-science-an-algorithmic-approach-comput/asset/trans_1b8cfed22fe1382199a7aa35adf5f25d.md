
代理 $i$ 的链接在时刻 $t$ 的状态作为状态 $S^t$。代理可以执行两种动作之一：添加或删除链接，这会确定性地使代理从一个状态转移到另一个状态。如果代理拥有 $\sigma$ 个现有链接，它将有 $\sigma$ 个可用的“删除”动作和 $I-\sigma$ 个可用的“添加”动作，总共 $I=\sigma+I-\sigma$ 个动作。如果目标代理的添加链接得到响应，则建立双向链接（即：实现）。否则，链接是单向的（即：向性的）。如果删除链接得到目标代理的回应，则该双向链接将断开。否则，单向（即：向性的）链接将保留。由于目标代理的动作是未知的，我们可以以概率方式对链接状态的结果进行建模。

随着每个链接的添加或删除，代理的连接性网络拓扑结构发生变化，这为代理创建一个新状态（即状态）。如果两个代理对删除的链接相互响应，它们之间将创建一个双向链接。每个代理涉及 $I+1$ 个状态，其中 $I$ 个状态是通过 $I$ 个动作到达的。代理 $i$ 可能的 $I+1$ 个状态表示为 $M_i$，构成了一个马尔可夫状态空间，因为状态变化是动作改变链接的确定性函数。代理将重视那些赋予其更好结构属性（例如，中心性度量）的状态，$\mu_i$ 是为玩家 $i$ 的每个状态分配效用的函数。综合起来，$\langle M_i, A_i, \mu_i \rangle$ 是玩家 $i$ 的马尔可夫决策过程（MDP）（Howard，1960）。玩家 $i$ 可以求解自己的马尔可夫过程以获得标记为 $\pi^*$ 的最优策略。由于有 $n$ 个代理且每个代理对应一个 MDP，总共有 $I \times (I+1)$ 个状态。

同时

## 5.5 结论

网络属性随时间而变化。捕捉这些变化的模型就是网络动力学模型。我们概述了建模动力学的各种方法。显然，这只是未来丰富模型的开端。

## 参考文献

- Corten, R., Buskens, V., 2010. Co-evolution of conventions and networks: an experimental study. Soc. Netw. 32 (1), 4–15.
- Elder, G. (1988). The life course as developmental theory. In: Child Development, Vol. 69, No. 1. Wiley, New Jersey, pp. 1–12.
- Howard, R., 1960. Dynamic Programming and Markov Processes. MIT Press.
- Hutchison, E. (2003). Dimensions of Human Behavior: Person and Environment Trade, 33rd edition Sage Publications, CA, (paperback).
- Kleinberg, J. (2002). Buffy and hierarchical structure in streams. In: Proceedings of the 8th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. ACM Press, New York, NY.
- Kumar, R., Novak, J., Raghavan, P., Tomkins, A., 2003. On the evolution of blog space. The 12th Annual World Wide Web Conference. Budapest, Hungary, New York: ACM Press, New York, NY.
- Newman, M., 2004. Detecting community structure in networks. Eur. Phys. J B 38, 321–330.
- Newman, M., 2010. Networks: An Introduction. Oxford University Press.
- Norris, J., 1998. Markov Chains. Cambridge University Press.
- Roth, C., Conintet, J., 2010. Social and semantic coevolution in knowledge network. Soc. Netw. 32 (1), 1–3.
- Snijders, T., Doreian, P., 2010. Introduction to the special issue on network dynamics. Soc. Netw. 32 (1), 1–3.
- Strooks, D., 2005. Introduction to Markov Processes. Springer.
- Tang, J., Musolesi, M., Mascolo, C., Latora, V., 2009. Temporal distance metrics for social network analysis. In: Proceedings of the 2nd ACM Workshop on Online Social Networks. ACM Press, New York, NY, pp. 31–36.
- Westaby, J., 2011. Dynamic Network Theory: How Social Networks Influence Goal Pursuit. APA Press.

## 练习

- 1. 波动性网络如何用于建模通信网络？
- 2. 为一个具有历史意义的社会网络（例如总统大选）绘制时间图。
- 3. 设计一个 $2 \times 2$ 的协调游戏概率矩阵（例如，斗鸡游戏）。将矩阵视为马尔可夫链并预测状态的长期分布。

## 第 6 章
### 扩散与传染

本章探讨了网络中泛化变化的现象，例如（a) 偏好的传播、（b) 渗透、（c) 疾病的流行（即传染）以及 (d) 社区组成。本章的其余部分将顺序回顾这四类。

## 6.1 人口偏好扩散

Schelling (1971) 的居住社区隔离模型是关于网络泛化变化的最早正式研究报告。Schelling 指出，对邻居是同种族裔的微小偏好会导致网络中出现广泛的隔离。他通过在网格纸上使用硬币，通过在单元格中以不同的模式放置分币和镍币来证明这一理论。如果硬币的组合不令人满意，则移动硬币。对于每个有色的单元格，如果相邻单元格中颜色不同的比例超过 33%，该单元格将移动到另一个选定的单元格。你可以使用 Chris Cook 的在线演示程序或 NetLogo 模型运行该模型。更多细节和出现的模式可见 Hatna 和 Benenson (2012)。令 $N$ 为人口规模，$p$ 为网络中每个个人与另一个人存在联系的均匀随机概率。忽略重复连接。由于 $p$ 的值很小且 $N$ 的值很大，$PN$ 代表个人与网络中其他人间接连接的概率，即通过个人的主要链接建立的二手联系。预期（即平均）可到达的人数如公式 6.1 所示。（注：原文此处有大量重复，已去重）。
