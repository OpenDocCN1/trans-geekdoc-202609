
$\\begin{array}{r} C\_{1} \\\\ C\_{2} \\\\ {C^{\\prime}}\_{1} \\\\ {C^{\\prime}}\_{2} \\\\ C^{\\prime} \\\\ C \\\\ \\end{array}\\,\\,\\,\\,\\begin{matrix} = \\\\ = \\\\ = \\\\ = \\\\ = \\\\ = \\\\ \\end{matrix}\\,\\,\\,\\,\\begin{array}{l} {\\neg P(x,F(x,A)) \\vee \\neg Q(x,A) \\vee R(x,B)} \\\\ {\\neg N(G(y),\\ z) \\vee P(H(y),\\ z)} \\\\ {\\neg P(H(B),F(H(B),A)) \\vee \\neg Q(H(B),A) \\vee R(H(B),B)} \\\\ {\\neg N(G(B),F(H(B),A)) \\vee P(H(B),F(H(B),A))} \\\\ {\\neg N(G(B),F(H(B),A)) \\vee \\neg Q(H(B),A) \\vee R(H(B),B)} \\\\ {\\neg N(G(y),F(H(y),A)) \\vee \\neg Q(H(y),A) \\vee R(H(y),B).} \\\\ \\end{array}$

我们确实看到 `C'` 是 `C` 的一个基实例。一般而言，若 `C1` 和 `C2` 有任何归结式，它们必须先对 `C1` 和 `C2` 应用 `C1` 与 `C2` 中一对互补文字的最一般合一子构造而成。根据提升引理，很容易推导出关于归结规则任意应用序列的类似陈述：
对于 `S'` 的归结闭包中的任意子句 `C'`，在 `S` 的归结闭包中存在一个子句 `C`，使得 `C'` 是 `C` 的基实例，并且 `C` 的推导长度与 `C'` 的推导长度相同。
由此可知，如果空子句出现在 `S'` 的归结闭包中，它也必须出现在 `S` 的归结闭包中。这是因为空子句不能是任何其他子句的基实例。回顾一下：我们已证明如果 `S` 不可满足，则存在一个使用归结规则的空子句的有限推导。
从基子句到一阶子句的定理证明的提升提供了巨大的能力增强。这种增强源于一阶证明只需将变量实例化到证明所必需的程度，而基子句方法则需要检查大量任意实例化。

