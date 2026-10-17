
![Image](img/bull.jpg)The importance of finding tools able to measure the problem

![Image](img/bull.jpg)The importance of models in troubleshooting

![Image](img/bull.jpg)The concept of half split and move

![Image](img/bull.jpg)The concept of technical debt

It’s 2 a.m., the network is down, and the CEO is on the phone asking when it is going to be back up. The overnight job crucial to the business opening in the morning has failed, and the company stands to lose millions of dollars if the network is not fixed in the next hour or so. Almost every network engineer has faced this problem at least once in his career, often involving intense bouts of shouting (and/or screaming) intermixed with panicked attempts to find the root cause and fix it.

And yet troubleshooting is a skill that is hardly ever taught. There are a number of computer science programs that do include classes in troubleshooting, but these tend to be mostly focused on tools, rather than technique, or focused on practical skill application. While this chapter cannot be a complete course in troubleshooting, it will provide a basic overview of troubleshooting, including the problem set and some tools you will find helpful in locating and fixing problems (more) quickly. The basic question this chapter will answer is

**What is the most effective process for finding and fixing problems in a network?**

Each of the following sections will address one part of the answer to this question.

**Note**

In many cases, the points made in this chapter will be exemplified through stories told in the first person; these are true stories of troubleshooting success and failure supplied to help you understand the point being made.

### What Is the Purpose?

Troubleshooting tends to be an exercise in narrowing—starting from a broad and imprecise description of the problem, moving to a more focused description, and finally finding one or more things to change in the network to resolve the problem. As with design, however, it is often easy to narrow too quickly and then to hop around rather than remembering to refocus on the overall purpose of the system if your first attempt at solving the problem does not turn out to be “the” problem.

In the middle of a long, exhausting troubleshooting session, it is easy to think of the system as the network path the application runs over and the application itself. To use an example from electronics, rather than networking:

*One of the pieces of equipment on the flightline was a wind speed indicator. This is fancy name for a really simple device; there was a small “bird” attached to the top of a pole with a tail guiding the bird into facing the wind, and then at the nose of the bird an impeller attached to a Direct Current (DC) motor. The DC motor drove a simple DC voltmeter graduated with wind speeds, and the entire system was calibrated using a resistive bridge in the wind speed indicator box, and another in the wind bird itself. The power from the impeller was passed to the voltmeter, several miles away, through a 12-gauge cable. These cables were particularly troublesome, as they were buried, and had to be spliced using gel-coated connectors, with splices buried in gel-filled casing. This was all before the advent of nitrogen-filled conduit to keep water out*.

*In one particular instance, a splice failed, requiring the cable to be dug up by hand, and the splice opened and repaired. A special team was called in to resplice the cable, but even with the new splice in place, the wind system could not be calibrated to work correctly. The cable team argued the cable had all the right voltage and resistance readings; we argued back that the equipment had been working correctly before the splice failed, and all tested on the bench okay, so the problem must still be in the splice. The argument lasted for days. From the view of the cable team, their “system” was working properly. From the perspective of the weather techs, the system was not, even though the testable components were. Who was right? It all came down to this: What does the “system” consist of, and what does “working properly” mean?*

*Eventually, by the way, the cable splice was fingered as the problem in a capacitive crosstalk test. The splice was redone, and the problem disappeared*.

The purpose is ultimately what the system is supposed to *do*, not just what *you can measure*. It does not matter if the network, or some component of the network, appears to be working fine. What matters is whether or not the system is accomplishing its purpose.

Of course, this means you need to understand what the purpose of the system is. In the broadest view, this means *what the system is supposed to accomplish from a business perspective*. A network can be running just fine from the perspective of the engineers who built it, but if it is not solving a business problem the way the business problem needs to be solved, it is still broken.

On the other hand, it is important to remember business folks do not always understand precisely how the business and the network relate, or they may have unrealistic expectations of what the network is capable of, or what is possible. In these cases, resist the urge to ask, “How high?” when the business says, “Jump!” Rather, cultivate a conversation in which you, the network engineer, have the right to say, “No, this will add too much complexity,” or “The tradeoff here is too high.”

Moving from the business to the network itself, there is a different, but still large, context: the network components.

### What Are the Components?

说“网络由组件构成”就像说“手工玻璃动物园由……玻璃构成”一样——这没什么用。更具体地说，网络的组件是什么？在网络世界中，有

• 处理和转发流量的硬件设备，例如路由器、交换机和有状态数据包过滤器

• 环境因素，例如电力和制冷

• 布线、接口和其他硬件

• 运行在这些设备上的软件（操作系统）

• 提供转发数据包所需信息的软件应用程序；控制平面

• 网络的设计规范以及为了满足*业务需求*而需要运行的规范

• 应用程序对网络提出的要求，网络正在支持这些应用程序

