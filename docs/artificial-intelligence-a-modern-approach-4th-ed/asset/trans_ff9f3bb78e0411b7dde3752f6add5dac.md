
## 广义假言推理

细心的读者会注意到，命题化方法会产生许多不必要的全称量词句实例化。我们更希望采用一种仅使用一条规则的方法，推理 `{x / John}` 如何解决查询 `Evil(x)` 如下：给定贪婪的国王是邪恶的规则，找到某个 `x` 使得 `x` 是国王且 `x` 是贪婪的，然后推断这个 `x` 是邪恶的。更一般地，如果存在某个替换 `θ` 使蕴含前提的每个合取项与知识库中已有的句子相同，那么在应用 `θ` 之后，我们可以断言蕴含的结论。在这种情况下，替换 `θ = {x / John}` 实现了这一目标。现在假设我们不是知道 `Greedy(John)`，而是知道每个人都是贪婪的：
$\\begin{matrix} {\\forall y\\,\\, Greedy\\,\\text{(}y\\text{)~}\\text{.}} & {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,(9.2)} \\\\ \\end{matrix}$
那么我们仍然希望能够得出 `Evil(John)`，因为我们知道 `John` 是国王（已知）并且 `John` 是贪婪的（因为每个人都是贪婪的）。要使这项工作奏效，我们需要为蕴含句中的变量以及知识库中句子的变量找到一个替换。在这种情况下，将替换 `{x / John, y / John}` 应用于蕴含前提 `King(x)` 和 `Greedy(x)` 以及知识库句子 `King(John)` 和 `Greedy(y)` 将使它们相同。因此，我们可以推断蕴含的后件。
这一推理过程可以被概括为一条单一的推理规则，我们称之为广义假言推理：[2](#Chapter09-07.xhtml#sup09-2) 对于原子句子 `p_i`、`p_i'` 和 `q`，其中存在一个替换 `θ` 使得 `SUBST(θ pi') = SUBST(θ, p[i])`，对所有 `i` 成立，
**广义假言推理**
$\\frac{\\left. p\_{1}{}^{'},p\_{2}{}^{'}\\ldots,p\_{n}{}^{'},(p\_{1} \\land p\_{2} \\land \\ldots \\land p\_{n}\\Rightarrow q) \\right.}{\\text{SUBST(}\\theta\\text{,}q\\text{)}}.$
该规则有 `n + 1` 个前提：原子句子 `p[i]'` 和一个蕴含式。结论是把替换 `θ` 应用于后件 `q` 的结果。对于我们的例子：
$\\begin{array}{l} {p\_{\\text{1}}{}^{\\prime}\\text{~is~}King\\text{(}John\\text{)}} \\\\ {p\_{\\text{2}}{}^{\\prime}\\text{~is~}Greedy(y)} \\\\ {\\theta\\text{~is~\\{}x\\text{/John,y}/\\text{John\\}}} \\\\ {\\text{SUBST(}\\theta\\text{,}\\, q\\text{)~is~}Evil\\text{(}John\\text{)~}\\text{.}} \\\\ \\end{array}\\,\\,\\,\\,\\,\\,\\begin{array}{l} {p\_{\\text{1}}\\text{~is~}King\\text{(}x\\text{)}} \\\\ {p\_{\\text{2}}\\text{~is~}Greedy\\text{(}x\\text{)}} \\\\ {q\\text{~is~}Evil\\text{(}x\\text{)}} \\\\ \\\\ \\end{array}$
很容易证明广义假言推理是一个可靠的推理规则。首先，我们观察到，对于任何句子 `p`（其变量假定为全称量化的）以及任何替换 `θ`，
*p* ⊨ SUBST(*θ*, *p*).
根据全称实例化为真。对于满足广义假言推理规则条件的 `θ` 尤其如此。因此，从 `p1'`、…、`pn'` 我们可以推断
`SUBST(θ, p[1]′) ∧ … ∧ SUBST(θ, p[n]′)`
并且从蕴含式 `p[1] ∧ … ∧ p[n] ⇒ q` 我们可以推断
`SUBST(θ, p[1]) ∧ … ∧ SUBST(θ, p[n]) ⇒ SUBST(θ, q)`.
现在，`θ` 在广义假言推理中定义为 `SUBST(θ, pi') = SUBST(θ, pi)`，对所有 `i` 成立；因此，这两个句子中的第一个与第二个的前提完全匹配。故，`SUBST(θ, q)` 根据假言推理可得。
广义假言推理是假言推理的提升版本——它将假言推理从无变量的命题逻辑提升到一阶逻辑。我们将在本章剩余部分看到，可以开发前向链接、后向链接和归结算法的提升版本，这些算法在[第7章](#Chapter07-00.xhtml)中介绍。提升推理规则相对于命题化的关键优势在于，它们只进行允许特定推理进行的必要替换。
**提升**
## 9.2.1 统一
提升推理规则需要找到使不同逻辑表达式看起来相同的替换。这一过程称为统一，是所有一阶推理算法的关键组成部分。`UNIFY` 算法接收两个句子，并在存在时返回它们的统一子（一个替换）：
**统一**
**统一子**
`UNIFY(p, q) = θ where SUBST(θ, p) = SUBST(θ, q)`.
让我们看看 `UNIFY` 应如何表现的一些例子。假设我们有一个查询 `AskVars(Knows(John,x))`：John 知道谁？对此查询的答案可以通过找到知识库中与 `Knows(John, x)` 统一的所有句子来找到。以下是与知识库中可能存在的四个不同句子统一的结果：
$\\begin{array}{l} {\\text{UNIFY}\\,\\text{(}Knows\\text{(}John\\text{,}\\, x\\text{),~}Knows\\text{(}John,Jane\\text{))~=~\\{}x\\text{/Jane\\}}} \\\\ {\\text{UNIFY}\\,\\text{(}Knows\\text{(}John\\text{,}\\, x\\text{),~}Knows\\text{(}y,Bill\\text{))~=~\\{}x\\text{/}Bill,y/John\\text{\\}}} \\\\ {\\text{UNIFY(}Knows\\text{(}John\\text{,}x\\text{),~}Knows\\text{(}y\\text{,}Mother\\text{(}y\\text{)))~=~\\{}y\\text{/}John\\text{,}x\\text{/}Mother\\text{(}John\\text{)\\}}} \\\\ {\\text{UNIFY(}Knows\\text{(}John\\text{,}\\, x\\text{),~}Knows\\text{(}x\\text{,~}Elizabeth\\text{))~=~}failure\\ \\text{.}} \\\\ \\end{array}$
最后一次统一失败，因为 `x` 不能同时取 John 和 Elizabeth 的值。现在，记住 `Knows(x, Elizabeth)` 表示“每个人都认识 Elizabeth”，因此我们应该能够推断 John 认识 Elizabeth。问题只出现在两个句子恰好使用了相同的变量名 `x`。通过对正在统一的两个句子之一进行变量标准化来避免名称冲突，可以避免这个问题，这意味着重命名其变量以避免名称冲突。例如，我们可以将 `Knows(x, Elizabeth)` 中的 `x` 重命名为 `x[17]`（一个新变量名），而不改变其含义。现在统一将起作用：
**变量标准化**
`UNIFY(Knows(John, x), Knows(x[17], Elizabeth)) = {x/Elizabeth, x[17]/John}`
练习 9.STAN 进一步探讨了变量标准化的必要性。
还有一个并发症：我们说 `UNIFY` 应该返回一个使两个参数看起来相同的替换。但可能存在不止一个这样的统一子。例如，`UNIFY(Knows(John,x), Knows(y,z))` 可能返回 `{y/John,x/z}`，也可能返回 `{y/John, x/John, z/John}`。第一个统一子将统一的结果给出为 `Knows(John, z)`，而第二个给出 `Knows(John, John)`。第二个结果可以通过额外的替换 `{z/John}` 从第一个得到；我们说第一个统一子比第二个更一般，因为它对变量值的限制更少。
每对可统一的表达式都有一个唯一的、最多一般的统一子（MGU），在变量重命名和替换意义下是唯一的。例如，`{x/John}` 和 `{y/John}` 被认为是等价的，`{x/John,y/John}` 和 `{x/John,y/x}` 也是如此。
**最一般统一子（MGU）**
