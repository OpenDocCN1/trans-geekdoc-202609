
# 2019 第四届国际信息技术研究会议 (ICITR) (斯里兰卡莫拉图瓦 2019.12.10-2019.12.13)

包含数据库+区块链。`Stellar` 的优势在于与其他链相比，其交易费用非常低（等于 `0.0001 XLM`）[22]。对于 1 美元，一个人可以进行约 390,000 次交易。与其他链相比，高性能是一个主要优势。

`Stellar` 中没有挖矿费（`Gas`）。这意味着你不需要加入挖矿来赚取代币。它没有基于货币的货币。在网络创世之初，并没有使用千亿个 `Lumens`（光币）。通胀是创建新恒的唯一方式。`1%` 的通胀率用于覆盖用户的增长和流失。这些新的 `Lumens` 通过直接的投票方法创建并分发[25]。

在 `Stellar` 中，主要的缺点是它没有灵活的合约[22]。虽然它的合约是预定义的，并且在运行时，人们可以获得最多 `64` 字节的数据。`Stellar` 也将数据保存在数据库中，但存储在项（`entry`）中。由于其去中心化的特性，使用公链比使用这种研究人员选择的公共通信价格和去中心化元素更容易。

## V. 加密经济

加密经济是利用激励和密码学来设计新类型的系统、应用和网络[27]。特别是，加密经济创造了事物的产生，它更符合数学和经济经济学的关注。加密经济是应用了密码学并考虑了经济和激励理论的领域。`Bitcoin`、`Ethereum`、`NEO` 以及许多基于区块链的应用都是基于加密经济提供激励的。

在这项研究中，我们将加密经济作为一种用户机制，激励他们正确执行，并在他们表现不佳时进行惩罚。`Dblock` 系统有两个代币。这些被称为 `Stellar` 和 `Trustcoin`。`Trustcoin` 是现实世界事件或资产的表示。

第二种代币被称为 `Trustcoin`。这种 `Trustcoin` 等于该账户的价值。这种代币无法通过购买获得，也不能通过金钱获得。最初，所有医院都将有一个基础代币数量。每个医院的信任成本将为零币。信任成本将由提供它的设施决定。加入医院的医生将获得源自医院信任数的相应代币。员工也是如此。患者、用户、研究人员、助理和学生也将遵循相似的过程。研究人员还可以添加自己的代币，大学可以在其大学下赚取积分。

患者的信任成本由其个人资料的背书者创建。如果一个患者想去一个具有高价值和医生的医院，医院的信任价值也比患者高。为了获得该利润，必须由执行其使用的医生进行背书。然后一段时间后，患者将获得额外的信任币作为奖励。医院也想要获得更多信任币。此外，所有添加到该医院和医生的个人资料都将在其个人资料中增加信任价值。

一旦背书者发现数据不正确，他将提出挑战。如果经过权威的验证和批准，则医生将受到惩罚，患者将获得一些信任币作为奖励。部分医生信任币将从医院移除，剩余部分给患者以及添加到医生或医院的个人资料。

这将使医生和背书者在背书之前通过个人资料来做好工作。此外，它将减少虚假个人资料和糟糕的工作。从长期来看，系统将保持稳定并激励每个患者行为，因为他们正在花钱进行背书。如果他们操作不当，他们将失去资金，医院也将失去医生的信任水平，这将激励医生验证个人资料，否则他们将失去信任币。

这种信任成本将帮助研究人员仅为研究选择高水平的资料，并为研究质量提供激励。同时，共享患者可以检查研究人员的价值，然后根据此做出选择。

## VI. 人工神经网络

本项目中使用的人工神经网络用于根据患者数据识别医疗文本的价值。这里有许多不同的层用于分类。其中，`CNN`（卷积神经网络）天然适合分类任务[28]。使用了一个输入层、隐藏层和输出层进行分类。参数被用于输入层。每一层都有一个神经元。每个输入都已传输到一个神经元。权重与两个神经元之间的关系相关。当输入传递到神经元的另一层时，关系权重将对其进行乘法运算。在网络的初始阶段，使用随机函数来分配权重（`Wi`）以更新隐藏层和输出层的连接，领域人员搜索了现有的信任水平、位置、背书者和之前的接受率作为均值。通过这种 `ACO`（蚁群算法）方法，训练过程的参数——这些权重通过反传播算法更新。隐藏层和输出层使用了 `sigmoid` 函数。

