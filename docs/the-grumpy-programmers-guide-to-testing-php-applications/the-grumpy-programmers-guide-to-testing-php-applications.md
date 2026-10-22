# 暴躁程序员 PHP 应用测试指南

















作者
Chris Hartjes

编辑
Kara Ferguson

版式
Oscar Merida

出版者
musketeers.me, LLC.
4627 University Dr
Fairfax, VA 22030 USA

240-348-5PHP (240-348-5747)
info@phparch.com
www.phparch.com











































# 索引 139

# 1. 引言

在这次发布之后，我被叫到项目经理办公室开会。讨论以他说，“好吧，我们不需要这个了，”结束，并把装着解雇信和遣散费支票的信封扔进了垃圾桶，随后他递给我一本书说，“我希望你周末看看这本书，周一早上告诉我你的想法。”那本书是 Ron Jeffries、Ann Anderson 和 Chet Hendrickson 合著的《Extreme Programming Installed》一本复印件。当时，我从大多伦多地区的外围通勤，乘坐通勤火车往返 90 分钟进城，回家要 2 小时（由于换乘）。我有充足的时间来阅读这本书。

你很少会遇到一个真正改变成年后生活的概念。在这种情况下，当我读到书中关于单元测试的部分时，我震惊又兴奋。原来我们可以用计算机本身来发现代码中的错误和 bug，而不是依赖 QA 人员或我们的客户？尽管我已经从事有偿编写计算机程序工作五年了，这对我来说仍然是革命性的。

当我回到工作岗位并再次与那位项目经理会面时，我们制定了计划开始解决我们在应用程序中面临的问题并建立某种测试。不久之后，我使用 SimpleTest 框架（基本上是 PHPUnit，但测试在浏览器中运行）编写了第一个单元测试，剩下的就是以测试为中心的职业生涯。

测试作为一个概念，很难向初学者程序员解释：“我们将编写代码来确保你的其他代码按预期工作。”这一切背后的假设是你已经懂得如何在你选择的语言中编写计算机程序！这使得向初学者或经验不足的程序员教授它变得非常困难。当你再加上 PHP 不强制任何特定结构的特点时，就形成了一个环境，只有真正有动力的人才会学习测试。

这里也存在类似“幸存者偏差”的情况。那些把测试作为实践纳入开发工作流程的人，都是在其中取得成功的人。我们很少听到那些尝试学习测试（无论是自学还是向他人学习）却没有成功的人的声音。总的来说，测试社区规模很小，但对自己的观点非常直言不讳。我可以理解人们犹豫不愿分享自己的失败。

这本书是我为希望变得更以测试为中心的发展者提供帮助的方式。通过学习基本技能（技术和非技术），你将能够使用几乎任何测试框架和几乎任何 PHP 应用程序编写测试。

我们将从了解测试到底是什么开始，因为我觉得很多人（包括经验丰富的测试人员）对测试的目标存在误解。之后，我们将看看 PHPUnit 如何工作，以便你了解更好的使用方法。掌握这些知识后，我们将使用测试驱动开发（TDD）构建一些代码，以说明测试如何驱动应用程序代码的设计。

我们大多数人都没有机会在新项目中使用 TDD。我将向你展示如何为现有应用程序编写测试，尤其是那些没有考虑到测试而编写的应用程序。工具是相同的；我们只是以不同的方式使用它们。

在编写了一些测试之后，我们将转向测试的人性化方面，提供策略来帮助你身边的人变得更以测试为中心。认识到测试更多关乎人而非工具本身，对我来说是一个重大的启示。

为了充分利用本书，你应该是一名对 PHP 有中级理解的开发者。当你对语言本身没有坚实掌握时，编写测试会很困难，而且你将编写的测试类型更多是需要理解和维护的 PHP 代码。

祝好运，我希望你觉得这里的材料有用。我很乐意在你阅读本书的过程中听到你的反馈。联系我的最佳方式是通过 Twitter，我在那里以 @grumpyprogrammer 的身份进行行为艺术。如果 Twitter（或社交媒体一般）不是你的菜，你也可以发邮件到 chartjes@grumpy-learning.com。我会阅读所有未被标记为垃圾邮件的邮件，并尽力尽快回复。




# 第3章 什么是测试？

我们可以用几种方式回答这个问题。当我最初学习编写测试时，我并没有真正深入思考它。我写了一些代码，运行测试运行器，然后看看结果是否符合预期。如果我们稍微退一步，我认为我们能得到一个更有用的答案。

从非常高的层面来看，测试是你编写的、用于确认你正试图测试的代码行为符合预期的代码。这是一个非常简单的概念。其他所有用来描述测试是什么的说法，都建立在这个基础之上。

如果你换个角度思考，每次写代码时都应该问自己一个问题：我如何证明这段代码的行为符合我的预期？通过专注于确保行为被测试，而不是盯着代码行数，我们最终的测试套件会更专注于“证明”这一任务，而不是为了追求一个往往很随意的“我们的代码有多少被测试覆盖？”的数字。

在我开始讨论你可能创建的不同层级的测试之前，我想先分享一个关于测试和TDD（测试驱动开发）有效性的故事。

2008年6月，一篇关于TDD有效性的论文发表了。论文讨论了IBM和微软如何通过给团队分配相同的编程任务来试验TDD，但要求其中一些团队使用TDD，而其他团队则完全不采用任何正式测试实践。

使用TDD的团队在开发时间上多花了15%到35%。这并不令人意外，因为测试是你为了证明其他代码行为正确而编写的代码。这很可能会花费更多时间，所以这个结果与我个人的经验相吻合。

与不使用TDD的团队相比，使用TDD的团队代码中缺陷数量减少了40%到90%。对我来说，这就是为应用程序编写测试所获得的巨大胜利。拥有能够主动防止缺陷发布到生产环境的东西，是一个巨大的胜利。

我们正处于软件开发的这样一个阶段：大家都在急于“赶快发布点什么”或“你必须发布一个最小可行产品。”请注意，“确保东西对你的用例正常工作”这句话在这些建议中完全缺失。把测试推给应用程序的用户，是一个似乎正在兴起的可怕趋势。通过学习编写测试所需的技能，你可以帮助扭转这一趋势。

我想分享我认为你最终会为应用程序创建的测试类型的发展过程。最终目标始终是一样的：一个可重复的流程，确保你的代码始终按照你预期的方式运行。这并不一定意味着不会出现任何缺陷，尽管使用测试极大地减少了用户可能遇到的缺陷。在这个列表中，我会提到一些你可能不熟悉的测试概念，但这些概念会在本书后面章节中讲到。不要担心，也不要感到畏惧！

## 先决条件

在你开始编写测试之前，你需要先具备一些其他条件，才能让这些测试值得去做。首先，你需要某种方法来回退应用程序代码的更改。希望你正在使用某种版本控制系统。Git目前是行业标准，你可以在网上找到大量关于如何使用Git以及与之配套的工具的信息。

接下来，你需要某种方法来应用和回滚你对数据存储工具所做的任何更改。不管它是关系数据库、键值存储还是文档数据库——如果你无法回滚对数据或用于组织数据的模式所做的更改，你将不断遇到无法回退的情况。

有一些PHP工具可以帮助你进行数据库迁移（通常指你对数据源所做的更改），而且许多流行的对象关系映射器（ORM）都带有管理它们的工具。

我怎么强调都不为过：在尝试引入测试之前，你必须有回滚更改的流程。

## 手动测试

如果你还没有任何测试，你首先应该编写的是供某人手动遵循的检查清单。这些测试应当让某人实际使用你的应用程序并执行一个或多个任务，以确保应用程序的功能符合预期。我通常建议人们从那些必须100%按预期运行的核心功能的检查清单开始。

如果这些测试中有任何一项失败，你应该回滚你所做的更改，并将应用程序恢复到之前的状态。然后，再次运行你的检查清单，确保测试仍然通过。一旦你确认缺陷存在，就该找人修复它，重新应用更改，并再次运行检查清单。如果缺陷仍然存在，再次回滚，并持续重复这个过程，直到应用程序通过你的检查清单测试。

## 使用真实依赖的半自动化测试

手动测试的下一步是开始使用PHP测试框架（我使用PHPUnit）编写测试来验证代码的行为，并使用真实依赖，而不是创建替代品（通常称为测试替身）。我们会在本书后面讨论测试替身，但我们继续往下看。

这是你在学习使用工具创建“测试即代码”时面临的最大障碍。术语不清晰，工具看起来很吓人，你不知道从哪里开始。在另一章中，我会介绍从零开始创建测试，但此时，请将这些测试视为产生“通过”或“失败”响应的黑盒。

这些测试最终看起来与应用程序中的实际代码非常相似。实际上，你现有的代码是你可以用来编写使用测试框架的测试的第一个模板！从将应用程序中的代码复制粘贴到测试中，然后添加一个断言（判断条件是否为真的语句）开始，是测试套件的第一个构建块。

那么为什么我把这一步称为半自动化？PHPUnit（以及其他PHP测试框架）可以从命令行运行。如果你已经有了一些测试，有人可以从版本控制中获取包含更改的代码，然后手动从命令行运行测试。最后这一步仍然需要人工参与。

## 使用测试替身的半自动化测试

在教别人如何编写测试时，我鼓励他们使用依赖的“真实”版本。然而，有些时候你需要用一个可以控制其所有方面的版本，来替代真实的依赖（比如数据库或API调用的结果）。我会介绍测试替身，所以不必担心它们的细节。

在这个阶段，我们重新审视已经编写的测试，并决定其中哪些依赖需要转换为测试替身。根据需要修改测试，然后通过CLI（命令行界面）运行它们。

## 自动化测试

测试的最终阶段是可以通过鼓励自动化的工具运行的测试。这些工具通常被称为构建服务器或持续集成服务器。不管你怎么称呼它们，它们的工作都是为你执行自动化任务。以下是一组包含构建服务器的典型操作：

- 你将更改提交到版本控制系统
- 版本控制系统向你的构建服务器发送信号
- 构建服务器接收信号并启动其自动化任务
- 它从版本控制中获取一份包含你的更改的代码副本
- 它执行任何必要的工作，为你的代码运行创建环境
- 它运行你的测试





- 它会报告测试是通过还是失败

进入最后这一阶段的好处之一是，你利用了计算机非常擅长的事情：一遍又一遍地做你让它们做的事情，通常还毫无怨言。所以，如果我能让另一台计算机对我所做的事情作出反应并替我运行测试，我就可以专注于解决问题，而不是去记忆一串很有可能不小心搞乱的命令。

## 最后的思考

测试的目的是让你有信心：任何进入代码的缺陷都会在应用发布到生产环境之前被检测出来。这种信心也让你能够重构或重写代码，因为你知道，如果你不小心破坏了之前能正常工作的东西，你会在用户发现之前就知道。

# 第 4 章 PHPUnit 的工作原理

## 高层概览

虽然 PHPUnit 不是我使用的第一个测试框架（这个荣誉属于 SimpleTest），但它是我最常使用的框架。市面上还有很多其他测试代码的工具，但我总是回到 PHPUnit，因为它方法简单，而且其他人创建了大量插件让它更加有用。

PHPUnit 是一组工具的集合，包含一个测试框架和一些命令行实用程序，允许你运行用 PHP 编写的测试。它最初由 Sebastian Bergmann 开发，如今已经拥有众多贡献者，并且仍在积极开发中。

PHPUnit 的工具采用所谓的 xUnit 架构。xUnit 有许多约定，引导你通过使用断言来以特定方式构建测试。断言（PHP 的内置特性）是用于断言特定条件为真或假的语句，具体取决于你所创建测试场景的目标。

维基百科上关于 xUnit 的文章有一个很好的总结，但这里是我们需要关注的几个部分：

- 测试运行器
- 测试用例
- 测试套件

在我们讨论这些之前，需要先安装 PHPUnit。

## 我们如何安装 PHPUnit？

PHPUnit 官网是任何与 PHPUnit 相关内容的最佳真相来源。在安装之前，请务必查看网站上的任何要求。在我写这本书的时候，PHPUnit 当前版本是 8.4。假设你满足它的最低要求，有两种方式可以安装 PHPUnit。

### 通过 PHP Archive（PHAR）安装

PHPUnit 的 PHAR 版本是一个二进制文件，你可以下载并安装到路径中的某个位置。要使用它，你还必须为 PHP 安装并启用 phar 扩展。PHPUnit 建议下载 PHAR 版本并在本地为你的项目提供它，而不是全局安装。

PHPUnit 还建议不要在 production 环境中安装 PHPUnit。带有 CLI（命令行界面）组件的工具可能会通过其他库中的漏洞被利用，而且一个坚决的攻击者有机会从测试运行的输出中了解到某些信息的概率并非为零。

我不是安全专家，但为什么要给人们机会来捣乱你的应用呢？

### 通过 Composer 安装

Composer 是 PHP 社区用于安装 PHP 相关包及其依赖的工具。强烈建议使用 Composer 将 PHPUnit 仅作为开发时依赖来安装。同样，我们希望避免在生产环境中安装任何与 PHPUnit 相关的东西。

假设你已经安装了 Composer，你可以通过 shell 执行以下 CLI 命令将 PHPUnit 添加到你的项目中。这会安装任何与当前依赖兼容的 8.4 及以上版本的 PHPUnit。

```
composer require --dev phpunit/phpunit ^8.4
```

安装好 PHPUnit 之后，我们可以看看如何执行你将要编写的测试用例。

## PHPUnit 测试运行器

测试运行器是一个 CLI 工具，用于执行你的测试用例并报告这些测试的结果。要使用 PHPUnit，你需要熟悉你所选操作系统上的 CLI 用法。

测试运行器有许多你应该了解的参数。和许多强大的工具一样，它有各种各样的选项；你会发现你只会使用其中一小部分。

最基本的是，你从 shell 中使用 `phpunit` 命令（这要求你要么指定 phpunit 的完整路径，要么它就在你的 shell 执行路径中）。然后它会从当前目录（默认）或你指定的路径开始递归搜索带有 `.php` 扩展名的文件。

如果这些文件包含一个继承自 PHPUnit 基础测试用例类之一的对象，PHPUnit 就会尝试执行它识别为测试的任何类方法。默认情况下，它假定任何以 `test` 开头的方法都应该是测试用例，并尝试执行其中的代码。你也可以使用带有注解的 DocBlocks 来指示某个类方法应该是测试。本书后面会有一些这样的示例。

测试运行器会执行这些测试，并继续尝试执行它认为是测试的任何内容，直到找不到更多为止。

下面是对运行器工作方式的一个小演示。首先，你需要创建最简单的测试用例。别担心；稍后你会了解测试用例的基础知识。我们现在只需要一个占位符。安装好 PHPUnit 后，创建以下文件并将其命名为 `BasicTestCase.php`。

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function testCase()
    {
        $this->assertTrue(false);
    }
}
```

接下来，使用 CLI 测试运行器。你应该会得到与以下输出非常相似的结果：

```
> phpunit BasicTestCase.php
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

F                                      1 / 1
(100%)

Time: 91 ms, Memory: 12.00 MB

There was 1 failure:

1) BasicTestCase::testCase
Failed asserting that false is true.

/Users/chartjes/grumpy-guide/test/basic_test_case.php:9

FAILURES!
Tests: 1, Assertions: 1, Failures: 1.
```

如你所见，测试运行器告诉我们：

- 测试的状态（在这里 F 表示失败）
- 花费了多长时间
- 消耗了多少内存
- 概述了具体的失败原因，并贴心地包含了行号
- 包含多少个测试和多少个断言

现在创建一个通过的测试用例，这样你就可以看到区别：

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function testCase()
    {
        $this->assertTrue(true);
    }
}
```

然后，使用测试运行器运行这个测试。

```
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

.                                   1 / 1
(100%)

Time: 97 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)
```

测试运行器现在显示的信息更少了，但会告知你一个测试中的一个断言通过了。如果你再加一个断言会怎么样？

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function testCase()
    {
        $this->assertTrue(true);
        $this->assertFalse(false);
    }
}
```

PHPUnit 默认的测试运行器输出会提供足够的细节，让你能够弄清楚哪些测试失败，也可以作为一种健全性检查，确保你编写的测试和断言数量是正确的。PHPUnit 为你提供了许多改变显示输出的选项。同样，我将在本书后面深入介绍这些内容。

## PHPUnit 测试用例

我们已经看到了如何使用测试运行器处理一些非常简单（且一次性）的测试用例；现在，是时候更仔细地看看我们如何在 PHPUnit 中构建测试用例了。

在最上层，你有一个文件，其中包含一个继承自某个基础测试类的类。还记得你的第一个基础测试用例示例吗？

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function testCase()
    {
        $this->assertTrue(false);
    }
}
```

要创建测试用例，你需要创建需要被识别为测试的类方法。有两种方法可以做到这一点。要么像你的示例中那样在测试方法前面加上 `test` 这个词，要么为测试方法创建一个文档块并添加 `@test` 注解，以表明下面的方法是测试用例。就像这样：

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function firstTestCase()
    {
        $this->assertTrue(false);
    }
}
```


## PHPUnit 测试用例

```php
<?php

declare(strict_types=1);

class BasicTestCase extends PHPUnit\Framework\TestCase
{
    public function firstTestCase()
    {
        $this->assertTrue(False);
    }
}
```

测试运行器告诉你...

```
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

W 1 / 1 (100%)

Time: 109 ms, Memory: 12.00 MB

There was 1 warning:

1) Warning
No tests found in class "BasicTestCase".

