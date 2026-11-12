

重要的一点是能够开发用于检查内部属性的工具。此外，普遍关注的问题是，开发者应当能够查看其自身合约中存储的值。

因此，在此语境下，检查合约属性对于使用智能合约的开发者来说不仅重要，而且是必要的。

## 挑战

要突破不透明性问题并揭示合约信息，面临诸多挑战。

- **二进制且不完整的规范。** 从技术层面来看，我们只有以太坊 API 来访问合约的二进制表示。我们面临的第一个挑战是 Solidity 编译器执行的合约编码是一个*不完整*的规范 [Eth18c]。
- **哈希计算规范不一致。** 与规范相关的另一个挑战是动态类型的哈希计算。静态类型使用文本作为哈希计算的输入。然而，动态类型遵循一个不同的标准，该标准在文档中并未明确指定。对于动态类型，有必要为每个类型使用专门打包的二进制数据。例如，要访问数组，有必要将索引号和数组位置（偏移量）打包为二进制表示，以获得正确的哈希。其他动态类型需要不同的输入来获取其哈希。
- **打包且有序的数据。** 我们还强调解码类型的挑战，因为编译器尽可能将大量数据打包到连续内存中。因此，我们需要知道按正确顺序排列的特定类型才能获取合约数据，而在规范不完整的情况下，这并非易事。

我们承认，分析在以太坊区块链数据库中部署的自身合约所面临的挑战和困难是一个问题。为了解决这个问题，我们提出了一个检查器，允许用户感知实例数据属性的干净表示。此类检查器是使用平台的几个组件构建的：FogComm、FogLive。

## 方法：SmartInspect

SmartInspect [BRDD18a] 是一个基于可插拔镜像映射反射系统的 Solidity 合约内部状态检查器。该工具的目标是允许根据源代码检查已知的合约实例。部署合约的二进制结构是使用从其源代码构建的内存布局细化进行反编译的。因此，只有拥有源代码及其部署二进制表示访问权限的人才能检查其内部属性。此外，SmartInspect 方法可以在不重新部署合约或开发额外解码代码的情况下，内省智能合约实例的当前状态。SmartInspect 使用 Pharo 实现，并作为 SmartAnvil 工具套件的一部分公开可用于 GitHub (github.com/RMODINRIA-Blockchain/SmartShackle)。

智能检查器的一般理念是反编译由以太坊 API 编码的存储布局。通过使用合约源代码作为参考，可以知道属性值在编码后的二进制结构中的存储位置（图 13.3）。反编译内存布局是一项挑战，因为 Solidity 文档 [Eth18c] 关于某些类型如何编码的内容不完整。因此，我们不得不自己对编译器执行的某些编码进行逆向工程。

在解码内存布局后，我们仍然需要将解决方案应用于任何合约，以实现通用的可重用解决方案。我们采用了一种镜像映射架构 [BU04]，它模仿任何合约的结构，以便我们访问可以解码的内存布局。镜像映射像一个独立的元编程层，将反射功能的关注点拆分为镜像对象。首先，我们需要合约源代码作为输入来开始构建镜像映射。然后我们解析源代码（使用前面描述的 Solidity 解析器）来创建一个 AST（抽象语法树）。通过解释

![](img/a0011e82f3a3a41227dc70cd0ddb893a_215_0.png)

### 图 13.3 内存布局表示

![](img/a0011e82f3a3a41227dc70cd0ddb893a_216_0.png)

### 图 13.4 SmartInspect 构建过程

AST，我们能够按照正确的顺序发现合约中声明的每种类型。我们需要这些信息来解码内存布局并访问合约数据。为了实现通用解决方案，我们模型化可配置的镜像对象，使我们能够与同配置的已部署合约实例进行交互（通常指同一合约在区块链上部署的情况）。

图 13.4 展示了检查合约的完整过程图；可插拔反射架构使用给定合约的 AST 为其源代码生成一个镜像映射。然后，我们使用该镜像映射从部署在区块链上的远程合约实例中提取信息（该实例编码为二进制内存布局）。我们收集的合约数据以四种不同的格式暴露：(1) 数据代理对象 (REST)，(2) Pharo 窗口部件用户界面，(3) JSON，以及 (4) HTML。

这种方法使我们能够以结构化的方式访问远程无结构信息。我们的解决方案满足了远程检查所需的大多数可取属性，即交互性和分布性 [PBD+15]。

## 示例说明

我们现在展示一个用 Solidity 编写的智能合约示例，并使用 SmartInspect 内省其内容。假设一个场景，主管管理一个投票，用户只能投票一次。投票被编码为智能合约，因为它用于依赖信息真实性和不可更改性的管理决策。只有合约的主管才允许修改选民列表。以下列表（清单 13.2）突出了此合约的最重要代码部分：

### 清单 13.2 Solidity 投票合约示例

```
pragma solidity ^0.4.24;
/** @title Poll Contract Example
 * @author RMoD-Blockchain Team
 */
contract RModPoll {
 /* * Type Definition */
 enum Choice {POSITIVE, NEGATIVE, NEUTRAL}
 struct PollEntry {address user; Choice choice; bool hasVoted;}

 /* * Attributes/Internal State */
 PollEntry[] pollTable;
 address private supervisor;

 /* * Constructor */
 constructor() public {supervisor = msg.sender;}

 /* * Functions */
 // Add the account as a voter in this poll
 function addVoter(address account) public returns (uint) { . . . }
 // Verifies if the account is already registered in this poll
 function isRegistered(address account) public view returns(bool) { . . . }
 // Returns the Voter's index in the pollTable
 function voterIndex(address voterAccount) private view returns(int) { . . . }
 // Function called by the voter to assert his vote
 function vote(Choice myChoice) public { . . . }
 // Verifies if everyone registered for this poll have voted
 function everyoneHaveVoted() public view returns (bool) { . . . }
 // Return the amount of votes for Positive, Negative, and Neutral
 function countVotes() public view returns (uint,uint,uint) { . . . }
}
```

此合约定义两个自定义类型：Choice（第 5 行）和 PollEntry（第 6 行）。Choice 模拟投票的答案（无论投票是肯定的、否定的还是中立的）。PollEntry 是一个表示投票的记录，即投票用户、所选选项以及他是否已投票。请注意，要引用选民，我们需要一个账户地址（使用原始类型 address），它指向一个

![](img/a0011e82f3a3a41227dc70cd0ddb893a_218_0.png)

### 图 13.5 SmartInspect Pharo 用户界面截图

以太坊账户。合约在内部存储一个投票表（PollEntry 数组，第 9 行）和一个指向投票主管账户的地址（第 10 行）。投票表是一个空数组，主管将最终在其中存储投票信息（即，数组将为每个被允许投票的用户创建一个条目）。主管的地址用于安全检查，即，确保只有主管可以调用某些特定函数（例如 addVoter 函数）。对于此示例说明，没有必要定义和解释其余函数。

假设投票即将结束，但并非所有人都已投票。因此，投票的主管将需要向尚未投票的用户发送提醒。然而，合约的属性未定义为公共。此外，我们在部署合约之前未创建任何函数来检查该信息。由于我们无法更新已部署合约实例的源代码，检查其内部状态是了解哪些账户尚未投票的唯一方法。因为主管既能访问合约源代码，也能访问其已部署实例，所以他/她可以执行 SmartInspect 来查看合约数据（图 13.5）。最后，主管可以看到哪些用户在当前投票实例中未投票。

## 评估

我们调查 SmartInspect 与其他检查器相比是否实现了必要且可取的功能。我们确定了六个特征

