# 2020 第25届国际复杂计算机系统工程会议 (ICECCS)(新加坡 2020.10.28-2020.10.31) 2020 第25届国际复杂计算机系统工程会议






Babu Pillai | Kamanashis Biswas | Zhè Hōu | Vallipuram Muthukumarasamy
babu.pillai@griffith.edu | kamanashis.biswas@acu.edu.au | z.how@griffith.edu | v.nuthu@griffith.edu

**摘要——**多区块架构取决于新协议的出现以实现跨链参与者之间的信任。然而，区块链之间的互操作性仍然是一个未解决的问题。缺乏基于桥接的系统，很难对跨链转移的安全性和正确性产生信任，从而在过程中嵌入信任。我们提出了一种销毁即提取跨链协议，用于在区块链之间安全地交换资产。我们的系统可以在资产从源链销毁并在目标链提取的任何地方工作。我们使用签名和时间锁等交易细节以分布式方式运行该协议。我们提供了一个分析，证明跨链转移能够正确转移资产。术语——区块链、互操作性、资产转移、跨链协议

利用 Hyperledger 和 Coral 等技术来充分发挥去中心化账本技术的潜力。

为了解决提出的问题，我们提出了一种集成到协议中的内置流程，用于执行交易并促进系统之间的互操作性。我们根据之前的工作 [13] 和销毁即提取跨链协议形式化了互操作性概念。将其定义为一个由两个部分组成的过程：退出交易（exitTransaction）和进入交易（entryTransaction），用于验证证明的有效性以重建资产。该流程的贡献有三个方面：

- **协议**：我们处理跨链资产转移，交易在去中心化且无信任的网络中执行。
- **工作流**：我们提出了一个灵活简单的工作流，可以适用于区块链之间的数字资产转移，无需理解区块链技术的关键特性。
- **分析**：我们进行了初步分析，证明了所提协议的正确性、安全公平性。

 I. 引言

区块链技术为交易处理提供了一种不可篡改、去中心化且透明的机制。除此之外，人们认为区块链系统能够在网络内转移价值的一个原因是是，当前区块链的架构限制了同一网络内的转移。然而，目前的架构无法利用多个网络或其保障的组合 [1]。出现这个问题的原因是跨链具有其自身的自主可扩展性问题 [5]，因此一个网络无法验证另一个网络中的信息。此外，两个区块链之间的无缝共识是困难的 [12]。跨链集成将实现不同、异构区块链之间的互操作性 [8]。根据目前的区块链协议，系统之间实现直接互操作性是困难的 [4]。系统内没有提供跨链价值转移的方法；因此，需要外部交易。然而，区块链系统无法识别和验证由第三方销毁的任何资产。本文讨论了企业区块链应用如何运行在私有链上

## A. 假设

所提协议做出了以下假设：

- 底层区块链网络是安全的，具有在时间内达成交易最终确定性的共识，所有交易均不可回滚 [2]
- 跨链通信过程中的参与者“信任”对方会满足要求的机制，并愿意在对方提供有效证明时处理交易。所需的信任水平取决于具体应用，并被用于
- 网络节点有动力参与两个区块链上相应的证明机制（挖矿）。
- 交易携带单个输出，对应单个资产，且网络识别并对它们正在转移的资产形成共同理解。

在这些假设下，一旦广播交易，区块网络将验证该交易并将其包含在区块中。区块链系统于通过协议进行同步，以产生新区块并向整个网络发布。在加密货币的情况下，这种行为是由奖励驱动的。我们假设存在激励机制来促进节点的参与。

 II. 销毁即提取协议

在本节中，我们正式定义了销毁即提取协议及其属性。本文使用的摘要可在 git 存储库中找到

### A. 网络间的通信

销毁即提取协议由两个部分组成：用于验证证明有效性以重建资产的退出交易（exitTransaction）和进入交易（entryTransaction）。

**定义 1（销毁地址）**：销毁地址 `毁eta` 是一个可以发送但无法提取的地址。

