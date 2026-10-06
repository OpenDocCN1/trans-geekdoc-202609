
# 参考文献

Averroes, R. (2021). *BABB Whitepaper*. Getabb.com. Retrieved from https://getbabb.com/wp-point/uploads/2021/03/BABB-Whitepaper.pdf

Back, A. (2002, August). *Hashcash – A denial of service countermeasure*. Hashcash. Retrieved from http://www.hashcash.org/hashcash.pdf

Blockchain.com. *Fees per transaction (USD)*. Blockchain.com. Retrieved from https://www.blockchain.com/charts/fees-used-per-transaction

Buterin, V. (2013). *Ethereum Whitepaper*. Retrieved from https://ethereum.org/en/white-paper/

Buterin, V. (2017, June). *On path independence*. Vitalik.ca. Retrieved from https://vitalica.ca/general/2017/06/22/marketmakers.com

Buterin, V. (2020, November). *Why proof of state*. Vitalik.ca. Retrieved from https://vitalica.ca/general/2020/11/h6pofstake.model

Buterin, V. (2021, May 23). *The limits to blockchain scalability*. Vitalik.ca. Retrieved from https://vitalica.ca/general/2021/05/23/scaling.html

Flitter, E. (2021). The world's biggest crypto exchange still lacks U.S. footing. *The New York Times*, August 19. Retrieved from https://www.nytimes.com/2021/08/19/business/finance-crypto-exchange-ipo.html

Hertzog, E., Benarti, G., & Benarti, G. (2018, March). *Bitcoin protocol*. Storage.googleapis.com. Retrieved from https://storage.googleapis.com/website-bitcoin/2018/04/01ba8253-bitcoin_protocol_whitepaper_en.pdf

"Litecoin – Litecoin Wiki". (2022). Litecoin.info. Retrieved from litecoin.info/index.php/Litecoin. Accessed on February 14.

Luz, N. (2019). *Digital is the cash*. Retrieved from https://media.dash.org/wp-content/uploads/Digital_the_Cash_Nathaniel_Luz.pdf

Ossinger, J. (2021, August 15). Crypto market retails $2 trillion cap amid bitcoin gains. Bloomberg.com. Retrieved from https://www.bloomberg.com/news/articles/2021-08-15/crypto-market-retails-2-trillion-market-cap-amid-bitcoin-gains

Nakamoto, S. (2008). *Bitcoin: A peer-to-peer electronic cash system*. Bitcoin.org. Retrieved from https://bitcoin.org/bitcoin.pdf

Qin, K., Zhou, Livshits, B., & Gervais, A. (2021). Attacking the DeFi ecosystem with flash loans. In Borisov & Diaz (Eds.), *Financial cryptography and data security*. Lecture Notes in Computer Science (vol. 12674). Berlin: Springer

Schoenberg, T. (2021, May 13). Binance forces probe by U.S. money laundering and sleuths. Bloomberg.com. Retrieved from https://www.bloomberg.com/news/articles/2021-05-13/binance-probed-by-u-s-gains

# 正文

学者、密码学家，以其在数字合约和数字货币领域的研究而闻名。Szabo 经常对他对数字革命以及人类如何签订合同发表预测。他认为会有人开发出用于“智能合约”的算法。根据 Szabo (1997) 的观点，智能合约是一组数字承诺，包含了一些协议，双方在这些协议内利用人工智能履行对方的承诺。

DeFi 以完全无许可的方式运行，没有公司或政府等第三方来阻止交易或收取费用。这种情况通过智能合约实现，智能合约是代码的段落，它们规定了交易员的条款，然后根据这些条款自动执行交易。这些合约及其结果在分布式区块链上是透明的，没有任何单一实体可以控制它。也就是说，它是抗审查的。

本章旨在提供 DeFi 及其实现的概述。下一节提供了 DeFi 特性的背景介绍，介绍了 DeFi 堆栈的组件，并涵盖了从 DeFi 到中心化金融（CeFi）的对比。随后，本章回顾了去中心化项目和应用的各种用途：(1) 去中心化交易所（DEXs），(2) 稳定币，(3) 借贷与贷款，(4) 资产管理，(5) 衍生品，(6) 保险以及 (7) 支付。最后，本章通过识别 DeFi 目前的局限性总结。

## DeFi 特性

