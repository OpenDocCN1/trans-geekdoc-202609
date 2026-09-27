
# 2021 IEEE 第37届国际数据工程研讨会 (ICDEW) (希腊恰尼亚 2021.4.19-2021.4.22)

**Panagiotis Drakakratos, Erodotos Demetriou, Stavroulla Koumou, Andreas Konstantidis, Demetrios Zeinalpour-Yazti**

塞浦路斯大学计算机科学系，1678, 10356 Cyprus
弗雷里克大学计算机科学系，10356 Cyprus
{drak001,edemet0,skoum001,akstant,deemetni}@cs.uc.ac.cy

**摘要**—物联网（IoT）将传感器设备引入了不断增长的智能环境。物联网场景的一个关键需求是需要一种允许所有人进行协作、透明、准确运行且具有性能保证的数据库。社区已经提出了许多数据库来应对这些挑战。在文中，我们提出了 `Triebee`，这是一种新型区块链数据库系统，它利用机器学习将数据转换为原始块，随后在区块链中存储和检索。它并不存储所有数据，这从根本上源是因为昂贵的验证成本。我们阐述了所设计的架构，该架构在其共识协议中采用了新技术，即联邦学习证明（Proof-of-Federated-Learning, `PoFL`）的概念。

**索引术语**—物联网，联邦学习。

目标是允许用户在协作数据库上执行更新和查询，同时保持系统的一致性和透明性。然而，被恶意攻击者破坏在本质上是常见的。为了让所有参与者之间能够信任协作，需要一种创新的共享数据库设计。社区提出了区块链数据库来缓解这些挑战。然而，现有的区块链架构在吞吐量和延迟方面的性能面临瓶颈，这导致执行以顺序方式进行。后者与并发结合，没有留下空间给

# I. 引言

物联网（IoT）指的是大量连接到互联网的设备，我们能够通过其他协议对它们进行观察、听取、思考、执行和相互通信 [1–14]。物联网设备主要通过 `ipv4` 协议（`5G`, `WiFi 6`）连接到云端和边缘应用程序，并提供低延迟和安全性。在人类健康和福祉方面，预计物联网到 2020 年将使设备数量增加到惊人的 400 亿，是 2015 年的两倍以上。这将为多个场所之间的物联网创造出巨大的机遇，例如协作机器学习 [6]、机器学习 [7]、认知机器人和现实技术 [9]。

物联网场景中的一个关键组件是需要利用共享数据库，允许所有参与者以更丰富的功能进行协作。共享数据库可以桥接物联网应用产生的数据 [10] 与这些数据实时处理速率之间的实际鸿沟。

提供一个每秒可以处理数十亿交易的数据库是关键的，而目前由于昂贵的验证成本这是瓶颈的原因。

在本文，我们提出了 `Triebee`（灵感来自希腊语“三”），这是一种用于 Web 3.0 的数据库，一个许可级数据库系统，它在原始块中执行机器学习，随后从区块链中存储和检索。我们将存储共享数据库的部分和使用数据库进行其操作的部分（例如向区块链账本发送查询和更新请求）分离开来。我们期望区块链在去中心化的区块链网络中同步。客户端仅使用区块头，而不是存储整个区块链的全节点。

为了实现这一目的，关键在于找到一种能够实现以下点的健壮设计：i) 在 `ii` 执行学习算法；ii) 在去中心化环境中运行；以及 iii) 缓解与数据隐私的问题。我们的主要目标是实现以下方面：

- **不可变性**：我们需要确保任何提交到区块链的数据都是不可变的，不会被任何恶意攻击者更改；
- **透明性**：我们强制共享数据库严格遵守提交的交易。数据库操作（例如插入、删除、更新）对节点是透明的，用户可以在任何时候获取提交到区块链的所有历史数据；
- **正确性**：当客户端从服务器节点接收结果时，以最小的计算需求且不产生过度的能量消耗执行所有操作；
- **性能**：我们的系统必须支持广泛的查询和索引。因此，我们应该允许 `Triabase` 实现更好的性能并提高网络的整体吞吐量，以最小化导致延迟的非必要开销；
- **隐私性**：联邦学习算法要求客户端提供训练模型，这包括高风险的数据泄露风险，这是 `Triabase` 必须考虑的因素。

