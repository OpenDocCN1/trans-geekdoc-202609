

# 广播 vs. SPDZ vs. MYSTIKO

广播的性能和可扩展性远超标准环形协议，因为每个节点独立于其他节点进行传输。由于 SPDZ 要求在将每个参与者的梯度向量广播给其他参与者之前，先将其划分为秘密份额，因此 SPDZ 的效率和可扩展性不如广播。对于 MYSTIKO，双重广播是不必要的，因为数据使用 Paillier 理论进行加密，然后使用聚合梯度集中解密。切换到替代协议对两种不同性能类型的影响如[表 1](#ch4.xhtml#tab4_1)所示。

## 表 1. MYSTIKO：广播、环形和 SPDZ 相比于全归约的性能下降

### 通信时间

| # 参与方 | 全归约 | 广播 | 环形 | SPDZ |
| :--- | :--- | :--- | :--- | :--- |
| 20 | 1 | 64–7.2× | 382–39.9× | 131–14.2× |
| 40 | 1 | 79–8.6× | 705–80.8× | 138–14.7× |

### 总同步时间

| # 参与方 | 全归约 | 广播 | 环形 | SPDZ |
| :--- | :--- | :--- | :--- | :--- |
| 20 | 1 | 12–51% | 27–100% | 22–6.1× |
| 40 | 1 | 6–25% | 15–59% | 13–2.6× |

虽然全归约承诺“巨大”的加速，但当计入整个同步时间时，这些加速便消失了。这四种可扩展性协议的总体趋势没有变化；总同步时间的减少仍然相当可观（[表 4.1](#ch4.xhtml#tab4_1)中展示了两个例子）。然而，与增强通信所带来的收益相比，这些改进相当微不足道。这说明，与 MYSTIKO 和 SPDZ 中的非私有梯度下降相比，在共享梯度之前修改梯度所花费的时间是私有梯度下降的主要成本。[图 7](#ch4.xhtml#fig4_7)和[表 1](#ch4.xhtml#tab4_1)说明了通信时间对于不太复杂的模型（5 层 CNN 和 ResNet-18）变得越来越关键。然而，大型模型从梯度修改中获益更多（如 ResNet-50 和 VGG-16）。

在比较私有和非私有梯度下降时，作者发现当使用轮次时间作为训练时间的代理时，前者的同步时间明显更长。原因之一是梯度修改在 CPU 上执行，而训练在 V100 GPU（拥有数百个核心）上完成。尽管全同态加密确实存在（但在 CPU 上性能不如 Paillier），研究人员目前尚不知晓 Paillier 技术的 GPU 加速版本。

# 5.2 可信执行环境：AMD SEV

与 MYSTIKO 和 SPDZ 相比，最小开销是主要优势。使用 TEE 会导致更多工作，因为 EVM 必须执行聚合。每个联邦同步轮次产生了 2% 到 4% 的额外端到端延迟。收敛率和准确率均保持一致。

# 6. 结论

本章探讨了联邦学习中私有参数聚合的选项。显然，每种方法都有其优缺点，寻找最优解仍是一个持续的研究领域。尽管差分隐私在防止数据泄露方面显示出前景，但这是以牺牲模型准确性为代价的，并且需要非平凡的超参数调整（学习率调度、批量大小）以获得最佳结果（甚至是接近最佳的结果）。鉴于超参数调整依赖于所有参与者在较长时期内的可用性，且进行多次试验会增加总延迟，这在联邦场景中可能不切实际。使用同态加密或安全多方计算方案时，既不需要调整准确率，也不需要调整收敛率。然而，它们在运行时方面有显著开销；正如 MYSTIKO 所示，如果聚合协议设计良好，加法同态加密可以大幅降低这一开销。最后，如果有人愿意投资一些专用硬件，TEE 可以将聚合开销降低到几乎为零，且对准确率或收敛率没有负面影响。

## 参考文献

1.  [Abdel-Basset, M., Hawash, H. and Moustafa, N.](#ch4.xhtml#R_ref4_1) 2022. Toward privacy preserving Federated Learning in internet of vehicular things: Challenges and future directions. IEEE Consum. Electron. Mag., 11(6): 56–66. doi: [10.1109/MCE.2021.3117232.](http://dx.doi.org/10.1109/MCE.2021.3117232)

2.  [Ibitoye, O., Shafiq, M.O. and Matrawy, A.](#ch4.xhtml#R_ref4_2) 2022. Differentially private self-normalizing neural networks for adversarial robustness in Federated Learning. Comput. Secur., 116. doi: [10.1016/j.cose.2022.102631.](http://dx.doi.org/10.1016/j.cose.2022.102631)

3.  [Moudoud, H. and Cherkaoui, S.](#ch4.xhtml#R_ref4_3) 2022. Toward Secure and private Federated Learning for IoT using blockchain. In 2022 IEEE Global Communications Conference, GLOBECOM 2022—Proceedings, pp. 4316–4321. doi: [10.1109/GLOBECOM48099.2022.10000623.](http://dx.doi.org/10.1109/GLOBECOM48099.2022.10000623)

4.  [Guo, K., Chen, Z., Yang, H.H. and Quek, T.Q.S.](#ch4.xhtml#R_ref4_4) 2022. Dynamic scheduling for heterogeneous Federated Learning in private 5G edge networks. IEEE J. Sel. Top. Signal Process, 16(1): 26–40. doi: [10.1109/JSTSP.2021.3126174.](http://dx.doi.org/10.1109/JSTSP.2021.3126174)

5.  [Cholakoska, A., Pfitzner, B., Gjoreski, H., Rakovic, V., Arnrich, B. and Kalendar, M.](#ch4.xhtml#R_ref4_5) 2021. Differentially private federated learningfor anomaly detection in eHealth networks. In UbiComp/ISWC 2021 - Adjunct Proceedings of the 2021 ACM International Joint Conference on Pervasive and Ubiquitous Computing and Proceedings of the 2021 ACM International Symposium on Wearable Computers, pp. 514–518. doi: [10.1145/3460418.3479365.](http://dx.doi.org/10.1145/3460418.3479365)

6.  [Ziller, A. et al.](#ch4.xhtml#R_ref4_6) 2021. PySyft: A library for easy Federated Learning. Studies in Computational Intelligence, 965: 111–139. doi: [10.1007/978-3-030-70604-3_5.](http://dx.doi.org/10.1007/978-3-030-70604-3_5)

7.  [Augustine, C., Anand, J., Kaleeswaran, D., Muneeswari, G. and Santhoshkumar, S.P.](#ch4.xhtml#R_ref4_7) 2022. 6G-based mobile IPTV using adaptive hybrid transmission. In Handbook of Research on Design, Deployment, Automation, and Testing Strategies for 6G Mobile Core Network, IGI Global, pp. 72–91.

8.  [Liang, Y., Guo, Y., Gong, Y., Luo, C., Zhan, J. and Huang, Y.](#ch4.xhtml#R_ref4_8) 2021. FLBench: A benchmark suite for Federated Learning. Communications in Computer and Information Science, 1385 CCIS. pp. 166–176. doi: [10.1007/978-981-16-1160-5_14.](http://dx.doi.org/10.1007/978-981-16-1160-5_14)

9.  [Kong, L., Tao, H., Wang, J., Huang, Z. and Xiao, J.](#ch4.xhtml#R_ref4_9) 2020. Network coding for Federated Learning Systems. Lecture Notes in Computer Science (including subseries Lecture Notes in Artificial Intelligence and Lecture Notes in Bioinformatics), 12533 LNCS. pp. 546–557. doi: [10.1007/978-3-030-63833-7_46.](http://dx.doi.org/10.1007/978-3-030-63833-7_46)

10.  [Dhanalakshmi, R., Anand, J., Sivaraman, A.K. and Rani, S.](#ch4.xhtml#R_ref4_10) 2022. IoT-based water quality monitoring system using cloud for agriculture use. In Cloud and Fog Computing Platforms for Internet of Things, Chapman and Hall/CRC, pp. 183–196.

11.  [Wang, H., Li, A., Shen, B., Sun, Y. and Wang, H.](#ch4.xhtml#R_ref4_11) 2020. Federated multi-view spectral clustering. IEEE Access, 8: 202249–202259. doi: [10.1109/ACCESS.2020.3036747.](http://dx.doi.org/10.1109/ACCESS.2020.3036747)

12.  [Yang, Z., Zhou, M., Yu, H., Sinnott, R.O. and Liu, H.](#ch4.xhtml#R_ref4_12) 2023. Efficient and secure Federated Learning with verifiable weighted average aggregation. IEEE Trans. Netw. Sci. Eng., 10(1): 205–222. doi: [10.1109/TNSE.2022.3206243.](http://dx.doi.org/10.1109/TNSE.2022.3206243)

