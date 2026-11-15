

![](img/3cc494b92b35bef197b953dcaa648a44_231_0.png)

图 7.2
不同 $\delta$ 值下算法 1 的收敛性：$\delta = 0,\ \delta = 30,\ \delta = 60$, 和 $\delta = 120$。

influences convergence speed. Specifically, perturbations slow down convergence, and the size of $\delta$ is inversely related to algorithm performance. For smaller $\delta$, Algorithm 1's convergence closely resembles the decentralized dual averaging push algorithm [27] without privacy protection (i.e., $\delta = 0$).

影响收敛速度。具体而言，扰动会减慢收敛速度，$\delta$ 的大小与算法性能成反比。对于较小的 $\delta$，算法 1 的收敛性与无隐私保护（即 $\delta = 0$）的去中心化双平均推算法 [27] 非常接近。

![](img/3cc494b92b35bef197b953dcaa648a44_231_1.png)

图 7.3
在构建的有向网络 $\mathcal{G}$ 中，不同边采样概率下算法 1 的收敛性。

(iii) This part explores how varying network connectivity (different sampling probabilities) affects Algorithm 1's convergence (with other parameters the same as part (i)). Fig. 7.3 shows that network connectivity significantly impacts the convergence rate, whereas denser networks facilitate faster convergence.

（iii）本部分探讨不同网络连通性（不同采样概率）如何影响算法 1 的收敛性（其他参数与部分（i）相同）。图 7.3 显示，网络连通性显著影响收敛速率，而更密集的网络有利于更快的收敛。

### 7.6.2 去中心化能量源定位问题

In this subsection, we tackle a decentralized energy-based source localization problem, formulated as

在本小节中，我们研究一个去中心化能量源定位问题，其表述为

```
\min_{x \in \Omega} \sum_{i=1}^{m} (\frac{1}{n_i} \sum_{j=1}^{n_i} (m_{ij} - \frac{a}{||x - c_i||^v})^2)
```

where the parameters are provided in Section 7.2.3. In the simulations, m = 50 sensors were randomly placed in a 100 x 100 area. A stationary acoustic source x* \in \Omega \subseteq \mathbb{R}^2 is located at (60, 60), inaccessible to any sensors. Parameters are set to c = 100, v = 1.3, and n_i = 100 for i = 1, ..., 50. Following the method in Section 7.1, the time-varying directed network \Omega = [0, 100]^2 was constructed. The paths of Algorithm 1 (10 randomly selected) plotted over log-likelihood contours and its convergence performance are shown in Fig. 7.4 and Fig. 7.5, respectively. These figures indicate that Algorithm 1 can accurately pinpoint the source location of the decentralized energy-based problem at a sublinear rate.

其中参数见第 7.2.3 节。在仿真中，m = 50 个传感器随机布置在 100 × 100 的区域内。一个静止声源 x* \in \Omega \subseteq \mathbb{R}^2 位于 (60, 60)，任何传感器均无法访问。参数设置为 c = 100、v = 1.3，且对 i = 1, ..., 50 取 n_i = 100。沿用第 7.1 节的方法，构建了时变有向网络 \Omega = [0, 100]^2。算法 1（随机选取的 10 条路径）在对数似然轮廓线上的路径及其收敛性能分别见图 7.4 和图 7.5。这些图表明，算法 1 能以次线性速率准确定位去中心化能量问题的源位置。

![](img/3cc494b92b35bef197b953dcaa648a44_232_0.png)

**FIGURE 7.4** The 10 paths (randomly selected) of Algorithm 1 displayed on top of contours of the log-likelihood function.

**图 7.4** 算法 1 的 10 条路径（随机选取）显示在对数似然函数轮廓线之上。

## 7.7 结论

This study has introduced an effective privacy-preserving decentralized dual averaging push algorithm for time-varying directed networks. Theoretical analysis confirms that our algorithm not only safeguards the privacy of normal nodes but also converges precisely to the optimal solution under less stringent initial conditions compared to existing decentralized methods. Extensive simulations have been performed to validate the algorithm's effectiveness. However, the proposed algorithm is not without

本研究针对时变有向网络提出了一种有效的隐私保护去中心化双平均推算法。理论分析表明，与现有去中心化方法相比，我们的算法不仅能够保护普通节点的隐私，而且在较宽松的初始条件下也能精确收敛到最优解。已进行大量仿真以验证该算法的有效性。然而，所提算法并非

![](img/3cc494b92b35bef197b953dcaa648a44_233_0.png)

FIGURE 7.5
The convergence of Algorithm 1 with the residual being the same as in Section 7.1.

图 7.5
算法 1 的收敛性，残差与第 7.1 节相同。

its shortcomings, with some issues warranting further research. For instance, its current implementation is not cost-effective, and it is unsuitable for problems with general inequality constraints over random networks. Future work will focus on enhancing communication and computational efficiency by employing event-triggering communication strategies and unbiased stochastic gradient techniques. Additionally, developing robust privacy-preserving decentralized dual averaging algorithms to handle more complex problems (inequality constraints, random networks, etc.) remains a promising research avenue.

