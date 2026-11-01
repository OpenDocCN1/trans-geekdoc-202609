
FOIL 及其相关方法已被用于学习各种各样的定义。其中最令人印象深刻的演示之一（Quinlan and Cameron-Jones, 1993）涉及解决 Bratko（1986）Prolog 教科书中关于列表处理函数的一系列练习。在每种情况下，程序都能够从一组小的示例中学习到函数的正确定义，并将之前学习到的函数用作背景知识。

## 20.5.3 反向演绎的归纳学习

ILP 的第二种主要方法涉及反转正常的演绎证明过程。逆向归结基于以下观察：如果示例 `Classifications` 由 `Background ∧ Hypothesis ∧ Descriptions` 推出，那么必须能够通过归结来证明这一事实（因为归结是完备的）。如果我们能“反向运行证明”，那么就可以找到一个 `Hypothesis` 使证明成立。关键在于找到一种反转归结过程的方法。

*逆向归结*

我们将展示逆向归结的反向证明过程，它由单独的反向步骤组成。回想一下，普通的归结步骤取两个子句 `C1` 和 `C2` 并将它们归结以产生归结式 `C`。逆向归结步骤取一个归结式 `C` 并产生两个子句 `C1` 和 `C2`，使得 `C` 是对 `C1` 和 `C2` 归结的结果。或者，它可以取一个归结式 `C` 和子句 `C1` 并产生一个子句 `C2`，使得 `C` 是对 `C1` 和 `C2` 归结的结果。

逆向归结过程的早期步骤在 [图 20.13](#Chapter20-05.xhtml#fig20-13) 中显示，其中我们关注正例 `Grandparent(George, Anne)`。该过程从证明的末尾开始（显示在图的底部）。我们取归结式 `C` 为空子句（即矛盾），而 `C2` 为 `¬Grandparent(George;Anne)`，它是目标示例的否定。第一个逆向步骤取 `C` 和 `C2` 并为 `C1` 生成子句 `Grandparent(George, Anne)`。下一步将该子句作为 `C`，将子句 `Parent(Elizabeth, Anne)` 作为 `C2`，并生成子句

![Fig-303.jpg](images/Fig-303.jpg)

图 20.13 逆向归结过程的早期步骤。阴影子句由右侧子句和下方子句的逆向归结步骤生成。非阴影子句来自 Descriptions 和 Classifications（包括否定 Classifications）。

`¬Parent(Elizabeth, y) ∨ Grandparent(George, y)`

作为 `C1`。最后一步将该子句视为归结式。以 `Parent(George, Elizabeth)` 作为 `C2`，一个可能的子句 `C1` 是假设

`Parent(x, z) ∧ Parent(z, y) ⇒ Grandparent(x, y)`。

现在我们有一个归结证明，表明假设、描述和背景知识蕴含分类 `Grandparent(George, Anne)`。

显然，逆向归结涉及搜索。每个逆向归结步骤都是非确定性的，因为对于任意 `C`，可能存在许多甚至无限多个归结为 `C` 的子句 `C1` 和 `C2`。例如，在 [图 20.13](#Chapter20-05.xhtml#fig20-13) 的最后一步中，而不是为 `C1` 选择 `¬Parent(Elizabeth,y) ∨ Grandparent(George,y)`，逆向归结步骤可能选择以下任何句子：

```
¬Parent(Elizabeth,Anne) ∨ Grandparent(George,Anne).
¬Parent(z,Anne) ∨ Grandparent(George,Anne).
¬Parent(z,y) ∨ Grandparent(George,y).
```

（参见练习 20.4 和 20.5。）此外，参与每一步的子句可以从 `Background` 知识、示例 `Descriptions`、否定的 `Classifications` 中选择，或从逆向归结树中已生成的假设子句中选择。可能性数量众多意味着分支因子很大（因此搜索效率低下），除非有额外的控制。许多用于驯服搜索的方法已在实现的 ILP 系统中尝试过：

1. 可以消除冗余选择——例如，通过只生成尽可能具体的假设，并要求所有假设子句彼此一致，并且与观察一致。这一最后标准将排除前面列出的子句 `¬Parent(z,y) ∨ Grandparent(George,y)`。
2. 可以限制证明策略。例如，我们在 [第 9 章](#Chapter09-00.xhtml) 中看到，线性归结是一种完备的受限策略。线性归结产生的证明树具有线性分支结构——整个树沿着一条线展开，只有单个子句从该线分支出来（如 [图 20.13](#Chapter20-05.xhtml#fig20-13) 所示）。
3. 可以限制表示语言，例如通过消除函数符号或只允许 Horn 子句。例如，`PROGOL` 使用逆向蕴含操作 Horn 子句。其思想是将蕴含约束

*逆向蕴含*

`Background ∧ Hypothesis ∧ Descriptions ⊨ Classifications`

改为逻辑等价的形式

`Background ∧ Descriptions ∧ ¬Classifications ⊨ ¬Hypothesis`。

由此，可以使用类似于普通 Prolog Horn 子句演绎的过程，结合失败即否定来推导出 `Hypothesis`。由于它限制为 Horn 子句，这是一种不完备的方法，但它可能比完整的归结更高效。也可以使用逆向蕴含进行完备推理（Inoue, 2001）。
4. 推理可以用模型检验而不是定理证明来完成。`PROGOL` 系统（Muggleton, 1995）使用一种模型检验形式来限制搜索。也就是说，像答案集编程一样，它为逻辑变量生成可能的值，并检查一致性。
5. 推理可以用基命题子句而不是一阶逻辑来完成。`LINUS` 系统（Lavrauc and Duzeroski, 1994）通过将一阶理论翻译成命题逻辑，用命题学习系统求解，然后再翻译回来。处理命题公式在某些问题上可能更高效，正如我们在 [第 10 章](#Chapter10-00.xhtml) 中看到的 `SATPLAN` 一样。

## 20.5.4 用归纳逻辑编程进行发现

反转完备归结策略的逆向归结过程在原则上是学习一阶理论的完备算法。也就是说，如果某个未知的 `Hypothesis` 生成了一组示例，那么逆向归结过程可以从示例中生成 `Hypothesis`。这一观察提示了一个有趣的可能性：假设可用示例包括各种下落物体的轨迹。逆向归结程序在理论上是否能够推断出万有引力定律？答案显然是肯定的，因为在合适的背景数学下，万有引力定律可以解释这些示例。同样，可以想象电磁学、量子力学和相对论理论也都在 ILP 程序的范围内。当然，它们也都在一只拿着打字机的猴子的范围内；我们仍然需要更好的启发式方法和新的搜索空间结构方式。
