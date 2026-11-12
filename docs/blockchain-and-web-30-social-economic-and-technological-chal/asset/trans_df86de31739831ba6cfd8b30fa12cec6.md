

![](img/a0011e82f3a3a41227dc70cd0ddb893a_261_0.png)

图 15.2 DFiles 系统架构

连接到以太坊区块链私有版本（通过 MetaMask 的 Google Chrome/Firefox 扩展）的以太坊节点，在此可以部署智能合约、开发应用程序和运行测试：Ganache（Consensys, 2018a）。

最后两个阶段是实现阶段（实际编码在此进行）和测试阶段。当详细介绍 DFiles 核心智能合约时，所有这些阶段都会变得清晰，重点放在后者。还存在部署阶段，将在“局限性与未来工作”章节中讨论。

## 核心智能合约

开发以太坊智能合约需要大量的设计和测试，以确保其无错误，因为一旦部署后就无法更改。在 DFiles 中，核心智能合约 Files.sol 使用了流行的以太坊编程语言 Solidity 开发，并使用 Web3JS 在前端与其交互。

```
// A structure that contains information about the user's files
struct File {
string name; // the file's name
string extension; // the file's extension
uint32 size; // the file's size
string hash; //the IPFS file hash
string timestamp; // the transaction timestamp is stored in the JavaScript and is in the Unix Epoch time;
string ethereumAccount; // the user's Ethereum Address that uploaded the file
}
//The files belonging to each user (or address)
mapping(address => File[]) private userFiles;
```

### 代码片段 15.1 Files.sol 智能合约数据结构

在众多现成的 Solidity 设计模式中，仅因所开发智能合约的简单性而选择了 Ownable 模式。其实现由 OpenZeppelin 提供。4 代码从 Files.sol 智能合约继承而来。随后确定了要使用的整体数据结构——对于用户文件，使用一个映射将用户的以太坊地址与 File 结构关联，即 userFiles。该结构存储关于文件的数据——代码片段 15.1。

随后开发了一个函数，用于向用户映射添加文件，如代码片段 15.2 所示。

最后，创建了两个只读函数，用于返回给定文件的索引并返回映射的长度。这些函数允许通过在前端通过 Web3JS 迭代映射来发送大量的 gas。

Files.sol 源代码的完整代码可在 Bitbucket 上找到。5

BOSE 的最后一个阶段之一是测试，尤其是涉及智能合约时。Truffle 框架提供了一个不错的单元测试套件。6 执行了以下测试：

- 创建一个与智能合约结构具有相同属性的新文件对象，将其插入测试区块链，获取插入的数据，然后将其与原始文件对象进行比较。如果相同，则测试通过。否则，测试失败。

- 创建一个新文件对象，将其插入测试区块链，并尝试遍历无效的文件索引（不存在的文件）。如果循环失败，则该索引处没有文件，因此测试通过。

## 简要演示

本节介绍 DFiles DApp 的核心功能。此外，还解释了文件加密和文件解密的工作原理。

首先，用户注册账户并登录（此过程通过 NodeJS/Express 集中式服务器处理）。然后，他们会被带到上传文件页面以选择要上传的文件，如图 15.3 所示。

```
// @notice This function inserts information of a file to the
userFiles array: name, size, extension in addition to a timestamp and
the IPFS file hash
// @param _name file name
// @param _hash IPFS file hash
// @param _extension file extension
// @param _size file size
// @param _timestamp a timestamp
// @param _ethereumAccount the user Ethereum account calling this contract
function addFile(string _name, string _hash, string _extension, uint32 _size, string _timestamp, string _ethereumAccount)
public {
require(_size>0 && _size<=4294967295, "Invalid file size");
File memory file = File(_name, _extension, _size, _hash, _timestamp, _ethereumAccount);
userFiles[msg.sender].push(file);
}
```

### 代码片段 15.2 在 Files.sol 智能合约中添加文件信息

