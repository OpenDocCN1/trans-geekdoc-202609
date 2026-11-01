
`Married(Father(Richard), Mother(John))` 断言理查德·狮心王的父亲与约翰王的母亲结婚（再次，在合适的解释下）。[5](#Chapter08-06.xhtml#sup08-5)

原子句子在给定模型中为真，当且仅当谓词符号所指的关系在论元所指的对象之间成立。

## 8.2.5 复杂句子

我们可以使用逻辑联结词构造更复杂的句子，其语法和语义与命题演算相同。以下是根据我们的预期解释在 [图 8.2](#Chapter08-02.xhtml#fig8-2) 的模型中为真的四个句子：

$\\begin{array}{l} {\\neg Brother(LeftLeg(Richard),John)} \\\\ {Brother(Richard,John)\\operatorname{\\,\\land}Brother(John,Richard)} \\\\ {King(Richard) \\vee King(John)} \\\\ \\left. \\neg King(Richard)\\ \\Rightarrow\\ King(John)\\ . \\right. \\\\ \\end{array}$

## 8.2.6 量词

一旦我们有了允许对象的逻辑，自然就会想要表达整个对象集合的属性，而不是按名称枚举对象。量词使我们能够做到这一点。一阶逻辑包含两个标准量词，称为全称和存在。

量词

### 全称量化 (∀)

回顾我们在 [第 7 章](#Chapter07-00.xhtml) 中用命题逻辑表达一般规则时遇到的困难。诸如“与 wumpus 相邻的方格有臭味”和“所有国王都是人”之类的规则是一阶逻辑的精髓。我们在 [第 8.3 节](#Chapter08-03.xhtml#sec8-3) 中处理前者。后者规则“所有国王都是人”在一阶逻辑中写成

`∀x King(x) ⇒ Person(x)`.

全称量词 ∀ 通常读作“对于所有...”。（记住倒置的 A 代表“all”。）因此，该句子说，“对于所有 `x`，如果 `x` 是国王，则 `x` 是人。” 符号 `x` 称为变量。按照惯例，变量为小写字母。变量本身就是一个项，因此也可以作为函数的参数——例如，`LeftLeg(x)`。不含变量的项称为基项。

全称量词
变量
基项

直观上，句子 `∀x P`，其中 P 是任意逻辑句子，断言 P 对每个对象 `x` 都为真。更精确地说，`∀x P` 在给定模型中为真，当且仅当 P 在从模型给出的解释构造的所有可能的扩展解释中都为真，其中每个扩展解释指定 `x` 所指的域元素。

扩展解释

这听起来很复杂，但它实际上只是对全称量化的直观含义的一种谨慎表述。考虑 [图 8.2](#Chapter08-02.xhtml#fig8-2) 中显示的模型及其对应的预期解释。我们可以以五种方式扩展该解释：

$\\begin{array}{l} \\left. x\\rightarrow\\text{Richard~the~Lionheart}\\text{.} \\right. \\\\ \\left. x\\rightarrow\\,\\text{King~John,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{Richard}'\\text{s}\\,\\text{left~leg,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{John}'\\text{s}\\,\\text{left~leg,} \\right. \\\\ \\left. x\\rightarrow\\,\\text{the~crown}\\text{.} \\right. \\\\ \\end{array}$

全称量化句子 `∀x King(x) ⇒ Person(x)` 在原始模型中为真，当且仅当句子 `King(x) ⇒ Person(x)` 在每一种五种扩展解释下都为真。也就是说，全称量化句子等价于断言以下五个句子：

$\\begin{array}{l} \\left. \\text{Richard~the~Lionheart~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{Richard~the~Lionheart~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{King~John~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{King~John~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{Richard's}\\,\\text{left~leg~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{Richard}'\\text{s}\\,\\text{left~leg~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{John}'\\text{s}\\,\\text{left~leg~is~a~king}\\,\\,\\Rightarrow\\,\\,\\,\\text{John}'\\text{s}\\,\\text{leftleg~is~a~person}\\text{.} \\right. \\\\ \\left. \\text{The~crown~is~a~king}\\,\\,\\Rightarrow\\,\\,\\text{the~crown~is~a~person}\\text{.} \\right. \\\\ \\end{array}$

让我们仔细看看这一组断言。由于在我们的模型中，约翰王是唯一的国王，第二句话断言他是人，正如我们所希望的那样。但其他四个句子呢，它们似乎对腿和王冠做出断言？这是“所有国王都是人”的含义的一部分吗？事实上，其他四个断言在模型中为真，但对腿、王冠或理查德的人身资格完全不做任何断言。这是因为这些对象都不是国王。查看 `⇒` 的真值表（[图 7.8](#Chapter07-04.xhtml#fig7-8) 第 [第 237 页](#Chapter07-04.xhtml#page_237)），我们看到当其前提为假时蕴含为真——无论结论的真假如何。因此，通过断言全称量化句子，等价于断言一系列个体蕴含，我们最终只对前提为真的那些对象断言规则的结论，而对前提为假的那些对象则完全不说任何话。因此，`⇒` 的真值表定义对于用全称量词书写一般规则来说是完美的。

常见的错误，即使是仔细阅读了这段话数次的读者也经常犯，就是使用合取而不是蕴含。句子

`∀x King(x) ∧ Person(x)`

等价于断言

理查德·狮心王是国王 ∧ 理查德·狮心王是人，

约翰王是国王 ∧ 约翰王是人，

理查德的左腿是国王 ∧ 理查德的左腿是人，

等等。显然，这并不能表达我们想要的意思。

### 存在量化 (∃)

全称量化对每个对象做出断言。类似地，我们可以使用存在量词在不命名对象的情况下对某个对象做出断言。例如，要说约翰王头上戴着王冠，我们写成

存在量词

`∃x Crown(x) ∧ OnHead(x, John)`.

`∃x` 读作“存在一个 `x` 使得...”或“对于某个 `x`...”。

直观上，句子 `∃x P` 断言 P 对至少一个对象 `x` 为真。更精确地说，`∃x P` 在给定模型中为真，当且仅当 P 在将 `x` 赋给域元素的至少一个扩展解释中为真。也就是说，以下至少有一个为真：

理查德·狮心王是王冠 ∧ 理查德·狮心王在约翰头上；

约翰王是王冠 ∧ 约翰王在约翰头上；

理查德的左腿是王冠 ∧ 理查德的左腿在约翰头上；

约翰的左腿是王冠 ∧ 约翰的左腿在约翰头上；

王冠是王冠 ∧ 王冠在约翰头上。

第五个断言在模型中为真，因此原始的存在量化句子在模型中为真。请注意，根据我们的定义，该句子在约翰王戴着两顶王冠的模型中也为真。这与原始句子“约翰王头上戴着王冠”完全一致。[6](#Chapter08-06.xhtml#sup08-6)

正如 `⇒` 似乎是与 ∀ 一起使用的自然联结词，`∧` 是与 ∃ 一起使用的自然联结词。用 `∧` 作为 ∀ 的主联结词在上一节的例子中导致了过于强的断言；用 `⇒` 与 ∃ 一起通常会导致非常弱的断言。考虑以下句子：

`∃x Crown(x) ⇒ OnHead(x, John)`.