```
$f(x) = \frac{1}{1+e^{-Tx}}$
```

`sigmoid` 激活函数用于转换从每个隐藏神经元传输出的值（`Wi`）。激活函数的目标是将输入转换为……（注：原文此处似乎有缺失，根据上下文为输出值）。激活函数的目的是将输入转换为……。隐藏层和输出层使用的 `sigmoid` 激活函数用于转换从每个隐藏神经元传输出的值（`Wi`）。激活函数的目的是将输入转换为……。训练过程中，反传播（`BP`）用于更新……的权重。

```
$E = \frac{1}{2} \sum(O_j - t_j)^2$
```

上述公式用于计算误差。`(O_j)` 指示了输出层的……（注：原文此处逻辑不完整）。用于更新……

```
$$\frac{\partial E}{\partial W_{jk}} = (O_k - t_k)(O_k)$$
```

上述公式用于计算输出层的梯度。`(O_k)` 指示了输出层的实际输出，`t_{jk}` 用于更新……的输出。

```
$$\delta_{jk} = \delta_j(1-O_j)W_{jk}$$
```

`(O_j)` 是上述的实际输出。上述公式：

```
$$\Delta W_{jk} = -\alpha\delta_{jk} + \alpha Uwt_{1}$$
```

上述公式在训练过程中每个记录通过流层后用于更新信息素权重。在训练开始时，每个信息素权重被定义为零，并根据个人资料进行更新。对于测试过程，存储了最终权重

## VII. 蚁群算法

最早的 `ACO` 算法由 `Marco Dorigo` 及其同事在 90 年代初开发。蚂蚁是昆虫。它们在群体中生活，其行为取决于族群的生存。人工 `ACO` 设计了蚂蚁寻找食物回到巢穴的方式，并根据食物的质量和数量释放信息素。浓度会有差异。

由于其巡逻的特性，`ACO` 用于寻找路径。但研究人员在研究中使用 `ACO` 来衡量人工记录的媒体资料，这些路径与其他路径相比具有人工信息素。如果用户个人资料选择高信息素路径，那么它比低信息素的路径更有可能是真实的。路径或无路径

`ACO` 公式在生成良好的记录并验证负数量时用于构建。结果将基于整个路径。有许多参数作为其关键资料，真发现的价值是控制整个数据流。研究通过 `ACO` 研究测量媒体资料并检查路径。如果正确路径出现，它将始终显示比虚假路径更短且权重较高的路径。

# $\Delta T_{ij} = \sum_{k=1}^{\infty} \Delta T_{ij}^k$

## VIII. 提出的设计

在本节中，研究人员详细解释了流程。在研究人员解释了数据存储机制、事务结构和账户之后，随后将介绍平台托管情况。

### A. 系统流程

流程从用户在旅馆下使用其账户开始。一旦链接，医院工作人员和医生就可以输入数据。此外，他们还可以输入患者。用户随后可以审核数据，一旦数据通过验证，他们就可以接受，这些数据将与他们的个人资料关联。如果平台拒绝了无效数据，它将不会在任何地方显示。

医生想要查看个人资料，患者可以接受或拒绝。对于研究人员，他们可以根据自己的信任级别请求数据，取决于他们是否想要出售自己的数据。如果他们接受，数据将与他们共享并可以返回给研究人员。否则，如果他们撤销请求期限，他们可以赚到钱，一些人的账户可以被退回。

### B. 存储机制

所有用户数据将使用输入用户的私钥进行加密。接受数据的患者也将使用私钥进行加密。只有加密后的数据会被存储在数据库中。而原始数据将存储在存储器。

数据库的选择可以定义为：此系统允许并支持中心化数据库、分布式数据库和去中心化数据库，如区块链大数据库（一种存储所有数据格式的区块链数据库）。该平台的设计使得此类数据类型是灵活的。

