
- 如果 `Redeemer` 是 `Cancel`，则检查交易中的所需签名是否与 Datum 中的公钥哈希匹配。若匹配，验证器允许所有者随意处置该 UTXO。

- 如果 `Redeemer` 是 `Claim`，则当 `Redeemer` 中的消息与合约参数 `MESSAGE` 的值匹配时返回 `true`。

- 如果 `Redeemer` 既不匹配 `Cancel` 也不匹配 `Claim`，或返回假值，验证器将返回 `false`，交易将失败。

### Helios 链下解锁

首先，我们将创建一个 `Unlock.tsx` 组件，允许用户输入 `Redeemer` 的文本并选择按钮以构建解锁交易，如 *Figure 6.3* 所示。

![](img/Figure-6.3.jpg)

**Figure 6.3:** Unlock UI Component³

然后，我们在主页面 `index.tsx` 中创建解锁函数，该函数接受 `Redeemer` 参数并构建交易。*Figure 6.4* 中的解锁函数类似于锁定函数，但我们需要在第 171 行获取一个接收地址以发送解锁后的资金。在第 186 行，我们将验证器脚本附加到交易中，作为脚本见证包含在内。

![](img/Figure-6.4.jpg)

**Figure 6.4:** Unlock Function Vesting Program⁴

接下来，在 *Figure 6.5* 中，我们需要在第 189 行获取锁定在脚本地址上的 UTXO，并在第 193 行构建 `Redeemer`。在 Helios 中，我们可以直接从链上代码导入 `Redeemer` 类型，并使用 `_toUplcData()` 函数生成 UPLC 代码。然后在第 198 行添加 UTXO 输入和 `Redeemer`，它们将作为 `Redeemer` 见证关联在一起。第 206 行还创建了一个 UTXO 输出，用于在脚本地址上的 UTXO 被花费后将 2 Ada 发送到接收地址。

![](img/Figure-6.5.jpg)

**Figure 6.5:** Unlock Function Inputs and Outputs⁵

第 189 行的 `getVestingUtxo` 函数向一个 Next.js API 发起网络调用，该 API 被创建用于查询脚本地址上的 UTXO。该 Next.js API 使用 `Blockfrost`（一个第三方区块链 API 提供商），并在服务器端执行。查询 Cardano 区块链还有其他提供商和方法，例如 Maestro、Ogmios 和 Koios。我们将在 *第 8 章，工具* 中回顾其他区块链 API 提供商。服务端使用 `Blockfrost` API 的优势在于：避免直接从浏览器调用 API 导致 API 密钥泄露；此外，还避免了向不同域名发起网络调用，从而防止浏览器 CORS 错误。*Figure 6.6* 展示了由 `index.tsx` 中的 `getVestingUtxo` 函数调用的 Next.js `vestingUtxo` API 代码。

![](img/Figure-6.6.jpg)

**Figure 6.6:** getVestingUtxo API⁶

解锁函数的其余部分与锁定函数相同，负责组装、签名并将交易提交到网络。带有解锁按钮和 `Redeemer` 消息输入的新 UI 如 *Figure 6.7* 所示。

![](img/Figure-6.7.jpg)

**Figure 6.7:** Helios Unlock UTXO

### 链下取消

我们创建了一个 `Cancel.tsx` 组件和 `index.tsx` 内部的 `cancel` 函数，它们与 `Lock.tsx` 组件和 `unlock` 几乎完全相同。解锁和取消函数之间只有少数差异。你能在 *Figure 6.8* 中找出这些差异吗？

![](img/Figure-6.8.jpg)

**Figure 6.8:** Helios Cancel UTXO⁷

其中一个差异是我们必须为交易显式添加所需签名者。第 294 行的 `.addSigner()` 函数将钱包的公钥哈希添加到交易中，并将其作为必需签名者包含在内。Cardano 节点将确保任何必需签名者在见证集中都有相应的有效签名。链上代码随后在必需签名者列表中查找公钥哈希，以查看是否匹配。

### 试运行

要运行演示，你需要执行以下命令；除非你更改版本号或 `vesting` 脚本，否则验证器脚本地址对所有人都是相同的：

```
$ cd chapter_06/helios/vesting
$ npm install
$ echo export BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc
$ echo export NEXT_PUBLIC_ENV="dev" >> ~/.bashrc
$ echo export NEXT_PUBLIC_HOST="demeter-run-host" >> ~/.bashrc
$ echo export NEXT_PUBLIC_PROTOCOL="https" >> ~/.bashrc
$ echo export NEXT_PUBLIC_PORT="" >> ~/.bashrc
$ source ~/.bashrc
$ npm run dev
```

现在你应该能够使用暴露的端口 URL 访问该应用程序。你可以锁定 2 Ada，并使用正确的 `Redeemer` 值进行领取（解锁）或取消。*Figure 6.9* 展示了一个使用正确 `Redeemer` 值成功领取 2 Ada 的交易。

![](img/Figure-6.9.jpg)

**Figure 6.9:** Helios Vesting Claim⁸

