

当此函数被调用时，飞地生成一对ECC公钥和私钥（分别称为PPK和PSK），并创建一个名为MCID的单调递增计数器。然后，飞地使用SealKey加密PPK、PSK和MCID。加密后的PPK、PSK和MCID称为sealedSignUpData。除了sealedSignUpData，飞地还生成一个报告和一个PSEmanifest。根据PoET规范，不清楚报告和PSEmanifest中确切包含哪些信息。推测它们用于证明目的。最后，矿工向网络广播一个加入请求（使用矿工的PPK签名），包括必要的身份验证信息。

网络中的其他节点将验证加入请求。如果成功，新矿工将被接受，并为新矿工生成一个内部注册证书。新加入的矿工随后必须等待c个区块在区块链上发布，之后才被允许参与新区块生成的竞争。当准备好这样做时，矿工将首先使用等待时间的局部平均值调用createWaitTimer()函数。该调用会立即返回一个waitTimer对象。尽管PoET规范没有明确说明，但推测矿工将在等待计时器过期的同时继续创建新区块。当计时器过期时，它将使用刚创建的新区块的摘要作为输入调用createWaitCertificate()。飞地随后将签名的waitCertificate返回给矿工。矿工随后将waitCertificate和新区块广播到网络。等待时长最低的waitCertificate的矿工将被选为本轮竞赛的胜者。

这种设计有一个潜在问题，因为等待调用采用localMean参数，恶意矿工可能将其操纵为远小于应有值的数值。为了缓解此类威胁，系统使用一种称为z-test的统计测试，以确定矿工是否不成比例地赢得了竞争，如果是，则将该矿工列入黑名单。

可以看出，PoET设计确实满足非交互式ZKP设计要求。等待时间的分布是一个完全随机的过程，由SGX环境控制，假设所有矿工都诚实地使用localMean。它还满足我们列举的一些要求，包括新鲜性、不可预测性、非交互式验证和抗溯源性。由于PoET实际上不使用任何谜题，因此谜题设计的不可逆性、完备性和可靠性要求不相关。

![](img/7320b1480d74f1d65f74659cab456782_404_0.png)

图 9.7 PoET共识的主要步骤。

图 9.7 说明了在有四个矿工且共识过程中无故障时PoET共识的主要步骤。表面上看，PoET似乎是一个为许可型区块链达成共识而设计良好的方案。然而，它存在几个问题。首先，PoET设计有明显的可扩展性问题。这是因为根据PoET的设计，每个矿工每轮都会广播一个带有waitCertificate的新区块。在收集广播消息后，即可确定本轮选举的胜者。如果矿工数量庞大，将会产生大量的广播消息。也许PoET最初就不是为大型网络设计的，这从PoET规范中使用的术语可以看出，其中矿工被称为验证者。事实上，比可扩展性问题更严重的问题还存在。在确定每次选举的胜者时，PoET规范没有描述执行此类检查的时间条件。节点是否应等待直到收到网络中每个矿工的输入？如果是这样，该设计就不是容错的，因为单个崩溃的节点将阻止系统取得进展。假设系统设计为容忍最多f个故障节点，并在每个节点收集n - f个输入后计算胜者，其中n是矿工总数。由于系统的异步性，不同节点可能收集不同的n - f输入集，那么它们的决定可能完全不同！PoET规范完全未描述此问题，且未提供任何恢复机制。PoET规范在描述胜者确定步骤时使用了术语"server"。也许假设单个服务器负责执行该任务，这将以单点故障为代价避免正确性问题。无论如何，PoET设计存在固有的技术问题。

## References

