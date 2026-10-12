
# 动态工具 MAIAN

动态工具 `MAIAN` 考虑智能合约的执行轨迹，即在区块链上运行合约时记录的序列。`MAIAN` 还结合漏洞类别考虑执行轨迹。每次交易都会请求智能合约运行一个函数，从而导致针对给定输入的执行路径被利用。因此，执行轨迹可能具有连锁效应。因此，为在智能合约的指定执行轨迹上查找漏洞利用，`MAIAN` 工具使用系统化技术。`MAIAN` 由两大主要组件组成，即符号分析和具体验证。符号分析组件的输入为合约字节码、分析规范及漏洞类别。`MAIAN` 持续执行直到到达具有漏洞属性集的不确定轨迹。所有执行均在 `EVM` 上进行，这将简化智能合约字节码的符号执行。每条执行轨迹均以符号变量作为输入，以便符号分析组件在合约暴露出漏洞时返回给定符号变量的具体值。具体验证的作用是验证符号分析的结果，并确认在智能合约中发现的 Bug 的准确性。分析期间，`MAIAN` 不会影响主以太坊区块链上合约的状态 [8]。该工具自 2018 年 3 月起已在 GitHub 上以 MIT 许可证提供 [21]。

## ContractLarva

该工具用于智能合约的运行时验证。用户可使用动态事件自动机 (`DEA`) —— `ContractLarva` 使用的一种规范语言 —— 来证明给定智能合约的属性。该工具通过接收给定合约的规范作为输入来生成一个新的 `Solidity` 合约。新合约的功能与原始合约相同，但向合约中添加了代码以检查运行时验证，并在观察到任何违规时做出相应反应。尽管 `ContractLarva` 已在许多智能合约上实现以部署运行时验证和恢复，但它面临许多需要解决的挑战 [27]。该工具可在 GitHub 上以 Apache-2.0 许可证获取 [21]。

# 基于漏洞的扫描工具

## Mythril

一款用于分析智能合约的自动化工具。分析基于字节码。它使用污点分析和控制流分析来查找漏洞。`Mythril` 使用命令行作为界面 [22]。通过该工具发现的漏洞均有详细记录和文档说明。`ConsenSys` 于 2017 年 9 月在 GitHub 上开发并维护 `Mythril`，采用 MIT 许可证 [21]。

## Securify

另一款基于用户界面的自动化安全分析工具，用于基于字节码的以太坊智能合约，可检测重入、输入验证等漏洞 [22]。如果检测到某种模式，该工具可提供额外保证，即合约代码具备相应的安全属性。该工具采用 `Java` 编写，自 2018 年起已在 GitHub 上以 Apache 2.0 许可证提供 [21]。

## SmartCheck

一款开源、基于用户界面的自动化工具，可运行 `Solidity` 源代码并检查漏洞及其他安全问题 [22]。`SmartCheck` 将代码转换为可扩展标记语言 (`XML`) 语法，并将漏洞指定为 `XQuery` 路径表达式，用于在 `XML` 树中搜索模式。该工具的最新版本为闭源，其漏洞检查模式数量是之前的两倍。该工具采用 `Java` 编写，可通过 `SmartCheck` 公司网站访问 [21]。

# 符号执行工具

## DART

符号执行领域较早的工具之一，能够通过动态分析执行随机测试，以查找由库函数引起的 Bug。`DART` 使用单路径测试输入（不采用路径选择机制）来检查违规、断言、崩溃和非终止等标准错误 [20]。该工具在 GitHub 上公开可用。`DART` 软件开发工具包包含 VM、`dart2js`、核心库等。

## Manticore

一种能够发现组合路径的符号执行工具。

`Manticore` 将 `Solidity` 代码编译为字节码，以分析漏洞的执行轨迹并在源代码中报告它们。**Trail of Bits** 公司开发了该工具以使用 `Python API`。自 2017 年起，该工具在 GitHub 上以 AGPL-3.0 许可证公开可用 [21]。

## Oyente

一种用作参考点并用于各种项目的工具。它以符号方式执行字节码，并检查多次执行的合约的执行轨迹。使用 `Oyente` 需要一个 `Solidity` 编译器来获取字节码。`Oyente` 是一个用 `Python` 编程语言编写的命令行工具。自 2016 年起，该工具在 GitHub 上以 GPL-3.0 许可证公开可用 [21]。

### 表 14.2：工具及其目的和分析方法调查

