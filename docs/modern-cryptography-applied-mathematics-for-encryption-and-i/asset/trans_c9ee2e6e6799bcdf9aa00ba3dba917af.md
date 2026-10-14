
![image](Images/image00484.jpeg) `Axiom` 一个公理（或 `premise` 或 `postulate`）是被假设为真的东西。本质上，你必须从某处开始。现在你可以像哲学家笛卡尔那样开始说：“我思故我在”（`Cogito ergo sum`），但这在大多数数学目的上并不实用。因此，我们从一些由定义本身就是真的公理开始。例如，任何只能被它本身和 1 整除的整数被认为是质数。

![image](Images/image00484.jpeg) `Statement` 这是一个简单的声明，表示某事为真。例如，“3 是质数”是一个声明，而“16 是 3 的立方”也是一个声明——它是错误的，但仍然是一个声明。

![image](Images/image00484.jpeg) `Argument` 一个论证是一系列声明的集合。其中一些声明，即前提，被假设为真并作为接受论证中另一个声明（即结论）的基础。

![image](Images/image00484.jpeg) `Proposition` 这是最基本的声明。命题是一个要么为真要么为假的声明。例如，如果我告诉你我要么是男性要么是女性，这是一个命题。如果我接着说我不是女性，这是另一个命题。如果你遵循这两个命题，你就会得出结论：我是男性。有些陈述没有真值，因此不能是命题。例如，“停止做那事！”没有真值，因此不是命题。

形式逻辑的令人兴奋之处在于，如果你从一个为真且忠实遵循逻辑规则的前提开始，那么你会得出一个为真的结论。从公理推导出结论是 `deductive reasoning`（演绎推理），这是数学证明中常用的推理方式。`Inductive reasoning`（归纳推理）是从前提进行概括。归纳推理可能因过度概括而出错。本书将专注于演绎逻辑。

###### Propositional Logic（命题逻辑）

你读过命题的定义，可能会回想到数学逻辑关注的是论证的结构，而非内容。这导致了教科书中常用的呈现方式——即忽略实际陈述，用字符代替。通常，`p` 和 `q` 用作占位符，它们可以代表你想要表达的任何命题。例如，`p` 可能表示“本书作者有灰色胡须”，而 `q` 可能表示“本书作者没有面部毛发”。在这两个命题的基础上，很可能有

              Either `p` or `q` is true.

              It is impossible that `p` and `q` are both true.

              It is possible that not `p` is true.

              It is possible that not `q` is true.

可以为这些陈述（以及你想要表达的其他陈述）使用符号。重要的是，你要熟悉基本逻辑符号。[Table 4-1](#part0012.xhtml#ch04tab01) 提供了演绎逻辑中最常用符号的说明。

**TABLE 4-1    Symbols Used in Deductive Logic**

![Images](Images/image00576.jpeg)

[Table 4-1](#part0012.xhtml#ch04tab01) 并非逻辑符号的完整列表，但这些是最常用的符号。在继续本节的其余部分之前，请确保你熟悉这些符号。

其中一些符号被称为 `connectives`（连接词），这意味着它们用于连接两个命题。下面给出了一些关于连接词的基本规则，如同 [Table 4-2](#part0012.xhtml#ch04tab02) 所示。

**TABLE 4-2    Connectives**

![Images](Images/image00577.jpeg)

以下是关于连接词的一些基本事实：

  ![image](Images/image00484.jpeg) `Expressions`（表达式）在连接词两侧被称为 `conjuncts`（合取数） (`p ∧ q`)。

  ![image](Images/image00484.jpeg) `Expressions`（表达式）在连接词两侧被称为 `disjuncts`（析取数） (`p ∨ q`)。

  ![image](Images/image00484.jpeg) 在蕴含 `p ⇒ q` 中，`p` 被称为 `antecedent`（前件），`q` 被称为 `consequence`（后件）。

  ![image](Images/image00484.jpeg) 与连接词的优先级顺序是：括号、否定、合取、析取、蕴含。

###### Building Logical Constructs（构建逻辑构造）

现在你已经熟悉了演绎逻辑的基本概念，并掌握了必要的符号，让我们练习将一些文本陈述转换为逻辑结构。这是应用逻辑以判断陈述真伪的第一步。考虑以下示例句子：

              Although both John and Paul are amateurs, Paul has a better chance of winning the golf game, despite John’s significant experience.

我们现在用演绎逻辑的语言来重述这句话。首先，我们需要将这段长句拆解为单独的命题并为每个命题分配变量：

              `p`: John is an amateur

              `q`: Paul is an amateur

              `r`: Paul has a better chance of winning the golf game

              `s`: John has significant golf experience

我们现在可以用符号表达这个句子：

`(p ∧ q) ∧ r ∧ s`

这个句子不容易直接推导出真值，但它很好地展示了如何将句子转换为逻辑符号。

###### Truth Tables（真值表）

一旦你掌握了命题和连接词的基本概念，下一步就是熟悉真值表。真值表提供了一种可视化命题真值的方法。

下面是一个简单的例子。请记住，实际陈述本身并不重要，重要的是结构。但如果这有助于你理解概念，`P` 可以是命题“你正在阅读这本书”。

![Images](Images/image00578.jpeg)

这个表告诉我们，如果 `P` 为真，那么 `¬P` 不可能为真。同时，如果 `P` 为假，那么 `¬P` 为真。这个例子很简单，甚至有点琐碎。这个真值表只是形式化、直观地告诉你：要么你在阅读这本书，要么你不在，两者不能同时为真。

虽然这个例子看似微不足道，你可能会想，为什么还要用真值表来展示这么明显的事实？实际上，你可能不会用真值表来展示这个例子。不过，由于大多数人很容易理解“某事要么为真要么为假”这一事实，这成为学习真值表的良好起点。几分钟后你将看到一些不那么平凡的表格。

接下来，我们来看一个稍微复杂一些的真值表，它引入了合取（`∧`）的概念。具体命题的内容并不重要。这个真值表说明了只有当 `p` 为真且 `q` 为真时，`p ∧ q` 才为真。

![Images](Images/image00579.jpeg)

下面是一个关于析取（`∨`，即“或”）运算符的真值表。

![Images](Images/image00580.jpeg)

你可以看到，这个表清楚地表明了前面关于“或”（析取）连接词的描述。

`exclusive or`（异或）运算也很有趣，可以用真值表观察。回顾我们之前说明：要么 `p` 为真，要么 `q` 为真，但不能同时为真。

![Images](Images/image00581.jpeg)

接下来，我们来看蕴含（`→`）的真值表。考虑 `p → q`。这读作“`p` 蕴含 `q`”。

**Tip**

在逻辑中，术语 `implies`（蕴含）比日常用语更强。这里它的意思是：如果你拥有 `p`，那么你必然拥有 `q`。

![Images](Images/image00582.jpeg)

前面的真值表虽然看似显而易见，不需要详细解释，但这一个表可能需要一点讨论：

  ![image](Images/image00484.jpeg) `The first row`（第一行）应该对你有意义。如果我们在陈述“`p` 蕴含 `q`”，并且发现 `p` 为真且 `q` 为真，那么我们的陈述“`p` 蕴含 `q`”是真。

  ![image](Images/image00484.jpeg) `The second row`（第二行）也很明显。如果 `p` 为真但 `q` 为假，那么“`p` 蕴含 `q`”就不可能为真。

