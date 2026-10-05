
> 2 为了简便起见，我们假设一个人只说一种语言。显然，对于瑞士和印度等国家，该规则必须经过修正。

## 20.4 节 使用相关信息学习

如 (20.6) 所示句子代表了严格的相关性：语言被完全确定了。（换句话说：语言是国族的函数。）这些被称为函数依赖或确定关系。它们在某些应用程序（例如设计数据库系统）中非常常见，因此使用特殊的语法来编写。我们采用 Davies (1985) 的概念：

`Nationality(x,n) > Language(x,l)`

像通常一样，这是一种语法糖，但它明确了这种确定是谓词之间的事实：国籍决定语言。决定导电性的相关属性可以类似地表示：

`Material(x,m) > Temperature(x,t) > Conductance(x,ρ)`

`Material(x,m) > Temperature(x,t) > Determination(x,d)`.

相应的泛化从确定和观察中逻辑导出。

### 20.4.1 确定假设

虽然确定许可了关于所有巴西人或给定温度下所有铜的结论，但无法通过单个示例产生适用于所有国籍或所有材料的预测理论。它们的主要作用是限制学习代理所需的假设大小。例如，在预测导电性时，只需要考虑材料和温度，而忽略质量、所有权等。假设可以包含由材料和温度决定的项，例如分子结构、热能或自由电子密度。确定指定了用于构造目标谓词假设的特定词汇。这一结论可以通过证明给定确定与使用左侧所有谓词定义的逻辑逻辑等来得出。

直观地说，缩小假设的大小更容易学习谓词。利用计算学习理论的基础，首先回想布尔函数需要 `log(|H|)` 个示例来收敛到一个假设，其中 `|H|` 是假设空间的大小。如果学习者有 `n` 个布尔特征来构造假设，那么在没有进一步限制的情况下，`|H|=O(2ⁿ)`，示例的数量为 `O(2ⁿ)`。如果确定左侧包含 `d` 个谓词，学习者只需要 `O(2ⁿᵈ)` 个示例。

### 20.4.2 学习与相关信息

正如本章引言所述，先验知识在学习中是有用的；但它也必须被学习。为了提供相关性学习的完整描述，我们提供一种确定关系的学习算法。我们现在提出的学习算法基于一种简单的方法，寻找与观察结果一致的最简单确定关系。如果一组示例中的每对在左侧谓词匹配的同时，在目标谓词上也匹配，则该确定关系与该集合一致。

# 第20章 学习中的知识

```python
function MINIMAL-CONSISTENT-DET(E,A) returns a set of attributes
  inputs: E, a set of examples
          A, a set of attributes, size n
  for i = 0 to n do
    for each subset A_i of A of size i do
      if CONSISTENT-DET?(A_i,E) then return A_i
```

```python
function CONSISTENT-DET?(A,E) returns a truth value
  inputs: A, a set of attributes
          E, a set of examples
  local variables: H, a hash table
```

for each example `e` in `E`
if some example in `H` has the same values as `e` for the attributes `A`
but a different classification return false
store the class of `e` in `H`, indexed by the values for attributes `A` of the example `e`
return true

图 20.8 一种寻找最小一致性决定的算法。

例如，假设我们有以下关于材料样本导电率的示例：

| 样本 | 质量 | 温度 | 材料 | 尺寸 | 导电率 |
|---|---|---|---|---|---|
| S1 | 12 | 26 | 铜 | 3 | 0.59 |
| S2 | 12 | 100 | 铜 | 3 | 0.57 |
| S3 | 24 | 26 | 铜 | 6 | 0.59 |
| S3 | 12 | 100 | 铅 | 2 | 0.05 |
| S4 | 24 | 26 | 铅 | 4 | 0.04 |

最小一致性判定与导电率不一致。这是因为示例中的尺寸和确定密度是一致的，而在我们的集合中，有两个相同密度的不同材料。按照惯例，我们需要一个更大的集合来消除一个接近正确的假设。

有几种可以寻找最小一致性决定的可能算法。最明显的方法是在判定空间中进行搜索，检查所有具有一个谓词、两个谓词等等的判定，直到找到一个一致的判定。我们将假设使用基于属性的表示法，这就像第 19 章中用于决策树学习的方法一样。判定 `d` 将由左侧的属性集表示，因为目标谓词被假设是固定的。算法概述如图 20.8 所示。

该算法的时间复杂度取决于最小一致性判定的规模。假设该判定在 `n` 个总属性中具有 `p` 个属性。那么该算法在搜索到 `A` 的大小为 `p` 的子集之前是找不到。有 `\binom{n}{p} = O(n^p)` 个这样的子集；然而，该算法相对于最小判定的规模呈指数级增长。事实证明该问题是 NP-完全的，因此我们无法期望在一般情况下获得更好的结果。在大多数领域中，会有足够的局部结构（局部结构化域的定义见第 13 章），`p` 是很小的。

