
![](img/a35f8e852e0ee65e528c95ad0821783b_353_0.png)

图 1. 用于铸造 NFT 的前端。

在 MOTOKO 后端和 JavaScript 前端之间。前端可以如图 1 所示简单。用户只需点击文件选项上传 NFT 数据，这些数据可以是 jpg、jpeg、png 等格式。
一旦用户提供了 NFT 数据、类名并点击“铸造 NFT”按钮，就会调用 NFT actor 类，从而以程序化的方式创建 NFT。在后端创建的 NFT 将通过 NFT actor 类内部的函数显示给用户，该函数返回 NFT 数据。图 2 展示了铸造的 NFT。

![](img/a35f8e852e0ee65e528c95ad0821783b_353_1.png)

图 2. 铸造的 NFT。

NFT 电子商务网站的用例描述了其功能需求（图 3）。它包含两个参与者：用户（包括买家和卖家）。它涵盖了以下功能方面：

- 浏览 NFT
- 查看 NFT
- 铸造 NFT
- 出售 NFT

用例图中的参与者包括：
- 用户：包括买家和卖家。
- 简单合约（Simple Contracts）：由执行特定函数的程序容器（canisters）。该参与者作为用例：购买 NFT、浏览 NFT、查看 NFT、铸造 NFT 和出售 NFT 资产的主要参与者，并作为用例显示 NFT、支付、上传文件和出售价格的次要参与者。

![](img/a35f8e852e0ee65e528c95ad0821783b_354_0.png)

图 3. NFT 电子商务网站的用例。

## 6 结论

本文提供了创建 NFT 和所有者验证的算法，确保了增强的验证并提供了一种简单的 NFT 铸造方法。这可以无缝集成到 NFT 电子商务网站中，该网站提供了一个铸造、购买和出售 NFT 的单一平台。本文提出的算法首先创建一个 actor 类，该类是一个由多个 actor（包含 NFT 的容器容器）组成的父类，并为单个用户拥有的每个 NFT 创建了多个 actor。算法通过 actor 类的唯一 principal ID 提供所有者验证，并通过每个 NFT 的 token ID（不同 NFT 的 ID 不同）来确保 NFT 的唯一性。

## 参考文献

- [1] Karthika, V. and Jaganathan, S. (2019) 'A Quick Synopsis of Blockchain Technology', Int. J. Blockchains and Cryptocurrencies, Vol. 1, No. 1, pp. 5-66.
- [2] M. Dowling. (Apr. 29, 2021). 'Is Non-fungible Token Driven by Cryptocurrencies?' — Elsevier Enhanced Reader.
- [3] Casey Newton. (Jul. 22, 2021). 'Mark Zuckerberg is Betting Facebook's Future on the Metaverse — The Verge'
- [4] Peter Allen Clark. (Nov, 15, 2021). 'What is the Metaverse? Why it's Matters — Time

- [5] 'Non-fungible Token (NFT)'
- [6] 'ERC-721 Fungible Token', ethereum.org.
- [7] R. Conti. (Apr. 29, 2021). 'What You Need to Know About Non-fungible Tokens (NFTs),' Forbes Advisor. Section: Investing
- [8] J. Fairchild, 'Tokenized: The Law of Non-fungible Tokens and Digital Property', Social Science Research Network, Rochester, NY, SSRN Scholarly Paper ID 3821102, Apr. 6, 2021
- [9] (Jul. 22, 2021). ...
