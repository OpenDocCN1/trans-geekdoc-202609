
# 增强型语法和词汇化PCFG

在本节中，我们展示语法如何表示这类知识，以便对哪些句子更可能做出更细粒度的区分。我们还将展示如何以组合的方式构建短语语义的表示。所有这些都将通过增强型语法实现，在该语法中，非终结符不仅仅是像 `Pronoun` 或 `NP` 这样的原子符号，而是结构化表示。例如，名词短语“I”可以表示为 `NP(Sbj, 1S, Speaker)`，其含义是“名词短语处于主格、第一人称单数，且其含义是句子的说话者。”相比之下，“me”将被表示为 `NP(Obj, 1S, Speaker)`，标明它处于宾格。

### Augmented grammar

考虑序列“Noun and Noun or Noun”，它可以解析为 “[Noun and Noun] or Noun”，也可以解析为 “Noun and [Noun or Noun]”。我们的上下文无关语法无法表达对其中一种分析的偏好，因为并列名词短语的规则 `NP → NP Conjunction NP[0.05]` 会给每种分析相同的概率。我们希望语法更偏好分析 “[[spaghetti and meatballs] or lasagna]” 和 “[spaghetti and [pie or cake]]”，而不是这些短语的另一种括号结构。

词汇化PCFG是一种增强型语法，允许我们根据短语中词语的性质（而不仅仅是句法范畴）分配概率。如果例如40个词句子的概率取决于全部40个词，数据将非常稀疏——这正是我们在使用n-gram时所指出的相同问题。为简化，我们引入短语的“核心”概念——最重要的词。因此，“banana”是NP“a banana”的核心，“ate”是VP“ate a banana”的核心。符号 `VP(v)` 表示范畴为 `VP` 且核心词为 `v` 的短语。下面是一个词汇化PCFG：

### Lexicalized PCFG
### Head

$\\begin{array}{l} \\left. VP(v)\\rightarrow Verb(v)\\ NP(n) \\right. \\\\ \\left. VP(v)\\ \\rightarrow\\ Verb(v) \\right. \\\\ \\left. NP(n)\\ \\rightarrow\\ Article(a)\\ Adjs(\\ j)\\ Noun(n) \\right. \\\\ \\left. NP(n)\\ \\rightarrow\\ NP(n)\\ Conjunction(c)\\ NP(m) \\right. \\\\ \\left. Verb\\,\\text{(}\\mathbf{ate}\\text{)~}\\rightarrow\\ \\mathbf{ate} \\right. \\\\ \\left. Noun\\text{(}\\mathbf{banana}\\text{)~}\\rightarrow\\ \\mathbf{banana} \\right. \\\\ \\end{array}\\,\\,\\,\\,\\,\\begin{array}{l} {\\lbrack P\_{1}(v,n)\\rbrack} \\\\ {\\text{\[}P\_{2}\\text{(}v\\text{)\]}} \\\\ {\\text{\[}P\_{\\text{3}}\\text{(}n,a\\text{)}\\rbrack} \\\\ {\\text{\[}P\_{\\text{4}}\\text{(}n,c,m\\text{)\]}} \\\\ {\\text{\[0}\\text{.002\]}} \\\\ {\\text{\[0}\\text{.0007\]}} \\\\ \\end{array}$

这里 `P1(v, n)` 表示由 `v` 为核心的VP与由 `n` 为核心的NP结合形成VP的概率。我们可以通过确保 `P1(ate, banana) > P1(ate, bandanna)` 来指定“ate a banana”比“ate a bandanna”更可能。请注意，由于我们只考虑短语核心，`P1` 无法捕捉“ate a banana”与“ate a rancid banana”之间的区别。从概念上讲，`P1` 是一个巨大的概率表：如果词汇表中共有5,000个动词和10,000个名词，那么 `P1` 需要5千万个条目，但其中大部分不会显式存储；而是通过平滑和回退推导出来。例如，我们可以从 `P1(v, n)` 回退到仅依赖于 `v` 的模型。这种模型所需的参数会少10,000倍，但仍能捕捉重要的规律，例如及物动词“ate”比不及物动词“sleep”更可能后面跟一个NP（无论核心词是什么）。

我们在[第24.2节](#Chapter24-02.xhtml#sec24-2)中看到，`ξ[0]` 的简单语法会过度生成，产生诸如“I saw she”或“I sees her”之类的非句子。为避免此问题，我们的语法必须知道“her”而不是“She”是“saw”（或任何其他动词）的有效宾语，并且“see”而不是“sees”是与主语“I”搭配的动词形式。

我们完全可以通过概率条目编码这些事实，例如对所有动词 `v` 使 `P1(v, she)` 成为一个很小的数。但更简洁且模块化的方法是为范畴 `NP` 增加额外变量：`NP(c, pn, n)` 用于表示具有格 `c`（主格或宾格）、人称和数 `pn`（例如第三人称单数）以及核心名词 `n` 的名词短语。[图24.9](#Chapter24-04.xhtml#fig24-9) 显示了一个处理这些额外变量的增强型词汇化语法。让我们详细考虑一条语法规则：

Description
一个矩形部分代表transformer层。transformer层内部有两个部分分别标记为Self-Attention和Feedforward。transformer层内部有两个节点各标记有一个加号。一组标记为input vectors的箭头从transformer层外部指向Self-Attention部分。Self-Attention部分的输出输入到第一个带加号的节点。一条标记为residual connection的箭头从input vectors指向第一个带加号的节点。第一个带加号节点的输出输入到Feedforward部分。Feedforward部分的输出输入到第二个带加号的节点。一条标记为residual connection的箭头从第一个带加号的节点指向第二个带加号的节点。第二个带加号节点的输出标记为output vectors。

×![](images/Fig-346.jpg)

图24.9 处理格一致性、主谓一致性和核心词的部分增强型语法。大写名称为常量：`Sbj` 和 `Obj` 分别表示主格和宾格；`1S` 表示第一人称单数；`1P` 和 `3P` 分别表示第一人称复数和第三人称复数。如常，小写名称为变量。为简单起见，概率已被省略。

`S(v) → NP(Sbj,pn,n) VP(pn,v) [P5(n,v)]`.

该规则表示当NP后面跟VP时它们可以构成S，但前提是NP具有主格（`Sbj`）且NP和VP的人称和数（`pn`）相同。（我们称之为一致。）如果成立，则我们得到一个以VP中的动词为核心的S。这里有一个词汇规则的例子，

`Pronoun(Sbj,IS,I)→I [0.005]`

它表示“I”是一个主格、第一人称单数、核心为“I”的Pronoun。

## 24.4.1 Semantic interpretation

为了展示如何向语法添加语义，我们从比英语更简单的例子开始：算术表达式的语义。[图24.10](#Chapter24-04.xhtml#fig24-10) 显示了一个算术表达式的语法，其中每条规则都用一个参数增强，表示短语的语义解释。像“3”这样的数字的语义就是数字本身。表达式“3 + 4”的语义是将运算符“+”应用于短语“3”和“4”的语义。语法规则遵循组合语义的原则——短语的语义是子短语语义的函数。[图24.11](#Chapter24-04.xhtml#fig24-11) 显示了根据该语法对 `3 + (4 ÷ 2)` 的分析树。分析树的根是 `Exp(5)`，其语义解释为5。

Description
