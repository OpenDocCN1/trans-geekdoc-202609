
# 分片与区块链扩展性解决方案

分片可能是最有希望的，因为它们可以克服性能和扩展性问题。分片方案允许跨越节点组（称为分片）处理交易。结果是，分片并行运行可以在不需要显著减少通信、计算和存储开销的情况下最大化性能和吞吐量，允许工作在大系统中进行（Zamani, Movahedi, & Raykova, 2018）。当更多参与者加入网络时，可以增加吞吐量。可以形成更多委员会来并行处理交易（Wang, Shi, Nixon, & Han, 2019）。

使用不同的区块链结构（如无环图 `DAG`）是第 1 层的另一种解决方案。为了避免通过排序区块消耗基于时间的交易，像 Sompolinsky 和 Zohar (2013) 提出的区块链系统将交易组织成图拓扑结构。系统通过减少所需的通信、计算和存储开销来提高性能。然而，开源项目和解决方案的来源较少。Wang 等人 (2020) 提供了基于 `DAG` 的扩展性解决方案的最新综述。

第 2 层区块链是为了卸载第 1 层（主链）执行的工作而构建的层。第 2 层解决方案通过处理链外交易来提高扩展性，不需要对主链进行任何更改，并且通常依赖于主链的安全性。图 18.3 也显示了扩展性第 2 层解决方案。

## 支付通道与状态通道

支付通道是一种允许许多参与者进行链外交易的去中心化网络，能够以极低的成本实现即时处理。支付通道的基本思想是让双方（例如 Alice 和 Bob）在区块链上的智能合约中“锁定”一些硬币，合约中双方金额的动态变化可以在不与区块链交互的情况下发生。双方随后可以通过交换通道内每个伙伴拥有的新余额签名，在“链外”更新这些代币的分布。当双方决定关闭通道时，区块链将实现最新的签名的链外代币分布。主链的另一个用途是解决双方对通道当前链外余额的争议（Dziembowski, Eckey, Faust, Hesse & Hostáková, 2019）。支付通道的一种扩展是比特币上的闪电网络（Poon & Dryja, 2016），它允许用户通过更长的通道路径对交易进行“路由”。状态通道是另一种支持通用状态更新链外执行的扩展。

## Plasma、侧链与 Rollups

- **Plasma** 是一系列智能合约，通过根区块链协调许多区块链。Plasma 区块链是一个允许创建树形层次结构组成的子链的框架。这一成就涉及在主区块链上使用欺诈证明组合智能合约，以强制状态转换在父区块链上发生。与闪电网络一样，提现需要时间退出（Poon & Buiten, 2017）。

- **侧链** 是一个独立的区块链网络，通过双向锚定与主区块链（第 1 层）连接，该机制允许在固定汇率下进行资产的双向传输，并由一组服务器（联邦）调解，由这些服务器决定何时锁定或释放代币。侧链拥有共识协议，该协议可能与主链协议完全不同。侧链与主链隔离，不依赖于第 1 层区块链的安全性。因此，在发生攻击或存在恶意设计的侧链时，损害将完全局限于侧链（Singh et al., 2020）。

- **Rollups（汇总）** 是一个概念，它将整个交易数据留在链上，同时将交易计算移至链外以提高效率。Rollups 与 Plasma 有些关系，但它们声称是去信任的。通过仅在链上发布足够的数据，Rollups 解决了之前的第 2 层扩展解决方案所面临的数据可用性问题。交易被封装进 `Merkle` 树中以减少链上存储的数据量并增加安全性。以太坊的共识协议不验证交易，而是依赖零知识证明或欺诈证明（Schaffner, 2021）。

![图 18.3：第 1 层和第 2 层区块链的可扩展性解决方案。来源：作者。注：此图展示了两个区块链层，并概述了提高扩展性的某些通用方法。](img/5113a532010ddac03a91c547bc2ad6ff_281_0.png)

# 用于交换加密资产的技术

