

因为请求仅在以下情况之一时完成：(1) 客户端接收到 3f + 1 条匹配的 SPEC-RESPONSE 消息，或 (2) 2f + 1 条匹配的 LOCAL-COMMIT 消息。由于非故障副本对相同序列号接受一条 ORDER-REQ 消息或发送一条 LOCAL-COMMIT，如果请求在情况 (1) 下完成，则没有其他请求可能使用相同序列号完成；如果请求在情况 (2) 下完成，任何其他请求最多只能收集 2f 条匹配的 ORDER-SEQ 或 LOCAL-COMMIT 消息，因此无法使用相同序列号完成。

接下来，假设 Req1 使用序列号 i 完成，Req2 使用序列号 j 完成。不失一般性，设 i < j。对于请求完成，至少有 2f + 1 个副本接受了 Req1 的 i，且至少有 2f + 1 个副本接受了 Req2 的 j。由于共有 3f + 1 个副本，这两个副本集合必须在至少 f + 1 个副本处相交，且其中至少有一个副本是非故障的。该非故障副本对 Req1 和 Req2 都进行了排序。这将确保 hi 是 hj 的前缀。

另一方面，假设 Req1 在视图 v1 中使用序列号 i 完成，Req2 在视图 v2 中使用序列号 j 完成。不失一般性，设 v1 < v2。如果 Req1 在客户端接收到 3f + 1 条匹配的 ORDER-REQ 消息时完成，那么在 VIEW-CHANGE 消息中，每个非故障副本都必须包含相应的 ORDER-REQ 消息，这确保了视图 v2 的主副本了解 Req1 的序列号 i 和历史哈希 hi。因此，视图 v2 中的主副本不能为 Req2 分配相同的序列号，且 hi 必须是 hj 的前缀。如果 Req1 在客户端接收到 2f + 1 条匹配的 LOCAL-COMMIT 消息时完成，那么至少 f + 1 个非故障副本必须在 VIEW-CHANGE 消息中包含 i 的相应提交证书，且其中至少一个必须包含在视图 v2 的主副本接收到的 2f + 1 条 VIEW-CHANGE 消息集合中。该非故障副本将确保历史信息从视图 v1 正确传递到视图 v2。

### 定理 7.5 活性属性。如果非故障客户端发出请求，则该请求最终将完成。

*证明：* 我们分两步证明此属性。首先，我们证明如果非故障客户端发出请求且主副本非故障，则请求将完成。其次，我们证明如果请求未完成，则将发生视图更改。

如果客户端和主副本都非故障，则一致性协议保证所有非故障副本都将接受相同的 ORDER-REQ 消息，执行请求，并向客户端发送匹配的 SPEC-RESPONSE。由于至少有 2f + 1 个非故障副本，客户端在最坏情况下能够接收到至少 2f + 1 条匹配的 SPEC-RESPONSE 消息，随后接收到 2f + 1 条匹配的 LOCAL-COMMIT 消息，或在最好情况下接收到 3f + 1 条匹配的 SPEC-RESPONSE 消息。在这两种情况下，请求都将在客户端完成。

如果请求在客户端未完成，则客户端必须已接收到 3f + 1 条匹配的 SPEC-RESPONSE 消息，且未接收到 2f + 1 条匹配的 LOCAL-COMMIT 消息。可能存在两种场景：

- 1. 客户端未接收到冲突的 SPEC-RESPONSE 和 LOCAL-COMMIT 消息（如果有的话），且接收到的 SPEC-RESPONSE 消息数量少于 3f + 1，LOCAL-COMMIT 消息数量少于 2f + 1。在这种情况下，客户端将请求重新发送到所有副本（可能重复多次，直到请求完成）。这将确保所有非故障副本接收到该请求。如果主副本拒绝向所有或某些非故障副本发送 ORDER-REQ 消息，这些副本将怀疑主副本。由于我们假设客户端接收到的 LOCAL-COMMIT 消息少于 2f + 1 条，至少 f + 1 个非故障副本将怀疑主副本，这将导致视图更改。

- 2. 客户端接收到冲突的 SPEC-RESPONSE 或 LOCAL-COMMIT 消息，在这种情况下，客户端将向所有副本多播 POM 消息。这将导致视图更改。

## 参考文献

- 1. A. Avizienis 和 L. Chen. 关于执行期间软件容错 n 版本编程的实现。在 IEEE 国际计算机软件与应用会议论文集中，第 149–155 页，1977。

- 2. E. D. Berger 和 B. G. Zorn. Diehard：面向不安全语言的概率内存安全。在 *ACM 编程语言设计与实现会议论文集* 中，第 158–168 页，2006。

- 3. S. Bhatkar, D. C. DuVarney 和 R. Sekar. 地址混淆：应对广泛内存错误漏洞利用的高效方法。在 *第 12 届 USENIX 安全研讨会论文集（第 12 卷）* 中，SSYM'03，第 8–8 页，加利福尼亚州伯克利，美国，2003。USENIX 协会。

- 4. M. Castro 和 B. Liskov. 无需公钥密码学的经过身份验证的拜占庭容错。技术报告 技术备忘录 MIT/LCS/TM-589，MIT 计算机科学实验室，1999。

- 5. M. Castro 和 B. Liskov. 实用拜占庭容错。在 *第三届操作系统设计与实现研讨会论文集* 中，OSDI '99，第 173–186 页，加利福尼亚州伯克利，美国，1999。USENIX 协会。

