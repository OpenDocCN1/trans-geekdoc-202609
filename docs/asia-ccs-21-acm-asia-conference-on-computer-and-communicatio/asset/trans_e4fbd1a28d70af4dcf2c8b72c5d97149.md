
**算法 1** Eth2Vec 的一次 epoch 的训练算法 TRAIN

**要求：** Dict
**保证：** 任意 `in_j` 的 token 的向量表示和 \(\vec{\theta}_{f_s}\)

1. **对所有** \(C_i \in Dict\) **做**
2.     **对所有** \(f_s \in \mathcal{U}(C_i)\) **做**
3.         **对所有** \(seq_i \in \mathcal{S}(f_s)\) **做**
4.             **对所有** \(in_j \in \mathcal{I}(seq_i)\) **做**
5.                 将 \(f_s\) 向量化为 \(\vec{\theta}_{f_s}\)
6.                 根据公式 (3) 计算 \(\mathcal{CT}(in_{j+1})\)
7.                 根据公式 (3) 计算 \(\mathcal{CT}(in_{j-1})\)
8.                 根据公式 (4) 计算 \(\delta(in_j,f_s)\)
9.                 **对所有** \(t_c \in \mathcal{T}(in_j)\) **做**
10.                    根据公式 (7) 计算 \(\vec{\theta}_{f_s}\) 的梯度
11.                    根据公式 (8) 计算 \(\vec{v}_{t_c}\) 的梯度
12.                    根据公式 (9) 计算 \(\vec{v}_{\mathcal{P}(j+1)}\) 的梯度
13.                    根据公式 (10) 计算 \(\vec{v}_{\mathcal{A}(in_{j+1})}\) 的梯度
14.                    根据公式 (9) 计算 \(\vec{v}_{\mathcal{P}(j-1)}\) 的梯度
15.                    根据公式 (10) 计算 \(\vec{v}_{\mathcal{A}(in_{j-1})}\) 的梯度
16.                **结束循环**
17.                更新 \(in_j\) 的 token 的向量
18.                更新 \(\vec{\theta}_{f_s}\)
19.            **结束循环**
20.        **结束循环**
21.    **结束循环**
22. **结束循环**

**算法 2** Eth2Vec 的查询推理算法 Infer

**要求：** 合约 \(C_t \notin Dict\)
**保证：** 任意 \(f_t \in \mathcal{U}(C_t)\) 的向量表示 \(\vec{\theta}_{f_t}\)

1. 初始化 \(f_t \in \mathcal{U}(C_t)\) 的向量表示 \(\vec{\theta}_{f_t}\)
2. **对所有** \(f_t \in \mathcal{U}(C_t)\) **做**
3.     **对所有** \(seq_i \in \mathcal{S}(f_t)\) **做**
4.         **对所有** \(in_j \in \mathcal{I}(seq_i)\) **做**
5.             根据公式 (3) 计算 \(\mathcal{CT}(in_{j+1})\)
6.             根据公式 (3) 计算 \(\mathcal{CT}(in_{j-1})\)
7.             根据公式 (4) 计算 \(\delta(in_j,f_t)\)
8.             **对所有** \(t_c \in \mathcal{T}(in_j)\) **做**
9.                 根据公式 (7) 计算 \(\vec{\theta}_{f_t}\) 的梯度
10.                更新 \(\vec{\theta}_{f_t}\)
11.            **结束循环**
12.        **结束循环**
13.    **结束循环**
14. **结束循环**

## 4.6 实现

