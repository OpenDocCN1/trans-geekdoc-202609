
在实践方面，命题逻辑求解器的效率提升显著。在十分钟的计算时间内，1962 年的原始 DPLL 算法仅能解决不超过 10 或 15 个变量的问题。到 1995 年，SATZ 求解器（Li 和 Anbulagan，1997）能够处理 1,000 个变量，这得益于用于变量索引的优化数据结构。两个关键贡献是 Zhang 和 Stickel（1996）提出的**观察字面**索引技术，它使单元传播非常高效，以及 Bayardo 和 Schrag（1997）引入的从约束满足（CSP）社区的条款（即约束）学习技术。利用这些思想，并受解决工业规模电路验证问题的前景驱动，Moskewicz **et al.**（2001）开发了 CHAFF 求解器，该求解器能够处理数百万个变量的问题。自 2002 年起，SAT 竞赛定期举办；获胜者大多是 CHAFF 的后代或采用相同的一般方法。值得注意的是，RSAT（Pipatsrisawat 和 Darwiche，2007），2007 年的获胜者，属于后者类别。另一个值得注意的成果是 MINISAT（Een 和 Sörensson，2003），这是一个开源实现，可在 `http://minisat.se` 找到，设计时易于修改和改进。当前求解器的研究概览由 Gomes **et al.**（2008）进行。

本地搜索算法在 1980 年代被多位作者尝试；所有算法都基于最小化不满足条款数量的思想（Hansen 和 Jaumard，1990）。特别有效的算法由 Gu（1989）开发，并独立由 Selman **et al.**（1992）提出，他们称其为 GSAT，并展示了它能够非常快速地解决一系列非常难的问题。本章节描述的 WALKSAT 算法归 Selman **et al.**（1996）。

随机 k-SAT 问题的“相变”现象首次由 Simon 和 Dubois（1989）观察，这一现象引发了大量理论和实证研究——部分原因是其与统计物理中的相变现象的显而易见联系。Cheeseman **et al.**（1991）观察到多个约束满足（CSP）问题中存在相变，并猜想所有 NP 硬问题都存在相变。Crawford 和 Auton（1993）定位到 3-SAT 的相变点在变量/条款比率约为 4.26，并指出这与其 SAT 求解器运行时间的陡峭峰值相吻合。Cook 和 Mitchell（1997）对早期文献提供了优秀的总结。

当前理论理解的状态由 Achlioptas（2009）总结。**满足性阈值猜想** 表示，对于每个 *k*，存在一个尖锐的满足性阈值 *r*[*k*]，当变量数 *n* 趋于无穷大时，阈值以下的实例满足性为 1，而阈值以上的实例不满足性为 1。该猜想未被 Friedgut（1999）完全证明：虽然存在尖锐阈值，但其位置可能随 *n* 变化，即使 *n* 趋于无穷大。尽管在大 *k* 的阈值位置渐近分析方面取得了显著进展（Achlioptas 和 Peres，2004；Achlioptas **et al.**，2007），对于 *k* = 3 只能证明阈值位于 [3.52, 4.51] 区间内。当前理论表明，求解器运行时间的峰值不一定与满足性阈值相关，而是与 SAT 实例解的分布和结构中的相变有关。Coarfa **et al.**（2003）的实证结果支持这一观点。事实上，诸如 **调查传播**（survey propagation）（Parisi 和 Zecchina，2002；Maneva **et al.**，2007）等算法利用了随机 SAT 实例在满足性阈值附近的特殊性质，并在此类实例上显著优于通用 SAT 求解器。

---

### SATISFIABILITY THRESHOLD CONJECTURE

---

### SURVEY PROPAGATION

---

The best sources for information on satisfiability, both theoretical and practical, are the *Handbook of Satisfiability* (Biere **et al.**, 2009) and the regular *International Conferences on Theory and Applications of Satisfiability Testing*, known as SAT.

The idea of building agents with propositional logic can be traced back to the seminal paper of McCulloch and Pitts (1943), which initiated the field of neural networks. Contrary to popular supposition, the paper was concerned with the implementation of a Boolean circuit-based agent design in the brain. Circuit-based agents, which perform computation by propagating signals in hardware circuits rather than running algorithms in general-purpose computers, have received little attention in AI, however. The most notable exception is the work of Stan Rosenschein (Rosenschein, 1985; Kaelbling and Rosenschein, 1990), who developed ways to compile circuit-based agents from declarative descriptions of the task environment. (Rosenschein’s approach is described at some length in the second edition of this book.) The work of Rod Brooks (1986, 1989) demonstrates the effectiveness of circuit-based designs for controlling robots—a topic we take up in Chapter 25. Brooks (1991) argues that circuit-based designs are *all* that is needed for AI—that representation and reasoning are cumbersome, expensive, and unnecessary. In our view, neither approach is sufficient by itself. Williams **et al.** (2003) show how a hybrid agent design not too different from our wumpus agent has been used to control NASA spacecraft, planning sequences of actions and diagnosing and recovering from faults.

