
## 针对扣块后分叉（FAW）攻击的应对措施

为了解决FAW攻击问题，Kwon等人[31]引入了定时控制信标，这些信标由矿池运营者分配给矿工。针对每次分配，矿工计算并确定其拥有的工作量证明，然后将答案连同信标值一起发送给矿池运营者。几秒钟后，信标值会被更新，以便在有效解被保留并随后在网络中传播时发现恶意矿工。然而，作者也指出，该技术在某些场景下可能并不可行，并认为研究界和学术界仍在努力解决FAW攻击问题。

Chang和Park[32]提出了静默时间戳（Silent Timestamping）作为抵御FAW攻击的防御机制，该机制确保份额排序，并从本质上消除了FAW的激励效应。对理想攻击者针对静默时间戳的行为进行了研究，发现最佳FAW攻击策略被迫下降为道德挖矿。静默时间戳无需网络连接，也无需对矿工代码进行任何修改。因此，静默时间戳提供了一种可行、向后兼容且有效的保护方案。表1总结了各种区块链攻击面及其应对措施。

表1. 区块链攻击面及其应对措施摘要

| 序号 | 攻击类别 | 每个类别下的攻击类型 | 每种攻击的应对方案 |
|---|---|---|---|
| 1 | 区块链网络攻击 | 分布式拒绝服务 | 高检测率和低误报率[1]<br>信用加分惩罚策略（CBPS）[2]<br>增加区块大小[3] |
| 1 | 区块链网络攻击 | 交易可变性攻击 | 软分叉[5] |
| 1 | 区块链网络攻击 | 时间劫持 | 同步时钟 |
| 1 | 区块链网络攻击 | 路由攻击 | 矿池多归属[6] |
| 1 | 区块链网络攻击 | 女巫攻击 | 网络威胁情报平台[7]<br>信任链（Trustchain）[8] |
| 1 | 区块链网络攻击 | 日食攻击 | 对等节点监控[9] |
| 1 | 区块链网络攻击 | 针对权益证明网络的长距离攻击 | 最长链规则、移动检查点、密钥演化密码学、上下文感知交易和充分性规则[10] |

无需中介的去中心化应用，也是互联网安全基础设施关键组件的基石。因此，识别现有研究中尤其与区块链应用于网络安全问题相关的内容，对于探讨新兴技术如何提供解决方案以减少新出现的风险至关重要。

理解和管理区块链网络风险对区块链安全非常重要。区块链安全模型是确保这些控制措施安全的蓝图。区块链安全模型的构建应确保所有基本安全防护措施都得到所有必要安全手段的保护。要执行区块链解决方案的安全模型，管理员必须建立一个能够管理所有行业、治理、技术和流程风险的风险模型。因此，应审查与区块链相关的风险。然后，管理员必须根据以下三类措施制定安全措施来限制风险和威胁：实施区块链特有的安全机制，采用标准安全措施，并确保区块链上设有业务控制。

## 发表同意书

不适用。

## 利益冲突

作者声明不存在财务或其他方面的利益冲突。

## 致谢

声明无。

## 参考文献