- 1. E. Akbari, W. Zhao, S. Yang, and X. Lou. 区块链参数对吞吐量和安全性的影响. In Proceedings of the 2020 International Conference on Blockchain Technology, pages 13–18. ACM, 2020.
- 2. M. Ball, A. Rosen, M. Sabin, and P. N. Vasudevan. 有用工作证明. IACR Cryptol. ePrint Arch., 2017:203, 2017.
- 3. M. Ben-Or. 自由选择的另一个优势（扩展摘要）完全异步一致性协议. In Proceedings of the second annual ACM symposium on Principles of distributed computing, pages 27–30, 1983.
- 4. J. Benet and N. Greco. Filecoin：去中心化存储网络. Protoc. Labs, pages 1–36, 2018.
- 5. I. Bentov, A. Gabizon, and A. Mizrahi. 无需工作量证明的加密货币. In International conference on financial cryptography and data security, pages 142–157. Springer, 2016.
- 6. K. P. Birman, R. van Renesse, et al. 使用Isis工具包的可靠分布式计算，第85卷. IEEE Computer Society Press Los Alamitos, 1994.
- 7. M. Castro and B. Liskov. 实用拜占庭容错与主动恢复. ACM Transactions on Computer Systems (TOCS), 20(4):398–461, 2002.
- 8. T. D. Chandra and S. Toueg. 面向可靠分布式系统的不可靠故障检测器. Journal of the ACM (JACM), 43(2):225–267, 1996.
- 9. Y. Deswarte, J-J. Quisquater, and A. Saïdane. 远程完整性检查. In Working conference on integrity and internal control in information systems, pages 1–11. Springer, 2003.
- 10. S. Dziembowski, S. Faust, V. Kolmogorov, and K. Pietrzak. 空间证明. In Annual Cryptology Conference, pages 585–605. Springer, 2015.
- 11. M. J. Fischer, N. A. Lynch, and M. S. Paterson. 存在一个故障进程时分布式共识的不可能性. Journal of the ACM (JACM), 32(2):374–382, 1985.
- 12. A. Gervais, G. O. Karame, K. Wüst, V. Glykantzis, H. Ritzdorf, and S. Capkun. 关于工作量证明区块链的安全性与性能. In Proceedings of the 2016 ACM SIGSAC conference on computer and communications security, pages 3–16, 2016.
- 13. S. Goldwasser, S. Micali, and C. Rackoff. 交互式证明系统的知识复杂性. SIAM journal on computing, 18(1):186–208, 1989.
- 14. Jutarul. Ppcoin - 质押烧穿漏洞. https://bitcointalk.org/index.php?topic=131901.0., Dec. 2012.
- 15. S. King. Primecoin：基于素数工作量证明的加密货币. http://primecoin.io/bin/primecoinpaper.pdf, July 2013.
- 16. S. King and S. Nadal. Ppcoin：基于权益证明的点对点加密货币. https://www.peercoin.net/whitepapers/peercoin-paper.pdf, Aug. 2012.
- 17. H. Kopp, C. Bösch, and F. Kargl. Koppercoin——一种带有财务激励的分布式文件存储. In Proceedings of the International Conference on Information Security Practice and Experience, pages 79–93. Springer, 2016.
- 18. L. Lamport. 分布式系统中的时间、时钟与事件排序. Commun. ACM, 21(7):558–565, July 1978.
- 19. L. Lamport. 快速Paxos. Distributed Computing, 19(2):79–193, 2006.
- 20. L. Lamport et al. Paxos简化. ACM Sigact News, 32(4):18–25, 2001.
- 21. L. Lamport, R. Shostak, and M. Pease. 拜占庭将军问题. ACM Transactions on Programming Languages and Systems, 4:382–401, 1982.
- 22. A. Miller, A. Juels, E. Shi, B. Parno, and J. Katz. Permacoin：将比特币工作重新用于数据保存. In Proceedings of the IEEE Symposium on Security and Privacy, pages 475–490. IEEE, 2014.
- 23. L. E. Moser, P. M. Melliar-Smith, D. A. Agarwal, R. K. Budhia, and C. A. Lingley-Papadopoulos. Totem：一种容错多播组通信系统. Communications of the ACM, 39(4):54–63, 1996.
- 24. Ngalim. 权益证明奖励调整（peercoin rfc-18）. https://github.com/peercoin/rfcs/blob/master/text/0018-pos-reward/0018-pos-reward.md, Apr. 2020.
- 25. C. Rackoff and D. R. Simon. 非交互式零知识证明与选择密文攻击. In Annual International Cryptology Conference, pages 433–444. Springer, 1991.
- 26. Y. Saito and M. Shapiro. 乐观复制. ACM Comput. Surv., 37(1):42–81, Mar. 2005.
- 27. H. Shacham and B. Waters. 紧凑型可检索性证明. In Proceedings of the International conference on the theory and application of cryptology and information security, pages 90–107. Springer, 2008.
- 28. A. Shoker. 通过运动证明实现可持续区块链. In Proceedings of the IEEE 16th International Symposium on Network Computing and Applications (NCA), pages 1–9. IEEE, 2017.
- 29. Y. Sompolinsky and A. Zohar. 比特币中的安全高速交易处理. In International Conference on Financial Cryptography and Data Security, pages 507–527. Springer, 2015.
- 30. W. Wang, D. T. Hoang, P. Hu, Z. Xiong, D. Niyato, P. Wang, Y. Wen, and D. I. Kim. 区块链网络中共识机制与挖矿策略管理综述. IEEE Access, 7:22328–22370, 2019.
- 31. W. Zhao. 构建可靠的分布式系统. John Wiley & Sons, 2014.
- 32. W. Zhao, S. Yang, and X. Luo. 关于公有链共识. In Proceedings of the 2019 International Conference on Blockchain Technology, pages 1–5, 2019.