区块链参与者最终可能出于投资或交易目的将他们的加密资产交换为其他加密资产或法币。交换解决方案的基本属性必须确保**原子性**：要么转移约定账户中的所有资产，要么不发生任何转移。如果没有原子性，交易者可能发送了资产而没有收到任何回报。大多数商业和金融平台依赖此特性以避免需要受信任的中介机构来保证匿名性。在具有一个或多个区块链的去信任分布式环境中，需要特殊逻辑来确保交易的原子性。原子交换（`Atomic swap`）是一项协调任务，双方要么收到原始资产要么失败（Garcia-Molina, 1983）。通过实现智能合约（如自动做市协议（`AMM`）协议），在单个账本上可以轻松实现原子交换（Xu, Vavyk, Paruch, & Cousa, 2021）。传统方法使用中心化交易所（`CEX`）进行跨链资产交换，其特点是高效且快速，例如 Coinbase、币安国际、FTX 和 Kraken。然而，这种方法需要中介费用，并对交易所匹配机制的可靠性和透明度表示信任。此外，`CEX` 容易受到各种攻击，从钱包黑客攻击到分布式拒绝攻击（`DDoS`）（Moore & Christen, 2013）。`DDoS` 攻击是一种试图通过大量的互联网流量淹没目标或其周边基础设施来破坏目标服务器、服务或网络的正常流量（Cloudflare, 2022）。

为了解决 `CEX` 的问题，去中心化交易所（`DEX`）最近成为跨链资产交换的流行工具，例如 Uniswap、Sushis 和 0x。在这种点对点的环境中，传输代理直接与交易对手的潜在恶意行为进行交互。因此，此类环境下的主要挑战是实现跨账本交易的原子性。要么执行整个交易，要么在失败时什么都不发生。

可能令人惊讶的是，大多数加密资产交易发生在金融机构用于传统资产（如股票和大宗商品）的链外系统中。2021 年凸显了链上加密资产交易的可行性，从几乎为零增长到每月总量的 5% 到 10%（CMC, 2022）。

## DEX 上的链外交换

市场参与者通常使用 `DEX` 获取和交易加密资产。`CEX` 是一个金融中介，允许买卖双方在由中介构建的平台上相互匿名交易，但中介本身不是交易的中介。然而，`CEX` 使用官方身份文件来验证交易者的身份。平台控制交易者转移的加密资产或货币。因此，它是托管制的，因为中介必须批准流入和流出的转移。`CEX` 使用中心限价订单簿（`CLOB`）来连接可用的买单和卖单。交易通常是快速且廉价的，因为它们在运行高度优化匹配引擎的专用且隔离的高性能服务器上进行。因此，在 `CEX` 上交易需要对中介有相当的信任。

某些交易所近年来增加了透明度和监管合规性。这种情况也允许平台与传统金融系统连接，使用信用卡和银行转账等标准银行协议进行法币支付。因此，这些平台充当了使用货币购买加密资产的个人的入金通道（ramp）。`DEX` 使用的大多数技术并非特定的区块链，除非是转移加密资产所需的钱包组件。第二章对 `DEX` 提供了进一步讨论。

`OTC` 操作对于大型金融交易也很常见。这些交易通常涉及为大交易提供流动性的专业投资者和参与者。与 `DEX` 的重要区别是，`OTC` 交易通常是交易后结算的，这意味着货币和代币的转移发生在达成协议后的几小时甚至几天。

## 使用 DEX 进行链上交换

以太坊区块链拥有数千种代币。无需中介即可交换这些资产的协议数量不断增加。然而，由于交易量，在区块链上直接实现 `CLOB` 交易所面临挑战。每个交易每天产生数百万订单，例如 `CEX` 上的 `BTC/USDT`。因此，遵循相同的 `CLOB` 设计可能会由于耗时的挖掘过程和支付给矿工的 `Gas` 费用而变得昂贵且缓慢，并受到区块链容量的进一步限制。

由于这些原因，`DEX` 开发了嵌入智能合约的自动做市（`AMM`）算法。`AMM` 智能合约控制流动性池，这些池是由市场参与者提供的加密资产。该合约允许市场参与者交换资产并进入这些池。当使用 `AMM` 将一种代币交换另一种代币时，交易者将代币交换请求和要出售的代币发送到 `AMM` 智能合约。`AMM` 根据可用流动性池自动确定交易价格，通常使用守恒函数确定池想要交换的代币数量。如果 `AMM` 交换率在交易者请求中指定的接受范围内，`AMM` 的流动性池会接收交易者的代币。它会自动将请求的代币发送给交易者。如果交换率不可接受，`AMM` 智能合约会将交易者的代币退回交易者的钱包，且不发生交易。流动性池通过对每笔交易产生费用来获得提供流动性的补偿。Xu、Vavryk 等（2021）对去中心化交易所（`DEXs`）提供了进一步讨论。