我们利用 Kam1n0（版本 2.0.0：https://github.com/McGill-DMaS/Kam1n0-Community）和 py-solc-x（https://pypi.org/project/py-solc-x/）实现了 Eth2Vec。首先，主要模块 PV-DM 模型由 Kam1n0 实现，Kam1n0 是一个用于二进制分析 [11] 的服务器系统 [10]。我们主要修改了 DisassemblyFactoryIDA.java 和 ExtractBinaryViaIDA.py 中的源代码。特别是，ExtractBinaryViaIDA.py 最初通过反汇编二进制代码从 IDA 生成提取的 JSON 文件，然后 DisassemblyFactoryIDA.java 接收该文件以将二进制代码存储在 Kam1n0 中。然而，IDA 不能使用 EVM 字节码来实现 Eth2Vec。因此，我们更改了 ExtractBinaryViaIDA.py。例如，代码信息是通过使用 py-solc-x 编译 Solidity 文件而无需 IDA 获得的，然后提取其生成的汇编代码、抽象语法树（AST）和二进制代码。

同时，当前的输出显示遵循 Kam1n0 的接口；漏洞按每个合约的函数级别列出。特别是，测试合约的漏洞会显示其置信度。我们在附录 A 中展示了 Eth2Vec 的输出示例。

我们通过 GitHub（https://github.com/fseclab-osaka/eth2vec）公开发布了整个实现的源代码。

## 5 实验

在本节中，我们描述了为评估 Eth2Vec 而进行的实验。首先，我们描述实验的目的。然后，我们讨论用于评估的数据集和训练方法。最后，我们展示实验结果。

### 5.1 实验目的

为了评估 Eth2Vec 的性能，我们尝试通过使用已知存在漏洞的合约进行训练来检测待分析代码中的漏洞。为此，我们首先检查 Eth2Vec 是否能够适当表示待分析代码与训练阶段学习到的代码之间的关系。我们评估 Solidity 语言代码的克隆检测，以确认 Eth2Vec 是否能够适当提取代码的特征。在此过程中，我们还基于词法-语义关系评估语义克隆，以确认 Eth2Vec 对代码重写的鲁棒性。

接下来，我们检查是否通过训练代码及其与给定代码的代码相似性来识别所有学习到的漏洞。在此过程中，我们还评估漏洞检测与上述克隆检测结果的一致性。特别是，我们检查漏洞检测的输出是否与被识别为克隆的代码中的漏洞相同，以及克隆是否包含在克隆检测输出中。

我们确认 Eth2Vec 可以精确地提取特征，从而可以通过上述实验检测漏洞。我们还将 Eth2Vec 的性能与 Momeni 等人 [31] 的现有工作进行比较，后者手动提取特征，作为基线。

### 5.2 实验设置

如上所述，实验分为两个阶段，即智能合约的克隆检测和漏洞检测。我们将在下面描述每个实验的设置。我们首先详细描述数据集和基线。

**5.2.1 数据集。**

我们从 Etherscan（https://etherscan.io/）收集了 5,000 个合约文件作为实验中使用的数据集，该数据库是智能合约的开放数据库。这 5,000 个文件也与近期工作 [15] 中使用的文件相同。然后我们仅使用可以用 Solidity 版本 0.4.11 作为编译器编译的文件。数据集包含 95,152 个合约和 1,193,868 个区块。

**5.2.2 基线。**

我们将 Eth2Vec 的性能与 Momeni 等人 [31] 基于支持向量机（SVM）的方案进行比较作为基线。尽管基于机器学习的几种通用结果 [15, 26, 48] 可以检测各种漏洞，但其源代码未发布或我们无法在我们的环境中构建其源代码。因此，我们采用了 Momeni 等人提出的 SVM 方法，我们能够从头开始重现。

Momeni 等人从以太坊智能合约的抽象语法树（AST）中提取了 16 个特征。我们使用了其中 15 个特征，排除了十六进制地址，因为十六进制地址无法从源代码中获得，即在未部署的情况下。其他特征在附录 B 中描述。

**5.2.3 克隆检测。**

我们检查 Eth2Vec 是否能够通过训练合约精确检测作为输入的测试合约的克隆。特别是，在 10 折交叉验证中，随机选择 500 个测试合约，其余 4,500 个合约用作训练合约。此过程重复 10 次。同时，用于检测克隆的代码相似度阈值为 0.8。