更广泛、更简单的术语集合可能是：需求 + 网络软件 + 协议 + 设备。再说一次，这可能有点显而易见，但在凌晨 2 点火灾猛烈燃烧时，你试图扑灭它们，很容易忘记整个画面。

你能多好地了解这四个系统中的每一个？你能详细到最后一个传输的数据包和每个数据包中的最后一位吗？你能知道每个数据包在网络中的流动，以及任何特定应用程序推送到数据包中的每条信息，或不断变化的完整业务需求集吗？

显然，这些问题的答案是否定的。

当网络中的这四个系统相互作用（还记得第一章中的交互表面吗？）时，它们会形成一个更大的系统，该系统会遭受组合爆炸。Figure 24-1 说明了这一点。

![Image](img/24fig01.jpg)

**Figure 24-1** *Combinatorial Explosion of Systems in a Network*

组合太多，状态也太多，任何一个人都无法全部知道。如何减少信息量，以便合理地理解整个系统的状态，从而能够对其进行故障排除？通过构建系统组件的抽象模型、这些组件之间的交互点，以及最终系统本身的模型。

**这是有效故障排除的第一项技能：构建描述系统的模型集。**

所有模型必然是*不完整*的；模型只能代表整个系统或子系统的某些方面。因此，模型是一把双刃剑：它们呈现了更容易理解的系统版本，但也呈现了必然不完整的系统版本。

### Models and Troubleshooting

没有单一的方法，也没有单一的工具集可以用来构建有效的模型。本节将考虑一些常见的模型类型——*如何*模型和*什么*模型——并讨论如何构建它们。准确模型的 重要性以及在故障排除过程中有效使用模型的能力也在此考虑。

**Note**

这当然有一些有趣的含义。例如，当系统是“黑盒子”时，这意味着你不应该知道系统如何工作，你对系统本身进行故障排除的能力为零，你对黑盒子作为组件的任何更大系统进行故障排除的能力也严重受损。

#### Build *How* Models

*How* 模型是使用问题/解决方案集构建的。事实上，本书的全部内容就是构建 *how* 模型的练习，使用三步流程：

1\. 确定需要解决的问题。

2\. 调查该特定问题的可能解决方案范围。

3\. 理解这种特定实现如何使用特定解决方案解决特定问题。

在这三步之外，一个潜在的第四步是将许多解决方案集成到一个完整系统中，考虑解决方案之间的交互（例如，一个解决方案如何减少或增加另一个解决方案的有效性等）。

*How* 模型当然不只回答一种问题；例如，在考虑 *how* Border Gateway Protocol (`BGP`) 对等体形成时：

1\. `BGP` 如何在两个 `BGP` 扬声器之间管理流量控制、错误控制/纠正和数据编组？

2\. `BGP` 如何在两个 `BGP` 扬声器之间管理对等状态？

3\. 操作员如何配置 `BGP` 以正确地在两个 `BGP` 扬声器之间形成对等关系？

每个都是一个单独的 *how* 问题。许多工程师在为故障排除建立坚实基础时出错的地方在于，他们知道第二和第三个问题的答案，而从未花时间研究第一个。工程往往最终关注的问题是 *我如何完成这个？* 而不是 *这是如何工作的？*，具体来说 *为什么这样工作？* 其结果是一种“试探性”的故障排除风格——将过去问题的少量片段与大量关于如何配置事物使其工作起来的知识结合起来。这通常是一种非常低效的方式，不仅用于设计网络和协议，也用于故障排除。

你需要能够构建所有三种类型的 *how* 模型。有几种有用的方法可以建立你的 *how* 模型储备，包括

• 阅读协议理论和规范，以便理解协议如何以及为何运行（正在解决什么问题以及如何解决）

• 检查协议和网络的设计，以及它们在现实世界中的表现

• 学习基本算法和启发式方法，以及它们旨在解决的问题

本质上，构建 *how* 模型更多是关于*理论*而不是*实践*；这就是为什么工程师经常跳过学习 *how* 模型——这会阻止他们从长远来看提高工程技能。*How* 模型有时最好以图形格式表达，例如通用建模语言（`UML`）草图或流程图。

#### Build *What* Models

*What* 模型与 *how* 模型不同之处在于描述特定网络或应用程序的状态，或在许多网络或应用程序中发现的常见模式。这些类型的模型通常回答诸如

• 这种流量流（信号路径）在系统（例如网络、应用程序等）中的正常路径是什么？

• 这个网络上的正常顶级对话者集是什么？

• 这两个网络路径之间的负载正常分布是什么？

• 两个 `BGP` 扬声器之间的正常启动过程是什么？

唯一真正学习 *what* 的方法就是反复观察和总结。例如，观察大量网络中的顶级对话者，甚至在单一网络中跨越数年，将会给你一个很好的感觉去哪里寻找顶级对话者，以及在*这种情况下*顶级对话者何时不合理。

观察过程中的操纵也很重要；Figure 24-2 说明了这一点。

![Image](img/24fig02.jpg)