The general problem of keeping track of a partially observable environment was introduced for state-based representations in Chapter 4. Its instantiation for propositional representations was studied by Amir and Russell (2003), who identified several classes of environments that admit efficient state-estimation algorithms and showed that for several other classes the problem is intractable. The **temporal-projection** problem, which involves determining what propositions hold true after an action sequence is executed, can be seen as a special case of state estimation with empty percepts. Many authors have studied this problem because of its importance in planning; some important hardness results were established by Liberatore (1997). The idea of representing a belief state with propositions can be traced to Wittgenstein (1922).

---

### TEMPORAL-PROJECTION

---

逻辑状态估计，当然需要对行动效果进行逻辑表示——这是自 1950 年代末期以来人工智能领域的核心问题之一。主流的方案是 `situation calculus` 形式主义（McCarthy, 1963），它基于一阶逻辑。我们在 `第 10 章` 和 `第 12 章` 中讨论 `situation calculus` 以及各种扩展和替代方案。本章采用的方法——在命题变元上使用时间索引——虽然更具限制性，但具有简洁性的优势。`SATPLAN` 算法的总体思路由 Kautz 和 Selman（1992）提出。随后的 `SATPLAN` 版本能够利用前文所述 SAT 求解器的进步，并且仍然是解决困难问题的最有效方法之一（Kautz, 2006）。

`frame problem` 首先由 McCarthy 和 Hayes（1969）提出。许多研究者认为在一阶逻辑内部无法解决该问题，这激发了大量关于非单调逻辑的研究。从 Dreyfus（1972）到 Crockett（1994）的哲学家都把 `frame problem` 视为整个 AI 企业必然失败的一个症状。通过 successor‑state 公理解决 `frame problem` 的方法归功于 Ray Reiter（1991）。Thielscher（1999）把推理 `frame problem` 视为独立概念并给出了解决方案。回顾起来，可以看到 Rosenschein（1985）的代理人实际上使用了实现 successor‑state 公理的电路，但 Rosenschein 没有注意到由此基本上解决了 `frame problem`。Foo（2001）解释了工程师通常使用的离散事件控制理论模型不必显式处理 `frame problem`：因为他们关注预测和控制，而非对反事实情况的解释和推理。

现代命题求解器在工业应用中具有广泛的适用性。命题推理在计算机硬件合成中的应用已成为标准技术，拥有许多大规模部署（Nowick **et al.**, 1993）。`SATMC` 满足性检查器用于检测 Web 浏览器用户登录协议中的先前未知漏洞（Armando **et al.**, 2008）。

Wumpus 世界由 Gregory Yob（1975）发明。讽刺的是，Yob 之所以创造它是因为他对在矩形网格上进行的游戏感到无聊：他的原始 wumpus 世界拓扑是十二面体，我们把它重新放回了无聊的旧网格。Michael Genesereth 最先提出将 wumpus 世界用作代理测试平台。

### EXERCISES

**7.1** 假设代理已经到达图 7.4(a) 所示的位置（Figure 7.4），在页 239（page 239），它感知到 `[1,1]` 没有任何事物，`[2,1]` 有阵风，`[1,2]` 有恶臭，现在它关心 `[1,3]`、`[2,2]` 和 `[3,1]` 的内容。这些格子中每个可能包含深井，且至多一个格子包含食尸。遵循 Figure 7.5 的示例，构建可能世界的集合。（你应该会得到 32 个世界。）标记出 KB 为真且每个下列句子为真的世界：

> α[2] = “`[2,2]` 中没有深井。”

> α[3] = “`[1,3]` 中有一只食尸。”

从而证明 *KB* ⊨ α[2] 且 *KB* ⊨ α[3]。

**7.2** （改编自 Barwise 和 Etchemendy (1993)。）在给定以下信息的情况下，你能证明独角兽是神话吗？它是魔法的吗？是有角的吗？

> 如果独角兽是神话，则它是永生的；但如果它不是神话，则它是有胎的哺乳动物。如果独角兽是永生或哺乳动物，则它是有角的。独角兽是魔法的，当且仅当它有角。

**7.3** 考虑判断给定模型下命题逻辑句子是否为真这一问题。

> **a**. 编写一个递归算法 `PL‑TRUE?(*s*, *m*)`，使其返回 *true* 当且仅当句子 *s* 在模型 *m*（该模型为每个句子中的符号赋予真值）中为真。算法的运行时间应与句子的大小线性。（也可以使用在线代码仓库中的该函数的一个版本。）

> **b**. 给出三个在部分模型中（即未为部分符号指定真值）可以判断为真或假的句子示例。

> **c**. 说明在部分模型中，句子的真值（如果有）一般无法高效确定。

> **d**. 修改 `PL‑TRUE?` 算法，使其能够在部分模型上有时判断句子的真值，同时保持递归结构和线性运行时间。给出三个在部分模型中其真值不被你的算法检测到的句子示例。