本节回顾了 DeFi 的主要特性。

### 去中心化

在 CeFi 系统下运行的金融机构通过作为中间人促进许多交易来帮助降低交易成本。降低的交易成本和更处理时间为系统用户创建了一个流畅高效的系统。然而，随着交易数量的增加，中心化金融机构极有可能膨胀并垄断市场。因此，客户可能需要支付垄断价格，而不是基于提供价值的最优价格。DeFi 系统通过 P2P 网络模型从上解决了这个问题，确保没有单一实体主导。点对点（P2P）网络是一种去中心化平台，两个个人可以在没有第三方中介的情况下直接交互。DeFi 的网络效应有助于将成本保持在市场决定的最优水平（Catalini & Gans, 2020）。

### 创新性

中心化架构通过中央机构的某种程度的控制来促进创新。相比之下，DeFi 在没有任何中央组织规定规则的情况下促进了创新。它催生了组合性和无许可创新（Hellar, Crawford, Rocca, Teodori, & Veneziani, 2020）。在中心化平台上工作开发产品的第三方开发者，其许可可能会被中央实体撤销。由于去中心化平台没有中央实体，开发者可以自由开放地开发产品，从而以更高速度创建创新产品，并将产品的所有权留给市场参与者或客户。中心化平台使用商标和专利来保护其竞争优势，阻碍了市场创新的速度。在开源技术的帮助下，去中心化平台促进了组合创新，加速了创新和产品的创造。以太坊（ETH）和 BTC 是两个去中心化网络，在上面可以创建许多应用程序。

### 互操作性

互操作性是不同金融系统和机构无缝无延迟地工作的能力。DeFi 利用互操作性来促进高额金融资本跨产品、边界和服务的转移。传统金融在孤岛中运行，信息是具有价值的稀缺资源。各个部门和组织都有自己的账本，形成了一个阻碍互操作性的复杂系统。DeFi 借助开源公共区块链可以解决这些局限性。目前，由于不同区块链之间的应用价值转移困难，尚无法完全实现互操作性。然而，新系统的实施并不遥远。Polkadot 和 Cosmos 是两个尝试与其他区块链网络实现互操作性的区块链示例。

### 透明性与无国界

传统或 CeFi 涉及一个其只能访问的中央账本。DeFi 使用包含由分布式共识保护的交易的公共账本克服了透明度的缺乏。它在没有先验关系的情况下在交易参与者之间建立了信任和透明度。账本可以公开查看并验证当前或过去的财务失误。DeFi 与任何国家的法货币之间都没有联系，与 CeFi 形成鲜明对比。因此，它促进了全球资本和价值的顺利转移。DeFi 不受任何中央政府实监管。它真的是无国界的，只需点击即可在没有任何中介的情况下实现价值转移。

## DeFi 堆栈

DeFi 堆栈是 DeFi 生态系统层的组合，允许使用网络。该堆栈包含价值单元、交易层、预言机、市场和钱包。不同的应用程序可以在 DeFi 堆栈的跨层之间以及任何给定的层内相互交互，因为它们是可组合的。组合性意味着某人可以使用构建模块的输出作为另一个构建模块的输入。然而，这种特征允许各种组件相互交互并相互构建。但组合性也意味着 DeFi 堆栈层与下方层一样安全。例如，如果某层被破坏，每个后续层将是不安全的。

### 价值单元

价值单元是 DeFi 过程的起点。价值单元通常涉及稳定币、价格挂钩到另一种加密货币的加密货币、法币或交易所商品。稳定币的示例包括 `Tether`、`USD Coin`、`Binance USD`、`DAI` 和 `Pax Dollar`。其他价值单元可能包括 `BTC`、`ETH` 和 `Litecoin` 等加密货币。

### 交易层

层 1 解决方案是交易层的底层区块链架构，允许在 `ETH` 之上构建智能合约。开发者可以使用编程语言创建应用程序并使用以太虚拟机（`EVM`）执行这些应用程序。`EVM` 在编程语言和执行机器之间创建兼容性，确保每个应用程序免受其他程序及其主机的侵害。`ETH` 可以管理每秒 30 次交易，并具有较高的 `gas` 费用（即补偿验证交易所需的计算能力的费用）。