### C. 事务结构

每个用户插入其账户以及用户所创建的更改将激活并存储在该章节中。每个账户将作为一个单独分区存储，并与该账户执行的最后一次操作相关联。

这种链接将确保活动被记录，如果任何用户想要破坏它，将很难重建一条有效的链。每条链将存储元数据、原始数据和事务哈希作为主要信息进行存储，并由用户的私钥进行签名。

### D. 账户结构

对于每个用户，当他们签名时，新账户将同时包含公钥和私钥。用户将使用公钥进行分类，私钥将作为账户密码。私钥以加密格式存储。私钥使用用户密码存储。为了使系统更安全，该密码不会存储在任何地方。此外，用户身份将使用私钥加密，除用户之外的任何人无法访问。这将确保在共享数据时的匿名性。

此研究人员使用 `Stellar` 网络来创建账户，因为账户只能通过发送原始光币（`lumens`）来访问。每个账户将使用用于开发者开发的 `Stellar` 测试进行资金。一旦账户创建，该机制可以通过 `Stellar` 观察者转变为区块链的透明化。

### E. 托管

去中心化应用（`dApps`）是运行在 `P2P` 网络上的应用程序，自 `P2P` 网络出现以来一直可用。它们是设计为存在于互联网并管理实体控制的软件。

研究人员将其设计作为 `dApp` 运行。代码和数据将插入互联网。并且将没有单点故障。每个用户都在区块链上工作。研究人员选择了 `IPFS` 上的文件共享平台来托管此应用程序的前端，而后端可以在每台机器上执行。这种类型的托管将提供可靠性和隐私性，因为所有数据在作为服务器的前端机器上都经过加密。

采用开源许可证运行允许我们在不受版权限制的情况下开放进行创新。此外，完全开源的去中心化应用在开源软件的法律模型下运行。例如，我们使用 `MIT` 开源许可。

## IX. 实验与结果

研究人员使用了孕妇的医疗记录来证明该流程正按计划运行。计划呈现报告，因为它是医疗领域最敏感的区域。此研究收集的数据通过医院和卫生部（`MOH`）部门的 `B` 卡获得。`2021` 年的数据的预处理，研究人员在此项研究使用了 `15` 名患者的记录。

使用这些数据，研究人员测试了 `ANN`。我还测试了数据和账户模型视图。为了训练 `ANN`，研究人员对学习机制进行了实验。最后，在经过一系列实验后，研究人员选择了准确率较高的最佳组合。这里使用了 `8.0` 速率和 `0.2` 月。下面显示了每个算法的准确率。

| 算法 | 准确率 |
| :--- | :--- |
| `ACO` | `81%` |
| `ANN` | `70%` |

与其他研究和怀孕领域相比，这是一个很好的准确率，当有更多数据可用时可以进一步提高。此外，我们根据研究人员搜索的区块链评估了系统的性能和成本效益。该系统中存储在区块链上的每个事务需要 `3.5-26` 秒，每个账户至少需要 `5` 次传输才能运行。这花费为 `$0.6`，与现有的系统相比效率更高。

作为未来的研究增强，将使用集成技术和在医疗保健系统内共享加密信息的信任模型来提高模型的准确率。信任将提供更高的效率，并使医院和医生提供适当的护理，因为该过程是透明的，任何人都可以挑战。

## X. 结论

## XI. 参考文献

- [1] Mr. Roushan Jha, M. Sneha Dutta, S. Dongre, Jat. Luthak M. Department of Computer Science and Engineering G. H. Rao Department of Computer Science, roushan.jha@gmail.com Department of Computer Science Data Mining: A Review: Class Imbalance in Data Mining.
- [2] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [3] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [4] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [5] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [6] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [7] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [8] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [9] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [10] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [11] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [12] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [13] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [14] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [15] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [16] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [17] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [18] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [19] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [20] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [21] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [22] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [23] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [24] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
- [25] A critical review of class imbalance and its current applications, Tayee M. J. and K. K. Hong.
