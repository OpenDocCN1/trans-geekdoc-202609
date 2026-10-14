
Dept. Computer & Information Sciences, London, UK

`h.jahankhani@northumbria.ac.uk`

## ABSTRACT

确保任何调查中的证据连续性是有问题的，尤其是在多个机构参与时。确保与证据被没收相关的文件一致性是困难的，并且常常会在法庭上受到审查。本原型区块链的开发是为了在调查期间记录证据的转移，旨在提供证据连续性的保证。本文的区块链实现使用了 `Hyperledger`，并在本文中被称为证据链的区块链 (`BoC`)。本文通过进行两个简单的模拟调查并对其进行评估来测试 `BoC`。评估内容包括查询证据、访问控制、开发、安全性和审计。本文认为 `BoC` 的实现是成功的，并讨论了未来改进、缺点和优势。

*Keywords*: `Bitcoin`, `HyperLedger`, `blockchain`, `chain of custody`, `timestamp`, `legal assurance`

### 10.1. Introduction

近年来，关于分散式应用 (`DApps`) 和区块链的炒作已经使研究人员偏离了理性思考，使他们只考虑新的发展。技术是在推动变革，还是变革在推动技术？本文抓住了机会，研究区块链技术如何用于证据的没收和转移，或者说区块链保管链是如何工作的。本提案考虑了开发、实施、好处、问题以及对一般法医学的影响。

当前证据保管链的完成方式存在许多问题。特别是，关于防止篡改 (`ISO`, 2017 (Section 7.11)) 这一问题。证据保管链自动化软件几乎是认证实验室的标准，`ISO` (2017, 2013) 也推荐使用。然而，在将证据转移给第三方时，还有改进空间，以确保保管链是不可篡改且不可逆转的。这也是本文的主要动机，即研究区块链软件开发生命周期以促进保管链程序。

证据链的区块链 (`BoC`) 是一个去中心化应用，提供证据收集后任何事件的保管链不可篡改且不可逆转的记录。它不打算取代提供行业标准和结构的证据管理软件，例如 `Foreman` (`Lowman`, 2018)，该软件用于生成报告和管理人员和设施。相反，`BoC` 旨在与这些软件协同工作，提升与证据相关的材料在保管链方面的能力、价值和质量。

### 10.2. Background

- 虽然许多人赞赏比特币（`B`）对加密货币的价值，但比特币对软件工程最大的贡献是去中心化应用或区块链。比特币（`Nakamoto`, 2008; `Antonopoulos`, 2017）与区块链密不可分；没有区块链技术，比特币无法运行。区块链和共识工程是比特币的副产品。区块链具有透明、公开、不可篡改、不可逆转、安全、异步、自调节和国际化等特点。简言之，比特币用户拥有一个钱包，可以通过公钥基础设施（`PKI`）加密安全地向其他钱包发起交易；这一过程由分布式账本（即区块链）来促成。区块链存储在网络的多个节点上，每个节点都存储钱包之间的所有交易。每笔交易的确认由节点完成，节点会检查交易的有效性，然后将其验证给网络中的其他节点。比特币（`BoC`）与比特币的相似之如下：

—交易：比特币中的交易表示两方之间资金的转移。一旦交易被验证，它会被添加到区块链中。`BoC` 的交易记录的是 artefact 之间的转移，且区块链可以轻松修改以容纳此类交易，参见 `Greenspan` (2015)。

—不可否认性：比特币交易验证的动机是确认花费方拥有资金且无双重支出。核心动机在于财务准确性。`BoC` 交易验证的动机是确保链条保管的完整性。

—长期性：比特币账本中的交易在比特币存续期间均保存。`BoC` 链条保管的所有交易同样持续至 `BoC` 存续期间，远超案件信息保存所需时间。由于数据无法删除，个人数据在 `BoC` 中存储引发一定担忧。

—隐私性：比特币公开，账本可被参与者和非参与者查看。`BoC` 则是私有区块链（`Greenspan`, 2015），通常称为许可区块链，仅允许授权访问。

—数据：比特币交易包含用户、转账金额、时间戳及其他元数据。`BoC` 交易则通常包含接收方、提交方、管理方、证据 ID、调查 ID 及时间戳。

—延迟：比特币区块链验证的延迟可能长达 10 分钟，这对 `BoC` 应用来说过长。延迟可缩短至 10-20 秒，在私有区块链上可接受，参见 `Greenspan` (2015) 和 `Hyperledger Architecture Working Group` (2017)。

—激励机制：运行比特币节点的激励是获得一定价值的回报，通常以数字加密货币形式呈现。`BoC` 中不存在此类奖励，但监管机构（如 `FSR`，Forensic Science Regulator, 2017）和认证实验室通常会有激励。若设为国家级激励，节点将由监管机构独立运行。这提供了私有透明性，并能查看每个证据项的链条保管情况。

—去中介化（`Gaur et al.`, 2018）：许多企业和组织依赖中介机构，例如企业依赖银行完成交易，需要信任中介方。比特币通过共识工程解决此问题，从而消除对中介的依赖。`BoC` 也能受益于去中介化，即不依赖监管机构或审计机构。然而，与比特币系统中缺乏如银行等监管机构不同，监管机构会被整合进 `BoC` 系统。

总之，`BoC` 是一个在更新后不可变且不可逆的系统。该系统基于区块链技术，而区块链技术源自比特币技术。其核心贡献在于确保链条保管的不可变和不可逆，从而显著提升所有被扣押证据（包括实物和数字）的完整性，进而改善证据管理的整体质量。

### 10.3. Blockchain of Custody, BoC

