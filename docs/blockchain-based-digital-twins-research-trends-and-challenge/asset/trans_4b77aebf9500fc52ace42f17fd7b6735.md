

## 10.3.3.2 数字孪生区块链

基于区块链的实时机器每个物理部分的数字孪生（DTs）是由互连的数字孪生区块链网络组成的。这是一个通过区块链连接的多个数字孪生网络。DTBC账本存储了所有DT虚拟实体的状态信息、数字孪生的所有者、记录状态的时间、数字孪生与其物理实体同步的时刻，以及数字孪生之间交换的数据。图10.10展示了DTBC账本的数据结构。

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_343_0.png)

图 10.10 DT_Parts 的数据结构。

数字孪生的区块链网络如图10.11所示。带有每个DT_Parts交易数据的区块被创建，并根据构建RMBC时描述的步骤，添加到基于云的区块链网络中，使用基于以太坊的工作证明共识算法。

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_344_0.png)

图 10.11 数字孪生的区块链网络。

## 10.3.4 深度学习模型的构建

为了对从实时物联网机器中收集的序列数据及其数字实体（即数字孪生集合）的时间关系建模，所提框架考虑了基于RNN的学习模型。为了预测故障并识别需要及时维护的模式，需要对描述不同时期收集的机器部件状态的数据进行更长时间的依赖关系建模。为了预测机器运行行为的异常，需要识别预期目标特征与机器当前行为之间的差异。

所提框架通过两种类型的区块链RMBC和DTBC提供了这种支持。DTBC提供了机器的预期行为。预测性维护的另一个要求是找到状态信息序列之间的关系。令 $s_t$ 为机器在时间't'的状态，$s_{t-1}$ 为机器在时间't-1'的状态。在分析 $s_t$ 以以预测维护需求或故障概率时，也必须考虑't-1'时刻的机器状态知识，即 $S_{t-1}$。通过同样考虑之前的'n'个状态信息（如 $S_{t-1,t-2}, S_{t-3\dots t-n}$），可以提高预测任务的精确性。因此，长短期记忆（LSTM）神经网络被认为是所提预测性维护的合适学习模型。

LSTM可以使用从过去数据中获得的知识对当前输入进行分析和分类。LSTM可以决定哪些信息值得关注。LSTM的架构有四个门，以支持基于长期依赖关系的学习。这些门决定了学习、忘记、记忆和使用什么。学习门（Learning gate）接受当前状态 $C_t$ 和之前的短记忆记忆 $SM_{t-1}$ 作为输入。它决定哪些信息是相关的，并仅保留用于预测的学习。使用权重矩阵 $(M_n)$ 的学习门 $(lg)$ 操作如下：

```
$Learning Matrix (L_t) = \tanh(M_n [SM_{t-1}, S_t]) + bias\_n$
```
```
$Ignoring factor (ig_t) = (M_n [SM_{t-1}, S_t]) + bias\_n$
```
```
$lg_{output} = L_t \cdot ig_t$
```

遗忘门（Forgetting gate）接受长期记忆 $(SM_t)$ 作为输入，并决定忘记什么和记住什么，遵循如下：

```
$Ignoring factor (ig_t) = (M_n [SM_{t-1}, S_t]) + bias\_n$
```
```
$LM_t = LM_{t-1} \cdot ((M_n [SM_{t-1}, S_t]) + bias\_n)$
```

记忆门（remembering gate）的输出通过加上学习门和遗忘门的输出产生。使用门（use gate）结合长期记忆和短期记忆产生下一个单元的短期记忆。一旦将RMBC的数据输入到基于LSTM的模型，就可以预测故障类型。在DTBC的帮助下，预测精度得到了提高。所提框架的架构如图10.12所示。

![](img/5575f2d1bada0bd1c2731bf9be91c7c9_347_0.png)

图 10.12 基于数字孪生的预测性维护架构。

## 10.3.4.1 基于数字孪生的预测性维护挑战

预测性维护的主要挑战是工业机器数据和行为的可变性。所提框架采用的LSTM通过将隐藏层的sigmoid函数替换为ReLU可以解决梯度消失问题，但容易出现过拟合。

## 10.4 结论

在本章中，利用边缘计算、DT和区块链技术提出了一种用于物联网行业预测性维护的新型框架。从DT收集的数据改进了预测有效性。区块链技术的结合确保了利益相关者之间数据的流畅共享。

## 关键词
- 区块链
- 深度学习
- 数字孪生
- 边缘计算
- 工业机器
- 长期记忆
- 机器学习
- 新型框架
- 预测性维护
- 利益相关者

## 参考文献
1. Zwinska, B., & Wiercioch, J. (2022). 机器维护策略的选择。Sustainability, 14(19), 1953.
2. Sharma, J., Mittal, M. L., & Soni, G. (2022). 基于机器学习和可解释性的状态维护。International Journal of System Assurance and Management, 15(2).
3. Lavanya, S., Prasanth, A., & Jayachitra, S. (2021). 用于物联网应用的异构故障诊断的调优方法。Measurement, 183, 1–23.
4. Guo, H., & Yu, X. (2022). 区块链及其安全性。Blockchain: Research and Applications, 3(2).
5. Thang, P., Trang, T., & Tai, B. (2022). 区块链内的多媒体隐私、安全与保护。Proceedings of 5th IEEE International Conference on Contemporary Computing and Informatics, 1171–1176.
6. Chandana, K. P., Samaniego, S. L., & Chaudhary, S. S. C. (2022). 与区块链安全分析的智能边缘计算。International Journal of Communication Networks and Information Security (IJCNIS), 14(3), 110–122.
7. Hassan, N., Gilani, S., & Ahmed, E. (2018). 边缘计算在物联网中的作用。IEEE Communications Magazine, 56(11), 110–115.
8. Vinodha, D., & MaryAnita, E. A. (2018). 无线传感器网络的安全数据聚合技术。Archives of Computational Methods in Engineering, 26(8), 1134–3060.
9. Florian, E., Sgarbossa, F., & Zendaro, I. (2021). 基于机器学习的预测性维护：一种面向成本的实现模型。International Journal of Production Economics, 236, 108114.
10. Werbos, P. J. (2015). 非线性敏感性分析的应用。System Modelling and Optimization, 38, 762–770.
11. Serradilla, O., Zugasti, E., & Rodriguez, J. (2022). 预测性维护的深度学习模型：综述、比较、挑战与展望。Applied Intelligence, 52, 10934–10964.
12. Hasan, H. R., Salah, K., & Jayaraman, R. (2020). 创建数字孪生的区块链方法。IEEE Access, 8, 34113–34126.
13. Feng, H., Chen, D., & Lv, Z. (2022). VANET中基于数字孪生的车辆管理区块链。IEEE Transactions on Intelligent Transportation Systems, 23(20), 19613–19623.
14. Adi, S. (1979). 如何分享秘密。Communications of the ACM, 22(11), 612–613.
15. Kumar, P., Kumar, R., & Kumar, A. (2022). 用于数字孪生驱动的工业物联网安全通信的区块链和深度学习。

