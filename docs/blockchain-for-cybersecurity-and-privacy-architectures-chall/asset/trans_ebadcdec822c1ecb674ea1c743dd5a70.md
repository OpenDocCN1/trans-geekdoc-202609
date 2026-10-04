

## 基于 CCN 的物联网中基于区块链的信任与安全

## 算法 2：区块链中名称/值对注册的步骤

+ 1: 生成 $P_{iK}$ 和 $P_{jK}$
2: 哈希 $\rightarrow$ (名称, 内容, 签名信息)
3: 加密消息摘要：$Value = (Name, Content, SignInfo)$_{P_K}$
4: 将名称/值对放置在区块链上
5: 工矿验证该名称是否之前注册过。如果是，则拒绝该值对；如果不是，则可以添加。

为了与名称建立链接，每个数据包中都嵌入了数字签名。事实上，该签名是使用生产者的私钥对整个数据包（名称，内容，签名信息...）计算的，以确保该内容的溯源性。其验证确保了收到的数据未被篡改（数据完整性），并且它与兴趣包（Interest packet）中表达的名称对应，因为这与数据包中的名称相同（名称的真实性）。数据包签名验证需要生产者的公钥。为此，在为该内容生成数字签名后，将名称/值对发布在区块链上，允许申请者决定该值对是否可接受并能够验证数据包的签名。

### 7.6.1.2 验证

为了确保内容的有效性和溯源性，申请者必须验证收到的包的签名。这基于该包中包含的签名信息，以检索验证所需的公钥。
算法 3 描述了查找操作。

查找操作确保公钥与给身份对应。因此，当用户想要检查某个值对是否属于该身份时，他会遍历区块链并搜索每个交易的身份和公钥对。当 ID 不对应公钥时，向对象返回 FALSE；否则返回 TRUE。

## 算法 3：查找操作

```
Input: ID, P_K
Output: TRUE or FALSE
1: 用户执行 ID 的查找
2: 如果 P_{i*K} 对应 ID，则
3: | return TRUE
4: else
5: | return FALSE
```

## 数据交付

注册后，对象和服务即可供用户和应用程序使用。当他们想要检索内容时，他们会向下一跳发送带有其所需数据名称的请求消息（兴趣包）。由于数据可以放置在离用户更近的地方（网络缓存），响应时间可以缩短，网络流量也可以减少。此外，网络缓存允许传感器进入休眠模式，从而降低能耗。值得注意的是，生产者使用其密钥对内容签名，这些密钥必须在消费者处可用或可以从区块链检索。

在向请求者路由内容之前，网络节点会将副本存储在自己的缓存中（网络缓存），以响应后续请求。一旦消费者收到数据包，它将通过对区块链执行包含所需内容名称或内容所有者身份的查询来检查密钥状态（是否有效）。如果密钥有效，它会计算接收到的数据包的哈希并与收到的哈希进行比较。如果两个哈希匹配，则内容通过了验证。

## 实验结果与讨论

在本节中，我们评估了确保给定公钥对应给定身份的查找操作。实验在 Intel Core i5 2.2 GHz 处理器、1 TB HDD、6 GB DDR3 内存和 Microsoft Windows 10 环境下进行。

我们使用了从 https://medium.com/crypto-currently/lets-build-the-tiny-blockchain-c70965a248b 获取的用 Python 编写的区块链数据结构。

我们对其进行了一些修改，以适应我们的方法。如图 7.7 所示，查找操作所需的时间取决于区块链的大小。从链长度大于 500 个区块开始，验证时间变得更长。例如，对于长度为 950 个区块的链，查找操作耗时了约 11 秒。

区块的数量实际上没有上界；区块在链尾以平均每 10 分钟 1 个的速度持续被添加。这一过程不会停止，因为海量的连接设备需要区块来存储它们的交易。在每个区块的交易数量方面，平均值实际上接近 1500 个，区块大小为 1 MB (1024 KB)(区块链)。

然而，我们认为使用分布式哈希表（存储 (身份, 密钥) 对）可以支持查找操作。任何节点都可以高效地检索与给定身份相关的公钥，而无需遍历整个区块链。

与常见的公钥基础设施（PKIs）不同，信息的访问不是由任何中央机构读取或写入。使用区块链消除了对中心机构的依赖，并解决了单点故障问题。尽管如此，区块链的特性非常适合存储和维护公钥，并声称所有人所知的电子设备的所有权。

## 基于 CCN 的物联网中基于区块链的信任与安全

![](img/816c34830872ca25a809f80557c76d27_177_0.png)

图 7.7 查找操作。

### 7.7.1 局限性与挑战

在 CCN 中设计或适配区块链技术面临着若干障碍，某些问题源于区块链技术的本质。其他挑战在 Ghandour 等人 (2019) 中提出，例如监管问题、标准挑战以及知识缺乏。

此外，区块链规模的指数级增长将增加查找操作的时间，需要遍历整个区块链。区块（图 7.8）意味着更多的计算力来挖掘该链。例如， 2017 年 12 月的数据量超过了 38 GB（fastsync）。

## 7.8 结论与未来工作

物联网 承诺了前所未有的便利。然而，为了物联网实现其全部潜力，必须在和设备之间建立信任并保护数据。在本章中，我们引入了一种基于 CCN 和区块链的混合解决方案，以在物联网中构建信任和安全，同时考虑到物联网设备的资源限制。

尽管 CCN 方法是一个极具前景的方案，但它仍然是一个非常年轻的研究领域。许多问题仍然开放且没有明确的答案。提出一个合适的命名系统以确保大多数安全服务是一个悬而未决的问题。为此，我们需要加强 CCN 采用的安全模型，并在内容中集成加密机制。未来的未来工作可能包括其他系统，例如使用密码累加器来提供高效的支持。

## 参考文献

- Amadeo, Marica, Claudia Campolo, Antonio Ileri, 和 Antonella Molinaro. “Named data networking for IoT: An architectural perspective.” In 2014 European Conference on Networks and Communications (EuCNC), 1–5. IEEE, 2014.
- Bacci, Emmanuel, Christian Mehlis, Oliver Hahm, 和 Matthias Wählich. “Information centric networking in the IoT: Experiments with NDN and the wild.” In Proceedings of the 1st ACM Conference on Information-Centric Networking, 77–86. ACM, 2014.
- Balte, Ashwini, Ashita Kashid, 和 Balaji Patil. “Security issues in Internet of things (IoT); A survey.” International Journal of Advanced Research Computer Science and Software Engineering 5, no. 4 (2015): 1–10.
- Tutt, Talal Ashraf, Jain Philli, Lin Guan, 和 George Oikonomou. “Adaptive and context-aware service delivery for the internet of things.” In Internet of Things, Smart Places, and Next Generation Networking, Part of the Lecture Notes in Computer Science series (LNCS, no.8121), 36–47. Springer, Berlin, Germany, 2013.
- Conti, Mauro, Muhammad Hassan, 和 Chagan Lal. “Block-Auth: Blockchain-based security for the IoT.” (注：OCR 文本略有碎片，根据上下文重构)。
- (注：Average block size in MB. (Blockchain.com)
