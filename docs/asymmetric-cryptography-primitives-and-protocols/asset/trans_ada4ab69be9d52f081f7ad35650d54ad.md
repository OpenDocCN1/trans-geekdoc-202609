
与 BPR 安全博弈最显著的对比在于谁决定诚实 `P[i]` 的密码输入。在 BMP 模型中，诚实参与方的输入由一个称为*环主*的特殊实体决定，但不失一般性，环主可以遵循对手 ![image](images/a.jpg) 的指示。因此，有些反直觉的是，是对手 ![image](images/a.jpg) 决定了所有密码。这与 BPR 安全博弈形成强烈对比，在 BPR 中 `P[i]` 的密码是由博弈挑战者从某个字典中随机选择的，而非由对手选择。然而，正如我们稍后将看到的，这种看似反直觉的选择不仅讲得通，而且意味着对任意密码分布的安全性，还有助于克服 BPR 模型的其他几个局限性（参见[第 10.3.3 节](#c10.xhtml#sec10-3-3)）。与 BPR 模型一样，![image](images/a.jpg) 可以揭示任意诚实参与方的会话密钥，但由于不再存在对手“测试”的会话，不失一般性，![image](images/a.jpg) 可以获取所有 `P[i]` 输出的会话密钥。

### 理想世界博弈

我们颠倒了 Boyko 等人 (2000) 采用的表述顺序，从*隐式认证* PAKE 情况入手，这作为 BPR 定义的基本情况，随后成为了 PAKE 的标准概念。我们将在[第 10.4.4 节](#c10.xhtml#sec10-4-4)解释向*显式认证*（PAKE-EA）的扩展。BMP 模型中的理想世界博弈是模拟器算法 ![image](images/a.jpg)^∗ 与 PAKE 方案的理想功能 ![image](images/f.jpg)`PAKE` 之间的交互，过程如下：

1.  当诚实参与方 `P[i]` 被环主以某个密码 `pw [P[i]]` 调用时，![image](images/f.jpg)`PAKE` 向 ![image](images/a.jpg)^∗ 发送 (`NewSession`, `P`, `i`) 并为此会话创建一个内部状态，将其标记为 `fresh`。因此，理想世界对手知道是否有某个 `P[i]` 正在运行协议，但它不知道他们的密码输入。环主在 ![image](images/a.jpg)^∗ 的信号下启动 `P[i]`，同时设置 `P[i]` 的 `role` 位及其预期的对端标识符 `pid`。

2.  对于任意会话 `P[i]`，对手 ![image](images/a.jpg)^∗ 可以向 ![image](images/f.jpg)`PAKE` 发送消息 (`TestPwd`, `P`, `i, pw*`^∗)，这模拟了一种主动攻击，即真实世界的对手在与 `P[i]` 交互时，遵循 PAKE 方案使用密码猜测 `pw*`^∗。如果 `pw*`^∗ = `pw[P[i]]`，则 ![image](images/f.jpg)`PAKE` 将 `P[i]` 的会话标记为 `compromised`，否则将其标记为 `interrupted`。（这些标记将决定 ![image](images/f.jpg)`PAKE` 如何响应 `NewKey` 查询；见下文。）此外，![image](images/f.jpg)`PAKE` 将此标记揭示给 ![image](images/a.jpg)^∗，这意味着真实世界的 PAKE 协议可以揭示主动攻击是否成功。关键在于，![image](images/a.jpg)^∗ 对每个 `P[i]` 会话*最多只能发送一个* `TestPwd` 查询，这强制要求对手在被攻击的会话上最多只能测试一个密码猜测。此查询可以在 `fresh` 会话或 `dangling` 终止会话上进行；见下文 `NewKey` 处理。确实，![image](images/a.jpg)^∗ 能够进行*终止后*密码测试的能力（这在 PAKE-EA 中依然保留，见[第 10.4.4 节](#c10.xhtml#sec10-4-4)）是基于模拟的 BMP 模型与 Canetti 等人 (2005) 的 UC PAKE 模型（见[第 10.5 节](#c10.xhtml#sec10-5)）之间的一个关键区别。

3.  对于任意会话 `P[i]`，对手 ![image](images/a.jpg)^∗ 可以向 ![image](images/f.jpg)`PAKE` 发送 (`NewKey`, `P`, `i,` `P`′, `j, sk*`^∗)，这模拟 `P[i]` 接收到最后一条协议消息（假定来自 ![image](images/ppj.jpg)）并终止并产生某个输出。作为响应，![image](images/f.jpg)`PAKE` 终止此会话并按如下方式决定其输出 `sk[i]`：

    a) 如果 `P[i]` 会话是 `compromised`，则设置 `sk[i]` ← `sk*`^∗。

    b) 如果 `P[i]` 和 ![image](images/ppj.jpg) 均为 `fresh`，`pw [P[i]]` = `pw [![image](images/ppj.jpg)]`，`pid[P[i]]` = `P`′ 且 `pid[![image](images/ppj.jpg)]` = `P`，![image](images/ppj.jpg) 和 `P[i]` 的 `role` 位将它们定义为先完成方和后完成方，并且 ![image](images/ppj.jpg) 输出了 `sk[j]`，则 `sk[i]` ← `sk[j]`。

    c) 否则设置 `sk[i]` ←[$] {0, 1}^(*κ*)，且如果 ![image](images/a.jpg)^∗ 请求，则将 `P[i]` 标记为 `dangling`。