（注：原文此处存在大量重复的 "cross-chain transfers transfer assets correctly" 以及 "Burn-to-claim" 描述，翻译已根据指令保留逻辑结构并对应内容。）





# 算法 2 入口交易协议

```
1: function entryImport($Tx,Tx^i,K^B_{\beta},v,Tx,\Gamma,\sigma$)
2: if importVerifier($Tx,Tx^i,\sigma$) and
3:     ($Tx.time$ is under the limit) and
4:     decrypt($K^B_{\beta},H(\gamma)$) is true then
5:     $\beta \leftarrow K^B_{\beta}:v$
6:     $Tx \leftarrow (Tx,H(\gamma),\sigma)$
7: else
8:     invalid transaction
9: end if
10: return transaction receipt
11: end function
```

这些系统并不连接，它们拥有由协议和一些共同共识约束的足够信誉。例如，它们可以是共同利益的不同分支、公司的不同分支或组织中的不同部门。本文的目的是解决跨链操作问题，我们关注于如何验证交易的共识构建，以及交易有效的条件。

- 1) 网络假设。为了解决状态问题，我们对网络及其挖矿能力做了一些假设。我们假设链的密码学原语是安全的。这与 [5, 11] 中提出的假设相同。其中一个假设是发送者和接收者网络与全局时同步。

算法 2 中的函数 `entryImport` 定义了一个元组 $(Tx,K^i,K^B_{\beta},v,Tx,\Gamma)$ 作为输入，其中 $Tx$ 包含公钥 $K^i$、接收地址 $K^B_{\beta}$、销毁地址、值 $v$ 和交易 $Tx$；$\Gamma$ 代表加密的密钥，$\sigma$ 表示数字签名。

在我们的节点模型中，假设每个区块链都是一个自治系统，通过跨链协议相互通信。为了方便区块链之间的通信，依赖于能够识别和解决跨链问题的去中心化共识机制。这种去中心化集成机制充当跨链协议的验证方法。我们模型的架构可以被视为若干（基于拓扑）通过网关机制或网络网络连接的网络。

**定义 3 (importVerifier)。** importVerifier 由两个函数 `importVerifier` 和 `proofVerifier` 组成，如果两个子函数都返回 true，则返回 true，否则返回 false。

- importVerifier：如果从 $K^B_{\beta}$ 的销毁地址返回 true 且 `getAddress($Tx$)` 返回 $K^B_{\beta}$（假设网络使用源链的 getAddress 函数），则返回 true；否则返回 false。
- proofVerifier：如果 $Tx$ 生成自 $K^B_{\beta}$，且 balance($beta$) = $Tx,Tx^i$ 处于有效状态，则返回 true；否则返回 false。

会有多个节点作为网络的网关；它们将相互竞争奖励。我们假设并非所有节点都会验证交易，但有足够节点将确保交易的安全。每个节点将根据我们信任的网关的信誉接受提的证明。我们将去中心化集成机制的细节留给未来的工作。

`proofVerifier` 实际上是 `assetVerifier` 的版本。来自源网络的证明需要验证。我们假设通过网关机制，目标节点能够验证该证明。通过 $Tx$，网关节点可以访问源网络中的公共交易。当 `importVerifier` 返回 true 时，节点需要检查时间锁和密钥。我们假设时间锁周期和密钥都与嵌入交易的哈希值匹配，即发送到接收者 $K^B_{\beta}$ 的资产。

我们设定了一个例子：区块链网络 $N_1$ 中的 Alice（发送者）想要向区块链网络 $N_2$ 中的 Bob（接收者）转移资产。Alice 向网络 $N_1$ 提交一个 `entryTransaction`。网络 $N_1$ 执行交易，向 Alice 返回收据。网络 $N_1$ 将资产返回给 Bob 的销毁证明。网络 $N_2$ 验证该证明，如果成功，则将资产分配给 Bob。

