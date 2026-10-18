
# 强化学习简介：Rosie 机器人的学习过程

除了能够识别自身状态之外，Rosie 有三个内置的 *actions* 可以执行：她可以向前迈一步 *Forward*，向后迈一步 *Backward*，或者 *Kick*。（如果 Rosie 碰巧踩出界，她被编程为立即踩回界内。）为了体现操作性条件反射的精神，只有在 Rosie 成功踢到球时才给予奖励。请注意，Rosie 事先不知道哪些状态或动作会导致奖励。

鉴于 Rosie 是一台机器人，她的“奖励”仅仅是一个数字，比如 10，添加到她的“奖励内存”中。我们可以将数字 10 视为机器人版本的狗零食。或者也许不是。与真正的狗不同，Rosie 对零食、正数或任何其他东西都没有内在的 *desire*。如下文所述，在强化学习中，人类创建的算法指导 Rosie 对奖励的学习过程；也就是说，算法告诉 Rosie *如何* 从她的经验中学习。

强化学习是通过让 Rosie 在一系列学习 *episodes* 中采取行动来实现的，每个 episode 由若干个 *iterations* 组成。在每个 iteration 中，Rosie 确定她当前的状态并选择要采取的动作。如果 Rosie 收到奖励，她随后会 *learn* 某些东西，如下文所示。这里我让每个 episode 持续到 Rosie 成功踢到球，此时她会收到奖励。这可能需要很长时间。就像训练真正的狗一样，我们必须耐心。

[Figure 23](#chapter8.xhtml#fig23) 说明了一个假设的学习 episode。episode 开始时，训练师（我）将 Rosie 和球放置在场地上的某个初始位置，Rosie 面朝球（[figure 23*A*](#chapter8.xhtml#fig23)）。Rosie 确定她当前的状态：距离球十二步远。因为 Rosie 还没有学到任何东西，我们的狗，一个天真的“tabula rasa”，不知道应该偏好哪个动作，所以她从三个可能性中随机选择一个动作：*Forward*、*Backward*、*Kick*。假设她选择了 *Backward* 并向后退了一步。我们人类可以看出 *Backward* 是一个不好的动作，但请记住，我们让 Rosie 自己想出如何完成这项任务。

![FIGURE 23: A hypothetical first episode of reinforcement learning](images/Figure23.jpg)

FIGURE 23: A hypothetical first episode of reinforcement learning

在 iteration 2 中（[figure 23*B*](#chapter8.xhtml#fig23)），Rosie 确定她的新状态：距离球十三步远。然后她选择一个新动作，再次随机：*Forward*。在 iteration 3 中（[figure 23*C*](#chapter8.xhtml#fig23)），Rosie 确定她的“新”状态：距离球十二步远。她回到了原点，但 Rosie 甚至不知道她之前处于这个状态！在最纯粹的强化学习形式中，学习代理不记得其之前的状态。一般来说，记住之前的状态可能需要大量内存，并且最终并不必要。

在 iteration 3 中，Rosie——再次随机——选择了动作 *Kick*，但因为她在踢空气，所以她没有得到奖励。她还没有学到踢球只有在她靠近球时才会得到奖励。

Rosie 继续在许多 iterations 中选择随机动作，没有任何反馈。但在某个时刻，假设在 iteration 351，Rosie 仅凭运气最终靠近球并选择了 *Kick*（[figure 23*D*](#chapter8.xhtml#fig23)）。最后，她得到了奖励并用它来学习一些东西。

Rosie 学到了什么？这里我们采用最简单的强化学习方法：在收到奖励后，Rosie 只学习紧接在奖励之前的状态和动作。特别是，Rosie 学到如果她处于该状态（例如，距离球零步远），采取该动作（例如，*Kick*）是个好主意。但她只学到这些。例如，她不会学到如果她距离球零步远，*Backward* 会是一个 *bad* 的选择。毕竟，她还没有尝试过。就她所知，在该状态下向后退一步可能会导致更大的奖励！Rosie 此时还没有学到，如果她距离球 *one* 步远，*Forward* 会是一个好选择。她必须等到下一个 episode 才能做到这一点。一次学习太多可能会有害；如果 Rosie 在距离球两步远时碰巧踢空气，我们不希望她学到这个无效的踢球实际上是获得奖励的必要步骤。在人类中，这种行为可能被称为迷信——即错误地相信某个特定动作可以帮助导致某个特定的好或坏结果。在强化学习中，迷信是你必须小心避免的事情。

强化学习中一个关键的概念是 *在给定状态下执行特定动作的价值*。状态 *S* 下动作 *A* 的 *value* 是一个数字，反映了代理当前预测如果在状态 *S* 下执行动作 *A*，然后继续执行高价值动作，最终将获得多少奖励。让我解释一下。如果你当前的状态是“手里拿着一块巧克力”，高价值的动作就是把手送到嘴边。随后的高价值动作是张开嘴，把巧克力放进去，咀嚼。你的奖励是吃巧克力的美味感觉。把手送到嘴边不会立即产生这个奖励，但这个动作走在正确的道路上，如果你以前吃过巧克力，你可以预测即将到来的奖励的强度。强化学习的目标是让代理学习即将到来的奖励的良好预测值（假设代理在采取该动作后继续做正确的事情）。^() ![FIGURE 24: Rosie’s Q-table after her first episode of reinforcement learning](images/Figure24.jpg)

FIGURE 24: Rosie’s Q-table after her first episode of reinforcement learning

Rosie 在她的计算机内存中保存一个大表格，记录动作的值。这个表格在 [figure 24](#chapter8.xhtml#fig24) 中有所插图，列出了 Rosie 的所有可能状态（即她可能距离球的所有距离，直到场地长度），以及每个状态下她可能的动作。给定一个状态，该状态下的每个动作都有一个数值；这些值会随着 Rosie 继续学习而改变——变得更准确地预测即将到来的奖励。这个状态、动作和值的表格被称为 Q-table。这种形式的强化学习有时被称为 Q-learning。字母 *Q* 被使用是因为字母 *V*（代表 *value*）在 Q-learning 的原始论文中被用于其他目的。^()

在 Rosie 训练开始时，我通过将所有值设置为 0 来初始化 Q-table——一个“blank slate”。当 Rosie 在 episode 1 结束时因踢球而获得奖励时，在状态“距离球零步远”时动作 *Kick* 的值被更新为 10，即奖励的值。在未来，当 Rosie 处于“距离球零步远”状态时，她可以查看 Q-table，看到 *Kick* 具有最高值——即预测最高奖励——并决定选择 *Kick* 而不是随机选择。这就是这里“学习”的全部含义！