在上述设置中，精度被用作评估指标。对于每个函数的克隆，即函数级克隆，以超过 0.8 的阈值输出，我们检查合约中相似度最高的函数是否确实是给定输入的克隆。为了比较 Eth2Vec 的性能，我们还通过手动标记每个函数来评估上述 SVM 方法。同时，本实验中的克隆对应于文献 [38] 中的 type-I 至 type-IV 克隆，而语义克隆与 type-IV 克隆相同。

**5.2.4 漏洞检测。**

我们检查 Eth2Vec 是否能够通过学习训练合约精确检测作为输入的测试合约中的漏洞。特别是，我们检查 Eth2Vec 以 0.8 的阈值输出的测试合约的漏洞是否与合约中的真实漏洞相同。

### 5.3 克隆检测结果

Eth2Vec 的克隆检测结果如表 1 所示。根据该表，Eth2Vec 可以隐式提取比 SVM 方法 [31] 更多的特征。例如，Eth2Vec 的标准差值明显小于 SVM 方法的值。直观地说，这意味着 Eth2Vec 的特征提取更稳定，因此 Eth2Vec 能够在各种代码上表示特征。

**表 1：Eth2Vec 的克隆检测精度。** 本表显示了 10 折交叉验证中 10 次精度测量执行的平均值和标准差。“SVM w/o few clones”列显示了通过移除具有少量克隆的测试数据集计算的 SVM 设置的结果。数字截断到一位小数。

|  | Eth2Vec | SVM [31] | SVM w/o few clones |
|---|---|---|---|
| 平均值 | 74.9% | 34.6% | 42.7% |
| 标准差 | 0.9 | 34.6 | 43.6 |

当克隆检测性能与 EClone [26] 作为参考进行比较时，EClone 在阈值为 0.4 时的检测率为 58.2%。尽管如第 5.2.2 节所述，我们没有自行实现 EClone，但我们相信由于其更复杂的特征提取，Eth2Vec 可以比 EClone 更好地检测以太坊智能合约的克隆。

当我们详细检查 Eth2Vec 的输出时，它包含语义克隆。我们在清单 1 和清单 2 中展示了一个具体示例。Eth2Vec 的输出，即清单 2，是原始函数所示清单 1 的克隆，排除了第 5 行和第 9 行。根据 [38] 中的定义，清单 2 与清单 1 相同为 type-III 克隆。这意味着 Eth2Vec 可以精确检测克隆，即使是重写后的代码。

**清单 1：Transfer 的原始函数**

```solidity
function _transfer(address _from, address _to, uint _value) internal {
    require(_to != 0x0);
    require(balanceOf[_from] >= _value);
    require(balanceOf[_to] + _value > balanceOf[_to]);
    uint previousBalances = balanceOf[_from] + balanceOf[_to];
    balanceOf[_from] -= _value;
    balanceOf[_to] += _value;
    Transfer(_from, _to, _value);
    assert(balanceOf[_from] + balanceOf[_to] == previousBalances);
}
```

**清单 2：Eth2Vec 找到的 Transfer 原始函数的克隆**

```solidity
function _transfer(address _from, address _to, uint _value) internal {
    require(_to != 0x0);
    require(balanceOf[_from] >= _value);
    require(balanceOf[_to] + _value > balanceOf[_to]);
    balanceOf[_from] -= _value;
    balanceOf[_to] += _value;
    Transfer(_from, _to, _value);
}
```

SVM 的标准差尤其是比 Eth2Vec 大得多，因为检测每个克隆的准确度差异过大。具体来说，SVM 以 91.3% 的精度检测到一个克隆。另一方面，SVM 以 0% 的精度检测到另一个克隆。特别是，以 0% 精度检测到的克隆的比例很高，然后 SVM 的平均值低于 SVM 的标准差。同时，SVM 方法的精度较小，因为在多次执行中测试数据集包含的克隆很少。SVM 方法推断负值用于