## 基于哈希时间锁合约的跨链交换

某些协议采用了哈希时间锁合约（`HTLCs`）。这些合约由 TierNolan 在比特币论坛上首次提出（BW, 2022），旨在不通过账本之间进行直接通信的情况下，实现跨链交易的原子性。研究和改进 `HTLCs` 具有极大的意义（Kirsten & Dwaranah, 2018; Liu, 2018; Xu, Ackerer, and Dubovitskaya, 2021; Zyskind, Kisagun, and Fromknecht, 2018）。本节剩余部分将提供 `HTLCs` 的概述。

假设两个用户想要交换存储在两个不同区块链上的各自资产。每位用户分别在各自的区块链上锁定资产，并使用其中一个用户生成的秘密的哈希值。用户可以通过揭示哈希值的原像（`preimage`）来解锁资产。用户在执行合约的断开账本（`Chain_a` 和 `Chain_b`）上拥有账户（钱包）。

假设 Alice 想要将 `Chain_a` 上的资产发送给 Bob，以换取 Bob 在 `Chain_b` 上的资产。

1.  **步骤 1**：Alice 通过生成一个用于解锁资产的秘密（密钥）来启动交易。随后，她在 `Chain_a` 上部署了一个合约，锁定她的资产直到时间 `t_a`。只有当 Alice 生成的秘密被揭示并输入智能合约时，该合约才会将资产传输给 Bob。秘密的哈希值作为智能合约的一部分被提交（图 18.4，步骤 1）。该合约的一个关键特性是，在时间 `t_a` 之后如果秘密未揭示，智能合约将过期，解锁并将 Alice 的资产返回到她的钱包。

2.  **步骤 2**：Bob 可以验证 Alice 在 `Chain_a` 上部署的合约，并使用 Alice 提交的哈希值在 `Chain_b` 上部署一个类似的合约（图 18.4，步骤 2），指定他将传输给 Alice 的金额和过期时间 `t_b`。在此之前，Bob 的资产锁定在 `Chain_b` 上。

3.  **步骤 3**：Alice 可以验证 Bob 在 `Chain_b` 上部署的合约，解锁资产，并通过在 `Chain_a` 上揭示秘密来启动传输。一旦秘密在 `Chain_a` 上被揭示（在 Alice 传输完成之前），Bob 就可以利用揭示的秘密解锁 `Chain_b` 上的资产，完成跨账本交易。理想情况下，这种机制使得能够在不依赖信任方和账本间连接的情况下交换原子跨账本资产。如果 Alice 在 `t_b` 之前没有解锁 `Chain_b` 上的资产，资产将返回给 Bob。因此，她没有动力揭示（在 `t_b` 之后和 `t_a` 之前）那个允许 Bob 在 `Chain_a` 上执行智能合约并将资产传输给 Alice，同时保留其 `Chain_b` 上资产的秘密。一旦秘密揭示，Bob 的资产将传输给 Alice。他应该立即执行 `Chain_b` 上的智能合约以完成交易。否则，他将在没有收到 Alice 资产的情况下就传输了其资产。在实践中，扩展上述 `HTLC` 逻辑可以包括额外的激励机制，如资本抵押和声誉。

![图 18.4：哈希时间锁合约的步骤，显示了 Alice 在 Chain_a 上拥有的代币向 Bob 的跨链传输。作为交换，Alice 在 Chain_b 上接收来自 Bob 的相应数量代币。注：此图强调了 HTLC 的步骤，显示了 Alice 在 Chain_a 上拥有的代币向 Bob 的跨链传输。作为交换，Alice 在 Chain_b 上接收来自 Bob 的相应数量代币。](img/5113a532010ddac03a91c547bc2ad6ff_285_0.png)