## B. 协议工作流
本节介绍了使用两个自给安全的区块链的销毁-认领协议的工作流。这两个网络运行不同的应用程序，但它们需要操作。它们可能采用不同协议的参与者。假设两个网络中的大多数参与者都是诚实的。这里的假设是即使

- 3) 准备阶段：在准备阶段，Alice 通过交换机制交换密钥。我们使用 Bob 的公钥加密密钥 ($\gamma$) 并与 $i$ 共享加密密钥 ($\Gamma'$)。然后，他们必须等待时间锁周期 $t$。之后，Alice ($S$) 生成了销毁 ($\beta$)。我们详细描述这些步骤。

为了花费 Alice 的值，她需要证明生成地址的公钥的所有权。

![img/d47811a3daf8f2b85d6c009253_0.png](img/d47811a3daf8f2b85d6c009253_0.png)

## 4. 提交阶段：在提交阶段，S 创建并广播一个 exitTransaction 以调用网络 N1 中的算法 2

# 算法 3 出口交易时间锁代码

```
1: while (time-lock is true)
2: if (R claim v) then
3: reveal secret v to N2
4: N1,miner gets v from N2
5: N1,miner claims his-locked v
6: end
7: end (while after the (t_{lock}))
8: if (R failed to claim v) then
9: S reveals $\gamma$ to N1
10: S re-claim v
11: N1,miner claims his-locked v
12: end
13: reveal \gamma$ is known to N2
14: end
```

算法 3 显示了交易条件。这里是在认领交易后（包括资产和矿工）必须公开密钥。因此，交易将由访问交易网络数据的矿工维护。

时间锁机制显然允许同一时间只有一个一方可以认领资产。例如，当



Tx 在源网络中被时间锁定，如果 R 在其网络中揭露秘密代码 $\gamma$，则在源网络中挖掘此交易的矿工将在源网络中公开它以提取其手续费；此时 $\gamma$ 对两个网络都是已知的。之后，S 将无法提取该资产。同样，如果 R 未能在规定时间内提取资产，随后随后在源网络中揭露 $\gamma$ 已过期以取回资产。或者设计的 $\gamma$ 未被网络所知晓；因此，新公开的 $\gamma$ 将在 $t_{lock}$ 到期后能够提取该资产。

## 算法 4 reclaim-transaction-protocol

- 1: function reclaimTransaction(Tx($K^S_{adr},K^R_{adr},v,Tx)$, $\gamma$)
2: if reclaimVerifier() is true
3: ($Tx^{t_{lock}}$ pass the time limit) and
4: decrypt($K^S,H(\gamma$)) is true) then
5: return $K^R_{adr} : v$
6: else
7: invalid transaction
8: end
9: return transaction receipt
10: end function

**5) 执行：** 该阶段有两种可能：要么 R 在传输时间期内提取资产，要么 S 在时间期结束后提取资产。

a) R 提取资产：R 构建一个入站交易（entry-transaction）并广播到 $N_2$。如果 R 能证明 $K^R$ 的所有权，矿工将能够处理它。然而，该协议需要可靠的证据证明 S 已在源网络上销毁了资产。在这里，R 提供了一个销毁证明 $\beta$ 和一个之前的交易 $Tx'$，这构成了在源链上的提取证明。