## 9.5.5 等式
本章迄今描述的推理方法都无法在不做额外工作的情况下处理形如 `x = y` 的断言。可以采取三种不同的方法。第一种是对等式进行公理化——在知识库中写下关于等价关系的句子。我们需要说明等式是自反的、对称的和传递的，并且我们还必须说明可以在任何谓词或函数中以等代等。因此我们需要三个基本公理，然后为每个谓词和函数各一个：
$\\begin{array}{l} {\\forall x\\ x = x} \\\\ \\left. \\forall x,y\\ x = y\\ \\Rightarrow\\ y = x \\right. \\\\ \\left. \\forall x,y,z\\,\\, x = y \\land y = z\\Rightarrow x = z \\right. \\\\ \\left. \\forall x,y\\ x = y\\ \\Rightarrow\\ (P\_{1}(x)\\ \\Leftrightarrow\\ P\_{1}(y)) \\right. \\\\ \\left. \\forall x,y\\ x = y\\ \\Rightarrow\\ (P\_{2}(x)\\ \\Leftrightarrow\\ P\_{2}(y)) \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\vdots} \\\\ \\left. \\forall w,x,y,z\\,\\, w = y\\, \\land x = z\\Rightarrow(F\_{1}(w,x) = F\_{1}(y,z)) \\right. \\\\ \\left. \\forall w,x,y,z\\,\\, w = y \\land x = z\\Rightarrow(F\_{2}(w,x) = F\_{2}(y,z)) \\right. \\\\ {\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, \\vdots} \\\\ \\end{array}$
给定这些句子，像 `resolution` 这样的标准推理过程可以执行需要等式推理的任务，例如求解数学方程。然而，这些公理会产生大量结论，其中大多数对证明没有帮助。因此第二种方法是添加推理规则而不是公理。最简单的规则 `demodulation` 取一个单位子句 `x = y` 和包含项 `x` 的某个子句 `α`，并生成通过在 `α` 内用 `y` 替换 `x` 形成的新子句。如果 `α` 中的项与 `x` 合一，则该规则有效；它不必与 `x` 完全相等。请注意 `demodulation` 是有方向的；给定 `x = y`，`x` 总是被 `y` 替换，从不相反。这意味着 `demodulation` 可用于使用如 `z + 0 = z` 或 `z1 = z` 之类的去模器简化表达式。作为另一个例子，给定
$\\begin{array}{l} {Father(Father(x))\\ = \\ PaternalGrandfather(x)} \\\\ {Birthdate(Father(Father(Bella)),\\, 1926)} \\\\ \\end{array}$
我们可以通过 `demodulation` 得出结论
`Birthdate(PaternalGrandfather(Bella), 1926)`。
更正式地，我们有
• `Demodulation`: 对于任意项 `x`、`y` 和 `z`，其中 `z` 出现在文字 `m` 的某处，并且 `UNIFY(x, z) = θ ≠ failure`，
$\\frac{x = y,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, m\_{1} \\vee \\cdots \\vee m\_{n}}{\\text{SUB(SUBST(}\\theta,x\\text{),~SUBST(}\\theta,y\\text{),}\\, m\_{\\text{1}}\\ \\vee \\cdots \\vee m\_{n}\\text{)}}.$
其中 `SUBST` 是绑定列表的通常替换，而 `SUB(x,y,m)` 表示在 `m` 内某处用 `y` 替换 `x`。
该规则还可以扩展以处理包含等号的非单位子句：
• `Paramodulation`: 对于任意项 `x`、`y` 和 `z`，其中 `z` 出现在文字 `m` 的某处，并且 `UNIFY(x,z) = θ`，
$\\frac{\\mathcal{l}\_{1} \\vee \\cdots \\vee \\mathcal{l}\_{k} \\vee x = y,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\,\\, m\_{1} \\vee \\cdots \\vee m\_{n}}{\\text{SUB(SUBST(}\\theta,x\\text{),~SUBST}\\,\\text{(}\\theta,y\\text{),}\\,\\text{SUBST}\\,\\text{(}\\theta,\\,\\mathcal{l}\_{k} \\vee m\_{\\text{1}} \\vee \\cdots \\vee m\_{n}\\text{))}}.$
例如，从
$\\begin{matrix} {P\\text{(}F\\text{(}x,B\\text{)},x\\text{)} \\vee Q\\text{(}x\\text{)}} & \\text{and} & {F\\text{(}A,y\\text{)} = y \\vee R\\text{(}y\\text{)}} \\\\ \\end{matrix}$
我们有 `θ = UNIFY(F(A,y),F(x,B)) = {x/A,y/B}`，并且我们可以通过 `paramodulation` 得出句子
`P(B, A) ∨ Q(A) ∨ R(B)`。
`Paramodulation` 为带等式的一阶逻辑提供了一个完备的推理过程。
第三种方法完全在扩展的合一算法内部处理等式推理。也就是说，如果在某种替换下它们是可证明相等的，则项是可合一的，其中“可证明”允许进行等式推理。例如，项 `1 + 2` 和 `2 +1` 通常不可合一，但知道 `x + y = y + x` 的合一算法可以用空替换将它们合一。这种类型的等式合一可以用为特定公理（交换律、结合律等）设计的有效算法完成，而不是通过对这些公理的显式推理。使用该技术的定理证明器与 `Section 9.4` 中描述的 `CLP` 系统密切相关。

## 9.5.6 归结策略
我们知道 `resolution` 推理规则的重复应用最终会找到证明（如果存在的话）。在本小节中，我们研究有助于高效找到证明的策略。
`Unit preference`：该策略更倾向于进行其中一个句子是单个文字（也称为单位子句）的归结。该策略背后的思想是我们试图产生空子句，因此更倾向于产生较短子句的推理可能是一个好主意。用单位句子（如 `P`）与任何其他句子（如 `¬P∨¬Q ∨ R`）进行归结总是产生一个子句（在本例中为 `¬Q ∨ R`），该子句比另一个子句更短。当 `unit preference` 策略于 1964 年首次用于命题推理时，它导致了显著的加速，使得在没有该偏好的情况下无法处理的定理变得可行。`Unit resolution` 是一种受限的归结形式，其中每一步归结必须涉及一个单位子句。`Unit resolution` 一般是不完备的，但对于 `Horn clauses` 是完备的。`Horn clauses` 上的 `Unit resolution` 证明类似于 `forward chaining`。