# 总结与结论

本章讨论了加密资产的底层技术，包括基础密码学原语、分布式账本技术（`DLTs`）以及最近的无许可区块链技术。区块链社区近期提出了多种方法来提高可扩展性并实现类似 VISA 的交易处理速度。本章回顾了适用于第 1 层和第 2 层区块链的技术。它还考虑了区块链三角，指出去中心化、安全性和可扩展性无法完美共存。本章最后提供了交换加密资产技术的概述，由于加密资产的日益普及，这是一个动态的研究开发领域。

# 讨论

1.  列出公钥加密（非对称加密）可以提供的功能。
2.  识别采用区块链技术的主要障碍。
3.  讨论提高其扩展性的可能性。
4.  定义第 1 层安全要求。
5.  识别 `HTLC` 的主要用途。

# 参考文献

- Anagnostou, E., & Hadzilacos, V. (1993). Tolerating transient and permanent failures. In International workshop on distributed algorithms (pp. 174–188). Retrieved from https://link.springer.com/10.1007/3547-5271
- Binance Academy. (2022). Training complete. Retrieved from https://academy.binance/en/english/glossary/complete
- Boneh, D., Gentry, C., Lynn, B., & Shacham, H. (2003). A survey of signature aggregations. RSA Crypto, 6, 1–9.
- Bonneau, J., Miller, A., Clark, J., Narayanan, A., Kroll, J., & Felten, E. W. (2015). Research and perspectives for blockchain and cryptocurrencies. In 2015 IEEE security and privacy (pp. 104–121).
- BW. (2022). Bitcoin Wiki: Atomic cross-chain trading. Retrieved from https://bitcoinf.wiki/
- Buterin, V. (2014). Ethereum: a next-generation smart contract and decentralized application platform. Retrieved from https://github.com/ethereum/wiki/White-Paper
- Cahin, C. (2017). Blockchains and consensus protocols: Snake oil. In 2017 13th European dependable computing conference (EDCC) (pp. 1–12).
- Canetti, R, Goldreich, O., & Halevi, S. (2004). The random oracle methodology, revisited. Journal of the ACM, 51, 557–594.
- Chaum, D. (1984). Blind signature system. In Advances in cryptography (p. 153). Boston, MA: Springer.
- CMC (2022). CoinMarketCap. Retrieved from https://marketcap.com
- Cloudflare (2022). 什么是 DDoS 攻击？检索自 https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/
- 跨链 (2019, 11月). 德国意志交易所。Swisscom 及其合作伙伴成功通过代币结算安全交易。检索自 https://www.swisscom.ch/en/news/2019/11/19-wertptiertransaktionen-mi-t.tokens.html
- Diffie, W., & Hellman, M. (1976). 密码学的新方向. IEEE Transactions on Information Theory, 22(6), 644–654.
- Dziembowski, S., Eckey, L., Forst, S., Hesse, J., & Hoštková, K. (2019). 多方虚拟状态通道. 加密技术理论与应用国际会议 (pp. 625–656). Cham: Springer.
- Dubitovskaya, A. (2018). 硬件中的隐私保护数据交换与聚合. 博士论文, EPFL.
- EBA. (2019). 给欧洲委员会关于加密资产的建议报告。检索自 https://www.eba.europa.eu/site/default/files/documents/2019/10/201025457/67493-daa-858-4429-a91-9e5d8684/EBA%20Report%20on%20crypto%20assets
- EY. (2021). 加密资产：全球监管视角。检索自 https://assets.ey.com/banking-and-capital-markets/ey-crypto-assets-the-global-regulatory-perspective.pdf
- Garcia-Molina, H. (1983). 分布式数据库中事务处理的语义锁. ACM Transactions on Database Systems, 8(2), 186–213.
- Gervais, A., Game, O., Witt, K., Klyantzis, V., Ritzdorf, H., & Capkun, S. (2016). 关于工作链的安全性与性能. 在 2016 ACM SIGSAC 计算机与通信安全会议上 (pp. 3–16).
- Gilbert, S., & Lynch, N. (2009). Brewer 猜想以及一致性、可用性和分区容错 Web 服务的可行性. ACM News, 33(2), 51–59.