- [1] J. Cheng, R. Xu, X. Tang, V.S. Sheng, and C. Cai, "An abnormal network flow feature sequence prediction approach for DDoS attacks detection in big data environment", Comput. Mater. Continua, vol. 55, no. 1, pp. 95-119, 2018.
- [2] H. Yang, J. Yuan, H. Yao, Q. Yao, A. Yu, and J. Zhang, "Blockchain-based hierarchical trust networking for JointCloud", IEEE Internet Things J., vol. 7, no. 3, pp. 1667-1677, 2020. [http://dx.doi.org/10.1109/JIOT.2019.2961187]
- [3] M. Saad, M.T. Thai, and A. Mohaisen, "POSTER: deterring ddos attacks on blockchain-based cryptocurrencies through mempool optimization", Proceedings of the 2018 on Asia Conference on Computer and Communications Security, 2018 pp. 809-811 [http://dx.doi.org/10.1145/3196494.3201584]
- [4] U. Rajput, F. Abbas, and H. Oh, "A solution towards eliminating transaction malleability in bitcoin", Journal of Information Processing Systems, vol. 14, no. 4, pp. 837-850, 2018.
- [5] Alex Boverman, "Timejacking & bitcoin", Culubas blog, 2011.
- [6] M. Apostolaki, A. Zohar, and L. Vanbever, "Hijacking bitcoin: Routing attacks on cryptocurrencies", 2017 IEEE Symposium on Security and Privacy (SP), IEEE, pp. 375-392, 2017. [http://dx.doi.org/10.1109/SP.2017.29]
- [7] S. Gong, and C. Lee, "Blocs: blockchain-based cyber threat intelligence sharing framework for sybil-resistance", Electronics (Basel), vol. 9, no. 3, p. 521, 2020. [http://dx.doi.org/10.3390/electronics9030521]
- [8] M. Samaniego, U. Jamsrandorj, and R. Deters, "Blockchain as a Service for IoT." In 2016 IEEE international conference on internet of things (iThings) and IEEE green computing and communications (GreenCom) and IEEE cyber, physical and social computing (CPSCom) and IEEE smart data (SmartData). IEEE, 2016, pp. 433-436.
- [9] E. Heilman, A. Kendler, A. Zohar, and S. Goldberg, "Eclipse attacks on bitcoin's peer-to-peer network", In 24th {USENIX} Security Symposium ({USENIX} Security 15), pp. 129-144. 2015.
- [10] E. Deirmentzoglou, G. Papakyriakopoulos, and C. Patsakis, "A survey on long-range attacks for proof of stake protocols", IEEE Access, pp. 28712-28725, 2019.
- [11] P. Gaži, A. Kiayias, and A. Russell, "Stake-bleeding attacks on proof-of-stake blockchains", 2018 Crypto Valley Conference on Blockchain Technology (CVCBT), 2018 pp. 85-92 [http://dx.doi.org/10.1109/CVCBT.2018.00015]
- [12] R. Canetti, S. Halevi, and M. Steiner, "Mitigating dictionary attacks on password-protected local storage", Annual International Cryptology Conference, 2006 pp. 160-179 [http://dx.doi.org/10.1007/11818175_10]
- [13] Y. Zhu, R. Guo, G. Gan, and W-T. Tsai, "Interactive incontestable signature for transactions confirmation in bitcoin blockchain", In: 40th Annual Computer Software and Applications Conference (COMPSAC) vol. 1. IEEE, 2016, pp. 443-448. [http://dx.doi.org/10.1109/COMPSAC.2016.142]
- [14] Z. Zheng, S. Xie, H. Dai, X. Chen, and H. Wang, An overview of blockchain technology: Architecture, consensus, and future trends. In 2017 IEEE international congress on big data (BigData congress). IEEE, 2017, pp. 557-564. [http://dx.doi.org/10.1109/BigDataCongress.2017.85]
- [15] M. Gentilal, P. Martins, and L. Sousa, "TrustZone-backed bitcoin wallet", Proceedings of the Fourth Workshop on Cryptography and Security in Computing Systems, 2017 pp. 25-28 [http://dx.doi.org/10.1145/3031836.3031841]
- [16] Shahriar Ebrahimi, Parisa Hasanizadeh, Seyed Mohammad Aghamirmohammadali, and Amirali Akbari, "Enhancing Cold Wallet Security with Native Multi-Signature schemes in Centralized Exchanges", 2021.
- [17] Alkhafifah, Ayman, Alex Ng, Paul A. Watters, and A. S. M. Kayes. "A Mechanism to Detect and Prevent Ethereum Blockchain Smart Contract Reentrancy Attacks." Frontiers in Computer Science 3 2021. [http://dx.doi.org/10.3389/fcomp.2021.598780]
- [18] A. Miller, A. Kosba, J. Katz, and E. Shi, "Nonoutsourcable scratch-off puzzles to discourage bitcoin mining coalitions", Proceedings of the 22nd ACM SIGSAC Conference on Computer and Communications Security, 2015 pp. 680-691 [http://dx.doi.org/10.1145/2810103.2813621]
- [19] M. Saad, L. Njilla, C. Kamhoua, and A. Mohaisen, "Countering selfish mining in blockchains", 2019 International Conference on Computing, Networking and Communications (ICNC), 2019 pp. 360-364 [http://dx.doi.org/10.1109/ICNC.2019.8685577]
- [20] M. Bastiaan, Preventing the 51%-attack: a stochastic analysis of two phase proof of work in bitcoin., 2015. http://referaat.cs.utwente.nl/conference/22/paper/7473/preventingthe-51-attack-a-stochasticanalysis-o