| 工具 | 目的 | 分析方法 |
| :--- | :--- | :--- |
| | 安全问题 | 攻击利用 | 动态分析 | 人工分析 | 符号执行 | 漏洞扫描 | 控制流分析 | 污点分析 |
| ContractLarva | | | | | **X** | | | |
| MAIAN | **X** | **X** | **X** | | **X** | | | |
| DART | **X** | | | | **X** | | | |
| Manticore | **X** | | | | **X** | | | |
| Oyente | **X** | | | | **X** | | | |
| Mythril | **X** | **X** | | | | | **X** | |
| Securify | **X** | | | | | | **X** | |
| SmartCheck | **X** | | | | | **X** | | |
| McCabe IQ | **X** | | | | | | | **X** |
| EVM | | | | **X** | | | | **X** |
| TAJ | | | **X** | | | | | **X** |
| Dytan | **X** | | | | | **X** | **X** | **X** |

# 总结与结论

随着数字货币、区块链技术和智能合约持续获得关注，需要一种系统以公众可查看和访问的形式对可能的漏洞进行分类。本章提供了大量实证事实，以帮助智能合约开发人员、安全研究人员和安全审计员更好地理解智能合约漏洞，以及识别此类缺陷的各种方法论。

以太坊智能合约使用 `Solidity` 编写——一种具有高度抽象的图灵完备编程语言。在对过往研究和其他相关资源进行文献分析后，收集、检查并使用了相关信息，以对以太坊区块链上智能合约的当前缺陷进行分类。作为本研究的结果，一份详尽的有据可查的漏洞主列表在本章中呈现。

# 核心概念

*   以太坊是智能合约的扩展框架——由相互分布的节点网络执行的计算机程序，无需第三方授权。
*   由于智能合约处理和转移有价值的资产，保护智能合约实现免受旨在窃取和操纵资产的攻击同等重要。
*   分析了智能合约的安全漏洞，并提供了导致漏洞的编程语言缺陷。还重点介绍了利用智能合约漏洞窃取资金的攻击。
*   以太坊智能合约根据其方法论使用各种软件工具。这些工具是自动化的，在部署到区块链之前检查合约中的漏洞、错误和安全措施。
*   基于漏洞的扫描工具（如 `Mythril`、`Securify` 和 `SmartCheck`）用于查找代码中的漏洞。其中一些工具用于智能合约的运行时验证，如 `ContractLarva` 等。

# 促进理解的活动

有兴趣制定区块链相关审计清单的智能合约应用测试人员和信息系统审计师，建议带着以下问题研究下面的智能合约审计清单：

## 智能合约审计清单

| 序号 | 智能合约攻击/漏洞 | 审核检查项 | 是 | 否 | 审计员备注 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1. | 重入攻击 | 递归回调功能是否正常运行？ [27] | | | |
| 2. | DoS 攻击 | 回退函数是否正常工作？ [6] | | | |
| 3. | 时间戳依赖 | 时钟是否同步？ [27] — 随机数生成器功能是否可能被操纵？ [24] | | | |
| 4. | 算术上溢/下溢攻击 | 输入是否经过验证？ [24] | | | |
| 5. | 短地址 | 攻击者是否篡改参数？ [1] | | | |
| 6. | 竞争条件 | 攻击者能否修改合约中的权限？ [1] | | | |
| 7. | 访问控制 | 攻击者是否会获得执行操作的特权？ [5] | | | |
| 8. | 未检查返回值 | 开发人员能否检查返回值？ [1] | | | |
| 9. | 不良随机性 | 攻击者能否预测前一个区块的哈希值？ [17] | | | |

1.  逐一检查清单中的九个领域，在不查看章节内容的情况下，使用上述清单测试您的智能合约漏洞知识。您第一次尝试答对了多少个？
2.  再次详细检查提供的审计清单，看看是否有审计清单中未涵盖的额外智能合约漏洞考量因素？
3.  在智能合约应用开发、测试或审计的哪些具体阶段和以何种方式，该清单能发挥作用？
4.  在您看来，在本章讨论并列在表 14.2 中的九种智能合约攻击中，哪种漏洞/攻击最难缓解？

# 参考文献

