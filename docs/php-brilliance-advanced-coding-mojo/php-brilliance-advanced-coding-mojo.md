
# PHP 高级指南：高级编码实战

![](img/d1c46c42bbfc0403b6b413d27d7d9213_0_0.png)

# 推特这本书！

请通过在 Twitter 上分享这本书来帮助 Thunder Raven-Stoker 尽忙！

此书建议使用的标签是 `#phpbrilliance`。

点击此链接在 Twitter 上搜索该标签，即可查看其他人对这本书的评价：

https://twitter.com/search?q=#phpbrilliance

我想将这本书献给我已故慈爱的父亲，他是一位传统意义上的工程师。他也很喜欢用这种想法来取我的玩笑，说：“程序员什么都不做！他们整天只会按按钮而已。”

爸爸，这本是送给你的，包含了所有避不开的“按按钮”。

- 接下来 ................................................................................................... 346

# 前言部分

## 前言

感谢拿起这本书。我们的旅程从这里开始，只有你和我。我们将穿过章节和段落，沿着一条艰难的道路。有人曾尝试过，但遗憾未能到达终点。但你与他们有所不同之处。我不确定具体是什么，但一旦我们共同开启这段旅程，我确信能够指出它。

让我们开始。

## 本书的读者群体

简而言之，我的目标是那些渴望发光的优秀开发者，让他们培养近乎超自然的预见和避免错误场景的能力，变得卓越。

这并不是一本 PHP 入门指南，也不是为中级开发者编写的。我的写作目标受众主要是处于高级水平的开发者，尽管我承认“高级开发者”这个词对不同的人和不同的组织意味着完全不同。

## 为什么我要写这本书？

这是一个非常好的问题，而且伴随着许多答案。顺便说，这并不是在推托，在我接受这个可能的项目时，过去以及现在都有几个动机。我将在下面列出它们，但请记住顺序是随机的——每个动机的权重与其他基本相同。

在前一节中，关于我的第一个动机有一个巨大的线索。到底什么是“高级开发者”呢？这个词的定义非常灵活，而且在很大程度上具有主观性。A 公司的高级开发者可能仅仅通过工龄获得了职级，而 B 公司的高级开发者则是通过对语言表现出证明性的能力获得的。尽管如此，B 公司的高级开发者在能力上可能仅与 C 公司的中级开发者相当，因为 C 公司有一位极其厉害的 CTO 领导技术团队。无论个人公司对其团队适用的职级规模如何，在英国，招聘人员对申请高级职位的人员标准确实较低。曾几何时，你只需要在简历/简历上写上 `MVC` 和 `Zend`，就能作为高级开发人员职位的候选人被提交。

现在，别误会我，我并不是说这本书将成为衡量高级开发者是或否的新标杆。我可能很有野心，但也许对于这项工作可以实现的成就并没那么野心。对于这个特定的动机，我的目标是找到一个我认为高级开发者应该知道的知识的共同基础。

另一个动机，如果你愿意的话，可能更多是对网络上、书籍甚至通过……提供的大量低质量资源的一种反应。

教育机构。这是一场无声的反叛！一想到我们这个奇妙的 PHP 开发者社区的新手可以在线搜索关于面向对象的 PHP 教程，然后用他们稚嫩、纯真的大脑充满各种糟糕的、在某些情况下甚至是极其危险的建议，就让我感到痛苦。撇开那些关于搜索引擎及其页面排名算法的阴谋论不谈，目前还没有人完全迎合互联网，而在这种情况下，整理出优秀的内容似乎是有价值的。

现在，我大可以自己建立一个网站，并链接到所有好东西……

互联网上有许多非常棒的教程。有很多恰恰所需的信息。这很棒，但它们没有包含对那些正在教给你的内容的警告，也没有突出这些内容本身的陷阱。虽然它们告诉了你*可以*做什么，但并不总是告诉你你*应该*做什么。它们显然并没有总是包含关于这个或那个主题的陷阱、坑（gotchas）以及需要避免的事。

这刻意是这本书在你面前展开的一个核心特征；我想强调每个特定主题中可能出现的那些陷阱和问题，而不是告诉你你可以做这个或你可以做什么。一个例子出现在早期的“抽象”章节中。完全不缺那些告诉你抽象能促进代码、帮助避免代码重复的教程。这是错误的，但我把解释留到了相关章节。在某些方面，你可能认为这本书是鼓励我们忘记许多人在旅程中习得的坏习惯的方法，同时也是一种突出优秀内容的方法。

最后，这里还有一个隐藏的动机，一个几乎近乎自私的理由。在过去的几年里，我挑选了成百上千份简历，检查了成千上行的示例代码，并花费了无数个小时的时间对我我参与项目的各种职位的候选人进行面试。如果那些候选人在面试中与我讨论这本书，将是多么么梦想的事。他们对什么认同？对什么不认同？为什么不呢？我知道我说过，我并不打算让这本书成为高级开发者的衡量标准，或者它不是这样，但它确实可以作为一个帮助我衡量候选人处于什么水平的尺子，无论招聘官在寻找新才的过程中使用了任何赞美词。

在考虑到这一切之后……

## 这本书是关于什么的？

用一个词来说，卓越。《PHP 卓越》`PHP Brilliance`是我自己开始使用的一种元标准（meta-yardstick）。我之所以说“元-”，是因为经验告诉我它将是一个移动的目标。五年前，我会强烈地推崇 `MVC` 设计模式。现在，PHP 框架的世界已经成熟到正处于其黄昏之年的边缘。在五年后，这样的框架可能不再被提及，除非是从历史的角度来谈。

那么，《PHP 卓越》就是我逐渐认为的一种适用于当今 PHP 开发者的某种编程知识标准。在它的范围内，它涵盖了 PHP 中面向对象编程的核心基础。它跨越了许多原则和方法论。它涵盖了各种架构考虑的优缺点，并检查和赞扬良好的工作实践。

## 出版，Leanpub 方式。

我是精益（lean）流程模式的忠实粉丝。我确信当我们进入书籍的良好实践部分时，这一点将显而易见。我喜欢 `leanpub.com` 的那些优秀人才所做的工作，他们将这一概念应用于书籍的出版过程中。

如果你不熟悉 `leanpub.com` 发布的精益出版宣言¹，我在这里引用它。请务必访问网站以获取进一步的解释。

> 精益出版是使用轻量级工具和多次迭代出版一本进行中的书籍，以获取读者反馈，不断调整直到你拥有正确的书并建立起动力。

讽刺的是，甚至可能虚伪的是，我已经应用或正打算应用许多软件开发流程来达到完成一本书的最终目标。

首先，在写作时，我已经完成了我认为书中应该包含的内容的全部初稿。这并不符合精益，因为精益自然会厌恶这种浪费。

https://leanpub.com/manifesto

这是瀑布式开发（waterfall），一个会让大多数开发者起鸡皮疙瘩的过程。为了避免尴尬的自残行为，我将这个过程称为“汇集我所有预期的源材料”。这是一个借口，我坚持这么说。

从传统上，书籍出版完全是一个类似于瀑布式的过程。作者构思出一个项目，他们希望至少人类的某一部分会想读它。出版商买账这个想法（希望如此！）。完成的手稿在编辑的指导下，被发送给校对员、评审者和技术编辑，然后发送到印刷厂。希望在此期间，营销销售机器已经启动，以便在各种分销渠道获得它们可能热切期待的内容之前，引起兴趣。原始提议和最终产品之间存在着巨大的脱节，时间可能在 6 到 12 个月甚至更久。

对于《PHP Bliss》，下一步是迈向出版的第一步。在 2015 年 3 月底，第一部分将安装并供购买。到那时，我将开始一种类似于冲刺（sprint）的结构，承诺每两周发布一次书籍的更新版本。但我并没有真正采用冲刺；我甚至不确定能否说服猫参加每日站会，无论我用多少零食来诱惑贿赂它们。

每两周一次的迭代对我来说，是一种在编辑、修订和发布书籍的过程中应用纪律的一种小方法，也是我建立良好习惯的一种大方法。

最近我的一位读者指出，要了解自上次更新以来发生了哪些变化并不是总是易的事。

因此，我在开头处添加了这个页面，列出了自上次发布以来的新增和更新内容。

希望这对你有所帮助！

- 2016年1月22日

  - 更新内容

    * 第一部分 大脑检查

    * 第二部分 大脑检查

    * 第三部分 讨论点

    * 第三部分 大脑检查

## 前言 (Prelude)

> “这个营地里有人并非他看起来的样子。现在这可能是我们中的一个或两个。到了春天，可能就是我们所有人。” - 麦克迪 (MacReady)

## 更多消遣时间 (More Pub Time)

在开始阅读正文之前，有一个核心原则是我们应该首先关注的。在写作时，你极可能以前从未听过这个原则。我很想说，它是某个不靠谱的、不在记录在案、机密的政府机构经过多年秘密研究的结果，并且它以某种方式落入了我的手中。

我很很想说，为了更大的利益，我现在将该原则的细节泄露到公共领域，以便全人类能够阅读、理解并吸收。

然而，我做不到这些。

遗憾的是，情况的现实要平庸得多。

它是我我编造的，专门用作这些页面中出现内容的统一主题。

## 引入“更多消遣时间”原则 (The More Pub Time principle)

如果我用一种简洁明了的方式来表达这个原则，可以这样描述：

> 通过预见性地获取正确的知识，程序员可以加速自己向精通领域的个人发展，并产出健壮、高质量的软件应用程序。反之，可以避免常见的易错场景，并保留极具价值的消遣时间。 - “更多消遣时间”原则²

不过，我并不太喜欢口号式的格言，所以让我们继续将其拆解为更有实际意义的内容吧。

## 什么是正确的知识？

上述原则的表述留下了被指责为陈述显而易见事实的空间。如果一个开发者脑子里拥有所有正确的知识，那么他的应用程序代码质量自然而然应该是高标准的。

但什么是正确的知识呢？

为了回答这个问题，我们首先需要对几点进行限定，包括对代码质量本身的定义。幸运的是，我们可以站在巨人的肩膀上，研究该领域已经完成的工作。

- 功能质量（Functional quality）反映了特定应用程序在服务于其预期用途方面的程度。

- 结构质量（Structural quality）反映了非功能性需求，以及应用程序代码如何支持应用程序功能需求的实现。

通常所谓的“适用性”（Fitness for purpose）并不是我们在这里考虑的内容；构建一个可以与桌面版本竞争的在线文字处理器，与尝试构建专门为阿拉斯加鱼爱好者设计的社交网络，其功能需求会有很大不同。

任何给定软件项目的功能质量将根据该项目的特定标准进行判断。换句话说，它是否实现了它应该做的事。

## 可靠性 (Reliability)

任何给定软件项目的功能质量将根据该项目的特定标准进行判断。换句话说，它实现了它应该做的事。

## 可维护性 (Maintainability)

任何给定软件项目的功能质量将根据该项目的特定标准进行判断。换句话说，它实现了它应该做的事。

## 安全性 (Security)

安全性可能是软件质量中最被误解的方面。自然地，作为开发者，我们希望保护应用程序的数据免受外界更恶意元素的影响，但安全性的影响范围远超常见的（尽管同样关重要的）防御攻击向量的行为。

就安全性而言，有从更广泛的术语来考虑这个话题。所有应用程序的共同点是它们都会收集、处理和存储数据。无论是游戏、社交网络、公司内网还是博客网站，数据在任何情况下都是王道。

因此，就软件质量的安全性方面而言，我们必须扩大定义，从防止黑客攻击扩大到承认维护数据完整性至关重要的程度。

如果我们应用程序中的数据“大部分没问题”，那么我们就麻烦了，因为这意味着其中某些数据是坏的。我们需要应用程序中的所有数据在任何时候都是好数据，它们需要出现在它们应该出现的地方，而不是出现在不该出现的地方。

## 更多下酒时间

因此，评估软件质量的安全性方面不仅仅是确保我们保护自己免受 SQL 注入攻击，或正确地对用户密码进行哈希处理。它还确保我们已经部署了正确的验证机制，并将这些验证代码放在了正确的位置。它还确保在多阶段数据处理过程中，如果某个阶段失败，可以回滚到原始状态。它涉及许多方面，但最终结果必须是：所有正确的数据都处于所有正确的位置，且没有出现在任何其他地方。

确保我们已经准备好应对使用 `;DROP TABLE users;@hotmail.com` 作为邮箱地址的用户是一回事，但如果我们团队的某人创建了一个算法，无意中将每个用户的名字都设置为四个字符的 "John"，那么我们已经身处绝境了，而且连救命都看不见。

## 效率

我过去认识过一些开发者，他们对创建极高效、运行快速、低内存占用的代码有乎常人的重视。他们认为声明的代码只有在速度快时才是美的。

谢天谢地，我们大多数人已经更明智了。

在云计算和虚拟化爆发之前的日子、几个月和几年里，应用程序的性能通常可以通过被称为“投入更多硬件（throwing more tin at it）”的操作来提高。在机架上增加一台服务器或安装快速硬盘或更多内存，通常比支付开发者优化代码所需的时间薪水要便宜得多。

如今，我们仍然可以以虚拟化的方式“投入更多硬件”，即通过启动另一个实例来实现。

尽管如此，如果我们希望保住我们那至关重要的“下酒时间”，那么创建性能良好且高效的代码仍然非常重要。已经可靠、安全且易于维护的代码始终可以针对速度和效率进行优化。

但先为了速度而编写的代码，在事后很难针对可靠性、安全性和可维护性进行优化。

这并不是说速度和效率不重要。一个需要花费三十七分钟才将一个请求转换为响应的在线应用程序，如果它还存在留住用户的微小希望，那么它在周期结束时提供的必须是绝对关键的信息。

绝大多数在线应用程序的现实是，请求-响应循环需要在几秒钟内完成，而不是几分钟。对于我们在线世界来说，幸运的是，有很多技术可以提高应用程序的感知性能，从而提升用户体验。

与其将账户激活邮件作为注册程序的一部分发送，我们可以将其放入队列，由独立进程（如 cron 或守护进程）来处理。

与其在请求-响应循环中解析和处理上传的 CSV，我们可以将文件移动到一个监控目录中，并允许通过一系列后续的异步调用将文件的处理状态报告回前端。

当然，我们可以优化应用程序代码的实际性能和效率，而不仅仅是感知性能和效率。那个执行了 `SELECT * FROM users` 然后在内存中遍历整个结果集，只为了找到刚刚登录用户的行的开发者，可能首先需要被踢一屁股，其次要被教他如何写 `WHERE` 子句。在这种情况下，返回单行显然比拉取整个表要高效得多。

尽管效率位于这个列表的底部，但在评估应用程序及其代码质量的四个因素清单中，效率仍然是一个非常重要的因素。

> 软件质量本身就是一个宏大的课题，关于这个主题已经出版了数百本书和学术论文。在这里，我仅仅触及皮毛，而且触得非常浅。尽管如此，我希望我至少传达了关于“高质量代码是可靠的、可维护的、安全的且高效的”这一含义的模糊印象。

这让我们更接近于考虑什么是正确的知识。但在在此之前，我们应该花点时间考虑错误的

## 你好，世界！

学习过程有详尽的记录。不仅在编程圈，在任何一种行业或手工艺中，从业者都会经历几个独特的阶段。开始是初学者（novice），他们学习基础知识和第一性原理。我这么说可能非常自大，但我准备好打赌，我们许多人都是从 1973 年在屏幕上写下“Hello World”开始这段旅程的，这都要归功于当年的 Brian Kernighan。

超越初学者阶段的是行者（journeyman），他们通过获取额外知识并与经验相结合，在基础的基础上进行构建，以磨练技能并促进个人发展，最后为进入最后一个阶段——大师（master craftsman）阶段做好准备。

传统上，大师的头衔是由监督他们特定行业或手工艺的行会授予从业者的。当准备好后，行者准备并提交一份作品作为申请过程的一部分，由行会成员对该作品进行判断，并确定他们认为是否值得。



在在线应用程序创建的世界里，我们没有拥有这种结构化的个人发展方法；人们无法轻易向一位公认的大师学习徒。因此，我们的行者阶段与其说是在一个阳光明媚的草地上欢快地跳跃，不如说是在一个充满陷阱和坑洞的危险沼泽中蹒跚前行。

得益于互联网，这变得非常巨大。由于拥有大量可用材料来进进知识和能力，行者级开发者字面上被机会所淹没。既有在线课程，也有传统的实体学习机构可以供选择，还有数不尽的文章和博客文章。

而这正是危险所在；很大程度上不受限制和不受监管的教程和培训视频发布，对行者级程序员构成了非常真实的危险。面对如此难以想象的海量信息，行者级程序员如何希望从劣质信息中筛选出优质信息，尤其是当劣质信息以不断增加的速度不断涌来时？

举例来说，最近在 2015 年 12 月，我在经常访问的开发者论坛上遇到了两个质量极差的教程。第一个展示了如何“使用 `extract()` 函数轻松填充变量”，这是一种特别危险的“技巧”，在没有让读者充分意识到其中危险的情况下就让他们学习它。

然而，与第二个教程相比，即使那个也显得微不足道。第二个教程说明了如何使用 AJAX 将搜索词从 HTML 表单发送到 PHP 后端，后端在查询数据库后将搜索结果返回前端。从表面上看，这似乎是一个发布教程的完全合理的行为，作为一个主题，它无疑已经被讨论过无数次。

然而，在这个特定的教程中，示例代码演示了通过遍历 `$_POST` 全局变量并直接使用这些值来创建 SQL 查询，而没有进行任何形式的验证或清理。

对于任何有经验的开发者来说，这应该是一个恐怖的局面；一个在 2015 年发布的教程对防止 SQL 注入攻击毫无帮助，并证明了“浅学而止，是危险的”这句谚语。

然而，很容易忘记，每天都有新的新手在编码道路上迈出第一步。任何这样不幸地复制并粘贴这段教程代码到他们工作项目中的人，都会受到那些相同的 SQL 注入攻击的威胁，直到他们获得正确的知识并让他们能够防御这些攻击为止。

这让我们很自然地绕回考虑什么构成了正确的知识。遗憾的是，在写作时，这个问题还没有一个肯定的答案。我也怀疑是否会有这样的答案。

软件开发职业带来的巨大乐趣之一，就是学习过程永远不会结束。无论开发者在这一主题上达到了多么高深的程度，总有新的东西要学习。一方面，是因为这个主题本身非常庞大；另一方面，是因为技术在不断进步。

由于这两个不同的原因，完全精通应用程序软件开发是无法实现的。在任何时刻，一个人的大脑都装不下这么多内容。而今天的最新技术极可能在明天被取代。

# 更多的下酒时间

尽管如此，但我坚信，每一位高级开发人员及以上的人都应该有一套必须掌握在胸中的知识库。这种知识库可以涵盖各种主题，从非常具体的细节（如始终确保对输入进行适当的转义、验证和清理）到广泛的概念（如核心软件开发原则、规则，甚至是设计模式）。

但为什么呢？

原因本身可以简单地表述为：为了构建更好的软件。更具体地说，是为了从结构质量上构建更好的软件，使其变得可靠、可维护、安全且高效。

太棒了！现在我们已经确定了软件质量的定义，以及实现软件质量所需的正确知识……

# 所谓的下酒时间到底是什么鬼？

如果我们想通过提前学习正确的知识来保护我们宝贵的下酒时间，从而实现高质量的软件，我们需要知道所谓的下酒时间到底是什么鬼？

这是“更多下酒时间原则”`The More Pub Time Principle`中比较幽默的一方面，这也是它永远不会被学术界接受为有效的软件原则的原因，但简而言之，它是这样的：

> 下酒时间是以任何方式投入、比留在办公室里寻找并修复那些完全可以避免的软件漏洞更有利于快乐和充实生活的时间。

对我来说，这通常意味着和朋友一起去酒吧叙叙旧，但从定义上讲，它并不局限于去酒吧。下酒时间可以带着你心爱的去吃一顿浪漫晚餐。也可以意味着准时回家给小孩子们读睡前故事。或者去看戏。或者去健身房健身锻炼。或者启动游戏机炸掉外星入侵者的脑袋。

事实上，任何能够提高你生活质量和增加乐趣的活动，都可以被视为“下酒时间”，这与浪费在深夜去寻找和修复完全可以避免的软件缺陷相比。

# 结论

软件开发人员职业生涯中的练手阶段`journeyman stage`定义得有些模糊，对于在网络世界工作的开发者来说，更是如此。

网页很大程度上是构建在 PHP、Ruby 和 Python 等开源语言之上的。这些每种语言都有忠实的追随者，并受到极优秀社区的支持，因此，在线和线下都有大量的学习资源。

然而，互联网永远无法通过消除练手阶段来实现这一点。对于学习任何手艺或主题的学习者来说，都不可能在没有度过练手阶段的情况下直接跳到精通`novice`。这并不是未来可能解决的技术局限性，而是人类思维的局限。知识的获取是通过学习过程完成的，这使我们受限于目前的生物局限性。

我们绝对可以做的是缩短练手阶段开发者所经历的路径。当面对着新手之地与大师之地之间的沼泽时，我们可以挑选出一条可靠、快速且安全的路径来遵循——一条能带我们去往所有值得去的地方，并引导我们安全地避开陷阱和深坑的路径。

这正是“更多下酒时间原则”通过提供其相当模糊的定义所旨在做的：

> 通过提前获取正确的知识，程序员可以加速自己向精通的个人发展，并产出健壮、高质量的软件应用程序。反之，可以避免常见的易错场景，并保留极价值的下酒时间。

目前已经有一些倡议，旨在帮助练手阶段的开发者在泥沼中找到更快、更安全的路线。一个非常优秀的资源是 `PHP: The Right Way`^3 项目，我强烈向每个阶段的 PHP 开发者推荐它。另一个资源就是此书。

《PHP Brilliance》作为一本书的目标是将所有正确类型的信息呈现在你面前。从架构方面的考虑（如 MVC vs 服务面向型架构 vs 微服务）到对 SOLID 原则的彻底检查，从全新的角度看待抽象和继承，到考虑利用闭包`closures`的“弗兰肯斯坦方法”。

《PHP Brilliance》作为一种心态的目标是确保你有能力领导团队创建可靠、可维护、安全且高效的美丽代码。

生命短暂，所以请将这一建议记在心上：保护好你极其宝贵的时间，并享受沿途的程。

最后但绝不是最后，请记住：理性喝酒。

> ^3`http://www.phptherightway.com/`

# 基础

> “我不知道里面到底是什么什么鬼，但它很奇怪而且很火大，不管它是什么。” - Clark

# 面对象思维

在进入真正有干货之前，我们需要停顿一下，检查我们对什么是面向对象编程的理解。虽然这本书不是写给那些刚开始开发生涯的人的，但当我们作为开发者第一次遇到面向对象`OO`这个概念时，很容易对它形成一个固定的看法。

此外，还有大量的在线教程它们都采取几乎相同的方法来解释它，因此，这些教程往往会在这一领域传播一些相当固定的思维。

如果我们打算用优优雅的 PHP 代码构建我们的宫殿和城堡，我们必须把注意力转向我们打算构建在基础之上。为了建立起逻辑宏伟的伟大建筑，使其不仅融入网络世界的天际线，而且真正成为定义该天际线的一部分，我们专注于基础工作。我们的应用程序不仅需要经受箭矢，还需要屹立不倒。所以，让我们回到基础，检查我们知道的。。很多教程会将对象视为某个事物的表示，然后页面本身用 html 构建，并点插内联 php 结构。顶部是程序逻辑，底部是输出。

这种方法的用处是给出的示例对读者来说已经熟悉。任何开始学习面向对象 PHP 的人都知道汽车是什么或狗是一种动物。这里的危险在于`这也是我们许多人掉过的陷阱`，开发者开始执着于这种将他们创建的对象链接起来的想法。在他们之后的下一个项目中，他们开始寻找项目中的“名词”，并围绕它们规划对象。这里是一个用户`User`，那里有一个产品`Product`。对于识别和设计将成为应用程序关键角的对象来说，这是一个完全有效的起点。

如果你将指导和导师团队中更初级的成员，你会在过程中看到一些相当糟糕的代码。我想设定我们为了达到面向对象思维将要采取的路径。它从一个光鲜崭新的新手开始，Joe 在 PHP 学习版图中所走的路线为了到达我们办公室学习 OO，这种事并不罕见。我想说这完全是虚构的，但事实并不完全如此。你看，Joe 的路径实际上是我所走过的路径，尽管在各处添加了一些大量的艺术加工许可。我不觉得羞愧。

从一开始，Joe 就学会了用 PHP 编写脚本；为他构建的网站每个页面使用一个脚本。这里有一个 `index.php`，那里有一个 `about.php`。数据库访问和变量赋值等操作可以在文件顶部完成，然后页面本身用 html 构建，并点插内联 php 结构。过了一段时间，Joe 意识到他在脚本之间重复了大量的代码。这就是他开始将其拆分成独立文件的地方：头部`header`、页脚`footer`、访问数据库的程序，其他用于构建 html 表的程序。不久后，他创建了常用函数库，可以将这些函数从一个项目移植到另一个项目。诸如 `database.php` 的巨大 PHP 文件，

## 面向对象的思维

html .php 以及其他将有用函数聚集在单个文件中的集合。

当 Joe 开始学习面向对象开发时，会发生什么？他被引入了一个“Car”`汽车`类，这个类不仅拥有轮子和引擎等属性，还拥有方法`函数！`让汽车执行如 `move()``移动`、`turn()``转向`和 `stop()``停止`等操作。

Joe 认为将他精心设计的函数库封装在类语句中是一个好主意。现在 Joe 正可以选择两条路径之一：他是应该实例化一个 `Database` 对象来使用这些移植的库方法？还是在函数声明中添加 `static` 关键字，以便他可以静态地调用这些类方法？

嗯，实例化对象看起来并没有特别用。我们还是选择静态的吧。

现在 Joe 的代码中经常会出现这样的内容：

```php
<?php
include("Config.php");
include("Database.php");
$conn = Database::connect($dbname, $dbuser, $dbpass);
```

哎。

最终，我们的开发者将完成转变：从将函数库封装在类语句中，转变为识别系统中的名词并围绕这些名词构建对象。这与他所遵循的教程非常一致。我们从 Joe 身上看到的，是这些教程以及他们过早完成主题的习惯导致的主要但自然的结果。

Joe 的类变得异常巨大。应用程序中心的类，无论是 `User``用户`类还是 `Product``产品`类，都是真正巨大的，跨越了数千行代码，且方法长到屏幕上无法同时显示开头和结尾。滚动，滚动，再滚动。

这里发生了什么？

开发者为了编写对象方法，再次退回到了过程式代码知识，而不是执行一个单一函数、从头到尾运行整个过程。这最显而易见的例子是一个对象方法，它可能位于一个名为 'User' 的类中，并且最可能命名为类似 'create'`创建`或 'register'`注册`。

我承认，对于许多 Web 应用程序来说，用户注册过程可能是一个复杂的过程：需要对提交的多个表单字段进行验证，创建带有登录凭据的用户记录，可能还要存储地址并将新创建的用户与其关联，以及挂载任意数量配置设置。这里发生的情况是，开发者取了一个过程化的流程，并简单地将其移植到一个对象方法中。原本用于接收和处理用户注册的单一 php 页面，被整体移植到了 `User` 类中的单个方法中。你要明白，这并不是字面上的复制粘贴操作，而是对代码进行选择性的提取和重建模，将其挤在这些开闭大括号之间。

Joe 从验证传递给 `register()` 方法的参数开始。如果一切进展顺利，他就会开始执行必要的数据库操作，以将数据存入存储并提取 ID。这部分可能产生一次查询，也可能是：基础用户详情可能伴随着一个表中的某行默认偏好设置，以及另一张表中的物理家庭地址。如果一切进展顺利，Joe 就会发送欢迎兼验证邮件，最后向该方法的原始调用者返回 `true``真`或 `false``假`。

在这一个方法中，我们至少有三个断点——过程可能失败的地方——导致了脆弱的设计，这种设计会以多种方式崩溃，同时难以维护。即验证阶段、数据库阶段和邮件发送阶段。

现在是为面向对象思维引入一个核心原则的好时机。我不记得第一次在哪里遇到这个原则的，但它从那时起一直留在我脑海。它是这样的：一个对象要么知道事情，要么做事情，但绝不能兼者兼。

我们构建的许多应用程序都有一个 `User` 模型对象。如果这样一个模型对象代表了我们对特定用户的了解，而我们知道用户注册是一个过程，那么自然而然是，我们的 `User` 模型类不能有一个 `register()` 方法。

你对这思考越多，它就越合理。毕竟，为什么我们所有的 `User` 类实例都要围绕一个最初目的是为了创建用户记录的方法转转呢？这种实例什么时候再次需要 `register()` 方法呢？

如果你将那个“知道事情”或“做事情”的原则应用到你最近的应用程序模型层，它会建议你修改多少个模型类？你的模型中有多少实体知道它们所代表的事物的细节`即其代表的数据`，并提供了除了设置和获取`set and get`之外的操作这些数据的方法？

在大多数情况下，我们模型层的主要居民将是代表应用程序内部数据的对象。从这个意义上说，这些是“知道事情”的对象。例如，假设我们有一个处理大量 `User` 实例的应用。我们应该确保每个实例都知道它所代表的用户的姓名、生日和地址。同样，一个完整的应用程序将使用包含更多细节的 `User`，但目前这可以作为我们良好的起点。这些实例中的任何一个都不持有持有其所代表的各个数据片段的方法。我们模型类的方法将完全是内省的`introspective`。setters 和 getters 自然属于这一类，但那些我们可以识别为“处理器”`processors`的方法又是呢？

我说的处理器是指什么？

处理器是“做事情”的方法。验证用户输入的方法是处理器。触发发送邮件的方法是处理器。在几乎所有情况下，除非处理器是特定的内省性的，否则它可以移动到一个新对象中，该对象设计用于处理和封装该过程。

对于注册程序，理想情况下，我们寻找的是一组在用户账户创建过程中协作的对象。每个对象都将有一个严格定义的关注领域，执行单一任务并将其做好。让每个微小的部分作为目标的一部分运行是我们的目标。我们寻找一组验证器对象，负责检查每个部分`密码验证器可以确认提供的密码具有正确的字符数量和范围，日期验证器可以确认提交的出生日期格式正确，并且可能重要的是，在正确的范围内`18岁以上？`。

当我们采用这种方法时，我们巧妙地将执行验证的逻辑与执行记录创建的逻辑分离开来。按照理想方式继续，我们的记录创建过程应该被妥善地收起来，并与代表这些数据记录的对象分开。

你在书中完全可能会注意到的这一点就是我经常引起你注意显而见的循环引用。关于继承的章节会引导你预读关于“里氏夫替换原则”`Liskov Substitution Principle`的章节。里氏夫替换原则章节会引导你引回继承章节，并横向引导你查看“推进组合优于继承”的部分。一个主题有许多方式依赖或强化另一个主题，以至于边界变得模糊。每当交叉发生时，我都会力求指出它们。

# 面向对象的思维

如 `if` 或 `switch` 等条件语句出现在方法中，这些条件语句并不是用于执行验证，而是根据传入的参数选择要执行的不同逻辑路径。请尝试将 `if` 语句的使用限制在验证上。如果你是因为某个特定属性的值而在代码中创建了分支过程，那么几乎可以确定，通过为每个分支过程创建一个独立的对象，并利用类似策略模式`Strategy pattern`或责任链模式`Chain of Responsibility pattern`的机制来处理，将会对你大有益。

你无法同时看到某个方法的开始和结束。如果一个方法在你所选的编辑器中占据了超过一个屏幕的长度，那么你就有问题了。仔细观察方法，看看你是否至少可以将它们拆分开——很有可能是你正在执行多项任务。作为一个通用的原则，我建议确保你的方法包含活跃代码不超过二十行。

你的方法内部有很多内容。文档记录良好的代码是一件好事，但如果你发现一个方法需要解释你所采取的每一步，那么要么是执行的步骤太多了，要么是作者认为你是个笨蛋`numpty`。最好的方法是简洁明了的，并在上方的 docblock 中对意图提供易于遵循且简练、有帮助的解释。

这些就是我们需要关注的问题类型。文档记录良好的代码是一件好事，但如果你发现一个方法需要解释你所采取的每一步，要么是执行的步骤太多了，要么是作者认为你是个笨蛋`numpty`。最好的方法是简洁明了的，并在上方的 docblock 中对意图提供易于遵循且简练、有帮助的解释。

## 四大核心原则

这四个核心原则当然是*封装、抽象、继承*和*多态*`orphism`；这些主题只要面向对象编程一存在，它们就一直存在。每一个原则都有自己一个独立的章节，我将按照同样的顺序来处理它们。

那么，我们该翻页了，开始钻研*封装*了，因为我确信你们对阅读这部分内容感到兴奋的心情正如我在编写它时一样兴奋。噢，确实如此。

## 封装我们的思想。

你上一次考虑*封装*是什么时候？

很有可能已经过了很长一段时间了，特别是如果你已经身处资深开发者的行列中。封装是你学习面向对象开发时学到的第一个概念，它几乎不是一个你经常需要重新审视的话题。

尽管如此，我非常希望我们再次回顾这个主题。我们已经讨论过很多次，要确保我们在坚实的基础上进行构建，而为了做到这一点，我们需要彻底掌握最基础的知识。

如果

看到了吗？里面完全没有隐藏任何东西。不过，这自然应该与我之前提议的契合，即我们应用程序中的*知情者*`knowers`应该只携带负责维护和操作这些*知情者*所持有的数据的方法。

用代码给出一个极其简短的示例，像这样的代码就能说明封装的思想。

```
class User
{
  public $name;

  public function setName($name)
  {
    $this->name = $name;
  }

  public function getName()
  {
    return $this->name;
  }
}
```

这只是一个简单到痛苦的类，展示了数据和 getName() 分别对应的封装。那里没有一点隐藏任何东西的迹象，特别是当你考虑到 `$name` 属性和两个方法都被声明为 public`公有`时。

所以，那个给你关于数据隐藏的标准回答的家伙？他有点偏离了目标，但又能能怪他呢？即使 Wikipedia 上关于封装的页面也推崇同样的理念。但请不要误，当我们构建健壮、可扩展且易于维护的应用程序时，我们实际上想要将封装和数据隐藏的想法结合在一起。

那么，数据隐藏到底是什么？



首先，让我们完全抛弃“数据隐藏”这个术语。准确地说，我们需要将其称为“信息隐藏”（information hiding），这更恰地涵盖了数据方面以及在这些数据上运行的实现逻辑。信息隐藏是一个过程，通过 `private`、`protected` 和 `final` 等访问修饰关键字，防止类和对象的某些数据和逻辑部分被客户端和协作者访问。或者换句话，信息隐藏完全在于保护我们对象的内部工作免受外部干扰的能力。但这有什么好处呢？答案在于保护你的数据完整性的能力。没有什么比这对你的应用程序安全更重要的了。

## 封装我们的思想

当我们从在线应用程序的角度考虑安全问题时，我们通常关注保护该应用程序免受外部攻击的问题。我们想让坏人远离我们的数据库，确保其免受邪恶的侵害。这当然是本该的，但我还想确保当我们谈论应用程序安全时，我们将观点重新定位到“数据完整性”。数据完整性不仅意味着它留在它应该去的地方（即我们设计和实现的存储系统内部），还意味着它保持正确和真实。

在我们继续之前，让我们确保清楚这个所谓的“信息隐藏”鬼东西到底是怎么回事。如果我们再次看上面那个简单的类，`$name` 属性显然是暴露的。我们的任何其他代码在看到这个 `User` 类的实例时，都可以愉快地且不加区分地更改 `$name` 属性的值。

```
user->name = 'Joe';
```

非常基础的内容！我们可以通过确保将 `$name` 属性声明为 `private` 来防止那种无节制的数据篡改。当我们这样做时，我们是将其锁定在公有视线之外，随后强制任何客户端代码利用我们提供的 `public` 接口来请求访问该数据。当然，我们决定提供的此类接口将充斥着如验证、授权之类的陷阱。

> 有方法可以可以直接访问对象的私有属性，但我会将那些留到以后说，并仅作为告示性的故事。为了保持文本的连贯，我现在将假装私有属性的值无法从外部被直接修改。希望你们在这一点上能认同我。

现在，我只花了几页纸的内容就强调了封装和信息隐藏作为两个独立事物的区别，我接下来想做什么呢？

噢，不是要把它们重新结合在一起！

## 封装我们的思想

在后的内容中，我想把封装看作既是将数据和相关方法打包在一起，并确保我们继续隐藏那些真正敏感的部分。在这一点上，我不想在还没有对真正的原始封装和作为独立事物的信息隐藏进行区分的情况下继续下去。现在我们现在都可以放心地知道，从现在起，我们将把封装看作既是正当的封装，也是信息隐藏。这个想法是，那些最初属于“封装就是数据隐藏”阵营的人和那些不属于该阵营的人，希望现在达成一致了。

## 保护我们的数据

那么我们的目标就是保护我们的数据并保持其完整性。这里有一个新颖的想法——让一切都私有。

这听起来可能有些离谱！

一个只有私有属性且无法公开访问的对象，这为数据提供了最大的安全性。记住，世界上最安全的不可被黑客攻击的对象是那些私有属性的。在这里，这里可以画一个类比——一个拥有所有 `private` 属性且没有 `public` 方法的对象。如果所有的属性都是私有的，那么就不会发生意外在数据上。

当然，让我们以此作为你设计对象的基础。从不要有任何理由提供 `public` 属性开始。

`PHP` 作为一种语言，其最大的优势之一是它允许你开发应用程序的速度。事实上，许多 `PHP` 的无数 `MVC` 框架都描述了如何在一小时内创建一个应用程序。自矛盾的是，这种 `PHP` 允许快速开发的能力也是它最大的弱点。它积极地鼓励了懒惰。这种懒惰对于经验丰富的 `Java` 开发者来说是反感的。创建高质量的 `PHP` 代码通常意味着避免“捷径”，并投入时间走远路。

让我们深入研究这个问题。

### 封装我们的思想

假设我们有一个用户对象，其属性为用户名、电子邮件地址和某种信用余额。我们可以合理地预期会将这些属性值渲染到用户的浏览器上。远来看，这样做最简单最快的方法是将这些属性设为 `public`，并在代码的相关点将它们输出出来。让我们看一下这段代码，这样我们就能看到我在说什么。

```php
class User {
    public $username;
    public $email;
    public $balance;
    public function __construct($username, $email, $balance) {
        $this->username = $username;
        $this->email = $email;
        $this->balance = $balance;
    }
}

$u = new User('joe', 'joe@example.com', 12.95);
```

```
echo $u->username;
```

这是我们超级快速且简单的设置对象并渲染我们对象的公共属性的方法。对于 `PHP` 来说，这是完全有效的代码。当然，对于通过成为健壮、安全且易于维护的企业级应用程序的一部分来反映 `PHP` 的卓越来说，它完全不是那样。

所以我们该怎么办？修复上面的用户对象的第一步是将属性声明为 `private`。这始终是正确的做法。如果我们的世界是那些理想世界之一，根本就不可能将对象的属性声明为 `public`。不幸的是，我们的世界离理想还有一点距离，所以我们需要警惕这种基础性的错误。我说是要警惕，但 `PHP` 开发者越早开始用 `private` 来构建他们的类定义越好。

### 封装我们的思想

属性越多，越好。这是那种本应该少是第二本能，而多是基本直觉的事情。

让我们来看看这个变化。

```php
class User {
    private $username;
    private $email;
    private $balance;
    public function __construct($username, $email, $balance) {
        $this->username = $username;
        $this->email = $email;
        $this->balance = $balance;
    }
}
$u = new User('joe', 'joe@example.com', 12.95);
```

```php
// 我们再也无法这样做了...
echo $u->username;
```

好的，现在代码看起来好了一点。通过上面的代码，显而易见的是 `username`、`email` 和 `balance` 属性受到了不受任何外部影响的保护。该类目前的状况并不是完全可用的，因为我们已经没有办法访问这些值了，但无论我们的团队成员对应用程序做什么，只要他们不编辑这个类，一旦实例创建，就没有办法在运行时有意地或无意地更改这些属性。

太棒了。

我们创建了一个超级安全的 `User` 类，它并不是特别有用，但是嘿，至少那些棘手的属性现在是安全可靠的。不过，我们的工作远未结束——至少可以预期，即使我们不需要显示这些属性，`balance` 值也很可能通过我们网站的经常使用而发生变化。更多工作？是的，考虑到我们正处于旅程的起点，这是理所当然的。“这是一个曲折的旅程，而且无法在途中找到神奇的戒指来将它们束缚在一起。”

记住，在途中你会遇到很多陈词滥调。这里就有一个。关于冲刺和马拉松的什么。是的，这不是一场冲刺。

本着上述陈词滥调的精神，让我们来进行小小的偏移。我看到开发者反复地实现魔法的 `__get()` 和 `__set()` 方法，为了操作对象中属性的值。有些 `PHP` 框架甚至支持这种方法，在我看来，这是一种极度残忍的罪行。并不是因为此类框架的流行意味着许多 `PHP` 开发者接触到了这种方法，其中许多人甚至可能认为这是正确的编码方式，“嘿，这些哥们儿是这么做的。”

让我们看看这段代码，以便我们更好地看到发生了什么。

```php
// 为了可读性省略了错误处理和验证
class User
{
    private $data = array();

    public function __set($key, $value)
    {
        $this->data[$key] = $value;
    }

    public function __get($key)
    {
        return $this->data[$key];
    }
}
```

开发者的内疚减轻了。他将对象的属性持在一个私有的 `$data` 数组中，这当然是正确的做法，对吧？让我问你一个问题：这和使用公共属性有什么区别？答案当然是它们没有区别。当然，我们可以开始向 `__get()` 和 `__set()` 方法中添加逻辑来收紧它们，但如果我们认为通过这样做实际上在改进我们的代码，我们无疑是在自欺欺人。随着我们继续深入 `PHP` 辉煌之路，这将会变得更加明显。

你看过剧集《迷失》(*Lost*)吗？*Jack*、*Kate*、*Sawyer*、*Locke* 等人在飞机坠毁后被困在一个神秘岛屿上。该剧的第一季、第二季和第三季在第二次看时非常有意义。一旦你知道了结局，开头会有多得多的“啊哈！”时刻，这让第二次观看的体验由于与第一次观看不同的原因变得愉快。不可避免，这本书也会有点像那样。承认吧，只不过极熊较少。



本着上述陈词滥调的精神，让我们来进行小小的偏移。我看到开发者反复地实现魔法的 `__get()` 和 `__set()` 方法，为了操作对象中属性的值。有些 PHP 框架甚至支持这种方法，在我看来，这是一种极度残忍的罪行。并不是因为此类框架的流行意味着许多 PHP 开发者接触到了这种方法，其中许多人甚至可能认为这是正确的编码方式，“嘿，这些哥们儿是这么做的。”

让我们看看这段代码，以便我们更好地看到发生了什么。

```php
// 为了可读性省略了错误处理和验证
class User
{
    private $data = array();

    public function __set($key, $value)
    {
        $this->data[$key] = $value;
    }

    public function __get($key)
    {
        return $this->data[$key];
    }
}
```

开发者的内疚减轻了。他将对象的属性持在一个私有的 `$data` 数组中，这当然是正确的做法，对吧？让我问你一个问题：这和使用公共属性有什么区别？答案当然是它们没有区别。当然，我们可以开始向 `__get()` 和 `__set()` 方法中添加逻辑来收紧它们，但如果我们认为通过这样做实际上在改进我们的代码，我们无疑是在自欺欺人。随着我们继续深入 PHP 辉煌之路，这将会变得更加明显。

你看过剧集《迷失》（*Lost*）吗？*Jack、Kate、Sawyer、Locke 等人在飞机坠毁后被困在一个神秘岛屿上。该剧的第一季、第二季和第三季在第二次看时非常有意义。一旦你知道了结局，开头会有多得多的“啊哈！”时刻，这让第二次观看的体验由于与第一次观看不同的原因变得愉快。不可避免，这本书也会有点像那样。承认吧，只不过极熊较少。

封装我们的思想。

如果我们不这样做，将会导致致命错误（fatal error）。然而，作为人类，我们可以通过这两个参数被赋予的名称直观地理解它们本应该代表什么。

但 PHP 解释器并不会。目前，只要在创建对象时传递了两个值，PHP 解释器就会愉快地继续执行。如果由于某种原因，代码为第一个参数提供了整数而为第二个参数提供了布尔值，我们最终将得到一个已经创建的对象，但其属性的值在本质上将是错误的。

这是 PHP 语言中另一个被为人知的缺陷之一。它的松散类型特性允许我们开发者在编码时犯下各种极其糟糕的错误。我们修复这段代码的自然反应是开始在构造函数中添加验证逻辑，其精神在于声明：如果这些参数看起来是有效的，我们就接受它们。快速看一眼这种变化可能像这样：

```php
public function __construct($username, $email)
{
    if (!$this->isValidUsername($username)) {
        throw new Exception('Username parameter is invalid');
    }

    if (!$this->isValidEmail($email)) {
        throw new Exception('Email parameter is invalid');
    }

    $this->username = $username;
    $this->email = $email;
}
```

我承认，这要好。只要那些 `isValidXYZ()` 方法被正确实现，我们就加强了创建此 `User` 对象实例的过程。理论上，任何 `User` 实例内部都将有一个有效的类字符串 `username` 属性和一个有效的电子邮件地址属性。然而，我们刚刚在编码中引入了一个新的痛点。在构造函数中抛出异常，或者更糟，在由构造函数调用的方法中抛出异常，就像把头伸进垃圾处理器并希望有一个好结果。我在这里只使用了最通用的类来说明问题，因为异常处理至少值得专门用一个章节。为什么我……

封装我们的思想。

……会对在构造函数中抛出异常这件事感到自命不凡？这本身就是一个持续了很久久的争论，它将观众坚定地分为了“支持”和“反对”两个阵营。这也是我将在以后题为“实例化恐惧症”（Instantiophobia）的章节中详细处理的内容，但目前，我只需要指出这一点：你无法正确地测试一个构造函数。它没有返回值。它无法被 mock（模拟）。有更好的方法来实现我们想要的结果，我将在适当的时候讨论这些。

回到我们最初的问题，即如何在实例化点为我们的对象获取有效值。这里的技巧，即加强约束并防止由于松散类型语言带来的那种数据不安全的方法，是使用语言为提供的类型提示（type hinting）功能。PHP 开发者一直没有获得标量变量的类型提示，至少目前如此，这给我们带来了一些问题。并不是多大的问题——让我们创建验证器对象。

```php
public function __construct(StringValidator $username, EmailValidator $email)
{
  $this->username = $username->getValue();
  $this->email = $email->getValue();
}
```

这稍微好了一点。我们的 `User` 类现在将验证过程委托给专门的对象，这些对象是可以我们可以为构造函数方法签名显式进行类型提示的。通过委托，我们转嫁了确保我们需要的值确实是有效的责任。此外，通过封装，我们是在说：“嘿，我不需要查看你的内部实现来判断你是否在履行工作，只需让我调用你的公共接口，以便我获取我需要的值。”同时，希望这些验证器已经经过了适当的单元测试。

不过继续下去，能让你的 PHP 才华大放异彩的方式是你似乎预测了神秘的开发者水晶球，因此在两个、三个或六个月后，业务团队的某人会走到你的桌前说：

“我们需要在 `User` 类中增加 `phone_number` 属性。”

“我们需要在 `User` 类中增加 `address` 属性。”

“我们需要在 `User` 类中增加 `date_of_birth` 属性。”

“我们需要在 `User` 类中增加 `is_active` 属性。”

“我们需要在 `User` 类中增加 `，我们需要在 `User` 类中增加 `gender` 属性。”

“我们需要在 `User` 类中增加 `country` 属性。”

“我们需要在 `User` 类中增加 `time_zone` 属性。”

“我们需要在 `User` 类中增加 `bio` 属性。”

“我们需要在 `User` 类中增加 `profile_picture` 属性。”

“我们需要在 `User` 类中增加 `preferences` 属性。”

“我们需要在 `User` 类中增加 `last_login` 属性。”

“我们需要在 `User` 类中增加 `password_hash` 属性。”

“我们需要在 `User` 类中增加 `email_verified` 属性。”

“我们需要在 `User` 类中增加 `created_at` 属性。”

“我们需要在 `User` 类中增加 `updated_at` 属性。”

“我们需要在 `User` 类中增加 `deleted_at` 属性。”

“我们需要在 `User` 类中增加 `role_id` 属性。”

“我们需要在 `User` 类中增加 `organization_id` 属性。”

“我们需要在 `User` 类中增加 `team_id` 属性。”

“我们需要在 `User` 类中增加 `post_count` 属性。”

“我们需要在 `User` 类中增加 `follower_count` 属性。”

“我们需要在 `User` 类中增加 `following_count` 属性。”

“我们需要在 `User` 类中增加 `likes_count` 属性。”

“我们需要在 `User` 类中增加 `comments_count` 属性。”

“我们需要在 `User` 类中增加 `notifications_count` 属性。”

“我们需要在 `User` 类中增加 `settings` 属性。”

“我们需要在 `User` 类中增加 `theme` 属性。”

“我们需要在 `User` 类中增加 `language` 属性。”

“我们需要在 `User` 类中增加 `currency` 属性。”

“我们需要在 `User` 类中增加 `timezone` 属性。”

“我们需要在 `User` 类中增加 `status` 属性。”

“我们需要在 `User` 类中增加 `permissions` 属性。”

“我们需要在 `User` 类中增加 `tags` 属性。”

“我们需要在 `User` 类中增加 `metadata` 属性。”

“我们需要在 `User` 类中增加 `is_admin` 属性。”

“我们需要在 `User` 类中增加 `is_staff` 属性。”

“我们需要在 `User` 类中增加 `is_verified` 属性。”

“我们需要在 `User` 类中增加 `is_banned` 属性。”

“我们需要在 `User` 类中增加 `account_locked_at` 属性。”

“我们需要在 `User` 类中增加 `password_reset_token` 属性。”

“我们需要在 `User` 类中增加 `email_verification_token` 属性。”

“我们需要在 `User` 类中增加 `email_verified_at` 属性。”

“我们需要在 `User` 类中增加 `two_factor_secret` 属性。”

“我们需要在 `User` 类中增加 `two_factor_enabled` 属性。”

“我们需要在 `User` 类中增加 `two_factor_backup_codes` 属性。”

“我们需要在 `User` 类中增加 `last_login_ip` 属性。”

“我们需要在 `User` 类中增加 `last_login_at` 属性。”

“我们需要在 `User` 类中增加 `failed_login_attempts` 属性。”

“我们需要在 `User` 类中增加 `locked_until` 属性。”

“我们需要在 `User` 类中增加 `imfa_method` 属性。”

“我们需要在 `User` 类中增加 `subscription_plan` 属性。”

“我们需要在 `User` 类中增加 `subscription_status` 属性。”

“我们需要在 `User` 类中增加 `trial_ends_at` 属性。”

“我们需要在 `User` 类中增加 `billing_address` 属性。”

“我们需要在 `User` 类中增加 `payment_method` 属性。”

“我们需要在 `User` 类中增加 `customer_id` 属性。”

“我们需要在 `User` 类中增加 `stripe_id` 属性。”

“我们需要在 `User` 类中增加 `paypal_id` 属性。”

“我们需要在 `User` 类中增加 `invoice_id` 属性。”

“我们需要在 `User` 类中增加 `transaction_id` 属性。”

“我们需要在 `User` 类中增加 `refund_id` 属性。”

“我们需要在 `User` 类中增加 `coupon_code` 属性。”

“我们需要在 `User` 类中增加 `referral_code` 属性。”

“我们需要在 `User` 类中增加 `referred_by` 属性。”

“我们需要在 `User` 类中增加 `wallet_balance` 属性。”

“我们需要在 `User` 类中增加 `points_balance` 属性。”

“我们需要在 `User` 类中增加 `avatar_url` 属性。”

“我们需要在 `User` 类中增加 `banner_url` 属性。”

“我们需要在 `User` 类中增加 `bio` 属性。”

“我们需要在 `User` 类中增加 `website` 属性。”

“我们需要在 `User` 类中增加 `twitter_handle` 属性。”

“我们需要在 `User` 类中增加 `github_handle` 属性。”

“我们需要在 `User` 类中增加 `linkedin_url` 属性。”

“我们需要在 `User` 类中增加 `facebook_id` 属性。”

“我们需要在 `User` 类中增加 `instagram_id` 属性。”

“我们需要在 `User` 类中增加 `tiktok_id` 属性。”

“我们需要在 `User` 类中增加 `phone_number` 属性。”

“我们需要在 `User` 类中增加 `address` 属性。”

“我们需要在 `User` 类中增加 `city` 属性。”

“我们需要在 `User` 类中增加 `state` 属性。”

“我们需要在 `User` 类中增加 `postal_code` 属性。”

“我们需要在 `User` 类中增加 `country` 属性。”

“我们需要在 `User` 类中增加 `birthday` 属性。”

“我们需要在 `User` 类中增加 `gender` 属性。”

“我们需要在 `User` 类中增加 `preferences` 属性。”

“我们需要在 `User` 类中增加 `notification_settings` 属性。”

“我们需要在 `User` 类中增加 `privacy_settings` 属性。”

“我们需要在 `User` 类中增加 `security_settings` 属性。”

“我们需要在 `User` 类中增加 `integration_settings` 属性。”

“我们需要在 `User` 类中增加 `api_keys` 属性。”

“我们需要在 `User` 类中增加 `webhooks` 属性。”

“我们需要在 `User` 类中增加 `audit_logs` 属性。”

“我们需要在 `User` 类中增加 `activity_logs` 属性。”

“我们需要在 `User` 类中增加 `features` 属性。”

“我们需要在 `User` 类中增加 `flags` 属性。”

“我们需要在 `User` 类中增加 `roles` 属性。”

“我们需要在 `User` 类中增加 `groups` 属性。”

“我们需要在 `User` 类中增加 `stats` 属性。”

“我们需要在 `User` 类中增加 `metrics` 属性。”

“我们需要在 `User` 类中增加 `analytics` 属性。”

“我们需要在 `User` 类中增加 `reports` 属性。”

“我们需要在 `User` 类中增加 `alerts` 属性。”

“我们需要在 `User` 类中增加 `tasks` 属性。”

“我们需要在 `User` 类中增加 `projects` 属性。”

“我们需要在 `User` 类中增加 `documents` 属性。”

“我们需要在 `User` 类中增加 `messages` 属性。”

“我们需要在 `User` 类中增加 `comments` 属性。”

“我们需要在 `User` 类中增加 `posts` 属性。”

“我们需要在 `User` 类中增加 `files` 属性。”

“我们需要在 `User` 类中增加 `media` 属性。”

“我们需要在 `User` 类中增加 `orders` 属性。”

“我们需要在 `User` 类中增加 `payments` 属性。”

“我们需要在 `User` 类中增加 `subscriptions` 属性。”

“我们需要在 `User` 类中增加 `invoices` 属性。”

“我们需要在 `User` 类中增加 `discounts` 属性。”

“我们需要在 `User` 类中增加 `coupons` 属性。”

“我们需要在 `User` 类中增加 `refunds` 属性。”

“我们需要在 `User` 类中增加 `reviews` 属性。”

“我们需要在 `User` 类中增加 `ratings` 属性。”

“我们需要在 `User` 类中增加 `favorites` 属性。”

“我们需要在 `User` 类中增加 `shares` 属性。”

“我们需要在 `User` 类中增加 `follows` 属性。”

“我们需要在 `User` 类中增加 `followers` 属性。”

“我们需要在 `User` 类中增加 `blocks` 属性。”

“我们需要在 `User` 类中增加 `memberships` 属性。”

“我们需要在 `User` 类中增加 `admins` 属性。”

“我们需要在 `User` 类中增加 `moderators` 属性。”

“我们需要在 `User` 类中增加 `users` 属性。”

“我们需要在 `User` 类中增加 `organizations` 属性。”

“我们需要在 `User` 类中增加 `teams` 属性。”

“我们需要在 `User` 类中增加 `projects` 属性。”

“我们需要在 `User` 类中增加 `tasks` 属性。”

“我们需要在 `User` 类中增加 `issues` 属性。”

“我们需要在 `User` 类中增加 `requests` 属性。”

“我们需要在 `User` 类中增加 `commits` 属性。”

“我们需要在 `User` 类中增加 `branches` 属性。”

“我们需要在 `User` 类中增加 `tags` 属性。”

“我们需要在 `User` 类中增加 `releases` 属性。”

“我们需要在 `User` 类中增加 `environments` 属性。”

“我们需要在 `User` 类中增加 `templates` 属性。”

“我们需要在 `User` 类中增加 `configs` 属性。”

“我们需要在 `User` 类中增加 `scripts` 属性。”

“我们需要在 `User` 类中增加 `logs` 属性。”



“我们需要在 `User` 类中增加 `metrics` 属性。”

“我们需要在 `User` 类中增加 `alerts` 属性。”

“我们需要在 `User` 类中增加 `jobs` 属性。”

“我们需要在 `User` 类中增加 `queues` 属性。”

“我们需要在 `User` 类中增加 `caches` 属性。”

“我们需要在 `User` 类中增加 `databases` 属性。”

“我们需要在 `User` 类中增加 `servers` 属性。”

“我们需要在 `User` 类中增加 `containers` 属性。”

“我们需要在 `User` 类中增加 `clusters` 属性。”

“我们需要在 `User` 类中增加 `networks` 属性。”

“我们需要在 `User` 类中增加 `security` 属性。”

“我们需要在 `User` 类中增加 `identity` 属性。”

“我们需要在 `User` 类中增加 `auth` 属性。”

“我们需要在 `User` 类中增加 `storage` 属性。”

“我们需要在 `User` 类中增加 `compute` 属性。”

“我们需要在 `User` 类中增加 `search` 属性。”

“我们需要在 `User` 类中增加 `analytics` 属性。”

“我们需要在 `User` 类中增加 `ai` 属性。”

“我们需要在 `User` 类中增加 `ml` 属性。”

“我们需要在 `User` 类中增加 `data` 属性。”

“我们需要在 `User` 类中增加 `blockchain` 属性。”

“我们需要在 `User` 类中增加 `iot` 属性。”

“我们需要在 `User` 类中增加 `edge` 属性。”

“我们需要在 `User` 类中增加 `mobile` 属性。”

“我们需要在 `User` 类中增加 `web` 属性。”

“我们需要在 `User` 类中增加 `cloud` 属性。”

“我们需要在 `User` 类中增加 `enterprise` 属性。”

“我们需要在 `User` 类中增加 `consumer` 属性。”

“我们需要在 `User` 类中增加 `finance` 属性。”

“我们需要在 `User` 类中增加 `health` 属性。”

“我们需要在 `User` 类中增加 `education` 属性。”

“我们需要在 `User` 类中增加 `social` 属性。”

“我们需要在 `User` 类中增加 `entertainment` 属性。”

“我们需要在 `User` 类中增加 `gaming` 属性。”

“我们需要在 `User` 类中增加 `ecommerce` 属性。”

“我们需要在 `User` 类中增加 `marketing` 属性。”

“我们需要在 `User` 类中增加 `sales` 属性。”

“我们需要在 `User` 类中增加 `support` 属性。”

“我们需要在 `User` 类中增加 `operations` 属性。”

“我们需要在 `User` 类中增加 `hr` 属性。”

“我们需要在 `User` 类中增加 `legal` 属性。”

“我们需要在 `User` 类中增加 `finance` 属性。”

“我们需要在 `User` 类中增加 `strategy` 属性。”

“我们需要在 `User` 类中增加 `innovation` 属性。”

“我们需要在 `User` 类中增加 `product` 属性。”

“我们需要在 `User` 类中增加 `service` 属性。”

“我们需要在 `User` 类中增加 `design` 属性。”

“我们需要在 `User` 类中增加 `engineering` 属性。”

“我们需要在 `User` 类中增加 `technology` 属性。”

“我们需要在 `User` 类中增加 `data` 属性。”

“我们需要在 `User` 类中增加 `science` 属性。”

“我们需要在 `User` 类中增加 `ai` 属性。”

“我们需要在 `User` 类中增加 `ml` 属性。”

“我们需要在 `User` 类中增加 `security` 属性。”

“我们需要在 `User` 类中增加 `privacy` 属性。”

“我们需要在 `User` 类中增加 `ethics` 属性。”

“我们需要在 `User` 类中增加 `sustainability` 属性。”

Why am about throwing exceptions in a constructor? This in itself is a debate that's gone on for a long time, one that polarises the audience firmly into the yes and no camps. It's also something that I will deal with properly at length in the chapter entitled Instantiophobia but for now, I shall just bring up the point that you can't test a constructor properly. There's no return value. It can't be mocked. There are better ways of achieving our desired outcome, and I'll get to those in due course.

Back to our original problem of getting valid values into our object at the point of instantiation. The trick here, the way to tighten things up and prevent the kind of data insecurity that comes with a loosely typed language is to use the type hinting features that the language provides with us. With PHP developers have not been given type hinting on scalar variable, not at least, which gives us something of a problem. Not that much of a problem - let's create validator objects.

```php
public function __construct(StringValidator $username, EmailValidator $email)
{
  $this->username = $username->getValue();
  $this->email = $email->getValue();
}
```

That's a little better. Our `User` class is now delegating the validation process to dedicated objects, ones that we can explicitly type-hint for the constructor's method signature. Through delegation, we're offloading the responsibility for ensuring that the values we need are indeed valid. Additionally, through encapsulation we're saying "Hey, I don't need to see your internals to determine whether you're doing your job, just let me invoke your public interface so that I can get the values I need." In the meantime, let's hope that validators are properly unit-tested.

Moving on though, the thing that's going to let your PHP brilliance shine is the way that you seemingly your mysterious developers crystal ball and so, in two, three or six months, someone from the business team is going to wander up to your desk and say:“We need in the `User` class to add `phone_number` property.”

“We need in the `User` class to add `address` property.”

“We need in the `User` class to add `city` property.”

“We need in the `User` class to add `state` property.”

“We need in the `User` class to add `postal_code` property.”

“We need in the `User` class to add `country` property.”

“We need in the `User` class to add `birthday` property.”

“We need in the `User` class to add `gender` property.”

“We need in the `User` class to add `preferences` property.”

“We need in the `User` class to add `notification_settings` property.”

“We need in the `User` class to add `privacy_settings` property.”

“We need in the `User` class to add `security_settings` property.”

“We need in the `User` class to add `integration_settings` property.”

“We need in the `User` class to add `api_keys` property.”

“We need in the `User` class to add `webhooks` property.”

“We need in the `User` class to add `audit_logs` property.”

“We need in the `User` class to add `activity_logs` property.”

“We need in the `User` class to add `features` property.”

“We need in the `User` class to add `flags` property.”

“We need in the `User` class to add `roles` property.”

“We need in the `User` class to add `groups` property.”

“We need in the `User` class to add `stats` property.”

“We need in the `User` class to add `metrics` property.”

“We need in the `User` class to add `analytics` property.”

“We need in the `User` class to add `reports` property.”

“We need in the `User` class to add `alerts` property.”

“We need in the `User` class to add `tasks` property.”

“We need in the `User` class to add `projects` property.”

“We need in the `User` class to add `documents` property.”

“We need in the `User` class to add `messages` property.”

“We need in the `User` class to add `comments` property.”

“We need in the `User` class to add `posts` property.”

“We need in the `User` class to add `files` property.”

“We need in the `User` class to add `media` property.”

“We need in the `User` class to add `orders` property.”

“We need in the `User` class to add `payments` property.”

“We need in the `User` class to add `subscriptions` property.”

“We need in the `User` class to add `invoices` property.”

“We need in the `User` class to add `discounts` property.”

“We need in the `User` class to add `coupons` property.”

“We need in the `User` class to add `refunds` property.”

“We need in the `User` class to add `reviews` property.”

“We need in the `User` class to add `ratings` property.”

“We need in the `User` class to add `favorites` property.”

“We need in the `User` class to add `shares` property.”

“We need in the `User` class to add `follows` property.”

“We need in the `User` class to add `followers` property.”

“We need in the `User` class to add `blocks` property.”

“We need in the `User` class to add `memberships` property.”

“We need in the `User` class to add `admins` property.”

“We need in the `User` class to add `moderators` property.”

“We need in the `User` class to add `users` property.”

“We need in the `User` class to add `organizations` property.”

“We need in the `User` class to add `teams` property.”

“We need in the `User` class to add `projects` property.”

“We need in the `User` class to add `tasks` property.”

“We need in the `User` class to add `issues` property.”

“We need in the `User` class to add `requests` property.”

“We need in the `User` class to add `commits` property.”

“We need in the `User` class to add `branches` property.”

“We need in the `User` class to add `tags` property.”

“We need in the `User` class to add `releases` property.”

“We need in the `User` class to add `environments` property.”

“We need in the `User` class to add `templates` property.”

“We need in the `User` class to add `configs` property.”

“We need in the `User` class to add `scripts` property.”

“We need in the `User` class to add `logs` property.”

“We need in the `User` class to add `metrics` property.”



“We need in the `User` class to add `alerts` property.”

“We need in the `User` class to add `jobs` property.”

“We need in the `User` class to add `queues` property.”

“We need in the `User` class to add `caches` property.”

“We need in the `User` class to add `databases` property.”

“We need in the `User` class to add `servers` property.”

“We need in the `User` class to add `containers` property.”

“We need in the `User` class to add `clusters` property.”

“We need in the `User` class to add `networks` property.”

“We need in the `User` class to add `security` property.”

“We need in the `User` class to add `identity` property.”

“We need in the `User` class to add `auth` property.”

“We need in the `User` class to add `storage` property.”

“We need in the `User` class to add `compute` property.”

“We need in the `User` class to add `search` property.”

“We need in the `User` class to add `analytics` property.”

“We need in the `User` class to add `ai` property.”

“We need in the `User` class to add `ml` property.”

“We need in the `User` class to add `data` property.”

“We need in the `User` class to add `blockchain` property.”

“We need in the `User` class to add `iot` property.”

“We need in the `User` class to add `edge` property.”

“We need in the `User` class to add `mobile` property.”

“We need in the `User` class to add `web` property.”

“We need in the `User` class to add `cloud` property.”

“We need in the `User` class to add `enterprise` property.”

“We need in the `User` class to add `consumer` property.”

“We need in the `User` class to add `finance` property.”

“We need in the `User` class to add `health` property.”

“We need in the `User` class to add `education` property.”

“We need in the `User` class to add `social` property.”

“We need in the `User` class to add `entertainment` property.”

“We need in the `User` class to add `gaming` property.”

“We need in the `User` class to add `ecommerce` property.”

“We need in the `User` class to add `marketing` property.”

“We need in the `User` class to add `sales` property.”

“We need in the `User` class to add `support` property.”

“We need in the `User` class to add `operations` property.”

“We need in the `User` class to add `hr` property.”

“We need in the `User` class to add `legal` property.”

“We need in the `User` class to add `finance` property.”

“We need in the `User` class to add `strategy` property.”

“We need in the `User` class to add `innovation` property.”

“We need in the `User` class to add `product` property.”

“We need in the `User` class to add `service` property.”

“We need in the `User` class to add `design` property.”

“We need in the `User` class to add `engineering` property.”

“We need in the `User` class to add `technology` property.”

“We need in the `User` class to add `data` property.”

“We need in the `User` class to add `science` property.”

“We need in the `User` class to add `ai` property.”

“We need in the `User` class to add `ml` property.”

“We need in the `User` class to add `security` property.”

“We need in the `User` class to add `privacy` property.”

“We need in the `User` class to add `ethics` property.”

“We need in the `User` class to add `sustainability` property.”

## 封装我们的思想

这当然没问题。至少在我们达到那种同事开始从变量中持有的类名来实例化对象的程度之前。你知道我指的是什么：动态类解析。

```
// 危险的代码
$className = $propertyName . 'Validator';
$validator = new $className($propertyValue);
return $validator;
```

这类操作只应该发生在工厂（无论是抽象工厂还是其他的）中，并且返回的对象必须符合一个清晰且易于理解的接口。如果它发生在“荒野”——即构成应用程序正常业务流程的代码中，那么坦率地说，你的代码已经出大问题了。游戏结束了，是时候开始着手重写了。

与其试图逃避它，不如说，我们不打算这样做。松解耦合和依赖注入的概念将在本书的后部分详细讨论。对使用 `new` 关键字产生过敏的想法也将在此讨论。不过，目前，我只想让你们默认这样一点：在我们的 `User` 类内部实例化验证器实例是一个严格禁止的场景。我让你们默认，是因为如果你已经是在读这本书的第二遍或更多遍，你已经知道为什么应该这样了。

看到了吧？我告诉过你的。北极熊！

那么，我们如何将验证器引入 `User` 类呢？有一种答案，当然是通过构造函数将其传递进来。我们的下一次重构正是如此做的。

```php
public function __construct(
    array $userData,
    UserDataValidator $udv
) {
    if (!$this->isValid($userData)) {
        throw new Exception(
            $udv->getErrorMessage(),
            $udv->getErrorCode()
        );
    }
    $this->userData = $userData;
}
```

## 封装我们的思想

看看我们做了什么！这里的建议是，针对 `$UserData` 数组的所有验证逻辑都很好地被封装在了 `UserValidator` 对象中。只要我们对这个验证器及其操作充满信任，就能以非常简洁的方式使用经过验证的数据初始化我们的 `User` 对象。此外，$UserData$ 结构的未来任何更改（你知道的，业务团队想要记录“喜爱的颜色”，下周就会变成“鞋码”）都不会导致我们现有的 `User` 类发生任何变化，这只能是好事，对吧？

尽管如此，我们还可以更进一步。我们可以将 `$UserData` 数组和 `UserValidator` 合并为一个对象。我们管它称为 `UserDataTransport` 对象，并修改代码如下：

```php
class User
{
  /**
   * @var UserDataTransport
   */
  private $userData;

  public function __construct(UserDataTransport $udt)
  {
    $this->userData = $udt;
  }
}
```

最后，我们得到了一个非常短小优雅的 `User` 类，它正确地在私有属性中持有验证过的用户属性，但这种方式不会让验证程序弄乱 `User` 类本身，而这些程序我们可能在其他地方也会。从 `User` 类的角度来看，它现在被有效数据正确初始化，因为我们也信任 `$udt` 实例在被传递之前已经正确地完成了它的工作。

你们中你们可能在想，我们在这里成就的仅仅是把本应该在 `User` 类中的方法移动到了其他地方，然后在上面套上了一个名为 `User` 的相当没用的壳。如果这就是我们旅程的终点，那么就是完全正确的。

但并不是旅程的终点。虽然我们确实正在接近最后的直道，但我们已经到了应该停顿一下、泡杯好茶并思考一下的地步。

## 封装我们的思想

如果你观察我们在这里所做的，可以将 `$udt` 实例看作一个种子、一个内核、一个单元，它仅仅代表了我们想要持久化到应用程序中需要实现的任何存储系统中的数据。我们到达了一个非常有趣的点。我们的可持久化数据现在被**封装**在一个离散的单元中，该单元与我们的模型类分离并被其消费。

这是我们在构建大规模应用程序时想要实现的关键设计目标。我们希望我们的模型类专注于表现得它们应该具有的模型类的行为。通过向模型类注入诸如数据传输对象等的方法，我们能够将模型层与处理数据持久化的实现细节解耦。

如果你对市面上的一个或多个 PHP 框架稍微熟悉，你可能会意识到它们在实现模型层持久化时所采取的许多多样化方法。在某些情况下，你被要求扩展框架提供的基础模型来实现应用模型。在另一些情况下，你被要求混合你的模型类设计，以便向装饰器和适配器暴露它们管理的属性。无论哪种情况，你都被要求将你的模型设计适应到它们的持久化机制中，在此过程中，你被预期放弃至少一个或另一个健康的设计原则。在我看来，这不仅很糟糕，而且简直不可理喻。

通过向你的模型类注入必需的数据内核，你让自己从这种破坏原则的约束中解放出来。你的模型可以正确地封装它们本应承担的业务逻辑，而存储解决方案的反复变化会立即且正确地被归到模型层之外，并到它们真正所属的持久化层。

我们的 `User` 类还剩下什么？我们仍然处于需要提供访问数据手段这一点。我们的起点是提供 getter 和 setter，它们构成了实体。到目前为止，我们唯一的用例是将数据取出来，我将访问修饰符设置为私有。

## 封装我们的思想

```php
class User {
    /**
     * **var UserDataTransport
     */
    private $userData;

    public function __construct(UserDataTransport $udt) {
        $this->userData = $udt;
    }

    private function getDataTransport() {
        return $this->userData;
    }

    public function getUsername() {
        return $this->userData->getUsername();
    }

    public function getEmail() {
        return $this->userData->getEmail();
    }

    public function setEmail($email) {
        try {
            $this->userData->setEmail($email);
            return $this;
        } catch (DataTransportException $e) {
            $msg = $e->getMessage();
            $code = $e->getCode();
            throw new ModelException($msg, $code);
        }
    }
}
```

这里有几点需要注意。首先，由于我们目前没有获取数据的用例，我将 `getDataTransport()` 方法的访问修饰符设置为私有，以供构成公共接口的 getter 使用。此外，我们这里只有一个 setter 方法，即针对 email 属性的。除非你的应用程序支持用户更改用户名，否则用户名属性的 setter 可能是多余的。

## 封装我们的思想

现在，让我们把注意力转向执行者，即应用程序的处理器。我们已经讨论过如何通过实现一个 `PasswordManager` 类，将密码处理过程从我们的 `User` 类中分离出来。为了开启这一路线，让我们来看看这在代码中是如何实现的。

```php
class PasswordManager {
    const PASSWORD_MANAGER_COST = 10;

    public function getPasswordHash($rawPassword)
    {
        $options = array(
            'cost' => self::PASSWORD_MANAGER_COST
        );
        return password_hash($rawPassword, PASSWORD_BCRYPT, $options);
    }

    public function verifyPassword($rawPassword, $hashedPassword)
    {
        return password_verify($rawPassword, $hashedPassword);
    }
}
```

正如你所看到的，我们的 `PasswordManager` 类的意图表达非常明确。即使没有代码中本应包含的文档块（docblocks），你也能非常清晰地遵循它的执行路径。我们成功地将确保使用最佳密码处理方法的两个核心方法封装在一个目的单一的单元单元中。从这里开始，实现 PHP 提供的其他 `password_hash()` 相关函数以完成该类定义的实用性只需简单一步。

> 顺便提一下，如果你从这一章没有学到任何东西，把这个 `PasswordManager` 类复制并粘贴到你自己的应用程序中也比什么都好。如果你还没有使用语言提供的 `password_hash()` 函数，你应该开始使用。我稍后会解释原因，因为这个主题在书中“实践”部分会有专门的章节介绍。

封装我们的思想。

遵循同样的原则，我们没有理由不回到早早消除的 `$balance` 属性，并编写一个 `BalanceManager` 类，这个类封装了我们处理用户余额所需的所有知识。

为了指定多个账单地址和送货地址。这难道不是非常适合提供一个 `AddressManager` 类吗？

# 总结

我们走了一段长而曲折的道路才到达这里。在开始，我指出纯粹意义上的“封装”不等同于“信息隐藏”。然后我要求你将这两者视为同一种事物。我非常希望，你并不是把我当成某个疯子，而是能理解我的意图——每个完成这一章的人，无论其起始知识如何，在结束时都有共同的理解：当我们在日常工作中谈论封装时，我们实际上指的是这两个捆绑为一的概念。

共同的术语、共同的语言，是协作软件开发中的一个重要因素。我希望实现的只是这一理想中的一小部分。

在翻阅这些章节的过程中，我探索了一个相当典型（尽管极其瘦小）的模型类的演变，在此过程中，我似乎过度关注了将单个职责拆分为更小的、离散的代码包。之所以这样做也有一些辅助性的动机，我在此承认这一点。



一方面，把培训中的类看作孤岛，我们可以欢快地向里面倾倒工具方法，这种习惯我发自内心认为我们都应该抛弃。我经常会遇到某些如巨兽般的类定义，无论从方法的数量还是单个方法的大小来看都是如此。这表明要么是最初的设计糟糕，要么是构建期间的技术领导力匮乏。开发团队中的初级成员遵循先前的示例，简单地在现有类中添加新方法，而不是迈出更大的一步，为特定的工作流创建专门的类。这并不是同事的错，而是负责开发人员的错，即那些本该引导架构的人，那些本该负责指导团队的人。

另一方面，我也为我们在学到“单一职责原则”（`Single Responsibility Principle`）时将涵盖的话题打下了基础。当我们到达那里时，你会发现自己已经准备好了。

尽管如此，我们现在都处于一个对封装进行扩展考虑的阶段，相对于 PHP 世界中汹涌的大众来说是这种扩展。欢迎加入俱乐部。希望你在这里过得愉快。

我之前提到过，有方法从外部访问一个对象的私有属性。其中一种方法与封装主题相关，因此我在这里提到它。你们中的许多人已经知道了，但我还是会涵盖它，因为我认为每个人意识到这一点是合适的。

情况是这样的：当你有同一个类的两个对象实例时，其中一个实例可以获取并设置另一个实例的私有属性，就像它们是公共属性一样。基本前提是，如果一个对象对其内部工作原理非常熟悉，那么它对同类其他实例的内部工作原理也同样熟悉。

正如人们所说，当你这样考虑时它是合理的，代码胜过万言，所以这里是此的一个实际示例。

```php
class Point
{
    // 声明为私有的属性
    private $latitude;
    private $longitude;

    public function getDistanceTo(Point $p)
    {
        // 访问传入的 Point 实例的
        // 私有属性，//就像它们被声明为公共一样
        $remoteLat = $p->latitude;
        $remoteLong = $p->longitude;

        // 执行距离计算
        ...
        return $result;
    }
}
```

封装我们的思想。50

就是这样。原始的 `Point` 实例可以将传入实例的私有属性视为公共属性，因为它们都是同一个类的实例。这在面向面向对象的语言中并不罕见，但也很少作为一种特性被强调。

# 代码，但在抽象意义上。

如果你足够幸运受过计算机科学的正规教育，那么你极有可能以惊人的次数遇到过“抽象”（`Abstraction`）这个词。计算机科学的学术方法会结合数据处理和流/过程控制来讨论抽象。

然而，如果你是作为一个天真的开发者（`naive developer`）到达这里的，那么你对“抽象”的理解可能只是从 PHP 手册、PHP 编程书籍以及那些我似乎一直在抱怨的讨厌的在线教程中获得的。这没关系。重要的是，从面向对象的角度记住，当我们谈论抽象时，我们谈论的是数据抽象和控制抽象。

> 过去，有人创作艺术，但没有受过正规训练或艺术教育的人被称为“天真艺术家”（`Naive Artist`）。他们创作的作品被称为“天真艺术”（`Naive Art`）。这并不是为了贬义，只是对未受过正规训练的人创作的艺术的一种分类形式。我在这里借用“天真”一词是指在自己的专业领域没有接受过正规训练的人。在我们的案例中，我特指用它来代表我们这些没有计算机科学学位的人。作为参考，在这方面我也是一个天真的开发者。

还记得我们之前讨论过的 Joe 吗？那个新加入我们团队的平易近人的家伙。嗯，他又回来了，并且似乎非常乐意帮助我们探索“抽象”。

虽然封装是一个我们很少思考的话题，但抽象是一个我们难以逃避的话题。对于任何接触过 PHP 领域中充斥着的各种开源 MVC 框架的人来说，这一点尤为真实。粗略估计，我认为这基本上就是我们所有人。

代码，但在抽象意义上的代码。

Joe 确实是那个帮派的一员。当我们请他解释一下什么是抽象时，他的初始反应是告诉我们这完全关乎代码重用以及它如何让我们避免重复。我们很难指责他的所言，这确实是对该问题最常见的回答之一，而且十分合理，因为这通常被描绘成抽象本身的主要益处之一。但这个想法是从哪里来的呢？如果你花时间阅读任意数量关于 PHP 类抽象的文章，你会发现，主张通过抽象实现代码重用的人和不主张此点的人之间几乎是平分的。它甚至可能稍微更倾向于“不主张”阵营。请理解，这完全基于我个人的感受，而不是基于任何定性或实证研究。

在开始挑选关于抽象是什么的各种观点之前，我将利用一个熟悉得令人不过的代码陈词滥调，在我们开始之前先写几行代码。

```php
abstract class Animal
{
    private $strength = 1;

    abstract public function say();

    public function isHungry() {
        return $this->strength < 2;
    }

    public function eat(Food $food) {
        $this->strength += $food->getStrengthValue();
    }
}

class Cat extends Animal {
    public function say() {
        print "Meow";
    }
}
```

不过我不写狗的例子了——我们对这个例子已经太熟悉了。上面定义了一个名为 `Animal` 的类，并将其标记为抽象类，它是抽象的。在 PHP 中，这防止了我们直接创建 `Animal` 类的新实例。要使用这段代码，我们必须创建自这个抽象父类的子类。在这个抽象父类中，我们定义了一个私有属性（`$strength`）、两个公共方法（`isHungry()` 和 `eat()`）以及最后一个抽象公共方法（`say()`）。通过将 `say()` 方法标记为抽象，我们是在声明任何继承此抽象父类的子类都必须实现它们自己的 `say()` 方法版本。这正是我们在 `Cat` 类中作为继承父类 `Animal` 的子类所做的事情。

你已经知道这些了，对吧？只是确认一下。

回到我们最初的问题，这种“抽象促进代码重用以避免重复”的想法到底是从哪里来的？试图确定一个单一来源可能是一种愚蠢行为，甚至可以说是推测。虽然我们可以使用所有喜爱的搜索引擎来定位在线上推销这一理念的文章，但我认为主要的罪魁祸首就在我们眼底下，而且我之前就发现了它。

如果我们确实都接触过 PHP 的许多 MVC 类似框架实现中的至少一个，那么我们都潜移默化地接触了“抽象即代码重用”的观点。当你为了扩展基类模型类来实现你的 `User` 模型、`Blog` 模型或 `Product` 模型时，你很可能正是这样做是为了利用父类中某些通用的、理论上相关的代码。它可能没有被直接标记为代码重用，但在推广这种做法时，有着非常强烈的暗示。该领域的早期参与者这样做了这一点，例如 `phpCake` 和 `CodeIgniter` 等实现，这种做法在一些更现代的框架中（包括 `Phalcon` 和 `Laravel` 在内）仍然被推崇。当文档告诉你要扩展基类模型时，是因为基类模型类已经填充了许多工具方法。这些方法将完成从与应用程序数据库接口到提供模型属性便捷访问以及其间一切的工作。

问题在于，这些框架简直太该死的好用！

尽管如此，这并不能免除它们在底层发生的对良好编程实践的严重违背。如果你还没有查看过代码，现在看一眼你当前或最近的基于 MVC 框架的应用程序。如果你通过扩展框架的基模型来实现模型或控制器，请查看基类，并考虑这些类与你随后在子类中创建的截然不同的实体有什么关系。

哈！我听到你反驳道，但我们不仅仅是在提供框架对模型定义的子类特化吗？

从表面上看也许是。但如果我们认同我们的对象要么是知者（`knowers`）要么是执行者（`doers`），而不能兼者，那么这里显然存在这种情况：框架要求我们创建对象来代表我们的 `User` 模型，而这个对象还必须携带触发数据库查询和其他其他无关操作的方法。这并不是我们作为优秀开发者应该推广的想法。

框架将一直存在，至少还会持续一段时间。虽然目前我们许多人可能仍旧与单体架构共存。尽管如此，当我把注意力转向上面简要提到的某件事时：工具方法（`Utility methods`），或者用我倾向的称呼方式：便利方法（`convenience methods`）。

正是在这一点，我应该引入一些额外的参与者。“不要重复自己”（`DRY`）原则和 Kent Beck 的“一次且仅一次”（`OAOO`）——这两个观点正确地指出了代码重复是禁忌，会导致维护噩梦和一大堆 Bug。其基本前提是，如果你在多个位置有相同的代码，并且当你通过发现 Bug 或由于更改而确定该代码需要更改时，那么极有可能必要的更改无法正确或有效地应用到该代码段出现的每一个位置。如果重复代码的出现处之间失去了同步，那么自然而然的结果是它们运行的方式将产生分歧。被遗漏的拷贝或副本现在将处于错误状态。

自然，让我们确保相关的代码段只出现一次且位于单个位置对我们来说完全合理。当我们这样做时，我们清楚地知道去哪里看，并且完全有信心只需要在一个地方进行更改。

然而，就我们的抽象的话题而言，当我们看到一个类中的某个特定方法如果位于另一个类中也会很有用时，问题就出现了。正如我之前提到的，我们通常是一群懒人，有时满足我们懒惰倾向的最好方法就是将那个实用的方法向上移动到父类中，两个类都继承该父类。如果方法在父类中，那么两个子类都可以使用。

这当然是我回到对框架中基模型类考虑的地方。如果你被要求扩展基模型类来创建你自己的模型，那么基模型很可能预加载了便利方法。我把它们称为便利方法（我绝对不孤单），因为它们是为我们做事的方法，与结果类的预期本质完全无关，并且方便地放置在触手可及的地方。

> `DRY` 原则述为：“系统中的每一部分知识必须有一个唯一的、无歧的、权威的表示”

因此，重复代码是坏的，代码重用是。

这里重要的注意的是，有许多不同的方法可以避免代码重复并促进代码重用。通过父类（无论是否抽象）来实现代码重用只是可用选项中最糟糕的。有更合适的替代方案，并且仍然能让我们遵循 `DRY` 原则。你将在处理委托多态、组合、特性的（`traits`）和闭包（`closures`）问题时看到这些问题的详细讨论。在此期间，如果你遇到文章、教程、博客文章甚至另一位开发者告诉你抽象促进代码重用，千万别上当。

代码，但在抽象意义上的代码。

抽象促进了代码复用，就像每天上班会促进人们去进行犯罪作案一样。我觉得这个说法可能需要稍微解释一下，所以让我们先把注意力回到 Joe 身上，他是个很讨喜的人。

Joe 对工作也非常投入，正如所有新员工应该做的那样。每天，他都会来到办公室，敲几行代码，并将它们推送到主仓库（`master repo`），然后回家吃晚餐。他之所以他的原因之一是他希望在月底领到工资，这是理所当然的。然而，当他拿到工资时，他会取出所有的钱，用劳动的报酬买一把枪，然后去抢抢劫尽可能多的超市吗？

无论他有多么讨喜，人们无疑希望他不会这样做。上班并完成我们获得报酬的工作，并不意味着我们会把工资花在买枪和抢劫上。上班和工作可能会让我们有机会去做这种事（前提是我们有这种倾向的话），但这通常不是一个礼貌社会所积极鼓励的想法。与此类似，抽象可能为我们提供了实现代码复用的可能性，但并不意味着我们应该这样做这样做。它绝不会以任何方式促进这种观念或鼓励这种行为。

事实上，将抽象和继承作为代码复用的机制是一种广为人知的“代码异味”（`code smell`）。当框架要求你扩展一个实际上是有用函数库时，这就是它们对你的项目所做的。它们让你的代码产生了异味。

请记住，我们不再将抽象视为复用现有代码和避免重复的手段。在接下来的章节中，我们将看到如何创建体现复用性的代码块，同时允许停止污染我们的父类。当我使用“污染”这个词时，它是否给了你提示这指的是哪里？

让我们现在开始通往抽象启蒙的之旅。为了做到这一点，我们将首先看看类定义到底是什么，然后开始考虑这个简单的概念如何应用到我们的类抽象中。

在今天几乎所有的语言中，无论是强类型还是否，我们都拥有这样一种概念：我们可以使用特定类型的变量来存储应用程序的数据。正如你已经痛苦地察觉到的那样，PHP 并不是那些类型语言之一。

代码，但在抽象意义上的代码。

我们不仅免去了初始化新变量时声明类型的义务，而且我们（实际上 PHP 解释器）可以随心所欲地在变量应用的类型之间进行切换。

我确定你知道我在说什么，但为了正确设置，让我们考虑一个用代码表示的 PHP 标量类型（`scalar types`）示例列表。

```
$integer = 5;
$float = 7.25;
$boolean = true;
$string = "Hello Joe!";
```

这四行清晰地展示了 PHP 中四种数据类型的概念。这并不意外，我们可以通过包含一些复杂数据类型来增加这个列表，就像我们开始包含数组和关联数组一样。

```
// 数字索引数组
$sequence = [1,2,4,8,16,32];
```

```php
// 关联数组
$person = [
  'name' => 'James',
  'age' => 39,
  'gender' => 'male'
];
```

作为封装，我不认为你最近在日常工作中在这些考虑上花费太多精力。尽管如此，我希望你现在这样做。请考虑这个最简单的想法：你已经习惯了处理这些类型的数据，以至于在使用它们时甚至不需要考虑类型。你需要执行浮点数运算，你会选择 `float`，在此过程中，你很清楚它比使用 `string` 更适合你的需求。你有一个需要表示简单真/假条件的情况？噢，那将是一个 `boolean`。

我在这里想要表达的观点是，无论我们处理的是整数、布尔值还是简单数组，只要我们知道正在处理的变量类型，我们也会知道该类型的特定属性和特征

代码，但在抽象意义上的代码。

并能够利用这些知识来恰当地操作变量。我们已经习惯了它们的工作方式。

这里有另一个说明这一观点的例子。

```php
// 将一个简单数组声明为人员队列
$queue = ['James', 'Mary', 'Paul'];
```

```php
// 获取队列中的下一个人
$nextLine = array_shift($queue);
```

作为开发者，我们知道这段代码之所以有效，恰恰是因为我们理解 PHP 数组的行为。同样，我们知道不能向整数值添加或取走元素，因为整数值不是那样工作的。列表或队列之类的特性存在于简单数组中，而不是整数中。整数就是简单的整数，到此结束。它们的行为对我们是为人知的。

我们对 PHP 数据类型及其工作方式的知识，支撑了使用哪种数据类型来编写特定问题解决方案的决策。

那么为什么不进一步推进这个想法，并扩展它（此处并非双关）来涵盖我们代码库中类定义的创建呢？当我们作为开发者开始编写某种描述的类时，我希望留在你脑海中的想法是：我们正在创建一个新的数据类型。我们之所以这样做，正是因为我们对 PHP 的现有知识告诉我们，这种语言已经没有我们需要的正确数据类型。因此，我们需要构建自己的类型。

为了支持这个观点，我将回到第一个数据类型列表并添加几个。

代码，但在抽象意义上的代码。

```php
$integer = (int) 5;
$float = (float) 3.14;
$boolean = true;
$string = "Hello World";
$vehicle = new Car();
$person = new Person();
```

希望现在，你可以看到我在讨论在应用程序中定义类和对象时采用的思路。在几乎每一个使用对象作为存储为对象属性的数据存储的情况下，理论上我们可以使用关联数组。就像这样：

```php
$person = array(
  'name' => 'Joe',
  'age' => 26,
  'gender' => 'male'
);
```

可怜的 Joe！我确定你最近在日常工作中在这些考虑上花费了很多精力。尽管如此，我希望你现在这样做。请考虑这个最简单的想法：你已经习惯了处理这些类型的数据，以至于在使用它们时甚至不需要考虑类型。你需要执行浮点数运算，你会选择 `float`，在此过程中，你很清楚它比使用 `string` 更适合你的需求。你有一个需要表示简单真/假条件的情况？噢，那将是一个 `boolean`。

我在这里想要表达的观点是，无论我们处理的是整数、布尔值还是简单数组，只要我们知道正在处理的变量类型，我们也会知道该类型的特定属性和特征并能够利用这些知识来恰当地操作变量。我们已经习惯了它们的工作方式。

这里有另一个说明这一观点的例子。

```php
// 将一个简单数组声明为人员队列
$queue = ['James', 'Mary', 'Paul'];
```

```php
// 获取队列中的下一个人
$nextLine = array_shift($queue);
```

作为开发者，我们知道这段代码之所以有效，恰恰是因为我们理解 PHP 数组的行为。同样，我们知道不能向整数值添加或取走元素，因为整数值不是那样工作的。列表或队列之类的特性存在于简单数组中，而不是整数中。整数就是简单的整数，到此结束。它们的行为对我们是为人知的。

我们对 PHP 数据类型及其工作方式的知识，支撑了使用哪种数据类型来编写特定问题解决方案的决策。

那么为什么不进一步推进这个想法，并扩展它（此处并非双关）来涵盖我们代码库中类定义的呢？当我们作为开发者开始编写某种描述的类时，我希望留在你脑海中的想法是：我们正在创建一个新的数据类型。我们之所以这样做，正是因为我们对 PHP 的现有知识告诉我们，这种语言已经没有我们需要的正确数据类型。因此，我们需要构建自己的类型。

为了支持这个观点，我将回到第一个数据类型列表并添加几个。

```php
$integer = (int) 5;
$float = (float) 3.14;
$boolean = true;
$string = "Hello World";
$vehicle = new Car();
$person = new Person();
```

希望现在，你可以看到我在讨论在应用程序中定义类和对象时采用的思路。在几乎每一个使用对象作为存储为对象属性的数据存储的情况下，理论上我们可以使用关联数组。就像这样：

```php
$person = array(
  'name' => 'Joe',
  'age' => 26,
  'gender' => 'male'
);
```



可怜的 Joe！我确定你最近在日常工作中在这些考虑上花费了很多精力。尽管如此，我希望你现在这样做。请考虑这个最简单的想法：你已经习惯了处理这些类型的数据，以至于在使用它们时甚至不需要考虑类型。你需要执行浮点数运算，你会选择 `float`，在此过程中，你很清楚它比使用 `string` 更适合你的需求。

代码，但在抽象意义上的代码。

在代码中实现这种新的数据类型，这样我们团队中的每位开发者都能读懂这段代码，并随后理解构成我们 `Person` 数据类型的属性和特征。

假设你读到了这本书的最后，你会注意到在接下来的章节中，我会多次提到“创建新数据类型”这个观点。这是我在尝试对这一观点进行正强化，而就我们目前而言，这个想法可能与你对抽象的既有认知背道而驰。

好了。现在既然我已经提醒了你正在读的是关于抽象的章节，你可能刚刚在想：“这关于数据类型的废话和抽象到底有什么关系？”

是吗？不是吗？也许你确实这么想了，也许你没有。目前可以确定的是，我完全还没有为抽象提供过任何有力的论据。你注意到这一点是完全正确的，但请放心，我正要谈到这个话题。

回想一下本章的开头以及那个被过度使用的代码段落：

```php
abstract class Animal {
    private $strength = 1;

    abstract public function say();

    public function isHungry() {
        return $this->strength < 2;
    }

    public function eat(Food $food) {
        $this->strength += $food->getStrengthValue();
    }
}

class Cat extends Animal {
    public function say() {
        print "Meow";
    }
}
```

代码，但在抽象意义上的代码。

62

如果我们不再使用那个 `Animal` 类作为我们认为需要的继承层次结构的根节点，不再将那个 `Animal` 类作为我们认为的层次结构其他部分共同需求的方法的仓库，而是将那个 `Animal` 类视为一种新数据类型的**不可变定义**呢？

如果我们的应用程序需要一个 `Animal` 数据类型，我们现在已经有了，并且是以完全易读的代码显式列出的。如果，我们我们这些良好的程序员能够通过大量使用 `docblocks` 对代码进行妥记录，理论上我们可以得到可以被视为 PHP 手册扩展的内容，至少从这个应用程序的角度来看是这样。团队的其他成员随后可以参考这段代码及其文档，不仅能从中学习，还能理解描述 `Animal` 数据类型行为的所有属性（属性）和特征（方法）。

我在上一段中提到了“不可变”（immutable）这个词，但由于我们是在 PHP 代码中创建这些新的数据类型，“不可变”这个术语最多只能是概念性的。我们甚至还没有提到继承和多态的话题，但尽管如此，我知道你们很优秀。你们懂 Bean（beans）。当涉及到从这个抽象父类创建子类时，你们知道开发者可以通过重写一个或多个父类方法来改变子实例表现出的行为。这会好事吗？答案无疑是否定的。尤其是当我们确实认同抽象父类定义了类型这一观点时。

让我们来看一个非常愚蠢的例子来帮助说明这一点。在另一个无限的平行宇宙中，PHP 的创建者们认为，允许开发者创建数组构造的自定义版本是一个好主意。他们非常明智，认为我们应该能够在 `php.ini` 中将第一个索引值设置为一个配置选项，从而允许应用程序构建者自己选择数组索引开始的数字。

结果是，在一个应用程序中，数字索引数组的第一个元素可以使用数字 7 来引用，导致代码看起来像：

```php
$myArray = array('first', 'second', 'third');
print $myArray[7];
// output is 'first'
```

在另一个应用程序中，首席架构师选择了起始索引‘42’，因为这与他们的“我爱道格拉斯·亚当斯”T 恤非常合拍。

你明白意思了。我在这里试图在你们的大脑侧面涂鸦的图像相对简单，也许部分是因为我画得很烂。事实是：如果我们最基础的数据类型的属性和特征在不同地方之间不同，我们又如何可能且合理地被构建构建健壮、安全且可靠的应用程序呢？这个问题当然是反问句，因为我们根本做不到。我们可能会被诱惑迁移到另一种语言，一种不会阴险地鼓励这种广泛的维护噩梦的语言。

因此，为什么我们不能对那些通过使用 `class` 关键字在代码中创建的自定义数据类型应用同样的严谨性呢？我想我们可以。我认为我们应该。事实上，我认为我们必须。

为了我们应用程序数据的安全和可靠，我们的数据类型（包括我们的对象）表现得一致并符合既定的规范是至关重要的。这意味着既适用于语言内置的既定类型，也适用于我们每当声明抽象基类时添加到语言中的类型。正如数组从一个 php 文件到另一个 php 文件的行为一致一样，`Animal` 类型的实例也应该从一个到另一个保持一致。

PHP 确实在某些方面帮助我们实现了这一点。每当你对类使用 `abstract` 关键字，并可选地对该类中的一个或多个方法使用，PHP 会对该抽象类的使用进行一些限制。我会简要介绍这些限制，以确保你知道我在说什么。

这些限制中的第一个显然是你不能直接从该类实例化对象，而必须使用子类。这一点非常准确，在制定这项限制时，我认为它有助于促进我们正在为一种新数据类型制定蓝图的想法。

代码，但在抽象意义上的代码。

78

第二个限制是，对于抽象类中任何也是抽象的方法，开发者被迫在其创建的任何子类中实现它们。单此一个概念就有助于加强抽象在使用上施加规则的观点。

此外，实现方法的可见性级别必须与抽象方法中声明的级别相同或限制更少。例如，如果抽象方法被声明为 `protected`，那么子类中的实现方法必须声明为 `protected`（相同）或 `public`（限制更少）。然而，子类中的实现方法不能声明为 `private`，因为这比抽象方法的限制更多。

此外，实现方法的签名也必须与父类抽象方法的签名匹配。这意味着它们应该具有相同的名称和输入参数类型。我在这里说，是因为实际上在实现方法中可以定义更长的输入参数列表，但我之所以强调这一点是为了在事实上正确。在我看来，在这样的实现方法能够拥有更长的输入参数列表会以一种微妙的方式破坏这种*不可变*数据类型的概念。

代码，但从抽象意义上来说。

当你创建一个抽象类时（当然，你现在这样做是为了为新的数据类型奠定蓝图），你实际上是在指定该类型的接口。你正在向整个世界宣告——或者至少在你的应用程序代码库的边界之内——宣告：这个新数据类型的消费者、协作者和客户端可以如何与它交互。当你为你的新数据类型提供公共方法时，你是在说：“看，当你有一个这个特定数据类型的变量时，你可以对它进行这些操作。你可以预期它以这种特定的方式运行。”就像数组、字符串和整数一样，你创建的新对象也应该是这样的。

通过继承，你可以让这一切变得非常一团糟，特别是当涉及到从方法调用返回的值时。至少目前，PHP 不允许你像 Java 那样在方法声明中指定返回类型。让我给你们看一段简短的 Java 代码来帮助说明这一点。

```java
abstract class Foo {
    public Bar getBarInstance() {
        return new Bar();
    }
}
```

第 3 行的方法声明通过在实际方法名之前指定返回类型，指示了该方法返回的值将是 `Bar` 类型的实例。

由于 PHP 并不依赖方法调用强制执行返回类型的能力，我们必须依靠自己和同事来遵循一种约定，即一种遵循我们在抽象父类中指定的接口的标准方法。当然，当抽象父类为该方法提供实现时，这一点很容易被传达。开发者可以从代码中看到调用此方法时的预期返回类型。

然而，缺失的是当抽象父类也定义了抽象方法时，缺失了返回类型的声明。例如下面这一个：

代码，但从抽象意义上来说。

```php
abstract public function say();
```

看着那行代码，显然没有任何东西能告诉我们，当我们从这个抽象类派生出子类并编写此方法的实现时，我们预期返回什么。这段代码的原始作者，即该类的设计者有权向使用此蓝图的开发者传达他的意图。作者应该，也应该使用 docblock（文档块）注释来指示返回类型，生成的代码可能像这样：

```php
/** method description
 * .. other docblock tags
 * @return AnimalSound
 */
abstract public function say();
```

当然，你应该为你创建的每个方法在 docblock 中提供 `@return` 标签，但我觉得在类似情况下，即方法声明本身未能指定返回类型时，这尤为重要。支持这一观点的约定是：缺失 `@return` 标签意味着返回类型是 `void`。既然如此，如果你正在编写抽象方法，只要预期的返回值是 `void` 的其他任何内容，你就应该在 docblock 中提供 `@return` 标签。

如果你漏掉了 docblock，并且子类派生类返回了一系列完全不同的类型，那是你的错。你这个坏人。

但如果你提供了适当的 docblock，而实现开发者忽略了它并选择返回他们喜欢的任何内容，那么那就是他们的错。在后一种情况下，是你能早点回家，而他们是那些留下来修复 bug 的人。这种方式提供接口的概念只是有助于传达对我们新数据类型属性和特征的彻底理解，但它是过程中一个至关重要的一部分。

这个想法允许我顺畅地过渡到讨论的最后部分：类型提示（type hinting）。我有理由相信你们都知道它是什么（线索就在名字里），但如果我们至少不触及它，我们对抽象的探索将是不完整的。

代码，但从抽象意义上来说。

类型提示是声明我们的代码接受哪些特定数据类型的实践。在大多数面向对象的情况下，我们会在方法签名中使用类型提示，告知客户端代码，如果它们想调用此方法，必须传递什么作为参数。这是一个例子。

```php
class Zoo
{
    private $animals = array();

    public function addAnimal(Animal $animal)
    {
        print "Welcome to the zoo, " . $animal->getName();
        $this->animals[] = $animal;
    }
}
```

没什么意外的。我们的 `addAnimal()` 方法声明要传递的参数必须是 `Animal` 类的实例。如果我们尝试传递一个不是精确的 `Animal` 类实例或不是其派生子类实例的参数，PHP 会极其糟糕地报错，我们的应用程序就会崩溃。

使用类型提示的原因很简单：我们想要确保传递的所有参数都遵循在 `Animal` 类中定义的接口。出于这个原因，我在第 7 行调用 `getName()` 方法的地方说明了这一点。如果我们认为抽象父类 `Animal` 定义了 `getName()` 方法是理所当然的，那么我们应该有信心，任何从 `Animal` 类派生的具体实例不仅也实现了相同的方法（无论是直接实现还是通过重写实现），还提供了相同类型或兼容类型的返回值。考虑下面这段代码：

代码，但从抽象意义上来说。

```php
abstract class Animal
{
    /**
     * @return string
     */
    abstract public function getName();
}

class Cat extends Animal
{
    public function getName()
    {
        return new AnimalName('Cat');
    }
}
```

抽象父类通过注释的力量声明了 `getName()` 方法的实现应该返回一个字符串值。我们新数据的预期行为一而易见。然而，在派生的 `Cat` 类中，返回值显然是一个对象，这将意味着我们的客户端代码在使用该值之前，可能需要进行一些返回类型检测（可能使用 `if` 语句）。我们破坏了关于“什么是动物实例”的定义，并给我们的客户端代码施加了不必要的负担。顺便说一下，这种负担不太可能被承担。尽管如此，对于 PHP 解释器来说，这段代码是完全有效的。真是一团糟！

当我们允许同名方法调用返回不同的类型时，我们剥夺了自己利用这一非常强大的功能的机会。不仅如此，我们还在为未来的 bug 修复和维护埋下伏笔。

那些展现出 PHP 才华的开发者，是那些遵循抽象父类中定义的新数据类型规范的人，直到确保返回类型保持兼容。他们也是那些不乐意在大家都去酒吧时留下来修复 bug 的人。

## 流程与控制的抽象

尽管如此，如果我们不对控制的抽象进行适当考虑，我们对抽象的讨论将是不完整的。然而，你可能会感到庆幸，

代码，但从抽象意义上来说。

这件事将不再之前那样需要这么多字了。本质上，我们已经涵盖了大部分基础工作，再稍微扩展这些想法也不需要费多少精力。

到为止，我一直在从数据的角度考虑抽象，在此过程中，我们探索了如何创建可能非常复杂的结构，这些结构不仅描述了单个属性如何更合逻辑地组合成一个整体，还描述了我们期望这个收集的数据单元如何运行以及与系统的其余部分交互。

如果你考虑上一章中 `User` 类的最后一个示例，我们已经将本质属性和特征提炼成了一个蓝图，据此创建用户对象。你会记得，这样的用户对象是通过构造函数注入的 `UserTransport` 实例来种化的，而 `User` 类本身的公共接口并没有提供此类活动的任何线索。

因此，我们一直在讨论数据抽象。

通过控制的抽象，我们将注意力从“知道事情”的对象转移开，转而考虑那些“执行操作”的对象集合。

核心原理是相同的。我们试图通过将给定过程的复杂性隐藏在接口之后来掩盖它们，接口虽然可能很复杂，但它让操作者不需要知道整个过程的内部实现细节。让我们花时间考虑汽车的案例如何帮助我们理解这种风格的抽象。

代码，但在抽象意义上的代码。

你正在调节液体氢油进入燃烧室的流量，施加电火花引起受控爆炸，并使活塞头部承受不断增加的牛顿力，这些力通过齿轮系传递将让我们能够在更短的时间到达目的地？不。你不是那样做的。你用力踩踏板，大喊道：“噢耶！烧胎啦，宝贝！”

或者也许那只是我个人的想法。

无论如何，将化学势能转化为动能的转换细节对你来说是隐藏的——假设你不是一个化学家的话。内燃机运行的复杂性被抽象化，隐藏在构建于“驾驶舱”背后的接口之后。

在对象编程中，我们实现了完全相同的事情，仅仅是通过将我们极其复杂的流程编写成代码，并将它们隐藏在某种接口之后。我们获取一个想要发生的动作的想法，用代码将它们表达，然后提供一种可以调用该过程的方法。对于汽车来说，实际启动引擎的过程隐藏在转动点火钥匙之后。对于我们的代码，运行复杂操作的过程隐藏在公共方法的定义之后。

这是从我们这些执行者的角度来看的抽象。

让我们通过代码的魔力再次检查一下我们的理解。

```php
class PasswordManager {
  const PASSWORD_MANAGER_COST = 10;

  public function getPasswordHash($rawPassword) {
    $options = array(
      'cost' => self::PASSWORD_MANAGER_COST
    );
    return password_hash($rawPassword, PASSWORD_BCRYPT, $options);
  }

  public function verifyPassword($rawPassword, $hashedPassword) {
    return password_verify($rawPassword, $hashedPassword);
  }
}
```

很熟悉对吧？欢迎回到 `PasswordManager` 类，我们上一个章节的执行者。我们采用了一个流程——即将用户提供的字符串转换为该字符串的哈希表示的概念，并编写了完成此任务所需的代码。我承认，在第 7-11 行 `getPasswordHash()` 方法那片潮湿、恶臭的丛林中，抽象并不特别复杂。但请注意，这段代码并没有自由漂落在我们的代码库中，它被锁在一个方法内部。当我们的调用代码需要哈希密码值时，它无法直接使用该代码，因为我们已经将其抽象到了方法调用之中。当我们需要触发其背后的复杂过程时，该方法调用就会被激活。

这种做法的之处在于，它赋予了我们在不中断应用程序运行的情况下改变后台发生变化的能力。如果我们需要增加哈希操作的成本，我们可以这样做。如果我们需要用更新、更安全的算法来补充 `PASSWORD_BCRYPT` 算法，我们也可以这样做。只要该方法继续接受原始密码并返回哈希密码，我们就不一定需要知道在该简单接口背后被抽象了哪些过程。

这就是控制的抽象——将一组动作的细节（计算字符串的哈希）隐藏在另一组动作（调用方法并收集返回值）之后。

# 总结

在抽象抽象抽象旅程中，我们从抽象滥用的那片潮湿、恶臭的丛林开始，考虑代码复用概念是如何被错误地纠缠到抽象到类以及自类的过程中的。现在，我希望你已经认同：利用抽象作为避免重复的手段并不是一种尊重 DRY 原则的稳妥方法。如果有运气的话，我在这一过程中引入了便利方法的概念，加强了这一论点。

不过作为快速复习，便利方法是指那些可能被添加到父类中的方法，以便方便访问某个实用的例程或过程：这个过程与我们通过编写特定类所实际尝试定义的对象几乎或完全没有关系。

这一章就像生活本身，在反向体验（或者在第二次阅读时）会更有意义。我在这里真正想要推动的观点是：创建一个抽象类，实际上是为我们每天使用的语言定义一种新的数据类型。这在很大程度上是因为它确实是如此。通过类定义进行数据抽象赋予了我们权力：“嘿，PHP，你的数组类型并不适合我正在处理的数据，我要添加更多类型。”

但为了实现 PHP 的精妙，我们在定义新类型时需要保持谨慎。我们希望对“类型”究竟是什么实现一个紧凑且全面的定义，因为我们希望团队中的男女孩们对新类型属性和特征的熟悉程度，能达到他们对语言中已有类型的熟悉程度。



如果我们能做到这一点，如果我们能实现这种理解，我们就走在了为应用程序构建健壮性的道路上。相反，每当我们向父类（无论是否是抽象类）添加便利方法时，我们都在逐渐模糊新数据类型的意图陈述，从而增加了应用程序的脆弱性。你可以确定，脆弱性会导致 Bug 和系统崩溃。

拼杀出那片丛林，沐浴在由严谨的新数据类型构建的阳光世界的耀眼光芒中。

# 继承巨额财富并不总是好事。

现在我们已经详细讨论了抽象，是时候将注意力转向硬币的另一面了。如果我们对抽象的理解发生了变化，或者至少被重新对齐了，我们应该如何看待继承？

一旦定义了抽象类，就可以使用 `extends` 关键字创建子类。这对于定义和抽象功能非常有用，并允许在相似性的基础上实现额外的功能，而无需重新实现所有共享功能。

我坚信，继承的概念在对象编程中的重要性丝毫不亚于在现实生活中。通过继承的过程，我们拥有了创建紧密相关的数据类型家族的权力。但在编程中，我们需要比大自然传播祖先特征的混沌过程要小心得多。毕竟，既然我们已经开始投入如此多的关注和精力来定义新类型，我们应该有特别的动力在我们让我们留于世上的每个后代中保留这些特征。

我们已经知道，使用 `extends` 关键字赋予了我们创建另一个类的子实例的能力，这样做子实例将继承父类的所有的非私有属性和非私有方法。除非类重写了这些方法，否则它们将保留原始功能。

通过参考大家最喜爱的 PHP 各类信息来源，我们可以看到：

> 继承是一项成熟的编程原则，PHP 在其对象模型使用了这一原则。这一原则将影响许多类和对象之间相互关系的方式。例如，当你扩展一个类时，子类继承自父类的所有的公共（public）和保护（protected）方法。除非类重写了这些方法，否则它们将保留原始功能。这对于定义和抽象功能非常有用，并允许在相似性的基础上实现额外的功能，而无需重新实现所有共享功能。 – PHP 手册 (`http://php.net`)

继承巨额财富并不总是件好事。

这在它的简洁性上本身就是件美事。那么，我可以让这一章就此结束吗？不。

我们之所以必须在追求的过程中坚持前行，恰恰是因为继承的过程也赋予了我们在真正宏大的规模上把事情搞砸的能力。而我确实非常擅长搞砸。说得并不夸张：每当我看到继承处理得正确、智能、恰当时，我都会见证上百个真正糟糕的实现。

想象一下，你们公司内部开发的某个“类 MVC”框架，在其中，你通过扩展 `View` 类来创建控制器。我将不再详细赘述这个特定恐怖故事的细节。至少目前是如此。

## 为什么要费力使用继承？

这是一个很好的问题，一旦我们不再用“代码复用”和“便利性”作为借口，这个问题的答案就会变得越来越困难。答案确实在于为我们之前构建在抽象类中的新数据类型创建特异化的过程。

随着本章的深入，我们将熟悉一个术语——“继承层次结构”（inheritance hierarchy），所以我现在就涵盖它。继承层次结构恰恰发生在你定义一个类来扩展另一个类时。只要你有了一个父类和一个子类，你就拥有了一个层次结构。你同时也承担了额外的责任。

当然，这就是世界运作的方式。你创造了一个孩子，你就得到了额外的责任。从编程的角度来看，在继续创建子类时，脑中要有这种“家庭”的概念是非常重要的。当你忙于行使你那神一般的权力，并涉足于填充应用程序空间中的居民时，记住你的责任也同样重要。随着我们的后续操作，这些责任将变得显而易见。

到此为止，读这里的每个人理应该已经知道，当你创建一个扩展另一个类的空子类时，子类的实例将继承父类所有的公共（public）和受保护（protected）方法及属性。我知道这非常像是“继承入门”的内容，但让我们看一些代码，以确认我们处于同一个频道上。

```php
// 定义新的数据类型
abstract class Vehicle
{
    protected $modelName;

    public function setName($modelName)
    {
        if (!$this->validateName($modelName)) {
            throw new Exception('Invalid model name parameter');
        }
        $this->modelName = $modelName;
    }

    public function getModelName()
    {
        return $this->modelName;
    }

    private function validateName($modelName)
    {
        // 内部验证程序
        // 针对 $modelName 属性
    }
}
```

```php
// 添加空子类实现
class Car extends Vehicle
{
    // 空类定义
}
```

```php
class Motorcycle extends Vehicle
{
    // 空类定义
}
```

到此为止，一切都非常清晰。在代码列表的顶部，我们清楚地定义了新的 `Vehicle` 数据类型，其属性仅包含一个 `$modelName` 属性。我们的 `Vehicle` 数据类型的特征描述在两个公共方法 `setModelName()` 和 `getModelName()` 中。请记住，就我们新数据类型的特征而言，我们只认为公共方法是定义这些特征的。也就是说，从该对象的协作者的角度来看，此类类对象将表现出的整体行为是由这些对象呈现给协作者的公共方法（即暴露的接口）所决定的。

在 `abstract` 类所给出的数据类型定义之下，我提供了两个空子类实现，分别对应 `Car` 和 `Motorcycle`。我提供这两个空类纯粹是为了强化最初的观点：这两个子类的行为与父类 `Vehicle` 完全一致。在不经修改的情况下，我们的子类将表现出相同的行为。

当你开始向子类添加代码的过程时，问题开始出现。当你开始这样做时，你需要确保你所做的更改不会改变父类的接口。这本身听起来就很绕口，所以让我们探讨一下它的含义。

许多开发者将重写父类方法视为一种恩赐；它赋予了子类特异化。毕竟，如果不能重写父类方法，提供特异化子类的意义何？这就是我们讨论继承的核心。直接的答案是，是的，你可以为了提供子类所需的行为而重写方法。实现这一点需要谨慎处理，也许是你目前为止一直在使用的谨慎处理。

目前，让我们看看上一章介绍的例子。如果我们通过创建一个抽象父类为新数据类型提供蓝图，那么我们希望所有的子类都符合该新数据类型的规范。简而言之，子类应该遵守父类所做出的承诺。

在子类中重写抽象父类的方法时，我们应该确保子类的方法与父类的规范保持兼容。

我们可以通过遵循三个规则来实现这一点。这些规则帮助我们维护在抽象类中创建的新数据类型的类型安全。我们的家庭

### 这些规则是什么？

第一条规则涉及重写方法的输入参数。子类方法中的输入参数数量应相同或多于父类方法的输入参数数量。理想情况下，我们保持输入参数的数量相同，因为当我们这样做时，我们强化了父类的定义为法则。然而，我们也需要意识到，由于我们正在编写子类以适应更特异的情况，我们有时可能需要在数据类型要求之外额外增加一些内容。这可能没必要说得防遗漏，我们只需注意，无论输入参数的数量是否相同，父类方法中指定的参数顺序应该在子类中得到遵守。

第一条规则还有第二个方面——这可能更为重要。重写方法的输入参数类型应与父类指定的类型相同或更通用。

这到底是什么胡闹？更通用？乍一看，这要么荒谬，要么不可理解，或者两者兼有。如果我们我们要采用一种机制来提供更特异的子类，类方法的参数难道不需要根据子类的需求而不是父类的需求来改变吗？并非如此。

继承巨富并不总是好事。

为了保持我们维护类型安全的目标，我们必须将注意力牢牢锁定在抽象类所表达的数据类型定义上。抽象类应该是我们关于该数据类型定义的单一事实来源。

考虑以下代码。

```php
abstract class Mechanic
{
    public function fixVehicle(Car $car)
    {
        ... // do repairs
        return $car;
    }
}
```

为了说明这一点，我想让你想象我们正在运行一个三级的继承结构——但这仅用于此说明。

```php
class Vehicle
{}
```

```php
class Car extends Vehicle
{}
```

```php
class SportsCar extends Car
{}
```

我承认，这不是最令人兴奋的代码，但我不想让你忽视事实上：我们拥有从通用的 Vehicle 到最专用的 SportsCar 逐渐专业化的类。

现在，根据我们对 Mechanic 数据类型的定义，当我们调用 `fixVehicle()` 方法时，我们期望传入一个 `Car` 类型的实例。如果我们假设客户端代码会这样做，那么从数据类型定义来说，一切都是好的。

让我们开始编写 `Mechanic` 类的子类。

```php
class SportsCarMechanic extends Mechanic
{
    public function fixVehicle(Car $car) {
        // do car based repairs
        return $car;
    }
}
```

到目前为止，一切良好。我们的输入参数是相同的，所以我们甚至不需要纠结是否仍然实现了类型安全，因为我们必须这样做。这是你最稳妥的选择。然而，这个类被称为 `SportsCarMechanic`（跑车修理师）。它不是一个专家吗？难道你不认为 `SportsCarMechanic` 会专长修理跑车吗？如果我们假设这是真的，我们的代码看起来像这样：

```php
class SportsCarMechanic extends Mechanic
{
    public function fixVehicle(SportsCar $car) {
        // do car based repairs
        return $car;
    }
}
```

乍一看，这似乎非常有逻辑。我们将 `SportsCarMechanic` 声明为普通 `Mechanic` 的专业版本。我们只向 `fixVehicle()` 方法传递 `SportsCar` 实例似乎是完全合理的。

但这是错误的。即使我们的逻辑告诉我们它是的，它也是错误的。我们大脑告诉我们，如果我们正在创建一个更专的修理师，理所当然地应该期望它在更专业的情况下运行。我们实际上是将现实世界的经验映射到应用逻辑上，这可能是我们在刚开始学习时读过的那些教程导致的。

面对现实吧，如果我们足够幸运买得起一辆法拉利，我们可能更倾向于把它交给一个只修法拉利的人，而不是那种什么都能修的通用修理师。然而，通过对一个更具体的参数进行类型提示，我们违反了我们的类型定义，因为规则告诉我们的参数应该是相同的或更通用的。

继承巨富并不总是好事。

当我们把注意力转向一小部分时，它错误的原因应该变得更加清晰。我们在抽象父类中规定的数据类型定义规定，`Mechanic` 类型的变量可以通过提供 `Car` 实例作为输入参数来调用 `fixVehicle()` 方法。识别到数据类型定义，我们的客户端代码在调用 `fixVehicle()` 方法时提供了一个 `Car` 类型的实例。这是我们可以做的唯一安全假设，因为这是写在定义本身中的。

鉴于此，`SportsCarMechanic` 现在破坏了抽象父类承诺的合约。`SportsCarMechanic` 接受 `SportsCar`（甚至更具体的）实例。当我们的客户端代码发送一个普通的 `Car` 实例时（它是这样做的，因为数据类型定义是要求的），`SportsCarMechanic` 会崩溃并导致我们的应用程序死亡。

让我们修复那段代码。

```php
class SportsCarMechanic extends Mechanic {
    public function fixVehicle(Vehicle $car)
    {
        // do car based repairs
        return $car;
    }
}
```

在这里，我将 `$car` 参数的类型提示替换为更通用的形式 `Vehicle`。

这。看起来。很。错。它是一个 `SportsCarMechanic`，但它接受一个 `Vehicle`。然而，它是正确的。

继承巨额并不总是一件好事。

```
class SportsCarFactory extends CarFactory
{
    public function getCar() {
        // 创建一辆跑车
        return new Vehicle();
    }
}
```

我替换了返回类型，使得 `getCar()` 方法返回一个更通用的 `Vehicle` 实例。根据我们的规则，这是错误的。如果我们遵循这个逻辑，我们可以确认它是错误的。请记住，我们在抽象父类中的定义是，此方法调用返回的是一个 `Car` 实例。因此，我们的客户端代码是倾向于处理它期望从调用此方法中获取的 `Car` 实例的。然而在这里，当我们的客户端代码遇到一个 `SportsCarFactory` 实例时，它产生的是更通用的 `Vehicle` 类型。从我们的层级结构中知道，`Vehicle` 并不是 `Car` 的类型。当客户端期望与 `Car` 实例一起工作但却得到了一个 `Vehicle` 实例时，问题定会随之而来。结果呢？玩游戏的时间变少了。

我们认为保持返回类型相同会更好，但幸运的是，现实世界中的预期通常会符合第二条规则。更get化的子类可以发射更专门的返回类型。

那么我们的最后一条规则呢？我们的最后一条规则非常简单，因为它将第二条规则的逻辑映射到异常的使用上。让我们明确一下：子类中的重写方法只能抛出与父类被重写方法中可以抛出的异常相同的、或更专门的异常实例。

让我们再次从完全相同的数据类型开始。

继承巨额并不总是一件好事。

```php
abstract class CarFactory
{
    /**
     * @throws CarException
     */
    public function getCar()
    {
        throw new CarException('无法制造汽车');
    }
}
```

这一次，我只关注正在被抛出的异常。我们有一个新的继承层级结构要处理，但由于它与我们的 `Vehicle` 层级结构直接对应，我将跳过代码，仅这样表达它：`VehicleException->CarException->SportsCarException`。和之前一样，我们的数据类型选择了中间类型作为它发射的类型，但由于它是异常，它会被抛出而不是返回。

现在让我们来看我们修改后的 `SportsCarFactory`，它的代码应该是这样的：

```php
class SportsCarFactory extends CarFactory
{
    public function getCar()
    {
        throw new SportsCarException('无法制造跑车');
    }
}
```

我们的专门子类实例现在正抛出一个更特定类型的异常。这仍然是可以的。我们的数据类型定义说明此方法可以抛出 `CarException`，相应地，我们的客户端代码为此做好了准备。

继承巨额并不总是一件好事。

```php
try {
    $sportsCar = $factoryInstance->getCar();
} catch (CarException $e) {
    Logger::crit('哎呀');
}
```

由于我们的 `SportsCarException` 是 `CarException` 的一种类型，客户端代码中的 `try/catch` 块可以愉快地接纳它。那么如果我们反过来这样做会发生什么呢？

```php
class SportsCarFactory extends CarFactory
{
    public function getCar()
    {
        throw new VehicleException('无法制造跑车');
    }
}
```

这一次，我们违反了抽象父类所设定的定义，因为它抛出了更通用的异常类型，结果就是我们发射了一个客户端代码没有准备好处理的异常。由于我们的定义告诉我们要预期某种类型的异常，作为出色的 PHP 开发者，应该在编写客户端代码时使其能够处理它。或者说，我们应该在编写子类时，保持其与客户端代码的预期保持兼容。

只要我们遵循这条规则，即子类重写方法所抛出的异常应该是相同类型或更具体的类型，我们就可以高枕无忧了。毕竟，我们没有人捕获过生产环境中要抛出的异常。当应用程序崩溃时。

“计算机科学中，‘悠悠问题’（yo-yo problem）是一种反模式，当程序员必须阅读并理解一个程序，而该程序的继承图如此长且复杂，以至于程序员必须在许多不同的类定义之间不断切换来跟踪程序的控制流。” —— 来自 `Wikipedia.com`

那么，我们为什么要这么做呢？为什么这个问题如此普遍，以至于它都有自己的名称和维基百科页面？提供三层或更多层级继承的无限制能力，在我看来，源于一种误导观念，认为抽象和继承可以促进代码重用并帮助开发者避免重复。我很抱歉提醒了你这个观点，但我仍然坚决地认为它们并不能如此。

不过，代码重用是好的。我们知道这一点。避免代码重复也是好的。我们也知道这一点。“不要重复自己”（DRY）原则的追随者热衷于保留和传播这些知识，而且这是明智之举。不要误会我，认为我是在因为看不起代码重用而排斥它，我并不是。如果我要把“继承滥用”表达为一个单一概念，它将是：

继承滥用的发生由于一个类对另一个类无根据的过度扩展，其理由仅仅是扩展类可以访问并因此利用被扩展类的逻辑、例程和/或属性。



正如你可能推断出的，我再次提到了便利性问题，但这次，我不是在描述特意在父类中编写一个便利方法以便子类可以轻松访问的过程，我特地指的是这种做法：让一个类继承另一个类，*纯粹*是因为预期的类包含了“有用的东西”。当这种情况发生时，开发者显然忽视了任何关于家族、层次结构或数据类型的概念。当这种情况发生时，是因为开发者想要将父类目标的一些功能“导入”到他们正在创建的子类中。这是另一种极其糟糕且易于识别的代码异味。

我特别渴望鼓励的一点是让开发者避免陷入继承滥用的陷阱。让你的层次结构尽可能地扁平。两层是努力追求的理想目标：由抽象父类提供数据类型定义，由子类提供具体的数据类型特化。当然，并不是所有的应用需求都是相同的，但如果你确实需要超越这些层级，请务必有一个非常充分、非常有力的理由。在过程中，请务必记住，你在继承层次中每添加一个层级，都会为你的应用程序增加比例的脆弱性，这很大程度上是因为“人非完失”。

## 通过扩展引入第三方代码

这很好地引出了我们的下一个考虑点。有时，我们被迫进入继承滥用的陷阱，一头扎地掉进层次结构的兔子洞，在双手被缚在脑后的情况下跌入未未的领域。在我变得太戏剧化之前，我所指的情况是我们被强加了未计划的层次结构。这种“未计划”的意思是，原始代码的作者与我们正在工作的项目没有直接联系。

我说的是第三方库、组件和框架的使用。这个概念当然是值得赞美的。开源软件运动最人的方面之一，仅仅是因为出色的代码可以由大量聪明的人创建和策划，并由许多人进行代码审查、审计和合理性检查。这反过来导致了一些健壮的可重用代码包，以满足几乎每一个可以想象的用例。记住，代码重用是好的。至少，它让我们不必一次又一遍地造轮子。

会出现这样的情况：我们都被鼓励将继承滥用作为做事的正确方法。无论是公司政策还是仅仅是 CTO 的个人偏好，我们可能会发现其他人受限于特定的库或框架。在商业环境中，通常无法花时间去尝试和探索各种现有产品。业务需求需要产品上市，缩短开发时间。

但问题在于：如果那个 `UserDataTransport` 类就是我们扩展框架提供的基类的方式呢？

```php
class UserDataTransport extends FrameworkXYZ_Base_Model
{
  ..
}
```

It may not be an ideal solution because we are still having to accomod the reuse-by-extension idea that the framework imposes upon us, but by turning our derived so called model class into this notional `UserDataTransport` class, what we've actually achieved is a very nice layer of separation between our models and the framework.

# Summary

Whilst this chapter on Inheritance isn't quite as wordy as the Abstraction chapter that precedes it, I hope that I've managed to convey the key concepts in a way that is, at the least, comprehensible. If you accept that abstraction we are developers able to extend the range of data types that is natively available in our language of choice, hopefully you will also be to accept that the child classes that we derive from those abstract parents must remain compatible with the specification of the data type that the abstract parent provides.

继承巨额财富并不总是件好事。

如果所有子类都符合并兼容抽象父类定义的接口，我们永远不会遇到由于意外的变量类型传递给方法调用或从方法调用返回而产生的问题。我们子类的实例都将显示父类定义的数据类型的属性和特征。

这一切都归结为被称为可替换性（Substitutability）的概念，并构成了里基夫替换原则（Liskov Substitution Principle）的核心前提，我之前提到过这一点，并在本书的后面将进行更深入的探讨。简而言之，可替换性要求我们考虑：如果我们随机将一个子实例替换为同一继承家族中的任何其他子实例，我们的应用程序是否能够在无任何故障或异常的情况下运行。如果我们能够心所欲地切换和交换而不失败，那么强烈表明我们已经实现了可替换性。然而，如果我们因为某个实例的行为不完全符合预期而遇到问题，那么这显然是一个未能实现这一非常理想目标的典型案例。

你还记得我在本章开头设定的那三条规则吗？尽可能遵守这些规则将显著减少你的应用程序中出现类型安全相关 Bug 的可能性。

其连锁反应是什么？你那近乎超能力的预见力声誉会因此增加一点点。

## 探究多态

多态在应用于 PHP 时，是一个完全让人混乱的话题。如果你花点时间在网上研究这个特定的怪兽，你会发现大量相互冲突的信息，这些信息的总和让你怀疑自己到底是对这个主题是过了还是学到了什么。

这并不是我第一次诅咒互联网，因为它允许以极其糟糕的方式传播不合格的信息。你现在可能不会惊讶于发现我正要求你忘记一些事情，这很大程度上是因为大多数糟糕教程倾向于使用所谓的“子类多态”（*subtype polymorphism*）来解释 PHP 如何实现多态。它们并不总是解释得很清楚。在这个阶段，我希望并祈祷我不会掉进坑！在接下来的内容，我将尝试涵盖“不该做的”（*don'ts*）以及“应该做的”（*dos*），希望我的读者能够充分吸收并内化所有的糟糕建议。

首先，让我们花一点时间提醒一下多态。毕竟，这并不是一个我们许多人经常思考的特定话题。但它*真正意味着*什么？

“多态”（Polymorphism）一词源于两个希腊词的结合；*Polys* 意思是“许多”，*morph* 意思是“形状”。这给我们的字面意思是“许多形式”。到目前为止，没什么新奇的。

编程社区普遍接受的解释是，多态是“为不同类型的实体提供单一接口”。这本身就是对比雅尼·斯特拉斯鲁普（Bjarne Stroustrup）C++ 词典的直接引用，由于斯特拉斯鲁普是 C++ 的创建者，我们很应该相信这一陈述的准确性。

探究多态。

从 PHP 开发者的角度，我想提供一个非常简单的翻译：“同名不同逻辑”。然而，这并不完全，虽然它在最基本的字面解释上可能是正确的，但在告诉多态是什么或如何实现方面还不到一半。尽管如此，在我们处理这个话题时，将引用这个“同名不同逻辑”的想法来解释它是如何链接。在进入细节之前，我们应该对该话题有一个更通用的视角，所以让我们开始吧。

讽刺的是，多态本身有许多形式，区分不同的类型非常重要，我们需要学习哪些类型在 PHP 中是可以实现的，哪些不能。请注意，我将仅在面向对象编程的范围内涵盖多态。第二个需要注意的是，我将讨论最常考虑的类型。那里有很多，但我将它们留给你作为进一步研究的可选练习。

我将从一种我们在 PHP 中无法完成的类型开始。

### 特殊多态（Ad Hoc Polymorphism）

特殊多态依赖于语言支持方法重载（method overloading）的能力，从而允许开发者在同一个类中编写同一个方法的多个版本。这非常符合“同名不同逻辑”的思想。这里要求的是，开发者应该提供多个相同相同但通过不同数量和类型的输入参数提供不同签名的方法。通过这种方式，开发者将方法的选择交给程序的执行环境。无论你是否熟悉 Java 语言，下面的示例都应该很容易理解。

探究多态

```
class MethodOverloading
{
    public int add(int x, int y)
    {
        return x+y;
    }

    public int add(double x, int y)
    {
        return (int)x+y;
    }

    public int add(int x, int y, int z)
    {
        return x+y+z;
    }
}
```

从上面的代码示例可以看出，我们的 `MethodOverloading` 类提供了三个都称为 `add()` 的公共方法。在每情况下，三个 `add()` 方法都拥有不同的方法签名；执行哪一个 `add()` 方法完全取决于所传递参数的数量和类型。

显然，我们无法在 PHP 中实现这种多态。解释器一旦遇到包含两个或多个同名方法的类，就会直接崩溃并死亡，无论方法签名本身是否不同。因此，我们不要在这个特定类型上停留太久。

### 子类多态与方法覆盖的致命案例

我们在多态弹药库中的下一个考虑因素是被称为“子类多态”（subtype polymorphism）的内容。这似乎是我在本章开头提到的那些糟糕教程作者们最喜爱的。

在某种奇妙的命运转折中，当我审查这一章时，我决定在 Google 上搜索“Polymorphism”一词，看看会出现什么。

探究多态。你瞧，就在我搜索结果的第一页最上方，Google 非常热心地地标出了 Webopedia.com 对多态的定义，我在这里直接引用它：

在面向对象编程中，多态指的是编程语言根据对象的数据类型或类以不同的方式处理对象的能力。更具体地说，它是为派生类重新定义方法的能力。什么是多态？Webopedia www.webopedia.com/TERM/P/polymorphism.html

你看到他们做了什么吗？一瞬间，Google 和 Webopedia.com 似乎都通过将一个信息不全且不合格的陈述作为权威信息来威胁人类的未来。当然了，我极度地夸大了这种可能的影响。或者不是呢？难道需要如此奇幻的想象力飞跃，才能构出一个负责 NASA 撞击行星激光的小员在无意中覆盖了子类中的 `fire()` 方法，结果意外将其变成了引力束的形象吗？是的，好吧，也许确实如此。为了记录一下，我想说 NASA 的程序员显然非常有才华，是顶流的代码手。

产生多态。

```php
class RegularBullet {
    private $baseDamage = 10;
    public function getDamagePoints() {
        return $this->baseDamage;
    }
}
class HollowPoint extends RegularBullet {
    public function getDamagePoints() {
        $damagePoints = 2 * $this->baseDamage;
        return $damagePoints;
    }
}
```

希望这段简单的代码能相当清晰地说明**子类多态（subtype polymorphism）**的概念。我们的子类 `HollowPoint` 重写了父类的 `getDamagePoints()` 方法，从而改变了特定类型子弹击中目标时计算伤害点的逻辑。这仍然符合我们早期对多态的定义，即“同名、不同逻辑”。通过子类多态，我们通过在子类中提供重写父类中同名方法的方法，实现了相同的同名限定。

如果你还没有猜到，我正要开始抱怨我的其中一个不满点了。这个抱怨的核心点在于，通常情况下，我非常反感的那些该死的教程就仅限于此水平。让我们回到 Webopedia.com 那个定义的第二句。

更具体地说，它是为派生类重新定义方法的能力。

我多希望那句陈述能更严谨啊？我多希望包含该定义的文章能详细介绍正确的用法、陷阱和注意事项啊。我多希望我们的初级开发者在第一次在网上搜索关于多态的文章时，能看到更高质量的信息？

让我们来衡量一下我们的例子，但用一种完全符合这个所谓多态定义的方式。

```php
class ExplosiveRound extends RegularBullet
{
    public function getDamagePoints(Player $enemyPlayer )
    {
        $armorFactor = $enemyPlayer->getArmorPoints();
        $damagePoints = $this->getDamagePoints();
        $damagePoints = $damagePoints * 2;

        $damagePoints -= $armorFactor;
        return $damagePoints;
    }
}
```

乍看之下，这似乎满足了子类多态的要求——紧接着，我们在派生类中成功地重新定义了 `getDamagePoints()` 方法。诚然，我们现在可能不得不修改整个敌人受伤害的程序，以确保在玩家被 `ExplosiveRound`击中时能正确处理玩家实例，但嘿，这点我们可以做得到。

多态达成！检查！搞崩了我们的应用程序？

然而，这就是基础教程对待多态这一主题的典型程度。当我们可怜的初级开发者编写上述代码时，他们该怎么办？这种代码本应该是那种引发泪水洪水、导致类似圣经规模洪水的代码。

对于真正想要实现 PHP 卓越境界的开发者来说，他将知道为了正确使用子类多态，否则他必须表现得非常小心。我们来说幸运的是，你已经经历了前两章关于“抽象”和“继承”的痛苦和折磨，作为结果，你已经知道上面的代码是一个巨大的禁忌。

你已经知道这一点了，因为在上一章关于“继承”的章节中，你可能意识到（也可能没有）我已经处理过子类多态了，尽管我没有专门使用这个术语。在对抽象父类声明的数据类型的子类实现中，我们可以提供重写父类中声明的同名方法。我们只需要在执行时记住这三条规则即可。

重写方法中方法签名的任何更改必须与父类中声明的方法签名保持兼容。子类中重写方法返回值的任何更改必须与父类中声明的返回类型保持兼容。最后，如果子类中的重写方法可以抛出异常（或者实际上是触发异常抛出），那么这些异常必须与父类中相同方法可以抛出的异常类型相同，或派自这些异常。只要我们遵循这三条规则，就能将未来的 Bug 和头疼问题降到最低。一个需要注意的迹象（一个静静告诉我们未能遵守这些规则的信号）是：如果你发现自己需要在客户端代码中实现特殊逻辑，以适应特定继承层级中一个或多个子类的奇特行为。也就是说，如果你发现自己正在编写条件语句来判断你处理的是 `RegularBullet` 还是 `ExplosiveRound`，那么你可以确定，你的子类没有符合父类提供的数据类型定义。

好了，我确实警告过我会重复一遍了。

尽管如此，这才是应该处理子类多态的方式。对于见多识的人来说，这看起来非常像我正试图让子类多态服从参数多态（parametric polymorphism）的意志。当然，我确实是。

# 参数多态 (Parametric Polymorphism)

在我开始定义参数多态之前，我觉得必须声明，PHP 通常不被认为是一种原生支持该概念的语言。尽管如此，这种语言极其松散的类型特性意味着，参数多态可以说“开箱即用”。

考虑以下代码片段。

```php
<?php
function multiplier($a, $b) {
    return $a * $b;
}

echo multiplier((int)2,(int)4); // 输出 '8'

echo multiplier((float)2.5, (float)6.0); // 输出 '15'

echo multiplier('abc', 5); // 输出 '0'
```



上述示例函数可以被认为支持参数多态，因为它无论类型如何都能执行。然而，我们太沉溺于背景细节了，要说明的重点是：只要 `renderVehicle()` 方法接收到的是一个标识为 `Vehicle` 数据类型实例的参数，该方法就应该成功执行且不报错。

### 探测多态

正如第一个例子中的函数那样。尽管如此，还有另一个关键点需要说明：作为消费者，`renderVehicle()` 方法不需要知道 `$vehicle` 参数是具体哪个类的实例。只需要它符合由抽象父类给出的、更通用的 `Vehicle` 定义所指定的接口即可。

到这里，我想请大家重新关注我在本章开头给出的对多态的那种简单解释。尽管我们将重点从提供者转移到了消费者，但“相同名称，不同逻辑”的想法对于这种类型的多态仍然是一致的。“相同名称”组件指的是我们在为 `renderVehicle()` 方法提供输入参数类型提示时，使用的是抽象父类的类名。同时，我们知道“不同逻辑”组件通过该方法可以接收该特定类型族中的任何一个派生类这一事实得以满足。

作为开发者，显而易见的是我们在日常编码中经常使用多态（或者至少，我是这么做的），因此也应该显而易见，为什么我要花这么多精力来试图传达这种数据类型定义的思想。

我会再说一遍。当然，我会一直这么说的。只要我们继续正确地支持“抽象父类为我们提供了新数据类型的定义”这一观点，并且只要我们确保任何派自抽象父类的类都继续支持该数据类型的定义，我们就可以合理地预期与此数据类型实例工作的协作方可以在运行时不会错误，无论它们最终处理的是哪一个具体的类实例。

这就是应用于面向对象 PHP 的泛型编程的基石。

但是，如果不说明我们如何破坏参数化多态（parametric polymorphism），这个讨论将是不完整的。要做到这一点异常简单。我知道这一点，是因为我在太多的项目中见过太多次了。它的做法是这样的：

### 探测多态

## `class VehicleRenderer`

```
public function renderVehicle($Vehicle $vehicle)
{
    switch(get_class($vehicle)) {
        case "Car":
            $this->renderCar($vehicle);
            break;
        case "Motorcycle":
            $this->renderMotorcycle($vehicle);
            break;
        case "JetSki":
            $this->renderJetSki($vehicle);
            break;
    }
}

// 针对不同车辆类的独立渲染方法
...
```

破坏它的方法非常简单。我们不再像以前那样依赖抽象父类车辆类提供的接口，而是将对具体子类实现的深入了解构建到我们的消费者中，并在过程中破坏了它的泛型本质。`renderVehicle()` 方法在继续渲染其中包含的细节之前，知道如何检查其输入参数的实际类。

每当你看到这种编码方法时，你就可以确定被消费对象的底层数据类型已经通过不当使用继承被破坏了，这很遗憾，因为对特定子类的修改需要对该子类的消费者也进行相应的修改。在一个较大的应用程序中，你可以相信这将导致 bug；通过搜索代码库以找到每一行需要修改的代码通常确实如此。

正如你所看到的，子类型多态（subtype polymorphism）和参数化多态（parametric polymorphism）实际上关系非常紧密，只要它们被正确实现。对抽象和继承的不当使用将破坏我们完美的多态过程，在几乎没有时间内将优雅的编程变成一团乱条代码。但如果我告诉你，你可以享受多态行为的所有益处，而完全没有使用继承的任何缺点呢？嗯，你确实可以做到，我接下来将开始讨论它。

## 委托多态 (Delegate Polymorphism)

如果我们不再依赖于将数据类型的所有不同逻辑实现硬编码到各种专门的子类中，而是可以完全放弃抽象和继承的概念，并且仍然支持更好地代表我们应用程序内实际行为的可切换行为，会怎样？我们对抽象和继承实际含义的那些粗糙且有些分散的解释，将突然不再是这么多 bug 的根源。

好消息是，我们可以做到这一点。尽管我不怀疑这种想法可能会让许多资深开发者的脊背发凉，但一旦我们探索了可能性，我确定至少你们中的一些人可能会开始构思在你的项目中实现委托多态的方法。

正如名称所示，该过程依赖于一种名为“委托”（Delegation）的设计模式的实现，这种模式体现了这样一种观点：本会成为专门子类的变化方面被封装在单独、独立的对象中，而是将方法调用委托给这些对象，以执行委托对象所封装的特定逻辑。

我在这里说的基本上是可注入的、封装的行为以辅助类的形式出现。让我们来看一些代码。

```
abstract class MortgagePlan {
    private $loanValue;

    private $loanTerm;

    abstract public function getPaymentPlan();
}
```

到目前为止，一切良好。显然我们在这里创建了一个新的数据类型，名为 `MortgagePlan`。我们有私有属性代表贷款价值，以及以贷款期限表示的贷款时长。

```
class FixedMortgage extends MortgagePlan
{
    public function getPaymentPlan()
    {
        // 计算抵押还款计划的逻辑
        // 基于固定贷款利率
        ...
        return $mortgagePlan;
    }
}
```

```
class CappedMortgage extends MortgagePlan
{
    public function getPaymentPlan()
    {
        // 计算抵押还款计划的逻辑
        // 基于浮动利率
        // 有上限以防止还款金额
        // 超过特定值
        ...
        return $mortgagePlan;
    }
}
```

在这里我提供了专门子类方面的常客疑犯。在第一个实例中，我们有 `FixedMortgage`，它能够计算提取固定利率贷款时的还款金额。第二个实例包含了必要的逻辑，以计算浮动利率贷款，但设有上限，以防止还款金额超过某一水平。

我有足够的信心，我的读者中的每一个人都遇到过这种代码：根据稳定类旨在代表的一组情况来实现专门逻辑的子类。这是标准做法，但事实并非如此。

如果我们对上述方案应用委托多态，我们实际上可以抛弃抽象和继承过程。尽管这显然是另一个简单的示例，现实中的项目很少如此简单，但它确实为该观点提供了很好的说明。

### 探测多态

不需要大量的重构，就可以将这种不必要的继承层级转换为一个简单的贷款类和一对可注入的行为。让我们看看它的运行效果。

```
class MortgagePlan
{
    private $loanValue;
    private $loanTerm;
    private $repaymentCalculator;

    public function setCalc(RepaymentCalc $calc)
    {
        $this->repaymentCalculator = $calc;
    }

    public function getCalc()
    {
        return $this->repaymentCalculator;
    }

    public function getPaymentPlan()
    {
        $calc = $this->getCalc();
        return $calc->getPaymentPlan($this->loanValue, $this->loanTerm);
    }
}
```

提供多态。

```php
interface RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm);
}

class FixedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on a fixed interest rate
        //
        return $paymentPlan;
    }
}
```

```php
class CappedMortgageCalc implements RepaymentCalc
{
    public function getPaymentPlan($loanValue, $loanTerm)
    {
        // Logic to calculate a mortgage repayment
        // based on variable interest rates but subject
        // to a cap to prevent repayments exceeding
        // a certain value
        //
        return $paymentPlan;
    }
}
```

正如你所见，我提供了一个接口，以确保当我们将计算器注入到 `MortgagePlan` 时，该计算器将提供 `getPlan()` 方法。实现该接口意味着如果缺少该方法，PHP 将抛出致命错误。

最后，第一个示例中的那两个专用类现在经过了修改，它们不再继承 `MortgagePlan`，而是实现 `RepaymentCalc`。每个计算器现在都是一个可注入的行为，允许我们在运行时更改调用对象的行为。这是一个重要的区别，意味着 `MortgagePlan` 实例独立于封装了不同还款逻辑的计算器。

更进一步地说，这也意味着我们可以随时更改 `MortgagePlan` 产生还款的方式。如果我们想切换到固定利率，只需将 `FixedMortgageCalc` 的实例注入到 `MortgagePlan` 中，还款行为就会自动为我们改变。

为了让这个示例回到最初支持“相同，不同逻辑”这一理念的理论框架中，`MortgagePlan` 实例仍然会调用 `getPlan()` 方法，这就是“相同”的部分。但现在，`MortgagePlan` 实例将提供还款的责任委托给任何注入到它的计算器，这就是“不同逻辑”的部分。

使用这种方法还有额外的好处。如果将来我们发现需要一种新类型的还款计算器，实现起来将变得容易得多。毕竟我们已经定义了所需的接口，我们只需要编写新的还款计算器来封装新逻辑即可大搞定。

然而，如果我们不关注委托多态的潜在缺点，那么我们对委托多态的分析将是不完整的。尽管我上面所说明的，但委托多态并非万事完美。

使用这种技术的主要批评是它导致了方法声明的大量重复。别惊慌！我并不是说我们要复制实际逻辑，而仅仅是方法名。我们必须在主类中创建代理方法，作为客户端代码和真实目标之间的中介。

我们从上面的代码中可以看到这一点。如果我们的主类是 `MortgagePlan`，我们可以看到它如何在其公共接口上提供 `getPlan()` 方法。这个 `getPlan()` 方法本身没有执行任何真实的逻辑。相反，它将请求代理给它所消耗的 `RepaymentCalc` 实例。

像这样的简单例子，在主类中声明 `getPlan()` 然后在每个不同的计算器类中声明另一个 `getPlan()` 并没有引起太大问题。但即便如此，考虑一下，如果在应用程序演进过程中，我们发现必须扩展所消耗代理的接口会发生什么？这对整合到调用对象中的代理方法数量产生什么影响？

调用对象的接口被代理方法填满的可能性很大。这是我们需要做好准备的，并且可能需要我们提问：这些代理方法是否符合我们对主类接口本应该是什么的愿景。

考虑一下我们已经看过的常用模型类 `User`。可以说，我们将密码处理的责任委托给了 `PasswordManager` 的专用实例。通过消耗 `PasswordManager`，`User` 需要对代理的哪些方法进行代理？扩展我们的思维，当我们消耗一个 `AddressManager` 代理并在调用端添加一个 `Orders` 代理时，我们的 `User` 接口会发生什么？可以想象，甚至在我们开始添加自己的用户特定专用方法之前，我们的 `User` 接口就可能变得非常庞杂。

那么，这一切都变成了一个考虑和经验的问题，尽管我希望这本书能让你在后方面采取一些有效的捷径。如果你预见到某一天你最终会有大量的代理方法，那么颠倒处理这些程序可能会对你很有帮助。与其对消耗的 `AddressManager` 进行方法调用代理，不如构建一个地址管理模块，并让 `User` 实例变成被传递的参数呢？

# 总结

我理解这看起来似乎我试图说服不要使用抽象作为定义新数据类型的方法，并为此费了大量精力来让你相信这样做的好处。这完全并非本意。正如生活中的许多事情一样，你需要根据你对情况的最优判断来做出决定。你如何做出这些判断自然会受到你对手头话题了解程度的影响。

在这种情况下，你现在知道在你的语言中使用抽象类作为定义新数据类型的方法是构建应用程序的一种非常强大的技术。你还知道使用接口作为定义约的方法是另一种同样强大的技术。最后，你见证了如何使用委托多态来创建灵活且可维护的代码，尽管我所说明的那样，它并非完美。所有这些技术都是你武器库中强大的工具，你现在知道如何有效地使用它们了。

要点。

```php
class Application
{
  ... // 所有的代码
}
```

```php
$app = new Application();
$app->run();
```

一个文件。一个类。所有内容都很好地封装，没有任何抽象、继承和多态的痕迹来阻碍。我真的在提倡这种方法吗？我希望到目前，你已经知道我并不是。

尽管如此，这并没有阻止它成为一种可能的选择。在理论上，没有理由让单个 Application 实例不能处理每个请求并发出正确的响应，坦率地说，它完全可以胜任这项工作。

我刚才说过没有理由吗？我想说的是，除了一点外没有其他理由。你看，我们回到了所有应用开发中固有的那个棘手的小问题——人为因素。在写作时，我们目前还没有以任何重大规模利用人工智能来为我们构建 Web 应用程序。注意我在这里含了推辞。我怀疑外面至少有一个项目是我们正在尝试做的（有人想加入“天网”吗？）。

这引出了一个问题：我们为什么要写我们写的这些代码？我们为什么要费心设计类结构？我们为什么要考虑知者和执行者？我们为什么要费力遵守某些每个文件只写一个类的标准？是为了让 PHP 解释器过得更轻松吗——提供更小、更易于消化的代码块？

自然不是，答案是如此。我们写代码时心里只有一个受众。人类。最经常阅读我们代码的人就是我们自己。如果我们在商业环境中工作，我们的同事可能也想读懂我们的代码。如果我们在构建开源软件，那么潜在的受众可以是几十万、甚至数百万 PHP 开发者。

我们写代码是为了让人类而不是计算机来阅读和理解它。显然，我们仍然必须遵循语言本身的语法规则和词汇，但由于我们的 PHP 兄弟们也在不同程度上接受过这门艺术的训练，

要点。

114

这归结为我们如何布局代码，如何构建代码的结构，如何将所有这一切联系在一起——正是这一点让它对于我们自己以及周围的 PHP 开发者来说变得易理解。

这让我们回到了我们那种单体式的“整个应用都在一个类中”的概念。我可以确定，我没有机会在一个类中理解一个整个应用程序，假设代码的规模达到了数百个方法和数万行代码。我不确定我是否认识谁能做到这一点。即使我们能够将其放入我们首选的代码编辑器中而不让那个神圣的东西崩溃，对应用程序内部运作的理解充其量上仅仅是碎片化的。

因此，我们需要将其拆分为更易管理的块，进入一种更具操作性的格式，这种格式能够考虑到将在其上工作的人的缺点。作为一个极好的起点，记住将我们的*知者*与*执行者*分开将有助于我们实现这一目标。

你还记得我提到过某些开发者倾向于将特定的类看作独奏（solo）吗？如果某个方法可以被看作与用户模糊相关，就把它放进去。这是麻烦小径的开始，最终导致了“类中的应用”效应。它始于我们需要隔离设计中名词的念头，但在光谱的另一端，它导致了一个众为人知的反模式，被称为“上帝对象（God Object）”。

## 上帝对象

上帝对象恰恰发生在对象被认为知道得太多或做得太多的这一点。

这是一个非常笼统的陈述，几乎没有任何限制条件，所以让我们试着对其进行限定。“上帝对象”这一术语的产生是为了代表一种对象似乎变得“全知”的方式，也就是说，它的影响在整个代码库的许多部分都能感受到，要么指的是代码库外部的大部分代码，或者更常见的是，通过大部分代码库必须向*上帝对象*本身获取、处理或二者兼备。从个人偏好来说，我喜欢赋予这样一个想法：*上帝对象*不仅是“全知的”，而且是“无不在的”。

为什么是坏事？

## 要点。

在第一种情况下，当一个对象可以导致应用程序远端发生事情时（也就是说，跨距离发生），那么我们确实为追踪 bug 制造了困难，简单来说，因为 bug 的症状与问题本身的原因（当我们发现它时）之间似乎存在清晰的隔阂。

考虑一下：

```php
$user->getBalanceManager()
  ->getBalance()
  ->getNewTransaction()
  ->setTitle('Foo')
  ->setValue('10')
  ->save();
```

尽管这段代码很丑陋，但调用这个特定链的代码与在用户账户上保存新事务的行为之间至少隔了两个层级。尽管我们还没有研究那些引导我们实现卓越的各种原则和范式，你可能已经知道那里至少发生了三次违规行为。

无论现阶段情况如何，我们都能清楚地看到调用者在完全无视封装的情况下，对于创建事务的内部运作了解得太多了。我们可以逻辑地得出结论，这也是一种非常脆弱的代码方法。即使它今天能工作，但由于链中有许多环节，因此有许多故障点，明天一点变动链条就会崩溃。

这种表达是否会更好：



```php
$result = $user->getBalanceManager()->addTransaction(
array(
  'title' => 'Foo',
  'value' => 10
)
);
```

对于这段特定的代码而言，期望 `BalanceManager` 至少提供添加事务的相关方法是合理的。内部发生了什么以及实现它的精细细节对于你的调用者来说并不重要。或者至少不应该重要。

要点。

116

知道太多是一件坏事。除非你正在参加游戏节目或问答竞猜。

“上帝对象”硬币的反面在对象发现自己被卷许多过程时显现出来。这是“孤岛”思维的直接结果，将模糊相关的方法归类到一个类中。在注册用户的过程中？`User` 类恰好有这些方法。需要发送用户邮件？再看一遍，`User` 类恰好有这些票子。在哪里找到一个用户发布的所有博客文章？是的，你猜对了。`User` 类拥有这一切以及更多。

在表面上，为那里所有不同的方法辩护变得非常容易。它们与用户直接相关。然而，邮件本身是一个独立的实体。博客文章也是如此。

## 讨论点

作为一个起点，让我们重新考虑一下我们的三个车辆类。

```php
class Vehicle {}
```

由于我们现在不需要考虑实现细节，我省略了它们，以便集中于生成的继承层次结构。

在下部分，我们需要考虑生产这些“商品”的工厂的层级结构。

```php
class VehicleFactory {
    public function create()
    {
        return new Vehicle();
    }
}
```

现在我们有两个继承层次结构，从祖类到父类再到子类的演进过程同样清晰。此外，我还提供了最顶层 `Vehicle` 类中 `create()` 方法的实现细节。当你考虑到派生类没有提供自己的重写实现时，这与我们的讨论是相关的。

这给了我们第一个需要考虑的变体情况：**不变性（invariance）**。应该很清楚，无论你处理的是哪一个特定的类，当你调用 `create` 方法时，你将得到一个非常具体的 `Vehicle` 类的实例。无论你在层次结构中向上还是向下移动，从产品层次中选定的结果保持不变。它始终是一个 `Vehicle` 实例。

然而，我们已经检查了如何合理地期望 `SportsCar-Factory` 为我们提供一个 `SportsCar` 实例。为了支持这一点，我们还需要在 `SportsCarFactory` 类内部实现一个重写的 `create()` 方法。如下。

## 讨论点

```php
class SportsCarFactory extends CarFactory
{
    public function create()
    {
        return new SportsCar();
    }
}
```

我们特殊的 `SportsCarFactory` 现在返回了同样专门的 `SportsCar` 实例。通过这样做，我们同时以相同的方向遍历了工厂层次结构和产品层次结构。这就是**协变（covariance）**。

为了让我们的应用程序保持类型安全，我们方法提供的返回值应该是**不变的（invariant）**或**协变的（covariant）**。

我们在这里最后的考虑是**逆变（contravariance）**。为了在我们的继承层次结构中维护类型安全，这是我们在输入参数上需要采用的。为了考虑这种类型的变体，我将引入第三个继承层次结构供我们观察。

```php
class BasicEngine {}
class RegularEngine extends BasicEngine {}
class HighPerformanceEngine extends RegularEngine {}
```

正如你所看到的，尽管是刻意设计（如果你原谅这个双关语的话）为了试图难为我们，但从通用到最专门的流同样明显。

如果我们选取“中间”的 `CarFactory` 类并为它提供 `create()` 方法，它看起来像这样：

## 讨论点

```php
class CarFactory extends VehicleFactory
{
    public function create(RegularEngine $engine)
    {
        return new Car($engine);
    }
}
```

到目前为止一切都很顺利。中间工厂接受中间引擎类型来产生中间汽车类型。然而，我已经指出过我们需要在输入参数上使用逆变。这正是它变得反直觉的地方。逆变意味着向相反方向移动。因此，如果我们移动工厂层次结构，我们需要向上移动引擎层次结构，这给了我们一个看起来像这样的 `SportsCarFactory`。

```php
class SportsCarFactory extends CarFactory
{
    public function create(BasicEngine $engine)
    {
        return new SportsCar($engine);
    }
}
```

比这更糟的可能是观察当我们向上移动工厂层次结构从而向下移动引擎层次结构时会发生什么。

```php
class VehicleFactory
{
    public function create(HighPerformanceEngine $engine)
    {
        return new Vehicle($engine);
    }
}
```

当你这样看它时，它没有任何意义，这在某种程度上是我最初构思引擎层次结构的原因。重要的考虑因素，至少在维护那个重要的类型安全方面，是层次结构中最顶层的类（即终极父类）是决定数据类型的类。

## 讨论点

在我们刚刚探索的示例中，数据类型（`VehicleFactory`）告知我们的客户端代码，引擎参数至少应该是 `HighPerformanceEngine` 实例。因此，客户端代码应该只传递 `HighPerformanceEngine` 实例，或者其更专门的（子类）版本。按照我们目前的层次结构，`HighPerformanceEngine` 是目前提供的最专门的版本。

因此，如果客户端代码始终传递高性能引擎，我们的汽车工厂将始终生产高性能汽车。但是，如果我们想能够向工厂传递一个普通引擎呢？这正是逆变发挥用场的地方。

如果我们希望工厂能够接受任何至少是普通引擎的引擎，我们需要将参数类型向上移动层次结构。这意味着工厂的方法应该接受 `BasicEngine` 而不仅仅是 `RegularEngine`。这就是逆变。

同样，如果我们希望工厂能够返回任何专门的汽车，我们需要将返回类型向下移动层次结构。这就是协变。

（注：原文后续部分存在大量重复和乱码，此处已根据前几页的逻辑流进行了清理处理。）

## 讨论点

```php
class User
{
    private $hobbies = array();

    public function addHobby(AbstractHobby $hobby)
    {
        $this->hobbies[] = $hobby;
    }
}
```

这一个非常直观。我们的 `$hobbies` 属性通过 `addHobby()` 变器方法进行修改，这允许我们以适当的方式调用状态变更。我们还可以提供一个相应的 `removeHobby()` 方法来涵盖此情况的反反面。

```php
class PlayerScore
{
    private $score;

    public function addScore(ScoreEvent $event)
    {
        $changeValue = $event->getScoreDelta();
        $changeValue = $this->applyBuffs($changeValue);
        $this->score += $changeValue;
    }
}
```

在这个示例中，我们为修改玩家得分的过程添加了多一点控制逻辑。在接口上，我们将输入参数限制为 `ScoreEvent` 的实例，这反过来应该向我们保证 `getScoreDelta()` 方法是可用的。随后，我们将产生的 `$changeValue` 传递给内部的 `applyBuffs()` 方法，以在将更改应用于我们的 `$score` 属性之前，检查玩家是否有任何激活的 buff 或增强器。

结果是，`PlayerScore` 类对其内部状态的控制比我们允许应用代码直接提供显式值要多得多。最终结果是封装得到了恢复，内部工作机制被隐藏起来，对我们的属性及其值的任何更改都按照我们的意愿发生。这正是它应该有的样子。

# 规则是用来被打破而生的

尽管我们刚刚读到第一部分的结尾，但你可能已经注意到我已经发布了相当多的规则了。既然你在这儿了，这条规则也放在这里吧，同时也请记住这三个规则。我知道，这对你来说要求很大。

幸运的是，规则是用来被打破而生的。对于我们在这些页面中检查的每一条“规则”，请记住每条规则都具有某种程度的弹性。有些规则很容易弯曲，否则它们在向错误方向受到哪怕最轻微的推力时就会断裂。除非某条特定规则属于后一种类型（即应该被视为法律），否则我不打算告诉你哪些是真正的规则，哪些仅仅是建议性的指南。我知道这听起来可能很傲慢，如果这偏离了提供充分装备以得出你自己结论的目标，我表示道歉。一个例子很快就会在我们进入关于特性的（traits）章节时出现。我会提出一条规则，但仅在我们分析这些这些事物的优缺点之后，那时我希望你会认同所呈现的规则。

在此期间，我想给你们讲一个故事。这真的不会花很长时间。

几年前，好吧，算是不长吧，我辅导一个私学生，他非常渴望开始学习对象导向的内容。从开始我就给了他一条规则：你不能直接从类创建对象，你总是必须创建一个名为工厂（factory）的类并使用它来创建对象。因此，我们创建了一个 `Class` 和相应的 `UserFactory` 类，后者包含一个静态 `create()` 方法，该方法会乐意地返回新造的对象。它生效了，证实了这条规则是正确的。

嗯，这种正确只持续到学生发现这完全是一个胡言为止。到那时，这个建议已经植下了种子，而且描述为什么这条“规则”实际上是一个非常强力的建议就变得更容易了。即使学生后来学到工厂类上的静态 `create` 方法甚至不是最好的方法，但通过通过将新对象的创建锁定在单一位置，它仍然帮助规避了许多未来的错误。这是一个胜利，但手段令人存疑。

无论如何，我们已经到了第一部分的末尾。让我用一个略显尴尬的类比把你们留在这里结束吧。

如果你早上出门时皮带系得太紧了，在路上的某一点你会停下来，把它调松一两个孔，然后松了一口气。而反之，如果你早上出门时皮带系得太松，你的裤子可能会掉下来。

# 大脑检查

我们现在真的到了第一部分的末尾了，但在继续之前，让我们回顾一下到目前为止涵盖的内容。

在某种程度上，这一节可以被视为一个术语表；它确实符合这一特定特征。然而，术语表并不是它的全部意图。相反，它是一个展现 PHP 卓越才华（PHP Brilliance）的开发者可以站出来进行闪电（lightning talk）的话题清单。

花点时间回顾一下列表。在有30分钟准备时间的情况下，你能对每个主题进行一个 10 页幻灯片、5 分钟的演示吗？在不求助于搜索引擎的情况下？

如果答案是“否”，请考虑加强你在相关主题上的知识。

# 封装与信息 / 实现隐藏

封装（Encapsulation）是将值（属性）与作用于这些属性的方法结合在一起的过程。信息/实现隐藏（Information / implementation hiding）是一种“外挂式”概念，我们可以应用它来更新封装，以提供作为黑盒运行的对象，保护它们的属性并通过良好定义的公共接口控制访问。

## 通过 setters 和 getters 暴露状态

延续封装原则，应用“愚笨的”（dumb）setters 和 getters——即除了提供访问对象属性之外什么都不做的方法——使我们容易受到由于对象对其状态失去控制而导致的漏洞的影响。魔法 `__get()` 和 `__set()` 方法可能会引起很多问题，在使用它们之前应该极其谨慎。

# 抽象与继承

延续上述，抽象（Abstraction）为我们提供了定义新类型的方法，而继承（Inheritance）允许我们提供特化。

# 多态

多态（Polymorphism）可以通过多种方式在 PHP 中实现，但并非临时多态（Ad Hoc Polymorphism），即提供相同名称的方法。我们还有子类型多态（Subtype Polymorphism），这种类型允许子类重写父类的方法。在所有多态类型中，委托多态（Delegate Polymorphism）是我们的最佳选择。最后一种类型允许我们将逻辑封装到不同的类中。

# 神对象

也被怪物对象（monster objects），这些东西出现在对象知道太多或做得太多，或者两者兼之的情况下。当问题对象应该被拆分成更小的部分时显现。

# 逆变、协变与不变性

这是一个在抽象和继承主题中起作用的关键特性。为了类型安全，理解这三种变异类型扮演的作用是关重要的。

# 扩展我们的对象大脑

> “该死的第一个周。” - MacReady

好了。所以我们在四个核心原则的世界进行了一次相当迂折的漫步，现在我们对封装、继承和多态的理解得到了加强。巩固。或者只是得到了证实。结果是，我们清除了所有脆弱的不一致性，我们这些才华团队的成员现在拥有了可以在其上进行构建的坚实基础。

进性的演进，客观地说。

这些东西一直存在。一些核心概念并不会随着“上一个、当前或下一个大热点”的短生命周期而消失。良好的原则已经存在了很长时间，这既是好事也是坏事——因为我们无法在新手开发者一上手时，就将那些优质的、可靠的理论编程知识直接塞进他们的脑子里。

我认为这是一件坏事，因为这需要时间、精力以及大量的错误，才能最终将那些好东西固化在开发者的大脑中，而这些时间我们本可以更好地用来构建下一个产物。

我也认为这是一件好事，因为无止境的发现之旅能保持人们的胃口、热情和内心的愉悦感流淌。如果你在第一次尝试 MVC 框架时感到惊艳，那么当你第一次使用 Vagrant 启动虚拟机时，是否也有同样的惊艳感？我知道我有过。这正是我非常热爱这份行业的原因。

想象一下，如果 PHP 停留在 5.2 版本，你的世界会变成什么样（哪怕只是瞬间）。如果 Zend 在那时已经完成了该语言。如果你的工作只是为又一个 WordPress 安装换皮肤，因为这就是你让应用程序上线唯一需要做的所有事情。加上插件，给这头巨兽换个壳，然后为了下一个应用再次经历那著名的“分钟安装”。

忘记那些小丑和被怪物追逐却逃得不够快的事吧。这才是真正的噩梦素材。周而复始的 Wordpress。

我们不要纠结于那个特定的反乌托邦愿景，而是迅速转向更美好的想象。我确定你已经猜到了，我喜欢在把你拖入温暖明媚的正确道路之前，先带你走一段阴暗而可怕的小路。好吧，至少是我版本中的“正确道路”。

为了公平起见，请让我带着感谢和赞美说，PHP 并没有停在 5.2 版本，而是快乐地发展到了许多阶段，其中包括一个强大得对象模型。我们知道这一点，是因为在随后的版本中出现了一些新的“好东西”。比如命名空间（namespaces）。比如闭包（closures）。

这便构成了我们继续探索 PHP 风格的面向对象编程基础的基础。书的这部分将探索近期 PHP 版本中关键“精辟”部分的概念和实际影响，以扩展我们的知识库，改进我们用于构建极佳代码库的基础工具箱。仅仅这样做，就能让我们在即将到来的光辉中增添额外的润色。

在我们做所有这一切之前，我们仍然需要对 PHP 如何处理接口（interfaces）的理解进行现实检查。那将在下一章出现。

好了。快翻页吧。

## 通过接口享受更多酒吧时光

我们在几个章节前讨论抽象时，已经触及了接口的概念。在本章中，我们将通过更详细地观察概念接口和通过同名关键字（`interface`）定义的具体接口，来进一步推进这一想法。

## 接口是……一个接口

在我们开始讨论应该如何在我们的应用程序代码中使用接口的理论之前，让我们简单地回顾一下接口是如何定义的。

```php
<?php
interface InterfaceName
{
    /**
     * 示例方法定义
     * @var mixed $parameter
     */
    public function methodName($parameter);

    // 其他任何方法定义
}
```

这一切都非常直观。在这个非常简单的接口定义中，我为仅仅的一个方法提供了规范，在这里命名为 `methodName()`。确实非常直观。

通过接口享受更多酒吧时光。

> 你可能会想，认为我忘记了这不是一本给初学者的书，但别担心，我在这里包含这些是为了提供一个共同基础，让我们从这个基础上扩展理解。

每当我们以这种方式创建一个接口时，我们是在制定一个特定的规范，规定其中声明的方法将出现在任何实现该接口的类中。这在很多地方被称为“合同”（contract），但我更倾向于称它为“保证”（guarantee）。这对我来说是个人偏好：我觉得“保证”这个词提供了更强有意图的。

在现实世界中，合同除非被违背，否则很少会成为新闻，而我们不希望这种内涵渗透到我们对接口的理解中。对于我们的目的来说，我们需要将接口视为坚如磐石、铸铁般、不可侵入、不可破解的保证。尽管如此，如果你觉得“合同”一词让你更舒服，请完全可以在随后的文中互相替换。

每当我们编写一个实现接口的对象时，我们实际上是在该对象上贴了一个标签——一个闪闪发光的荧光橙色徽章，上面写着：“嘿哥们，你不需要知道我是谁或是什么，我带着这个保证，看到了吗？你不需要我的家族史，也不需要我的大腿内侧测量数据。你只需要这个保证。有了它，你可以放心我可以做这个，还能做那个。”

无论“这个和那个”指的是什么，都取决于你作为开发者如何声明你的接口。如果你需要指定一个对象保证接收数组数据并将其转换为其他东西，你可能只需要像这样一个简单的接口声明：

```
interface ArrayTransformer
{
    public function getTransformed(array $data = []);
}
```

这是一个非常简单的保证，一个声明任何佩戴接口的对象都提供该方法的保证。

通过接口享受更多酒吧时光。



你可能会想，认为我忘记了这不是一本给初学者的书，但别担心，我在这里包含这些是为了提供一个共同基础，让我们从这个基础上扩展理解。

（注：原文后续部分存在大量重复的段落，已根据要求去重处理，仅保留核心翻译内容。）

通过接口提供更多的公开内容。

一个特定的方法被包含在一个对象中，客户端代码只对它实际上可以调用的方法感兴趣。它不需要知道对象的内部实现。同样，接口是为了实现该对象的协作者的利益而做出的公开声明。

不过，这里有几件非常重要需要记住的事情。这种重要就像“你配偶的生日是什么时候”那样重要。

第一，接口永远不会声明方法内部的实际实现逻辑。它提供的保证仅限于声明所提供的方法名称，以及每个这些方法预期的参数列表。当然，这并不保证命名的方法的行为会像方法名可能暗示的那样。那个特定的责任由你和/或你的团队成员承担。

因此，在接口中声明的方法名总是被写成单行代码，并以分号结束，如下：

```php
public function methodName($arg1, $arg2);
```

这被称为“方法签名”`method signature`，它反过来精确由方法名本身以及该方法所需的任何参数声明组成。只要机会允许，展现出 PHP 才华的开发者还会在那里添加适当的类型提示`type hints`，导致方法规范看起来更像这样：

```php
public function setAdapter(AdapterInterface $adapter);
```

第二个需要注意的重要点是，在我们等待 PHP7 成为主流期间，我们的接口无法声明调用声明方法可能返回的任何值的数据类型。这意味着现实中，即使接口保证了 `getEmail()` 将存在，这种保证也没有延伸到确保实现的方法将向你返回一个电子邮件地址，或者该返回值甚至可以是一个字符串。PHP7 在某种程度上提供了这种能力，但在此期间，责任也完全落在你和你团队的肩上。

# 抽象类也是一种接口

当然，你已经知道这一点了。特别是如果你关注过关于*抽象*`abstraction`的章节。你没关注，对吧？我们在这里有一个强化这一想法的机会，因为我们刚刚通过了代码中声明的接口应当是一种*保证*`guarantee`。

回想一下关于*抽象*的章节。在这里，我们花了大量的时间探索抽象类是定义新数据类型的一种手段。我们认识到，PHP 给我们的原生数据类型对于我们的目的来说并不够。是的，我们可以在关联数组中调用用户数据，但它并不能充分代表我们对“用户”到底是什么的构想。它之所以不具备 *User* 类型数据的属性和特征，仅仅是因为它具备 *Array* 类型数据的属性和特征。

这也是这里的关键点。

现在既然我们花了这么多时间编写*接口*`interfaces`来表示一种有保证的行为，我们应该能够将同样的“保证”概念应用到抽象类提供的各种*接口*上。

但这里的关键区别在于，抽象类还可以提供实际的实现逻辑。提供的保证可以扩展到包含声明方法的逻辑实现。让我们看看早期的示例如何调整以适应我们这里的需求：

```php
abstract class AbstractRenderer
{
    private $data;

    public function setData(array $data = [])
    {
        $this->data = $data;
    }

    abstract public function getTransformed();
}
```

在这里，我们声明了一个名为 *AbstractRenderer* 的新数据类型，它为应用程序的其他部分提供了一个*接口*。这个*接口*规定，当客户端代码看到数据类型为 AbstractRenderer 的对象时，可以确保有两个方法可用。第一个是 `$data` 属性的 setter 的完整逻辑实现。第二个 `getTransformed()` 将是任何派自此数据类型蓝图的子类提供的特殊方法。我们知道这一点，是因为 `getTransformed()` 方法被声明为抽象的`abstract`。

让我们来看完整的实现。

```php
class CsvRenderer extends AbstractRenderer
{
    public function getTransformed()
    {
        // 将 $data 转换为 CSV 字符串的逻辑。
    }
}
```

当我们实例化 `CsvRenderer` 时，我们可以非常清楚地看到（很大程度上是因为这段代码很精简），抽象父类声明的接口在派生子类中得到了完全遵守。我们的保证已经到位。我们稳如磐山。

抽象父类为我们安排了所有重要的属性和特征。就像我们可以编写处理整数和数组的代码一样，我们也可以编写处理 AbstractRenderers 的代码。

遗憾的是，现在轮到了某些能力较弱的开发者开始出错了。让我们修改我们的抽象类来帮助说明接下来的点。

```php
abstract class AbstractRenderer
{
    private $data;

    public function setData(array $data = [])
    {
        $this->data = $data;
    }

    public function getTransformed()
    {
        return print_r($this->data, true);
    }
}
```

引入了一个微妙的差异，这种差异并不像我们希望的那样不常见。我们没有将 `getTransformed()` 方法声明为抽象的`abstract`，因此要求在派生子类中有特定的实现，我们在这里做的是对方法本身的实际逻辑实现。

这种方法的通常理由是，我们想为子类提供某些默认行为。但如果一个子类本应该提供自己的实现却忘记了，这就会导致问题。这就是为什么 `abstract` 关键字如此重要；它强迫子类提供自己的实现，否则代码将无法运行。

在我们的案例中，我们通过显式声明 `getTransformed()` 方法返回字符串，改变了接口。无论由哪个子类提供实现，这是一个客户端代码可以赖的保证。

```php
return print_r($this->data, true);
```

只要你记住抽象父类现在提供了一个包含返回类型的扩展保证，这可能就不那么担心。该保证是为了告知客户端代码该数据类型的行为。因此，我们的责任确保每个派自父类的类都遵守这一保证。

幸运的是，PHP7 的变化在某些方面缓解了这种情况。我将如何实现它的细节包含在你希望查看的附录中。

# 变量常数的奇案

这个想法一直从某种程度上让我感到“坐立不安”，尽管它显然是一个非常有用的功能。作为一个是如此守规的人，常量可以拥有变量值的想法只是让我感到，我不知道，怎么有点发痒。至少当我记得类常量可以持有标量值时，我可以早点松口气。

```php
class AbstractDataTable {
    const TABLE_NAME=null;
}
```

```php
class UsersTable extends AbstractDataTable {
    const TABLE_NAME="users";
}
```

```php
class OrdersTable extends AbstractDataTable {
    const TABLE_NAME="orders";
}
```

通过接口获得更多的发布时间。

显然，这是应用程序持久化层的一个部分，它似乎将提供对象属性与数据库表之间的映射。常量 `TABLE_NAME` 的可变性通过在 `childish` 类中重写并重新声明该常量来实现。这非常直观且确实非常有用。当然，该值的常量性在类内部得以维持，随后从该类创建的任何实例化实例中也是如此。

例如，你无法编写在运行时修改 `TABLE_NAME` 常量值的代码。如果这是可能的话，坦率地说，我们会去切换语言了。

# 常量常量的快乐介绍

然而，你确实拥有创建“常量”的能力。这些常量在编译时或运行时都无法被任何东西改变。如果你有一个需要真正不可更改的常量常量的情况，你可以将其写入接口中。

为了说明这个观点，这里有一个代码示例。

```php
interface MathConstantsInterface
{
    const PI = "3.14159266";
    const GIBBS = "1.85193705198246617036";
}
```

```php
class MathConstants implements MathConstantsInterface
{}
```

```php
print MathConstants::PI; // output - "3.14159266"
```

搞定。通过提供一个真正不可更改的常量，恢复了理智。`MathConstants` 类无法无法提供它自己的常量定义，否则会导致 PHP 解释器以致命错误退出。因此，如果你需要一个可以通过你的类定义访问、并保证在任何实现类中都无法被更改的硬编码值，那么在接口内部提供常量是可行的方案。它带给你与通过过程方式使用 `define()` 函数相同的常量性，但又避免了污染全局命名空间带来的头疼问题。

## 哪个是哪个？

这并不是一个常见的问题：什么时候应该使用抽象类，而什么时候应该倾向于使用接口？坦率地说，我们已经有一个相当完善的答案来决定采取最合适的路线。

当我们回想起对象应该被分为*知情者*`knowers`和*执行者*`doers`的这一观点时，答案的一半已经为我们提供。作为一个通用的经验法则，*执行者*应该配备一个*接口*，并佩戴着那个引人注目的徽章，上面写着：“嘿，伙计，这就是我能做的。”

这就留下了另一半问题来回答系统中的*知情者*。既然我们已经确定*知情者*是充当数据管家的人，那么建议他们可以自动被视为数据类型难道不合理吗？如果是那样，我们难道不应该走提供抽象类的路线吗？

这些问题的答案同时是模棱两角的“是”和“否”。

你在这里需要做的是暂时抛弃“知情”这一方面，而实际上考虑你所面临的需求。我们已经考虑过提供抽象类是指定新数据类型的一种手段，但这个*特定的知情者*会从被定义为数据类型本身中受益吗？

让我们看看 PHP 世界中一个相当常见的用例。如果你在一个类似 MVC 的框架内工作，那么我们知情者的主要来源将位于模型层。根据定义，这就是模型层应该代表的：存在于我们应用程序中的数据。模型层中唯一的居民将是能够在它们运行的上下文以及模型内数据范围内封装应用程序业务逻辑的类。不需要太多思考就能判断出，浮动在那里的业务逻辑单元已经可以归类为*执行者*，因此，我们已经确定它们更可能需要一个接口而不是抽象父类。

现有的某些框架希望你将模型层视为数据库访问层。如果一个第一次发现 MVC 的开发者恰好选择了这些“模型等同存储”框架之一来方便他的学习，那么这个想法很有可能刻在他们的脑海中。这种类型框架的关键问题在于，它们倾向于对其存储解决方案施加不必要的限制。当你正确地分离模型层`数据`和持久层`处理数据的代码`时，你将更有能力为每个特定的数据元素找到合适的存储解决方案。用户？嗯，他们使用 RDBMS，正如我完美喜欢的那样。这些用户创建的可搜索博客文章？我们将它们存储在像 MongoDB 或 ElasticSearch 这样的文档数据库中会有更好的服务。我们用户的朋友和关注者呢？显然，如果我们预见到需要将应用程序扩展到几千个用户以上，我们应该追求一个能够适当让数据层和存储层良好分离的解决方案。在一个基础模型专门设计用于读写 RDBMS 的框架中，你是做不到这一点的。

然而，框架指望你通过扩展框架本身提供的基模型来创建模型类，这并不罕见。框架的基模型是一个合适的数据类型定义吗？这个问题很少会得到肯定的回答，原因很简单，基模型往往被加载了许多便利方法。

举个例子，Sitepoint 最近进行的框架调查显示 Laravel 是明确的获胜者。然而，Eloquent ORM 的实现提供了一个完全充斥便利方法的基类。不要误会我，Laravel 并不是唯一的罪魁祸首，但当开发者使用这个框架时，他们在写第一行代码之前就已经导入了 3000 多行便利方法。

这样的开发者能记住这种基类中定义的每一个方法，并避免意外覆盖某个方法吗？记住，我们的客户端代码将依赖于这些接口来确保特定的运行模式，这是重要的。

> http://www.sitepoint.com/best-php-framework-2015-survey-results/

这一点不言而喻。此外，期望他们这样做完全是不合理的。举个例子，那里有一个 `toJson` 方法；这是一个非常典型的便利方法。但在响应 API 调用或 AJAX 请求时渲染模型数据时。

回到正点，如果我们的模型类已经扩展了框架的基模型，我们就再无法做出是否应该提供抽象类的决定了。接口尽管可能已经杂乱不堪，但它已经放弃了控制权。

这种情况真的必须如此吗？

幸运的是，一切还没有失去，更好的是，我们通过查看一种更面向领域模型的方法，已经发现了解决方案。你可能在这段代码中至少认出来自书第一部分的一些影响：

通过接口获得更多的发布时间。

145

```
class UserDataTransport
    extends WhateverFrameworkAbstractModel
    implements StorageInterface
{
    ...
}
```

是的，我们把框架的基础模型类封装在一个任意的 `UserData-Transport` 类中，通过这种方式，我们重新获得了对模型及其接口决策过程的控制权。看这里。

```php
class UserModel
{
    private $userDataTransport;
    public function __construct(StorageInterface $userDataTransport)
    {
        $this->userDataTransport = $userDataTransport;
    }
}
```

我们正在进行类型提示的这个接口是什么？坦率地说，任何我们想要或需要它成为的东西——它为我们提供了机会，传入任何能够履行携带实际数据值并为触发数据存储提供某种触发钩子的对象。我们失去的是对模型单一接口上呈现的仅限 CRUD 的便利方法集合的即时访问，但我们重新获得了对接口本身的完全控制。这对于实现 PHP 的卓越表现至关重要。当我们的对象基于扩展臃肿的抽象时，它们根本无法采用激光聚焦的意图，但当我们抽象掉这些臃肿的抽象时，它们就能恰好做到。

现在我们终于可以实现我们的目标了——由我们自己决定模型对象是否受益于一个声明的抽象数据类型。我想问，为什么不呢？如果你的应用程序将处理许多不同类型的用户，你可以自由定义一个 `User` 数据类型并创建所需的专门化。你发现你需要声明不同类型的产品？尽管去用吧。你自己的社交网络可能充满了多样但易于识别的数据类型。

通过接口获得更多的发布时间。

尽管如此，记住模型中的数据在每次请求之间仍然需要被持久化是有价值的。然而，如何实现这一点的细微细节超出了专门探讨接口的章节的范围。为此，我将只给你留下一些可以作为 `StorageInterface` 起点的内容。

```php
interface StorageInterface
{
    public function setStorageAdapter( StorageInterface $adapter );

    public function getStorageAdapter();

    public function create(array $data = []);

    public function read($id);

    public function update($id, array $data = []);

    public function delete($id);
}
```

仅仅这样做还有另一个重要的副作用：存储适配器将很容易被 mock 模拟，从而产生可以飞速运行的单元测试套件。

## 为我们的空间命名。

我们使用命名空间`namespaces`已经六年了，你不是已经在用了吗？实际上你确实用了，我们都在用，无论我们是否意识到这一点。在 2009 年 `namespace` 关键字出现之前，编写的每一行代码最终都落在一个空间中：全局`全局`或根命名空间。

命名空间是许多编程语言的共同特征，这非常有道理，因为它们很好地赋予了我们恰当、智能且符合逻辑地将代码组织成合理单元的能力。

### 命名空间之于代码目录之于文件

由于缺乏定义命名空间的能力，我们面临着两个竞争性的问题。

第一个问题源于一个事实：你不能在同一个作用域内声明多个同名的类或接口。这门课程是完全合逻辑的——如果你提供了自己的版本，你无法合理地期望 PHP 解释器从正确的 PDO 类中可靠地实例化对象。这可能是被称为“冲突”`collision`的现象最直观的表示。如果语言本身在全局命名空间内提供了一个命名类，你就被剥夺了在你的类中使用相同名称的机会。

这种问题以一种更为隐蔽的方式出现，当你开始向项目引入第三方代码库时。

考虑一下如果你在全局命名空间中定义了自己的 `User` 类会发生什么。看起来很合理，对吧？但接着你又添加了一个带有自己的 `User` 类的第三方库呢？你必须承认“User”这个名字是一个非常流行的选择，但现在你的应用程序就会崩溃。PHP 将仅仅因为存在两个竞争的类名而拒绝运行它。为了修复这个问题，你可能会想将你的类重命名为 `MyUser`。呃！

为我们的空间命名。

我为这一节的副标题使用了目录和文件的类比。现在引入这种比较正合适。在指导团队成员关于命名空间时，我们可以从文件系统的根部开始。在基于 Windows 的机器上，通常被称为“C:\”，但由于我是 Linux 人，我将坚持极其简单的且类 Unix 的“/”。文件系统的根目录与我们代码中的全局命名空间可以直接对比。

我们可以问开发者他们是将创建的文件都放在一个根位置，还是还是使用目录为代码库的布局实施一些理性和秩序？这当然是一个修辞性问题。任何对音乐充满热情的人机器上可能都有成百甚至上千个 mp3，但它们不会保存在同一个 `$username/Music/` 文件夹中。极有可能，它们会被组织成文件夹。首先按艺术家的命名，然后按专辑标题，产生一个像这样的文件夹结构。



```
/home/thunder/
Music/
haus/
Crackle/
Iron Slave/
Metallica/
Master of Puppets/
```

这是直接在文件系统内运行的命名空间——材料的逻辑收集。当考虑到这个类比时，很难看出为什么不使用它。显然，通过提供适当的命名空间，类本身变得更短、更简洁且更容易理解。这两个问题都可以通过应用自定义命名空间轻松解决，这赋予了我们将类准备成合理单元的能力，正如将文件组织成目录一样。然而，我不希望被视为推广一个旧框架，所以我将切换到一个更现代的选择。

为我们的空间命名。

```php
<?php
/**
 * 此文件是 Symfony 程序包的一部分。
 * (c) Fabian Potencier <fabian@symfony.com>
 *
 */
namespace Symfony\Component\Console;

class Application
{
    ...
}
```

这是 Symfony 控制台组件中 `Application` 类的精简表示，但你不需要我告诉你这些，对吧？我关于这段代码的所有说法都可以从类本身以及它所属的命名空间中推断出来。我认为这是通过适当命名空间代码可以实现的清晰度的最佳示例之一。

要围绕 Symfony 控制台组件构建命令行工具，你只需要创建一个 `Application` 类的实例，配置该实例，然后调用 `run()` 方法。

现在你可以在你的新语句中使用完全限定类名，它看起来像这样：

```php
$myApp = new \Symfony\Component\Console\Application();
```

你可能会注意到我在引用 Symfony 控制台应用类时包含了一个前导 `\`。这纯粹是为了确保我们通过“绝对”命名空间路径引用它。如果没有前导 “\”，命名空间将以相对方式解析，这是一个产生许多困惑的潜在来源

但使用完全限定类名并不回到 ZF1 示例中所示的那些非常长的类名好到哪里。

不要担心，通过 `use` 关键字的力量恢复了易用性。

## 为我们的命名空间命名。

```php
<?php
use Symfony\Component\Console\Application;
...
myApp = new Application();
```

搞定。我们的代码再次恢复了清晰。`$myApp = new Application();` 这一行的意图显而易见，不需要我们费心去解析命名空间。这是因为 `use` 关键字为我们导入了该定义。

然而，虽然我们解决了类名问题，但再次引入了命名冲突问题。使用“Application”作为类名在 Symfony 组件中并不独特，就像在其他框架一样，这是一个非常常见的选择。事实上，我们可能都想使用同一个单词。

```php
<?php
namespace CompanyName;

use Symfony\Component\Console\Application;

class Application {
    private $app;

    public function __construct(Application $app) {
        $this->app = $app;
    }
}
$myApp = new Application();
```

即使 PHP 允许你这样做，你也将需要花费费力去解析代码里到底在发生什么。所有的清晰度再次丢失了，因为你只能假设作者的意图是在构造函数中通过传递 Symfony Console 的实例来实例化自己的 Application 类。在当前作用域内重新声明 Application 是毫无意义的，因为 PHP 会因此卡死并崩溃。

尽管如此，我们可以通过对导入的类使用别名（aliasing）来修复这个问题，从而允许声明自己的 Application 类。

```php
<?php
namespace Company\AppName;

// 格式："use $fullPath as $localName"
use Symfony\Component\Console\Application as $sfApp;

class Application
{
    private $sfApp;

    public function __construct($sfApp)
    {
        $this->sfApp = $sfApp;
    }
}

$myApp = new Application(new sfApp());
```

任务完成。我们现在不仅解决了命名冲突，同时也明确了意图。虽然涉及的内容不多，但至少不需要费费精力就能确定 `Application` 实例是为了组合 Symfony Console 的实例。

在最后那句话中，我刻意地使用了“组合（compose）”这个词，因为这是我将命名空间的通用概念引入 PHP 领域的章节。

“一个框架搞定一切”的单体时代正在走向结束，至少在构建商业应用程序方面是这样。这并不是说我们要突然从头开始构建一切。事实上，我们已经确定重新造轮子是非常浪费时间的行为。尽管如此，我们不再需要为了运行项目而选择这个框架或那个框架。

近年来，在应用程序设计中使用组件库的趋势非常稳定且在加速，其原因显而易见。每个 Web 应用在核心处都有相同的需求。简单的列表如下：

| 组件 | 提供 |

| --- | --- |

| 路由 | 将请求路径映射到负责生成响应的代码 |

| 数据库/存储 | 大多数应用需要在某处存储数据 |

| 模板 | 简化/标准化生成响应体的过程 |

在实际应用中，高级组件的列表增长非常快：缓存、身份验证、授权和配置等等，只是我们常见的额外功能。当我们考虑到目前没有一个框架能为我们的所有需求提供最佳解决方案时，使用完整的单体框架变得越来越难以证明。

展现 PHP 才华的开发者不会满足于仅仅“凑合”，因为混合匹配“最佳”组件的能力字面上来说是触手可及的。

如果你在应用程序中需要最佳路由解决方案，只需执行以下命令即可：

```bash
composer require league/fastroute
```

如果你已经猜到了，这正是我之前提到“组合（compose）”一词的原因。Composer 的强大在于你可以在几小时内拼凑出自己的类 MVC 框架，一个为每个高级需求都使用最佳组件的框架。

> ^7 https://getcomposer.org/

这完全否定了这种观点：即全能型一个框架”的方法除了开发者对某个框架的熟悉所带来的启动优势外，没有任何其他好处。当然，我并不是建议你立即开始重写现有应用程序以从单体切换到组件库，因为每当开发者开始一项新工作时，代码中就会产生某种脆弱性。但我建议的是，你可以以组件库的方式来探索自己的应用程序——仅仅通过使用 fastroute，你可能会让自己惊讶。

- 尽管如此，我还应该指出，“单体（Monolithic）”一词指的是那些不仅在一个包内提供所有所需，而且让开发者难以更换更好的模板引擎的框架。如今许多流行的框架也都在走由 Composer 管理的组件化路线。无论如何，最终都应该归结为为任务选择最好的工具。

## Composer 与命名空间有什么关系？

事实证明，关系很大。随着 Composer 作为依赖管理器日益普及和使用，越来越难以忽视它促进使用 PSR-0 以及最近的 PSR-4 标准作为自动加载器的方式。我在这里不会介绍这些标准，因为它们在稍后会进行更详细的探讨。在此只需说明标准中设定的严苛要求实际上让我们开发者更容易对代码施加逻辑顺序。这既适用于代码本身，也适用于它在文件系统中的布局。

让我们来看一个例子：

```php
<?php
namespace Vanguard\BlogService;

use Vanguard\Service\ControllerInterface;

class PageController implements ControllerInterface
{
    ...
}
```

## 为我们的命名空间命名。

它变成了 `PageController.php`。我们确实需要遵守 `.php` 强制性文件扩展名，但由于我想我很长一段时间以来在野外没有见过除了 `.php` 以外的其他东西，所以这没什么好提的。

正如你所看到的，Composer 为了满足 PSR-4 标准对我们施加的最低要求是非常容易实现的。不仅如此，它们也非常合理！剩下的唯一工作就是告诉 Composer 的自动加载器（autoloader）如何找到正确命名的类。

这是通过在 Composer 的配置文件 `composer.json` 中添加一个 autoload 条目来实现的。我们上面的简单示例将产生一个看起来像这样的条目。

```json
{
  "require": {
    ...
  },
  "autoloader": {
    "psr-4": {
      "Vanguard\\": "src/"
    }
  }
}
```

我们在这里所做的只是提供了一个简单的键值对，告诉符合 PSR-4 标准的自动加载器：以 "Vanguard" 命名空间开头的类可以在相对于 `composer.json` 文件本身的 "src/" 目录下找到。

然而，我们的工作还没有完全结束。我们只是告诉了 Composer 我们的 vendor（供应商）命名空间。为了保持合规性（以及功能性！）我们仍然需要考虑在删除 vendor 前缀后剩余的任何子命名空间。在我们上面的示例中，我们的命名空间是 "VanguardController"。一旦我们从列表中删除了 "Vanguard" 前缀，剩下的就只有一个子命名空间，即 "Controller"。PSR-4 告诉我们，它应该直接映射到我们在 `composer.json` 中映射到前缀的目录下的子目录。再次，拼写和大小写在这里是非常重要的。

这引导我们得到了类似这样的文件系统布局。

```text
$PROJECT_ROOT/
composer.json
src/
// 此目录映射到 "Vanguard" 前缀
Controller/
Interface/
ControllerInterface.php
PageController.php
Service/
BlogService.php
Auth/
Strategy/
Acl.php
```

正如你所看到的，即使是遵循 PSR-4 标准的最基本应用，也能得到一个既整洁又又非常有逻辑性的文件系统布局。为了进一步说明，我还包含了一个被称为 "VanguardAuthStrategyAcl" 的类的路径，仅仅是为了展示这里的每个命名空间（"Auth" 和 "Strategy"）如何对应于同名的目录。采用这种方案意味着类的自动加载问题已经得到解决。一如既常，永不重复造轮子是非常非常明智的事。

> 你可以通过其 `composer.json` 文件向 Composer 提供许多选项，但我们将在书的后部分介绍这些内容。

虽然我在这里只展示了一个非常简单的策略，但更常见的情况是“扩展”我们使用的命名空间前缀，以提供项目层面的隔离。如果说 vendor 命名空间代表你（或你的公司），那么第一个子命名空间可以用来指示你正在工作的特定项目。

对上面的示例进行微小的修改，结果将如下所示。

为我们的命名空间命名。

```php
<?php
namespace Vanguard\MyApplication\Controller;

use Vanguard\MyApplication\Service\BlogService;
use Vanguard\MyApplication\Controller\ControllerInterface;
```

```php
class PageController implements ControllerInterface
{
}
```

那里唯一的变化是我在命名空间声明中插入了 “MyApplication”。我们是否应该将所有代码移动到一个新的 “MyApplication” 文件夹中？嗯，如果我们愿意的话可以这样做。如果我们预见到这个特定的项目目录最终将包含多个子项目，那么这样做是有意义的。否则，没有重新组织项目的文件系统布局，我们只需要告诉 Composer 命名空间前缀已经更改。

```json
{
  "require": {
  },

  "autoloader": {
    "psr-4": {
      "Vanguard\\MyApplication\\": "src",
      "Vanguard\\MyPackage\\": "lib/mypackage/"
    }
  }
}
```

为了说明如何适应一个新的子项目，我在自动加载规范中添加了第二个条目；它将命名空间 “VanguardMyPackage”映射到一个新目录。即使你不使用 Composer 来引入和管理外部依赖，只需对自己的代码遵循这些命名空间指南并对 `composer.json` 进行适当修改，自动加载就会变得简单且完全无忧。

既然项目已经有了免费且简单的自动加载解决方案，只需遵循它要求的标准，就能让我们的项目在通往高度清洁和逻辑分离道路道路良好开始，非常就像一个组织良好的 mp3 集合。显然，我无法自动为我们提供“正确”的目录及其相应的子命名空间，但我们对框架的接触极有可能意味着我们已经知道了大多数流行的选择。

# 结论

如果我能把这一章浓缩为五个词，那就是“命名空间一切”。

表达良好的特性（Traits）。

在抽象基类中添加便利方法并不是良策，因为通过继承进行代码复用是非常糟糕的事情。

当然，既然我们现在处于特性的（Traits）这一章节，我们应该看看如何通过 trait来实现它。首先，我们将从修改后的模型类开始。

```php
<?php
// File: src/Model/UserModel.php

namespace Vanguard\MyProject;
use Vanguard\MyProject\Persist as MySqlStorageTrait;

class UserModel
{
    use MySqlStorageTrait;
    ...
}
```

在这里，我们已经有几点需要检查。在类 {} 定义本身之外，我使用了 `use` 关键字将 trait 导入到当前作用域，并对类进行了别命名，以便我们可以在本地作为 `MySqlStorageTrait` 引用它。

在类定义内部，我正在告诉 PHP 解释器将别名为为 `MySqlStorageTrait` 的 trait 内容复制到我使用 `use` 关键字的位置。这里有一个非常重要的区别需要说明——在执行任何代码之前，带有 `use` 关键字的行将被其所引用的 trait 的全部内容替换。PHP 在内部使用完成的类定义之前，需要知道类的最终结构是什么样的。我知道这偶尔会让开发者感到困惑，值得指出的是，这阻止我们使用变量（例如 `$trait`）来标识要使用的实际 trait。

无论如何，让我们来看看这个 trait。

```php
<?php
// File: src/Persist/Mysql.php

namespace Vanguard\MyProject\Persist;

trait Mysql
{
    public function save()
    {
        ... // 触发存储
    }
}
```

同样，这是一个非常简单的示例。如你所见，trait 只包含了 `save()` 方法，而该方法之前位于 `UserModel` 类中。如果我们记住，大括号之间的内容将被复制并粘贴到目标类中，那么我们应该能够推断出 PHP 看到的“完成”的类定义实际上与第一个根本没有引用 trait 的示例是相同的。

为什么这样做是有利的？

这个示例的即时好处有三点。首先，从理论上讲，我们现在可以通过在目标类的适当位置添加 `use MySqlStorageTrait;`，为我们选择的任何类提供该 trait的功能。

其次，由于可复用的代码存储在单一位置，因此更容易维护。如果我们需要对 trait 的内部逻辑进行更改，甚至提供额外的功能（例如，一个删除方法？），这相对容易做到。由于我们拥有单一的、权威的代码来源，我们成功地避免了代码重复，不再需要搜索该代码出现的每个实例。胜利。

最后，它使得在编译时切换存储策略变得非常简单。假设你已经在后台准备好了适当的迁移脚本，将某个特定模型的 `MySqlStorage` 切换为 `MongoStorage` 变得非常容易。胜利。

这比在基类中编写特定于 mysql 和 mongo 的便利方法要好吗？肯定的。这是一种明智之举吗？绝对不是。

表达良好的特性。

164

哈？

在展示了 trait 的三个看似积极的方面之后，我现在似乎正试图通过拒绝这个想法来让你困惑。这到底是怎么回事？

主要，trait 的作用是为具有交叉关注点的对象提供可复用的代码。换句话说，否则之间之间没有明显关系的对象，现在有机会实现一个公共方法，而开发者无需诉诸实际的复制粘贴，也不会触犯创建一个通用基类来放置所需方法（们）的错误。这正是它们的初衷，我之所以提出“可切换策略”的情况，是因为我实际上在野外环境中遇到过这种方法。事实上，有许多更好的方法来实现可切换策略，当我们进入连接架构和应用程序设计的章节时，会有深入介绍。

与此同时，让我们花点时间检查一下防蛇手套是否戴得很紧。

我们通过上面那些示例引入的关键问题（这对于所有 trait 的用法都是如此），是我们在修改了消费类的接口，而没有提供我们已这么做的任何指示。在我们费了这么多精力去赞扬将概念接口表示为一种保证的处处，通过简单地应用 trait，我们现在却提供了无保证的功能。

如果我们的目标之一是确保代码库保持健壮且能够抵抗错误，那么我们需要提供一个接口（interface）。为了提供适当的说明，我将切换到一个更常用的引用示例。



```php
<?php
interface Loggable
{
    public function log($msg, $level);
}
trait LoggingTrait
{
    public function log($msg, $level)
    {
        ... // 写入日志
    }
}
class AnythingThatNeedsLogging implements Loggable
{
  use LoggingTrait;
```

我在这里排除了命名空间声明是为了保持清晰，但如你所见，我们的恐慌结束了。消费 `LoggingTrait` 的类现在通过实现相应的接口，同样保证它具有 `Loggable` 功能。

这应该是我们的黄金法则：对于我们创建的每一个 trait，我们都应该提供一个相应的接口定义，涵盖在该 trait 中定义的方法。任何随后的消费 trait 的对象也应该实现相应的接口，以保持其保证的完整性。

# 见死的泄露型特性（leaky traits）

由于我们实际上无法直接在 trait 上指定接口，我们已经看到我们需要为该 trait 提供一个独立但非常具体的接口声明。我将其定为黄金法则的显式原因是，如果不这样做，将在将来开启某些相当多 Bug 的场景大门。尽管如此，trait 仍然可能对消费它的任何类的结构产生直接影响。这就是我所指的“泄漏型” trait。

当一个 trait 具有自省性并且仅关注它自己的内容时，我们可以认为使用它是安全的。它的边界被定义良好。这种整个操作模式封装在它自己的大括号作用域内。在这种情况下，我们就拥有了一个非泄漏的 trait。

然而，由于 trait 本质上是由普通的 PHP 组成的，一个缺乏经验的开发者可能会开始在我们之前的密不透水的船身上打洞，导致 trait 的关注点滴落处处。

## 如何做到的？

我们将检查的第一种泄漏方法是通过将 trait 方法声明为抽象的（abstract）来实现的。通过将方法标记为抽象的，trait 要求任何消费类都必须提供该抽象方法的具体实现。回到我们的 `LoggingTrait` 示例，我们可能会得到类似这样的代码。

```php
trait LoggingTrait
{
    private $logger;

    public function log($msg, $level)
    {
        $filename = $this->getLogFileName();
        $this->logger->setFileName($filename)
        ->log($msg, $level);
    }

    abstract public function getLogFileName();
}
```

表达良好的特性。

通过这种方式，我们规定了需要消费 `LoggingTrait` 的类也必须提供 `getLogFileName()` 方法，因为 trait 中的代码现在依赖它。这是我们的第一种泄漏抽象，承认，这不是一个糟糕的泄漏。我们的 trait 表达了必须提供以使 trait 类正常工作的外部依赖。由于需求是显式的，我们可以相应地修改 `Loggable` 接口来适应它，一切应该是好的。任何想要消费该 trait 的类也应该实现为 trait 提供的接口。

然而，我们陷入了一些困境。我们应该清楚这一点：接口是为任何遇到接口的客户端代码的特定利益而提供的保证的公开表达。`getLogFileName()` 应该是消费者公共保证的一部分吗？在这一特定实例中可能不是。对于你自己的应用程序，这取决于对你的消费类需要提供什么的了解。在上面的示例中，我们可以修复这一点。但我们的下一个泄漏示例是无法通过接口防御的。它发生在 trait 中的代码引用了在消费类中应该存在的属性。

## 良好的特性（Traits）。

```php
trait LoggingTrait
{
    private $logger;

    public function log($msg, $level)
    {
        $this->filename = $this->logFileName;
        $this->logger->setFileName($filename)
        ->log($msg, $level);
    }
}
```

尽管 PHP 非常乐意让我们这样做，但出于某些显而易见的原因，我们绝对不能让这种情况发生。不仅适用于属性，也不适用于类常量。当然，我们现在可以向 trait 对应的接口中添加常量定义，但我们现在很清楚，在接口中定义的常量仅仅是“常量级”的常量，我们实际上是在完全浪费时间。消费类无法更改它，因此不如直接写在 trait 中。

无论如何，我们的 trait 已经过度关注了边界之外的事物。如果它无法在相应的接口中涵盖，它就不应该包含在 trait 的代码中。方法是安全的，因为它们确实有机会出现在接口中。常量有时是安全的，只要我们记住，在接口中声明时它们会变成不可变的。当一个 trait 引用定义在外部的属性时，它永远是不安全的。

我们的下一个“泄漏”场景桥接了之前的泄漏与方法重写这一更通用问题之间的鸿沟。它也非常棘手。

## 良好的特性。

```php
use Vanguard\MyProject\Logging\SimpleLogger;
```

```php
trait LoggingTrait
{
    private $logger;

    public function __construct(\SimpleLogger $logger)
    {
        $this->logger = $logger;
    }

    public function log($msg, $level)
    {
        $this->logger->log($msg, $level);
    }
}
```

“这到底什么鬼，”我听到你这么说，我想补充一句，你说得完全如此。

是的，尽管我认为这有些许疏忽，但 PHP 的 trait 系统允许你尝试为使用该 trait 的任何消费类提供你自己的自定义构造函数。如果消费类接受了该构造函数，那么你真的陷入困境了，因为类自身的构造函数在从该类实例化的任何对象的设置过程中，起着至关重要的作用。

在我看来，这不仅仅是一个泄漏——它是对我们应用程序其他部分的清晰切分。从逻辑上讲，trait 不应该在管理可能消费它的对象的实际设置中起任何作用。这种想法完全超出了其自身关注的边界，尤其是当你回想起一个旨在为原本毫无共同点的对象提供通用功能的 trait 时。

你可能已经注意到，对于构造函数是否真的成功粘贴到消费类中，我表现得有些闪烁，事实证明这是很有理由的。这一点正是我们开始从“泄漏”转变为“如履薄冰”。

# 我该如何确定谁得到了什么？

每当你将一个 trait 导入到消费类时，通常是因为该 trait 代表了两个或多个不相关类所需的某些功能。正如我们已经看到的，traits 为我们提供了一种方便的方法来创建可用代码，而无需诉继承。这部分我们已经理解。

当我们意识到 trait 内部的内容只有在消费类没有先声明同名方法的情况下才能被成功导入到消费类中时，事情开始变得有些棘手。或者换句话说，只有那些在消费类中已经不存在的方法才会从 trait 中导入。

这就是为什么我之前在包含构造函数定义的 `LoggingTrait` 示例中表现得有些闪烁。trait 版本的构造函数只会导入到尚未声明相应构造函数的类中。

这有多棘手？显而易见，trait 代码的结果依赖于那个 `logger` 属性，但指定一个需要构造函数的路径会导致……

## 表达良好的 trait（特性）。

当你在 `use` 声明中间遇到这个笨拙的关键字时，你需要去查看包含该未成功方法的 trait。你是否满意该方法对于 trait 的操作来说是完全最优的？这不仅需要考虑当前的情况，还要考虑所有情况。如果另一个团队成员倾向于使用一种不同的方法而不是这一个，会导致 bug（错误）的产生吗？

当然，我们可能会倾向于对 trait 的方法进行“伪命名空间”处理，以避免任何冲突的可能性，但正如我们所见的那样，当需要封装时，就应该使用封装。

最后，我们来到了优先级层次结构中的最后一层。当一个消耗 trait 的类本身通过继承的奇迹派生自父类时，父类中声明的任何方法都将被子类所消耗的任何 trait 中同名的方法所覆盖。当你回想起 trait 质上就是一个自动复制粘贴机制背后的机制时，这在实际上是符合逻辑的。最终结果与直接在子类中编写重写方法的结果是一样的。

然而，由于重写方法对开发者来说并不是立即可可见的（它们被“隐藏”在 `use` 关键字后面），因此务必应该保持谨慎，以确保 trait 的方法不会意外覆盖父类声明的任何方法，尤其是因为父类向我们代码的其他部分提供了那至关重要的接口保证。换句话说，trait 可能会破坏你的数据类型定义，而在问题出现之前，你可能根本察觉不到。

## 瑜洋问题（Yo-Yo problem）……水平化

我并没有为了支持 trait 而描绘一幅美好的蓝图，对吧？然而，它们为我们提供了一种实现代码复用的非常有力的手段。我们已经知道我们的应用程序应该是 DRY（不要重复自己），而不是 WET（湿代码）。我们已经知道，在整个应用程序代码库中重复相同的代码段在未来只会导致维护的噩梦。

尽管我已经带我们经历了一段相当噩梦般的图景，但我们对 trait 带来的问题的考虑还没有结束，尽管我承诺这是最后一个了！

## 表达良好的 trait。

这是我已经简要提到过的一点，它关乎可见性问题。当开发者查看某个特定类的代码，而该类消耗了一个 trait 时，推导出开发者面前不再有完整的蓝图了。除非他们同时将两者并排打开。考虑到我们的代码是为特定的人类阅读而写的，我们需要确保他们能够接受这样一个想法：在类内部使用 `use` 关键字意味着他们也必须将 trait 的代码看作是内联在面前类中的代码进行考虑。

这无疑非常像需要检查继承层次结构中的父类一样，而父类要求开发者通俗来说要“向上”看，而 trait 则要求开发者“向侧”看。

这反过来导致了瑜洋问题的“水平化”。你看，尽管我甚至还没有提到它，但一个 trait 消耗另一个 trait 是完全可能的，而后者反过来又可以消耗另一个 trait。结果，我们可能会得到一堆像癌肿瘤一样从类侧面凸出的 trait。

如果说瑜洋问题描述的是一种继承层次结构的层级太多，以至于开发者需要在类树上上下跟踪，以解析通过对象的控制流，那么这种新生成的水平化瑜洋问题就发生在多个 trait 链在一起时，从而给开发者带来了一项艰巨的任务：试图弄清楚哪些方法会成功进入最终类。

```php
trait Foo
{
    public function FooMethod()
    {
    }

    public function FooTooMethod()
    {
    }
}
```

这是我们提议的链中的第一个 trait。它非常直接，所以我们不会久留于它。

## 表达良好的 trait。

```php
trait Bar
{
    use Foo; // Bar trait 消耗 Foo trait

    public function BarMethod()
    {}

    public function FooMethod()
    {}
}
```

现在我们的第一个异类点出现了。Baz trait 消耗了之前的 Foo trait，但重写了 `FooMethod()` 以提供它自己的版本。

```php
trait Baz
{
    use Bar; // Baz trait 消耗 Bar trait

    public function BazMethod()
    {}
}
```

我们链中的最后一个 trait，Baz trait 也很非常直接。

```php
class AwesomeThing extends AwesomeBase
{
    use Baz; // 目标类消耗 Baz trait

    public function doStuff()
    {}
}
```

通过在目标类中消耗 Baz trait，因为开发者需要知道什么样的“东西”会在编译时被粘贴到类内部。这意味着我们必须检查我们所消耗的 trait 的内容。打开

## 表达良好的 trait。

在编辑器中打开该文件将导致我们需要打开 Bar trait，这反过来导致打开 Foo trait 的文件。在这一切之后，我们必须设地折叠该结构，直到我们确定哪些方法的哪些版本将结束在 `AwesomeThing` 之中。对于如此简单的结构，我们发现 `Bar::FooMethod()` 可能是唯一的意外来源应该没有太大困难。但当你开始在里面放入真正的代码时……

由于我们的 `AwesomeThing` 类似乎继承自 `AwesomeBase`。噢天哪。

简而言之：甚至不要想以这种方式链联 trait。除非该层次结构只有两层：消耗的类和被消耗的 trait。

# 总结

总的来说，这一章通过说明使用 trait 会产生许多陷阱可能看起来相当负面。尽管如此，让这些知识成为我们智慧的手段。每当我们作为开发者学习新知识时，都在丰富我们的心理工具箱。了解其中的几点有助于在处理 trait 时做出更好的判断。正如对千年 Bug 的所有准备让它变成了未事件一样，我们可以避免自己代码中的痛苦。结论！trait 应该节制且明智地使用。保持意图的集中和敏锐。然后从精心管理的强大代码复用系统中获益。胜利万岁！

## 寻找闭包（Closure）。

闭包是些有趣的东西。不是那种 YouTube 上的小猫视频那种有趣。而是像“如果我在午夜喂这哥们，它会毁掉我的公寓”那种有趣。尽管如此，我们还是来看看。

在开始之前，你可能甚至怀疑为什么我要在本关于面向对象编程的书里包含它们。当你考虑到它们也被称为匿名函数时，这种情况可能尤为如此。它们甚至看起来像普通的过程函数。只是，你知道，没有名字。

我为它们专门开一章的原因将变得清晰。在此期间，我们需要一个“回归基础”的示例。

```php
$myFunc = function($name)
{
    return "Hey ${name}";
}
echo $myFunc('Joe');

// 输出: "Hey Joe"
```

那么匿名函数就是那样：一个没有名字的。这样做带来的直接益处是，它们不会让它们所在的任何命名空间被那些、旧式的函数名称所污染。这对于全局命名空间尤为重要。

## 寻找闭包。

## 可移植、一次性函数

将函数赋值给变量的一个潜在好处是，该函数现在变得可移植了。与其在与实际使用地相当遥远的文件中创建常规函数库，你现在可以在可以在需要的地方*精确地*设置函数，根据需要对其进行多次传递，并在完成后将其销毁。

最后一部分也具有重要意义。在单个网络请求的语境下，编写在*必需*文件中的具名函数在整个请求期间都存在。而匿名函数的生存时间仅取决于你需要它们多长时间，并且一旦承载它的变量超出作用范围，它们将受 PHP 垃圾回收机制的影响。

当然，你也可以通过对赋值给该函数的变量调用 `unset` 来手动销毁该函数，如下所示：

```php
unset($myFunc);
```

正由于这个原因，匿名函数通常被称为“丢弃代码”。不过，我个人的倾向略有不同。从最基础的意义上来说，我倾向于将它们视为宏。我确实觉得这恰恰更好地传达了它们所提供的实用性。

> “宏用于将一系列计算指令对程序员呈现为单一的程序语句，使编程任务变得不那么乏味且不易出错。” - Wikipedia.org*

这难道不能更好地描绘出这种强大工具可以做什么吗？在匿名函数的体内部，你可以编写你所需的适当逻辑过程，然后在需要的地方执行该“宏”。

这正是为什么移植性特别值得关注的原因。在某位置创建函数、将其赋值给变量并传递该变量的能力具有巨大的价值。

*http://en.wikipedia.org/wiki/Macro_(computer_science)*

## 寻找闭包。 179

你可能已经在疑惑，既然我们已经看过了如何在恰恰需要的地方创建它们，为什么这部分仍然相关呢？事实上，你可能已经得出结论：如果这样的函数（或者至少是它承载的逻辑过程）需要在多个地方，那么一个普通的、常规具名的函数可能更符合我们的需求。

也许吧。

## 另一个“用”例

匿名函数相对于它们更熟悉的兄弟函数，一个明显的优势是可以在定义点从父级作用域导入变量。这一方面是另一个需要密切关注的关键特征。

通常，函数内部变量的生命周期仅限于函数执行的时间。默认情况下，作为参数传递给函数的值是函数调用时可用值的副本。例外情况是带有 `&` 前缀的引用传递变量，以及本身就是按引用传递的对象。

在过去那些糟糕的日子里，赋值在函数内部作用域之外声明的变量意味着使用 `global` 关键字或访问 `$GLOBALS` 数组。这样做会让变量在函数内部可用。

```php
<?php
$driver = "mysql";

function showDriver() {
    global $driver;

    echo "Driver is set to: {$driver}";
}

showDriver();
// 输出: "Driver is set to: mysql"
```

这当然是可怕的。将变量（可能是至关重要的变量）留在全局命名空间中是灾难的根源，因为它们对所持有的值完全没有任何保护，并且可能会随心所欲地更改。当一个应用程序运行到数千行代码时，试图追踪那个无意中改变全局变量值的代码可能会导致浪费大量宝贵的调试时间。

这让我们再次回到了 `use` 关键字。我们已经看到了如何通过在文件顶部应用 `use` 关键字，向我们当前的命名空间导入类、接口、函数或 trait 的定义。

我们还看到了如何通过在消费类内部应用 `use` 关键字，将特定 trait 的实际内容导入类定义中。

现在，我们也可以将 `use` 关键字应用于函数，这为我们匿名函数的可用性（！）增加了一个全新的维度。

基本语法看起来如下：



```php
<?php
$config = array(
    "driver" => "mysql",
    "dan" => "mysql:host=localhost;port=3306",
    "user" => "root",
    "pass" => "secret"
);

$getConfig = function() use ($config) {
    return $config;
}
```

让我们通过观察 `use` 子句本身开始检查过程。

该子句允许我们将变量按照其在函数父级作用域中的状态导入到函数。这非常重要。在函数本身相同的作用域内声明了这里的 `config` 数组，这意味着该数组可以导入到函数中。一旦进入函数内部，你就可以通过简单的传递 `$getConfig` 变量将函数发送到所需的任何地方。对于驻在另一个文件中静态声明的函数，要实现这一点困难得多。

那么，我们拥有一种将其他变量（主要是对象）传输到应用程序其他部分的强大方法，并帮助你避免可能诉诸访问全局变量或访问（例如）注册表单例的情况。

不过，它是双向的。

我们不仅仅是通过从父级作用域导入并发送到其他地方来打包变量，还可以利用 `function() use()` 结构让我们的父级作用域变量受到远程影响。

```php
class MessageQueue
{
    private $messages = [];

    public function addMessage($message)
    {
        $this->messages[] = $message;
    }

    public function getMessages()
    {
        return $this->messages;
    }
}
```

`$mq = new MessageQueue();`

`$queueMessage = function($value) use ($mq) {`

    `$mq->addMessage($value);`

`};`

`$queueMessage("first element");`

寻找闭包。 196

寻找闭包。

## 寻找闭包（Closure）。

这虽然简单得令人痛苦，但它能完美地说明这个观点。赋值给变量 `$doubler` 的匿名函数既短又切中重点。作为一个“宏”，它并没有做什么。尽管如此，我们仍然看到它被调用了五次，输入数组 `$values` 数组的每个元素调用一次，并且在 `array_walk()` 函数完成后，它的效果在数组中是可见的。

完全没有理由说明我们不能将一个复杂得多的过程封装到函数中并将其传递给 `array_walk()`。

尽管如此，在这个例子中，我们选择了一个非常简单的例子。鉴于移植性方面在这里并不重要，我们可以省略变量赋值，直接将匿名函数写在需要的地方。

就像如下所示：

```php
<?php
$values = array(1,2,3,4,5);

array_walk($values, function(&$number) {
    $number *= 2;
});

print_r($values);

/* Output:
Array(
    [0] => 2
    [1] => 4
    [2] => 6
    [3] => 8
    [4] => 10
*/
```

额外加分！该函数只在需要时存在，并在数组被“遍历”后不久就会被销毁。

但这里的重点在于：每当你有一个要求在每次迭代中都需要回调函数的迭代过程时，匿名函数将是那些切合要求的要求的候选者之一。它只需要是可调用的即可。

从过程的角度来说，这意味着使用 `is_callable()` 函数的测试返回 `true`，而在面向对象的角度来说，它应该满足“Callable”类型提示的要求。我们可以用一段相对短的代码来同时满足这两个条件，并说明这些事实。

```php
$myFunc = function() {
    echo "Hey Joe!";
}

var_dump(is_callable($myFunc));
// Output: bool(true)

// 我们也可以对 "Callable" 进行类型提示
function isCallable(Callable $func) {
    echo "Yes, it passes the typehint test";
}

isCallable($myFunc);
// Output: "Yes, it passes the typehint test";
```

到为止，我们已经看到了匿名函数为开发者提供的几处优势。

通过将它们赋值给变量，我们能够根据我们的解码意图到处传递它们。我们可以在需要的地方精确创建它们，而不是在一个相对“遥远”的文件中。我们可以导入原始定义该函数的局部变量，然后让这些变量在函数最终所在的任何地方都可用。

由于它们也是可丢弃的，一旦我们实际上完成了使用，就可以销毁它们。它们那些具名的“表亲们”则不能如此。在相关文件被引入后，这些具名函数定义在整个请求期间都会保留在内存中，无论它们是否真的被需要。

我们还看到了它们是可调用的，因此可以在用于任何要求提供回调函数的地方。它们满足了被类型提示为“Callable”的要求，并从 `is_callable()` 函数返回 `true`。

## 寻找闭包（Closure）。

186

我们还没有真正考虑过的一点是：到底什么鬼它们会被包含在书中名为“扩展你的面向对象大脑”的章节中。原因其实并不是“因为它们实际上是对象”，尽管那部分是正确的。

## 匿名函数是对象

每当你创建一个匿名函数并将其赋值给变量（可移植特性）时，PHP 都会为你将其转换为一个对象。不是一个普通的 `stdClass` 类型对象，而是 `Closure` 类的实例。

现在，我们把这个东西和章节标题本身给对齐了。

`Closure` 类是专门针对这些特殊怪物的。你不能在代码中通过编写类似 `$c = new Closure();` 的语句来创建自己的实例。你无法从它派生类，因为该类在内部被标记为 `final`，因此无法被扩展。

并不是你真的想做这种事情。如果你真的想创建自己的可调用对象，你完全可以自由地这样做。当闭包最初出现在 PHP 中时，它们带来了一个新的魔术方法：`__invoke()`。我们很快会看看这与此的关系，但让我们先集中在 `Closure` 类的结构上，而不是过早超前。

每当解释器遇到被赋值给变量的匿名函数时，它将变成一个 `Closure` 实例。在此过程中，你的“现在是对象的函数”在沿途中获得了一个有趣的方法：`bindTo()`。

`bindTo()` 方法赋予了你非凡的力量，可以残暴地对待和骚扰其他对象的私有属性。

我这么写是为了以防你要睡着了。尽管如此，这是事实。`bindTo()` 方法允许你创建一个当前闭包的副本，但将其其中一个活动状态绑定到另一个对象。

这样做的效果是，如果相关的闭包包含了对 `$this` 的引用，那么 `$this` 所引用的范围就可以动态更改。结果是，$this$ 可以引用一个完全不同的对象的内部范围。

看。

## 寻找闭包（Closure）。

```php
<?php
class SecretValue
{
    private $secret = 'nobody-knows';
}

$shhh = new SecretValue();
```

我们在这里极其有限的界面应该能够充分保护 `$secret` 属性的值。换句话说，没有办法从外部访问它。在没有放置相应方法的情况下，不应该有办法从中读取或写入它。

然而，通过包含对 `$this` 引用的闭包，我们可以简单通过 `bindTo()` 方法将其弹出。

```php
$closure = function() {
    return $this->secret;
}
```

```php
echo $closure($shhh); // Output: nobody-knows
```

这里的 `bindTo()` 方法接受两个参数。第一个参数是闭包应该绑定的对象。第二个参数是可选的，如果提供了，它指定了闭包运行的新范围。当我们分配同一个对象作为新范围参数时，我们实际上是将闭包挂到了该对象。

尽管 `$boundClosure` 是在类外部创建的。

这有意义吗？它可能有助于稍微扭转这个想法，尽管我应该指出这在技术上是错误的，但如果它有助于理解，那么我们可以被原谅。也许。

## 寻找闭包（Closure）。

202

无论如何，让这个错误的陈述靠边吧。一旦我们将闭包绑定到一个对象并包含了可选的范围，闭包的内容——即我们提供的逻辑——就像目标对象内部的一个具命名方法。我们可以通过从外部调用闭包来触发具命名方法。

那个触发发生在上一个代码块的最后一行，`echo $boundClosure();` 是我们导致闭包内部逻辑（实际上是 `$this->secret;`）弹出那个理论上不可访问的私有属性的方法。

当然，也可以反过来，这也是为什么我们在这一部分引入了能够残暴骚扰私有属性的概念。

```php
$closure = function($newValue) {
    $this->secret = $newValue;
}
```

```php
$boundClosure = $closure->bindTo($shhh, $shhh);
```

```php
$boundClosure('Not very secret afterall!');
```

## 寻找闭包。

当你在其中一个类中编写此特定方法的代码时，你使得该类型的对象变得可调用的。结果，在任何你可以使用闭包作为回调的地方，你都可以用它来替代同样支持 `__invoke()` 方法的对象实例。

当然，是否采用这种方法取决于你。如果你认为闭包本身不能满足你的需求，你可以将自己的对象实例传递给像 `array_walk()` 这样的函数。

```$php
$callback = new MegaArrayTransformer();
array_walk($_POST, $callback);
```

尽管如此，通过提供一个桥接 `array_walk` 过程与 `MegaArrayTransformer` 的闭包，可能对你更有帮助。

## 构建你的对象

尽管如此，向现有对象中注入新的、未命名的方法的概念仍然是一个非常有吸引力的提议。尽管在非常受限的情况下，我们即将观察的这种技术我所知知的只有一个模糊可以合理的用例。如果你知道更多用例，我非常乐意听听。

为了遵循模型-视图-控制器（MVC）模式的正确定义，控制器的任务是请求模型，然后将其呈现给视图，允许视图更新自身。HTTP 协议的停止-开始特性使得难以正确遵循该模式，这导致视图层变成了“构建 html 页面并发送到浏览器的部分”（暂不考虑 Ajax）。

尽管如此，我们仍然有机会去遵循该过程的第一部分。对于 GET 请求，你的控制器将转到模型层（可能通过服务）并检索它需要传递给视图的模型。

在我们的视图将显示来自多个数据源的数据的情况下，这给我们带来了一点问题。

从不同的模型源检索该数据并将其杂合成一个视图可以访问的单元并不是控制器的任务。尽管如此，网络上字面上确实展示了成百上千的例子，这种做法被展示为正确的方法：控制器中的动作方法收集数据，然后为视图做好准备。

我们可以用一个并不太常见的例子来说说明这一点。

假设我们需要一个页面来显示客户详情，以及他们下过的任何订单以及与这些订单相关的发票相应状态。采用错误的方法可能像这样：

```php
// 在控制器中
$customerDetails = $this->modelService->fetch('Customers', $customerId);
$orderDetails = $this->modelService->fetch('Orders', $customerId);

$orderIds = [];
foreach ($orderDetails as $order) {
  $orderIds[] = $order->OrderId();
}

$invoiceDetails = $this->modelService->fetch('Invoices', $orderIds);

$this->view->render(array(
  'customer' => $customerDetails,
  'orders' => $orderDetails,
  'invoices' => $invoiceDetails
));
```

我并不是说每个人都这样做，但我确实看到这种方法被经常地采用。让控制器方法像这样将模型数据杂合为视图可消费的单元的问题在于，我们不可避免地为自己埋下了代码重复的种子。这是一个等待发生的 DRY（不要重复自己）违背行为。

为什么？

我们这里的假设是，特定的控制器方法将是触发此数据渲染的唯一方式。如果事实确实如此，现在及永远如此，那么我们就可以逃过这一点。

但直到财务部门的信贷控制员请求每月将相同的信息通过电子邮件发送给他们。总部希望能够从 API 调用中以 json 负载的形式获取这些数据。

因此，让模型层执行数据准备并返回一个包含所有相关信息的单个可用单元会更有意义得多。问题是，这种需求是否值得创建一个全新的模型对象来仅携带数据。

# 寻找闭包。

```php
public function __call($methodName, $args)
{
    if (is_callable($this->this->methods[$methodName])) {
        return call_user_func_array(
            $this->methods[$methodName],
            $args
        );
    }
}
```

结果是什么？视图通过调用各个闭包，*就像它们是公共方法一样*，来访问所需的数据。

账号：<?= echo $model->getAccountNumber(); ?>

客户名称：<?= echo $model->getCustomerName(); ?>

```php
<?php foreach ($model->getOrders() as $order): ?>
// 按需渲染细节。
<?php endforeach; ?>
```

显然，你会根据自己的需求调整输出的生成。我们在这里观察到的全部，就是闭包的调用*类似于*对对象方法的的调用。

# 回到宏（macros）。

一个关于闭包的章节，如果不提到你在实战中可能会遇到闭包的最常见情况，那么它是不完整的。

在最近几年里，PHP 世界中对依赖注入容器（Dependency Injection Containers）有很多讨论，而对路由（routing）的艺术与科学的讨论虽然较少，但同样重要。如果你最近接触过这两个概念中的任何一个，你可能会发现很难注意到它们也广泛地使用了闭包。

因此，这两个概念为我们从真实世界的背景下检查闭包的使用提供了一个理想方式。

我们的第一个例子是路由，它直接来自 Slim 微框架¹⁰ 的首页。

> ¹⁰http://www.slimframework.com/

# 寻找闭包。

```php
<?php
$app = new \Slim();
$app->get('/hello/:name', function ($name) {
    echo "Hello, $name";
});
$app->run();
```

这种路由方法在 PHP 框架世界正变得无处可见，而且也是有原因的。这是一种非常有效且极其灵活的方法，可以将这种类似宏的结构映射到 URL 模式上，从而根据模式与传入的请求路径的匹配结果，自动执行包含在其中的代码。

尽管上面的代码非常简单，但我们应该在这里考虑它。一方面，我们有触发宏执行的各个方面；另一方面，我们有宏本身的定义，每当模式匹配时就会被触发。

当然，这个宏的体（即这个闭包）是极其简单的。一点细微的修改也能非常出色地引入下一个想法。

```php
<?php
$app = new \Slim();
$app->get('/blog/:postId', function ($postId) use ($app) {

    $service = new BlogService();
    $controller = new BlogController($app, $service);
    $controller->renderPostAction($postId);
});
```

好了，也许不那么微妙了，但至少我们的可调用对象已经通过更具相关性的代码充实起来，在此过程中帮助我们将其看作更像一个宏。

在我们可调用对象的体内部有两行代码，导致了 `BlogService` 和 `BlogController` 对象的实例化。鉴于这个可调用对象在它被调用之前不会执行，很容易看出我们是如何延迟到最后一刻才对服务和对象进行实例。

# 寻找闭包。

# 196

当这样使用时，闭包非常积极地帮助我们支持延迟加载（lazy loading）的概念。可以肯定，这种方法会使我们在早期的设置和配置阶段花费相当的时间，但所获得的收益将非常出色地补偿我们早期的努力。

假设我们正在使用一种严谨的自动加载策略，创建闭包来促进在需要的地方再实例化对象，这节省了浪费服务器资源的成本，并在处理端用户请求和交付响应时提供了最大的效率。

这种按需延迟加载对象的概念是依赖注入容器的核心特性。在本书后面探索依赖注入的过程中，我们将更仔细地观察其中的一些内容。

尽管如此，为了我们的目的，让我们简单看看 Pimple¹¹，来自 SensioLabs 的 DI 容器。再次，我将直接从首页借用一些代码，以便我们像上面 Slim 提供的路由示例一样对其进行挑选。



```php
<?php
use Pimple\Container;

$container = new Container();

// 定义一些服务
$container['session_storage'] = function ($c) {
    return new SessionStorage('SESSION_ID');
};

$container['session'] = function ($c) {
    return new Session($c['session_storage']);
};

// 获取 session 对象
$session = $container['session'];
```

除了纯粹为了避免混淆之外，几乎值得注意的是，Pimple 中的 `Container` 类实现了 `ArrayAccess` 接口，这就是为什么我们看到使用数组方括号访问器分配闭包。

> ¹¹http://pimple.sensiolabs.org/

# 寻找闭包

在任何情况下，我们仍然可以追溯这段代码以检查为什么这种基于闭包的方法是理想的。

从最后一行开始，我们在这里将 `$session` 变量赋值为存储在容器中的 `'session'` 键的内容。在 Pimple 中，当你第一次访问容器的键之一时，存储在上面的可调用对象就会被调用，产生它的返回值。在这种情况下，它是一个 `Session` 类的实例。

此阶段真正相关的部分是相应的闭包并不是孤立地返回新实例，而是通过另一个闭包返回的值来配置该实例；这次是对应于 `'session_storage'` 键的那一个。在内部，这个 session 闭包实例化并返回了一个配置好的存储对象。

这正是我们开始从最初设置容器的努力中获得回报的地方。通过将所有闭包都放在一个位置来建立配置，我们再次欣赏那段代码片段中最后一行的力量和简单。

```php
$session = $container['session'];
```

远离原始的配置和设置，`$session` 变量被填充了一个正确配置的 `Session` 实例，一个带有了所有依赖并准备就绪的实例。在执行这一行之前，session 对象并不存在，类也没有被解析。这对于我们希望构建一个不仅仅是“简陋”的网站带来了性能收益。

尽管如此，就我们而言，这一行客户端代码使得我们能够快速方便地更改实现。由于新的 session 继续遵循之前的接口，所有的 session 都不会被破坏。

# 总结

正如我在开始建议的那样，可能最好在午夜不要喂这些小生物。

一方面，我们看到了如何使用它们来获得对另一个对象受严格保护的私有属性的完全读写访问。不这样做是一个特别明智的立场。

另一方面，我们还考虑了如何通过从其他真实的活对象实例中挑选方法来创建完全新的对象，并且这些方法保留了它们原始的作用域。对于从各种模型创建一个只读对象来说，这是一种幸事。然而，正如之前提到的，这种技术在现实世界应用中的用例非常有限。我们显然无法将这样的结构呈现给客户端代码进行进一步处理，因为它本身不带接口。这种缺乏抽象基类或已实现接口的保证意味着不得不诉诸鸭子类型（duck typing）。有了这样一个“弗兰肯斯坦怪物”在手，即使是那样也是痛苦的。

## 讨论点

我们已经到达了第二部分的结束，借此，我们也接近了《PHP Brilliance》基础部分的终点。在进入编程原理、范式和设计模式这些迷人的话题之前，仍然有一些事情我们需要处理。

所以，我们又来到了另一个“讨论点”。

### 那么，究竟是哪个？合同（Contract）还是保证（Guarantee）？

早在关于接口的章节中，我倾向于使用“保证”（guarantee）这个词。尽管世界上其他地方称之为“合同”（contracts）。明确一下，我并不打算在这个问题上发表立场并宣布世界上都是错的。那样太愚蠢了。

尽管如此，我认为在这里（远离接口章节本身）探索这些想法是有价值的。正如我之前提到的，这在很大程度上取决于偏好。最终结果应该是相同的：我们寻找的是一个可执行的协议。

在正常情况下，合同指的是两个或多个双方达成共识的事物。例如，每当你光顾商店用现金换取最畅销的跳舞科技小道具时，你就签署了一份销售合同。或者，每当你付费下载另一个 Minecraft 内容包时也是如此。这是一份合同，因为双方都根据这些相互认可的条款提供了某些东西并得到了回报。你同意提供资金并接收产品；商店同意提供产品并收取资金。

话如此，这种情况下合同的概念源于 Bertrand Meyer 在 1986 年提出的“契约设计”（Design By Contract）方法，并在他的著作《面向对象的软件构造》（Object Oriented Software Construction）中得到了详尽记录。

> ¹https://archive.eiffel.com/doc/manuals/technology/contract/

讨论点。

200

> 契约设计（DbC）是一个值得阅读的想法，尽管它是为了在 Eiffel 语言中创建软件设计的。然而，字面执行 DbC 会导致违反 Liskov 替换原则（将在第四部分介绍），从而导致应用程序代码不是类型安全的。在此告知各位。

与此相反，这种“保证”（guarantee）通常是单方面的事务，即一个关于履行保证本身的单方面承诺。当这些保证的条款被写出来时，往往在不知道利益相关方将会是谁的情况下写下的。

归根结底，它应该被视为合同还是保证的问题，其实是一个无关紧要的问题。当你考虑逻辑过程中的双方——即对象与与其协作的客户端代码时，合同术语是完美适用。

“保证”这一术语的提议是一个更单方面的安排，它是针对目标受众，即我们代码的读者提供的。

当家电制造商运出一台全新的冰箱时，他们会附带一份书面保证（保修）。从理论上讲，保证是一种在发生故障时修理或更换电器的单方面协议。如果电器在保证期内运行完美，那么保证可能不会被履行。

换句话说，任何购买该冰箱的人都有权阅读该保证中列出的条款和条件，并借此理解如果万一发生，如何与制造商签订服务合同。制造商并不知道谁会阅读这份文档，也不知道他们是否能读懂那些小字中充斥的专业术语和法律语言。

本质上，这就是我提出的观点。在指导同事的过程中，我想建议这些接口是用来设定合作的条款和条件的。在编写利用这些东西的代码之前应该先阅读并理解，这正是合同类比变得更合适的地方。代码的合同，编码者的保证。

归根结底，只要基础概念在我们各自的团队内部被理解，它就并不重要。

### 鸭子类型（Duck typing）

我在上一个章节中简要提到了鸭子类型概念，所以我觉得在这里引入它来看一看是合适的，考虑到我们刚刚讨论完那套关于保证/合同的胡说。正如你可能已经察觉到的，我更倾向于“保证”风格的方法，因为这样我们以后不太可能遇到问题。

无论如何，鸭子类型是指检查一个对象能做什么，以查看它是否能做你想它做的事。

这是什么意思？

鸭子类型并不是通过类型提示或针对 `instanceof` 关键字进行测试来测试保证的存在，而是依赖于在调用该方法或读取该属性之前检查该方法或属性是否存在。

这个概念基于19世纪诗人 James Whitcomb Riley 的引言：

> 当我看到一只鸟像鸭子一样走路、像鸭子一样游泳、像鸭子一样叫时，我称那只鸟为鸭子

这给我们留下了一个想法：我们只是检查某个方法或特征是否存在，以判断该对象对我们是否有用。

将 Riley 先生的名言转换成代码，实际上等同于：如果一个对象提供了 `quack()` 方法，那么该对象就可以被视为鸭子的实例，无论它实际上是是否。

在代码中，它可能像这样：

```php
public function doStuff($param)
{
    if (is_callable(array($param, 'quack'))) {
        return call_user_func(array($param, 'quack'));
    }
}
```

讨论点。

203

不过，这并不是我们要采取的方法。这不是实现《PHP Brilliance》的方法。这种方式过于依赖作为参数输入的正确项，而且你已经忍受了关于构造函数中异常的抱怨，并将这一过程比作把头伸进垃圾处理器中。

> 我保证，我们很快就会讨论实例化恐惧症（Instantiaphobia），这包括了整个构造函数事务——就在第三部分。

要点说明。

```php
if (method_exists($viewData, 'greet')) {
  // 不执行。
  $viewData->greet();
}
```

因此，我们必须回到修改骨类本身来支持鸭子类型（duck typing）。我们通过添加一个特定的方法来可靠地提供我们所需要的布尔响应。

```php
<?php
class ViewData {
  private $methods = array();
  ...

  public function hasMethod($methodName) {
    return (
      array_key_exists($methodName, $this->methods) &&
      is_callable($this->methods[$methodName])
    );
  }

// 因此，为了实现鸭子类型
if ($viewData->hasMethod('greet')) {
  $viewData->greet('Joe');
}
```

当然，这种方式更好，因为在处理这种棘手的家伙时，它为我们提供了一定的额外的安全性。

# 继续

我们的注意力在这些细节和细小文字上停留了太久了。现在是时候拉远视角，给自己泡杯好茶，然后进入第三部分，开始挑选模式、原则和范式了。

# 大脑检查

欢迎来到第二部分的最后一个章节。

这一部分是让我们通过问自己来对书中部分涵盖的内容进行自测：“我能针对每一个点做一个闪电演讲（lightning talk）吗？”

这是一份清单，也是一份突出需要进一步阅读区域的指南。

## 接口

接口允许我们向对象的协作者提供一种保证，即描述的方法在实现对象中是可用的。抽象父类也提供了一个我们可以进行类型提示的接口，在这种情况下，这种保证并不存在，确保子类遵守父类接口的责任在于开发者。

## 命名空间

命名空间为我们提供了一种将代码封装成凝聚、逻辑化、组织良好的单元或模块的方法，并避免与我们可能引入的其他第三方代码发生命名冲突。PSR-0 和 PSR-4 自动加载标准要求我们的代码进行命名，但为遵循相同标准的其他包提供了极大的便利性和兼容性。

## Composer

Composer 已成为 PHP 应用开发领域首选的包管理器，它在管理应用程序依赖方面通过提供易用性和非凡的力量，甚至取代了 Pear。

## 特性 (Traits)

PHP 引入特性是为了为那些彼此没有关系的类提供一种代码复用机制。特性通过一种系统级的“复制并粘贴”过程应用到消费类中，但需要

## 大脑检查

在使用特性时应该加小心，因为当消费类已经提供了同名方法时，并不是特性的所有方法都会被导入。

## 闭包 (Closures)

闭包也被称为匿名函数，因为它们可以在没有函数名的情况下进行声明。相反，闭包代表的函数被直接应用于变量的值。在内部，闭包被表示为 `Closure` 类的实例，功能绑定到 `__invoke()` 魔法方法上，允许它们被视为回调函数。两种类型都可以测试是否为“callable”类型实例。

## 鸭子类型

鸭子类型是一种测试变量能力的形式，而不是针对特定接口或类名进行类型提示。在面向对象中，这通常意味着在尝试使用那些方法或属性之前，测试变量是否存在特定的方法和/或属性。

## 立足原则

> “布莱尔，你相信这些鬼的胡话吗？” - Childs

# 在基石上构建

好了。我们成功地处理了基础性内容。你不觉得感觉好多了吗？我知道我觉得好。

即使这样做的好处还不明显，但它们很快就会显现。无论距离上次考虑封装和继承等事情已经过了多久，或者是否甚至在书中遇到过它们，我们实际上所做的都是让那些基石到位。我们的目标是确保我们有一个坚实的基础，以此构建那些流光溢彩的软件伟大殿堂。

本书前部分的关联性将在接下来的页面中变得显而易见。在书的这一部分，我们超越了基础，开始建立那些最终将成为大师们以自然方式展现的潜意识技巧。

工匠的职业生涯会有这样一个阶段，在施加锤击于凿头或在画布上运笔时，不再需要意识的思考。经验决定了动作应该有多大或多快。当这样的工匠发现自己停下来评估动作的速度、力量或方向时，那就是他们失手的地方。

在这里，我们将考虑引导软件工匠之手的原则，并通过足够的重复来鼓励它们成为更多是“肌肉记忆”而非有意识的思考。

在接下来的页面中，我们将探索获得 PHP 卓越表现所必要的原则、模式和范式。但仅限核心内容。此目的并不是把它变成一个模式目录，尤其是因为对于对此感兴趣的开发者来说，已经有许多现成的优秀示例。

尽管如此，这里介绍的内容与我们已经涵盖的内容或即将出现的内容有着极其紧密的联系。

换句话说，将有很多我在书开头处暗示过的那些循环引用。

让我们开始开始吧。

# 灵魂捕手者 (Ghostbusters)

记得第一部分中的 Joe 吗？尽管他是个那么讨人的人，但我们不得不让他离开。无论他有多么讨人，坦率地说，公司不能被认为在支持那种材料的下载。取而代之的是 Lizzie。她是个好手。

然而，她对闭包章节提供的可能性感到非常兴奋，认为构建一个 DataMapper 类型的东西是个好主意，从模型中提取数据并将更改存回数据库。

这种态度完全是值得赞的，但这也是为什么我们书的这部分从一个反模式开始的原因。那种涌动的兴奋需要被某种方式控制。

我们所说的的反模式被称为“灵异”（Poltergeist）。它也被称为吉普赛车（Gypsy Wagon），但我认为“灵异”是一个更贴切的名字，它描述了一种“某种东西出现，导致事情然后消失”的现象。

其本身，这是一个非常贴切的描述，描述了闭包的错误用法，它表现为那些没有真实实质的对象。我们对“灵异”的考虑是双倍重要的，因为我们花了大量时间考虑如何将对象分为认知者和执行者。

我们系统的认知者更准确地分为两个阵营。第一个较大的阵营我们可以标记为实体（Entities）。这些是核心玩家，即维护应用程序数据的模型，提供了保留数据的属性和允许操作数据的方法。

第二个小得多的认知者阵营由值对象（value objects）组成。这些小家伙允许我们在一个过程到另一个过程之间传输复杂结构。它们既不对持有的数据操作，也不因为数据执行过程。

这剩下的就是执行者（doers）。执行者是我们要求执行过程的那些们，即那些更准确地被称为服务（Services）。

灵异行为的示例，尽管是一个极其单薄的示例。尽管如此，我们留下的对象除了在模型数据和存储机制之间创建一个临时桥接之外，没有明显的用途。

这本身为我们提供了一个难以追踪错误产生的过程，但并不是我们需要的问题。事实上，如果我们通过在模型对象和存储之间建立一个更显式的桥接，我们会受益更多。

# 捉灵敢卫队

// 在控制器内部

```php
if ($_POST['accept_terms']) {
  $user = new User();
  $user->setEmail($_POST['email']);
  $user->setPassword($_POST['password']);

  if ($user->save()) {
    $email = new Email();
    $email->setSubject('Please verify..');

    if ($email->send()) {
      $this->flashMsg('Congrats');
      $this->redirect('/login.php');
    } else {
      // 关于邮件失败的处理
    }
  } else {
    // 关于用户保存失败的处理
  }
}
```

看起来眼熟吗？我认识许多 PHP 开发者在职业生涯中都做过这种事情，当注册过程涉及的步骤比简单的创建用户记录和发送邮件要多时。我们已经看到，在控制器方法内部进行这种数据弄乱会导致代码重复；这是一种完全可以避免的情况。

Lizzie 会怎么做？她的第一次尝试可能是将整个过程封装到单个对象中，从而产生一个看起来像这样的控制器方法。

// 在控制器内部

```php
$accepted = filter_input(INPUT_POST, 'accept_terms');
if ($accepted) {
  $reg = new UserRegistration();
  if ($reg->addUser($_POST)) {
    $this->flashMsg('Congrats');
    $this->redirect('/login.php');
  } else {
    $errors = $reg->getErrors();
    // 显示错误
  }
}
```

## 捉灵敢卫队 213

从我们控制器的角度来看，这是一个巨大的改进。我们不再被大量杂乱的 `if` 语句填充（其中有些甚至是嵌套的），现在我们只需要对 `UserRegistration` 实例调用一次 `addUser()` 方法。

这里的假设是，`UserRegistration` 对象协调了验证用户数据、哈希密码、创建用户记录以及任何相关行并最后发送到电子邮件的整个过程。

乍一看，这看起来完全令人满意。毕竟，我们现在拥有了一个对象，只需要向它传入一个结构适当的数据数组即可创建用户账户，结果是一个更精简、更简洁的控制器。更好的是，我们似乎遵循了“执行，不要询问”（Tell, Don’t Ask）原则，尽管我们还没有读过相关内容。

所以，这是向正确方向迈的一步，但我们完成这段特定的旅程了吗？这取决于 `UserRegistration` 类及其 `addUser()` 方法。如果只是只是把那些嵌套的 `if` 移动到了方法里，那么我们实际上什么都没有实现。



```php
<?php
class UserRegistration
{
    public function addUser(array $data) {
        $user = new User();
        $user->setEmail($data['email']);

        if ($user->save()) {
            $email = new Email();
            $email->setSubject('Please verify...');

            if ($email->send()) {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    }
}
```

# 捉灵敢卫队 214

此外，如果我们所做的只是将整个过程放在一个方法调用之后，那么我们实际上是将自己限制在了一种“全有全无”的方法上。我们将所有必要的数据都丢给该方法；如果它成功了，那就太好了。如果不成功，呢？再重试一遍？

即使没有功能完好的水晶球，我们也可以相当确定，我们的用户至少会有一个人欢迎再次发送邮件，特别是当我们要求他们验证电子邮箱地址以激活账户时。

考虑到这一点，我们至少可以确定需要将该过程分为两个部分。此外，由于我们已经考虑过这些执行者实际上是服务候选人，那么让 Lizzie 在适当的服务类上通过实现方法调用的方式来实现这两个过程将是完全合理的。

这可能会导致我们得到类似这样的代码。

```php
<?php
class UserRegistration
{
    public function addUser(array $data)
    {
        $userService = new UserService();
        $user = $userService->addUser($data);

        if($instance instanceof User) {
            $emailService = new EmailService();
            $emailService->send($user, 'welcome.email.tpl');
        }
    }
}
```

现在我们完全拥有了 `UserService` 和 `EmailService` 类。太棒了。

然而，如果一个灵体（poltergeist）是由一个几乎或没有任何内部状态的对象泛化出来的，且其表面目的仅仅是触发其他系统对象的方法调用，那么这正是我们这里拥有的东西。

诚然，这是我们为了得到灵体而采取的一种高度刻意的路线，但对于我们那些经验较少的同胞来说，仅仅将一系列按键操作封装到一个似乎在为我们“自动化”事情的对象中，其实并不罕见。创建一个显式意图为了自动化一个……

# 捉灵敢卫队 215

复杂的过程看起来似乎是一个完全有效的方法，但如果这个对象本身没有带来任何实质内容，那么它很可能就是一个灵体。

幸运的是，修复我们现有的代码非常简单且直接。像任何“灵体”（Poltergeist）反模式的实例一样，它都可以通过重构来驱逐。驱逐灵体只需要将逻辑从执行体移动到调用者。由于它们本身没有实质内容，这一点在它们作为触发器时是显而易见的。驱逐我们的灵体只需将这些服务移回控制器即可。

```php
// 在控制器内部
```

$accepted = filter_input(INPUT_POST, 'accept_terms');

if ($accepted) {

    $userService = new UserService();

    $emailService = new EmailService();

    try {

        $user = $userService->addUser($data);

        $emailService->send($user, 'welcome.email.tpl');

        $this->flashMsg('Congrats!');

        $this->redirect('/login.php');

    } catch (UserService $use) {

        // 错误处理

    } catch (EmailService $ese) {

        // 错误处理

    } catch (Exception $e) {

        // 未知错误处理

    }

}

通过这些更改，我们现在消除了代码中的灵体，允许安全地删除 `UserRegistration` 类。此外，两个服务类的加入让我们能够访问创建账户和发送欢迎邮件这两个独立的过程。

这在许多方面都有意义。

# 捉灵敢卫队 216

将账户创建过程从控制器解耦，使得在 Web 环境之外创建用户成为可能。这样做有什么好处？如果我们在一个大型组织中部署，或者我们需要从旧应用程序迁移用户到新的应用程序中，批量创建用户账户的能力对我们来说将非常有益。从上传的 CSV 文件生成用户帐户变得轻而易举。

捉灵猎人

217

相比之下，我们的 `UserService` 为我们提供了大量的空间，可以在服务接口上构建更多与用户相关的方法。毕竟，它被称为 `UserService` 而不是 `UserRegistrationService`，后者会让我们再次回到“灵异（poltergeist）”的领域。更通用的 `UserService` 名称允许我们为这个特定的执行者充更多与用户相关的操作，同时避免让对象失去焦点。

## 什么时候面模式不再是面模式？

“当灵异出现时。”这无疑是我们可能给出的答案之一。如果你已经熟悉面模式模式（Facade pattern），就会知道这种模式旨在为复杂的操作提供一个简化的接口。事实上，这正是该设计模式公认的定义。

我也认为，正是这个定义及其变体导致了开发者从初创建了“灵异”。将复杂的多阶段过程隐藏在单一、简化的方法调用背后的这种想法自然地具有吸引力。但正确地说，面模式不仅仅是一个按钮，而是一组连贯的方法集合，它们作为特定包或一组相关逻辑过程的接口呈现出来。

如果我们构建得当，`EmailService` 尽管目前只展示了单一的 `send()` 方法，但它提供了一种清晰的方法，客户端代码可以在程序执行期间的任何一点触发电子邮件的发送。然而，构建电子邮件涉及的复杂性（包括模板的解析）仍然对客户端代码隐藏。

使用像这样的面模式有一个非常显著的益处：我们可以更改发送电子邮件时采用的实际逻辑，而对需要发送邮件的客户端代码产生任何影响。

对于一个“规模扩大”的应用程序，这使得从直接发送电子邮件切换到实现基于数据库的电子邮件队列系统变得异常简单，只需通过管道连接 beanstalkd、RabbitMQ 甚至 Apache Kafka 等队列系统即可。

这是一个关键考量，当我们到达第五部分讨论架构问题时，将进行更详细的介绍。我打赌你迫不及待了！

# 总结

我们需要防范系统内部“灵异”的出现。根据其本质，它们向我们的对象图引入了不必要的复杂性。它们通过类似于控制的运行模式被识别出来，根据反模式的定义，它们是虚幻且转即逝的，它们“出现，引发事情，然后再次消失”。

掌握“告知，不要询问（Tell, Don't Ask）”原则将有助于防止这些麻烦的幽灵出现在我们的代码库中。我们很快就会讨论这一点。

与此同时，请记住，虽然扫帚柄可能很好帮助我们关门、开关灯和切换电视频道，但对于我们的代码而言，我们需要它跳出那该死的扶手椅，并去自己完成那些事情。

## 偏爱接口。

在面向对象编程世界，最常引用的原则可能是这一个。

> “面向接口编程，而不是面向实现编程。”

尽管如此，我们并不会花费大量时间来考虑它。

到底为什么不呢？

这个原因简单而扼要——我们应该已经搞定了它，Lizzie 已经做到了。如果你还没有，说明你落后了。回到关于抽象和接口的章节，完成后后再回到这里报告。

这个特定原则之所以被搞定，源于所有关于接口以及它们如何为我们提供方法可用性保证的讨论。

不仅如此，当然，它也被搞定了、解决了，是因为所有关于我们如何使用抽象类为新的自定义数据类型铺设蓝图的讨论。

在考虑其中任何一点的范围内，我们真正关注的是实现类型安全这一非常理想的目标。当我们考虑到作为开发者，理解 PHP 自有的原生数据类型的行为时，这变得尤为相关。

是的，我将再次重复这一点。

如果我们作为开发者能够完全理解整数、字符串和关联数组是如何运作的，我们就可以创建与它们可靠运行的应用程序代码，从而获得一致的结果。

将整数相乘将得到一个整数结果。

将一个整数除以一个浮点数将得到一个浮点数结果。

使用一个字符串值对数组进行前推（unshift）将得到一个包含该字符串作为其第一个索引的数组。

这就是类型安全的发挥作用。任何清醒的开发者都不会尝试用一个字符串除以一个数组并期望得到布尔结果。事情不是那样运行的。

我们应该能够将同样的概念应用于我们创建的自定义数据类型上。我们在代码中定义的抽象类和接口定义描述了可以在方法签名中进行类型提示（type hint）的内容。

当我们对这些内容进行类型提示时，我们依赖于在操作原生数据类型时可以运用的同样的知识。只要我们继续遵守接口声明所提供的保证。只要我们继续遵守抽象类所描述的接口。

当我们这样做时，当我们确保我们的自定义数据类型行为一致时，我们就在代码中实现了类型安全，并扩展之，我们消除了由于我们未能这样做而导致产生漏洞的可能性。

这就是“面向接口编程，而不是面向实现编程”这一理念的基础。当我们可以在方法签名中提示特定类型的数据时，该方法内部的代码就可以与这些输入参数可靠地协作。但前提是我们必须认真对待这些接口和抽象类。

这一切的核心概念是，我们的客户端代码、我们的方法体，应该能够与这些输入参数一致地运行，无论这些参数的实际、具体身份是什么。

在实际操作中，遵循这一原则意味着不要这样做：

```php
class AbstractDocument
{
    private $db;
    public function __construct(mysqli $db)
    {
        $this->db = $db;
    }
}
```

而是要这样操作：

```php
<?php
use MyVendor\MyApplication\Storage\StorageInterface;

class AbstractDocument
{
    private $storage;
    public function __construct(StorageInterface $db)
    {
        $this->storage = $db;
    }
}
```

偏好接口（Favour Interfaces.）

- 在 MongoDB 中创建或更新文档记录

- 将文档的标题和永久链接（permalink）详情添加到在 Redis 或 Memcache 等键值存储器中维护的标签映射中。

所有这些内容都可以在无需对 `AbstractDocument` 继承层次结构的代码进行任何更改的情况下实现。这是一个非常理想的结果，而当我们遵循这一特定原则时，这种结果是非常容易。

与此形成鲜明对比的是，对如 Mysql 实例等特定具体类进行类型提示，不可避免地会导致我们的 `Document` 子类代码充斥着 Mysql 特有的方法调用——这是一个非常不理想的结果，因为以后如果想要添加其他类型的存储方式，将需要重大的重构工作。

# 总结

这里没什么好补充的。当我们能够从容且一致地识别抽象数据类型以及佩戴接口的实现者的特征和属性，而不是被迫围绕具体类周围转动代码时，我们实现了以下目标：

- 基于对类型安全一致尊重的韧性代码

- 根据引入的变更请求减少了未来的维护需求，因此：

- 更多的去酒吧时间（pub time）。

尽管如此，Lizzie 还是希望我们将偏好顺序重写为“冰淇淋优于接口，接口优于实现”，这尤其是因为开心果、巧克力和薄荷味显然是那只狗最爱吃的。

# 同样也要偏好组合（And favour Composition too.）

Lizzie 可能对我的章节标题感到有些沮丧。因此，我可能不得不把关于 Ben & Jerry’s “Pphish food”口味的笑话留到以后。不过作为一种让协，我们就说，没有什么能比开心果、薄荷和巧克力味的冰淇淋更棒了。

解决了这些无稽之之后，让我们继续另一个流行的原则；其内容如下：

> “偏好组合优于继承”（Favour composition over inheritance）

这是我们之前遇到过的一个，尽管相当短暂。当我们非常明智地考虑摒弃任何通过继承来实现代码复用的想法时，在途中不小心被“偏好组合优于继承”的想法绊住了。

自然，这我们将认真审视它的地方，特别是结合直接说明这一概念的设计模式。这些都是非常好的东西。好的东西很少被承认，经常被忽略，但重要性丝毫不减。

这一点的基本前提是，当我们从各种离散的、关注层的资源组合我们完成的对象时，比起尝试构建复杂的继承层次结构，我们可以获得一个强大得多、灵活得多的对象图。

是的，这意味着我们必须再次考虑继承的话题。我对此表示歉意。从好的一方面看，我们已经几乎把这个话题讲透了，这至少意味着我们只需要简单复习一下即可。

请记住，反对提交“滥用继承”（Inheritance Abuse）的理由已经成立了，无论是通过继承另一个类仅仅为了访问某个特别需要的方法，还是通过创建一个父类来共享该方法。或者通过创建巨大的、摇晃的“通过继承进行复用”塔，并使用方法重写来清空我们不需要的方法。

这里的核心问题源于我们通过 `extends` 关键字自然创建的硬编码依赖。作为开发者，我们了解到类与类之间的硬编码依赖是件坏事。它们会导致紧耦合的发生，反过来导致脆弱的代码驻留在我们的应用程序中。这并不好。

在大多数情况下，确实如此。

父类与任何派生自它的子类之间发生的紧耦合，本身就是继承的自然结果。只要我们以正确的方式对待抽象和继承，这对我们来说永远不会是一个问题。

为什么如此？

因为我们承认，是抽象父类提供了我们希望在所有子类实例中存在的数据类型定义。如果我们继续修改父类的行为，那么这些行为变化随后应当相应地在所有子类中显现出来，这是一个理想的结果。

遗憾的是，我们无法对基于代码使用的继承层次结构说同样的话。当层次结构是为了方便访问有用方法而构建的时，对这些共享方法的更改必须根据其对所有子类的相应影响进行评估。

如果说导致极具价值的酒吧时间毁灭性损失的最显著原因，那就是为了代码使用而构建的继承层次结构。

幸运的是，我们比他们清楚。当那些流行的类 MVC 框架希望通过让同事扩展一个加载了便利方法的基模型类来“污染”他们的头绪时，我们可以采取措施保护我们的应用程序代码免受它们所代表的危险侵害。

思考一下这一点——如果在构建应用程序的过程中，我们最终创建了一百个不同的模型类，它们都基于框架的便利导向的基模型，结果就是我们有一百个模型对象，其行为可能会因为底层基类的变化而改变（读作“崩溃”）。

这并不是一个遥不可的场景。如果框架的基模型类删除了 `save()` 方法并增加了 `insertOrUpdate()` 方法，由于我们的模型与框架抽象基类之间存在依赖，我们将有一百个损坏的模型类。

现在考虑另一种策略的影响，这种策略将“可保存性”（save-ability）注入到我们的模型类中，而不是在抽象基类存在的“可保存性”之上构建模型类。

如果我们用自己的适配器类封装框架的基模型，然后安排将其注入到新的模型实例中，我们就保护了我们的模型层，免受该抽象基类中此类破坏性的接口变化。

并且也偏于组合（Composition）。

```php
class Order
{
    private $status;

    public function isDispatched()
    {
        return $this->status == "DISPATCHED";
    }

    public function canBeCancelled()
    {
        if ($this->status == "PENDING") {
            return true;
        } else if ($this->status == "PROCESSING") {
            return true;
        } else if ($this->status == "DISPATCHED") {
            return false;
        } else if ($this->status == "CANCELLED") {
            return false;
        }
    }
}
```

当然，我将这些精简为为了恰恰表达观点的几种方法样式。当我们开始在对象方法中看到类似这样的逻辑时，这就是需要使用状态模式（State Pattern）的迹象。一方面，我们在报告某个属性是否为某个特定值；另一方面，我们引入了臃肿的条件结构，通过测试属性的值来决定如何向调用者报告。

换句话说，我们正在检查一个或多个对象属性的状态，以决定我们应该如何响应。

这代表了一个问题，而且它不是通过向类中添加常量就能解决的，尽管这显然是是需要的。当业务团队冲到我们的办公桌前，给我们另一个可能的状态时，我们在把那个新状态挤进去时将面临一项真正的棘手工作——这种工作需要仔细处理，以确保为所有此类类型的方法给出正确的响应。

我们该如何解决这个顽固的烂摊子？起初看起来，一个继承层次结构（inheritance hierarchy）

并且也偏于组合。

似乎是可行的方案，因为这将为我们提供为每个表示的订单状态创建一个子类。

```php
<?php
abstract class OrderAbstract
{
    protected $status;
    abstract public function isDispatched();
    abstract public function canCancelled();
}
```



再次，我只提到了我们感兴趣的两个示例方法来说明这一点。自然地，一个 `Order` 对象最终会比这复杂得多。

尽管如此，这里是用于表示待处理（pending）订单的相应子类。

```php
<?php
class PendingOrder extends OrderAbstract
{
    public function isDispatched()
    {
        return false;
    }
    public function canCancelled()
    {
        return true;
    }
}
```

另一个类仅用于说明另一种可选的实现。

```php
<?php
class DespatchedOrder extends OrderAbstract
{
    public function isDispatched()
    {
        return true;
    }

    public function canBeCancelled()
    {
        return false;
    }
}
```

这似乎是解决该问题的非常合适的方案。涉及的代码非常清晰且易于阅读。当业务团队下次带着一个新的需要实现的订单状态再次冲到我们桌前时，我们不能直接推出另一个子类来表示该状态吗？

我们可以这样做，但这种方法有两个关键问题。其中一个强调了我们需要在一个活生生的、呼吸的、运行良好的应用程序上下文中考虑我们所编写的代码。换句话说，在页面上这看起来很完美。但在现实世界中，我们将面临问题。

何解？首先，如果我们从事将待处理订单转换为已发货订单的业务，我们知道订单必须从一个状态转换到另一个。这意味着我们保证在订单生命周期中会有状态变化点，因为如果状态不，我们就会破产。

使用继承层次结构来表示订单状态，这意味着我们要么用更新后的状态重新实例化一个新的订单对象，要么在现有的订单对象中设置错误的状态。我们应该选择哪一个？低效的路线还是无效的路线？

答案显然两者都不是。

答案自然应该是两者都不是。

通过检查一个或多个对象属性的状态来决定我们应该如何响应。这代表了一个问题，而且它不是通过向类中添加常量就能解决的，尽管这显然是需要的。当业务团队冲到我们的办公桌前，给我们另一个可能的状态时，我们在把那个新状态挤进去时将面临一项真正的棘手工作——这种工作需要仔细处理，以确保为所有此类类型的方法给出正确的响应。

我们该如何解决这个顽固的烂摊子？起初看起来，一个继承层次结构并且也偏于组合。

似乎是可行的方案，因为这将为我们机会为每个表示的订单状态创建一个子类。

并且也偏于组合（Composition）。

```php
class Order
{
    private $status;

    public function isDispatched()
    {
        return $this->status == "DISPATCHED";
    }

    public function canBeCancelled()
    {
        if ($this->status == "PENDING") {
            return true;
        } else if ($this->status == "PROCESSING") {
            return true;
        } else if ($this->status == "DISPATCHED") {
            return false;
        } else if ($this->status == "CANCELLED") {
            return false;
        }
    }
}
```

当然，我将这些精简为为了恰恰表达观点的几种方法样式。当我们开始在对象方法中看到类似这样的逻辑时，这就是需要使用状态模式（State Pattern）的迹象。一方面，我们在报告某个属性是否为某个特定值；另一方面，我们引入了臃肿的条件结构，通过测试属性的值来决定如何向调用者报告。

换句话说，我们正在检查一个或多个对象属性的状态，以决定我们应该如何响应。

这代表了一个问题，而且它不是通过向类中添加常量就能解决的，尽管这显然是需要的。当业务团队冲到我们的办公桌前，给我们另一个可能的状态时，我们在把那个新状态挤进去时将面临一项真正的棘手工作——这种工作需要仔细处理，以确保为所有此类类型的方法给出正确的响应。

我们该如何解决这个顽固的烂摊子？起初看起来，一个继承层次结构（inheritance hierarchy）并且也偏于组合。

似乎是可行的方案，因为这将为我们提供机会为每个表示的订单状态创建一个子类。

```php
<?php
abstract class OrderAbstract
{
    protected $status;
    abstract public function isDispatched();
    abstract public function canCancelled();
}
```

再次，我只提到了我们感兴趣的两个示例方法来说明这一点。自然地，一个 `Order` 对象最终会比这复杂得多。

尽管如此，这里是用于表示待处理（pending）订单的相应子类。

```php
<?php
class PendingOrder extends OrderAbstract
{
    public function isDispatched()
    {
        return false;
    }
    public function canCancelled()
    {
        return true;
    }
}
```

另一个类仅用于说明另一种可选的实现。

```php
<?php
class DespatchedOrder extends OrderAbstract
{
    public function isDispatched()
    {
        return true;
    }

    public function canBeCancelled()
    {
        return false;
    }
}
```

这似乎是解决该问题的非常合适的方案。涉及的代码非常清晰且易于阅读。当业务团队下次带着一个新的需要实现的订单状态再次冲到我们桌前时，我们不能直接推出另一个子类来表示该状态吗？

我们可以这样做，但这种方法有两个关键问题。其中一个强调了我们需要在一个活生生的、呼吸的、运行良好的应用程序上下文中考虑我们所编写的代码。换句话说，在页面上这看起来很完美。但在现实世界中，我们将面临问题。

何解？首先，如果我们从事将待处理订单转换为已发货订单的业务，我们知道订单必须从一个状态转换到另一个。这意味着我们保证在订单生命周期中会有状态变化点，因为如果状态不，我们就会破产。

使用继承层次结构来表示订单状态，这意味着我们要么用更新后的状态重新实例化一个新的订单对象，要么在现有的订单对象中设置错误的状态。我们应该选择哪一个？低效的路线还是无效的路线？

答案自然应该是两者都不是。

而且要偏于组合（Composition）。

只需要确保它获取适当的状态实例即可。对于一个繁忙的应用来说，这是一个巨大的优势。

在编写本文时，我们正处于一个令人兴奋的时刻，有几个项目正尝试攻克状态化的 PHP 应用。与普通 PHP 脚本的 `boot->shutdown` 生命周期不同，在生产能够维持多个请求上下文和状态的 PHP 应用程序服务器方面取得了巨大进展。我们需要关注如 `Appserver.io`* 和 `ReactPHP`* 之类的项目，因为它们很可能消除我们目前所知的对缓存的需求。

> http://appserver.io

http://reactphp.org/

## 策略模式（Strategy Pattern）

与状态模式（State Pattern）密切相关的是策略模式。在某些情况下，它们的关系如此紧以难以区分。想象一下 Lizzie 有一个双胞胎姐姐 Lottie。她们长得一模一样，衣服也一模一样。区分它们的唯一方法是她们吃冰淇淋的时候，因为 Lizzie 会是那个激烈守护开心果味、巧克力和薄荷口味的人；而另一方面，Lottie 则相当偏爱 Ben & Jerry's "Pish Food"。

噢，抱歉。

幸运的是，状态模式和策略模式并没有那么难以区分。同样地，到此为止，我们将注入一些封装的行为，该行为将代表一种在外部（通常是外部数据）上运行的自定义算法。

这是状态模式和策略模式区别的关键部分。状态模式根据实现者内部状态的某些概念提供了可交换的行为，而策略模式则根据我们希望这些行为如何处理事物的概念提供了可交换的行为。

而且要偏于组合。

显然，我们在这里讨论的是执行者（doers），在这种情况下我们需要一个接口。一个能够保证方法或多个方法存在的接口，这些方法将是我们接入目标行为的钩子（hooks）。

这相当方便，因为策略模式的非正式定义如下：定义一组相关的算法，将每一个算法封装为自己的对象，并用通用接口将它们统一起来，确保它们是可交换的。

从上面这段话中产生了一个有趣的点。定义由通用接口统一的一组相关对象，听起来它们似乎可能是抽象类和一组相关子类的类的候选者。

在某些情况下，这确实是合适的，但仅当你可以确定每个封装的策略将管理其自身的对象状态时才如此。

对于大多数用例来说，每个策略将操作的状态将存在于策略被注入的消费者对象内部，或者存在于与策略及其消费者完全分离的数据或对象上。

在我们深陷理论之前，让我们启动一个例子让旅程变得顺畅一点。

```php
<?php
class ReportData
{
    private $data;

    public function getOutput($format = 'csv')
    {
        switch ($format) {
            case 'csv':
                $lines = [];
                foreach ($this->data as $row) {
                    $lines[] = '' . implode(',', $row) . '';
                }
                return implode("\n", $lines);
                break;
            case 'array':
                return $this->data;
```

而且要偏于组合。

235

```php
break;
}
}
```

这里没什么特别的——一个定义对象的类，该对象似乎持有着报告数据。显然，这个对象是从传递到模型层的请求中被发出的，一次又一次，我们似乎有一个条件结构来决定报告数据的检索格式。

无论这个条件结构是我们在之前在状态模式中看到的 if/else 子句堆，还是像这里的 switch 语句，并不重要。如果我们发现自己在根据条件语句选择要运行的代码块，我们几乎肯定会从将这些代码块抽象为代表可注入行为的独立对象中获益。

尽管如此，我们这里的示例说明了报告数据如何作为（构建得糟糕的）CSV 字符串或原始数据数组返回。尽管业务团队一直在催促我们提供 HTML 表格、PDF 和用于 API 的 JSON 字符串。

我们要向 switch 语句中再添加三个情况吗？不，我们当然不这样做。



我们也不会创建一个由抽象父类链接起来的 `ReportData` 类族，这正是是因为我们在上一节的订单（`Order`）示例中看到的原因。如果这个对象代表报告数据，那么可以假设生成结果至少花费了成本。因此，通过缓存这些数据可能会节省大量的资源，即使是短时间内。

为什么呢？

业务团队要求数据能够以 HTML 表格以及 PDF/CSV 的形式可用。无论他们的大脑有时运行得有多么奇异，我们至少可以假设他们的愿望包括在浏览器中显示这些数据，并提供指向下载文件的链接。

这些输出格式要求是表示为可注入行为的完美候选者，每种所需的输出格式都由一个单一的、封装良好的算法表示，用于相应地转换报告数据。

而且要偏于组合。

考虑到这一点，让我们先看看我们可能如何修改 `ReportData` 类。

```php
class ReportData
{
    private $data;
    private $formatter;

    public function setFormatter(ReportFormatStrategy $formatter)
    {
        $this->formatter = $formatter;
    }
    public function getOutput()
    {
        if (isset($this->formatter)) {
            return $this->formatter->formatData($this->data);
        }
        return $this->data;
    }
}
```

我们在这里做了什么？首先，我们极大地简化了 `getOutput()` 方法，只有两个选择可以适应对数据的每可能的请求——要么是对原始数据数组的请求，要么是在返回之前对该数组进行格式化的请求。

第二点是，我们的 `ReportData` 对象现在接受一个用于 `setFormatter()` 方法的格式器。具体来说，该方法类型提示了一个佩有 `ReportStrategy` 接口的对象。

> 在为策略模式实现提供接口时，通常在接口名称后面加上“Strategy”一词非常有用。这使得接口的意图变得完全清晰。

结果，我们现在有了一个 `ReportData` 类，它会简洁得多，但能够以团队现在和未来可以想象的任何格式输出其数据，而不需要要求我们进一步修改 `ReportData` 类。

而且要偏于组合。

我们需要快速看一眼剩余的代码来看看它是如何实现的。首先，统一接口看起来像这样：

```php
<?php
interface ReportFormatStrategy {
    public function formatData(array $data);
}
```

嗯，这不能更简单了。具体的策略又是怎样的？

```php
<?php
class JsonFormatStrategy implements ReportFormatStrategy {
    public function formatData(array $data) {
        return json_encode($data);
    }
}
```

使用 JSON 总是总是简单得多。其他格式呢？

```php
<?php
class CsvFormatStrategy implements ReportFormatStrategy {
    public function formatData(array $data) {
        $csv = fopen('php://temp', 'r+');
        $filesize = 0;
        foreach ($data as $row) {
            $filesize += fputcsv($csv, $row);
        }
        fseek($csv, 0);
        $csvData = fread($csv, $filesize);
        fclose($csv);
        return $csvData;
    }
}
```

并且同样支持组合。

`CsvFormatStrategy` 被整洁地封装在它自己的类中，我们还借此机会对算法进行了重构，以更简洁、更优雅的方式完成所需的任务。我们可能在这里是在对同道中说教，但这确实是一个优雅得多的方法。

通过两个输出格式化策略，显而易见的是我们拥有了如此高度可复用的代码，这允许我们将任何数组转换为 JSON 结构以向 API 调用发送响应，或者准备一个可以到浏览器的 CSV 文件，而无需接触文件系统。

这是策略模式本身的一个特性。由于这些离散的行为单元是完全自给包含的（也就是说，它们不感知消费它们的对象），因此它们可以被广泛地复用。

如果你简单回想一下关于继承的章节，你可能还记得我们曾考虑过将一个非常有用的方法向上移动到父类中以便共享吗？现在至少显而易见的是，使用组合比尝试用继承来凑合要强得多，它是代码复用的机制。

通过状态模式和策略模式，我们看到了两种向对象中注入可切换行为以在运行时修改我们行为方式的方法。这两种强大的技术让我们能够在不修改对象本身的情况下，改变系统内部主对象之间交互的方式，只需让它们能够接收我们想要注入的行为即可。

这两个模式是所谓的“委托模式”（Delegation Pattern）的更具体的例子，在委托模式中，一个对象不再亲自执行特定任务，而是将该任务委托给它所的一个辅助对象。正是通过这种方式，我们才能支持在第一部分遇到的那种委托多态。

尽管如此，我们并不总是需要向主对象中注入行为来支持组合优于继承。我们可以将注入概念反过来，将主对象注入到包装器中，以修改它们的行为。

并且同样支持组合。

# 装饰器模式 (The Decorator Pattern)

在运行时更改对象的行为不仅限于状态模式和策略模式。我们考虑如何可能支持组合的第三种模式采取了相反的方法：通过将对象注入到包装器中来改变其行为。

## 如何实现？

要回答这个问题，我们应该从模式的定义本身开始。它大致如下：

装饰器模式（The Decorator Pattern）允许对对象进行静态或动态包装，以修改它们现有的职责或属性。

之所以说“大致像这样”，是因为在这个特定主题上，可能会发现许多有些微妙且令人困惑的变体。不过，我们可以先总结几个要点，以帮助理解这个“怪兽”。

首先，我们将创建一个类来包装我们关注的主对象，以便将主对象注入到我们的包装器中。由于我们的包装器将依赖于注入的主对象，这应该在构造函数中发生。

第二个要点是，如果我们修改主对象的行为方式，我们的装饰器也必须提供一个与被包装对象相同的接口。这就是事情可能变得困惑的地方，因为该特定的 UML 图表规定装饰器是主对象的子类，从而利用继承来获取父类。

我们将先通过一个相当典型的披萨例子来看这种技术，以便我们能够掌握原始的定义。但此之后，我们将查看该模式的另一种解释，并考虑每种方法的优缺点。

这是你的披萨。

并且同样支持组合。

```php
<?php
abstract class PizzaBase
{
    private $ingredients = [];
    public function addIngredient($ingredient)
    {
        $this->ingredients[] = $ingredient;
    }
    public function getIngredients()
    {
        return implode(', ', $this->ingredients);
    }
}

class MargheritaPizza
{
    public function __construct()
    {
        $this->addIngredient('cheese');
        $this->addIngredient('tomato');
    }
}

$pizza = new MargheritaPizza();
echo $pizza->getIngredients();
// output: cheese, tomato
```

按照此模式的 UML 定义，我们现在应该派生这个披萨基类以开始提供装饰器。这意味着首先，我们需要一个基装饰器，让我们现在就做这个吧。

并且同样支持组合。

```php
<?php
abstract class PizzaDecorator extends PizzaBase
{
    private $pizza;
    public function __construct(PizzaBase $pizza)
    {
        $this->pizza = $pizza;
    }
}
```

注意这种感觉从一开始就是多么别扭。我们从一个抽象父类中定义了一个抽象类。诚然，我们的抽象装饰器基类现在拥有了所需的接口，这正是我们需要做的，但对于我们这些面向 PHP 卓越导向的大脑来说，将抽象类作为子类来创建一个待处理的抽象父类似乎并不协调。如果我们应该将抽象类视为定义新数据类型的蓝图，那么对于从另一个蓝图定义一个新数据类型，我们应该感到有些不适。

我们很快会修复，但现在请注意基装饰器类型在其构造函数中对我们自己的类的类型提示。这是装饰器模式的一个关键特性——装饰器和它所组合的对象都向世界呈现相同的接口。

现在，我们需要创建几个装饰器来修改我们那相当基础且略显平庸的玛格丽披萨。

```php
class HamDecorator extends PizzaDecoratorBase
{
    public function getIngredients()
    {
        return $this->pizza->getIngredients() . ', ham';
    }
}
$pizza = new MargheritaPizza();
$decoratedPizza = new HamDecorator($pizza);
echo $decoratedPizza->getIngredients();
// output: cheese, tomato
```

到目前为止，一切看起来良好。我们将原始的 `MargheritaPizza` 实例包装在一个新的 `HamDecorator` 实例中，然后调用 `getIngredients()` 方法查看列表是否发生了变化。果然，它变了，因为装饰器对主对象的 `getIngredients()` 方法的返回值应用了自身的“转换”。

注意最后那几行示例代码可以重写为如下：

```php
$pizza = new HamDecorator(new MargheritaPizza());
echo $pizza->getIngredients();
```

结果是一样的；我们仍然是将一个新的 `MargheritaPizza` 实例传递给 `HamDecorator` 的构造函数。然而，这将帮助我们说明装饰器模式的另一个特性：装饰器必须允许递归组合。

这一特定特性是将装饰器与普通适配器区分开来。适配器通常只包装一次对象，而装饰器提供了无限的递归组合，以无限次地修改方法的结果。我们可以通过 `OliveDecorator` 看到这种操作。

```php
class OliveDecorator extends PizzaDecoratorBase
{
    public function getIngredients()
    {
        return $this->pizza->getIngredients() . ', olives';
    }
}

$pizza = new OliveDecorator(
    new HamDecorator(
        new MargheritaPizza()
    )
);

echo $pizza->getIngredients();
// output: cheese, tomato, ham, olives
```

并且同样支持组合。

而且也偏好组合。

我意识到这个说法可能很难理解，但它是事实。有些人喜欢吃沙拉！而那些吃沙拉的人其实也喜欢橄榄。

我确定你已经看出问题的走向了。由于我们之前创建的 `OliveDecorator` 在构造函数中需要一个 `PizzaBase` 实例，因此它以目前的形式并不完全可重用。

我们要重构吗？要在我们日益摇摇欲坠的食物层级中创建一个 `AbstractFood` 作为新的终极父类吗？这样做确实让我们可以在任何菜肴上“装饰”上额外的橄榄。

然而，我们在这里面临的问题是，我们将得到一个真正难以维护的继承层级结构，无法指望任何团队成员能在脑中记住这样一个层级结构。结果呢？为了后期修复 Bug 而牺牲了宝贵的发布时间。

幸运的是，这些都是非常容易解决的。通过抛弃装饰器模式的原始定义，并用更现代的方式对其重塑，就可以解决。这种方法提炼了原始模式，但去掉了继承要求所拖累其后的负担。

如果装饰器需要与它所装饰的对象呈现相同的接口，我们只需要提供一个涵盖所需行为的接口即可。

换句话之，放弃继承层级结构，并使用通用接口来保证所需的行为。

为了说明它的工作原理，我可以回到之前的快速应用程序，并以面向接口的方式重新编写示例，但我实际上想用一种更合适的方式来涵盖这一点。我所说的“更合适”，是指一种能更简洁地证明为什么继承方法是有缺陷的方法。

自然地，我们将从 `Warrior`（战士）的类定义开始。

而且也偏好组合。

```php
<?php
class Warrior
{
    private $health = 100;
    public function take($damage = 0)
    {
        $this->health -= (int) $damage;
        if ($this->health < 1) {
            throw new Exception("天鬼，我死掉了");
        }
    }
}
```

一如既往，我们缺少了构成 `Warrior` 实例的大部分类代码，只关注相关的特性：在这种情况下，一个允许我们的战士角色在战场上承受伤害的方法，以及我们角色健康值的实时计数。

当然，我们在这里是在他或她送上战场之前对其进行装饰，这是因为我们希望我们的战士能战胜敌人。如何装饰？用护甲！

首先，我们需要那个极其重要的接口。根据我们上面的 `Warrior` 类，这将是一个简单的接口。

```php
<?php
interface Damageable
{
    public function takeDamage($damage = 0);
    public function getHealth();
}
```

接下来，我们需要一个告白。告白我们并没有完全抛弃继承，因为我们仍然要创建一个相关的装饰器家族，并且我们仍然需要尊重递归组合的能力，这是此类装饰器的一个基本特征。我们现在就来这样做。

而且也偏好组合。

```php
<?php
abstract class ArmourDecorator implements Damageable
{
    protected $health = 0;
    protected $subject;
    public function __construct(Damageable $subject)
    {
        $this->subject = $subject;
    }
    public function takeDamage($damage = 0)
    {
        $this->health -= (int) $damage;
        if ($this->subject->health < 1) {
            $this->subject->takeDamage(abs($this->health));
            $this->health = 0; // 需要重置为零
        }
    }
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```

作为一个抽象数据类型定义，这个类为我们完成了一切。构造函数对所需接口的类型提示允许我们实现开发装饰器家族所需的递归组合。

此外，我们有了对 `Damageable` 接口要求的两个方法的实现。这使得我们在创建具体的装饰器时，工作变得非常轻松。

但首先，我们需要将那个可装饰的接口放入 `Warrior` 类本身中，并添加 `getHealth()` 方法以满足接口的要求。

而且也偏好组合。

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```

等等，让我根据 OCR 的流程重新对齐逻辑：

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        // 基于文本上下文的实现逻辑
    }
}
```

实际上，查看 OCR 的文本结构：

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```

修正：OCR 显示 `Warrior` 类正在被更新。让我们正确地重构最后的片段：



```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        // 文本暗示 Warrior 现在实现了 Damageable
    }
}
```

等等，第 261 页的文本说是：

```php
<?php
class Warrior implements Damageable
{
    public function getHealth()
    {
        return $this->health + $this->subject->getHealth();
    }
}
```

实际上，该代码片段在 OCR 或源文件中似乎有一个错误（因为 `Warrior` 并没有 `$subject`）。让我们遵循文本的意图：

最后，我们能够以适当的方式开始装饰我们的战士了。

```php
<?php
class BoiledArmour extends ArmourDecorator
{
    protected $health = 150;
}

class ChainMailHaerk extends ArmourDecorator
{
    protected $health = 200;
}

class OakShield extends ArmourDecorator
{
    protected $health = 75;
}

$decoratedWarrior = new OakShield(
    new ChainMailHaerk(
        new BoiledArmour(
            new Warrior()
        )
    )
);
echo $decoratedWarrior->getHealth(); // 输出: 525
```

我们的最终结果？一个被“包裹”在煮皮、链甲和橡木盾中的 `Warrior` 实例。一旦我们把这个角色送上战场，它可以尽可能地向内吸收。那么我们的工作完成了吗？还不完全。但在我们处理它之前，我们应该花一点时间考虑我们取得了什么。

通过将装饰器家族与被装饰的对象解耦，我们成功地释放了装饰器并提高了了它们的可重用性。

我们在这里引入了一个非常明显的问题。如果我们把 `Warrior` 实例发送到战场，除了承受伤害和报告其当前健康值之外，我们什么也做不了。对于战士来说，这很糟糕。

我们应该如何修复这种情况？

我们可以继续扩展所需的接口，使其也包含所有 `Warrior` 的战斗方法，但这将是混乱。我们将得到一个某种方式知道如何战斗的 `ChainMauber`，这显然是错误的。

相反，我们需要用完全不同的策略来处理 `Warrior` 的构建。那个词。策略。

由于我们的护甲装饰器都与防御有关，我们最好的方法是使用策略模式创建防御策略，例如 `StandAndFight`（就地抗战）、`HideAndSnipe`（隐蔽伏击）或 `RunAway`（逃跑），然后我们可以根据需要用护甲对其进行装饰。

同样的方法也可以应用于创建战斗策略的概念以及相应的装饰器；火焰的？还是毒尖的？这两个选项同样适用于 `Sword`（剑）、`Dagger`（匕首）或 `Arrow`（箭）的实例。

而且也偏好组合。

如果我们战士的健康、护甲和武器也由状态模式（一个非常合适的候选者）表示，那么在构建 `Warrior` 实例时，我们显然有一个相当复杂的构造需要考虑。幸运的是，那是下一章的主题，实例化恐惧（Instantiaphobia）。

# 总结

在一个致力于帮助我们摒弃继承是有用的这一观念的章节中，我们学习了三种常见的设计模式，这些模式有力地证明了放弃继承作为创建可重用代码的手段。

除非你真的认为橄榄配料足以被视为一种披萨，是这样。

通过在本章中考虑的三种设计模式，我们应用程序中的核心实体能够在不更改核心实体实际代码的情况下，支持任何所需的行为修改。

每种模式都为我们提供了一种极其强大的方式，以保持符合开闭原则（SOLID 原则中的第二条，第四部分将致力于该原则）。我们只需要几个章节后就能发现如何做到。

# 告知，而非询问

在软件开发海洋的深水区航行的所有原则中，*告知，而非询问*（Tell, Don't Ask）原则或许是那些狂野暗流中最不常见的一个。事实上，如果构成 SOLID 原则的原则是装饰豪华的加勒比邮游轮，那么这一原则可能更被视为一艘俄亥俄级导引导导弹潜艇，静静地穿行在深水之中，无人看见，无人听闻。在大多数时候，它都处于视野之外，被遗忘在外。

它很少出水面，但当你开始欣赏那些流畅线条的力量时，尽管它并不能完全装载一百五十枚“战斧”巡航导弹。

尽管如此，这一特定原则在野外如此罕见，但对于一个拥有蓬勃 PHP 才华的开发者来说，它是可以加入思维工具箱的最强大的原则之一。

在所有这些炒作和渲染声势中，你可能会认为这是一个充满了神秘奥秘和禁忌知识的原则。认为它被赋予了某种异世界的力量；一种需要通过符文和咒语驯服，并在洒在地面上的盐圈内安全地施放的跨维度位移兽。

尽管要感谢《实战程序员》中那些超级聪明的人们，但现实完全并非如此。事实上，这个命名恰当的原则在实际上非常简单。你的代码应该试图“告知”对象去做某些事，而不是“询问”状态元素并根据返回的值做出决策。

带着这种思想，让我们从 Alex Sharp 的一段引用开始，他在他的书《Smalltalk by Example》中用寥寥数语就非常简洁地引入了这一观点。

> 过程化代码获取信息然后做出决策。面向对象的代码则告知对象去做某些事。 – Alex Sharp

这段引用中的第二个句子触及了该原则的核心。许多经验丰富的 Web 应用开发者都见过控制器类的动作方法（action methods）访问模型对象的属性，以便根据这些属性的值做出逻辑决策，或者直接对该对象属性执行某种操作。

为了说明这一点，让我们考虑以下代码段落：

```php
class OrderController {
    public function addOrderAction() {
        $userBalance = $userAccount->getBalance();
        if ($userBalance < $orderTotal) {
            throw new InsufficientFundsException();
        }

        $newBalance = $userBalance - $orderTotal;
        $userAccount->setBalance($newBalance);
    }
}
```

如往常一样，我有些依赖你在脑海中补全初始化的空白，以免让代码示例变得过于混乱。这个示例的重点在于两个部分。第一部分是一个逻辑决策（或者说是验证测试），用于判断用户的余额是否足够支付显然正在下单的订单。

```php
$userBalance = $userAccount->getBalance();
if ($userBalance < $orderTotal) {
    throw new InsufficientFundsException();
}
```

在这里，我们从 `$userAccount` 对象中提取了余额值，并将该值与 `$orderTotal` 变量进行比较。如果用户的余额小于订单总额，则会抛出一个 `InsufficientFundsException`。

该示例中的第二个考虑是在对象外部清晰且直接地操作对象的属性。

```php
$newBalance = $userBalance - $orderTotal;
$userAccount->setBalance($newBalance);
```

在这种特定情况下，我们设置了一个名为 `$newBalance` 的新变量，作为从 `$userBalance` 中减去 `$orderTotal` 的结果，然后将其传回 `$userAccount` 对象，作为它应该维持的新余额值。

只需要仔细考虑片刻，就会意识到这是一种极其糟糕的编程方法。在两种情况下，我们都在访问一个属性值，而该值本该应该是私有且仅属于所属对象实例的。在在这两种情况下，我们都违背了本应该理解的封装概念。

我们示例中的第一种情况很糟糕，但第二种情况是不可原谅的。

尽管如此，这种情况在 PHP 代码中发生得异常频繁，以至于你可能会认为这实际上是处理问题的方法。花点时间考虑你过去编写的控制器方法；你曾多少向模型层请求过数据元素，然后要么将它们处理成视图文件使用的结构，甚至对获取到的值做出了某种逻辑决策？我过去确实做过成百上千次这种事情。

如果我们被要求是告知对象去做某些事，而不是询问它们的细节并由我们执行操作，那么我们就不再应该在控制器中看到这样的违规行为了。

为什么创建这种违规行为是坏事呢？答案在于我们在企业级应用程序中编写的代码很少是完整、完成并结束的。业务团队中那些讨厌的小家伙们会确保做到这一点。

因此，每当我们暴露对象的状态细节点时（正如在上面的示例中做了两次那样），我们也将代码与这些相同的状态细节紧密耦合在一起。

换句话说，我们让自己容易于出现类似 bug 的情况，如果我们未来在某个时刻修改了 `UserAccount` 类的内部实现，这些情况肯定会出现。

考虑一下如果我们未来在某个时刻修改了 `UserAccount` 类的内部实现将产生的影响。如果计算余额的逻辑发生变化，我们被迫去寻找执行该计算的每一个控制器。

正确的答案自然是，你倾向于修改一个类。带着这种思想，在我们继续之前，让我们修复一下代码，以处理这些违规情况。这样的修复可能像这样：

```php
class OrderController {
    public function addOrderAction() {
        try {
            $userAccount->payOrder($order);
        } catch (InsufficientFundsException e) {
            // 处理异常
        }
    }
}
```

在这里发生了什么？首先，我们从 `addOrderAction()` 方法中消除了这段验证代码。它从根就不属于那里。为什么不呢？原因很简单，控制器的工作不是对模型状态（在本例中为实际余额值）拥有深入了解。只有模型对象本身（即 `UserAccount` 实例）应该它是如何工作的。第二种情况，即直接修改实例值的情况也被从控制器中移除了。

永远记住：动作方法没有权限直接修改属性。动作方法的存在是为了让事情发生，而不是由它们自己执行工作。

再次查看修复方案。我们将余额验证行和余额修改行替换了单一的方法调用：

```php
$userAccount->payOrder($order);
```

## 不要询问，要指令 (Tell, Don't Ask)

如果业务团队走到我们的办公桌前对我们说这句话，这个相当二元的结构会发生什么呢？

“你知道，我们需要的不仅仅是用户和管理员，我们还需要成员角色、版师角色、编辑角色和发布者角色。”

如果我们坚持上述原始且错误的方法，我们需要在原始的 `if else` 中添加几个 `else if ()` 分支。更糟糕的是，用 `switch()` 语句替换 `else`。

然而，如果我们从一开始就有远见，正确地应用了“不要询问，要指令”原则，我们的代码看起来应该是这样的：

```php
echo $user->getWelcomeMessage();
```

现在，业务团队可以花所有时间为我们的用户构思奇妙的新角色，而我们根本不需要关心。至少，我们不需要担心为了正确处理每种用户类型而可能需要修改哪些视图代码片段。基于对象属性值的逻辑决策已经从那些本不属于它的地方被移除了。

“啊，但是，”我听见你说，“这不仅仅是把 `if else` 移动到了用户对象中吗？这并没有完全消除问题。”

对此，将得到一个不棱不定的回答：“不，不一定。”

在不想偏题太远的情况下，让我们花点时间来看。即使我们直接将 `if else` 结构移动到 `User` 类中，我们也会看到质量上的微小提升，因为该逻辑决策被限制在了代码库中的单一位置。记住，我们想要保持代码库 DRY（不要重复原则），而不是让代码散落在多个地方反复出现。

然而，由于我们正寻求以“卓越团队”（Team Brilliance）展现出的天然天赋来构建企业级应用程序，在这种情况下，我们根本不会使用那种 `if else` 结构。避免 `if` 语句的两种可能性立即进入脑海。

第一种可能性是围绕 `User` 类本身创建一个继承层次结构，从而创建一个抽象的 `BaseUser`，并从其创建更专门的子类，如 `Administrator`、`Member` 和 `Editor` 类。这些子类中的每一个都根据需要编写了它们自己的 `getWelcomeMessage()` 方法实现。

如果我们对用户角色的实现要求极其简单，这可能是可以的。

现实情况是，在面对业务团队时，不存在所谓的“简单”。

这引导我们走向第二种也更有可能的用户角色编码方法。我们创建一个角色类的继承层次结构，以 `BaseRole` 为抽象父类，以更专门的子类如 `EditorRole`、`PublisherRole` 和 `AdministratorRole`。每当 `User` 实例实例化时，就会创建这些角色实例并注入到 `User` 实例中。

结果如何？在这种情况下，显示欢迎消息的过程没有使用任何 `if()` 语句来显示所需的消息。`User` 实例被恰当地配备了角色实例，使它们能够正确响应 `getWelcomeMessage()` 方法调用，而没有任何任何决策过程干扰。

让我们回到正轨。如果 Alec Sharp 引言中的关键元素是“面向对象是指指令去做某事”，那么如果我们不是在创建读取、写入和操作对象状态的对象方法，我们到底在做什么呢？

这听起来熟悉吗？这理应如此，因为我们花费了大量时间研究封装。是的，这是我之前提到的循环引用之一。“不要询问，要指令”原则与我们所知的封装以及封装的定义有直接的相关性，即“将属性和作用于属性的方法封装成一个单一逻辑单元”。

这正是为什么 Lizzie 现在正兴奋地指着屏幕跳来跳去的原因。这种突然疯狂且略显反常的行为的原因？编程世界的某些权威在发现这一特定原则时，认为它在许多情况下是多余且没必要的。Martin Fowler 就是其中一位权威，他在他的博客文章¹中对该原则提出了许多非常充分的观点。

¹ http://martinfowler.com/bliki/TellDontAsk.html

在某种程度上，反对者们指出这一点是正确的。如果“不要询问，要指令”原则真的只是告诉我们应该正确地进行封装，那么是的，这个原则本身对于我们这些优秀程序员应该知道的知识清单来说，是不必要的添加。

如果“不要询问，要指令”原则要求我们为对象所持数据所需的每项操作都向对象添加一个方法，那么我们的类随着时间的推移极可能会变得臃肿。我们确实应该努力在尽可能的情况下避免类臃肿。

最后，如果我们对“不要询问，要指令”原则变得狂热，那么我们可能会开始消除之前写在类中的所有 getter 方法。在某些领域，getter 方法因暴露了对象的内部状态而违反了封装原则而受到批评。然而，狂热通常不是好事，而且在这种情况下，完全消除 getter 也会严重限制我们为系统中的对象创建协作者的能力。

想象创建一个 `SalesReport` 对象，它接收了合适的 `SalesOrder` 实例，却无法为它试图构建的报告获取有关这些订单的任何信息。显然，`SalesOrder` 实例需要与 `SalesReport` 实例协作，而且订单对象必须能够提供它们代表的销售订单详情。

那么我们这些“卓越团队”的成员处于什么位置呢？

好消息是，这让我们处于一个非常好的位置。通过将这一原则加入我们的工具箱，我们支持并加强了我们已经理解的内容。当我们无意中对对象状态做出逻辑决策时，更容易发现自己。

# 结论

这一特定原则的力量并非直接来自其内容，而是来自它帮助我们保持符合封装的方式。如果我们正确地进行封装，那么我们极可能遵循了这一原则。反之，如果我们正确地执行，我们同样可能正在正确地封装。

这里的关键在于，这个原则更有可能留在我们的脑海中，并在我们在代码中出错时让我们停顿。因此，有了与俄亥俄级潜艇的比喻。你可能看不到它，但当它向你发射时，你就知道它在那里了！

## 实例化恐惧 (Instantiaphobia)

你可能已经注意到我已经提了好几次这个特定原则了。嗯，好消息是，我们终于到了讨论“实例化恐惧”原则的章节。承认，这是一个我自创的原则，但请放心，它已经离开出炉了足够久，让你可以拿起它、转转它并从每个角度检查它，而不会烫伤手指。

本质上，这个原则处理的是我认为的对使用 `new` 关键字的过敏。不久，我将认为这是开发那种显然具有避免 bug 场景的感应能力的关键技术之一。

该原则本身只是一个简单的句子，所以让我们尽早地解决它。

> 对于应用程序代码库中定义的每个类，应该且只有一个位置可以实例化该类的对象。

反之亦然。如果不承认这一特定原则，将导致代码库对那种最宝贵的商品之一：高质量的发布时间付出惨痛的代价。

在敏捷的世界里，由于过度热衷的业务团队拥有似乎无穷无尽的“扳手”可以随时向工程中投掷，我们并不总能够在构建某个特定类之前预先知道它的最终版本应该长什么样。老实，在敏捷的世界里，我们很少能得到一个完成的对象。相反，我们不得不满足于运行软件的间隙时刻。这些开发时间线上的时刻通常被称为“发布（releases）”，并被标记为此类。

当然，在已经在生产环境的应用代码中修改特定类的构造函数，是初始设计不佳的重大迹象。幸运的是，如果你采纳了我们书中讨论的所有观点，那么糟糕的设计日子应该彻底彻底过去了。

这就是本章存在的初衷——它关乎于今天采用一种非常特定的编码技术来避免未来的头疼问题。在未来的某个时刻，如果你现在就采用这种方法，你的同事很可能会认为你是个读心者。

但这种方法是什么呢？

让我们从一段代码片段开始：

```
$user = new User();
```

我们亲爱的 `user` 类再次出现了！一旦我们庆祝完这个事实，就应该问自己“这段代码在哪里？”在一个设计天真的系统，或者更有可能是一个简单地有机成长的系统中，它会在任何需要 `User` 对象实例的地方无处不在。



从字面上说，在任何需要 `$user` 实例的地方，它都会被实例化。我之前工作过的一个项目在每个请求的开始时都会实例化当前登录用户的 `$user` 实例，无论该实例是否会被用于处理该请求。对于一个具有大量功能的大型应用程序来说，这意味着这一特定行（无论是否有构造函数参数）可能会出现在数百个不同的位置。

如果我们再次过一遍封装章节，但是在一个调用 `new User()` 超过一百次的应用程序内部进行，那么为了更新每一处出现的地方，难道不代表着要进行大量的重复性工作吗？IDE、终端和命令行客户端都提供了全局搜索功能，从理论上讲，这允许你定位并修改每一处出现的地方，以适应构造函数修改后的方法签名。

也就是说，只要你的同事中没有实现过使用持有类名的变量来创建对象的代码。我什么意思是？嗯，让我给你看另一段代码，一段说明动态类名解析的代码：

```php
public function getObject($className)
{
    return $className;
}
```

无论你所选编辑器的全局搜索有多高效，只要有一行代码调用了此方法并将 `'User'` 设置为 `$className` 的值，它就无法找到实例化 `new User` 的每一个代码位置。

在多个位置对同一个类使用 `new` 关键字，这简直是给你制造了无穷的麻烦。就如此简单。

正如在你正在编写的代码中输入 `$user = new User()` 一样简单，我可以以一种近乎自自得意的自信程度向你保证，你以后会在某一个点后悔这个决定。

这就是“实例化恐惧症（Instantiaphobia）”登场的地方。好吧，我承认——这是一个完全虚构的词，但我想它捕捉到了这一特定课程的精髓，可以这么说。我希望达到的是产生一种对创建新实例的非理性恐惧。

我称之为“恐惧（phobia）”对我们非常有帮助。如果恐惧是非理性的恐惧，那么对使用 `new` 关键字产生一种（最初）无法轻易解释的恐惧，将对我们的未来大有益处。

关于对象何时可以被认为是“新生的”，有很多论述，事实上，所提出的论对于旨在在离线世界的桌面上运行的软件确实是正确的。

某些开发者可能会辩称，创建一个巨大且复杂但健壮且安全的应用程序，并在整个代码库中对相同的类调用数百次 `new`，是完全可能的。这样的应用程序可能会被誉为我们新发现的恐惧确实是非理性的唯一证明。

### 但是

这种方法伴随着巨大的风险。即使代码库现在是安全且稳定的，未来对任何类的构造方法的任何更改都将涉及大量的工作来实施所有必要的更改。

请记住，我们的世界不是以桌面为导向的离线世界。我们的软件不是作为完成品通过可安装的光盘或 DVD-ROM 交付的。

相反，我们通过遵循精益或敏捷方法论迭代周期来交付标记的发布，编写单个故事（stories）以添加到下一次发布中的产品中，并且业务团队总是站在我们的肩膀上，抓挠着下一个变更请求。

如果对于你应用程序代码中的每个类声明，每个涉及的类都只有一个、单一且独特的位置使用 `new` 关键字，那该有多好？

顺便说一下，我从未暗示我们应该总是避免使用 `new`。在创建面向对象的代码时，这是不可能的。我只是至少想说明这一点。

让我再次过一遍。对于我们在代码库中声明的每一个类，我们应该只有一个且唯一的位置对该类使用 `new` 关键字。

所以，如果我们在应用程序中创建一个 `User` 类，我们需要有一个且只有一个的位置编写相应的 `new User()` 代码。采用这种方法的益处是多多的，尽管它们将在未来的某个时刻才被感受到。

## 每个类中的工厂方法

如果我们想实现每个类仅有一个 `new` 关键字实例的目标，那么开始这项工作最简单的方法是在类本身中添加一个工厂方法。或者换句话，每当我们在应用程序中创建一个新类时，我们可以为该类添加一个工厂方法，我们就解决了 `new` 关键字的单例问题。

这是这种情况的一种说明：

实例化恐惧症（Instantiaphobia）

```php
class User {
    private function __construct() {
        // 初始化对象
    }
    /**
     * 包含类中的工厂方法
     */
    public static function create() {
        return new User();
        // 真实的 (create) 方法自然会为设置用户实例
        // 做更多工作，而不仅仅是 "return new"
    }
}

// 在我们应用程序的其他地方
$user = User::create();
```

在创建时的构造函数处，我们在同一个文件中还有且仅有一次 `new User()` 调用。

想象一下，如果你的应用程序中所有的类声明都自动包含了这个静态 `create` 方法，那么管理对象创建过程会变得简单多少？当该类对象的实例化唯一位置仅位于类定义内部时，安全地修改类构造函数的方法签名会变得简单多少呢？

当然，这并不是最终的解决方案。对于具有同样复杂对象的大型复杂应用程序来说，情况更是如此。眼光敏锐且具有批判性思维的读者已经推断出，对于拥有一组复杂构造参数的对象，如果工厂方法本身仅仅是将这些参数代理给构造函数，那么这种技术对我们来说无异于没有。

在代码中，看起来可能像这样：

```php
public static function create($userId, $userRole, $userAccount)
{
    return new User($userId, $userRole, $userAccount);
}
```

然而，如果该方法执行了一些实际工作，那么工厂方法技术确实可以保护我们免受未来巨大的痛苦。

```php
public static function create($userId)
{
    // 收集角色和账户实例
    $userRole = UserRole::create($userId);
    $userAccount = UserAccount::create($userId);
    // 收集实际的用户详情
    $dbConn = Database::getInstance();
    $userData = $dbConn->query("SQL statement here");
    $user = new User($userData, $userRole, $userAccount);
    return $user;
}
```

这种区别是显而易见的。在应用代码中，获取用户实例的仅仅是 `$user = User::create($userId);`，但返回的对象已经妥善准备了角色和账户对象，并准备就绪。

对于较小的应用程序，这种方法使代码库立即变得更具可维护性。以前你可能有一百个或更多地方实例化 `User` 对象，而现在只有一个地方。当你修改构造函数时，不再需要进行全局搜索和替换——你只需要修改一个方法，而且该方法就位于被修改的构造函数旁边。对于作为初级开发者的你，这种技术也为你带来了更大的便利；而在采用这种方法的团队工作时，它也提供了更高的一致性。

想看——如果你的整个团队都遵循相同的约定，并在目标类相同的类定义中创建对象的工厂方法，那么未来对该对象实例化过程的任何更改都只涉及编辑这一个文件。

使用这种技术还有一个可选的辅助益处。通过将工厂方法放在同一个类中（或放在一组相关类的基类中），你可以将构造方法本身设置为非公共（non-public）。因此，私有（private）或保护（protected）构造函数可以保证客户端代码无法绕过工厂方法过程，通过直接调用 `new` 来获取可用的实例。在基于团队环境中，新成员有时会被直接放置在代码中的约束条件强迫遵循团队规约。一个被设置为私有的构造函数会自动做到这一点。

只要工厂方法是执行任务的实体，而不仅仅是参数列表的代理，这一切就能行得通。

尽管如此，它仍然只是一个折中方案。它远优于我们那些缺乏经验同事可能习惯的在代码库中到处洒 `new This()` 和 `new That()` 的习惯，但离理想状态还有很长的路。

为什么呢？嗯，让我们花一点时间探索一下你可能也想避免这种技术的两个关键原因。

第一个我们已经简要遇到过。如果我们的工厂方法

## 实例化恐惧症 (Instantiaphopobia)

仅仅是将构造参数列表代理给构造函数本身，那么我们的工厂方法完全是多余的，收益随之消失了。这件事本意是为了保护我们更广泛的应用代码，使其不再需要处理该参数列表。这样做是为了让我们在每次构造参数列表更改时，无需对代码库进行全局搜索。

第二个关键问题出现在考虑自动化测试时，这个主题将在《PHP Brilliance in Practice》中更详细地讨论。首先，任何单元测试的爱好者都会对大量静态方法的出现自动感到反感，而且这完全是正确的。

在我们构建大型复杂应用程序的世界里，我们理想上希望尽可能获得高质量的代码覆盖率。然而，在我们最近版本的 `create()` 方法中，我们让单元测试变得不再可能。或者说，是我这么做的，而且是有意的，并将这种断裂分成了两种不同的类型。

第一批接受审判的是对其他静态 `create` 方法的调用：

```php
// 收集角色和账户实例
$userRole = User::create($userId);
$userAccount = User::create($userId);
```

这些硬编码虽然在此例中无疑是有效的，但意味着对 `User::create()` 方法的任何“单元”测试都会同时交叉测试其他的 `create()` 方法。事实证明，这一点也不“单元”。

但第二批接受审判的是这两个罪犯中性质更大的一个——获取一个似乎是数据库连接单例实例的调用。

```php
$dbConn = Database::getInstance();
```

这里有一条绝不应违反的硬规则：单元测试的执行在不需要拖入应用程序存储系统的情况下进行。数据库连接在任何应用程序中始终是性能瓶颈，即使在数据库服务器和应用程序服务器位于同一物理主机上的单机设置中也是如此。

没有什么比运行超过十分钟的测试套件更能杀灭自动化测试的兴趣了。数据库连接在任何应用程序中始终是性能瓶颈，即使在数据库服务器和应用程序服务器位于同一物理主机上的单机设置中也是如此。

富有创意的程序员通过允许单例设置模拟（mock）实例来绕过这个“拖拽数据库”的问题。但编写面向测试的代码还是面向应用程序的代码是另一个引起争议的话题。

那么我们现在该往何处走？我们的改进方案是什么？嗯，既然我们已经成功通过工厂方法将双脚从泥沼中拔出来，并让工厂方法之火温暖了我们的脚趾，我们现在应该准备好进入下一个阶段。

## 提供专用工厂类

标题所示，我们对象创建之旅的下一步是将这些工厂方法移动到它们自己的类中。

在这个阶段，内部规则变为：应用程序中的每个类都应该有一个对应的工厂类。

对于我们的简单示例，从工厂方法到专用工厂类的迁移过程变成了简单的剪贴操作。

我们从 `User` 类中剪切，留下了：

### 实例化恐惧症

```php
class User
{
    // 注意在这里必须恢复
    // 公共（public）访问
    public function __construct($userData, $userRole, $userAccount)
    {
        // 实例设置代码
    }
}
```

并将剪切的内容粘贴到一个新的 `UserFactory` 类中，它看起来应该是这样的：

```php
class UserFactory
{
    public static function create($userId)
    {
        // 收集角色和账户实例
        $userRole = UserRole::create($userId);
        $userAccount = UserAccount::create($userId);
        // 收集实际的用户详情
        $dbConn = Database::getInstance();
        $userData = $dbConn->query("SQL statement here");
        $user = new User($userData, $userRole, $userAccount);
        return $user;
    }
}
```

## 实例化恐惧症 (Instantiaphobia)

将注意力转回 `User` 类，你应该能看到直接的好处。我们的 `User` 类实例不再需要携带一个理论上冗余的静态方法，结果是我们应用程序的内存占用减少了，尽管微乎其微。

更重要的是，我们的 `User` 类是完全可测试的。这段独特的代码允许我们通过向构造函数提供模拟（mocks）、存根（stubs）和虚拟数据来实例化用户对象，并测试对象的所有方法，而不会遇到静态方法调用，或在途中选取数据库单例。单元测试的爱好者们欣喜若舞！

让我们用稍微有不同的措辞再次看一遍，以确认我们刚刚考虑的内容。`User` 类已经精简到只包含与用户对象实例直接相关的方法（诚然，在我们目前的代码中，这已经是一个相当精简的对象了）。

虽然我之前“无意中故意”忽略了提到工厂方法的这个缺点，但现在值得快速看一眼。每当你从一个也包含静态方法的类中实例化对象时，生成的对象实例也会携带那些静态方法。

为了方便理解，我们来简单说明这一点。

```
// 以常规方式获取用户实例
$fred = User::create(1);
// $fred 也携带了 create() 方法
$mary = $fred->create(2);
// $mary 也是如此
$jenny = $mary::create(3);
```

如你所见，我们的 `User` 实例获取了那个工厂方法并使其供使用。或者说，取决于你的观点，是供其“滥用”。

它们确实是这样。

该工厂方法是类定义的一部分，因此预计每个 `User` 实例也会提供对 `create()` 方法的访问。

这是向专用工厂过渡所允许我们规避的问题的问题之一。通过将创建方法移动到它们自己的专用类文件中，我们不再需要浪费处理器周期和内存来在对象上维护冗余方法，面对事实吧，这些对象在繁忙的应用程序运行的一天中会被频繁使用。

此外，没有理由在特定实例上调用工厂方法，特别是当代码已经声明了它的使用意图时——作为一个静态调用的类方法。

这让我们回到了为系统中的对象提供专用工厂的问题上。如果你已经在公司里达到了高级别别，那么很有可能你已经熟悉工厂模式（Factory Pattern），因此，你很可能意识到我在这里提议的并不是这种模式的规范化实现。

在通常术语中，我在这里实际上做的是创建一个通常被称为“简单工厂”（simple factory）的东西。实际上，就“实例化恐惧症”这一原则而言，发生的一切只是我们仍然成功地将 `new` 关键字的使用限制在了单一位置。

让我们再次看一遍代码。

```php
class UserFactory {
    public static function create($userId)
    {
        // 收集角色和账户实例
        $userRole = UserRole::create($userId);
        $userAccount = UserAccount::create($userId);
        // 收集实际的用户详情
        $dbConn = Database::getInstance();
        $userData = $dbConn->query("SQL statement here");
        $user = new User($userData, $userRole, $userAccount);
        return $user;
    }
}
```

从单元测试的角度来看，这仍然是一个噩梦，但我们至少正在取得进展。你可以选择运行覆盖此及任何其他简单工厂的测试套件，与覆盖核心应用程序代码的测试套件分开运行。请记住，相应的 `User` 类不再包含这个充满依赖的静态工厂方法，因此现在可以根据需要向构造函数传递模拟和存根来独立进行完全测试。

不过我们的简单工厂仍然是一团糟。我们该如何清理它呢？

首先，我们应该关注 `create()` 方法列出的依赖项。以下是涉及的代码行：

```
$userRole = UserRole::create($userId)
$userAccount = UserAccount::create($userId)
$dbConn = Database::getInstance();
```

前两行显然应该执行同样的“将工厂方法迁移到它自己的专用类”，允许 `User` 类变得完全可测试。

```
$userRole = UserRole::create($userId)
$userAccount = UserAccount::create($userId)
$dbConn = Database::getInstance();
```



## 实例化恐惧症

一个完全自包含的静态方法是一回事。一个调用其他方法的静态方法是另一回事。一个依赖数据库的静态方法是最糟糕的。

## 实例化恐惧症 (Instantiaphobia)

275

然而，第二个问题更切实际：我们如何让这些工厂在需要的地方可用？回到之前通过静态方法调用访问它们时，我们可以在代码的任何地方调用工厂来为我们创建一个对象。

现在它们是对象实例了，我们必须解决如何在需要的地方让它们可用的问题。如果你碰巧在视觉化化针对这个特定问题的解决方案时遇到了一点困难，请不要担心，你绝不孤单。这是设计和布局应用程序代码库中最棘手的问题之一。尽管第二个问题更切实际，但我们将在更合适的地方处理它的解决方案。不过目前，这里有一个提示：它并不是“构建一个*注册模式*（*Registry Pattern*）的实现”……

由于我们目前正处于一个专门讨论尽量减少 `new` 关键字使用的章节，让我们来处理*实例化*（*newing*）工厂实例的问题。

我们正在寻找的问题的解决方案是某种“超级工厂”，即某种可以产生我们的 `User` 类实例的对象，且该实例的所有依赖项都得到了满足。

我们真正寻找的是以下内容之一：

### 依赖注入容器 (Dependency Injection Containers)

这是一个华丽的名字，但在许多方面，依赖注入容器的行为就像一个“加强版”的普通工厂。本质上，依赖注入容器是一个知道如何准备、配置、创建和管理其他对象实例的对象。

它是如何知道这些的？

你告诉它，这就是怎么做的。无论你是使用库中的第三方容器还是自己编写代码，在这一阶段都不重要。在这两种情况下，你都必须通过直接编写代码或配置参数为容器播入适当的对象构建知识。

无论哪种情况，你最终都会得到一个容器对象，该对象提供对相关工厂方法的访问，以便为你的客户端代码提供所需的正确配置的对象。

将我们的 `UserFactory` 类迁移到某种类似容器的上下文中可能像这样：

```php
class Container
{
    private $db;
    public function __construct(Database $db)
    {
        $this->db = $db;
    }
    public function createUser($userId)
    {
        $userData = $this->collectDbRow('users', $userId);
        $role = $this->createRole($userData);
        $account = $this->createAccount($userData);
        $user = new User($userData, $role, $account);
        return $user;
    }
    public function createRole(array $userData)
    {
        ...
    }
    public function createAccount(array $userData)
    {
        ...
    }
}
```

再次，为了简洁起见，我省略了 `createRole()` 和 `createAccount()` 方法体，但希望你仍然能看到，我们没有在各自特定的类内部维护这些对象创建方法，而是将它们整合到了一个统一的容器结构中。

即使是这样一个简单的结构，也可以注意到 `createUser()` 方法已经获得了它提供一个完成的 `User` 实例所需的所有知识。

```php
public function createUser($userId)
{
    $userData = $this->collectDbRow('users', $userId);
    $role = $this->createRole($userData);
    $account = $this->createAccount($userData);
    $user = new User($userData, $role, $account);
    return $user;
}
```

在这里，我隔离了该方法以便更好地观察。你可以清楚地看到，为了为我们提供一个准备良好的 `User` 实例，容器知道从数据库中获取一行数据，并准备 `User` 实例将依赖的另外两个对象。

这会满足我们的“实例化恐惧症”原则吗？
答案是肯定的。

# 总结

这一章完全是关于培养对使用 `new` 关键字的厌恶，从而尽可能少地使用它。当然，你能够使用 `new` 关键字的绝对最少次数将是每个类一次，这将是极具吸引力的，而正是我们通过遵循“实例化恐惧症”原则所要实现的目标。

让我们再次看看这段措辞：

> 对于应用程序代码库中定义的每一个类，应该有且仅有一个位置可以从该类实例化对象。

顺便说一下，这与挑剔或反复无常无关。遵循这一原则将对保护你那极其宝贵的酒吧时光（pub time）产生非常积极的影响。

如果说有什么事是你肯定的，那就是：在需要的地方随心所欲地创建对象，这种做法在未来保证会变成维护的噩梦。维护噩梦总是随之而来的一件事就是深夜在办公室里修复 bug。

这一切问题的归根结底是：当创建特定对象的环境发生变化时，你会希望修改创建这些对象的唯一位置，而不是得遍遍整个代码库去寻找并修改它们，同时还希望你确实找到并正确地编辑了每一个地方。

我知道，我宁愿和队友们待在酒吧里，而不是成为那个被留下来收拾烂子的人。

## 别射传信者 (Do shoot the messenger)

现在我们已经非常简要地看了依赖注入容器，是时候检查另一个反模式了。令人遗憾吗？是的。可以避免吗？不。

所涉及的反模式被称为“*信员*”（*The Courier*）。这个术语是由 Tom Butler 在他的博客文章 [`https://t.je/oop-anti-pattern.html`](https://t.je/oop-anti-pattern.html) 中提出的。

我们的控制器之所以接受 `$db` 对象是为了将其传递给模型类上的工厂方法。这就是“信员”反模式的体现。一个对象接收了一个它实际上并不使用的依赖项。相反，它接收一个依赖项是为了传递给另一个对象、方法或函数。

为什么这会问题？它是那种问题：虽然今天运行良好，但明天几乎会坏掉。这纯粹是糟糕的设计。不过，让我们关注坏掉的情况。虽然我们似乎遵循了上一章提出的修复方法，即在目标对象上实现工厂方法，但该工厂方法本身在方法签名中声明了依赖项。这意味着调用该工厂方法的代码必须提供该依赖项。

但如果我们的需求变了呢？如果我们清醒过来，决定从工厂方法迁移到完整的工厂对象，或者更好的依赖注入容器呢？

在每种情况下，创建 `Profile` 实例方式的变化都会导致 `ViewController` 类内部的代码更改。无论你选择的 IDE 或编辑器全局搜索替换功能有多强大，你都将面临在根本不需要触碰的代码部分中进行更改（可能是影响深远的更改）的需求。

# 杀掉信使者 282

本质上，我们需要将表单数据数组传递给 `Profile` 模型的实例，以便该模型能够相应地进行更新。这意味着，控制器需要一种获取该 `Profile` 模型实例的方法。

这并不是说我们需要向控制器注入我们正在寻找的那个特定的 `Profile` 实例，尽管这无疑是一个可行的解决方案。相反，我们应该考虑为控制器注入某种描述的工厂实例；一个能够为我们产出构建恰当的 `Profile` 实例的工厂。

```php
class ProfileController
{
    private $profileFactory;
    public function __construct(FactoryInterface $profileFactory)
    {
        $this->profileFactory = $profileFactory;
    }
    public function updateAction()
    {
        $userId = $_SESSION['user_id'];
        $profile = $this->profileFactory->create($userId);
        $profile->update($_POST);
    }
}
```

从这些变化中有很多几点需要注意。首先，最重要的是，我们控制器那种类似于“信使者”的性质现在已被完全消除了。它提供的唯一依赖是它自己真正需要使用的依赖。

在这一特定案例中，第二个但同样重要的考虑是，我们的控制器现在完全与应用程序的存储系统的任何概念隔绝了。这是一个至关重要的变化。控制器不应该感知任何关于应用程序持久化机制的信息，我们在这里所做的更改确保了这一点。

> 我们将在下一章中解释其中的缘由，但**不要和陌生人交谈**

这确实有些讽刺的是，依赖注入容器本身可能被视为一种依赖，但事实是，它通常确实如此。归根结底，本章之所以存在以及它为什么紧接着“实例化恐惧”章节之后，原因就在于此。

当开发者遇到这个命名如此华丽的超级工厂时，他们的第一反应通常是认为依赖注入容器是应用程序中所有准备就对象的唯一且单一来源。

因此，我们将开始看到“信使者”接连出现，因为容器需要从一个层被传输到下一层，再到下一层，如此往复。

处理这种特定场景简单得惊人：反过来看这个过程并向后推。

正如 Lizzie 可能会热于指出的，以前那种开发者会按照请求进入、处理处理并输出响应的方式来思考这个过程。这在我们的应用程序代码中确实很可能发生。

这也是许多初学者处理编写特定功能问题的方法。

但在我们构建它之前，我们并不一定应该那样思考它。

在多层应用程序中，这可能涉及设计一个依赖于持久化层的模型工厂，而模型工厂又由服务代理设置在服务实例上，服务实例又可能被设置在控制器实例上。

换句话说，并没有规则规定我们不能创建多个依赖注入容器并让它们成为每层之间的桥梁。控制器、服务、模型和可持久数据对象都可以由它们各自的专用容器提供；这些是具有极度专注能力的离散单元。

而且再找不到任何信使者的身影。

现在我们真的应该让 Lizzie 回到电脑面前，这样她就可以继续为我们产出优秀的代码了。

# 结论

信使者模式是一种反模式，当依赖注入容器出现时，它经常会现头，简单来说，因为一个实例化的对象需要提供给需要它的对象。

尽管如此，当你遇到一种情况，仅仅将一个对象设置到另一个对象上是为了让接收对象再次将其传递，而不是直接使用它，你就遇到了一个“信使者”实例。

这不可避免地会导致酒吧时间的严重损失，简单来说是因为最终接收者的需求可能会改变。当发生这种情况时，由于有信使者的参与，你不可避免地发现自己必须既更改信使者也要更改最终接收者的代码。这正是宝贵酒吧时间的严重损失。

换句话说，信使者的存在带来了紧密耦合的幽灵，以及这种幽灵不可避免产生的所有问题。

因此，请务必在每一个机会杀掉那些信使者。打断他们的膝盖。使用代码等同于至少 `.38` 口径的武器。并且在这样做时不要留任何活口。

# 不要和陌生人交谈

在上一章中，我们开始观察即使是无意实现的信使者，也极可能让你的应用程序部分变得脆弱且容易出现 Bug。我们看到的示例是一个带有控制器的数据库连接，以便到达模型实例内部的最终终点。

问题不在于代码不起运行，或者它偶尔崩溃（尽管如果你没有对数据库连接的建立进行适当的保护和错误处理，它是可能会的）。不，问题在于，当目标代码接收数据库连接的方式发生任何重大变化时，你必须考虑一系列其他类。

这完全是“我在这里在这里修好了，但现在那里坏了！”的情况。

本章关注一个非常相似的问题，并涉及一个有许多名称的概念，其中之一是**迪米特律**（Law of Demeter）。迪米特律由 Ian Holland 在 1987 年制定，并不是一条法律，而是一条指南。我想我们可以原谅提出这个名字的优秀才子们，因为“迪米特指南”听起来没那么有力。

Emerson¹⁶ 将迪米特律简化为三个简洁的陈述，它们分别是：

- 每个单元对其他单元的了解应该是有限的：仅与当前单元“紧密”相关的单元。
- 每个单元只应该与其朋友交谈；不要和陌生人交谈。
- 只与你的直接朋友交谈。

但在某种意义上，这三个陈述过于简洁了。在没有适当上下文或对该准则预先知识的情况下，很难直观地理解它们的含义或预期应用。

但嘿，这正是本章的意义。让我们开始吧。

¹⁶http://emerleite.com/

# 最少知识原则

上面的子标题给了我们该准则的另一个名称，至少这一次它更符合这个主题的实际内容。这个新名称与我们在本章第一页看到的三个项目点结合得很好。

最少知识原则的背后的思想是，无论你在应用程序内部何处编写，你编写的代码都应该只表达对其周围环境的了解。当你遵循这一特定准则时，你自动促进了代码库中松散耦合的概念，从而导致了更高程度的可维护性。

这到底意味着什么呢？

显然，我们现在需要这样一个例子。

```php
class OrderController {
    public function addOrderAction() {
        try {
            $user->get()
                ->getBalance()
                ->deductAmount($orderTotal);
        } catch (InsufficientFundsException $e) {
            // handle exception
        }
    }
}
```

在这里又遇到了那个被误滥的 `addOrder` 方法，寻找一种让我们的客户支付他们该死的账单的简单方法。

在这种情况下，看起来我们是将订单的值传递给一个名为 `deductAmount()` 的方法，捕获用户账户中没有足够的资金支付订单可能抛出的异常。

这没问题，对吧？我们在那里有错误处理，即使你在这个这么小的代码片段中看不到它，后台中 `UserAccount` 和 `AccountBalance` 对象正在进行懒加载。

## 不要和陌生人说话

Lizzie 对这种方法可不陌生；她在以前的老公司就用过，而且那家公司确实开发了一些相当实用的应用程序。不过，这并不能改变 Lizzie 上上家公司很糟糕的事实。

别告诉她是我这么说的，我们有她的加入真是太幸运了。

回到代码。既然它在一切正常时可以工作，并且在出现问题时能捕获异常，那么它的问题到底在哪里呢？答案不在于它现在运行得完美，而在于它为我们的未来留下了潜在的问题。

没有什么比那些对我们宝贵的调试时间产生如此负面影响的代码结构，更能为缺陷的滋生提供肥沃土壤了。

在将保护调试时间固化放在首要位置的情况下，是时候看看这个特定原则的另一个名称了。

## 单点原则。

需要注意的第一点是，这个特定名称是为那些使用点（句号）符号将对象与其字段分离的语言设计的，实际上，除了 PHP 和 Perl 之外，几乎所有的语言都是如此。

你懂这种事的。如果你只是对 Java 看过一眼，也会遇到下面这行代码：

```
System.out.println("Hello, World");
```

当然，在 PHP 中，我们使用箭头 (`->`) 来分离对象及其字段，但原理是一样的；如果你使用了超过一个点来访问属性或方法，那么极有可能你没有正确遵循“最少知识原则”（Principle of Least Knowledge）。

需要注意的第二点是，该准则/习语/原则的这个特定版本是目前所有名称中最不准确的。判断我们是在遵循还是违反了德墨特律（Law of Demeter），是一个稍微复杂的数点数过程。

尽管如此，我们甚至还没有考虑这为什么是一件坏事，所以让我们通过回顾那行违规的“代码行”直接进入正题吧。

## 不要和陌生人说话

```php
$user -> getAccount()
    ->getBalance()
    ->deductAmount($orderTotal);
```

在 PHP 术语中，那里直接就是三个“点”……

我们可以通过遵循这种“单点”方法来修复这段代码吗？

```php
$account = $user->getAccount();
$balance = $account->getBalance();
$balance->deductAmount($orderTotal);
```



答案是坚决不。

我们在这里所做的仅仅是将这三个麻烦“点”中的每一个移动到了它们各自的行上。核心问题仍然存在：这里包含了太多的知识。

它不仅意识到调用 `getAccount()` 方法会返回一个带有 `getBalance()` 方法的对象，还意识到 `getBalance()` 方法的返回值提供了 `deductAmount()` 方法。

这知识太太多了。

在德墨特律的语言中，这行代码是穿过中间对象来调用链末尾的 `deductAmount()` 方法。我们编写这段代码的方式，即使在将链拆解为三个独立的语句后，仍然表达了对该链一直到最终方法结构的内在认知。

我们在这里看到的是紧耦合的另一个实例，这是我们应该一直努力避免的。紧耦合通过增加维护的难度，降低了我们编写的应用程序代码的质量。对某部分紧耦合代码的更改需要我们检查并可能修改该紧耦合关系中的所有其他成员。

为了直观说明这一点，想象一种情况：几个月后，业务团队提出了一个新需求：不再要求用户预存资金，而是我们将为其中少数用户提供信贷额。

不要和陌生人说话

为了让事情变得更复杂，让我们想象一下预存资金的用户将享受订单折扣，而使用信贷的用户将需要支付小额额外费用。

对于业务来说，这是一个重大变化，但目前的情况，多亏于我们紧耦合的设计，这对代码库来说是一个巨大的变化。

当这个故事落在 Lizzie 头上时，显然她将在将在 `UserAccount` 类中工作，以处理信贷与预存账户的情况。

不幸的是，得亏于我们紧耦合的代码，她还要检查整个代码库，以确定应用程序的其他部分是否也受到了影响。其中，我们知道 `addOrderAction()` 方法必须修改，因为它目前显然无法兼顾信贷额度的概念。

如果公司提供按月订阅服务呢？这种想法并非没有可能，但如果答案是肯定的，那么可怜的 Lizzie 就要面临翻找 cron 脚本的前景了。在这种情况下，我们最好确保厨房里有足够的咖啡。

如果我们从一开始就意识到德墨特律，所有这些额外的工作可能就可以避免了。与其让我们的操作方法穿过多个对象来触发订单支付，我们的控制器代码可能像这样：

```php
class OrderController
{
    public function addOrderAction()
    {
        try {
            $user->payOrder($order);
        } catch (OrderPaymentException $e) {
            // 处理错误
        }
    }
}
```

## 不要和陌生人说话

关键代码行是这一行：

```php
$user->payOrder($order);
```

通过这一操作，我们消除了操作方法本不该拥有的所有额外知识。尽管我让你们想象这个方法是如何获取 `$user` 和 `$order` 实例的，但将 `$order` 实例传递给用户的 `$payForOrder()` 方法这一简单动作，在信贷账户时代和后信贷账户时代都同样适用。

换句话说，对订单支付过程内部机制的知识已经从不该存在的地方移除了。我们的操作方法不再对 `$payForOrder()` 调用另一端的 `Order` 实例发生了什么任何想法。

现在，它对过程的唯一知识就是如果抛出异常，它就必须处理，这正是它应该做的。

> 如果你之前遇到过德墨特律，你可能注意到，我们在这里处理的示例与 David Beck 一篇名为《报报童、钱包与德墨特律》的论文主题之间存在一些明显的相似之处。在文中他描述了支付报童的过程：不是让客户递交钱包，而是让报童请求付款，并允许客户安排账单如何支付。换句话说，报童完全不需要看到钱包，甚至不知道它是否存在。我强烈推荐阅读这篇论文。http://www.ccs.neu.edu/research/demeter/demeter-method/LawOfDemeter/pdf

但这是否意味着处理订单支付的逻辑现在必须移动到 `User` 类中？

完全不是。根据我们已经看到的代码，以及 Lizzie 必须处理的故事的性质，我们知道是 `UserAccount` 对象将处理订单支付。

我们在 `User` 类中添加的是代理方法，如下：

## 不要和陌生人说话

```php
class User
{
    public function payOrder(Chargeable $order)
    {
        try {
            $this->getAccount()->payOrder($order);
        } catch (InsufficientFundsException $e) {
            // 抛出 OrderPaymentException();
        }
    }
}
```

> 记得我提到过 User 实例是懒性加载的吗？如果是这样的话，通过 `getAccount()` 方法获取它就是实现这一点的合理方式。另一种方案是通过构造函数注入一个预先的 `UserAccount` 实例，在这种情况下我们可能会使用 `$this->account`。

> 为了单点原则，我们可以安全地排除任何对 `$this` 引用后面的箭头。我稍后会讨论这一点。

可以看到，只需向 `payForOrder()` 方法发送一个符合 `chargeable` 接口的实例即可支付订单。

事情开始变得有点混乱的地方在于当我们添加了过多的代理方法时。没多久，我们就会发现 `User` 模型的公共接口充斥了大量仅与我们对 `User` 究竟是什么的理解相关的方法。当这种做法过多时，我们的模型最终看起来就像是一个外观模式（Facade Pattern）的实现。

不过，我们想得太远了。如果我们不想走添加代理方法的这条路线，我们该如何在控制器的动作方法中解决这个问题呢？

一种可能性是跳过中间人，直接与 `UserAccount` 实例交互，得到如下所示的代码：

```
public function addOrderAction()
{
  try {
    $userAccount->payOrder($order);
  } catch (OrderException $e) {
    // handle exception
  }
}
```

如果你在这一章的前面读到这里，你可能会忍不住叹道：“啊！但这不就像是把钱包交给送报员吗？”答案是，谢天地，并不是。如果我们的账户方法表现得像送报员，它仍然成功地忽略了实际的支付过程，该过程仍然被很好地封装在 `payForOrder()` 方法之后。

我们实际上看到的是动作方法直接与一个即时协作者工作。诚然，我们的控制器更好的做法可能是将整个订单/支付过程交给一个服务，让该服务协调与模型之间的适当交互，但那是架构方面的问题，我们将在书的第五部分讨论。

# 不要和陌生人交谈

将代码与其即时协作者连接起来正是德梅特法则（Law of Demeter）希望我们所做的。让我们重新看看本章开头提到的那三个要点：

- 1. 每个单元对其他单元的了解应该是有限的：仅限于与当前单元“紧密”相关的单元。
- 2. 每个单元应该只与它的朋友交谈；不要与陌生人交谈。
- 3. 只与你的直接朋友交谈。

通过修改代码来跳过中间人（`User` 实例），我们将三个“朋友”靠得更近了：`Order` 实例、`UserAccount` 实例以及 `ViewController` 本。尽管如此，我们仍在促进系统内部参与者之间的松耦合；如何处理 `Chargeable` 项目的知识仍然稳固地留在它应该在的地方，而不是不该在的地方。

这让 Lizzie 在 `UserAccount` 对象内部开始大显身手了。只要她接收一个 `Chargeable` 对象，并且当该对象的值无法从用户账户扣除时抛出异常，那么实际的代码实现是什么样就并不重要。其他任何代码都不会因为知识实现方式的改变而损坏。

这就是我们所处的处境，这种处境促进了松耦合，并帮助我们把对潜在复杂操作的知识正确地封装到它们应该所在的地方。

德梅特法则帮助我们实现了这两种理想的结果。

# 总结

德梅特法则希望我们亲近朋友，并尽可能离敌人远点，在沿途中筑起屏障和界篱。紧耦合是其中一种敌人，虽然它确实在 100% 的情况下无法避免，但建立适当的边界可以让我们避免远程效应带来的痛苦公共时间损失。

在我们早期的错误示例中，我们的控制器代码穿过了 `$user` 实例和 `$userAccount` 实例来获取 `$balance` 实例的 `deductAmount()` 方法。希望现在应该清楚这如何导致问题的了。负责 `UserAccount` 或 `Balance` 类的开发者并不一定会控制器代码正在直接访问 `$balance` 实例的方法。

有了适当的屏障 `payForOrder(Chargeable $order);` 方法，控制器代码对订单支付结算方式的任何变化都变得不可感知，这正是我们想要的。

不过，我们仍然需要警惕的是代理方法的泛滥，这可能导致接口臃肿、混乱。

但通过应用德梅特法则来促进松耦合和封装，我们就已经稳赢了。

不要和陌生人交谈。除非他们提议帮你结账单。

# 讨论点

现在我们已经到达第三部分的末尾，是时候再次总结那些遗留问题了。在书的这一部分，我们的旅程已经带我们离开了草木丛生的平原，推入了 PHP 辉煌山脉中树木葱密的山坡。我们走了一条蜿蜒的小径，在粗壮的树干和健实的幼树之间不断向上，只有当头顶茂盛翠叶的树冠出现缝隙时，金色的阳光才驱散了转瞬即逝的阴影，将周围的环境沐浴在检查与理解的温暖光芒中，我们才停下来观察四周。

因为我们走的森林是软件工程世界中非常特殊的生物群，那里每一棵树都代表一个独立的设计模式、编程范式或软件原则。如果我们把每一个模式、范式或原则都列出来，可能需要一整片森林来制作索引卡。

那里有很多此类，有很多书专门为它们编写，尽管我倾向于推荐阅读两本核心书籍：《设计模式》（GoF）¹⁷ 和马丁·福勒的《企业应用架构》⁸，它们有时可能有点晦涩。

你明白，开发者喜欢新点子，那里有很多开发者一旦发现某个新模式，就会努力把它塞进他写的每一行代码中。始终记住，设计模式和软件原则是为了给问题提供解决方案。

¹⁷https://phpbrilliance.com/url/ta6
¹⁸https://phpbrilliance.com/url/x11

讨论点

要有效使用模式或原则，首先必须理解它。内化它的如何、为什么以及这些东西所解决问题的本质。之后，有必要识别出你何时拥有该问题。

# 松耦合与可测试性的艺术

在本书的这一部分中，我们处理了一个核心关注点，即使没有经常提及名称，即松耦合与紧耦合的概念。

紧耦合的代码是脆弱的代码，是容易损坏的代码，是对准时下班去酒吧的真实威胁。

这里是另一个采用备受诟誉的单例数据库模式的紧耦合代码示例：

```
class Database
{
    private $pdo;
    private static __instance;
    private function __construct($dsn, $user, $pass) {
        $this->pdo = new PDO($dsn, $user, $pass);
    }
    public static function getInstance() {
        if (is_null(self::$instance)) {
            $config = Config::getInstance()->getParams('db');
            self::$instance = new self($config);
        }
        return self::$instance;
    }
}
```

这是实现单例的旧方法，通过提供私有构造函数和静态实例访问器。现在不要误会我，单例仍然有

# 讨论要点

……位置并且它仍然是一个完全有效的模式。可以肯定的是，你永远不会希望为你执行的每一个查询都实例化一个新的数据库连接，因此对于此类事宜，采用单例模式（Singleton pattern）仍然是合适的。

然而，上述方法存在的问题是多方面的，其核心问题与其说在于代码本身，不如说在于这段代码如何鼓励在整个代码库的其他部分使用它。

无论是否有命名空间，数据库单例实例都是全局可用的，这导致代码看起来非常像下面：

```php
// 其他地方...
class OrderModel {
    private $db;
    public function __construct() {
        $this->db = Database::getInstance();
    }
}
```

当一个明知自己需要避免使用这种反模式、并且不通过控制器传递数据库连接的开发者，在代码中写了类似上面的操作时，结果就会变得有些混乱。我们最终留下的是一个硬编码依赖；一个 `OrderModel` 类与 `Database` 类紧密耦合，而 `Database` 类又依赖于 `Config` 类。换句话说，这全错了。

这是紧耦合代码的典型示例。我们的 `OrderModel` 对 `Database` 类有明确依赖，因为它被硬编码在 `__construct()` 方法体中。更糟糕的是，它完全无视了德梅节律（Law of Demeter）中“只与最邻的朋友交谈”的思想。然而，最糟糕的还在后面；在 `__construct()` 方法中获取数据库连接为我们带来了一个特殊的挑战。所有这些事情使得我们的 `OrderModel` 容易失败。怎么说？忽视上述代码中没有错误处理的事实会让它无法从失败的连接尝试中安全恢复，这种代码的紧耦合特性给开发团队实施了额外的责任，以确保现在和未来的更改不会产生不利影响。

开发团队避免对代码库的更改产生不利影响的最佳方法就是使用测试。大量的测试。软件测试可以通过多种不同的方式进行：功能测试、集成测试、回归测试和单元测试，共共四种。每种测试在不同阶段都涉及不同程度的劳动。单元测试在设置阶段需要的劳动最多；你编写代码，并为其编写相应的测试代码（如果你推崇测试驱动开发，则反之），但运行测试套件投入的精力很少。

在光谱的另一端，功能测试在代码创建阶段需要的精力很少，但在交付阶段的压力异常大，特别是当开发团队与测试（QA）协作工作时。参与敏捷方法和流程所鼓励的迭代构建周期，意味着我们希望大部分如果不是全部的测试都是自动化的。为每个冲刺（Sprint）投入一周时间进行测试，并在逐个故事（story）地交付代码的同时尽可能减少自己的痛苦，这对我们所有人都有益。这意味着需要适当的自动化测试。

那么哪些层次是正确的呢？幸运的是，这个问题已经解决了。迈克·科恩（Mike Cohn）在他优秀的著作《敏捷成功》（Succeeding with Agile）中提出了“测试金字塔”（Testing Pyramid）的概念，它完美地说明了我们如何将大部分精力集中在单元级，通过最宽的测试覆盖范围证明金字塔宽大的底部，并逐渐缩小每个测试层级的范围，直到到达功能测试顶端。

许多开发者讨厌单元测试，最常见的原因是正确地进行测试花费了太多精力。另一个答案是修复漏洞花费了太多精力，你别无选择只能这样做，代价是花费时间在开发新功能上，或者更糟，为此牺牲了其他时间！

采用单元测试制度，建立一套具有高代码覆盖率的有效测试套件将为你和你的团队节省未来无数修复漏洞的时间。这是一件非常好事。为了建立这些测试套件，你首先必须创建可测试的代码。为了清楚起见，让我们把那个 `OrderModel` 带回视线中。

```php
class OrderModel
{
    private $db;
    public function __construct()
    {
        $this->db = Database::getInstance();
    }
}
```



目前，这个糟糕的模型类是不可能进行单元测试的。为什么？首先，我们对 `Database` 类有硬编码依赖，就在代码里，由于对 `getInstance()` 的调用，使得在没有 `Database` 类存在的情况下几乎无法测试此类。我之所以说“几乎不可能”，是因为有一个名为 `Patchwork` 的巧妙工具允许你即时重写类定义，它还包含了静态定义的类方法。你应该将其视为测试遗留代码的逃生计划，而不是现在和未来编写不可测试代码的脱身条款！

其次，那个硬编码依赖被写在了构造函数中，这意味着你无法直接测试该方法，只有在调用之后效果才会变得显现（即创建了新的对象实例）。显然，我们需要一种不同的开发方法，因为带着一个未经测试且不可测试的 `OrderModel` “上线”是不可设想的。这正是本书很大一部分内容一直在讨论的主题：通过推崇松耦合来实现可测试性，从而促进出具有高结构质量的代码。

不要要求我们把业务逻辑封装在正确的地方；即逻辑易于测试的地方。德梅节律希望我们通过只与最邻的朋友交谈（协作）来解耦代码。在测试环境中，朋友可以很容易用模拟对象（mocks）和存根（stubs）替换。实例化恐惧（Instantiaphobia）希望我们把对象创建过程集中在非常独特的位置，要么是专用工厂，要么是依赖注入容器。为什么？因为随意创建对象会导致对所引用类的紧密耦合。

# 核心要点

根据应用程序内部事件发生的顺序（从初始请求到最终响应）来编写代码，是一个理所当然的想法。毕竟，这通常是散落在网络各处的在线教程所采用的方法。如果你在 Google 上搜索“如何用（在此插入你选择的框架）制作博客网站”，极有可能发现这些流程指南会要求你先设置路由器，然后是控制器，最后是视图模板。

然而，这种方法往往会导致“幽灵对象”（poltergeists）和“快递员”（couriers）的出现，这两者都倾向于在运行中拖着紧耦合的幽灵随形。

相反，如果我们采用反向思维的方法来解决问题，我们更有可能获得更简洁、更松耦合，从而对 Bug 更有韧性的代码。

让我们反向推演创建一个博客文章的过程，以此来说明这一点。

首先，我们需要一个显示确认信息和新创建的博客文章内容的视图。太棒了，这需要知道视图本身需要什么。让我们来编写视图。

为了知道视图需要什么数据，我们的模型需要返回一个 `BlogPost` 实例，哦，这个实例还需要被持久化到数据库中。太棒了，这意味着我们需要带有所需的数据库连接来设置 `BlogPost` 模型。让我们来编写模型，并注入数据库连接。

然后，嗯，某些东西需要根据用户提交的内容将数据设置在模型上——让我们来编写一个 `BlogPostService` 对象，它将接收一个与其协作的模型对象。好了，完成。

我们如何获取该服务的实例呢？这很可能是我们在应用程序特定代码与所选框架代码的边界处通常会采用的方法：通过路由组件来实现。

这种反向构建的方法使我们能够从一开始就正确处理依赖注入。它也让我们更容易避免那些“快递员式”的情况——即我们可能会为了将对象传递给模型或持久化层，而倾向于通过控制器或服务进行传递。

请务必在用户故事中按从开始到结束的顺序记录整个过程，但在实际编写代码时，请试着反向来来。如果你有这种倾向，就先写单元测试。

# 你的代码“不靠谱”吗？

我之前提到过这一点，但现在我们要将其单独列出一个子章节。在早期的“告知，不要询问”（Tell, Don't Ask）中，我们会触及一点：不要为了做出逻辑决策而从对象的状态中提取元素。我们需要花点时间来扩展一下这个观点。

`IF` 是一个极其危险的关键词。当然，你可能不相信我。毕竟，它是我们在学习编程语言时遇到的第一个关键词之一。但这并不会减轻初始陈述的危险性。

事实上，当我们在代码中使用任何种条件逻辑时，危险就存在了。

诸如 `if (...)`、`while (...)` 甚至 `foreach (...)` 这样的语句都会增加应用程序代码执行流程的复杂性。任何增加应用程序复杂性的因素都会为 Bug 提供肥沃的温床。而 Bug 意味着什么？对我们发布时间的维护是致命且毁灭性的打击！

把这个看作是一个稍微极端的例子。

```php
$uri = $_SERVER['REQUEST_URI'];

if (preg_match('^\/##', $uri, $matches)) {
    // 加载首页
} else if (preg_match('/\/blog\/([0-9]+)$', $uri, $matches)) {
    // 加载 ID 为 $matches[1] 的博客
} else if (preg_match('/\/contact$/', $uri, $matches)) {
    // 加载联系页面
}
```

这是可维护的吗？不，它离可维护性还有很远距离。然而，它说明了问题。当你使用条件逻辑来确定下一步执行哪条代码路径时，你实际上在为未来充斥 Bug 的场景埋下伏笔。

当你以这种方式继续路由过程时，你最终会得到大量的、难以管理的 `IF` 语句。在未来的某个时刻，某些事情会出错，即使它现在看起来运行良好。

处理这一特定问题的现代方法是构建你自己的路由器，或者更好的是，使用由他人构建并被成千上万开发者使用的路由包。目前两个比较流行的路由包是 Nikita Popov 的 `FastRoute`¹ 和 The League of Extraordinary Packages 的 `route`²，这两者都允许你以一种高度可维护的方式来设置路由。

避免复杂性是实现可维护性和提高代码可测试性的关键。尽可能将 `IF` 关键字留给验证，并使用策略（Strategy）、命令（Command）、装饰器（Decorator）甚至责任链（Chain of Responsibility）等模式来为代码库中提供分支逻辑。

¹https://github.com/nikic/FastRoute
²https://github.com/thephpleague/route

# 大脑检查

欢迎来到第三部分的最后一章。
这一部分我们将通过问自己：“我能对其中的每一个项做一次闪电演讲（lightning talk）吗？”来对本书这部分涵盖的内容进行自。
这是一个清单，也是突出进一步阅读区域的指南。

# 幽灵对象 (Poltergeist)

幽灵对象是一种反模式，用于描述一种短命的对象，它没有自己的状态，用于对其他对象或系统的其他部分执行操作。一个唯一目的是配置另一个对象的对象就是幽灵对象的典型范例。

# 外观模式 (Facade Pattern)

外观模式为更复杂的子系统提供了简化的接口。将外观与幽灵对象区分开的一个显著特征是：外观应该被提供访问其旨在交互的组件权限，而幽灵对象则是自己伸手去自取。

# 接口优于实现

这是一种实现松耦合的机制，通过关注协作者“做什么”，而不是协作者“是什么”。通过这种方式，调用者可以获得一个支持特定接口的协作者，从而保证了协作者能够做什么，而无需知道其具体类型。这允许我们在不破坏应用程序的情况下切换不同的实现。

# 组合优于继承

另一种实现松耦合的机制，通过将其封装到自己的离散对象中来实现代码复用。继承是将特定依赖硬编码到父类中，而组合则允许注入依赖（从而在运行时进行切换）。

# 状态模式 (State Pattern)

这是组合的一种特定实现，通过向对象中注入代表所需行为的对象，允许对象的状态（以及相应的行为）在运行时被修改。

# 装饰器模式 (Decorator Pattern)

这是另一种通过组合实现代码复用的方法，允许对目标对象进行包装，使得装饰器可以拦截目标对象的一个或多个方法，以提供不同但符合预期的结果。装饰器应该与被装饰的对象呈现相同的接口，以便与协作者的交互如预期进行。

# 策略模式 (Strategy Pattern)

策略模式与状态模式类似，它允许对象根据环境条件接收自定义逻辑或算法。状态模式代表可改变的内部关注的行为，而策略模式允许在处理协作者时提供可改变的外部行为。

# 快递员模式 (The Courier anti-pattern)

当一个对象接收到一个它本身并不使用的依赖时，快递员模式就会出现。相反，该依赖被传递给它是为了随后将其传递给对象的另一个协作者。这构成了一种形式的紧耦合，因为中间节点（或快递员）隐含地了解了最终接收者为了运行需要什么。如果这些需求发生了变化，那么快递员代码也随之需要修改，这增加了代码库的脆弱性。

# 迪米特律 (The Law of Demeter)

在促进松散耦合方面，这也许是最有效的原则之一。它也被称为“最少知识原则”，每当代码对另一个对象的内部结构产生感知时，就违反了该原则。所有对象应该只与其直接协作对象的公共接口感知。通过这种方式，当其他对象的内部实现发生变化但公共接口保持不变时，就可以避免程序崩溃。

# 测试金字塔 (The Testing Pyramid)

这是一个说明性的概念，鼓励我们建立一个宽大的单元测试基础，向上延伸到狭窄的功能和手动测试顶端，中间夹着其他类型的测试层；例如集成测试。任何具有宽大基础的东西通常比其底部窄的同类更稳定。然而，许多软件项目采取了相反的方法，优先测试用户界面，导致了所谓的“测试冰淇淋锥”（testing ice-cream cone）。冰淇淋锥通常是不稳定的，即使放在平整的表面也是如此。

# 转向 SOLID

> “我知道你们先生已经经历了很多，但当你们有时间的时候，我不想在这个冬天剩下的时间里都**绑在这张该死的沙发上**！” - Garry

# 介绍 SOLID 原则

占位章节 - 内容即将到来！

# 占位符 (Placeholders)

这是结束点吗？

完全不是，但一些读者建议我包含占位符章节（本质上是空章节），以便提供某种展示即将出现的内容的方式。

从实验性的来看，我确实这样做。

接下来的章节是空占位符，随着我完成每个发布版本，它们将逐步填充内容。

这是一个好主意吗？

你发现更倾向于看到后续还有什么吗？或者当你反复切换目录却发现空白页时，这些空章节会让你感到厌烦吗？

请让我知道你的想法：

Thunder

feedback@vanqard.com²²³

在此期间，你可以点击/触摸此处直接跳转到书末的内容

## 单一责任原则 (The Single Responsibility Principle)

这是一个空占位符章节。内容即将到来！

# 开闭原则 (The Open / Closed Principle)

这是一个空占位符章节。内容即将到来！

# 里可夫替换原则 (The Liskov Substitution Principle)

这是一个空占位符章节。内容即将到来！

# 接口隔离原则 (The Interface Segregation Principle)

这是一个空占位符章节。内容即将到来！

# 依赖倒置原则 (The Dependency Inversion Principle)

这是一个空占位符章节。内容即将到来！

# 讨论点 (Talking Points)

这是一个空占位符章节。内容即将到来！

# 大脑检查 (Brain Check)

欢迎第四部分的最后一章。

能够对每个 SOLID 原则进行闪电（lightning talk）特别具有挑战性，但绝对并非不可及。

# 应用软件架构 (Applying Software Architectures)

> “我在想酋岩号（El Capitan）什么时候才有机会用上他的泡枪。” 
Palmer

# 介绍架构 (Introducing Architectures)

这是一个空占位符章节。内容即将到来！

## 要 MVC 或不要 MVC (To MVC or not MVC)

这是一个空占位符章节。内容即将到来！

# 服务面向架构 (Service Oriented Architecture)

这是一个空占位符章节。内容即将到来！

# API 导向架构 (API Oriented Architecture)

这是一个空占位符章节。内容即将到来！

## 架构堡垒 (The Architectural Fortress)

这是一个空占位符章节。内容即将到来！

# 讨论点 (Talking Points)

这是一个空占位符章节。内容即将到来！

# 大脑检查 (Brain Check)

这是一个空占位符章节。内容即将到来。

# 不要恐慌！(DON’T PANIC!)

尽管我们正准备进入“附录”领域，但在未来几周内，书中还有大量正文内容发布。

由于 PHP7 具有高度的时效性，我已经建立了 PHP7 附录的开头。在这个阶段，我们已经有了一份商定的特性列表，预计将进入 2015 年 10 月的最终发布中。不仅如此，由于每日构建（nightly builds）已经可用，我们有机会在语言变化影响我们的日常编码之前，尝试并熟悉一些新功能。

# 附录 (Appendices)

# PHP7

应该记住，在编写时，PHP7 刚刚进入 GA（正式发布），这意味着我们很可能在不久的将来看到大量的错误报告和错误修复发布。尽管如此，此处包含的大部分内容是基于 RFC 并结合我使用 PHP7 每日构建的个人实验。

> 此附录可能处于剧烈变动的状态。随着新版本发布到我们的桌面上，我们可能有一点时间等待

在充分理解上述警告的范围内，让我们现在开始看看 PHP7 中引入的一些变化将如何影响我们在前几个部分已经涵盖的内容。

## 标量类型提示 (Scalar Hinting)

这可能是 PHP7 为语言带来的影响最大的变化之一，仅仅通过观察 RFC 在被提议、拒绝、重拟和重新提交期间该话题引发的激烈辩论程度，就能显而易见。

为什么会有如此激烈的辩论？分歧源于对 PHP 是否应该是弱类型语言的考量，如果不是，应该如何以对扰动最小的方式实现类型支持。

## 蓝蓝角 (In the blue corner)

保留弱类型的支持者认为，PHP 应该继续尊重它的历史根源，并像过去一直那样表现。这意味着它应该继续支持早已公认的预期，即向一个严格要求数值的函数发送一个看起来像数字的字符串。

```php
<?php
class Calculator
{
    function add($a, $b)
    {
        return $a + $b;
    }
}
$calc = new Calculator();
$first = "12"; // 一个字符串
$second = 4.5; // 一个浮点数
echo $calc->add($first, $second);
// 输出: 16.5
```

尽管提供的第一个参数是一个字符串变量，但 PHP 内部可以很轻松地处理到浮点的类型转换并执行加法。保留 PHP 的弱类型本质允许该语言遵循“最小惊奇原则”：它一直以来都是这样运行的，没有理由在我们向严格要求数值的函数传递类数字的字符串时，通过破坏他们的应用程序来让每个人都感到惊讶。

这种论点在使用 Composer 的应用背景下尤为相关。如果我们导入应用程序的某个包开始声明我们未曾准备好的方法参数类型，会发生什么？考虑到 $_GET 和 $_POST 数组中的值总是字符串，一个供应商发布其包的强类型更新，可能意味着我们不得不进行大量的重构才能让应用程序重新运行。

具体如何呢？

假设第一个示例中的 `calculator` 类位于我提供的包中，而你的应用程序依赖于该包。如果我选择强类型实现，它看起来可能会像这样。

```php
<?php
class Calculator {
    function addThe(float $a, float $b) {
        return $a + $b;
    }
}
```

这只是一个非常小但非常重要的变化。`addThe()` 方法的签名现在声明了它正如类型提示所暗示的需要接收两个 `float`（浮点数）。尽管实际代码更改非常小，但其影响是巨大的。现在要使用此包的新版本，意味着我们必须搜索整个代码库，找到调用此方法的每个地方，并在过程中进行相应的更改，以确保该方法只接收两个 `float` 类型的值。

```php
<?php
// 之前我们是这样使用的
$calc->addThe($first, $second);
// 我们现在需要像这样的代码
$calc->addThe((float) $first, (float) $second);
```



自然，这把一个相当沉重的负担直接落在了我们的肩上。如果该包提供者在这次更新中包含了一个重大的安全修复，我们别无选择只能走重构路线——要么满足类型表达出的新需求以利用安全修复，要么切换到另一个提供相似功能的替代包。

鉴于我们已经完全能够编写高质量的应用程序，我们真的需要通过对语言引入重大变化来如此地打乱局面吗？工具已经存在了，可以通过将输入强制转换为我们明确想要处理的特定类型来适应用户层实现中的缺陷。如果我们真的想对传入的变量类型非常挑剔，我们可以对这些类型进行验证，并在客户端代码出错时抛出错误和异常。

## PHP7

331

显然，反对者有非常有力的论据。在拳台的另一边，论点又是怎样的呢？

# 红角一方

能够对标量值（scalar values）进行类型提示的处是显而易见的，但在我们考虑这些之前，首先有一个特别相关的点需要说明。

我们可以对**所有内容**进行类型提示。

如果你把脑海回回到书的开头章节，你会记得我们在考虑抽象类作为定义新数据类型手段时所付出的努力。我们为什么要这样做？我们这样做是因为我们意识到语言的原生数据类型无法完全代表我们的需求。当然，它们并非为此设计的。通过提供自定义数据类型，我们让我们的应用程序代码（更重要的是编写代码的开发者）能够享受到这些事物预期工作方式的知识。

其中的关键部分是，抽象类尽可能地记录了从该数据类型派生的实例的预期行为。抽象类文档的一部分包括告知客户端代码（协作者）每个方法期望多少个参数以及它们应该是什么类型。除非这些参数的预期是标量值。

此外，我们重新审视了接口（interfaces）的作用，以及它们如何让我们开发者能够在实现它们的对象中对方法的可用性提供保证。与抽象类一样，我们能够非常简洁地表达这些接口中方法的要求。同样，预期为标量值的参数除外。

标量类型提示的提供完成了闭环。单这一点就对我们渴望展现 PHP 之光（PHP Brilliance）的开发者来说提供了巨大的价值。这是我们对抗 Bug 大军的另一个武器，这些 Bug 不断威胁要爬入我们的应用程序并消耗我们宝贵的时间。

展望未来，标量类型提示让我们能够“对所有事物进行类型提示”。对于输入参数，我们编写的每个方法都能声明它需要和期望的所有内容，而不仅仅是大多数内容。

# PHP7 332

在这方面，标量类型提示将消除我们代码中的又一个脆弱性元素。减少脆弱性自然意味着提高了生成应用程序的健性和安全性。

如果我们能像处理其他所有类型一样对字符串、整数、浮点和布尔进行类型提示，我们就不需要显式地对它们进行验证了。我们也不需要将输入参数转换为我们期望处理的类型，这种次优的方法会导致数据的细微且无声损坏。

```php
class Calculator
{
    public function addThe($a, $b)
    {
        $a = (int) $a;
        $b = (int) $b;
        return $a + $b;
    }
}

$calc = new Calculator();
echo $calc->addThe("3.14", 2);
// 输出：5，而不是预期的 5.14
```

这个 Bug 是我们造成的。嗯，好吧，我很乐意承担上述的所有责任。作为这个特定版本 `Calculator` 类的作者，我预期的是与整数值工作，这就是为什么我在相加之前将输入转换成了整数。尽管如此，类定义底部的客户端期望计算器实例只是……你懂的，把数字加在一起。这是一个完全合理的假设，因为方法签名中已经隐含了这一点。

当然，如果我的类中的代码没有通过强制转换为整数来静默地破坏 `addThe()` 方法接收的输入，那么它会更好。

无声的输入破坏在 PHP 世界中随处可见，导致了极其微妙的 Bug 产生，仅仅是因为我们的代码正试图将意外的值强制转换为内部逻辑工作所需的类型。标量类型提示

PHP7

允许我们避免这种破坏，产生更具表现力的方法签名，以及更明确的从一种类型到另一种类型的转换实例。

# 这是一场击杀！

在 RFC 方面经过反复争论后，标量提示得到了绝大多数人的赞同。这意味着我们可以开始考虑在实现中如何利用这种重大变化。

但是，这里有一个例外情况。总有例外。

首先是标量类型以及我们用于提示它们的关键词简要介绍。

| 标量数据类型 | 类型提示“关键词” |
|---|---|
| 字符串 | string |
| 整数 | int |
| 浮点数 | float |
| 布尔 | bool |

在此阶段值得注意的是，RFC 特别排除了别名，例如在整数值的情况下，我们必须使用 `int` 作为类型提示。同样，对于布尔值，我们需要使用 `bool` 而不是 `boolean`。

一个简单的示例代码应该让用法显而易见，让我们来看看。

> ²⁴https://wiki.php.net/rfc/scalar_type_hints_v5

# PHP7

```php
class ScalarTypeHints
{
    public function setInt(int $int) {}
    public function setFloat(float $float) {}
    public function setString(string $string) {}
    public function setBool(bool $bool) {}
}
```

使用标量类型提示（Scalar type hinting）情况就不同了。由于 PHP 在历史上是一门弱类型语言，它一直支持这样一个观点：特定变量的底层类型可以更改以适应代码中描述的情况。例如：

```
$myVar = "42"; // $myVar 定义为字符串
var_dump($myVar * 2);
// $myVar 类型内部已转换为整数以执行乘法
// 输出: int(84)
```

结果是，PHP似乎将继续支持变量类型从一种到另一种类型的内部转换。当我们再次查看 `add()` 方法时，实际发生的情况是：如果第一个参数不是浮点数，PHP 将尝试将其转换为浮点数。同样，如果第二个参数不是整数，它也会将其转换为整数。

在可以进行这些转换的地方，这种做法*至少不意味着*方法内部的逻辑将获得类型提示所指定的数据类型。然而，另一方面却导致了一个非常细微的数据损坏问题，我们应该特别关注并避免这种问题。

```
$calc = new Calculator();
var_dump($calc->addThe(3.5, "2.75"));
// 输出: float(5.5)
```

按理说，我们本期望结果是 6.25。但我们得到的并不是这个结果，而是 5.5 这个答案。

看起来我们的计算器类出问题了。原因在于我们的第二个参数 "2.75" 在输入时被静默转换成了整数。结果是我们方法的内部逻辑处理的是整数值 2，而不是预期的值 2.75。

只要类型转换是可能的，PHP 就不会报错。即使将浮点数和类浮点数字符串转换为整数会导致从我们代码开发者和错误修复人员的角度来看产生的数据损坏也是如此。

# PHP7 336

这代表了一个巨大的挑战。如果我们对支持 `ArrayAccess` 接口的参数进行类型提示，当我们未能提供该接口时，PHP 将报错。如果我们对标量值进行类型提示，PHP7 只有在无法在内部执行类型转换时才会报错。

鉴于我们完全有能力显式地将一个标量转换为另一个标量（例如 `$int = (int) "31.25";`），我认为当方法期望一种类型但接收到不同类型时，让 PHP 报错是更好的。

这可以实现吗？答案是肯定的，但在我看来这个解决方案相当笨拙。

我们可以通过在每个需要文件的顶部添加一条语句来告诉 PHP7 开启严格检查。该语句的格式如下：

```php
<?php
declare(strict_types=1);
```

此阶段需要注意的是，`declare()` 语句必须是每个需要严格类型检查文件的第一个指令。当在文件顶部进行声明时，我们的标量类型提示将按照我们预期的方式工作。也就是说，如果我们尝试将浮点数作为提示为整数的参数传递，PHP 将抛出错误。同样，当我们尝试在提示要求浮点数或整数时传递数字字符串时，也会得到错误。

> 为了增加复杂性，当开启严格检查时，你仍然可以向期望浮点数的方法传递整数。这是一个“特性”，因为整数可以轻松转换为浮点数而不会产生任何损失或损坏。整数 42 只需变为浮点数 42.0。

这才是需要的。与其让类型转换在后台静默发生，如果我们有一个字符串并且它需要是数值类型之一，我们将被迫在代码中显式地执行转换。这显著提高了我们在手动执行类型转换时所犯任何错误的可见性，并因此使我们更容易识别和修复这些错误。

# PHP7

还有一点必须注意：该声明仅适用于出现在同一文件中代码，或者通过 trait（特性的）消耗的代码。通过 `require` 或 `include` 指令引入的任何代码都不会受严格类型声明的影响，除非这些文件顶部也有相同的声明。

我在上面提到了 trait，我认为这些“小怪兽”值得进一步考虑。你可能会认为，在 trait 文件的顶部添加声明应该足够开启该 trait 内容的严格类型检查了。

我的什么意思是？

```php
<?php
declare(strict_types=1);
trait AddingTrait {
    public function add(float $a, int $b) {
        return $a+$b;
    }
}
```

尽管我告诉过你对于任何需要开启严格类型检查的代码，声明必须位于最顶端，但它对 trait 是无效的。无论这是刻意的还是被忽略的，这都是需要警惕的。我们可能会认为以下代码现在可以工作了。

```php
<?php
class Calculator {
    use AddingTrait;
}
```

遗憾的是，事实并非如此。简而言之，trait 无法为它自己的方法开启严格检查。相反，责任在于使用该 trait 的类。在我们的示例中，这意味着包含 `Calculator` 类的文件必须进行严格类型声明。trait 本身怎么做与之无关。

```php
<?php
declare(strict_types=1);
class Calculator {
    use AddingTrait;
}
```

所以，为了使用严格检查，你必须在定义类文件的顶部添加 `declare(strict_types=1);` 语句。

## 返回提示 (Return Hinting)

还有一点必须注意：该声明仅适用于出现在同一文件中代码，或者通过 trait 消耗的代码。通过 `require` 或 `include` 指令引入的任何代码都不会受到……除非这些文件顶部也有相同的声明。

返回类型提示正如你想象的：它是声明方法返回的数据类型。你可能会认为我正要关于接口、合约和保证，但实际上我不会那样做。我们稍后会谈到这些，但首先让我们看看实现。

```php
<?php
declare(strict_types=1);
class Calculator {
    public function addThe(float $sa, float $b): float {
        return $sa+$b;
    }
}
```

希望你能从上一个章节认出这个类。如果没有，你的大脑在想什么？我们几页前才刚刚讨论过这一点。我想，如果你是在一家由极其迷人的咖啡师经营的咖啡店阅读这些，是可以被原谅的。

好了集中注意力。我们再次看到了一个允许相加两个数字的简单对象。正如你所见，我们为 `$sa` 和 `$b` 声明了浮点类型。此外，我们现在通过在方法签名后附加冒号和类型来声明浮点类型。

这是我们今天在 PHP 代码中面临的局面。当一个方法返回了一个非预期类型的值时，由此产生的错误可能出现在代码库的任何地方。

这对于我们的保证、契约以及抽象类接口意味着什么？事实上，影响很大。我们即将考虑的关键因素是，PHP 7 中初始实现的返回类型提示（return type hinting）是**不变型（invariant）**的。这将直接影响到派生自使用了返回类型提示的抽象基类的子类中的返回类型提示。

我们稍后会详细讨论这一点，但简而言之，这意味着特殊子类实现中的方法无法应用与父类方法不同的返回类型提示。

这个表述需要一些代码来澄清这一点。如果我们回到很早时候的一个例子，即 `SportsCarFactory`，我们可以看到不变返回类型提示是如何影响我们的编码方式的。

```
abstract class CarFactory {
    /**
     * @return Car
     */
    public function getCar(): Car {
        // make a car
        return new Car();
    }
}
```

在这里，抽象父类 `CarFactory` 对 `getCar()` 方法标注了返回类型。具体来说，它声明返回类型为 `Car`。

现在，既然创建了一个类型为 `SportsFactory` 的特殊子类，我们可能会合理地认为，既然实际返回值将是 `SportsCar` 的实例，我们应该在方法声明中进行相应的类型提示。

## PHP7 341

```
class SportsCarFactory extends CarFactory
{
    public function getCar(): SportsCar
    {
        // make a sports car
        return new SportsCar();
    }
}
```

无论我们多想告诉调用此方法的客户端代码返回的是一个 `SportsCar` 实例，要做到这一点需要 PHP7 支持**协变型（covariant）**类型提示。

由于 PHP 7 采用的是不变特性，上面的代码将无法工作，解释器会通过错误明确告诉我们原因。

所以，让我们遵守不变性并修复我们的代码：

```
class SportsCarFactory extends CarFactory
{
    public function getCar(): Car
    {
        // make a sports car
        return new SportsCar();
    }
}
```

通过将返回类型更改为与父类中声明的完全相同（即 `Car`），问题解决了。这样做之后，我们现在满足了不变返回类型提示的要求。考虑到该类的接口声明返回的是 `Car` 但实际上返回的是 `SportsCar` 实例，我们可能开始对该类的接口声明感到有些别扭。

这种别扭感只有当我们孤立考虑 `SportsCar` 类时才会出现。只要我们记住实际上是父类在制定规则，就可以发现不变特性对我们非常有利。对于那些接受“抽象类为新数据类型提供蓝图”这一点的开发者来说，不变返回类型提示的应用让他们处于明显的优势地位。这样做在无意中有益地锁定了该数据类型的特征。如果每个子类在接口层面的行为都符合抽象父类的要求（这正是这种类型提示所支持的），那么我们的应用程序代码自然会保持类型安全。实现这一点的最终结果是减少未来修复 Bug 的时间，代价是现在需要更仔细地编码。记住，Bug 越少，去酒吧的时间越多！

对于许多滥用继承的开发者来说，这个特性很可能会成为他们的问题所在源。因此，我无法预见这一新语言特性会有广泛的采用。

对于那些采用返回类型提示的人，还有几个需要留意的辅助考虑因素。

与标量输入参数的提示不同，标量值的返回提示不需要在文件顶部使用 `declare(strict_types=1)`。输入参数标量类型提示与返回值标量类型提示之间这种明显的不一致性令人担忧。在任何情况下，我建议对标量值进行任何类型提示的开发者养成一种坚持的习惯，即始终在文件顶部包含 `declare()` 语句。

为什么？因为更安全的假设是，另一位开发者可能会从标量返回类型提示的存在推断出输入参数的标量类型提示已经“开启”。

我们是否应该把责任放在同事身上，让他们验证文件中是否包含了严格类型的声明，尽管我们的返回类型提示并不需要它？还是说，直接提供声明以防止任何不愉快的意外更好？

输入参数标量类型提示与返回值标量类型提示之间的行为差异已经足够混乱了。

接下来，我们应该看看对具体接口实现的影响。如果在抽象类上应用返回类型提示让我们能够扩展应用于子类中的规则，那么好消息是，在接口定义内部应用返回类型提示可以帮助我们在实现此类接口的相互无关的对象内部实现同样的严谨保证。

一个刻意的例子可以完美地说明这一点。

# PHP7

```php
declare(strict_types=1);
interface ReturnTypesInterface
{
    public function getFloat(): float;
    public function getString(): string;
    public function getArray(): array;
    public function getDatabaseAdapter(): PDO;
}
```

我们可以清楚地看到，在接口级别应用返回类型提示赋予了我们显著扩展我们所提供的保证范围的能力。任何实现此类接口的对象，尽管它们之间可能完全无关，都被要求遵守此类保证的返回类型。对于我们应用程序代码中的类型安全来说，这是一个极好的消息。

为了说明这种效果，让我们考虑以下代码：

```php
declare(strict_types=1);
interface FooGuarantee
{
    public function getFoo(): Foo;
}
```



在这里我们有一个接口声明，要求实现者提供 `getFoo()` 方法。那些实现者还必须确保他们的方法版本包含完全相同的返回类型。也就是说，实现的方法必须在方法声明中指定 `: Foo`。

由于我们现在要求提供返回类型提示，我们的方法实现现在被要求返回 `Foo` 对象的实例或扩展 `Foo` 的子类的实例。然而，你可能会注意到实际方法返回了 `Bar` 实例。只有当 `Bar` 是 `Foo` 的子类时，这才能工作。如果 `Bar` 在其继承层次中没有包含所需的 `Foo` 类作为父类之一，`PHP7` 将愉快地崩溃。避免致命错误（即使是可捕获的错误）是我们追求的目标。

当我们讨论接口话题时，我们需要考虑接口本身是否可以用于返回类型声明。换句话说，我们是否能够保证方法调用返回的值遵守其自身的保证。

快速看一眼示例就能清楚这个问题。

```php
interface Foo
{
    public function getArray(): array;
}
```

这里是我们的起点。一个名为 `Foo` 的接口，保证 `getArray()` 方法将返回一个数组。

```php
interface FooAble
{
    public function doFoo(): Foo;
}
```

在这里我们指定了 `FooAble` 接口的实现者必须提供 `doFoo()` 方法。到目前为止，这一切都符合预期。

然而，`doFoo()` 方法包含了 `: Foo` 的返回类型提示。在实践中，这意味着 `doFoo()` 方法的具体实现必须返回此后实现了 `Foo` 接口的对象。这本身对 PHP 代码来说具有重大意义。

结论是？返回类型提示是实现非常健壮、类型安全的应用代码迈出的非常积极的一步。点赞。

## 下期预告

在你的下一个精彩章节中...

书的这一部分将随着每次连续发布而变化，因此，这是我与读者你们之间的联系标准。我将保持此页面的更新，作为一种沟通自上次发布以来发生的事情以及下一次发布将包含的内容的形式。

新年快乐！希望 2016 年带你在所有的努力中获得幸福和成功。

这是 2016 年的第二次内容发布，正如你所看到的，我们已经达到了第三部分的结尾。虽然还需要进行一些润色工作，但令人兴奋的消息是，我们将在不久的将来开始进入第四部分。

我非常期待与你们分享我关于 SOLID 原则的观点。我深信掌握这套准则（即这五个核心原则的集合）是开发者大放异彩的关键。因此，它们是实现 PHP 卓越的关键，我等不及要开始与你们分享这些了。

你可能注意到，我终于将“更多时间”（The More Time）原则放在了书的最开头。如果你错过了，请现在去补上。

你们对实现这个项目提供的帮助和协助一如既往地令我感谢。你们有很多方法可以提供帮助。

首先是反馈。虽然我已经收到了你们几位非常好的建议，并对此表示感谢，但我还需要更多反馈。你觉得这些内容如何？太啰嗦了？还是不够啰嗦？是否漏掉了你可能认为应该在这里的话题？

如果你能花几分钟（或更长时间！）给我写封信，分享你的想法、印象，最重要的是批评和投诉，请尽管这样做。

下期预告。

反馈邮箱地址在这里：`feedback@vanquard.com`²⁵
或者，在你们最喜欢的社交媒体上推特或分享链接也确实有助于扩大反馈范围。如果这听起来有点像是在要求你为我的书做广告（确实是这样，不是吗？），只需给上面的邮箱地址发封信，我会回复你一个“免费副本”优惠码，这样 a) 你送书的行为让你看起来超级酷，b) 我能获得更多反馈，从而为所有人带来更高质量的产品。双赢！
一如既往，书籍的状态更新会发布在 Twitter 和 Facebook 上。以下是链接：
Twitter: `https://twitter.com/devbrilliance`²⁶
Facebook 用户看：`https://www.facebook.com/brilliancebook`²⁷
这两个平台可能是镜像关系，所以除非你真的想那样，否则不需要两个都关注。
感谢阅读！
下次见。
顺颂商祺，Thunder

²⁵`mailto:feedback@vanquard.com`
²⁶`https://twitter.com/devbrilliance`
²⁷`https://www.facebook.com/brilliancebook`