## 第 20.4 节 使用相关性信息进行学习

![](img/e36752d03ef5263fc4a8dddbd735be2d_756_0.png)

**图 20.9** `DECISION-TREE-LEARNING` 和 `RBDTL` 在随机生成的数据上的性能比较，该目标函数仅依赖于 16 个属性中的 5 个。

本节浅介绍了声明性偏置（declarative bias）领域，以理解如何利用先验知识来识别合适的假设空间，并在其中搜索正确的目标定义。有许多未解决的问题：

- 如何扩展算法以处理噪声？
- 我们能处理连续值变量吗？
- 除了判定外，还可以如何使用其他类型的先验知识？
- 如何将算法泛化以涵盖任何一阶理论，而不仅仅是基于属性的表示？

这些问题中的一些将在下一节中讨论。

## 20.5 归纳编程

归纳编程（ILP）将归纳方法与一阶表示结合起来。它之所以流行有三个原因：首先，ILP 提供了一种解决基于知识问题的严谨方法。其次，ILP 可以从示例中推导出通用的逻辑理论，这在学习蛋白质结构方面是非常有效的。例如，图 20.10 中的蛋白质三维配置无法通过属性来合理表示。第三，逻辑系统产生的假设对于人类来说易于阅读。这种逻辑表示可以被生物学家审查和批判。对于神经网络等“黑盒”分类器，这种参与是不可能的。

### 20.5.1 示例

回顾方程 (20.5)，基于知识的归纳过程是为了“解决”

> `Background \wedge Hypothesis \wedge Descriptions`

对于已知的假设 `Hypothesis`，给定 `Background` 和 `Descriptions` 来学习对象之间的关系。为了说明这一点，我们将使用图 20.11 所示的家族树，其描述包含了母亲、父亲和婚姻等属性。这些描述如下：

- `Father(Philip, Charles)` `Father(Anne)`
- `Mother(Mum, Margaret)` `Mother(Elizabeth)`
- `Married(Diana, Charles)` `Married(Elizabeth)`
- `Male(Philip)` `Male(Charles)`
- `Female(Beatrice)`

归纳学习程序的目标是产生一组句子，以满足一致性约束。此时可能会参考第 7 章以了解 Horn 子句、合取范式、合一和求解。

## 第 20.5 节

![](img/e36752d03ef5263fc4a8dddbd735be2d_758_0.png)

**图 20.10** (a) 和 (b) 分别显示了蛋白质折叠领域中“四螺旋束”概念的正例和负例。每个示例结构都被编码为学习一个包含约 100 个合取式的表达式，如 `TotalLength(D2mr,118) \wedge NumberHelices(D2mr,6) \wedge \dots`。从这些描述和分类 `Fold(FOUR-HELICAL-AND-BUNDLE,D2mr))` 中，ILP 系统 `PROGOL` 学习了以下规则：

```python
Fold(FOUR-HELICAL-AND-BUNDLE,p) \leftarrow\nHelix(p,h1) \wedge Length(h1,H1) \wedge Position(p,h1,n)\n\(1 \leq n \leq 3) \wedge Adjacent(h1,h2) \wedge Helix(h2).
```

这种规则可以通过我们在之前章节中基于属性的机制来学习或表示。该规则可以翻译成英文：“如果蛋白质 `p` 在二级结构位置 1 到 3 之间包含长螺旋 `h1`，且 `h2` 与之相邻，则它具有‘四螺旋束’类。”

代理没有背景知识：背景知识是空的。那么假设的一个可能解是：

```python
Grandparent(x,y) \leftarrow\n\[z Mother(x,z) \wedge Mother(z,y)]\nV\[z Mother(x,z) \wedge Father(z,y)]\nV\[z Father(x,z) \wedge Mother(z,y)]\nV\[z Father(x,z) \wedge Father(z,y)].
```

注意，基于属性的学习算法（如 `DECISION-TREE-LEARNING`）在解决这个问题上将无无进展。为了将 `Grandparent` 表示为一种属性（即一元谓词），我们需要将人的对转换为对象：

# 第 20 章 学习中的知识

`Grandparent((Mum, Charles))`.

我们随后陷入了尝试表示示例描述的困境。唯一可能的属性是一些极其糟糕的属性，例如

`FirstElementsMotherOfElizabeth((Mum, Charles))`.

基于这些属性的 `Grandparent`（祖父母）定义变成了大量特定情况的析取，而无法泛化到所有属性。基于属性的学习算法无法学习关系谓词。因此，ILP 算法的主要优势之一是它们适用于更广泛的问题，包括关系性问题。

读者一定会注意到，少量的背景知识将有助于 `Grandparent` 定义的表示。例如，如果背景知识（`Background`）中包含以下句子：

```
Parent(x,y) <=> Mum(x,y) ∨ Father(x,y)
```

