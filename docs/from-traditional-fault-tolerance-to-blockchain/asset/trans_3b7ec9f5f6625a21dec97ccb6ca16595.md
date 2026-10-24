

### 4.4.1.1 CA 系统

CA 系统牺牲分区容忍性以换取一致性和可用性。这意味着网络分区故障被排除在系统设计所使用的故障模型之外。这类系统只能在网络分区故障很少发生的环境中使用，例如局域网或数据中心。旨在实现悲观复制的系统通常是 CA 系统。

### 4.4.1.2 CP 系统

基于我们之前的论点，我们无法构建一个在容忍所有形式网络分区故障的同时确保强一致性的系统，因为根据网络分区的定义，必然存在一些副本无法访问其他副本。然而，在以下条件下，CP 系统是可能的：

- 一致性通过基于法定人数的算法实现。也就是说，只要大多数副本彼此一致，系统就被视为一致。
- 网络分区故障导致的分区包含系统中大多数副本。

在这样的 CP 系统中，位于大多数分区中的副本将照常运行（即，仿佛没有网络分区故障），而位于少数分区（或分区）中的副本将停止运行，从而失去可用性属性。许多容错的组通信系统 [3, 20] 是 CP 系统。

### 4.4.1.3 PA 系统

许多新的云计算系统 [1, 23]，以及采用乐观复制的系统 [25]，都是为确保 PA 而设计的。如我们在 4.3 节中讨论的，一致性的丢失只是暂时的——当网络分区合并且系统处于静止状态时，副本状态最终会收敛。

### 4.4.2 启用分区容忍性的影响

对于 PA 系统，它应努力检测并协调任何不一致，因为用户确实期望最终一致性，即使他们能容忍在网络分区期间出现暂时的不一致状态。在没有网络分区的情况下，系统将表现为 CA 系统。当副本意识到与另一个节点通信有困难时，它将进入分区模式，如图 4.18 所示。在分区模式期间，副本会用一致性换取更好的可用性。然而，当分区合并时，副本将协调其不一致，类似于我们在 4.3 节中在乐观复制的上下文中描述的冲突协调。冲突协调的知名方法包括：

![](img/7320b1480d74f1d65f74659cab456782_172_0.png)

图 4.18 分区模式和分区恢复。

- 补偿事务/操作。在某些系统中，例如事务处理系统，可以通过应用用户定义的补偿操作 [10] 来撤销操作的影响。因此，在分区恢复期间，操作可以按需重新排序。

- 操作转换。对于协作编辑系统，操作转换通常用于协调对共享文档的冲突编辑 [28]。给定在站点 i 上应用的两个冲突操作 Oi 和在站点 j 上应用的 Oj。Oi 转换为 O'i，Oj 转换为 O'j，使得在初始状态相同的情况下，在站点 i 上先应用 Oi 再应用 O'j 的最终状态，与在站点 j 上先应用 Oj 再应用 O'i 的最终状态相同。

- 交换复制数据类型（CRDTs）。这种方法最初作为协作编辑的替代方案开发 [22]，最近已扩展到潜在的许多其他应用程序 [27]。通过使用 CRDTs 表示状态，对状态的所有操作现在都是交换的。因此，并发操作不再相互冲突。副本可以立即应用本地提交的操作，并异步地将更新传播到其他副本。副本在接收到由另一个副本发送的远程更新时，也会确定性地对其进行排序，*不需要*任何副本间通信。

对这些方法的详细讨论超出了本书的范围。

为了总结本节，考虑到副本检测网络分区故障的唯一方式是通过超时，并且用户必须等待有限的时间才能看到其请求得到服务，系统设计中真正重要的是以下两个参数：

- 端到端延迟。该参数定义了系统根据业务要求可以容忍的端到端延迟。

- 分区超时值。该参数定义了系统设计者选择的超时值，副本可以使用该值进入分区模式。通常，分区超时值显著高于端到端延迟。

对于部署在广域网上的系统，如果两个远程副本之间的往返延迟接近分区超时值，那么系统大部分时间将运行在分区模式下，因此系统基本上将作为 PA 系统运行。否则，系统将作为 CA 系统运行，直到发生网络分区故障。根据这种解释，PACELC 模型似乎不是必要的（因为模型中 A 和 C 之间的差异未定义）。

## 参考文献

- 1. D. Abadi. 现代分布式数据库系统设计中的一致性权衡：CAP 只是故事的一部分. IEEE Computer, 45(2):37–42, 2012.
- 2. P. A. Bernstein, V. Hadzilacos, and N. Goodman. 数据库系统中的并发控制与恢复. Addison-Wesley Longman Publishing Co., Inc., Boston, MA, USA, 1987.
- 3. K. Birman. 虚拟同步复制模型的历史. In B. Charron-Bost, F. Pedone, and A. Schiper, editors, Replication, pages 91–120. Springer-Verlag, Berlin, Heidelberg, 2010.
- 4. K. A. Birman, D. A. Freedman, Q. Huang, and P. Dowell. 通过一致软状态复制克服 CAP. IEEE Computer, 45(2):50–58, 2012.
- 5. K. P. Birman. 可靠分布式系统指南 - 构建高可靠性应用程序和云托管服务. Texts in computer science. Springer, 2012.
- 6. E. A. Brewer. 迈向健壮的分布式系统（摘要）. In Proceedings of the nineteenth annual ACM symposium on Principles of distributed computing, PODC ’00, pages 7–, New York, NY, USA, 2000. ACM.
- 7. E. A. Brewer. 推动 CAP：一致性和可用性策略. IEEE Computer, 45(2):23–29, 2012.
- 8. M. Castro and B. Liskov. 实用拜占庭容错与主动恢复. ACM Transactions on Computer Systems, 20(4):398–461, 2002.
- 9. P. Felber and R. Guerraoui. 在 CORBA 中使用对象组进行编程. IEEE Concurrency, 8(1):48–58, Jan. 2000.
- 10. H. Garcia-Molina and K. Salem. Sagas. In Proceedings of the ACM SIGMOD Conference, pages 249–259, San Francisco, CA, 1987.
- 11. S. Gilbert and N. Lynch. Brewer 的猜想与一致、可用、分区容忍 Web 服务的可行性. SIGACT News, 33(2):51–59, June 2002.
- 12. S. Gilbert and N. A. Lynch. CAP 定理的视角. IEEE Computer, 45(2):30–36, 2012.
- 13. R. A. Golding and D. D. E. Long. 全球规模分布式数据库弱一致性协议中副本分歧的建模. Technical report, University of California, Santa Cruz, CA, USA, 1993.
- 14. J. Gray and A. Reuter. 事务处理：概念与技术. Morgan Kaufmann Publishers Inc., San Francisco, CA, USA, 1st edition, 1992.
- 15. R. G. Guy, J. J. Popek, T. W. Page, Jr. 乐观复制的一致性算法. In Proceedings of the First IEEE International Conference on Network Protocols, 1993.
- 16. D. S. P. Jr., G. J. Popek, G. Rudisin, A. Stoughton, B. J. Walker, E. Walton, J. M. Chow, D. A. Edwards, S. Kiser, and C. S. Kline. 分布式系统中相互不一致的检测. IEEE Trans. Software Eng., 9(3):240–247, 1983.