4.  ![image](images/a.jpg)^∗ 还可以请求任意已终止会话 `P[i]` 的输出 `sk[i]`（因此不失一般性，可以假设所有 `sk[i]` 输出都发送给 ![image](images/a.jpg)^∗），并终止任意正在运行的会话 `P[i]` 使其输出 ⊥（这在真实世界中模拟了对 `P[i]` 的拒绝服务攻击）。

5.  每个 `P[i]` 的输入 `pw^i` 和输出 `sk[i]` 都被记录在理想世界交互记录 `transcriptideal[![image](images/a.jpg)^∗, ![image](images/f.jpg)PAKE]` 中，![image](images/a.jpg)^∗ 也可以在任何时刻向记录中添加任意消息，以模拟 ![image](images/a.jpg) 在真实世界协议中会接收和发送的消息。

### BMP 安全定义

鉴于上述真实世界和理想世界博弈的规则，PAKE 安全性的 BMP 定义如下：

**定义 10.3。** – *如果对于所有高效算法* ![image](images/a.jpg) *都存在一个高效算法* ![image](images/a.jpg)^∗ *使得*

![image](images/p228-1.jpg)

*即由* ![image](images/a.jpg) *和* Π *定义的真实世界博弈记录，与由* ![image](images/a.jpg)^∗ *和* ![image](images/f.jpg)`PAKE` *定义的理想世界博弈记录，在计算上是不可区分的。*

由于证明必须展示一个对任意 ![image](images/a.jpg) 都有效的算法 ![image](images/a.jpg)^∗，因此 ![image](images/a.jpg)^∗ 的一种自然构造是将 ![image](images/a.jpg) 作为*预言机*使用。由于 ![image](images/a.jpg) 期望与运行协议 Π 的真实世界 `P[i]` 交互，![image](images/a.jpg)^∗ 需要向 ![image](images/a.jpg) *模拟* 这些 Π 实例，即它需要创建与协议 Π 中 `P[i]` 的消息不可区分的消息。安全性证明的挑战在于 ![image](images/a.jpg)^∗ 必须仅凭 ![image](images/f.jpg)`PAKE` 提供的信息来完成此模拟，例如，这些信息不包含 `P[i]` 的输入 `pw`。然而，如果 ![image](images/a.jpg)^∗ 成功完成了这种模拟，那么 ![image](images/a.jpg) 必须像在真实世界博弈中那样回复这些模拟消息（除非以可忽略的概率区分出 ![image](images/a.jpg)^∗ 的模拟消息与 `P[i]` 的真实消息），并且如果 ![image](images/a.jpg)^∗ 将其发送给和从预言机 ![image](images/a.jpg) 接收到的所有消息都放入 `transcriptideal[![image](images/a.jpg)^∗, ![image](images/f.jpg)PAKE]` 中，则理想世界记录可以与真实世界记录不可区分。

### 10.4.2. BMP 定义的优势：任意密码、紧致安全性