`reclaimVerifier` 函数包含两个子函数 `spendVerifier` 和 `proofVerifier`。`verify($Tx,K^S$，$\gamma$)` 返回 true，$getAddress($K^R_{adr}$)` 返回 true。然后 `proofVerifier` 检查 $Tx'$ 的证明，验证 balance($beta$) = burn true 且 $B$ 在 $E$ 中返回 false。为了清晰起见，`reclaimTransaction` 可以包含在 `entryTransaction`，我们展示一个独立的交易。

## III. 分析

我们的协议需要一个节点能够挖掘区块链的过程。借此，$m$ 个网关中的 $n$ 个节点提出此交易，最终其中一个提案被网络接受。然后，这些网关能够通过 $Tx'$ 验证交易。节点验证销毁操作发生在源链上，且该交易包含在区块中。这可以通过检查区块链的链有效性 [7] 来完成。

在本节中

如果 `notVerifier` 将网络资产返回给接收者 $K^R_{adr}$，这意味着秘密代码 $\gamma$ 对她是已知的，之后，源网络矿工将将其带到源链以提取其手续费。

需要注意的是，我们协议中的销毁（burn-in）不是由普通密钥生成的，而是每次通过组合接收者地址和其他参数生成的唯一密钥。这在当前网络中是不可能执行的。然而，通过 $\gamma$ 的签名及其出现，在提议方案中销毁的资产将保持未被花费状态。

b) S 提取资产：在接收者在时间锁定期内没有资产的情况下，发送者收到网络或执行 $Tx$ 的矿工的通知，然后发送者调用 `reclaim`，这是 `entryTransaction` 的一部分并将资产包含回。交易首先检查签名以验证 `verify($Tx,K^S$，$\gamma$)`；然后检查时间锁定和秘密代码哈希。正如之前所述，我们的协议需要某些矿工在两条链上进行挖掘。那么，我们假设矿工在此交易之前能够与网络 $N_2$ 进行检查。

引理 1 (不可花费)。对于区块链协议 [11]，销毁证明 $\beta$ 是未花费的。

`entryTransaction` 的功能是在资产在源链上销毁后提取资产。在我们的协议中，资产必须在提交阶段永久销毁。通过销毁协议及其不可花费属性，在提取源链资产之前已被永久销毁。

引理 2 (销毁提取)。从 $N_1$ 传输到 $N_2$ 的资产 $v$ 在用户可以在 $N_2$ 提取它之前，必须在 $N_1$ 中销毁。

发起退出交易的发送者必须确保正在被销毁。在 `exitTransaction` 中，`exportVerifier` 确保了交易的有效性和所有者的花费能力。这必须由网络执行。因此，只要网络是安全的，参与者只能进行交换。

# 参考文献

[1] Ghasam O Haramane, Ili Arroumani, and Sardarjan Kapoor. Double-spending payments in bitcoin. Proceedings of the 2012 ACM conference on Computer Security.

[2] Itay Elal, Adam Ef, and Sergio Gen. Atomic Swaps. PhD thesis, 2019.

[3] Pascal Lasecurade and Leonard-Mirinot. On blockchain interoperability. Information Processing Letters, 105976, 2020.

[4] Michael McDonald, Christopher Reiter, and Stefan Schulz. A scalable cross-chain protocol. International Conference, 45–59, 2018.

[6] Jianxi, Daniel Li, and Shloym Levin. A scalable method to a network of networks. National Science Review, 12(3):336–346, 2018.

[7] Kostis Karantis, Angelos Kiyas, and Diminos Zhou. Proof-of-Burn Blockchain. International Conference on Cryptography and Data Security, 2019.

[8] Angelos Kiyas, Alexander Russell, Bernard David, and Roman Oynoyrov: A scalable cross-chain blockchain protocol. International Cryptographic Conference, 355–388, 2017.

[11] Babu Pili, Kamalishi Biswas, and Vallipururam Mukhamkaram. Cross-chain interoperability among blockchain-based systems using transactions. Knowledge Engineering, 35, 2020.

[14] Lain Stewart. Proof of burn - bitcoin. Available at: https://bitcoin.com/wiki/Proof_of_burn, Dec 2012.

# IV. 结论 在本文中，我们分析了区块链交易协议并提出了解决互操作性问题的新功能。我们方法的关键特征之一是了一个价值/资产交换的内部函数。内部协议使用通用语言，通过这种协议，用户可以直接通信并使用标准路径传输各种形式的数据。我们简要证明了销毁提取（Burn-to-Claim）协议通过其正确性和公平性能够抵御双花费。