层 2 可以构建在其之上，例如各种类型的 `rollups`（汇总）。因此，层 2 解决方案是底层区块链之上的叠加网络。`rollup` 是一种在主 `ETH` 链（层 1）之外执行交易并在层 1 上发布交易数据的解决方案。通过这些解决方案，交易将在层 2 更快地执行并在层 1 `ETH` 结算。我们的贡献者。层 2 `rollup`。根据 Haga (2021) 的数据，2021 年前九个月 DEX 的交易量超过了 8290 亿美元。目前 DEX 交易量的 90% 通过 `ETH` 进行。另一个层 1 示例是 `Solana` (`SOL`)。`SOL` 使用历史证明来验证事件之间的顺序和时间，对交易进行时间戳以便按正确顺序拼接（Yakovenko, 2017）。历史证明的引入允许 `SOL` 减少接收交易的缓冲时间并每秒处理高达 65000 次交易。另一个层 1 解决方案是 `Cardano`。`Cardano` 使用代币作为网络费用、新铸代币或其他形式的奖励。这些奖励被称为验证。验证在确认新区块准确并符合协议规则时才被允许。

### 预言机

预言机是第三方，为链上智能合约提供执行这些合约所需的外部链外信息（真实世界数据）。链上是区块链上的价值移动，而链外是区块链外的价值移动。智能合约的有效性很大程度上取决于其对准确信息的获取，大多数预言机会从多个来源寻找数据以确保准确性。最广泛使用的预言机是 `Chainlink`，它是一个为智能合约提供可靠、不可篡改的输入和输出的多链网络。

### 钱包与 CeFi 对比 DeFi

加密钱包通过存储私钥来确保数字资产的安全。硬件钱包允许冷存储。黑客无法访问硬件钱包，因为它没有连接到互联网。在线钱包允许在应用或通过软件存储私钥。CeFi 和 DeFi 都是个人获取与加密货币相关的服务的媒介。CeFi 是传统金融的另一种传统替代方案。CeFi 用户信任公司的管理层来执行由源代码所承诺的服务。相比之下，DeFi 用户信任技术性能能够如源代码所承诺的那样运行。表 10.1 显示了 CeFi 和 DeFi 之间的相似与不同之处。

## 去中心化货币

传统上，黄金等贵金属支撑着一个国家的法币。该系统进了演变。一个国家公民对中央银行、政府和经济的信任决定了大多数法币的价值。`BTC` 是一种通过技术发行的去中心化货币，具有固定供应以控制通胀影响。它在去中心化世界中充当价值存储手段的角色，就像黄金在传统金融世界中一样。`BTC` 可在全球范围内存储和传输价值，而不受任何中心实体的控制。它的效用仍然是一个受关注的问题。其他流行的加密货币是 `ether` 和 `dash`。

### 表 10.1. CeFi 和 DeFi 的主要区别

| 特性 | CeFi | DeFi |
|---|---|---|
| 底层技术 | 区块链 | 区块链 |
| 资产焦点 | 数字资产 | 数字资产 |
| 记账单位 | 法币计价 | 数字资产或稳定币计价 |
| 执行 | 金融中介 | 智能合约 |
| 清算与结算 | 由服务提供商或结算所处理 | 将交易写入底层区块链 |
| 治理 | 依赖于服务机构和监管机构 | 由协议开发者或具有投票权的用户管理 |
| 可审计性 | 第三方审计师 | 供所有人访问的开源代码和公共账本 |
| 隐私 | 身份检查和个人数据受国家法律验证要求的限制，如了解您的客户 `KYC` 和反洗钱 `AML` | 目前无身份识别 |
| 安全性 | 受到数据泄露、黑客和故障的影响 | 用户承担所有风险 |
| 政府强制披露、消费者保护和监管 | 政府强制披露、消费者保护和监管 | 用户承担所有风险 |

备注：此表显示了 CeFi 和 DeFi 的不同之处。CeFi 用户信任公司的管理层负责任地执行承诺的服务。相比之下，DeFi 用户信任技术性能能够如源代码所承诺的那样运行。

## 去中心化融资

公司通常以各种方式筹集资金。一种方法是通过首次公开募股（`IPO`），当私有公司通过在证券交易所出售股份给机构投资者和零售投资者来实现上市。`IPO` 涉及许多障碍，例如律师和银行等中介机构，以及政府等监管机构。它受到高度监管并涉及大量的准备工作。`IPO` 之前的文书工作通常需要六个月。

