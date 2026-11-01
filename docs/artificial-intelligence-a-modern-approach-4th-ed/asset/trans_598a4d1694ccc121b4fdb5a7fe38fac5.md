
这种问答对在网络上相当常见，因此可以在没有人工专家参与的情况下建立一个大型数据库。利用这一庞大的数据源，可以构建出性能优于使用小型标注逻辑形式数据库的解析器（Liang et al., 2011; Liang and Potts, 2015）。这些论文中描述的关键方法是发明一种内部逻辑形式，它是组合性的，但不允许指数级大的搜索空间。

## 24.5 真实自然语言的复杂性

真实英语的语法是无穷无尽复杂的（其他语言同样复杂）。我们将简要提及一些导致这种复杂性的主题。

### 量化

考虑句子“Every agent feels a breeze.”该句子在 `ξ[0]` 下只有一个句法分析，但语义上是模糊的：是所有代理都感受到同一个微风，还是每个代理都感受到各自的个人微风？这两种解释可以表示为

```
$\\begin{array}{l} \\left. \\forall a\\,\\,\\, a \\in \\text{Agents}\\Rightarrow \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\exists b\\, b \\in Breezes \\land Feel\\text{(}a,b\\text{);}} \\\\ \\left. \\exists b\\,\\,\\, b \\in Breezes \\land \\forall a\\,\\,\\, a \\in Agents\\Rightarrow \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, Feel\\text{(}a,b\\text{)}\\text{.}} \\\\ \\end{array}$
```

一种标准的量化方法是让语法定义不是实际的逻辑语义句子，而是准逻辑形式，然后由解析过程之外的算法将其转换为逻辑句子。这些算法可以有偏好规则来选择一个量词作用域而非另一个——这些偏好不必直接反映在语法中。

### 准逻辑形式

### 语用学

我们已经展示了代理如何感知一串词语并使用语法推导出一组可能的语义解释。现在我们讨论通过添加关于当前情况的上下文相关信息来完成解释的问题。语用信息最明显的需求在于解决指示词的含义，指示词是指直接指向当前情况的短语。例如，在句子“I am in Boston today”中，“I”和“today”都是指示词。单词“I”将被 `Speaker` 表示，这是一个在不同时间指代不同对象的 fluent，而由听者来解决该 fluent 的指称对象——这不被认为是语法的一部分，而是语用学问题。

#### 指示词

语用学的另一部分是解释说话者的意图。说话者的言语被视为言语行为，而听者需要破译其是哪种类型的行为——问题、陈述、承诺、警告、命令等等。诸如“go to 2 2”之类的命令隐含地指代听者。到目前为止，我们对 `S` 的语法仅涵盖陈述句。我们可以将其扩展以涵盖命令——命令是一个动词短语，其主语隐含地是命令的听者：

#### 言语行为

```
S(Command(pred(Hearer))) → VP(pred)
```

### 长距离依赖

在 [图 24.8](#Chapter24-03.xhtml#fig24-8) 中我们看到“she didn’t hear or even see him”被分析为有两个缺口，其中 `NP` 缺失，但指代 `NP`“him”。我们可以使用符号 ⎵ 来表示缺口：“she didn’t \[hear ⎵ or even see ⎵\] him。”一般来说，缺口与其所指的 `NP` 之间的距离可以任意长：在“Who did the agent tell you to give the gold to ⎵?”中，缺口指代“Who”，相隔 11 个词。

可以采用一套复杂的增广规则系统来确保缺失的 `NP` 正确匹配。规则很复杂；例如，你不能在 `NP` 并列的一个分支中有一个缺口：“What did she play \[`NP` Dungeons and ⎵\]?” 是不合语法的。但你可以在 `VP` 并列的两个分支中都有相同的缺口，如句子“What did you \[`VP` \[`VP` smell ⎵\] and \[`VP` shoot an arrow at ⎵\]\]?”所示。

### 时间和时态

假设我们想表示“Ali loves Bo”和“Ali loved Bo”之间的差异。英语使用动词时态（过去、现在和将来）来表示事件的相对时间。表示事件时间的一个不错选择是 [第 10.3 节](#Chapter10-03.xhtml#sec10-3) 的事件演算记法。在事件演算中我们有

```
$\\begin{array}{l} {\\text{Ali}\\,\\,\\text{loves}\\,\\,\\text{Bo}:E_{1} \\in Loves(Ali,Bo) \\land During(Now,Extent(E_{1}))} \\\\ {\\text{Aliloved}\\,\\,\\text{Bo:}\\, E_{2} \\in Loves(Ali,Bo) \\land After(Now,Extent(E_{2})).} \\\\ \\end{array}$
```

这表明我们对单词“loves”和“loved”的两个词法规则应该是这些：

```
$\\begin{array}{l} \\left. Verb(\\lambda y\\,\\lambda x\\, e \\in \\, Loves(x,y) \\land During(Now,e))\\rightarrow\\mathbf{loves} \\right. \\\\ \\left. Verb(\\lambda y\\,\\lambda x\\, e \\in \\, Loves(x,y) \\land After(Now,e))\\rightarrow\\mathbf{loved}. \\right. \\\\ \\end{array}$
```

除此之外，语法的一切都保持不变，这是一个令人鼓舞的消息；它表明如果我们能如此轻松地添加动词时态这样的复杂性，我们就走在正确的轨道上（尽管我们才刚刚触及时间与时态的完整语法的表面）。

### 歧义

我们倾向于将歧义视为沟通失败；当听者有意识地察觉到某个言语中的歧义时，意味着该言语不清晰或令人困惑。以下是一些取自报纸头条的例子：

Squad helps dog bite victim.
Police begin campaign to run down jaywalkers.
Helicopter powered by human flies.
Once-sagging cloth diaper industry saved by full dumps.
Include your children when baking cookies.
Portable toilet bombed; police have nothing to go on.
Milk drinkers are turning to powder.
Two sisters reunited after 18 years in checkout counter.

此类混淆是例外；大多数时候我们听到的语言似乎没有歧义。因此，当研究人员在 1960 年代首次开始使用计算机分析语言时，他们相当惊讶地发现几乎每个句子都是歧义的，具有多种可能的分析（有时数百种），即使单一的首选分析是母语者注意到的唯一一种。例如，我们理解短语“brown rice and black beans”为“\[brown rice\] and \[black beans\]”，并且从不考虑低概率的解释“brown \[rice and black beans\]”，其中形容词“brown”修饰整个短语，而不仅仅是“rice”。当我们听到“Outside of a dog, a book is a person’s best friend”时，我们将“outside of”解释为“except for”的意思，并且在 Groucho Marx 笑话的下一句是“Inside of a dog it’s too dark to read”时觉得好笑。
