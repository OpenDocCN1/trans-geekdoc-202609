

![](img/058011bdc8fc3d3d77199bfcbf721be0_61_0.png)

图 3.11 CF 计算。

- 3. 接收到 RREQ 数据包后，每个中间节点评估 \(\mu\)。如果 \(\mu > \tau\)，则转发 RREQ 数据包。否则，丢弃该请求。
- 4. 在传输过程中，RREQ 数据包会累乘其遇到的所有节点的 DoT。
- 5. 目标节点接受具有最高 DoT 的 RREQ 数据包并回复。

## 示例拓扑中的 QTFPN 路由

在图 3.12(a) 中，示例 MANET 拓扑包含八个节点，其中 1 和 8 分别为源节点和目标节点。在图 3.12(b) 中，相同的 MANET 被建模为 DFPN。这里，源节点到目标节点有五条备选路径，即 1-2-5-8、1-3-5-8、1-3-6-8、1-4-6-8 和 1-4-7-8。但由于 \(\mu < \tau\)，路由 1-4-6-8 无效。接下来，评估路由 1-2-5-8 的 DoT 值如下：

```
(1 x 0.8) > 0.3 => 0.8
(0.8 x 0.7) > 0.4 => 0.56
(0.56 x 0.8) > 0.3 => 0.448
```

同样，我们可以分别评估剩余三条路径的 DoT 值为 0.576、0.567 和 0.448。在此，路径 1-3-5-8 具有最大 DoT；因此，目标节点选择此路径。

## 3.4.3 Dempster-Shafer 理论

Dempster-Shafer 理论 [3] 是数学聚合函数。节点使用 DST 来聚合多个信任推荐

![](img/058011bdc8fc3d3d77199bfcbf721be0_62_0.png)

![](img/058011bdc8fc3d3d77199bfcbf721be0_62_1.png)

**图 3.12** (a) MANET 网络拓扑。(b) 基于 DFPN 建模的 MANET 网络。

这些推荐是从多个路径接收的。DST 方法可以识别有偏推荐，并能降低有偏推荐对信任计算的影响。

DST 函数依赖于三个函数，即质量函数、可能性函数 (PI) 和信念函数 (Bel)。设事件 e 发生，E = {e1, e2, e3} 是关于事件 e 的证据集。幂集 P(E) 是 {Ø, {e1}, {e2}, {e3}, {e1, e2}, {e2, e3}, {e1, e3}, {e1, e2, e3}}。

*质量函数*：质量函数 (m) 将 P(E) 中的所有子集映射到范围 [0,1]，m:P(E) → [0,1]，其中 m(Ø) = 0 且 ΣB∈P(E) m(B) = 1。

*信念函数* (Bel)：如果 X 是 P(E) 中的子集，则 bel(X) = ΣC⊆X m(C)。

*可能性函数* (pl)：如果 X 是 P(E) 中的子集，则 pl(X) = ΣC∩X≠Ø m(C)。

### 3.4.3.1 组合的 Dempster 规则

![](img/058011bdc8fc3d3d77199bfcbf721be0_63_0.png)

图 3.13 QoS 信任推荐的聚合。

设 X 是 P(E) 中的元素，A 和 B 是关于事件 X 的两个观测节点。它们的观测表示为 m<sub>A</sub>(X) 和 m<sub>B</sub>(X)。这两个观测的组合可以使用公式 (13) 计算。

```
m_{A,B}(X) = \frac{\Sigma_{P \cap Q=X} m_A(P) m_B(Q)}{1 - K} (13)
```

其中常数 K 定义为 K = \Sigma_{P \cap Q = \emptyset} m_A(P) m_B(Q)。

### 3.4.3.2 DST 示例

在图 3.13 中，节点 S 正在从节点 P 和 Q 获取关于节点 D 的信任推荐。信任推荐的形式为 (T, T̄, U)，即分别表示信任、不信任和不确定性。在此，节点 P 和 Q 对节点 D 的信任推荐分别为 {0.7, 0.2, 0.1} 和 {0.3, 0.5, 0.2}。这些推荐会乘以各自的信任值。

节点 S 对 P 有 0.9 的信任，因此 P 的信任被重新计算为

```
m<sub>P</sub>(T) = T<sub>P</sub> × 0.7 = 0.63
m<sub>P</sub>(T̄) = T<sub>P</sub> × 0.2 = 0.18
m<sub>P</sub>(U) = T<sub>P</sub> × 0.1 = 0.09
```

节点 S 对 Q 有 0.8 的信任，因此 Q 的信任被重新计算为

```
m<sub>Q</sub>(T) = T<sub>Q</sub> × 0.3 = 0.24
m<sub>Q</sub>(T̄) = T<sub>Q</sub> × 0.5 = 0.40
m<sub>Q</sub>(U) = T<sub>Q</sub> × 0.2 = 0.16
```

P、Q 节点对节点 D 的推荐聚合按公式 (21) 评估如下。

\( m_{P,Q}(T) = \frac{m_P(T)m_Q(T) + m_P(T)m_Q(U) + m_P(U)m_Q(T)}{1 - [m_P(T)m_Q(\overline{T}) + m_P(\overline{T})m_Q(T)]} \)
\( = \frac{0.05}{0.09} = 0.55 \)

该公式可以扩展用于组合 n 个节点对节点 D 的推荐，即 \( m_{1.....n}(T) \)。

## 3.4.4 信任矩阵运算

信任矩阵运算用于在网络中传播信任值，以避免同一节点的信任计算工作风险。

此处每个节点都有信任信息，并以 \( n \times n \) 阶矩阵格式维护该信息（n 表示网络中的节点数量）。

