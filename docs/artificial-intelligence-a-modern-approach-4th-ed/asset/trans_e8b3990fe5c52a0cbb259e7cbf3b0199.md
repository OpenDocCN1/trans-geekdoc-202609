
# 语义语法与Transformer架构

## Transformer架构描述
Transformer架构用六行描述。底部第一行包含五个节点，每个节点标记为 `Embedding lookup`。句子的每个词进入底部行中的一个节点，且没有节点有两个词进入。第二行的五个节点标记为 `Positional Embedding 1`、`Positional Embedding 2`、`Positional Embedding 3`、`Positional Embedding 4` 和 `Positional Embedding 5`。每列第一行和第二行节点之间有一个加号。第三、四、五行标记为 `Transformer layer`。第二行五个节点的输出被送入第三行的 `Transformer layer`。第三行 `Transformer layer` 的输出被送入第四行的 `Transformer layer`。第四行 `Transformer layer` 的输出被送入第五行的 `Transformer layer`。第六行包含五个标记为 `Feedforward` 的节点。第五行 `Transformer layer` 的输出被送入第六行的五个节点。第一个 `Feedforward` 节点的输出为类别等于副词。第二个 `Feedforward` 节点的输出为类别等于代词。第三个 `Feedforward` 节点的输出为类别等于过去时动词。第四个 `Feedforward` 节点的输出为类别等于限定词。第五个 `Feedforward` 节点的输出为类别等于名词。

×![](images/Fig-347.jpg)

## 图24.10 算术表达式的语法
图24.10 一个增强了语义的算术表达式语法。每个变量 `xi` 代表一个成分的语义。

### 描述
该模型用四行描述，每行包含五个节点。底部第一行标记为 `Non-contextual representations (word embeddings)`。第一行中的每个节点标记为 `Embedding lookup`。句子的每个词进入底部行中的一个节点，且没有节点有两个词进入。第二行中的每个节点标记为 `RNN`。第一行中每个节点的输出输入到第二行中的一个 `RNN` 节点。第三行标记为 `contextual representations (RNN output)`。一列中 `RNN` 节点的输出输入到下一列的 `RNN` 节点，并输入到第三行对应列的节点。第四行中的每个节点标记为 `Feedforward`。第三行中每个节点的输出输入到第五行中的一个 `Feedforward` 节点。第一列 `Feedforward` 节点的输出为红色；第二列为汽车；第三列为；第四列为大；第五列为 open angle bracket e o s close angle bracket。

×![](images/Fig-348.jpg)

图24.11 字符串“3 + (4 ÷ 2)”的语义解释的解析树。

## 组合语义
现在让我们转向英语的语义，或者至少是其中一小部分。我们将使用一阶逻辑作为我们的语义表示。因此简单句子“Ali loves Bo”应得到语义表示 `Loves(Ali, Bo)`。那成分短语呢？我们可以用逻辑项 `Ali` 表示 NP “Ali”。但 VP “loves Bo”既不是逻辑项也不是完整的逻辑句子。直观上，“loves Bo”是一个描述，可能适用于某个特定的人，也可能不适用。（在这种情况下，它适用于 Ali。）这意味着“loves Bo”是一个谓词，当与表示人的项结合时，会产生一个完整的逻辑句子。

使用 λ 符号（参见 [第277页](#Chapter08-02.xhtml#page_277)），我们可以将“loves Bo”表示为谓词
`λx Loves(x, Bo)`。

现在我们需要一条规则，说明“语义为 n 的 NP 后跟语义为 pred 的 VP 会产生一个语义为 pred 应用于 n 的结果的句子：”
`S(pred(n))→NP(n) VP(pred)`。

该规则告诉我们，“Ali loves Bo”的语义解释是
`(λx Loves(x, Bo))(Ali)`，
这等价于 `Loves (Ali, Bo)`。从技术上讲，我们说这是 lambda 函数应用的 β 约简。

其余的语义可以从我们迄今为止所做的选择中直接推导出来。因为 VP 被表示为谓词，所以动词也应该是谓词。动词“loves”表示为 `λy λx Loves(x, y)`，即当给定参数 Bo 时，返回谓词 `λx Loves(x, Bo)` 的谓词。我们最终得到在 [图24.12](#Chapter24-04.xhtml#fig24-12) 中显示的语法和解析树。在更完整的语法中，我们会将所有增强（语义、格、人称-数和中心词）放在一起作为一组规则。这里我们只展示语义增强，以便更清楚地说明规则的工作原理。

### 描述
该模型由五行中的节点描述。底部第一行包含四个节点，每个节点标记为 `embedding lookup`。词 the 输入到第一个 `embedding lookup` 节点，river 输入到第二个 `embedding lookup` 节点，five 输入到第三个 `embedding lookup` 节点，feet 输入到第四个 `embedding lookup` 节点。第二行和第三行各包含五个节点，每个节点标记为 `RNN`。任意两个相邻的 `RNN` 节点之间存在两个方向相反的箭头。第一个 `embedding lookup` 节点的输出输入到第一个 `RNN` 节点，第二个 `embedding lookup` 节点输入到第二个 `RNN` 节点，第三个 `embedding lookup` 节点输入到第四个 `RNN` 节点，第四个 `embedding lookup` 节点输入到第五个 `RNN` 节点。Open square bracket masked close square bracket 输入到第三个 `RNN` 节点。第二行中每个 `RNN` 节点的输出输入到第三行对应列的 `RNN` 节点。第三行中第三个 `RNN` 节点的输出输入到第四行中标记为 `MLM embedding` 的节点。`MLM embedding` 节点的输出输入到第五行中标记为 `Feedforward` 的节点。`Feedforward` 节点的输出为词 rose。

×![](images/Fig-349.jpg)

图24.12(a) 一个可以推导出“Ali loves Bo”（以及另外三个句子）的解析树和语义解释的语法。每个范畴都用一个表示语义的单一参数增强。(b) 字符串“Ali loves Bo”的语义解释的解析树。

## 24.4.2 学习语义语法
不幸的是，`Penn Treebank` 不包含其句子的语义表示，只包含句法树。因此，如果我们要学习语义语法，我们将需要不同的示例来源。Zettlemoyer 和 Collins (2005) 描述了一个系统，该系统从由句子与其语义形式配对而成的示例中学习问答系统的语法：
•句子: What states border Texas?
•逻辑形式: `λx.state(x) ∧ λx.borders(x, Texas)`

给定大量类似的配对以及每个新领域的一点手工编码知识，系统会生成合理的词法条目（例如，“Texas”和“state”是名词，使得 `state(Texas)` 为真），并同时学习语法参数，使系统能够将句子解析为语义表示。Zettlemoyer 和 Collins 的系统在两个不同的未见句子测试集上达到了 79% 的准确率。Zhao 和 Huang (2015) 展示了一种运行更快的 `shift-reduce` 解析器，其准确率达到 85% 至 89%。

这些系统的局限性在于训练数据包含逻辑形式。这些创建成本很高，需要具有专业知识的人工标注者——并非每个人都理解 lambda 演算和谓词逻辑的细微差别。收集问答对示例要容易得多：
•问题: What states border Texas?
• 答案 : Louisiana, Arkansas, Oklahoma, New Mexico.
•问题: How many times would Rhode Island fit into California?
•答案: 135
