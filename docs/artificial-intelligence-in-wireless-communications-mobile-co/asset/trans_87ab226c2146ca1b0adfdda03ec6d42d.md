

# 52 无线通信中的人工智能

[14] J. Feigin, "Practical Costas Loop: Designing a Simple and Inexpensive BPSK Costas Loop Carrier Recovery Circuit," RF Signal Processing, pp. 20 – 36, 2002.

[15] K. Mueller and M. Müller, “Timing Recovery in Digital Synchronous Data Receivers,” IEEE Trans. Communications, Vol. 24, No. 5, pp. 516 – 531, 1976.

[16] G. R. Danesfahani and T.G. Jeans, “Optimisation of Modified Mueller and Mueller Algorithm,” Electronics Letters, Vol. 31, No. 13, pp. 1032 – 1033, 1995.

[17] Ettus Research, LLC, Universal Software Radio Peripheral, [URL: http://ettus.com], 2009.

[18] P. MacKenzie, Software and Reconfigurability for Software Radio Systems, Ph.D. diss., Trinity College Dublin, Ireland, 2004.

[19] M. Robert, S. Sayed, C. Aguayo, R. Menon, K. Channak, C. V. Valk, C. Neely, T. Tsou, J. Mandeville, and J. H. Read, “OSSIE: Open Source SCA for Researchers,” Software Defined Radio Forum Technical Conference, 2004.

[20] E. Blossom, “gcell - An SPE Scheduler and Asynchronous RPC Mechanism for the Cell Broadband Engine,” Software Defined Radio Forum Technical Conference, 2008.

[21] D. E. Knuth, The Art of Computer Programming, Volume 2: Seminumerical Algorithms, Vol. 3, Boston: Addison-Wesley, 1998.

## 4

## 无线资源优化

如上一章所示，认知无线电利用人工智能来适应并优化无线平台（特别是软件定义无线电 SDR）的性能。在本章中，我们解释了无线资源优化的概念，特别关注从一组目标函数的角度来理解物理层。这种讨论建立了一种思考如何优化特定目标的方法。尽管本章仅包含了所有可能目标的一个子集以及一些基础近似，但其开发应该提供基础，以便随着更多信息和能力的出现而进行进一步的扩展和增强。

### 4.1 目标空间

与任何问题一样，我们首先必须定义词汇。在优化问题中，这种词汇就是目标空间，它是问题所有可能解的集合，通常位于多维目标函数集合上。认知无线电目标空间描述了决定无线行为的无线资源。

无线电在通信时会消耗资源，从而剥夺其他无线电访问相同资源的机会。频谱是关键通信资源。从经济角度来说，频谱是一种可重复资源，在一个无线电消耗频谱后，仍然供其他无线电使用。事实上，无线电可以在空间、时间、发射功率和其他允许信号在相同频率上共存的方法上共享频谱。频谱共享和复用通过许多技术实现，例如小区基础设施中的空间分布或波形天线 [1]。时分多址（TDMA）和分频多址（FDMA）等标准允许允许时域和频域进行共享和复用。频谱接入（DSA）技术正在发展，以提供智能方案，在主用户空闲时使用频谱 [2]。超宽带下层接入和干扰温度等概念都是通过管理发射功率来允许与其他无线系统共存的方法 [3, 4]。最后，传输如直接序列扩频（DSSS）等正交信号可以减少占用同一时间的信号之间的干扰。任务是妥善利用资源，在所有无线电之间提供适当的共享，同时维持适当的服务质量（QoS）。

每个用户对基于无线电性能的服务质量有不同且主观的观点。根据使用无线电服务的情况，无线电可能需要高数据速率、低延迟或长电池寿命。视频会议需要高数据速率和低延迟，而语音通话需要低延迟，但对平均吞吐量的要求显著降低。另一方面，查看股票价格甚至人类对速度也有要求。在没有电源的情况下的长途旅行会增加对低功耗和更长运行时间的偏好。

网络中的每个节点都可以将资源分配视为一个具有两个潜在目标的问题。首先，它可以尝试通过最大化资源利用化来优化其通信能力；这是一种贪心算法方法。另一种方法是从需求角度看资源利用率；即寻求资源来支持服务需求。使用更多资源是浪费，而使用较少资源会降低服务质量。在需求的任何一方进行资源分配都是低效的。当然，看待资源分配还有第三种方法，即从全局角度来看，考虑所有节点的资源利用情况 [5]。虽然这种方法有巨大的收益，但我们在这里提出的论点在于对提供服务质量的个人观点，因此是看无线电如何利用资源提供用户所需的 QoS。认知无线电在最小化资源消耗的同时为用户提供适当的服务并允许资源共享。

另一种看待此问题的方法是考虑的目标分析。如果服务需要高数据速率、低比特错误率和低延迟，并且在使用特定波形时关注功率，无线电就有潜力平衡这些需求并设计出满足所有目标的波形。

## 无线资源优化

遗憾的是，BER（错误率）或 SINR 计算无法说明波形的全貌。如果使用了糟糕的编码器（编码/解码）或传播路径出现突发错误，语音系统的比特错误率并不一定意味着 QoS。许多因素影响无线系统的 QoS，因此需要联合优化和分析。从讨论可以看出，资源分配优化是一个多目标问题：多目标分析。下一节将讨论多目标优化概念以及物理层使用的目标。

### 4.2 目标空间：目标函数

多目标优化在数学、运筹学和经济学领域具有悠久的历史。Hwang 和 Sayed 的一本较旧的书 [6] 为多目标优化研究提供了全面的数学介绍。我们在 [7] 中为无线通信引入了这一概念，并在这里重复和扩展该讨论。Zitzler [8] 概述了多目标问题，并给出了多目标决策（MODM）问题的的基本公式，如 (4.1) 所示。

$min/max \tilde{y} = f(\tilde{x}) = [f_1(\tilde{x}), ..., f_n(\tilde{x})]$
受限于：$\tilde{x} = (x_1, x_2, ..., x_m) \in X$
$\tilde{y} = (y_1, y_2, ..., y_n) \in Y$ (4.1)