WARNINGS!
Tests: 1, Assertions: 0, Warnings: 1.
```

...它没有找到任何测试。如果你曾经为 PHPUnit 为什么找不到我们的测试而困惑不解，首先要查看的就是你的测试方法名称以及是否使用了注解。

我已经介绍了 PHPUnit 工作原理的基础知识。在下一章，我将向你展示一种我喜欢使用的测试设计模式，用来组织我的测试以提供清晰度并让我专注于正在做的事情。

# 第 5 章：测试替身

## 什么是测试替身？

测试替身是一个概念，在讨论测试的人之间引发了最多的争论。它们是一个你必须理解的概念才能真正对它们发表意见，但我们都知道这从未阻止人们争论。

Wikipedia 有一个直击要点的定义：

> “在自动化单元测试中，可能有必要使用看起来和行为像其发布预期对应物的对象或过程，但实际上是简化版本，可降低复杂性并促进测试。测试替身是用于这些对象或过程的通用（元）术语。”

测试替身是我们可以用来自表示给定测试场景所需依赖项的工具。在 PHP 世界中，它们通常被称为 mocks，但我想让你养成使用正确词语的习惯。你很快就会明白为什么。

在高层次上，当由于某种原因我不使用真实的东西时，我会使用一个替身来表示测试所需的某些依赖项。不使用“真实”依赖项可能有很多原因。最常见的原因是“它与数据库通信”或“它与远程 API 通信”。

在继续之前，我想明确一点，使用测试替身没有正确或错误的方法。一些编程社区主张对所有依赖项使用替身。一些主张永远不要使用替身。其他使用可以在运行时修改对象和函数的语言的编程社区（通常称为“猴子补丁”）使用该技术代替替身。

在本章中，我想向你展示 PHP 程序员可用的不同类型的测试替身，并让你自己做出决定。我的做法是尽可能使用真实依赖项，除非有显著开销。对我来说，通常的罪魁祸首是使用数据库的依赖项或框架中使用的“请求”对象。

在本章中，我将使用测试替身框架 Prophecy[1]，它自 PHPUnit 4.5 版本以来就可用。我也使用过 Mockery[2]，也很喜欢它的语法。没有“正确”的选择——你甚至可以使用 PHPUnit 内置的测试替身工具。选择一个你喜欢的并坚持使用；之后需要维护测试的人会感谢你的坚持一致。

在这些示例中，我将使用在生产中用于帮助跟踪模拟棒球联赛交易的应用程序的代码。

- [1] Prophecy: https://github.com/phpspec/prophecy
- [2] Mockery: https://github.com/mockery/mockery

## 假对象

假对象是你可能需要的第一个测试替身。以 Wikipedia 为指南：

> “...在需要测试方法参数但实际上不需要使用该参数时使用。”

在实际使用中，当你测试的代码需要一个依赖项，但该依赖项在测试期间永远不会被使用时，你会想要使用一个假对象。随着 PHP 越来越多地使用类型提示和返回类型，假对象的用途有限，因为创建一个没有类型的依赖项很可能会导致 PHP 报错。如果你使用的是类型未被使用的旧代码库，你可以通过使用 PHP 内置的 stdClass 对象来创建一个假对象。

所以假设你正在编写一个测试，需要使用这段特定的代码：

```php
class Roster
{
    public $_db;
    public $pdo;
    public $previous_season;
    public $current_season;

    /**
     * Constructor for class
     *
     * @param Aura\SqlQuery\QueryFactory $db
     */
    public function __construct($db)
    {
        $this->_db = $db;
        $this->pdo = new PDO(
            'pgsql:host=localhost;dbname=user=;password=' );
    }

    // Other code snipped out
}
```

但你的测试不需要对它做任何事情。你可以创建一个没有类型的假对象来满足需要“一个 RosterModel 对象”的条件。

```php
// Create a dummy of our database and pass it to our Roster model
$db = new stdClass();
$rm = new Roster($db);
```

## 测试桩

在我们类型化的 PHP 代码世界中，假对象将被升级为测试桩。再次以 Wikipedia 为指南，我们得到以下定义：

> “用于为被测试代码提供‘间接输入’。”

这是更简洁的说法，即一个与我们的依赖项具有相同类签名的对象，但不期望在测试期间调用该对象的任何方法。

所以，使用你正在尝试测试的相同代码，但现在你对 $db 参数应该是什么进行了类型提示，因此你需要将其创建为测试桩。这次你使用 Prophecy 来实现。

```php
// Create a stub of the QueryFactory object the constructor needs
$db = $this->prophesize(QueryFactory::class);
$db->reveal();
$rm = new Roster($db);
```

用更清晰的语言来说，这两行代码的作用是：

- 创建一个与 QueryFactory 具有相同类签名的测试替身对象（因此它是正确的类型）
- 激活该替身
- 创建一个 Roster 对象，该对象接受我们的测试替身作为构造函数参数

## 模拟对象和测试间谍

在本节中，我将结合两种类型的测试替身，因为它们都将在此测试场景中使用。

首先，我们有模拟对象，它用于通过先在被测试代码执行前定义期望来验证被测试代码的“间接输出”。

模拟是你在使用测试替身时在测试中最常用的测试替身。模拟是我们最终在 arrange 步骤中产生大量代码的地方。

其次，我们有测试间谍，用于通过在之后断言期望（而非在被测试代码执行前定义期望）来验证被测试代码的“间接输出”。它有助于记录有关创建的间接对象的相关信息。

当你期望模拟上的某个方法将被调用，但不需要担心发生的任何副作用（即相关代码采取的动作）时，就会使用间谍。

在此示例中，你正在为生成我们“交易日志”中条目的某些代码编写测试。这是我多次破坏过的代码，因为我最初没有为其编写测试。经过一些重构，以下是你将要测试的代码：

```php
<?php
use Roster;

class Transaction
{
    protected $rosterModel;

    public function __construct(Roster $rosterModel)
    {
        $this->rosterModel = $rosterModel;
    }

    public function generateTradeLogEntry($data, $tradePartner): string
    {
        $tradeDate = date('m/y');
        $tradedPlayers = [];

        foreach ($data as $playerInfo) {
            [$tmp, $playerId] = explode('_', $playerInfo);
            $playerInfo = $this->rosterModel->getById($playerId);
            $comment = "Trade {$tradePartner} {$tradeDate}";
            if ($playerInfo['ibl_team'] !== $tradePartner) {
                $tradedPlayers[] = trim($playerInfo['display_name']);
                $this->rosterModel
                    ->updatePlayerTeam($tradePartner, $playerId, $comment);
                $this->rosterModel->makeInactive($playerId);
            }
        }

        return 'Trades ' . implode(', ', $tradedPlayers) . ' to ' . $tradePartner;
    }
}
```

所以第一步是识别依赖项。你有：

- 一个我们无法覆盖的日期（也许以后重构以避免奇怪的边缘情况）
- 一个调用 getById() 的 Roster 对象
- 一个调用 updatePlayerTeam() 的 Roster 对象
- 一个调用 makeInactive() 的 Roster 对象

你的测试场景是什么？首先，你构建一个包含该场景的测试骨架。



# 5. 测试替身

```php
<?php
declare(strict_types=1);
use Aura\SqlQuery\QueryFactory;

require __DIR__ . '/../models/rosters.php';
require __DIR__ . '/../models/transactions.php';

class TransactionsTests extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function it_generates_proper_transaction_info_for_a_trade(): void
    {
        /**
         * Given I have an array that contains players
         * When I submit a list of players
         * And I submit a transaction description
         * Then I should get a one-line transaction being generated
         */

        // Assert
        $this->assertTrue(false);
    }
}
```

是时候创建测试所需的数据以及 Roster 对象的模拟，然后运行你的测试了。记住在每次更改后都要这样做，以帮助你隔离可能遇到的问题！

```php
// Arrange
$expected = 'Trades Moe, Larry, Curly to TEST';
$tradePartner = 'TEST';

// Data contains compound ID's of <trade partner 1>_<player_id>
$data = ['team1_1', 'team1_2', 'team1_3'];

$rm = $this->prophesize(Roster::class);
$tm = new Transaction($rm->reveal());
```

测试失败了（正如预期的那样！）

```
TypeError : Return value of Double\Roster\P1::getById() must be of the type array, null returned
```

现在回到你的模拟上实现预期的调用和返回值。首先是 getById() 调用：

```php
$rm->getById(1)
    ->willReturn(['ibl_team' => 'TEST', 'display_name' => 'Moe']);
$rm->getById(2)
    ->willReturn(['ibl_team' => 'TEST', 'display_name' => 'Larry']);
$rm->getById(3)
    ->willReturn(['ibl_team' => 'TEST', 'display_name' => 'Curly']);
```

Prophecy 使用一种用于模拟的 API，你可以指定期望被调用的方法，然后指定该特定调用将返回的内容。Prophecy 允许你模拟多个调用，以便你可以获得所需的精确控制级别。

测试运行失败...

```
Prophecy\Exception\Call\UnexpectedCallException : Unexpected method call on Double\Roster\P1:
  - updatePlayerTeam(
      "TESTMORE",
      "1",
      "Trade TESTMORE 01/01"
    )
expected calls were:
  - getById(
      exact(1)
    )
  - getById(
      exact(2)
    )
  - getById(
      exact(3)
    )
```

...因为你尚未实现 updatePlayerTeam() 测试间谍。

接下来，我们必须为 updatePlayerTeam() 的调用创建期望。这里存在一个潜在问题。updatePlayerTeam() 方法依赖于以其期望的方式格式化的日期作为参数传递，但我们无法为测试目的覆盖它。如果测试恰好在日期从一天滚动到另一天时运行，这可能导致边缘情况。“This isn’t a big deal, Chris,” I can hear you saying. 我更喜欢代码没有这种奇怪的边缘情况。因此，我要求你重构 Transaction 模型，使其具有 tradeDate 参数，我们在构造函数中设置它，但在测试中可以覆盖。

```php

class Transaction
{
    protected $rosterModel;
    public $transactionDate;

    public function __construct(Roster $rosterModel)
    {
        $this->rosterModel = $rosterModel;
        $this->transactionDate = date('m/y');
    }

