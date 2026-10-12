

# 第 14 章：结束语

## 简介

本章将回顾 Cardano 的精神内核，以及它如何与同行评审流程和形式化方法相关联。我们将考察软件行业标准，以及这些标准为何在高保障软件方面显得力不从心。我们将了解半形式化方法是如何被用于构建 Cardano 的，以及像 `IACR` 这样的密码学协会是如何促进同行评审流程的。接下来，我们将结合现实案例，探讨利用 Cardano 实现社会公益的潜力。我们还将讨论监管与合规风险，以及需要注意的事项。随后，我们将回顾技术采纳的五个阶段，以及它们如何应用于区块链。最后，我们将探讨 Cardano 的发展历程及通往此处的道路。

## 结构

在本章中，我们将讨论以下主题：

*   Cardano 精神内核
*   软件行业标准
    *   区块链风险
    *   半形式化方法
    *   IACR
*   社会公益潜力
*   监管与合规风险
*   技术采纳
*   Cardano 的发展历程

## Cardano 精神内核

开放与透明是 Cardano 的精神内核[¹](#c14.xhtml#ftn1)，也是为何如此重视同行评审和形式化方法的原因之一。国际密码学研究协会（`IACR`）[²](#c14.xhtml#ftn2)等组织的同行评审流程采用双盲机制，使作者和评审者彼此匿名[³](#c14.xhtml#ftn3)。这有助于消除偏见，并在评审过程中促进公平与透明。除了同行评审流程，`IOG`（`IOHK`）还应用形式化方法，严格运用数学技术确保软件按预期运行[⁴](#c14.xhtml#ftn4)。例如，用 Haskell 编写的 Cardano 账本代码可以追溯到已通过同行评审的形式化规范。这种可追溯性和透明度在区块链行业中是无与伦比的，通常仅见于航天、航空和金融行业的高保障软件中[⁵](#c14.xhtml#ftn5)。

从根本上说，区块链技术旨在赋予边缘（用户）自主权和自我控制权。赋能边缘（个人或员工）的益处在于提高生产力、增强参与度并改善社会成果[⁶](#c14.xhtml#ftn6)。然而，由于底层加密货币代币可自由交易，这必然会导致投机。这种投机常被滥用，区块链（及项目）伪装成无许可和去中心化，其主要目的却是榨取价值。自比特币早期 ICO 时代起，这便是一个问题[⁷](#c14.xhtml#ftn7)。因此，建议与专注于服务他人的区块链和项目保持一致，这最终将导致正确的价格发现、价值与市场契合度。

## 软件行业标准

质量、韧性和无缺陷通常与大多数软件无关，尤其是近期发布的软件。这种“行业标准”门槛很低，通常通过定期软件更新来逐步提高软件质量。这种方法不适用于区块链！区块链本质上是不可变的，一旦部署，*真正*去中心化和无许可的区块链无法被中央权威停止、重置或修补。此外，区块链可能涉及数百万美元的价值，这些价值可能因利用软件中发现的漏洞而被窃取。

## 区块链风险

让我们首先看看设计和部署区块链时可能出现的问题。以下是可能发生的问题列表[⁸](#c14.xhtml#ftn8)：

*   协议设计缺陷
*   设计实现错误
*   典型软件错误
*   业余密码学实现
*   错过性能期限
*   负载下崩溃
*   扩展失败
*   DoS 故障
*   易受经济攻击

## 参考文献

[^(37)](#c13.xhtml#ftn37a) <https://cardanoscan.io/pools>

[^(38)](#c13.xhtml#ftn38a) <https://pool.pm/>

[^(39)](#c13.xhtml#ftn39a) <https://developers.cardano.org/docs/operate-a-stake-pool/>

[^(40)](#c13.xhtml#ftn40a) <https://cardano-community.github.io/guild-operators/>

[^(41)](#c13.xhtml#ftn41a) <https://www.coincashew.com/coins/overview-ada/guide-how-to-build-a-haskell-stakepool-node>

[^(42)](#c13.xhtml#ftn42a) Crypto Carlos, "Node course | Creating a stake pool, the setup"

[^(43)](#c13.xhtml#ftn43a) <https://iohk.io/en/blog/posts/2020/09/16/project-catalyst-introducing-our-first-public-fund-for-cardano-community-innovation/>

[^(44)](#c13.xhtml#ftn44a) <https://cardano.ideascale.com/c/landing>

[^(45)](#c13.xhtml#ftn45a) Tim Richmond, "Project Catalyst - A virtuous cycle of Cardano ecosystem development"

[^(46)](#c13.xhtml#ftn46a) <https://cardano.ideascale.com/c/landing>

[^(47)](#c13.xhtml#ftn47a) <https://projectcatalyst.io/>

[^(48)](#c13.xhtml#ftn48a) <https://www.youtube.com/@IohkIo>

[^(49)](#c13.xhtml#ftn49a) <https://t.me/cardanocatalyst>

[^(50)](#c13.xhtml#ftn50a) <https://www.w3.org/TR/did-core/>

[^(51)](#c13.xhtml#ftn51a) <https://atalaprism.io/#why>

[^(52)](#c13.xhtml#ftn52a) <https://github.com/hyperledger/identus>

[^(53)](#c13.xhtml#ftn53a) <https://midnight.network/>

[^(54)](#c13.xhtml#ftn54a) Neil Burgess, "Calling trailblazers to Midnight"

[^(55)](#c13.xhtml#ftn55a) Mike Ward, "Partner chains are coming to Cardano"

[^(56)](#c13.xhtml#ftn56a) Mike Ward, "Partner chains are coming to Cardano"

[^(57)](#c13.xhtml#ftn57a) Red Sheehan, "State of Cardano Q4 2023"

[^(58)](#c13.xhtml#ftn58a) <https://milkomeda.com/>

[^(59)](#c13.xhtml#ftn59a) <https://www.wanchain.org/>

[^(60)](#c13.xhtml#ftn60a) <https://worldmobile.io/en>

[^(61)](#c13.xhtml#ftn61a) <https://developers.cardano.org/docs/smart-contracts/plutus>

[^(62)](#c13.xhtml#ftn62a) <https://www.youtube.com/playlist?list=PLnPTB0CuBOBypVDf1oGcsvnJGJg8h-LII>

[^(63)](#c13.xhtml#ftn63a) <https://developers.cardano.org/docs/smart-contracts/opshin>

[^(64)](#c13.xhtml#ftn64a) <https://developers.cardano.org/docs/smart-contracts/plu-ts>

[^(65)](#c13.xhtml#ftn65a) <https://academy.cardanofoundation.org/>

[^(66)](#c13.xhtml#ftn66a) <https://www.youtube.com/channel/UCX9j__vYOJu00iqBrCzecVw>

[^(67)](#c13.xhtml#ftn67a) <https://education.emurgo.io/>

[^(68)](#c13.xhtml#ftn68a) <https://gimbalabs.com/gimbalgrid>

[^(69)](#c13.xhtml#ftn69a) <https://www.youtube.com/@LearnCardano>

[^(70)](#c13.xhtml#ftn70a) <https://www.youtube.com/@CardanoWithPaul>

