

[^(16)](#c01.xhtml#ftn16a) Charles Hoskinson, “Cardano whiteboard; overview with Charles Hoskinson.”

[^(17)](#c01.xhtml#ftn17a) Cryptopedia, “The Blockchain Trilemma: Fast, Secure, and Scalable Networks.”

[^(18)](#c01.xhtml#ftn18a) [https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3](https://medium.com/certik/the-blockchain-trilemma-decentralized-scalable-and-secure-e9d8c41a87b3)

[^(19)](#c01.xhtml#ftn19a) [https://coinmarketcap.com/currencies/cardano/#About](https://coinmarketcap.com/currencies/cardano/#About)

[^(20)](#c01.xhtml#ftn20a) [https://cardano.org/genesis/#audit](https://cardano.org/genesis/#audit)

[^(21)](#c01.xhtml#ftn21a) [https://cardano.org/partners/](https://cardano.org/partners/)

[^(22)](#c01.xhtml#ftn22a) [https://cardano.org/partners?tab=iog](https://cardano.org/partners?tab=iog)

[^(23)](#c01.xhtml#ftn23a) cardanians.io, “There is 1.23B ADA in Cardano’s.”

[^(24)](#c01.xhtml#ftn24a) Source data from:

[https://www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp](https://www.investopedia.com/what-is-xrp-6362550#toc-xrp-ledger-and-xrp)

[https://coinmarketcap.com/currencies/dogecoin/#About](https://coinmarketcap.com/currencies/dogecoin/#About)

[https://www.coingecko.com/en/coins/ethereum/tokenomics](https://www.coingecko.com/en/coins/ethereum/tokenomics)

[https://coinmarketcap.com/currencies/cardano/#About](https://coinmarketcap.com/currencies/cardano/#About)

[https://www.coingecko.com/en/coins/polkadot/tokenomics](https://www.coingecko.com/en/coins/polkadot/tokenomics)

[https://coinmarketcap.com/currencies/polygon/#About](https://coinmarketcap.com/currencies/polygon/#About)

[https://coinmarketcap.com/currencies/bnb/#About](https://coinmarketcap.com/currencies/bnb/#About)

[https://coinmarketcap.com/currencies/toncoin/](https://coinmarketcap.com/currencies/toncoin/)

[https://coinmarketcap.com/currencies/solana/#About](https://coinmarketcap.com/currencies/solana/#About)

[^(25)](#c01.xhtml#ftn25a) [https://docs.cardano.org/explore-cardano/monetary-policy/](https://docs.cardano.org/explore-cardano/monetary-policy/)

[^(26)](#c01.xhtml#ftn26a) [https://docs.cardano.org/about-cardano/evolution/eras-and-phases/](https://docs.cardano.org/about-cardano/evolution/eras-and-phases/)

[^(27)](#c01.xhtml#ftn27a) [https://roadmap.cardano.org/en/](https://roadmap.cardano.org/en/)

[^(28)](#c01.xhtml#ftn28a) [https://roadmap.cardano.org/en/byron/](https://roadmap.cardano.org/en/byron/)

[^(29)](#c01.xhtml#ftn29a) [https://roadmap.cardano.org/en/shelley/](https://roadmap.cardano.org/en/shelley/)

[^(30)](#c01.xhtml#ftn30a) [https://roadmap.cardano.org/en/basho/](https://roadmap.cardano.org/en/basho/)

[^(31)](#c01.xhtml#ftn31a) [https://roadmap.cardano.org/en/voltaire/](https://roadmap.cardano.org/en/voltaire/)

[^(32)](#c01.xhtml#ftn32a) [https://docs.cardano.org/explore-cardano/eras-and-phases/](https://docs.cardano.org/explore-cardano/eras-and-phases/)

[^(33)](#c01.xhtml#ftn33a) [https://github.com/cardano-foundation/CIPs/blob/master/CIP-0059/feature-table.md](https://github.com/cardano-foundation/CIPs/blob/master/CIP-0059/feature-table.md)

[^(34)](#c01.xhtml#ftn34a) [https://consensys.io/blockchain-use-cases/capital-markets](https://consensys.io/blockchain-use-cases/capital-markets)

[^(35)](#c01.xhtml#ftn35a) [https://consensys.io/blockchain-use-cases/media-and-entertainment](https://consensys.io/blockchain-use-cases/media-and-entertainment)

# 第 2 章

# 密码学与共识算法概述

# 简介

在本章中，我们将介绍密码学和加密哈希。我们将展示加密哈希在区块链技术中是如何生成和使用的。接下来，我们将探讨比特币区块链使用的工作量证明共识协议。我们将展示证明者和验证者如何协同工作以保护区块链。随后，我们将考察权益证明及其相对于工作量证明的优势。最后，我们将回顾 Ouroboros，即 Cardano 的权益证明共识协议。

# 结构

在本章中，我们将讨论以下主题：

*   密码学 
    *   公钥加密
    *   哈希
*   数字签名 
    *   所有权链
*   工作量证明 
    *   挖矿
*   权益证明 
    *   概率最终性（基于链）
    *   绝对最终性（PBFT）
*   Ouroboros 
    *   Ouroboros Classic
    *   Ouroboros BFT
    *   Ouroboros Praos
    *   Ouroboros Genesis
    *   Ouroboros Crypsinous
    *   Ouroboros Chronos
    *   Ouroboros 协议生命周期

# 密码学

“斯巴达人最早于公元前 400 年使用密码设备进行通信，这是有记录以来最早将密码学用于通信的案例。”[¹](#c02.xhtml#ftn1) 密码是指转换消息以隐藏其含义的任何方法。[²](#c02.xhtml#ftn2) 在 1970 年代中期之前，所有密码系统都使用对称密钥算法，即发送方和接收方使用相同的加密密钥配合底层算法，双方都必须保密该密钥。[³](#c02.xhtml#ftn3) `对称` 加密的挑战在于秘密密钥必须事先安全传输，当需要管理许多密钥或不存在事先的安全通道时，这种方式难以扩展。[⁴](#c02.xhtml#ftn4) 这一局限性通过 `非对称` 加密得以解决，后者用于 `公钥加密` 和 `数字签名`。

# 公钥加密

使用公钥加密的过程的第一步是使用基于数学的单向加密算法生成一对公钥和私钥。[⁵](#c02.xhtml#ftn5) 经典的密码学示例是指 Alice 试图向 Bob 发送加密消息，如[图 2.1](#c02.xhtml#fig2_1)所示。在这种情况下，Alice 需要使用 Bob 的公钥来加密消息。除了持有私钥的 Bob 之外，该消息对所有人都是不可读的。当 Bob 收到加密消息时，他使用自己的私钥对其进行解密，并读取 Alice 发送的原始消息。

![](images/Figure-2.1.jpg)

**图 2.1：** 公钥加密

# 哈希

加密哈希是使用一种数学函数生成的，该函数接受任意大小的输入并生成固定长度的输出。[⁶](#c02.xhtml#ftn6) 这被称为单向哈希，无法解码以揭示输入的原始内容。对于相同的输入集，生成的输出将始终相同。如果输入哪怕发生最微小的变化，生成的哈希将完全不同，这被称为雪崩效应。[⁷](#c02.xhtml#ftn7) 雪崩效应确保了抗碰撞性和篡改检测，这在区块链中被广泛使用。

`BLAKE2b-256` 加密哈希算法用于在 Cardano 中生成地址，[⁸](#c02.xhtml#ftn8) `BLAKE2b-224` 用于生成公钥哈希。哈希函数也用于区块链中，以生成包含交易列表的区块的哈希。这有助于检查和确保不可变性，因为区块中所含交易的任何变更都会改变区块哈希。

# 数字签名

`数字签名` 为 Alice 提供了一种签署消息的方式，以便稍后任何人都可以使用 Alice 的公钥来验证该签名。[⁹](#c02.xhtml#ftn9) 消息不像公钥加密那样被加密；相反，数字签名证明了这条消息是由 Alice 且仅由 Alice 签署的。在区块链的语境下，消息是一笔交易，而 Alice 是区块链地址的所有者。当一笔交易由 Alice 的私钥签署时，区块链上的任何其他人都可以使用 Alice 的公钥进行验证，如[图 2.2](#c02.xhtml#fig2_2)所示。

![](images/Figure-2.2.jpg)

**图 2.2：** 数字签名

