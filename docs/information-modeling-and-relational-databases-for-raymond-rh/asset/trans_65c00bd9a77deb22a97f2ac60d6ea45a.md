
# 15.3 过程理论基础

过程建模是一项应用，它激励了许多技术专家构建自动化系统，以支持过程定义、执行、管理等。目前流通的工具和技术可能远不止一百种，而且还在不断涌现。不幸的是，大多数方法都是基于对过程特性的模糊直觉，导致其相关语义往往只能靠猜测。如果我们有雄心从业务模型中推导信息系统要素，这是一种不幸的情况，因为我们的模型没有提供一个确定的基线来开展工作。由此产生的问题促使人们对以更正式的方式定义过程产生了兴趣。这种形式化不一定需要在业务层面暴露，但我们需要确信我们的业务模型建立在坚实的基础之上。

在这方面受到最多关注的技术是使用 `Petri nets`（Petri网）。这些最早是在 Carl Adam Petri 1962 年的博士论文中定义的。它们立即引起了理论家的兴趣，但花了更长的时间才找到实际用途。`Petri nets` 现在被用于许多领域，基本概念也已以多种方式进行了扩展。本节简要介绍它们如何用于表示业务过程。关于 `Petri nets` 更详细论述的参考资料见章节注释。

从根本上说，`Petri net` 是一个二分图，其某些节点具有可变标记。有两种节点类型：`places`（库所）和 `transitions`（变迁）。`Places` 和 `transitions` 通过有向弧连接。可能的连接是 place-to-transition（库所到变迁）或 transition-to-place（变迁到库所），但绝不会是 place-to-place（库所到库所）或 transition-to-transition（变迁到变迁）。`Petri net` 用于表示动态情况，但图的结构不会随着情况的展开而改变。相反，不同的条件通过网络中 `places` 处 `tokens`（令牌）的不同排列来标记。`Tokens` 的特定配置有时被称为网络的 `state`（状态）——此处的 `state` 并不完全具有我们稍后在本章讨论的状态机上下文中的相同含义。`Tokens` 根据特定规则在 `places` 处被创建或移除。`Token` 不能存在于 `transition` 处。在图形上，`places` 通常显示为大空心圆；`tokens` 显示为小实心圆；`transitions` 显示为矩形或粗条。[图 15.11](#Ch015_773-830_B9780443237904000190.xhtml#f0060) 显示了一个简单的 `Petri net`，其网络 `places` 处有一些 `tokens`。

![图 15.11 一个简单的 Petri 网。](images/B9780443237904000190/f15-11-9780443237904.jpg)

[图 15.11](#Ch015_773-830_B9780443237904000190.xhtml#B-f0060) 一个简单的 `Petri net`。

如果 `transition` 的每个输入 `place` 都有一个 `token`，则称该 `transition` 为 `enabled`（使能/就绪）。一个 `enabled` 的 `transition` 可以 `fire`（触发/发生），这样做会从其每个输入 `place` 消耗一个 `token`，并在其每个输出 `place` 产生一个 `token`。对于 [图 15.11](#Ch015_773-830_B9780443237904000190.xhtml#f0060) 所示的配置，`transition` `t1` 是 `enabled` 的，但 `t2` 和 `t3` 不是（`t3` 并非在其所有输入 `places` 处都有 `token`）。`transition` `t1` `fired` 后的结果情况如 [图 15.12](#Ch015_773-830_B9780443237904000190.xhtml#f0065) 所示。一个 `token` 从 `p1` 移除，一个新 `token` 在 `p2` 处添加。

![图 15.12 图 15.11 的网络在变迁 t1 触发后的状态。](images/B9780443237904000190/f15-12-9780443237904.jpg)

[图 15.12](#Ch015_773-830_B9780443237904000190.xhtml#B-f0065) [图 15.11](#Ch015_773-830_B9780443237904000190.xhtml#f0060) 的网络在 `transition` `t1` `fired` 后的状态。

概念上，`tokens` 在 `transitions` 处被消耗或创建。`Transitions` 可以有输入 `places`（从 `place` 指向 `transition` 的弧）或输出 `places`（从 `transition` 指向 `place` 的弧）。同一个 `place` 相对于某个 `transition` 可以既是输入 `place` 又是输出 `place`。在 [图 15.11](#Ch015_773-830_B9780443237904000190.xhtml#f0060) 中，`transition` `t1` 以 `p1` 作为输入 `place`，以 `p2` 作为输出 `place`。`Place` `p3` 对于 `t3` 既是输入 `place` 又是输出 `place`。

现在，`t2` 和 `t3` 都是 `enabled` 的。因为我们在 `p2` 处只有一个 `token`，所以 `t2` 和 `t3` 中只有一个可以 `fire`。在基本 `Petri net` 中，这种情况是非确定性的，因为我们无法预先决定哪个 `transition` 将会 `fire`。向 `place` `p2` 添加更多 `tokens` 无法解决这个问题，因为 `transitions` `t2` 和 `t3` 仍会竞争每个 `token`。然而，在这种情况下，无论哪个 `transition` `fires`，结果都是相同的 `state`。如果 `t2` `fires`，它消耗 `p2` 处的 `token` 并在 `p4` 处产生一个 `token`。如果 `t3` `fires`，它消耗 `p2` 和 `p3` 处的 `tokens` 并在 `p3` 和 `p4` 处产生 `token`。最终结果如 [图 15.13](#Ch015_773-830_B9780443237904000190.xhtml#f0070) 所示。此时，没有进一步的 `transitions` 是 `enabled` 的，活动停止。

