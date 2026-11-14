

分层优先行为列表以略微增加复杂度为代价获得了分层决策能力，但在其他方面与优先行为列表共享相同的优势和劣势。

## 6.4.3 Behaviour Trees

Behaviour trees are the perfect embodiment of hierarchical decision-making. 行为树是分层决策的完美体现。

They are also very strong when it comes to modularisation given that most implementations are built with a heavy emphasis on reusable building blocks, even though technically that is not a requirement. 在模块化方面也非常强大，因为大多数实现都大量强调可重用的构建块，尽管从技术上讲这并非要求。

Behaviour trees allow the author good reasoning about which behaviour is going to execute, as their execution order is the depth-first search order of the tree until the first valid leaf is located. 行为树使作者能够很好地推理哪个行为即将执行，因为它们的执行顺序是树的深度优先搜索顺序，直到找到第一个有效叶节点。

Understanding the current state of a behaviour tree and why a specific behaviour has been selected is straightforward. 理解行为树的当前状态以及为何选择了特定行为非常简单。

Just looking at the current active branch will give you most of the information, and by saving a little more data, you can easily display exactly which tests failed and which succeeded. 只需查看当前活跃分支即可获取大部分信息，再保存一点更多数据，就可以轻松显示哪些测试失败了，哪些测试成功了。

Displaying the current state of a behaviour tree in game can be a little tricky since fitting trees on a screen quickly becomes difficult as they scale, but many systems have solved this problem by connecting their tree editor to the run-time, which allows for good visualisation. 在游戏中显示行为树的当前状态可能有点棘手，因为随着树的规模扩大，在屏幕上容纳树会迅速变得困难，但许多系统通过将树编辑器连接到运行时来解决了这个问题，从而实现了良好的可视化。

Where behaviour trees fall short is when you are dealing with states and state transitions. 行为树的不足之处在于处理状态和状态转换时。

For instance, a node, like one playing an animation, that cannot be immediately exited requires some awkward compromises. 例如，像播放动画这样无法立即退出的节点需要一些笨拙的折中方案。

## 6.4.4 Finite-State Machines

FSMs excel when it comes to describing states and transitions between them. 有限状态机在描述状态及其之间的转换方面表现出色。

They make it easy to understand under what circumstances a behaviour is going to be active, and they are straightforward to visualise, yet FSMs' real weakness is in those same transitions. 它们使得在什么情况下某个行为会处于活跃状态变得容易理解，并且易于可视化，但有限状态机的真正弱点在于那些相同的转换。

The problem is that each state needs to have one transition per state that it is possible to transition to from that state. 问题是，每个状态都需要为从该状态可能转换到的每个状态提供一个转换。

Often, most states are available from a given state, which leads to n² transitions. 通常，从给定状态可以访问大多数状态，这会导致 n² 个转换。

This results in a maintenance nightmare to keep track of all the transitions as the number of states grow. 这导致随着状态数量增长，跟踪所有转换变成了维护噩梦。

This creates a lot of work to add all the needed connections when adding a new state and makes it difficult to visualise a large number of states and transitions. 这在添加新状态时需要大量工作来添加所有所需的连接，并且使可视化大量状态和转换变得困难。

Another related issue is that in many cases, there is no need for states with elaborate transitions in the first place. 另一个相关问题是，在许多情况下，根本不需要带有复杂转换的状态。

For instance, in combat, an agent may switch freely between most actions available to it assuming that they are valid. 例如，在战斗中，代理人可能会在大多数可用动作之间自由切换，假设它们有效。

It might want to switch from attacking to moving closer to its target as soon as the target moves out of range, and back to attacking when it gets within range again. 它可能希望在目标移出攻击范围时立即从攻击切换到向目标移动，并在重新进入范围时切换回攻击。

The AI does not need a complex transition from attacking to moving, it just needs to start moving, and when it is close enough, it will switch back to attacking again. AI不需要从攻击到移动的复杂转换，它只需要开始移动，当足够接近时，就会切换回攻击。

Implementing this in an FSM just adds unnecessary overhead. 在有限状态机中实现这一点只会增加不必要的开销。

## 6.4.5 HIERARCHICAL FINITE-STATE MACHINES

Hierarchical Finite-State Machines (hFSMs) are FSMs where each state can contain a nested state machine that forms a hierarchy. 分层有限状态机（hFSMs）是指每个状态可以包含嵌套状态机以形成层次结构的有限状态机。