![](img/a0011e82f3a3a41227dc70cd0ddb893a_263_0.png)

图 15.3 DFiles 文件上传示例

单击“上传文件”按钮后，文件将使用 crypto-js API 加密，7 用户的私钥存储在集中式服务器中。然后，用户必须接受一笔使用智能合约的交易，该交易将关于文件的多个详细信息存储在本地以太坊区块链（Ganache）中，如图 15.4 所示。

gas 费和总交易成本取决于 gas 价格（以 GWEI 计）和预定义的 gas 限制（这对于评估部分非常重要）。然后，文件被发送到本地集中式 IPFS 节点，该节点返回包含加密文件的哈希值。此后，用户会看到其 URL 的成功消息，如图 15.5 所示。

![](img/a0011e82f3a3a41227dc70cd0ddb893a_264_0.png)

图 15.4 以太坊 MetaMask 交易提示

### 上传文档

一键上传文档或重要文件。支持的格式：png、txt、jpg、gif、bmp、pdf、csv、xml、xlsx、pptx、docx

![](img/a0011e82f3a3a41227dc70cd0ddb893a_264_1.png)

文件 gdpr-2018.pdf 上传成功。在 myfiles 中查看或点击此链接

图 15.5 文档上传成功消息

点击链接后，用户会看到文件，但为加密形式（图 15.6）。

最后，可以浏览其文件的详细信息，尽管这些信息未加密（图 15.7）。

一旦用户点击“解密并下载”，所选文件将被解密并下载。当用户调用 GDPR 的删除权时，其所有详细信息（包括用于加密其文件的私钥）都会被删除。文件仍然基本上位于 IPFS 节点中，尽管已加密。由于它们无法访问，可以视为已删除。这样，不可变性问题得以解决。在下一节中，将进行统计分析以了解这种方法是否可行。

## 评估

如前所述，GDPR 对确保 DApp 符合其要求构成了重大挑战，主要原因是被遗忘权。本节将进行统计分析，以了解在将文件发送到 IPFS 节点之前加密个人数据（或文件）是否可行。这样一来，加密文件将在节点提供服务的期间一直保留，但其内容对第三方仍然无法访问，这与文件删除相同。

在以太坊中，存在“gas”概念：

> 交易发送者在以太坊区块链上进行每项操作都需要支付的执行费。gas 这个名字来源于这样的观点：该费用充当加密燃料，推动智能合约的运行。gas 由执行代码的矿工以以太币购买。（以太坊基金会，2016）

与 gas 相关的四个重要方面：

- **gas 限制**：交易中要支付的最大 gas 数量；
- **交易使用的 gas**：交易消耗的总 gas；
- **gas 价格**：交易中指定的每单位 gas 的价格（以以太币计）；以及
- **总交易成本**：gas 使用量 × gas 价格。

开发了两个版本的 DFiles DApp：一个没有用户身份验证和文件加密，另一个同时具有用户身份验证和文件加密/解密。所有即将发布的统计数据均可在 Bitbucket 上找到。8 首先，随机选择了 100 个文件，扩展名各不相同：.pdf、.docx、.xlsx 和 .pptx，但由于硬件限制无法全部使用。然后将它们分为四组：小（1 KB–1 MB）、中（1 MB–20 MB）、大（20 MB–200 MB）和特大（200 MB–2 GB）。除此之外，对于相同的文件和 DFiles 的两个版本，还测量了从用户点击“上传文件”按钮、文件发送到本地 IPFS 节点（加密或未加密）以及用户点击按钮接受交易的耗时，以及以太币（由 MetaMask 提供；根据 gas 限制和 gas 价格而有所不同）的总交易成本。附录 A 显示了部分收集的数据。

但是，由于文件加密的硬件限制，以下统计分析仅考虑了高达 14.2 MB 的文件。仍然记录了总交易成本和上传耗时，以便在加密和非加密文件之间的总体结论中进行比较。