第二种方法是风险融资。它要求投资者提供资金。网络效应是指随着用户数量增加，产品的价值也随之增加。这种融资依赖于投资者。

第三种方法是去中心化融资。去中心化融资通过首次代币发行（`ICO`）来克服障碍，初创公司通常使用这种工具。这种 `ICO` 促进了区块链的创新。`ICO` 允许通过发行代币来筹集资金。`ICO` 能够在全球范围内筹集资金，不受中心实体的限制。最近，一种不同的 `ICO` 形式，即首次交易所发行（`IEO`），已经出现。`IEO` 是项目通过出售其代币来筹集资金的方式。这种 `ICO` 允许初创公司通过发行代币来筹集资金，并提供即时流动性。

## 去中心化支付服务

目前的支付服务基于中心化网络，如 `Visa` 收取高额费用，跨境支付。去中心化网络通过低成本支付解决了这个问题，提供了更好的安全性和透明度。例如，`BTC` 闪电网络使用由去中心化网络维护的支付通道，实现了微支付。`Twitter` 和 `Square` 是尝试去中心化支付的公司之一。商家向低成本移动，服务在未来将会下降。同样，`Ripple` 提供了更快、更便宜的跨境支付。

## 去中心化合约

合同需要双方之间的信任，通常由金融中介提供支持。这些合同涉及许多成本，如谈判、起草和重新谈判。区块链技术利用 P2P 智能合约在满足协议规定的规则时自动执行不同阶段。它降低了项目的成本和复杂性，同时增加了信任、透明、不可篡改性和自动化。这种技术也导致了创新。基于智能合约的贷款和借贷就是例子。这些成本节省可以传递给终端用户，有助于提高。

## 治理机制

DeFi 没有中心实体。由于其分布式共识机制，治理机制将控制权从第三方转移到活跃协议用户。协议的活跃用户做出决策。一组投资者和开发者创建一个协议。然而，由于其去中心化的本质，每个活跃参与用户都为协议做出选择，使其更加透明可靠。DeFi 最青睐的治理机制是下文讨论的流动民主，以及其他治理机制。

### 创始人控制

最初，创始人控制 DeFi 项目。他们控制项目并尽可能扩大规模。

### 委员会控制

委员会控制模式的权力属于一组核心开发者，他们为项目的路线图和战略制定计划，就像 `ETH` 和 `BTC` 的开发者一样。

### 流动民主

它是允许活跃协议用户对决策发表意见的治理机制。成员通过满足最低治理代币要求进行投票，该要求因区块链网络而异。持有的治理代币数量决定了投票权重。投资者青睐这种 DeFi 项目，因为他们在网络协议中拥有相当的份额。因此，治理代币确保了 DeFi 的民主和去中心化治理。目前，网络根据他们参与协议时质押的流动性或提供的押金来获得治理代币。

## 去中心化项目与应用

DeFi 有许多应用，包括 (1) 去中心化交易所 (`DEXs`)、(2) 稳定币、(3) 借贷、(4) 资产管理、(5) 保险、(6) 去中心化保险以及 (7) 支付。

## 去中心化交易所

`DEX` 是一种连接加密货币买家和卖家的非托管型交易所。它利用智能合约执行交易，无需中间环节。非托管的性质确保了用户保留自己的私钥和资金，而不是第三方。每笔交易都在区块链上安全运行，从而使交易所能够基于信任和透明提供一系列全新的数字金融资产和产品。缺乏作为结算机构的中间环节确保了交易者每笔交易的费用更低。因此，`DEX` 提供了更好的定价、安全性和费用。DeFi 的增长显然意味着 `DEX` 的流动性。目前正在进行开发以解决后文将讨论的扩展性三难困境，`BTC` 和 `ETH` 区块链是构建 `DEX` 智能合约的底层。`DEX` 的示例包括 `Uniswap`、`Bancor` 和 `Kyber`。

## 稳定币

加密货币以高波动性和价格波动而闻名，这使得它们在许多应用（如借贷）中变得不可行。由于价格不稳定，政府实体和其他金融机构不太可能支持这些加密货币。这种不稳定性是涉及加密货币与美元等法币货币金融交易之间最显著的区别之一。
