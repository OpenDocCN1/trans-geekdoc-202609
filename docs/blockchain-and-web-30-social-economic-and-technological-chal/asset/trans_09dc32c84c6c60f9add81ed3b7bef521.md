
标准JSON对象被使用。除此之外，IPFS显然还有很长的路要走，才能让去中心化应用（DApp）成为主流。首先，它存在存储非常大文件的日益严重的问题，正如DFiles所展示的那样。如果需要加密，那么可能的最大文件大小要低得多。已证明，由于硬件限制以及以太坊和IPFS的当前状态，加密仅适用于小型到中型文件。以太坊、IPFS和数据保护技术将在未来发生重大演变，这理论上将允许更好的加密技术或其他隐私技术，从而为未来需要数据隐私和保护的去中心化应用（DApp）带来希望。

如前所述，DFiles旨在展示通过加密个人数据是否可以实现GDPR合规。然而，这种方法还存在其他问题，例如曾经被证明高度安全的弱加密算法。这些算法的示例包括MD5和SHA1（The Open Web Application Security Project (OWASP), 2018）。出于这个原因，最流行的区块链中使用的算法有可能在短时间内变得过时——在此期间数据可以轻松被解密——然后再被另一个更安全的算法取代。

除此之外，量子计算很快可能成为现实，在相当长一段时间内，大多数区块链（如以太坊）中加密的所有数据，以及通过DFiles去中心化应用（DApp）在IPFS中存储的所有加密文件都可能被轻松解密。这是作者们认为的，在不久的将来对区块链技术的最大威胁。

关于DFiles的未来工作，与其使用本地IPFS节点，不如使用Infura节点。这带来了几个优势，因为硬件限制被最小化，但也带来了一系列新问题，例如存储在Infura IPFS节点中的文件没有长期保留的动力。

需要改进的另一个方面是将DFiles智能合约部署到Rinkeby之类的测试网络，并更新DFiles去中心化应用（DApp）以使用此部署的智能合约，而不是本地Ganache私有以太坊区块链。早期部署已完成，但还需要进一步测试。该智能合约可在Rinkeby测试网络上使用。

简而言之，本节讨论了IPFS和以太坊的局限性，包括DFiles的未来工作。然而，可以得出一些一般性结论：

- IPFS文件加密仍处于起步阶段；因此，存在重大的硬件和技术限制，阻碍其大规模采用。
- 以太坊是一个公共账本，因此提供的隐私很少或没有。唯一可能的方法是使用IPFS等其他去中心化技术对数据进行加密。以太坊也有大量的限制——例如不支持JSON，以及由于高昂的总交易成本而不鼓励某些计算循环指令（例如for、while）——这些限制影响了其全球采用。
- 出于GDPR合规目的加密个人数据受到严重限制，甚至可能被不鼓励。IPFS和以太坊都应被视为GDPR的特例，以避免数据加密方面的问题。

## 结论

在本章中，首先介绍了最重要的GDPR概念，以及处理个人数据的几种合法依据和几种个人权利。其“被删除权”干扰了区块链的不可篡改性。在此基础上，讨论了三个场景，涉及该权利是否可以遵守，随后介绍了一份适用于以太坊去中心化应用（DApp）的GDPR合规指南。

为了测试此指南，开发了一个案例研究：DFiles。它是一个使用以太坊和IPFS等中心化与去中心化技术混合构建的以太坊去中心化应用（DApp）。其主要目标是了解以太坊（Homestead）去中心化应用（DApp）是否可以遵守此法规，以及通过加密保护个人数据是否可行。

DFiles还通过遵循软件开发生命周期（尽管已针对去中心化应用（DApp）进行了调整），坚持区块链软件工程的原则。其核心智能合约也得到了解释，从实现的设计模式到主要数据结构和功能，此外还简要介绍了其核心功能。简而言之，DFiles允许用户上传和查看其提交的文件。

随后进行了一项统计分析，以验证遵守“被删除权”的加密可行性，但由于硬件限制，仅针对部分文件进行了分析。创建了两个去中心化应用（DApp）变体：一个带有文件加密，一个不带有文件加密。上传的文件被分为四个类别：小型（1 KB–1 MB）、中型（1 MB–20 MB）、大型（20 MB–200 MB）和超大型（200 MB–2 GB）。

