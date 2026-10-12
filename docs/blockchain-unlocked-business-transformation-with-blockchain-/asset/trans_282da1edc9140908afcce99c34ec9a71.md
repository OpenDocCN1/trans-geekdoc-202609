
简而言之，你需要投入大量资源。一旦你获得了 51% 的算力，网络的其余部分可以选择分叉区块链，让你只得到一个空壳。它可以创建一份高达 51% 算力时刻的账本副本（即获得超过网络 51% 的算力），然后创建一个新分支并继续更新有效账本。随后你可能不得不发起另一次昂贵的反击。以这种方式浪费资源几乎没有任何理由；利用资源为网络挖矿并获取挖矿奖励在经济上更合理。事实上，比特币区块链背后的博弈论旨在激励人们建设系统而非破坏它。简而言之，遵守规则比破坏规则更有利可图。

话虽如此，区块链领域担心量子计算的发展可能会使攻击和摧毁区块链网络变得更容易、更廉价。这种妥协可能表现为破解区块链密码学的能力。无需窃取私钥，推算出私钥将变得更容易^([5](#ch04.xhtml#ch04fn5))。

因此，区块链开发者和创新者正在超前思考，以生产能使量子计算对区块链技术无关紧要的协议。两种抗量子计算协议是以太坊的 Serenity 和 zkSTARKs^([6](#ch04.xhtml#ch04fn6))。

### 代码和协议是否稳健？

现在让我们看看第三个也是最后一个角度，通过它你可以确定区块链是否安全。网络上的任何设备都必须安装并运行其核心软件，以便与共享账本上的其他设备通信并形成共识，因为区块链依赖它来执行协议。第一个版本通常来自网络的创始人；例如，创始人中本聪编写了比特币核心软件的第一个版本。后续版本是不同参与者或核心开发者协作工作的产物。任何人都可以通过比特币改进提案（BIP）流程提议对核心软件和协议进行更改。提议者与社区其他成员交谈，创建包含更改的核心软件的下一个版本，并说服其他人下载并运行它。该过程比我在这里描述的更复杂。但我想你已经明白了。

像任何代码一样，区块链核心软件最终可能会存在 bug 和执行弱点。这些可能使用户面临许多风险，例如双重支付和攻击点。主要区块链都曾发现过 bug。其中一些 bug 非常严重，危及区块链上持有的价值。2018 年底，发现了一个缺陷，本可被利用来关闭比特币网络的部分功能，并允许恶意行为者凭空创造比特币。在顶级比特币核心开发者修复它之前，该缺陷被保密了（数天）^([7](#ch04.xhtml#ch04fn7))。

2016 年初，德国区块链初创公司 Slick.it 在以太坊区块链上推出了去中心化自治组织（DAO）。该实体本应作为一家只有投资者、没有管理层或员工的公司运作。投资者将通过投票，聘请服务提供商代表 DAO 履职。结果发现，将这一想法变为现实的代码中存在 bug。但攻击者利用了它，并开始窃取投资者筹集的近 1.5 亿美元资金。为阻止攻击，以太坊网络升级了其核心软件并回滚了交易。这导致网络分裂为两个：以太坊（ETH）和以太坊经典（ETC）^([8](#ch04.xhtml#ch04fn8))。

总之，区块链并非万无一失。本章所述三个层面的区块链安全性考量，都应与其他现有系统进行比较。在许多方面，区块链比其寻求取代的系统更安全。区块链密码学让用户对其活动和资产拥有更多控制权和安全性。管理区块链的博弈论使攻击不太可能发生。至于代码中的 bug，区块链是开源项目，往往拥有负责任的社区；任何 bug 通常都会在危害生态系统之前被发现并修复。

^([1](#ch04.xhtml#ich04fn1)) Shane, Daniel. “Coincheck: $530M Cryptocurrency Heist May Be Biggest Ever.” CNNMoney, Cable News Network, Jan. 2018, [money.cnn.com/2018/01/29/technology/coincheck-cryptocurrency-exchange-hack-japan/index.html](http://money.cnn.com/2018/01/29/technology/coincheck-cryptocurrency-exchange-hack-japan/index.html)。

^([2](#ch04.xhtml#ich04fn2)) Redman, Jamie. “Hackers Have Looted More Bitcoin Than Satoshi’s Entire Stash.” Bitcoin News, 24 Mar. 2019, [news.bitcoin.com/hackers-have-looted-more-bitcoin-than-satoshis-entire-stash/](http://news.bitcoin.com/hackers-have-looted-more-bitcoin-than-satoshis-entire-stash/)。

^([3](#ch04.xhtml#ich04fn3)) “Total Hash Rate (TH/s).” Blockchain.com, [www.blockchain.com/en/charts/hash-rate](http://www.blockchain.com/en/charts/hash-rate)。

^([4](#ch04.xhtml#ich04fn4)) McCarthy, Niall. “Bitcoin Devours More Electricity Than Switzerland \[Infographic\].” Forbes, Forbes Magazine, 8 July 2019, [www.forbes.com/sites/niallmccarthy/2019/07/08/bitcoin-devours-more-electricity-than-switzerland-infographic/#39b7e85521c0](http://www.forbes.com/sites/niallmccarthy/2019/07/08/bitcoin-devours-more-electricity-than-switzerland-infographic/#a5c02393e59c943d6a75a9241140faca339b7e85521c0)。

^([5](#ch04.xhtml#ich04fn5)) Sharma, Toshendra Kumar. “Can Blockchain Be Under Quantum Attacks ?” Blockchain Council Blockchaincouncilorg, 6 Dec. 2018, [www.blockchain-council.org/blockchain/can-blockchain-be-under-quantum-attacks/](http://www.blockchain-council.org/blockchain/can-blockchain-be-under-quantum-attacks/)。

^([6](#ch04.xhtml#ich04fn6)) Bouguera, Amira. “How Will Quantum Computing Affect Blockchain?” ConsenSys, Dec. 2018, [consensys.net/blog/blockchain-development/how-will-quantum-supremacy-affect-blockchain/](http://consensys.net/blog/blockchain-development/how-will-quantum-supremacy-affect-blockchain/)。

^([7](#ch04.xhtml#ich04fn7)) “CVE-2018-17144 Full Disclosure.” Bitcoin Core, 20 Sept. 2018, [bitcoincore.org/en/2018/09/20/notice/](http://bitcoincore.org/en/2018/09/20/notice/)。

^([8](#ch04.xhtml#ich04fn8)) Siegel, David. “Understanding The DAO Attack.” CoinDesk, CoinDesk, 27 June 2016, [www.coindesk.com/understanding-dao-hack-journalists](http://www.coindesk.com/understanding-dao-hack-journalists)。

| ![image](images/ch-5.jpg) | | **私有链与公有链** |
| --- | --- | --- |

比特币是第一条区块链上的一个应用。根据 CoinMarketCap 上市的数字资产数据，自 2009 年 1 月推出以来，已涌现出 3,000 多条公有链。随着人们对该技术的兴趣与日俱增，我们预计这一数字将持续增长。

所有区块链都具有相似的基本结构。它们是建立在点对点网络或独立计算机之上的平台，这些计算机协作实时维护共享账本。然而，每条区块链实施的协议至少与下一条略有不同。每条链都是为解决特定问题而设计的。例如，比特币区块链的主要关注点是支付，而以太坊区块链或多或少是一台虚拟机，可作为各种应用程序的后端。

话虽如此，区块链可以使用多种标准进行分类。本章将探讨其中之一：区块链因设计而异的运作方式。在这方面，区块链主要分为两种类型：每条区块链都可归类为公有链或私有链。

### 私有链与公有链：有何区别？