    public function generateTradeLogEntry($data, $tradePartner): string
    {
        $tradedPlayers = [];

        foreach ($data as $playerInfo) {
            [$tmp, $playerId] = explode('_', $playerInfo);
            $playerInfo = $this->rosterModel->getById($playerId);
            $comment = "Trade {$tradePartner} {$this->transactionDate}";
            if ($playerInfo['ibl_team'] !== $tradePartner) {
                $tradedPlayers[] = trim($playerInfo['display_name']);
                $this->rosterModel
                    ->updatePlayerTeam($tradePartner, $playerId, $comment);
                $this->rosterModel
                    ->makeInactive($playerId);
            }
        }

        return 'Trades ' . implode(', ', $tradedPlayers) . ' to ' . $tradePartner;
    }
}
```

然后，你将交易日期设置为测试目的所需的值：

```php
$tm = new Transaction($rm->reveal());
$tm->transactionDate = '01/01';
```

## 模拟对象和测试间谍

接下来，你创建测试间谍，指定你期望发生的特定调用：

```php
// Create our updatePlayerTeam test spies
$rm->updatePlayerTeam($tradePartner, 1, $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam($tradePartner, 2, $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam($tradePartner, 3, $tradeComment)->shouldBeCalled();
```

那些偷看 Prophecy 文档的人会注意到，有方法可以在不指定参数及其顺序的情况下创建这些间谍。我本可以这样做间谍：

```php
// Create our updatePlayerTeam test spies
$rm->updatePlayerTeam(
    \Prophecy\Argument::any(),
    \Prophecy\Argument::any(),
    \Prophecy\Argument::any()
)->shouldBeCalled(3);
```

这相当于 “I expect updatePlayerTeam() to be called, with any values as three arguments, three times.” 我更喜欢我的测试尽可能具体，因为它降低了测试用例以我未预期的方式失败的可能性。

测试失败…

```
Prophecy\Exception\Call\UnexpectedCallException : Unexpected method call on Double\Roster\P1:
  - makeInactive(
      "1"
    )
expected calls were:
  - getById(
      exact(1)
    )
  - getById(
      exact(2)
    )
  - getById(
      exact(3)
    )
  - updatePlayerTeam(
      exact("TESTMORE"),
      exact(1),
      exact("Trade TESTMORE 01/01")
    )
```

# 5. 测试替身

```php
- updatePlayerTeam(
    exact("TESTMORE"),
    exact(2),
    exact("Trade TESTMORE 01/01")
  )
- updatePlayerTeam(
    exact("TESTMORE"),
    exact(3),
    exact("Trade TESTMORE 01/01")
  )
```
```

...因为你还有一组测试间谍需要实现。你可以按照为 updatePlayerTeam() 所做的相同模式为 makeInactive() 调用实现。

```php
$rm->makeInactive(1)->shouldBeCalled();
$rm->makeInactive(2)->shouldBeCalled();
$rm->makeInactive(3)->shouldBeCalled();
```

现在你有一个通过的测试！

```
OK (1 test, 7 assertions)
```

再做一次重构，避免在依赖项中硬编码值，以便更改在同一位置发生（在本例中为玩家 ID），以下是完成的测试。

```php
<?php

declare(strict_types=1);

require __DIR__ . '/../models/rosters.php';
require __DIR__ . '/../models/transactions.php';

class TransactionsTests extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function it_generates_proper_transaction_info_for_a_trade(): void
    {
        /**
         * Given I have an array that contains players
         * When I submit a list of players
         * And I submit a transaction description
         * Then I should get a one-line transaction being generated
         */
        // Arrange
```

```php
$expected = 'Trades Moe, Larry, Curly to TESTMORE';
$tradePartner = 'TESTMORE';
$tradeComment = 'Trade TESTMORE 01/01';

// Data contains compound ID's of <trade partner 1>_<player_id>
$data = ['team1_1', 'team1_2', 'team1_3'];
$rm = $this->prophesize(Roster::class);
$playerIds = [1, 2, 3];

// Mock our getById() calls
$rm->getById($playerIds[0])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name' => 'Moe']);
$rm->getById($playerIds[1])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name'=> 'Larry']);
$rm->getById($playerIds[2])->willReturn(
    ['tbl_team' => 'TEST',
    'display_name'=> 'Curly']);

// Create our updatePlayerTeam test spies
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[0],
    $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[1],
    $tradeComment)->shouldBeCalled();
$rm->updatePlayerTeam(
    $tradePartner,
    $playerIds[2],
    $tradeComment)->shouldBeCalled();

$rm->makeInactive($playerIds[0])->shouldBeCalled();
$rm->makeInactive($playerIds[1])->shouldBeCalled();
$rm->makeInactive($playerIds[2])->shouldBeCalled();

$tm = new Transaction($rm->reveal());
$tm->transactionDate = '01/01';

// Act
$response = $tm->generateTradeLogEntry(
    $data, $tradePartner);
```




# 5. 测试替身

```php
// Assert
$this->assertEquals($expected, $response);
}
}
```

## 伪造对象

伪造对象是测试中一种经常未被充分利用的工具。你可以不使用测试框架工具创建的模拟（mock），而是创建自己的对象，让它完成你期望从依赖中获得的行为。以我们刚才编写的测试为例，如果我决定使用伪造对象而不是 Prophecy 所提供的功能，那会是什么样子呢？

有几种方法可以处理这个问题。你可以在测试之外创建一个独立对象，扩展我们正在为其创建替身的方法。可能看起来像这样：

```php
<?php
declare(strict_types=1);

class FakeRosterModel
{
    public function getById($id): array
    {
        $responses = [
            0 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
            1 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
            2 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
        ];

        return $responses[$id];
    }

    public function updatePlayerTeam(
        $iblTeam, $playerId, $comments = ""): bool
    {
        return true;
    }

    public function makeInactive($player_id): bool
    {
        return true;
    }
}
```

最大的问题是 Transaction 对象在构造函数中期望一个类型化的 Roster 对象。没有简单的方法解决这个问题。我可以让这个对象继承 Roster 并传入一个 QueryFactory，但不对它做任何处理。如果我真的想对 Roster 对象使用伪造对象而不是 Prophecy，这似乎是阻力最小的路径。所以我会这么做。这个伪造对象现在看起来像这样：

```php
<?php
declare(strict_types=1);

require_once __DIR__ . '/../models/rosters.php';

class FakeRosterModel extends Roster
{
    public function __construct($db)
    {
        $this->db = $db;
    }

    public function getById($id): array
    {
        $responses = [
            1 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
            2 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
            3 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
        ];

        return $responses[$id];
    }

    public function updatePlayerTeam(
        $iblTeam, $playerId, $comments = ''): bool
    {
        return true;
    }

    public function makeInactive($player_id): bool
    {
        return true;
    }
}
```

我使用这个伪造对象的测试如下：

```php
/**
 * @test
 */
public function it_generates_proper_transaction_info_for_a_trade_using_fakes(): void
{
    /**
     * Given I have an array that contains players
     * When I submit a list of players
     * And I submit a transaction description
     * Then I should get a one-line transaction being generated
     */

    // Arrange
    $expected = 'Trades Moe, Larry, Curly to TESTMORE';
    $tradePartner = 'TESTMORE';

    // Data contains compound ID's of <trade partner 1>_<player_id>
    $data = ['team1_1', 'team1_2', 'team1_3'];
    $db = new \Aura\SqlQuery\QueryFactory('sqlite');

    $rm = new class($db) extends Roster {
        public function __construct(\Aura\SqlQuery\QueryFactory $db)
        {
            $this->db = $db;
        }
        public function getById($id): array
        {
            $responses = [
                1 => ['ibl_team' => 'TEST', 'display_name' => 'Moe'],
                2 => ['ibl_team' => 'TEST', 'display_name' => 'Larry'],
                3 => ['ibl_team' => 'TEST', 'display_name' => 'Curly'],
            ];
            return $responses[$id];
        }
        public function updatePlayerTeam($iblTeam, $playerId, $comments = ''): bool
        {
            return true;
        }
        public function makeInactive($player_id): bool
        {
            return true;
        }
    };

    $tm = new Transaction($rm);
    $tm->transactionDate = '01/01';

    // Act
    $response = $tm->generateTradeLogEntry($data, $tradePartner);

    // Assert
    $this->assertEquals($expected, $response);
}
```

无论你决定走哪条路，都最好知道：你可以为那些使用测试替身工具复制起来可能非常麻烦的东西创建替身。想想那些会发送电子邮件的功能，而在测试中你完全不想发送任何电子邮件。你可以创建一个使用完全相同的方法但从不发送邮件的伪造对象。

对于伪造对象，我的偏好是在测试用例中使用匿名类，除非你百分之百确定你创建的伪造对象可以被其他测试重用。记住，关于代码重用和尽量避免重复的规则同样适用于你的测试！

## 结语

测试的核心在于你控制所有依赖状态的场景。有时你可以使用“真实”依赖，其他时候则需要创建替身。根据你的需要，有多种替身可供选择：

- 哑对象（Dummies）：如果你没有使用类型提示的代码，并且需要一个在测试中不会调用任何方法的依赖
- 测试桩（Test Stubs）：如果你需要一个哑对象，但你的代码有类型提示
- 间谍对象（Spies）：如果你需要一个桩，其中某些方法会被调用，但你不需要关心该方法是否执行了任何操作
- 模拟对象（Mocks）：如果你需要一个依赖，其中特定方法会被调用，并且这些方法需要返回某些内容或执行测试所需的操作

测试替身绝对是测试从业者争论最多的话题——其次才是每个测试中应该有多少个断言。本章应该能让你有信心判断何时适合使用测试替身，以及该选择哪一种。

# 第 6 章：测试驱动开发示例

在理想的软件开发世界中，你会使用测试驱动开发（TDD）为应用程序编写所有代码，逐个测试地实现功能并决定 API 和接口。我使用 TDD 的方式遵循以下工作流程：

- 创建一个失败的空白测试
- 将我的测试场景写成伪代码
- 将伪代码转换为 PHPUnit 测试
- 运行测试
- 如果失败，继续编写代码，直到我正在测试的行为通过

多年来的经验告诉我，很多程序员都能从 TDD 所强加的结构和纪律中获益。我喜欢每次只关注一个测试的方式，这能让我的思绪不会游离或想得太远。当然，我总是从高层思考我正在做什么，但我非常努力地实现最简单的解决方案来让测试通过，因为我知道我可以用测试来验证在重构代码时不会破坏任何东西。

在这个例子中，我将解决以下问题：

> *编写一些代码，将任意阿拉伯数字转换为其对应的罗马数字，最大支持到 100。*

这是一个很好的问题，因为它有已知的解决方案（更容易编写测试），并且要求你熟练掌握几种常见的编程技术和结构。

## 工具

我在 2016 年末的 MacBook Pro 笔记本电脑上运行 macOS 10.14.6 来编写这些示例。我使用 PhpStorm（启用了 Vim 绑定，因为我是唯一真正的编辑器的支持者）编写 PHP 代码。我使用通过 Homebrew 安装的 PHP 7.3.6，并按照 PHPUnit 官网的说明安装了 PHAR 版本的 PHPUnit。

我使用的具体工具并不重要！你不必为了编写测试而模仿我的做法。只需确保你安装了稳定版本的 PHP，并且可以使用 PHPUnit 即可。

## 入门

我创建了一个空目录来存放代码。我的代码将放在 src 目录中，测试放在 tests 目录中。由于 PHP 和 PHPUnit 的灵活性，只要路径处理正确，你可以按照自己的意愿组织这些文件。

首先，让我们讨论如何解决这个问题。罗马数字由一组符号组成的字符串构成，这些符号共同表示正的阿拉伯整数值。你从左到右读取结果。那么，我们需要关注的基本符号有哪些？

- I -> 1
- V -> 5
- X -> 10




- L -> 50
- C -> 100

有些数字以不同的方式表示，因此我们还需要考虑这些情况：

- IV -> 4
- IX -> 9

那么，让我们创建一个空测试来验证：当我们传入 1 时，返回的是 I。

```
<?php
declare(strict_types=1);

class NumeralConverterTest extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function converts1ToRomanNumeral(): void
    {
        $this->assertTrue(false);
    }
}
```

这是能够在 PHP 或 PHPUnit 不抱怨配置错误的情况下运行的最简测试类。

我喜欢在测试方法的文档块中使用 @test 注解，而不是在每个测试方法前都加上 test 前缀。这样我可以使用更接近英文描述的方式命名测试方法。

如果我运行这个测试，它会失败：

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:11

Time: 188 ms, Memory: 12.00 MB
```

# 6. 测试驱动开发示例

## 第一个测试

第一个测试总是最难的，因为我们要为之后的所有代码搭建舞台。我确实会花一些时间进行原型设计或思考我想让接口和参数长什么样。在这个例子中，我从一开始就很清楚我希望它们是什么样。我会编写第一个测试用例：

```
public function converts1ToRomanNumeral() : void
{
    // Arrange
    $nc = new NumeralConverter();
    $input = 1;
    $output = 'I';

    // Act
    $result = $nc->arabicToRoman($input);

    // Assert
    $this->assertEquals($output, $result);
}
```

在深入细节之前，我想谈谈一个多年前有人教给我的测试设计模式，我经常使用它来保持测试用例的组织性。它被称为 Arrange-Act-Assert 模式。

## 安排

这个部分是我创建测试场景所需依赖的地方。在这个例子中，我创建了一个 NumeralConverter 对象，以及传给方法的输入和期望输出。在更高级的测试用例中，我需要创建的测试替身也放在安排部分。在大多数测试用例中，安排步骤包含的代码最多。

## 操作

这是我们使用被测代码生成输出，然后验证输出是否符合预期的地方。在我们的例子中，我们执行 arabicToRoman() 方法，传入所选输入并将输出存储在一个变量中。

这部分代码可能很多，也可能只有一行，就像我们的例子一样。它完全取决于测试场景。需要注意的一点是，确保该部分的操作与使用被测代码的应用代码一致。你在测试中对代码的使用方式偏离它在生产环境中的使用方式越远，你就越可能得到测试通过但应用程序并不按预期工作的结果。

## 断言

测试的最后一部分是我们进行所有断言或其他验证语句的地方，用来确认代码的行为符合我们的预期。有些人遵循“每个测试一个断言”的规则，而另一些人遵循“需要多少断言就用多少断言”的做法。没有正确答案，但一个没有某种断言的测试用例实际上没有测试任何东西。在我们的例子中，我们验证预期输出与 arabicToRoman() 方法返回的结果一致。

回到我们的示例；测试失败是因为我还没有创建 NumeralConverter 对象。

```
Error : Class 'NumeralConverter' not found
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:11
```

让我为这个对象创建一个空壳。

```
<?php
declare(strict_types=1);

class NumeralConverter
{
}
```

然后，我更新测试，添加一行加载这个对象的代码：

```
require __DIR__ . '/../src/NumeralConverter.php';
```

最后，我再次运行测试，它失败了，因为我要测试的方法还不存在。

```
Error : Call to undefined method NumeralConverter::arabicToRoman()
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:16
```

是的，这正是我进行测试工作的方式。我缓慢而稳定地推进，确保不遗漏任何东西。我们都有自己的习惯和喜欢使用的编程技巧；刻意而为能最大限度地降低我跳过步骤或犯下很容易避免的错误的风险。

现在，我编写刚好足够的代码来满足我们测试的行为。

# 6. 测试驱动开发示例

```
1. public function arabicToRoman($value) : string
2. {
3.     $result = '';
4.
5.     if ($value === 1) {
6.         $result .= 'I';
7.     }
8.
9.     return $result;
10. }
```

测试通过了。

OK (1 test, 1 assertion)

## 下一个测试

当然，我的解决方案非常简单，并且做了一些显然会改变的假设。我没有从一开始就尝试构建最优解决方案，而是决定想清楚我想要做什么。对于下一个测试，验证我们正确处理 2 和 3 的转换（我决定把它们放在一组），我将引入数据提供器（data provider）的概念。

数据提供器是一个向测试方法传入数据集的方法。在实现上，它是一个返回数组的数组的方法。我首先创建数据提供器方法。命名约定并不重要——尽量起一个描述性强、能让以后阅读测试代码的人理解其含义的名字。

```
public function dataSetsForConversion() : array
{
    return [
        [2, 'II'],
        [3, 'III']
    ];
}
```

然后，我创建一个使用该数据提供器的失败测试方法。

```
/**
 * @dataProvider dataSetsForConversion
 * @test
 */
public function converts2and3ToRomanNumeral($input, $expected)
{
    $this->assertTrue(false);
}
```

要告诉 PHPUnit 某个测试用例使用哪个数据提供器，你需要为测试方法提供一个 DocBlock（如果你还没有使用的话），然后在其中添加 @dataProvider 注解。注意大小写！然后，你的测试方法需要接受与传入数据值数量相同的参数。

对于这个测试，我决定提供我要测试的输入以及期望的结果。

现在我来验证测试会失败。

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:34

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:34
```

不，我没有重复复制粘贴结果。使用这个数据提供器的测试方法会对每一组数据执行一次。

第一步完成后，我开始编写代码，让第二个测试用例通过。

```
```php
public function arabicToRoman($value) : string
{
    $currentValue = $value;
    $result = '';

    while ($currentValue > 0) {
        if ($currentValue % 1 === 0) {
            $result .= 'I';
            $currentValue--;
        }
    }

    return $result;
}
```
```

测试通过了。

## 构建更多测试用例

我为验证 2 和 3 能正确转换而写的实现让我觉得应该继续以类似方式扩展代码来处理其他情况。我会添加一个测试用例来验证 4、5 和 9 被正确处理。这些情况代表了非标准行为。

首先，失败的测试。

```
```php
/**
 * @dataProvider exceptionDataSets
 * @test
 */
public function convertsSingleDigitExceptions($input, $expected)
{
    $this->assertTrue(false);
}
```
```

它如预期那样失败了。

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53
```

这里有三个失败，因为我使用了三组数据。

然后，我修改代码以正确处理这种新行为。

```
```php
1. public function arabicToRoman($value) : string
2. {
3.     $currentValue = $value;
4.     $result = '';
5. 
6.     while ($currentValue > 0) {
7.         switch ($currentValue) {
8.             case $currentValue % 9 === 0:
9.                 $result .= 'IX';
10.                $currentValue -= 9;
11.                break;
```


## 重构测试

等等！发生了什么？啊，我忘了添加代码来正确处理这些值。让我现在做。

```
1. case $currentValue % 100 === 0:
2. $result .= 'C';
3. $currentValue -= 100;
4. break;
5. case $currentValue % 50 === 0:
6. $result .= 'L';
7. $currentValue -= 50;
8. break;
9. case $currentValue % 10 === 0:
10. $result .= 'X';
11. $currentValue -= 10;
12. break;
```

现在测试通过了。

```
OK (9 tests, 9 assertions)
```

现在，我去罗马数字的维基百科页面，并在数据集中添加一些值，将它们重构为按数字顺序排列：

```
1. return [
2. [1, 'I'],
3. [2, 'II'],
4. [3, 'III'],
5. [4, 'IV'],
6. [5, 'V'],
7. [9, 'IX'],
8. [10, 'X'],
9. [14, 'XIV'],
10. [15, 'XV'],
11. [29, 'XXIV'],
12. [40, 'XL'],
13. [44, 'XLIV'],
14. [49, 'XXXIX'],
15. [50, 'L'],
16. [57, 'LVII'],
17. [63, 'LXIII'],
18. [78, 'LXXVIII'],
19. [82, 'LXXXII'],
20. [91, 'XCI'],
21. [100, 'C']
22. ];
```

# 6. 示例驱动的测试开发

我运行测试。

```
Failed asserting that two strings are equal.
Expected :'XIV'
Actual  :'IIIVIVIV'

Failed asserting that two strings are equal.
Expected :'XV'
Actual  :'VX'

Failed asserting that two strings are equal.
Expected :'XXIV'
Actual  :'IIIVVXX'

Failed asserting that two strings are equal.
Expected :'XL'
Actual  :'XXXX'

Failed asserting that two strings are equal.
Expected :'XLIV'
Actual  :'IVXXXX'

Failed asserting that two strings are equal.
Expected :'XXXXIX'
Actual  :'IIVIVXXXX'

Failed asserting that two strings are equal.
Expected :'LVII'
Actual  :'IIIVIVIVXXXX'

Failed asserting that two strings are equal.
Expected :'LXIII'
Actual  :'IXIXIXIXIXIXIX'

Failed asserting that two strings are equal.
Expected :'LXXVII'
Actual  :'IIIVIXIXIXIXIXIXIXIX'

Failed asserting that two strings are equal.
Expected :'LXXXII'
Actual  :'IIXIXIXIXIXIXIXIXIX'

Failed asserting that two strings are equal.
Expected :'XCI'
Actual  :'IXXXXL'

FAILURES!
Tests: 20, Assertions: 20, Failures: 11.
```

呃。又来了！看，我忘了正确处理其中一些异常值，而且我的数据集中也有错误。我回去检查错误信息和数据集并修复它们。

我在实现中犯了很多错误（记住，我实际上是在不作弊、不查看 Stack Overflow 或其他充满可复制粘贴答案的网站的情况下做的）。

这也说明了当你被迫在幕后重构代码时，有测试是多么有用。是时候重新思考我的做法了！

好吧，现在我的数据提供者中有正确的值，并且我添加了一个以确保 6 能被正确处理。

```
```php
return [
    [1, 'I'],
    [2, 'II'],
    [3, 'III'],
    [4, 'IV'],
    [5, 'V'],
    [9, 'IX'],
    [10, 'X'],
    [14, 'XIV'],
    [15, 'XV'],
    [29, 'XXIX'],
    [36, 'XXXVI'],
    [40, 'XL'],
    [44, 'XLIV'],
    [49, 'XLIX'],
    [50, 'L'],
    [57, 'LVII'],
    [63, 'LXIII'],
    [78, 'LXXVIII'],
    [82, 'LXXXII'],
    [91, 'XCI'],
    [100, 'C']
]
```
```

这是执行转换代码的新实现：

# 6. 示例驱动的测试开发

```
1. while ($currentValue > 0) {
2.     switch ($currentValue) {
3.         case $currentValue - 100 >= 0:
4.             $result .= 'C';
5.             $currentValue -= 100;
6.             break;
7.         case $currentValue - 90 >= 0:
8.             $result .= 'XC';
9.             $currentValue -= 90;
10.            break;
11.        case $currentValue - 50 >= 0:
12.            $result .= 'L';
13.            $currentValue -= 50;
14.            break;
15.        case $currentValue - 40 >= 0:
16.            $result .= 'XL';
17.            $currentValue -= 40;
18.            break;
19.        case $currentValue - 10 >= 0:
20.            $result .= 'X';
21.            $currentValue -= 10;
22.            break;
23.        case $currentValue - 9 >= 0:
24.            $result .= 'IX';
25.            $currentValue -= 9;
26.            break;
27.        case $currentValue - 5 >= 0:
28.            $result .= 'V';
29.            $currentValue -= 5;
30.            break;
31.        case $currentValue - 4 >= 0:
32.            $result .= 'IV';
33.            $currentValue -= 4;
34.            break;
35.        case $currentValue - 1 >= 0:
36.            $result .= 'I';
37.            $currentValue--;
38.            break;
39.     }
}
```

现在所有测试都通过了！

```
OK (21 tests, 21 assertions)
```

# 6. 示例驱动的测试开发

这个测试通过了。

> OK (1 test, 2 assertions)

我添加的下一个测试确保我们不接受大于 100 的任何值。这是可以稍后删除的东西，但原始需求（不要屈服于范围蔓延！）是只处理到 100 的情况。

我再次从一个失败的测试开始。

```
```php
/**
 * @test
 */
public function onlyAccepts100orLess()
{
    $this->assertTrue(false);
}
```
```

我编写一个测试，期望特定的异常和异常消息。

```
```php
public function onlyAccepts100orLess()
{
    $this->expectException(RuntimeException::class);
    $this->expectExceptionMessage('This method converts positive integers less than or equal to 100');
    $nc = new NumeralConverter();
    $nc->arabicToRoman(101);
}
```
```

验证该测试是否失败。

> Failed asserting that exception of type "RuntimeException" is thrown.

编写实现此预期行为的代码。

```
```php
if ($value > 100) {
    throw new RuntimeException('This method converts positive integers less than or equal to 100');
}
```
```

这个测试通过了。

> OK (1 test, 2 assertions)

整个测试套件通过了。

> OK (23 tests, 25 assertions)

## 最后的想法

TDD 确实迫使你以与你习惯不同的方式做事。它更关注代码的更低层次，确保在已编写的代码按预期行为时，不要继续编写其他代码。我认为对此的一个很好的类比是把它想象成用乐高积木搭建代码。一块一块地将其拼合在一起，希望最终结果是你所期望的。

# 第7章

# 示例的测试后开发

## 有什么区别？

上一章我向你展示了使用测试驱动开发的示例，说明了 TDD 在很大程度上是一种设计模式，其副作用是拥有证明你编写的代码按预期行为的测试。当你已经有一些代码在运行，并且它正在提供业务价值或以其他方式解决问题时，你需要以不同的方式来处理对其进行测试的过程。

# 7. 示例的测试后开发

在这些场景中，多年来我发现自己一直在问同样的三个问题。

- 预期的行为是什么？
- 我将如何测试该行为？
- 为了测试这段代码，我需要做出哪些改变？

在已有工作代码后编写测试的最大挑战是，为了使其“可测试”而需要做出的更改可能具有挑战性。很可能需要改变某些东西。对“已经在运行”的东西进行更改的恐惧是为现有代码编写测试的真正障碍。

因为代码通常是在没有考虑其独立可测试性的情况下编写的，我发现很难提供超出通用建议的内容。我确实认为如何做到这一点的示例非常有帮助。幸运的是，我有一个例子在脑海中。

## 预期的行为是什么？

很多年前，我编写了一些基于网络的工具来帮助我所在的桌面棒球联赛的管理。我们需要一些东西来管理发生的各种交易：交易、球员签约和阵容变动。该代码最初于 2005 年编写，我很遗憾地说，我没有为它编写任何测试。我需要它尽快完成，所以我拼凑了一个原型，界面非常糟糕。原型变成了生产版本。多年来它经历了一些修订（用于交易的拖放界面），但大部分代码仍然保持不变。

应用程序中给我带来很多问题的部分之一是显示球员“未上榜”状态的代码。联赛有关于在他们在我们使用的游戏中没有代表他们的卡片的赛季中保留球队球员的规则。我们最近更新了一些这些规则，所以我必须添加代码，以确保每当我们显示球员的详细信息时，如果适用，我们会显示他们的“未上榜状态”。

每个球员在 Postgres 数据库中的表中有一行。有一个字段表示球员未上榜的“赛季”。这是一个两位整数——例如 19 代表 2019 年。显示逻辑应该是这样的：

给定我是球员并且本赛季我有未上榜状态或上赛季我有未上榜状态当我的详细信息显示时我应该看到我的名字并且我应该看到我的未上榜状态



# 7. 以示例为导向的测试后开发

看起来一个不错的测试是创建一个场景，我们从数据库中检索一条记录，其中包含一名球员，其未上卡状态设置为当前赛季。然后，我应该检查返回的详细信息是否符合预期。以下是测试的大纲，写成好像一切都已正常工作。我稍后再回来弄清楚依赖关系。

```php
<?php
require __DIR__ . '/../models/rosters.php';

class RostersTests extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function it_displays_uncarded_players_correctly()
    {
        // Arrange
        require __DIR__ . '/../db_config.php';
        $rm = new Roster($db);
        $expected = 'TST McTesterton [UC19]';

        // Act
        $response = $rm->getById(1);

        // Assert
        $this->assertEquals($expected, $response['display_name']);
    }
}
```

这个测试失败了，因为数据库中没有 ID 为 1 且与预期球员姓名匹配的球员。我需要创建一个数据库连接的双对象，使其返回我们期望获取的信息。在弄清楚测试的过程中，我们有两个选择。

我可以走使用真实依赖进行此测试的路线，也可以为我需要的一切创建双对象。查看代码本身时，我需要以下依赖：

- 数据库对象
- 需要返回的‘select’对象
- select 对象上需要保持流畅的五个不同方法
- 带有返回语句的 prepare 方法的 PDO 对象
- 带有两种不同方法的 PDO 语句

## 我该如何测试这个？

为此创建双对象工作量很大。测试的 Arrange 部分会非常庞大。如果我不想做任何这些，也许我可以为此测试创建一个内存数据库？这样我就可以插入所需的记录，然后在测试结束时它就会消失。我不确定是否想创建所有这些测试双对象。我会查看 PDO 和我选择的另一个 SQL 库（Aura.sql）的文档，看看是否可以在内存中或使用 SQLite 实现。存储 Aura 对象和 PDO 对象的属性设置为 public 可见性，因此在我创建 Roster 对象后可以覆盖它们。

这就是测试现在看起来像的样子——注意我只是在更改创建某些依赖的方式，而不是测试本身。

```php
public function it_displays_uncarded_players_correctly()
{
    // Arrange
    $db = new QueryFactory('sqlite');
    $pdo = new PDO('sqlite::memory:');
    $commands = [
        'CREATE TABLE IF NOT EXISTS rosters (
        id INTEGER PRIMARY KEY,
        tig_name TEXT,
        tbl_team TEXT,
        comments TEXT,
        status INTEGER,
        item_type INTEGER,
        uncarded INTEGER DEFAULT 0,
        retro_id TEXT)',
        "INSERT INTO rosters(tig_name, tbl_team, comments, status, item_type,
        uncarded, retro_id)
        VALUES('TST McTesterton', 'TST', 'Test player', 1, 1, 19, 'retroid')"
    ];
    foreach ($commands as $command) {
        $pdo->exec($command);
    }
    $rm = new Roster($db);
    $rm->pdo = $pdo;
    $rm->current_season = 19;
    $rm->previous_season = 18;
    $expected = 'TST McTesterton [UC19]';

    // Act
    $response = $rm->getById(1);

    // Assert
    $this->assertEquals($expected, $response['display_name']);
}
```

```php
12. $pdo = new PDO('pgsql:host=localhost;dbname=ibl_stats;user=;password=');
13. $sth = $pdo->prepare($insert->getStatement());
14. return $sth->execute($insert->getBindValues());
15. }
```

那么，处理创建日志条目的代码呢？我四处查找并在处理交易的代码中找到了一个示例：

```php
1. // Now add entries into the transactions table
2. $team1_trade_report = implode(', ', $team1_trade_players);
3. $team2_trade_report = implode(', ', $team2_trade_players);
4. $team1_transaction="Trades {$team1_trade_report} to {$team1} for {$team2_trade_report}";
5. $team2_transaction="Trades {$team2_trade_report} to {$team2} for {$team1_trade_report}";
6. 
7. require_once 'transaction_log.php';
8. transaction_log($team2, $team1_transaction, $db);
9. transaction_log($team1, $team2_transaction, $db);
```

好吧，所以没有使用我们可以测试的对象。那么 $team1_trade_players 和 $team2_trade_players 是如何构建的呢？

```php
1. foreach ($data1 as $playerInfo) {
2.     list($dataSet, $playerId) = explode('_', $playerInfo);
3.     $playerInfo = $rosterModel->getById($playerId);
4. 
5.     if ($playerInfo['ibl_team'] !== $team1) {
6.         $team1_trade_players[] = trim($playerInfo['display_name']);
7.         $rosterModel->updatePlayerTeam($team1, $playerId, $team2TradeComment);
8.         $rosterModel->makeInactive($playerId);
9.     }
10. }
11. 
12. foreach ($data2 as $playerInfo) {
13.     list($dataSet, $playerId) = explode('_', $playerInfo);
14.     $playerInfo = $rosterModel->getById($playerId);
15. 
16.     if ($playerInfo['ibl_team'] !== $team2) {
17.         $team2_trade_players[] = trim($playerInfo['display_name']);
18.         $rosterModel->updatePlayerTeam($team2, $playerId, $team1TradeComment);
19.         $rosterModel->makeInactive($playerId);
20.     }
21. }
```

这是我在判断要做多少额外工作的点。这段代码使用了我重构的 getById() 方法，以确保它正确地为球员信息添加未上卡标识。我真的需要创建一个单独的对象来处理球员详情数组并创建日志条目，然后再将其交给 transaction_log() 函数吗？我认为更好的做法是遍历生成交易日志条目的任何代码，并确保它们使用的是经过测试的 RosterModel 方法。

进一步搜索后，我找到了这段代码片段，每当一名或多名球员从球队被释放时就会使用它。

```php
1. if (isset($_POST['release'])) { $release = true; }
2.
3. if ($release === true) {
4.   $release_list = $_POST['release'];
5.   $released_players = [];
6.
7. /** @var array $release_list */
8. foreach ($release_list as $player_id) {
9.   $info = $roster->getById($player_id);
10.   $player_name = trim($info['tig_name']);
11.
12.   if ($roster->isUncarded($player_name)) {
13.     $uc_value = $roster->getUncardedValue($player_name);
14.     $player_name .= " [UC {$uc_value}]";
15.   }
16.
17.   $released_players[] = $player_name;
18. }
19.
20. $log_entry = 'Releases ' .implode(', ', $released_players);
21. transaction_log($tbl_team, $log_entry, $db);
22. $roster->releasePlayerByList($release_list);
23. include 'templates/modify_roster/release.php';
24. }
```

我认为我可以重构这段代码以使用不同的方法，并且确信在生成日志条目时它能正确执行。

```php
if ($release === true) {
    $release_list = $_POST['release'];
    $released_players = [];

    /** @var array $release_list */
    foreach ($release_list as $player_id) {
        $info = $roster->getById($player_id);
        $released_players[] = $info['display_name'];
    }

    $log_entry = 'Releases ' . implode(', ', $released_players);
    transaction_log($tbl_team, $log_entry, $db);
    $roster->releasePlayerByList($release_list);
    include 'templates/modify_roster/release.php';
}
```

所以现在我有代码做的事情与之前完全相同，但代码行更少。此外，它使用了我已编写测试的代码，以确认边缘情况（该球员是否未上卡？）是否被正确处理。

当你深入为现有应用程序编写测试时，你会发现这种方法非常有用：

- 我正在测试什么行为？
- 处理此行为的代码是什么样的？
- 该行为的测试会是什么样？
- 我们有哪些依赖？
- 这些依赖需要更改还是可以使用真实的？
- 我们是否需要质疑关于代码实际如何工作的假设？
- 我们是否需要更改代码以使测试通过？
- 我们是否有通过的测试？

在上面的示例中，你可以看到我遵循了每一步。我经常告诉大家，测试就是专注于小块工作并不断迭代，直到回答一个问题：这段特定的代码是否显示了我期望的特定行为？大部分工作只是遵循我上面分享的类似清单，并在最后回答那个高层次的问题。



# 7. 以示例为依据的测试后开发

有时候情况决定了你在已有可运行应用之后才编写测试。这并不意味着你不能开始编写测试。只需做好为期望结果做出选择的准备。你很可能需要修改一些代码以使其可测试。你会发现有些事情并不像你想象的那样工作。

最终，你所寻找的是一个测试系列，它能让你确信，如果你更改了某些内容，就有一些测试可以告诉你是否破坏了某些东西。就像事务日志条目一样。再次。

# 8. 重构辅助工具

测试是你编写的代码，用来确保其他代码按预期行为。
它们需要与你对所测试代码应给予的同等程度的关怀和关注。我们处理应用代码重构的许多相同方法也适用于测试代码。在本章中，我想展示我是如何重构一个现有的测试辅助工具使其更有用。

# 8. 重构辅助工具

首先，我需要给你一些背景。我投入最多工作的开源项目是 OpenCFP，这是一个自托管的 PHP 应用，会议组织者可以用它来收集和评定会议演讲提案。它有很多测试。测试数量没有我希望的那么多，但我只是一个人，时间有限。我的贡献者也是如此。

所以我觉得同时需要务实和自律，如果这有意义的话。我们通过在该方法的 DocBlock 中添加注解来标记一个辅助方法以便将来移除。下面是我要重构的那个方法：

```
```php
/**
 * @deprecated
 *
 * @param array $properties
 *
 * @return Model\\User|\\PHPUnit_Framework_MockObject_MockObject
 */
private function createUserMock(array $properties = []): Model\\User
{
    $user = $this->createMock(Model\\User::class);

    $user
        ->expects($this->any())
        ->method('__get')
        ->willReturnCallback(function (string $property) use ($properties) {
            if (\\array_key_exists($property, $properties)) {
                return $properties[$property];
            }
        });

    return $user;
}
```
```

重构结束时，这个辅助工具应该做同样的事情：创建一个可被现有测试使用的依赖。那，我们从哪里开始？

OpenCFP 的测试套件同时使用 Mockery 和 Prophecy，这两个库用于创建测试替身。如果我有强烈的偏好，我可能会选择其中一个工具，然后将使用未选工具的辅助方法标记为已弃用，或在测试中添加注释以指示需要修改。

我不认为其中一个对项目来说是“正确”的。我最初使用 Mockery，然后尝试了一些使用 Prophecy 的测试，我真的无法做出决定！不过，我确实需要一些东西来帮助我做出决定。

# 8. 重构辅助工具

一切都通过了。下面是辅助工具现在的样子：

```
```php
/**
 * @param array $properties
 * @return Model\User
 */
private function createUserMock(array $properties = []): Model\User
{
    $user = new class extends Model\User {
        public $properties;

        public function __get($property)
        {
            if (\array_key_exists($property, $this->properties)) {
                return $this->properties[$property];
            }
        }

        public function __set($property, $value)
        {
            $this->properties[$property] = $value;
            return;
        }
    };
    $user->properties = $properties;

    return $user;
}
```
```

重新运行测试并确保这次重构没有破坏任何东西。

```
```
/usr/local/bin/php -dxdebug.remote_mode=jit \
/Users/chartjes/Sites/opencfp/vendor/phpunit/phpunit/phpunit \
--no-configuration OpenCFP\Test\Unit\Domain\Speaker\SpeakerProfileTest \
/Users/chartjes/Sites/opencfp/tests/Unit/Domain/Speaker/SpeakerProfileTest.php \
--teamcity
PHPUnit 7.5.8 by Sebastian Bergmann and contributors.

Time: 301 ms, Memory: 10.00 MB

OK (45 tests, 45 assertions)

Process finished with exit code 0
```
```

太棒了！测试套件仍然通过，并且我已修复了已弃用方法。

# 9. 测试 API

我所做的大部分测试工作都集中在测试应用代码上。这对于帮助设计可测试代码和防止未来回归非常有效。但除了应用代码之外，还有很多其他东西需要测试。

## 响应验证

接下来，我将为测试制定我的 Arrange-Act-Assert 步骤，以伪代码形式完成。

```
```php
public function it_finds_a_page_of_cards(): void
{
    // Arrange
    /**
     * What are the fields we want to see?
     * What is the API call we are making?
     */

    // Act
    /**
     * Make the API call
     * Turn the JSON response into something we can compare
     */

    // Assert
    /**
     * Assert that the response matches our expectation
     */
    $this->assertTrue(false);
}
```
```

现在，我将把该伪代码转换为实际代码。

```
```php
public function it_finds_a_page_of_cards(): void
{
    // Arrange
    $expected_fields = ['object', 'total_cards', 'has_more', 'next_page'];
    $api_url = 'https://api.scryfall.com/cards?page=1';

    // Act
    $response = json_decode(
        file_get_contents($api_url),
        true,
        512,
        JSON_THROW_ON_ERROR
    );

    // Assert
    foreach ($expected_fields as $field) {
        $this->assertArrayHasKey($field, $response);
    }
}
```
```

# 9. 测试 API

测试通过了吗？

```
Testing started at 1:54 p.m. ...
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
--no-configuration --filter "/(::it_finds_a_page_of_cards)( .*)?$ /" \
ApiResponseTest /Users/chartjes/grumpy-guide/test/api_response_test.php \
--teamcity
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 409 ms, Memory: 14.00 MB

OK (1 test, 4 assertions)
```

接下来，我想编写一个测试，当我可以保证无论调用多少次，我即将进行的 API 请求都将相同。查看他们的文档后，似乎他们使用唯一 ID 来表示数据库中的卡片。我将构建一个测试，执行其中一个特定调用，然后确保响应中的某些字段包含我期望的值。下面是测试的样子：

```
1. public function it_gets_card_details_as_expected(): void
2. {
3.   // Arrange
4.   $card_id = '9ff745f8-8fc2-4f88-ba25-03f8b9ae4932';
5.   $api_url = 'https://api.scryfall.com/cards/' . $card_id;
6. 
7.   // Act
8.   $response = json_decode(
9.     file_get_contents($api_url),
10.    true,
11.    512,
12.    JSON_THROW_ON_ERROR
13.  );
14. 
15.   // Assert
16.   $this->assertEquals('card', $response['object']);
17.   $this->assertEquals($card_id, $response['id']);
18.   $this->assertEquals('Dusk // Dawn', $response['name']);
19. }
```

我的测试通过了。

```
```text
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
 --no-configuration --filter "/(::it_gets_card_details_as_expected)( .*)?$/" \
 ApiResponseTest /Users/chartjes/grumpy-guide/test/api_response_test.php \
 --teamcity
 PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

 Time: 1.21 seconds, Memory: 12.00 MB

 OK (1 test, 3 assertions)
```
```

这类测试相当直接，但根据返回的响应类型，它们可能提供的价值不足。我可以编写一个更全面的测试来检查更多字段的存在，但我仍然存在一些潜在问题。如果响应包含我未预期的额外字段怎么办？或者如果某个字段的值从整数变为字符串怎么办？大多数 API 会随时间变化，我希望我的测试能够随之变化。对于这种情况，我最好的选择是转向执行模式验证测试。

## API 模式验证

描述 API 的标准称为 OpenAPI。从该规范的网站上：

> > The OpenAPI Specification (OAS) defines a standard, language-agnostic interface to RESTful APIs which allows both humans and computers to discover and understand the capabilities of the service without access to source code, documentation, or through network traffic inspection. When properly defined, a consumer can understand and interact with the remote service with a minimal amount of implementation logic. An OpenAPI definition can then be used by documentation generation tools to display the API, code generation tools to generate servers and clients in various programming languages, testing tools, and many other use cases. This is of interest to programmers because it allows for a development-with-testing workflow that looks like this:

+   - API 开发者构建他们的 API
+   - 他们使用支持生成 OpenAPI 规范的工具对其进行文档化
+   - 测试可以通过验证响应是否符合规范来编写





# 9. 测试 API

这里要强调的一点是，这类测试并不关心响应的实际内容。我不一定关注具体的值，比如 ID 或时间戳。我想要做的是确保响应中的任何数据都符合字段名称和数据类型的预期。

从宏观层面来看，这些测试的目标如下：

-   获取被测 API 的 OpenAPI 模式
-   向 API 发出请求
-   根据模式验证响应

在下面的所有示例中，我使用 OpenAPI 3.x 作为 API 文档的标准。Swagger 是旧式的 API 文档方式，所以我强烈建议大家转向（或从一开始就使用）OpenAPI 3.x。关于使用 OpenAPI 及相关工具的更多细节可以在 OpenAPI.Tools[^1] 找到，而关于使用 OpenAPI 规范构建 API 的优秀建议可以在 https://apisyouwonthate.com 找到。非常感谢 Phil Sturgeon 和 Matthew Trask 为我指出了许多非常有用的 API 资源。

## 获取被测 API 的 OpenAPI 模式

在这些示例中，我将使用一个带有 OpenAPI 模式的公开 API。你可以在 https://petstore.swagger.io 查看这个 API。

下一步是将其从 Swagger 转换为 OpenAPI。OpenAPI.Tools 有一个它们推荐的工具列表。同样，选择一个适合你的。就我而言（因为我用 Python 做了很多测试工作），我选择了 pyswagger[^2]。下载 Petstore 的 YAML 规范后，我进行了转换，最终得到一个符合 OpenAPI 3.x 的 YAML 文件。

但我还没有完成——我安装了 Speccy[^3]，并用它来验证这个新文档，修复了我发现的任何错误。然后，我在测试目录中创建了一个名为 specs 的目录，并将我的新规范文件复制到该目录中。

## 向 API 发出请求

在进一步操作之前，让我先创建第一个验证测试的骨架。

```php
/**
 * @test
 */
public function it_validates_getPetById(): void
{
    $this->assertTrue(false);
}
```

现在，我构建要向 API 发出的请求。

```php
public function it_validates_getPetById(): void
{
    $uri = 'https://petstore.swagger.io/v2/pet/1';
    $responseData = json_decode(
        file_get_contents($uri),
        true,
        512,
        JSON_THROW_ON_ERROR
    );

    // other code below...
}
```

为了验证这些响应，我采纳了一些 OpenAPI.Tools 的建议，选择使用 OpenAPI-Validator，你可以使用 Composer 安装它（作为开发依赖，而不是放在生产环境中，这始终是一个好主意）。

```shell
composer req --dev mmal/openapi-validator
```

现在，我想与你分享一些东西。不同的 OpenAPI 验证工具使用不同的技术来判断你的规范是否有效。在我修复了 Speccy 报告的问题后，Speccy 说我的规范符合 OpenAPI。而当我使用 OpenAPI-validator 时，嗯，它对什么是有效的 API 有自己的看法。当我添加验证规范的代码时，它报告了许多错误，我一一修正，直到一切看起来正常。

虽然遍历这些错误令人烦恼，但这恰恰说明了一个要点：规范的工作就是告诉你是否在做正确的事情。与单元测试非常相似，一份好的、全面的规范意味着你不会浪费时间调试那些容易被捕获的错误。

## API 模式验证

因此，按照文档说明，我添加了验证规范并确保返回的响应符合我们期望的代码。

```php
// Added these dependencies that we needed at the top of the file
use Mmal\OpenapiValidator\Validator;
use Symfony\Component\Yaml\Yaml;

public function it_validates_getPetById(): void
{
    $uri = 'https://petstore.swagger.io/v2/pet/1';
    $responseData = json_decode(
        file_get_contents($uri),
        true,
        512,
        JSON_THROW_ON_ERROR
    );
    $validator = new Validator(Yaml::parse(
        file_get_contents(__DIR__ . '/specs/api.yaml')
    ));
    $result = $validator->validateBasedOnRequest(
        '/pet/{petId}',
        'GET',
        200,
        $responseData
    );
    $this->assertFalse($result->hasErrors());
}
```

好的，我将从头到尾解释这个测试。

首先，我调用 API，得到 JSON 响应，并将其解码存储到 $responseData 中。接下来，我使用 Validator 对象结合 YAML 解析器来查看我的规范文件并验证它。

下一步需要更多解释。当你使用 validateBasedOnRequest() 方法时，需要提供以下内容：

-   在 OpenAPI 规范中定义的、你正在测试的调用路径
-   你用于请求的 HTTP 方法
-   你期望的 HTTP 状态码
-   你期望看到的 JSON 解码数据

有了这些信息，我们通过断言来完善测试：当将响应内容与我们的规范进行比较时，没有错误。测试通过了吗？

```text
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
--no-configuration --filter "/(::it_validates_getPetById( .* )?$/" \
ApiResponseTest /Users/chartjes/grumpy-guide/test/api_response_test.php \
--teamcity
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 612 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)
```

那么，如何证明验证确实有效呢？我将创建一个包含错误值的 API 响应，然后测试应该会报告验证错误。

```php
/**
 * @test
 */
public function it_catches_invalid_responses(): void
{
    // Arrange
    $invalidResponse = '
    {
        "id": "0",
        "category": {
            "id": 0,
            "name": "string"
        },
        "name": "doggie",
        "photoUrls": [
            "string"
        ],
        "tags": [
            {
                "id": 0,
                "name": "string"
            }
        ],
        "status": "available"
    }';

    $validator = new Validator(Yaml::parse(
        file_get_contents(__DIR__ . '/specs/api.yaml')
    ));

    // Act
    $result = $validator->validateBasedOnRequest(
        '/pet/{petId}',
        'GET',
        200,
        json_decode($invalidResponse, true, 512, JSON_THROW_ON_ERROR),
    );

    // Assert
    $this->assertTrue($result->hasErrors());
}
```

测试通过。

```text
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
 --no-configuration --filter "/(::it_catches_invalid_responses)( .*)?$/" \
 ApiResponseTest /Users/chartjes/grumpy-guide/test/api_response_test.php \
 --teamcity
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 278 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)

Process finished with exit code 0
```

验证测试非常适合发现你的 API 是否在没有被察觉的情况下发生了变化——这种不确定性可能导致糟糕的体验，并在生产环境中出现奇怪的错误。需要说明的是，这里确实有额外的工作，因为需要有人创建并维护 OpenAPI 规范。你可以使用像 Stoplight Studio[^4] 这样的工具，在创建 API 的同时创建规范。

# 第 10 章 数据提供器

## 为什么你应该使用数据提供器

你的主要目标之一始终应该是编写尽可能少的代码来解决特定问题。对于测试来说也是如此，测试本质上不过是代码。

在我开始编写全面测试套件时，学到的早期经验之一就是始终在测试中寻找重复。这里有一个可能发生这种情况的示例。

你可能熟悉 FizzBuzz 问题[^5]，即使仅仅因为它有时作为面试的一部分被提出。这是一个好问题，因为它涉及许多非常基础的编程知识——你需要理解循环、集合和条件语句。

当你为 FizzBuzz 编写测试时，你想要做的是传递一组值，并验证它们是否被正确地 FizzBuzz 处理。这可能会导致你编写多个相同的测试，只是测试用的值不同。数据提供器为你提供了一种简化该过程的方法。

数据提供器是一种创建多组测试数据的方式，这些数据可以作为参数传递给你的测试方法。你创建一个测试类可用的方法，它返回一个与传入测试的参数匹配的值数组。

听起来比实际更复杂；让我们看一个示例。

## 看看所有这些测试

如果你不知道数据提供器，你的 FizzBuzz 测试会是什么样子？

```php
<?php
class FizzBuzzTest extends PHPUnit\Framework\TestCase
{
    public function setUp()
    {
        $this->fb = new FizzBuzz();
    }

    public function testGetFizz()
    {
        $expected = 'Fizz';
        $input = 3;
        $response = $this->fb->check($input);
        $this->assertEquals($expected, $response);
    }
}
```

[^1]: OpenAPI.Tools: https://openapi.tools
[^2]: pyswagger: https://github.com/mission-liao/pyswagger
[^3]: Speccy: https://github.com/wework/speccy
[^4]: Stoplight Studio: https://stoplight.io
[^5]: FizzBuzz 问题: <http://en.wikipedia.org/wiki/FizzBuzz>





# 10. 数据提供者

```php
17. public function testGetBuzz()
18. {
19.     $expected = 'Buzz';
20.     $input = 5;
21.     $response = $this->fb->check($input);
22.     $this->assertEquals($expected, $response);
23. }
25. public function testGetFizzBuzz()
26. {
27.     $expected = 'FizzBuzz';
28.     $input = 15;
29.     $response = $this->fb->check($input);
30.     $this->assertEquals($expected, $response);
31. }
33. function testPassThru()
34. {
35.     $expected = '1';
36.     $input = 1;
37.     $response = $this->fb->check($input);
38.     $this->assertEquals($expected, $response);
39. }
40. }
```

我相信你能看出其中的模式：

- 多个输入值
- 测试的搭建和执行过程极其相似
- 反复使用相同的断言

## 创建数据提供者

数据提供者是测试类中的另一个方法，它返回一个结果数组，其中每个结果集本身也是一个数组。通过一些神奇的内部操作，PHPUnit 会将返回的结果集转换为你的测试方法签名需要接受的参数。

```php
public function fizzBuzzProvider()
{
    return [
        [1, '1'],
        [3, 'Fizz'],
        [5, 'Buzz'],
        [15, 'FizzBuzz']
    ];
}
```

提供者的函数名无关紧要，但我倾向于给它们起一个像英文一样可读的名称，因为当测试失败时，PHPUnit 会告诉你一个名为“ex1ch2”或类似难以立即理解其用途的数据提供者，你可能会一头雾水。

要使用数据提供者，我们需要在测试方法前面的 DocBlock 中添加一个注解，这样 PHPUnit 就会知道使用它。在注解中给出数据提供者方法的名称。

```php
/**
 * 测试我们的 FizzBuzz 对象
 *
 * @dataProvider fizzBuzzProvider
 */
public function testFizzBuzz($input, $expected)
{
    $response = $this->fb->check($input);
    $this->assertEquals($expected, $response);
}
```

现在我们只有一个测试（减少了需要维护的代码量），而且可以通过数据提供者随心所欲地添加场景（甚至更好）。我们还学会了对自己编写的测试代码进行批判性分析的技巧，以确保只编写真正需要的测试。

使用数据提供者时，PHPUnit 会针对提供者传入的每组数据运行一次测试方法。如果测试失败，它会指出在关联数组中哪一个索引被用于该次测试运行。

## 更复杂的示例

不要觉得只能使用非常简单的数据提供者。你所需要做的就是返回一个数组的数组，其中每个结果集都与你测试方法期望的参数相匹配。下面是一个更复杂的例子：

```php
public function complexProvider()
{
    // 从 CSV 文件中读取一些数据
    $fp = fopen("./fixtures/data.csv");
    $response = [];

    while ($data = fgetcsv($fp, 1000, ",")) {
        $response[] = array($data[0], $data[1], $data[2]);
    }

    fclose($fp);

    return $response;
}
```

不要以为数据提供者能做的事情仅限于此。目标是创建对测试有用的数据集。

## 数据提供者技巧

由于数据提供者返回关联数组，你可以为它们指定更具描述性的键，以帮助调试。例如，我可以重构 FizzBuzz 测试的数据提供者：

```php
return [
    'one' => [1, '1'],
    'fizz' => [3, 'Fizz'],
    'buzz' => [5, 'Buzz'],
    'fizzbuzz' => [15, 'FizzBuzz']
];
```

此外，数据提供者不必是同一个类中的方法。你可以使用其他类中的方法，只需将它们的可见性设置为 public。你也可以使用命名空间。以下两个示例可以放入任何想要使用其他类中提供者的测试的 DocBlock 中：

- `@dataProvider Foo::dataProvider`
- `@dataProvider Grumpy\Helpers\Foo::dataProvider`

这允许你创建专门用作数据提供者的辅助类，并减少测试代码中的重复代码量。

## 最后思考

数据提供者的作用是通过提供一种让测试使用多组输入数据和/或预期结果数据的方式，来减少测试中的代码重复。就像任何代码一样，如果你发现自己正在重复编写相同的代码，我建议你审视一下测试，判断数据提供者是否是一个合适的解决方案。

# 第 11 章：包装器

## 高视角下的包装器

我在这里提出的想法可能属于某种软件设计模式，但我似乎找不到那本非常著名的《设计模式：可复用面向对象软件的基础》一书。我们就把它称为包装器吧。

创建一个对象，其构造函数接受另一个知道如何与 API 通信的对象作为参数。这个包装器对象通常会复制主要 API 对象的方法，以减少对功能方面的困惑。让我给你看一个例子。

我在 Twitter 上寻求一些免费、可公开访问且能生成有用信息的 Web API 示例。我收到了许多建议，但我选择的是 JSONPlaceholder[1]。它自称是一个“免费的在线 REST 服务，你可以在需要任何假数据时使用”。听起来正是我需要的。

当然，我会从测试开始：

```php
<?php
declare(strict_types=1);

require '../vendor/autoload.php';
require '../src/JsonPlaceHolder.php';

class JsonPlaceHolderTest extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function callToPostsReturns100Posts()
    {
        $jph = new JsonPlaceHolder();
        $posts = $jph->getPosts();
        $this->assertCount(100, $posts);
    }
}
```

测试失败，因为我还没有写任何代码。

我的 JSONPlaceholder 对象应该是什么样子才能通过测试呢？

[1] JSONPlaceholder: http://jsonplaceholder.typicode.com

```php
<?php
declare(strict_types=1);

class JsonPlaceHolder
{
    public $url = 'http://jsonplaceholder.typicode.com';

    public function getPosts()
    {
        $response = file_get_contents("{$this->url}/posts");
        return json_decode($response, true, 512, JSON_THROW_ON_ERROR);
    }
}
```

测试现在通过了。

```text
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
  --no-configuration JsonPlaceHolderTest \
  /Users/chartjes/grumpy-guide/test/JsonPlaceHolderTest.php --teamcity \
  --cache-result-file=/Users/chartjes/grumpy-guide/.phpunit.result.cache
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 292 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)

Process finished with exit code 0
```

如果我想为这段代码编写一些单元测试，该怎么做？我不想真正去访问 Web API，所以我们可以创建一个包装器。我来创建一个简单的直通包装器。

```php
<?php
declare(strict_types=1);

class JsonPlaceHolderWrapper
{
    public $jph;

    public function __construct(JsonPlaceHolder $jph)
    {
        $this->jph = $jph;
    }
}
```

现在，既然我在使用包装器，我就可以创建一些行为上像我期望的 JSONPlaceholder 对象、但完全不与 API 通信的东西。

```php
<?php
declare(strict_types=1);

require '../src/JsonPlaceHolder.php';

class FakeJsonPlaceHolder extends JsonPlaceHolder
{
    public function getPosts()
    {
        /**
         * 我们知道一条记录应该看起来像这样：
         * {
         * "userId": 1,
         * "id": 1,
         * "title": "sunt aut facere repellat provident occaecati",
         * "body": "quia et suscipit suscipit recusandae consequuntur"
         * }
         */
        $response = [];
        $x = 1;
        while ($x <= 100) {
            $post = [
                'userId' => 1,
                'id' => uniqid('', true),
                'title' => uniqid('', true),
                'body' => uniqid('', true)
            ];
            $response[] = $post;
            $x++;
        }

        return $response;
    }
}
```

接下来，我将测试修改为使用这个假对象。




# 11. 包装器

```php
<?php
declare(strict_types=1);

require '../vendor/autoload.php';
require 'FakeJsonPlaceHolder.php';
require '../src/JsonPlaceHolderWrapper.php';

class JsonPlaceHolderTest extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function callToPostsReturns100Posts()
    {
        $jph = new FakeJsonPlaceHolder();
        $wrapper = new JsonPlaceHolderWrapper($jph);
        $posts = $wrapper->getPosts();
        $this->assertCount(100, $posts);
    }
}
```

测试仍然通过：

```
/usr/local/bin/php -dxdebug.remote_mode=jit /usr/local/bin/phpunit \
--no-configuration --filter "/(::callToPostsReturns100Posts)(.*)?$/" \
JsonPlaceHolderTest /Users/chartjes/grumpy-guide/test/JsonPlaceHolderTest.php \
--teamcity --cache-result-file=/Users/chartjes/grumpy-guide/.phpunit.result.cache
PHPUnit 8.3.4 by Sebastian Bergmann and contributors.

Time: 163 ms, Memory: 12.00 MB

OK (1 test, 1 assertion)

Process finished with exit code 0
```

这种方法的缺点是，你通过测试暴露了依赖项的一些实现细节。这是一个创建测试替身的非常简单的例子，但我写过需要多层替身返回替身再返回替身的测试。它很脆弱，而且如果依赖项本身发生变化，测试很容易不再反映现实。

# 第12章：元测试

如果你不熟悉《万智牌》，我只能把它描述成国际象棋，但棋子不断被创造出来。旧棋子可以在二级市场上卖出很多钱。你通过购买或与其他人交易来获得卡牌，并用卡牌组建卡组来玩游戏。它是世界上最受欢迎的收藏卡牌游戏，拥有令人眼花缭乱的卡牌和格式可供选择。

竞技锦标赛中出现的一个有趣概念是元游戏的想法。它是贴在人们选择的卡组和他们可能使用的策略上的标签。高水平玩家（是的，甚至有职业玩家）通过了解他们将要参加的锦标赛的元游戏并尝试弄清楚哪些卡组和策略最有可能给他们带来优势，从而获得优势。

这与为你的 PHP 代码编写测试有什么关系？我们可以将元游戏的概念应用于测试实践。显然，有些实践是好的，有些则不是那么好。我想研究其中的一些，以帮助你找到可能带来更好应用结果的东西。记住，你用测试真正想要做的是防止回归并确保应用程序对将使用它的人有用。最终没有别的什么重要。

那么从我的角度来看，测试的“元游戏”是什么样的？

## 成熟的测试工具可用

PHP 开发者在测试工具方面选择众多。单元测试工具的黄金标准 PHPUnit（一种推广使用 xUnit 测试模式的测试工具）稳定且成熟。我不想说“在我那个年代你得双向做事，逆着雪上坡”，但我在 2019 年底写这篇文章时，PHPUnit 周围有一个很棒的生态系统，并且有很多互补的工具以及以 PHPUnit 为基础构建的工具。

当你考虑诸如 Behat（一种推广使用行为驱动开发来定义测试的测试工具）或 Codeception（一种专注于使用浏览器自动化的测试工具）等工具时，很明显没有不采用自动化测试实践的真正借口。

虽然开发者倾向于重新发明工具而不是修改现有工具，但我认为我们已经达到一个阶段，即 PHP 社区已经接受了一些可靠的测试策略。选择一个工具并开始吧。

你可以编写可以自动化的测试，也可以编写可以手动执行的测试。无论哪种方式，你都在编写测试。为什么不让计算机——它对应用程序哪些部分重要没有任何偏见——为你运行测试呢？

是的，以前这些工具安装并不容易，也没有太多关于如何全面使用它们的信息。但现在不是了。

测试你的代码。它将为你节省时间和金钱，让你专注于解决问题，而不是修复本可以防止进入生产环境的错误。

## 开源推动接受

你依赖的任何开源代码来完成日常工作几乎不可能没有测试。每个流行的 PHP Web 应用程序框架都有全面的测试套件以及如何运行它的说明。你使用的数据库有全面的测试。你的应用程序所依赖的 Web 服务器也有全面的测试。

就我个人而言，我避免使用没有自己测试套件的第三方库。在我看来，这充分说明了作者对代码质量和寿命的承诺。

事实上，许多项目不会在没有测试证明修复按预期工作时接受错误修复。对于想要开始为开源项目贡献代码的人来说，只需查看已存在的测试，你就能获得一次关于如何编写测试的速成课程。

## 证明存在以支持承诺

2008 年，发表了一篇关于 TDD 影响的论文，其中研究了微软和 IBM 进行的案例研究。你可以在网上找到这项研究[1]。

[1] 在线：http://research.microsoft.com/en-us/groups/ese/nagappan_tdd.pdf

几支团队被要求通过代码解决同一个问题。其中一些团队被要求使用 TDD，其他团队则没有。这项研究的结果非常有趣，是编写代码测试价值的实际证据。

我鼓励你阅读实际的论文（它只有 14 页），但最大的收获是：使用 TDD 的项目报告的缺陷比未使用它的项目少 40-90%，但它们完成工作所需的时间长了 15-35%。

如果你喜欢在与人讨论时利用统计数据，可以总结为“每周多花一天时间，我们最多可以减少 90% 进入生产环境的错误”。这是一个非常有力的论点。

## 测试将错误修复转移到周期的更便宜部分

这个特定的概念是我花了几年时间才完全理解的。就像关于 TDD 带来的好处是生产错误更少而开发时间只略有增加的论点一样，“转移成本”的论点也非常有力。

从投入的开发人员时间和资源来看，发现代码中错误最便宜的时间是在开发人员进行初始开发和探索性测试期间。如果你实践 TDD，你会为代码预期的工作方式编写测试，然后编写代码直到测试通过。我们称此成本为 X。

一旦开发人员“完成”，代码就需要从“开发”状态转移到“质量保证”状态。这可以采取多种形式，例如代码审查、用于测试代码更改的暂存环境。在代码审查期间发现错误的成本可能在 2X 到 10X 之间。

为什么？想想看——你现在必须回去不仅验证错误，还要确保你所做的代码更改不会导致其他东西损坏。然后，你必须再次将代码从“开发”移出并重新进入“质量保证”。不要自欺欺人；这个过程需要时间，而且往往受制于他人的日程安排！

一旦你确信你的代码按预期运行，它就需要进入“已部署”状态。我可以从个人经验告诉你，修复错误最昂贵的时间是当它被野外的第三方发现时。我认为保守估计是将其标记为 100X。事实上，让我们进一步分解。

首先，我们有错误的情感或“文化”成本。严重的生产错误通常伴随着恐慌的环境，以及许多人混乱地试图解决同一个问题。我曾在许多公司工作过，这些公司强迫开发团队都留下来解决问题——即使你与问题无关也帮不上忙。

如果有足够多的错误进入生产环境，你可能会导致部署变得超级有压力。那会怎样？部署会转移到“正常”工作时间之外进行——意味着你最终会比平时晚很多或早很多工作。“每个人都需要在这里，以防出现问题。”换句话说，对生产推送的恐慌变得“新常态”，而不是本应无关紧要的问题。

生产错误的第二个成本是机会成本的损失。如果你负责一个正在进行项目的团队，你必须本能地理解花费在修复已发布产品中发现的错误上的每一分钟，都是没有用于推进项目目标的一分钟。错误阻止你的团队重构旧问题或实现新功能。这是一项真正的成本，很少被考虑。

## 良好的文档化构建系统鼓励持续部署

投入大量资源用于自动化测试的原因之一是创建自动化构建系统，这些系统获取已编写的代码，运行所有测试，如果全部通过，则自动部署代码（以及支持它所需的一切）。




## 文档完善的构建系统鼓励持续部署

当我刚开始思考如何实现这一点时，选用的工具是 Jenkins[2]。它是一个基于 Java 的自动化工具，在帮助你方面极其灵活，并且有大量可用的插件。很有可能，如果你想要用 Jenkins 做某事，已经有人想出了用插件实现的方法。

构建自动化的理念是，将你在部署和测试过程中通常手动完成的步骤自动化。毕竟，计算机非常擅长一遍又一遍地执行你吩咐它们做的事情，而且毫无怨言！与许多事情一样，一旦你自动化了测试的运行方式，就不必再为之操心了。你可以把脑力节省下来，用于在公司聊天中开玩笑或在社交媒体上怼人。

然而，你的选择并不局限于 Jenkins。对于那些不想自己托管 CI 服务器的人来说，一个很好的替代方案是使用 Travis CI[3]、CircleCI[4] 或 GitHub Actions[5] 等服务。这些服务允许你复制当有人获取你的代码并想要运行测试时所经历的过程。它们都有各自独特的语法和怪癖，但最终都会殊途同归——一个以 Git 为中心的系统，可以对拉取请求或合并做出反应，并执行一系列步骤，最终运行你的测试。

对于 OpenCFP[6]，我已开始使用 GitHub Actions 作为我的构建自动化工具。查看它的配置文件时，它会为我完成以下所有事情：

- 检出代码
- 安装我希望测试所针对的精确 PHP 版本
- 使用 Composer 安装所有依赖
- 对代码运行代码检查器和样式修复器
- 运行数据库迁移
- 构建我的 CSS 和 JS 资源
- 验证使用 ORM 的代码的所有映射和模式
- 运行测试

[2] Jenkins: https://jenkins-ci.org
[3] Travis CI: https://travis-ci.org
[4] CircleCI: https://circleci.com
[5] GitHub Actions: https://github.com/features/actions
[6] OpenCFP: https://github.com/opencfp/opencfp

# 12. 元测试

这些一开始都是手动完成的事情，但我希望它们自动化。在理想的环境中，我会希望这类事情在本地完成。该项目确实使用 Composer 的 “scripts” 部分来定义一些任务，以完成上述那些确切的步骤。我要再次强调，我希望计算机为我一遍又一遍地重复这些任务。与计算机执行相比，我在其中某一步出错的可能性要高得多。

## 有一些很棒的互补工具

仅仅拥有代码测试是不够的。持续编写这些测试并专注于有效使用测试驱动开发（TDD）确实需要大量的自律。幸运的是，其他人也一直在解决同样的问题，并且有一些我可以推荐的解决方案。

### XDebug

首先，有 XDebug[7]。XDebug 是一个 PHP 扩展，它可以让你做两件对 PHP 开发者有用的事情。第一，当你在重构现有代码或只是想弄明白“为什么这段代码没有按我预期的方式运行？”时，你可以将它用作逐步调试器。有很多关于如何安装 XDebug 并配置它与你喜欢的编辑器或 IDE 协作的文章。多年来，我一直抗拒使用调试器，而是依赖测试和在代码中打印调试语句。养成新习惯需要很长时间，但在 PhpStorm 的帮助下，我一直在努力记住我有一个逐步调试器，它可以在断点处向我展示变量的内容。对于任何语言的程序员来说，学习使用调试器都是一项值得精进的技能。

对于 PHP 开发者来说，XDebug 的第二个优点是，它可以与 PHPUnit 结合生成代码覆盖率报告。代码覆盖率是一个指标，许多人用它来跟踪你的代码中有多少被测试执行。代码覆盖率非常高（90% 及以上）的代码库往往可靠且没有错误。达到 100% 的代码覆盖率是可能的，但如果你不采用 TDD 来构建项目，就很难做到。

要生成代码覆盖率报告，你需要在从命令行运行测试的命令中添加一些选项，然后就会为你生成报告。最常见的选项是生成基于 HTML 的报告，你可以在浏览器中加载它，以验证测试覆盖了什么和没覆盖什么。

对于 OpenCFP，我们生成基于文本的覆盖率报告。下面是一个示例：

[7] XDebug: https://xdebug.org

```text
Code Coverage Report:
  2019-12-27 19:36:57

Summary:
  Classes: 43.69% (45/103)
  Methods: 52.15% (206/395)
  Lines:   42.50% (1085/2553)

\OpenCFP::OpenCFP\Environment
  Methods: 100.00% (12/12)   Lines: 100.00% (22/22)
\OpenCFP::OpenCFP\Path
  Methods: 75.00% (3/4)     Lines: 80.00% (4/5)
\OpenCFP::OpenCFP\WebPath
  Methods: 66.67% (2/3)     Lines: 66.67% (2/3)
\OpenCFP\Application::OpenCFP\Application\Speakers
  Methods: 100.00% (4/4)    Lines: 100.00% (13/13)
\OpenCFP\Http\Action\Profile::OpenCFP\Http\Action\Profile\EditAction
  Methods: 50.00% (1/2)     Lines: 35.48% (11/31)
\OpenCFP\Http\Action\Profile::OpenCFP\Http\Action\Profile\ProcessAction
  Methods: 25.00% (1/4)     Lines: 19.35% (12/62)
```

（看起来我还有通过测试提高覆盖率的工作要做。）

代码覆盖率报告还有其他格式——它可以生成基于 XML 的格式以供其他工具导入，或者生成一系列 HTML 页面，如果你想查找尚未测试的特定代码段，可以浏览这些页面。

就像我之前说的，代码覆盖率只是一个数字；在覆盖率 100% 的代码库中，你仍然可能会有错误和意外行为。100% 的覆盖率，如果与数据验证、过滤输入和转义输出等防御性编程技术相结合，确实可以降低代码出现错误和/或意外行为的可能性。

### 静态分析工具

测试无法告诉你是否正确使用了 PHP 语言本身的特性，甚至无法告诉你是否在制造非常隐蔽的错误。随着 PHP 在参数、返回类型和类属性中使用显式类型的方向进一步发展，一个能够发现类型相关错误实例的工具将非常有帮助。在 OpenCFP 中，我使用了两个工具——PHPStan 和 Psalm。

PHPStan[8] 这样描述自己：

[8] PHPStan: https://github.com/phpstan/phpstan

# 12. 元测试

> PHPStan 专注于在不实际运行代码的情况下发现代码中的错误。它甚至在你为代码编写测试之前就能捕获整类错误。它使 PHP 更接近编译语言，因为在运行实际代码行之前，就可以检查每一行代码的正确性。

OpenCFP 过去曾使用过 PHPStan，并且已经有一个配置文件和相应的工具来运行它。以下是我对代码库运行 PHPStan 时它告诉我的一些信息示例：

```text
------ -------------------------------------------------------------------------
 Line  src/Http/Action/Talk/UpdateAction.php
------ -------------------------------------------------------------------------
 74    Property OpenCFP\\Http\\Action\\Talk\\UpdateAction::$twig has unknown class OpenCFP\\Http\\Action\\Talk\\Twig\\Environment as
       its type.
------ -------------------------------------------------------------------------

------ -------------------------------------------------------------------------
 Line  src/Infrastructure/Event/TwigGlobalsListener.php
------ -------------------------------------------------------------------------
 45    Property OpenCFP\\Infrastructure\\Event\\TwigGlobalsListener::$twig has unknown class
       OpenCFP\\Infrastructure\\Event\\Twig\\Environment as its type.
------ -------------------------------------------------------------------------

------ -----------------------------------------------------------------
 Line  tests/Unit/Domain/Services/ResetEmailerTest.php
------ -----------------------------------------------------------------
 44    Class OpenCFP\\Test\\Unit\\Domain\\Services\\Twig\\Template not found.
------ -----------------------------------------------------------------
```

看来我需要检查一些使用 Twig 的代码。

Psalm[9] 声称自己：

> Psalm 是一个静态分析工具，它试图深入研究你的程序，并尽可能多地发现类型相关的错误。

按照说明安装并配置它之后，下面是它针对 OpenCFP 代码库报告的一个示例：

[^9]: Psalm: https://psalm.dev




## 有一些很棒的互补工具

```
INFO: MissingClosureParamType - src/Infrastructure/Templating/TwigExtension.php:65:50 - Parameter $route has no provided type
    new TwigFunction('active', function ($route) {

ERROR: PossiblyNullReference - src/Infrastructure/Templating/TwigExtension.php:67:67 - Cannot call method getRequestUri on possibly null value
    === $this->requestStack->getCurrentRequest()->getRequestUri();

INFO: MissingReturnType - src/Infrastructure/Validation/RequestValidator.php:38:21 - Method OpenCFP\Infrastructure\Validation\RequestValidator::validate does not have a return type, expecting void
    public function validate(Request $request, array $rules)

INFO: MissingReturnType - src/Kernel.php:69:21 - Method OpenCFP\Kernel::registerContainerConfiguration does not have a return type, expecting void
    public function registerContainerConfiguration(LoaderInterface $loader)

(Other details snipped)

-----------------------------
138 errors found
-----------------------------
133 other issues found.
You can hide them with --show-info=false
-----------------------------
Psalm can automatically fix 14 issues.
Run Psalm again with
--alter --issues=MismatchingDocblockReturnType,InvalidReturnType,InvalidFalsableReturnType,MissingParamType --dry-run
to see what it can fix.
-----------------------------
```

你应该使用这两种工具之一，选择哪一个其实完全是个人偏好。两者中任何一个都会对你有所帮助。

我目前偏爱 Psalm 而非 PHPStan 的原因之一，是因为它能尝试修复自己发现的问题。正如我已经说过很多很多次的那样——我更喜欢使用那些能自动修复我可能会遗漏之事的工具，这样我就可以把精力用来解决更困难的问题。

# 12. 元测试

## 变异测试

我鼓励你了解的最后一个互补测试工具是 Infection，一个变异测试工具。来自 Infection 的网站[10]：

> 变异测试涉及对程序进行小幅修改。每一个被修改后的版本都称为一个“变异体”（Mutant）。为了评估给定测试集的质量，这些变异体会针对输入测试集执行，以查看是否能够检测到被植入的缺陷。如果变异后的程序产生了失败的测试，这被称为一个“被杀死”的变异体（killed mutant）。如果变异代码上的测试仍然通过，那么我们就得到了一个“逃逸”的变异体（escaped mutant）。

如果你曾想过是否存在一个可以测试你的测试的工具，那么你会发现 Infection 这样的工具很有价值。OpenCFP 也被配置为将 Infection 作为开发依赖使用。按照说明安装并配置 Infection 之后，下面是它针对这个代码库给我的报告：

```
Running initial test suite...

PHPUnit version: 7.5.17

  575 [====================] 8 mins

Generate mutants...

Processing source code files: 119/119
Creating mutated files and processes: 1000/1000
.: killed, M: escaped, S: uncovered, E: fatal error, T: timed out

.MS...S.SSM..M...MM.MM.MM.M. MMMMMMMM.MMM.......  (  50 / 1000)
M.....M....M....M.......S..M..............  ( 100 / 1000)
...M..MS....MSSSSSSSSSS...........M.M..MMM.MMM.  ( 150 / 1000)
M.M.....M.M..M....M.M..M...........M...........  ( 200 / 1000)
....SSSSM..MM..M.SSSSMM.M..SSSSSMMM.S..MSM.....  ( 250 / 1000)
.MMMM.....M......MM.M.....SSS.SSSSSSSSSSSSSSM....  ( 300 / 1000)
..MMMM...MMMMMM.MMMMMMMMMM..MMMMSM.M.SM.M.MMM...M  ( 350 / 1000)
..MM...MMSS.MMMM....MMMMMM.MMMMMMMMM....MS.M..  ( 400 / 1000)
.M......MM.M.MMSS.....M.......................  ( 450 / 1000)
.......MMMMMMMMMMSSMMMMMMMMMMMMMMMMMMSSSS.......  ( 500 / 1000)
....MMMMMMMMMMMMMM.M....MM....MM.MSMMM.M.SM...M  ( 550 / 1000)
...M.......M....MM.M.......................M...  ( 600 / 1000)
........M.MM....SSSS..M.MM...SS.SS....M.SS.......S   ( 650 / 1000)
SS...........................................SSSSSSSSSS   ( 700 / 1000)
SSSSSSS........S...MM...SS...................S..S..S   ( 750 / 1000)
.M......MMM....MMM.................S.S.S.S...SSSS..S.S.   ( 800 / 1000)
...................................S..M..MMSS.MMSSSSSSSSSS   ( 850 / 1000)
...............................................M..M...MM   ( 900 / 1000)
...............M..............M...................S.M.......M..   ( 950 / 1000)
M..M..M.......SSSSSS.................M..........M.......S.M   (1000 / 1000)

1000 mutations were generated:
    629 mutants were killed
    136 mutants were not covered by tests
    235 covered mutants were not detected
    0 errors were encountered
    0 time outs were encountered

Metrics:
    Mutation Score Indicator (MSI): 63%
    Mutation Code Coverage: 86%
    Covered Code MSI: 73%

Please note that some mutants will inevitably be harmless (i.e., false positives).
```

[10] Infection: https://infection.github.io/guide/

作为一个粗略的指南（再说一次，这只是我的观点），MSI 与突变代码覆盖率（Mutation Code Coverage）值之间的差距表明我的测试本身还需要改进。Infection 网站上有更多关于如何解读这些数值以及如何处理的文档。

# 第 13 章 构建测试文化

要营造一个让测试成为日常工作不可或缺一部分的环境，需要付出大量努力。它不能是事后的想法，也不能在截止日期逼近时被抛诸脑后。测试必须成为一项首要实践，否则根本无法奏效。我们还要确保把术语都弄清楚——当我说“构建测试文化”时，它到底意味着什么？

## 首要目标

首要目标应该是“我们的开发人员为所有进入生产环境的代码编写测试。”任何低于这一标准的情况，都会让那些纪律稍差或对交付时间更加焦虑的人有机会故态复萌，并放弃为所有代码编写测试这一首要目标。

首要目标本应是崇高而雄心勃勃的——但在这种情况下，它们完全可以实现。你绝对可以为开发人员提供他们学习编写测试所需的全部培训和支持。你只需要改变自己的行为，并且很可能需要挑战许多你原来关于编程的信念。

设定好首要目标之后，我们来谈谈实现首要目标所需的次级目标。

## 将测试视为一流组件

当然，如果你没有任何测试，就不可能拥有包含测试的文化！这通常是任何组织走向以测试为中心的最大障碍。回想一下你学习用 PHP 编程的时候——有人教过你编写测试吗？如果有，那你真是太幸运了！

这看起来可能不言而喻，但你要做的第一件事是承诺为任何新编写的代码编写测试。是的，随着组织转型，这很可能会很痛苦。是的，你可能会为此抱怨。我不止一次参加过这样的会议，人们抱怨说如果不是“因为这些我必须写的愚蠢测试”，他们的工作早就完成了。

开发人员大多以自己的逻辑和问题解决能力为傲，但他们和其他人一样抗拒改变。养成让代码总是伴随测试的习惯会很难。

如果你想找一种更轻松地开始添加测试的方法，这里有一些你可以采用的策略。

## 为 Bug 编写测试

每当有人报告 Bug 时，编写一个测试来验证该 Bug 确实存在。我的意思是，这个测试应该失败；你应该知道正确结果应该是什么，然后让测试生成它自己的结果，并与预期进行比较。

有了一个失败且包含正确结果预期的测试，你不断修改被测代码，直到测试通过。现在，你有了一个通过的测试！

由 Bug 修复组成的测试套件，还能让你看到代码中的一些常见模式——尤其是当你觉得自己在反复修复同一类 Bug 时。

从指导者的角度看，让项目新手编写能验证 Bug 存在的测试用例可能是一个好策略。这让他们有机会探索代码库，理解各个部分如何组合在一起。对于某些代码库来说，这肯定会让人望而生畏。让他们有机会通过测试来学习代码库，可能比分配需要上线到生产环境的工作风险更低。

## 为新功能编写测试

每当你添加新代码时，都必须附带能证明新代码按预期工作的测试。这与为 Bug 编写测试类似，但在这种情况下，你是用测试来帮助自己创建可工作的代码。

在“测试是为新功能服务”的语境下，测试驱动开发（TDD）可以真正大放异彩。TDD 本质上是一种以特定方式编写代码的策略——它能让代码在很少摩擦或开发痛苦的情况下被测试。

这并非没有代价。通常，遗留应用并不适合让你编写易于测试的代码。这是许多开发人员撞上的障碍，结果他们放弃了拥有测试的目标。

我没有任何捷径能让这件事变得更容易。你所感受到的痛苦既不好也不坏——它只是当前应用架构的结果。测试良好的应用往往由一些小型代码模块组成，这些模块：

- 接受少量输入
- 除了传入的内容之外不修改任何东西（无副作用）
- 返回少量输出

当你拥有这样的代码时，测试就很容易！大多数代码并非如此。你将需要重写一些代码；你将需要开始使用新的策略；你最终创建新代码及其配套测试所需的时间，会比你以为的更久。

这一切的好处在于，根据你编写代码时所掌握的信息，你拥有能证明新功能将按预期工作的测试。良好的防御性编码习惯会有一些帮助，但事实是，拥有 100% 覆盖率单元测试的代码并不总是意味着你的应用就能正确运行。你仍然需要将它们连接起来，并以合理的方式使用它们。测试绝对不是常识的替代品。



# 13. 建立测试文化

## 重构的测试

你可能会认为这在新功能测试的章节中已经涵盖了，但我觉得它们是两回事。

你对重构的定义可能与我不同。对我来说，重构是指取一段按预期工作的代码并对其进行修改，以利用新的知识、技术或库。代码的输出或最终结果不应改变！如果发生了改变，那你就是在重写代码以实现不同的功能。

所以就重构而言，这在我看来是测试的完美候选：

- 为使用预期结果的代码编写测试
- 开始修改正在被测试的现有代码
- 运行测试并确保它通过

重复上述三个步骤，直到你满意重构已完成。

## 对同行评审的承诺

我工作过的每个拥有强大测试文化的团队都非常重视代码同行评审。对我来说，同行评审意味着在代码投入生产之前，有其他人查看我的代码以验证它是否实现了预期结果。如果你除了在开发实践中增加代码同行评审外什么都不做，代码的质量以及更重要的是代码的目的都会得到极大改善。

与主要目标相关时，我们得到的流程如下：

- 开发者正在编写代码来解决问题
- 开发者包含测试（最好使用 TDD，但测试后也有价值）
- 开发者表示代码已准备就绪
- 同行评审代码，检查测试和代码的正确意图
- 在同行批准后，代码移至下一个目标环境

现在，有一点我觉得非常重要需要强调——它应该是同行评审，而不是上级评审。说实话，大多数人不喜欢被告知自己工作的代码不好。我过去对自己写的代码以及与这些决定相关的想法极度防御。这使得同行评审比必要的更具压力，因为我浪费了更多时间争论和试图为自己的选择辩护，而不是理解所提出的批评。

明确地说，代码评审往往非常政治化，可能反映了项目或工作场所中存在的权力动态。你必须非常努力地防止它们变成那样！记住，你应该评审的是想法和实现，而不是利用它来抬高自己的自尊或拆台你可能与之有个人问题的同事。

## 开发环境的一致性

在我 20 多年的软件开发生涯中，我使用过各种不同的开发环境：

- 整个开发团队使用的共享服务器
- 由系统部门维护的虚拟服务器
- 使用 FreeBSD jail[^1] 配置以模拟生产的办公桌 PC
- 使用 Vagrant[^2] 的虚拟机
- 我想在自己的笔记本上安装的任何东西

显然，并非所有这些环境都是最佳的。有时你别无选择——决定是由你无法控制的人做出的。但很明显，让每个人不使用相同的开发环境是导致出现奇怪 bug 的可靠方法。

以测试为中心的文化注重可重复的过程，为人们工作提供易于重建的开发环境绝对值得投入时间。为什么？你在试图消除“在我机器上能运行”这一原因，使其不再成为东西无法工作的原因列表中的一项。

这里的关键是确保每个人都使用相同的构建块。

## 自动化是你的朋友

我花费大量时间推广的另一个概念是使用自动化来帮助你更快地完成任务。如果我发现自己手动做某件事超过几次，这就是一个信号，表明该任务绝对可以从自动化中受益。

在我们拥有 Vagrant 和 Docker 等工具的时代，它们允许我们为代码运行创建环境，为什么你还要依赖人类做重复性任务？计算机在重复执行我们告诉它们的事情方面非常出色。尽可能多地编写脚本是理所当然的。

自动生成开发环境的过程也意味着当开发者不小心搞乱了自己的环境时（我已经记不清这种情况发生过多少次了），你可以快速恢复到已知良好的状态。这让开发者可以自由实验，知道如果犯错也不会有数小时的停机时间。

几乎每种编程语言都有自动化工具，所以你很可能不需要学习另一种语言来帮助构建你的自动化工作。

## 相同的语言和工具

这些问题中最重要的一点可能是确保每个人都使用相同版本的所选编程语言。如果你的所选语言还支持扩展或附加库，也要确保每个人在那里使用相同的库！这看起来似乎很容易做到，但由于每个开发者对此类事情都有自己的个人政策，如果没有严格的程序，几乎不可避免地会出现一些偏差。

这应适用于应用程序的其他互补部分：数据库服务器、缓存服务器、用于压缩和缩小事物的构建工具。这样保持一致也能消除因工具不同版本行为略有不同而导致的奇怪 bug。

我相信始终使用应用程序使用的每个工具的最新稳定版本。这样，你就可以利用任何用于修复错误或修补安全问题的更新。你推迟更新应用程序使用的工具的时间越长，就越可能被入侵或处于将升级到最新稳定版本变成噩梦的境地。不要让它发展到那一步。

## 相同的做法

我觉得这一点极度被低估，并且常常会导致很多摩擦。你可能熟悉编码标准——代码本身在缩进、括号位置、大括号等方面应如何结构化。大多数语言都产生了社区驱动的工具，使其易于强制执行甚至自动应用。

除了代码风格问题之外，你还应专注于确保大家使用相同的编码实践。如果你的首选语言遵循“只有一种方法”的路径，这可能不是问题，但混合过程式、面向对象和函数式实践的语言（如 PHP）会给无聊的程序员提供大量创建难以在未来维护的代码的选择。

选择一些你满意的编码实践，并确保通过代码评审来强制执行。结构和实践的一致性将使你更容易发现出了什么问题，而不是必须进行心理上下文切换来适应他人的风格。

就像测试中心文化所涉及的许多事情一样，你在前期做很多工作以换取未来的巨大收益。

## 信任

最后，我需要和你谈谈信任。当你看看我倡导的实践时，似乎我不信任你去做“正确的事情”，正如所有这些规则所表达的那样：

- 我们评审代码，这样你就能理解其他人都在做什么。
- 我们为一切编写测试，因为你需要对事物正常工作有信心。
- 我们以相同的风格编写代码，这样你在命名事物时摩擦更少。
- 我们使用相同的实践编写代码，这样你调试起来更容易。
- 我们自动化事物，这样你就不会走神并犯下关键错误。

换句话说，我试图让你处于成功的位置！以测试为中心的文化是可以建立的；它只是需要大量的工作，并且需要你（和其他人）改变你一直以来的做法。

2003 年一次糟糕的开发经历和疯狂的加班（比如六周 120 小时）才让我转变并开始做出我认为需要做出的改变，以确保它永远不会再次发生。我努力推动灌输我上面概述的许多实践。其中一些奏效了，一些没有，当我意识到我不会如愿时，我就离开了。

从那以后，我非常努力地在每个地方实施同样的实践，希望信任我的同事认为这些事情与我一样重要。它并不总是奏效，但每当我离开时，我都觉得我已经努力去改变事情。那是我真正想要的全部。

[^1]: FreeBSD jail：https://en.wikipedia.org/wiki/FreeBSD_jail
[^2]: Vagrant：https://vagrantup.com



# 第14章 引导启动

大多数现代 PHP Web 应用程序框架使用前端控制器设计模式[^1]来处理传入请求。这种设计模式的使用也常常伴随着用于“引导”应用程序的代码。

[1] 前端控制器设计模式：https://en.wikipedia.org/wiki/Front_controller

# 14. 引导启动

这是应用程序中你可能正在初始化数据库、设置环境变量或向服务定位器添加内容的区域。简而言之，这项工作对于让应用程序运行至关重要。

自然，你的很多代码都依赖于引导过程中所完成的事情，因此出于测试目的，我们需要创建自己的引导序列。此前版本的 OpenCFP[2] 不得不作为引导序列的一部分做更多的工作，但为了使其更像“Symfony”而进行的大规模重构消除了其中一些问题。

默认情况下，PHPUnit 会在其运行的同目录下查找 phpunit.xml 文件。你可以编写大量测试，并且永远不需要处理这些配置文件。当你确实需要针对应用程序的某些特定内容来帮助测试时，就需要创建和修改这个文件。

对于 OpenCFP，该文件如下所示：

```
<phpunit
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:noNamespaceSchemaLocation="vendor/phpunit/phpunit/phpunit.xsd"
  backupGlobals="false"
  backupStaticAttributes="false"
  bootstrap="vendor/autoload.php"
  colors="true"
  columns="max"
  verbose="true"
  convertErrorsToExceptions="true"
  convertNoticesToExceptions="true"
  convertWarningsToExceptions="true"
  processIsolation="false"
  stopOnFailure="false"
>
  <php>
    <env name="COLUMNS" value="120"/>
    <ini name="memory_limit" value="-1"/>
    <server name="CFP_ENV" value="testing"/>
    <env name="CFP_ENV" value="testing"/>
    <env name="KERNEL_CLASS" value="OpenCFP\Kernel"/>
  </php>
  <filter>
    <whitelist>
      <directory>src</directory>
    </whitelist>
```

[2] OpenCFP：https://github.com/opencfp/opencfp

# 14. 引导启动

```
24. $this->register(new ControllerResolverServiceProvider);
25. $this->register(new DatabaseServiceProvider);
26. $this->register(new ValidatorServiceProvider);
27. $this->register(new TranslationServiceProvider);
28. $this->register(new MonologServiceProvider, [
29.     'monolog.logfile' => $this->config('log.path') ?: "{$basePath}/log/app.log",
30.     'monolog.name' => 'opencfp',
31.     'monolog.level' => strtoupper(
32.         $this->config('log.level') ?: 'debug'
33.     ),
34. ]);
35. $this->register(new SwiftmailerServiceProvider, [
36.     'swiftmailer.options' => [
37.         'host' => $this->config('mail.host'),
38.         'port' => $this->config('mail.port'),
39.         'username' => $this->config('mail.username'),
40.         'password' => $this->config('mail.password'),
41.         'encryption' => $this->config('mail.encryption'),
42.         'auth_mode' => $this->config('mail.auth_mode'),
43.     ],
44. ]);
45.
46. $this->register(new SentryServiceProvider);
47. $this->register(new TwigServiceProvider);
48. $this->register(new HtmlPurifierServiceProvider);
49. $this->register(new SpotServiceProvider);
50. $this->register(new ImageProcessorProvider);
51. $this->register(new ResetEmailerServiceProvider());
52.
53. // Application Services...
54. $this->register(new ApplicationServiceProvider);
55.
56. $this->registerGlobalErrorHandler($this);
57. }
```

当时作为一个 Silex[3] 应用程序，引导过程主要使用一个全局的 Application 对象，然后初始化一系列服务，并让这个全局可用对象了解这些服务。出于测试目的，我们有时需要用自己的值来替换。让我们看看其中一个较旧的测试（针对应用程序的 DashboardController 对象的测试）是如何设置这些内容的。

首先，我们创建 Application 对象并告诉它我们处于测试模式。接下来，我们将应用程序中的 session 对象设置为一个假对象。

[3] Silex：http://silex.sensiolabs.org

## 测试环境引导

```
$app = new Application(BASE_PATH, Environment::testing());
$app['session'] = new Session(new MockFileSessionStorage());
```

喜欢使用测试替身的测试人员有时会忘记可以使用假对象来代替创建桩件或模拟对象。在这个例子中，我们使用的是来自 Symfony 项目的一个假对象。

我们的应用程序使用 Sentry[4] 处理身份验证和授权，所以我需要为这个特定测试创建一个测试替身。

```
1. // Set things up so Sentry believes we're logged in
2. $user = m::mock('StdClass');
3. $user->shouldReceive('id')->andReturn(1);
4. $user->shouldReceive('getId')->andReturn(1);
5. $user->shouldReceive('hasAccess')->with('admin')->andReturn(true);
6. 
7. // Create a test double for Sentry
8. $sentry = m::mock('StdClass');
9. $sentry->shouldReceive('check')->times(3)->andReturn(true);
10. $sentry->shouldReceive('getUser')->andReturn($user);
11. $app['sentry'] = $sentry;
```

仪表板控制器期望存在一个用户资料以及一个与该用户关联的演讲。

```
1. // Create a test double for a talk in profile
2. $talk = m::mock('StdClass');
3. $talk->shouldReceive('title')->andReturn('Test Title');
4. $talk->shouldReceive('id')->andReturn(1);
5. $talk->shouldReceive('type', 'category', 'created_at');
6. 
7. // Create a test double for profile
8. $profile = m::mock('StdClass');
9. $profile->shouldReceive('name')->andReturn('Test User');
10. $profile->shouldReceive(
11. 'photo', 'company', 'twitter', 'airport', 'bio', 'info', 'transportation', 'hotel'
12. );
13. $profile->shouldReceive('talks')->andReturn([$talk]);
14. 
15. $speakerService = m::mock('StdClass');
16. $speakerService->shouldReceive('findProfile')->andReturn($profile);
17. 
18. $app['application.speakers'] = $speakerService;
```

[4] Sentry：https://cartalyst.com/manual/sentry/2.1

# 14. 引导启动

我希望你注意到这里的模式：

- 为现有依赖创建一个替代品
- 告诉 Application 对象使用它

现在我们已经完成了引导，我们实际“运行”应用程序，使用输出缓冲来防止输出干扰测试输出，然后运行我们的测试场景。

```php
1. ob_start();
2. $app->run(); // Fire before handlers... boot...
3. ob_end_clean();
4.
5. // Instantiate the controller and run the indexAction
6. $controller = new \OpenCFP\Http\Controller\DashboardController();
7. $controller->setApplication($app);
8.
9. $response = $controller->showSpeakerProfile();
10. $this->assertContains('Test Title', (string) $response);
11. $this->assertContains('Test User', (string) $response);
```

我知道我展示了很多代码，但请回过头来思考为你的测试创建引导序列的基础：

- 注意应用程序本身设置的依赖
- 为这些依赖创建替代品
- 在测试设置中设置它们

像许多其他情况一样，当你开始为代码编写测试时，通过全局“应用程序”对象简化应用程序构建的设计决策，往往在测试时会带来额外的工作。

## 自动装配引导

上一节中的示例针对的是一个较旧的应用程序，它使用的模式在 2019-2020 年冬季我写这篇文章时所流行的 PHP Web 应用程序框架中也许不太常见。OpenCFP 也在进化，以利用 Symfony 采用的“尽可能多内置功能”的方法。与其为自定义引导序列做所有那些工作（那些我不得不维护的许多行代码），我可以使用应用程序的“内核”来替我完成创建依赖的所有工作。





## 自动装配引导

在 phpunit.xml 文件中，有一个区域可以设置 PHP 能够看到的环境变量。在当前版本的 OpenCFP 中，它看起来像这样：

```
<php>
<env name="COLUMNS" value="120"/>
<ini name="memory_limit" value="-1"/>
<server name="CFP_ENV" value="testing"/>
<env name="CFP_ENV" value="testing"/>
<env name="KERNEL_CLASS" value="OpenCFP\Kernel"/>
</php>
```

所以，为了利用我只能形容为“自动装配引导”的特性，我们通过 KERNEL_CLASS 设置一个环境变量，指向我们的自定义 Symfony 内核。该变量由 symfony/framework-bundle 包提供的基础测试用例对象所使用。如果我通过继承这个基础测试用例对象来创建其他测试对象，幕后的一些魔法就会运行我自定义内核中的所有代码，这意味着我应该能够访问被测代码所期望的几乎所有内容。

这意味着我的测试不必像旧的测试引导那样显式地完成所有工作。这确实意味着可能会创建一些我的特定测试不需要的依赖项，但我将不必维护多个引导和初始化部分（它们之间通常只有细微差别）视为一种额外的好处。

选择使用 Web 应用框架的原因之一，就是利用那些为解决程序员常见问题而创建的工具。如果框架为你提供了让编写测试更轻松的工具，那就使用它们！Symfony 的内核允许你减少所做的引导工作量，而为测试基于 Laravel 的应用在运行时修改门面的能力也浮现在我的脑海中。

# 第15章：没有测试？没问题！

大多数 PHP 应用的默认状态是没有自动化测试。在过去，谈到这一点时，我会开始谈论缺乏专业精神，甚至将其表述为道德上的失败。当然，这是一种很糟糕的处世方式。相反，更好的做法是专注于如何从没有测试到至少有一个测试，并希望能朝着拥有更多测试的方向前进。

## 我们最终怎么会沦落到没有测试的境地？

有两个主要力量导致应用没有任何测试。第一个是，很难教一门语言的初学者如何使用测试工具；他们还在学习语言本身！既然测试是以特定方式、用特定工具编写的代码，那么人们难以独自搞定这一切也就不足为奇了。测试只是展示如何使用其他代码的代码；这对初学者来说是一个非常抽象的概念。别担心，你会做到的。

第二个力量是工作文化的压力，声称你没有时间写测试。我曾因不断被告知这一点而辞职。当然，那个代码库充满了 bug，而且难以调试。这种对待测试的态度之所以如此有害，其中一个原因是，你最终花在修复生产环境中出现的 bug 上的时间，比如果“被允许”编写测试要多得多。现在有大量实际研究证明了在开发过程中为应用编写测试的价值。用你最喜欢的搜索引擎搜索“TDD 研究”。你会对找到的结果感到惊讶。

暂且把这些放在一边，你现在已经决定要为你的应用编写测试了。太好了！我想分享一些对我自己和其他人都行之有效的策略。

## Bug 修复需要证明

一个对我自己和其他人都行之有效的策略是实施一项政策，要求所有 bug 修复都必须有一个或多个可自动化的测试，以证明 bug 确实被修复了。这个过程通常类似于以下步骤：

首先，一个 bug 被报告，有人验证所报告的问题确实是一个 bug。有时，它只是一个意外的结果，或是对用户体验的抱怨。我们都知道，“它坏了！”并不总是 bug 报告，而常常是一种沮丧的表达。

在掌握了存在待修复 bug 的证据后，下一步应该是编写一个假设该 bug 不存在的测试。使用 bug 发生的条件，你创建一个假设（像所有测试一样）一切正常工作的测试。这个测试应该因为 bug 而失败！然后你继续正常的 TDD 周期，在修改代码时重新运行测试，直到测试通过。

现在你有了一个测试，证明这个 bug 不再存在！同时，希望你没有破坏应用其他部分的东西。如果发生了这种情况，你编写另一个测试来验证这个新问题（技术术语叫回归）已修复，然后验证你为最初的 bug 修复编写的测试仍然通过。测试套件是你对抗代码回归的头号武器；你可不想在做出更改时总是破坏旧代码！

## 新功能需要证明

另一种测试策略是要求所有新功能都有测试，以证明新功能按预期工作。这与“bug 修复”策略的不同之处在于，你通常最终会编写多个测试来证明新功能正常工作。正是在这种策略中，你才能看到 TDD 作为设计易于测试代码的工具的力量。

那么你该怎么做呢？你需要首先决定如何在代码层面证明该功能正在工作。你是否需要一个带有新方法并返回特定值的新对象？你是否在使用现有代码？是的，你可能需要事先做一些工作，来弄清楚如何让这个新功能工作。但这正是 TDD 的闪光点！

下一步是编写一个测试，假设新的或修改后的代码能正常工作。当然，测试会失败！同样，就像你在处理验证 bug 修复的测试时一样，你不断编写代码并运行测试，直到它们全部通过。现在你有一个或多个测试，在代码层面验证这个新功能按预期工作。

此外，就像 bug 修复策略一样，这些更改很有可能在代码库的其他地方导致回归。请务必在已被视为关键的领域，使用应用本身进行一些彻底的检查。

## 测试套件并非万无一失

在这一点上，你开始拥有一个测试套件，它覆盖了应用的一部分，并有助于提供有限的回归保护。小心不要被任何数量的通过测试引诱到虚假的安全感中。毕竟，这些测试是由人类编写的，而不是由旨在将我们引向丰饶之地、过上悠闲生活的超级智能 AI 编写的。

测试只覆盖编写者在编写时能想到的场景。是的，完全有可能拥有一个 100% 覆盖代码的测试套件（意味着应用中的每一行代码都在测试中执行过），但应用仍然无法正常工作。

你需要各种各样的测试——针对单个对象的单元测试，验证这些对象正确交互的集成测试，以及一些功能测试（也许手动完成），以确保应用正常工作。

覆盖率高的测试套件让你能够专注于解决问题，并有一定信心不会在现有系统中引入新的 bug。

现在，出去开始构建那些测试套件吧！

# 第16章：没有人运行测试！

## 时间压力

“我们当时急于完成一堆功能，继续写测试拖慢了我们的速度，所以我们停了下来。”啊，是的，时间，开发者梦想的杀手。它是唯一我们永远无法创造更多的东西。

鉴于我经历过的各种开发冲刺，你极有可能花在修复非正常工作条件所引入 bug 上的时间，比继续以 TDD 倡导的稳扎稳打节奏前进要多得多。

能做些什么来帮助解决这个问题呢？坚定地承诺持续使用测试，作为验证代码按预期工作的一种方式，即使面对利益相关者的恐吓或威胁。

我意识到这并不容易。当我坚持认为测试是开发者工作流程中不容协商的一部分时，我曾被一些人指责为鲁莽。“我要是这么建议会被解雇的！”

那不是我的本意！我的意图是提出这样一个论点：为了赶截止日期而进行某种疯狂加班，最终会比采用更有分寸的节奏在代码中造成更多错误。

## 测试太慢

测试套件应该运行得快；更快的运行意味着更快的反馈和更多实际编写代码的时间。我曾参与过运行测试套件需要一小时以上的项目。在这种情况下，没有人是赢家。人们会不愿意将运行测试套件作为日常工作流程的一部分。

想象一下这样的过程：

- 开发者在开发新功能时编写测试
- 开发者运行该功能的测试，直到全部通过
- 然后开发者运行整个测试套件，以确保没有破坏其他东西

到第三步时，你有多少次会说：“算了吧，我可不想在这儿坐一个小时。”这就是缓慢的测试如何毁掉你在测试套件其他部分所做的一切努力。

什么样的条件会导致非常慢的测试套件？

我在寻找一种能准确表达我想法的方式上费了一番功夫。我的许多测试布道同行都不喜欢使用测试替身的想法。他们抱怨需要在测试中编写大量额外代码，抱怨替身是多么容易……


与它们所代表的依赖关系失去同步，依赖测试替身（doubles）的测试整体上“脆弱”，以及其它一些不值得在此赘述的抱怨。

他们的解决方案是创建伪造对象（fakes，即伪装的测试替身），或者尽可能使用真实依赖。我并不真正反对这种技术——使用真实依赖是件好事！

拒绝使用测试替身的副作用是，你会开始承受我称之为“外部参与者”成本。每当测试与真实数据库或真实 Web 服务交互时，它们都会额外消耗一点点时间（有时还有额外内存）。当你的测试套件规模还小时，这更像一个减速带。一旦你的测试套件开始覆盖大型应用程序的大部分，你就会注意到这个问题。

此时，你可能会感到纠结。一方面，你想确保应用有足够的测试覆盖率，以便捕捉回归缺陷，并让你更容易编写新代码。另一方面，你又希望测试套件快如闪电，让开发者不必干等着测试跑完。

### 单体式启动引导

大多数 Web 应用框架都围绕前端控制器[1]设计模式构建。使用这种模式的一部分，还有一个在请求处理之前发生的引导序列。通常，这里面要做很多事情，这意味着你在 Arrange-Act-Assert[2] 测试模式的“arrange（准备）”阶段要做大量工作。当然，测试也有测试的模式；开发者并不是唯一能享受模式乐趣的人。

我们能做什么？嗯，我发现的一个方法是，将你的引导序列从一个做大量工作的单体方法，拆分成一个较小的方法，让它调用一系列完成所有引导工作的小方法。这样你就更容易弄清楚，对于你要测试的代码来说，引导序列中的哪些部分是绝对必要的。

### 共享测试环境

这已经不是过去的问题了，这要归功于虚拟机和容器等技术的快速普及。这些工具可以用来在你自己的计算机上复制你的代码可能运行的环境。我在 2017 年初从一台 2012 年中期的 MacBook Air 升级到 2016 年末的 MacBook Pro（没错，就是带酷炫触控条的那款），因为我发现自己总是因为所需现代开发环境的要求而资源耗尽。

[1] 前端控制器：https://en.wikipedia.org/wiki/Front_controller
[2] Arrange-Act-Assert：http://wiki.c2.com/?ArrangeActAssert

# 16. 没有人运行测试！

那么，当有了共享开发环境会发生什么呢：

- 项目上的所有开发者都做自己的工作，也许会运行个别测试
- 到了某个时间点，他们需要合并自己的工作并运行整个测试套件
- 共享环境因负载而崩溃
- 测试套件由于共享资源（如数据库）上的竞争条件而随机崩溃

是的，我经历过。最终你会陷入一个可怕的循环：人们直到最后一刻才运行测试，因为当大家在最后一刻都试图运行测试时，共享环境就会崩溃。这种情况几乎永远持续下去，直到有足够多的人离职，使得共享环境上的负载不再重要，或者有人花大量时间学习 Vagrant[^3] 或 Docker[^4]，并强迫所有人切换。

[^3]: Vagrant：https://vagrantup.com
[^4]: Docker：https://docker.com

# 第 17 章

# “你拿钱不是为了测试！”

很多次，我听到在代理商或自由职业者工作的人说，每当提到测试这个话题，他们就会遇到很多阻力。你对我说：“我很难让客户相信测试的价值。”我完全理解。我经常被告知：“克里斯，客户看到发票上有测试这一项，就会开始抱怨！”

# 17. “你拿钱不是为了测试！”

你能对此做些什么？我想和你分享一些我认为可能有帮助的策略。

## 测试就是工作的一部分

我们已经过了那个可以理直气壮地说写代码的人没有责任测试代码的时代。即使你没有使用自动化测试，你仍然在测试你所做的东西！你有没有在提交的发票上把“浏览器中的测试”列为一项？恐怕你得原谅我对当前客户开票惯例的无知，但这在我看来实在是太不可能了。

我没有那么激进，不会告诉你“不写测试就不是专业人士”，因为那个时代早已过去。底线是，你需要为你为他人所做的工作提供某种可重复的测试。

如果你可以使用一个并非公司内部发明的 Web 应用框架，那么你很可能正在使用一些带有自动化测试的工具。但是，你“不被允许”为你做的其他事情写测试吗？

所以我的建议是，写测试，并把它们作为你正在做的工作的一部分。如果被问及，你只能这样回答：“测试是我交付的一部分，所以在我不再参与之后，它不会出问题。”我知道你会遇到一些非常咄咄逼人的客户，他们会宣称你理应交付无缺陷的产品。我无法想出任何办法来减少出现的缺陷数量，除了确保你有测试来验证一切按预期工作。

## 错失的机会成本

这个话题已成为我个人最喜欢的，因为它对非技术型人群来说非常有共鸣。它重点指出：带着缺陷进入生产的 bug 实际上会花费你的金钱。其原理如下。

一个开发者正在开发一个新功能。如果他们发现了一个缺陷，现在是修复它的最便宜时机——而拥有自动化测试来验证一切正常是一个好方法。但他们没有测试，所以他们只能尽力而为。尽管尽了最大努力，他们还是制造了一个缺陷。

下一步是让同事通过审查来检查他们的代码。如果审查者发现了一个缺陷，那么我们勇敢的开发者就必须回去修复它。这会花费时间和金钱。一旦他们认为自己修复了问题，代码就必须再次交给审查者。在这种情况下，审查者给他们竖起大拇指，代码就可以进入 QA 阶段。

## 错失的机会成本

但如果有测试呢？我敢打赌，引入的缺陷很可能在代码到达审查者之前就被发现。审查很可能进行得更顺利，花费更少的时间和资源。

现在，如果 QA 在人工测试中发现缺陷，那么修复它的成本现在就明显更高了。想想现在的流程是：

- 开发者实现功能，未发现缺陷
- 代码被审查，未发现缺陷
- QA 发现缺陷
- 开发者回去修复缺陷（希望如此）
- 代码被审查，未发现缺陷
- QA 未发现缺陷

这多出了三个步骤，而这些步骤在时间和/或金钱方面并不免费（我不能再强调这一点了）。

假设代码一路进入生产环境，然后客户发现了一个缺陷。修复它的成本也许很便宜：

- 开发者实现功能，未发现缺陷
- 代码被审查，未发现缺陷
- QA 未发现缺陷
- 客户发现缺陷
- 开发者回去修复缺陷（希望如此）
- 代码被审查，未发现缺陷
- QA 未发现缺陷
- 客户未发现缺陷

那总共是八个步骤，但有时候有些缺陷真的非常昂贵。它们可能花费你相当于开发者时间成本十倍的钱。甚至可能毁掉你的公司。幸运的是，在我的职业生涯中，只有一次我把带有严重缺陷的代码发布到生产环境，导致整个应用被关闭。那可不是一次愉快的经历。

所以，缺乏测试不仅会随着缺陷出现在流程中更昂贵的环节而让你花费更多钱去修复，而且不得不回头修复这些缺陷实际上也会让你错过其他工作。



# 17. “你不是为了测试而拿薪水！”

新功能怎么办？不行——在修 bug。回头重构一些代码以使用新库呢？不行——在修 bug。给客户做一些定制工作呢？不行——在修 bug。

我想你已经开始看出这里的共同点了。

要求开发者编写可自动化的测试的价值在于，你更有可能在 bug 进入生产环境之前就发现它们。这是测试的最终目标——迅速将代码从开发者的环境中移出并投入生产，在那里它能够实现应用的目标。

# 18. 这关乎人

我请了一些实际做测试的开发者给我一些想法或问题，以便我可以回应。

## 像操场上的孩子

> “开发团队在测试方面往往像个婴儿；他们需要来自上层的推动才会开始做。例如，如果一个家长不希望自己的孩子吃泥土但什么也没说，而操场上的其他孩子也没说什么，那么一个小孩子告诉那个孩子不要吃并告诉其他孩子不要吃也没用。他们只会被认为‘爱管闲事’和‘烦人’，然后被要求‘冷静点’。”

这是一个很好的例子，说明改变需要来自上层并得到更接近开发团队的人的强化。说实话；大多数人只会做完成工作所需的最低限度。在我惹大家生气之前，请不要给我发邮件举例说明你们的高效团队如何拥抱测试。你的团队是异类；要知足。

那么可以做些什么来改善这种情况呢？这需要付出大量努力，既要将代码测试作为政策实施，也要保持他们持续执行。要求人们为自己的代码编写某种可重复的测试是合理的。许多人认为这种事情是成为程序员的基本最低要求。

要坚定，并将以测试为中心的政策作为开发工作流程中不可协商的一部分。许多开发者在面对测试驱动开发时都会本能地抗拒改变。引导他们并帮助他们理解，TDD 和测试实践很快就会像他们以前不理解但现在已拥抱的其他编程技术一样自然。

## 缺乏好的文档

> “其他原因更有趣。其中一个是 perceived 缺乏好的文档。例如，大多数关于单元测试的文档使用简单的例子，这对于理解概念是可以的，但缺乏实际应用。一些开发者实际上想使用 TDD，但他们担心项目测试起来太难，因为关于如何测试复杂系统的良好文档并不多。”

多年来我一直在努力寻找对此的良好方法。确实如此——大多数关于如何编写单元测试的示例都极其简单。提供更复杂答案会很困难，因为每个人的代码库都略有不同并带来独特挑战。例如，我多次提到的项目 OpenCFP 有一个约束，即需要始终考虑一个全局应用对象，其中包含需要被覆盖和重新定义的部分，以便测试应用的部分。除非你理解你的测试旨在做很多与你的应用应该做的事情类似的事情，否则很难直观地知道这一点。

这触及了教人测试的最大问题的核心。几乎不可能给人们提供关于他们应该做什么的通用建议！当然，我们可以看看一些指导原则，比如 Arrange-Act-Assert[^1] 或鼓励人们不要滥用测试替身，但这还不够。

讽刺的是，尽管我们可以通过互联网获取大量信息，但教人单元测试的最好方式实际上是坐下来与某人一起指导他们完成任务。

## 说服人们关于时间

> “我的团队正在考虑将单元测试整合到我们的开发流程中。到目前为止，我们只是在一个相当小的原型环境中进行了实验。理论上，我完全同意你的观点，但在实践中，我还没有看到好处。编写这些测试确实花费了我们时间。我想知道这真的值得吗。至少感觉很慢，因为你最终会花一半的时间编写测试。你真的能把这段时间找回来吗？”

这是一个完全公平的问题：我从编写测试所花费的时间中会看到好处吗？我 pretty sure 你知道我的看法是什么，但让我们更深入地探讨这个问题。

这位人士正确地指出了编写测试需要时间。毕竟，你花费时间思考如何测试某物。然后你必须花费时间编写测试并在编写它们时迭代测试，并确保你覆盖了所有分支和条件，那所有时间都去哪了？！

那段时间花在了你对你试图解决的问题更加审慎和深思熟虑上！你花费时间编写的那些测试是为了确保你没有意外破坏其他东西。它们也存在于下一次代码在其他地方被更改并因此而破坏时。除了你会在实际编码工作中发现它，而不是在漫长的一天结束时当你的注意力不应该如此时，也许你累了想回家。

我觉得有必要回到“机会成本损失”的想法。想法是 TDD 的使用将导致进入生产环境的 bug 更少。这意味着你就可以继续进行其他任务，比如新功能或对关键子系统的急需重构。

更不用说使以信心修改现有代码变得更容易的有益副作用了。为什么？测试会让你知道你是否破坏了某些东西！这使我们能够继续向前推进的循环，而不是感觉你处于永久的紧急 bug 修复状态。

## 我上司是牛仔程序员

> “当你的老板是牛仔程序员时，你如何推销测试？”

有段时间，当有人抱怨工作或糟糕流程时，我的反应是立刻说，“好吧，你应该辞职！”多年来我对这个问题软化了立场，但我认为这种情况确实是应该这样做的。

基本上，你不想为这样的人工作。除非你真的不在乎自己在做什么。在这种情况下，你也应该辞职。

这不是关于专业精神或软件工艺。这关乎理解在一个你不被鼓励对自己正在做的工作深思熟虑——并且被阻止使用导致可重复成功工具和实践的环境是 toxic 的。

我多年来曾在足够多的有毒环境中工作过，它们都有很多共同点。学会识别当你工作的地方会阻碍你而不是让你作为程序员和作为个人成长时。

就像我说的，测试真的关乎人。

[^1]: Arrange-Act-Assert: http://wiki.c2.com/?ArrangeActAssert

# 索引

- A
  - API, 31, 41, 74, 77–80, 82, 90, 93
    - 构建, 78
    - 调用, 12
    - 公开可用, 74
    - 模式验证, 77, 79, 81
    - 测试, 73–74, 76, 78, 80, 82
    - 第三方, 89
  - 应用
    - 遗留, 109
    - 真实世界, 136
  - 自动化, 7, 12, 99, 111
    - 浏览器, 96
- B
  - Behat, 96
  - 行为驱动开发, 96
  - Beizer, Boris, 5
  - Bergmann, Sebastian, 16, 18–20, 22–23, 71–72, 76–77, 81–82, 91–92, 94
  - 启动, 115–18, 120, 129
    - 序列, 116, 120, 129
    - 测试环境, 117, 119
  - bug
    - 生产, 97–98
    - 测试, 108–9
    - 类型相关, 101–2
- C
  - CircleCI, 99
  - 代码
    - 覆盖率, 100–101
    - 剪切粘贴, 12
    - 重复, 87
    - 语法检查器, 99
    - 变异, 104
    - 重构, 53
    - 发布, 133
    - 评审, 98
    - 风格问题, 112
    - 可测试, 73
    - 类型提示, 40
  - Codeception, 96
  - Composer, 17, 71, 79, 99–100
    - 已安装, 17
  - 构造函数, 27–28, 32, 37
    - 参数, 28, 90
  - 控制器, 115, 120, 129
    - 前端, 129
  - 覆盖率, 6, 101, 109, 125
- D
  - 数据库
    - 初始化, 116
    - 内存中, 63
    - 迁移, 11, 99




## Q
- 质量保证 (QA), 98, 132–33

## R
- 重构, 28, 49, 51, 53, 98, 100, 110, 134

## S
- Scryfall, 74
- 服务器, 12, 77, 99
  - 缓存, 112
  - 持续集成, 12
  - 网页, 97
- 服务
  - 远程, 77
  - 网页, 129
- Silex, 118
- Speccy, 78–79
- 间谍, 28, 33, 40
- Sturgeon, Phil, 78
- Swagger, 78
- Symfony, 80, 117, 121

## T
- TDD (测试驱动开发), 3, 10, 41–42, 44, 46, 48, 50, 52, 54, 56–57, 59, 97, 100, 109–10, 136
  - 研究, 124
- TeamCity, 71–72, 76–77, 81–82, 91–92, 94
- 测试
  - 自动化, 12, 98, 123, 132
  - 替身, 11–12, 25–26, 28, 30, 32, 34, 36, 38, 40, 44, 63, 70, 119, 128–29
  - 集成, 7, 125
- 间谍, 28–29, 31, 33–35
- 套件, 6, 10, 16, 124–25, 128
- 单元, 2, 7, 71, 79, 89, 91, 109, 125, 136–37
- 测试用例
  - 高级, 44
  - 基础, 21
  - 通过, 19
- 工具
  - 自动化, 99, 112
  - 代码生成, 77
  - 静态分析, 101–2
  - 测试, 77, 96, 104, 124
- Task, Matthew, 78
- Travis CI, 99
- Twig, 102

## V
- Vagrant, 111, 130
  - 学习时间, 130

## W
- 工作文化压力, 124

## X
- XDebug, 100

# 反馈与更新
请告诉我们您对本书的看法！您喜欢什么？什么地方令人困惑或可以改进？您是否发现了勘误？您对本书的任何反馈和想法都将帮助我们改进未来的版本。

如需留下评论，请访问 https://phpa.me/grumpy-testing-book

## 跟随作者
Chris Hartjes 在 twitter 上活跃，@grmpyprogrammer，并分享他在测试和编程方面的经验、教训和建议。

## 更新
如需保持联系并获知本书未来版本的通知，请访问 http://phparch.com 并订阅我们的（低频率）邮件列表。

您也可以在 twitter 上关注我们 @phparch，以及在 facebook 上关注我们：https://facebook.com/phparch/

## php[architect] 书籍
php[architect] 系列书籍涵盖与现代 PHP 编程相关的主题。我们的大多数书籍均提供印刷版和数字版。印刷版价格包含运往美国的免费配送。数字版书籍以 DRM-free 的 PDF、ePub 或 Mobi 格式提供，可在支持这些格式的任何设备上阅读。

如需查看完整的书籍选集并订购自己的副本，请访问：
http://phparch.com/books/.

- **Fizz Buzz 修复：像经验丰富的开发者一样思考的秘诀**
  - 由 Edward Barnard
  - ISBN: 978-1940111759
- **开发主管的战壕：管理开发人员的经验教训**
  - 由 Chris Tankersley
  - ISBN: 978-1940111711
- **使用 PHP 进行网页抓取，第二版**
  - 由 Matthew Turland
  - ISBN: 978-1940111674
- **PHP 应用的安全原则**
  - 由 Eric Mann
  - ISBN: 978-1940111612
- **面向开发者的 Docker，第二版**
  - 由 Chris Tankersley
  - ISBN: 978-1940111568 (印刷版)
- **下一步？职业发展建议**
  - 由 Oscar Merida 编辑
  - ISBN: 978-1940111513
- **PHP 中的函数式编程，第二版**
  - 由： Simon Holywell
  - ISBN: 978-1940111469
- **Web 安全 2016**
  - 由 Oscar Merida 编辑
  - ISBN: 978-1940111414
- **使用 WordPress & Thesis 构建卓越网站**
  - 由 Peter MacIntyre
  - ISBN: 978-1940111315
- **使用 OAuth 和 PHP 集成 Web 服务**
  - 由 Matthew Frost
  - ISBN: 978-1940111261
- **Zend Framework 1 到 2 迁移指南**
  - 由 Bart McLeod
  - ISBN: 978-1940111216
- **使用 PHP 解析 XML**
  - 由 John M. Stokes
  - ISBN: 978-1940111162
- **Zend PHP 5 认证学习指南，第三版**
  - 由 Davey Shafik 与 Ben Ramsey
  - ISBN: 978-1940111100
- **精通 SPL 库**
  - 由 Joshua Thijssen
  - ISBN: 978-1940111001