*   Antonopoulos, A. M. (2018). Mastering Ethereum: Building Smart Contracts and DApps. O’Reilly Media. 来源：[`cypherpunks-core.github.io/ethereumbook/09smart-contracts-security.html`](https://cypherpunks-core.github.io)

*   Wang, X., He, J., Xie, Z., Zhao, G., & Cheung, S. C. (2019). ContractGuard: Defend Ethereum Smart Contracts with Embedded Intrusion Detection. IEEE Transactions on Services Computing, *13*(2), 314–328. 来源：[`arxiv.org/pdf/1911.10472`](https://arxiv.org)

*   Eskandari, S., Moosavi, S., & Clark, J. (2019, February). Sok: Transparent Dishonesty: Front-Running Attacks on Blockchain. In International Conference on Financial Cryptography and Data Security (pp. 170–189). Springer, Cham. Retrieved from [`arxiv.org/pdf/1902.05164`](https://arxiv.org)

*   Maesa, D. D., Mori, P., & Ricci, L. (2018). Blockchain Based Access Control Services. IEEE International Conference on Internet of Things (iThings) and IEEE Green Computing and Communications (GreenCom) and IEEE Cyber, Physical and Social Computing (CPSCom) and IEEE Smart Data (SmartData). doi:[10.1109/Cybermatics_2018.2018.00237](http://dx.doi.org/10.1109/Cybermatics_2018.2018.00237)

*   Zhang, Q., Wang, Y., Li, J., & Ma, S. (2020). Ethploit: From Fuzzing to Efficient Exploit Generation against Smart Contracts. International Conference on Software Analysis, Evolution and Reengineering. doi:[10.1109/SANER48275.2020.9054822](http://dx.doi.org/10.1109/SANER48275.2020.9054822).

*   Liu, B., Sun, S., & Szalachowski, P. (2020). Smacs: Smart Contract Access Control Service. International Conference on Dependable Systems and Networks (DSN)*.* IEEE. doi:[10.1109/DSN48063.2020.00039](http://dx.doi.org/10.1109/DSN48063.2020.00039).

*   Sayeed, S., Marco-Gisbert, H., & Caira, T. (2020). Smart Contract: Attacks and Protections. 6–7.Retrieved from [`hackingdistributed.com/2016/06/18/analysis-of-the-dao-exploit/`](https://hackingdistributed.com)

*   Praitheeshan, P., Pan, L., Yu, J., Liu, J., & Doss, R. (2019). Security Analysis Methods on Ethereum Smart Contract Vulnerabilities: A Survey. Retrieved from [`arxiv.org/pdf/1908.08605`](https://arxiv.org)

*   Atzei, N., Bartoletti, M., & Cimoli, T. (2017). A survey of attacks on Ethereum smart contracts. Retrieved from [`link.springer.com/content/pdf/10.1007%2F978-3-662-54455-6_8.pdf`](https://link.springer.com)

*   Andrew, M., Zhicheng, C., & Somesh, J. (2018). Smart Contracts and Opportunities for Formal Methods. Springer, Cham. doi:[`par.nsf.gov/servlets/purl/10098553`](https://par.nsf.gov)

*   Palladino, S. (2017, July). The Parity Wallet Hack Explained. OpenZeppelin blog. Retrieved from [`blog.openzeppelin.com/on-the-parity-wallet-multisig-hack-405a8c12e8f7`](https://blog.openzeppelin.com)

*   EIP-1559: A Proposal to Update Transaction Fees on Ethereum. Retrieved from [`www.gemini.com/cryptopedia/ethereum-improvement-proposal-ETH-gas-fee#section-ethereum-transaction-fees`](https://www.gemini.com)

*   Programmer Sought. (2018). ERC20 short address attack. Retrieved from [`www.programmersought.com/article/44231449349/`](https://www.programmersought.com)

*   Grishchenko, I., Maffei, M., & Schneidewind, C. (2018). Foundations and Tools for the Static Analysis of Ethereum Smart Contracts. International Conference on Computer Aided Verification*.* Retrieved from [`link.springer.com/chapter/10.1007/978-3-319-96145-3_4`](https://link.springer.com)

*   Kaden, Z. (2019, October 24). Smart Contract Attack Vectors. Retrieved May 9, 2021, from [`github.com/KadenZipfel/smart-contract-attack-vectors/blob/master/attacks/dos-gas-limit.md`](https://github.com)

*   Kim, K. B., & Lee, J. (2020, November). Automated Generation of Test Cases for Smart Contract Security Analyzers. doi: [10.1109/ACCESS.2020.3039990](http://dx.doi.org/10.1109/ACCESS.2020.3039990)

*   Poston, H., & Bennett, K. (2019). Certified Blockchain Security Professional official Exam Study Guide. Retrieved from [`blockchaintrainingalliance.com/products/cbsp-official-exam-study-guide`](https://blockchaintrainingalliance.com)
