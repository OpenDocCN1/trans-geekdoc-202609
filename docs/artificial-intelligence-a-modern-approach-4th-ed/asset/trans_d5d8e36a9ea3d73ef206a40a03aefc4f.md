
表面上，这看起来像是我们句子的一个合理表述。应用语义后，我们看到该句子说以下断言中至少有一个为真：
理查德·狮心王是王冠 ⇒ 理查德·狮心王戴在约翰头上；
国王约翰是王冠 ⇒ 国王约翰戴在约翰头上；
理查德的左腿是王冠 ⇒ 理查德的左腿戴在约翰头上；
等等。蕴含式在前提和结论都为真时为真，或前提为假时也为真；因此如果理查德·狮心王不是王冠，那么第一个断言为真且存在量词得到满足。所以，存在量化的蕴含句子只要有任何对象不满足前提就为真；因此这类句子实际上并没有说太多。

## 嵌套量词
我们经常希望使用多个量词来表达更复杂的句子。最简单的情况是量词类型相同。例如，“兄弟是兄弟姐妹”可以写成
`∀x∀y Brother(x,y) ⇒ Sibling(x,y)`。
连续的同类型量词可以写成一个带有多个变量的量词。例如，要说兄弟关系是对称关系，我们可以写
`∀x ,y Sibling(x,y) ⇔ Sibling(y,x)`。
在其他情况下我们会有混合。“每个人都爱某人”意味着对于每个人来说，都有某个人是那个人所爱：
`∀x ∃y Loves(x,y)`。
另一方面，要说“有人被每个人所爱”，我们写
`∃y ∀x Loves(x,y)`。
量化的顺序因此非常重要。如果插入括号会更清楚。`∀x (∃y Loves(x, y))` 说每个人都有一个特定属性，即他们爱某人的属性。另一方面，`∃y (∀x Loves(x, y))` 说世界上有人具有特定属性，即被所有人所爱的属性。
当使用相同变量名时可能会产生混淆。考虑句子
`∀x (Crown(x) ∨ (∃x Brother(Richard, x)))`。
这里 `Brother(Richard, x)` 中的 `x` 是存在量化的。规则是变量属于提到它的最内层量词；然后它不会受到任何其他量化的影响。另一种思考方式是：`∃x Brother(Richard, x)` 是关于理查德的句子（他有一个兄弟），而不是关于 `x` 的；因此在它外面加上一个 `∀x` 没有效果。它同样可以写成 `∃z Brother(Richard, z)`。因为这可能导致混淆，我们在使用嵌套量词时将始终使用不同的变量名。

## ∀ 与 ∃ 之间的联系
这两个量词实际上通过否定彼此紧密相连。断言每个人都讨厌欧防风根等同于断言不存在喜欢它的人，反之亦然：
`∀x ¬Likes(x, Parsnips)` is equivalent to `¬∃x Likes(x, Parsnips)`.
我们可以更进一步：“每个人都喜欢冰淇淋”意味着没有人不喜欢冰淇淋：
`∀x Likes(x, IceCream)` is equivalent to `¬∃x ¬Likes(x, IceCream)`.
因为 ∀ 实际上是对对象宇宙的合取，而 ∃ 是析取，所以它们服从德摩根规则不足为奇。量化与非量化句子的德摩根规则如下：
```
\begin{matrix}
{\neg\exists x\, P \equiv \forall x\,\neg P}\\
{\neg\forall x\, P \equiv \exists x\,\neg P}\\
{\forall x\, P \equiv \neg\exists x\,\neg P}\\
{\exists x\, P \equiv \neg\forall x\,\neg P}
\end{matrix}
\begin{matrix}
{\neg(P \vee Q) \equiv \neg P \land \neg Q}\\
{\neg(P \land Q) \equiv \neg P \vee \neg Q}\\
{P \land Q \equiv \neg(\neg P \vee \neg Q)}\\
{P \vee Q \equiv \neg(\neg P \land \neg Q).}
\end{matrix}
```
因此，我们并不真正需要同时拥有 ∀ 和 ∃，就像我们并不真正需要同时拥有 ∧ 和 ∀ 一样。尽管如此，可读性比简约更重要，所以我们将保留这两个量词。

## 8.2.7 等式
一阶逻辑除了使用前面描述的谓词和项来构造原子句子外，还包括另一种方法。我们可以使用等号符号来表示两个项指代同一个对象。例如，
等号符号
`Father(John) = Henry`
说 `Father(John)` 所指的对象和 `Henry` 所指的对象是同一个。因为解释固定了任何项的指称，判断等式句子的真值只是看两个项的指称是否相同对象。
等号符号可用于陈述给定函数的事实，就像我们刚才对 `Father` 符号所做的那样。它也可以与否定一起使用来坚持两个项不是同一个对象。要说理查德至少有两个兄弟，我们会写
`∃x , y Brother(x, Richard) ∧ Brother(y, Richard) ∧ ¬(x = y)`.
句子
`∃x , y Brother(x, Richard) ∧ Brother(y, Richard)`
没有预期的含义。特别是，它在 [图 8.2](#Chapter08-02.xhtml#fig8-2) 的模型中为真，其中理查德只有一个兄弟。为了说明这一点，考虑扩展解释，其中 `x` 和 `y` 都被赋值为国王约翰。添加 `¬ (x = y)` 排除了此类模型。符号 `x ≠ y` 有时被用作 `¬ (x = y)` 的缩写。

## 8.2.8 数据库语义
继续上一节的例子，假设我们认为理查德有两个兄弟，约翰和杰弗里。[7](#Chapter08-06.xhtml#sup08-7) 我们可以写
```
\begin{matrix}
{Brother(John,Richard) \land Brother(Geoffrey,Richard),} & {(8.3)}
\end{matrix}
```
但这并不能完全捕捉实际情况。首先，这个断言在理查德只有一个兄弟的模型中为真——我们需要加上 `John ≠ Geoffrey`。其次，该句子没有排除理查德除了约翰和杰弗里之外还有更多兄弟的模型。因此，“理查德的兄弟是约翰和杰弗里”的正确翻译如下：
```
\begin{matrix}
{Brother\,(John,Richard) \land Brother\,(Geoffrey,Richard) \land John \neq Geoffrey}\\
{\land \forall x\, Brother\,(x,\, Richard)\Rightarrow(x\,=\, John \vee x\,=\, Geoffrey).}
\end{matrix}
```
这个逻辑句子看起来比对应的英语句子冗长得多。但如果我们未能正确翻译英语，我们的逻辑推理系统就会出错。我们能否设计一种语义，使逻辑句子更简洁？
数据库系统中非常流行的一种提议如下。首先，我们坚持每个常量符号都指代不同的对象——唯一名称假设。其次，我们假设未知为真的原子句子实际上为假——封闭世界假设。最后，我们引入域闭包，意味着每个模型包含的域元素不超过常量符号所命名的元素。
唯一名称假设
封闭世界假设
域闭包