那么 `Grandparent` 的定义将被简化为：

```
Grandparent(x,y) <=> [∃z Parent(x,z) ∧ Parent(y,z)].
```

这展示了背景知识如何大幅减少解释观测结果所需的假设规模。

ILP 算法还可能创建新的谓词来辅助解释性假设的表达。考虑到之前所示示例，ILP 程序产生一个额外的谓词（我们称之为“`Parent`”）以简化目标谓词是完全合理的。生成新谓词的算法被称为构造归纳（constructive induction）。显然，构造归纳是累积学习图景中不可或缺的一部分。它是机器学习中最困难的问题之一，但某些 ILP 技术为实现它提供了有效机制。

在本章的剩余部分中，我们将学习 ILP 的两种主要方法。第一种使用基于逆转解析证明的技术。

![](img/e36752d03ef5263fc4a8dddbd735be2d_759_0.png)

图 20.11 一个典型的家族树。

# 第 20.5 节 归纳逻辑编程

## 20.5.2 自上而下的归纳方法

ILP 的方法是从一个非常通用的规则开始，逐渐特化以适应数据。这本质上是决策树学习中发生的情况，即决策树逐渐生长直到它与观测结果一致。对于 ILP，我们使用一阶文字（first-order literals）而不是子句（clauses），假设是子句集而不是决策树。本节描述了 `FOIL` (Quinlan, 1990)，最早的 ILP 程序之一。

假设我们正尝试学习 `Grandfather(x,y)`（祖父）的定义，使用与之前相同的家族数据。在决策树学习中，我们可以将示例分为正例和负例。正例是：

- `(George,Anne)`, `(Philip,Peter)`, `(Spencer,Harry)`, ...
- `(George,Elizabeth)`, `(Harry,Zara)`, `(Charles,Philip)`, ...

负例是：

注意，每个示例都是对象对，其中 `Grandfather` 是一个二元谓词。家族树中总共有 12 个正例和 388 个负例（所有其他人类组合）。

`FOIL` 构建一个以 `Grandfather(x,y)` 为头部的子句集。头部必须将这 12 个示例归类为 `Grandfather(x,y)` 关系的实例，同时排除那 388 个负例。这些子句是 Horn 子句（Horn clauses），其扩展允许在子句的体部允许否定文字，并在 Prolog 中使用“失败即否定”（negation as failure）进行解释。初始子句有一个空的体部：

> `⇒ Grandfather(x,y).`

该子句分类了每一个正例，因此它需要被特化。我们通过向左侧一次添加一个文字来实现这一点。这里是三种可能的添加项：

- `Father(x,y) ⇒ Grandfather(x,y)`
- `Parent(x,z) ⇒ Grandfather(x,y)`
- `Father(x,z) ⇒ Grandfather(x,y)`.

（注意，我们假设定义 `Parent` 的子句已经是背景知识的一部分。）这三个子句中的第一个归类了所有 12 个正例，可以忽略。第二个和第三个与所有正例一致，但第二个涵盖的负例比例更大——多出两倍，因为它包含了母亲也包含了父亲。在这里，我们更倾向于选择第三个子句。

现在我们需要特化这个子句，以排除 `x` 是某些 `z` 的父亲但 `z` 不是父亲的情况。通过添加单个文字 `Father(z,y)`，可以正确地归类所有示例。`FOIL` 将找到并选择这个文字，从而解决该任务。通常情况下，解决方案是一组 Horn 子句，每个子句都推导出目标谓词。例如，如果我们的词汇表中没有 `Father` 谓词，这种解决方案可能是：

- `Father(x,z) ∧ Grandfather(x,y)`
- `Father(x,z) ⇒ Mother(z,y)`.

注意，这些子句中的每一个涵盖了更多的正例，它们涵盖了所有正例，且 `NEW-CLAUSE` 的设计使得没有子句能成功覆盖一个负例。

```python
function FOIL(examples,target) returns a set of Horn clauses
  inputs: examples, set of examples
          target, literal for the goal
  local variables: clauses, set of clauses, initially empty
  while examples contains positive examples do
    clause <- NEW-CLAUSE(examples,target)
    remove positive examples covered by clause
    add clause to clauses
  return clauses
```

```python
function NEW-CLAUSE(examples,target) returns a Horn clause
  local variables: clause, a clause with head and an empty body
                   l, a literal to be added to the clause
                   extended_examples, set of examples with values for new variables
  extended_examples <- examples
  while examples contains negative examples do
    clause <- CHOOSE-LITERAL(clause,extended_examples)
    append to the body of clause
    extended_examples <- set of examples created by applying EXTEND-EXAMPLE to each example in extended_examples
  return clause
```

```python
function EXTEND-EXAMPLE(example, literal) returns a set of examples
  if example satisfies literal
  then return the set of examples created by extending with possible constant value for new variable in literal
  else return the empty set
```
