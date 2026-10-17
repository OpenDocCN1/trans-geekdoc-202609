
# 人工智能入门指南

![image](img/9781000284256.jpg)

Nicolas Sabouret

插图由 Lizete De Assis 绘制

![image](img/inlinefm_1.jpg)

![image](img/logo.jpg)

已尽合理努力确保出版的数据和信息可靠，但作者和出版商不承担所有材料的有效性或其使用后果的责任。作者和出版商已尝试追踪本出版物中所有材料的版权持有者，并对未获得出版许可的版权持有者表示歉意。如果本出版物中任何版权材料未被注明，请写信告知我们，以便在未来重印时进行更正。

除美国版权法允许的范围外，本书的任何部分不得以任何电子、机械或其他任何方式（现有或以后发明的方式，包括复印、微缩摄影、录音或在任何信息存储或检索系统中使用）复制、再版、传输或利用，未经出版商书面许可。

如需许可复印或电子使用本书内容，请访问 [www.copyright.com](http://www.copyright.com) 或联系版权清除中心（CCC），地址：222 Rosewood Drive, Danvers, MA 01923，电话：978-750-8400。对于未在 CCC 上提供的作品，请联系 mpkbookspermissions@tandf.co.uk。

*商标声明*：产品或公司名称可能是商标或注册商标，仅用于识别和说明，且不意侵犯任何权利。

ISBN: 978-0-367-53136-2 (平装)

ISBN: 978-0-367-52435-7 (精装)

ISBN: 978-1-003-08062-6 (电子版)

排版采用 Times New Roman 字体

由 MPS Limited, Dehradun 设置排版

*致查克，满怀友谊*。

## 1 什么是人工智能？理解计算机、算法、程序，特别是人工智能程序

计算机科学与计算机

计算机与算法

算法与计算机科学

全能机器

编程程序编程程序

人工智能在此过程中处于何处？

一个会学习的机器？

服从，我说！

注意：一个程序可能隐藏另一个程序！

那么，人工智能是什么？

参考

跟随乌鸦

有一个技巧！

First, it effectively calculates a solution: that’s a good start. Plus, it does it very fast. The program’s complexity is the number of points squared, the same as with Dijkstra’s algorithm, which we used for the GPS. This means the computer can work on graphs with a thousand points before hitting any real difficulty. Not so bad, right? Especially for an AI algorithm that requires less than ten lines of computer code!

Now, with that being said, the solution probably won’t be the best. In certain cases, it can even be very bad.

Imagine we leave from Limoges and have to visit Toulouse, Bordeaux, Marseille, and Nantes before we return to Limoges. With the greedy algorithm, we’re going to go to Bordeaux first (137 miles), then to Toulouse (152 miles), then to Marseille (252 miles), before we go 615 miles in the opposite direction to Nantes, passing through Bordeaux and Toulouse, or through Clermont-Ferrand. If we had done a little thinking, we probably would have gone to Nantes first, which is, admittedly, a little further from Limoges than Bordeaux (186 miles), but then we would have passed through all the other cities in a loop (Nantes, Bordeaux, Toulouse, Marseille), instead of making the same trip twice. Our loop would have been 805 miles instead of almost 1,160 miles!

## COME ON, WE CAN DO BETTER!

The problem with the greedy algorithm is that it doesn’t attempt to do any better than the first path it determines. It’s a real shame because this first solution isn’t necessarily very good, and it might be easy to fix a few mistakes, like going to Nantes and back, which isn’t well positioned on the route。

幸运的是，人工智能研究者拥有更好的方法。要理解它们，我们必须探索一个新的空间。

但先让我们回到我们已经看到的内容：`state` 空间的探索。记住：`state` 空间是可能状态的集合。在 GPS 问题中，我们在这个空间中行走，寻找解决方案。在旅行售货员问题中，情况完全相同：我们的贪婪的售货员会按照“就近选择”原则，从一个点跳到另一个点。

然而，还有一个空间：`solution` 空间。这个概念稍微难以理解。想象一下，你不再关心你经过的城市（即状态），而是关心决定你整个路径的城市列表（即解）。在旅行售货员问题中，任何解都是指你已经访问了所有城市，无论顺序如何。波尔多、图卢兹、马赛、 Nantes 是一个解。马赛、图卢兹、波尔多、 Nantes 是另一个（更好的）解。所有这些解的集合，统称为解空间。

贪婪算法只是匆忙地搜索“任意”解：它选择解空间中的一个单一值。

![image](img/inline6_3.jpg)

### THE SOLUTION SPACE

旅行售货员问题的难点在于解空间的规模。如果我们要访问 `N` 个城市（除了出发城市），那么第一个城市有 `N` 种选择，下一个有 `N - 1` 种选择，以此类推。总共有

`N × (N − 1) × (N − 2) × ⋯ × 3 × 2 × 1`

种访问所有城市的方案。这对数学家来说很熟悉，被称为 `factorial`，用感叹号表示。因此，我们有 `N!` 种方案来访问 `N` 个城市。换句话说，对于大小为 `N` 的状态空间（如旅行售货员问题），其解空间的大小为 `N!`。

一旦我们开始讨论复杂度和问题规模，`factorial` 函数就失去了魅力。事实上，它的值增长得非常迅速。为了让你有个概念，如果 `N` = 4，我们将有 24 种可能的解；如果 `N` = 7，这就已经是 5,000 种了；如果 `N` = 10，则超过 3 百万！因此，尝试全部方案以决定最佳方案是不可想象的。

### ONE GRAPH CAN CONCEAL ANOTHER!

另一方面，尽管有这么多解，我们仍然可以构建一个图：只需“连接”这些解即可。计算机科学家喜欢这些图，因为他们可以基于图编写大量算法。

要构建这个解空间图，我们需要在解空间中连接两个解，当它们仅因两个城市的位置不同而相同时。例如：

`Limoges` → `Marseille` → `Toulouse` → `Bordeaux` → `Nantes`

将是 `Limoges` → `Bordeaux` → `Toulouse` → `Marseille` → `Nantes` 的邻解。

我们只是在路线中交换了 Bordeaux 和 Marseille 的位置。

在拥有 24 种解（四个城市需要访问）的解空间中，我们将把每个解与六个邻解相连，每个邻解对应于在路线中交换两个城市的可能情况。

现在，我们拥有一个带有邻解的图，情况与状态空间类似。因此，我们可以使用算法来“探索”这个解空间。为什么不呢！

### SPACE EXPLORATION

这一想法被应用于 1986 年由科罗拉多大学研究员 Fred Glover 提出的算法——`Tabu search` 方法。这个有趣的名字来源于在该算法中，我们被禁止重新考虑已经被探索过的任何解：它是禁忌的。该算法不限于旅行售货员问题，它可以用于探索任何人工智能问题的解空间。

使用 Tabu search 方法解决问题的步骤如下：你从一个初始解开始（例如，由贪婪算法得到的解），然后查看其在解空间中的邻解。对于每个邻解，你可以计算其 `cost`——即使用该新解时需要行驶的总里程（如果你在解决旅行售货员问题）。Tabu search 算法然后选择成本最低的邻解。注意：这个解可能比你的初始解**不如**它！它只是在所有邻解中成本最低的那一个。无论它是更好还是更差，你都会把前一个解放入“Tabu”列表。

然后，算法继续：你检查新解的邻解（除非它们已经被禁忌），并选择最佳的一个。接着，你把旧解放入 Tabu 列表，重新开始，以此类推。

![image](img/inline6_4.jpg)

一段时间后，我们需要停止。如果继续下去，我们可能会尝试检查所有的解。数量太多：著名的 `N!`。例如，你说：“好，我只尝试 10,000 种解后停止。”此时，你查看 Tabu 列表中的所有解，从第一个（你最初使用的）到最后一个（你结束时的解），并保留最好的一个。

这就是 Tabu 方法。简单吧？而且这个方法产生相当不错的结果。但如果我们认真思考，我们可以做得更好。为此，我们只需要汇聚多于一个人的努力。

| Darwin 2.0*Understanding How to Explore Space as a Group* || 7 |

| --- | --- |

一种广为人知的人工智能方法用于探索解空间，即使用 `evolutionary algorithms`（进化算法）。该方法由德国研究员 Ingo Rechenberg 在 1965 年发明；然而，人工智能研究者直到 1990 年代末才开始关注它。

### NATURAL SELECTION

进化算法的思想是直接借鉴自然选择理论——查尔斯·达尔文在 1838 年的进化论中提出的原理。达尔文认为，物种的进化取决于环境。适应性更强的个体更有可能生存。生存下来的个体会繁衍后代，传递那些帮助它们生存的特征（更好）。

以一群史前长颈鹿为例：长颈和长腿的长颈鹿会比其他长颈鹿更有优势，因为它们能够吃到非洲草原上生长的金合欢树叶。因此，它们更有可能生育后代，而长颈和长腿是遗传特征，在繁殖时会传递给后代。于是，随着时间的推移，群体中只会留下长颈鹿——即我们今天所知的长颈鹿。

人工智能利用这个思想，构建启发式方法来探索解空间。

我觉得你可能有点困惑。我们要让长颈鹿编程电脑吗？不完全是。我们要编写一个算法，在所有可能的解中找到最佳的一个。从这个意义上说，它和 Tabu 算法类似——但这次，我们不满足于只有一个微不足道的个体在“解空间”图中漫无目的地游荡；我们将使用一整群个体。为此，我们将从草原上的长颈鹿中汲取灵感。

### COMPUTING HERDS

想象一下，如果我们不是长颈鹿，而是一群解——也就是在解空间中有一个点的集合。想象你可以从这群中随机选择两个解，然后从中生成新的解。目前，这可能听起来有点抽象，但我们稍后会更清晰地看到。暂且假设这是可能的。

演化算法的原理如下。我们从我们的群体（即“群体”）中随机选择两个解，并基于这两个点构建新的解。我们不断重复这一过程。初始解的总数随着其他解和从其他解生成的解而增多。

随后，我们消除最弱的解（这是自然选择的硬性法则），从而稍微稀释我们的群体。理论上，新群体的解质量应高于初始群体。初始群体中最好的几个解会保留，而糟糕的解则被消除。同样，在“子解”中，只有最好的才会保留，糟糕的解则被消除。

随后，演化算法在新群体上运行，进行繁殖和选择，以持续改进种群。经过一段时间，我们应只有最优秀的解！

![image](img/inline7_1.jpg)

### YOU’VE GOT TO START SOMEWHERE

使用此类算法需要遵循三个步骤：

```
1. 构建初始解集。
```

```
2. 选择成对的解以生成新解。
```

```
3. 消除最弱的解并重复步骤 2。
```

每个步骤都有其自身的困难。第一个困难是创建一个包含大量不同解的群体。如何做到这一点？我们花了一整章时间才理解如何生成一个单一解！

老实说，这取决于具体问题。对于旅行售货员问题，很容易生成大量解：我们只需随机选择一个城市接一个城市即可。 Limoges、Marseille、Bordeaux、Toulouse、Nantes，就完成了！不需要思考。可以编写一个随机生成解的算法如下：

```
Let L be the cluster of cities.
Randomly choose a city in L.
Remove this city from L.
Repeat.
```

它运行非常快：对于包含一百个城市的图（N = 100），我们可以在一千毫秒内生成一千个解！

当然，随机选择的解不一定质量好，恰恰相反，它们很可能完全无用。但这不重要：算法会使它们演化成更好的东西。

### TWO BEAUTIFUL CHILDREN!

记住原则：就像长颈鹿一样，个体（解）会繁殖并生出孩子，只有最优秀的才能在旅行售货员丛林中艰难的自然选择法则下存活。

你可能在想，“解”基本上只是电脑中的数字，怎么能繁殖并产生孩子？为什么不设置一个 eHarmony 供解匹配呢？你是对的。这只是一个示例。我们将随机选择两个解并“混合”它们，就像两个生物体结合 DNA 一样。

让我们看一个例子。假设我们需要访问 15 个城市，我们将它们命名为 A、B、C、D、E、F、G、H、I、J、K、L、M、N、O。现在，随机选择两个解：Dad-solution，其路线为 ABEDCFHGJMNLKIO，以及 Mom-solution，其路线为 DFKNMJOACBEIGLO。

构建“子”解时，我们取 Dad 解中指定顺序的前几个城市，以及 Mom 解中按顺序的后续城市。

我们随机选择初始城市数量。例如，我们决定保留 Dad 的前六个城市：ABEDCF。然后，我们按顺序取 Mom 的城市（排除已访问的）：KNMJOIGLO。这给出以下解：

ABEDCF KNMJOIGLO

这就完成了！这个操作称为 crossover（交叉），也可以写成算法形式：父解是从中取元素放入“子”解的集群。如果算法写得好，它只需要很少的操作，从而可以通过选择父解对来生成大量解。如果我们回到一千个包含一百个城市的解的例子，通过对随机选择的父解一千次应用交叉算法，我们在一千毫秒内得到一千个全新的“子”解！

![image](img/inline7_2.jpg)

### A LITTLE MORE RANDOMNESS

演化算法也可以使用基因突变，就像在现实生活中一样。有时（随机地），子解中的一个会“突变”，即交换两个城市。这个小操作可以帮助算法更快找到好解，只要这些突变保持罕见。它会生成与父解不一致的解：如果结果灾难性，突变将不会被保留。但如果质量好，突变将在未来世代中对解有益！

演化算法本质上是一种聪明地探索解空间的方法。因为我们的“个体”只是机器中的数字，所以不存在自然选择。当你“混合”两个解来生成新解时，你只是在解空间中选择一个新点，该点共享初始解的特征。

如果你的两个初始解是好的（即相对较短的旅行售货员路径），你有两种可能性。一种是子解的路径不如父解好，此时它将在旅程结束后被消除。另一种可能是子解的路径更好，因为父解的路径帮助缩短了另一条路径，此时我们保留它。这就是你的种群如何进步。

![image](img/inline7_3.jpg)

突变本身的行为类似于我们上一章末尾看到的 Tabu search。它允许我们在解空间中探索邻域，寻找旅行售货员的新路径，而不会丢失之前已经计算的所有内容。

研究人员数学上证明，这种算法运行良好。只要你编程正确，并且进行足够多的迭代，你就会得到一个非常好的解！

### SO, WHAT IS THIS GOOD FOR?

与 Tabu search 类似，演化算法是我们称之为 *metaheuristics* 的方法，因为它们在解空间工作，而不是在状态空间。像所有启发式方法一样，它们不寻找最佳解，而是尽可能探索解空间的一小部分，以在可用时间内找到一个“好”解。最终，它们选择的解不过是一种启发式：比如“如果你经过 Nantes、Bordeaux、Toulouse，然后去 Marseille，这不应该太差”。

这些方法的优势在于它们可以用于各种不同的问题，无论解是如何构建的。这使它们非常强大！元启发法广泛用于物流：优化卡车车队的路线、管理空中交通、改善核反应堆的装载……这只是演化算法和元启发法搜索方法的小样本。

还有更多例子，例如 3G 移动网络优化（即在哪里放置天线以确保最佳覆盖），甚至 NASA 工程师开发的自动空天线，它是通过演化算法自动计算的。我们尚未回答的问题是“如何最大化接收？”计算机的答案是这根小而弯曲的铁丝。谁 else 会发明这个，如果不是计算机？

![image](img/inline7_4.jpg)

### THIS DOESN’T SOLVE EVERYTHING, HOWEVER