`Evidential Continuity` 是证据管理的一部分，并包含在 `ISO17025`（`ISO`, 2017（第 7.11 条））中。这意味着要成为 `ISO17025` 认证的法医实验室，必须（除其他要求外）拥有一个安全的信息系统，该系统需记录、删除、报告失败、确保数据完整性并提供适当的授权访问。`ISO17025` 合规性是所有处理证据的法医实验室的议题，并允许对证据连续性进行透明审计。这些通常仅在法院披露或审计后进行审查。在设计和实施 `BoC` 时，以下因素被考虑。

#### 10.3.1. Scope

该证据管理系统的范围涉及所有利益相关方，但系统仅记录证据在提交方与接收方之间的转移。详细信息将包括提交方、接收方、调查 ID 和 artefact ID 的无歧义唯一标识符。业务模式涉及以下利益相关方：

**执法机构：** 警察；法医实验室；军队；安全部机构；内部质量保障机制；国家安全机构；专家证人，以及其他政府机构。

**法律代表：** 检察官；辩护；Para-Legals；内部质量保障机制；内部调解辅助人员，以及其他与法律相关的代表。

**审计机构：** 法医科学监管机构；独立警察监督机构；法律保障机构，以及其他与执法和法律相关的外部机构。

#### 10.3.2. Transactions

数据库管理系统（`DBMS`）的事务用于将数据库从一种一致状态转换到另一种一致状态。部分事务不可发生，且事务必须提交。事务日志常用于备份实例或故障恢复。事务必须通过 `ACID` 属性：原子性、一致性、隔离性和持久性（`Haerder and Reuter`, 1983）进行验证。多年后出现了 `OLTP` 和 `OLAP`，它们如今主导组织的数据仓库和数据挖掘活动。`Brewer` (2000) 也指出了这些问题，且大型数据库无法同时满足这三点。自 2000 年以来，大量研究已开展，`Brewer` (2017) 进一步阐述了技术进步。

区块链和分布式账本的事务定义为记录交易输入、交易输出以及消费金额。事务会改变区块链中的数据。然而，关于区块链如何应用一致性，知之甚少。虽然在特定情况下区块链是去中心化的，但它可以通过验证（`Verdian et al.`, 2018）通过 `ACID` 测试。这对 `BoC` 这类应用至关重要，因为一致性是其必要条件。

#### 10.3.3. No Wi-Fi, no reception

没有 `Wi-Fi` 的地区在犯罪现场很常见，例如地下。公开网络的隐私问题也通过提交数据的加密得以解决。在没有 `Wi-Fi` 访问的情况下，传统的取证和纸质文件仍然足够，并伴随证据直至到达有指定 `Wi-Fi` 的地点并更新区块链。这与当前操作类似，在网络不可用时禁止联网。

#### 10.3.4. Incentives

The biggest implementation of blockchain is `Bitcoin` (`Nakamoto`, 2008). It is permissionless and secure; however, there are weaknesses. `Sompolinsky and Zohar` (2018) have discussed the arms race for `proof-of-work`, the updating of the blockchain and the rewards received. Such incentives yield an uneven playing field created by nodes investing heavily in `ASIC` hardware to complete `proof-of-work` and can lead to centralisation. As pointed out by `Sompolinsky and Zohar`, this will even out when the reward for block creation is withdrawn, and the focus is on transaction rewards. This does not affect permissioned blockchains, whereby control can be exerted over the network through consensus engineering. In permissioned blockchain applications where there are no tokens or coins, this is not a threat since there are no incentives for block creation and no reward for transactions.

#### 10.3.5. Permissioned blockchain

The idea and advantages of permissioned blockchain (aka private blockchain) are discussed in `Greenspan` (2015). Permissioned blockchain (aka public blockchain) only allows authorised access, in other words, it is not permissionless. For `BoC`, permissioned blockchain is advantageous for the following reasons:

—It allows one to maintain control over transactions and how they are completed.

—The blockchain is only accessible by approved, trained and certified personnel.

—The blockchain has low latency. Permissionless blockchains, e.g., `Bitcoin`, have some latency between the timestamp of the transaction and the creation of the blockchain. This is to prevent node domination and is the result of the consensus algorithm, `proof-of-work`. With a permissioned blockchain, one can have control over the nodes, so competitive consensus algorithms are not required. Whilst consensus is required, the ability of a member of the blockchain to engage in node domination can be controlled.

—The members of the blockchain can be vetted. Vetting is an important process that is difficult in permissionless blockchains since anyone can join. In permissioned blockchain, members can be vetted and the issuance of keys can be controlled and managed.

#### 10.3.6. Tokens

Blockchain is often incorrectly used synonymously with `Bitcoin` and therefore it is assumed that upon a transaction made on the blockchain an exchange of coins, or tokens, is required. Blockchain development can be completed without tokens; the question is, does the `BoC` application require them? Having a clear breakdown is not only important for designers and programmers, but also important for training purposes and ensuring that users follow procedures for updating the blockchain.

Typically, tokens are used in decentralised applications to prevent `DoS` attacks on nodes from disgruntled employees who have permissions to update multiple times. This could also apply to device breach, but this is unlikely since this would normally be reported and addresses associated with the device blocked. Tokens provide an additional level of security; however, the issuance of tokens would have to be centralised and updated accordingly. Re-distribution, re-use and the possible disposal of tokens is a concern, e.g. evidence store managers will have a surplus of tokens, whereas `FRT` members will have less, see Fig. 3.6. In order to perform a transaction, one would have to have a token of the minimum/smallest value. The value of the tokens can be controlled at issuance.

![image](img/fig10.1.jpg)

**Fig. 10.1.**Uneven token distribution: Where the evidence life-cycle ends, due to disposal or returns, there is an accumulation of tokens, represented by highlighted nodes in red.