#### Aiken

Aiken 是一种函数式编程语言，其编译器由 Rust 编写。我们将使用 `aiken build` 命令编译 Aiken 脚本。这将生成编译后的 Plutus 代码和一个包含元数据和类型定义的 **blueprint** 文件。要在 `Demeter.run` 工作区中安装 Aiken，首先需要下载安装程序：

```
$ curl -sSfL https://install.aiken-lang.org | bash
$ echo export PATH=:/config/.aiken/bin:$PATH >> ~/.bashrc
$ source ~/.bashrc
```

然后，运行以下命令：

```
aikup
```

安装好 `aiken` 后，你可以使用 help 开关查看以下可用选项：

```
$ aiken --help
Cardano smart contract language and toolchain
Usage: aiken <COMMAND>
Commands:
new         Create a new Aiken project
fmt         Format an Aiken project
build       Build an Aiken project
address     Compute a validator's address
check       Type-check an Aiken project
docs        Build the documentation for an Aiken project
add         Add a new project package as dependency
blueprint   Commands for working with Plutus blueprints
packages    Managing project dependencies
tx          Commands for working with transactions
uplc        Commands for working with untyped Plutus-core
completion  Generates shell completion scripts
help        Print this message or the help of the given subcommand(s)
```

你可以使用以下命令创建一个新项目：

```
aiken new aiken-lang/new-project
```

这将创建以下项目文件和文件夹：

```
└── new-project
├── aiken.toml
├── lib
│   └── new-project
├── README.md
└── validators
```

`aiken.toml` 包含有关项目的信息，包括库和 GitHub 仓库。`validators` 文件夹包含链上 Aiken 源代码，`lib` 目录包含该项目所需或创建的任何项目库。你可以通过在 `new-project` 目录中执行 `aiken build` 和 `aiken check` 来快速测试，确认一切安装正确。

在本书的示例中，我们将所有 Aiken 链上验证器代码和工件放在每个章节项目的 `contracts` 目录中。例如：

`chapter_06/aiken/vesting/contracts`

如果你想了解更多关于设置和安装任务（包括 IDE 语言配置）的信息，请参阅 Aiken 在线文档。⁹

### Aiken 链上验证器

### Aiken 验证器脚本分析

现在，我们准备好查看第一个 Aiken 验证器脚本，如图 6.10 所示：

![](img/Figure-6.10.jpg)

**图 6.10：** Aiken 链上验证器声明¹⁰

图 6.10 中的前 5 行是我们将要使用的类的显式导入，随后是 `Datum` 和 `Redeemer` 类型。`Datum` 包含一个 `Hash` 对象，其中包含 `Blake2b_224` 和 `VerificationKey` 对象。值得注意的是，这在链上作为单个 `ByteArray` 存储，代表公钥哈希。在第 15 行，`Redeemer` 包含两个条件（`Cancel` 和 `Claim`），用于花费锁定在此脚本地址上的 UTXO。`Claim` redeemer 还使用 `ByteArray` 数据类型包含一个 `msg` 载荷。在第 21 行，我们将 "`Hello World!`" 消息硬编码为脚本常量。

接下来，在图 6.11 中，我们在第 23 行定义验证器函数，并创建 vesting 函数，以 `Datum`、`Redeemer` 和 `ScriptContext` 作为参数：

![](img/Figure-6.11.jpg)

**图 6.11：** Aiken 链上验证器主体¹¹

在第 26 行，我们确定特定交易提供的 `Redeemer` 类型。在 `Cancel` 的情况下，第 29 行的代码会遍历所需签名者列表，并确认是否存在与 datum 中的公钥哈希匹配的公钥哈希。如果为真，则验证器评估为真，并允许花费锁定在脚本地址上的 UTXO。如果 `Redeemer` 是 `Claim`，我们在第 32 行将 `msg` 载荷与硬编码的消息常量进行比较。如果 `Redeemer` 没有匹配项，则验证器将失败，不允许花费锁定在脚本地址上的 UTXO。

### Lucid 链下解锁

我们将创建与使用 Helios 时相同的 `Unlock.tsx` 组件和 `index.tsx` 中的 `unlock function`。我们需要为 unlock function 创建一个 `Redeemer`，但不需要创建 `Datum`，因为它已经是我们想要花费的 UTXO 的一部分。图 6.12 第 172 行的 `Redeemer` 创建了一个 Plutus Data 对象，对应于我们在第 4 章 Plutus 中看到的 UPLC 数据类型。在这种情况下，我们在索引 1 处创建一个 `Constr`，包含一个十六进制编码的字符串。当脚本被评估时，这个十六进制编码的字符串将被转换为 `Redeemer` `Claim` `ByteArray` 载荷。我们指定索引为 1，因为 `Redeemer` `Cancel` 是在 Plutus 脚本中首先定义的 `Redeemer`，索引为 0。按顺序的下一个 `Redeemer` 将具有索引 1，即 `Claim` `Redeemer`。

![](img/Figure-6.12.jpg)

**图 6.12：** Lucid 链下解锁¹²