其不足之处，仍有一些问题有待进一步研究。例如，其实现目前不够经济高效，且不适用于随机网络上的一般不等式约束问题。未来工作将着重通过采用事件触发通信策略和无偏随机梯度技术来提升通信和计算效率。此外，开发稳健的隐私保护去中心化双平均算法以处理更复杂的问题（不等式约束、随机网络等）仍是一个有前景的研究方向。

## 参考文献

- [1] T. Yang, X. Yi, J. Wu, Y. Yuan, D. Wu, Z. Meng, Y. Hong, H. Wang, Z. Lin, K.H. Johansson, 分布式优化综述, Annual Reviews in Control 47 (2019年5月) 278–305.
- [2] L. Gao, S. Deng, H. Li, C. Li, 基于共识的分布式优化中梯度跟踪的事件触发方法, IEEE Transactions on Network Science and Engineering 9 (2) (2022年3-4月) 510–523.
- [3] C. Li, X. Yu, W. Yu, T. Huang, Z-W. Liu, 智能电网经济调度的分布式事件触发方案, IEEE Transactions on Industrial Informatics 12 (5) (2016年10月) 1775–1785.
- [4] L.-N. Liu, G.-H. Yang, 基于时变有向通信图的微电网分布式最优经济环保调度, IEEE Transactions on Network Science and Engineering 8 (2) (2021年4-6月) 1913–1924.
- [5] M. Assran, N. Loizou, N. Ballas, M. Rabbat, 分布式深度学习的随机梯度推, 载于: 第 36 届国际机器学习会议 (ICML) 论文集, 美国加利福尼亚州长滩, 2019, 第 344–353 页.
- [6] H. Li, Q. Lü, T. Huang, 具有一般不平衡有向通信网络的分布式优化算法收敛性分析, IEEE Transactions on Network Science and Engineering 6 (3) (2019年7-9月) 237–248.
- [7] M. Rossi, M. Centenaro, A. Ba, S. Eleuch, T. Erseghe, M. Zorzi, 物联网网络最优数据路由的分布式学习算法, IEEE Transactions on Signal and Information Processing over Networks 6 (2020年2月) 175–195.
- [8] C. Ke, C. Li, Q. Zhang, 基具有时滞状态约束脉冲协议的非线性多代理系统分布式自适应容错一致性, IEEE Transactions on Network Science and Engineering 7 (4) (2021年10-12月) 3112–3121.
- [9] H. Li, Q. Lü, G. Chen, T. Huang, Z. Dong, 基于异步广播算法的不平衡有向网络分布式约束优化, IEEE Transactions on Automatic Control 66 (3) (2021年3月) 1102–1115.
- [10] A. Nedic, A. Ozdaglar, 多代理优化的分布式次梯度法, IEEE Transactions on Automatic Control 54 (1) (2009年1月) 48–61.
- [11] A. Nedic, A. Olshevsky, 时变有向图上的分布式优化, IEEE Transactions on Automatic Control 60 (3) (2015年3月) 601–615.
- [12] J. Zhu, C. Xu, J. Guan, D. Wu, 时变有向网络上的差分隐私分布式在线算法, IEEE Transactions on Signal and Information Processing over Networks 4 (2018年3月) 4–17.
- [13] B. Huang, L.-N. Liu, H. Zhang, Y. Li, Q. Sun, 考虑通信延迟的微电网分布式最优经济调度, IEEE Transactions on Systems, Man, and Cybernetics: Systems 49 (8) (2019年8月) 1634–1642.
- [14] L.-N. Liu, G.-H. Yang, 集成能源系统分布式最优能量管理, IEEE Transactions on Industrial Informatics 18 (10) (2022年10月) 6569–6580, https://doi.org/10.1109/TII.2022.3146165.
- [15] L.-N. Liu, G.-H. Yang, 微电网分布式定时最优资源管理, IEEE Transactions on Automation Science and Engineering 20 (1) (2023年1月) 404–412, https://doi.org/10.1109/TASE.2022.3155163.
- [16] Z. Wang, H. Li, 基于边的分布式优化随机梯度算法, IEEE Transactions on Network Science and Engineering 7 (3) (2020年7-9月) 1421–1430.
- [17] J. Duchi, A. Agarwal, M. Wainwright, 分布式优化的双平均法: 收敛性分析与网络规模化, IEEE Transactions on Automatic Control 57 (1) (2012年3月) 151–164.
- [18] C. Liu, H. Li, Y. Shi, 面向分布式双平均法的 $O(1/t)$ 收敛速率, IFAC-PapersOnLine 53 (2) (2020年3月) 3254–3259.
- [19] C. Liu, Y. Shi, H. Li, 加速去中心化双平均法, arXiv 预印本, arXiv: 2007.00514v1, 2020年7月.
- [20] S. Hosseini, A. Chapman, M. Mesbahi, 动态网络上的在线分布式凸优化, IEEE Transactions on Automatic Control 61 (11) (2016年11月) 3545–3550.
- [21] C. Song, Y. Jiang, Y. Ma, 基于加速双平均法的有限和优化方差缩减, 载于: 神经信息处理系统进展 (NIPS), vol. 33, 2020, 第 833–844 页.
- [22] I. Colin, A. Bellet, J. Salmon, S. Clemencon, 成对函数去中心化优化的闲聊双平均法, 载于: 第 33 届国际机器学习会议论文集, 纽约, 纽约州, 美国, PMLR, vol. 48, 2016, 第 1388–1396 页.

