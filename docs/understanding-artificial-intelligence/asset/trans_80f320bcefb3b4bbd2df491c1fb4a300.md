
-   [事实上，这个名称在计算机科学研究人员和人工智能用户之间引发了巨大的误解。显然，这不是让程序在自然界中自由运行并指望它们自>能够独立管理的问题！我们只是利用计算机科学的一个属性。数据处理（例如如何进行加法运算）在程序中描述，而程序本身是提供给机器的数据。一个既是程序又是数据的程序可以被另一个程序修改或构建。

在如此看来，你可以编写基于数据的程序，这些程序能够生成新的人工智能程序。

![image](images/inline1_3.jpg)

## [OBEY, I SAY!](#contents.xhtml#toc2_10)

一切发生的方式就像在选择你的冒险的书中，作者让你重写一页的内容，通过替换某些词汇或在书的结尾空白页上写新的指令来实现。电脑处理的信息（无论是数据还是程序本身）都可以被程序修改。

然而，这种转换只能在遵循算法指令的情况下发生。程序不能产生*任何*程序。如果初始程序没有良好的指令，结果程序很可能包含错误，并且无法进行最基本的“智能”处理。让我们回到选择你的冒险的书的例子。如果作者的指令是将每个“e”替换为“w”，在完成指令后继续冒险的可能性很小！

此外，重要的是记住，你的学习程序（即产生处理程序的程序）所执行的操作始终取决于它接收到的数据。在选择你的冒险的书中，这样的指令可能是“找到你第一次捡起的第一个物品的第一个字母”。因此，修改取决于数据（即你选择先捡起的那个物品）。显然，如果数据选择不当，结果程序也不会很有效。

因此，使用机器学习的 AI 程序只能在我们提供良好数据和良好指令时，产生“好的”程序。这一切都不靠自动完成！

## [ATTENTION: ONE PROGRAM CAN CONCEAL ANOTHER!](#contents.xhtml#toc2_11)

我们离看到电脑自行编写程序以解决它从未被设计的问题还很遥远。这太困难了。数据集差异太大，可能需要编写的规则也太多，才能让程序正确运行。一个能解决任何问题并额外给你泡杯咖啡的 AI 根本不存在，因为每个问题需要特定的程序和匹配的数据。

为了编写 AlphaGo，谷歌的工程师必须编写一个初始程序来观察 Go 游戏的部分局面。利用这些数据，他们编写了第二个程序，能在每种情况下提供最佳走法。这花费了多年时间！而且他们必须给程序提供良好的信息，以便它能从数据中*学习*。

获得的结果特定于 Go：你不能直接将其用于其他游戏。你可以将分析程序适应并使用不同的数据来构建另一个程序，能够在国际象棋或跳棋中提供最佳走法。Google 已经做过这件事。但这需要程序员分析生成程序，修改它，描述国际象棋的规则，并解释如何分析国际象棋棋盘，这与分析 Go 棋盘大相径庭。你的程序不能修改自身来产生更智能的东西。

我们会期待赛车能跑赢鸡蛋并洗衣服吗？

![image](images/inline1_4.jpg)

## [SO, WHAT IS AI?](#contents.xhtml#toc2_12)

要理解 AI 是什么，我们将查看用于编写人工智能程序的不同方法。

所有这些方法都依赖于算法，这些算法有时易于理解，但往往难以实现。我们将看到，不同的人类推理任务促使研究人员发明方法来自动化它们。我们也会看到，有时这些方法与人类在相同情境下会做的完全不同的做法。正如 [Minsky (1968)](#ch01.xhtml#ref1_1) 所说，“让计算机程序执行人类在相同情境下更满意地完成的任务”。这不是让程序像人类一样完成任务。

Marvin Minsky 对 AI 的定义因此有些令人沮丧。从一开始，他就对 AI 设定了限制。一旦机器执行的任务与人类在完成同一任务方面表现相当，它就不再是 AI。这确实属实：如今没有人觉得 GPS 装置为去科罗拉多州看奶奶提供正确路线和花费其童年一样出色，但这仍然是 AI。

当然，还有其他关于人工智能的定义。1979 年 1 月 *La Recherche* 杂志（Research）第 96 期提出的定义很有趣，它指出：“人工智能旨在赋予计算机系统与人类相当的智能能力。”这仍然是幻想：“为机器赋予与人类相当的智能能力。”

这是一个非常雄心勃勃的目标。它让人稍稍梦想，也正是它让人兴奋的原因。然而，真正的问题是我们能在这一方向上走多远。

![image](images/inline1_5.jpg)

## [REFERENCE](#contents.xhtml#toc3_13)

Minsky, M. (1968). *Semantic Information Processing*. The MIT Press, Cambridge, MA.

\_\_\_\_\_\_\_\_\_\_\_\_\_

[1](#ch01.xhtml#Cfn1_1)  Indeed, in some languages, such as French and German, computer science is called “informatics,” which has the same root as “information.”

| [The Turing Test](#contents.xhtml#toc1_14)[*Understanding That It Is Difficult to Measure the Intelligence of Computers*](#contents.xhtml#toc1_14) || [2](#contents.xhtml#toc1_14) |

| --- | --- |

Before we develop any kind of artificial intelligence, it would be good if we define what intelligence is… and that’s where things get complicated! While we know quite well how to recognize stupidity (all you have to do is look around you and see what people do wrong), it’s harder to explain exactly what human intelligence is.

## [WHAT IS INTELLIGENCE?](#contents.xhtml#toc2_15)

The first idea that comes to mind is to define intelligence as the opposite of ignorance. Unfortunately, it’s not that simple. If I ask you what year the city of Moscow was founded, you most likely won’t know the answer. Yet no one could accuse you of not being intelligent just for that, even though the answer can be found in any encyclopedia. And you wouldn’t say the encyclopedia is intelligent simply because it can tell you the date Moscow was founded. Intelligence doesn’t consist of knowledge alone. You must also be able to use what you know.

A second idea would be to associate intelligence with the ability to answer difficult questions. For example, let’s consider Georg Cantor, the mathematician who founded set theory in the 19th century. To deal with such in-depth mathematical problems, he was clearly very intelligent. However, one’s ability in math is not enough to characterize intelligence. If I ask you what 26,534 × 347 is, it might take you some time to get the answer. However, a calculator will give you the result in an instant. You wouldn’t say that the calculator is intelligent, not any more intelligent than the encyclopedia.

![image](images/inline2_1.jpg)