# II. 背景与相关工作

区块链架构主要用于在不可变的区块链上保留记录，其中节点对不可信方的状态达成共识。这构成了区块链平台，可以被看作是一个分布式（事务日志）或数据库系统。区块由大多数验证者使用能够容忍拜占庭故障的共识协议达成共识。众知的平台包括 [12]、`Hyperledger` [13]、`Monad` [14]。这种架构不需要中心化的服务器和任意权威。

[112] 的作者引入了一个名为 `Caper` 的系统，这是一种基于无环图的许可区块链架构，并通过三种共识协议来支持内部和外部应用开发者。[115] 引入了一个新框架 `Cail`，它能够由用户存储和检索数据并验证查询以确保安全。

为了增强 `Triabase` 的安全性和隐私，我们提出联邦学习 [11] 作为分布式学习的新型明智选择。来自传统人工智能的联邦学习在服务器端训练联邦学习模型，将完整数据保留在用户端，从而减轻安全和隐私风险。

为了提高我们方法的有效性，我们提出了使用 `hyperledger fabric` 对我们的架构进行增强实现，这使我们能够衡量负载和搜索查询期间实现的不同部分的延迟和吞吐量。我们的主要结果是鼓舞的，表明我们的架构可以平衡延迟与联邦学习训练模型效率之间的权衡。

人工智能与区块链技术的集成解决各种资源优化问题具有巨大前景。此外，[17] 中提出的方法的通过开发使用 `DRL` 的缓存机制来实现安全的共享。[17] 介绍了区块链如何可能提高物联网效率，以及区块链如何克服易受威胁的安全挑战。

我们展望论文的主要贡献是：

- 我们引入了 `Triabase`，一种通过联邦学习方法增强的区块链数据库，它包含了区块链节点的性质和行为以确保用户的安全数据隐私；
- 我们提出了一种新的协作共识，命名为联邦学习证明（`PoFL`），在分布式多个处共享参数以减少数据泄露风险并保护联邦节点不被篡改；
- 我们还通过集成开源平台实现了建议，以提供一个更真实的场景。

本文其余部分的结构如下：第二节介绍相关工作。第三节介绍了所提出的架构。第四节讨论了所提系统的当前局限性和未来工作。

# III. TRIBASE 架构

在本节中，我们从底层向上介绍了 `Triabase` 架构。

## A. 区块链层

比特币协议使用 `PoW`（工作量证明）共识机制验证区块链中的交易。然而，`PoW` 是一种高成本算法，会导致过度的能量消耗。因此，`Triabase` 架构需要一种低成本的共识机制来提供同样如此。在本文中，我们提出了联邦学习证明（`PoFL`），它在安全级别方面带来了新的技术优势。

`Triage` 区块链维护着一个许可区块链，其中联邦学习的本地模型存储在分布式账本中。因此，我们定义了两类记录：训练模型记录和 `IoT` 数据集。我们仅将块中包含每代聚合模型的第一条记录视为一个联邦学习轮次。我们通过共享模型块 $k-1$ 及其现有的本地模型来生成下一轮的模型。

该过程始于使用用户侧的数据训练本地模型。然后，在各轮次之间进行通信，以广播模型并将其存储为分布式账本。来自上一轮的区块链节点（根据区块链差异）负责 2 步共识，并构建包含所有尚未处理交易的区块。

此外，获胜者负责聚合用户模型并生成共享模型。共享模型将作为第一笔交易添加到下一轮的区块中，以便在下一轮中进行访问。我们的 `PoFL` 共识机制确保了区块链过程中的参与者将获得训练奖励。用户根据其在训练中的表现获得奖励，即联邦训练是否收敛更快且达到了更高的精度。考虑到区块链差异，该轮的获胜节点是实现更高精度的节点。此外，训练轮将根据用户的贡献对用户进行调整。

