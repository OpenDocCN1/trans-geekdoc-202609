
# 认知无线电网络与会会

并行遗传算法（GAs）具有某种形式的迁移或种群成员共享，以便对结果进行全局分析以找到解决方案。迁移的设计应该考虑到所需的网络开销。另一个问题是，认知无线电网络是动态的，节点会随机加入或离开。大多数并行遗传算法的研究是在处理元素网络已为该任务建立的假设下进行的。相反，认知无线电网络中的并行遗传算法是将并行化作为正常通信的次要过程执行的。算法必须根据网络的动态性实现，并对处理节点的成本具有鲁棒性。分布式人工智能在改进全局解决方案方面具有巨大潜力，并能减少任何单个节点所需的时间和功率，但这些都是实现分布式系统时必须考虑的一些问题。

## 7.4 结论

虽然本章提供的答案较少，但我们讨论了认知无线电电在未来开发和部署中的一些重要考虑因素。认知无线电网络必须包含一种在所有节点之间传输波形的方法，并在设计新波形时考虑其他节点的需求。网络方面本身开启了利用分布式和并行处理来增强网络认知能力的潜力。无论何种，都必须考虑在网络上传输与认知无线电性能和网络维护相关信息所需的开销。

为了下一章实验的实际目的，节点控制使用的方法是在当开发出新波形时从一个节点到其他节点的简单推送方法。此外，默认波形提供了一个回退通道和调制，供节点在通信丢失时使用。

## References

- [1] J. Perez-Romero, O. Sallent, R. Agusti, and L. Giupponi, “A Novel On-Demand Pilot Channel Enabling Dynamic Spectrum Allocation,” IEEE Proc. DySPAN, 2007, pp. 46 – 54.
- [2] C. Cordeiro and K. Challapali, “C-MAC: A Cognitive MAC Protocol for Multi-Channel Wireless Networks,” IEEE Proc. DySPAN, 2007, pp. 147 – 157.
- [3] J. Zhao, H. Zheng, and G. Yang, “Distributed Coordination in Dynamic Spectrum Allocation Networks,” IEEE Proc. DySPAN, 2005, pp. 259 – 268.
- [4] P. D. Sutton, K. E. Nolan, and L. E. Doyle, “Cyclostationary Signatures for Rendezvous in OFDM-Based Spectrum Access Networks,” IEEE Proc. DySPAN, 2007, pp. 220 – 231.
- [5] B. Horine and D. Turgut, “Link Rendezvous Protocol for Cognitive Radio Networks,” IEEE Proc. DySPAN, 2007, pp. 444 – 447.
- [6] R. W. Thomas, R. S. Komali, A. B. Mackenzie, and L. A. DaSilva, “Joint Power and Channel Minimization in Topology Control: A Cognitive Network Approach,” IEEE ICC, Jun. 2007, pp. 6538 – 6543.
- [7] R. W. Thomas, D. H. Friend, L. A. DaSilva, and A. B. Mackenzie, “Cognitive Networks: Adaptation and Learning to Achieve End-to-End Performance Objectives,” IEEE Communications Magazine, Vol. 44, No. 12, pp. 51 – 57, Dec. 2006.
- [8] J. Neel, “Analysis and Design of Cognitive Radio Networks and Distributed Resource Management Algorithms,” Ph.D. diss., Virginia Tech, 2007.
- [9] D. E. Goldberg, Genetic Algorithms in Search, Optimization, and Machine Learning, Reading, MA: Addison-Wesley, 1989.
- [10] E. Alba and J. M. Troya, “A Survey of Parallel Distributed Genetic Algorithms,” Complexity, Vol. 4, No. 4, pp. 31 – 52, 1999.
- [11] W.-Y. Lin, T.-P. Hong, and S.-M. Liu, “On Adaptation Migration Parameters for Multi-Population Genetic Algorithms,” IEEE Proc. Systems, Man and Cybernetics, 2004, pp. 5731 – 5735.
- [12] J. P. Coohoon, W. N. Martin, and D. S. Richards, “Punctuated Equilibria: A Parallel Genetic Algorithm,” Proc. Int. Conf. Genetic Algorithms, New Frontiers, 1987, pp. 148 – 154.
- [13] L. Chambers, Practical Handbook of Genetic Algorithms: New Frontiers, Boca Raton, FL: CRC Press, 1995.

## 8 认知引擎示例

在过去的几个章节中，我们一直在构建认知引擎的设计。现在我们展示认知引擎的实现，并提供仿真和空口实验的示例。我们把实验分为四个部分开发：使用遗传算法设计波形的简单应用、在示例中添加干扰源、使用基于案例的决策理论反馈机制，最后是认知引擎在空中的应用。

我们在展示结果时必须解决的一个主要问题是缺乏用于比较结果的确定性机制。与之前介绍的背包问题（仅用一个指标代表优化的成功程度）不同，这里的结果是多维的。此外，对于复杂环境，存在许多潜在解决方案。