随后在两个版本中测量了以太币的总交易成本以及用户点击上传按钮到文件上传完成之间的总耗时。随后介绍了其结论。简而言之，遵守GDPR及其“被删除权”仅对最大14.2 MB的加密文件可行。

最后，解释了案例研究的局限性及其未来工作。

## 注释

- 1 访问自 https://bitbucket.org/duarte_1110199/dfiles-ethereum-dapp/src/master/.
- 2 访问自 https://trufflesframework.com/.
- 3 访问自 https://github.com/ethereum/wiki/wiki/JavaScript-API.
- 4 访问自 https://github.com/OpenZeppelin/openzeppelin-solidity
- 5 https://bitbucket.org/duarte_1110199/dfiles-ethereum-dapp/src/master/contracts/Files.sol.
- 6 访问自 https://trufflesframework.com/docs/truffle/testing/writing-tests-in-javascript.
- 7. 访问自 https://github.com/brix/crypto-js.
- 8. 访问自 https://bitbucket.org/duarte_1110199/dfiles-r-statistical-data/src/master/.
- 9. 访问自 https://infura.io/.
- 10. 访问自 https://rinkeby.etherscan.io/address/0x09C5b627354eF29c3B6507aABa7386Ce240fFf9C.

## 参考文献

- Bitcoin 项目。(2018)。Bitcoin – 开源点对点货币。检索自 https://bitcoin.org/en/
- Consensys。(2018a)。Ganache。检索自 https://truffleframework.com/docs/ganache/overview
- Consensys。(2018b)。Metamask。检索自 http://metamask.io/
- Destefanis, G., Marchesi, M., Ortu, M., Tonelli, R., Bracciali, A., and Hierons, R. 2018。智能合约漏洞：区块链软件工程的号召？面向区块链的软件工程（IWBOSE），国际研讨会。坎波巴索：IEEE。
- 以太坊基金会。(2014)。Solidity，面向合约的编程语言。检索自 https://github.com/ethereum/solidity
- 以太坊基金会。(2016)。账户类型、Gas和交易。检索自 www.ethdocs.org/en/latest/contracts-and-transactions/account-types-gas-and-transactions.html
- 以太坊基金会。(2018)。以太坊区块链应用平台。检索自 www.ethereum.org/
- EU GDPR Compliant。(2018)。什么是数据主体？检索自 https://eugdprcompliant.com/what-is-data-subject/
- 欧洲数据保护监督官。(2018)。一般数据保护条例的历史。检索自 https://edps.europa.eu/data-protection/data-protection/legislation/history-general-data-protection-regulation_en
- 欧盟。(2016)。欧洲议会和理事会2016年4月27日关于保护自然人关于处理个人数据和此类数据自由流通的第(EU) 2016/679号条例。欧洲联盟官方公报，1–88。
- Falkon, S. (2017年12月24日)。DAO的故事——其历史和后果。检索自 https://medium.com/swlh/the-story-of-the-dao-its-history-and-consequences-71e6a84a551ee
- ICO。(2018年8月2日)。一般数据保护条例（GDPR）指南。检索自 https://ico.org.uk/media/for-organisations/guide-to-the-general-data-protection-regulation-gdpr-1-0.pdf
- Parity Technologies。(2017年7月20日)。多签名攻击：事后分析。检索自 https://paritytech.io/the-multi-sig-hack-a-postmortem/
- Petrov, S. (2017年11月7日)。另一次Parity钱包攻击的解释。检索自 https://medium.com/@Pr0Ger/another-parity-wallet-hack-explained-847ca46a2e1c
- Protocol Labs。(2018)。IPFS是分布式网络。检索自 https://ipfs.io/
- Szabo, N. (1996)。智能合约：数字市场的构建模块。检索自 www.fon.hum.uva.nl/rob/Courses/InformationInSpeech/CDROM/Literature/LOTwinterschool2006/szabo.best.vwh.net/smart_contracts_2.html