hFSMs are like FSMs in their strengths and weaknesses, with the difference that they gain the advantage of hierarchical decision-making. hFSMs在优势和劣势上与有限状态机类似，区别在于它们获得了分层决策的优势。

## 6.4.6 UTILITY-BASED DECISION-MAKING

Sometimes, it is not possible to assign static priorities to behaviours, and instead, each behaviour’s relative priority needs to be decided at run time. 有时，无法为行为分配静态优先级，而是需要在运行时决定每个行为的相对优先级。

Utility-based solutions were designed to solve this problem. 基于效用的解决方案旨在解决此问题。

In utility-based solutions, a utility score, i.e., a measure of how useful a particular behaviour would be for the AI to execute, is calculated for each behaviour, every update. 在基于效用的解决方案中，每次更新都会为每个行为计算一个效用分数，即衡量特定行为对 AI 执行有多有用的指标。

The behaviour with the highest score is then selected to be executed. 然后选择得分最高的行为进行执行。

In many ways, utility-based decision-making is very similar to the prioritised behaviour list, except that instead of having static priorities, the behaviours are re-prioritised each update. 从很多方面看，基于效用的决策与优先行为列表非常相似，区别在于不采用静态优先级，而是在每次更新时重新对行为进行优先级排序。

This flexibility to be able to reprioritise the behaviours for a given situation is utility-based decision-making’s biggest strength, but the complexity of making it work is also its biggest weakness. 这种能够针对给定情况重新排序行为的灵活性是基于效用决策最大的优势，但使其工作的复杂性也是其最大的弱点。

Usually, when utility-based decision-making is described in literature, there will be a 2D graph showing how the utility of two different behaviours changes based on a single variable. 通常，在文献中描述基于效用的决策时，会有一个 2D 图表，显示两种不同行为的效用如何随单个变量的变化而变化。

It is easy to look at the graph and see where one behaviour becomes more important than the other, and the AI’s behaviour can be both easily understood and modified using this graph. 查看图表并查看哪种行为比另一种更重要很容易，并且可以使用此图表轻松理解和修改 AI 的行为。

Unfortunately, in order to create an interesting agent, your utility calculations will depend on a large number of variables, not just one, used to calculate the utility of a significant number of behaviours, often using non-linear functions. 不幸的是，为了创建有趣的代理人，你的效用计算将取决于大量变量，而不仅仅是一个，这些变量用于计算大量行为的效用，通常使用非线性函数。

To illustrate how the different behaviours interact, you would need a graph with one additional dimension for each additional variable, something that quickly becomes impossible to illustrate. 为了说明不同行为如何交互，你需要为每个额外变量增加一个维度的图表，这很快就会变得无法说明。

Keeping track of all these interactions is very challenging for any interesting AI system, which is why in practice you will see most utility systems divide their behaviours into classes that occupy distinct utility bands. 跟踪所有这些交互对任何有趣的 AI 系统来说都非常具有挑战性，这就是为什么在实践中你会看到大多数效用系统将其行为划分为占据不同效用带的类别。

This results in sets of a few behaviours in each band (often as few as just two or three), needing to have their utility calculations tuned against each other as the utility scores of all other behaviours are guaranteed to be outside their band. 这导致每个带中只有少数几个行为（通常只有两三个），需要相互调整其效用计算，因为所有其他行为的效用分数保证在它们的带之外。

## 6.4.7 HIERARCHICAL UTILITY-BASED DECISION-MAKING

As with most of the other solutions, it is easy to create a hierarchical version. Utility-based decision-making is no different and allows this approach to gain the strength of hierarchical decision-making. 与其他大多数解决方案一样，创建分层版本很容易。基于效用的决策也不例外，它允许这种方法获得分层决策的优势。

## 6.4.8 PLANNERS

Planners allow the AI to construct plans at run time that match the current situation the AI finds itself in. 规划者允许 AI 在运行时构建与其当前所处情况相匹配的计划。

These plans are constructed by assembling individual actions from a selection of actions that the AI has available to it. 这些计划是通过从 AI 可用的操作选择中组装单个操作来构建的。

The actions come with pre- and post-conditions and the planner uses these conditions to create a string of actions that allows the AI to transform the world in such a way that by the end of the plan, the current world state is transformed into the goal state. 操作带有前置条件和后置条件，规划者使用这些条件创建一系列操作，使 AI 能够以这样的方式转换世界，以使在计划结束时，当前世界状态转换为目标状态。

