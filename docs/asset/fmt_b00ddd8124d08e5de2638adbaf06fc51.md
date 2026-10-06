
Figure 21-21: The same game as Figure 21-20 after 6,000 episodes of training

This is very nice. The algorithm found the easy answer and went right for it.

We seem to have created a great algorithm for learning and playing. So why did we label everything with "L" for lousy? It seems to be working just fine.

It *is* just fine, as long as the environment remains completely predictable. Remember that earlier in this chapter we discussed unpredictable environments. In reality, most environments are unpredictable. Logic-based single-player games, such as the Flippers game we've been looking at, are one of the few activities that are completely deterministic. If our goal is to play only single-player games in completely deterministic environments where we are able to execute every intended move perfectly and the environment responds identically every time, then this algorithm isn't so lousy. But such deterministic games and environments are rare. For example, as soon as there's a second player, there's uncertainty, and the game becomes unpredictable. In any situation in which the environment is not perfectly deterministic, the L-learning algorithm flounders.

Let's see why, and then we will see how to fix it.

### Handling Unpredictability

Because we don't have an opponent when playing Flippers on the computer, we have a completely deterministic system. Every time we make a move, we are guaranteed to get back the same result. But in the real world, even single-player activities can have unpredictable events. Video games throw random surprises at us, a lawnmower can hit a rock and jump to the side, or an internet connection can stutter and cause us to miss making the winning bid in an auction.

Since handling unpredictability is so important, let's introduce some artificial randomness into Flippers and see how our L-learning algorithm responds. Our model of randomness takes the form of a big truck that drives by our playing area every now and then, shaking our board. Sometimes it's enough to cause one or more random tiles to spontaneously flip over. Of course, we still want to play good games and win, even in the face of such surprises, but our L-learning system is helpless in the face of this kind of event.

It's the combination of our policy and update rule that causes trouble. Remember that before we start learning, each row starts out with all zeros. When a training game is finally won, every action gets the same score, based on the length of the game, as we saw in Figure 21-19. As we continue to play our training games, the next time we come to that board, we pick the cell with the largest value.

Suppose we're in the midst of a training game. We're looking at a board that we once received as a starting board and we won it in two moves. The `L`-table values for each of those moves have large scores, so we select the high-scoring move, preparing to win on the next flip. But just after our first move, the big truck comes rumbling by, shaking our board and flipping a tile. Playing from this board forward, we end up requiring lots of moves before winning. This means that the `TFR` that ultimately comes from playing that action is less than if the truck hadn't come by.

And here's the problem: that smaller value overwrites the previous value in every cell that led to this long game. In other words, because of that event, every action we played sees its `L`-value lowered. In particular, that great starting move that led to victory in just one more move now has a low score. When we encounter this board again in a later game, we might find that one of the other cells has a larger value than the cell that formerly held the great move. The result is that this one-time random event causes us to stop making the best move we've found up to that point. We have "forgotten" that this was a great move, because a random event turned it into a bad move once. That low score makes it unlikely that we'll ever choose that move again.

Let's see this problem in action. Figure 21-22 shows an example where there are no unpredictable events. We start at the top with a board with three dots, and we find that the largest value in that row of the table is 0.6, corresponding to a flip of the center square. We make that move, and supposing the next move is also well-chosen, we have a victory in two moves, as shown in the center row. The reward of 0.7 replaces the 0.6 that was there for our first move, cementing that move's status as the one to make. Everything went right.

![Figure 21-22: 当没有惊喜时，我们的算法表现良好。(a) 起始棋盘的 L 表的行。(b) 游戏进行并仅用两步即获胜。(c) 0.7 的值覆盖了导致此成功的所有表条目的先前值。](img/F21022.png)

Figure 21-22: 当没有惊喜时，我们的算法表现良好。(a) 起始棋盘的 L 表的行。(b) 游戏进行并仅用两步即获胜。(c) 0.7 的值覆盖了导致此成功的所有表条目的先前值。

在 Figure 21-23 中，我们介绍了我们的震动卡车。翻转中心瓦片后，卡车晃动棋盘，右下角的瓦片翻转。这使我们走上全新的路径。假设算法最终在四步后找到胜利。总共是五步，奖励 0.44 置于导致此成功的每个单元格中。

这很糟糕。在一次快速的动作中，我们"忘记"了最佳动作。在此示例中，另外两个动作现在得分更高。下一次我们来到这张棋盘时，得分为 0.55 的单元格会被选中，这与之前将我们一步远离胜利不同。换句话说，我们的最佳动作现在被遗忘了，我们总是会选择更差的动作。

![Figure 21-23: (a) 卡车震动时，它翻转右下角方格，导致游戏用五步获胜。(b) 新奖励 0.44 覆盖了旧值 0.6。该单元格不再是该行中最高得分的单元格。](img/F21023.png)

