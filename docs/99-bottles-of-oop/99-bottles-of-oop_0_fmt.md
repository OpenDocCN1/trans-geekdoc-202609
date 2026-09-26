
# 99 瓶 OOP 实战

## 1. 重新发现简单

### 1.1 简化代码

#### 1.1.1 难以理解的简洁

- [一致性]
- [重复]
- [命名]

#### 1.1.2 投机性的通用

#### 1.1.3 具体性的抽象

#### 1.1.4 毫无颜色的绿色（测试通过）

### 1.2 评价代码

#### 1.2.1 基于观点的代码评估

#### 1.2.2 基于事实的代码评估

- [源代码行数]
- [圈复杂度]
- [赋值、分支与条件 (ABC) 指标]

#### 1.2.3 比较解决方案

### 1.3 总结

## 2. 测试驱动“毫无颜色的绿色”

### 2.1 理解测试

### 2.2 编写第一个测试

### 2.3 消除重复

### 2.4 容忍重复

### 2.5 遵循计划

### 2.6 暴露职责

### 2.7 选择命名

### 2.8 揭示意图

### 2.9 编写高性价比的测试

### 2.10 避免回声室效应

### 2.11 考虑选项

### 2.12 总结

## 3. 挖掘概念

### 3.1 倾听变化

### 3.2 从开闭原则开始

### 3.3 识别气味

### 3.4 识别最佳切入点

### 3.5 系统化地重构

### 3.6 遵循群集规则

### 3.7 收敛于抽象

#### 3.7.1 关注差异

#### 3.7.2 简化困难问题

#### 3.7.3 为概念命名

#### 3.7.4 进行有方法的转换

#### 3.7.5 渐进式重构

### 3.8 总结

## 4. 练习水平重构

### 4.1 将差异转化为相同性

### 4.2 命名的歧义

### 4.3 从职责导出命名

### 4.4 选择有意义的默认值

### 4.5 寻找稳定的着陆点

### 4.6 遵守里可夫替换原则

### 4.7 迈出更大的步

### 4.8 发现更深层的抽象

### 4.9 依赖抽象

### 4.10 总结

## 5. 分离职责

### 5.1 选择目标代码气味

#### 5.1.1 识别代码中的模式

#### 5.1.2 发现共同特征

#### 5.1.3 列举群集方法的共性

#### 5.1.4 坚持使用消息

### 5.2 提取类

#### 5.2.1 抽象建模

#### 5.2.2 为类命名

#### 5.2.3 提取 `BottleNumber`

#### 5.2.4 移除参数

#### 5.2.5 信任流程

### 5.3 赏析不可变性

### 5.4 假设足够快速

### 5.5 创建瓶数数字（`BottleNumbers`）

### 5.6 识别 Liskov 违背

### 5.7 总结

## 6. 实现开放性

### 6.1 固化数据簇（Data Clumps）

### 6.2 理解条件逻辑

### 6.3 用多态替换条件逻辑

#### 6.3.1 拆解条件逻辑

#### 6.3.2 制造对象

#### 6.3.3 盛行多态态

### 6.4 类型之间的转换

### 6.5 进行简单的更改

### 6.6 守护领域

### 6.7 总结

## 7. 制造智能

### 7.1 对比具体工厂与无耻的绿色

### 7.2 洞察工厂

### 7.3 开启工厂

### 7.4 支持任意类名

### 7.5 分散选择逻辑

### 7.6 自注册候选对象

### 7.7 总结

## 8. 开发编程美学

### 8.1 赏析机械过程

### 8.2 用伪代码明确职责

### 8.3 提取诗句（The Verse）

### 8.4 顺望性思维编码

### 8.5 反转依赖

#### 8.5.1 注入依赖

#### 8.5.2 隔离变体

#### 8.5.3 与反转斗争

### 8.6 遵循迪密特法则（Law of Demeter）

#### 8.6.1 理解该法则

#### 8.6.2 治愈迪密特违背

### 8.7 识别诗句想要什么

### 8.8 将对象创建推向边缘

### 8.9 总结

## 9. 收获设计的收益

### 9.1 选择测试哪些单元

#### 9.1.1 对比单元测试与集成测试

#### 9.1.2 放弃测试

### 9.2 重组测试

#### 9.2.1 收集诗句测试

#### 9.2.2 揭示意图

### 9.3 寻求上下文独立性

#### 9.3.1 检查瓶的职责

#### 9.3.2 使用伪造（Fakes）净化测试

#### 9.3.3 剔除冗余测试

#### 9.3.4 从松耦合中获益

### 9.4 与未来交流

#### 9.4.1 用信号丰富代码

#### 9.4.2 验证角色

#### 9.4.3 消除过时的上下文

### 9.5 总结

## 后记

## 附录 A：初始练习

### 如何获取练习

### 如何完成练习

### 测试套件

## 参考文献

## 谢谢

- 打印书籍（个人使用除外）

## 献辞

**Sandi**

*献给 Amy，感谢她所是与所做的一切；献给 Jasper，他教会了我没有什么东西能比得上一次愉快的散步。*

**Katrina**

*献给 Sander，他的毅力超乎想象。*

**TJ**

*献给那些鼓励过我的人，特别是我的父母和老师。还有我最努力去鼓励的 Graylyn。*

## 前言

事实证明，关于面向对象设计（OOD）你需要了解的一切知识，都可以从 [99 瓶啤酒](https://en.wikipedia.org/wiki/99_Bottles_of_Beer) 这首歌中学习。

嗯，也许不是*所有*，但无疑包含了*许多*事情。

这首歌既易于理解，又充满了隐藏的复杂性，这使其成为挂载 OOD 的完美骨架。歌曲中嵌入的这些如此实用且广泛，以至于过去三年里，它已成为 Sandi Metz [实用面向对象设计课程](http://www.sandimetz.com/courses/) 课程体系的核心部分。

书中的思想反映了 Sandi、Katrina Owen 和 TJ Stankus 之间无数小时的讨论与合作。这些想法经过了数百名学生的实战，并由一系列深思熟虑的共同讲师（从 Katrina 开始）进行了完善。虽然作者们都没有自大地声称完美理解，但所有人都通过教授这首歌学习了许多面向对象设计的知识，并觉得有必要将它们全部写下来。

因此，这本书现在有了第二版。我们希望你发现它既有用又有趣。

### 本书内容

这本书关于如何编写高效益、易于维护且令人愉悦的代码。

第 1 章探索了如何判断代码是否“足够好”。本章使用指标来比较解决 99 瓶问题的几种可能方案。它引入了一种被称为*无颜绿色*（Shameless Green）的解决方案类型，并认为尽管无颜绿色既不聪明也不易更改，但它是解决许多问题的最佳*初始*解决方案。

第 2 章是测试驱动开发（TDD）的入门教程，TDD 用于寻找“无颜绿色”。本章关注决定测试什么，以及创建能够乐于接受底层代码变化的测试。

第 3 章引入了一个新需求（六瓶装），引出了关于在更改代码时如何决定从何处下手的讨论。本章检查了开闭原则，然后探索了代码气味。随后该章节定义了一组简单的*群集规则*（Flocking Rules），这些规则指导代码的逐步重构。

第 4 章继续了这种逐步重构。

第 5 章探索了不可变性。

第 6 章探索了里氏替换原则。

第 7 章探索了对象。

第 8 章探索了工厂。

第 9 章探索了测试。

**Sandi Metz** 是 [Ruby 语言面向对象设计](http://www.poodr.com/) 的作者。她拥有三十年的大型面向对象应用程序开发经验。她曾在 Agile Alliance 技术会议、Craft Conf、Øredev、RailsConf 和 RubyConf 等许多会议上发表过关于编程、面向对象设计和重构的演讲。她信奉简单的代码和直观的解释，并因对 Ruby 社区的贡献荣获了 Ruby 英雄奖。她更倾向于编写运行良好的软件、实用的解决方案以及长途自行车旅行（顺序不限）。你可以在 [sandimetz.com](http://sandimetz.com) 了解更多关于 Sandi 的信息。

## Katrina Owen

Katrina 在 GitHub 的开源团队担任倡导师（Advocate）。Katrina 有十年的经验，主要使用 Go 和 Ruby。她是 [exercism.io](http://exercism.io/) 的创始人，这是一个涵盖 30 多种语言的编程技能开发平台。她曾在 NordicRuby、Mix-IT、Software Craftsmanship North America、OSCON、Bath Ruby 和 RailsConf 等国际会议上进行过关于重构和开源的演讲。她因对 Ruby 社区的贡献荣获了 Ruby 英雄奖。编程时，她关注的是自动化、工作流优化和重构。你可以在 [kytrinyx.com](http://kytrinyx.com/) 了解更多关于 Katrina 的信息。

## TJ Stankus

TJ 在 boldfacet LLC 担任软件开发者，并与 Sandi 共同教授软件设计课程。他在 20 多年前偶然开启了编程生涯。通过拼凑 `WordPerfect` 宏来简化他的校对工作时，他发现自己对编程的热爱不亚于追求过的任何创作活动。他曾从事移动端应用和后端 Web 开发。在 `SMTP` 服务器看起来像是个好主意时，他甚至写过一个。如今，他主要使用 Elixir 和 Ruby。他的主要兴趣不在于特定的编程语言，而在于跨越编程语言和范式的核心设计思想。你可以在 [tj.stank.us](https://tj.stank.us/) 了解更多关于 TJ 的信息。

## 关于翻译者

### Tom Stuart

JavaScript 版本的翻译由 Tom Stuart 完成。Tom 是一位计算机科学家、程序员和技术主管。他曾是 [FutureLearn](https://www.futurelearn.com/) 和 [Econsultancy](https://econsultancy.com/) 的 CTO。他曾在剑桥大学[讲授过优化编译器](http://www.cl.cam.ac.uk/teaching/2006/OptComp/slides/)，并在《卫报》撰写过技术文章。

Tom 是 [计算原理](http://computationbook.com/) 的荣誉作者，该书由 [O’Reilly](http://www.oreilly.com/) 于 2013 年出版。

### Matthew Fonda

Matthew Fonda 就如何思考 PHP 和面向对象提供了深度思考且极具帮助的指导。Matthew 是 eNotes.com 的 CTO，在那里他花了 15 年时间构建一个帮助学生学习的平台。在 eNotes 工作期间，他亲身体会到了构建随时间推于修改的代码库的重要性，并且比以往任何时候都更加确定软件开发中每个问题的答案都是“取决于情况”。Matthew 是 PHP 社区的长期成员，也是 PHP 文档的偶尔贡献者。不在电脑前时，你可以在太平洋西北地区的山里发现他正在滑雪。

### Stockton 兄弟

Dave 和 Dann Stockton 兄弟花费了无数小时思考第一版 PHP 的初始翻译。他们是首次将书籍转换为另一种编程语言的尝试，因此他们承受了人们可以想象的所有痛苦。我们对他们的努力和贡献永表感谢。

书中所展示 PHP 代码由 Katrina 编写，并得到了 Matthew、Dave 和 Dann 的慷慨投入。

## 引言

本书为 “[99 瓶啤酒](https://en.wikipedia.org/wiki/99_Bottles_of_Beer)” 歌曲问题创建了一个简单的解决方案，然后应用一系列重构来改进代码的设计。

就这么说，这个话题听起来如此显而易见，以至于人们可能会合理地怀疑整本书是否可以用几段代码示例所取代。这些重构“端点”的大小仅是这本书的一小部分，读起来也快得多。遗憾的是，它们几乎无法教你任何编程的知识。编写代码是通向下一个稳定端点的*过程*，而不是端点本身。你并不是预先知道答案，而是在寻找答案。

这本书记录了代码每条路径的每一步，因此为整个过程中做出的决策提供了引导性导览。它不仅展示了良好的代码完成后长什么样，还揭示了产生它的思想。它的目标是无一遗漏。它揭开了“制作香肠”背后的面纱。

在进入正文之前，还有最后的注意事项。

接下来的章节将一个通用的、广泛的解决方案应用于特定的狭窄问题。作者们愉快地[规定](https://en.wikipedia.org/wiki/Stipulation) 这样一个事实：你在日常工作中不太可能遇到“99 瓶啤酒”歌曲，而且规模类似的问题最好用简单的方法解决。对于本书而言，“99 瓶啤酒”很方便，因为它既易于理解又出乎意料地复杂，因此是更复杂问题的便利替代品。一旦你理解了这里的解决方案，就能将它们应用到庞大的现实世界中。

此外，书中的代码示例通常遵循公认的风格指南，但偶尔会使用额外的换行。这意味着你可能预期在一行中看到的一些代码实际上被分成了两行。这些预见性的断行是为了阅读方便，而不是对这种风格的认可。

言此而已，进入正文。

## 1. 重新发现简单

当你刚开始编程时，你写的是简单的代码。尽管你那时可能并没有意识到这一点，但这是一种巨大的优势。从那时以后，你学到了新技能，应对了更困难的问题，并产生了日益复杂的解决方案。经验告诉我们，大多数代码终将改变，因此你开始为了预见这一天进行设计。

你曾经为了可理解性而优化代码，现在你关注的是它的可变性。你的代码变得不那么具体，但更加抽象——你为了以后更容易维护，在初期增加了理解的难度。

这就是面向对象设计（OOD）的基本承诺：如果你愿意接受代码在*某些*维度上的复杂度增加，你将在*其他*维度获得复杂度降低的回报。

设计决策不可避免地涉及权衡。要有代价。例如，如果你在许多地方重复了某些代码，“不要重复自己”（DRY）原则要求你将重复部分提取到单一公共方法中，然后用这个新方法替换旧代码。DRY 是一个很棒的主意，但这并不意味着它是免费的。你为提取重复代码所付出的代价是，新方法的调用者不再知道结果，只知道它应该发送的消息。如果你愿意支付这个代价，即你愿意对实际行为一无所知，那么你获得的奖励就是当行为改变时，你只需要在一个地方修改代码。

你是否将一个大类拆分成了许多小类？你现在可以相互独立地重用这些新类，但对于原始案例，它们是如何组合在一起的已不再明显。你是否注入了依赖，而不是硬编码协作类的类名？接收者现在可以自由地依赖新的以及之前未预见的对象，但它必须对这些实际类保持无知。

上面的示例通过提高代码的抽象层次来改变代码。`DRY`（不要重复）代码实际上是在使用行为的地方和定义行为的地方之间插入了一层间接。将一个大类拆分为许多小类会迫使你创建某种新事物来体现这些部分之间的关系。注入依赖则将接收者转变为依赖于抽象角色而非具体类的实体。

这些设计选择每种都有成本，只有当你也能获得一些抵消收益时，支付这些成本才有意义。因此，设计就是关于选择正确的抽象。如果你选择得当，你的代码将具有表现力、易于理解且灵活，每个人都会既喜欢你的代码也喜欢你本人。然而，如果你选错了抽象，你的代码将变得错综、困惑且昂贵，你的编程同僚会讨厌死你。

遗憾的是，抽象是很难的，即使意图良好，也很容易出错。心怀良好的程序员倾向于过度预判抽象，从不完整的信息中过早推断出抽象。早期的抽象往往并不准确，因此它们创造了一个“两陷入为地”的困境：在没有完全理解代码之前，你无法创建正确的抽象，但错误抽象的存在可能会阻止你永远做到这一点。这表明你不应该去追求抽象，相反，你应该抵制它们，直到它们绝对要求必须被创建为止。

这本书是关于寻找正确抽象的。第一章将从剥离复杂性的迷雾开始，定义编写简单代码的含义。

## 1.1 简化代码

你编写的代码应该满足两个经常相互矛盾的目标。它必须保持足够具体以便于理解，同时保持足够抽象以允许更改。

![short_bottle](img/short_bottle_small.png)

想象一个连续体，一端是“最具体”，另一端是“最抽象”。具体端的代码可能被表示为一个包含大量 `if` 语句的单一过程。抽象端的代码可能由许多类组成，每个类都有一个只包含单行代码的方法。

大多数问题的最佳解决方案不在这个连续体的极端，而是在中间某个地方。有一个甜点代表了理解力与可变性之间的完美折中，你作为程序员的任务就是找到它。

本节讨论了解决“99 瓶啤酒”问题的四种不同解决方案。这些解决方案的复杂性不同，从而说明了该连续体上的不同点。

你现在必须做出决定。正如序言中所警告你的那样，从书中学习最好的方法是亲自完成练习。如果你在以自己的方式解决问题之前继续阅读，你的想法会被随后的代码所污染。因此，如果你计划跟着做，现在就去完成 [99 瓶啤酒练习]。完成后，你就可以准备好检查以下四种解决方案了。

### 1.1.1 难以理解的简洁

这是“99 瓶啤酒”歌曲的四种不同解决方案中的第一个。

[列表 1.1: 难以理解的简洁](https://github.com/sandimetz/99bottles_php/blob/2.1.1-initial-variations-10/lib/Bottles.php#L3-L23)

```php
 1 class Bottles {
 2   public function song(): string {
 3     return $this->verses(99, 0);
 4   }
 5 
 6   public function verses(int $hi, int $lo): string {
 7     return implode("\n", array_map([$this, 'verse'], range($hi, $lo)));
 8   }
```



虽然 `method`（方法）和 `function`（函数）这两个术语通常是可以互用的（至少在引用对象的实例方法时），但 `send`（发送）和 `call`（调用）这两个词包含的意思略有不同。对于你的面向对象思维来说，理解这种差异很重要。

将执行行为称为“调用”（calling）方法或函数，暗示了（尽管很微弱）你知道被调用的代码在做什么。相反，将此行为描述为“发送消息”（sending a message）则在发送者的意图和接收者的实现之间留下了更多的心理空间。这种虚拟的间隙鼓励你创建那些刻意忽略实现细节的消息发送者，并促进了发送者与接收者之间的独立性。这种独立性是可维护面向对象代码的核心特征。

因此，虽然这些术语在某些情况下都是适用的，但本书通常倾向于使用“发送消息”而不是“调用方法/函数”，你会在书中看到这种表述方式。

创建一个方法需要识别你想要提取的代码并决定一个方法名。这反过来要求对该概念命名，而命名是一件极其困难的事情。在上面的例子中，情况尤为困难。这段代码不仅包含许多隐藏的概念，而且这些概念混合在一起、混淆，导致它们的个体本质被模糊了。将许多想法合并到一小段代码中很难分离并命名任何单一概念。

当你第一次写一段代码时，你显然知道它是做什么的。因此，在初始开发期间，糟糕命名付出的代价相对较低。然而，代码被阅读的次数远多于编写，其最终成本往往很高且由他人支付。编写代码就像写书；你的努力是为了*其他*读者。虽然寻找好名字是痛苦的，但如果你希望你的工作能够留存并被阅读，这种努力是值得的。代码的清晰度建立在命名之上。

一致性、重复和命名的问题共同作用，使得 Listing 1.1: 难以理解的简洁 中的代码很可能是代价昂贵的。

请注意，上述断言目前是一个没有根据的观点。判断代码最好的方法是比较它的 `value`（价值）与其 `cost`（成本），但遗憾的是很难获得良好的数据。因此，对代码的判断通常被简化为个人观点，而人类并不总是意见一致的。这个问题没有完美的解决方案，但本章稍后的判断代码章节提供了获取关于代码优劣的经验数据的方法。

独立于对代码安排优劣的所有判断之外，代码还承担着完成它*现在*应该做的任务，并且要易于修改以便*以后*做更多事情。虽然很难获得价值和成本的精确数字，但询问以下问题将让你对这段代码的潜在开销产生洞察：

1. `写起来有多困难？`
2. `理解它有多困难？`
3. `修改它的代价有多高？`

过去（“was it”）是记忆，未来（“will it be”）是想象的，但现在（“is it”）是此时真实的。查看一段代码的行为本身就宣布了你希望在*此时此刻*理解它。上述问题 1 和 3 可能与你无关，但问题 2 始终适用。

当代码清晰地反映它正在解决的问题时，它是易于理解的，从而公开暴露了该问题的领域。如果 Listing 1.1: 难以理解的简洁 公开暴露了“99 瓶”领域，扫一眼代码就能回答这些问题：

1. `有多少种歌词体？`
2. `哪些歌词最相似？在哪些方面？`
3. `哪些歌词最不同？在哪些方面？`
4. `确定下一段歌词的规则是什么？`

这些问题反映了问题的核心概念，但没有任何答案在这个解决方案中显而易见。变体的数量、变体之间的差异以及循环算法都令人痛苦地晦涩。这段代码没有反映它的领域，因此你可以推断它写起来很难，且修改将是一个挑战。如果你必须刻画 Listing 1.1: 难以理解的简洁 作者的目标，你可能会认为他们的最高优先级是简洁。简洁可能是机智的灵魂，但在代码中会很快变得乏味。

难以理解的简洁显然不是“99 瓶”问题的最佳解决方案。是时候检查一个更冗长的方案了。

### 1.1.2 推测性的泛化

下一个解决方案在另一个方向上犯了错。它很多方面做得很好，但无法沉溺于不必要的复杂。看看下面的代码：

[Listing 1.2: 推测性的泛化](https://github.com/sandimetz/99bottles_php/blob/2.1.1-initial-variations-20/lib/Bottles.php#L3-L78)

```php
 1 class Bottles {
 2   private $noMore;
 3   private $lastOne;
 4   private $penultimate;
 5   private $default;
 6 
 7   public function __construct() {
 8     $this->noMore = function (object $verse) {
 9       return $verse->number() . " bottles on the wall,\n" .
 10      "more of beer.\n" .
 11      "Go to the store and buy some,\n" .
 12      "99 bottles on the wall.";
 13    };
 14    $this->lastOne = function (object $verse) {
 15       return $verse->number() . " bottle on the wall,\n" .
 16      "1 bottle of beer.\n" .
 17      "Take one down and pass it around,\n" .
 18      "no bottles on the wall.";
 19    };
 20    $this->penultimate = function (object $verse) {
 21       return $verse->number() . " bottles on the wall,\n" .
 22      "2 bottles of beer.\n" .
 23      "Take one down and pass it around,\n" .
 24      ($verse->number() - 1) . " bottles on the wall.";
 25    };
 26    $this->default = function (object $verse) {
 27       return $verse->number() . " bottles on the wall,\n" .
 28      $verse->number() . " bottles of beer.\n" .
 29      "Take one down and pass it around,\n" .
 30      ($verse->number() - 1) . " bottles on the wall.";
 31    };
 32   }
 33 
 34   public function song(): string {
 35     return $this->verses(99, 0);
 36   }
 37 
 38   public function verses(int $finish, int $start): string {
 39     return implode("\n", array_map([$this, 'verse'], range($finish, $start)));
 40   }
 41 
 42   public function verse(int $number): string {
 43     return $this->verseFor($number)->text();
 44   }
 45 
 46   private function verseFor(int $number): object {
 47     switch ($number) {
 48     case 0:  return new Verse($number, $this->noMore);
 49     case 1:  return new Verse($number, $this->lastOne);
 50     case 2:  return new Verse($number, $this->penultimate);
 51     default: return new Verse($number, $this->default);
 52     }
 53   }
 54 }
 55 
 56 class Verse {
 57   protected $number;
 58   private $lyrics;
 59 
 60   public function __construct(int $number, object $lyrics) {
 61     $this->number = $number;
 62     $this->lyrics = $lyrics;
 63   }
 
 64   public function text(): string {
 65     return ($this->lyrics)($this);
 66   }
 
 67   public function number(): string {
 68     return $this->number;
 69   }
 70 }
```

上述代码首先定义了四个闭包（第 8、15、22 和 29 行），并将它们保存为对象属性（`noMore`、`lastOne`、`penultimate` 和 `default`）。注意，每个闭包都接收参数 `verse`，但只有 `default` 实际上引用了它。代码随后定义了 `song` 和 `verses` 方法。接下来是 `verse` 方法，它将当前的诗歌编号传递给 `verseFor`，并将 `text` 发送到结果中（第 47 行）。这行代码负责为歌曲的某节诗歌返回正确的字符串。

`verseFor` 方法中的事情变得更有趣，但在思考该方法之前，请先看第 60 行的 `Verse` 类。`Verse` 实例通过两个参数初始化：`$number` 和 `$lyrics`，并且它们对两个消息做出响应：`number` 和 `text`。`number` 方法简单地返回传递给 `__construct` 的诗歌编号。`text` 方法要复杂得多；它调用了 `lyrics`，并将 `$this` 作为参数传递。

如果你现在回到 `verseFor` 并检查第 52-55 行，你可以看到当创建 `Verse` 实例时，`$number` 参数是一个诗歌编号，而 `$lyrics` 参数是其中一个闭包。`verseFor` 方法会在歌曲的每一节中被调用，因此将创建一百个 `Verse` 实例，每个实例包含一个诗歌编号和一个与编号对应的闭包。

总结一下，向 `Bottles` 实例发送 `verse($number)` 会调用 `verseFor($number)`，它使用 `$number` 的值来选择正确的闭包，并创建并返回一个 `Verse` 实例。然后 `verse` 方法将 `text` 发送给返回的 `Verse`，后者反过来调用闭包并将 `$this` 作为参数传递。这触发了闭包，闭包可能可能并不实际使用传递的参数。无论如何，执行闭包都会返回一个包含歌曲某节诗歌词的字符串。

如果你怀疑这过于复杂，那是可以被原谅的。确实如此。然而，奇怪的是，尽管有这种复杂性，Listing 1.2: 推测性的通用 在回答领域问题方面比 Listing 1.1: 难以理解的简洁 做得好得多：

1. **有多少种诗歌变体？**

   有四种诗歌变体（它们分别从上述第 8、15、22 和 29 行开始）。

2. **哪些节诗最相似？相似之处何？**

   第 3-99 节最相似（事实证明它们都是由 `default` 变体产生的）。

3. **哪些节诗最不同？不同之处何在？**

   第 0、1 和 2 节与 3-99 节明显不同，尽管具体的不同之处并不明显。

4. **决定下一节唱哪节诗的规则是什么？**

   在 `noMore` 闭包深处隐藏了一个硬编码的 "99"，这可能会让人推断出第 99 节在第 0 节之后。

该解决方案对上述三个问题的回答相比 Listing 1.1: 难以理解的简洁 有了很大改进。然而，并非一切完美；它在价值/成本问题上表现依然糟糕：

1. **写起来有多困难？**

   这里的代码比通过测试所需的要多得多。这些不必要的代码花费了时间。

2. **理解起来有多困难？**

   许多层级的嵌套让人很困惑。

3. **修改起来有多困难？**

   间接层的存在暗示了其必要性，但你可能需要花费大量时间来理解。

```php
1 class Bottles {
  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $bottlesAtStart, int $bottlesAtEnd): string {
    return implode("\n", array_map([$this, 'verse'], range($bottlesAtStart, $bottlesAtEnd)));
  }

  public function verse(int $bottles): string {
    return (string)new Round($bottles);
  }
}

class Round {
  public $bottles;

  public function __construct(int $bottles) {
    $this->bottles = $bottles;
  }

  public function __toString(): string {
    return $this->challenge() . $this->response();
  }

  public function challenge(): string {
    return ucfirst($this->bottlesOfBeer()) . ' ' .
      $this->onWall() . ', ' . $this->bottlesOfBeer() . ".\n";
  }

  public function response(): string {
    return $this->goToTheStoreOrTakeOneDown() . ', ' .
      $this->bottlesOfBeer() . ' ' . $this->onWall() . ".\n";
  }

  public function bottlesOfBeer(): string {
    return $this->anglicizedBottleCount() . ' ' .
      $this->pluralizedBottleForm() . ' of ' . $this->beer();
  }

  public function beer(): string {
    return 'beer';
  }

  public function onWall(): string {
    return 'on the wall';
  }

  public function pluralizedBottleForm(): string {
    return $this->lastBeer() ? 'bottle' : 'bottles';
  }

  public function anglicizedBottleCount(): string {
    return $this->allOut() ?
      'no more' : (string)$this->bottles;
  }

  public function goToTheStoreOrTakeOneDown(): string {
    if ($this->allOut()) {
      $this->bottles = 99;
      return $this->buyNewBeer();
    } else {
      $lyrics = $this->drinkBeer();
      $this->bottles--;
      return $lyrics;
    }
  }

  public function buyNewBeer(): string {
    return 'Go to the store and buy some more';
  }

  public function drinkBeer(): string {
    return 'Take ' . $this->itOrOne() . ' down and pass it around';
  }

  public function itOrOne(): string {
    return $this->lastBeer() ? 'it' : 'one';
  }

  public function allOut(): bool {
    return $this->bottles === 0;
  }

  public function lastBeer(): bool {
    return $this->bottles === 1;
  }
}
```

这种解决方案的特点是拥有许多小方法。这通常是一件好事，但在这种情况下，它却变得非常糟糕。看看这个解决方案在领域问题上的表现：

1. *有多少种歌节变体？*

   几乎无法判断。

2. *哪些歌节最相似？在哪些方面？*

   同上。

3. *哪些歌节差异最大？在哪些方面？*

   同上。

4. *确定下一个应该唱哪个歌节的规则是什么？*

   同上。

它在价值/成本问题上的表现也同样糟糕。

1. *编写它有多困难？*

   困难。这显然花费了大量的思考和时间。

2. *理解它有多困难？*

   单个方法很容易理解，但尽管如此，很难对整首歌有一个整体的感觉。各个部分似乎无法组合成一个整体。

3. *修改它的成本有多高？*



虽然修改任何单个方法内部的代码是便宜的，但在许多情况下，一个简单的更改会产生连锁反应，强制许多其他更改。

显而易见，这段代码的作者致力于做正确的事，并且仔细地遵循了*红、绿、重构*（Red, Green, Refactor）的代码编写风格。构成歌曲的各种字符串从未重复——看起来这些字符串在第一次出现重复迹象时就地重构成了独立的方法。

代码是 DRY（不要重复）的，而 DRY 代码*应该*会降低成本。DRY 承诺，如果你将一段代码放入变量中，它应该降低成本。

将 `beer` 方法重命名为 `beverage` 可以很容易地将字符串 "beer" 替换为字符串 "Kool-Aid"，但对提高这段代码在领域问题上的评分没有帮助。这个问题远比方法命名不当要深得多。不仅仅是名称错误，而是方法本身就有问题。这段代码中的许多方法代表了错误的抽象。

识别*正确*抽象的挑战将在后续章节中探讨，但现在，是时候考虑另一种解决方案了。

### 1.1.4 无颜耻的绿色

到目前为止显示的所有解决方案在价值/成本问题上表现都不理想。*不可理喻的简洁*（Incomprehensibly Concise）只关注简洁。*推测性的通用*（Speculatively General）尝试追求扩展性，但带来了不必要的复杂性。*具体抽象*（Concretely Abstract）的核心位置正确，但它无法从泥潭中挣脱。

用这些任何一种方法解决“99 瓶啤酒”问题所需的精力比需要的多，产生的复杂性比需要的多。这些解决方案的成本太高；它们做了太多错误的事，而做的正确的事太少。

*推测性的通用*和*具体抽象*都是为了减少未来的成本而编写的，看到良好的意图遭遇如此惨烈的失败令人深感遗憾。特别遗憾的是，抽象是错误的，因为只要有机会，代码完全愿意揭示出正确的抽象。这里的失败不是因为坏意——而是因为耐心不足。

接下来的示例*确实*是有耐心的，因此它为之前的所有问题提供了一种良药。以下解决方案被称为*无颜耻的绿色*：

[代码 列表 1.4：无颜耻的绿色](https://github.com/sandimetz/99bottles_php/blob/2.1.1-initial-variations-40/lib/Bottles.php#L3-L43)

```php
 1 class Bottles {
 2   public function song(): string {
 3     return $this->verses(99, 0);
 4   }
 5 
 6   public function verses(int $upper, int $lower): string {
 7     return implode(
 8       "\n",
 9       array_map([$this, 'verse'], range($upper, $lower))
10     );
 11   }
 12 
 13   public function verse(int $number): string {
 14     switch ($number) {
 15     case 0:
 16       return
 17         "No more bottles of beer on the wall, " .
 18         "no more bottles of beer.\n" .
 19         "Go to the store and buy some more, " .
 20         "99 bottles of beer on the wall.\n";
 21     case 1:
 22       return
 23         "1 bottle of beer on the wall, " .
 24         "1 bottle of beer.\n" .
 25         "Take it down and pass it around, " .
 26         "no more bottles of beer on the wall.\n";
 27     case 2:
 28       return
 29         "2 bottles of beer on the wall, " .
 30         "2 bottles of beer.\n" .
 31         "Take one down and pass it around, " .
 32         "1 bottle of beer on the wall.\n";
 33     default:
 34       return
 35         $number . " bottles of beer on the wall, " .
 36         $number . " bottles of beer.\n" .
 37         "Take one down and pass it around, " .
 38         ($number - 1) . " bottles of beer on the wall.\n";
 39     }
 40   }
 41 }
```

这段代码最直观可见出的特点是它是非常简单。这里没有任何花机。代码易于理解得令人欣慰。不仅如此，尽管缺乏复杂性，这个解决方案在领域问题上的表现非常出色。

1.  *有多少种诗歌变体？*

    显然，有四个。

2.  *哪些诗歌最相似？在哪些方面相似？*

    3-99 节，只有诗歌编号在变化。

3.  *哪些诗歌最不同？在哪些方面不同？*

    0、1 和 2 与 3-99 不同，尽管弄清楚如何不同需要用肉眼解析字符串。

4.  *确定下一首唱哪首诗的规则是什么？*

    这仍然并不明确。第 0 节包含一个深埋的、硬编码的 99。

这些答案与代码 列表 1.2：推测性的通用中实现的完全相同。然而，*无颜耻的绿色*和*推测性的通用*的区别在于它们在价值/成本问题上的比较方式。*无颜耻的绿色*是一个重大的改进。

1.  *写这个有多难？*

    写起来很容易。

2.  *理解它有多难？*

    它很容易理解。

3.  *修改它的成本有多高？*

    修改会很便宜。尽管诗歌字符串重复了，但如果一首诗发生了变化，很容易保持其他诗同步。

根据这些标准，*无颜耻的绿色*无疑是最好的，但令人遗憾的是，它几乎没有被编写。它虽然易于理解，但缺少了许多你期望的品质。它重复了字符串且包含的抽象很少。大多数程序员都有强烈的冲动去做更多，但有时在这里停止最好。如果你被要求编写 99 瓶啤酒的歌词，那么正确的行动路线并不十分清晰。当你提取重复代码或创建一个方法来命名一段代码时，你增加了间接性。理论上这些抽象使得代码更容易理解和修改，但在实践中它们往往适得其反。

### 1.2 判断代码

你现在有了五种解决该啤酒问题的解决方案：之前列出的四种和你自己写的一种。哪种最好？

你可能对这个问题有看法——这种看法受到了上述内容的影响。然而，不受此影响，你的经验和预期预定了你会以独特的方式评估代码的好坏。你不断地判断代码。编写代码需要选择；你的选择反映了个人化的标准。你意在编写“好”代码，而且如果你认为自己写了“坏”代码，你显然意识到自己这么做了。无论这些标准是隐性的、不可实现的还是没有帮助的，你已经对代码有了规则。

虽然拥有*任何*标准都是一种优点，但如果标准是明确且可量化的，实现标准的概率就会增加。回答“什么是好代码？”这个问题需要以具体可操作的方式定义好。

这比想象的要困难。

#### 1.2.1 基于观点评估代码

你可能会认为，到目前应该存在一个公认的良好代码定义，可以明确地指导我们的编程行为。不幸的现实是不仅存在多种定义，而且这些定义通常描述代码完成后的样子，而没有提供如何实现目标的具体指导。

正如“每个人都在抱怨天气，但没有人采取行动，”^(\[4\])，每个人对良好代码看起来都有意见，但这些意见通常并不告诉我们要采取什么行动来创建它。这里有几个清洁代码的定义。注意，它们同样可以描述艺术或葡萄酒，而非软件。

> 我喜欢我的代码优雅且高效。
>
> —— Bjarne Stroustrup
>
> C++ 发明者

> 清洁的代码是……充满锐利的抽象……
>
> —— Grady Booch
>
> [面向应用对象分析与设计](http://www.amazon.com/Object-Oriented-Analysis-Design-Applications-3rd/dp/020189551X) 作者

> 整洁的代码是由在乎的人编写的。
>
> — Michael Feathers
>
> [有效维护遗留代码](http://www.amazon.com/Working-Effectively-Legacy-Michael-Feathers/dp/0131177052) 的作者

你自己的定义可能也遵循类似的思路。任何代码堆都可以运行（`work`）；但良好的代码不仅能运行（`works`），而且简单、易于理解、具有表现力且易于更改。

这些定义的缺陷在于，尽管它们准确地描述了良好的代码在写完成后是什么，但它们对于实现这种状态没有帮助，并且在多个竞争性的解决方案之间做出选择时提供的指导很少。它们用于描述良好代码的特质是定性的，而非定量的。

“优雅”意味着什么？什么让抽象变得“干练”？尽管这些定义不可否认是正确的，但没有哪一个可以通过可衡量的方式来精确定义。这种精确性的缺乏意味着，意良好的程序员可能持有相同的高标准，但会在相对优劣上产生巨大的分歧。因此，我们对代码的争论是徒劳的。

由于形式随功能，良好的代码也可以被简单地（并在某种程度上循环地）定义为：以最低成本提供最高价值的代码。我们对优雅、表现力和简单性的感知是我们在阅读和修改代码时经验的产物。易于理解且易于扩展的代码自然地让人感到简单且优雅。

如果你能够识别并衡量这些特质，你就可以勤勉且刻意地追求它们。因此，尽管你对代码的意见很重要，但事实将让你获益良多。

#### 1.2.2 基于事实评估代码

“指标”（`metric`）是对代码某些质量的衡量。显然，指标是由人创建的，因此有人可能会认为它们仅仅表达了某个人的观点。然而，这种断言极大地低估了它们的价值。升华为指标的衡量标准有着经受住时间考验的研究支持。它们多年来一直被许多人审查过。你可以将指标视为关于代码质量的“众包”意见。

如果你将相同的指标应用于两段不同的源代码，你就可以通过比较结果数字来对这些代码进行比较（至少在指标所衡量的方面）。虽然你可能对某个特定指标的前提持不同意见，并坚持它所衡量的东西没有用，但数学规则要求所有人承认，指标产生的数字是事实。

如果有一个公认的事实来比较代码将极其方便。在寻找这些事实的过程中，本节检查了三种不同的指标：`源代码行数`（Source Lines of Code）、`圈复杂度`（Cyclomatic Complexity）和 `ABC`。

##### 源代码行数

在古代，对开发应用程序成本的可重复、可靠信息的渴望导致了简单被称为`源代码行数`（Source Lines of Code，`[SLOC](http://en.wikipedia.org/wiki/Source_lines_of_code)`，有时简写为 `LOC`）的指标。这个数字一直被用于预测开发软件所需的总工作量，衡量编写代码人员的生产力，并预测维护成本。

该指标的优点是容易获取和复制，但存在许多缺陷。

使用 `SLOC` 预测新项目所需的开发工作量，是通过统计已知总工作量的`现有`项目的 `SLOC` 来完成的：判断这些现有项目中哪一个与新项目最相似，然后运行成本估算模型进行预测。如果负责估算的人对新项目最像哪些现有项目判断是正确的，那么这个预测可能是准确的。

通过通过代码行数来衡量程序员的生产力，假设所有程序员编写的代码效率相同。然而，新手程序员通常比比有经验的程序员要啰嗦得多。尽管新手编写了更多代码却只产生了更少的功能，但根据这一指标，他们看起来生产力更高。

虽然维护成本与应用程序的大小有关，但代码组织的方式也很重要。维护一个设计良好的应用程序比维护一堆“面条代码”（spaghetti-code）便宜得多。

`SLOC` 数字反映了代码量，虽然它对某些用途有用，但仅知道 `SLOC` 还不足以预测代码质量。

##### 圈复杂度

1976 年，Thomas J. McCabe, Sr. 发表了[复杂度衡量方法](http://www.literateprogramming.com/mccabe.pdf)，他在文中断称：

> 需要的是一种数学技术，能够为模块化提供定量依据，并允许我们识别出难以测试的软件模块。

用于识别难以维护代码的“数学技术”——[圈复杂度](http://www.literateprogramming.com/mccabe.pdf) 指标，这是一种计算源代码体中执行路径数量的算法。将这种算法想象成一台小机器，它思考着你的代码，然后映射出通过每个分支每种组合的所有可能路线。一个具有许多嵌套条件的方法得分会很高，而一个没有条件的方法得分为 0。

圈复杂度既不预测应用程序的开发时间，也不衡量程序员的生产力。它对识别难以维护代码的目标直接指向代码质量。

圈复杂度可以以几种方式使用。首先，你可以用它来比较代码。如果你有两个方法的变体，你可以根据它们的圈复杂度在它们之间进行选择。得分越低越好，因此此类，得分最低的代码是最好的。

其次，你可以用它来限制整体复杂度。你可以为你愿意接受的分数高度设定标准，并在允许代码超过此最大值之前获得明确的豁免。

最后，你可以用它来确定你是否编写了足够的测试。圈复杂度告诉你覆盖代码中所有逻辑所需的最小测试次数。如果你的测试次数少于圈复杂度建议的次数，你就没有完全的测试。

圈复杂度听起来很棒，也能看出它可能有用，但它通过一个狭窄的视角观察代码世界。

##### 分配、分支与条件 (ABC) 指标

圈复杂性的问题在于它没有考虑到所有因素。代码不仅仅是评估条件；它还给变量赋值并发送消息。这些因素会累积，随着你做的这些事情越来越多， 你的代码会变得越来越难以理解。

1997 年，在圈复杂度公布二十一年后，Jerry Fitzpatrick 发表了[将 ABC 指标应用于 C、C++ 和 Java](http://www.softwarerenovation.com/ABCMetric.pdf)，他在文中描述了一种不仅考虑条件的指标。他的 `ABC` 代表分配、分支和条件，其中：

*   `分配`（Assignments）是变量赋值的计数。
*   `分支`（Branches）计算不是 if 语句的分支（正如人们可能推出的那样），而是控制分支，意味着函数调用或消息发送。
*   `条件`（Conditions）计算条件逻辑。

Fitzpatrick 将 `ABC` 指标描述为一种大小的衡量标准，仿佛 `ABC` 是 `SLOC` 的更高级版本。这是他提出的指标，因此他当然有权定义它代表了什么，但如果你将 `ABC` 分数看作反映认知大小而非物理大小，那么你不会出错的。高 `ABC` 值表示代码占据了大量的心理空间。从这个意义上说，`ABC` 是复杂性的衡量标准。高度复杂的代码难以理解和修改，因此 `ABC` 分数是代码质量的辅助指标。

PHP 有许多可用的静态分析工具（例如 [phploc](https://github.com/sebastianbergmann/phploc)），尽管流行的工具中没有哪一个是计算 `ABC` 分数的。这一领域在不断演变，因此当你阅读此书时，值得检查是否有新的功能和工具。

`ABC` 分数提供了一个独立的视角，可能会挑战你对复杂性和设计的观点。高分意味着代码将难以测试且维护成本高昂。如果你认为你的代码是简单的，但 `ABC` 分数却不如此，那么你应该重新考虑。

指标是有可能错误的，但人类的观点也并不更精确。定期检查指标会让你保持谦逊并改进你的代码。

#### 1.2.3 解决方案对比

现在你已经对代码指标有了些了解，是时候思考本章所示的代码示例之间是如何比较的了。

由于所有解决方案对于 `song` 和 `verses` 的实现几乎完全相同，因此可以忽略它们，将计数集中在定义 `verse` 必需的代码上。

下表显示了每个解决方案的总代码行数（`SLOC`）以及赋值、分支和条件判断的粗略计数以及生成的 `ABC` 分数。

表 1.1: 指标

| 解决方案 | SLOC | 赋值 | 分支 | 条件判断 | ABC |
| --- | --- | --- | --- | --- | --- |
| 示例 1.1: 晦不可喻的简洁 | `26` | `0` | `0` | `18` | `18` |
| 示例 1.2: 推测性的通用 | `94` | `6` | `10` | `4` | `12` |
| 示例 1.3: 具体的抽象 | `93` | `4` | `20` | `10` | `23` |
| 示例 1.4: 无颜耻的绿色 | `43` | `0` | `0` | `4` | `4` |

这是上述 `SLOC` 和 `ABC` 分数的图表。

![metrics](img/c1_examples_metrics_php.png)

图 1.1: 指标图

尽管 `SLOC` 与 `ABC` 分数没有直接关系，但两者都被视为大小的衡量标准，且它们似乎大致相关。从 `SLOC` 来说，较大的解决方案在很大程度上其 `ABC` 分数也较大。*Shameless Green* 是显著的例外——它的 `SLOC` 仅位次第二，但其 `ABC` 分数明显最低。

*Incomprehensibly Concise* 和 *Concretely Abstract* 的有趣之处在于，它们都具有特征性的复杂代码，但处于不同的维度上。*Incomprehensibly Concise* 的行数最少，但条件判断最多。它成功地将大量的复杂性压缩到了极少数行中。而在 *Concretely Abstract* 中，相反，它将大量的复杂性压缩到了极少数行中，但条件判断最多（注：此处原文重复，已按要求翻译）。其有趣之处在于它们都具有特征性的复杂代码，但处于不同的维度上。



*Speculatively General* 优于 *Concretely Abstract* 在 `SLOC` 分数上。*Shameless Green* 在所有计数上都表现优异。*Incomprehensibly Concise* 和 *Shameless Green* 的相似之处在于，它们在方法上是相似的。尽管如此，如果你比较它们的 `SLOC` 和条件判断数量，你会发现它们截然不同。*Incomprehensibly Concise* 和 *Shameless Green* 在 `ABC` 分数上截然不同。*Incomprehensibly Concise* 和 *Shameless Green* 在 `SLOC` 分数上截然不同。

## 1.3 总结

随着程序员的成长，他们变得能够解决问题，并对复杂性感到舒适。本章研究了“99 瓶啤酒”的四种解决方案，并认为 Shameless Green 是最好的。它使用了测试来驱动理解，而不是让人们相信复杂性是不可避免的。Shameless Green 解决方案由意图清晰、运行良好的软件组成，是编写简单代码以通过一系列预设测试的结果。编写 Shameless Green 是快速的，且生成的代码可能是“足够好的”。然而，如果永远不改变，最有效的策略是部署这些代码并离开。

挑战出现在变更请求到来时。在不改变时足够好的代码在发生变化时可能并不足够好。第 3 章将引入这样的变更，在该章中你将改进代码。在继续之前，是时候回一步，学习如何测试驱动 Shameless Green。

## 2 测试驱动 Shameless Green

前一章研究了“99 瓶啤酒”的四种解决方案，并断定名为 Shameless Green 的是最好的。Shameless Green 解决方案由意图清晰、运行良好的软件组成，是编写简单代码以通过一系列预设测试的结果。

第 1 章代码的来源是显而易见的，但测试并没有解释。现在是时候回头，研究如何创建驱动 Shameless Green 的测试。

### 2.1 理解测试

一代以前，少数极限编程（XP）实践者开始使用他们称为“测试先行开发”的技术编写自动化测试。他们的想法如此成功，以至于自动化测试已成为常态，而且这些测试通常在编写代码之前编写。

在编写代码之前编写测试的做法被称为测试驱动开发（TDD）。简单来说，TDD 的工作如下：

1. **编写测试**。

由于代码尚不存在，此测试会失败。测试运行器通常用红色显示失败的测试。

2. **使其运行**。

编写代码使测试通过。测试运行器常用绿色显示通过的测试。

3. **使其正确**。

每当你回到绿色状态，你就可以将代码重构为更好的形状，只要测试继续通过，你就确信它是正确的。

在《测试驱动开发实例》中，Kent Beck 将其描述为 `红/绿/重构` 循环，并称之为“TDD 格言”。

测试以及优先测试的思想已经赢得了程序员们的心。然而，致力于编写测试并不意味着这件事情变得容易。TDD 提出了一个无休止的挑战。你必须不断决定下一个写哪项测试、如何安排代码使测试通过，以及在测试通过后进行多少程度的重构。每一个决策都需要判断，并产生后果。

如果你的 TDD 判断力尚未完全成熟，那么暂时采用大师的判断是合理的。这里有一条极佳的指导原则：

> 快速变绿可以原谅一切罪恶。
>
> — Kent Beck

#### 测试驱动开发实例

绿色意味着安全。绿色表示，至少从现有测试来看，你已经理解了问题。绿色是你背后的坚盾，让你能够信心地向前迈。快速实现绿色会简化后续的所有工作。

本章说明了如何增量地创建测试，然后使用这些测试来驱动代码开发。示例严格地遵循了 `红/绿/重构` 循环，但做法相当保守。由于初始目标更多是关于变绿而不是编写完美代码，因此重构步骤有时会消除重复，有时则会保留重复。

计划是创建能够彻底描述“99 瓶酒”问题的测试，然后用被称为 `Shameless Green`（无耻绿）的来实现解决问题。无耻绿方案追求最大的可理解性，但通常不关心可变性。无耻绿并不是否定可变性，它只是意识到快速变绿通常与编写完美可变的代码相冲突。本章侧重于创建测试并编写简单的代码来通过测试。未来的章节将重构生成的代码以改进设计。

### 2.2 编写第一个测试

第一个测试通常最难编写。此时，你对打算做的事情了解最少。你的问题是一个巨大的、模糊且无形状的团块，想要伸进去切出一块是非常具有挑战性的。选择良好的起点非常重要，因为你的起点决定了你之后将如何进行，并最终决定了你的终点。因此，第一个测试似乎充满了危险。

尽管其意义重大，但你在这里所做的选择几乎并不重要。在开始阶段，你对问题有一些想法，但实际上了解很少。你的想法可能是正确的，但也同样可能事实会证明它们是错误的。在编写一些测试之前，你无法确定什么是正确的，而在那时，你可能会发现最佳行动方案是丢弃一切并重新开始。因此，你某些测试的可能很可能为了证明它们代表了坏主意。学习哪些想法行不通是一种进步，无论这在当时有多令人失望。

所以，虽然在编写第一个测试之前考虑问题并勾勒整体计划*确实*是重要的，但不要过度思考。找一个起点并开始吧，坚信随着你不断进行，迷雾会散去。

如果你为“99 瓶酒”勾画一个公共应用程序接口（API），它可能像这样：

* `verse($n)`：返回 `n` 瓶酒的歌词。
* `verse($a, $b)`：返回从 `a` 到 `b` 瓶酒的歌词。
* `all()`：返回所有 99 瓶酒的歌词。

测试可能像这样：

```php
public function test_first_bottle() {
    $expected = "99 bottles of beer on the wall, 99 bottles of beer\nTake down and pass around, 98 bottles of beer on the wall\n";
    $this->assertEquals($expected, (new Bottles())->verse(99));
}
```

[Listing 2.4: 第 99 节代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-60/lib/Bottles.php#L3-L12)

```php
1 class Bottles {
2   public function verse(): string {
3     return
4       "99 bottles of beer on the wall, " .
5       "99 bottles of beer.\n" .
6       "Take one down and pass it around, "
7       "98 bottles of beer on the wall.\n";
8   }
9 }
```

尽管这段代码通过了测试，但它显然没有解决整个问题。事实上，编写第二个测试将会破坏它。虽然编写一段显然是临时且过渡性的代码似乎可能毫无意义，但这正是 TDD（测试驱动开发）的精髓所在。

作为测试编写者，你清楚 `verse` 方法最终必须考虑其参数的值，但作为代码编写者，你必须在不知道这一事实的情况下行动。在进行 TDD 时，你需要在两个帽子之间切换。当你戴着“编写测试”的帽子时，你要关注大局，并根据整体计划向前推进。当你戴着“编写代码”的帽子时，你要假装自己除了对当前测试所指定的限制之外一无所知。因此，尽管每个单独的测试都是正确的，但在所有测试完成之前，代码是不完整的。

### 2.3 去重

既然第一个测试已经通过了，你必须决定下一个测试什么。接下来的测试应该执行最简单、最实用的操作，证明你现有的代码是错误的。虽然由于可能性似乎是无限的，构思第一个测试可能很困难，但接下来的测试通常更容易，因为它是相对于第一个测试进行检查的。

诗歌从第 99 节到第 3 节几乎相同——它们唯一的区别在于每节中的数字发生了变化。上面的测试已经检查了该范围的高端，因此，现在测试低端是有意义的。

针对第 3 节的以下测试暴露了当前 `verse` 方法是不够的：

[Listing 2.5: 第 3 节测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-70/test/BottlesTest.php#L15-L22)

```php
1 public function test_another_verse() {
2   $expected =
3     "3 bottles of beer on the wall, " .
4     "3 bottles of beer.\n" .
5     "Take one down and pass it around, " .
6     "2 bottles of beer on the wall.\n";
7   $this->assertEquals($expected, (new Bottles())->verse(3));
8 }
```

TDD 要求你通过编写简单的代码来通过测试。然而，大多数编程问题都有许多解决方案，而且并不总是清楚哪一个是最简单的。例如，以下代码通过重命名输入参数并添加一个检查 `$number` 值并返回正确字符串的条件判断，通过了当前的测试：

[Listing 2.6: 条件判断](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-80/lib/Bottles.php#L4-L18)

```php
1 public function verse(int $number): string {
2   if ($number === 99) {
3     return
4       "99 bottles of beer on the wall, " .
5       "99 bottles of beer.\n" .
6       "Take one down and pass it around, " .
7       "98 bottles of beer on the wall.\n";
8   } else {
9     return
10      "3 bottles of beer on the wall, " .
11      "3 bottles of beer.\n" .
12      "Take one down and pass it around, " .
13      "2 bottles of beer on the wall.\n";
14  }
15 }
```

乍看之下，这段代码似乎实现了简单性的极致。它只能产生第 99 节和第 3 节的歌词，这正是通过测试所绝对需要的。

但请考虑，它现在包含了一个原本不存在的条件判断。这可能会让你想起第 1 章中的圈复杂度。这个条件判断为代码增加了一条新的执行路径，而额外的执行路径增加了复杂度。这段代码的简单在于它能做的不多，但它用一种过度复杂的方式完成了那件事。问题部分原因在于，尽管 `if` 语句根据 `$number` 进行切换，但真、假的分支包含许多不随 `$number` 变化的内容。分支的区别在于一个说是 99/98，另一个说是 3/2，但对于所有其他歌词来说它们是相同的。这段代码将变化的事与不变的事混淆在了一起。如果只提取出变化的部分，代码看起来像这样：

[Listing 2.7: 条件判断](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-90/lib/Bottles.php#L4-L16)

```php
1 public function verse(int $number): string {
2   if ($number === 99) {
3     $n = 99;
4   } else {
5     $n = 3;
6   }
7 
8   return
9     $n . " bottles of beer on the wall, " .
10    $n . " bottles of beer.\n" .
11    "Take one down and pass it around, " .
12    ($n-1) . " bottles of beer on the wall.\n";
13 }
```



```
class Bottles {
  public function verse(): string {
    return
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, "
      "98 bottles of beer on the wall.\n";
  }
}
```

尽管这段代码通过了测试，但它显然没有解决整个问题。事实上，编写第二个测试将会破坏它。虽然编写一段显然是临时且过渡性的代码似乎可能毫无意义，但这正是 `TDD`（测试驱动开发）的精髓所在。

作为测试编写者，你清楚 `verse` 方法最终必须考虑其参数的值，但作为代码编写者，你必须在不知道这一事实的情况下行动。在进行 `TDD` 时，你需要在两个帽子之间切换。当你戴着“编写测试”的帽子时，你要关注全局，并根据整体计划向前推进。当你戴着“编写代码”的帽子时，你要假装自己除了对当前测试所指定的限制之外一无所知。因此，尽管每个单独的测试都是正确的，但在所有测试完成之前，代码是不完整的。

## 2.3. 去重

现在第一个测试已经通过了，你必须决定下一个测试什么。接下来的测试应该执行最简单、最实用的操作，证明你现有的代码是错误的。虽然由于可能性似乎是无限的，构思第一个测试可能很困难，但接下来的测试通常更容易，因为它是相对于第一个测试进行检查的。

诗歌从第 99 节到第 3 节几乎相同——它们唯一的区别在于每节中的数字发生了变化。上面的测试已经检查了该范围的高端，因此，现在测试低端是有意义的。

针对第 3 节的以下测试暴露了当前 `verse` 方法是不够的：

[Listing 2.5: 第 3 节测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-70/test/BottlesTest.php#L15-L22)

```
public function test_another_verse() {
  $expected =
    "3 bottles of beer on the wall, " .
    "3 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "2 bottles of beer on the wall.\n";
  $this->assertEquals($expected, (new Bottles())->verse(3));
}
```

`TDD` 要求你通过编写简单的代码来通过测试。然而，大多数编程问题都有许多解决方案，而且并不总是清楚哪一个是最简单的。例如，以下代码通过重命名输入参数并添加一个检查 `$number` 值并返回正确字符串的条件判断，通过了当前的测试：

[Listing 2.6: 条件判断](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-80/lib/Bottles.php#L4-L18)

```
public function verse(int $number): string {
  if ($number === 99) {
    return
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n";
  } else {
    return
      "3 bottles of beer on the wall, " .
      "3 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "2 bottles of beer on the wall.\n";
  }
}
```

乍看之下，这段代码似乎实现了简单性的极致。它只能产生第 99 节和第 3 节的歌词，这正是通过测试所绝对需要的。

但请考虑，它现在包含了一个原本不存在的条件判断。这可能会让你想起第 1 章中的圈圈复杂度。这个条件判断为代码增加了一条新的执行路径，而额外的执行路径增加了复杂度。这段代码的简单在于它能做的不多，但它用一种过度复杂的方式完成了那件事。问题部分原因在于，尽管 `if` 语句根据 `$number` 进行切换，但真、假的分支包含许多不随 `$number` 变化的内容。分支的区别在于一个说是 99/98，另一个说是 3/2，但对于所有其他歌词来说它们是相同的。这段代码将变化的事与不变的事混淆在了一起。如果只提取出变化的部分，代码看起来像这样：

*(注：由于你提供的文本在 Listing 2.7 处意外中断了，我将严格基于你提供的文本进行翻译。)*

如前所述，指标并非一切，但它们确实是很有用的参考。为了希望数据能帮助回答这个问题，下表显示了各种变体的源代码行数（`SLOC`）、圈复杂度（Cyclomatic Complexity）和 `ABC` 指标，这些是粗略用纸笔计算出的。

## 表 2.1：第 97 和第 3 节测试后的代码变体指标

| 方案 | SLOC | 圈复杂度 | ABC |
| --- | --- | --- | --- |
| Listing 2.6: 条件分支 | `15` | `2` | `2.0` |
| Listing 2.7: 稀疏条件 | `13` | `2` | `2.8` |
| Listing 2.8: 通用诗节 | `7` | `1` | `0` |

如你所见，随着示例的推进，代码变得更短了，圈复杂度分数也有提高。相反，`ABC` 分数在变好之前变得更差了。当然，你必须对指标持保留态度，但在这里，它们清晰地投票支持：像 Listing 2.8: 通用诗节 那样，用抽象来取代重复。

下一节将检查一个几乎相同的情况，在这种情况下，如何处理重复的选择并不那么显而易见。

### 2.4. 容忍重复

第 2、1 和 0 节仍然必须经过测试，且每一节都是独特的。既然已经确了按照出现顺序测试诗节的模式，那么接下来测试第 2 节是有逻辑的。

第 2 节与之前的第 97 节有一个微小不同。之前所有诗节的最后一个短语指的是墙上的“*n* 瓶（bottles）”，因此“bottles”一词是复数。但在第 2 节中，最后一个短语读作“1 瓶（bottle）”。因此，在对第 2 节的后续测试第 6 行中，“bottle”一词是单数而非复数。

[Listing 2.9: 第 2 节测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-110/test/BottlesTest.php#L24-L31)

```
public function test_verse_2() {
  $expected =
    "2 bottles of beer on the wall, " .
    "2 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "1 bottle of beer on the wall.\n";
  $this->assertEquals($expected, (new Bottles())->verse(2));
}
```

运行该测试会产生以下失败：

```
-Take one down and pass it around, 1 bottle of beer on the wall.
+Take one down and pass it around, 1 bottles of beer on the wall.
```

这个失败是完美的；测试预期的是 `1 bottle`，但得到的是 `1 bottles`。

与第 3 节的测试一样，有两种根本上不同的方法可以通过此测试。你可以在现有代码*周围*添加一个新的条件判断，或者在*内部*以某种方式使用 `$number` 的值。

下一个示例通过将代码封装在一个新的条件中说明了第一种可能性：

[Listing 2.10: 生硬条件](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-120/lib/Bottles.php#L4-L18)

```
public function verse(int $number): string {
  if ($number === 2) {
    return
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n";
  } else {
    return
      $number . " bottles of beer on the wall, " .
      $number . " bottles of beer.\n" .
      "Take one down and pass it around, " .
      ($number-1) . " bottles of beer on the wall.\n";
  }
}
```

相比之下，下面的替代方案将逻辑嵌入到现有的诗节字符串中：

[Listing 2.11: 嵌入逻辑的条件](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-130/lib/Bottles.php#L4-L11)

```
public function verse(int $number): string {
  return
    $number . " bottles of beer on the wall, " .
    $number . " bottles of beer.\n" .
    "Take one down and pass it around, " .
    ($number-1) . "bottle" . ($number-1 === 1 ? '' : 's') .
      " of beer on the wall.\n";
}
```

乍看之下，这两个解决方案看起来与之前探索的替代方案非常相似。Listing 2.10: 生硬条件 将代码封装在一个新的条件中；而 Listing 2.11: 嵌入逻辑的条件 则修改了现有的诗节字符串。虽然这两个解决方案看起来很像之前第 3 节的方案，但生硬条件 是在代码周围包裹了一个新条件，而嵌入逻辑的条件 是调整了诗节字符串，类似于 Listing 2.8: 通用诗节。

第 3 节的最佳选择是由指标引导的，这在这里同样适用。下表显示了新示例的指标：

## 表 2.2：第 2 节测试后的代码变体指标

| 方案 | SLOC | 圈复杂度 | ABC |
| --- | --- | --- | --- |
| Listing 2.10: 生硬条件 | `15` | `2` | `2` |
| Listing 2.11: 嵌入逻辑的条件 | `8` | `2` | `2` |

生硬条件 的长度是嵌入逻辑的条件 的两倍。嵌入逻辑的条件 都包含了条件判断，因此它们的圈复杂度是相同的，`ABC` 分数也是相同的。唯一的区别在于，嵌入逻辑的条件 更短。通常越短越好，但遗憾情况下并非如此。

正如前一节所述，随着测试变得具体，代码应该变得通用。代码通过变得更抽象来变得通用。使代码通用的某种方法是 `DRY`（消除重复），即将重复的代码提取到单个方法中并给方法命名，然后通过这个新名称引用代码。提取代码消除了重复，从而减少了整体尺寸。

在嵌入逻辑的条件中，代码确实变短了。人们希望这是因为代码变得更抽象了，但遗憾并非。观察新的条件（为了方便重复）：

```
($number-1) . "bottle" . ($number-1 === 1 ? '' : 's') .
```

注意，即使这里存在抽象，它也完全没有被命名。如果强制命名，你可能会将底层概念称为“复数化”，断言新的条件通过在 `$number-1` 不等于 1 时在字符串“bottle” 之后添加“s”来处理复数化。

如果复数化对于“99 瓶”是一个有意义的抽象，也许我们创建一个 `pluralize` 方法，如下：

```
public function verse($number) {
    // ...
    ($number-1) . $this->pluralize($number)  . " of beer on the wall.\n";
    // ...
}

public function pluralize($number) {
    return ($number-1) === 1 ? 'bottles' : 'bottle';
}
```

遗憾的是，上面的代码只会混淆问题。复数化概念是一个红鲱鱼（干扰项）。这种需求突然出现，所以它看起来像是一个重要的、有意义的、测试驱动的想法，但仅仅是因为你正在处理不完整的信息。

查看 Listing 2.11: 嵌入逻辑的条件，并统计“bottle”一词出现的次数，无论它是单数形式还是复数形式。“bottle”多次出现这一事实表明，存在一个尚未发掘的底层概念。在歌词的领域内，“bottle/bottles”代表了某些重要的东西，而那个东西就是`不是`复数化。这些词都有共同点，在复数逻辑后面隐藏一个单次出现会掩盖这种共性。让其中一个看起来与不同，最终会让你更难观察到它们是如何相同的。

像 `pluralize` 方法这样的代码通常是程序员将 `DRY` 原则推向极端时写的，仿佛他们对重复过敏一样。`DRY` 虽然很重要，但如果应用得太早且用力过猛，其弊可能大于利。当面对这种情况时，请问自己这些问题：

- `我正在考虑的更改会让代码变得更难理解吗？`

  当抽象是正确的，代码就是易于理解的。对任何让水浑浊的更改保持警惕；这表明你对问题的理解不足。

- `现在什么都不做的未来成本是什么？`

  某些更改无论你现在进行还是推迟到以后进行，成本都是相同的。如果它不会增加你的成本，就推迟更改。被迫做出更改的那一天可能永远不会到来，或者时间可能会提供关于更改应该是什么样的更好的信息。无论何种情况，等待都能为你节省资金。

- `未来何时到来，或者我多久多久能获得更多信息？`

  如果你正在编写测试套件中间，更好的信息就在下一个测试用例中。在每个测试结束时挤掉所有的重复并不是必要的。在几个测试之间容忍一些重复是完全合理的，希望通过编写若干个略微重复的示例来揭示正确的抽象。容忍重复总比预判错误的抽象要好。

Listing 2.10: 裸露的条件 和 Listing 2.11: 嵌入逻辑的条件 具有相同的 `ABC` 分数和圈复杂度分。从指标的角度来看，这两个示例之间唯一可衡量的区别是 Listing 2.11: 嵌入逻辑的条件 更短。遗憾的是，它并不是因为包含了一个抽象而变短的，而是因为它将缺乏理解的内容挤在了一个非常小的空间里。这种简洁使得代码更难理解，并掩盖了“bottles”背后的底层概念。

编写“无耻绿”（Shameless Green）意味着为了可理解性而非可变性而进行优化，并且如果这样做有助于底层抽象，就耐心地容忍重复。随后的测试或未来的需求将提供改进代码所需的确切信息。尽管 Listing 2.10: 裸露的条件 保留了一些重复，但它抵制在获得所有可用信息之前创建抽象，因此是两种方案中更优的。

### 2.5. 遵循计划

正如你所看到的，朝着“无耻绿”努力意味着有时应该消除重复，有时应该保留重复。“无耻绿”方案是针对直观和揭示意图而优化的，并不关心可变性或未来的维护。目标是利用“绿色”来最大化你对问题的理解，并在提交抽象之前发掘`所有`信息。

在某一个点（实际上，在本章结束时），你将为“99 瓶啤酒”编写一套完整的测试套件，和一个完整的“无耻”解决方案。一旦完成，你有两个选择：你可以将无耻的代码部署到生产环境并离开，或者通过 `DRY` 重复代码将其重构为更具变性的结构。

在“无耻绿”中，为那些拥有许多示例的理念创建抽象是完全可以的。例如，Listing 2.8: 通用诗节 将 97 简化为了单一抽象。拥有许多示例让你有信心认为你看到的是正确的抽象，并且尽早创建该抽象会让代码更易理解。

在编写“无耻绿”时，你应该表达无歧的抽象，但要避免捕捉那些并不成熟的抽象。Listing 2.11: 嵌入逻辑的条件 将一个条件挤在诗节字符串内部，以避免编写第 2 节的独立副本。在这种情况下，新代码令人困惑，且只有两个示例，所以这里最好深吸气，在等待更多信息时写下第 2 节。

将通“无耻绿”的路径想象成沿着水平轴运行。某些更改推动你沿着这条路径前进并帮助你达到“绿色”，而另一些则是垂直方向上推测性和分散的切线。你应该在沉溺于任何离题之前完成整个水平路径。现在你已经有了第 99 到第 2 节的代码，继续沿着水平路径为第 1 节编写测试是有意义的，如下所示：



# 2.6 暴露职责

`verses` 方法需要两个参数 `$a` 和 `$b` 来表示段歌范围的开始和结束。例如，`verses(99, 98)` 应该返回段歌 99 和 98 的歌词。

目标是泛化 `verses` 方法使其能够处理任何段歌范围。这将涉及循环遍历范围并累积歌词。

```php
public function verses($a, $b)
{
  $result = "";

  for ($i = $a; $i > $b; $i--) {
    $result .= $this->verse($i) . "\n";
  }

  return $result;
}
```

上面的代码有一个错误：它在结果最后多了一个换行符。我们可以通过只在最后一段之前添加换行符来修复它。

在本章开头，从段歌 99 开始是合理的。然而，由于 `verses` 方法需要两个参数，从 99 和 98 开始是合理的。

这里是测试：

[Listing 2.16: 段歌 99 98 测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-190/test/BottlesTest.php#L51-L63)

```php
public function test_a_verses()
{
  $expected =
    "99 bottles of beer on the wall, " .
    "99 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "98 bottles of beer on the wall.\n" .
    "\n" .
    "98 bottles of beer on the wall, " .
    "98 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "97 bottles of beer on the wall.\n";

  $this->assertEquals($expected, (new Bottles())->verses(99, 98));
}
```

这是通过该测试的一种可能方法：

[Listing 2.17: 段歌 99 98 字面量](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-200/lib/Bottles.php#L4-L15)

```php
public function verses(): string
{
  return
    "99 bottles of beer on the wall, " .
    "99 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "98 bottles of beer on the wall.\n" .
    "\n" .
    "98 bottles of beer on the wall, " .
    "98 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "97 bottles of beer on the wall.\n";
}
```

虽然上面的代码明显通过了测试，但许多程序员会认为它是不可接受的。如果被要求说明其中的缺陷，你可能会抱怨它重复了 `verse` 方法中的代码。这确实如此。`verse` 方法已经包含了相当的重复，而这个新的 `verses` 方法又重复了其中一些已有的代码。

在寻找“无耻的绿瓶”的过程中，某些重复是可以容忍的。然而，并不是所有重复都有帮助，上述引入的这种重复具有某些特性，意味着它*不应该*被容忍。这段新代码反而让水变得浑浊，而不是变得清晰，理解其原因至关重要。

当重复能为你尚不理解的通用概念提供独立、具体的示例时，它是有用的。例如，在前一节中，`verse` 内部的 `switch` 语句演变为包含四个不同的模板。这些模板是更通用的歌谣的具体示例。每个模板都提供了独特的信息，但它们共同引导你通向底层的抽象。

上述 `verses` 实现的问题在于，它*没有*隔离出一个新的、独立的示例，而是重复了你已经识别出的示例。生成第 99 和第 98 首歌谣的代码已经存在于 `verse` 方法 `switch` 语句的 `default` 子句中（重复如下）。

[Listing 2.18: 歌谣拥有默认值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-210/lib/Bottles.php#L11-L38)

```php
public function verse(int $number): string
{
  switch ($number) {
    // ...
    default:
      return
        $number . " bottles of beer on the wall, " .
        $number . " bottles of beer.\n" .
        "Take one down and pass it around, " .
        ($number-1) . " bottles of beer on the wall.\n";
  }
}
```

注意 Listing 2.17: 99 98 歌谣字面量版 只是上述模式的非通用版本。因此，这段新代码*重复了一个已经存在的示例*，因此没有就该问题提供任何新信息。此外，重复这些已有的代码掩盖了 `verses` 的真实职责。如果暴露这个隐藏的职责而不是掩盖它，这个方法将更具意图。

`verses` 方法的职责是理解它的输入参数，并知道如何使用这些参数产生正确的输出。它的工作不是知道任何歌谣的确切歌词。它的工作反而是反复将这个问题转交给 `verse` 方法，并将答案累积成一个多首歌谣的字符串。

代码渴望尽可能保持无知。虽然让 `verse` 方法负责知道歌谣模板是完全合理的，但一旦 `verse` 承担了这一责任，你应用程序的其他部分就不应该抢夺这一责任。

这里是 `verses` 的另一种实现，它知道的更少，但揭示的更多：

[Listing 2.19: 99 98 歌谣消息版](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-210/lib/Bottles.php#L4-L9)

```php
public function verses(): string
{
  return
    $this->verse(99) .
    "\n" .
    $this->verse(98);
}
```



这段代码讲述的故事是：`verses` 是由 `verse` 组成的（抱歉），并且歌谣序列与单首歌谣之间存在某种关系。Listing 2.17: 99 98 歌谣字面量版 隐藏了这种关系，而这个示例开始暴露它。

上面的代码是通过此测试的最简单方式，但你可能已经迫不及待要做更多了。你一定知道 `verses` 方法最终必须为 100 首歌谣生成歌词。你意识到上面的代码是不完整的，因此是临时的。你知道真正的 `verses` 实现最终将从高到低循环，为每个数字调用 `verse` 并累积响应。在这里遵循“最简单事物”规则在真实解决方案如此明显时，可能会感到枯燥且耗时。

在《实例测试驱动开发》（Test-Driven Development by Example）的第 28 章中，Kent Beck 描述了让测试通过的不同方法。他的“绿条模式”中有三种：

* 伪装（Fake It - Til You Make It）
* 显然实现
* 三角化

之前对 `verses` 的两次尝试（Listing 2.17: 99 98 歌谣字面量版 和 Listing 2.19: 99 98 歌谣消息版）都是*伪装*的示例，因为尽管每个实现都通过了当前测试，但测试尚未完成。第一个示例被放弃了而选择了第二个，但两者都是*伪装*，因为它们都没有做完最终版本要做的所有。

```php
public function test_a_few_verses() {
  $expected =
    "2 bottles of beer on the wall, " .
    "2 bottles of beer.\n" .
    "Take one down and pass it around, " .
    "1 bottle of beer on the wall.\n" .
    "\n" .
    "1 bottle of beer on the wall, " .
    "1 bottle of beer.\n" .
    "Take it down and pass it around, " .
    "no more bottles of beer on the wall.\n" .
    "\n" .
    "No more bottles of beer on the wall, " .
    "no more bottles of beer.\n" .
    "Go to the store and buy some more, " .
    "99 bottles of beer on the wall.\n";
  $this->assertEquals($expected, (new Bottles())->verses(2, 0));
}
```

你再次必须在硬编码一个新的特例情况或泛化代码之间做出选择。例如，你*可以*通过在 `verses` 方法中显式地添加新条件来使测试通过，如下：

[Listing 2.21: 特定歌节范围](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-230/lib/Bottles.php#L4-L15)

```php
public function verses(int $upper, int $lower): string {
  if ($upper === 99) {
    return
      $this->verse(99) . "\n" .
      $this->verse(98);
  } else {
    return
      $this->verse(2) . "\n" .
      $this->verse(1) . "\n" .
      $this->verse(0);
  }
}
```

或者，你可以修改代码使其更抽象，如下所示：

[Listing 2.22: 范围内的歌节](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-240/lib/Bottles.php#L4-L9)

```php
public function verses(int $upper, int $lower): string {
  return implode(
    "\n",
    array_map([$this, 'verse'], range($upper, $lower))
  );
}
```

在 a) 添加条件或 b) 使代码更抽象之间做出这种选择，应该让你想起之前的早前的讨论。在消除重复 章节中，当你修改 `verse` 以通过第 3 个歌节的测试时，你就面临过完全相同的情况。

在这两种情况下，都有许多该问题的现有示例，并且底层抽象已经得到了理解。因此，在消除重复 中提出的论点在这里与之前一样适用。

与其替代方案相比，Listing 2.22: 范围内的歌节 更容易理解，且实现成本相同，你拥有所有所需的信息来确信它是正确的。它是最佳解决方案，不仅因为它通过了测试，还因为它清晰地揭示了 `verses` 产生*任何*范围歌节的责任。它泛化了代码，当你确信自己理解了抽象时，这是最佳选择。现在你已经可以生成任何序列的歌节了，最后的任务是为整首歌生成歌词。

### 2.7 选择名称

在本章开始时，计划是创建一个 `Bottles` 类，实现以下 API：

* `verse(n)`
* `verses($upper, $lower)`
* `song()`

到目前为止，这个计划是通行的。`verse` 和 `verses` 方法已经完成；现在是处理 `song` 方法了，正如这里的[Listing 23: 代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-260/lib/Bottles.php#L4) 所示：

```php
public function song(): string {
  return $this->verses(99, 0);
}
```

反思 `song` 方法整体的好时机。`song` 方法在 API 中是显式的，调用者并不需要知道 `verses(99, 0)` 的细节。`song` 方法的出现并不是为了增加负担，因为 `verses(99, 0)` 就能返回整首歌。`song` 方法的存在是合理的，但 `verses(99, 0)` 产生相同的输出这似乎是冗余的。`song` 的调用者想要的是整首歌，他们不应该去纠结它是如何实现的细节。

### 2.8 揭示意图

Kent Beck 解释了意图与实现的区别：

> 意图与实现的区别允许你在本质上理解计算，并在必要时再考虑细节。
> —— Kent Beck，《实现模式》第 69 页

这里 `song` 是意图，而 `verses(99, 0)` 是实现。对于想要某个范围歌节的人来说，`verses` 方法有很大差异。`song` 方法的依赖关系产生了如下结果：

* 歌节的名称
* 歌曲的开始
* 歌节的结束
* 99 瓶啤酒开始
* 0 瓶啤酒的结束

这产生了大量的知识。`song` 方法的发送者想要的是歌节，而不是强迫他们去思考它是如何发生的。在 `song` 方法捍卫了自己的价值后，这里是 99 瓶啤酒的完整“绿色”代码。[Listing 2.24: 初始绿色代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-260/lib/Bottles.php#L3-L48)

```php
class Bottles {
  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    switch ($number) {
      case 0:
        return
          "No more bottles of beer on the wall, " .
          "no more bottles of beer.\n" .
          "Go to the store and buy some more, " .
          "99 bottles of beer on the wall.\n";
      case 1:
        return
          "1 bottle of beer on the wall, " .
          "1 bottle of beer.\n" .
          "Take it down and pass it around, " .
          "no more bottles of beer on the wall.\n";
      case 2:
        return
          "2 bottles of beer on the wall, " .
          "2 bottles of beer.\n" .
          "Take one down and pass it around, " .
          "1 bottle of beer on the wall.\n";
      default:
        return
          $number . " bottles of beer on the wall, " .
          $number . " bottles of beer.\n" .
          "Take one down and pass it around, " .
          ($number-1) . " bottles of beer on the wall.\n";
    }
  }
}
```

事实上，测试中存在许多遗漏。例如，第 4 到 97 节歌没有任何覆盖，而且无法保证这些节歌按照正确的顺序出现。

`Bottles` 现在已经产生了正确的输出了，在这一刻，人们很想就此收手。然而，这样做是将让这段代码保持持续运行的负担转嫁给了某个可怜的下游程序员，而他们对该问题的理解远不如现在的你。

因此，接下来的章节将关注于如何收紧测试。

## 2.9 编写成本效益的测试

TDD（测试驱动开发）承诺提供简单直接、无 bug 且能够放信且轻松地更改的软件。TDD 并不声称它是免费的，而是认为它的收益大于成本。

对 TDD 价值的信仰已成为主流，遵循这种实践的压力已接近于一种不成文的指令。对这一指令的接受可以从这一事实看出：不写测试的人经常会感到局愧并道歉。即使是那些不写测试的人，似乎也认为自己应该这样做。

尽管有这种普遍共识，但悲哀的事实是 TDD 的承诺并没有得到普遍实现。许多应用程序的测试难以理解、难以更改，且运行耗时得惊人。这些测试不仅没有实现变更，反而积极地阻碍了变更。世界上充斥着被维护者深恶恶的测试套件，有时到了被遗弃的地步。

这种痛苦大部分源于与代码耦合过紧密的测试。当这样做时，代码的每一步改进都会破坏测试，迫使测试随之改变。因此，学习测试艺术的第一步是理解如何编写测试来确认你的代码执行了*什么*，而无需知道代码是*如何*做到的。

本节将探讨测试与代码之间耦合的问题。为了回顾现状，这里是目前的测试代码：

[列表 2.25：无歌词测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-260/test/BottlesTest.php#L5-L91)

```php
class BottlesTest extends \PHPUnit\Framework\TestCase {
  public function test_the_first_verse() {
    $expected =
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verse(99));
  }

  public function test_another_verse() {
    $expected =
      "3 bottles of beer on the wall, " .
      "3 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "2 bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verse(3));
  }

  public function test_verse_2() {
    $expected =
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verse(2));
  }

  public function test_verse_1() {
    $expected =
      "1 bottle of beer on the wall, " .
      "1 bottle of beer.\n" .
      "Take it down and pass it around, " .
      "no more bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verse(1));
  }

  public function test_verse_0() {
    $expected =
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verse(0));
  }

  public function test_couple_verses() {
    $expected =
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n" .
      "\n" .
      "98 bottles of beer on the wall, " .
      "98 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "97 bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new Bottles())->verses(99, 98));
  }
}
```



确实，测试中存在许多遗漏。例如，第 4 到 97 节歌没有任何覆盖，而且无法保证这些节歌是按照正确的顺序出现。

`Bottles` 现在已经产生了正确的输出了，在这一刻，人们很想就此收手。然而，这样做是将让这段代码保持持续运行的负担转嫁给了某个可怜的下游程序员，而他们对该问题的理解远不如现在的你。

因此，接下来的章节将关注于如何收紧测试。

## 2.9. 编写成本效益的测试

TDD 承诺提供简单直接、无 bug 且能够自信且轻松地更改的软件。TDD 并不声称它是免费的，而是认为它的收益大于成本。

对 TDD 价值的信仰已成为主流，遵循这种实践的压力已接近于一种不成文的指令。对这一指令的接受可以从这一事实看出：不写测试的人经常会感到愧疚并道歉。即使是那些不写测试的人，似乎也认为自己应该这样做。

尽管有这种普遍共识，但悲哀的事实是 TDD 的承诺并没有得到普遍实现。许多应用程序的测试难以理解、难以更改，且运行耗时得惊人。这些测试不仅没有实现变更，反而积极地阻碍了变更。世界上充斥着被维护者深恶痛绝的测试套件，有时到了被遗弃的地步。

这种痛苦大部分源于与代码耦合过紧密的测试。当这样做时，代码的每一步改进都会破坏测试，迫使测试随之改变。因此，学习测试艺术的第一步是理解如何编写测试来确认你的代码执行了*什么*，而无需知道代码是*如何*做到的。

本节将探讨测试与代码之间耦合的问题。为了回顾现状，这里是目前的测试：

[列表 2.25：无歌词测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-260/test/BottlesTest.php#L5-L91)

（此处省略重复的代码块，按要求处理）

```php
class Bottles {

  public function song(): string {

    return $this->verses(99, 0);

  }

  public function verses(int $upper, int $lower): string {

    if ($upper === 99 && $lower === 98) {

      return

        $this->verse(99) . "\n" .

        $this->verse(98);

    } else if ($upper === 2) {

      return

        $this->verse(2) . "\n" .

        $this->verse(1) . "\n" .

        $this->verse(0);

    } else {

      return 'ok';

    }

  }

  public function verse(int $number): string {

    switch ($number) {

      case 0:

        return

          "No more bottles of beer on the wall, " .

          "no more bottles of beer.\n" .

          "Go to the store and buy some more, " .

          "99 bottles of beer on the wall.\n";

      case 1:

        return

          "1 bottle of beer on the wall, " .

          "1 bottle of beer.\n" .

          "Take it down and pass it around, " .

          "no more bottles of beer on the wall.\n";

      case 2:

        return

          "2 bottles of beer on the wall, " .

          "2 bottles of beer.\n" .

          "Take one down and pass it around, " .

          "1 bottle of beer on the wall.\n";

      default:

        return

          $number . " bottles of beer on the wall, " .

          $number . " bottles of beer.\n" .

          "Take one down and pass it around, " .

          ($number-1) . " bottles of beer on the wall.\n";

    }

  }

}
```

上面的代码利用了测试中的弱点，在没有实际生成所有章节的情况下通过了测试（绿色）。为了纠正这一点，你可能会按照以下方式修改 `song` 测试：

[列表 2.28: 再次完整的歌曲测试逻辑](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-300/test/BottlesTest.php#L84-L91)

```php
public function test_the_whole_song() {

  $bottles = new Bottles();

  $expected = implode(

    "\n",

    array_map([$bottles, 'verse'], range(99, 0))

  );

  $this->assertEquals($expected, $bottles->song());

}
```

这个新测试成功地强制 `song` 生成每一个章节，但以这种方式修改测试只是在让自己越陷越深。考虑一下刚刚发生了什么。原始测试断言发送 `song` 产生的结果与运行当前包含在 `song` 中的代码相同。换句话说，它断言

```
song()
```

和

```
verses(99, 0)
```

返回相同的输出。

这个新测试断言 `song` 的结果与运行当前包含在 `verses` 中的代码相同。因此

```
song()
```

和

```
implode(
  "\n",
  array_map([$bottles, 'verse'], range(99, 0))
);
```

返回相同的输出。

注意，尽管第二个变体强制了每个章节的生成，但测试仍然在复制 `Bottles` 中的代码。现在，它不是断言 `song` 的输出类似于 `song` 的当前实现，而是断言 `song` 的输出类似于 `verses` 的当前实现。这并没有改进测试，只是将测试与堆栈中更深一步的代码紧密耦合在一起。如果那段更远的代码发生了变化，这个测试可能会崩溃。

这个测试问题有一个显而易见的解决方案，上面提到过。`song` 测试不应该知道 `Bottles` 类是如何生成歌曲的。这里清晰且明确的预期是 `song` 返回完整的歌词，而测试 `song` 最好且简单的方法是显式地断言它是这样做。

这就是该测试：

[列表 2.29: 歌曲测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-310/test/BottlesTest.php#L84-L390)

```php
public function test_the_whole_song() {

  $expected = <<< SONG
99 bottles of beer on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer on the wall.
98 bottles of beer on the wall, 98 bottles of beer.
Take one down and pass it around, 97 bottles of beer on the wall.
97 bottles of beer on the wall, 97 bottles of beer.
Take one down and pass it around, 96 bottles of beer on the wall.
... (已省略)
SONG;

  $this->assertEquals($expected, (new Bottles())->song());

}
```

在上面的列表中，`$expected` 字符串非常长，以至于你可能不想写出完整的歌词。所需的文本相当冗长。

### 2.11 考虑选项

如果你发现重复让你感到困扰，请考虑替代方案。你的选择有：

1. *断言预期输出与另一个方法的匹配。*

前两个 `song` 测试变体都是这样做。这些测试与当前实现耦合，因此依赖关系意味着即使应用程序没有问题，测试也可能会崩溃。

2. *断言预期输出与动态生成的字符串匹配。*

一旦你接受 `song` 测试应该验证特定的输出而不是耦合到实现，你就必须决定如何创建输出。由于 `song` 返回的是长且重复的字符串，许多程序员想要、甚至有义务在*测试内部*减少这种重复。

然而，在测试内部减少重复必然需要逻辑。这种逻辑已经存在于 `Bottles` 类中，因此测试将被强制调用、复制或重新实现它。无论你如何做，在这里使用任何逻辑意味着 `Bottles` 的更改可能会以意想不到且困惑的方式破坏 `song` 测试。

3. *断言预期输出与硬编码字符串匹配。*

在这种情况下（如列表 2.29: 歌曲测试），不仅预期输出清晰明确，而且测试没有依赖关系。这些质量结合使其易于理解并容忍代码的变化。

在这三个选择中，只有第三种独立于当前实现，因此能够应对 `Bottles` 的变化。你可能很难说服自己写下整个歌词字符串，但记住，在测试中进行 DRY 处理会迫使你引入抽象。测试*不是*抽象的地方——它们是具体实现的地方。抽象属于代码。

DRY 在代码中是一个很好的主意，但在测试中用处不大。测试时，最好的选择通常是直接写下来。

这里是完整的 `Bottles` 列表：

[列表 2.30: 无耻的绿色](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c2-tests-310/lib/Bottles.php#L3-L48)

```php
class Bottles {

  public function song(): string {

    return $this->verses(99, 0);

  }

  public function verses(int $upper, int $lower): string {

    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );

  }

  public function verse(int $number): string {

    switch ($number) {

    case 0:

      return
        "No more bottles of beer on the wall, " .
        "no more bottles of beer.\n" .
        "Go to the store and buy some more, " .
        "99 bottles of beer on the wall.\n";

    case 1:

      return
        "1 bottle of beer on the wall, " .
        "1 bottle of beer.\n" .
        "Take it down and pass it around, " .
        "no more bottles of beer on the wall.\n";

    case 2:

      return
        "2 bottles of beer on the wall, " .
        "2 bottles of beer.\n" .
        "Take one down and pass it around, " .
        "1 bottle of beer on the wall.\n";

    default:

      return
        $number . " bottles of beer on the wall, " .
        $number . " bottles of beer.\n" .
        "Take one down and pass it around, " .
        ($number-1) . " bottles of beer on the wall.\n";

    }

  }

}
```

`Bottles` 的测试和代码现在已经完成了。测试非常直观，代码也易于理解。

## 2.12. 总结

测试如果做得当，可以加速开发并降低成本。遗憾的是，事实也是：错误的测试会拖慢你的速度并浪费金钱。

因此，精通测试是值得的。`TDD` 可以防止昂贵的猜测，但前提是你承诺以小步骤编写代码。测试可以让重构变得安全且容易，但前提是它们必须与当前代码仔细地解耦。

良好的测试不仅能讲述一个故事，还能一步步引导你得出一个组织良好的解决方案。本章编写的测试（假设程序员保持了恰当的节制）产生了“无耻之绿”（Shameless Green）。

“无耻之绿”方案既聪明也不具有扩展性。它的价值在于代码易于理解且编写成本低。如果事情永远不发生变化，这个方案绝对足够了。

只有当某些事情需要改变时，事情才会变得有趣。所以，进入第 3 章，它将引入一个新需求，并迫使你对代码做出一些艰难的决定。

## 3. 挖掘概念

“无耻之绿”方案看重可读性、直观性和效率，而很少考虑可变性。它包含了重复，并且对倾向于过程化的方向并无歉意。它快速且廉价，至少在事情发生变化之前可能是足够的。

然而，在现实世界中，需求*会*发生变化，当这种情况发生时，代码的标准也会随之提高。

本章定义了一个新需求，这触发了对代码结构的更深层次观察。随后引入了一些直观的规则，允许你系统且增量地改进代码，而不必担心迷失或引入 Bug。这些规则很简单，但它们允许复杂行为的出现。到本章结束时，你将开始挖掘目前隐藏在代码中的概念。

### 3.1. 倾听变化

代码是昂贵的。编写代码需要时间或金钱。因此，你有必要尽可能高效。最具成本效益的代码是“够用即可，绝不过好”。

然而，编程是一门艺术，程序员热爱优雅的代码。困境在于，一旦存在一个初始的、更平庸的解决方案，问题就解决了，此时选择是否继续改进需要权衡。

如果现在就重构，你可能在浪费时间；但如果推迟再重构，你可能要付出昂贵的代价。良好的测试可以让重构变得安全且容易，但前提是它们与当前代码仔细地解耦。

（此处省略了原文中重复部分，已合并翻译）

```php
public function verse(int $number): string {

  switch ($number) {

  case 0:

    return
      "No more bottles of beer on the wall, " .
      // ...

  case 1:

    return
      "1 bottle of beer on the wall, " .
      // ...

  case 2:

    return
      "2 bottles of beer on the wall, " .
      // ...

  case 6:

    return
      "1 six-pack of beer on the wall, " .
      "1 six-pack of beer.\n" .
      "Take one down and pass it around, " .
      "5 bottles of beer on the wall.\n";

  case 7:

    return
      "7 bottles of beer on the wall, " .
      "7 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 six-pack of beer on the wall.\n";

  default:

    return
      $number . " bottles of beer on the wall, " .
      // ...

  }

}
```



`verse` `switch` 语句最初包含四个分支，而在上面的代码中分支的数量已经膨胀到了六个。这是不可接受的。条件判断会“繁殖”，既然现在这一个已经开始繁殖了，你必须采取措施来停止它。

### 3.2 从开闭原则开始

最初是否进行重构的决定，应该取决于你的代码是否已经对新需求是“开放”的。

“开放（Open）”是“开闭（Open/Closed）”的缩写，而后者又是“对扩展开放，对修改关闭”的缩写。“开放”中的“O”提供了缩写词“SOLID”中的“O”（参见侧边栏）。当你可以在不更改现有代码的情况下满足新需求时，代码就是对新需求开放的。

#### SOLID 设计原则

SOLID 这一缩写由 Michael Feathers 创造，并由 Robert Martin 推广。每个字母代表面向对象设计中的一个广为人知的原则。以下是每个原则的正式定义：

- **S - 单一责任原则 (Single Responsibility)**：类中的方法应该围绕单一目的保持内聚性。
- **O - 开闭原则 (Open-Closed)**：对象应该对扩展开放，但对修改关闭。
- **L - 利可夫替换原则 (Liskov Substitution)**：子类应该可以替换它们的父类。
- **I - 接口隔离原则 (Interface Segregation)**：对象不应强制依赖于它们不使用的方法。
- **D - 依赖倒转原则 (Dependency Inversion)**：依赖抽象，不要依赖具体实现。

如果你觉得上面的定义没那么启发性，不要绝望。当书中引用这些原则时，会附上通俗语言的解释（如下所示）。

“开放”原则指出，你不应该将移动代码的过程（即重构）与添加新功能的行为混淆。相反，你应该将这两个操作分开。面对新需求时，首先重新调整现有代码，使其对新功能开放，一旦完成，再添加新代码。

当前的 `Bottles` 类对“六瓶装”需求是不开放的，因为添加新的变体需要编辑条件语句。因此，当面对这个新需求时，你的首要任务是重构现有代码，使其变成一种你只需通过添加代码就能实现新需求的形式。遗憾的是，你很可能不知道如何这样做，因此对于如何处理这个问题感到无所措。

幸运的是，你不需要知道所有事情才能选择正确的位置。面对这种情况时，请遵循以下流程图。

图 3.1：开闭流程图。根据上述流程图，首先问问自己，现有代码是否已经对新需求开放？如果是，你的工作仅仅是编写新代码。如果不是，接着问自己是否知道如何修改现有代码使其对新需求开放。这也很简单直观。如果是，就进行修改，然后编写新代码。然而，悲哀的事实是，这两个问题的答案往往是“否”。现有代码对新需求开放，而你不知道如何让它变得开放。在此时，“代码异味（code smells）”将来救援。如果你能识别出代码中的异味，就隔离并修正它们。

### 3.3 识别代码异味

大多数代码都是不完美的。它们的缺陷很多，而且纠缠得很，导致无法一次性纠正所有缺陷。如果你曾经处理过一段代码，在不断做出更改却无法完成任务，并最终回滚了所有更改，你就理解这个问题了。成功改进包含许多缺陷代码的诀窍在于一次隔离并修正它们。Martin Fowler 在他的《重构》(http://martinfowler.com/books/refactoring.html) 一书中识别并命名了常见的缺陷，并提供了修复它们的重构配方。第 3 章（由创造该术语的 Kent Beck 合写）将缺陷称为“代码异味”。多亏了 Fowler 的书，如果你能识别出代码中的异味，就可以查找相应的治疗性重构并应用该重构来消除缺陷。

如果你在想现在是否需要阅读 Fowler 的书，答案是“不一定”。Fowler 的原则在这里得到了介绍和演示。然而，本书仅探索了许多重构配方中的几种，熟悉这些对你有大益。Fowler 的书是一项极佳的投资。如果被要求列举几种代码异味，你可能会建议“重复”或“类太大”，而`重复代码（Duplicated Code）`和`大类（Large Class）`确实是 Martin Fowler《重构》书中列出的两种异味。消除这些异味的方法显而易见（抽象重复或将一个类拆分），因此异味似乎是一个很泛的概念。

然而，还有许多你可能不熟悉的代码异味。你可能猜出`发散变化（Divergent Change）`的定义，但你能定义`特征嫉妒（Feature Envy）`吗？你能识别并指定`原始痴迷（Primitive Obsession）`、`不恰亲密（Inappropriate Intimacy）`或`散弹手术（Shotgun Surgery）`的治疗性重构吗？

探索每一个代码异味超出了本书的范围，特别是 Fowler 先生已经彻底涵盖了这个主题。然而，在这里进行的重构将由异味驱动和引导，因此当前的任务是在当前的 `Bottles` 类中识别异味。

### 3.4 确定最佳攻击点

当前的 99 Bottles 代码对六瓶装需求是不开放的。如果不清楚如何让它开放（通常通常如此），前进的方法是开始消除代码异味。如果异味并不显而易见，请从列出你不满意的地方开始。

考虑 `verse` 方法（如下）。

列表 3.3：无耻的 Verse (https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L15-L42)

```php
public function verse(int $number): string {

  switch ($number) {

  case 0:

    return

      "No more bottles of beer on the wall, " .

      "no more bottles of beer.\n" .

      "Go to the store and buy some more, " .

      "99 bottles of beer on the wall.\n";

  case 1:

    return

      "1 bottle of beer on the wall, " .

      "1 bottle of beer.\n" .

      "Take it down and pass it around, " .

      "no more bottles of beer on the wall.\n";

  case 2:

    return

      "2 bottles of beer on the wall, " .

      "2 bottles of beer.\n" .

      "Take one down and pass it around, " .

      "1 bottle of beer on the wall.\n";

  default:

    return

      $number . " bottles of beer on the wall, " .

      $number . " bottles of beer.\n" .

      "Take one down and pass it around, " .

      ($number-1) . " bottles of beer on the wall.\n";

  }

}
```

该方法包含一个 `switch` 语句（即 `Switch Statements` 坏气味），其分支包含许多重复的字符串（`Duplicated Code` 重复代码）。在这两种气味中，`Duplicated Code` 是最直观的，因此首先处理它。

因此，当前任务是重构 `verse` 方法以消除重复，希望并期待生成的代码能够更好地对“六音节”（six-pack）需求保持开放。

在进行此重构之前，必须承认，消除重复与成功使代码对六音节需求保持开放之间并没有`直接`的联系。然而，这正是这种技术的精妙之处。你不需要预先知道如何解决整个问题。计划是像蚕食叶一样，一次处理一个代码气味，信通通开放之路会逐渐显现。

### 3.5 系统化重构

在反复讨论这个词之后，现在是时候给“重构”下一个正式的定义了。根据 Fowler 的定义：

> 重构是改变软件系统的一种，使其在不改变代码外部行为的同时，改进其内部结构。
>
> — Martin Fowler

#### 重构

简而言之，重构在不改变行为的情况下改变代码的排列。记住，新需求应该分两个步骤实现：首先，你重新排列现有代码，使其对新需求开放。接下来，你编写新代码来满足该需求。这些步骤中的第一步就是重构。

注意，安全的重构依赖于测试。如果你确实是在不改变行为的情况下重新排列代码，那么在过程中的每一步，现有测试都应该继续通过。测试是安全保障，赋予了你对新代码安排的信心。如果它们开始失败，那么只有两种可能：要么 a) 你在无意中破坏了代码，要么 b) 现有测试存在缺陷。

如果测试因为你破坏了代码而失败，解决办法很简单：撤销上一次更改，进行一次更好的更改，然后愉快地继续你的工作。

然而，如果你在`不改变行为`的情况下重新排列代码但测试开始失败，那么测试本身是有缺陷的。对事情的`如何`执行而非对实际发生了`什么`的进行断言的测试，是导致这种困境的主要原因。例如，一个对方法的如何实现方式进行断言的测试，在你改变该方法的实现方式时显然会崩溃，即使它的输出没有变化。在这种情况下，除了在开始重构之前改进测试外别无其他选择。

测试是你背后的盾牌。成功的重构`依赖`于绿色测试（通过的测试）。因此，你不应该在重构期间更改测试。如果你的测试存在缺陷并干扰了重构，请先改进它们，然后再进行重构。

### 3.6 遵循群集规则

记住，当前任务是消除 `verse` 方法中 `switch` 语句的重复。

`switch` 语句有四个分支，每个分支都包含一个诗歌模板（verse template）。模板代表了不同的诗歌变体。这些变体显然不同，但在某些尚未识别的、更抽象的情况下，它们也是相似的。

从更高的视角来看，每个变体都只是歌曲中的一段诗歌；从这个意义上说，它们都是相同的。每个具体变体的底层都是通用的诗歌抽象。如果你能找到这种抽象，就可以用它将四分支的 `switch` 语句简化为一行代码。

好消息是，你不需要预先能够看到这种抽象。你可以通过迭代应用一组简单的简单规则来发现它。这些规则被称为“群集规则”（Flocking Rules），如下：

#### 群集规则

1. 选择最相似的东西。
2. 找到它们之间最小的差异。
3. 做出简单的更改以消除该差异。

代码的更改可以分为四个不同的步骤：

1. 解析新代码
2. 解析并执行它
3. 解析、执行并使用其结果
4. 删除未使用的代码

这些步骤将在稍后更详细地解释，但现在请将解析（parse）步骤视为确认语法有效，将解析/执行（parse/execute）步骤证明代码运行无崩溃，将解析/执行/使用（parse/execute/use）步骤确保它返回正确的结果。

做出小的更改意味着当出现问题时你会获得非常精确的错误信息，因此知道如何在这种粒度下工作非常有用。随着经验的增加，你会开始迈更大的步，但如果你迈了一大步并遇到错误，应该撤销更改并改作较小的更改。

当你遵循群集规则时：

* 现在，一次只更改一行。
* 每次更改后都运行测试。
* 如果测试失败，撤销并进行一次更好的更改。

#### 为什么是“群集”？

鸟类成群，鱼类成群，昆虫成群。群的行为可能看起来是同步且复杂的，以给人一种中心化协调的印象。事实远非如此。群的行为是每个参与个体所做出的一系列连续微小决策的结果。这些决策受到三个简单规则的指导。

1. 对齐（Alignment）——向邻居的平均方向飞行
2. 分离（Separation）——不要离邻居太近
3. 凝聚（Cohesion）——向群的平均位置移动

因此，复杂的行为产生于简单规则的重复应用。正如规则允许鸟成群一样，代码的“群集规则”让抽象得以出现。

![惊人的群集](img/the_flock_of_starlings.jpg) 行为中的星牛群，John Holmes, CC BY-SA 2.0

要查看群集行为的精彩示例，请观看 Steven Strogatz 的[同步科学](https://youtu.be/IiXaZGqp?t=196) TED 演讲。

### 3.7 收敛于抽象

群集规则如此原子化且通用，以至于可能无法引发信心。本章的剩余部分将使用它们在 `verse` 方法中挖掘抽象，之后你可能会发现这个过程更有说服力。

#### 关注差异

虽然对于某些问题的解决方案是显而易见的，但任何有趣规模的问题都无法即时理解。它们太大，或者包含许多部分。

在检查复杂问题时，眼睛首先会被相似性吸引。然而，尽管相似性更容易识别，但差异更有用，因为它更有意义。提取相似性有一定的价值，但提取差异更有价值。

Erich Gamma、Richard Helm、Ralph Johnson 和 John Vlissides 被称为“四人帮”，因为他们合著了[面向对象软件的设计模式](https://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)。这本富有影响力的书籍描述了二十三种解决面向对象编程问题的模式或解决方案，它这样解释这一过程：

> 这里的重点是封装发生变化的概念，这是许多设计模式的主题。

好消息是，重构规则的系统应用会将差异转换为相似性，将问题分解为它的组成部分。更好的消息是，这是自动发生的。你不需要在重构之前识别底层的抽象。你只需要按照规则编写代码，抽象就会随之而来。

这种认为自己已经理解了抽象，并直接跳到一个预设的解决方案的习惯已经根深蒂固了。程序员研究一个问题，决定一个解决方案，然后对其进行实现。解决方案是有意图地构建的。

如果这描述了你过去所有的经历，你可能会发现以下代码令人惊讶。它通过许多微小的、迭代的步骤，最终产生一个通过重构*发现*的解决方案。

为了将 `verse` 函数中的 `switch` 语句简化为一行代码，规则要求首先识别出最相似的事物。这意味着你应该选择两个最相似的分支，并专注于让它们变得完全相同。

这里再次是对 `switch` 语句的提醒：

列表 3.4：歌方法条件判断 (https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L16-L41)

```php
 1 switch ($number) {

 2 case 0:

 3   return

 4     "No more bottles of beer on the wall, " .

 5     "no more bottles of beer.\n" .

 6     "Go to the store and buy some more, " .

 7     "99 bottles of beer on the wall.\n";

 8 case 1:

 9   return

10     "1 bottle of beer on the wall, " .

11     "1 bottle of beer.\n" .

12     "Take it down and pass it around, " .

13     "no more bottles of beer on the wall.\n";

 14 case 2:

 15   return

 16     "2 bottles of beer on the wall, " .

 17     "2 bottles of beer.\n" .

 18     "Take one down and pass it around, " .

 19     "1 bottle of beer on the wall.\n";

 20 default:

 21   return

 22     $number . " bottles of beer on the wall, " .

 23     $number . " bottles of beer.\n" .

 24     "Take one down and pass it around, " .

 25     ($number-1) . " bottles of beer on the wall.\n";

 26 }

```

注意，虽然第 2 段包含了硬编码的数字 `2` 和 `1`，但它完全可以使用 `$number` 和 `$number-1`，就像 `default` 分支中那样。这部分看起来不同，但在逻辑上是相同的。回想起第 2 段仅有一个测试，该测试断言最后一行说的是“1 bottle”而不是“1 bottles”。`2` 分支和 `default` 分支之间唯一的真实区别是“bottle”单词与“bottles”单词的区别。因此，这些行是最相似的行。

### 3.7.2 简化复杂问题

找到最相似的字符串后，下一个任务是让它们变得相同。专注于这一特定目标而不屈服于偏离主题的诱惑是非常重要的。

将将这两行转为一行的过程想象成行走在一条水平路径上。^(\[10。在这条路径上行走时，如果代码的其他部分（可能在 `0` 或 `1` 分支中）某些东西吸引了你的注意力，你可能会想要垂直方向偏离。然而，如果你在合并 `2` 和 `default` 分支之前开始对代码的其他部分进行更改，你就离开了熟悉的小径，进入了一片如此黑暗和阴险的森林，以至于可能永远无法回来。虽然交替进行水平和垂直工作可能有用，但最好在水平路径的终点在可见时完成当前的旅程。

看看下面的代码：

列表 3.5：2 与默认分支 (https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L16-L41)

```php
 1 case 2:

 2   return

 3     "2 bottles of beer on the wall, " .

 4     "2 bottles of beer.\n" .

 5     "Take one down and pass it around, " .
```



这种认为自己已经理解了抽象，并直接跳到一个预设的解决方案的习惯已经根深蒂固了。程序员研究一个问题，决定一个解决方案，然后对其进行实现。解决方案是有意图构建的。

如果这描述了你过去所有的经历，你可能会发现以下代码令人惊讶。它通过许多微小的、迭代的步骤，最终产生一个通过重构*发现*的解决方案。

为了将 `verse` 函数中的 `switch` 语句简化为一行代码，规则要求首先识别出最相似的事物。这意味着你应该选择两个最相似的分支，并专注于让它们变得完全相同。

这里再次是对 `switch` 语句的提醒：

[Listing 3.4: 歌方法条件判断](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L16-L41)

```
 1 switch ($number) {
 2 case 0:
 3   return
 4     "No more bottles of beer on the wall, " .
 5     "no more bottles of beer.\n" .
 6     "Go to the store and buy some more, " .
 7     "99 bottles of beer on the wall.\n";
 8 case 1:
 9   return
10     "1 bottle of beer on the wall, " .
11     "1 bottle of beer.\n" .
12     "Take it down and pass it around, " .
13     "no more bottles of beer on the wall.\n";
 14 case 2:
 15   return
 16     "2 bottles of beer on the wall, " .
 17     "2 bottles of beer.\n" .
 18     "Take one down and pass it around, " .
 19     "1 bottle of beer on the wall.\n";
 20 default:
 21   return
 22     $number . " bottles of beer on the wall, " .
 23     $number . " bottles of beer.\n" .
 24     "Take one down and pass it around, " .
 25     ($number-1) . " bottles of beer on the wall.\n";
 26 }
```

注意，虽然第 2 段包含了硬编码的数字 `2` 和 `1`，但它完全可以使用 `$number` 和 `$number-1`，就像 `default` 分支中那样。这部分看起来不同，但在逻辑上是相同的。回想起这一点可能有帮助，即：第 2 段仅有一个测试，该测试断言最后一行说的是“1 bottle”而不是“1 bottles。”`2` 分支和 `default` 分支之间唯一的真实区别是“bottle”单词与“bottles”单词的区别。因此，这些行是最相似的行。

### 3.7.2. 简化复杂问题

找到最相似的字符串后，下一个任务是让它们变得相同。专注于这一特定目标而不屈服于偏离主题的诱惑是非常重要的。

将这两行转为一行的过程想象成行走在一条水平路径上。^(\[10]在这条路径上行走时，如果代码的其他部分（可能在 `0` 或 `1` 分支中）某些东西吸引了你的注意力，你可能会想要垂直方向偏离。然而，如果你在合并 `2` 和 `default` 分支之前开始对代码的其他部分进行更改，你就离开了熟悉的小径，进入了一片如此黑暗和阴险的森林，以至于可能永远无法回来。虽然交替进行水平和垂直工作可能有用，但最好在水平路径的终点在可见时完成当前的旅程。

看看下面的代码：

[Listing 3.5: 2 与默认分支](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L16-L41)

```
 1 case 2:
 2   return
 3     "2 bottles of beer on the wall, " .
 4     "2 bottles of beer.\n" .
 5     "Take one down and pass it around, " .
 6     "1 bottle of beer on the wall.\n";
 7 default:
 8   return
 9     $number . " bottles of beer on the wall, " .
10     $number . " bottles of beer.\n" .
11     "Take one down and pass it around, " .
12     ($number-1) . " bottles of beer on the wall.\n";
```

（注：根据原文文本逻辑，此处 Listing 3.5 对应的代码块在描述中并不完整或有偏差，我将根据上下文逻辑进行翻译呈现。）

看看下面的代码：

[Listing 3.6: 替换数字](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-20/lib/Bottles.php#L16-L41)

```
 1 case 2:
 2   return
 3     $number . " bottles of beer on the wall, " .
 4     $number . " bottles of beer.\n" .
 5     "Take one down and pass it around, " .
 6     ($number-1) . " bottle of beer on the wall.\n";
 7 default:
 8   return
 9     $number . " bottles of beer on the wall, " .
10     $number . " bottles of beer.\n" .
11     "Take one down and pass it around, " .
12     ($number-1) . " bottles of beer on the wall.\n";
```

（注：根据原文文本逻辑，此处 Listing 3.6 描述的是将数字替换为变量）

通常规则是，事物的名称应该比事物本身高出一个抽象级别。`"bottle/bottles/six-pack"` 这些字符串是某些类别的实例，而任务是使用领域语言为该类别命名。

识别该类别的一种方法是将具体实例想象成电子表格中的行和列。下面的表说明了这一想法。该表包含三行，每行对应一个具体实例。每行有两个列。第一列包含瓶的数量，下一列是歌曲中与该数字一起使用的单词。

### 表 3.1：瓶数列标题

| Number | `xxx?` |
| --- | --- |
| 1 | `bottle` |
| 6 | `six-pack` |
| n | `bottles` |

上面的列 1 包含数字，因此 `"Number"` 作为列标题是合理的。表头 `"Number"` 比具体实例高出一个抽象级别。`"1,"`、`"6,"` 和 `"n"` 是数字。

第二列包含 bottle、six-pack 和 bottles 条目。Bottle 是这个尚未命名的类别中的一个实体，而不是类别本身。

看起来 `"Unit"`（单位）似乎是一个很好的标题。虽然每个例子都是某种单位，这是事实，但这个名称有两个问题。首先，它太抽象了。Unit 并没有比示例高出一个抽象级别——而是高出许多级。在 `"bottle"` 和 `"unit"` 之间的连续体上，有许多良好的命名替代方案。其次，unit 不属于领域语言。你选择的名称将成为你与客户交流时使用的名称。根据领域概念为事物命名可以改进你与付账单的人们之间的沟通。这只有好处。

当你苦苦于寻找一个好名字，但只有几个具体实例可以指导你时，想象其他也属于同一类别的东西可能会大受启发。例如，如果这首歌是关于葡萄酒的，葡萄酒可能装在水壶里。果汁有时装在盒子里。软饮料通常装在罐子里。

如果你询问你的用户`“瓶是什么种类的东西？”`，他们不会回答`“它是一个单位。”`相反，他们可能会称之为 `container`（容器）。在 `"99 Bottles"` 的语境下，container 是该概念的一个很好的名称。container 有意义、易于理解且无歧义。

命名了概念后，是时候编写代码来消除差异了。

### 3.7.4. 有条理的转换

现在你已经决定创建一个 `container` 方法，是时候更改代码了。人们往往想一次性完成所有更改。这样做需要添加一个新方法并在两个地方调用它。以下是新方法：

**Listing 3.8：猜测整个容器**

```php
public function container(int $number): string {
  if ($number === 1) {
    return "bottle";
  } else {
    return "bottles";
  }
}
```

此方法必须在 `verse` `switch` 语句的两个分支中都被调用。以下是代码：

**Listing 3.9：调用 Container 的代码**

```
($number-1) . " " . $this->container($number-1) .
  " of beer on the wall.\n";
```



等一下。注意，上面的更改增加了七行新代码，更改了两行现有的代码，并修改了三个地方的代码。这些更改中的任何都可能引入错误，导致你不得不理解并纠正这些错误。这个小例子代表了现实生活中规模得得的问题：在实现新功能的过程中，你增加了许多行代码，更改了许多其他代码，然后运行测试，结果面对的是一片通红（失败）。

现实世界的问题是巨大的。真实的代码有 Bug。真实的测试通常与当前的实现紧密耦合。如果你同时更改许多内容导致某些部分坏了，你就被迫理解一切才能修复任何问题。你最终可能会在绝望感不断加剧的情况下追逐红色错误，最后不得不放弃所有更改并重新开始。

同时进行大量更改并不是重构（`refactoring`），而是“重新黑改”（`rehackoring`）。更好的做法是进行一系列微小的更改，并在每次之后运行测试。如果测试失败，你就知道导致失败的确切更改，并可以回滚到绿色（通过）然后进行更好的更改。如果测试通过，你就知道当前代码工作正常，即使重构只完成部分。

正式的重构带来两个额外好处。首先，因为没有一个更改会破坏测试，代码可以在任何中间点部署到生产环境。这允许你避免累积大量的更改并忍受痛苦的合并。接下来，运行正常的代码...

从现在起，不言而喻，你应该在每次更改后运行测试。

既然 `container` 返回的是一个可用的值，请修改 `default` 分支，发送消息来代替单词 "bottles"，如下所示第 11 行所示：

[列表 3.13: 在默认分支中使用的稀疏容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-80/lib/Bottles.php#L15-L47)

```
 1 public function verse(int $number): string {

 2   switch ($number) {

 3   // ...

 4   case 2:

 5     return

 6       // ...

 7       ($number-1) . " bottle of beer on the wall.\n";

 8   default:

 9     return

10       // ...

11       ($number-1) . " " . $this->container() .

12         " of beer on the wall.\n";

13   }

14 }

15 

16 public function container() {

17   return "bottles";

18 }

```

到目前为止一切顺利，但请考虑下一步。为了在 `2` 和 `default` 用例中均可用，`container` 最终必须在 `bottle` 或 `bottles` 之间返回正确的选择。它们之间的决定取决于 `$number` 的值，而 `container` 目前还不知道这个值。因此，必须更改 `container` 以接收一个参数。

就像 `container` 目前没有*接收*参数（如上面的第 16 行）一样，它的调用者目前也没有*发送*参数（第 11 行）。现在你面临着一个困境。目标是一次只修改一行，因此你必须仔细选择下一次更改。

传递一个未被使用的参数是完全合法的，因此将第 11 行更改为：

```
($number-1) . " " . $this->container($number-1) .
```

不会破坏测试。

然而，如果你将第 16 行更改为期望一个尚未传递的参数：

```
public function container($number) {
```

测试将开始失败。

这个问题需要添加一个必要的参数，在现实世界中经常出现。但不像这种情况中只有一个发送者和一个接收者，真实的应用程序可能有 10、100 或 1000 个发送者。可能无法一次修复所有问题，因此了解这种以增量方式解决此问题的技巧非常有帮助。

### 3.7.5. 逐步重构

Joshua Kerievsky 在他的书《重构模式》（Refactoring to Patterns）中讨论了“渐进过渡重构”（Gradual Cutover Refactoring），这是一种通过逐渐切换小部分来保持代码处于可发布状态的策略。这种重构可以与其他开发工作同时进行，而不影响发布进度。如果你采用这种策略，你的同事和客户将感谢你对保持代码可部署承诺。

这种策略意味着你不应该一次更改所有内容。因此，为了进行渐进过渡重构，你必须弄清楚如何允许某些发送者传递新参数而其他保持不变。由于 PHP 函数会忽略它们不认识的参数，你*可以*从定位 `container` 的发送者开始，并逐个将它们更改为传递 `$number`。然而，由于你目前正专注于 `container` 函数的行为，从这里开始更有意义。保持测试绿色通过的诀窍是在添加 `$number` 参数的同时提供一个默认值，如下所示：

[列表 3.14: 带有默认参数的容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-90/lib/Bottles.php#L45-L47)

```
1 public function container($number="FIXME") {

2   return "bottles";

3 }

```

上述代码接受一个名为 `$number` 的参数，其默认值为字符串 `'FIXME'`。你可能期望默认值是 `null`，或者至少是一个数值，但在这种情况下，将其设置为某个有用的错误值是有意义的。`'FIXME'` 既提醒你默认值是临时的，也提醒你参数需要类型声明。一旦重构完成，*应该*移除默认值并指定类型。使用像 `'FIXME'` 这样的值将帮助你记住这两件事。

现在 `container` 方法接受了一个参数，请考虑下一步。你可以：

*   修改 `container` 以检查 `$number` 的值并返回 "bottle" 或 "bottles"，这意味着更改接收者，或者
*   修改 `default` 分支以向 `container` 消息添加 `$number` 参数，这意味着更改发送者。

重构规则禁止你同时进行这两个更改，因此你必须必须二其一。

由于 `container` 方法尚未引用 `$number`，将 `default` 分支更改为传递此参数对代码几乎没有改变。与其传递参数，更好的选择是扩展 `container` 中的代码，使用 `$number` 来决定返回 "bottle" 还是 "bottles"，如下：

[列表 3.15: 带有条件判断的容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-100/lib/Bottles.php#L45-L51)

```
1 public function container($number="FIXME") {
2   if ($number === 1) {
3     return "bottle";
4   } else {
5     return "bottles";
6   
```

关于上述内容有几点注意。首先，注意添加条件是一个多行更改。这似乎违反了“单行”规则，但在这种情况下，多行的 `if` 形式更优，原因将在后面的章节中明确。这个条件可以使用三元运算符表示：

```
return $number === 1 ? "bottle" : "bottles";
```

接下来，记住该方法仅从一个地方调用（`switch` 的 `default` 分支），并且尚未传递参数。这意味着 `$number` 参数被设置为 `'FIXME'`，从而进入执行分支。在执行现有代码的同时添加新分支是开闭原则的一个微型示例。你可以将这种更改视为让 `container` 方法开放——能够偶尔返回单词 "bottle"。

下一个微步骤是更改发送者实际传递新参数。因为 `container` 是从歌曲的第四句调用的，参数的值为 `$number-1`，如下文所示所示：

[列表 3.16: 向容器传递参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-110/lib/Bottles.php#L15-L51)

```
 1 public function verse(int $number): string {

 2   switch ($number) {

 3   // ...

 4   case 2:

 5     return

 6       // ...

 7       ($number-1) . " bottle of beer on the wall.\n";

 8   default:

 9     return

10       // ...

11       ($number-1) . " " . $this->container($number-1) .

12         " of beer on the wall.\n";

13   }

14 }

15 

16 public function container($number="FIXME") {

17   if ($number === 1) {

18     return "bottle";

19   } else {

20     return "bottles";

21   }

22 }

```

上面的步骤看起来可能微到没有意义，但因为 `'FIXME'` 默认值执行 false 分支与因为 `$number` 参数的值路由到那里之间存在真正的区别。在第一种情况下，你知道*如果进入 false 分支*测试会通过；而在第二情况下，你知道*传递的参数带你进入了 false 分支*。这两者必须正常工作，否则测试就会崩溃。在这种粒度上更改代码使得处理意外失败变得更容易。

下一步是修改 `2` 分支，使其也调用容器方法，如下所示第 8 行和第 9 行：

[列表 3.17：相同的 2 情况和默认情况](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-120/lib/Bottles.php#L15-L52)

```
 1 public function verse(int $number): string {

 2   // ...

 3   case 2:

 4     return

 5       $number . " bottles of beer on the wall, " .

 6       $number . " bottles of beer.\n" .

 7       "Take one down and pass it around, " .

 8       ($number-1) . " " . $this->container($number-1) .

 9         " of beer on the wall.\n";

10   default:

11     return

12       $number . " bottles of beer on the wall, " .

13       $number . " bottles of beer.\n" .

14       "Take one down and pass it around, " .

15       ($number-1) . " " . $this->container($number-1) .

16         "of beer on the wall.\n";

 17   }

 18 }

19 

20 public function container($number="FIXME") {

 21   if ($number === 1) {

 22     return "bottle";

 23   } else {

 24     return "bottles";

 25   }

 26 }

```

上述更改有两个结果。首先，`container` 中的所有代码现在都在执行。接下来，`verse` 语句中 `2` 和默认分支的代码现在是完全相同的。

完成这整个水平重构还剩余两个任务。首先，由于所有 `container` 的调用者现在都传递了 `$number`，`'FIXME'` 默认值已经完成了它的使命。可以将其删除，并更新方法签名以包含类型声明。接下来，`2` 情况现在已经过时了，因此也可以删除。以下示例展示了重构后的代码：

[列表 3.18：2 合并入默认情况](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-140/lib/Bottles.php#L15-L45)

```
 1 public function verse(int $number): string {

 2   switch ($number) {

 3   case 0:

 4     return

 5       "No more bottles of beer on the wall, " .

 6       "no more bottles of beer.\n" .

 7       "Go to the store and buy some more, " .

 8       "99 bottles of beer on the wall.\n";

 9   case 1:

10     return

11       "1 bottle of beer on the wall, " .

12       "1 bottle of beer.\n" .

 13       "Take it down and pass it around, " .

14       "no more bottles of beer on the wall.\n";

 15   default:

16     return

17       $number . " bottles of beer on the wall, " .

18       $number . " bottles of beer.\n" .

19       "Take one down and pass it around, " .

20       ($number-1) . " " . $this->container($number-1) .

21         "of beer on the wall.\n";

 22   }

 23 }

 24 

25 public function container(int $number): string {

 26   if ($number === 1) {

 27     return "bottle";

 28   } else {

 29     return "bottles";

30   }

31 }

```

这种水平重构需要大量的解释。以下是关键动作的回顾：

1. 识别出 `verse` 中的 `2` 和默认情况是最相似的。
2. 从左到右工作。
3. 将 `verse` `2` 情况中硬编码的 `2` 替换为 `$number`（两次）。
4. 将 `verse` `2` 情况中硬编码的 `1` 替换为 `$number-1`。
5. 识别出 "bottle" 和 "bottles" 是差异所在。
6. 为该差异代表的概念命名为 `container`。
7. 创建空的 `container` 方法。
8. 将 `container` 修改为返回 "bottles"。
9. 将 `verse` 默认情况修改为发送 `container` 以替换 "bottles"。
10. 将 `container` 修改为接受带有 `'FIXME'` 的默认参数。
11. 在 `container` 中添加条件逻辑，根据 `$number` 返回 "bottle" 或 "bottles"。
12. 将 `verse` 默认情况修改为传递 `$number-1` 给 `$this->container()`。
13. 将 `verse` `2` 情况修改为发送 `$this->container($number-1)` 以替换 "bottle"。
14. 删除 `verse` `2` 情况。
15. 删除 `container` 的 `'number'` 参数。

在这 15 步中，有 12 步涉及代码更改。每次更改后都会运行测试，因此修复新引入的问题轻而易举。

上述冗长的描述可能会让你担心这种工作方式会非常慢。再看一遍，可以看到代码并不多，通过练习，编写会变得非常快。在增量更改上花费的少量时间，远比避免冗长且沮丧的调试所的回报。这种编码风格不仅快速，而且没有压力。

`1` 情况与 `default` 情况有几处不同。它使用一个硬编码的 `1` 作为起始数字，递减时使用的是 `"it"` 而不是 `"one"`，并且以 `"no more"` 结尾，而不是 `$number-1` 瓶。

`0` 情况甚至与 `default` 情况更加不同。它以 `"No more"` 开头，说的是 `"Go to the store and buy some more"`，并以 `"99"` 结尾。

最后，`1` 情况和 `0` 情况之间也有许多不同之处。与彼此相比，它们与 `default` 情况的共同点反而更多。

在这三个诗歌（verse）模板中，`1` 情况和 `default` 情况最相似，因此它们是下一个要处理的。先从观察每个模板的第一行开始：

[Listing 4.2: 1 和 Default 第一句的差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-140/lib/Bottles.php#L23-L31)



`1` 情况与 `default` 情况有几处不同。它使用一个硬编码的 `1` 作为起始数字，递减时使用的是 `"it"` 而不是 `"one"`，并且以 `"no more"` 结尾，而不是 `$number-1` 瓶。

`0` 情况甚至与 `default` 情况更加不同。它以 `"No more"` 开头，说的是 `"Go to the store and buy some more"`，并以 `"99"` 结尾。

最后，`1` 情况和 `0` 情况之间也有许多不同之处。与彼此相比，它们与 `default` 情况的共同点反而更多。

在这三个诗歌模板中，`1` 情况和 `default` 情况最相似，因此它们是下一个要处理的。先从观察每个模板的第一行开始：

[Listing 4.2: 1 和 Default 第一句的差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c3-flocking-140/lib/Bottles.php#L23-L31)

```
1 case 1:
2   return
3     "1 bottle of beer on the wall, " .
4     // ...
5 default:
6   return
7     $number . " bottles of beer on the wall, " .
8     // ...
```

与 `2` 情况和 `default` 情况一样，第一个字符也是不同的。通过在 `1` 情况中使用 `$number` 代替硬编码的 `1` 来消除这种差异，如下所示：

[Listing 4.3: 进展中的 1 和 Default 第一句](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-10/lib/Bottles.php#L23-L31)

```
1 case 1:
2   return
3     $number . " bottle of beer on the wall, " .
4     // ...
5 default:
6   return
7     $number . " bottles of beer on the wall, " .
8     // ...
```

在上一章中也进行过类似的修改，在合并 `2` 情况和 `default` 情况时，将硬编码的 `"2"` 替换为了 `$number`。这种用变量替换显式数字的行为是非常微小的，以至于无法充分反映其底层思想的宏大，但请后退一步考虑一下刚刚发生了什么。将不同的具体值替换为对公共变量的引用，将*差异*转化为了*相同*。

已知参数等于 `1` 这一事实并不重要。这种替换很重要，并不是因为改变了结果的值，而是因为增加了抽象层级。正是这种抽象层次的提升使得事物变得相同。如果没有它，你注定会陷入条件判断的泥。

下一个差异是“bottle”与“bottles”。这恰好是之前确定的“容器（container）”概念。每一行都已更改为发送 `container` 消息，结果如下所示：

```
1 case 1:
2   return
3     $number . " " . $this->container($number) .
4       "of beer on the wall, " .
5     // ...
6   return
7     $number . " " . $this->container($number) .
8       " of beer on the wall, " .
9     ...
```

第一句现在是完全相同的。每个情况的第二句与第一句非常相似，正如你在这里看到的：

[Listing 4.5: 1 和 Default 第二句的差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-20/lib/Bottles.php#L23-L34)

```
1 case 1:
2   return
3     $number . " " . $this->container($number) .
4       "of beer on the wall, " .
5     // ...
6   return
7     $number . " " . $this->container($number) .
8       " of beer on the wall, " .
9     ...
```



## 重构 99 Bottles：消除重复与提升抽象

### 初始代码对比

```php
1 case 1:
2   return
3     $number . " bottle of beer on the wall, " .
4     // ...
5 default:
6   return
7     $number . " bottles of beer on the wall, " .
8     // ...
```

### 核心重构思想：将差异转化为相同

在上一章中也进行过类似的修改，在合并 `2` 情况和 `default` 情况时，将硬编码的 `"2"` 替换为了 `$number`。这种用变量替换显式数字的行为是非常微小的，以至于无法充分反映其底层思想的宏大，但请后退一步考虑一下刚刚发生了什么。将不同的具体值替换为对公共变量的引用，将**差异**转化为了**相同**。

已知参数等于 `1` 这一事实并不重要。这种替换很重要，并不是因为改变了结果的值，而是因为**增加了抽象层级**。正是这种抽象层次的提升使得事物变得相同。如果没有它，你注定会陷入条件判断的泥潭。

### 消除 "bottle" 与 "bottles" 的差异

下一个差异是“bottle”与“bottles”。这恰好是之前确定的“容器（container）”概念。每一行都已更改为发送 `container` 消息，结果如下所示：

```php
1 case 1:
2   return
3     $number . " " . $this->container($number) .
4       "of beer on the wall, " .
5     // ...
6   return
7     $number . " " . $this->container($number) .
8       " of beer on the wall, " .
9     ...
```

第一句现在是完全相同的。每个情况的第二句与第一句非常相似，正如你在这里看到的：

[Listing 4.5: 1 和 Default 第二句的差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-20/lib/Bottles.php#L23-L34)

```php
1 case 1:
2   return
3     $number . " " . $this->container($number) .
4       "of beer on the wall, " .
5     // ...
6   return
7     $number . " " . $this->container($number) .
8       " of beer on the wall, " .
9     ...
```

---

### 处理 "it" 与 "one"：引入 `pronoun` 方法

最后，与其自己独自尝试执行上述两种策略之一，你完全可以向他人寻求帮助。在任何程序员小组中，通常都有人擅长命名。如果你的小组中有这样的人，你很清楚他们是谁。任命他们为“命名大师（name guru）”，并在需要命名时利用他们的长处。

在“99 Bottles”中处理 `"it"` 或 `"one"` 的情况下，目前 `pronoun` 就足够了。如果以后出现了更好的方案，你随时可以改进这个名称。

将 `"it"` 和 `"one"` 转换为 `pronoun` 的过程与将 "bottle" 和 "bottles" 转换为 `container` 的过程相同。由于之前已经练习过，接下来的这次重构将非常快。下面的示例演示了转换过程。记住在每次更改后都运行测试。

#### 步骤 1：定义空的 `pronoun` 方法

[Listing 4.8：空 Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-40/lib/Bottles.php#L49-L50)

```php
1 public function pronoun() {
2 }
```

#### 步骤 2：修改 `pronoun` 返回 `default` 分支的值 "one"

[Listing 4.9：稀疏 Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-50/lib/Bottles.php#L49-L51)

```php
1 public function pronoun() {
2   return "one";
3 }
```

#### 步骤 3：修改 `default` 分支使用 `pronoun`

[Listing 4.10：在默认分支中发送 Pronoun](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-60/lib/Bottles.php#L23-L35)

```php
 1 case 1:
 2   return
 3     // ...
 4     "Take it down and pass it around, " .
 5     // ...
 6 default:
 7   return
 8     // ...
 9     "Take " . $this->pronoun() . " down and pass it around, " .
10     // ...
```

#### 步骤 4：为 `pronoun` 添加带默认值的参数

[Listing 4.11：带默认参数的 Pronoun](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-70/lib/Bottles.php#L49-L51)

```php
1 public function pronoun($number="FIXME") {
2   return "one";
3 }
```

#### 步骤 5：修改 `pronoun` 处理 `1` 的情况

[Listing 4.12：带条件的 Pronoun](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-80/lib/Bottles.php#L49-L55)

```php
1 public function pronoun($number="FIXME") {
2   if ($number === 1) {
3     return "it";
4   } else {
5     return "one";
6   }
7 }
```

#### 步骤 6：修改 `default` 分支传递 `$number` 参数

[Listing 4.13：向 Pronoun 传参](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-90/lib/Bottles.php#L23-L35)

```php
 1 case 1:
 2   return
 3     // ...
 4     "Take it down and pass it around, " .
 5     // ...
 6 default:
 7   return
 8     // ...
 9     "Take " . $this->pronoun($number) . " down and pass it around, " .
10     // ...
```

#### 步骤 7：修改 `1` 分支使用 `$this->pronoun($number)`

[Listing 4.14：1 和默认分支发送 Pronoun](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-100/lib/Bottles.php#L23-L35)

```php
 1 case 1:
 2   return
 3     // ...
 4     "Take " . $this->pronoun($number) . " down and pass it around, " .
 5     // ...
 6 default:
 7   return
 8     // ...
 9     "Take " . $this->pronoun($number) . " down and pass it around, " .
10     // ...
```

#### 步骤 8：清理 `pronoun` 方法，移除 `'FIXME'` 并添加类型声明

```php
1 public function pronoun($number="FIXME") {
2   if ($number === 1) {
3     return "it";
4   } else {
5     return "one";
6   }
7 }
```

---

## 4.3. 从职责命名

尽管 `pronoun` 可能显得太泛，但它代表的概念是清晰的。如果你必须描述其底层思想，可能会说：“`pronoun` 消息返回了在每段歌第三句中，紧跟 ‘Take’ 之后替代名词 ‘bottles’ 的单词。”尽管这种解释很刻板，但它是完全正确的。这就是 `pronoun` 的职责。

命名 `pronoun` 的困难说明了即使在理解概念时，选择一个名称是多么困难。想象一下，当你不理解概念时，选择名称又是多么不可能。下一节将处理第四个也是最后一个短语。

你确实可以将这个概念命名为“剩余数”（remainder），并继续重构。然而，为了少受一些痛苦，请稍微向前看一眼。你很快就会考虑到 `0` 的情况，该情况如下：

```
No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall.
```

注意，`0` 情况以 `"No more"` 开头，就像 `1` 情况以 `"no more"` 结尾一样。这首歌的逻辑是：每当剩下 `0` 瓶酒时，你就唱 "no more"，并根据情况进行大写。

当 `"No more"` 出现在歌曲开头时，它显然不是剩余数。这意味着如果 `"no more"` 和 `"No more"` 代表同一个意思，那么 `remainder` 就不是这个底层概念的好名字。

如果你重新考虑上面的表格，右侧实际上是所歌唱的瓶子的“名称”（name）、或“描述”（description），或者可能是“数量”（quantity）。它是要在任何数字出现的地方被唱出的字符串。虽然不完美，但 `quantity` 至少试图指示你计划创建的方法所承担的责任，因此是一个合理的命名首选尝试。

在实现 `quantity` 之前，考虑一下如果你将这个概念命名为 `remainder` 会发生什么。在完成 `1` 情况后，你会进展到 `0` 情况，并发现它是以 `"No more"` 开头的。这将导致你重新考虑 `remainder`。你可能会将重构回溯到这一点，并重新寻找名字。

现实生活就是这样，你会在当时做出所能的最优决定，并在了解更多信息时重新评估。如果你是独自进行这次重构，你很可能会走上 `remainder` 的道路，并遭受最终的推倒重来。由于现实中的痛苦已经足够多了，这里就把这种痛苦留给你去想象吧。

不要把这看作是长远思考的普遍许可。虽然你可以使用常识，但通常最好的做法是保持水平思维，专注于当前目标。在创建抽象时，首先根据你目前对它的理解来描述描述的责任，然后选择一个反映该责任的名字。你现在在选择好名字上付出的努力，将通过让以后更容易识别完美的名字来获得回报。

---

## 4.4. 选择有意义的默认值

之前的几次重构使用了临时将参数设置为默认值的技巧。在每种情况下，字符串 `'FIXME'` 都被用作默认值。`'FIXME'` 非常方便，因为这个名字本身就会提醒你它的临时性，并作为在重构结束时删除它的提醒。尽管 `'FIXME'` 很有用，但遗憾的是它在所有情况下都不起作用。有时，情况会迫使你在这些重构期间不得不使用一个真实值作为默认值。下一节将深入探讨此类情况。

记住当前正在解决的差异是：

```
"no more"
```

它对应：

```
$number-1
```

底层概念是 `quantity`。为了消除这种差异，首先添加 `quantity` 方法：

[Listing 4.16: 初始数量方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-120/lib/Bottles.php#L41-L2)

```php
1 public function quantity() {
2 }
```

下一步是将此方法更改为返回这两个差异中的一个。到目前为止，你选择返回 `default` 分支的值。但在这种情况下，`default` 分支包含了引用 `$number` 的代码。因此，除非你先修改 `quantity` 将 `$number` 作为参数，否则你不会将 `default` 分支复制到 `quantity`。



`1` 分支包含字符串 "no more"，这是一个更简单的差异。这种简单性使得这里成为探索如果切换顺序并先返回非 `else` 值会发生什么的好地方。由于这种策略的改变，完全按照你所做的方法进行最终会导致错误。观察这种错误的发生很有启发性，如下面的代码所示。

开始从 `1` 情况返回值：

[Listing 4.17: 数量方法返回](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-130/lib/Bottles.php#L41-L3)

```
public function quantity() {
  return "no more";
}
```

在 `1` 情况中用 `quantity` 替换 `"no more"`：

[Listing 4.18: 发送数量消息](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-140/lib/Bottles.php#L23-L30)

```
case 1:
  return
    // ...
    $quantity() . " bottles of beer on the wall.";
default:
```

在 `default` 分支中为 `quantity` 添加 `$number`：

[Listing 4.19: 默认值为数量](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-140/lib/Bottles.php#L41-L43)

```
public function quantity($number="FIXME") {
   return "no more";
}
```

在 `quantity` 中添加 `'FIXME'` 默认值：

[Listing 4.20: 带条件判断的数量](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-150/lib/Bottles.php#L41-L47)

```
public function quantity($number="FIXME") {
   if ($number === 0) {
     return "no more";
   } else {
     return $number;
   }
}
```

如果你现在对这段代码有顾虑，请坚持住。问题将会出现，但很快就会解决。

在之前的重构中，每种情况下测试都通过了，但在这种情况下并非如此。测试现在报错了：

```
-Take it down and pass it around, no more bottles of beer on the wall.
+Take it down and pass it around, FIXME bottles of beer.
```

查看下面的 switch 语句。检查第 4 行并尝试解释哪里错了。

[Listing 4.21: 使用来自 1 情况的数量默认值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-160/lib/Bottles.php#L23-L37)

```
case 1:
  return
    // ...
    $quantity() . " bottles of beer on the wall.";
default:
  return
    // ...
    ($number-1) . " " . $container($number-1) .
      " of beer on the wall.";
```

这种失败发生是因为上面的第 4 行调用 `quantity` 时没有传递参数。调用时，`quantity` 方法将 `$number` 设置为 `'FIXME'`，这导致执行跳转到判断条件的假分支。假分支顺从地返回了 `$number`，但遗憾的是它仍然包含 `'FIXME'`。这个结果随后被用于歌词中。因此，变成了 "FIXME bottles of beer"。

'FIXME' 默认值在之前的情况下有效是因为在那些情况下你*想要*执行假分支。但现在你需要真分支，因此需要更具体的默认值。

测试失败了，规则要求你撤销并返回绿色状态。幸运的是，这只需要一次撤销，即可将 `quantity` 恢复如下：

[Listing 4.22: 默认值为 FIXME 的数量参数回归](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-170/lib/Bottles.php#L41-L43)

```
public function quantity($number="FIXME") {
   return "no more";
}
```

# 使用默认值

一个像 `'FIXME'` 这样明显错误且临时的值可以作为一个方便的默认值，但只有当你开始重构时是从返回 `default` 分支的差异开始，才能使用这种技术。虽然通过返回“no more”（非 `default` 分支的差异）开始是完全可以的，但这意味着你必须更仔细地考虑默认值。因此，请审慎地使用像 `'FIXME'` 这样的默认值。

在这种情况下，驱动执行到正确分支的默认值是 `0`，如下所示：

[Listing 4.23: 数字参数默认为 0](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-180/lib/Bottles.php#L41-L43)

```
public function quantity($number=0) {
  return "no more";
}
```

现在默认值是正确的，可以将条件判断如下所示重新添加到 `quantity` 中：

[Listing 4.24: 默认值进入真分支](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-190/lib/Bottles.php#L41-L47)

```
public function quantity($number=0) {
  if ($number === 0) {
    return "no more";
  } else {
    return $number;
  }
}
```

尽管自上次尝试以来条件判断没有发生变化，但现在默认值是正确的，因此测试通过了。

使用默认值导致了 `true` 分支的执行。现在是确保传递参数也能同样的效果。下面的第 4 行已更改为向 `quantity` 传递 `$number-1`：

[Listing 4.25: 情况 1 传递参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-200/lib/Bottles.php#L23-L38)

```
case 1:
  return
          ...
    $this->quantity($number-1) . " bottles of beer on the wall.\n";
default:
  return
    $number . " " . $this->container($number) .
    // ...
      " of beer on the wall.\n";
}
```

测试仍然通过。下一步是在 `default` 情况中使用 `quantity`，如下如下面的第 9 行所示：

[Listing 4.26: 默认情况发送数量](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-210/lib/Bottles.php#L23-L38)

```
case 1:
  return
    // ...
    $this->quantity($number-1) . " bottles of beer on the wall.\n";
default:
  return
    // ...
    $this->quantity($number-1) . " " . $this->container($number-1) .
      " of beer on the wall.\n";
}
```

此时，`quantity` 已经完全实现。默认值不再需要，可以删除了。最终的方法所示：

[Listing 4.27: quantity 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-220/lib/Bottles.php#L41-L47)

```
public function quantity(int $number): string {
  if ($number === 0) {
    return "no more";
  } else {
    return $number;
  }
}
```

在解决了 `quantity` 后，`1` 情况和 `default` 情况之间存在一个微小的差异。`1` 情况的最后一个短语是 `"bottles"`（下面的第 4 行），而在该位置 `default` 情况发送的是 `$this->container($number-1)`。

[Listing 4.28: 情况 1 和默认情况更加相似](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-220/lib/Bottles.php#L23-L38)

```
case 1:
  return
    // ...
    $this->quantity($number-1) . " bottles of beer on the wall.\n";
default:
  return
    // ...
    $this->quantity($number-1) . " " . $this->container($number-1) .
      " of beer on the wall.\n";
```

可以通过发送熟悉的 `container` 消息代替单词 `"bottles"` 来解决此差异。更改后，`1` 情况和 `default` 情况完全相同，其完整面貌所示：

[Listing 4.29: 情况 1 和默认情况一致](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-230/lib/Bottles.php#L15-L40)

```
public function quantity(int $number): string {
  if ($number === 0) {
    return "no more";
  } else {
    return $number;
  }
}
```

### 4.5 寻找着陆点

此时，`2` 情况和 `1` 情况已被移除，并识别出了三个新概念：`quantity`、`pronoun` 和 `container`。为了方便记忆，下面的列表重复了这些概念的代码：

[Listing 4.30: 抽象的概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-240/lib/Bottles.php#L34-L56)

```
public function quantity(int $number): string {
  if ($number === 0) {
    return "no more";
  } else {
    return $number;
  }
}

public function container(int $number): string {
  if ($number === 1) {
    return "bottle";
  } else {
    return "bottles";
  }
}

public function pronoun(int $number): string {
  if ($number === 1) {
    return "it";
  } else {
    return "one";
  }
}
```

想象你是一个孩子，在小溪边漫步，在石头一块块之间跳跃。有些石头宽大、平坦且干燥，有些则长满苔藓、摇摇晃晃且湿滑。再想象你不被允许湿着回家。

干燥的石头是稳定的着陆点，你可以在上面安全地休息，规划下一步行动。湿滑的石头是有风险的间隙，常识建议你尽快穿过它们。

重构代码就像在溪流中跳石。如果你遵循重构规则，你将很快跳过那些湿滑的地方，到达稳定、一致的休息点。然而，随心所欲地更改代码可能会导致意外和意料之外的“落水”。

上述代码的一致性为下一次重构提供了可能。目前，你必须相信这种判断，但这种信任将在未来的章节中获得回报。

### 4.6 遵守里氏夫替换原则

现在，回到水平重构。本章从一个三分支的 `switch` 语句开始。其中一个情况（`1` 情况）已被移除，留下了 `0` 和 `default` 情况待解决。以下是代码当前状态的提醒：

[Listing 4.31: 0 和 Default 情况不同](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-240/lib/Bottles.php#L15-L32)

```
public function verse(int $number): string {
  switch ($number) {
  case 0:
    return
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";
  default:
    return
      $number . " " . $this->container($number) .
        "of beer on the wall, " .
      $number . " " . $this->container($number) . " of beer.\n" .
      "Take " . $this->pronoun($number) . " down and pass it around, " .
      $this->quantity($number-1) . " " . $this->container($number-1) .
        "of beer on the wall.\n";
  }
}
```

开始下一次重构，重点关注上述第 5 行和第 11-12 行，即两个剩余情况的第一个短语。寻找最小差异，两行都以 `"of beer on the wall, "` 结尾，因此这是一个可以忽略的相似之处。`container` 方法用于 `default` 情况中的第 11 行。第 5 行的单词 `"bottles"` 是一个 `container`，因此 "bottles" 不是下一个差异的一部分。

剩余的差异位于第 5 行和第 11 行的最开头，即：

```
"No more"
```

对应：

```
$number
```

这感觉像是 `quantity` 概念，但目前来看，该方法无法无法解决这一差异。如果你将第 5 行更改为调用 `$this->quantity($number)` 来代替 `"No more"`，你将得到全小写的 "no more"，而测试将会失败。

这是一个困境。第 1 节需要小写形式 "no more"，而现在第 0 节也需要这两个词，只是作为句首需要字母大写。这两种情况的底层概念是相同的（当瓶子数量为 0 时唱道 "no more"），但根据它们在歌曲中的位置，表达方式略有不同。

这些词是一回事，而它们是否需要大写是另一回事。也许词汇的知识属于一个地方，而大写要求的知识属于另一个地方。

如果是这样，大写可以合理地在 `switch` 语句中进行。将 `"No more"` 替换为 `$this->quantity($number)` 并对结果进行大写，如下方的第 3 行所示：

[Listing 4.32: 0 情况下的数量大写](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-250/lib/Bottles.php#L17-L27)



上述更改遵循了逐渐使事物变得相似的策略，希望随后就能清楚如何让它们变得完全相同。在细化解决问题时，你不需要在做任何事情之前理解一切。处理好细节往往会让大问题迎刃而解。

完成上述更改后，显而易见的下一步是在 `default` 情况中进行类似的操作，如下方的第 8 行所示：

[Listing 4.33: Default 情况下的数量大写](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-230/lib/Bottles.php#L17-L27)

```
case 0:
  return
    ucfirst($this->quantity($number)) . " bottles" .
      "of beer on the wall, " .
    // ...
default:
  return
    $number . " " . $this->container($number) .
      "of beer on the wall,
```

（注：原文末尾存在大量重复内容，此处已按核心逻辑完成翻译。）

```
case 0:
  return
    ucfirst((string)$this->quantity($number)) . " bottles" .
      "of beer on the wall, " .
    // ...
  return
    ucfirst((string)$this->quantity($number)) . " " . $this->container($number) .
      "of beer on the wall, " .
    // ...
```

现在差异已经解决且测试正在运行，请退后一步考虑这个解决方案。问题的根源在于 `quantity` 返回了符合不同 API 的内容。`quantity` 的发送者期望可以直接将结果传递给 `ucfirst`，但这并不总是有效。不一致的返回类型迫使消息的*发送者*了解比它应该知道的更多。

上面的 `verse` 方法知道 `ucfirst` 需要一个字符串，知道 `quantity` 不可信赖会返回字符串，并且知道可以通过 `(string)` 将 `quantity` 返回的值转换为字符串。

每一项知识都是一个依赖，而 `quantity` 的写法要求 `verse` 了解过多的事情。如果 `quantity` 更加可信赖，`verse` 就可以少知道一些。

通过要求接收者返回可信赖的对象来减少施加在消息发送者身上的依赖，这种想法是里可夫替换原则的推广。里可夫的官方定义是：“子类型必须能够替换其超类型”。该原则最初是从类型和子类型的角度提出的，但你可以从更广泛的角度来考虑它。

用简单的话说，里可夫要求对象符合它们所承诺的。在使用继承时，你必须能够自由地用子类的实例替换其父类的实例。根据定义，子类包含了其父类的所有内容，*以及更多*，因此这种替换应该始终有效的。

里可夫禁止你执行任何迫使消息发送者测试返回结果以知道如何行为的操作。接收者与发送者之间有合约，尽管在动态类型对象型语言中这种合约具有隐性，但它必须被履行。

违反里可夫原则会迫使消息发送者了解各种返回类型，要么以不同方式处理它们，要么将它们转换为一致的内容。在上面的 `quantity` 方法中，一个返回遵循了“可大写”合约，而另一个没有。这种不一致性通常会迫使发送者实现一个条件判断来识别并修复错误的返回。在这种情况下，几乎所有的 PHP 对象都理解 `(string)`，因此在程序上很方便地无所谓地将每个返回转换为字符串，即使是那些已经是字符串的内容。这种无条件的转换避免了检查哪些值需要转换为 `(string)`，但增加了尝试将已经是字符串的内容再次转换为字符串的开销。

如果接收者履行了合约并提供了一致的返回，发送者的整个负担就消失了。与其强迫 `verse` 方法解决这个问题，不如 `quantity` 应该返回一个可信赖的值。

通过在 `quantity` 方法中进行转换可以轻松实现这一点，如下所示第 5 行所示：

[Listing 4.37: 遵循里可夫原则](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-290/lib/Bottles.php#L37-43)

```
public function quantity(int $number): string {
   if ($number === 0) {
     return "no more";
   } else {
     return (string)$number;
   }
}
```

现在 `quantity` 总是返回字符串，你可以假装 `verse` 中从未存在过 `(string)` 依赖，使代码恢复到此处的状态：

[Listing 4.38: 是可信赖的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-300/lib/Bottles.php#L19-29)

```
case 0:
  return
    ucfirst($this->quantity($number)) . " bottles" .
      " of beer on the wall, " .
    // ...
default:
  return
    ucfirst($this->quantity($number)) . " " . $this->container($number) .
      " of beer on the wall, " .
    ...
```

在修改了 `quantity` 使其在所有情况下可用后，第一个短句中剩余的差异是单词 "bottles"。这通过发送 `container` 来替它可以轻松解决：

[Listing 4.39: 0 情况的容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-310/lib/Bottles.php#L19-29)

```
case 0:
  return
    ucfirst($this->quantity($number)) . " " . $this->container($number) .
      " of beer on the wall, " .
    // ...
default:
  return
    ucfirst($this->quantity($number)) . " " . $this->container($number) .
      " of beer on the wall, " .
    ...
```

在该修改之后，`0` 情况和 `default` 情况第一个短句是相同的。

### 4.7. 迈出更大的步

你现在已经多次将小差异转换为消息发送，并且可能已经注意到所采取步骤与生成的代码之间的相似性。到为止，提取出的方法具有相同的形状，并以相同的方式被调用。

差异仍然存在。然而，开始感觉有一种通用的重构模式，人们可以合理地推论未来的差异将遵循过去使用的相同过程来解决。如果这个理论是正确的，那么通过将多个步骤合并为一次更改来加速下一次重构是有意义的。

`0` 和 `default` 情况的第一个短句是相同的，所以是时候检查第二个了。它在下方重复出现：

[Listing 4.40: 0 和 Default 的第二个差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-310/lib/Bottles.php#L19-30)

```
case 0:
  return
    // ...
    "no more bottles of beer.\n" .
    // ...
default:
  return
    // ...
    $number . " " . $this->container($number) . " of beer.\n"
    
```

上面的差异反映了 `quantity` 和 `container` 概念，这些概念早已识别出来。通过如下方式更改代码来解决它们：

[Listing 4.41: 第二个短句：数量与容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-330/lib/Bottles.php#L19-30)

```
case 0:
  return
    // ...
    $this->quantity($number) . " " . $this->container($number) . " of beer.\n"
    // ...
default:
  return
    // ...
    $this->quantity($number) . " " . $this->container($number) . " of beer.\n"
    
```

现在短句 1 和 2 是相同的，这里是整个 `verse` 方法。考虑代码，并识别下一个差异：

[Listing 4.42: 短句 1 和 2 是相同的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-330/lib/Bottles.php#L17-35)

```
public function verse(int $number): string {
   switch ($number) {
3   case 0:
4     return
5       ucfirst($this->quantity($number)) . " " . $this->container($number) .
6         " of beer on the wall, " .
7       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
8       "Go to the store and buy some more, " .
9       "99 bottles of beer on the wall.\n";
10  default:
11     return
12       ucfirst($this->quantity($number)) . " " . $this->container($number) .
13         " of beer on the wall, " .
14       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
15       "Take " . $this->pronoun($number) . " down and pass it around, " .
16       $this->quantity($number-1) . " " . $this->container($number-1) .
17         " of beer on the wall.\n";
18  }
19 }
```

为了找到下一个差异，再次从结尾反向扫描 verse 可能会帮助。两种变体都以 "of beer on the wall." 结束。在第 9 行，情况 `0` 的第四个短句以 "99" 开跟着 "bottles"。这些似乎与第 16 行的 `quantity` 和 `container` 相匹配。暂时忽略这个四个短句，将注意力转向第三个短句，如下所示：

[Listing 4.43: 0 和默认第三句句的差异](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-330/lib/Bottles.php#L19-L31)

```
case 0:
  return
    // ...
    "Go to the store and buy some more, " .
    // ...
default:
  return
    // ...
    "Take " . $this->pronoun($number) . " down and pass it around, " .
    // ...
```

上述行的共同点在于末尾的 `", "`，这意味着在这一点点之前的所有内容都是差异。如果 `0` 和 `default` 诗句变体反映了一个共同的诗句抽象，那么这个差异必须代表该较大抽象内部的一个更小的概念。这些字符串有多长并不重要——它们在这里的对立存在，意味着它们反映了单一的概念。

你必须为这个概念命名，创建一个方法来表示它，然后用一个消息发送替换这个差异。因此，第一步是为这两个短句所所属的具体示例的分类命名。

歌曲的这部分是关于当前啤酒数量所产生的结果。如果还有啤酒，你就喝一瓶。如果没有，你就去购物。这些行描述了要采取的 `action`（动作），所以这是该概念的一个好名字。

目前为止，你一直在以最小的步骤进行这种重构。提醒一下，这些步骤是：

*   为该概念定义一个方法。
*   修改它以返回其中一个差异。
*   用消息发送替换该差异。
*   向新方法添加 `$number` 参数，并带有相应的默认值。
*   实现条件判断。
*   从当前发送者传递 `$number` 参数。
*   从另一个分支发送消息，这次包含 `$number` 参数。
*   清理。

你可能已经注意到，你在这次重构期间创建的方法所包含的代码，与原始 `switch` 语句的形状完全镜像。一旦这一点变得显而易见，开始在一步中提取出方法就有意义了，如下所示：

[Listing 4.44: 采取行动](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-340/lib/Bottles.php#L53-L59)

```
public function action(int $number): string {
2   if ($number === 0) {
3     return "Go to the store and buy some more";
4   } else {
5     return "Take " . $this->pronoun($number) . " down and pass it around";
6   }
7 }
```

这个新的 `action` 方法包含一个反映其来源 `switch` 语句的条件。就像原始的 `switch` 语句对 `$number` 进行切换一样，新的 `action` 方法接收 `$number` 参数，并使用其值来选择返回的内容。新条件的 `true` 和 `false` 分支包含了直接从 `switch` 语句的 `0` 和 `default` 分支提取的代码。

一旦 `action` 存在，就可以通过用共同的消息发送替换它们的差异，使原始短句变得相同。这产生了以下代码：

[Listing 4.45: 第三句发送动作](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-350/lib/Bottles.php#L19-L31)

```
case 0:
  return
    // ...
    $this->action($number) . ", " .
    // ...
default:
  return
    // ...
    $this->action($number) . ", " .
    // ...
```

上一章展示了一个整个容器方法一次性创建的例子。那被作为一个*不应该* 做的示例。上面的 `action` 方法看起来非常像原始的 `container` 方法，似乎你现在被允许以那种方式行动了。

### 4. 发现更深层的抽象

到目前为止，`container`、`pronoun` 和 `action` 概念已经被识别，方法也已经提取出来。本节解决了 `switch` 语句。

The you the the the the the the is the a.

剩余的差异在 `0` 和 `default` 情况中，如下所示：

[Listing 4.46: 短句 1, 3 相同](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-350/lib/Bottles.php#L17-L35)



## 代码示例

```php
1 function verse(int $number): string {
2   switch ($number) {
3   case 0:
4     return
5       ucfirst($this->action($number)) . ", " .
6       $this->quantity($number) . " " .
7       "bottles of the wall.\n";
8


10 default:
11     return
12       ucfirst($this->action($number)) . ", " .
13       $this->quantity($number) . " " .
14       "bottles of the wall.\n";
15   }
16 }
```

上述行末尾的 `"of the wall"` 是相同性，第 9 行的 `"bottles"` 是 `container` 抽象的一个示例，该抽象已用于第 16 行。如果你现在忽略这些，剩余的差异是

```
"99"
```

相对于：

```
$this->quantity($number-1)
```

这可能会让你得出 `"99"` 是 `quantity` 抽象的第三个示例。如果是这样，这意味着你应该修改 `quantity` 以有时返回 `"99"`。生成的方法看起来如下：

### Listing 4.47: 数量过度处理了 99

```php
1 public function quantity(int $number): string {
2   switch ($number) {
3   case -1:
4     return '99';
5   case 0:
6     return 'no more';
7   default:
8     return (string)$number;
9   }
10 }
```

如果你进行了上述修改，然后用 `$this->quantity($number-1)` 替换 `"99"`，测试将继续通过。然而，测试通过并不意味着抽象是正确的。这个解决方案存在深层次的问题，并且有很多关于该问题的线索。

第一个线索是，上述更改使得 `quantity` 的形状与其他提取的方法不同。这里回顾一下在这些修改之前这些方法的模样：

### Listing 4.48: 一致的抽象

```php
public function quantity(int $number): string {
  if ($number === 0) {
    return "no more";
  } else {
    return (string)$number;
  }
}

public function container(int $number): string {
  if ($number === 1) {
    return "bottle";
  } else {
    return "bottles";
  }
}

public function action(int $number): string {
  if ($number === 0) {
    return "Go to the store and buy some more";
  } else {
    return "Take " . $this->pronoun($number) . " down and pass it around";
  }
}

public function pronoun(int $number): string {
  if ($number === 1) {
    return "it";
  } else {
    return "one";
  }
}
```

提议的更改修改了 `quantity`，使得：

- 它的条件判断有 3 个分支而不是 2 个
- 它有时会检查 `-1`，而这是一个无效的啤酒数量

这些不一致性并不保证一定有错误，但它们确实促使你更深入地思考底层的抽象。

问自己这两个问题：

1. `quantity` 方法的责任是什么？
2. 是否有方法让这四个短句更加相似，即使它们尚未完全相同？

首先，考虑责任。`quantity` 概念负责知道在数字的地方应该唱什么。如果有 `50` 瓶啤酒，数量就是 `"50"`；如果有 `5` 瓶啤酒，就是 `"5"`；如果有 `0` 瓶啤酒，就是 `"no more"`。这个概念代表了数字数值与所唱出的的字符串之间的映射。

随着歌曲的进行，歌节编号会递减。你已经很久没看到它们了，这里是 `song` 和 `verses` 方法的提示：

### Listing 4.49：歌曲与歌节的重现

```php
public function song(): string {
  return $this->verses(99, 0);
}

public function verses(int $upper, int $lower): string {
  return implode(
    "\n",
    array_map([$this, 'verse'], range($upper, $lower))
  );
}
```

上面的第 2 行编码了这样的知识：整首歌从第 99 节开始并计数到 0。第 7-9 行递减了歌节编号，使歌曲从一节移动到下一节。如果你熟悉《99 Bottles》，你一定知道这首歌比这段代码要长。真正的歌曲永远持续（或者至少直到所有歌手感到无聊）。这种“永远”发生在 `verse` 方法中 `0` 情况的第 4 个短句，如下所示：

### Listing 4.50：情况 0 处理

```php
public function verse(int $number): string {
  switch ($number) {
    case 0:
      return
        // ...
      "99 bottles of beer on the wall.";
    default:
      return
        // ...
        $this->quantity($number-1) . " " . $this->container($number-1) .
          " of beer on the wall.";
  }
}
```

上面的第 6 行包含一个硬编码的 `99`。这并不是 `quantity` 概念的特殊情况，该概念是关于在数字的地方唱什么的规则。上面的代码有一个微妙之处，即底层概念并不显而易见。如果你完美理解，就会写出完美的应用程序。但大多数情况下你是在摸索，由于信息不足而感到困惑。

当你感到困惑时，不要试图立即解决整个问题。你越困惑，让它们变得更相似就越重要。与其一次一次理解一切，不如通过使用现有代码寻找一种方法让上面的第 6 行看起来像第 10-11 行。

考虑这些问题可能会有所帮助：当 `$number` 的值为 `5` 时，`quantity` 返回什么？当 `$number` 是 `5` 时呢？最后，如果传入 `99`，`quantity` 会返回什么？

如果你刚刚意识到通过向 `quantity` 传递 `99` 可以让这些行变得更加相似，你就掌握了。以下是生成的代码：

### Listing 4.51：99 是一个数量

```php
case 0:
  return
    // ...
    $this->quantity(99) . " bottles of beer on the wall.";
default:
  return
    // ...
    $this->quantity($number-1) . " " . $this->container($number-1) .
      " of beer on the wall.";
```

从上面可以看出，现有的 `quantity` 规则是良好的并且已经适用。当 99 出现在歌曲中，你应该唱字符串 `"99"`。

此时，扫描 `"bottles"` 词并将其替换为 `container` 方法是合理的。这是一个很好理解的差异，现在将其移出可以减少心理负担。以下是生成的代码：

### Listing 4.52：情况 0 调用 Container

```php
case 0:
  return
    // ...
    $this->quantity(99) . " " . $this->container($number-1) .
      " of beer on the wall.";
default:
  return
    // ...
    $this->quantity($number-1) . " " . $this->container($number-1) .
      " of beer on the wall.";
```

让这些行尽可能相似后，现在显而易见：

```
"99"
```

必须代表与相同的概念：

```
$number-1
```

像一样，你必须命名这个概念，创建一个方法，并在差异的地方传递消息。

这个概念关于知道当 `number` 为 `50` 时结果是 `49`，为 `5` 时结果是 `4`，为 `1`、`0` 以及为 `0` 时结果是 `99`。这是歌曲决定下一节歌的地方。

从数学上说，数字的“后继”（successor）是高方向的下一个数字，而它的“前驱”（predecessor）是低方向的下一个数字。这符合大多数人对数字默认方向向上的直觉。

然而，在《99 Bottles》歌曲的歌节编号中，默认方向是向下。大多数歌节后面是编号较小的下一节（0 节除外，后面是 99 节）。`successor` 似乎是当前概念的正确名称，但使用它要求你定义 successor 为“跟随”而不是“更高”。

`successor` 概念是使用导致 `container`、`pronoun`、`quantity` 和 `action` 的相同重构规则发现的。由于这个想法比其他稍微抽象，建议以中等小的步骤进行重构。本着这种精神，首先创建方法，让它返回 `default` 分支的差异。以下是代码：

### Listing 4.53：Successor 处理默认

```php
public function successor(int $number): int {
  return $number - 1;
}
```

`successor` 中的代码引用了 `$number`，因此参数必须从第一个定义。

现在 `successor` 存在了，在 `default` 分支中使用它代替 `$number-1`（见下方第 8 行）：

### Listing 4.54：默认情况调用 Successor

```php
switch ($number) {
  case 0:
    return
      // ...
      $this->quantity(99) . " " . $this->container($number-1) .
      " of beer on the wall.";
  default:
    return
      // ...
      $this->quantity($this->successor($number)) . " " . $this->container($number-1) .
      " of beer on the wall.";
}
```

下一步是通过添加一个条件判断来返回正确的值，从而让 `successor` 可以在 `0` 的情况下使用：

### Listing 4.55：后继者处理两种情况

```php
1 public function successor(int $number): int {
2   if ($number === 0) {
3     return 99;
4   } else {
5     return $number - 1;
6   }
7 }
```

既然有了条件判断，可以将 `99` 替换为 `successor` 的调用，如下所示第 4 行：

### Listing 4.56：两种情况都发送后继者

```
 1 switch ($number) {
 2 case 0:
 3   return
 4     // ...
 5     $this->quantity($this->successor($number)) . " " . $this->container($number-1) .
 6       " of beer on the wall.\n";
 7 default:
 8   return
 9     // ...
10     $this->quantity($this->successor($number)) . " " . $this->container($number-1) .
11       " of beer on the wall.\n";
12 }
```

在进行此更改后，`0` 和 `default` 情况是完全相同的。以下是生成的 `verses` 方法的概览：

### Listing 4.57：相同但不完整

```
 1   switch ($number) {
 2   case 0:
 3     return
 4       ucfirst($this->quantity($number)) . " " . $this->container($number) .
 5         " of beer on the wall, " .
 6       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
 7       $this->action($number) . ", " .
 8       $this->quantity($this->successor($number)) . " " . $this->container($number-1) .
 9         " of beer on the wall.\n";
10   default:
11     return
12       ucfirst($this->quantity($number)) . " " . $this->container($number) .
 13         " of beer on the wall, " .
 14       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
 15       $this->action($number) . ", " .
 16       $this->quantity($this->successor($number)) . " " . $this->container($number-1) .
 17         " of beer on the wall.\n";
18   }
```

`successor` 概念说明了群聚规则（Flocking Rules）迭代应用的力量。在第 1 章给出的解决方案中，甚至没有提到这个概念，如果你在自己解决问题时发现了它，那么你属于少数派。这个概念非常微妙，大多数程序员并没有注意到它，但只要你遵循这套简单的规则，它就会出现。`successor` 是重要的，将它与 `quantity` 分离开可以使这两个方法都遵循单一职责原则。如果你将 `choosing-what-to-sing` 与 `deciding-what-to-sing-next` 混为一，导致的方法将更难以理解，重构将更加困难，并且对其中一个想法修改可能会破坏另一个。

## 4.9. 依赖抽象

抽象在许多方面都有好处。它们将代码合并到一个地方，以便于修改。这种合并后的代码可以作为某个想法的快捷方式。这些是有益的，但抽象还有其他好处。此外，抽象还会告诉你你的代码依赖于哪个想法。要获得这种好处，你必须在应用它的地方引用抽象。



研究上面的代码，考虑 `$this->container($number-1)` 的部分。当从 `0` 情况调用 `container` 时，参数的值是 `-1`。`-1` 导致 `container` 进入虚假分支并返回 "bottles."虽然这段代码通过了测试，但它是偶然。上面的代码并不想要 `$number-1` 的 `container`；它想要下一个 `container`。`successor` 方法负责确定下一个。你现在应该委托抽象，并将 `$number-1` 替换为 `$this->successor($number)`。

最后的更改导致了如下代码：

[列表 4.58：委托给后继者](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-420/lib/Bottles.php#L18-L35)

```
 1 switch ($number) {
 2 case 0:
 3   return
 4     // ...
 5     $this->quantity($this->successor($number)) . " " .
 6       $this->container($this->successor($number)) . " of beer on the wall.\n";
 7 default:
 8   return
 9     // ...
10     $this->quantity($this->successor($number)) . " " .
11       $this->container($this->successor($number)) . " of beer on the wall.\n";
 12 }
```

这是完整的 `verse` 方法，显示 `0` 和 `default` 情况是相同的：

[列表 4.59：相同并使用抽象](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-420/lib/Bottles.php#L17-L36)

```
1 public function verse(int $number): string {
2   switch ($number) {
3   case 0:
4     return
5       ucfirst($this->quantity($number)) . " " . $this->container($number) .
6         " of beer on the wall, " .
7       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
8       $this->action($number) . ", " .
9       $this->quantity($this->successor($number)) . " " .
10         $this->container($this->successor($number)) . " of beer on the wall.\n";
11   default:
12     return
13       ucfirst($this->quantity($number)) . " " . $this->container($number) .
14         " of beer on the wall, " .
15       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
16       $this->action($number) . ", " .
17       $this->quantity($this->successor($number)) . " " .
18         $this->container($this->successor($number)) . " of beer on the wall.\n";
19   }
20 }
```

最后一个重构技巧证明了此通用模板适用于所有情况。将模板复制并插入到 `switch` 语句上方，如下：

[列表 4.60：为每个诗使用相同的模板](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-430/lib/Bottles.php#L17-L44)

```
1 public function verse(int $number): string {
2   return
3     ucfirst($this->quantity($number)) . " " . $this->container($number) .
4       " of beer on the wall, " .
5     $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
6     $this->action($number) . ", " .
7     $this->quantity($this->successor($number)) . " " .
8       $this->container($this->successor($number)) . " of beer on the wall.\n";
9 
10   switch ($number) {
11   case 0:
12     // ...
13   default:
14     return
15     // ...
16   }
17 }
```

上面的更改让你能够对所有情况尝试这一个模板，同时在失败时保留了恢复到绿色（测试通过）的简单方法。在此更改之后，测试*是*绿色的，因此你可以安全地删除整个 `switch` 语句。

以下是结果代码的完整列表：

[列表 4.61：最终列表](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c4-flocking-440/lib/Bottles.php#L5-L66)

```php
class Bottles {
  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return
      ucfirst($this->quantity($number)) . " " . $this->container($number) .
        " of beer on the wall, " .
      $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
      $this->action($number) . ", " .
      $this->quantity($this->successor($number)) . " " .
        $this->container($this->successor($number)) . " of beer on the wall.\n";
  }

  public function quantity(int $number): string {
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }

  public function container(int $number): string {
    if ($number === 1) {
      return "bottle";
    } else {
      return "bottles";
    }
  }

  public function action(int $number): string {
    if ($number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun($number) . " down and pass it around";
    }
  }

  public function pronoun(int $number): string {
    if ($number === 1) {
      return "it";
    } else {
      return "one";
    }
  }

  public function successor(int $number): int {
    if ($number === 0) {
      return 99;
    } else {
      return $number - 1;
    }
  }
}
```

当前的重构已经完成。`verse` 中的 `switch` 语句已减少到一个模板，该模板引用了一系列微巧且一致的抽象。

现在你已经完成了，重要的是思考这段新代码是否真的比你最初开始的“无耻绿”（Shameless Green）有所改进。大多数程序员认为它更好，所以当你听到根据指标它反而更糟时，可能会感到沮丧；你所成就的仅仅是将一个条件变成了多个，同时又增加了 55% 的代码。

然而，请保持乐观。尽管复杂度得分很高，这段代码*确实*更好。它包含了一项静态分析工具无法看到的改进。`container`、`pronoun`、`quantity`、`action` 和 `successor` 概念在“无耻绿”中是不可见的，但在这段新代码中它们都被揭示并隔离了。

### 4.10. 总结

本章完成了从第 3 章开始的重构。它迭代地遵循“群聚规则”（Flocking Rules）来消除 `verse` 方法中的差异，从而挖掘出深藏在《99 瓶啤酒》歌曲中的抽象。

它说明了群聚规则发现复杂概念的力量，即使是那些在现有代码中只投下微弱影子的概念。你不需要理解整个问题就能找到并表达正确的抽象——你只需要反复应用这些规则，抽象就会自然出现。

在继续之前，最后一个最后的想法。考虑一下这个问题：如果几个不同的程序员都从“无耻绿”开始，并根据群聚规则重构 `verse` 方法，生成的代码会是什么样子的？如果你猜每个人的代码将完全相同，除了用于概念的*名称*之外，那么你是正确的。这具有巨大的价值。

现在进入第 5 章，回到“六个装”问题。

## 职责分离

之前的两章重构通过迭代地遵循群聚规则来消除 `verse` 方法中的差异，从而挖掘出《99 瓶啤酒》歌曲中深藏的抽象。

它说明了群聚规则发现复杂概念的力量，即使是那些在现有代码中只投下微弱影子的概念。你不需要理解整个问题就能找到并表达正确的抽象——你只需要反复应用这些规则，抽象就会自然出现。

### 5.1. 选择目标代码味

代码应该对扩展开放，但对修改关闭。现在是时候根据持续的需求重新审视代码了。回顾以下图表（它最初出现在第 3 章）：

![open closed](img/open_closed.png)

图 5.1：开闭流程图

尽管你已经通过命名良好的方法替换了 99 瓶啤酒领域中的大量重复，但结果代码尚未满足需求。如果非要说，目前的实现比“无耻绿”更*难*适应。

本章回到了“六个装”问题。代码味再次引导了下一次重构的选择。一个新的类被创建了，在此过程中探索了建模抽象和依赖；同时也考虑了副作用以及过早优化的危险。

#### 5.1.1. 识别代码中的模式

识别味的一种方法是练习描述代码特征。查看下方的 `Bottles` 类，并记录你感兴趣的内容。包括你看到的任何模式，以及你喜欢、讨厌或不理解的内容。列表之后有一系列引发进一步思考的问题，因此在继续阅读之前请思考一下。

[列表 5.1：DRY Bottles 类](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-10/lib/Bottles.php#L5-L67)

```php
class Bottles {
  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
       "\n",
       array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return
      ucfirst($this->quantity($number)) . " " . $this->container($number) .
        " of beer on the wall, " .
      $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
      $this->action($number) . ", " .
      $this->quantity($this->successor($number)) . " " .
        $this->container($this->successor($number)) . " of beer on the wall.\n";
  }

  public function quantity(int $number): string {
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }

  public function container(int $number): string {
    if ($number === 1) {
      return "bottle";
    } else {
      return "bottles";
    }
  }

  public function action(int $number): string {
    if ($number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun($number) . " down and pass it around";
    }
  }

  public function pronoun(int $number): string {
    if ($number === 1) {
      return "it";
    } else {
      return "one";
    }
  }

  public function successor(int $number): int {
    if ($number === 0) {
      return 99;
    } else {
      return $number - 1;
    }
  }
}
```

以下问题引起了对目前编写的代码中一些有趣的特征：

1. 是否有方法具有相同的形状？
2. 是否有方法接收相同名称的参数？
3. 相同名称的参数总是意味着相同的意思吗？
4. 如果你要将某些方法设为私有，是哪些方法？
5. 如果你要将这个类分成两部分，分界线在哪里？

对于由“群聚规则”（Flocking Rules）创建的方法（`quantity`、`container`、`action`、`pronoun` 和 `successor`，以下简称“五兄弟”）：

6. 条件分支中的测试是否有共同点？
7. 条件有多少个分支？
8. 方法中除了条件外是否还包含其他代码？
9. 每个方法更多依赖于传递的参数，还是更多依赖于类本身？

本节的剩余部分将探讨上述问题。如果你对任何一个问题没有想法，请回看代码并在继续之前尝试回答它们。

### 5.1.2. 发现共同特征

上述五个问题从整体上观察类，并揭示代码的共同特征。接下来的部分将详细探讨这些问题。

#### 问题 1：是否有方法具有相同的形状？



是的。“五兄弟”都具有相同的形状。

你可以通过“眯眼测试”（Squint Test，参见侧边栏）轻松识别出形状相同的方法。这些方法如此一致，是对“群聚规则”的致敬。如果这些方法是在不同的时间、由不同的人出于不同的原因创建的，它们很容易包含各种形状。例如，以下三个方法在逻辑上是相同的：

列表 5.2：各种条件形式

```php
 // 冗长的条件
public function container($number) {
  if ($number === 1) {
    return "bottle";
  } else {
    return "bottles";
  }
}

 // 卫语句
public function quantity($number) {
  if ($number === 0) {
    return "no more";
  }
  return (string)$number;
}

 // 三元表达式
public function pronoun($number) {
  return $number === 1 ? 'it' : 'one';
}
```

上述所有方法都通过了测试。之所以让这些方法看起来不同，是因为这种不必要的差异增加了代码的阅读成本。程序员自然会认为存在差异，但实际上并没有。这种差异让方法看起来很不同，但它们实际上是非常相同的。

这种差异让代码变得难以理解，但实际上并没有。这种差异让方法看起来很不同，但实际上它们是相同的。更重要的是，这些“五兄弟”具有相同的形状。

### 眯眼测试

判断代码的一种简单方法是进行“眯眼测试”。测试方法如下：

1. 将你感兴趣的代码放在屏幕上。
2. 眯起眼睛。
3. 眯着眼睛看代码，直到你无法阅读它。
4. 观察：
    1. 颜色的变化。
    2. 缩进的变化。

缩进揭示了条件的存在。多层缩进导致了多种执行路径，增加了代码的复杂度。

通过后退并眯眼，直到你无法阅读代码。

### 问题 2：是否有方法接收相同名称的参数？

有六个方法接收 `$number`——`verse` 方法和其他方法。

列表 5.3：接收命名参数的方法

```php
public function verse(int $number): string {
public function quantity(int $number): string {
public function container(int $number): string {
public function action(int $number): string {
public function pronoun(int $number): string {
public function successor(int $number): int {
```

### 问题 3：相同名称的参数总是意味着相同的意思吗？

理解 `$number` 代表什么的最简单方法是跟踪它的路径，从 `song` 开始。这里是该方法：

列表 5.4：song 方法

```php
public function song(): string {
  return $this->verses(99, 0);
}
```

当 `song` 发送 `$this->verses(99, 0)` 时，`99` 和 `0` 代表起始和结束的歌节数。你可以认为 `99` 和 `0` 代表要唱歌节中的瓶子数量，但那太牵强，你会属于少数。大多数人将 `99` 和 `0` 解释为节数。

如果 `song` 向 `verses` 发送节数，`verses` 方法必须接收它们。这里是该方法：

列表 5.5：verses 方法

```php
public function verses(int $upper, int $lower): string {
  return implode(
    "\n",
    array_map([$this, 'verse'], range($upper, $lower))
  );
}
```

`$upper` 和 `$lower` 参数是节数。`verses` 方法在它们之间迭代，所以迭代器 `i` 也必须代表一个节数。因此，非常合理地，调用 `verse` 的参数必须是要唱的节数。在 `verse` 中接收时，该参数命名为 `$number`。

```php
public function verse(int $number): string {
```

现在的问题是，`container` 接收到的 `$number` 是否与 `verse` 接收到的 `$number` 代表同一个概念。为了回答这个问题，请考虑整个 `verse` 方法：

列表 5.6：Verse 方法

```php
public function verse(int $number): string {
  return
    ucfirst($this->quantity($number)) . " " . $this->container($number) .
      " of beer on the wall, " .
    $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
    $this->action($number) . ", " .
    $this->quantity($this->successor($number)) . " " .
      $this->container($this->successor($number)) . " of beer on the wall.\n";
}
```

注意上面的第 3 行使用 `$number` 调用了 `container`，而第 8 行使用 `$this->successor($number)` 调用了 `container`。在每一个 verse 中，`container` 都被调用了两次，对应两个不同的值。

出现这种情况是因为每一节都涉及两个瓶子数量。例如，第 37 节以 37 瓶啤酒开始，以 36 瓶结束。正如你所看到的，传递给 `verse` 的输入参数 `$number` 代表的是*诗句编号*。然而，`verse` 随后传递给 `container` 的参数代表的是其他东西——*瓶子数量*。

其他五个聚类的方法也是如此——它们接收的参数是瓶子数量，而不是诗句编号。因此，`verse` 方法和这五个聚类方法相同的参数名称来表示不同的概念。

这通常不是一个好主意。

如果你早就注意到了这个问题，那么恭喜你，但你属于少数派。大多数处理这个问题的人都会根据从 `verse` 传递的参数来命名这五个聚类方法接收的参数。起初，这完全合理。在第 3 章中，当“聚类规则”（Flocking Rules）导致 `container` 方法被提取时，你对问题的理解还没有现在这么深。当时只很明确的是：

*   `verse` 中的 `switch` 语句是对 `$number` 进行分支的，
*   `container` 需要一个参数来决定返回 "bottle" 还是 "bottles"。

为了保持一致性，在第 3 章将 `container` 接收的参数命名为与从 `verse` 传递的参数同名是合理的。在此期间，`$number` 在 `verse` 内部代表诗句编号，而在 `container` 内部代表瓶子数量并不重要。

但现在，这变得重要了。多个方法接收相同的参数是一种“代码异味”（code smell）。然而，重要的是要意识到，这里的“相同”指的是*相同的概念*，而不是*相同的名称*。在理想的世界里，每个不同的概念应该有自己独特、精确的名称，并且没有任何歧义。遗憾的是，现实世界的代码往往无法达到这一理想。在长生命的应用中，同一个概念可能有多个不同的名称，或者像本例一样，同一个概念可能有多个不同的名称。

### 列举共同点

上述问题的答案揭示了代码的许多特征，但在继续之前，还有一个品质需要讨论。

### 5.1.4 坚持使用消息

这段代码包含一种深度非面向对象的模式：这五个聚类方法接收一个参数，检查它，然后*为其提供行为*。

正如你所看到的，这五个方法共享这种共同结构：

列表 5.8：Common Shape

```php
public function container(int $number): string {
  if ($number === 1) {
    return "bottle";
  } else {
    return "bottles";
  }
}
```

上述方法是由群集规则（Flocking Rules）创建的，因此表现出许多良好的特性。尽管如此，从独立面向对象（OO）从业者的角度来看，它存在深的缺陷。从业者在这里看到的将：有人费力注入了一个依赖（`$number`），但该依赖项过于残缺，无法提供所需的行为。因此，`container` 方法不仅了解 `$number`，还被迫去理解 `$number` 具体取值的含义，并需要知道每种情况下该做什么。`container` 方法*依赖*于这些中的每一个项。如果其中任何一个发生变化，`container` 方法都可能被迫随之改变。

在《无耻之绿》（Shameless Green）中，容忍条件判断是有意义的。那个解决方案优化了可理解性，而没有顾及可变性。它的目标是快速通过测试（get green）。生成的代码更多是过程化的而非面向对象的，但如果永远不发生变化，这就足够了。然而，现在你有了新需求并正在重新组织代码，你想应用全面的面向对象思维，而这种思维方式对条件判断深表怀疑。

作为一名 OO 从业者，当你看到条件判断时，脖子上的毛应该竖起来。它的存在本身就应该触犯你的感性。你应该觉得*有权*向对象发送消息，并寻找一种允许你这样操作的代码写法。上述模式意味着对象的缺失，并暗示需要后续的重构来揭示它们。要留意这种代码形状，因为它意味着还有更多工作要做。

这并不是说你会在面向对象应用中永远不会有条件判断。在 OO 中，条件判断*有*其存在之地。可管理的 OO 应用由许多小对象池组成，它们协作完成任务。协作者必须以有用的组合结合在一起，而组装这些组合需要知道哪些对象是合适的。某个地方的某个对象必须选择创建哪些对象，这通常涉及到条件判断。

然而，选择正确对象的条件判断与提供行为的条件判断之间存在巨大差异。前者是可以接受的且通常不可避免的。后者则表明你的领域中缺少对象。

`container` 方法渴望被注入一个更智能的对象，它只需向该对象转发消息即可，如下：

```php
public function container(object $smarterNumber): string {
  $smarterNumber->container();
}
```

现有代码正恳求你创建那个更智能的对象。

## 5.2 提取类

上述问题识别了将方法分组的特征，并且许多这些组是重叠的。例如，许多方法接收相同的参数。大多数此类方法具有相同的形状，包含一个条件判断，可以被认为是私有的，并且对参数的依赖超过对整个类的依赖。

上面的每一项都像一张选票，这些选票共同指向*原始类型痴迷*（Primitive Obsession）这一主要代码气味。内置类型如 `string`、`integer`、`array` 和 `boolean` 是“原始类型”的示例。*原始类型痴迷*是指使用这些类型之一来表示你领域中的概念。对原始类型的痴迷会导致代码在到处传递内置类型，并为它们提供行为。

*原始类型痴迷*的治疗方法是创建一个新类来代替原始类型。对于此操作，重构配方是*提取类*（Extract Class）。

### 5.2.1 建模抽象

在决定用*提取类*重构来治疗*原始类型痴迷*气味后，你现在必须为这个新类选择一个名称。

你正在替换的原始类型代表一个瓶号。注意，它不是一个*瓶子*：它是一个瓶*号*。瓶子是由塑料、玻璃或铝制成的，装有水、汽水或啤酒。瓶有形状和体积。它存在于物理世界。

与瓶子不同，数字不是东西——它们是思想，尽管这些思想无处不在，至于你可能已经忘记它们多么抽象、多么不可能。数字是用于描述物体数量的符号。它们在物理上并不存在。你可以拿起一个瓶子，但你无法拿起“六”。

这个新类并不代表一种瓶子：它代表一种数字。这种区别可能看起来微妙，但这两个概念之间的鸿沟是深渊般的。瓶子是一个东西，而数字是一个思想。这很容易想象。

### 5.2.2 类命名

上述问题识别了将方法分组的特征，并且许多这些组是重叠的。例如，许多方法接收相同的参数。大多数此类方法具有相同的形状，包含一个条件判断，可以被认为是私有的，并且对参数的依赖超过对整个类的依赖。

上面的每一项都像一张选票，这些选票共同指向*原始类型痴迷*这一主要代码气味。内置类型如 `string`、`integer`、`array` 和 `boolean` 是“原始类型”的示例。*原始类型痴迷*是指使用这些类型之一来表示你领域中的概念。对原始类型的痴迷会导致代码在到处传递内置类型，并为它们提供行为。

*原始类型痴迷*的治疗方法是创建一个新类来代替原始类型。对于此操作，重构配方是*提取类*。

### 5.2.3 提取 BottleNumber

本节从现有代码中提取一个名为 `BottleNumber` 的新类。它*没有*使用 TDD。相反，它通过遵循略微修改的 Martin·Fowler 的*提取类*重构配方来创建新类。

正如你可能记得的，安全的重构依赖于测试的绿色通过，因此新的 `BottleNumber` 类在测试到达之前出现这一事实会导致几个后果。首先，现有的 `Bottles` 测试变成了这个新类的安全网。它们最初被编写为单元测试，但通过通过它们间接测试 `BottleNumber`，它们转化为了某种集成测试。这些测试在每次更改后都必须继续运行。

接下来，在提取类时，将`已知可以工作`的代码从 `Bottles` 复制到 `BottleNumber`。在编辑任何复制的代码之前，将这个新类完全投入使用至关重要。安全性由 `Bottles` 的测试提供，因此它们必须尽快地让新代码运行起来。

在之前的章节中，更改代码的过程被分为四个步骤：

1. 解析新代码



## 2. 解析并执行它

## 3. 解析、执行并使用其结果

## 4. 删除未使用的代码

这些步骤仍然适用。通过创建一个空的 `BottleNumber` 类开始提取类，如下所示：

[列表 5.9：BottleNumber 类定义](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-20/lib/Bottles.php#L5-L69)

```
class Bottles {
  // ...
}

class BottleNumber {
}
```

在进行此重构时，请记住在每次更改后保存代码，并在每次保存后运行测试。

接下来，将专注于瓶 `$number` 的方法复制到新类中。

[列表 5.10：复制到 BottleNumber 的执着方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-30/lib/Bottles.php#L5-L108)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    // ...
  }

  public function container(int $number): string {
    // ...
  }

  public function action(int $number): string {
    // ...
  }

  public function pronoun(int $number): string {
    // ...
  }

  public function successor(int $number): int {
    // ...
  }
}

class BottleNumber {
  public function quantity(int $number): string {
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }

  public function container(int $number): string {
    if ($number === 1) {
      return "bottle";
    } else {
      return "bottles";
    }
  }

  public function action(int $number): string {
    if ($number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun($number) . " down and pass it around";
    }
  }

  public function pronoun(int $number): string {
    if ($number === 1) {
      return "it";
    } else {
      return "one";
    }
  }

  public function successor(int $number): int {
    if ($number === 0) {
      return 99;
    } else {
      return $number - 1;
    }
  }
}
```

记住 `verse` 方法**不**应该被提取。尽管它的参数也命名为 `$number`，在这种情况下它代表的是瓶数。

注意上面的示例从 `Bottles` 复制到 `BottleNumber`。这些方法并没有移动——它们被复制了，因此 `Bottles` 没有任何变化。这意味着旧代码继续工作，而新代码尚未执行。此时运行测试仅证明它在语法上是正确的。

如前面提到的，这里遵循的配方受到了 Martin Fowler 的启发。官方的“提取类”配方从链接旧类到新类开始。逐个移动属性，然后是方法。相反，上面的示例从 Fowler 的最后一步开始，在单个更改中组合所有方法。

这似乎是一个巨大的跨越，但在这里你可以确认自己正在移动正确的方法组。这些方法是由于内聚规则创建的，因此它们可见地共享一个共同模式。这种共同模式使得在提取类中变得容易。这种视觉上的相似性是对规则的致意（记住流？）。之前的重构产生了一致的代码，这里一致的代码使得重构变得容易。

`BottleNumber` 类需要知道 `$number` 值，因此添加一个 `__construct` 方法将其存储在属性中。代码如下：

[列表 5.11：持有数字的 BottleNumber](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-40/lib/Bottles.php#L68-L14)

```
class BottleNumber {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }
  // ...
}
```

`number` 属性在上面第 5 行的 `__construct` 方法中设置。当调用 `new BottleNumber()` 时，该 `__construct` 方法被调用。

`BottleNumber` 类现在包含了所有必要的代码，但目前这些代码仅被解析。下一步是在不使用结果的情况下执行类的一部分。

下面的示例通过修改 `Bottles` 的 `quantity` 方法来调用 `BottleNumber` 的 `quantity` 方法来实现这一点：

[列表 5.12：解析并执行部分代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-50/lib/Bottles.php#L5-67)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    (new BottleNumber($number))->quantity($number);
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }
  // ...
}
```

在上面的代码中，`new BottleNumber()` 和 `quantity` 都需要 `$number` 参数，因此必须传递两次。你可能会发现这非常冗余。在新创建的 `BottleNumber` 类中，`quantity` 方法可以很容易不需要参数运行。它可以通过它自己的 `$number` 属性获取正确的数字。比起上面的代码，你更喜欢：

```
(new BottleNumber($number))->quantity();
```

然而，如之前提到的，在新类完全连接之前，你应该避免修改这些方法中的代码。无论你有多讨厌传递两次参数，此时都应该抵抗做出上述更改的冲动。首先，完全连接 `BottleNumber` 到 `Bottles`。一旦完成，你就可以返回并改进 `BottleNumber` 中的方法。

所以，放下那些不愉快的代码，当前重构的下一步是在 `Bottle` 类中使用 `quantity` 方法的结果。实现这一点最简单的方法是在第 4 行开头添加 `return` 关键字，如下所示：

[列表 5.13：解析、执行并使用结果](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-60/lib/Bottles.php#L5-67)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    return (new BottleNumber($number))->quantity($number);
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }
  // ...
}
```

测试通过了，所以现在你可以删除 `quantity` 中的旧实现（上面的第 5-9 行）。这留下了以下代码：

[列表 5.14：生成的 Quantity 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-70/lib/Bottles.php#L5-L62)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    return (new BottleNumber($number))->quantity($number);
  }
  // ...
}
```

对从 `Bottles` 类复制的每个方法重复上述程序。这是一个极其机械化、奇妙地无聊且深感宽慰的重构过程。

以下是生成的 `Bottles` 类：

[Listing 5.15: 向 BottleNumber 转发消息](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-190/lib/Bottles.php#L5-L46)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    return (new BottleNumber($number))->quantity($number);
  }

  public function container(int $number): string {
    return (new BottleNumber($number))->container($number);
  }

  public function action(int $number): string {
    return (new BottleNumber($number))->action($number);
  }

  public function pronoun(int $number): string {
    return (new BottleNumber($number))->pronoun($number);
  }

  public function successor(int $number): int {
    return (new BottleNumber($number))->successor($number);
  }
}
```

`Bottles` 中的这些方法现在仅仅是将消息转发给 `BottleNumber`。

### 5.2.4 移除参数

现在，旧的 `Bottles` 类已经完全使用了 `BottleNumber`，现有的测试可以为新类的更改提供安全保障。这意味着你现在可以对新代码进行改进了。

尽管 `BottleNumber` 可以工作，但它的部分内容存在令人恼的冗余。问题在于，尽管 `BottleNumber` 的实例知道自己的 `$number`，但它的方法仍然需要 `$number` 作为参数。为了说明这一点，这里有两个 `quantity` 方法：

[Listing 5.16: 冗余参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-190/lib/Bottles.php#L5-L94)

```
class Bottles {
  // ...
  public function quantity(int $number): string {
    return (new BottleNumber($number))->quantity($number);
  }
  // ...
}

class BottleNumber {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function quantity(int $number): string {
    if ($number === 0) {
      return "no more";
    } else {
      return (string)$number;
    }
  }
  // ...
}
```

上面的第 4 行获取了一个新的 `BottleNumber` 并请求获取它的 `quantity`。这样做需要对 `$number` 进行两次引用。`__construct` 方法（由 `new` 调用并定义在第 12 行）和 `quantity` 方法（第 16 行）都需要一个 `$number` 参数。

`Primitive Obsession`（基本类型迷恋）/`Extract Class`（提取类）重构的意义在于创建一个更智能的对象来代替基本类型。这个更智能的对象根据定义，既知道基本类型的值，也知道与其相关的行为。由于新的 `BottleNumber` 类持有正确的数字，`BottleNumber` 中的方法不再需要接收参数，这些方法的调用者也可以从传递参数的义务中解出来。

既然 `BottleNumber` 已与 `Bottles` 完全连接，就可以安全地开始这些改进了。请注意，如果你愿意同时修改每个消息的发送者和接收者，那么这种更改是非常简单的。例如，你可以通过更改上面的第 4 行以移除传递给 `quantity` 的参数来修复 `quantity` 方法，同时删除第 16 行的参数，并将第 17 行和第 20 行对它的引用替换为 `$this->number`。如果你同时进行这两个更改并保存代码，测试将通过测试。

请记住，这是一个多行更改。有些问题非常简单，最好直接跳进去进行此类更改，但另一些问题又复杂到无法一次性修复所有内容。在真实世界的应用中，同一个方法名通常会被定义多次，消息可能会从许多不同的地方发送。学习逐行转换代码的艺术，同时保持每一步的测试通过，这让你能够分批次地进行巨大的重构。这个小问题是练习这种技术的好地方，为稍后处理更大的问题做准备。

在第 3 章中，你必须向一个已经*没有*参数调用的方法*添加*一个参数。这是一个相反的问题：在这里你需要从一个当前*带有*参数调用的方法中*移除*一个参数。

考虑下面再次列出的 `quantity`。该方法定义了一个 `$number` 参数。但请记住，`BottleNumber` 类本身有一个 `$number` 属性。

[Listing 5.17: BottleNumber Quantity 的重构](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-190/lib/Bottles.php#L5-L94)

```
class BottleNumber {
  // ...
  public function quantity(): string {
    if ($this->number === 0) {
      return "no more";
    } else {
      return (string)$this->number;
    }
  }
  // ...
}
```

在进行单行更改时保持测试通过（green）的技巧是将 `$number` 参数改为引用属性。

[Listing 5.18: 未使用的参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-190/lib/Bottles.php#L48-L94)



## 重构步骤回顾

### 移除参数的单行更改步骤

1. 修改方法体，将参数的出现处替换为同名属性的引用。

在上面的示例中：

```php
if ($number === 0) {
  return "no more";
} else {
  return (string)$number;
}
```

变为：

```php
if ($this->number === 0) {
  return "no more";
} else {
  return (string)$this->number;
}
```

2. 从方法定义中删除该参数。在示例中：

```php
public function quantity(int $number): string {
```

变为：

```php
public function quantity(): string {
```

3. 修改每个消息的发送者，以移除该参数。在示例中：

```php
return (new BottleNumber($number))->quantity($number);
```

变为：

```php
return (new BottleNumber($number))->quantity();
```

4. 通过在方法体中添加临时的守护语句，确认你已更新了每个发送者。在上面的示例中：

```php
public function quantity(): string {
  // ...
}
```

变为：

```php
public function quantity(): string {
  if (func_num_args() > 0) {
    throw new Exception('Wrong number of arguments.');
  }
  // ...
```

5. 最后，从方法定义中删除守护语句。因此：

```php
public function quantity(): string {
  if (func_num_args() > 0) {
    throw new Exception('Wrong number of arguments.');
  }
  // ...
}
```

变为：

```php
public function quantity(): string {
  // ...
}
```

如你所示，尽管解释很长，但该技术非常简单，仅涉及五个步骤。在 `quantity` 上练习后，其他方法将易如地迎合你的意愿。你现在可以遵循此过程从 `BottleNumber` 剩余的方法中移除 `$number` 参数。

如果你亲自进行这次重构，你会发现 `container` 和 `action` 的工作正常，但当你更改 `pronoun` 时，测试将开始失败。

### 5.2.5. 信任过程

导致错误的重构可能会动摇你对相应配方有效性的信心。然而，这些配方已证明对于许多人在许多情况下是可靠的。如果你遵循一个配方但测试开始失败，很可能是问题中存在某些你尚未理解的内容。

在这种情况下，你一直在使用“通过单行更改移除参数”的过程。它对 `quantity`、`container` 和 `action` 有效，但应用到 `pronoun` 时会导致测试失败。

具体来说，如果你进入 `BottleNumber` 中的 `pronoun`：

[列表 5.21：初始的 BottleNumber Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-280/lib/Bottles.php#L48-94)

```php
class BottleNumber {
  // ...
  public function pronoun(int $number): string {
    if ($number === 1) {
      // ...
    }
  }
}
```

将第 4 行的 `$number` 改为 `$this->number`：

[列表 5.22：更新后的 BottleNumber Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-281/lib/Bottles.php#L48-94)

```php
class BottleNumber {
  // ...
  public function pronoun(int $number): string {
    if ($this->number === 1) {
      // ...
    }
  }
}
```

并从方法定义中删除未使用的参数：

[列表 5.23：不带参数的 BottleNumber Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-290/lib/Bottles.php#L45-46)

```php
class BottleNumber {
  // ...
  public function pronoun(): string {
    if ($this->number === 1) {
      // ...
    }
  }
}
```

然后进入 `Bottles` 中的 `pronoun` 方法：

[列表 5.24：初始的 Bottles Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-290/lib/Bottles.php#L45-46)

```php
class Bottles {
  // ...
  public function pronoun(int $number): string {
    return (new BottleNumber($number))->pronoun($number);
  }
}
```

并从向 `BottleNumber` 转发 `pronoun` 的处移除参数：

[列表 5.25：更新后的 Bottles Pronoun 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-300/lib/Bottles.php#L45-46)

```php
class Bottles {
  // ...
  public function pronoun(int $number): string {
    return (new BottleNumber($number))->pronoun();
  }
}
```

现在当你回到 `BottleNumber` 中的 `pronoun` 方法定义并添加临时的守护语句：

[列表 5.26：回到 BottleNumber Pronoun](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-310/lib/Bottles.php#L48-97)

```php
class BottleNumber {
  // ...
  public function pronoun(): string {
    if (func_num_args() > 0) {
      throw new Exception('Wrong number of arguments.');
    }
    // ...
  }
}
```

然后测试开始报错：

```
Exception: Wrong number of arguments.
```

适用于其他方法现在在 `pronoun` 上失效了。这个错误可能会让你怀疑该技术的有效性，但它并不是过程本身的缺陷，而是暴露了一些代码。回顾移除参数所需的步骤：

1. 修改方法体，将参数的出现处替换为同名属性的引用。
2. 从方法定义中删除该参数。
3. 修改每个消息的发送者，以移除该参数。
4. 在方法体中添加临时的守护语句。
5. 删除守护语句。

失败出现在第 4 步之后。错误消息表明某些调用者仍在向 `pronoun` 传递参数。这意味着步骤 3 尚未完成；换句话说，某个发送者尚未修复。这应该促使检查发生错误的代码。当你这样做时，你会看到：

[列表 5.27：使用 Pronoun 的 BottleNumber 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-310/lib/Bottles.php#L48-97)

```php
class BottleNumber {
  // ...
  public function action(): string {
    if ($this->number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun($this->number) . " down and pass it around";
    }
  }
  // ...
}
```

事实 `pronoun` 仅从 `BottleNumber` 的 `action` 方法调用，那里的消息发送给 `$this`。之前在 `Bottles` 中定义的 `pronoun` 方法不再使用（你可以通过随意删除它并运行测试来确认）。

并不是修改 `Bottles` 中未使用的 `pronoun` 方法，步骤 3 应该从 `BottleNumber` 的 `action` 方法对 `pronoun` 的调用中移除 `$number` 参数，留下：

[列表 5.28：修正后的 BottleNumber Action 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-340/lib/Bottles.php#L44-90)

```php
class BottleNumber {
  // ...
  public function action(): string {
    if ($this->number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun() . " down and pass it around";
    }
  }
  // ...
}
```

现在 `pronoun` 已经工作了，只剩下 `successor` 方法。它毫无意外地顺从了这次重构。这完成了对 `BottleNumber` 类中方法多余参数的移除，并使代码处于以下停顿点。

[列表 5.29: 将消息传递给更智能的数字](https://github.com/sandimetz/99bottles_php/blob/2.1-extract-class-38/lib/Bottles.php#L5-L90)

```php
1 class Bottles {
2   public function song(): string {
3     return $this->verses(99, 0);
4   }
5 
6   public function verses(int $upper, int $lower): string {
7     return implode(
8       "\n",
9       array_map([$this, 'verse'], range($upper, $lower))
10     );
11   }
12 
13   public function verse(int $number): string {
14     return
15       $this->quantity($number) . " " . $this->container($number) .
16         " beer on the wall, " .
17       $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
18       $this->action($number) . ", " .
19       $this->quantity($this->successor($number)) . " " .
20         $this->container($this->successor($number)) . " of beer on the wall.\n";
21   }
22 
23   public function quantity(int $number): string {
24     return (new BottleNumber($number))->quantity();
25   }
26 
27   public function container(int $number): string {
28     return (new BottleNumber($number))->container();
29   }
30 
31   public function action(int $number): string {
32     return (new BottleNumber($number))->action();
33   }
34 
35   public function successor(int $number): int {
36     return (new BottleNumber($number))->successor();
37   }
38 }
39 
40 class BottleNumber {
41   protected $number;
42 
43   public function __construct(int $number) {
44     $this->number = $number;
45   }
46 
47   public function quantity(): string {
48     if ($this->number === 0) {
49       return "no more";
50     } else {
51       return (string)$this->number;
52     }
53   }
54 
55   public function container(): string {
56     if ($this->number === 1) {
57       return "bottle";
58     } else {
59       return "bottles";
60     }
61   }
62 
63   public function action(): string {
64     if ($this->number === 0) {
65       return "Go to the store and buy some more";
66     } else {
67       return "Take " . $this->pronoun() . " down and pass it around";
68     }
69   }
70 
71   public function pronoun(): string {
72     if ($this->number === 1) {
73       return "it";
74     } else {
75       return "one";
76     }
77   }
78 
79   public function successor(): int {
80     if ($this->number === 0) {
81       return 99;
82     } else {
83       return $this->number - 1;
84     }
85   }
}
```

这完成了 `BottleNumber` 的提取。原始的 `Bottles` 类现在没有了条件判断，但它们并没有消失——只是稍微简单的形式移动到了新类中。然而，尽管有条件判断，`BottleNumber` 中的代码具有一种令人愉的规律性，这对未来的重构是一个良好的预示。



# 5.3 欣赏不可变性

`mutate` 是改变。`State` 是“某个事物在特定时间的特定状态”。`variable` 是“发生变化的东西”，或者在数学中，“一个在同一个表达式中允许无限数量取值的量”。在物理世界中，情况随时间而变化。你的咖啡杯是满的，但现在是空的。你一直在运动，现在你饿了。喜马拉雅山正在上升。是同一个杯子，但它的状态改变了。现实世界渗透着这种思想——存在的，就会改变。

人类对于改变的必要性和权利的共识反映在计算机编程中 `variable` 的选择上。除了变化之外，变量还有什么目的？大多数面向对象的程序员编写的代码期望并依赖于变异。对象被构造、变异，然后被再次使用。

无论这看起来多么直观和自然，变异并不是绝对要求。完全可以（函数式语言程序员会乐意告知你）从 `immutable` 对象来构建应用程序，即不改变的对象。对于那些不习惯这种想法的人来说，想象由函数式程序员构建的现实可能会让他们无所措。你不是接满现有的杯，而是放弃它，转而使用一个看起来完全相同但装满咖啡的新杯。你不是让自己变饿，而是用一个新的、更饿的自己来替换自己。

# 5.4 假设足够快

不可变性的优势是如此巨大，以至于如果它是免费的，你每次都会选择它。不可变性带来的代价是双倍的。首先，你必须接受这个观点，这对于许多程序员来说可不是小事。其次，实现不可变性需要创建更多（有时是多得多）新对象。

习惯一种新的思维方式只需要发生一次，所以这种成本并不是永久性的担忧；今天饮下“不可变性酷尔水”（immutability Kool-Aid）就足够受用了。因此，不可变性的持续成本大部分体现在创建新对象上，而这本节的主题。

你可能很熟悉 Phil Karlton 的名言：“计算机科学中只有两类难题：缓存失效和命名。”你已经读过很多关于命名的内容了，现在是时候讨论缓存了。

在计算机科学中，`cache`（缓存）是存储在其他地方某个内容的本地副本。保存昂贵操作结果的本地副本，或对其进行 `caching`（缓存），被认为可以提高应用程序运行速度，从而降低成本。

上述陈述中的假设是双重的。首先，它假设缓存会让应用程序运行得更快，其次，它假设缓存会降低成本。这些陈述有时是正确的，但并非总是如此。

当你发送一条消息并将结果保存到变量时，你就创建了一个简单的缓存。如果变量中的值变得过时，你必须使缓存失效，要么丢弃它，要么重新发送消息并保存新结果。

缓存很容易。然而，弄清楚缓存需要更新可能是困难的。执行此操作的代码通常复杂且令人困惑。这些额外的代码必须经过测试，而且不可避免地，当发现测试不足时，还需要调试。管理缓存所需的额外代码可能非常难写、难理解，且运行昂贵，以至于抵消了原始带来的收益。

注意，缓存和变异（mutation）的成本是相互关联的。如果你缓存的内容不会发生变异，你的本地副本永远有效。如果你缓存了会变化的内容，你必须编写额外的代码来识别你的副本已过期，并重新运行初始操作来更新缓存。

如果你处理过处理复杂的缓存失效（cache invalidation）的代码，那么你不会意外发现这个词本身源于法语词 `cacher`，意为隐藏或遮盖。过时的缓存可能是晦涩、昂贵且令人沮丧的 bug 的源头。缓存的净成本只能通过比较速度提升的收益与创建及维护缓存的成本来计算。如果你需要这种速度提升，任何成本都是廉价的；如果你不需要，每种成本都太高了。

变异和缓存使代码复杂化。这种复杂性通常被接受为必要的，并由于认为它能提高性能而被合理化。然而，不幸的事实是，人类非常不长于预判一个程序整体是否足够快，如果不够，它的哪些部分会太慢。

在获得关于这些问题的实际数据之前，为了解决性能问题而使代码复杂化会增加成本，并且往往没有任何回报。这些猜测几乎肯定是错误的，仅仅会损害可读性并阻碍变更。

基于此，最好的编程策略是编写尽可能简单的代码，并在完成后测量其性能。如果整体速度未达到接受的标准，则对性能进行分析（profile），并加速最慢的部分。提高速度可能需要缓存，但许多问题可以通过在特定、狭窄的地方替换更高效的代码来解决。一旦你精确了解哪里出了问题，可能可以在不使用缓存的情况下修复它。

你的目标是在保持足够快性能的同时，优化易理解性。不要在获得可靠性能数据之前就牺牲可读性。任何问题的第一个解决方案都应该避免缓存，使用不可变对象，并将对象创建视为免费。这导致了简单代码的快速开发，留下了充足的时间来识别和纠正真正的性能问题。

现在这个某种带有理论性的讨论已经完成，是时候回到 `Bottles` 类，并将思想应用到实际代码中了。

# 5.5 创建 BottleNumbers

即使对于那些习惯对象创建的人来说，`Bottles` 中的代码也构建了相当数量的 `BottleNumber`。检查下面的方法，并计算 `verse` 创建新 `BottleNumber` 的次数。

## Listing 5.30: 许多新的 BottleNumbers

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return
      ucfirst($this->quantity($number)) . " " . $this->container($number) .
        " of beer on the wall, " .
      $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
      $this->action($number) . ", " .
      $this->quantity($this->successor($number)) . " " .
        $this->container($this->successor($number)) . " of beer on the wall.\n";
  }

  public function quantity(int $number): string {
    return (new BottleNumber($number))->quantity();
  }

  public function container(int $number): string {
    return (new BottleNumber($number))->container();
  }

  public function action(int $number): string {
    return (new BottleNumber($number))->action();
  }

  public function successor(int $number): int {
    return (new BottleNumber($number))->successor();
  }
}
```

在上述代码中，当调用 `quantity`、`container`、`action` 或 `successor` 时，都会创建一个新的 `BottleNumber` 实例。`verse` 方法总共发送了这些消息 9 次。因此，在整首歌中，创建了 900 个新的 `BottleNumber`。

这可能感觉很过度。这种对象的创建泛滥是之前重构的结果。该配方将每个原始方法的体替换为将消息转发到新类的代码。

在 `Bottles` 中，`verse` 是唯一发送 `quantity`、`container`、`action` 或 `successor` 消息的方法，因此这些转发方法的出现似乎是多余的。在这个简单的例子中确实如此。但在更复杂的问题中，执行提取类（Extract Class）重构后，发现生成的转发消息在原始类中被多次调用并不意外。这些转发方法的存在为原始类提供一个单一的地方来接收发送自己的消息，并将其传递给新类。

之前的重构配方并没有尝试减少新对象的数量，而是创建了一组直言不讳创建提取类实例的转发方法。结果是 900 个 `BottleNumbers`。

这段代码可以工作，如果你觉得它很痛苦，可能是因为感觉它很浪费。存在替代方案。如果不受配方的限制，有许多方法可以避免这种浪费的对象创建，考虑它们是有益的。

例如，歌曲第一节的前三句发送了两次 `quantity` 和两次 `container`，以及一次 `action`。这为 `$number` 99 创建了五个 `BottleNumber` 实例。如果第一个实例被缓存，它可以在这三句中被重用四次。

第 99 节的第四句发送了两次 `successor`，这创建了两个额外的 `BottleNumber` 99。之前缓存的瓶子数量可以在这里使用。因此，`BottleNumber` 99 只需要创建一次，然后就可以重用六次。

第 99 诗的第四句也发送了 `quantity` 和 `container`。这在后继者（即 98）上创建了两个 `BottleNumber` 实例。缓存第一个实例可以节省这节诗中的另外一次对象创建。此外，缓存的副本可以在下一节诗中重用，从而再节省七个对象的创建，总共可以节省八个。在整首歌中，缓存可以将新 `BottleNumber` 实例的数量从 900 个减少到 100 个。

对于那些觉得需要更加吝啬的人，可以创建一个 `BottleNumber` 实例并重用 900 次。要实现这一点，你需要为数字 `$number` 99 创建一个 `BottleNumber`，然后当对第 98 号瓶子产生需求时，直接在那个唯一的现存对象中将 `$number` 的值从 99 改为 98。就这样，你同时添加了缓存和变异。

因此，你可以通过缓存现有的实例来减少新 `BottleNumber` 的数量，如果你愿意对其进行变异，还可以进一步减少这个数量。做其中任何一种都可能降低某些成本，但无疑会增加其他成本。这些都不是免费的。

作为一个思维练习，在继续阅读之前，请花分钟想象一下修改现有代码以使用单个 `BottleNumber` 实例。如果你发现这个练习很容易，请尝试另一个，这次假设 `quantity`、`container`、`action` 和 `successor` 是从 `Bottles` 的多个方法发送的。如果你感兴趣，可以停一下，去编写代码。你会发现实现此所需的更改增加了复杂度。这种复杂度带来的成本可能超过性能提升带来的收益。

完成该实验后，回到当前的问题。在这个示例中，转发方法仅从 `Bottles` 的一个方法中调用。这意味着可能通过添加一个简单的、自动失效的低成本缓存来减少对象的创建。下面的示例显示了在第 4 行缓存了 `BottleNumber`：

## Listing 5.31: 缓存 BottleNumber

```php
class Bottles {
  // ...

  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);

    return
      ucfirst($this->quantity($number)) . " " . $this->container($number) .
        " of beer on the wall, "
      $this->quantity($number) . " " . $this->container($number) . " of beer.\n" .
      $this->action($number) . ", " .
      $this->quantity($this->successor($number)) . " " .
        $this->container($this->successor($number)) . " of beer on the wall.\n";
  }
  // ...
}
```

上面的第 4 行创建了 `BottleNumber` 的新实例，并将其缓存在 `verse` 方法中的一个临时变量中（这就是 `Temporary Variable` 代码气味）。该缓存在不增加太多额外复杂性的情况下减少了对象的创建，因此在这里是合理的，因为收益超过了成本。

既然这个缓存对象已经存在，你可以逐渐修改诗句模板，将消息发送给新对象而不是 `$this`。下一个示例从最可能的更改开始过渡。下面的第 8 行向这个新对象询问其 `action`：

## Listing 5.32: 向缓存对象请求动作

```php
class Bottles {
  // ...

  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);

      // ...
      $bottleNumber->action() . ", " .
      // ...
  }
}
```

在上面的代码中，`$this->action($number)` 被替换为 `$bottleNumber->action()`。这将 `action` 消息直接发送给新的 `BottleNumber`，完全跳过了本地实现。

在 `verse` 模板的第一和第二句中也可以进行类似的更改，如下：

## Listing 5.33: 在第一、二句中使用缓存对象

```php
}

public function verse(int $number): string {
  $bottleNumber = new BottleNumber($number);

  return
    ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
      " of beer on the wall, " .
    $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
    $bottleNumber->action() . ", " .
    // ...
}
```

在上面的代码中，`$this->action($number)` 被替换为 `$bottleNumber->action()`。这将 `action` 消息直接发送给新的 `BottleNumber`，完全跳过了本地实现。

# 5.6 识别 Liskov 违反

在上面的代码中，`$this->action($number)` 被替换为 `$bottleNumber->action()`。这将 `action` 消息直接发送给新的 `BottleNumber`，完全跳过了本地实现。

这种不一致性是对广义 Liskov 替换原则的另一种违反。名为 `successor` 的方法隐含地承诺它返回的内容将表现得像你发送消息的那个对象。但这个 `successor` 方法在撒谎。它违背了它的承诺，迫使发送者知道返回结果是不可信的，并采取步骤处理这种违规行为。

尽管这令人烦恼，但你正修改 `verse` 模板以向对象发送消息的中间。当前的重构几乎已经完成，在进行垂直方向的改进之前，完成水平方向的重构通常是更好的。你*可以*偏离路径并修复 Liskov 违规问题，但在在开始新任务之前完成当前思绪的精神下，请[坚持到底](https://en.wikipedia.org/wiki/Stay_the_course)。你已经声明了一个临时变量来存放第 99 号瓶。当前的问题可以通过声明另一个变量来存放第 98 号瓶并编写一些无廉耻的代码来解决。在下方的第 3 行，以下示例勇敢地做到了这一点：

## Listing 5.35: 缓存继者




# 重构 `verse` 方法：缓存 `BottleNumber` 实例

## 初始代码

```php
 1 public function verse(int $number): string {
 2   $bottleNumber = new BottleNumber($number);
 3   $nextBottleNumber = new BottleNumber($bottleNumber->successor());
 4 
 5   return
 6     ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
 7       " of beer on the wall, " .
 8     $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
 9     $bottleNumber->action() . ", " .
10     $nextBottleNumber->quantity() . " " . $nextBottleNumber->container() .
11       " of beer on the wall.\n";
12 }
```

上面的第 3 行在现有 `BottleNumber` 的继者上创建新的 `BottleNumber`。最终，你想改进这行代码，但目前只需推进当前的重构即可。既然 `$nextBottleNumber` 已经存在，第 10 行就可以向它索要 `quantity` 和 `container`。

在该更改之后，`verse` 方法包含了两个不同的部分。上面的第 6-11 行定义了一个模板，查询 `BottleNumber` 实例的详情。第 2 行和第 3 行创建了 `BottleNumber` 的新实例。第 2 行似乎合理，但第 3 行很别扭，因为 Liskov 违规迫使你自己调用 `successor()` 然后将它的返回值转换为 `BottleNumber`。

这完成了 `verse` 方法中对 `BottleNumber` 的缓存，但还有最后一个项更改要完成。现在 `verse` 直接与缓存在临时变量中的对象通信，转发方法不再需要了。删除它们后，代码简化为如下：

[列表 5.36: 治愈执念症](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-450/lib/Bottles.php#L5-L77)

```php
 1 class Bottles {
 2   public function song(): string {
 3     return $this->verses(99, 0);
 4   }
 5 
 6   public function verses(int $upper, int $lower): string {
 7     return implode(
 8       "\n",
 9       array_map([$this, 'verse'], range($upper, $lower))
10     );
 11   }
 12 
 13   public function verse(int $number): string {
 14     $bottleNumber = new BottleNumber($number);
 15     $nextBottleNumber = new BottleNumber($bottleNumber->successor());
 16 
 17     return
 18     ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
 19         " of beer on the wall, " .
 20       $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
 21       $bottleNumber->action() . ", " .
 22       $nextBottleNumber->quantity() . " " . $nextBottleNumber->container() .
 23         " of beer on the wall.\n";
 24   }
 25 }
 26 class BottleNumber {
 27   protected $number;
 28 
 29   public function __construct(int $number) {
 30     $this->number = $number;
 31   }
 32 
 33   public function quantity(): int {
 34     if ($this->number > 0) {
 35       return $this->number;
 36     } else {
 37       return 0;
 38     }
 39   }
 40 
 41   public function container(): string {
 42     if ($this->number == 1) {
 43       return "a bottle";
 44     } else {
 45       return "bottles";
 46     }
 47   }
 48 
 49   public function action(): string {
 50     if ($this->number > 1) {
 51       return "throw a bottle";
 52     } else if ($this->number == 1) {
 53       return "throw the bottle";
 54     } else {
 55       return "do nothing";
 56     }
 57   }
 58   
 59   public function successor(): BottleNumber {
 60     return new BottleNumber($this->number - 1);
 61   }
 62 }
```

## Liskov 替换原则违规分析

这种不一致性是对广义 Liskov 替换原则的另一种违反。名为 `successor()` 的方法隐含地承诺它返回的内容将表现得像你发送消息的那个对象。但这个 `successor()` 方法在撒谎。它违背了它的承诺，迫使发送者知道返回结果是不可信的，并采取步骤处理这种违规行为。

尽管这令人烦恼，但你正修改 `verse` 模板以向对象发送消息的中间。当前的重构几乎已经完成，在进行垂直方向的改进之前，完成水平方向的重构通常是更好的。你*可以*偏离路径并修复 Liskov 违规问题，但在在开始新任务之前完成当前思绪的精神下，[坚持到底](https://en.wikipedia.org/wiki/Stay_the_course)。你已经声明了一个临时变量来存放第 99 号瓶。当前的问题可以通过声明另一个变量来存放第 98 号瓶并编写一些无廉耻的代码来解决。在下方的第 3 行，以下示例勇敢地做到了这一点：

[列表 5.35: 缓存继者](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-440/lib/Bottles.php#L17-L28)

上面的第 3 行在现有 `BottleNumber` 的继者上创建新的 `BottleNumber`。最终，你想改进这行代码，但目前只需推进当前的重构即可。既然 `$nextBottleNumber` 已经存在，第 10 行就可以向它索要 `quantity` 和 `container`。

在该更改之后，`verse` 方法包含了两个不同的部分。上面的第 6-11 行定义了一个模板，查询 `BottleNumber` 实例的详情。第 2 行和第 3 行创建了 `BottleNumber` 的新实例。第 2 行似乎合理，但第 3 行很别扭，因为 Liskov 违规迫使你自己调用 `successor()` 然后将它的返回值转换为 `BottleNumber`。

这完成了 `verse` 方法中对 `BottleNumber` 的缓存，但还有最后一个项更改要完成。现在 `verse` 直接与缓存在临时变量中的对象通信，转发方法不再需要了。删除它们后，代码简化为如下：

[列表 5.36: 治愈执念症](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-450/lib/Bottles.php#L5-L77)

```php
 1 class Bottles {
 2   public function song(): string {
 3     return $this->verses(99, 0);
 4   }
 5 
 6   public function verses(int $upper, int $lower): string {
 7     return implode(
 8       "\n",
 9       array_map([$this, 'verse'], range($upper, $lower))
10     );
 11   }
 12 
 13   public function verse(int $number): string {
 14     $bottleNumber = new BottleNumber($number);
 15     $nextBottleNumber = new BottleNumber($bottleNumber->successor());
 16 
 17     return
 18       ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
 19         " of beer on the wall, " .
 20       $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
 21       $bottleNumber->action() . ", " .
 22       $nextBottleNumber->quantity() . " " . $nextBottleNumber->container() .
 23         " of beer on the wall.\n";
 24   }
 25 }
 26 class BottleNumber {
 27   protected $number;
 28 
 29   public function __construct(int $number) {
 30     $this->number = $number;
 31   }
 32 
 33   public function quantity(): int {
 34     if ($this->number > 0) {
 35       return $this->number;
 36     } else {
 37       return 0;
 38     }
 39   }
 40 
 41   public function container(): string {
 42     if ($this->number == 1) {
 43       return "a bottle";
 44     } else {
 45       return "bottles";
 46     }
 47   }
 48 
 49   public function action(): string {
 50     if ($this->number > 1) {
 51       return "throw a bottle";
 52     } else if ($this->number == 1) {
 53       return "throw the bottle";
 54     } else {
 55       return "do nothing";
 56     }
 57   }
 58   
 59   public function successor(): BottleNumber {
 60     return new BottleNumber($this->number - 1);
 61   }
 62 }
```



这种不一致性是对广义 Liskov 替换原则的另一种违反。名为 `successor` 的方法隐含地承诺它返回的内容将表现得像你发送消息的那个对象。但这个 `successor` 方法在撒谎。它违背了它的承诺，迫使发送者知道返回结果是不可信的，并采取步骤处理这种违规行为。

尽管这令人烦恼，但你正修改 `verse` 模板以向对象发送消息的中间。当前的重构几乎已经完成，在进行垂直方向的改进之前，完成水平方向的重构通常是更好的。你*可以*偏离路径并修复 Liskov 违规问题，但在开始新任务之前完成当前思绪的精神下，[坚持到底](https://en.wikipedia.org/wiki/Stay_the_course)。你已经声明了一个临时变量来存放第 99 号瓶。当前的问题可以通过声明另一个变量来存放第 98 号瓶并编写一些无廉耻的代码来解决。在下方的第 3 行，以下示例勇敢地做到了这一点：

[列表 5.35: 缓存继者](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-440/lib/Bottles.php#L17-L28)

上面的第 3 行在现有 `BottleNumber` 的继者上创建新的 `BottleNumber`。最终，你想改进这行代码，但目前只需推进当前的重构即可。既然 `$nextBottleNumber` 已经存在，第 10 行就可以向它索要 `quantity` 和 `container`。

在该更改之后，`verse` 方法包含了两个不同的部分。上面的第 6-11 行定义了一个模板，查询 `BottleNumber` 实例的详情。第 2 行和第 3 行创建了 `BottleNumber` 的新实例。第 2 行似乎合理，但第 3 行很别扭，因为 Liskov 违规迫使你自己调用 `successor` 然后将它的返回值转换为 `BottleNumber`。

这完成了 `verse` 方法中对 `BottleNumber` 的缓存，但还有最后一个项更改要完成。现在 `verse` 直接与缓存在临时变量中的对象通信，转发方法不再需要了。删除它们后，代码简化为如下：

[列表 5.36: 治愈执念症](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-450/lib/Bottles.php#L5-L77)

```php
class Bottles {

  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
        " of beer on the wall, " .
      $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
      $bottleNumber->action() . ", " .
      $nextBottleNumber->quantity() . " " . $nextBottleNumber->container() .
        " of beer on the wall.\n";
  }
}

class BottleNumber {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function quantity(): int {
    if ($this->number > 0) {
      return $this->number;
    } else {
      return 0;
    }
  }

  public function container(): string {
    if ($this->number == 1) {
      return "a bottle";
    } else {
      return "bottles";
    }
  }

  public function action(): string {
    if ($this->number > 1) {
      return "throw a bottle";
    } else if ($this->number == 1) {
      return "throw the bottle";
    } else {
      return "do nothing";
    }
  }

  public function successor(): BottleNumber {
    return new BottleNumber($this->number - 1);
  }
}
```

### 5.7. Summary

本章继续了使 `Bottles` 开放的任务。它还探索了建模的奖励、缓存的权衡以及不可变性的好处。你一直抱有认为消除代码异味最终会通向开放性。你的信念可能正在受到考验。

尽管有上述缺陷，但代码在某些方面*确实*更好了。现在有两个类，但每个类都有专注的职责。虽然整体变大了，但每个部分都易于理解和推理。

代码是一致的、规律的，并且体现了一个极其稳定的落点，完美地开启了下一次重构。

就这样，进入第 6 章。

### 6.1. 合并数据簇

`BottleNumber` 类包含了条件判断，移除它们将使代码更容易理解且维护成本更低。然而，在关注那个问题之前，有一个更简单的代码异味可以解决。

`verse` 方法包含两个总是成对出现的内容。看看下面的代码（已重复列），看看你能否识别出它们：

[Listing 6.1: 数量和容器形成数据簇](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-450/lib/Bottles.php#L5-L29)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst($bottleNumber->quantity()) . " " . $bottleNumber->container() .
        " of beer on the wall, " .
      $bottleNumber->quantity() . " " . $bottleNumber->container() . " of beer.\n" .
      $bottleNumber->action() . ", " .
      $nextBottleNumber->quantity() . " " . $nextBottleNumber->container() .
        " of beer on the wall.\n";
  }
}
```

在上方，`quantity` 和 `container` 在三个不同的地方共同出现（第 8、10 和 12 行）。这种配对的重复散发着“数据簇”（`Data Clump`）代码异味的臭味。正如名称所示，`数据簇` 正式是关于 `data` 的，它被定义为几个（三个或更多）数据字段经常一起出现的情况。

拥有一组数据簇通常意味着你缺少一个概念。当一个簇被作为一组参数发送时，接收该簇的方法很容易被管理簇的逻辑所污染。如果有多个方法接收相同的数据簇作为输入，那么这种管理逻辑的部分或全部将不可避免地在多个地方重复。维护这种重复不仅很痛苦，而且随着时间的推移，逻辑可能会意外产生分歧，引入错误并困扰所有相关人员。

在当前案例中，将上述 `quantity` 和 `container` 配对称为 `数据簇` 稍显牵强，但移除簇的价值如此巨大，以至于从这个角度来看这段代码是有意义的。如果这两个元素总是成对出现，这意味着这种配对代表了一个更深层次的概念，而这个概念应该被命名。

完整的 `数据簇` 通常通过提取一个类来移除，但在这个小示例中，简单创建一个新方法是有意义的。一如既往，应该给方法一个反映其目的的名字。

在这种情况下，`quantity` 和 `container` 频繁出现，以至于可以认为它们是 `BottleNumber` 的字符串表示。你可以实现一个返回该组合的 `__toString` 方法，但 `__toString` 有点“魔术化”，在此时最好是显式的。因此，下例示例声明了一个公有的 `toString` 方法。

[Listing 6.2: BottleNumber 提供字符串表示](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-10/lib/Bottles.php#L31-L82)

```php
class BottleNumber {
  // ...
  public function toString(): string {
    return $this->quantity() . " " . $this->container();
  }
  // ...
}
```

完成上述操作后，你现在可以使用简单的 `toString` 消息发送替换 `quantity`/`container` 簇。例如，`verse` 模板的第二个短句目前是：

```php
$nextBottleNumber->quantity() . " " . $nextBottleNumber->container()
```

有了 `toString`，你可以将对象转换为字符串：

```php
$bottleNumber->toString()
```

你可以在任何 `quantity` 和 `container` 同时使用的地方进行此更改。这里是整个 `verse` 方法，簇已被替换为对 `$bottleNumber` 的显式 `toString` 调用：

[Listing 6.3: 移除了簇的诗节](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-40/lib/Bottles.php#L5-L29)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst($bottleNumber->toString()) .
        " of beer on the wall, " .
      $bottleNumber->toString() . " of beer.\n" .
      $bottleNumber->action() . ", " .
      $nextBottleNumber->toString() .
        " of beer on the wall.\n";
  }
}
```

移除簇极大缩短了代码，使得代码可以重新格式化以更准确地反映歌曲。现在可以清楚地看到四句，如 8-11 行所示：

[Listing 6.4: 具有四句的诗节](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-40/lib/Bottles.php#L5-L29)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst($bottleNumber->toString()) .
        " of beer on the wall, " .
      $bottleNumber->toString() . " of beer.\n" .
      $bottleNumber->action() . ", " .
      $nextBottleNumber->toString() .
        " of beer on the wall.\n";
  }
}
```

既然 `toString` 方法可以工作了，它可以很容易转换为 `__toString`。要做到这一点，从复制方法并命名为 `__toString` 开始：

```php
class BottleNumber {
  // ...
  public function toString(): string {
    return $this->quantity() . " " . $this->container();
  }

  public function __toString(): string {
    return $this->quantity() . " " . $this->container();
  }
  // ...
}
```



回到 `Bottles` 并将 `toString` 调用替换为 `string` 显式转换（第 8、9 和 11 行）。这种转换将调用新的 `__toString` 方法。

```php
class Bottles {

  // ...
  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst((string)$bottleNumber) . " of beer on the wall, " .
      (string)$bottleNumber . " of beer.\n" .
      $bottleNumber->action() . ", " .
      (string)$nextBottleNumber . " of beer on the wall.\n";
  }
}
```

现在你可以利用字符串插值的隐式转换来简化 `verse`。下一个示例将 `$bottleNumber` 插值到每个句子中，删除了显式转换。

```php
class Bottles {

  // ...
  public function verse(int $number): string {
    $bottleNumber = new BottleNumber($number);
    $nextBottleNumber = new BottleNumber($bottleNumber->successor());

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$nextBottleNumber} of beer on the wall.\n";
  }
}
```

原始的 `toString` 方法现在已经过时，可以删除。

当前的 `__toString` 最大化了移除 `verse` 中`数据簇`的效果，因此这种实现很好地说明了移除簇的价值。随着时间的推移，如果你发现需要更通用的 `__toString` 实现，只需给当前方法起一个更具体的名字，并在 verse 模板字符串内部显式地发送新消息即可。

`verse` 方法变得越来越简单，但它仍然有多个职责。这个问题通过代码的结构反映出来——上述方法包含了一个空行。程序员添加空行来表示主题的改变。多个主题的存在意味着多个职责的存在，这使得代码在阅读时更难理解，在更改时更容易被破坏。

尽管 `verse` 方法执行了多项任务，但它*确实*得到了改进。它的模板现在包含四行，呼应了每段诗中的四个短语。每个模板行都足够短，可以在大多数阅读设备上无需换行即可显示。这种方法并非完美，但移除数据簇后提高了它的可读性，并使其意图更加清晰。

## 6.2. 理解条件判断

既然 `Bottles` 的 `quantity`/`container` 数据簇已经解决，现在是时候识别下一个代码气味了。

将注意力转向 `BottleNumber` 类。它充满了条件判断，而且所有这些判断的形式都相同。以下是这些代码：

[Listing 6.5: BottleNumber](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {

  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function __toString(): string {
    return $this->quantity() . " " . $this->container();
  }

  public function quantity(): string {
    if ($this->number === 0) {
      return "no more";
    } else {
      return (string)$this->number;
    }
  }

  public function container(): string {
    if ($this->number === 1) {
      return "bottle";
    } else {
      return "bottles";
    }
  }

  public function action(): string {
    if ($this->number === 0) {
      return "Go to the store and buy some more";
    } else {
      return "Take " . $this->pronoun() . " down and pass it around";
    }
  }

  public function pronoun(): string {
    if ($this->number === 1) {
      return "it";
    } else {
      return "one";
    }
  }

  public function successor(): int {
    if ($this->number === 0) {
      return 99;
    } else {
      return $this->number - 1;
    }
  }
}
```

上述条件判断与第 5 章中坚持使用消息章节中被强烈反对的非常相似。区别在于，它们现在依赖于 `number` 属性，而之前它们依赖于 `number` *参数*。

简要回顾一下那个转变可能会有所帮助。以下是方法在第 5 章中依赖 `number` 参数时的样子：

[Listing 6.6: Original Container Method Takes Number Argument](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c5-extract-class-10/lib/Bottles.php#L5-L66)

```php
class Bottles {

  // ...
  public function container(int $number): string {
    if ($number === 1) {
      return "bottle";
    } else {
      return "bottles";
    }
  }
  // ...
}
```

第 5 章认为，与其注入一个对象并有条件地为其提供行为，你应该安排代码，使得你只需要将消息转发给注入的对象。下面的代码展示了这种假设可能的写法：

Listing 6.7: 理想主义的容器方法

```php
class Bottles {
  //...
  public function container(object $smarterNumber): string {
    $smarterNumber->container();
  }
  //...
}
```

事实上，第 5 章引入了一个与上面显示的非常相似的方法。在该章节中，`Bottles` 的 `container(number)` 转发方法在重构早期出现，并存在了短暂（但有用）的。最终，代码被更改为在 `Bottles` 的 `verse` 方法内部缓存 `BottleNumber`，这使得所有的转发方法都失效了并导致了它们的删除。

因此，第 5 章反对条件判断，识别了对反复传递的参数的依赖，识别了*基本类型痴迷*（Primitive Obsession）代码气味，并提取了 `BottleNumber` 类来治愈这种痴迷。

提取 `BottleNumber` 确实从 `Bottles` 中移除了条件判断，但它们并没有消失：*它们只是移动了*到新提取的类中。虽然有所改进，即方法现在使用 `number` 属性而不是接收 `number` 参数，但它们（除 `__toString` 外）仍然包含条件判断。这些条件判断刻画了该类的特征，使得 *Switch 语句*成为最容易识别的代码气味。

Fowler 提供了几种治疗配方。主要的竞争者是 `用策略替换条件判断` 和 `用多态替换条件判断`。

这一奇迹依赖于“多态”（polymorphism），这个词结合了“poly”（多）和“morphs”（形式）。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。

### 6.3.1. 拆解条件判断

当前的代码不是多态的。不仅 `Bottles` 的 `verse` 方法显式地引用了具体的 `BottleNumber` 类，而且 `BottleNumber` 本身包含了许多由条件判断的方法，这些方法返回不同的结果。如果这段代码*依赖于多态*，那么这些条件中的逻辑将分散在几个不同类型的对象中，而 `verse` 将对 `BottleNumber` 的存在感知不到。

根据*定义*，多态涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {
  public function __toString(): string {
  public function quantity(): string {
  public function container(): string {
  public function action(): string {
  public function pronoun(): string {
  public function successor(): int {
}
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {
  // ...
  public function quantity(): string {
    if ($this->number === 0) {
      return "no more";
    } else {
      return (string)$this->number;
    }
  }
  // ...
}
```

上述方法是通过遵循*群集规则*（Flocking Rules）创建的，并在*提取类*（Extract Class）重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {
  // ...
  public function quantity(): string {
    if ($this->number === 0) {
  // ...
  public function container(): string {
    if ($this->number === 1) {
  // ...
  public function action(): string {
    if ($this->number === 0) {
  // ...
  public function pronoun(): string {
    if ($this->number === 1) {
  // ...
  public function successor(): int {
    if ($this->number === 0) {
  // ...
}
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一点的显而易见，[检查相等性的益处的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {
  public function __toString(): string {
  public function quantity(): string {
  public function container(): string {
  public function action(): string {
  public function pronoun(): string {
  public function successor(): int {
}
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```php
class BottleNumber {
  // ...
  public function quantity(): string {
    if ($this->number === 0) {
      return "no more";
    } else {



## 重构过程

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一点的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一点的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一点的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一点的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```



这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {
2   public function __toString(): string {
3   public function quantity(): string {
4   public function container(): string {
5   public function action(): string {
6   public function pronoun(): string {
7   public function successor(): int {
8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5       return "no more";
 6     } else {
 7       return (string)$this->number;
 8     }
 9   }
10   // ...
11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5   // ...
 6   public function container(): string {
 7     if ($this->number === 1) {
 8   // ...
 9   public function action(): string {
10     if ($this->number === 0) {
11   // ...
12   public function pronoun(): string {
13     if ($this->number === 1) {
14   // ...
15   public function successor(): int {
16     if ($this->number === 0) {
17   // ...
18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。



上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }

```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }

```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }

```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```



上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {
2   public function __toString(): string {
3   public function quantity(): string {
4   public function container(): string {
5   public function action(): string {
6   public function pronoun(): string {
7   public function successor(): int {
8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5       return "no more";
 6     } else {
 7       return (string)$this->number;
 8     }
 9   }
10   // ...
11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5   // ...
 6   public function container(): string {
 7     if ($this->number === 1) {
 8   // ...
 9   public function action(): string {
10     if ($this->number === 0) {
11   // ...
12   public function pronoun(): string {
13     if ($this->number === 1) {
14   // ...
15   public function successor(): int {
16     if ($this->number === 0) {
17   // ...
18 }
```



## 代码示例

```
 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {

2   public function __toString(): string {

3   public function quantity(): string {

4   public function container(): string {

5   public function action(): string {

6   public function pronoun(): string {

7   public function successor(): int {

8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5       return "no more";

 6     } else {

 7       return (string)$this->number;

 8     }

 9   }

10   // ...

11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {

 2   // ...

 3   public function quantity(): string {

 4     if ($this->number === 0) {

 5   // ...

 6   public function container(): string {

 7     if ($this->number === 1) {

 8   // ...

 9   public function action(): string {

10     if ($this->number === 0) {

11   // ...

12   public function pronoun(): string {

13     if ($this->number === 1) {

14   // ...

15   public function successor(): int {

16     if ($this->number === 0) {

17   // ...

18 }
```



上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于 `message`，而无需关心接收者的 `type`（或类）。消息的 `Senders` 不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {
2   public function __toString(): string {
3   public function quantity(): string {
4   public function container(): string {
5   public function action(): string {
6   public function pronoun(): string {
7   public function successor(): int {
8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5       return "no more";
 6     } else {
 7       return (string)$this->number;
 8     }
 9   }
10   // ...
11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5   // ...
 6   public function container(): string {
 7     if ($this->number === 1) {
 8   // ...
 9   public function action(): string {
10     if ($this->number === 0) {
11   // ...
12   public function pronoun(): string {
13     if ($this->number === 1) {
14   // ...
15   public function successor(): int {
16     if ($this->number === 0) {
17   // ...
18 }
```



## 拆解条件判断

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5   // ...
 6   public function container(): string {
 7     if ($this->number === 1) {
 8   // ...
 9   public function action(): string {
10     if ($this->number === 0) {
11   // ...
12   public function pronoun(): string {
13     if ($this->number === 1) {
14   // ...
15   public function successor(): int {
16     if ($this->number === 0) {
17   // ...
18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

至此，继续移除条件判断。记得 `BottleNumber` 包含以下方法：

[Listing 6.8: BottleNumber 概念](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
1 class BottleNumber {
2   public function __toString(): string {
3   public function quantity(): string {
4   public function container(): string {
5   public function action(): string {
6   public function pronoun(): string {
7   public function successor(): int {
8 }
```

这些方法构成了一份“瓶相关”概念的列表。方法实现（`__toString` 除外）共享以下形状：

[Listing 6.9: BottleNumber 条件形状](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5       return "no more";
 6     } else {
 7       return (string)$this->number;
 8     }
 9   }
10   // ...
11 }
```

上述方法是通过遵循*群集规则*创建的，并在*提取类*重构期间进行了简化。这个条件判断代表了一个极其稳定的落点。一旦你让代码变成这种形状，就可以庆祝了——问题已经几乎解决了。

`BottleNumber` 代表了一种聪明的、类瓶的数字。它的逻辑在绝大多数情况下对大多数数字来说都是正确的，但尚未在所有情况下都适用于所有数字。少数*特定*数字还不足够聪明。代码的一致性使得很容易看出哪些数字是缺失的。下方的代码提取包含了一个非常广泛的提示：

[Listing 6.10: 某些数字是特殊的](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-87/lib/Bottles.php#L29-L79)

```
 1 class BottleNumber {
 2   // ...
 3   public function quantity(): string {
 4     if ($this->number === 0) {
 5   // ...
 6   public function container(): string {
 7     if ($this->number === 1) {
 8   // ...
 9   public function action(): string {
10     if ($this->number === 0) {
11   // ...
12   public function pronoun(): string {
13     if ($this->number === 1) {
14   // ...
15   public function successor(): int {
16     if ($this->number === 0) {
17   // ...
18 }
```

上面的内容清楚地表明 `0` 和 `1` 是特殊的，并且需要更聪明。这一事实的显而易见，是[检查相等性的益处]的致敬。

这段代码让人想起了原始痴迷（primitive obsession）。然而，这里的执着点是特定的整数（`0` 或 `1`），而不是整个整数。痴迷通常通过提取一个类来治愈。

发送者并不关心接收者是什么；相反，它们依赖于接收者做什么。多态允许发送者依赖于`message`，而无需关心接收者的`type`（或类）。消息的`Senders`不需要关心正在与哪一个可能的接收者通信。在面向对象（OO）中，多态指的是存在多种不同类型的对象，它们对相同的消息做出响应。这一奇迹依赖于“多态”，这个词结合了“poly”（多）和“morphs”（形式）。

多态，*根据定义*，涉及一种以上的对象，因此从过程化的代码安排变为多态代码安排将增加类的总数。这反过来迫使你添加感知这些新类存在、并理解哪个类适用于什么条件的新代码。因此，随着条件判断从 `BottleNumber` 中消失，新的依赖关系将会产生。这些新的依赖关系可能会让代码变得杂乱，因此在随后的示例中对它们进行了细致的管理。

（注：由于输入文本中存在大量重复内容，翻译已按逻辑结构去重处理并对齐。）

[Listing 6.14: 诗句方法知道 BottleNumber 类名](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-110/lib/Bottles.php#L5-L27)

```
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     $bottleNumber = new BottleNumber($number);
5     $nextBottleNumber = new BottleNumber($bottleNumber->successor());
6     // ...
7   }
8 }
```

上述第 4 行和第 5 行都创建了 `BottleNumber` 的实例。既然你正在拆解条件判断，在某些情况下你现在实际上需要一个 `BottleNumber0` 的实例。

确保正确类型的瓶数量的一种方法是修改代码，根据 `number` 的值来选择类，如下例所示：

```php
$bottleNumber =
  ($number === 0 ? new BottleNumber0($number) : new BottleNumber($number));

$succ = $bottleNumber->successor();

$nextBottleNumber =
  ($succ   === 0 ? new BottleNumber0($succ)   : new BottleNumber($succ));
```

这种方法虽然可行，但显然不是最优的。它在一个整个目标都是移除条件判断的练习中引入了一个新的、重复的条件判断。这种改变会适得其反。相反，既然现在有多个类充当了瓶数量的角色，你需要共享的逻辑来选择正确的类。

### 6.3.2. 对象的制造

当多个类扮演共同的角色时，某些地方的某些代码必须知道如何为任何特定情况选择正确的角色扮演类。这种*选择*通常涉及一个条件判断，该条件判断应该存在且只存在于地方。这样的代码被称为“制造”（manufacture）正确类型对象的实例，因此通常被称为工厂（factory）。第 7 章将更详细地讨论工厂，但目前，请将工厂看作一个方法，其职责是返回正确的角色扮演对象。

当为某个角色存在一个工厂时，该工厂承担着创建该角色所需对象的唯一责任。工厂的目的是隔离具体类的名称，并隐藏选择正确类所需的逻辑。在创建工厂之后，你可能不再在应用程序的其他部分引用这些类的名称，或重复这种选择逻辑。

既然 `BottleNumber0` 已经存在，你需要一个瓶数量工厂。第一步是进行小幅重构，在 `Bottles` 的单个方法中隔离瓶数量的创建过程。

这里是新方法：

[Listing 6.15: 简单的瓶数量工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-120/lib/Bottles.php#L5-L31)

```php
1 class Bottles {
2   // ...
3   public function bottleNumberFor(int $number): BottleNumber {
4     return new BottleNumber($number);
5   }
6 }
```



`bottleNumberFor` 方法在对 `BottleNumber` 的需求与其创建之间引入了一层间接。它在代码中引入了一个缝隙，这使得在不担心破坏调用者的情况下更改工厂的工作方式成为可能。制造正确的对象是工厂的责任，而查询工厂瓶数量是所有代码的责任。

一旦 `bottleNumberFor` 存在，就可以像这里所示那样修改 `verse` 方法来调用它：

[Listing 6.16: 诗句方法知道工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-140/lib/Bottles.php#L5-L31)

```php
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     $bottleNumber = $this->bottleNumberFor($number);
5     $nextBottleNumber = $this->bottleNumberFor($bottleNumber->successor());
6     // ...
7   }
8 }
```

`bottleNumberFor` 方法承担了制造瓶数量的责任。到目前为止这一个直直接的重构，但现在新方法已经到位，你可以扩展它的行为。

以下示例更改了工厂，使其在选择返回哪种瓶数量时考虑 `number` 的值：

[Listing 6.17: 工厂方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-150/lib/Bottles.php#L5-L35)

```php
1 class Bottles {
2   // ...
3   public function bottleNumberFor(int $number): BottleNumber {
4     if ($number === 0) {
5       return new BottleNumber0($number);
6     } else {
7       return new BottleNumber($number);
8     }
9   }
10 }
```

上述代码有效，但并不完美。问题在于条件的分支将不同的部分（`BottleNumber0` 和 `BottleNumber`）与相同的部分（`return new($number)`）混合在一起了。这种混淆迫使读者研究代码以区分差异。

下面的方案采取了不同的策略：

[Listing 6.18: If 语句返回对象](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-170/lib/Bottles.php#L5-L36)

```php
1 class Bottles {
2   // ...
3   public function bottleNumberFor(int $number): BottleNumber {
4     if ($number === 0) {
5       $className = BottleNumber0::class;
6     } else {
7       $className = BottleNumber::class;
8     }
9     return new $className($number);
10   }
11 }
```

这个版本的用处是它隔离了变化的部分，从而突显了条件之间的差异。

现在 `verse` 正在调用工厂来获取合适的瓶数量，你可以从 `BottleNumber` 的 `quantity` 方法中移除默认值（`false` 分支）以外的所有内容。

这是生成的代码：

[Listing 6.19: BottleNumber 数量方法简化为默认值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-180/lib/Bottles.php#L38-L84)

```php
1 class BottleNumber {
2   // ...
3   public function quantity(): string {
4     return (string)$this->number;
5   }
6   // ...
7 }
```

在此点，测试仍然应该通过。测试通过证明工厂为每种情况制造了正确的瓶数量。

简单回顾，`BottleNumber` 的 `quantity` 方法最初包含一个条件，检查 `number` 是否等于 `0`。该条件在 `false` 分支中提供通用行为，在 `true` 分支中提供针对 `0` 的特定行为。条件的存在表明需要一个新类来代表 `0`。

`BottleNumber` 被继承为 `BottleNumber0`，并将 `quantity` 方法复制其中。这里是该点的情况：

[Listing 6.20: 重复数量方法的 BottleNumber0](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-100/lib/Bottles.php#L29-L89)

```php
1 class BottleNumber {
2   // ...
3   public function quantity(): string {
4     if ($this->number === 0) {
5       return "no more";
6     } else {
7       return (string)$this->number;
8     }
9   }
10   // ...
11 }
12 
13 class BottleNumber0 extends BottleNumber {
14   public function quantity(): string {
15     if ($this->number === 0) {
16       return "no more";
17     } else {
18       return (string)$this->number;
19     }
20   }
21 }
```

下一个目标是将子类的条件减少到其 `true` 分支，并将父类的减少到其 `false` 分支。子类的更改没有问题，但修改父类会导致测试失败。这种潜在的失败暴露了需要在这些类之间进行选择的需求。因此创建了 `bottleNumberFor` 工厂方法，之后测试再次通过。

结果代码重复如下：

[Listing 6.21: 工厂选择多态对象](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-180/lib/Bottles.php#L5-L90)

```php
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     $bottleNumber = $this->bottleNumberFor($number);
5     $nextBottleNumber = $this->bottleNumberFor($bottleNumber->successor());
6     // ...
7   }
8 
9   public function bottleNumberFor(int $number): BottleNumber {
10     if ($number === 0) {
11       $className = BottleNumber0::class;
12     } else {
13       $className = BottleNumber::class;
14     }
15     return new $className($number);
16   }
17 }
18 
19 class BottleNumber {
20   // ...
21   public function quantity(): string {
22     return (string)$this->number;
23   }
24   // ...
25 }
26 
27 class BottleNumber0 extends BottleNumber {
28   public function quantity(): string {
29     return "no more";
30   }
31 }
```

上面的示例说明了多态的力量。`BottleNumber` 和 `BottleNumber0` 都扮演着瓶子数量的 `role`。它们对相同的消息做出响应并遵循相同的 API，但以完全不同的方式实现了 `quantity`。

这些类是彼此可以替换的。当你调用工厂来获取瓶子数量时，你不需要知道返回对象的类类型。你只需要信任该对象会像瓶子数量一样运行，并对你计划发送的消息做出响应。

这种对类型的“刻意忽略”是面向对象编程的基础。它使调用工厂的代码免受该工厂内部实现变更的影响。通过拒绝感知与你交互的对象的类，你赋予了他人在不编辑代码源码的情况下更改你代码行为的自由。在遥远的未来，有人可以修改工厂以返回新引入的瓶子数量角色实现者，而你现有的代码会乐意与这些意料之外的对象协作。

`quantity` 方法现在通过多态实现了。现在是时候处理剩余的条件语句了。

### 6.3.3. 盛行多态

你已经经历了一完整轮的 `用多态替换条件语句`，重构的剩余部分只是重复操作。以下是该配方步骤的列表：

1. 创建一个子类来代表你进行 `switch` 的值。
    1. 将一个在该值上切换的方法复制到子类中。
    2. 在子类中，删除条件中真分支以外的所有内容。
        1. 在此时，如果工厂不存在，则创建一个工厂，并且，
        2. 如果尚未包含，则将此子类添加到工厂中。
    3. 在父类中，删除条件中假分支以外的所有内容。
    4. 重复步骤 a-c，直到所有在该值上切换的方法都分散完毕。
2. 迭代，直到对于每个你进行 switch 的不同值都存在一个子类。

对 `action` 和 `successor` 方法（两者都测试了 `0`）遵循这些步骤，将得到如下代码：

[Listing 6.22: 0 有它自己的类](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-280/lib/Bottles.php#L38-L90)

```php
1 class BottleNumber {
2   protected $number;
3 
4   public function __construct(int $number) {
5     $this->number = $number;
6   }
7 
8   public function __toString(): string {
9     return $this->quantity() . " " . $this->container();
10   }
11 
12   public function quantity(): string {
13     return (string)$this->number;
14   }
15 
16   public function container(): string {
17     if ($this->number === 1) {
18       return "bottle";
19     } else {
20       return "bottles";
21     }
22   }
23   
24   public function action(): string {
25     return "Take " . $this->pronoun() . " down and pass it around";
26   }
27 
28   public function pronoun(): string {
29     if ($this->number === 1) {
30       return "it";
31     } else {
32       return "one";
33     }
34   }
35 
36   public function successor(): int {
37     return $this->number - 1;
38   }
39 }
40 
41 class BottleNumber0 extends BottleNumber {
42   public function quantity(): string {
43     return "no more";
44   }
45 
46   public function action(): string {
47     return "Go to the store and buy some more";
48   }
49 
50   public function successor(): int {
51     return 99;
52   }
53 }
```

`quantity`、`action` 和 `successor` 方法现在分布在 `BottleNumber` 和 `BottleNumber0` 之间。这完成了针对 `0` 的瓶子数量。

下一个任务是对 `1` 重复此过程。在此之前，第一步创建一个空类：[Listing 6.23: 创建类](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-290/lib/Bottles.php#L92)

```php
1 class Bottle1
```

接下来，选择一个专注于 `1` 的方法并将其复制到子类。`container` 方法是一个合理的开始点：[Listing 6.24: 复制方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-300/lib/Bottles.php#L8)

```php
1 class BottleNumber {
2   // ...
3   public function container(): string {
4     if ($this->number === 1) {
5       return "bottle";
6     } else {
7       return "bottles";
8     }
9   }
10  // ...
11 }
12 class Bottle1 extends BottleNumber {
```

接下来，从子类中删除真分支以外的所有内容：[Listing 6.25: Bottle1 返回正确结果](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-320/lib/Bottles.php#L92)

```php
1 class Bottle1 extends BottleNumber {
2   public container(): string {
3     return "bottle";
4 }
```

现在，从父类中删除假分支以外的所有内容：[Listing 6.26: BottleNumber 方法默认值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-330/lib/Bottles.php#L38)

```php
1 class BottleNumber {
2   // ...
3   public function container(): string {
4     return "bottles";
5   }
6   // ...
7 }
```

遗憾的是，测试现在失败了：

```
1) BottlesTest::test_1
2 Failed asserting two strings are equal.
3 ---
4 +++ Actual
5 @@
6 -'1 bottle of beer on the wall, 1 bottle of beer.\n
7 +'1 bottles of beer on the wall, 1 bottles of beer.\n
8  Take it down and pass it around, no more bottles of beer on the wall.\n
9 '
```



针对第一句的测试失败是因为它得到了 `1 bottles` 而期望 `1 bottle`。这可能会让人困惑，因为你知道 `Bottle1` 正确地实现了 `container` 来返回 `bottle`。然而，问题不在于 `Bottle1` 是错误的，而是由于工厂尚未返回它。

按照目前的写法，每创建一个新的瓶子数量类都需要更新工厂。因此，下面的示例更改了 `bottleNumberFor`，在 `number` 值为 `1` 时返回 `BottleNumber1` 实例：[Listing 6.27: 工厂知道 Bottle1](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-360/lib/Bottles.php#L5)

```php
 1 class Bottles {

 2   // ...

 3   public function bottleNumberFor(int $number): BottleNumber {

 4     switch ($number) {

 5     case 0:

 6       $className = BottleNumber0::class;

 7       break;

 8     case 1:

 9       $className = BottleNumber1::class;

 10      break;

 11     default:

 12       $className = BottleNumber::class;

 13       break;

 14     }

 15     return new $className($number);

 16   }

 17 }
```

在添加新类时，语法也从 `if` 更改为 `case`，正如之前讨论过的样。

上述条件可能让你产生一种似曾相识（dejà vu）。它让你想起了原始的 Shameless Green 解决方案中的 `switch` 语句，尽管并不完全相同。在完成当前的重构时，请思考一下为什么会这样。相似之处将在本节末尾进行探讨。

现在 `BottleNumber1` 的实例正在被制造，测试再次通过，你可以继续处理 `pronoun`。一旦解决了 `pronoun` 的问题，最终代码如下：

[列表 6.28：BottleNumber 层次结构](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-420/lib/Bottles.php#L5-L98)

```php
 1 class Bottles {

 2   public function song(): string {

 3     return $this->verses(99, 0);

 4   }

 5 

 6   public function verses(int $upper, int $lower): string {

 7     return implode(

 8       "\n",

 9       array_map([$this, 'verse'], range($upper, $lower))

10     );

 11   }

 12 

 13   public function verse(int $number): string {

 14     $bottleNumber = $this->bottleNumberFor($number);

 15     $nextBottleNumber = $this->bottleNumberFor($bottleNumber->successor());

 16 

 17     return

 18       ucfirst("{$bottleNumber} of beer on the wall, ") .

 19       "{$bottleNumber} of beer.\n" .

 20       "{$bottleNumber->action()}, " .

 21       "{$nextBottleNumber} of beer on the wall.\n";

 22   }

 23 

 24   public function bottleNumberFor(int $number): BottleNumber {

 25     switch ($number) {

 26     case 0:

 27       $className = BottleNumber0::class;

 28       break;

 29     case 1:

 30       $className = BottleNumber1::class;

 31       break;

 32     default:

 33       $className = BottleNumber::class;

 34       break;

 35     }

 36     return new $className($number);

 37   }

 38 }

 39 

 40 class BottleNumber {

 41   protected $number;

 42 

 43   public function __construct(int $number) {

 44     $this->number = $number;

 45   }

 46 

 47   public function __toString(): string {

 48     return $this->quantity() . " " . $this->container();

 49   }

 50 

 51   public function quantity(): string {

 52     return (string)$this->number;

 53   }

 54 

 55   public function container(): string {

 56     return "bottles";

 57   }

 58 

 59   public function action(): string {

 60     return "Take " . $this->pronoun() . " down and pass it around";

 61   }

 62 

 63   public function pronoun(): string {

 64     return "one";

 65   }

 66 

 67   public function successor(): int {

 68     return $this->number - 1;

 69   }

 70 }

 71 

 72 class BottleNumber0 extends BottleNumber {

 73   public function quantity(): string {

 74     return "no more";

 75   }

 76 

 77   public function action(): string {

 78     return "Go to the store and buy some more";

 79   }

 80 

 81   public function successor(): int {

 82     return 99;

 83   }

 84 }

 85 

 86 class BottleNumber1 extends BottleNumber {

 87   public function container(): string {

 88     return "bottle";

 89   }

 90 

 91   public function pronoun(): string {

 92     return "it";

 93   }

 94 }
```

上述条件可能让你产生一种似曾相识的感觉。它让你想起了原始 Shameless Green 解决方案中的 `switch` 语句。在完成当前的重构时，请思考一下为什么会这样。这种相似之处将在本节末尾进行探讨。

现在 `BottleNumber1` 的实例正在被制造，测试再次通过，你可以继续处理 `pronoun`。一旦解决了 `pronoun` 的问题，最终代码如下：

### 6.4. 类型之间的转换

第 5 行的 Liskov 违背（Liskov violation）在多次重构中都存在，但为了修复其他代码异味（code smells），它被忽略了。在解决问题之前，回顾它的起源是有很有意义的。

在第 4 章，当 `successor` 方法在 `Bottles` 中首次创建 时，并没有违背。该方法是使用聚群规则（Flocking Rules）从 `verse` 模板中提取的，而在那个原始模板中，`successor` 确实是一个数字。在这种情况下，让 `successor` 返回该数字是合理且正确的。

Liskov 违反是隐蔽的，随着时间的推移会产生危害。随着应用程序的演进，`successor` 可能从很多地方调用。每个地方都必须知道 `successor` 返回一个数字，并且必须知道如何将其转换瓶数。这种知识网将每个 `successor` 的调用者与其当前的实现绑定，导致了难以修改的依赖关系。

如果 `successor` 遵循 Liskov 原则，你可以用下面第 6 行的假设代码替换第 5 行的代码：

```php
 1 class Bottles {

 2   // ...

 3   public function verse(int $number): string {

 4     $bottleNumber = $this->bottleNumberFor($number);

 5     $nextBottleNumber = $this->bottleNumberFor($bottleNumber->successor());

 6     //$nextBottleNumber = bottleNumber->successor();

 7     // ...

 8   }

 9   // ...

 10 }
```

在上面的第 6 行，`successor` 方法返回一个瓶数。这种实现避免了 Liskov 违背，减少了依赖关系，并简化了代码。

在第 5 章中，`successor` 方法被确定为一个过度关注 `number` 参数的方法，因此在*提取类*（Extract Class）重构过程中它被迁移到了 `BottleNumber`。正是在此时，出现了 Liskov 原则违反。问题的根源在于引入了一个新类型（`BottleNumber`），但它的 `successor` 方法继续返回旧类型（`int`）。

Liskov 原则违反在第 5 章的最终代码示例 中已经足够令人困扰，那里只包含 `successor` 的一个实现者和一个发送者。遗憾的是，本章的重构加剧了这个问题。现在 `successor` 有两个实现者、一个发送者，以及一个负责瓶号数构造的新工厂。推迟 Liskov 违反让情况变得糟糕，但自矛盾的是，它提供了一个更有助于学习解决的示例。

目前的困境代表了现实世界中的问题：需要更改一个具有多个实现者和多个发送者的多态方法的返回类型。这种现实中的困难可能包含许多部分，以至于无法一次性修复。以下技术可用于解决任何规模的类型更改问题。它通过随着时间进行微小的、可靠的、*独立的*的变化，逐步击破直到最终解决整个问题。

以下是与 `successor` 相关的代码总结：

[Listing 6.30：关于 Successor 的一切](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-430/lib/Bottles.php#L5-L89)

```php
 1 class Bottles {

 2   // ...

 3   public function verse(int $number): string {

 4     $bottleNumber = $this->bottleNumberFor($number);

 5     $nextBottleNumber = $this->bottleNumberFor($bottleNumber->successor());

 6     // $nextBottleNumber = $bottleNumber->successor();

 7 

 8     return

 9       ucfirst("{$bottleNumber} of beer on the wall, ") .

10       "{$bottleNumber} of beer.\n" .

11       "{$bottleNumber->action()}, " .

12       "{$nextBottleNumber} of beer on the wall.\n";

13   }

 14 

 15   public function bottleNumberFor(int $number): BottleNumber {

 16     switch ($number) {

 17     case 0:

 18       $className = BottleNumber0::class;

 19       break;

 20     case 1:

 21       $className = BottleNumber1::class;

 22       break;

 23     default:

 24       $className = BottleNumber::class;

 25       break;

 26     }

 27     return new $className($number);

 28   }

 29 }

 30 

31 class BottleNumber {

 32   // ...

 33   public function successor(): int {

 34     return $this->number - 1;

 35   }

 36 }

 37 

 38 class BottleNumber0 extends BottleNumber {

 39   // ...

 40   public function successor(): int {

 41     return 99;

 42
```

在上面的第 5 行，`verse` 方法知道 `successor` 返回一个数字，但它希望它能像第 6 行所示那样返回一个瓶号。两个 `successor` 方法（第 33 行和第 40 行）应该返回瓶号，为了做到这一点，它们必须调用工厂，而工厂并不容易触及。遗憾的是，上述困难由于你坚持通过一系列单行更改来解决问题而变得更加复杂。

在几个地方需要进行更改。最终：
1. 工厂应该放置在使得 `successor` 方法可以触及的地方，
2. `successor` 方法应该调用工厂，并且
3. `verse` 方法应该期望 `successor` 返回瓶号。

这个列表很短，但尽管如此，要通过一系列不破坏测试的单行更改来完成它仍然具有挑战性。对于这种规模的问题，*可能会*成功地一次性更改所有内容，但现实生活通常涉及更大的问题，需要更多的更改。以下逐步推进的策略非常有用，因为它适用于任何规模的问题。虽然在小问题上它可能过过了，但在大问题上它深令人宽慰。

本着这种精神，继续编写代码。第一步是将工厂放在 `successor` 的可触及范围内。有许多选项，但如果你想做出尽可能小的更改，最佳选择是将工厂变为现有类上的静态函数。在现有类中最合理的选择是 `BottleNumber`。

下面的示例将工厂复制到 `BottleNumber` 的一个静态函数中：

[Listing 6.31：BottleNumber 类包含工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-440/lib/Bottles.php#L45-L90)

```php
 1 class BottleNumber {

 2   // ...

 3   public static function for(int $number): BottleNumber {

 4     switch ($number) {

 5     case 0:

 6       $className = BottleNumber0::class;

 7       break;

 8     case 1:

 9       $className = BottleNumber1::class;

 10      break;

 11     default:

 12       $className = BottleNumber::class;

 13       break;

 14    }

 15    return new $className($number);

 16  }

 17  // ...

 18 }
```



你可以看到，在这里 `BottleNumber` 中，方法名被简化为了 `for`。

实现没有改变，只是方法名变了。在 `Bottles` 中，这个方法名完美地包含了两个部分：一个类型和一个通用请求。

正如在第 1 章的 `beer` 方法中所示，`bottleNumberFor` 是既多余又具体的。将它命名为 `for` 有两个很好的理由。

首先，更改名称避免了“回声室”效应。`bottleNumberFor` 与当前上下文紧耦合，而紧耦合使得代码难以更改。例如，如果有一天你决定重命名 `BottleNumber` 类，你也将更改这个方法名。

其次，更抽象地说，`for` 支持多态。为了说明这一点，考虑 `__toString`。类实现此方法以控制它们在被视为字符串时的反应。应用程序想要字符串表示的部分隐式或显式地调用此方法。

思考一下如果这种交易不存在会怎样。如果每个类都使用唯一的字符串化方法名，甚至用类型限定字符串化方法名（`bottleToString`），你必须知道对象的类型才能知道调用哪个方法。这会严重干扰你的代码。让可字符串化的对象多态地实现同名方法 `__toString`，并让其他部分预期该方法已实现简单得多。

就像 `__toString` 一样，`for` 是一个通用请求，可以很好地作为任何工厂的名字。当工厂对象多态地实现 `for` 时，你可以不考虑接收者的类型而发送此消息。多态保留了工厂本身可替换的选择。

现在 `for` 工厂方法已经存在，你可以修改 `verse` 来调用它，如下：

[Listing 6.32：Verse 方法使用工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-460/lib/Bottles.php#L5-L43)

```php
class Bottles {

  // ...
  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);
    $nextBottleNumber = BottleNumber::for($bottleNumber->successor());
    // ...
  }

  // ...
}
```

上面的第 4 行和第 5 行直接调用 `BottleNumber` 中的工厂。这使得 `bottleNumberFor` 变得过时。该方法现在可以删除了。

现在，两个 `successor` 方法都可以轻松触及工厂，所以你完成了第一步。

步骤 2 要求你更改两个 `successor` 方法以调用工厂，但遗憾的是，如果在不同进行所有剩余更改的情况下，修改其中任何一个都会导致测试失败。事实上，在此时，每一个未完成的更改都会破坏测试。

例如，在步骤 3 中，你可能希望将 `verse` 方法更改为如下：

```php
$nextBottleNumber = $bottleNumber->successor()
```

而不是：

```php
$nextBottleNumber = BottleNumber::for($bottleNumber->successor)
```

然而，上述操作依赖于已完成步骤 2，因为该步骤将 `successor` 方法更改为返回瓶子数字对象。你不能跳过步骤 2 直接执行步骤 3。

回到步骤 2，现在 `successor` 方法可以调用工厂了。但是，通过以下方式修改其中一个（但不修改另一个）：

```php
BottleNumber::for(99)
```

或者：

```php
BottleNumber::for($number - 1)
```

同样会导致测试失败。

问题的根源在于 `verse` 方法期望 `successor` 返回一个可以在工厂中使用的对象，而工厂又期望接收一个数字。如果你将其中一个 `successor` 方法更改为返回瓶子数字，那么 `verse` 将错误的类型传递给瓶子数字工厂，从而破坏测试。

由于你正在更改 `successor` 的类型，此次重构的第一步是临时移除工厂和 `successor` 方法中的类型声明，如下所示：

```php
class BottleNumber {

  // ...
  public static function for($number): BottleNumber {

    // ...
  }

  // ...
}
```

```php
class BottleNumber {

  // ...
  public function successor() {

    // ...
  }
}

class BottleNumber0 extends BottleNumber {

  // ...
  public function successor() {

    // ...
  }
}
```

放弃类型声明后，使用“单次撤销”更改（后文将详细介绍）继续前进的技巧，是临时修改工厂以容忍两种类型的输入。在一个 `successor` 方法返回瓶子数字而另一个方法返回原始类型的过渡期间，工厂必须处理这两种类型。这要求做一些违背你对象导向灵魂的事：你必须更改工厂以检查其输入参数的类型。

以下是代码：

[Listing 6.33: 如果已经是瓶子数字则返回参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-480/lib/Bottles.php#L30-L79)

```php
class BottleNumber {

  // ...
  public static function for($number): BottleNumber {

    if ($number instanceof BottleNumber) {
      return $number;
    }

    switch ($number) {
    case 0:
      $className = BottleNumber0::class;
      break;
    case 1:
      $className = BottleNumber1::class;
      break;
    default:
      $className = BottleNumber::class;
      break;
    }
    return new $className($number);
  }

  // ...
}
```

第 4-6 行的守护语句（guard clause）在输入已经是瓶子数字时将其返回。这行代码只在重构进行期间需要。一旦所有 `successor` 方法都返回瓶子数字，且所有 `successor` 的调用者都期望获得瓶子数字，第 4-6 行就可以删除。

如果这段代码看起来很困惑，那是因为命名的问题。例如，如果第 2 行的参数不是 `number` 而是 `numberOrNumber` 呢？在这种情况下：

既然工厂已经处理了两种输入类型，你可以通过更改 `successor` 方法返回瓶子数字来继续步骤 2。这是 `BottleNumber0` 中的更改：

[Listing 6.34: BottleNumber0 返回数字](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-490/lib/Bottles.php#L81-L93)

```php
class BottleNumber0 extends BottleNumber {

  // ...
  public function successor() {

    return BottleNumber::for(99);
  }
}
```

在此处，尽管一个 `successor` 返回数字而另一个返回瓶子数字，测试仍然通过了。

在成功处理 `BottleNumber0` 后，你可以继续 `BottleNumber`：

[Listing 6.35: BottleNumber 返回数字](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-500/lib/Bottles.php#L30-L79)

```php
class BottleNumber {

  // ...
  public function successor() {

    return BottleNumber::for($this->number - 1);
  }
}
```

漂亮，所有的 `successor` 实现都已更新，你完成了步骤 2。

步骤 3 要求更改 `verse` 方法使其期望 `successor` 返回瓶子数字。现在应该这样做。以下代码通过取消注释第 6 行来谨慎测试这一理论：

[Listing 6.36: 测试期望代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-510/lib/Bottles.php#L5-L28)

```php
class Bottles {

  // ...
  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);
    $nextBottleNumber = BottleNumber::for($bottleNumber->successor());
    $nextBottleNumber = $bottleNumber->successor();

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$nextBottleNumber} of beer on the wall.\n";
  }
}
```

上面的第 5 行是原始代码，你希望删除它。它用旧的方式设置 `$nextBottleNumber`。第 6 行是你保留的新代码，它用当前瓶子数字的后继者覆盖了 `$nextBottleNumber`。

通过并排运行旧代码和新代码来实现从旧代码到新代码的过渡，在你不 100% 确定自己写正确的情况下非常有用。如果发生了崩溃，同时观察两种变体可以减轻调试。

在这种情况下，测试继续通过，因此你可以放心地删除上面的第 5 行。这留下了以下代码：

[Listing 6.37: 信任 successor](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-520/lib/Bottles.php#L5-L27)

```php
class Bottles {

  // ...
  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);
    $nextBottleNumber = $bottleNumber->successor();

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$nextBottleNumber} of beer on the wall.\n";
  }
}
```

这无疑是一个改进。然而，注意第 5 行声明的临时变量 `$nextBottleNumber` 仅用了一次，即第 11 行。这提供了进一步简化的机会。仅使用一次的临时变量可以通过*内联临时变量*（Inline Temp）重构移除，结果如下代码：

[Listing 6.38: 简化的 verse 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-540/lib/Bottles.php#L5-L26)

```php
class Bottles {

  // ...
  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

此时，所有的 `successor` 方法都返回一个瓶子数量，且所有 `successor` 的调用者都期望接收一个瓶子数量。剩余的问题是工厂仍然包含守语句（guard clause），并且缺失了类型声明：

[列表 6.39: 带有过时守语句的工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-540/lib/Bottles.php#L28-L77)

```php
class BottleNumber {

  // ...
  public static function for($number): BottleNumber {

    if ($number instanceof BottleNumber) {
      return $number;
    }

    switch ($number) {
    case 0:
      $className = BottleNumber0::class;
      break;
    case 1:
      $className = BottleNumber1::class;
      break;
    default:
      $className = BottleNumber::class;
      break;
    }
    return new $className($number);
  }

  // ...
}
```

该守语句现在已经过时了，可以删除。现在是时候为 `successor` 方法和 `for` 工厂重新添加类型声明了。

这完成了对 `successor` 中里氏替换原则（Liskov violation）违反的修复。以下是代码的完整列表：

[列表 6.40: 完整列表](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-552/lib/Bottles.php#L5-L97)

```php
class Bottles {

  public function song(): string {

    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {

    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}

class BottleNumber {

  protected $number;

  public static function for(int $number): BottleNumber {

    switch ($number) {
    case 0:
      $className = BottleNumber0::class;
      break;
    case 1:
      $className = BottleNumber1::class;
      break;
    default:
      $className = BottleNumber::class;
      break;
    }
    return new $className($number);
  }

  // ...
}
```



```php
$className = BottleNumber::class;

break;

}

return new $className($number);

}

public function __construct(int $number) {

$this->number = $number;

}

public function __toString(): string {

return $this->quantity() . " " . $this->container();

}

public function quantity(): string {

return (string)$this->number;

}

public function container(): string {

return "bottles";

}

public function action(): string {

return "Take " . $this->pronoun() . " down and pass it around";

}

public function pronoun(): string {

return "one";

}

public function successor(): object {

return BottleNumber::for($this->number - 1);

}

}

class BottleNumber0 extends BottleNumber {

public function quantity(): string {

return "no more";

}

public function action(): string {

return "Go to the store and buy some more";

}

public function successor(): object {

return BottleNumber::for(99);

}

}

class BottleNumber1 extends BottleNumber {

public function container(): string {

return "bottle";

}

public function pronoun(): string {

return "it";

}

}
```

```php
1 class BottlesTest extends \PHPUnit\Framework\TestCase {

// ...

}

public function test_the_whole_song() {

$expected = <<< SONG

99 bottles of beer on the wall, 99 bottles of beer.

// ...

8 bottles of beer on the wall, 8 bottles of beer.

Take one down and pass it around, 7 bottles of beer on the wall.

7 bottles of beer on the wall, 7 bottles of beer.

Take one down and pass it around, 1 six-pack of beer on the wall.

1 six-pack of beer on the wall, 1 six-pack of beer.

// ...

1 bottle of beer on the wall, 1 bottle of beer.

Take it down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer.

Go to the store and buy some more, 99 bottles of beer on the wall.

SONG;

$this->assertEquals($expected, (new Bottles())->song());

}

}
```

上面的第 13 行和第 15 行现在断言第 6 段和第 7 段的内容应为“1 six-pack”而不是“6 bottles”。运行更新后的测试会得到此错误：

```
7 bottles of beer on the wall, 7 bottles of beer.
-Take one down and pass it around, 1 six-pack of beer on the wall.
+Take one down and pass it around, 6 bottles of beer on the wall.
-1 six-pack of beer on the wall, 1 six-pack of beer.
+6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.
```

错误信息中显然存在两个问题。首先，输出在应该显示“1”的地方显示了“6”。这就是 `quantity`（数量）的概念。其次，输出是“bottles”而不是“six-pack”（六瓶装）。这就是 `container`（容器）。

`BottleNumber` 的继承层次结构为解决这些问题提供了模范性的指导。遵循 `BottleNumber0` 和 `BottleNumber1` 的模式，首先创建一个作为 `BottleNumber` 子类的新 `BottleNumber6` 类：

[Listing 6.42: 新的 BottleNumber6 类](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-570/lib/Bottles.php#L99-L100)

```php
1 class BottleNumber6 extends BottleNumber {

2

}
```

接下来，实现其中一个必要的方法。例如，你可以如下所示实现 `container`：

[Listing 6.43: BottleNumber6 识别容器](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-580/lib/Bottles.php#L99-L103)

```php
1 class BottleNumber6 extends BottleNumber {

public function container(): string {

return "six-pack";

}

}
```

完成上述更改后，你可以合理地预期错误信息会发生变化，但的是，它并没有：

```
7 bottles of beer on the wall, 7 bottles of beer.
-Take one down and pass it around, 1 six-pack of beer on the wall.
+Take one down and pass it around, 6 bottles of beer on the wall.
-1 six-pack of beer on the wall, 1 six-pack of beer.
+6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.
```

在上方，第六个瓶子仍然报告“bottles”作为它的 `container`。错误信息没有变化。如果新的 `BottleNumber6` 没有被使用，就会发生这种情况，而事实确实如此。因为工厂尚未开放，仅仅创建新类是不够的——你还必须更新工厂。

将 `BottleNumber6` 添加到工厂会得到以下代码：

[Listing 6.44: 向工厂添加 BottleNumber6](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-590/lib/Bottles.php#L28-L76)

```php
1 class BottleNumber {

// ...

public static function for(int $number): BottleNumber {

switch ($number) {

case 0:

$className = BottleNumber0::class;

break;

case 1:

$className = BottleNumber1::class;

break;

case 6:

$className = BottleNumber6::class;

break;

default:

$className = BottleNumber::class;

break;

}

return new $className($number);

}

// ...

}
```

一旦更新了工厂，运行测试就会产生：

```
7 bottles of beer on the wall, 7 bottles of beer.
-Take one down and pass it around, 1 six-pack of beer on the wall.
+Take one down and pass it around, 6 bottles of beer on the wall.
-1 six-pack of beer on the wall, 1 six-pack of beer.
+6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.
```

（注：此处原文存在重复段落，排版已按逻辑去重处理）

### 6.6 保护领域

在继续下去之前，关于 `BottleNumber6` 的最后一点想法：你可能想过通过简单重写 `__toString` 来处理六瓶装的情况。例如，与其实现 `quantity` 和 `container`，你也可以这样做：

Listing 6.46: BottleNumber6 既不识别数量也不识别容器

```php
1 class BottleNumber6 extends BottleNumber {

public function __toString(): string {

return '1 six-pack';

}

}
```

上面的代码确实通过了测试。这种解决方案看起来可能很有吸引力，因为它比上一个短，因此可能感觉更高效。然而，代码少并不总是意味着代码更好。

考虑 `__toString` 与 `quantity` 和 `container` 的意义区别。后者两个方法反映了领域中的核心概念。无论你的应用程序如何使用瓶数，这些概念都存在。

从 `Bottles` 中提取 `BottleNumber` 将“瓶数化”的概念与“99 瓶啤酒”歌解耦。瓶数现在是独立的对象，并且可以在*提取它们的其他上下文*中自由使用。如果与歌曲充分分离，这些瓶数类可以用于例如新的库存系统。当冰箱报告它装有 0 瓶啤酒时，“去商店再买一些”这种操作是完全合理的。

放弃 `quantity` 和 `container`，转而直接将“1 six-pack”硬塞进 `__toString`，会污染 `BottleNumber6`，使其包含了 `Bottles` `verse` 模板的内部机制。`__toString` 解决方案之所以有效，是因为 `BottleNumber6` *知道* `verse` 会隐式地发送 `__toString`。这种预期将 `BottleNumber6` 耦合到了它被发现的上下文中，而这种耦合会干扰你在新上下文出现时重用瓶数类的能力。

通过实现唯一的 `__toString` 来解决眼前的问题虽然通过了今天的测试，但会误导未来的程序员。如果你重写了 `__toString`，你的代码将讲述这样一个故事：

1. `BottleNumber6` 导出其字符串表示的规则与其他瓶号不同，且
2. `BottleNumber6` 与其父类具有相同的 `quantity` 和 `container`。

这些主张是错误的，而且它们将成本从现在转移到了未来。

聪明的捷径是虚假的经济。要投资于能够反映事实的代码。直接把它写下来吧。

## 6.7 总结

本章的目的是产生一种能够对“六瓶装”需求开放的代码结构。它不仅成功地满足了这一需求，而且在此过程中解决了许多其他问题。

本章探索了 `Data Clump`（数据聚集）代码气味。它用一组多态对象替换了 `Switch Statement`（切换语句），这些对象是通过工厂的。它纠正了 `successor` 中违反 Liskov 原则的行为，并以该问题为切入点，引入了关于如何更改多态方法返回类型的更通用课程。

`BottleNumber` 的 `for` 工厂非常直观，而且圆满完成了任务。虽然这种简单工厂在很多情况下效果很好，但它们并不是所有情况下的最佳选择。存在着各种不同风格的工厂等待我们探索。因此，进入第 7 章。

## 7 制造智能

在第 6 章中，在通往实现极致开放代码的过程中，你创建了一组类，它们的实例以多态的方式扮演着瓶号的角色。`BottleNumber` 层次结构中的每个类都包含一组简单的代码，代表单个瓶号变体的具体实现。令人高兴的是，这些类不包含任何条件判断。

然而，对条件逻辑的需求并没有消失。在某些地方，代码必须知道如何为任何情况选择正确的瓶号类。这种选择发生在 `BottleNumber::for` 工厂中。在本章中，这个简单的工厂开启了对通用工厂更广泛的探索。

## 7.1 对比具体工厂与无耻的绿色

上一章中的 `Replace Conditional with Polymorphism`（用多态替换条件判断）重构结果产生了一个小小的瓶号层次结构。该层次结构是对开放的，这使得通过简单添加一个新的 `BottleNumber6` 类来实现六瓶装行为成为可能。

遗憾的是，在一切正常工作之前仍然有一处代码必须修改。`BottleNumber::for` 工厂包含一个硬编码的条件来选择正确的类，而这个条件必须更新以包含新的类名。

以下是生成的工厂回顾：

[Listing 7.1: 瓶号工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c6-polymorphism-600/lib/Bottles.php#L28-L76)

```php
1 class BottleNumber {

// ...
public static function for(int $number): BottleNumber {

switch ($number) {

case 0:

$className = BottleNumber0::class;

break;

case 1:

$className = BottleNumber1::class;

break;

case 6:

$className = BottleNumber6::class;

break;

default:

$className = BottleNumber::class;

break;

}

return new $className($number);

}

// ...

}
```

停下来思考片刻当前代码。上面的 `for` 方法包含一个用于选择类的简单 `switch` 语句。这个条件判断可能会让你想起原始“无耻的绿色”实现中包含的一个，如下文所示：

[Listing 7.2: 无耻的绿色的条件判断](https://github.com/sandimetz/99bottles_php/blob/2.1.1-initial-variations-40/lib/Bottles.php#L15-L42)

```php
1 public function verse(int $number): string {

switch ($number) {

case 0:

return

"No more bottles of beer on the wall, " .

"no more bottles of beer.\n" .

"Go to the store and buy some more, " .

"99 bottles of beer on the wall.\n";

case 1:

return
```



## 7.2. 理解工厂

面向对象的应用程序依赖于多态。多态导致了多个共同角色的类。多态的力量在于，从消息发送者的角度来看，这些扮演角色的对象是可以互换的。

消息发送者可以放心地与多态对象协作，相信它们都诚实地履行共同的角色，尽管它们代表不同的变体。消息发送对象将其协作者看作角色的扮演者，而不是某种类型。

同一角色的所有玩家共享一个公共 API。这个 API 暴露了一组公开的意图。在内部，每个角色执行者还包含了以不同方式实现这些意图的方法。这些替代实现的具体细节对外部世界是不可见的。

从消息发送者的角度来看，同一角色的所有玩家都是完全相同的。消息发送者依赖于角色执行者暴露的意图，同时对它们的详细内部实现保持“刻意的无知”。他们知道协作者在做什么，但拒绝去关注它们是如何做的。

一个由与角色扮演对象协作的消息发送者组成的系统，对于意外的更改具有极高的容忍度。例如，想象你创建了一个新类来代表瓶号的新变体。这个新瓶号与任何其他瓶号都是可互换的，因此任何已经与现有瓶号协作的类都能无缝地与这个新瓶号协作。消息发送者不需要更改；从它的角度来看，这个新瓶号和其他所有号是一样的。

显然，只有当消息发送者真的将协作者视为可互换的时，这个系统才能运作。如果让消息发送者在添加或删除角色执行者时免受副作用的影响，那么这些发送者就不能知道特定变体独有的信息。消息发送者不允许知道具体变体类的名称，也不被允许知道在它们之间进行选择所需的逻辑。

消息发送者无法知道这些信息，但当然，必须有人知道。关于变体类名的知识以及选择正确变体的必要逻辑，可以隐藏在——你猜得没错——工厂中。

工厂的责任是为给定的角色制造正确的对象。工厂不应该知道变体做什么，它们只需要知道如何为任何情况选择正确的变体。这种选择过程通常涉及一个条件判断，将此条件判断放在工厂中允许你将其隔离在代码的单一位置。

因此，工厂是条件判断“去死”的地方。在工厂中隔离条件判断可以松散协作对象之间的耦合，从而降低更改的成本。

工厂可以用许多不同的方式实现，但它们往往在几个有趣的维度上有所变化，每个维度都涉及自己的一套权衡。没有一种工厂风格适用于所有情况；正确的解决方案完全取决于手头的问题。理解这些维度以及它们之间的权衡，可以让你在面对竞争需求时做出良好的决策。

工厂在这些维度上变化：

1. 工厂是对新变体开放的还是关闭的。
2. 选择变体的逻辑可以由工厂拥有，也可以由变体本身拥有。
3. 工厂负责知道/找出哪些类符合制造的条件，或者变体可以自我推销。

接下来的章节将探索一系列递进的工厂解决方案，特别关注沿这些维度的权衡。

### 7.3. 开放工厂

回到当前的问题，当前的工厂并没有对扩展开放，因为它包含一个硬编码的条件判断。

你可能已经注意到瓶号类遵循一种命名约定。默认是 `BottleNumber`，特化类在名称后加上它们特定的 `number` 值后缀，例如 `BottleNumber0`、`BottleNumber1` 和 `BottleNumber6`。

这种可预测的模式使得你能够动态推导出正确的瓶号类。你可以创建与类 `names` 匹配的字符串，然后使用一点元编程将这些类名字符串转换为实际类。

这里是实现此点的简单方法：

[Listing 7.4: 元编程的类查找工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-20/lib/Bottles.php#L28-L66)

```
 1 class BottleNumber {
 2   // ...
 3   public static function for(int $number): BottleNumber {
 4     $className = 'BottleNumber' . $number;
 5     if (!class_exists($className)) {
 6       $className = BottleNumber::class;
 7     }
 8     return new $className($number);
 9   }
10   // ...
11 }
```

上述代码产生的输出与原始工厂相同。在检查之后，你可能会发现自己产生了反对。如果是这样，你并不孤单——很多人发现这个例子简直令人震惊。虽然完全承认它包含许多不受喜欢的地方，但这段代码也带来了明确的益处。因此，请暂时放下任何异议，阅读以下对该语法的解释。这种方法的优缺点将在之后进行审查。

首先是语法。注意 `for` 方法现在包含一个简单的条件判断，而不是一个 `switch` 语句。在第 4 行，进入条件判断之前，字符串 `"BottleNumber"` 与参数 `$number` 拼接。这可能会产生一个与类名匹配的字符串。

如果类存在（例如 `BottleNumber0` 存在），则跳过条件块。如果类不存在（如 `BottleNumber37` 等），则条件语句求值为 `true`，并且条件返回 `BottleNumber` 类。

它的优点是，这个工厂是对扩展开放的。只要你遵循命名约定，工厂就会乐意地接纳新添加的瓶号类，而无需更改。

尽管如此，这段代码仍有很多令人不受喜欢的地方。以下是几个常见且完全合理的反对意见：

1. 这个版本比原始版本更难理解。
   每个人都理解原始 `switch` 语句是如何工作的，但许多人不知道通过类名称的字符串值来定位类。某些程序员发现这段代码出乎意料且令人困惑。

2. `BottleNumber0` 等不再在源代码中被显式引用。
   想要寻找动态构建名称的类的引用，请祝你好运。尽管工厂完全有能力创建 `BottleNumber0` 的新实例，但它没有显式引用这个类名。试图通过在源代码中搜索 `BottleNumber0` 来寻找该类实例创建的地方是徒劳的，因此也是沮丧的。也可以想象，在过度的清理热中，有人可能会删除这个显然未被引用的类。如果这种情况发生且没有被测试捕获，应用程序将在一个非常遥远且极其不方便的时间崩溃。

3. 工厂忽略了名称不符合约定的瓶号类。
   如果一个毫无防备的程序员无意中创建了新类 `BottleNumberSix`，工厂将不知道它的存在。使用这个新类的尝试将静默失败，而没有任何关于底层问题的提示。这可能导致令人抓狂的调试过程。

鉴于这些反对意见，质疑开放这个工厂是否值得是逻辑上的。开放带来的益处是否足以抵消这种额外复杂性的成本？

答案正如大多数关于面向对象设计的问题一样，这取决于情况。如果你经常创建新的瓶号类，反复更改工厂的成本可能远超过让它开放的成本。相反，如果你从不添加新的瓶号类，工厂就永远不会更改，因此没有理由让代码复杂化。

上一个示例使用了简单的元编程来根据约定生成正确的类名。这显然要求所有类都必须按照该约定命名。

如果你无法强制执行某种约定，并且必须创建具有任意名称的类实例该怎么办？在这种情况下，你始终可以回到 `switch` 语句。那种形式的工厂可以工作，但遗憾的是，它对扩展是不开放的，而且每当有人添加新类时，都必须对其进行更新。如果经常添加新类，这会既令人困扰又昂贵。

`switch` 语句工厂易于理解，因为它集中化了必要的知识：它既知道候选类的名称，也知道可能选择任何一个类的原因。在工厂中将条件（`$number === 0`）和类名（`BottleNumber0`）放在一起，使得代码易于阅读，并便于理解一切是如何运作的。

如果你喜欢在工厂中集中所有知识的简单性，但又需要支持任意类名，那么要让工厂变得开放可能是一个挑战。虽然接下来的示例最终没有实现完美的开放，但它已经实现了大部分目标，并且在很多情况下是足够的。

通向既能集中知识又支持任意类名的开放工厂的第一步，是重新排列代码以增加名称的隔离性。你可以通过将 `switch` 语句替换为键值对查找来实现这一点，如下：

[Listing 7.5: 键值对查找工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-40/lib/Bottles.php#L28-L72)

```
 1 class BottleNumber {
 2   // ...
 3   public static function for(int $number): BottleNumber {
 4     $classNames = [
 5       0 => 'BottleNumber0',
 6       1 => 'BottleNumber1',
 7       6 => 'BottleNumber6',
 8     ];
 9     if (isset($classNames[$number])) {
10       $className = $classNames[$number];
11     } else {
12       $className = BottleNumber::class;
13     }
14     return new $className($number);
15   }
16   // ...
17 }
```

上面的示例将 `$number` 映射到类名（第 5-7 行），尝试根据 `$number` 的值选择类（第 9-10 行），并在找不到数字时默认使用 `BottleNumber`（第 12 行）。然后，它（第 14 行）创建了所选类的新实例。

这种键值对查找工厂看起来与之前的两个示例截然不同（Listing 7.3: 没有 Case 6 的工厂 和 Listing 7.4: 元编程类查找工厂），但尽管语法上不同，这三个示例在逻辑上非常相似。每个示例都使用 `$number` 来选择类名。`switch` 语句、元编程类查找和键值查找仅仅是表达这一组逻辑的不同方式：`switch` 语句允许任意类名，但它是关闭的；元编程在某些情况下是开放的，但它要求遵循命名约定；键值查找允许任意类名，并且部分开放。

简单流程的直观性让它们看起来很有吸引力，事实上，只要永远不发生变化，它们就是很好的。然而，如果你的代码需要适应和增长，那么支付 OOP 的代价是值得的。

### 7.5. 分散选择逻辑

如上所述，到目前为止的三个示例都包含相同的底层逻辑。在每种情况下，工厂都了解一切。它拥有选择逻辑（`number 的值为 n`），它知道可能被选中的项（`类名`），并且包含了在两者之间映射的逻辑（`number n 意味着类 x`）。

当选择逻辑简单且稳定时（如当前示例所示），拥有选择逻辑是有意义的。但很容易想象选择逻辑要复杂得多。选择正确类所需的逻辑可能很长、很复杂，并且与所选类本身的关系比与工厂的关系更紧密。如果选择逻辑与所选类中的代码同步变化，那么选择逻辑就属于该类，而不是工厂。

在这种场景下，每个可选择的对象都实现了自己的方法，来确定自己是否应该被选中。然后，工厂遍历所有可能的对象，并让它们来做决定。

这里是这种工厂的简单闭合形式：

[Listing 7.8: 分散选择逻辑](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-100/lib/Bottles.php#L28-L122)

```
 1 class BottleNumber {
 2   // ...
 3   public static function for(int $number): BottleNumber {
 4     $classNames = [
 5       'BottleNumber6',
 6       'BottleNumber1',
 7       'BottleNumber0',
 8       'BottleNumber',
 9     ];
10     foreach ($classNames as $className) {
11       if ($className::handles($number)) {
12         return new $className($number);
13       }
14     }
15   }
16 
17   public static function handles(int $number): bool {
18     return true;
19   }
20   // ...
21 }
22 
23 class BottleNumber0 extends BottleNumber {
24   public static function handles(int $number): bool {
25     return $number === 0;
26   }
27   // ...
28 }
29 
30 class BottleNumber1 extends BottleNumber {
31   public static function handles(int $number): bool {
32     return $number === 1;
33   }
34   // ...
35 }
36 
37 class BottleNumber6 extends BottleNumber {
38   public static function handles(int $number): bool {
39     return $number === 6;
40   }
41   // ...
42 }
```



上面的每个类现在都实现了方法 `handles($number)`。`BottleNumber0`、`BottleNumber1` 和 `BottleNumber6` 中的实现（第 25、32 和 39 行）在数字恰好为它们所代表的数字时返回 `true`。`BottleNumber` 的实现（第 18 行）无条件返回 true，因为 `BottleNumber` 是默认的。

第 3 行 `BottleNumber` 中的 `for` 方法通过 `foreach` 遍历类名数组。条件检查每个类以确定它是否能处理 `$number`，如果是，则返回该类的新实例。因此，这段代码制造了列表中第一个对 `handles($number)` 响应 `true` 的类的实例。

这种工厂将选择逻辑分散到了被选中的对象中。在这个示例中，该逻辑简单到让这种技术显得过度了，但在某些情况下，选择将涉及大量代码，而且这些代码将与所选类同步变化。这些就是这种技术能为你节省成本的情况。

这种工厂的结构引发了几个问题。首先，它是封闭的。每当添加新类时，你必须更新第 5-8 行的列表。

接下来，由于 `BottleNumber::handles` 总是返回 `true`，`BottleNumber` 必须始终是列表最后一个类。如果有人错误地在 `BottleNumber` *之后*添加新类，工厂将永远不会制造该新类的实例。

最后，可能会有多个 `handles` 方法返回 `true`。上面的代码在第一个候选者回答“是我！”时就停止查找，但可以想象在某些场景，你应该收集所有回答肯定的候选者，并给他们一个执行的机会。在这种情况下，候选者可能还想报告优先级，以便你可以按照它们应该的顺序对结果列表进行排序。

上面的示例展示了分散选择逻辑的最简单方法。这可能就是你需要的。如果你担心保持列表的顺序，或者需要处理多个想要自愿提供的候选者，你就必须写多一点代码。

在每情况下，基本问题都是相同的。如果你的选择逻辑与所选类的关系比与工厂的关系更紧密，那么选择逻辑应该与该类放在同一个位置。

### 7.6. 自注册候选者

上面的示例分散了选择逻辑，但工厂仍然有一个硬编码的候选类列表。该实现要求你手动将新创建的类添加到此列表中。如果你希望工厂在出现新候选者时只需继续工作，你有两个基本选项。

1. 工厂可以动态确定哪些类属于它的列表，但这并不总是成立的。
2. 候选者如果愿意依赖知道工厂的名字，可以承担起把自己放入列表的责任。选项 #2 始终是一个选择。

[Listing 7.9: 创建注册表](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-100/lib/Bottles.php#L28-L75)

```php
1 class BottleNumber {

2   protected static $registry = [];

3   // ...

4   public static function register(string $candidate): void {

5     array_unshift(self::$registry, $candidate);

6

```

上面的第 2 行定义了 `registry` 属性，它初始化为空数组。此类列表通常被称为*注册表*（registries）。

由于选项 #2 总是可能的，所以它是下一个示例。下面的 `BottleNumber` 工厂：

1. 持有注册表，并且
2. 为候选者提供了一种添加自己的方法。

现在这个注册表存在了，候选类可以注册自己。这是 `BottleNumber0` 的示例（第 4 行）：

[Listing 7.10: 候选者注册](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-100/lib/Bottles.php#L78-L95)

```php
1 class BottleNumber0 extends BottleNumber {

2   // ...

3 }

4 BottleNumber::register(BottleNumber0::class);

```

一旦对其他瓶数类（`BottleNumber1`、`BottleNumber6` 和 `BottleNumber`）做了上述更改，工厂中的硬编码候选者列表就可以替换为注册表的引用：

[Listing 7.11: 在工厂中引用注册表](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-100/lib/Bottles.php#L28-L75)

```php
 1 class BottleNumber {

 2   // ...

 3   public static function for(int $number): BottleNumber {

 4     foreach (self::$registry as $candidate) {

 5       if ($candidate::handles($number)) {

 6         return new $candidate($number);

 7       }

 8     }

 9   }

10   // ...

11 }

```

这里是将所有相关的代码汇总在一个列表列表中：

[Listing 7.12: 带自注册的工厂](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c7-factories-100/lib/Bottles.php#L28-L125)

```php

class BottleNumber {

  protected static $registry = [];

  // ...

  public static function register(string $candidate): void {

    array_unshift(self::$registry, $candidate);

  }

  public static function for(int $number): BottleNumber {

    foreach (self::$registry as $candidate) {

      if ($candidate::handles($number)) {

        return new $candidate($number);

      }

    }

  }

  // ...

}

BottleNumber::register(BottleNumber::class);

class BottleNumber0 extends BottleNumber {

  // ...

}

BottleNumber::register(BottleNumber0::class);

class BottleNumber1 extends BottleNumber {

  // ...

}

BottleNumber::register(BottleNumber1::class);

class BottleNumber6 extends BottleNumber {

  // ...

}

BottleNumber::register(BottleNumber6::class);

```

关于上面的列表有几点需要注意。首先，注意注册行显式地指出了类名 `BottleNumber`：

```php

BottleNumber::register(BottleNumber0::class);

```

而不是使用子类的名称并期望继承 `register` 方法，如下所示：

```php

BottleNumber0::register(BottleNumber0::class);

```

由于它没有显式提到 `BottleNumber`，第二个示例似乎包含的依赖更少。事实上，前两个示例包含的依赖数量完全相同；它们只是依赖于不同的东西。

`BottleNumber::register(BottleNumber0::class)` 示例向 `BottleNumber` 发送了 `register` 消息，因此依赖于知道工厂的名称。如果该名称以后发生变化，这段代码也必须跟着更改。

`BottleNumber0::register(BottleNumber0::class)` 示例向子类 `BottleNumber0` 发送了 `register` 方法。这段代码依赖于在类层次结构的某处找到 `register`，因此依赖于继承。如果有一天你将扮演瓶号角色的色的类移出 `BottleNumber` 层次结构，你就必须修改这行代码。

记住，任何实现 `BottleNumber` API 的类都可以扮演瓶号角色。在当前的示例中，`BottleNumber0`、`1` 和 `6` 使用继承来获取此 API 的部分，但并没有规则规定你必须使用继承。你的情况可能是，出于某些理由，创建不继承自 `BottleNumber` 但实现整个 API 的新类是有意义的。

在依赖类名和依赖继承之间选择，意味着对哪种依赖更稳定进行下注。是工厂名称更改的可能性更大，还是角色使用者停止使用继承的可能性更大？如果你认为工厂名称比继承的使用更稳定，你应该显式地将 `register` 消息导向 `BottleNumber`。如果你担心工厂名称可能会更改，但相信你将一直使用继承，你的代码应该依赖于在层次结构中寻找 `register`。

无论你现在如何决定，你的选择只能是一种猜测。关注你猜测的结果，它们会变得更好。经验丰富的程序员之所以擅长编写容错性代码，原因之一是他们建立了一套关于如何进行良好猜测的内部准则。他们理解，虽然依赖是无法避免的，但可以为了稳定性有选择地进行选择。

这个工厂现在对扩展开放，它分散了选择逻辑，并允许候选者注册自己。它可以制造它并不知道名称的类实例，而其原因它一无所知。

### 7.7. 总结

可维护的面向对象代码依赖于多态，依赖于从代表角色变体的小型、可交换对象族构建应用程序。与其编写包含许多条件判断来选择行为的类，多态要求你将行为的变体分散到自己的类中。

将变体放在单独的类中消除了这些类内部对条件判断的需求，但并没有完全消除条件判断的需求；它只是把那个所谓的“条件桶”踢向了更远的地方（或回到了堆栈）。在每个需要扮演角色的对象的情况下，某个地方的代码必须知道足够的信息来挑选正确的那个。

引入工厂。

工厂是条件判断的终结之地。它们包含了选择*类*的条件判断，并将这些条件判断隔离在一个单一、易于测试的地方。

## 8. 开发编程美学

到目前为止，“99 瓶”代码的大多数更改都是重构的结果。你是一个积极的参与者，选择了要攻击的代码味道并遵循了重构配方。这个过程既是规范性的也是限制性的；重构配方告诉你该做什么，同时禁止你去纠结无关紧要的东西。

本章抬高了视野，考虑了一些解决方案并不清晰的问题。有时，尽管安排良好、由配方驱动的代码，仍然令人感到不满意，因为它可能保留了一些重复，或者在某个地方添加另一个抽象会使之变得更容易，或者其实现方式让你担心它的可维护性。

自愿修改工作代码是有成本的，这样做意味着你认为现在重新排列代码比待办事项中的任何其他事情都重要。改进现有代码的机会成本是你可以无法同时处理其他事情。

如果你对代码中的某些部分感到困扰，你可能对想要做什么有一个想法。这些模糊情况带来的难题不在于弄清楚做什么，而在于判断是否有理由去做任何事情。代码味道和重构配方代表了许多资深面向对象实践者的经验判断。这些人编写了大量的代码，有好有坏，并随着时间的推移注意到代码安排与成本之间的联系。对最终结果的关注使他们产生了一种关于代码正确性的感觉，这种美学，指导了他们在困惑和不确定时期的决策。

本章的目标是引导你走上这条路。

### 8.1. 欣赏机械过程

在深入研究编程美学之前，花一点时间欣赏代码。如果你回到第 7 章中最简单的工厂，它看起来是这样的：

```php

  class Bottles {

  public function song(): string {

    return $this->verses(99, 0);

  }

  public function verses(int $upper, int $lower): string {

    return implode(

      "\n",

      array_map([$this, 'verse'], range($upper, $lower))

    );

  }

  public function verse(int $number): string {

    $bottleNumber = BottleNumber::for($number);

    return

      ucfirst("{$bottleNumber} of beer on the wall, ") .

      "{$bottleNumber} of beer.\n" .

      "{$bottleNumber->action()}, " .

      "{$bottleNumber->successor()} of beer on the wall.\n";

  }

}

class BottleNumber {

  protected $number;

  public static function for(int $number): BottleNumber {

    switch ($number) {

    case 0:

      $className = BottleNumber0::class;

      break;

    case 1:

      $className = BottleNumber1::class;

      break;

    case 6:

      $className = BottleNumber6::class;

      break;

    default:

      $className = BottleNumber::class;

      break;

    }

    return new $className($number);

  }

  public function __construct(int $number) {

    $this->number = $number;

  }

  public function __toString(): string {

    return $this->quantity() . " " . $this->container();

  }

  public function quantity(): string {

    return (string)$this->number;

  }

  public function container(): string {

    return "bottles";

  }

  public function action(): string {

    return "Take " . $this->pronoun() . " down and pass it around";

  }

  public function pronoun(): string {

    return "one";

  }

  public function successor(): object {

    return BottleNumber::for($this->number - 1);

  }

}

class BottleNumber0 extends BottleNumber {

  public function quantity(): string {

    return "no more";

  }

  public function action(): string {

    return "Go to the store and buy some more";

  }

  public function successor(): object {

    return BottleNumber::for(99);

  }

}

class BottleNumber1 extends BottleNumber {

  public function container(): string {

    return "bottle";

  }

  public function pronoun(): string {

    return "it";

  }

}

class BottleNumber6 extends BottleNumber {

  public function quantity(): string {

    return "1";

  }

  public function container(): string {

    return "six-pack";

  }
```



上面的代码是对通过熟练处理复杂性所实现的“极简主义”的致敬。它证明了通过识别代码气味并使用著名的重构配方消除气味的编程的有效性。设想一下，如果你直接从`30 分钟努力`的终点向前冲刺，代码会是什么样子——即使你最初是从第一章中的不可理解的简洁实现、推测性的通用实现或具体的抽象实现开始的。

正如你可能早已意识到的，“99 瓶啤酒”问题比看起来要微妙得多。像《99 瓶啤酒》这样的歌曲对于教授处理复杂性的深层教训非常有帮助。这首歌足够简单，可以被快速理解，但又为关于不同概念之间细微区别的无限讨论提供了素材。虽然上述精细的代码在在这种情况下可能显得有些大材小用，但创建它所使用的技术可以扩展到无限更困难的问题。歌曲之所以伟大，是因为它们能让你轻松练习技术，而这些技术随后可以用来征服极其复杂的领域。

特别是《99 瓶啤酒》歌曲，在这用途有着悠久的历史。著名的计算机科学家唐纳德·高斯（Donald Knuth）在 40 多年前写过的一名为[歌曲的复杂性](http://www.cs.stanford.edu/~friedl/alg/knuth_complexity.pdf)的文章，其中直接引用了《墙上的瓶啤酒》。99 瓶啤酒问题非常常见，以至于在各种编程语言中有超过[1500 种实现](http://bottles-of-beer.net/)。这首歌非常适合教学；它既足够简单以便学习，又足够困难以让教训变得有用。

这本书只是长链中的又一个环节点。当前实现所讲述的故事是，所有诗节在抽象上都是相似的，而瓶子数量在每个诗节中变化。`Bottles`的`song`和`verses`方法积累了各个诗节。`verse` 方法（下文所示）将数字转换为瓶子数量，然后使用该瓶子数量生成诗节。

### 列表 8.1：用“和”描述的诗节
https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-10/lib/Bottles.php#L17-L25

```php
public function verse(int $number): string {

  $bottleNumber = BottleNumber::for($number);

  return

    ucfirst("{$bottleNumber} of beer on the wall, ") .

    "{$bottleNumber} of beer.\n" .

    "{$bottleNumber->action()}, " .

    "{$bottleNumber->successor()} of beer on the wall.\n";

}
```

上一个句子中“and”一字的出现应该引起你的怀疑——它暗示`verse`方法做了两件事。上面第 3 行那行讨厌的空行可能会引起进一步的担心。程序员添加空行是为了指示主题的切换，而主题的切换意味着存在多项职责。空行是代码气味。

这些疑虑结合在一起，可能会促使你主动将`verse`重构为两个较小的方法：一个用于将`number`转换为瓶子数量，另一个用于生成实际的诗节。

尽管有这种非常合理的诱惑，但保持`verse`原样不变也有充分的理由。看在份上，这个方法可以正常工作，它只包含了六行代码，而且没有人要求过任何迫使做出更改的新功能。将`verse` 拆分为多个方法会引入额外的消息传递，并增加额外的间接层。增加间接性会让代码更难以追踪。

也许保持现状并悄悄地离开是最好的。

在这样的情况下，你应该怎么做？是自愿重写这个方法以分离职责更好，还是应该保持原样并观察未来发生什么？从更广阔的角度来看，自愿改进代码是否真的可以，还是你应该总是限制自己只编写重构配方规定或满足显式需求所必需的代码？

这些是实践程序员面临的一些最紧迫的问题。它们的共同点是不确定性。选择进行自愿更改就像是在下注，赌注更改的成本将在未来的抵消减少中获得回报。某些潜在的更改是非常好的赌注，应该总是这样做；而另一些则是注定失败的，应该始终避免。

由于你的潜意识无法交流，这正是编程开始感觉像门艺术的地方。你对代码正确性所产生的感觉可能是正确的，但你潜意识中那台超级计算机无法提供词汇来辩护这些感觉。遗憾的是，根据你无法解释的感觉来主张修改代码，不太可能具有说服力。

因此，虽然直觉能很好地提供关于代码的感受，引导你关注可能从行动中获益的事物，但如何将这些感受转化为文字则是你清醒大脑的任务。这些词汇构成了你的编程美学，或者说是支撑并指导你工作的原则集。直觉驱动行动，由美学证明，并由启发式方法引导。

编程美学有很多待探索的空间，但在简要思考了这些更广泛的问题后，我们先把它们放在一边。在危急时刻，你被一个新需求的到来解救了。

你的客户想要其他首与“99 瓶啤酒”相似但歌词不同的歌曲。

### 8.2. 使用伪代码明确职责

你的第一个问题应该是“在哪些方面相似？”回想一下 `verses` 方法：

[Listing 8.2: 倒计数的节歌](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-10/lib/Bottles.php#L10-L15)

```php
public function verses(int $upper, int $lower): string {

  return implode(

    "\n",

    array_map([$this, 'verse'], range($upper, $lower))

  );

}
```

该方法负责生成歌曲的一系列节歌。然而，在所有歌曲的宇宙中，“99 瓶啤酒”这首歌有点特殊，而这种特殊性通过上面第 4 行使用的 `range($upper, $lower)` 被暴露出来。通常歌曲是从底部开始向上计数的，但在这首歌是从顶部开始向下倒计数的。当你的客户要求你制作其他像“99 瓶啤酒”这样的歌曲时，他们是在要求你编写代码来生成其他同样倒计数的歌曲。

他们要求一个可以产生不同节歌的变体。这意味着代码必须发生变化。正如你在第 3 章中学到的，决定下一步写什么代码的第一步是咨询开闭原则流程图。

因此：

1. 代码对改变节歌的需求是开放的吗？
   不是。
2. 你知道如何让它开放吗？
   可能不知道。
3. 最容易理解的代码异味（code smell）是什么？
   虽然很清楚 `verse` 方法可能做得太多了，但并不清楚识别和修复任何当前存在的代码异味会有什么帮助。

悖论的是，当面对对下一步该做什么的不确定性时，深吸一口气，忽略你所学的一切，并只写一个新的条件判断，有时会有帮助。这个条件判断目的是提供更多关于问题的信息，编写它可以弄清楚需要改变的地方。一旦你理解了应该改变什么，就可以丢弃这个条件判断并编写更好的代码。

如果你 Sketch 勾勒出产生其他类型节歌所需的条件判断，那么 `verse` 方法看起来可能像这样：

```php
public function verse(int $number): string {

  // if (99BottlesSong) {

    $bottleNumber = BottleNumber::for($number);

    return

      ucfirst("{$bottleNumber} of beer on the wall, ") .

      "{$bottleNumber} of beer.\n" .

      "{$bottleNumber->action()}, " .

      "{$bottleNumber->successor()} of beer on the wall.\n";

  // } elseif (unknownSong2Verse) {

  //   ...

  //   组装歌曲 2 的节歌

  //   ...

  // } elseif (unknownSong3Verse) {

  //   ...

  //   组装歌曲 3 的节歌

  //   ...

  // }

}
```

上面的伪代码^(\[18\])被注释掉了，但它不是可运行的代码并不紧要——条件判断的存在就有助于弄清楚需要做什么。从反方向来说，这段伪代码的目的是引入新的代码异味。上面的 `verse` 方法现在包含一个切换语句（Switch Statement），并且是一个长函数（Long Function）。这些代码异味提供了对未来的展望，传递了如果你踏上通过添加条件判断来解决问题的路径将会发生什么。这个想象中的条件判断提供了可见的、不可否认的证明，说明这样做不会有任何结果。

现在你可以预见到这些异味了，你可以预先选择一个并应用治疗性的重构。函数之所以长是因为那个条件判断，所以你可以忽略那个异味，只留下 Switch 语句。每个想象中的分支都代表一组不相关的歌词，因此治愈这个条件判断的最好方法是对每个分支应用“提取类”（Extract Class）。

丢弃伪代码条件判断并恢复到早早的 `verse` 方法。你可以将原始代码视为想象中条件判断中的一个需要提取的分支。

### 8.3. 提取节歌

你已经在提取 BottleNumber 章节练习过提取类了。你可以把原始代码视为想象中条件判断中的一个需要提取的分支。

在第 5 章创建新类时，这里回顾一下操作：

*   选择类名并创建新类。
*   在新类中添加属性和构造函数（primitive）。
*   将旧类的方法复制到新类。
*   将旧类的调用转发到新类。
*   逐个从旧类的方法中移除参数。

第一个的问题始终是如何给新类命名。类应该根据它们的功能命名，因此一个代表“99 瓶啤酒”节歌的类可以合理命名为 `BottleVerse`，如下：

[Listing 8.4: 创建 BottleVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-20/lib/Bottles.php#L28-L29)

```php
class BottleVerse {

}
```

`BottleVerse` 需要一个接受 `$number` 参数的构造方法，以及一个存储该数字的属性。这是该代码：

[Listing 8.5: 初始化数字](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-30/lib/Bottles.php#L28-L34)

```php
class BottleVerse {

  protected $number;

  public function __construct(int $number) {

    $this->number = $number;

  }

}
```

你还没有更改过 `Bottles->verse`，因此此时运行测试确认了旧代码仍然有效，并证明了新的 `BottleVerse` 类语法是正确的。（注意 `Bottles->verse` 中的 `->` 表示 `verse` 是 `Bottles` 的实例方法。如果 `verse` 是静态函数，则应写为 `Bottles::verse`。）

由于你是遵循重构配方而不是通过 TDD 创建新类，通常会在修改新类的任何代码之前将其完全接入旧类。最安全的流程是先从完全复制的代码组装新类，然后修改旧类以调用新类的代码。只有然后才返回新类进行改进或更改。这种工作方法减少了破坏内容的概率，并让意外破坏的内容更容易调试。

因此，下一步是将 `Bottles` 中的整个 `verse` 方法复制到 `BottleVerse` 中。它看起来如下：

[Listing 8.6: 将节歌复制到 BottleVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-40/lib/Bottles.php#L28-L44)

```php
class BottleVerse {
  // ...
  public function verse(int $number): string {
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

一如既往，在进行此更改后运行测试。它们应该再次确认旧代码可以工作，并且新代码在语法上是正确的。

现在，你可以开始将这个新类重新整合到提取它的那个类中。回到 `Bottles` 类，在它的 `verse` 方法中插入一行，创建一个 `BottleVerse` 实例并转发 `verse` 消息，如下方的第 4 行所示。

[代码列表 8.7: 创建一个 BottleVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-50/lib/Bottles.php#L5-L28)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    (new BottleVerse($number))->verse($number);

    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

上面的第 4 行执行了新代码，但忽略了返回的 verse。你无法知道结果是否正确，但你*已经*证明了新的 `BottleVerse` 代码运行没有崩溃。

下一步是实际使用该结果。这通过注释掉旧代码并添加一个返回语句可以轻松实现，如下所示：

[代码列表 8.8: 使用 BottleVerse 的结果](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-60/lib/Bottles.php#L5-L28)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return (new BottleVerse($number))->verse($number);

    // $bottleNumber = BottleNumber::for($number);
    // return
    //   ucfirst("{$bottleNumber} of beer on the wall, ") .
    //   "{$bottleNumber} of beer.\n" .
    //   "{$bottleNumber->action()}, " .
    //   "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

运行测试确认你已成功提取了 `BottleVerse` 类。

此时代码已经可以工作了，但有一个令人讨厌的缺陷：上面的第 4 行引用了两次 `$number`。这显然是冗余的，应该被修复。这些冗余在 `BottleVerse` 中也有体现（下文重复）。与 `Bottles` 同步，`BottleVerse` 必须用 `$number` 初始化（第 4 行），并且它有一个需要 `$number` 参数的 `verse` 方法（第 8 行）。

[代码列表 8.9: 来自配方的 Bottle Verse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-60/lib/Bottles.php#L30-46)

```php
class BottleVerse {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function verse(int $number): string {
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

这些冗余在 `BottleVerse` 中也有体现（下文重复）。与 `Bottles` 同步，`BottleVerse` 必须用 `$number` 初始化（第 4 行），并且它有一个需要 `$number` 参数的 `verse` 方法（第 8 行）。



### 8.4. 幻想式编程

这些冗余在 `BottleVerse` 中也有体现。与 `Bottles` 同步，`BottleVerse` 必须用 `$number` 初始化（第 4 行），并且它有一个需要 `$number` 参数的 `verse()` 方法（第 8 行）。

```php
class BottleVerse {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function verse(int $number): string {
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

一如既往，在进行此更改后运行测试。它们应该再次确认旧代码可以工作，并且新代码在语法上是正确的。

现在，你可以开始将这个新类重新整合到提取它的那个类中。回到 `Bottles` 类，在它的 `verse()` 方法中插入一行，创建一个 `BottleVerse` 实例并转发 `verse()` 消息，如下方的第 4 行所示。

[代码列表 8.7: 创建一个 BottleVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-50/lib/Bottles.php#L5-L28)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    (new BottleVerse($number))->verse($number);

    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

上面的第 4 行执行了新代码，但忽略了返回的 verse。你无法知道结果是否正确，但你*已经*证明了新的 `BottleVerse` 代码运行没有崩溃。

下一步是实际使用该结果。这通过注释掉旧代码并添加一个返回语句可以轻松实现，如下所示：

[代码列表 8.8: 使用 BottleVerse 的结果](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-60/lib/Bottles.php#L5-L28)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return (new BottleVerse($number))->verse($number);

    // $bottleNumber = BottleNumber::for($number);
    // return
    //   ucfirst("{$bottleNumber} of beer on the wall, ") .
    //   "{$bottleNumber} of beer.\n" .
    //   "{$bottleNumber->action()}, " .
    //   "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

运行测试确认你已成功提取了 `BottleVerse` 类。

此时代码已经可以工作了，但有一个令人讨厌的缺陷：上面的第 4 行引用了两次 `$number`。这显然是冗余的，应该被修复。这些冗余在 `BottleVerse` 中也有体现。与 `Bottles` 同步，`BottleVerse` 必须用 `$number` 初始化（第 4 行），并且它有一个需要 `$number` 参数的 `verse()` 方法（第 8 行）。

[代码列表 8.9: 来自配方的 Bottle Verse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-60/lib/Bottles.php#L30-46)

```php
class BottleVerse {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function verse(int $number): string {
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

既然你已经表达了这一愿望，让它实现就简单了。回到原始的 `Bottles->verse()` 方法并插入这段愿望中的代码，如下所示：

[列表 8.10：空想思维的歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-80/lib/Bottles.php#L5-L27)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    // return (new BottleVerse($number))->lyrics();
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

上面的第 4 行尚无法工作，因此暂时被注释掉了。

下一步是进入 `BottleVerse` 并将 `verse($number)` 方法重命名为 `lyrics()`，引用数字属性而不是引用参数，如下面的第 3 和第 4 行所示：

[列表 8.11：BottleVerse 响应歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-90/lib/Bottles.php#L29-L45)

```php
class BottleVerse {
  // ...
  public function lyrics(): string {
    $bottleNumber = BottleNumber::for($this->number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

目前 `BottleVerse` 还没有被使用，所以运行测试只能证明这段代码在语法上是正确的。

现在回到 `Bottles` 并取消愿望中的第 4 行注释，如你所示：

[列表 8.12：获取 BottleVerse 的歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-100/lib/Bottles.php#L5-L27)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return (new BottleVerse($number))->lyrics();
    $bottleNumber = BottleNumber::for($number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

上面的第 4 行执行了新的 `BottleVerse->lyrics()` 方法并返回其结果。

最后（鼓点响起），从上面的方法中删除原始实现。这使得 `Bottles->verse()` 简化为：

[列表 8.13：Verse 获取歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-110/lib/Bottles.php#L5-L27)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return (new BottleVerse($number))->lyrics();
  }
}
```

`Bottles->verse()` 现在从 `BottleVerse` 获取歌词。

空想思维导致了对 `BottleVerse` 的提取。注意到，在 `Bottles` 中使用 `BottleVerse` 之前对 `BottleVerse` 进行多次更改增加了风险，这种替代方法非常高效。如果你在需要大量修改的情况下，从开始就进行 TDD（测试驱动开发），你可能会好运。这完成了 `BottleVerse` 的提取，一个响应 `lyrics()` 的新类。

### 8.5. 反转依赖

回顾提取 `BottleVerse` 的动力是为了 `verse()`。尽管已经提取了它，你还没有反转依赖。为什么？

依赖倒置原则（DIP）贡献了 SOLID 中的“D”，可以定义为“依赖抽象，而不是具体实现”。本节将揭秘这一原理并利用它松散 `Bottles` 与 `BottleVerse` 之间的耦合。这里是当前 `Bottles` 和 `BottleVerse` 的回顾：

[列表 8.14：Bottles 依赖 BottleVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-110/lib/Bottles.php#L5-L38)



```php
class Bottles {
  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return (new BottleVerse($number))->lyrics();
  }
}

class BottleVerse {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function lyrics(): string {
    $bottleNumber = BottleNumber::for($this->number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

在 `Bottles` 的 `verse` 方法第 14 行中，它知道具体 `BottleVerse` 类的名称。因此，`Bottles` 依赖于 `BottleVerse`。

### 8.5.1. 注入依赖

为了让 `Bottles` 产生不同的歌词而不使用条件判断，必须重新安排代码，使 `Bottles` 能够无缝地与任何歌词提供者通信。

另一方面，了解具体实现是完全可以避免的。`Bottles` 并不知道具体的类名 `BottleVerse`，这个名称可以很容易地从外部传递给 `Bottles`。这样做不仅减少了 `Bottles` 内部的依赖数量，还让 `Bottles` 开启了整个现有和潜在的歌词提供者的大门。

你可以将提供歌词的类看作扮演一个共同的角色。`BottleVerse` 响应的消息集建立了一个定义了该角色的 API。想要提供歌词的类必须符合这个 API。

角色需要名称，这个角色可以合理地命名为 `verse template`（诗歌模板）。下面的第 4 行体现了依赖于诗歌模板角色的执行者而非 `BottleVerse` 类的愿望：

[Listing 8.15: 想要从 BottleVerse 解耦](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-120/lib/Bottles.php#L5-L21)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    // return (new $this->verseTemplate($number))->lyrics();
    return (new BottleVerse($number))->lyrics();
  }
}
```

上面的愿望破坏了测试，因此它被临时注释掉了，但识别出这一点是值得的，因为它的存在促使你编写代码来实现它。

注意，这段愿望性代码通过将 `BottleVerse` 类名替换为 `verseTemplate` 角色名，实现了最小的改动。这行代码将两个依赖项链在一起。首先，它知道 `$this->verseTemplate(number)` 是一个构造函数，其次，它知道调用该构造函数会返回一个响应 `lyrics` 的对象。如果你担心这种链式调用，不要害怕；这是后续遵守迪米特节律 章节的主题。现在只需承认将 `BottleVerse` 改为 `verseTemplate` 不会增加任何额外的依赖。如果你突然担心上面的第 4 行，但之前并没被第 5 行困扰，在开始阅读迪米特节之前，花一分钟尝试表述你的顾虑。

回到当前的愿望，修改 `Bottles`，让外部代理在创建期间传递一个默认为 `BottleVerse` 的 `$verseTemplate`（下面的第 4 和 5 行）。接下来，创建一个属性来存储 `$verseTemplate` 的值（第 2 行）：

[Listing 8.16: 注入诗歌模板](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-130/lib/Bottles.php#L5-L27)

```php
class Bottles {
  protected $verseTemplate;

  public function __construct(string $verseTemplate = BottleVerse::class) {
    $this->verseTemplate = $verseTemplate;
  }
  // ...
}
```

现在 `verseTemplate` 被注入到 `Bottles` 中，愿望应该可以生效了。返回 `verse` 方法，取消愿望行的注释，运行测试，然后删除随后的那行代码。这使得 `verse` 的体缩小到第 20 行所示的单行代码：

[Listing 8.17: 使用诗歌模板](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-140/lib/Bottles.php#L5-L44)

```php
class Bottles {
  protected $verseTemplate;

  public function __construct(string $verseTemplate = BottleVerse::class) {
    $this->verseTemplate = $verseTemplate;
  }

  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return (new $this->verseTemplate($number))->lyrics();
  }
}

class BottleVerse {
  protected $number;

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function lyrics(): string {
    $bottleNumber = BottleNumber::for($this);
    return $bottleNumber .
      " on the wall, " .
      "take one, " .
      "pass one, " .
      "no more.\n";
  }
}
```

这些改动让 `Bottles` 开启了整个现有和潜在的歌词提供者的大门。首先，你可能会疑惑为什么 `$verseTemplate` 默认为 `BottleVerse`。此外，你可能在考虑：在注入时，应该注入类还是实例？

这些问题都将在遵守迪米特节律 章节中解决。现在只需承认将 `BottleVerse` 改为 `verseTemplate` 不会增加任何额外的依赖。

此前重构中发生的情况在技术上称为依赖倒置（dependency inversion）。依赖倒置原则（`DIP`）可能会让人困惑，因为它的名字本身就包含了你已经理解了它的假设。《韦斯特词典》将倒置（invert）定义为“翻过来、倒过来、放置在相反的顺序或方向上”。因此，倒置一个依赖意味着将其从一个状态翻转为该状态的反面。理解该原则的关键在于意识到：你的代码应该依赖于抽象。如果你发现代码处于依赖于具体实现的状态，`DIP` 认为你应该倒置这些依赖，转而依赖于抽象。

`Bottles` 曾经对 `BottleVerse` 具体实现有依赖，现在它对诗歌模板抽象（verse template abstraction）有了依赖。因此，原始的依赖被倒置了。

这种“依赖抽象，依赖具体实现”的定义提炼了 1996 年 5 月份《C++ Report》中更冗长的原始 DIP 定义的本质，该定义解释如下：

1. 高层模块不应该依赖低层模块。两者都应该依赖于抽象。
2. 抽象不应该依赖于细节。细节应该依赖于抽象。

为了回馈人类社会，以下段落使用此代码中的概念重新表述了该定义。

首先，注意上述定义中的“模块（module）”并非指特定的语言特性。在这个定义中，模块指的是程序中一个封装的、命名的功能单元。你可以用“类（classes）”或“对象（objects）”代替“模块”。

因此，`Bottles` 是代码中最高层的模块。另一种思考方式是，`Bottles` 是最外层的类。它是你开始编写的地方，到目前为止，它是唯一拥有测试的类。整个公共 API 目前都定义在 `Bottles` 中。

其他所有类都是通过从高层模块 `Bottles` 中提取行为而创建的。这些提取出的类代表了低层模块。（如果你觉得在一个产生许多歌曲的应用中，最高层模块被命名为 `Bottles` 很恼，你并不孤单。是时候开始考虑更好的名字了。这将在第 9 章中讨论。）

类名是具体实现（concretions）。当 `Bottles` 包含对 `BottleVerse` 的硬编码引用时，它直接依赖于该具体实现。因此，高层模块对低层模块有一个具体依赖。它依赖的是细节而非抽象。

就当前代码而言，官方依赖倒置原则定义可以重新表述为：

1. 像 `Bottles` 这样的高层模块不应该依赖于像 `BottleVerse` 这样的低层模块。每个都应该依赖于抽象。
2. `Bottles` 不应该依赖于像 `BottleVerse` 类名这样的具体细节。`Bottles` 应该依赖于一个多态地生成诗歌节的对象。

或者，使用第 3 章中较短的 DIP 定义形式，你可以说：

* `Bottles` 应该依赖于 `verseTemplate` 抽象而非 `BottleVerse` 具体实现。

隔离变体通常需要你倒置依赖，而倒置依赖的一种极佳技术是注入。本节隔离了 `BottleVerse` 变体，然后通过注入 `BottleVerse` 作为诗歌模板角色的执行者，倒置了依赖。

`Bottles` 依赖于诗歌模板角色。`BottleVerse` 扮演了这个角色。因为 `Bottles` 现在依赖于抽象角色而非具体类，你可以创建并注入其他扮演诗歌模板角色的执行者，而无需更改 `Bottles`。

你现在只需通过创建并注入一个新的扮演抽象诗歌模板角色但返回不同具体歌词的变体，即可完成本章开头提出的需求。

到达这一步，似乎你已经完成了，但再次是时候引入美学考虑了。

### 8.6. 遵守德密特律（Law of Demeter）

[注入依赖] 部分的总结对一行包含依赖链的代码表达了担忧。包含链式依赖的行（通常通过存在多个 `->` 暴露）可能会违反德密特律（`LoD`）。本节定义了该律，确定了它的适用范围，探索了忽略它的后果，并解释了如何修复违规行为。

#### 8.6.1. 理解律

请看以下示例：

[列表 8.18：诗歌方法包含许多依赖](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-140/lib/Bottles.php#L5-L26)

```php
class Bottles {
  // ...
  public function verse(int $number): string {
    return (new $this->verseTemplate($number))->lyrics();
  }
}
```

在上面的 `verse` 方法第 4 行，代码知道：

* `$this->verseTemplate` 可以用 `new` 调用
* `new` 期望一个参数
* `new` 的参数必须是一个数字
* 从 `new …($number)` 返回的对象响应 `lyrics` 消息
* `lyrics` 返回了感兴趣的实际歌词

这个列表列出了许多 `Bottles` 知晓但并不控制的事物，这意味着它们是依赖。依赖是脆弱性——如果它们的所有者更改了它们，该更改的影响将像水流一样顺向下传导到 `Bottles`。依赖是避免的，但应该降至最低。要警惕多余的依赖，并极其果断地移除它们。

该律解决的问题通过一个新示例解释得最清楚。考虑以下内容（此处省略了类型声明）：

列表 8.19：许多跳跃

```php
class Foo {
  public function durabilityOfPreferredToyOfFriends() {
    return $this->bestFriend->pet()->durability();
  }
}
```

注意：在此示例及随后的变体中，假设 `$bestFriend` 依赖已被注入。上面的第 3 行包含一条消息链（`$this->bestFriend->pet()->durability()`），每条消息都会产生一个符合不同 API 的对象。上面的第 3 行要求 `Foo` 知道：



* `pet` 消息位于 `$bestFriend` 所持对象的 API 中，
* `preferredToy` 在 `pet` 消息返回的对象的 API 中，以及
* `durability` 在 `preferredToy` 消息返回的对象的 API 中。

前一句话读起来很痛苦，这反映了代码底层的问题。以下是对象和消息的可视化图：

![lod camel](img/lod_camel.png)
图 8.3：违反德密特律

在上面的图中，`Foo` 首先向 `$bestFriend` 发送 `pet`。因为 `$bestFriend` 是被 `Foo` 知知的，你可以将其视为一个直接协作者。这返回了一个 `Pet` 实例。

到目前为止还好，但 `Foo` 接下来执行的操作是向该返回的 `Pet` 对象发送 `preferredToy`。注意，`Pet` 不是 `Foo` 的直接协作者；相反，它是 `Friend` 的协作者。这意味着 `Foo` 了解（或依赖）其协作者的协作者。

底层代码看起来无害，但图表显而易见地，除非你能提供一个拥有 `Pet` 且 `Pet` 拥有 `Toy` 的 `Friend`，否则你无法获得 `Foo`。代码目前可能会产生正确的输出，但它不会长久。这种跨越多个对象的紧耦合引入了两个严重问题，而这些问题被轻描淡写地推给了未来。

### 紧耦合的问题

首先，以这种方式安排代码会干扰你在新且意想不到的语境中使用 `Foo` 的能力。如果出现一个需要 `Foo` 行为的预见功能请求，你将无法通过提供一个 `Foo` 来满足该请求，你还需要提供一个拥有 `Pet` 且 `Pet` 拥有 `Toy` 的 `Friend`。这些消息将 `Foo` 紧耦合到不同对象的链上，而所有对象都必须可用。这里没有任何东西是孤立的——这组对象就像一个单一整体，任何使用都需要其中的每一个部分。

当你尝试重用 `Foo` 时，这些后果就变得显而易见。测试有许多用途，其中之一就是揭示重用代码是多么容易。紧耦合的代码难以测试。紧耦合的对象需要添加大量的上下文，为了运行任何测试，必须提供所有这些。

如果测试设置涉及创建一系列日益遥远的对象，或者你发现自己在不断存桩（stubs）中嵌套存桩，这意味着你正在测试的对象与应用程序的其他部分耦合得太紧了。一个难以测试的对象在警告你，它将很难重用。

尽管这些后果很糟糕，但这里还有一个可能更糟的问题。通过链式消息来满足需求允许你可以在不清楚对象到底想要什么的情况下让代码运行起来。在这种情况下，`Foo` 发送 `$this->bestFriend->pet()->preferredToy()->durability()` 是*出于某种原因*的。这个原因尚未被识别或命名。

该应用程序依赖于代码中隐含的一个概念、一个抽象。当前的作者显然理解这段代码背后的意图，但未来的维护者被迫进行“读心术”，而他们的感知能力可能并不可靠。

通过命名缺失的概念来解决这一 LoD（最少知识）违反行为很快就会发生，但在继续之前，理解德米特律还有最后一部分。现在是时候看看德米特律的正式定义了。《面向对象编程：一种客观风格》白皮书对该法则定义如下：

> 对于所有类 C 和附加到 C 的所有方法 M，M 发送消息的所有对象必须是与以下类关联的实例：
>
> 1. M 的参数类（包括 C）。
> 2. C 的实例变量类。
>
> （由 M 或由 M 调用的函数或方法创建的对象，以及全局变量中的对象被视为 M 的参数。）

上述内容是简洁精准的奇迹，但其极度简洁使其难以理解。虽然对这个正式定义留有大致的了解是值得的，但既然你已经看到了德米特律的实际运作，可以用更直白的语言重新表述该定义。

### 重新表述德米特律

德米特律说，从方法内部，消息应该只发送给：

* 作为方法参数传递的对象
* `$this` 直接可用的对象

请注意，德米特律比该定义暗示的要微妙得多。它关心的是返回对象的 API，而不是每个单独的对象。因此，代码如下

```
$i1 = new DateInterval("P10D");
$i2 = new DateInterval("P1D");
(new DateTimeImmutable("2050-06-04"))->add($i1)->sub($i2); // '2050-06-04'
```

`2050-06-04` 包含了许多操作，但并不是德米特律违反，因为每个消息返回的对象遵循相同的 API。德米特律有效限制了对象可以发送消息的*其他*对象。从消息发送者的视角来看，重要的不是消息返回的对象类型，而是消息链。对象只将消息发送给直接合作者。

### 8.6.2 治愈德米特违反

治愈消息链的一种明显方法是引入转发（forwarding），这种技术在口语中被称为委托（delegation）。此示例的转发代码可能如下：

```
class Friend {
   public function durabilityOfToyOfPet() {
     return $this->pet()->preferredToy()->durability();
   }
}
class Pet {
   public function durabilityOfToy() {
     return $this->preferredToy()->durability();
   }
}
class Toy {
   public function durability() {
     return "hour";
   }
}
class Foo {
   public function durabilityOfToyOfPet() {
     return $this->bestFriend->durabilityOfToyOfPet();
   }
}
```

上面的代码遵守了德米特律，因为它只向直接合作者发送消息。消息转发确实有帮助，如果你对类似“嘿，那只是增加了一堆间接层而没有从根本上改变任何东西”的反对是可以被原谅的。尽管如此，`Foo` 与其他对象之间的耦合已经减轻，这种松动在 `Foo` 的测试中立即可可见。测试设置现在只需要提供 `Friend` 对象。你不再需要提供 `Toy` 和 `Pet` 的实例，或者存桩。

这里是更新后的可视化：

![通过转发治愈的德米特]()

图 8.4：通过转发治愈 LoD 违反

这种变化确实改进了代码，但 `Foo` 仍然包含了应用程序结构问题的回声。虽然添加转发在技术上解耦了 `Foo` 与 `Pet` 和 `Toy`，但新的 `durabilityOfToyOfPet` 消息非常暗示了它们的持续存在。这个消息名称仅仅是原始消息链对象类型和消息的拼接，并且强烈暗示 `Foo` 只能在包含 `Pet` 和 `Toy` 的语境中使用。

当避免德米特违反的尝试被对应用程序现有对象和消息的知识劫持时，转发消息会被这样命名。遵守法则的同时避免将现有对象的名称编码到转发消息的名称中，技巧在于*从消息发送者的视角考虑设计*。`Foo` 想要知道最好的朋友的宠物喜欢的玩具的耐用性是有原因的，`Foo` 发送给 `$bestFriend` 的消息命名应该反映 `Foo` 的需求。

在这种情况下，`Foo` 正在试图为宠物聚会安排合适的时间。宠物通常在摧毁玩具之前快乐地玩耍，所以聚会的时间限制应该基于玩具预计生存多久。

如果 `Foo` 发送给 `$bestFriend` 的消息是 `playdateTimeLimit`，图表将变成这样：

![lod cured with abstraction camel](img/lod_cured_with_abstraction_camel.png)

图 8.5：通过抽象修复 LoD 违反

请注意，上述图表并未暗示除 `Foo` 和 `Friend` 之外还存在其他对象。对于 `Foo` 而言，不存在其他对象。`playdateTimeLimit` 消息反映了 `Foo` 安排约会的意愿，但并不包含对 `Friend` 如何满足这一请求的期望。

一旦你决定了这个新的消息名称，修复代码就只需让 `Foo` 发送该消息并让 `Friend` 实现它，如第 13 行和第 2 行所示：

```
 1 class Friend {
 2   public function playdateTimeLimit() {
 3     return $this->pet->durabilityOfPreferredToy();
 4   }
 5 }
 6 
 7 // Pet and Toy are unchanged
 8 
 9 // Foo 现在询问它想要的，而不是
10 // 对协作者的协作者做出假设。
11 class Foo {
12   public function playdateTimeLimit() {
13     return $this->bestFriend->playdateTimeLimit();
 14   }
 15 }
```

现在 `Foo` 只与直接协作者交谈，而不是窥探远处的对象，因此它更容易容忍意外的更改。如果出现新的需求，要求约会有时会涉及儿童而不是宠物，你可以在不改变 `Foo` 的情况下满足这一需求，如下所示。

```
 1 class FriendWithPet {
 2   public function playdateTimeLimit() {
 3     return $this->pet->durabilityOfPreferredToy();
 4   }
 5 }
 6 
 7 class Pet {
 8   public function durabilityOfPreferredToy() {
 9     return $this->preferredToy->durability();
10   }
11 }
12 
13 class Toy {
14   public function durability() {
15     return 3600;
16   }
17 }
 
18 class FriendWithChild {
19   public function playdateTimeLimit() {
20     return $this->child->toleranceForSocialContact();
21   }
22 }
23 
24 class Child {
25   public function toleranceForSocialContact() {
26     return 1800;
27   }
28 }
29 
30 class Foo {
31   public function playdateTimeLimit() {
32     return $this->bestFriend->playdateTimeLimit();
33   }
34 }
```

在上面的代码中，现在有两个扮演朋友角色的玩家，一个有一个宠物，另一个有一个孩子。它们都以多态的方式实现了 `playdateTimeLimit`。`Foo` 之外的世界变得更加复杂；它以意想不到且可能令人担忧的方式被重新设计，但 `Foo` 的行为在 `Foo` 本身没有任何改变的情况下扩展了。这两个变化——注入 `$bestFriend` 依赖和发送一个以 `Foo` 所想要的命名的消息——允许 `Foo` 无缝地与新对象协作并容忍意外的更改。

### 8.7 识别 verse 方法想要什么

现在你已经探索了迪米律（Law of Demeter）违反的定义和修正，是时候回到 `Bottles` 的 `verse` 方法中的问题了。这里是该代码的提示，第 4 行包含了问题：

```
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     return (new $verseTemplate($number))->lyrics();
5 }
```

你可能会抵制第 4 行违反了迪米律的观点，因为你知道 `verseTemplate` 包含一个类，并且你习惯于将 `new` 视为特殊的。在语法上它确实是特殊的，但在这种情况下，将 `new` 视为发送给类的一个消息是有用的。这里问题是，第 4 行总是需要一个带有参数的 `verseTemplate`，并创建一个反过来对 `lyrics` 响应的对象。从“`new` 是一个消息”的角度来看，这行代码是一个彻彻底尾的 LoD 违反。

注入依赖的规则是，你应该注入你想交谈的对象。换句话说，接收者只能直接向注入的对象发送消息，而不是向它及其所有的朋友发送消息。这条规则的实际效果是禁止在违反迪米律的消息链中使用注入的对象。如果 `new` 尽管在语法上很奇怪但被算作一条真正的消息，那么这条规则还建议你应该注入实例而不是类（你被迫对类发送 `new` 然后再发送其他内容——在这种情况下，是 `lyrics`）。

规则在这里被破坏了，因为在这种情况下无法注入 `BottleVerse` 的实例。看看整个 `Bottles` 类（如下所示），看看你是否能解释：

```
 1 class Bottles {
 2   protected $verseTemplate;
 3 
 4   public function __construct(string $verseTemplate = BottleVerse::class) {
 5     $this->verseTemplate = $verseTemplate;
 6   }
 7 
 8   public function song(): string {
 9     return $this->verses(99, 0);
10   }
 11 
12   public function verses(int $upper, int $lower): string {
13     return implode(
14       "\n",
15       array_map([$this, 'verse'], range($upper, $lower))
16     );
17   }
 
18   public function verse(int $number): string {
19     return (new $this->verseTemplate($number))->lyrics();
20   }
21 }
```

注意当上面第 20 行使用 `new` 调用 `$verseTemplate` 时，`$number` 是作为参数传递的。`Bottles` 的责任之一是计算 `$number`（在第 15 行的 `array_map` 中）。为了让 `Bottles` 独立于 `BottleVerse`，必须注入 `BottleVerse`。由于外部无法知道 `$number` 的值，他们无法创建并注入实例——他们只能传递类，希望某些下游过程确定正确的 `$number` 并创建正确的对象。

该领域的特殊性将你推入了编码死角。你想遵循规则并注入 `BottleVerse` 的实例，但你不能，因为 `$number` 的正确值直到以后才已知。注入类让你注定要在第 20 行发生迪米律违反。你现在必须决定是否值得修复这种违反。这就是你的编程美学发挥作用的地方。

代码看起来并不糟糕，未来的维护者可能不会觉得它奇怪。许多人甚至不会注意到这个问题，或者觉得忽略它是可以的。在代码中留下违反会带来什么可能的危害呢？

一种快速掌握代码安排后果的方法是尝试测试它。这些提取出来的类早该有它们自己的测试了。原始的 `Bottles` 测试提供了回归保护，但没有对不断演进的设计提供反馈。由于测试是下一章的主题，现在只需想象如何测试 `Bottles->verse` 方法即可。

记住测试是重用的第一形式，因此这种心理练习将提示你在应用程序的其他地方重用 `Bottles` 有多容易。测试设置的量将告诉你 `Bottles` 与对象的耦合有多紧。

为了让这个练习对应现实生活的问题，假设 `lyrics` 是一个昂贵的操作。你的 `Bottles` 测试应该能够在不运行那种远程昂贵代码的情况下确认 `Bottles` 的正确性，因此你希望此测试不要执行 `BottleVerse` 的实际 `lyrics` 方法。

由于迪米律的违反，你不能仅仅注入一个具有简单 `lyrics` 实现的 `$verseTemplate`。相反，你必须注入一个 `$verseTemplate`，其 `new` 实现返回一个包含简单 `lyrics` 实现的不同对象。这已经复杂到几乎难以解释，这对于测试来说不是好预兆。

这些困难与违反德梅特律（Demeter violation）直接相关。如果 `Bottles` 直接将 `lyrics` 发送给 `$verseTemplate`，一切都会变得更加简单。

是时候许另一个愿望了。如果你有一个歌词模板，并想要某个特定行号的歌词，作为一名根深蒂固的面向对象（OO）实践者，你有理由认为可以直接向你拥有的 `$verseTemplate` 对象发送 `lyrics(number)` 请求，如下所示第 4 行所示：

[列表 8.25：直接与歌词模板协作](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-150/lib/Bottles.php#L5-L27)

```
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     // return $this->verseTemplate->lyrics($number);
5     return (new $this->verseTemplate($number))->lyrics();
6   }
7 }
```

如果你想要什么，尽管去要。如果接收者不知道如何遵守，就教给它。不要被现状所困住，相反，通过*设计*一种体现消息发送者意图的对话来松散耦合。



上述第 4 行的愿望调用了 `verseTemplate` 上的 `lyrics` 方法。你可以说这段代码依赖于 `verseTemplate` 包含一个实例。要实现代码中所描述的愿望，需要引入一个实现了 `lyrics($number)` 方法的新事物。

实现这一愿望的另一种途径是让现有的 `verseTemplate` 变得智能，即直接在 `BottleVerse` 类中添加一个静态的 `lyrics($number)` 函数。这种方法的优点是尽可能减少活动部件的总数，但缺点是迫使愿望的代码显式地依赖 `verseTemplate` 包含一个类。这些优势至少目前来说是足够的，足以为创建和依赖静态函数提供合理理由。如果需求发生变化，你随时可以重新考虑这个决定。

在创建静态函数 `BottleVerse::lyrics($number)` 之前需要发生两件事。首先，`BottleVerse->lyrics` 实例方法的名称必须发生更改。其次，必须修改愿望以调用静态函数。

第一步是更改 `lyrics` 方法的名称。本着推迟决策的精神，下面的代码耸了耸肩将其重命名为 `_lyrics`（第 5 行和第 11 行）。注意，这两个更改是使用正则表达式同时完成的，因此这是一个“一次性撤销”（one-undo）更改而非单行更改（稍后将详细讨论一次性撤销更改）：

```php
 1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     // return $this->verseTemplate->lyrics($number);
5     return (new $this->verseTemplate($number))->_lyrics();
6   }
7 }
8 
9 class BottleVerse {
10   // ...
11   public function _lyrics(): string {
12     // ...
13   }
14 }
```

下一步是更新愿望以使用静态函数：

```php
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     // return $this->verseTemplate::lyrics($number);
5     return (new $this->verseTemplate($number))->_lyrics();
6   }
7 }
```

现在你可以向 `BottleVerse` 类中添加 `lyrics($number)` 函数，如下所示第 3-5 行所示：

[列表 8.26：教 BottleVerse 歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-160/lib/Bottles.php#L29-L49)

```php
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     // return $this->verseTemplate::lyrics($number);
5     return (new $this->verseTemplate($number))->_lyrics();
6   }
7 }
```

现在你可以向 `BottleVerse` 类中添加 `lyrics($number)` 函数，如下所示第 3-5 行所示：

```php
1 class BottleVerse {
2   // ...
3   public static function lyrics(int $number): string {
4     return (new BottleVerse($number))->_lyrics();
5   }
6 }
```

这个静态函数做了两件事。首先，它通过消除额外的跳转来解决德梅特律违反问题。其次，它为歌词模板建立了一个新的 API。在 `Bottles` 内部，`verseTemplate` 变量现在被认为持有一个类，而不是实例。

虽然 `lyrics` 静态函数听起来很像以前的 `_lyrics` 实例方法，但不要让这种相似性误导你。这个新的 `BottleVerse::lyrics($number)` 体现了 `Bottles` 从歌词模板获取歌词的愿望。注意它被命名为 `lyrics` 而不是 `newLyrics`；这。

`BottleVerse` 的实例方法现在是私有实现细节，并从视野中消失了。既然有了 `BottleVerse::lyrics($number)` 静态函数，你可能想把这些行为移动到这个新的静态函数中。这确实可行，并且减少代码量。为什么还要创建 `BottleVerse` 的实例呢？

尽管在这一章的早期，在判断 `new` 是否导致了德梅特律违反时，类被视为“另一个对象”，但在最基本的面向对象的方式中，类与实例是不同的。在实例中，共同行为与不同的数据结合以创建构成应用程序的对象。

将领域行为放在静态函数而不是实例方法中，是对该领域概念永远不会涉及会变化的数据的一种赌注。只有当今天不输入 `new` 的价值大于未来将所有静态函数转换为实例方法的成本时，这种赌注才是合理的。

由于静态函数难以重构，将领域行为从类移动到实例的成本可能非常高，并且远大于你避免输入 `new` 所带来的微小节省。由于你无法预测未来，因此无法正确判断何时遵循哪种策略。这表明最经济的整体计划是始终创建实例。不要浪费时间去考虑是否这样做。你编程审美的一部分是反射性地将领域行为放在实例上。

现在 `BottleVerse` 类响应 `BottleVerse::lyrics($number)`，你可以回到 `Bottles` 并将 `verse` 简化为行愿望代码，如下：

[列表 8.27：将 Verse 简化为实现的愿望](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-171/lib/Bottles.php#L5-L26)

```php
1 class Bottles {
2   // ...
3   public function verse(int $number): string {
4     return $this->verseTemplate::lyrics($number);
   }
6 }
```

完成该更改后，是生成的 `Bottles` 和 `BottleVerse` 类的概述。

[列表 8.28：BottleVerse 类响应歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-171/lib/Bottles.php#L5-L48)

```php
class Bottles {
  protected $verseTemplate;

  public function __construct(string $verseTemplate = BottleVerse::class) {
    $this->verseTemplate = $verseTemplate;
  }

  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return $this->verseTemplate::lyrics($number);
  }
}

class BottleVerse {
  protected $number;

  public static function lyrics(int $number): string {
    return (new BottleVerse($number))->_lyrics();
  }

  public function __construct(int $number) {
    $this->number = $number;
  }

  private function _lyrics(): string {
    $bottleNumber = BottleNumber::for($this->number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

不仅 `BottleVerse` 类被提取并注入，而且产生的迪米特法则违反（Demeter violation）也通过添加一个转发方法得到了修复。

既然你已经理解了迪米特法则（Law of Demeter），遵循它应该成为你编程审美的一部分。要极度倾向于修复违规行为。处理每处发生违规行为的总体成本，保证将低于修复那些在感染你的代码几年后才失控的少数违规行为所要付出的最终成本。诚然，在某些情况下，违反迪米特法则是有意义的。例如，打印数据库中所有关系的报告应该违反迪米特法则，而不是引入大量新的转发消息。但这些情况是特例。通常情况下，不要违反迪米特法则，并在发现违规行为时立即修复它们。

上面的代码看起来相当合理，但研究它应该提醒你注意最后一个疑虑。尽管本章努力依赖于抽象而不是具体实现，但上面的第 36 行仍然包含一个具体实现。`BottleVerse` 的 `lyrics` 方法包含对 `BottleNumber` 的硬编码引用。下一节也是最后一部分将探索安排此代码的其他替代方法。

### 8.8. 将对象创建推向边缘

最后一个未解决的问题是，`BottleVerse` 中的 `_lyrics` 实例方法直接引用了具体的 `BottleNumber` 类。

这里是 `BottleVerse` 的回顾：

[列表 8.29：实例方法依赖于 BottleNumber 类](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-171/lib/Bottles.php#L28-L48)

```php
class BottleVerse {
  protected $number;

  public static function lyrics(int $number): string {
    return (new BottleVerse($number))->_lyrics();
  }

  public function __construct(int $number) {
    $this->number = $number;
  }

  private function _lyrics(): string {
    $bottleNumber = BottleNumber::for($this->number);

    return
      ucfirst("{$bottleNumber} of beer on the wall, ") .
      "{$bottleNumber} of beer.\n" .
      "{$bottleNumber->action()}, " .
      "{$bottleNumber->successor()} of beer on the wall.\n";
  }
}
```

上面的代码包含一个 `lyrics(number)` 静态函数（第 4 行）和一个 `_lyrics` 实例方法（第 12 行）。该静态函数注入了一个 `$number`。静态函数创建了一个 `BottleVerse` 实例，并调用了 `_lyrics`。

迪米特法则的违规在以下几个方面令人担忧：首先，`_lyrics` 知道 `BottleNumber` 并且依赖于 `for`。如果 `_lyrics` 能够在不感知这些依赖的情况下完成工作，第 13 行就更好了。其次，`_lyrics` 包含一个空行（此处原文可能应为指方法做了更多事，但在该语境下指逻辑拆分或空行），这可能违反了单一职责原则，这暗示该方法承担了多项任务。最后，停下来思考一下，`_lyrics` 对 `$number` 的使用暗示了它在处理 `$number` 的转换，这应该让你汗毛竖立。

当你把这些观察结合起来考虑时，你会发现它们是重叠的。空行处的代码包含了 `BottleNumber` 具体实现，从而将 `$number` 转换为了其他对象。虽然列出的三个疑虑看起来是相互独立的问题，但它们实际上源于同一个设计问题。这是一个好消息，意味着一个修复就能解决所有问题。

良好的面向对象程序由松耦合的对象组成，这些对象依赖多态性来实现行为。注入依赖降低了耦合。多态性将行为隔离在外观相同但内部不同的对象中。

对于被注入的对象来说，这样做是完美的。因为接收注入的对象不需要更改就能与意外之外的协作者交互，它们是非常灵活的。需要新的变体？只需创建一个新类并注入它即可。接收者并不关心。

然而，这种思考对象的方式引入了一个尚未完全解决的问题。这些注入的对象在哪里创建？何时创建？由谁创建？

使用依赖注入的应用自然且必然地演变为对象创建与对象使用分离的系统。对象创建被推向更边缘、更靠外，而对象本身之间的交互更趋向中间、即内部。

在这种情况下，如果我们在代码中更早的地方将 `$number` 转换为 `BottleNumber`，然后在 `_lyrics` 中使用结果，代码将会更简单。这种更改会将对象创建移回堆栈，更趋向应用程序的边缘。

退一步考虑，目前的代码安排是可行的。你并没有新的需求。而且，尽管绑定了具体实现，`_lyrics` 方法已经足够灵活。因为因为 `BottleNumber::for` 是一个工厂，因此已经能够添加或更改瓶子数量角色而不破坏 `_lyrics` 方法。工厂可以制造不同类型的瓶子数量，`BottleVerse->lyrics` 可以愉快地与这些新对象协作而无需更改。

上一段的所有论点都认为这段代码目前运行良好，并建议你现在离开。但在你编写面向对象代码的审美中，还有一条规则（或者说是一条准则）。`_lyrics` 实例方法对 `BottleNumber` 类的硬编码引用是令人不安的。经验面向对象程序员知道，如果应用遵循以下原则，将最容易适应未知的未来：

- 避免实例方法感知具体的类名，以及
- 寻找机会将对象创建推向应用程序的边缘。

这些是准则，而非硬板的规则，因此你可以给自己留一点余地。在像这样的情况下尤其如此，因为硬编码的引用指向一个工厂，所以耦合性已经是松散了。尽管如此，你仍然应该时刻警惕引用类名的实例方法，并不断寻找移除这些引用的方法。

在这种情况下，很容易从 `_lyrics` 中移除对 `BottleNumber` 的引用，同时将对象的创建推回堆栈中。巧合的是，修复上一节中的迪米特法则违背（Demeter violation）为将 `$number` 转换为 `BottleNumber` 提供了完美的时机。

查看下方第 4 行的新愿望：

[列表 8.30：通过愿望思维注入 BottleNumber](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-180/lib/Bottles.php#L28-L49)

```php
1 class BottleVerse {
2   // ...
3   public static function lyrics(int $number): string {
4     // return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
5     return (new BottleVerse($number))->_lyrics();
6   }
7   // ...
8 }
```

上面的第 4 行在创建 `BottleVerse` 实例的同一个方法中将 `$number` 转换为 `BottleNumber`。注意此变化开始将对象的创建分组并将其与对象的使用分开。

这个愿望改变了在初始化期间传递给 `BottleVerse` 实例的对象的类型。正如你可能从 [列表 6.33：如果已经是瓶号则返回参数](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-190/lib/Bottles.php#L28-L51) 回忆的那样，通过类型更改进行重构的方法是修改接收端代码，使其临时同时忍旧类型和新类型。下方的第 4-6 行正是这样做的，它们同时兼容了 `$number` 和 `BottleNumber`。

[列表 8.31：接受 Number 或 BottleNumber](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-190/lib/Bottles.php#L28-L51)

```php
1 class BottleVerse {
2   // ...
3   private function _lyrics(): string {
4     $bottleNumber = $this->number instanceof BottleNumber ?
5       $this->number :
6       BottleNumber::for($this->number);
7     // ...
8   }
9 }
```



注意，由于这次重构正在更改类型，在你不从 `BottleVerse` 的 `__construct` 方法中移除 `$number` 参数的类型声明之前，之前的代码将无法工作，如下所示：

```php
1 class BottleVerse {
2   // ...
3   public function __construct($number) {
4     $this->number = $number;
5   }
6   // ...
7 }
```

现在 `_lyrics` 无论类型如何都能工作，你可以回到 `BottleVerse::lyrics($number)` 静态函数并取消愿望代码的注释，如下：

[列表 8.32：尝试愿望代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-200/lib/Bottles.php#L28-L51)

```php
1 class BottleVerse {
2   // ...
3   public static function lyrics(int $number): string {
4     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
5     return (new BottleVerse($number))->_lyrics();
6   }
7   // ...
8 }
```

运行测试证明代码可以工作。接下来，删除第 5 行的旧代码并再次运行测试。这应该可以，并将 `BottleVerse` 简化为：

[列表 8.33：在创建时向 BottleVerse 注入 BottleNumber](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-210/lib/Bottles.php#L28-L50)

```php
 1 class BottleVerse {
 2   protected $number;
 3 
 4   public static function lyrics(int $number): string {
 5     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
 6   }
 7 
 8   public function __construct(object $number) {
 9     $this->number = $number;
10   }
 11 
 12   private function _lyrics(): string {
13     $bottleNumber = $this->number instanceof BottleNumber ?
14       $this->number :
15       BottleNumber::for($this->number);
16 
17     return
18       ucfirst("{$bottleNumber} of beer on the wall, ") .
19       "{$bottleNumber} of beer.\n" .
20       "{$bottleNumber->action()}, " .
21       "{$bottleNumber->successor()} of beer on the wall.\n";
22   }
23 }
```

既然新类型正在被注入，你可以移除 `_lyrics` 中临时的类型检查。这使得下方的第 13 行简化为下文所示的这行略显困惑的代码。

[列表 8.34：移除临时类型检查](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-220/lib/Bottles.php#L28-L48)

```php
1 class BottleVerse {
2   protected $number;
3 
4   public static function lyrics(int $number): string {
5     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
6   }
7 
8   public function __construct(object $number) {
9     $this->number = $number;
10   }
11 
12   private function _lyrics(): string {
13     $bottleNumber = $this->number;
14 
15     return
16       ucfirst("{$bottleNumber} of beer on the wall, ") .
17       "{$bottleNumber} of beer.\n" .
18       "{$bottleNumber->action()}, " .
19       "{$bottleNumber->successor()} of beer on the wall.\n";
20   }
21 }
```

上面的代码可以运行，但包含了 `$number`。如果你将第 8-10 行的 `$number` 重命名为 `$bottleNumber`，该代码就接近完成了。

与其局限于单行，重构允许更大的更改。为了进行这次重构，首先添加一个属性来存储 `$bottleNumber` 并将其初始化为当前注入的 `$number`（第 7 行）。

[列表 8.35：设置 Bottle 为 Number](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-240/lib/Bottles.php#L28-L50)

```php
1 class BottleVerse {
2   protected $number;
3   protected $bottleNumber;
4   // ...
5   public function __construct(object $number) {
6     $this->number = $number;
7     $this->bottleNumber = $number;
8   }
9   // ...
10 }
```

现在在 `_lyrics` 中做两处更改。通过 `$this->bottleNumber` 引用属性，并删除 `$bottleNumber = $this->number;` 这一行。一旦完成这些操作，你可以删除空行，剩下：

[列表 8.36：歌词不再使用局部变量](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-250/lib/Bottles.php#L28-L48)

```php
1 class BottleVerse {
2   protected $number;
3   protected $bottleNumber;
4   // ...
5   public function __construct(object $number) {
6     $this->number = $number;
7     $this->bottleNumber = $number;
8   }
 
9   private function _lyrics(): string {
10     return
11       ucfirst("{$this->bottleNumber} of beer on the wall, ") .
12       "{$this->bottleNumber} of beer.\n" .
13       "{$this->bottleNumber->action()}, " .
14       "{$this->bottleNumber->successor()} of beer on the wall.\n";
15   }
16 }
```

现在删除上方第 6 行的 `$number` 属性赋值，并删除第 2 行的 `$number` 属性定义。接下来，将第 7 行的 `$number` 更改为 `$bottleNumber`。

[Listing 8.37: 合并对象创建](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c8-extract-bottleverse-280/lib/Bottles.php#L28-L46)

```php
 1 class BottleVerse {
 2   protected $bottleNumber;
 3 
 4   public static function lyrics(int $number): string {
 5     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
 6   }
 7 
 8   public function __construct(object $bottleNumber) {
 9     $this->bottleNumber = $bottleNumber;
10   }
 11 
 12   private function _lyrics(): string {
13     return
14       ucfirst("{$this->bottleNumber} of beer on the wall, ") .
15       "{$this->bottleNumber} of beer.\n" .
16       "{$this->bottleNumber->action()}, " .
17       "{$this->bottleNumber->successor()} of beer on the wall.\n";
18   }
19 }
```

这次重构就此结束。在进入章节总结之前，请最后思考一个问题。有人可能会认为 `BottleVerse::lyrics($number)` 做的事情多于一件事。它不仅创建了两个新对象（一个扮演瓶子数量角色的播放器，和一个 `BottleVerse` 类的实例），还向其中一个创建的对象发送了 `_lyrics` 方法。

如果你想严谨地将对象创建与对象使用分离开，可以将此代码重构为如下形式：

```php
 1 class BottleVerse {
 2   protected $bottleNumber;
 3 
 4   public static function for(int $number): object {
 5     return new BottleVerse(BottleNumber::for($number));
 6   }
 7 
 8   public static function lyrics(int $number) {
 9     return BottleVerse::for($number)->_lyrics();
10   }
 11   // ...
12 }
```

然而，上面的代码可能比你新新扩展的编程审美所要求的更加抽象和间接。这种分离可以推迟，直到有人提出需要直接访问 `BottleVerse` 对象的更改，而不仅仅是请求该对象的歌词。

### 8.9. 总结

本章将“99 瓶啤酒”歌曲的歌词从 `Bottles` 中提取出来，并将其放入一个新的 `BottleVerse` 类中。然后，它将 `BottleVerse` 的实例注入回 `Bottles`。提取 `BottleVerse` 减少了 `Bottles` 的职责，使其更易理解和维护。将 `BottleVerse` 注入 `Bottles` 弱化了 `Bottles` 与外部世界之间的耦合。`Bottles` 现在认为自己被注入了扮演歌词模板角色的播放器，只要该对象响应 `lyrics(number)` 方法，它就会乐意与任何新到达的对象协作。

提取 `BottleVerse` 的动力是产生具有不同歌词歌曲的新需求，即让歌词产生变化。本章的重构通过遵循面向对象设计的根本策略满足了这一需求：提取 `BottleVerse` 类隔离了新需求需要变化的行为。

在继续依赖代码气味和重构配方的同时，本章引入了**编程审美**的概念。编程审美是在不确定性时期引导你行为的一系列内部启发式。一旦你能够用流畅且有说服力的词汇来解释你的疑虑和建议的改进，你对代码正确性的模糊感觉就成了你审美的一部分。良好的编程审美关注于可能被证明是值得投入的改进。

本章提出了五条属于每个人的面向对象编程审美的准则：

*   将领域行为置于实例上。
*   反感允许实例方法知道常量名称。
*   寻求依赖注入的抽象，而不是硬编码的具体实现。
*   将对象创建推到边缘，期望对象在一个处被创建并在另一处被使用。
*   避免违反迪米特法则（Demeter violations），将产生这些违反的诱惑转化为寻找更深层抽象的动力。

遵循这些准则的实际效果是弱化对象之间的耦合。你应用这些准则的代码通常已经可以工作，因此遵循这些做法似乎是可选的，而且显然不是免费的。遵守这些准则会频繁增加代码量并增加间接层，至少在短期内如此。然而，这些增加的成本会被最终因解耦而节省的成本所抵消。

任何生存下来的应用程序都会发生变化。你唯一可以确定的是，你无法预测这种变化将发生在何处。变化的确定性加上变化位置的不确定性，意味着你最好的编程策略是从初始创建的那刻起，就努力弱化所有代码的耦合。

因此，这些准则并不试图预测未来；而是利用未来进行风险对冲。它们不是让你编写推测性假设某个特定功能未来可能需要的代码，而是告诉你要弱化所有代码的耦合，以便能够轻松适应任何可能到来的未来。

对未来的不确定性不是猜测的执照，而是解耦的指令。如果你能培养出一种驱动你这么做的的编程审美，你的未来将会更加光明。

## 9. 收获设计的收益

当前的“99 瓶啤酒”应用程序满足了所有已知需求。代码看起来非常面向对象，并且你可以为导致其当前形状的每一个决策提供一个有说服力的理由。

但测试已经陈旧了。它们逐渐从能够讲述“99 瓶啤酒”有用故事的测试，转变为对整个领域进行歪曲、甚至是谎言的测试。它们唯一的优点是当出错时，至少不至于完全崩溃。

得知哪里出错很重要，但测试可以做得更多。它们给了你一个向未来的读者解释领域的机会。它们暴露了导致代码难以重用的问题。良好的设计易于测试；当测试变得困难时，设计就需要关注了。

即使在现在，编写测试也会改进代码。本章正是如此。

### 9.1. 选择要的单元

每个类都应该有自己的单元测试，除非这样做可以省钱。跳过测试的门槛很高，但某些代码符合这一标准。本节首先将探讨这样一个案例。

#### 9.1.1. 单元测试与集成测试的区别

好消息是，编写测试将揭示每一处被忽略的紧耦合，并立即对你的修复给予奖励。以下是当前测试的回顾：

[列表 9.1：Bottles 测试回顾](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-10/test/BottlesTest.php#L5-L389)



## BottlesTest 代码示例

```php
 1 class BottlesTest extends \PHPUnit\Framework\TestCase {
 2   public function test_the_first_verse() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n";
 8     $this->assertEquals($expected, (new Bottles())->verse(99));
 9   }

10   public function test_another_verse() {
11     $expected =
12       "3 bottles of beer on the wall, " .
13       "3 bottles of beer.\n" .
14       "Take one down and pass it around, " .
15       "2 bottles of beer on the wall.\n";
16     $this->assertEquals($expected, (new Bottles())->verse(3));
17   }

18   public function test_verse_2() {
19     $expected =
20       "2 bottles of beer on the wall, " .
21       "2 bottles of beer.\n" .
22       "Take one down and pass it around, " .
23       "1 bottle of beer on the wall.\n";
24     $this->assertEquals($expected, (new Bottles())->verse(2));
25   }

26   public function test_verse_1() {
27     $expected =
28       "1 bottle of beer on the wall, " .
29       "1 bottle of beer.\n" .
30       "Take it down and pass it around, " .
31       "no more bottles of beer on the wall.\n";
32     $this->assertEquals($expected, (new Bottles())->verse(1));
33   }

34   public function test_verse_0() {
35     $expected =
36       "No more bottles of beer on the wall, " .
37       "no more bottles of beer.\n" .
38       "Go to the store and buy some more, " .
39       "99 bottles of beer on the wall.\n";
40     $this->assertEquals($expected, (new Bottles())->verse(0));
41   }

42   public function test_a_couple_verses() {
43     // ...
44     $this->assertEquals($expected, (new Bottles())->verses(99, 98));
45   }

46   public function test_a_few_verses() {
47     // ...
48     $this->assertEquals($expected, (new Bottles())->verses(2, 0));
49   }

50   public function test_the_whole_song() {
51     // ...
52     $this->assertEquals($expected, (new Bottles())->song());
53   }
54 }
```

## 测试策略分析

当 `Bottles` 是唯一的类时，这些测试是完全合逻辑的。作为对未知领域的首次尝试，它们表现得相当不错，但现在你已经更好地理解了“99 瓶啤酒”问题，你可能急于以不同的方式处理一些事情。

花一点时间回想一下为什么测试如此稀少。原始的 `BottleNumber` 类是通过“提取类”（Extract Class）重构配方从 `Bottles` 中提取出来并供其使用的。这个配方被证明是有效的。只要你每次只进行一次可撤销的更改，并在每次更改后都确认测试通过，你就可以放心地遵循该配方。

通过遵循配方而不是通过 TDD（测试驱动开发）来创建新类是完全允许的，但结果依赖于原始测试来确保提取出的类保持无误。使用配方将 `BottleNumber` 的正确性寄托给了 `Bottles` 的测试。如果 `BottleNumber` 错了，`Bottles` 的测试就会失败。

在提取 `BottleNumber` 或在进一步提取 `BottleNumber` 子类之后，并没有立即更新测试，而是通过提取另一个类 `BottleVerse` 加剧了对 TDD 的违背。`Bottles` 的测试为一系列其他对象提供了一个日益广泛的安全网。

`Bottles` 的测试最初是单元测试，但现在已变成了集成测试。单元测试旨在测试单个类的公共 API。被测试的单元通常需要几个协作对象才能运行，但这些其他对象是次要的，它们的存在是为了让你处理感兴趣的单元。单元测试不应该测试协作者。

集成测试旨在证明对象组之间的协作是正确的；它们展示了整个行为链可以工作。这正是这些 `Bottles` 测试所做的。

你通用的测试方法应该是为每个类创建一个单元测试，并测试该类公共 API 中的每个方法。要做到这一点，你必须选择从哪里开始。为了希望解决简单的问题能理清困难的问题，从简单的问题开始。

集成测试非常重要，但它们的作用与单元测试不同。集成测试擅长证明一组对象之间协作的正确性。它们展示了应用程序全部或部分部分的整体运行情况。因为它们覆盖的范围很广，所以通常运行较慢。

相比之下，单元测试是为了为你——程序员准备的。它们能帮助你写下、通信预期的行为、防止回归并调试较小的代码单元。当出现问题时，是单元测试在出错的行行附近提供了错误信息。由于它们缩小了任何问题背后的潜在代码魁祸首范围，使得调试变得更加容易。在编写代码时，它们不应该干扰你的思路，这意味着它们应该是快速的。

无论如何强调都不为过，大多数类都应该拥有自己的显式单元测试。这应该是你的默认观点。但正如每一条规则都注定会被打破一样，偶尔关于一个对象最有用的通信信息就是：它是如此的微小、简单或不可见，以至于单独对其进行测试会增加成本而非降低成本。偶尔，与其所属的单元结合测试一个对象是有意义的。这样做会创建一个渗透到集成与单元测试之间区域的测试，但如果你认为较小的对象是私有的，那么你完全可以认为整个整体就是一个单元测试。

`BottleNumber` 层次结构中的类就是那些如此微小、简单且不可见的例子，它们可能不值得拥有自己的单元测试。

如果你认同应用程序应该具有 100% 测试覆盖的原则，你可能需要重新审视你对该规则的定义。也许它意味着“100%的代码应该在单元测试期间执行”，而不是“100%的公共方法都应该有自己的独立测试”。

之前为 `BottleNumber1->pronoun` 想象的测试与实现细节结合得如此紧密，可能会干扰更改。测试应该给你改进代码的自由，而不是将你束缚在当前的实现上。当测试约束你而非解放你时，问问自己它们是否值得，并考虑省略它们。

在决定不为某个类提供单独单元测试的罕情况下，你必须能够通过清晰的理由来辩护这一决定。除了大小和复杂性，可见性也是一个重要的考虑因素。可见性是由该类所处的 `context`（上下文）决定的。

为了说明，这里是 `BottleVerse` 类的回顾，它在第 5 行引用了 `BottleNumber`：

[Listing 9.2: BottleVerse Reminder](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-10/lib/Bottles.php#L28-L46)

```php
 1 class BottleVerse {
 2   protected $bottleNumber;
 3 
 4   public static function lyrics(int $number): string {
 5     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
 6   }
 7 
 8   public function __construct(object $bottleNumber) {
 9     $this->bottleNumber = $bottleNumber;
10   }
 11 
 12   private function _lyrics(): string {
13     return
14       ucfirst("{$this->bottleNumber} of beer on the wall, ") .
15       "{$this->bottleNumber} of beer.\n" .
16       "{$this->bottleNumber->action()}, " .
17       "{$this->bottleNumber->successor()} of beer on the wall.\n";
18   }
19 }
```

`BottleVerse` 的整个公开 API 由第 2 行的 `lyrics` 静态函数组成，因此 `BottleVerse` 的所有实例方法都可以被视为私有。在这个唯一的公共方法中，`BottleVerse` 调用了 `BottleNumber` 工厂来获取一个扮演瓶数角色的实例。

注意 `BottleVerse` 对瓶数的依赖是多么深层次。`BottleVerse` 的实例完全依赖于瓶数来产生一段歌词。很难想象有任何不需要伴随瓶数而使用 `BottleVerse` 的场景。从 `BottleVerse` 的角度来看，它与它的瓶数是不可分割的。瓶数存在于 `BottleVerse` 的上下文中。

现在转转你的观点，从瓶数的角度考虑这些类之间的关系。情况发生了巨大的变化。单个瓶数并不知道 `BottleVerse` 的存在。它们不知道自己是某首歌的一部分。它们非常乐意在任何情况下被使用。它们对于上下文来说是 `independent`（独立的），这意味着它们可以很容易地在新的上下文中被复用。

前一段中的所有内容都说明瓶数是它们自成一体的事物，这反过来又说明它们应该拥有自己的测试。然而，它们非常微小、简单得令人痛苦，除了 `BottleVerse` 之外无在何处使用，并且可以由即将编写的 `BottleVerse` 测试完全覆盖。

决定如何测试的转折点是可见性。`BottleVerse` 已经承担了为自己提供 `BottleNumber` 的责任。`BottleNumber` 并不是从外部创建并注入的，而是由 `BottleVerse` 在内部知道了它们。`BottleVerse` 和 `BottleNumber` 之间的依赖对于外部观察者来说是不可见的。

在此时，应用程序中没有其他地方引用 `BottleNumber` 工厂或任何已制造的类。虽然以后将来某人可能会这样做，但目前还没有这样做。

`BottleVerse` 对 `BottleNumber` 的这种封装意味着，如果你站在公共对象之间的空间里，你永远看不到对 `BottleNumber` 的引用。它对观察者来说是如此不可见，以至于仿佛不存在。

总结来说，瓶数：

- 小型
- 简单
- `BottleVerse` 外部不可见
- 在 `BottleVerse` 之外不再使用

这些因素结合表明，至少目前，你应该将瓶数视为 `BottleVerse` 的组成部分，并在 `BottleVerse` 的单元测试中对它们进行测试。

大多数情况更为复杂，这意味着对象应该拥有自己的单元测试。即使这种情况将来也可能发生，导致瓶数应该进行独立的单元测试。在继续之前的最后一点是：瓶数最关键且复杂的部分是工厂，如果你将其他数字的行为交给 `BottleVerse`，你可能希望对其进行显式的单元测试。测试工厂时，重要的是测试工厂的职责，而不是它所制造的对象的职责。工厂的工作是接收一个数字并将数字转换为正确类的实例。因此，测试可能如下：

### Listing 9.3: Testing the Bottle Number Factory

```php
 1 class BottleNumberTest extends \PHPUnit\Framework\TestCase {
 2   public function test_factory() {
 3     // 0,1,6 是特殊的
 4     $this->assertInstanceOf(BottleNumber0::class, BottleNumber::for(0));
 5     $this->assertInstanceOf(BottleNumber1::class, BottleNumber::for(1));
 6     $this->assertInstanceOf(BottleNumber6::class, BottleNumber::for(6));
 7 
 8     // 其他数字获取默认值
 9     $this->assertInstanceOf(BottleNumber::class, BottleNumber::for(3));
10     $this->assertInstanceOf(BottleNumber::class, BottleNumber::for(7));
11     $this->assertInstanceOf(BottleNumber::class, BottleNumber::for(43));
12   }
13 }
```

上面的测试在单个测试中放置了多个断言，这违反了一条被广泛采纳的规则。然而，由于这是对工厂职责的最简洁表达，打破这条通用规则是合理的。

本节阐述了选择省略单元测试的一些考虑因素。这并不是许可编写一堆巨大的集成类测试并将其伪装成单元测试，而是承认某些事物之间的关联如此紧密，以至于独立测试它们会增加而非降低成本。你编写测试的目的是`省钱`，每一个潜在的测试都必须根据这一标准进行评估。

请运用明智的判断。极度倾向于为每个类公共 API 中的每个方法创建单元测试。但要确保所有测试都有其存在的理由，并消除那些没有理由的测试。

虽然所有的 `code` 都需要测试，但某些 `tests` 并不值得编写。

## 9.2. 重组测试

单元测试应该讲述一个引发启发的故事。它们应该展示并确认类的直接职责，而不做其他事情。你应该努力编写尽可能快的测试、数量最少的测试、使用意图的断言（expectations）以及最少代码。

下一节将检查现有测试，以确定谁真正对该行为负责，从而确定由谁来拥有这些测试。

现在，是时候处理 `BottleVerse` 了。

### 9.2.1. 收集 BottleVerse 测试

`BottleVerse` 比简单的瓶子数字类更复杂，也更高。以下是它的代码回顾：

[Listing 9.4: BottleVerse 实现了一个算法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-10/lib/Bottles.php#L28-L46)

```php
 1 class BottleVerse {
 2   protected $bottleNumber;
 3 
 4   public static function lyrics(int $number): string {
 5     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
 6   }
 7 
 8   public function __construct(object $bottleNumber) {
 9     $this->bottleNumber = $bottleNumber;
10   }
 11 
 12   private function _lyrics(): string {
13     return
14       ucfirst("{$this->bottleNumber} of beer on the wall, ") .
15       "{$this->bottleNumber} of beer.\n" .
16       "{$this->bottleNumber->action()}, " .
17       "{$this->bottleNumber->successor()} of beer on the wall.\n";
18   }
19 }
```

这里涉及相当的内容。相对于瓶子数字类，`BottleVerse` 显然更加复杂。很难一眼看出发生了什么，而且似乎匆忙更改可能会破坏某些东西。测试将增加安全性并帮助讲述这段代码的故事。

当某些外部实体选择它作为歌词模板并将其注入 `Bottles` 时，就会使用 `BottleVerse`，如下第 4 行所示：



# Listing 9.5: BottleVerse 与 Bottles 松耦合

```
 1 class Bottles {
 2   protected $verseTemplate;
 3 
 4   public function __construct(string $verseTemplate = BottleVerse::class) {
 5     $this->verseTemplate = $verseTemplate;
 6   }
 7   // ...
 8   public function verse(int $number): string {
 9     return $this->verseTemplate::lyrics($number);
10   }
11 }
```

在上一节中，`BottleNumber` 和 `BottleVerse` 之间的连接从外部是不可见的。在上面的代码中，`Bottles` 与其歌词模板之间的关系是暴露的。`Bottles` 不提供自己的模板；由他人选择并传入。

这种协作是公开的。注入歌词依赖降低了 `Bottles` 和 `BottleVerse` 之间的耦合，使这两个类相互独立。不要被第 4 行 `$verseTemplate` 默认为 `BottleVerse` 的事实所困扰；这是早期重构的产物，是因为现有测试在没有传递参数的情况下构造了 `Bottles`。本书的后续章节将更新 `Bottles` 测试以适应这种默认。代码复杂性和可见性的结合意味着 `BottleVerse` 应该拥有自己的单元测试。

像一样，通过创建一个类来开始：

# Listing 9.6: 为 BottleVerse 创建测试

```
1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
2 }
```

现在你需要决定测试什么。由于单元测试应对类公共 API 中的每个方法包含一个测试，你需要测试 `BottleVerse` 的 `lyrics` 函数。如果这样做有助于向读者解释其行为，那么为单个方法创建多个测试也是可以。

这个 `lyrics` 方法负责接收一个数字并返回相应的歌词。记下这一点，查看现有的 `Bottles` 测试：

# Listing 9.7: 现有测试

```
1 class BottlesTest extends \PHPUnit\Framework\TestCase {
2   public function test_the_first_verse() {
3     $expected =
4       "99 bottles of beer on the wall, " .
5       "99 bottles of beer.\n" .
6       "Take one down and pass it around, " .
7       "98 bottles of beer on the wall.\n";
8     $this->assertEquals($expected, (new Bottles())->verse(99));
9   }
 
10   public function test_another_verse() {
11     // ...
12     $this->assertEquals($expected, (new Bottles())->verse(98));
13   }
 
14   public function test_verse() {
15     // ...
16     $this->assertEquals($expected, (new Bottles())->verse(2));
17   }
 
18   public function test_verse() {
19     // ...
20     $this->assertEquals($expected, (new Bottles())->verse(1));
21   }
 
22   public function test_verse() {
23     // ...
24     $this->assertEquals($expected, (new Bottles())->verse(0));
25   }
 
26   public function test_a_couple_verses() {
27     // ...
28     $this->assertEquals($expected, (new Bottles())->verses(99, 98));
29   }
 
30   public function test_a_few_verses() {
31     // ...
32     $this->assertEquals($expected, (new Bottles())->verses(2, 0));
33   }
 
34   public function test_the_song() {
35     // ...
36     $this->assertEquals($expected, (new Bottles())->song());
37   }
38 }
```

`BottlesTest` 已经包含了针对“99 Bottles”各个节的多个测试。例如，上面的第 2 行测试确认了输入 `99` 会产生该节的歌词。上面又出现了四次类似的单节测试（注意第 13、18、23 和 28 行的断言）。

这些测试是在第 2 章对 `Bottles` 进行初始 TDD 时创建的，当时它们非常有意义。现在 `BottleVerse` 负责创建“99 Bottles”歌曲的各个节，`BottleVerseTest` 应该承担证明歌词正确的责任。这意味着 `Bottles` 中每个对“99 Bottles”单节进行断言的测试都应该移动到 `BottleVerseTest` 中。

开始的最佳方法是仔细地只移动一个测试。由于 `test_the_first_verse` 已经存在，移动将通过重构完成。测试套件目前通过通过，你不希望意外引入错误。移动代码最安全的方法是使用现在已经熟悉的技术：复制代码，在新处使其运行，然后从旧处删除它。

考虑到此，将 `BottlesTest` 中的 `test_the_first_verse` 复制到 `BottleVerseTest`，如下所示（注意，尽管在下面的列表中一起出现，但 `BottlesTest` 和 `BottleVerseTest` 位于不同的文件中）：

# Listing 9.8: 复制第一个测试

```php
 1 class BottlesTest extends \PHPUnit\Framework\TestCase {
 2   public function test_the_first_verse() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n";
 8     $this->assertEquals($expected, (new Bottles())->verse(99));
 9   }
10   // ...
11 }
12
13 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 14   public function test_the_first_verse() {
 15     $expected =
 16       "99 bottles of beer on the wall, " .
 17       "99 bottles of beer.\n" .
 18       "Take one down and pass it around, " .
 19       "98 bottles of beer on the wall.\n";
 20     $this->assertEquals($expected, (new Bottles())->verse(99));
 21   }
22 }
```

不要更改复制的测试代码。运行测试。应该有 9 个通过了。

接下来，修改新的断言以测试 `BottleVerse::lyrics($number)` 而不是 `Bottles->verse`，如下所示第 8 行所示：

# Listing 9.9: 更新断言

```php
 1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 2   public function test_the_first_verse() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n";
 8     $this->assertEquals($expected, (new Bottles())->verse(99));
 9   }
10 }
```

运行测试将显示仍有 9 个通过了。

既然 `BottleVerseTest` 中的新测试已证明可以工作，你可以删除 `BottlesTest` 中的旧版本。这留下了 8 个通过的测试。

验证此过程后，继续将 `BottlesTest` 中的所有其他单节测试复制到 `BottleVerseTest` 中，同样不要更改复制的代码。完成后后，`BottleVerseTest` 将如下：

# Listing 9.10: 复制剩余的单节测试

```php
 1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 2   public function test_the_first_verse() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n";
 8     $this->assertEquals($expected, BottleVerse::lyrics(99));
 9   }
10
 11   public function test_another_verse() {
 12     // ...
 13     $this->assertEquals($expected, (new Bottles())->verse(3));
 14   }
15
 16   public function test_verse_2() {
 17     // ...
 18     $this->assertEquals($expected, (new Bottles())->verse(2));
 19   }
20
 21   public function test_verse_1() {
 22     // ...
 23     $this->assertEquals($expected, (new Bottles())->verse(1));
 24   }
25
 26   public function test_verse_0() {
 27     // ...
 28     $this->assertEquals($expected, (new Bottles())->verse(0));
 29   }
30 }
```

此时，你将拥有 12 个通过的测试。在确保全部通过后，更新 `BottleVerseTest` 中的断言以调用 `BottleVerse::lyrics`，如下所示第 9、14、19 和 24 行，或许可以借此练习使用正则表达式替换：

# Listing 9.11: 更新测试断言

```php
 1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 2   public function test_the_first_verse() {
 3     // ...
 4     $this->assertEquals($expected, BottleVerse::lyrics(99));
 5   }
 6
 7   public function test_another_verse() {
 8     // ...
 9     $this->assertEquals($expected, BottleVerse::lyrics(3));
10   }
11
 12   public function test_verse_2() {
 13     // ...
 14     $this->assertEquals($expected, BottleVerse::lyrics(2));
15   }
16
 17   public function test_verse_1() {
 18     // ...
 19     $this->assertEquals($expected, BottleVerse::lyrics(1));
20   }
21
 22   public function test_verse_0() {
 23     // ...
 24     $this->assertEquals($expected, BottleVerse::lyrics(0));
25   }
26 }
```

在上述更新后，12 个测试应该仍然通过。一旦确认了这一点，你就可以放心地删除 `BottlesTest` 中的四个过时测试，而不用担心破坏任何内容。这次删除让你回到共 8 个通过的测试，并将 `BottlesTest` 减少到 3 个。

`BottleVerse` 的测试现在证明了它可以正确生成每种版本的“99 Bottles”歌词。歌词测试是正确且完整的，基本上是第 2 章最初创建的测试的更新版本。在当时，这些测试看起来足够了，但现在你从整个测试套件的角度来看，你可能会对这些测试所讲述的故事感到失望。它们错过了向未来读者传达对领域深层理解的黄金机会。

`BottleVerse` 的某些测试需要更好的名称。

## 9.2.2. 揭示意图

为一个新领域编写第一个测试可能是困难到令人瘫痪的。通常情况下，编写第十个、第五个或第二个要容易得多。第一个测试之所以重要，是因为没有它你根本无法开始。

尽管如此，这正是*先*写测试真正发光异彩的地方。与其编写你不理解的代码，不如在一个你不理解的测试上挣扎要好得多。

因此，尽管对细节还比较模糊，但在赋予编写代码生成 1) 整首“99 Bottles”歌、2) 一系列歌节或 3) 单节歌节的任务时，你勇敢地决定创建一个 `Bottles` 类，并提供 `song`、`verses` 和 `verse` 的公共 API。然后你选择经典的从内向外的 TDD 风格，并开始测试 `verse` 方法。此时，你想编写一个接收数字并返回相关歌节歌词的测试。为了实现这一点，你必须决定使用哪个数字以及给测试起名字。

名称是重要的，你本可以花时间为第一个测试找到一个完美的名称。在这种情况下，无知反而派上了用场。因为你知道在更好地理解该领域之前很难选出一个棒的名字，而且你也知道编写测试会提高你对该领域的理解，所以你没有在第一个名字上花费太多时间。调用 `test_the_first_verse` 让你能够继续下去，而继续下去带给了你有一天拥有足够知识并做得更好的希望。

至于选择第一个测试的数字，`99` 是合理的，因为它出现在歌曲的开头。当未来的程序员阅读你的测试时，他们会从每个决策中推导出含义。以 `99` 开始是意料之外的。任何其他数字都会让他们好奇你选择背后的深层含义。



`test_the_first_verse`/`'another verse'` 测试的存在是为了说明从 `99` 到 `3` 的歌句内容遵循类似的规则，但它们的名称并没有提供任何关于该规则存在的提示。测试体本身没问题——问题出在它们的名称上。当这些模糊的名称是你所能做的最好选择时，它们是完全可以的，但现在你了解得更多了，可以做得更好。是时候改进这个故事了。

这两个测试的名称应该传达以下信息：

* 这是一个歌句测试
* 存在一条规则
* 它适用于大多数歌句
* 它涉及一个范围
* 一个测试针对上限
* 另一个测试针对下限

像 `'verse general rule upper bound'` 和 `'verse general rule lower bound'` 这样的名称完美地满足了这些约束。

既然你已经完成了最困难的部分并找到了更好的名称，请像下方的第 2 行和第 11 行所示重命名前两个 `BottleVerse` 测试：

[Listing 9.12：为 99 和 3 重命名歌句测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-100/test/BottleVerseTest.php#L5-L50)

```
 1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 2   public function test_verse_general_rule_upper_bound() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n";
 8     $this->assertEquals($expected, BottleVerse::lyrics(99));
 9   }
10 
11   public function test_verse_general_rule_lower_bound() {
 12     $expected =
 13       "3 bottles of beer on the wall, " .
 14       "3 bottles of beer.\n" .
 15       "Take one down and pass it around, " .
 16       "2 bottles of beer on the wall.\n";
 17     $this->assertEquals($expected, BottleVerse::lyrics(3));
 18   }
 19   // ...
 20 }
```

这里是生成的 `BottleVerseTest` 的概览：

[Listing 9.13：中间版本的 BottleVerse 测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-100/test/BottleVerseTest.php#L5-L50)

```
 1 class BottleVerseTest extends \PHPUnit\Framework\TestCase {
 2   public function test_verse_general_rule_upper_bound() {
 3     // ...
 4     $this->assertEquals($expected, BottleVerse::lyrics(99));
 5   }
 6
 7   public function test_verse_general_rule_lower_bound() {
 8     // ...
 9     $this->assertEquals($expected, BottleVerse::lyrics(3));
10   }
11
12   public function test_2() {
13     // ...
14     $this->assertEquals($expected, BottleVerse::lyrics(2));
15   }
16
17   public function test_1() {
18     // ...
19     $this->assertEquals($expected, BottleVerse::lyrics(1));
20   }
21
22   public function test_0() {
23     // ...
24     $this->assertEquals($expected, BottleVerse::lyrics(0));
25   }
26 }
```

上面的名称是一致的。它们令人悦目，并比以前传达了更多信息。但它们仍然不够好。这些名称清楚地表明某些歌句遵循共同规则，而另一些并非如此。虽然完全正确，但对 7 和 6 的测试混淆了原本清晰的规则水域。如果你担心读者会感到困惑，请花点思考如何重命名这些测试来缓解这种担忧。

然而，目前的名称可能足够了。它们有了显著改进，并揭示了以前隐含的信息。它们是对命名力量的致敬。现在是时候宣布 `BottleVerse` 的测试完成并转向 `Bottles` 了。

### 9.3 寻求上下文独立

“上下文”一词已经多次使用，是基于其技术含义根据上下文清晰的假设。你可能已经对它的含义有了某种想法，但对这个术语进行讨论是必要的。

对象的上下文是其周围环境，或者它存在的相互关联条件。需要巨大、复杂上下文的对象对环境很挑剔；它们对外部世界的了解过多。它们要求环境必须满足某些条件，这限制了它们在特定情况下的使用。对象了解得越少就越易用。对环境期望越少的对象越容易应用于新颖的情况，因此提供了更大的实用性。最好用的是那些完全独立于上下文的对象；它们对外部世界没有预期，也不提出任何要求。在上下文方面，无知确实是福。

本节将通过检查 `Bottles` 类及其剩余测试，并减少它们的上下文来探索这些思想。

#### 9.3.1 检查 Bottles 的职责

在查看 `Bottles` 的测试之前，停下来并回顾一下类本身。

[Listing 9.15：重新考虑 Bottles](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-120/lib/Bottles.php#L5-L26)

```
 1 class Bottles {
 2   protected $verseTemplate;
 3
 4   public function __construct(string $verseTemplate = BottleVerse::class) {
 5     $this->verseTemplate = $verseTemplate;
 6   }
 7
 8   public function song(): string {
 9     return $this->verses(99, 0);
10   }
11
12   public function verses(int $upper, int $lower): string {
13     return implode(
14       "\n",
15       array_map([$this, 'verse'], range($upper, $lower))
16     );
17   }
18
19   public function verse(int $number): string {
20     return $this->verseTemplate::lyrics($number);
21   }
22 }
```

上面的代码是迭代提取需要变动的部分后的最终结果。结果是一个与“99 个瓶子”歌曲几乎没有关系的类。它保留了以前语境的痕迹（名称 `Bottles`、默认的 `BottleVerse`、魔法数字 `99`），但不熟悉代码历史的人无法认出这个类就是那首歌。

`Bottles` 不再是一个合适的名称了。它根本不是一个 `Bottles`；它是完全不同的东西。

`Bottles` 这个名字贬低了这个类的价值，使其看起来比其实际价值要低。它产生时环境的遗留继续将它束缚在一个特定的语境中，尽管它现在已经更具通用性。这个类已经变得更加抽象，但它的名字本身将阻止程序员识别出它更广泛的用途。

重新审视这段代码并描述它的功能。类的命名应该根据它的本质：它是什么？

你可能很倾向于说它是一首 `Song`。这是正确的，但你可以做得更好。它是一种特定的歌曲，其特征是通过上面第 15 行的 `range($upper, $lower)` 来区分的。可以假设具有有编号歌节的歌曲会递增计数，而这首歌有点出乎意料，因为它从顶部开始向下递减计数。这是一个 `CountdownSong`。

下一节将 `Bottles` 重命名为 `CountdownSong`，但在继续之前，请坐下来思考一下，一个名为 `CountdownSong` 的类与一个名为 `Bottles` 的类感觉有多么不同。`Bottles` 是狭隘的，只在一个特定情况下有用。而 `CountdownSong` 是通用的，在很多情况下都用。对于一个名为 `Bottles` 的类来说，`BottleVerse` 默认值和硬编码的 `99` 似乎完全合理。但在名为 `CountdownSong` 的类中，这些先前语境的遗迹纯粹是恼人的，你会有动力移除它们。`Bottles` 限制了可能性；`CountdownSong` 扩展了可能性。

你是否感到脚下的世界发生了旋转？这是对命名力量的又一次证明。

通过简单的重构，可以将 `Bottles` 重命名为 `CountdownSong`。一如既往，这个过程是进行单步撤销的更改，并在每次更改后确保测试通过。

从复制整个 `Bottles` 类开始，并将副本的名称改为 `CountdownSong`：

[Listing 9.16: 将 Bottles 复制为 CountdownSong](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-130/lib/Bottles.php#L5-L49)

```
 1 class CountdownSong {
 2   protected $verseTemplate;
 3
 4   public function __construct(string $verseTemplate = BottleVerse::class) {
 5     $this->verseTemplate = $verseTemplate;
 6   }
 7
 8   public function song(): string {
 9     return $this->verses(99, 0);
10   }
11
12   public function verses(int $upper, int $lower): string {
13     return implode(
14       "\n",
15       array_map([$this, 'verse'], range($upper, $lower))
16     );
17   }
18
19   public function verse(int $number): string {
20     return $this->verseTemplate::lyrics($number);
21   }
22 }
```



```php
 1 class CountdownSong {
 2   protected $verseTemplate;
 3 
 4   public function __construct(string $verseTemplate = BottleVerse::class) {
 5     $this->verseTemplate = $verseTemplate;
 6   }
 7 
 8   public function song(): string {
 9     return $this->verses(99, 0);
10   }
11 
12   public function verses(int $upper, int $lower): string {
13     return implode(
14       "\n",
15       array_map([$this, 'verse'], range($upper, $lower))
16     );
17   }
18 
19   public function verse(int $number): string {
20     return $this->verseTemplate::lyrics($number);
21   }
22 }
```

现在 `CountdownSong` 存在了，但在继续之前……（注：原文此处有逻辑重复，译文已去重）

现在 `CountdownSong` 存在了，你可以更新测试。首先，将 `BottlesTest` 重命名为 `CountdownSongTest`，如下所示：

[Listing 9.17: 修改测试名称](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-130/test/CountdownSongTest.php#L5-L34) 

```php
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_couple_verses() {
 3     // ...
 4     $this->assertEquals($expected, (new Bottles())->verses(99, 98));
 5   }
 6 
 7   public function test_few_verses() {
 8     // ...
 9     $this->assertEquals($expected, (new Bottles())->verses(2, 0));
10   }
 11 
 12   public function test_whole_song() {
 13     // ...
 14     $this->assertEquals($expected, (new Bottles())->song());
15   }
 16 }
```

现在进入 `CountdownSongTest` 并将所有提到 `Bottles` 的地方改为 `CountdownSong`，如下：

[Listing 9.18: 在测试中使用 CountdownSong](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-130/test/CountdownSongTest.php#L5-L34) 

```php
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_couple_verses() {
 3     // ...
 4     $this->assertEquals($expected, (new CountdownSong())->verses(99, 98));
 5   }
 6 
 7   public function test_few_verses() {
 8     // ...
 9     $this->assertEquals($expected, (new CountdownSong())->verses(2, 0));
10   }
 11 
 12   public function test_whole_song() {
 13     // ...
 14     $this->assertEquals($expected, (new CountdownSong())->song());
15   }
 16 }
```

此时，旧的 `Bottles` 类已不再被使用，因此你可以删除它。这会为你留下 10 个通过的测试。

这种更改类名的过程涉及了几个小步骤，而不是一个大步骤。它安排了这五个必要的更改（类名、测试名以及测试中对旧类的三次引用），以便它们可以顺序进行，同时始终保持测试处于绿色状态。

在这样一个小规模的问题中，你可能一次性进行所有更改也没问题，但你不应该这样做。养成重构的习惯。当你坚持在绿色状态下进行更改时，你不需要走太远就能调试你刚刚破坏了什么。这让一切变得更简单。总是进行重构的成本比有时调试大堆修改的代码要低得多。

#### 9.3.2. 使用伪造对象净化测试

现在 `CountdownSong` 存在了，仔细观察它的测试（重复如下）：

[Listing 9.19: CountdownSong 测试仍固于 99 个瓶子的歌词](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-130/test/CountdownSongTest.php#L5-L34) 

```php
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_a_couple_verses() {
 3     $expected =
 4       "99 bottles of beer on the wall, " .
 5       "99 bottles of beer.\n" .
 6       "Take one down and pass it around, " .
 7       "98 bottles of beer on the wall.\n" .
 8       "\n" .
 9       "98 bottles of beer on the wall, " .
 10       "98 bottles of beer.\n" .
 11       "Take one down and pass it around, " .
 12       "97 bottles of beer on the wall.\n";
 13     $this->assertEquals($expected, (new CountdownSong())->verses(99, 98));
 14   }
 15 
 16   public function test_a_few_verses() {
 17     $expected =
 18       "2 bottles of beer on the wall, " .
 19       "2 bottles of beer.\n" .
 20       "Take one down and pass it around, " .
 21       "1 bottle of beer on the wall.\n" .
 22       "\n" .
 23       "1 bottle of beer on the wall, " .
 24       "1 bottle of beer.\n" .
 25       "Take it down and pass it around, " .
 26       "no more bottles of beer on the wall.\n" .
 27       "\n" .
 28       "No more bottles of beer on the wall, " .
 29       "no more bottles of beer.\n" .
 30       "Go to the store and buy some more, " .
 31       "99 bottles of beer on the wall.\n";
 32     $this->assertEquals($expected, (new CountdownSong())->verses(2, 0));
 33   }
 34 
 35   public function test_the_whole_song() {
 36     $expected = <<< SONG
 37 99 bottles of beer on the wall, 99 bottles of beer.
 38 Take one down and pass it around, 98 bottles of beer on the wall.
 39 
 40 98 bottles of beer on the wall, 98 bottles of beer.
 41 Take one down and pass it around, 97 bottles of beer on the wall.
 42 
 43 97 bottles of beer on the wall, 97 bottles of beer.
 44 Take one down and pass it around, 96 bottles of beer on the wall.
 45 
 46 // ...
 47 
 48 No more bottles of beer on the wall, no more bottles of beer.
 49 Go to the store and buy some more, 99 bottles of beer on the wall.
 50 
 51 SONG;
 52     $this->assertEquals($expected, (new CountdownSong())->song());
 53   }
 54 }
```

这些测试的用处在于它们防止了回归，但在讲述 `CountdownSong` 的故事方面，它们是彻底的失败。它们存在你刚刚在代码中修复的问题；它们仍然反映了它们来源的上下文。预期值具有误导性，而第 46 行省略的 290 行代码仅凭其重量就能将你的思维拉回“99 瓶啤酒”的语境。这些测试强烈暗示了 `CountdownSong` 是关于“99 瓶啤酒”的。

测试证明代码可以工作是所应当的，但它们也有其他用途，其中一个向读者解释领域。这些测试所讲述的故事并不是 `CountdownSong` 的故事。测试应该解释类的本质。`CountdownSong` 的核心职责是接收一个歌词模板并生成一首倒数的歌曲。这些测试未能传达这些内容。

如果你仔细研究测试足够久，最终可能会发现预期中包含了倒数的歌词——但话说回来，你也可能发现。此外，`CountdownSong` 接受注入的歌词模板这一事实是完全不可见的。通过阅读测试，你无法得知歌词模板是可以变化的。

考虑第一个预期。如果 `test_a_couple_verses` 测试不是像这样，而是像这样，它的意图将会会更加清晰：

```php
$expected =
  "99 bottles of beer on the wall, " .
  "99 bottles of beer.\n" .
  "Take one down and pass it around, " .
  "98 bottles of beer on the wall.\n" .
  "\n" .
  "98 bottles of beer on the wall, " .
  "98 bottles of beer.\n" .
  "Take one down and pass it around, " .
  "97 bottles of beer on the wall.\n";
```

它的预期值读起来像：

```php
$expected =
  "This is verse 99.\n" .
  "\n" .
  "This is verse 98.\n" .
  "\n" .
  "This is verse 97.\n";
```

上面的第二个例子清楚地表明，预期输出包含倒数的歌词。这是一个更好的测试，而且拥有它就像想象一样简单。不要被你对现有歌词模板的知识束缚在原始环境中；`CountdownSong` 的测试注定要与 `BottleVerse` 协作。为你想要讲述的故事制定一个愿望。

结论是 `Fake` 是一个模式名称，因此 `VerseFake` 违反了 `don’t-include-pattern-names-in-class-names` 规则。

规则的存在是为了节省成本，而 `VerseFake` 违反的两个规则主要是为了在生产代码节省成本；它们在为了简化测试而创建的代码中可能并不适用。例如，`VerseFake` 的目的是伪造歌词模板的角色。在这种情况下，`VerseFake` 可能是意图表达最清晰的名字。如果你发现需要多种类型的伪造，你可能需要在它们的名称中添加额外的限定符（`SimpleVerseFake`、`ComplicatedVerseFake`），但 "fake" 一词在你的测试领域仍然增加了意义。

同样，生产代码的形状不要干扰你修改它的能力也很重要。`put-domain-behavior-on-instances` 规则服务于这一目标。然而，在测试中，你并不关心保持伪造的可变性，而更感兴趣于直接传达它的职责。将行为放在静态函数中简化了 `VerseFake` 中的代码，但代价是降低了它的适应性。这种权衡在仅供测试使用的代码中是你乐意做的。

要使用 `VerseFake`，创建一个备替的 `test_a_couple_verses` 测试。因为不允许重名，你必须先修改原始的名称。下面的第 5 行通过在初始测试名称后附加 `original` 实现了这一点，第 2 行显示了重用旧名称的新测试开头。

[Listing 9.21: 引入备替测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-180/test/CountdownSongTest.php#L11-L353) 

```php
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_a_couple_verses() {
 3   }
 4 
 5   public function test_a_couple_verses_original() {
 6     $expected =
 7       "99 bottles of beer on the wall, " .
 8       "99 bottles of beer.\n" .
 9       "Take one down and pass it around, " .
 10       "98 bottles of beer on the wall.\n" .
 11       "\n" .
 12       "98 bottles of beer on the wall, " .
 13       "98 bottles of beer.\n" .
 14       "Take one down and pass it around, " .
 15       "97 bottles of beer on the wall.\n";
 16     $this->assertEquals($expected, (new CountdownSong())->verses(99, 98));
 17   }
 18   // ...
 19 }
```

接下来，用一个使用伪造的全新实现填充这个备替测试，如下：

[Listing 9.22: 备替测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-190/test/CountdownSongTest.php#L11-L363) 

```php
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_a_couple_verses() {
 3     $expected =
 4       "This is verse 99.\n" .
 5       "\n" .
 6       "This is verse 98.\n" .
 7       "\n" .
 8       "This is verse 97.\n";
 9     $this->assertEquals(
 10       $expected,
 11       (new CountdownSong(VerseFake::class))->verses(99, 97)
 12     );
 13   }
 14   
 15   public function test_a_couple_verses_original() {
 16     $expected =
 17       "99 bottles of beer on the wall, " .
 18     // ...
 19     $this->assertEquals($expected, (new CountdownSong())->verses(99, 98));
 20   }
 21   //
```



上面的备替 `test_a_couple_verses` 测试（第 11 行）注入了 `VerseFake` 并根据该模板的行为（第 3 行）设置了断言。此时 11 个测试应该通过。

既然备替测试已证明可用，删除旧的进行清理。你现在应该有 10 个测试。这使得 `CountdownSongTest` 变为：

[Listing 9.23: 保留备替测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-200/test/CountdownSongTest.php#L11-L49)

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_a_couple_verses() {
    $expected =
      "This is verse 99.\n" .
      "\n" .
      "This is verse 98.\n" .
      "\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }
  
  public function test_a_few_verses() {
    // ...
  }
  
  public function test_the_song() {
    // ...
  }
}
```

注意 `test_a_couple_verses` 现在更具表现力，因为它包含的噪音更少。这个新版本验证了三个连续歌词（第 11 行的 `99, 97`）而不是两个。`VerseFake` 非常短，你可以扩大预期以更清晰地说明这是一个范围，而不会使测试变得复杂。

`test_a_couple_verses` 名称现在已经过时。记下它需要更新，但暂时可以容忍它。与旧的相比，这个新测试的主体意图更清晰且更短。使用伪造将其转化为简洁的模型。人们可能希望所有测试都是直观的。

### 9.3.3 清理冗余测试

接下来，关注另一个关于歌词的测试 `test_a_few_verses`，位于下面的第 15 行：

[Listing 9.24: 比较歌词测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-200/test/CountdownSongTest.php#L11-L49)

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_a_couple_verses() {
    $expected =
      "This is verse 99.\n" .
      "\n" .
      "This is verse 98.\n" .
      "\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }
  
  public function test_a_few_verses() {
    $expected =
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n" .
      "\n" .
      "1 bottle of beer on the wall, " .
      "1 bottle of beer.\n" .
      "Take it down and pass it around, " .
      "no more bottles of beer on the wall.\n" .
      "\n" .
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";
    $this->assertEquals($expected, (new CountdownSong())->verses(2, 0));
  }
  
  public function test_the_song() {
    // ...
  }
}
```

`test_a_few_verses` 是否必要？如果 `test_a_couple_verses` 和 `test_a_few_verses` 测试的是不同的内容，你应该保留它们。如果它们测试的是相同的内容，你应该删除其中一个。

尽管这些测试定义了不同的预期，但它们在逻辑上是相同的。每个测试都断言 `CountdownSong` 在给定的歌词模板和范围内产生正确的歌词列表。由于它们测试的是相同的内容，你不需要同时拥有它们。

通过想象添加其他冗余 `verses` 测试的逻辑结果，可以更有效地说明这一点。如果你觉得有必要同时测试 `99-97` 和 `2-0`，那么为什么不测试 `99-96` 呢？还有 `99-95` 呢？`40-28` 等？这样会导致疯狂。这些多余的测试会困扰读者并增加维护成本，而不会增加额外的安全性。一个 `verses` 测试就足够了。到此为止。

删除 `test_a_few_verses` 将测试压缩为：

[列表 9.25：仅测试一次 Verses 方法](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-210/test/CountdownSongTest.php#L11-L330) 

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_a_couple_verses() {
    $expected =
      "This is verse 99.\n" .
      "\n" .
      "This is verse 98.\n" .
      "\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }

  public function test_the_whole_song() {
    $expected = <<< SONG
99 bottles of beer on the wall, 99 bottles of beer.
// ...
Go to the store and buy some more, 99 bottles of beer on the wall.

SONG;
    $this->assertEquals($expected, (new CountdownSong())->song());
  }
}
```

生成的 `CountdownSongTest` 包含两个测试。整个测试套件现在包含九个测试用例，且所有测试用例都通过了。

`CountdownSong` 的公共 API 包含三个方法，但 `CountdownSongTest` 只覆盖了其中两个。上面的示例没有对 `verse` 进行测试。由于 `CountdownSong` 提供了这个公共方法，`CountdownSongTest` 必须对其测试。

`CountdownSongTest` 原测试了整个 API（`song`、`verses` 和 `verse`）。然而，原始的 `verse` 测试是针对“99 Bottles”的，它们最近被移动到了所属的 `BottleVerseTest` 中。这一移动导致 `CountdownSong` 的覆盖率留下了空白；它应该有一个针对 `verse` 的测试。

在经历了创建和使用 `VerseFake` 的练习后，在 `CountdownSongTest` 中为 `verse` 构建一个意图清晰的测试是非常容易的。这是一个示例：

[列表 9.26：在 CountdownSongTest 中测试整个 API](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-220/test/CountdownSongTest.php#L11-L339) 

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_verse() {
    $expected =
      "This is verse 500.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(500)
    );
  }

  public function test_a_couple_verses() {
    // ...
  }

  public function test_the_whole_song() {
    // ...
  }
}
```

注意，`CountdownSong` 使用 `500` 作为诗句编号来测试 `verse`。它刻意地传达了一个观点：`99-0` 范围之外的数字是可以接受的。这是一个明显的证据，表明 `CountdownSong` 并不限于其来源的“99 Bottles”上下文的限制。

应该再次有 10 个通过的测试。

既然你已经选择了 `test_verse` 作为 `verse` 测试的名称，请重新评估 `test_a_couple_verses` 的名称。将此测试命名为 `test_verse` 暗示了一种模式，遵循该模式会让其他测试更容易理解。如果将 `test_a_couple_verses` 重命名为 `test_verses`（如下所示），你的意图将更加清晰：

[列表 9.27：改进 Verses 测试名称](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-230/test/CountdownSongTest.php#L11-L339) 

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_verse() {
    $expected =
      "This is verse 500.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(500)
    );
  }

  public function test_verses() {
    $expected =
      "This is verse 99.\n" .
      "\n" .
      "This is verse 98.\n" .
      "\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }

  public function test_the_whole_song() {
    // ...
  }
}
```

使用 `VerseFake` 简化了 `verse` 和 `verses` 测试。它增强了 `CountdownSong` 的故事，而不是像旧的“99 Bottles”期望那样干扰它。

剩下的测试是针对 `song`。

#### 9.3.4. 从松耦合中获益

既然你已经通过 `VerseFake` 改进了其他测试，现在该处理 `test_the_whole_song` 了，其形式如下：

[列表 9.28：重访整个歌曲](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-230/test/CountdownSongTest.php#L11-L339)

```
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  // ...
  public function test_the_whole_song() {
    $expected = <<< SONG
99 bottles of beer on the wall, 99 bottles of beer.
98 bottles of beer on the wall, 98 bottles of beer.
97 bottles of beer on the wall, 97 bottles of beer.

SONG;
    $this->assertEquals($expected, (new CountdownSong())->song());
  }
}
```

这个测试需要处理。考虑到第 11 行省略的代码，它有 305 行，其中大部分都是期望。这种期望墙使得人们无法理解测试想要讲述的故事。

你已经使用了 `VerseFake` 来改进其他测试。在这里注入它无疑会有帮助，但无法解决文本墙的问题。

看看 `CountdownSong`，看看你能否发现问题所在：

[列表 9.29：CountdownSong 重现](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-230/lib/Bottles.php#L5-L26) 

```
class CountdownSong {
  protected $verseTemplate;

  public __construct(string $verseTemplate = BottleVerse::class) {
    $this->verseTemplate = $verseTemplate;
  }

  public function song(): string {
    return $this->verses(99, 0);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return $this->verseTemplate::lyrics($number);
  }
}
```

上面第 9 行的 `99` 判定了你面对一个包含 100 个诗句的期望。

将类泛化为 `CountdownSong` 解决了第一个问题，但其他遗留问题仍然存在。这些已过时上下文的回声会误导读者并干扰重用。由于测试是第一次重用，可读性问题通过测试被暴露了出来。这正是 `test_the_whole_song` 中那堵墙背后的原因。那个尴尬的测试指出，所有的 `CountdownSong` 都被必须恰好有 99 节诗。幸运的是，从上下文中获得独立是很容易；只需修改 `CountdownSong` 以处理任何范围内的任何数量的诗即可。然后提取出 `99` 和 `0`，以隔离你想改变的内容。第一步是为这些数字代表的概念命名。例如，你可能会选择 `max` 和 `min`。通过创建如所示的属性来开始使用这些名称：



## 完成这些后，你可以更改 `CountdownSong` 在 `construction` 期间接受并保存这些参数，如下所示：

[Listing 9.30: 注入并设置最大值和最小值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-250/lib/Bottles.php#L5-L28)

```php
class CountdownSong {
  // ...
  public function __construct(string $verseTemplate = BottleVerse::class, int $max = 99, int $min = 0) {
    $this->verseTemplate = $verseTemplate;
    $this->max = $max;
    $this->min = $min;
  }
  // ...
}
```

现在 `song` 方法可以引用这些抽象名称，而不是下面第 11 行的具体值：

[Listing 9.31: 在 Song 中使用最大值和最小值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-260/lib/Bottles.php#L5-L28)

```php
class CountdownSong {
  protected $verseTemplate, $min, $max;

  public function __construct(string $verseTemplate = BottleVerse::class, int $max = 99, int $min = 0) {
    $this->verseTemplate = $verseTemplate;
    $this->max = $max;
    $this->min = $min;
  }

  public function song(): string {
    return $this->verses($this->max, $this->min);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return $this->verseTemplate::lyrics($number);
  }
}
```

因此，依赖关系反转了。`CountdownSong` 以前依赖于 `99` 和 `0` 的具体实现，现在它依赖于 `max` 和 `min` 的抽象。它曾经被其所属的上下文所束缚，现在它独立于该上下文了。矛盾的是，现在由于它知道的少了，它反而能做更多。

这完成了 `max` 和 `min` 的提取。在继续更新测试之前，关于这些代码有几点需要注意。

首先，`max` 和 `min` 在第 4 行被赋予了默认值，这些默认值看起来很像只在“99 Bottles”歌曲的上下文中才有意义的值。传递更通用的默认值会更好，但你还不能这样做，因为除非 `max` 为 `99`，否则 `test_the_whole_song` 将失败。目前只需意识到你希望这个默认值是独立于上下文的，并留意可以使其如此的机会。

接下来，注意该歌曲在两个地方接受了界定诗范围的数字对（第 4 行和第 14 行）。在其中一个地方，这对被命名为 `max` 和 `min`，在另一个地方则是 `upper` 和 `lower`。这是故意的。一整首歌有固定节数诗歌的想法体现在 `max` 和 `min` 中。这是关于歌曲的。相比之下，`verses` 方法可以产生请求范围内的诗的想法体现在 `upper` 和 `lower` 中。这是关于要产生的诗的子集。这是两个不同的概念，给它们不同的名称可以使代码更清晰。现在 `max` 和 `min` 已经存在，你可以使用它们来简化 `test_the_whole_song`。下面的行显示了一个较短但可能更有用的测试：

[Listing 9.32: 备用全量测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-270/test/CountdownTest.php#L11-35)

```php
class CountdownTest extends \PHPUnit\Framework\TestCase {
  // ...
  public function test_the_song() {
    $expected =
      "This is verse 47.\n" .
      "\n" .
      "This is verse 46.\n" .
      "\n" .
      "This is verse 45.\n" .
      "\n" .
      "This is verse 44.\n" .
      "\n" .
      "This is verse 43.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class, 47, 43))->song()
    );
  }

  public function test_the_song_original() {
    $expected = <<<SONG
99 bottles on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer.

// ...

No more bottles on the wall, more bottles of beer.
Go to the store and buy some more, 99 bottles of beer.

SONG;
    $this->assertEquals($expected, (new CountdownSong())->song());
  }
}
```

现在有了更好的测试，你就可以删除旧版本了。你几乎完成了 `CountdownTest`。剩下的任务是重命名 `test_the_whole_song` 以与其他保持一致。将其命名为 `test_song` 效果非常好，在这样做之后最终的 `CountdownTest` 看起来如下：

[Listing 9.33: 美好的测试套件](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownTest.php#L11-50)

```php
class CountdownTest extends \PHPUnit\Framework\TestCase {
  public function test_verse() {
    $expected =
      "This is verse 500.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(500)
    );
  }

  public function test_verses() {
    $expected =
      "This is verse 99.\n" .
      "\n" .
      "This is verse 98.\n" .
      "\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }

  public function test_song() {
    $expected =
      "This is verse 47.\n" .
      "\n" .
      "This is verse 46.\n" .
      "\n" .
      "This is verse 45.\n" .
      "\n" .
      "This is verse 44.\n" .
      "\n" .
      "This is verse 43.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class, 47, 43))->song()
    );
  }
}
```

测试一直始终关注于向想象中的读者传达代码的意图。这种对彻底沟通的承诺指导了测试位置的选择、命名方式，以及提供哪些协作者的选择。尽管之前的更改很有帮助且必要，但代码仍有进一步改进的空间。

最后这一节对代码进行了几项最终的改动，以增加更多信息和安全性，并减少潜在的困惑。将这一轮看作是在提交代码并离开之前对代码进行的最后一次检查。

### 9.4.1. 用信号丰富代码

所有当前的测试都共享一个相似的三阶段结构。每个测试：

1. 定义一个预期，
2. 执行某些代码，并且
3. 断言结果符合预期

这种模式被称为“安排-执行-断言”（Arrange-Act-Assert, AAA）。并没有规定测试必须以此格式化。显然，无论如何安排，它们都能正常工作。这种严谨的一致性不是为了测试本身，而是为了人类。

承诺使用一种通用的形状可以减轻未来读者的认知负担。当每个测试的结构都相同时，读者就不需要浪费时间去判断细微的差异是否重要。代码本身的形状就能传达出：“这里没什么奇怪的，啦啦啦，一切都很无聊且正常，请继续吧。”

选择以类似的方式安排测试是一种编程风格问题。你的团队应该就通用风格达成一致。缺乏这一点，每个人的代码将以无意义的方式相互区别，从而增加了阅读代码的成本。

适用于所有情况的模式有时对于极其简单的情况可能显得有些沉重。例如，`test_verse` 刻意在下面的第 3 行声明了 `expected` 变量，尽管它完全可以直接在第 6 行硬编码 `"This is verse 500.\n"`。

[Listing 9.34: 风格胜过实质内容](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```php
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_verse() {
    $expected =
      "This is verse 500.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(500)
    );
  }
  // ...
}
```

在上面的测试中，对遵循通用风格的承诺超过了缩短列表的愿望。遵循风格向读者传达了：这个测试并没有特别或不寻常，传达这一信息比减少这一行代码更有价值。

从定义上说，你代码的未来读者知道的比你现在知道的少。他们游离在浑浊的水中，撞上感知模糊的概念，寻找清晰度。代码的形状本身可以成为一盏明灯，富有意义。你总是在寻找那些能向这些不幸的读者发送信号的代码安排。

风格是信号的一种，但还有其他信号。例如，你可能想过为什么 `test_song` 为 `max` 和 `min` 选择了 `47` 和 `43`（第 16 行）。

[Listing 9.35: 用素数传递信号](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```php
class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  // ...
  public function test_song() {
    $expected =
      "This is verse 47.\n" .
      "\n" .
      "This is verse 46.\n" .
      "\n" .
      "This is verse 45.\n" .
      "\n" .
      "This is verse 44.\n" .
      "\n" .
      "This is verse 43.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(47)
    );
  }
}
```




测试一直始终关注于向想象中的读者传达代码的意图。这种对彻底沟通的承诺指导了测试位置的选择、命名方式，以及提供哪些协作者的选择。尽管之前的更改很有帮助且必要，但代码仍有进一步改进的空间。

最后这一节对代码进行了几项最终的改动，以增加更多信息和安全性，并减少潜在的困惑。将这一轮看作是在提交代码并离开之前对代码进行的最后一次检查。

### 9.4.1. 用信号丰富代码

所有当前的测试都共享一个相似的三阶段结构。每个测试：

1. 定义一个预期，
2. 执行某些代码，并且
3. 断言结果符合预期

这种模式被称为“安排-执行-断言”（AAA）。并没有规定测试必须以此格式化。显然，无论如何安排，它们都能正常工作。这种严谨的一致性不是为了测试本身，而是为了人类。

承诺使用一种通用的形状可以减轻未来读者的认知负担。当每个测试的结构都相同时，读者就不需要浪费时间去判断细微的差异是否重要。代码本身的形状就能传达出：“这里没什么奇怪的，啦啦啦，一切都很无聊且正常，请继续吧。”

选择以类似的方式安排测试是一种编程风格问题。你的团队应该就通用风格达成一致。缺乏这一点，每个人的代码将以无意义的方式相互区别，从而增加了阅读代码的成本。

适用于所有情况的模式有时对于极其简单的情况可能显得有些沉重。例如，`test_verse` 刻意在下面的第 3 行声明了 `$expected` 变量，尽管它完全可以直接在第 6 行硬编码 `"This is verse 500.\n"`。

[列表 9.34: 风格胜过实质内容](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_verse() {
 3     $expected =
 4       "This is verse 500.\n";
 5     $this->assertEquals(
 6       $expected,
 7       (new CountdownSong(VerseFake::class))->verse(500)
 8     );
 9   }
 10   // ...
 11 }
```

在上面的测试中，对遵循通用风格的承诺超过了缩短列表的愿望。遵循风格向读者传达了：这个测试并没有特别或不寻常，传达这一信息比减少这一行代码更有价值。

从定义上说，你代码的未来读者知道的比你现在知道的少。他们游离在浑浊的水中，撞上感知模糊的概念，寻找清晰度。代码的形状本身可以成为一盏明灯，富有意义。你总是在寻找那些向这些不幸的读者发送信号的代码安排。

风格是信号的一种，但还有其他信号。例如，你可能想过为什么 `test_song` 选择了 `47` 和 `43` 为 `max` 和 `min`（第 16 行）。

[列表 9.35: 用素数传递信号](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   // ...
 3   public function test_song() {
 4     $expected =
 5       "This is verse 47.\n" .
 6       "\n" .
 7       "This is verse 46.\n" .
 8       "\n" .
 9       "This is verse 45.\n" .
 10      "\n" .
 11      "This is verse 44.\n" .
 12      "\n" .
 13      "This is verse 43.\n";
 14    $this->assertEquals(
 15       $expected,
 16       (new CountdownSong(VerseFake::class))->verse(47)
 17     );
 18  }
 19 }
```



测试一直始终关注于向想象中的读者传达代码的意图。这种对彻底沟通的承诺指导了测试位置的选择、命名方式，以及提供哪些协作者的选择。尽管之前的更改很有帮助且必要，但代码仍有进一步改进的空间。

最后这一节对代码进行了几项最终的改动，以增加更多信息和安全性，并减少潜在的困惑。将这一轮看作是在你提交代码并离开之前对代码进行的最后一次检查。

### 9.4.1. 用信号丰富代码

所有当前的测试都共享一个相似的三阶段结构。每个测试：

1. 定义一个预期，
2. 执行某些代码，并且
3. 断言结果符合预期

这种模式被称为“安排-执行-断言”（AAA）。并没有规定测试必须以此格式化。显然，无论如何安排，它们都能正常工作。这种严谨的一致性不是为了测试本身，而是为了人类。

承诺使用一种通用的形状可以减轻未来读者的认知负担。当每个测试的结构都相同时，读者就不需要浪费时间去判断细微的差异是否重要。代码本身的形状就能传达出：“这里没什么奇怪的，啦啦啦，一切都很无聊且正常，请继续吧。”

选择以类似的方式安排测试是一种编程风格问题。你的团队应该就通用风格达成一致。缺乏这一点，每个人的代码将以无意义的方式相互区别，从而增加了阅读代码的成本。

适用于所有情况的模式有时对于极其简单的情况可能显得有些沉重。例如，`test_verse` 刻意在下面的第 3 行声明了 `expected` 变量，尽管它完全可以直接在第 6 行硬编码 `"This is verse 500.\n"`。

[列表 9.34: 风格胜过实质内容](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   public function test_verse() {
 3     $expected =
 4       "This is verse 500.\n";
 5     $this->assertEquals(
 6       $expected,
 7       (new CountdownSong(VerseFake::class))->verse(500)
 8     );
 9   }
 10   // ...
 11 }
```

在上面的测试中，对遵循通用风格的承诺超过了缩短列表的愿望。遵循风格向读者传达了：这个测试并没有特别或不寻常，传达这一信息比减少这一行代码更有价值。

从定义上说，你代码的未来读者知道的比你现在知道的少。他们游离在浑浊的水中，撞上感知模糊的概念，寻找清晰度。代码的形状本身可以成为一盏明灯，富有意义。你总是在寻找那些向这些不幸的读者发送信号的代码安排。

风格是信号的一种，但还有其他信号。例如，你可能想过为什么 `test_song` 选择了 `47` 和 `43` 为 `max` 和 `min`（第 16 行）。

[列表 9.35: 用素数传递信号](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-290/test/CountdownSongTest.php#L11-L50)

```
 1 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
 2   // ...
 3   public function test_song() {
 4     $expected =
 5       "This is verse 47.\n" .
 6       "\n" .
 7       "This is verse 46.\n" .
 8       "\n" .
 9       "This is verse 45.\n" .
 10      "\n" .
 11      "This is verse 44.\n" .
 12      "\n" .
 13      "This is verse 43.\n";
 14    $this->assertEquals(
 15       $expected,
 16       (new CountdownSong(VerseFake::class))->verse(47)
 17     );
 18  }
 19 }
```

上述说明，想要扮演 `CountdownSongVerse` 角色的类必须实现一个名为 `lyrics` 的公共静态函数，该函数接收一个 `int` 并返回一个 `string`。

既然接口已经定义，`BottleVerse` 和 `VerseFake` 就可以实现它。它们已经包含一个名称正确的静态函数，因此只需要在类定义中添加 `implements` 关键字即可。以下是 `BottleVerse` 中的更改（下方第 1 行）：

[Listing 9.37: BottleVerse 是一个 CountdownSongVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-292/lib/Bottles.php#L34-L52)

```
1 class BottleVerse implements CountdownSongVerse {
2   // ...
3   public static function lyrics(int $number): string {
4     return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
5   }
5   // ...
7 }
```

以下是 `VerseFake` 中的相同更改（同样在第 1 行）：

[Listing 9.38: VerseFake 是一个 CountdownSongVerse](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-340/test/CountdownSongTest.php#L5-L9)

```
1 class VerseFake implements CountdownSongVerse {
2   public static function lyrics(int $number): string {
3     return "This is verse {$number}.\n";
4   }
5 }
```

现在运行测试确认 `VerseFake` 正确地扮演了歌曲模板的角色。

良好的面向对象设计会导致多态的角色扮演对象。当你识别并定义角色时，通过在接口中体现它们，并利用 PHP 来保持执行者之间的同步。

### 9.4.3. 消除过时的上下文

本节的最后一个任务是再次检查代码，找到并移除过时的上下文。`CountdownSong` 保留了一些关于“99 Bottles”的误导性遗迹；现在是时候移除它们了。

考虑下面的代码：

[Listing 9.39: CountdownSong 默认值反映了过时的上下文](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-340/lib/Bottles.php#L5-L28)

```
 1 class CountdownSong {
 2   protected $verseTemplate, $min, $max;
 3 
 4   public function __construct(string $verseTemplate = BottleVerse::class, int $max = 99, int $min = 0) {
 5     $this->verseTemplate = $verseTemplate;
 6     $this->max = $max;
 7     $this->min = $min;
 8   }
 9   // ...
 10 }
```

在上面的第 4 行中，`$verseTemplate`、`$max` 和 `$min` 的默认值是 `CountdownSong` 源自“99 Bottles”上下文的产物。这些默认值给人一种旧上下文仍然重要的印象。事实并非如此，清楚这一点最好的方法就是修改这段代码。

你现在需要决定是否提供默认值，如果提供，使用什么值。`CountdownSong` 理论上可以为 `$max` 和 `$min` 提供默认值，但无法合理地推测应该使用哪种歌曲模板。

让外部者提供 `$verseTemplate` 与移除默认值一样简单，如下方的第 4 行所示：

[Listing 9.40: 移除歌曲模板默认值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-350/lib/Bottles.php#L5-L28)

```
 1 class CountdownSong {
 2   protected $verseTemplate, $min, $max;
 3 
 4   public function __construct(string $verseTemplate, int $max = 99, int $min = 0) {
 5     $this->verseTemplate = $verseTemplate;
 6     $this->max = $max;
 7     $this->min = $min;
 8   }
 9   // ...
 10 }
```

这在之前是无法实现的，因为旧测试期望 `CountdownSong` 将 `$verseTemplate` 设置为 `BottleVerse`。现在所有测试都提供了歌曲模板，它们在整个过渡过程中无缝工作。

这留下了 `$max` 和 `$min`。较小的数字 `$min` 感觉和 `$verseTemplate` 一样直接。歌曲可能倒数到 `0`；在 `CountdownSong` 中将 `$min` 默认设置为 `0` 是很容易辩护的。

`$max` 数字稍微复杂一点。可以认为，就像 `CountdownSong` 不知道你想要的歌曲模板一样，它也不知道你的歌曲包含多少节。`CountdownSong` 的用户可能总是需要提供这个值。尽管如此，`CountdownSong` 可能想设置一个默认值以发送信号。

将 `$max` 设置为一个巨大的数字标志着 `CountdownSong` 可以处理很长的歌曲。以下代码片段实现了这一点：

[Listing 9.41: 重置最大值](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-360/lib/Bottles.php#L8-L12)

```
1 public function __construct(string $verseTemplate, int $max = 999999, int $min = 0) {
2   // ...
3 }
```

完成最后一次更改后，浏览完整的代码列表并庆贺你的成就：

[Listing 9.42: 最终代码](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-360/lib/Bottles.php#L5-L136)



```php
1 class CountdownSong {
  protected $verseTemplate, $min, $max;

  public function __construct(string $verseTemplate, int $max = 999999, int $min = 0) {
    $this->verseTemplate = $verseTemplate;
    $this->max = $max;
    $this->min = $min;
  }

  public function song(): string {
    return $this->verses($this->max, $this->min);
  }

  public function verses(int $upper, int $lower): string {
    return implode(
      "\n",
      array_map([$this, 'verse'], range($upper, $lower))
    );
  }

  public function verse(int $number): string {
    return $this->verseTemplate::lyrics($number);
  }
}

interface CountdownSongVerse {
  public static function lyrics(int $number): string;
}

class BottleVerse implements CountdownSongVerse {
  protected $bottleNumber;

  public static function lyrics(int $number): string {
    return (new BottleVerse(BottleNumber::for($number)))->_lyrics();
  }

  public function __construct(object $bottleNumber) {
    $this->bottleNumber = $bottleNumber;
  }

  private function _lyrics(): string {
    return
      ucfirst("{$this->bottleNumber} of beer on the wall, ") .
      "{$this->bottleNumber} of beer.\n" .
      "{$this->bottleNumber->action()}, " .
      "{$this->bottleNumber->successor()} of beer on the wall.\n";
  }
}

class BottleNumber {
  protected $number;

  public static function for(int $number): BottleNumber {
    switch ($number) {
    case 0:
        $className = BottleNumber0::class;
        break;
    case 1:
        $className = BottleNumber1::class;
        break;
    case 6:
        $className = BottleNumber6::class;
        break;
    default:
        $className = BottleNumber::class;
        break;
    }
    return new $className($number);
  }

  public function __construct(int $number) {
    $this->number = $number;
  }

  public function __toString(): string {
    return $this->quantity() . " " . $this->container();
  }

  public function quantity(): string {
    return (string)$this->number;
  }

  public function container(): string {
    return "bottles";
  }

  public function action(): string {
    return "Take " . $this->pronoun() . " down and pass it around";
  }

  public function pronoun(): string {
    return "one";
  }

  public function successor(): object {
    return BottleNumber::for($this->number - 1);
  }
}

class BottleNumber0 extends BottleNumber {
  public function quantity(): string {
    return "no more";
  }

  public function action(): string {
    return "Go to the store and buy some more";
  }

  public function successor(): object {
    return BottleNumber::for(99);
  }
}

class BottleNumber1 extends BottleNumber {
  public function container(): string {
    return "bottle";
  }

  public function pronoun(): string {
    return "it";
  }
}

class BottleNumber6 extends BottleNumber {
  public function quantity(): string {
    return "1";
  }

  public function container(): string {
    return "six-pack";
  }
}
```

[列表 9.43: Final 测试](https://github.com/sandimetz/99bottles_php/blob/2.1.1-c9-revisit-tests-360/test/CountdownSongTest.php#L5-L50)

```php
1 class VerseFake implements CountdownSongVerse {
  public static function lyrics(int $number): string {
    return "This is verse {$number}.\n";
  }
}

2 class CountdownSongTest extends \PHPUnit\Framework\TestCase {
  public function test_verse() {
    $expected =
      "This is verse 500.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verse(500)
    );
  }

  public function test_verses() {
    $expected =
      "This is verse 99.\n" .
      "This is verse 98.\n" .
      "This is verse 97.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(99, 97)
    );
  }

  public function test_song() {
    $expected =
      "This is verse 47.\n" .
      "This is verse 46.\n" .
      "This is verse 45.\n" .
      "This is verse 44.\n";
    $this->assertEquals(
      $expected,
      (new CountdownSong(VerseFake::class))->verses(47, 43)
    );
  }
}

3 BottleVerseTest extends \PHPUnit\Framework\TestCase {
  public function test_verse_rule_upper_bound() {
    $expected =
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(99)
    );
  }

  public function test_verse_rule_lower_bound() {
    $expected =
      "3 bottles of beer on the wall, " .
      "3 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "2 bottles of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(3)
    );
  }

  public function test_verse_7() {
    $expected =
      "7 bottles of beer on the wall, " .
      "7 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "6-pack of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(7)
    );
  }

  public function test_verse_6() {
    $expected =
      "6-pack of beer on the wall, " .
      "6-pack of beer.\n" .
      "Take one down and pass it around, " .
      "5 bottles of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(6)
    );
  }

  public function test_verse_2() {
    $expected =
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(2)
    );
  }

  public function test_verse_1() {
    $expected =
      "1 bottle of beer on the wall, " .
      "1 bottle of beer.\n" .
      "Take it down and pass it around, " .
      "no more bottles of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(1)
    );
  }

  public function test_verse_0() {
    $expected =
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";
    $this->assertEquals(
      $expected,
      BottleVerse::lyrics(0)
    );
  }
}
```

在编码的热热中，人们可能会想要跳过最后这一轮清理。但请不要错过最后的擦拭，以让代码闪放异彩。

## 9.5. 总结

测试有助于防止代码中的错误，但如果仅仅简单地描述它们是不公平的；它们提供的价值远不止。良好的面向对象设计构建在小型、可交换的对象之上，这些对象通过抽象进行交互。每个单独对象的行为通常显而易见，但整体运作并非如此。测试填补了这一缺口。

面向对象的应用程序依赖于消息传递。消息的核心优势在于它们增加了间接性（`indirection`）。消息允许发送者请求一种抽象，并确信接收者将使用适当的具体实现来实现请求。发送者负责知道自己想要什么，接收者负责知道如何实现。通过这种方式将意图与实现分离，允许你可以在不修改现有代码的情况下引入新的变体；只需创建一个新对象，用不同的实现来响应原始消息即可。

如果设计了以下特性，面向对象的代码就可以与新的、意外的变体进行交互，而无需更改：

1. **变体是隔离的。**

   它们通常被隔离在某种对象中，通常是一个新类。

2. **变体选择是隔离的。**

   选择发生在工厂中，工厂可能只是简单的选择某个类的隔离条件判断。

3. **消息发送者和接收者是松耦合的。**

   这通常通过依赖注入来实现。

4. **变体是可以交换的。**

   消息发送者将注入的对象视为相同角色的等执行者。

最初，这种对抽象和间接性的依赖增加了代码的复杂性。而面向对象所的回报是降低未来的更改成本。高度具体、紧耦合的代码将抵制明天的变化。而依赖于松耦合抽象的代码将鼓励变化。

由于测试需要执行代码，它们能够提供关于设计不足的早期且直接的信息，并为精炼提供动力和灵感。当测试难以编写、需要大量设置或无法讲述一个令人满意的故事时，说明出了问题。听从这种信号。现在解决问题比以后解决更便宜，而且会改进你的代码，明确你的测试，并让你的工作变得快乐。

## 后记

恭喜你，你做到了。你现在并非处于万物的终点，至少也处于*这本书*的终点。完成这本书是一项成就，在继续之前，你值得花一点时间沉浸在成功的中中。无论在你开始之前心态或经验水平如何，完成后，你已经变得不同了。

这本书有两个主要目标。第一个关于*过程*，第二个关于*视角*。

第一个目标是提供具体的、可重复的技术，你可以利用这些技术来改进你自己的应用程序。这些技术不仅通过代码进行了说明，还通过记录每个决策背后的逻辑进行了说明——在处理棘手问题时没有任何含糊其辞。这些详细、具体的解释最终汇成了关于如何编写代码的许多通用思想，或*准则*（`canons`）。

追求简单。不要过早抽象。关注气味。关注差异。小步跑步。遵循*群集规则*（`Flocking Rules`）。在测试通过的情况下重构。先解决简单的问题。横向工作。寻找稳定的着陆点。保持纪律。不要追逐花哨的东西。

此外，处理新需求时，首先通过重构现有代码使其对它们开放，然后编写新代码来满足它们。实现开放性通常是更具挑战性的任务，但如果你有作为后盾的测试，就可以在绝对的安全中寻求它。

你可能需要更好的测试。如果是这样，编写它们将为你节省资金。

准则是指导编程*过程*的实用规则。遵循它们将减轻你的压力，加快你的工作并改进你的代码。如果你只承诺遵循这些规则，那么你的阅读时间就没白虚费。

## 附录 A：初始练习

### 获取练习

书中的代码在 GitHub 上。获取练习最简单的方法是克隆仓库并检出正确的分支：

```
git clone --depth=1 --branch=2.1-appendix-exercise-10 https://github.com/sandimetz/99bottles.git
```

练习的目录结构应该如下：

```
├── lib
│   └── Bottles.php
└── test
    └── BottlesTest.php
```



如果你没有安装 git，请创建所需的目录结构，然后将 [GitHub 原始文件](https://raw.githubusercontent.com/sandimetz/99bottles_php/2.1-appendix-exercise-10/test/BottlesTest.php) 的内容复制并粘贴到 `BottlesTest.php` 中。

最后，如果你没有连接网络，可以在下面的测试套件部分找到测试套件的完整列表。

## 执行练习

要运行测试套件，使用 `composer install` 安装依赖，然后调用 PHPUnit：

```
./vendor/bin/phpunit test
```

测试套件包含一个失败的测试和许多跳过的测试。你的目标是编写通过所有测试的代码。遵循以下规程：

* 运行测试并检查失败原因
* 只编写足够通过失败测试的代码
* 取消跳过下一个测试（这模拟你自己编写它）

重复上述步骤，直到没有测试被跳过，且你已经编写了通过每一个测试的代码。

花 30 分钟处理这项任务。大多数人无法在 30 分钟内完成，但为了以后对比，记录你的进展程度是有用的。即使你无法强迫自己在那个点停止，也请在 30 分钟时休息并保存代码。

## 测试套件

列表 A.1: 练习



```php
<?php

require __DIR__ . "/../lib/Bottles.php";

class BottlesTest extends \PHPUnit\Framework\TestCase {
  public function test_the_first_verse() {
    $expected =
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verse(99));
  }

  public function test_another_verse() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "3 bottles of beer on the wall, " .
      "3 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "2 bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verse(3));
  }

  public function test_verse_2() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verse(2));
  }

  public function test_verse_1() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "1 bottle of beer on the wall, " .
      "1 bottle of beer.\n" .
      "Take it down and pass it around, " .
      "no more bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verse(1));
  }

  public function test_verse_0() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verse(0));
  }

  public function test_a_couple_verses() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "99 bottles of beer on the wall, " .
      "99 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "98 bottles of beer on the wall.\n" .
      "\n" .
      "98 bottles of beer on the wall, " .
      "98 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "97 bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verses(99, 98));
  }

  public function test_a_few_verses() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected =
      "2 bottles of beer on the wall, " .
      "2 bottles of beer.\n" .
      "Take one down and pass it around, " .
      "1 bottle of beer on the wall.\n" .
      "\n" .
      "1 bottle of beer on the wall, " .
      "1 bottle of beer.\n" .
      "Take it down and pass it around, " .
      "no more bottles of beer on the wall.\n" .
      "\n" .
      "No more bottles of beer on the wall, " .
      "no more bottles of beer.\n" .
      "Go to the store and buy some more, " .
      "99 bottles of beer on the wall.\n";

    $this->assertEquals($expected, (new Bottles())->verses(2, 0));
  }

  public function test_the_whole_song() {
    $this->markTestSkipped('准备好让测试通过时删除');
    $expected = <<< SONG
99 bottles of beer on the wall, 99 bottles of beer.
Take one down and pass it around, 98 bottles of beer on the wall.

98 bottles of beer on the wall, 98 bottles of beer.
Take one down and pass it around, 97 bottles of beer on the wall.

97 bottles of beer on the wall, 97 bottles of beer.
Take one down and pass it around, 96 bottles of beer on the wall.

96 bottles of beer on the wall, 96 bottles of beer.
Take one down and pass it around, 95 bottles of beer on the wall.

95 bottles of beer on the wall, 95 bottles of beer.
Take one down and pass it around, 94 bottles of beer on the wall.

94 bottles of beer on the wall, 94 bottles of beer.
Take one down and pass it around, 93 bottles of beer on the wall.

93 bottles of beer on the wall, 93 bottles of beer.
Take one down and pass it around, 92 bottles of beer on the wall.

92 bottles of beer on the wall, 92 bottles of beer.
Take one down and pass it around, 91 bottles of beer on the wall.

91 bottles of beer on the wall, 91 bottles of beer.
Take one down and pass it around, 90 bottles of beer on the wall.

90 bottles of beer on the wall, 90 bottles of beer.
Take one down and pass it around, 89 bottles of beer on the wall.

89 bottles of beer on the wall, 89 bottles of beer.
Take one down and pass it around, 88 bottles of beer on the wall.

88 bottles of beer on the wall, 88 bottles of beer.
Take one down and pass it around, 87 bottles of beer on the wall.

87 bottles of beer on the wall, 87 bottles of beer.
Take one down and pass it around, 86 bottles of beer on the wall.

86 bottles of beer on the wall, 86 bottles of beer.
Take one down and pass it around, 85 bottles of beer on the wall.

85 bottles of beer on the wall, 85 bottles of beer.
Take one down and pass it around, 84 bottles of beer on the wall.

84 bottles of beer on the wall, 84 bottles of beer.
Take one down and pass it around, 83 bottles of beer on the wall.

83 bottles of beer on the wall, 83 bottles of beer.
Take one down and pass it around, 82 bottles of beer on the wall.

82 bottles of beer on the wall, 82 bottles of beer.
Take one down and pass it around, 81 bottles of beer on the wall.

81 bottles of beer on the wall, 81 bottles of beer.
Take one down and pass it around, 80 bottles of beer on the wall.

80 bottles of beer on the wall, 80 bottles of beer.
Take one down and pass it around, 79 bottles of beer on the wall.

79 bottles of beer on the wall, 79 bottles of beer.
Take one down and pass it around, 78 bottles of beer on the wall.

78 bottles of beer on the wall, 78 bottles of beer.
Take one down and pass it around, 77 bottles of beer on the wall.

77 bottles of beer on the wall, 77 bottles of beer.
Take one down and pass it around, 76 bottles of beer on the wall.

76 bottles of beer on the wall, 76 bottles of beer.
Take one down and pass it around, 75 bottles of beer on the wall.

75 bottles of beer on the wall, 75 bottles of beer.
Take one down and pass it around, 74 bottles of beer on the wall.

74 bottles of beer on the wall, 74 bottles of beer.
Take one down and pass it around, 73 bottles of beer on the wall.

73 bottles of beer on the wall, 73 bottles of beer.
Take one down and pass it around, 72 bottles of beer on the wall.

72 bottles of beer on the wall, 72 bottles of beer.
Take one down and pass it around, 71 bottles of beer on the wall.

71 bottles of beer on the wall, 71 bottles of beer.
Take one down and pass it around, 70 bottles of beer on the wall.

70 bottles of beer on the wall, 70 bottles of beer.
Take one down and pass it around, 69 bottles of beer on the wall.

69 bottles of beer on the wall, 69 bottles of beer.
Take one down and pass it around, 68 bottles of beer on the wall.

68 bottles of beer on the wall, 68 bottles of beer.
Take one down and pass it around, 67 bottles of beer on the wall.

67 bottles of beer on the wall, 67 bottles of beer.
Take one down and pass it around, 66 bottles of beer on the wall.

66 bottles of beer on the wall, 66 bottles of beer.
Take one down and pass it around, 65 bottles of beer on the wall.

65 bottles of beer on the wall, 65 bottles of beer.
Take one down and pass it around, 64 bottles of beer on the wall.

64 bottles of beer on the wall, 64 bottles of beer.
Take one down and pass it around, 63 bottles of beer on the wall.

63 bottles of beer on the wall, 63 bottles of beer.
Take one down and pass it around, 62 bottles of beer on the wall.

62 bottles of beer on the wall, 62 bottles of beer.
Take one down and pass it around, 61 bottles of beer on the wall.

61 bottles of beer on the wall, 61 bottles of beer.
Take one down and pass it around, 60 bottles of beer on the wall.

60 bottles of beer on the wall, 60 bottles of beer.
Take one down and pass it around, 59 bottles of beer on the wall.

59 bottles of beer on the wall, 59 bottles of beer.
Take one down and pass it around, 58 bottles of beer on the wall.

58 bottles of beer on the wall, 58 bottles of beer.
Take one down and pass it around, 57 bottles of beer on the wall.

57 bottles of beer on the wall, 57 bottles of beer.
Take one down and pass it around, 56 bottles of beer on the wall.

56 bottles of beer on the wall, 56 bottles of beer.
Take one down and pass it around, 55 bottles of beer on the wall.

55 bottles of beer on the wall, 55 bottles of beer.
Take one down and pass it around, 54 bottles of beer on the wall.

54 bottles of beer on the wall, 54 bottles of beer.
Take one down and pass it around, 53 bottles of beer on the wall.

53 bottles of beer on the wall, 53 bottles of beer.
Take one down and pass it around, 52 bottles of beer on the wall.

52 bottles of beer on the wall, 52 bottles of beer.
Take one down and pass it around, 51 bottles of beer on the wall.

51 bottles of beer on the wall, 51 bottles of beer.
Take one down and pass it around, 50 bottles of beer on the wall.

50 bottles of beer on the wall, 50 bottles of beer.
Take one down and pass it around, 49 bottles of beer on the wall.

49 bottles of beer on the wall, 49 bottles of beer.
Take one down and pass it around, 48 bottles of beer on the wall.

48 bottles of beer on the wall, 48 bottles of beer.
Take one down and pass it around, 47 bottles of beer on the wall.

47 bottles of beer on the wall, 47 bottles of beer.
Take one down and pass it around, 46 bottles of beer on the wall.

46 bottles of beer on the wall, 46 bottles of beer.
Take one down and pass it around, 45 bottles of beer on the wall.

45 bottles of beer on the wall, 45 bottles of beer.
Take one down and pass it around, 44 bottles of beer on the wall.

44 bottles of beer on the wall, 44 bottles of beer.
Take one down and pass it around, 43 bottles of beer on the wall.

43 bottles of beer on the wall, 43 bottles of beer.
Take one down and pass it around, 42 bottles of beer on the wall.

42 bottles of beer on the wall, 42 bottles of beer.
Take one down and pass it around, 41 bottles of beer on the wall.

41 bottles of beer on the wall, 41 bottles of beer.
Take one down and pass it around, 40 bottles of beer on the wall.

40 bottles of beer on the wall, 40 bottles of beer.
Take one down and pass it around, 39 bottles of beer on the wall.

39 bottles of beer on the wall, 39 bottles of beer.
Take one down and pass it around, 38 bottles of beer on the wall.

38 bottles of beer on the wall, 38 bottles of beer.
Take one down and pass it around, 37 bottles of beer on the wall.

37 bottles of beer on the wall, 37 bottles of beer.
Take one down and pass it around, 36 bottles of beer on the wall.

36 bottles of beer on the wall, 36 bottles of beer.
Take one down and pass it around, 35 bottles of beer on the wall.

35 bottles of beer on the wall, 35 bottles of beer.
Take one down and pass it around, 34 bottles of beer on the wall.

34 bottles of beer on the wall, 34 bottles of beer.
Take one down and pass it around, 33 bottles of beer on the wall.

33 bottles of beer on the wall, 33 bottles of beer.
Take one down and pass it around, 32 bottles of beer on the wall.

32 bottles of beer on the wall, 32 bottles of beer.
Take one down and pass it around, 31 bottles of beer on the wall.

31 bottles of beer on the wall, 31 bottles of beer.
Take one down and pass it around, 30 bottles of beer on the wall.

30 bottles of beer on the wall, 30 bottles of beer.
Take one down and pass it around, 29 bottles of beer on the wall.

29 bottles of beer on the wall, 29 bottles of beer.
Take one down and pass it around, 28 bottles of beer on the wall.

28 bottles of beer on the wall, 28 bottles of beer.
Take one down and pass it around, 27 bottles of beer on the wall.

27 bottles of beer on the wall, 27 bottles of beer.
Take one down and pass it around, 26 bottles of beer on the wall.

26 bottles of beer on the wall, 26 bottles of beer.
Take one down and pass it around, 25 bottles of beer on the wall.

25 bottles of beer on the wall, 25 bottles of beer.
Take one down and pass it around, 24 bottles of beer on the wall.

24 bottles of beer on the wall, 24 bottles of beer.
Take one down and pass it around, 23 bottles of beer on the wall.

23 bottles of beer on the wall, 23 bottles of beer.
Take one down and pass it around, 22 bottles of beer on the wall.

22 bottles of beer on the wall, 22 bottles of beer.
Take one down and pass it around, 21 bottles of beer on the wall.

21 bottles of beer on the wall, 21 bottles of beer.
Take one down and pass it around, 20 bottles of beer on the wall.

20 bottles of beer on the wall, 20 bottles of beer.
Take one down and pass it around, 19 bottles of beer on the wall.

19 bottles of beer on the wall, 19 bottles of beer.
Take one down and pass it around, 18 bottles of beer on the wall.

18 bottles of beer on the wall, 18 bottles of beer.
Take one down and pass it around, 17 bottles of beer on the wall.

17 bottles of beer on the wall, 17 bottles of beer.
Take one down and pass it around, 16 bottles of beer on the wall.

16 bottles of beer on the wall, 16 bottles of beer.
Take one down and pass it around, 15 bottles of beer on the wall.

15 bottles of beer on the wall, 15 bottles of beer.
Take one down and pass it around, 14 bottles of beer on the wall.

14 bottles of beer on the wall, 14 bottles of beer.
Take one down and pass it around, 13 bottles of beer on the wall.

13 bottles of beer on the wall, 13 bottles of beer.
Take one down and pass it around, 12 bottles of beer on the wall.

12 bottles of beer on the wall, 12 bottles of beer.
Take one down and pass it around, 11 bottles of beer on the wall.

11 bottles of beer on the wall, 11 bottles of beer.
Take one down and pass it around, 10 bottles of beer on the wall.

10 bottles of beer on the wall, 10 bottles of beer.
Take one down and pass it around, 9 bottles of beer on the wall.

9 bottles of beer on the wall, 9 bottles of beer.
Take one down and pass it around, 8 bottles of beer on the wall.

8 bottles of beer on the wall, 8 bottles of beer.
Take one down and pass it around, 7 bottles of beer on the wall.

7 bottles of beer on the wall, 7 bottles of beer.
Take one down and pass it around, 6 bottles of beer on the wall.

6 bottles of beer on the wall, 6 bottles of beer.
Take one down and pass it around, 5 bottles of beer on the wall.

5 bottles of beer on the wall, 5 bottles of beer.
Take one down and pass it around, 4 bottles of beer on the wall.

4 bottles of beer on the wall, 4 bottles of beer.
Take one down and pass it around, 3 bottles of beer on the wall.

3 bottles of beer on the wall, 3 bottles of beer.
Take one down and pass it around, 2 bottles of beer on the wall.

2 bottles of beer on the wall, 2 bottles of beer.
Take one down and pass it around, 1 bottle of beer on the wall.

1 bottle of beer on the wall, 1 bottle of beer.
Take it down and pass it around, no more bottles of beer on the wall.

No more bottles of beer on the wall, no more bottles of beer.
Go to the store and buy some more, 99 bottles of beer on the wall.
SONG;
    $this->assertEquals($expected, (new Bottles())->song());
  }
}
```



## 参考文献

Abelson, Harold, and Sussman, Gerald, with Sussman Julie. [计算机程序的结构与解释，第二版](https://mitpress.mit.edu/books/structure-and-interpretation-computer-programs-second-edition)。 马萨诸塞州，剑桥：麻理工出版社，1996。

Beck, Kent. [实例引导测试驱动开发](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530/) 波士顿：Addison-Wesley，2002。

Beck, Kent. [“不要交叉横梁：避免水平与垂直重构之间的干扰”](https://www.facebook.com/notes/kent-beck/dont-cross-the-beams-avoiding-interference-between-horizontal-and-vertical-refac/260531380646400/) [https://www.facebook.com/kentlbeck/notes]。 2011 年 9 月 15 日。Web。2017 年 2 月 26 日。

Fowler, Martin, and Kent Beck. [重构：改进现有代码的设计](https://www.amazon.com/Refactoring-Improving-Design-Existing-Code/dp/0201485672/) 波士顿：Addison-Wesley，1999。

Fowler, Martin, with Beck, Kent. [重构：改进现有代码的设计，第二版](https://martinfowler.com/books/refactoring.html)。 波士顿：Addison-Wesley，2018。

Gamma, Erich, Richard Helm, Ralph Johnson, and John Vissides. [设计模式：可重用面向对象程序的要素](https://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/) 波士顿：Addison-Wesley，1994。

Kerievsky, Joshua. [重构模式](https://www.amazon.com/Refactoring-Patterns-Joshua-Kerievsky/dp/0321213351/) 波士顿：Addison-Wesley，2004。

Knuth, Donald. ["歌曲的复杂性。”](https://dl.acm.org/citation.cfm?id=358042) ACM 学报，第 27 卷第 4 期。计算机机器协会 (ACM)。1984 年 4 月。Web。2019 年 2 月 15 日。

Lieberherr, K., Holland, I., Riel, A. [面向对象编程：客观的风格感](https://www2.ccs.neu.edu/research/demeter/papers/law-of-demeter/oopsla88-law-of-demeter.pdf)。 OOPSLA '88 论文集。1988 年 9 月。Web。2019 年 2 月 15 日。

Meszaros, Gerard. [xUnit 测试模式](https://www.amazon.com/xUnit-Test-Patterns-Refactoring-Code/dp/0131495054)。 波士顿：Addison-Wesley，2007。

# 致谢

### Sandi Metz

这本书代表了关于面向对象编程和设计的无数讨论的结晶。正如每位程序员所知，这些对话并不是对所有人开放的。因此，我深感谢所有慷慨且热情地参与关于这些想法深度辩论的人。

我衷心感谢 Jim Gay、Avdi Grimm、Sara Mei、Katrina Owen、TJ Stankus 和 Tom Stuart，他们都帮助教授了 `POOD` 课程，这本书正起源于此。他们深厚的知识和温和的反对挑战了我的确定性并完善了我的思想。他们的影响贯穿全书。

我对所有上过 `POOD` 课程的人负有特殊的恩债。没有什么比尝试解释某事更能让你显易地发现自己其实并不理解它。正因为学生们坚持要求解释必须合乎逻辑，书中的解释才大大改进。我感激他们的执着。

Julia Trimmer 的编辑天赋在书中随处可见。这本书是对她对可读性不移承诺的致敬，也是她决定教我“which”和“that”用法区别的决心。我担心她只成功了前者，所以我心感激不尽。

### Katrina Owen

学习重构既有趣又令人困惑。对我来说，这可能比我的同事们更要费力。当这本书的第一版出版时，我们能够更快地涵盖 `POOD` 课程中的材料，利用腾出的时间，我们对问题进行了额外的需求实验。这些需求最终变成了你现在正在阅读的这本书第二版的新内容。

### TJ Stankus

2005 年，我发现自己坐在一个来自庞大大学系统不同部门的开发人员的会议室里。小组中有一个名叫 Sandi 的女性，我发现每当她说话时，我都会点头表示赞同。我们在 2006 年的第一次 `RailsConf` 上相遇了。从那时起，我与 Sandi 良好的合作关系和友谊是我职业生涯中最收获的方面之一。

[1]. 源自约瑟夫·赫勒的小说，“第 22 条法则](http://en.wikipedia.org/wiki/Catch-22_\(logic\))是指一种由于矛盾规则而无法逃脱的悖论处境。[2]。 根据[剑桥词典](https://dictionary.cambridge.org/us/dictionary/english/at-one-this-etc-remove)，它是指“被一段时间的时间或其他事件隔开”。[3]。对于不熟悉这个童话的人来说，这指的是[金发姑娘和三只熊](http://en.wikisource.org/wiki/The_Story_of_the_Three_Bears_\(Brooke\))中小熊（Little Bear）拥有的所有物品。[4]。 这句引言在历史上被认为源于马克·吐威恩，但现在被广泛归于[查尔斯·杜德利·华纳](http://en.wikipedia.org/wiki/Charles_Dudley_Warner)。吐威恩和华纳是邻居，前者显然是从后者那里听说的。[5]。 分支计数包括所有以括号结尾的内容、所有标准库调用，但不包括强制转换（coersion）。[6]。 ABC 分是根据[wikipedia](https://en.wikipedia.org/wiki/ABC_Software_Metric)定义的向量`<A,B,C>` 的模值。[7]。 [红鱱鱼](https://en.wikipedia.org/wiki/Red_herring)是指误导或分散人们对相关或重要问题注意力的事物。[8]。 毛衣，或称[苦行衣](https://en.wikipedia.org/wiki/Cilice)，是一种由动物毛发制成的内衣，通过穿着引起不适感作为忏悔或赎罪的标志。[9]。 [机会成本](https://en.wikipedia.org/wiki/Opportunity_cost)是指“未获得与最佳替代方案相关的收益而付出的‘成本’”。[10]。 参见肯特·贝克的[不要跨越光束：避免水平重构与垂直重构之间的干扰](https://www.facebook.com/notes/kent-beck/dont-cross-the-beams-avoiding-interference-between-horizontal-and-vertical-refac/260531380646400/)。[11]。 感谢[Avdi·格里姆](http://devblog.avdi.org/about/)的建议，在虚拟电子表格中使用行和列来帮助为底层概念命名。[12]。 感谢[汤姆·斯图特](https://codon.com/about)的建议，当你挣扎于为一个只有几个示例的概念命名时，想象其他可能也属于同一类别的具体事物会有帮助。[13]。 “你永远永远不会比你现在知道的更少”是肯特·贝克的一句名言。[14]。 蜘蛛感应是漫威漫画超级英雄[蜘蛛侠](https://en.wikipedia.org/wiki/Spider-Man%27s_powers_and_equipment) 颅骨基部的一种刺痛感，能警示他注意危险。[15]。 引自钦定本版圣经[哥林多后书 13:12](https://en.wikipedia.org/wiki/Corinthians_13) 的引言。[16]。 [梅丽·韦斯特词典定义`bang`](https://www.merriam-webster.com/dictionary/bang)为“完全正确”。）[17]。 [一团乱](https://www.phrases.org/meanings/kettle-of-fish)是指一种混乱或尴尬的境地。[18]。 [伪代码](https://en.wikipedia.org/wiki/Pseudocode) 是对计算机程序的非正式高层描述。[19]。 [转发](https://en.wikipedia.org/wiki/Forwarding_(object-oriented)) 是一种面向对象的技术，通过将消息指向另一个对象。[20]。 [委托](https://en.wikipedia.org/wiki/Delegation_(object-oriented)) 类似于[转发](https://en.wikipedia.org/wiki/Forwarding_(object-oriented))，但在接收对象中 `self` 指的是原始发送者，而不是当前对象。[21]。 [为什么 Ruby 方法难以重构](https://codeclimate.com/blog/why-ruby-methods-resist-refactoring/)来自[Code Climate 博客](https://codeclimate.com/blog/)。[22]。 [依赖图](https://en.wikipedia.org/wiki/Dependency_graph) 中的叶节点是终点。其他对象依赖它们，但它们不依赖任何对象。因此，它们通常比平均简单，且代表远离领域核心的概念。[23]。 设计模式的概念由建筑师[克里斯托弗·亚历山大](https://en.wikipedia.org/wiki/Christopher_Alexander) 提出。“四人帮”在其基性著作[设计模式：可重用面向对象的元素](https://en.wikipedia.org/wiki/Design_Patterns)中将其应用于软件。[24]。 [装饰器模式](https://en.wikipedia.org/wiki/Decorator_pattern) 允许动态地为单个对象添加行为，而不影响同一类的其他对象的行为。[25]。 [马丁·福勒对 xUnitTest Patterns 的介绍](https://martinfowler.com/books/meszaros.html) 比官方书籍简介](https://www.amazon.com/gp/product/0131495054) 更好地解释了为什么要读这本书。[26]。 Meszaros 关于[Mock、Fake、Stub](http://xunitpatterns.com/Mocks,%20Fakes,%20Stubs%20and%20Dummies.html) 部分的任何早期版本可以在他的[xUnitPatterns 网站](http://xunitpatterns.com/index.html) 上找到。[27]。 [Arrange Act Assert](https://wiki.c2.com/?ArrangeActAssert) 是一种用于单元测试代码安排的模式。它建议将测试分为三个部分：1) Arrange → 输入和先置条件，2) Act → 操作要测试的对象或方法，3) Assert → 断言获取的结果是否符合预期。[28]。 我们依然想念你，[Jim](https://en.wikipedia.org/wiki/Jim_Weirich)。
