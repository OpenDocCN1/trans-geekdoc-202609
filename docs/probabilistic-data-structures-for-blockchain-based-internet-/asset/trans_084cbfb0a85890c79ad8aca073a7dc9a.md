

Authors of `[[110](#bib.xhtml#ch00-bib-110)]` suggested to blockchain as a solution for resolving security issues existing among UAV and MEC server. This is the first attempt when outdoor health monitoring system is proposed using blockchain. Here, health information that is collected from via UAV from users and stored on MEC server is protected with blockchain based architecture. To validate users, authors have used `BF` and health data is only stored in blockchain if blockchain validators them. Every user first registers on the network and for that user first generate a public and private key pair by using `ECC`. Next, user requests MEC server for registration. The health data collected from wearable devices and this data is transferred to MEC server via UAV. Before sending health care data, user encrypt this data using public key of UAV. Next, after decrypting health data UAV users using `BF`. Finally after successful validation, MEC encrypts health data and forwards to nearest MEC server. However before forwarding data, UAV validates identity of user with `BF`. Hence, using a `BF` in this case reduces data transmission. MEC server decrypts this data and checks this data for finding abnormalities. In case of any issue it is reported to the hospital. To validate the results parameters, i.e., processing time of MEC server, UAV validation time, UAV energy consumption, transmission of data for MEC server are used. It has been proved in experiments expected size of transmission data increases at much lower rate with `BF` over non-`BF`. With increase in number of users, data increases exponentially for non-`BF`.

### [14.2.11 基于区块链和 BF 的 5G 及其以后 MEC 的多域协作](#contents.xhtml#rsec14_2_11)

IoT 和 5G 系统的快速增长加速了万物互联的概念 `[[145](#bib.xhtml#ch00-bib-145)]`、`[[55](#bib.xhtml#ch00-bib-55)]`。显然，设备数量的增加导致数据量大幅增长。然而，这种高速的数据增长对 5G 系统和云计算模型的计算能力构成了挑战 `[[58](#bib.xhtml#ch00-bib-58)]`。为了解决这个问题，设计了异构 MEC 系统 `[[132](#bib.xhtml#ch00-bib-132)]`、`[[220](#bib.xhtml#ch00-bib-220)]`。异构 MEC 被设计为一个分布式计算平台，集成了一个以上的 MEC 服务器、云服务器以及计算存储，在数据源附近提供智能边缘服务。由于这些系统具有短传输链路，边缘计算能快速响应服务请求。然而，为了实现异构 MEC 系统，多个 MEC 服务器需要整合其资源以完成大规模计算任务。不幸的是，这种多服务器协作涉及信任和安全问题，因为这些服务器属于不同的域，并由不同的组织管理。MEC 服务器通过由 `SDN` 控制器启用的跨域路由与其他 MEC 服务器联系。然而，为了确保多个服务器之间的跨域路由，`SDN` 控制器需要其他域的拓扑信息。值得注意的是，不同域的这些信息应相互保密，这种隐私泄露可能会损害 MEC 系统。

`[[218](#bib.xhtml#ch00-bib-218)]` 的作者使用区块链解决了隐私泄露问题。在这里，区块链实现了 MEC 服务器之间的可信数据共享，以实现多域 MEC 网络的可信协作。此外，该系统采用容纳性 `BF` 作为载体，帮助多域协作路由共识，而无需泄露拓扑隐私。

首先，跨域 MEC 请求通过域 1 到达控制器 A。根据此请求，控制器 A 计算域 1 的域内路径，并选择权重总和最小的最优路径。同时，新请求也发送到拥有域 1 虚拟拓扑的后续域控制器。此外，控制器 A 构建包含控制器路由结果的 `BF`。在这里，`BF` 维护分布式账本和高效路由机制。具体来说，`BF` 也被用作路由验证的载体。[表 14.2](#18chap_14.xhtml#tab14_2) 和 [14.3](#18chap_14.xhtml#tab14_3) 表示上述讨论方案的表格比较。

![TABLE 14.2 Comparison between different schemes integrating blockchain with BF.](images/tab14_2.jpg)

**TABLE 14.2**  

Comparison between different schemes integrating blockchain with BF.

![TABLE 14.3 Comparison between different schemes integrating blockchain with BF.](images/tab14_3.jpg)

**TABLE 14.3**  

Comparison between different schemes integrating blockchain with BF.

## [14.3 区块链与 QF 的集成](#contents.xhtml#rsec14_3)

`QF` 与 `BF` 起到相同的作用。但是，如果数据无法装入主内存，`BF` 就会失效。文献中不支持任何集成 `QF` 和区块链的工作。尽管如此，上述使用 `BF` 的工作可以用 `QF` 替代，特别是当过滤器大小太大而无法装入主内存时。

## [14.4 区块链与跳表的集成](#contents.xhtml#rsec14_4)

区块链值得一提的用例之一是用于公证文件，例如学术学位。区块链的防篡改和透明特性使得区块链上的文件更难以伪造和修改。然而，作为一个有前景的应用，公证用例存在一些局限性。其中一个挑战是验证文件在区块链上的存在，即使该文件相对于某个参考点非常旧。可能会出现用户未更新其区块链的情况，此时验证者在区块链上的参考点可能在时间上落后于待查询的区块。值得注意的是，对于低功耗设备来说，这个问题会变得更加严重。

解决这个问题的一个方案是使用 `SPV` 客户端，如前几章所讨论。此外，`SPV` 引入了安全弱点；如果 `SPV` 客户端从单个全节点获取交易，则可能容易受到单点故障的影响。此外，`SPV` 和全客户端容易受到隔离攻击（例如，来自公共区块链且工作量非常小的分叉）以及基于路由的劫持攻击 `[[37](#bib.xhtml#ch00-bib-37)]`。另外，如果 `SPV` 客户端连接到多个全节点，可能会导致带宽和功耗的消耗增加。因此，它不适合大量轻客户端。重要的是，`SPV` 客户端必须保持在线，以检查交易是否已提交到区块链。事实上，对于任何验证者进行验证，设备需要通过良好的互联网连接保持在线。在没有良好网络连接的情况下验证交易要么是不可能的，要么是不安全的。

解决这个问题的另一个方案是使用集体签名（`CoSi`）`[[183](#bib.xhtml#ch00-bib-183)]`，这是 ByzCoin 提供的一种高效数字签名技术。ByzCoin 从过去几天或几周内最近成功的工作量证明矿工中构建一个共识组。为了安全地提交交易，这个共识组运行 `PBFT` 算法。然而，而不是使用全对全通信，`CoSi` 在每个阶段都被使用，`CoSi` 生成一个单一的、高效可验证的紧凑集体签名，该签名经过加密签名，揭示共识组的一部分已经验证。要检查交易上的 `CoSi`，验证者应在交易提交时知道共识组中矿工的公钥。显然，这个共识组会不断变化。为了解决这个问题，当共识组发生变化时，之前共识组中的一些节点共同形成并签署一个前向链接，包含两个重要信息。`CoSi` 协议的架构在 [Fig. 14.3](#18chap_14.xhtml#fig14_3) 中表示。

![FIGURE 14.3. CoSi protocol architecture \[121\].](images/fig14_3.jpg)

**FIGURE 14.3.**