- 6. M. Castro 和 B. Liskov. 实用拜占庭容错与主动恢复。*ACM 计算机系统事务*，20(4):398–461，2002。

- 7. M. Castro, R. Rodrigues 和 B. Liskov. Base：使用抽象来提高容错性。*ACM 计算机系统事务*，21(3):236–269，2003。

- 8. H. Chai, H. Zhang, W. Zhao, P. M. Melliar-Smith 和 L. E. Moser. 面向 Web 服务业务活动的可信协调。*IEEE 服务计算事务*，6(2):276–288，2013。

- 9. H. Chai 和 W. Zhao. 拜占庭容错计算的交互模式。在 T.-h. Kim, S. Mohammed, C. Ramos, J. Abawajy, B.-H. Kang 和 D. Slezak 编辑，*Web、人机交互、信号与图像处理以及模式识别的计算机应用* 中，*计算机与信息科学通信* 第 342 卷，第 180–188 页。Springer Berlin Heidelberg，2012。

- 10. B.-G. Chun, P. Maniatis 和 S. Shenker. 单机拜占庭容错的多样化复制。在 *USENIX 2008 年度技术会议论文集* 中，ATC'08，第 287–292 页，加利福尼亚州伯克利，美国，2008。USENIX 协会。

- 11. F. Cohen. 通过程序演进进行操作系统保护。*计算机与安全*，12(6):565–584，1993 年 10 月。

- 12. B. Cox, D. Evans, A. Filipi, J. Rowanhill, W. Hu, J. Davidson, J. Knight, A. Nguyen-Tuong 和 J. Hiser. N-变体系统：一种面向多样性安全的无密钥框架。在 *第 15 届 USENIX 安全研讨会* 中，第 105–120 页，2006。

- 13. T. Distler 和 R. Kapitza. 通过按需副本一致性提高拜占庭容错系统的性能。在 *第六届 Eurosys 会议论文集* 中，2011。

- 14. H. Erven, H. Hicker, C. Huemer 和 M. Zapletal. Web 服务-业务活动-发起器 (WS-BA-I) 协议：Web 服务-业务活动规范的扩展。在 *IEEE 国际 Web 服务会议论文集* 中，第 216–224 页，2007。

- 15. M. Feingold 和 R. Jeyaraman. Web 服务协调，版本 1.1，OASIS 标准，2007 年 7 月。

- 16. S. Forrest, A. Somayaji 和 D. Ackley. 构建多样化计算机系统。在第六届操作系统热点研讨会论文集中，第 67–72 页，马萨诸塞州科德角，1997。

- 17. M. Franz. 理解并应对软件开发中的内部威胁。在国际 MCETECH 电子技术会议论文集中，第 81–90 页，2008 年 1 月。

- 18. T. Freund 和 M. Little. Web 服务业务活动版本 1.1，OASIS 标准。http://docs.oasis-open.org/ws-tx/wstx-wsba-1.1-spec-os/wstx-wsba-1.1-spec-os.html，2007 年 4 月。

- 19. Z. M. Kedem, K. V. Palem, M. O. Rabin 和 A. Raghunathan. 通过随机化实现弹性并行计算的高效程序转换。在第 24 届年度 ACM 计算理论研讨会论文集中，第 306–317 页，维多利亚，不列颠哥伦比亚省，加拿大，1992。

- 20. R. Kotla, L. Alvisi, M. Dahlin, A. Clement 和 E. Wong. Zyzzyva：投机式拜占庭容错。在第 21 届 ACM 操作系统原理研讨会论文集中，2007。

- 21. R. Kotla 和 M. Dahlin. 高吞吐量拜占庭容错。在国际可靠系统与网络会议论文集中，2004。

- 22. L. Lamport. 快速 Paxos。分布式计算，19(2):79–193，2006。

- 23. L. Lamport. 简要公告：无主拜占庭 Paxos。在第 25 届国际分布式计算会议论文集中，DISC'11，第 141–142 页，柏林，海德堡，2011。Springer-Verlag。

- 24. L. Lamport. 通过细化将拜占庭容错引入 Paxos。在第 25 届国际分布式计算会议论文集中，DISC'11，第 211–224 页，柏林，海德堡，2011。Springer-Verlag。

- 25. L. Lamport 和 P. M. Melliar-Smith. 拜占庭时钟同步。在第三届年度 ACM 分布式计算原理研讨会论文集中，PODC '84，第 68–74 页，纽约，纽约州，美国，1984。ACM。

- 26. L. Lamport, R. Shostak 和 M. Pease. 拜占庭将军问题。ACM 编程语言与系统事务，4:382–401，1982。

- 27. M. Little 和 A. Wilkinson. Web 服务原子事务版本 1.1，OASIS 标准。http://docs.oasis-open.org/ws-tx/wstx-wsat-1.1-spec-os/wstx-wsat-1.1-spec-os.html，2007 年 4 月。

- 28. J. Martin 和 L. Alvisi. 快速拜占庭共识。IEEE 可靠与安全计算事务，3(3):202–215，2006。

- 29. C. Pu, A. Black, C. Cowan 和 J. Walpole. 一种用于提高操作系统多样性的专业化工具包。在 ICMAS 基于免疫的系统研讨会论文集中，日本奈良，1996。

- 30. B. Vandiver, H. Balakrishnan, B. Liskov 和 S. Madden. 使用提交屏障调度在数据库系统中容忍拜占庭故障。在