Figure 21-23: (a) 卡车震动时，它翻转右下角方格，导致游戏用五步获胜。(b) 新奖励 0.44 覆盖了旧值 0.6。该单元格不再是该行中最高得分的单元格。

我们曾说，在训练时，我们会随机选择行中的一个单元格，以探索可能发生的情况。因此，有一天我们可能会做出新的选择，或者卡车再次震动并帮助我们记住该单元格，但这可能需要很长时间。到那时卡车到来并使该动作重新正确时，其他情况已经变坏了。L 表几乎总是低于它应有的水平，因此由 L 学习驱动的游戏在平均上更长，我们获得的奖励更低。一次惊喜导致我们忘记如何很好地玩这张棋盘。

因此，我们称这个算法是糟糕的。

但一切并非失去。我们之所以关注这个算法，是因为糟糕的版本可以被改进。算法的大部分是好的。我们只需要在面对不可预测性时修复它的失败。从现在起，我们假设在玩 Flippers 时，这辆大卡车可能会轰鸣而来，以不确定性的形式偶尔翻转一个随机瓦片。在下一节中，我们将看到如何优雅地处理这种不可预测的事件，并产生一个运行良好的改进学习算法。

## Q-Learning

通过不费力的努力，我们可以将 L-learning 升级为今天广泛使用的更有效的算法 `Q-learning`（`Q` 代表质量）(Watkins 1989; Eden, Knittel, and van Uffelen 2020)。`Q-learning` 看起来与 L-learning 非常相似，但自然地，它使用 `Q`-表填充 `Q`-值。主要改进是 `Q-learning` 在随机或不可预测的环境中表现良好。

从 L-learning 到 `Q-learning` 我们进行三个升级：改进 `Q`-表单元格的新值计算方式、改进现有值的更新方式、以及改进所使用的动作选择策略。

`Q`-table 算法基于两个重要原则。第一，我们*期望*结果中的不确定性，因此从一开始就将其纳入。第二，我们在进行过程中计算新的 `Q`-表值，而不是等待最终奖励。这个第二个想法使我们能够处理运行时间很长，甚至永远不会得出结论（如电梯调度）的游戏或过程。通过边更新边计算，即使我们从未收到最终奖励，也能构建有用的表。

为了实现这一点，我们还需要升级环境的简单奖励过程。与总是只在最终一步奖励 0 以外的情况不同，环境现在会在动作被取后立即返回奖励，以估计该动作的质量。

### Q-Values and Updates

`Q`-值是一种方式，用于在不知道结果如何结束时，近似总未来奖励。要找到一个 `Q`-值，我们将即时奖励加上尚未到来的其他奖励。迄今为止，这与总未来奖励的定义并无不同。变化在于，我们现在使用下一个状态的奖励来计算未来奖励。

在 Figure 21-17 中，我们为每一次移动保存了四个信息：起始状态、所选动作、获得的奖励以及该动作让我们到达的新状态。我们保存了新状态，以便在此使用它来计算其余的未来奖励。

关键的洞察是注意到，下一步的移动始于该新状态，并且按照我们的策略，我们总会选择 `Q`-值最大的动作单元格。如果该单元格的 `Q`-值等于该动作的总未来奖励，那么将该单元格的值与即时奖励相加，就得到当前单元格的总未来奖励。这是因为我们的策略保证在任何给定棋盘状态下，总是选择 `Q`-值最大的单元格对应的动作。

如果下一个状态中有多个单元格共享最大值，那么到达该状态时选择哪一个并不重要。我们现在只关心从该动作得到的总未来奖励。

Figure 21-24 直观地展示了这个想法。注意，我们在此步骤计算出的值不是最终的 `Q`-值，但它非常接近。

![Figure 21-24: 计算新 Q-值的过程的一部分。新值是其他两个值的和。第一个值是该单元格对应的动作的即时奖励，这里是 0.2。第二个值是新状态所有动作中最大的 Q-值，这里是 0.6。](img/F21024.png)

Figure 21-24: 计算新 `Q`-值的过程的一部分。新值是其他两个值的和。第一个值是该单元格对应的动作的即时奖励，这里是 0.2。第二个值是新状态所有动作中最大的 `Q`-值，这里是 0.6。

缺少的步骤是 `Q-learning` 如何考虑随机性。与其使用下一步动作的单元格值，我们使用该单元格的折扣值。回顾，这意味着我们将该单元格的值乘以折扣因子，一个在 0 到 1 之间的数，通常用 *γ* (gamma) 表示。正如我们之前讨论的，γ 越小，我们就越不确定未来的不可预测事件不会改变这个值。Figure 21-25 展示了这个想法。

![Figure 21-25: 为了找到 Q-值，我们在 Figure 21-24 中加入折扣因子 γ，它根据我们对未来不可预测事件不会改变该值的置信度来减少未来奖励。](img/F21025.png)
