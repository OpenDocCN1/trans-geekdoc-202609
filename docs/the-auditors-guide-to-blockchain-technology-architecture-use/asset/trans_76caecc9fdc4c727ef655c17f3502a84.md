

*   [Static Analysis](#ch21.xhtml#r481b). (2019, August 28). How to Detect, Prevent, and Mitigate Buffer Overflow Attacks: Synopsys. Software Integrity Blog. [https://www.synopsys.com/blogs/software-security/detect-prevent-and-mitigate-buffer-overflow-attacks/](https://www.synopsys.com).

*   [Svajcer, V.](#ch21.xhtml#r482b), &amp; Huey, C. (2020, October 13). Lemon Duck Brings Cryptocurrency Miners back into the Spotlight. Web log. [https://blog.talosintelligence.com/2020/10/lemon-duck-brings-cryptocurrency-miners.html](https://blog.talosintelligence.com).

*   [Tripwire Guest Authors](#ch21.xhtml#r483b). (2019, July 21). Six System and Software Vulnerabilities to Watch out for in 2019. [https://www.tripwire.com/state-of-security/vulnerability-management/six-system-and-software-vulnerabilities/](https://www.tripwire.com).

*   [Walker, M.](#ch21.xhtml#r484b) (2019, July 6). Blockchain, a Barrier against Ransomware. [https://thefintechtimes.com/blockchain-barrier-ransomware/](https://thefintechtimes.com).

# 14 智能合约漏洞、攻击与审计考量

Maheswar Sharma, Keerthana Kasthuri, Parvinder Singh and Nynisha Akula

DOI: [10.1201/9781003211723-14](http://doi.org/10.1201/9781003211723-14)

## 摘要

顾名思义，本章重点关注区块链技术中最脆弱的组件之一，即智能合约。本章通过审视此类安全漏洞的根本原因，讨论了总共九种与智能合约相关的攻击。这些攻击包括重入攻击、访问控制、算术运算、未检查返回值、DoS、不良随机性、竞争条件、短地址和时间戳依赖攻击。

除了编码错误和攻击讨论外，本章还讨论了七种不同的智能合约审计方法。虽然——取决于预期的用例——在智能合约开发过程中并不一定需要使用所有七种审计方法，但审计人员需要对这些审计方法有基本的了解，以便能够在智能合约发布前推荐合适的智能合约测试和评估组合。如前所述，在[第2章](#ch10.xhtml#c2)和[第9章](#ch17.xhtml#c9)中提到，在智能合约的编码和测试过程中必须极其谨慎，因为智能合约开发类似于固件开发，一旦部署，有缺陷的智能合约无法再通过应用软件补丁来修复。因此，唯一可行的解决方案是终止该智能合约——假设其设计中添加了此类终止开关——并用一个功能完善的智能合约来替换有问题的智能合约。

信息系统审计师也会发现智能合约审计模板是规划和实施智能合约审计的有用工具。

## 智能合约安全考量

智能合约已成为区块链技术中的一项重大编程突破。智能合约是在以太坊等平台上执行的计算机程序，`Solidity` 是用于编译以太坊虚拟机上使用代码的编程语言。

智能合约在区块链上被视为“公开”的，用户可以通过创建交易与智能合约进行交互。在处理智能合约程序时，需要熟悉与检测和避免智能合约代码主要缺陷相关的安全风险。在本节中，我们将考察代码执行过程中常见的已知安全漏洞 [1]。

### 重入攻击

重入攻击被视为最灾难性的智能合约攻击策略之一。这种攻击方法可能会破坏合约或促成敏感信息的窃取。当用户构建的功能允许外部函数在处理其后果之前调用另一个不受信任的智能合约时，就会发生重入攻击。该漏洞允许攻击者执行主函数的递归回调，导致非预期的循环重复多次。`Single` 函数和 `cross` 函数是攻击者用来破坏合约或获取有价值信息的两种不同类型的重入攻击（[图 14.1](#ch22.xhtml#t45)）[[7](#ch22.xhtml#r491)]。

![Figure 14.1  A sample code explaining the flaws leading to the reentrancy attack [14]. ¶ Source: [25].](html/images/Figure14_1.jpg)

[图 14.1](#ch22.xhtml#t46b)  解释导致重入攻击缺陷的示例代码 [[14](#ch22.xhtml#r498)]。 ¶ 来源：[[25](#ch16.xhtml#r312)]。

Solidity 的 call 构造（在 EVM 字节码中转换为 `CALL` 指令）会导致被调用者代码的一小部分被执行——正如 fallback 函数中所定义的那样。因此，当使用 call 构造时，创建者可能会假设一个原子值转移，其中可以执行另一个合约的代码。通过使用“Y”账户的地址调用“X”函数 `ping`，2 `wei`（以太币的最小面额）被转移到“Y”账户，此外，“Y”的 fallback 函数被调用。由于 fallback 函数再次使用 Y 的地址调用 `ping` 函数，在合约“X”的变量 `sent` 被设置之前，又转移了 2 `wei`。这种循环将持续到初始调用的所有 `gas`（在以太坊区块链平台上进行交易或执行合约所需的费用）被消耗殆尽或达到调用栈限制 [[14](#ch22.xhtml#r498)]。

#### 真实案例场景

通过研究 DAO（去中心化自治组织）案例可以看到重入攻击的影响，该组织由开发人员创立，旨在实现决策自动化并促进加密货币交易。DAO 是以太坊早期开发过程中的主要受害者之一。重入攻击发挥了关键作用，合约的总价值达 1.5 亿美元 [[7](#ch22.xhtml#r491)]。

### 访问控制

通常，智能合约具有受保护的功能，这意味着所有者和其他授权用户由其地址标识。访问控制系统可以部署在由所有者或受信任的第三方管理的智能合约上 [[4](#ch22.xhtml#r488)]。在以太坊智能合约中，访问控制的目的是限制对合约组件的访问 [[6](#ch22.xhtml#r490)]。

访问控制的漏洞在于攻击者可以阻止用户获得访问权限，或授予他人执行货币转账和/或合约自毁等操作的权限 [[5](#ch22.xhtml#r489)]（[图 14.2](#ch22.xhtml#t46)）。

![Figure 14.2  A sample code explaining the flaws leading to access control vulnerability [5]. ¶ Source: [25].](html/images/Figure14_2.jpg)

[图 14.2](#ch22.xhtml#t46b)  解释导致访问控制漏洞缺陷的示例代码 [[5](#ch22.xhtml#r489)]。 ¶ 来源：[[25](#ch16.xhtml#r312)]。

在上述示例的 `line 3` 中，通过执行公共函数 `ABC()`，原始所有者被修改为 `msg.sender`（`line 4`），而无需验证代码。攻击者还可以省略 `line 7` 中的 `only owner` 以提取合约中的所有以太币 [[5](#ch22.xhtml#r489)]。

#### 真实案例场景