> **e**. 研究修改后的算法是否能使 `TT‑ENTAILS?` 更高效。

**7.4** 哪些选项是正确的？

> **a**. `False` ⊨ `True`。

> **b**. `True` ⊨ `False`。

> **c**. `(*A* ⋀ *B*)` ⊨ `(*A* ⇔ *B*)`。

> **d**. `*A* ⇔ *B*` ⊨ `*A* ⋁ *B*`。

> **e**. `*A* ⇔ *B*` ⊨ `¬*A* ⋁ *B*`。

> **f**. `(*A* ⋀ *B*) ⇒ *C*` ⊨ `(*A* ⇒ *C*) ⋁ (*B* ⇒ *C*)`。

> **g**. `(*C* ⋁ (¬*A* ⋀¬*B*))` ≡ `((*A* ⇒ *C*) ⋀ (*B* ⇒ *C*))`。

> **h**. `(*A* ⋁ *B*) ⋀ (¬*C* ⋁ ¬*D* ⋁ *E*)` ⊨ `(*A* ⋁ *B*)`。

> **i**. `(*A* ⋁ *B*) ⋀ (¬*C* ⋁ ¬*D* ⋁ *E*)` ⊨ `(*A* ⋁ *B*) ⋀ (¬*D* ⋁ *E*)`。

> **j**. `(*A* ⋁ *B*) ⋀¬(*A* ⇒ *B*)` 是可满足的。

> **k**. `(*A* ⇔ *B*) ⋀ (¬*A* ⋁ *B*)` 是可满足的。

> **l**. `(*A* ⇔ *B*) ⇔ *C*` 对于任何固定的命题符号集合（包含 *A*, *B*, *C*）具有相同数量的模型。

**7.5** 证明下列断言：

> **a**. α 是有效的当且仅当 `True` ⊨ α。

> **b**. 对任意 α，`False` ⊨ α。

> **c**. α ⊨ β 当且仅当句子 `(α ⇒ β)` 是有效的。

> **d**. α ≡ β 当且仅当句子 `(α ⇔ β)` 是有效的。

> **e**. α ⊨ β 当且仅当句子 `(α ⋀ ¬β)` 是不可满足的。

**7.6** 证明或找到以下断言的反例：

> **a**. 若 α ⊨ γ 或 β ⊨ γ（或两者皆是），则 `(*α* ⋀ *β*)` ⊨ γ

> **b**. 若 α ⊨ `(*β* ⋀ *γ*)`，则 α ⊨ β 且 α ⊨ γ。

> **c**. 若 α ⊨ `(*β* ⋁ *γ*)`，则 α ⊨ β 或 α ⊨ γ（或两者皆是）。

**7.7** 只包含四个命题 *A*, *B*, *C*, *D* 的词汇中，下列句子有多少个模型？

> **a**. `*B* ⋁ *C*`。

> **b**. `¬*A* ⋁ ¬*B* ⋁ ¬*C* ⋁ ¬*D*`。

> **c**. `(*A* ⇒ *B*) ⋀ *A* ⋀ ¬*B* ⋀ *C* ⋀ *D*`。

**7.8** 我们定义了四个二元逻辑连接符。

> **a**. 还有其他可能有用的连接符吗？

> **b**. 可能有多少种二元连接符？

> **c**. 为什么有些连接符不太有用？

**7.9** 使用你喜欢的方法，验证 Figure 7.11（第 249 页）中的所有等价关系。

**7.10** 判断下列句子是否有效、不可满足或两者皆非。使用真值表或 Figure 7.11（第 249 页）中的等价规则进行验证。

> **a**. `*Smoke* ⇒ *Smoke*`

> **b**. `*Smoke* ⇒ *Fire*`

> **c**. `(*Smoke* ⇒ *Fire*) ⇒ (¬*Smoke* ⇒ ¬*Fire*)`

> **d**. `*Smoke* ⋁ *Fire* ⋁ ¬*Fire*`

> **e**. `((*Smoke* ⋀ *Heat*) ⇒ *Fire*) ⇔ ((*Smoke* ⇒ *Fire*) ⋁ (*Heat* ⇒ *Fire*))`

> **f**. `(*Smoke* ⇒ *Fire*) ⇒ ((*Smoke* ⋀ *Heat*) ⇒ *Fire*)`

> **g**. `*Big* ⋁ *Dumb* ⋁ (*Big* ⇒ *Dumb*)`

**b**. 证明每个句子（无论正文字符的数量）都可以写成 `(*P*[1] ⋀ … ⋀ *P*[*m*]) ⇒ (*Q*[1] ⋁ … ⋁ *Q*[*n*])` 的形式，其中 *P*s 和 *Q*s 为命题符号。由这些句子组成的知识库称为 **蕴含正常形式** 或 **Kowalski 形式**（Kowalski, 1979）。

---

### IMPLICATIVE NORMAL FORM

---