The most popular planner in games is Goal-Oriented Action Planning, but it should be noted that there are many other planners out there with different pros and cons. 游戏中最流行的规划者是目标导向动作规划，但应该注意的是，还有许多其他规划者，各有优缺点。

The big strength of the planners is that they allow the AI to solve situations that its creator has not thought of in advance. 规划者的最大优势在于它们允许 AI 解决其创建者未事先考虑过的情况。

Assuming that there is a way to solve a situation with the actions available, the AI will be able to generate a plan to do so. 假设有可用操作可以解决某个情况，AI 将能够生成一个计划来做到这一点。

This allows the programmer to focus on what actions an agent can take, which is a smaller problem, than on all the ways in which those actions can be combined. 这使程序员能够专注于代理人可以采取什么操作，这是一个较小的问题，而不是专注于这些操作可以组合的所有方式。

Another strength of planners is the ease of how they can be extended. 规划者的另一个优势是扩展非常容易。

Adding an action to the list of available actions immediately allows the AI to use that action in all situations that apply. 将操作添加到可用操作列表中，会立即允许 AI 在所有适用情况下使用该操作。

Planners also have significant weaknesses. 规划者也有显著的弱点。

The most important one is that it is by far the most CPU-intensive way to come up with a plan. 最重要的是，这远远是制定计划最占用 CPU 的方式。

The architectures discussed previously offload this work to the programmer who creates all the plans available to the AI offline, and at run time, the AI only needs to decide which plan is the best option at any given time. 之前讨论的架构将这项工作卸载给程序员，由程序员离线创建 AI 可用的所有计划，在运行时，AI 只需要决定在任何给定时间哪个计划是最佳选择。

Of course, that puts the onus on the programmer to come up with a plan for all possible scenarios to ensure that an agent always has a reasonable response, and if there are scenarios that the programmer has not considered, then there might be exploits or just bad reactions of the AI in the shipped product. 当然，这让程序员必须为所有可能的场景制定计划，以确保代理人始终有合理的响应，如果程序员没有考虑到某些场景，那么在交付的产品中可能会出现漏洞或 AI 的糟糕反应。

It might sound like a tall task, but as it turns out, for many games, it is not that difficult. 这听起来可能是一项艰巨的任务，但事实证明，对于许多游戏来说，并不那么困难。

In most games, particularly action games, the AI's life expectancy is very short, and they are engaged in a very active constrained activity (usually combat). 在大多数游戏中，尤其是动作游戏，AI 的生命周期非常短，并且它们正在参与非常活跃的受限活动（通常是战斗）。

Commonly, the majority of development time is spent on finding and fixing edge cases, something you would have to do when using a planner too. 通常，大部分开发时间都花在寻找和修复边缘案例上，使用规划者时也必须这样做。

To compound the issue of the overhead for planning, plans in these kinds of environments usually do not last very long, often mere seconds, or even just fractions thereof, after which a new plan needs to be generated, exacerbating the performance problems. 为了加剧规划开销的问题，这类环境中的计划通常不会持续很久，通常只有几秒钟，甚至只有几秒的几分之一，之后需要生成新计划，加剧了性能问题。

Where planners do shine is in situations where the AI can create long-term, complex, and stable plans where optimising its actions is important. 规划者确实发光的地方是 AI 可以创建长期、复杂且稳定的计划，并且优化其操作很重要的情况下。

## 6.4.9 HIERARCHICAL PLANNERS

As with many of the other solutions, planners can be hierarchical. Hierarchical Task Networks is the most well-known version of a hierarchical planner. 与许多其他解决方案一样，规划者可以是分层的。分层任务网络是分层规划者最著名的版本。

Such an approach has a significant benefit compared to non-hierarchical planners in that it is easy to create a system that is only creating a partial plan. 与非分层规划者相比，这种方法有一个显著的优势，即很容易创建一个只生成部分计划的系统。

This gets filled in as needed and can result in significant CPU savings. 这会根据需要填充，并可能带来显著的 CPU 节省。

## 6.5 CONCLUSION

At this point, you might be wondering which architecture is the best as all of them seem to have strengths and weaknesses. 在这一点上，你可能会想知道哪种架构是最好的，因为它们似乎都有优势和劣势。

The short answer is that none of them is the best. They are all good at different things. 简短的回答是，没有一种是最好的。它们各擅长不同的领域。

Understanding these strengths and 理解这些优势和