尽管如此，我们通过确保每个用户遵循简单调用“和平者”（`peacemaker`）的层次结构来保护我们使用的协议。`peacemaker` 实体负责确保联邦学习所遵循协议的正确性。例如，拒绝配合协议的用户将无法获得报酬。试图作弊并验证整个过程正确性的用户将受到 `peacemaker` 实体的惩罚。`peacemaker` 将获得调整后的模型作为其在协议过程中努力的奖励。

性能提升。该组件的灵感来源于我们早期的 `Sprite` [22] 以及关于 `datapunction` 的工作。

联邦学习过程旨在通过聚合所有客户端的本地模型来训练全局模型，从而允许客户端维护自己的数据。我们遵循了 [23] 中的加权平均法，在固定的 $N$ 个客户端中，每个客户端持有 $n_i$ 个数据点，并使用固定的学习率 $\eta$ 在当前模型 $w_t$ 上计算聚合数据：$g_t(w_t) = \sum_{i=1}^{N} \frac{n_i}{n} F_i(w_t)$，其中 $F_i$ 是本地数据上的预测。每个客户端随后更新其本地模型为 $w_{t+1} = w_t - \eta \nabla g(w_t)$。

`Triage` 的主要目标是不允许从设备中提取本地数据以保护其不受任何实体侵害，并在服务器更新全局模型时通过加密隐私推理保护本地数据。此外，我们的研究目标是为用户提供安全保障，并确保本地模型免受可能损害性能的攻击。

## B. 存储层

该层负责以离线或在线模式在 `Triage` 区块链中存储传入的数据，并为各种来源提供访问方法。此外，传入的数据会被联邦学习节点聚合并用于恢复信息，从而实现故障恢复、提高可用性并提升性能。

## C. Triage/索引层

该层的主要目的是通过高效的算法和最小的开销，最小化需要存储空间的响应时间。我们使用压缩技术来获得更高的压缩率。此外，我们将在 `Triage` 架构中使用特定类型的查询来优化响应时间。我们通过 `Triage` 标准查询指定了查询类型，其中包括仅查询下一个数据集、针对谓词范围的范围查询，以及帮助查询跟踪任何时期提交交易所引起更改的增量查询。

索引是提高查询性能的一项任务。在 `Triage` 架构中，我们使用机器学习模型根据其时间和空间特征对查询进行分类。因为不同的模型在不同时间和不同地理位置的数据上可能表现更好。为了优化查询性能，我们使用了无约束 `B+` 树索引。当添加新块时，树索引会根据新模型进行更新。这种时间索引可以根据我们的需求分为多个级别。底层（叶节点）持有存储在整个区块链中的特定模型的指针。使用这种数据结构，我们不需要扫描数据库来查找特定模型，而是通过索引导航到特定区块，从而逐渐复杂度提高到对数时间。

# IV. 局限性与未来工作

在 `IoT` 环境中，谨慎处理隐私至关重要。数据泄露高度敏感，因为很容易从跟踪器中提取用户活动。为了解决这些问题，我们正在研究实现强隐私的技术和算法。例如，利用 `zk-Snarks` [24] 来保护我们基础设施的隐私。未来，我们可能会使用布隆过滤器 [25]，它提供了一种高效的方法来描述搜索模式，而无需为实体指定和泄露信息。此外，一个关键挑战是实现合理的扩展性以提高 `Triage` 的性能。为了保护网络中交易的数据完整性，我们将使用哈希树（也称为梅克尔树），它可以构建结构并高效地验证交易。此外，我们可能仅使用基础哈希来构建从根到特定交易的梅克尔路径。将进行彻底的分析和实证证据来验证我们方法的性能。

## REFERENCES