\( N^T = \left( \begin{array}{ccccc} t_{11} & ... & t_{k1} & ... & t_{n1} \\ ... &  & ... &  & ... \\ t_{1k} & ... & t_{kk} & ... & t_{nk} \\ ... &  & ... &  & ... \\ t_{1n} & ... & t_{kn} & ... & t_{nn} \end{array} \right) \) (14)

在公式 (14) 中，\( t_{ij} \) 表示节点 i 对节点 j 的信任值。使用信任矩阵运算，节点可以计算非直接通信目标节点的信任值（通过应用信任传递规则）。

信任传递规则：

- i. \( t_{ij} \)：节点 i 对节点 j 的信任值
- ii. \( t_{jk} \)：节点 j 对节点 k 的信任值
- iii. 然后节点 i 对节点 k 的信任值计算为 \( t_{ik} = t_{ij} * t_{jk} \)。

设 \( t_i = [t_{i1}....t_{ik}....t_{in}] \) 为节点 i 的信任向量；它可以使用公式 (15) 进行迭代更新。

\(\left( \begin{array}{c} t_{i1} \\ ... \\ t_{ik} \\ ... \\ t_{in} \end{array} \right)_{NEXT} = \left( \begin{array}{ccccc} t_{11} & ... & t_{k1} & ... & t_{N1} \\ ... &  & ... &  & ... \\ t_{1k} & ... & t_{kk} & ... & t_{Nk} \\ ... &  & ... &  & ... \\ t_{1n} & ... & t_{kn} & ... & t_{nn} \end{array} \right) \otimes \left( \begin{array}{c} t_{i1} \\ ... \\ t_{ik} \\ ... \\ t_{in} \end{array} \right)_{CURRENT} \) (15)

在公式 15 中，值 \( t_{ik} \) 计算为 \( t_{ik} = max_{1 \le j \le n} \{t_{ij} \times t_{jk}\} \)。

此处节点 i 可以迭代应用此公式来查找多跳外节点的信任值，例如

- \( t_i = (N^T)t_i \)
- \( t_i = (N^T)^2t_i \)
- \( \vdots \)
- \( t_i = (N^T)^n t_i \)

## 3.5 结论

在 MANET 中，由于资源约束和网络动态性，复杂安全算法的实现会降低网络性能。在这项工作中，通过信任处理方法克服了这一局限性。此处在评估节点信任时会考虑能力（资源）和态度。对信任攻击及其对策进行了全面讨论。不同的软计算技术（即模糊逻辑、模糊 Petri 网、Dempster-Shafer 理论和信任矩阵运算）被讨论用于 MANET 中的信任管理。

## 参考文献

- 1. NageswaraRao Sirisala 和 C. Shoba Bindu. 基于模糊 Petri 网的 MANET 中新型 QoS 信任计算，International Journal of Intelligent Engineering and Systems，vol. 10, no. 2, 2017, pp. 116–125.
- 2. Yating Wang; Ing-Ray Chen. 面向服务的 Ad Hoc 网络中基于信任的多目标优化任务分配，vol. 14, no. 1, 2017, pp. 217–232.
- 3. NageswaraRao Sirisala 和 C. Shoba Bindu. 基于推荐的移动 Ad Hoc 网络中 QoS 信任聚合与路由，International Journal of Communication Networks and Information Security (IJCNIS)，vol. 8, no. 3, 2016, pp. 215–220.
- 4. Zeinab Movahedi, Zahra Hosseini. 移动 Ad Hoc 网络中信任扭曲信任管理框架：综述，IEEE Communications Surveys & Tutorials，vol. 18, no. 2, 2016, pp. 1287–1309.
- 5. NageswaraRao Sirisala 和 C.Shoba Bindu. 移动 Ad Hoc 网络中组播路由的基于模糊逻辑的 QoS 信任模型，International Journal of Applied Engineering Research vol. 10, no. 12, 2015, pp. 32175–32194.
- 6. NageswaraRao Sirisala 和 C. Shoba Bindu. MANET 中基于不确定规则的模糊逻辑 QoS 信任模型，International Conference on Advanced Computing and Communications - ADCOM，(IITM PhD 论坛)，2015, pp. 55–60.
- 7. F. Hao, G. Min 和 M.Lin. MobiFuzzyTrust：移动社交网络中高效模糊信任推断机制，IEEE Transactions on Parallel and Distributed Systems，vol. 25, no. 11, 2014 pp. 2944–2955.
- 8. NageswaraRao Sirisala 和 C.Shoba Bindu. 移动 Ad Hoc 网络中基于权重的可信 QoS 协议，IEEE Global Conference on Wireless Computing and Networking，2014, pp. 283–287.
- 9. W. Zhexiong 和 Tang. 使用不确定推理进行信任管理的移动 Ad Hoc 网络安全增强，IEEE Transactions on Vehicular Technology，vol. 63, no. 9, 2014 pp. 4647–4658.
- 10. F. Bao, J. Hee 和 C. Ing-Ray. 移动 Ad Hoc 网络中用于偏差最小化和应用性能最大化的信任管理，Ad Hoc Networks，vol. 19, 2014 pp. 59–74.
- 11. H. C. Liu 和 L. Liu. 使用模糊证据推理和动态自适应模糊 Petri 网进行知识获取与表示，IEEE Transactions On Cybernetics，vol. 43, no. 3, 2013, pp. 1059–1072.
- 12. Lei Ju, Edwin H. M. Sha, Hui Xia, Zhiping Jia, Xin Li. 移动 Ad Hoc 网络中的信任预测与基于信任的源路由，Ad Hoc Networks Elsevier，vol. 11, no. 7, 2013, pp. 2096–2114.