在第 175 行，通过调用 `lucid.utxosAt` 函数获得锁定在脚本地址上的 UTXO，该函数使用 Blockfrost API 查询区块链。接下来，我们构建交易，并在第 182 行指定输入 UTXO，在第 183 行指定验证器脚本。现在可以使用 `.complete()` 方法组装 lucid 交易。在幕后有大量活动来组装和完成交易。我们将专注于更常用的 `lucid tx` 方法来构建和提交交易。一旦交易完成，钱包将要求用户签名并将其提交到网络。

### Lucid 链下取消

最后，我们将创建一个新的 `Cancel.tsx` 组件和 `index.tsx` 中的 cancel function。`Cancel.tsx` 组件与 `Lock.tsx` 组件几乎相同，主要区别在于图 6.13 第 226 行交易中的所需签名。这是必需的，因为链上代码会检查所需的公钥哈希是否与存储在 datum 中的公钥哈希匹配。

![](img/Figure-6.13.jpg)

**图 6.13：** Lucid 链下取消¹³

### 试运行

要尝试该示例，请运行以下步骤：

```
$ cd chapter_06/aiken/vesting/contracts
$ aiken build
$ cd ..
$ echo export NEXT_PUBLIC_BLOCKFROST_API=https://cardano-preprod.blockfrost.io/api/v0 >> ~/.bashrc
$ echo export NEXT_PUBLIC_BLOCKFROST_KEY=your-blockfrost-API-key >> ~/.bashrc
$ source ~/.bashrc
$ npm install
$ npm run dev
```

### 结论

我们查看了使用 Helios 和 Aiken 语言构建的第一个链上 Plutus 验证器。然后我们查看了使用 Helios 和 Lucid 分别执行这些验证器的相应链下代码。我们了解了如何使用 Aiken 初始化项目以及如何编译 Aiken 智能合约。然后，我们研究了 `ScriptContext` 以及它如何包含关键交易信息，如输入、输出、脚本目的等。我们还查看了链上的 `Datum` 和 `Redeemer` 定义以及它们在脚本执行期间如何被访问。示例中还演示了链下 `Redeemer` 和所需签名者的创建。下一章将深入探讨铸造策略、参数化智能合约和铸造原生代币。

### 要点回顾

*   Helios 既用于链上代码也用于链下代码。

*   Helios 链上代码可以即时编译，因为 Helios 编译器是用 JavaScript 编写的。

*   Aiken 用于链上代码，并使用基于 Rust 的 `aiken` 编译器在运行前编译。

*   Aiken 还会生成一个蓝图文件，其中包含 Plutus 脚本元数据和类型定义。

*   `aiken` 程序有几个方便的实用函数，可用于智能合约开发期间。

*   Lucid 用于链下代码，经常与 Aiken 结合使用。

*   Lucid 和 Helios 链下代码依赖区块链 API 提供商来获取区块链信息，例如锁定在脚本地址上的 UTXO。

*   Helios 链下代码可以导入 Helios 链上代码，从而允许共享类型定义。

*   Helios 链下代码不需要任何第三方库，并整合到一个 JavaScript 文件中。

*   花费 UTXO 时，必须为锁定在脚本地址上的每个 UTXO 提供一个 `Redeemer`。

*   所需签名者必须在交易的见证集中包含签名。

### 多项选择题

1.  在 Plutus 脚本地址花费 UTXO 需要什么？

    1.  仅 Datum

    2.  铸造脚本

    3.  Datum 和 Redeemer

    4.  Epoch

2.  交易完成期间必须发生什么活动？

    1.  平衡输入和输出

    2.  指定 Redeemer

    3.  指定 Datum

    4.  签署交易

3.  链下代码如何访问区块链数据？

    1.  直接向节点发起 RPC 调用

    2.  通常不需要

    3.  使用 API 提供商（例如 `Blockfrost`、`Ogmios` 等）

    4.  CIP-30 钱包连接器

4.  链上代码执行的典型顺序是什么？

    1.  本地评估器，节点进行 `tx` 提交，所有区块链节点

    2.  仅所有区块链节点

    3.  仅节点进行 `tx` 提交

    4.  本地评估器然后所有区块链节点

5.  四种不同的脚本目的是什么？

    1.  `Validate`、`Mint`、`Reward`、`Cert`

    2.  `Spend`、`Burn`、`Cert`、`Reward`

    3.  `Spend`、`Mint`、`Burn`、`Context`

    4.  `Spend`、`Mint`、`Cert`、`Reward`

### 答案

1.  c

2.  a

3.  c

4.  a

5.  d

### 问题

1.  如何提高已执行智能合约的可审计性？

2.  为什么大多数智能合约在运行前部署？

3.  `Datum` 和 `ScriptData` 哈希的作用是什么？

4.  为什么执行智能合约时必须始终指定 redeemer？

5.  像 Lucid 和 Helios 这样的链下框架如何检索 Plutus 成本模型？

6. 交易所需签名者的 CDDL 规范标识符是什么？

### 关键术语