- [2] A. A. Fine, M. Guardi, M. Mohammani, M. Alahmadi, and M. Ayash, "IoT: A survey on emerging technologies, protocols, and applications." IEEE Access, 2015.
- [3] L. Lin, J. Lin, and S. Zhao, "The internet of things: A survey." Future Surveys, vol. 17, no. 2, pp. 243–259, 2017.
- [4] L. Azor, A. Iera, "The internet of things: A survey." IEEE Access, vol. 3, pp. 1943–1956, 2015.
- [5] J. Gutierrez, "Internet connected devices to address the problem of." Mobile, pp. 28–39, 2016.
- [6] W. Du and M. Attallah, "Privacy-preserving data aggregation in IoT." In 2001 IEEE Conference on Security and Networks, pp. 277–282. doi: 10.1109/ICSN.2001.9630.
- [7] D. Butler and M. Jarsky, "Information Filters: The Privacy of Users in the Age of Machine Learning." Machine Learning on Publications, pp. 99–114, 2008.
- [8] A. Atallah, M. Byanka, L. Li, and M. Fine, "Collaborative filtering." Proceedings of 2004 ACM Support for Cooperative Computing, pp. 103–114. doi: 10.1145/102901.102952.
- [9] J. Li, X. Lu, and Q. Zhao, "Localization for augmented reality." International Journal of Electronics, vol. 13, no. 6, pp. 727–741, 2020.
- [10] S. Chen, H. Du, B. Liu, and H. Wang, "A Vision of IoT: Challenges and Future Directions." Internet of Things Journal, vol. 1, no. 4, pp. 349–359, 2014.
- [11] V. Sharma, S. Kumar, and A. S. Talwalkar, "Multi-Task Learning." Advances in Information Processing Systems, 2007.
- [12] M. Jain, D. Agrawal, and E. E. Abadi, "CAPER: a permissioned blockchain," of VLDB, vol. 12, no. 11, pp. 1389–1398, 2019. [Online]. https://doi.org/10.14775/334263.334275
- [13] E. Androlaki, A. Garner, V. Bortnuk, C. Caschin, K. Christidis, E. Deneyeur, F. Gellman, Y. Manevich, S. Muralidiah, C. Berry, B. Ngayan, M. Seth, A. Mathopoulos, M. Williams, W. H. Cococo, "A distributed ledger framework," IEEE Conference: Association for Machine Computing, Apr. 2018.
- [14] J. Wang and H. Wang, "Monascade: Scale Blockchain with Ethereum Enhancements." IEEE Access, 2019, pp. 55–68.
- [15] C. Zheng, Zhang, and J. Xu, "Enabling Verifiable Range Queries over Blockchains." Proceedings of the Management Conference Association for Machine Computing, 2019, pp. 141–158. [Online]. https://doi.org/10.1145/3339933.3340098
- [16] Y. Chen, J. Chen, C. He, and Y. Zhang, "Blockchain and its integration with IoT." IEEE Access, vol. 7, pp. 172930–172940, 2019. [Online]. https://www.ieee.org/article/10.1109/ACCESS.2019.2925205
- [17] A. Zheng, J. Bray, N. Gaskin, and S. King, "Scaling Blockchain for Cryptocurrencies," in Proceedings of the International Conference on Computer Science, 2017, pp. 51–68. [Online]. https://doi.org/10.1145/3134677.3134771
- [18] E. J. K. Nagle, S. Kelly, G. L. Lasker, K. Kohli, M. J., and F. Beard, "Blockchain-Based Distributed Robustness," in Proceedings of the 30th Annual Conference on Security and Privacy (SP), May 2017, pp. 347–356. [Online]. https://doi.org/10.1109/SP.2017.3
- [19] T. Li, P. Li, Z. Wu, X. Lu, R. Liu, B. C. Qi, and K.-L. Tan, "BLOCKCHAINER: A Framework for Blockchain Analysis in IoT." Proceedings of the Management Conference Association for Machine Computing, 2017, pp. 105–118. [Online]. https://doi.org/10.1145/3134693.3134516



- [20] B. McElman, E. Doe, D. Ramirez, S. Hancock, and A. B. Yoon, "Federated Learning of Decentralized Data," in *Artificial Intelligence and Statistics*, 2017, pp. 1273–1282. [Online]. https://arxiv.org/abs/1606.00511 [cs.LG], Aug. 2018.

- [21] M. Pretk, "How and grow zk-SNARKs," arXiv:1906.07221 [cs.CR], Jul 2019. [Online]. https://arxiv.org/abs/1906.07221

- [22] B. Groth and M. Mitzenmacher, "Networks of Blockchain for IoT." *Internet Networks*, vol. 14, no. 4, pp. 485–500, 2014. [Online]. https://doi.org/10.1480/14682751.1029096
