# PHP 互补测试工具秘籍
















由  
Chris Hartjes 撰写

由  
PHP Architect, LLC. 出版  
9245 Twin Trails Dr #720503  
San Diego, CA 92129 美国

编辑  
Kara Ferguson

版式设计  
John Congdon

406-PHP-ARCH (406-747-2724)  
info@phparch.com  
www.phparch.com



# Marco Pivetta 的序言

（Marco 是开源 PHP 项目长期且高产的贡献者。我有幸与 Marco 合作多年，几乎每次进行代码审查或围绕软件开发展开讨论时，我都能学到如何更好地做事。我请他审阅了这本书，并回顾我们在相识这十年间在 PHP 开发社区中看到的变迁。）

我与这位“愤世嫉俗的程序员” Chris 相识已近十年：他在团队应如何控制软件复杂度和稳定性方面与我们拥有大部分相同的观点。

他在软件测试、自动化工具以及整体改善开发者状况方面拥有长达数十年的职业生涯，其所取得的成就正在对行业产生影响：十年前，在 PHP 生态系统中，测试往往受到怀疑，有时甚至遭到嫌弃，被视为“一项昂贵的练习”。

曾经充满怀疑的地方，如今在各个层面都清晰地展现出对测试的兴趣，讨论的焦点也从“我应该写测试吗？”转变为“什么是最好的测试技术？”。

整个社区显然已经采纳了软件测试，既然你在读这本书，可能你也是如此。

下一步在于理解我们的测试是否良好，是否验证了我们项目中所有重要的细节，以及我们编写的代码是否切中要点。我们希望避免无用的复杂性，拥抱简洁，并提高我们工作的表达力，从而造福于我们自己和同事。

作为一名代码质量倡导者，我建议你尝试一下下一章中介绍的工具和技术，并将它们据为己有。

你将了解到我将其纳入日常工作的一部分的实践，它们将对你编写软件的方式产生深远影响。

通过混合和利用这些工具，你或许能够找到自己在代码质量方面的舒适区，并掌握说服他人认可其价值的必要知识。

# 第 1 章：入门

## 目标读者

向刚学编程的人解释测试这一主题很难。“我要写代码来测试我自己写的其他代码？那看起来太难了！”我尚未见过任何教程教程序员如何从以测试为中心的立场来使用编程语言。

鉴于此，我为那些已有编写测试经验但希望进一步提升的 PHP 程序员写了这本书。自 2005 年以来，我一直从事这一工作，并不断经历学习新事物和强化旧习惯的过程，这些都能带来更好的结果。

我的书《愤世嫉俗的程序员测试 PHP 应用程序指南》（可通过 LeanPub[1] 或 php|architect[2] 获取）详细阐述了你需要学习（并希望精通）的基本技术技能，以让你的测试有效，并使编写测试变成一种常规操作，而非常态事件。

- [1] https://leanpub.com/grumpy-guide
- [2] https://phpa.me/grumpy-testing-book

在整本书中，我将展示如何为我最古老的仍在使用的基于 PHP 的 Web 应用程序添加有针对性的测试覆盖。该应用程序自 2004 年运行至今，我每隔几年更新一次基础框架（CakePHP[3]）。

## 为什么要付出这些努力？

该应用程序最初是一个 PHP 5 代码库，并在随后的几年中不断更新。它目前在 PHP 7.4 上运行良好，并希望很快能在 PHP 8.0 上运行。在软件行业的当前阶段，长时间维护一个应用程序是非常罕见的。从零开始构建某样东西所需的技能集，与维护现有代码库所需的技能集截然不同！我相信，越来越多的开发者理解了这一点，从而促成了多种语言中这些强大工具的涌现，使测试和代码分析变得更加容易。

毕竟，如果你构建某样东西并在部署后不再触碰它，那么你可能不需要自动化测试、代码检查和静态代码分析。然而，如果你正在构建某个将成为业务或项目长期核心的东西，那么探索自动化测试、代码检查和静态代码分析以了解它们如何帮助你，是值得的。

## 该应用程序

该应用程序本身是一个为联盟设计的网站，该联盟使用桌面棒球模拟游戏来打出一个完整赛季，并使用由现有美国职业棒球大联盟球队球员组成的阵容。我们自行制作该游戏并免费分发给联盟成员和其他感兴趣的方。

在验证应用程序是否按预期工作时，一些可以通过视觉确认的事项包括：

- 联盟排名
- 赛程安排
- 各队将使用的投手轮值
- 伤病情况

为了表述清晰——了解棒球运动并非理解我在本书中采用的方法的必要条件！它确实有帮助，但我想要强调的关键点是，如果没有关于你试图解决的问题的一些领域知识，你创建的测试可能毫无影响。

- [3] https://cakephp.org




## 应用背景

出于各种各样的原因，主要与“原型直接转正”这一概念有关，我们没有测试覆盖率。通常来说，对于任何人们频繁使用的网站，这都是一个巨大的问题。但我对于我们要解决的问题而言是一位“领域专家”。这让我可以非常省事地走捷径，并通过视觉验证来确保一切按预期工作。

很有可能，如果你加入一个项目并需要维护一个长期运行的遗留应用程序，你并不具备对应用程序代码及其所解决问题同等的认知深度。凭借我的专业知识，我可以跳过一整套将各种页面输出与基线进行比较的自动化测试。在做出小改动后手动重新加载页面并不是一种很好的实践。但即便如此，在此时，编写一系列自动化测试也不太可能给我们提供对所需部署的充分信心。也不太可能有其他开发者加入这个“团队”来处理它。我知道足够的知识，可以视觉确认事物是否按预期工作。

还是没有测试吗？是的，令我深感羞愧的是，这是一个现在必须纠正的巨大疏漏。每年当我们调整网站以适应即将到来的季节时，总有几处功能会损坏。因为我知道**一切**都应该如何工作，所以这些修复都是快速的改动。如果能到达这样一个阶段——所有损坏的地方都在我将更改推送到生产环境之前被发现——那就太好了。

鉴于某些类型的测试可能帮不上忙，我为什么要费心去添加自动化测试呢？正是因为领域知识常常让我忘记检查所有功能是否都正常工作，而只是通过视觉检查我更改的那一项。

通过添加覆盖那些在生产环境中部署更新代码时必须正常工作的功能的测试，我试图改变以下循环：

- 在本地进行更改
- 不完美地测试本地更改
- 将更改推送到生产环境
- 收到人们发来的“某处坏了”的邮件

在这里失败的代价相当低——这是一个支持爱好的网站。我感受到的任何紧迫感都是我自己制造的；很有可能你自己的情况大不相同。你网络应用程序中的错误或意外行为可能会导致金钱损失、失业，甚至损害其背后的业务。

我坚信让计算机为你执行可重复的任务。作为人类，我们会犯错。我们会跳过步骤。我们会假设事物的状态。计算机只会遵循我们给它的指令。希望这些指令符合我们认为事物应该如何表现的方式。

## 1. 入门

### 我们的工具

使用自动化工具通常就像团队里有另一个人不知疲倦地检查你的工作是否有错误，并建议更改什么。谁不想要这样的帮助呢？

截至本文撰写之时（2021 年春夏），我安装了以下工具；它们在本书中贯穿使用：

- PHP 7.4 和 PHP 8.0
- PHPStan 0.12.85
- Infection 0.21.0
- PHPUnit 8.5.1
- PostgreSQL 9.6

我在 macOS Big Sur 11.3 上进行这项工作，并使用 Homebrew¹ 安装了大部分我需要的依赖项。

我还在使用 PhpStorm² 作为我的编辑器，它与所有三个以测试为中心的工具都有很好的集成，此外还安装了 PHP Extended Inspections³ 扩展，该扩展提供大量的重构建议以及关于未初始化变量等问题的提醒。

在继续之前，我想提醒你，我选择工具只是我个人的选择。对于我正在使用的每一种工具，都有许多其他选项，而我坚信不要使用给你带来摩擦的工具。如果你想使用 PHPStan⁴ 进行静态代码分析，尽管去做！如果你想跳过变异测试，那也没问题。不喜欢 PHPUnit 的语法，想用类似 Pest⁵ 的东西？尽管去用。

重点在于开始整合使用那些与以测试为中心的实践互补的工具。你选择工具并不会改变你必须做的事情，但它会影响你对待这些事项的方式。

¹ https://brew.sh/  
² https://www.jetbrains.com/phpstorm  
³ https://phpa.me/php-inspections-extended  
⁴ https://phpstan.org  
⁵ https://pestphp.com  

### 初始设置

本书还假设你正在使用我认为永远改变了 PHP 开发的工具：Composer⁶。如果你不熟悉它，它是一个用于安装 PHP 包的命令行接口工具。在 2021 年，你很难找到一个不使用 Composer 的主要 PHP 库或框架。

我正在使用的一些工具需要你在开始使用之前进行一些配置工作。

⁶ https://getcomposer.org

### PHPStan

PHPStan 的文档可以在 https://phpstan.org 找到。

PHPStan 可以在没有默认配置文件的情况下使用——你只需要通过 CLI 传递信息给它。为了降低认知负荷，我将直接创建一个默认的 `phpstan.neon` 文件：

```
parameters:
    level: max
    paths:
        - src
        - tests
```

### Infection

Infection 的文档可以在 https://infection.github.io 找到。

我选择使用 PHIVE⁷ 安装 Infection，因为我遇到了一些无法妥善解决的 Composer 问题。

⁷ https://phar.io/

首次运行 CLI 工具时，你会收到类似的消息（部分输出已省略）。

```
1. > infection.phar
2.
3.    Welcome to the Infection config generator
4.
5.
6.
7.    We did not find a configuration file. The following questions will help us
    to generate it for you.
8.
9.
10.    Which source directories do you want to include (comma separated)? [src]:
11.    [0] bin
    [1] config
    [2] lib
    [3] logs
    [4] plugins
    [5] src
    [6] templates
    [7] tests
    [8] tmp
    [9] vendor
    [10] webroot
12.    > 6,7
13.
14.    Configuration file "infection.json.dist" was created.
```

我针对此工具的配置文件采用与 PHPStan 相同的策略。这是默认配置文件。我将在书中第一次使用它时解释如何调整它。

```
{
    "source": {
        "directories": [
            "src",
            "templates"
        ]
    },
    "mutators": {
        "@default": true
    }
}
```

## 2. 静态代码分析工具

### 它是什么？

我喜欢通过分享来自可靠来源的定义来介绍编程概念。在这种情况下，来源是维基百科：

> 静态程序分析是对计算机软件在不实际执行程序的情况下进行的分析，这与动态分析相对，动态分析是在程序执行期间进行的分析。在大多数情况下，分析是对源代码的某个版本进行的，在其他情况下，则是针对目标代码的某种形式。

当我最初开始研究静态分析时，令我着迷的是“在不实际执行程序的情况下”这一部分。大约十年前，我尝试创建自己的工具，对 PHP 代码进行静态分析，以确定测试所需的依赖项和语言结构。这很快让我掉进了一个理解如何解析 PHP 标记和抽象语法树的兔子洞里。

最终，我发现写书和做演讲来教人们做我的简陋工具试图自动完成的事情更容易。

在这本书中，我使用 PHPStan⁸，但我也曾使用过 Psalm⁹ 达到相同的目的。我知道的其他选项包括 phan¹⁰ 和 exakat¹¹。然而，PHPStan 和 Psalm 绝对是 PHP 领域中“市场份额”最大的两个工具。

作为一个简短的总结，并将本章其余部分的焦点集中起来：静态代码分析提供了一种测试代码而无需运行它的方法。静态分析工具可以查看你的 PHP 代码，并根据与你的变量、函数和类相关的类型推断出它应该如何工作。它可以突出显示你是否可能传递了类型含糊的参数，你是否以意外方式调用函数，识别永远不会执行的代码区域，等等。随着 PHP 的成熟并添加了类型提示和严格模式等功能，静态分析工具可以帮你更好地理解应用程序代码并提供更有用的反馈。

⁸ https://phpstan.org  
⁹ https://psalm.dev  
¹⁰ https://github.com/phan/phan  
¹¹ https://exakat.io

### 我为什么要使用它？

当我最初开始查看和使用这些工具时，我很快意识到它们的高层目的是准确确定我所写代码的意图。

当参数类型和返回值类型被添加到语言中时，它以两种方式帮助了我。首先，它消除了一整类旨在回答诸如“你是否得到了一个数组？”等问题的测试。一旦你可以在语言层面上说“这个变量应该是一个整数”，那么 PHP 解释器就可以替我做那个测试。

随着类型的使用，静态分析工具可以读取我的代码，解析它，然后开始查看调用它的代码。当我开始使用这些工具时，我开始欣赏到有某个东西在关注我做了什么并提出建议：

“我知道你接受一个数组作为这个参数，但看看在某个地方它被赋予了一个整数数组，而在其他地方它却是混合值的数组。你期望的是哪一个？”

“我注意到你在这个对象上调用了这个方法，而你在几行代码之前生成了这个对象。由于背后有一些延迟加载，我无法确定它应该是哪种类型的对象。你能添加一个注解来帮助我弄清楚吗？”





## 谁应该使用它？

开发人员在进行编码工作时应该使用静态代码分析工具，最好是在他们尝试将代码提交到版本控制系统之前。

如果你有一些不太情愿使用工具的开发人员，你可以始终依赖版本控制系统的提交钩子（commit hooks），并将其添加在那里。我自己的建议是将其创建为预提交钩子（pre-commit hook）——除非静态分析工具表示满意，否则不允许任何提交通过！

请记住，使用此类工具的任何场景都需要配合代码审查，以确保你可以用来让 PHPStan “满意”的一些技术被正确应用。

## 我该如何操作？

PHPStan 的配置文件（名为 `phpstan.neon`）包含最少数量的选项：

```yaml
parameters:
    bootstrapFiles:
        - config/bootstrap.php
    level: max
    paths:
        - src
        - tests
```

PHPStan 的文档涵盖了这些选项以及更多内容，但我想谈谈我正在使用的选项。

该应用程序的框架（CakePHP[6]）使用一个引导文件，因此我告诉 PHPStan 使用它，这样它就能看到框架相关的配置值以及我可能正在使用的任何自定义值。根据底层框架的不同，我可能根本不需要这个。

[5] https://docs.phpdoc.org/latest/guide/guides/docblocks.html

[6] https://cakephp.org

我还可以告诉它我想让它扫描哪些路径。我绝对不希望对通过 Composer 安装包创建的 `vendor` 目录中的第三方代码进行任何分析。

PHPStan 还使用了“分析级别”的概念。这告诉 PHPStan 在分析你的代码时应该有多严格。我选择了 `max`（这是 7 的别名），范围是 0 到 7。默认情况下，它使用的是 0。如果我选择级别 0 会怎样？

```
Note: Using configuration file /Users/chartjes/Sites/ibl/phpstan.neon.
51/51 ██████████████████ 100%
------------------------------------
Line    src/Shell/ConsoleShell.php
------------------------------------
60      Method App\Shell\ConsoleShell::main() should return int|null but return statement is missing.
------------------------------------
```

好吧，只有一个错误。我应该使用返回类型提示，PHPStan 告诉我添加一个。一旦我这样做，PHPStan 报告没有错误。

我不断提高级别，直到得到一组新的错误。在第二个级别，我得到：

```
1.  Note: Using configuration file /Users/chartjes/Sites/ibl/phpstan.neon.
2.  51/51 ██████████████████ 100%
3.  ------------------------------------
4.  Line    src/Controller/Component/StandingsComponent.php
5.  ------------------------------------
6.  514     Comparison operation ">=" between (array|float|int) and 13 results in an error.
7.  525     Comparison operation "<=" between (array|float|int) and 5 results in an error.
8.  ------------------------------------
9.
10.
11. Line    src/Model/Table/GamesTable.php
12. ------------------------------------
13. 143     Call to an undefined method Cake\ORM\Query::orWhere().
14. ------------------------------------
15.
16.
17. Line    src/Util/Rosters.php
18. ------------------------------------
19. 15      Call to an undefined method Cake\ORM\Table::generateListByNicknameName().
20. ------------------------------------
21.
22.
23. Line    src/View/AjaxView.php
24. ------------------------------------
25. 48      Call to an undefined method Cake\Http\Response::type().
26. ------------------------------------
27.
28. [ERROR] Found 5 errors
```

现在看起来 PHPStan 确实变得更严格了，并指出了我代码中的一些问题，虽然代码可以工作，但未来可能会导致麻烦。它的抱怨总结如下：

- 我需要在比较中显式转换一些值。
- 我需要明确告诉 PHPStan 正在使用的一些类是什么，而不是假设存在魔法。

好吧，我将做一些更改并解释为什么它们是必要的。以下是它抱怨的一行代码：

```php
if (($result->home_score + $result->away_score) >= 13)
```

PHPStan 正在审视这一行，并说：“我不完全确定 `$result->home_score` 或 `$result->away_score` 中可能包含什么，所以你能澄清一下吗？”

我认为这是一个合理的问题。修改后的行可能看起来像这样：

```php
if ((int)($result->home_score + $result->away_score) >= 13)
```

另一种做法是更严格，将两个值都强制转换为整数。

```php
if ((int)$result->home_score + (int)$result->away_score >= 13)
```

我的一位开发人员朋友不止一次说过，使用静态分析工具的代码“看起来不再像 PHP 了”。意思是，“它不再像很多人编写 PHP 代码的样子那样像 PHP 代码了。” 由于动态类型功能，PHP 在许多情况下都极其宽容。它试图弄清楚你的意图。也许这些 `home_score` 和 `away_score` 类属性总是整数。通过显式将它们强制转换为整数，我 100% 确保该比较不会导致 PHP 相关的错误。希望这两个属性永远不会包含不正确的值！

所以在级别 2，它说有四个更多的错误。我将修复其他与数学相关的一个，然后开始关注其他报告的问题。

| 行号 | 文件 | 描述 |
| :--- | :--- | :--- |
| 143 | `src/Model/Table/GamesTable.php` | 调用了未定义的方法 `Cake\ORM\Query::orWhere()`。 |

这个错误是因为 PHPStan 无法理解那个 `orWhere()` 方法来自哪里。这真的是一个错误吗？不。代码明显可以工作，所以我可以告诉 PHPStan 忽略这个问题。根据文档，我可以添加一个特定的 PHPStan 注释来告诉它忽略来自那一行的错误。

让我们这样做——某些工具确实可以报告假阳性，我觉得这就是其中之一。这是更新后的代码现在的样子：

```php
return $this->find()
    ->where([ 'week <=' => $week ])
    ->contain('HomeTeams, AwayTeams', function ( Query $sq ) use ( $teams ) {
        /** @phpstan-ignore-next-line */
        return $sq->where('HomeTeams in', $teams)
            ->orWhere('AwayTeams in', $teams);
    });
```

只剩下两个错误了。下一个是这个：

```
Line  src/Util/Rosters.php
15      Call to an undefined method Cake\ORM\Table::generateListByNicknameName().
```

嗯。我对代码库进行了搜索，该方法根本不存在。这是死代码吗？我做的一个从未完成的实验？更多的搜索让我相信，事实上，这是没有被使用的代码。对显示阵容页面的手动测试证实了这一点。

好的，只剩下最后一个错误：

```
Line  src/View/AjaxView.php
48      Call to an undefined method Cake\Http\Response::type().
```

我怀疑这是框架旧版本使用的代码，但在升级过程中，它留了下来。我可以删除该文件，但我没有足够的测试覆盖率来放心地这样做。相反，我将向 `phpstan.neon` 文件添加一些细节，告诉它忽略此文件。

```yaml
parameters:
  bootstrapFiles:
    - config/bootstrap.php
  level: 2
  paths:
    - src
    - tests
  excludePaths:
    - src/View
```

没有更多错误了！我必须将分析级别提高到六，才能收到另一组需要审查的问题：

```
Note: Using configuration file /Users/chartjes/Sites/tbl/phpstan.neon.
48/48 [||||||||||||||||||||||||||] 100%
-----------------------------------------
Line   src/Model/Table/GamesTable.php
   143  Method App\Model\Table\GamesTable::findAllByTeams() has parameter
   $teams with no value type specified in iterable type array.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
   143  Method App\Model\Table\GamesTable::findAllByTeams() return type has no
   value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
-----------------------------------------
   Line   src/Model/Table/TeamsTable.php
   104  Method App\Model\Table\TeamsTable::findByConference() return type has
   no value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
-----------------------------------------
   Line   src/Util/Boxscore.php
   12  Property App\Util\Boxscore::$schedule has no typehint specified.
   13  Property App\Util\Boxscore::$teams has no typehint specified.
   14  Property App\Util\Boxscore::$games has no typehint specified.
-----------------------------------------
[ERROR] Found 6 errors
```





## 2. 静态代码分析工具

此外，你现在可以看到 PHPStan 正在提供建议，说明如何解决这一级别中的一些问题。它似乎突出显示了相同的问题。我会去阅读该 URL 指向的页面。

好的，第一个问题：

```text
Line    src/Model/Table/GamesTable.php
143     Method App\Model\Table\GamesTable::findAllByTeams() has parameter
        $teams with no value type specified in iterable type array.
        □ See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type/
```

以下是它不喜欢的代码：

```php
public function findAllByTeams(int $week, array $teams): Query
```

它想知道 $teams 里面是什么。我认为它是整数，所以我可以为该方法创建一个 docblock，确保添加在那里，然后我可以重新运行 PHPStan。

```php
1.  /**
2.  * @param int $week
3.  * @param array<int> $teams
4.  * @return Query
5.  */
6.  public function findAllByTeams(int $week, array $teams): Query
7.  {
8.      return $this->find()
9.          ->where(['week <=' => $week])
10.         ->contain('HomeTeams, AwayTeams', function (Query $q) use ($teams) {
11.             /** @phpstan-ignore-next-line */
12.             return $q->where('HomeTeams in', $teams)
13.                     ->orWhere('AwayTeams in', $teams);
14.         });
15.  }
```

PHPStan 抱怨的下一个问题是，它想知道 findAllByTeams() 方法返回的那个 Query 集合里面有什么。答案是更改返回类型，说明该 Query 集合返回的是 GamesTable 对象。有了这个更改，这是完整的方法。

### 我该怎么做？

```php
1.   /**
2.     * @param int $week
3.     * @param array<int, Team>
4.     * @return Query<GameTable>
5.     */
6.   public function findAllByTeams(int $week, array $teams): Query
7.   {
8.       return $this->find()
9.            ->where(['week <='=> $week])
10.          ->contain(['HomeTeams, AwayTeams', function (Query $q) use ($teams) {
11.              /** @phpstan-ignore-next-line */
12.              return $q->where('HomeTeams in', $teams)
13.                       ->orWhere('AwayTeams in', $teams);
14.          });
15.   }
```

除了让 PHPStan 满意之外，这有什么意义？如本章前面所述，许多 IDE 可以查看这些文档块和代码本身，使代码补全更容易。如果其他代码正在遍历该方法返回的对象集合，它可以验证这些对象上有哪些可用方法。

所有这些静态分析都有一个目标——代码意图更清晰，更容易调试，并且不太可能以意外方式运行。

在这个级别只剩下两组错误了。我想修复这一个：

```text
Line           src/Model/Table/TeamsTable.php
104  Method App\Model\Table\TeamsTable::findByConference() return type has no value type specified in iterable type Cake\ORM\Query.
   See: https://phpstan.org/blog/solving-phpstan-no-value-type-specified-in-iterable-type
```

这是我刚才修复的问题的类似情况。类似的解决方案：

```php
1.   /**
2.     * @param string $conference
3.     * @return Query<TeamTable>
4.     */
5.   public function findByConference(string $conference): Query
6.   {
7.       return $this->find()
8.            ->contain('Divisions')
9.            ->where(['Divisions.conference' => $conference]);
10.   }
```

最后一组要修复的问题！

```text
Line src/Util/Boxscore.php
12 Property App\Util\Boxscore::$schedule has no typehint specified.
13 Property App\Util\Boxscore::$teams has no typehint specified.
14 Property App\Util\Boxscore::$games has no typehint specified.
```

只是缺少一些类型提示。查看代码，我知道它应该是什么类型。更新后的代码应该如下所示：

```php
1. <?php
2.
3. declare(strict_types=1);
4.
5. namespace App\Util;
6.
7. use Cake\ORM\Locator\TableLocator;
8. use Cake\ORM\Table;
9.
10. class Boxscore
11. {
12.
13.     public Table $games;
14.     public Table $schedule;
15.     public Table $teams;
16.
17.
18.     public function __construct()
19.     {
20.         $this->schedule = (new TableLocator())->get('Schedule');
21.         $this->teams = (new TableLocator())->get('Teams');
22.         $this->games = (new TableLocator())->get('Games');
23.     }
24.
25.    /**
26.     * @param int $slackerWeek
27.     * @return array<string, mixed>
28.     */
29.    public function getMissing(int $slackerWeek): array
30.    {
31.        if ($slackerWeek === 0) {
32.            return [];
33.        }
34. 
35.        $missingBoxes = [];
36. 
37.        // Build an array of teams with codes
38.        $results = $this->teams->find()
39.            ->select(['tbl', 'code'])
40.            ->all();
41.        $teams = [];
42. 
43.        foreach ($results as $result) {
44.            $teams[$result->code] = $result->tbl;
45.        }
46. 
47.        $results = $this->schedule
48.            ->find()
49.            ->contain('Teams')
50.            ->where([
51.                'Schedule.status' => 0,
52.                'Schedule.week <=' => $slackerWeek
53.            ])->order('Schedule.week, Teams.tbl');
54. 
55.        foreach ($results as $result) {
56.            $key = $result->week . $teams[$result->home];
57.            $missingBoxes[$key] =
58.                "wk{$result->week} {$teams[$result->away]}@{$teams[$result->home]}";
59.        }
60. 
61.        ksort($missingBoxes, SORT_NATURAL);
62.        return $missingBoxes;
63.    }
64. }
```

现在我将 PHPStan 分析级别设置为 7，看看它报告什么问题。

```text
Line   src/Console/Installer.php
----------------------------------------
148  Parameter #1 $array of function array_diff expects array, array<int,
string>|false given.
180  Parameter #3 $subject of function str_replace expects array|string,
string|false given.
```

这是我没有编写的代码；它是由框架创建的。我会告诉 PHPStan 忽略它。

```yaml
1. parameters:
2.     bootstrapFiles:
3.         - config/bootstrap.php
4.     level: 7
5. paths:
6.     - src
7.     - tests
8.     excludePaths:
9.         analyse:
10.        - src/View
11.        - src/Console/Installer.php
```

最终结果是 PHPStan 不再抱怨任何东西！

### 附加题！

PHPStan 揭示了代码库中的少量问题。如果你的应用程序结构松散得多怎么办？我恰好也有一个这样的应用！还有另一个应用可以被认为是我一直在分享样本的应用的“伴侣”。它几乎没有任何结构。假设我想开始对这个代码库应用最高级别的静态分析。它会说什么？

第一步是创建一个 PHPStan 配置文件：

```yaml
1. parameters:
2. bootstrapFiles:
3. - vendor/autoload.php
4. level: 7
5. paths:
6. - .
7. excludePaths:
8. analyse:
9. - vendor
```

情况能有多糟？

```text
[ERROR] Found 312 errors
```

也许这很糟糕。现在，如果这是一个付费项目而不是业余爱好者的项目，我可能不想花那么多开发人员时间修复旧问题。相反，我希望确保我编写的所有新代码都可以由 PHPStan 分析，但接受代码库的当前状态。

为此，PHPStan 有一个“设置基线”的概念。使用命令行中的 `--generate-baseline` 开关，PHPStan 生成一个包含其发现的所有错误的文件。

以下是我运行该命令时看到的内容：

```bash
./vendor/bin/phpstan --generate-baseline
```

```text
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [#################] 100%

[OK] Baseline generated with 312 errors
```

然后，根据说明，我在我的 phpstan.neon 配置文件中添加对该文件的引用。

```yaml
1. includes:
2.      - phpstan-baseline.neon
3.
4. parameters:
5.     bootstrapFiles:
6.      - vendor/autoload.php
7.      level: 7
8.      paths:
9.      - .
10.     excludePaths:
11.        analyse:
12.      - vendor
```

完成此操作后，下次我要求 PHPStan 分析我的代码时，我不应该看到任何错误：

```text
Note: Using configuration file /Users/chartjes/ibl.dev/webreg/phpstan.neon.
64/64 [████████████████████████████] 100%

[OK] No errors
```

现在我可以在项目中开始重构或添加代码，而 PHPStan 将只报告它尚未见过的错误。这是一个非常大的遗留项目的实用工具。




## 第 3 章：变异测试

### 它是什么？

你是否曾想过，有没有一种方法可以测试你编写的这些测试本身？这本质上就是**变异测试**所做的。

我首选的 PHP 变异测试工具是 Infection[^1]，它这样定义变异测试：

> 变异测试涉及对程序进行微小修改。每个变异版本被称为一个**变异体**（Mutant）。为了评估一组测试的质量，这些变异体会针对输入测试集执行，以查看是否检测到了引入的故障。如果变异后的程序导致测试失败，则称为**被杀死的变异体**（killed mutant）。如果变异后的代码测试仍通过，则存在一个**逃逸的变异体**（escaped mutant）。

在使用 Infection 的情况下，它会与 PHPUnit 协同工作，对代码进行有依据的随机更改，然后执行测试。

[^1]: [https://infection.github.io](https://infection.github.io)

### 我为什么要使用它？

我编写单元测试的方法大致如下：

- 我要测试的场景是什么？
- 我的依赖项有哪些？
- 如何创建这些依赖项？
- 如何将它们提供给被测试的代码？
- 我需要做哪些断言？
- 是否有任何代码需要更改才能使这些断言成功？

如果我提出了足够的场景，我会开始理所当然地认为我的测试覆盖率足够，并且测试本身也很完善。

**变异测试**开始挑战第二个假设。如果它通过像将 `if` (`$foo > $bar`) 切换为 `if` (`$foo < $bar`) 这样的方式来变异你的代码，而针对该部分代码的测试仍然通过，那么你的测试就存在问题。

是的，有时测试是通过巧合而成功的！如果你大量使用测试替身（test doubles），你需要一种方法来检测你为其创建替身的代码是否按测试预期那样运行。否则，你最终会拥有那些通过但不再反映代码实际工作方式的测试。

### 我如何使用它？

在我们的示例应用中，我想为验证我们排名榜中团队排序正确性的某些代码创建测试。测试看起来是这样的：

```php
public function it_sorts_standings_correctly(): void
{
    $unsortedStandings = unserialize(
        (string) file_get_contents(__DIR__ . '/../../Fixture/unSortedStandings.txt')
    );
    $expectedStandings = unserialize(
        (string) file_get_contents(__DIR__ . '/../../Fixture/sortedStandings.txt')
    );

    $results = $this->component->sort($unsortedStandings);

    self::assertSame($expectedStandings['AC1'], $results);
}
```

这看起来是一个直截了当的测试。变异测试能否揭示我们的预期是错误的？

在达到那一点之前，我不得不做一些配置工作。首先，我需要为 Infection 本身创建配置文件。它被命名为 `infection.json`，并存储在项目的根目录中：

```json
{
    "source": {
        "directories": [
            "src",
            "templates"
        ]
    },
    "logs": {
        "text": "infection.log"
    },
    "mutators": {
        "@default": true
    },
    "tmpDir": "tmp",
    "testFramework": "phpunit"
}
```

接下来，我确保我的 PHPUnit 配置文件按照我想要的方式设置。它被命名为 `phpunit.xml`，同样位于项目的根目录中：

```xml
<phpunit bootstrap="tests/bootstrap.php">
    <listeners>
        <listener class="\Cake\TestSuite\Fixture\FixtureInjector">
            <arguments>
                <object class="\Cake\TestSuite\Fixture\FixtureManager" />
            </arguments>
        </listener>
    </listeners>
    <testsuites>
        <testsuite name="unit">
            <directory>tests</directory>
        </testsuite>
    </testsuites>
</phpunit>
```

我正在使用的框架为我提供了 `bootstrap.php` 文件。有关更多详细信息，请查阅你的框架文档，或者如果你使用的是自定义解决方案，你需要弄清楚该文件中应该包含什么内容。

有了这两个配置文件，我使用 Infection 的 `--filter=path/to/code/to/test` 命令行选项来告诉它我们要查看什么代码。那么运行的结果是什么？

```
$ php infection.phar --filter=src/Controller/Component/StandingsComponent.php

Running initial test suite...

PHPUnit version: 8.5.15

      23 [============================] 8 secs

Generate mutants...

Processing source code files: 1/1
.: killed, M: escaped, U: uncovered, E: fatal error, T: timed out, S:
skipped

UUUUUUUT................M................................MMM   (  50 / 302)
MMMMMMMMMMMMM.............MMM..............M.............   ( 100 / 302)
M......MM........................TTTTTTTTTTTT..........   ( 150 / 302)
MMMMMMMMMMMM..M...MMMMMMMMMMMMMM.MMM..MMMMMM..   ( 200 / 302)
MMMMMM...MMMMMM...MMMMMMM...MMM.............   ( 250 / 302)
MMMMMM.MMMMMMM.....MMM.........MMMMMMMMMM......   ( 300 / 302)
..M                                        ( 302 / 302)

302 mutations were generated:
      39 mutants were killed
       6 mutants were not covered by tests
     255 covered mutants were not detected
       0 errors were encountered
       2 time outs were encountered
       0 mutants required more time than configured

Metrics:
       Mutation Score Indicator (MSI): 13%
       Mutation Code Coverage: 98%
       Covered Code MSI: 13%

Please note that some mutants will inevitably be harmless (i.e. false
positives).

Time: 4m 33s. Memory: 0.03GB
```

为了完全透明：我要求它查看的代码几乎没有自动化测试，除了那个检查排序的测试和一些检查页面中我期望的位置是否显示内容的功能风格测试。

我们应该担心摘要中的哪些信息？因为我们没有 `StandingsComponent.php` 的 100% 代码覆盖率，很难给出一个很好的答案。工具提供的答案可以引导我们找出应该在哪里集中注意力。

### 变异得分指标 (MSI)

你希望这个值尽可能高。它代表了被你的测试捕获的变异百分比。要理解这意味着什么，过程如下：

- 更改你正在分析的代码中的某些内容
- 运行“覆盖”该代码的测试
- 如果测试仍然通过，你就有一个未被捕获的变异体

13% 是一个非常低的数字，表明我们现有的测试没有发现大多数变异，这意味着我们的测试愉快地通过了，尽管存在本应被发现的更改。这并不好！

### 变异代码覆盖率

这个值应该接近你现有的代码覆盖率。我不知道我当前的代码覆盖率是多少，但看到它是 98% 很有趣。鉴于这个值和 MSI 之间的差距，这意味着我需要更多的测试。

### 覆盖代码变异得分指标

这是真正需要关注的值——它显示了实际被测试覆盖的代码的 MSI 是多少。现在，因为我过滤了内容并告诉 Infection 只查看一个文件，这应该与 MSI 完全映射。再次说明，这个数字真的很低。

### 变异体日志记录

在我的配置文件中，我要求 Infection 将其正在执行的操作写入名为 `infection.log` 的文件，该文件写入我们应用程序的根目录。由于我实际上只有一个针对排序方法的测试，让我搜索针对该代码进行的任何变异：

```
66) /workspace/src/Controller/Component/StandingsComponent.php:192 [M]
Foreach_

--- Original
+++ New
@@ @@
 public function sort(array $standings) : array
 {
     $column = [];
-    foreach ($standings as $tmp) {
+    foreach (array() as $tmp) {
         $column[] = $tmp['pct'];
     }
     array_multisort($column, SORT_DESC, $standings);
}

67) /workspace/src/Controller/Component/StandingsComponent.php:196 [M]
FunctionCallRemoval

--- Original
+++ New
@@ @@
 foreach ($standings as $tmp) {
     $column[] = $tmp['pct'];
 }
-    array_multisort($column, SORT_DESC, $standings);
+
// Determine who is the leader for games behind
$leaderDiff = 0;
foreach ($standings as $info) {
```

如果你不熟悉这里的记号，它遵循的是你使用版本控制系统或可以显示两个文件之间差异的工具（通常称为“diff”工具）时会看到的内容。

第一个变异体更改了一个获取我们想要排序的列详情的 foreach 循环。

第二个变异体完全移除了对数组的排序。

那些测试带着这些更改是如何通过的！我可以自己应用其中一个并查看测试是否通过。





## 我该如何使用它？

它确实运行了（虽然我不明白具体发生了什么），但同时也报告了一系列通知：

> 通知错误：试图访问类型为 null 的值的数组偏移量

我不明白的是：这个测试怎么会通过呢？！? 我做的比较有误吗？我的测试有问题吗？

首先，我检查从开始阶段开始，我的未排序数据是否与排序后的数据不匹配。

```php
public function it_sorts_standings_correctly(): void
{
    $unsortedStandings = unserialize(
        (string) file_get_contents(__DIR__ . '/../.../Fixture/unSortedStandings.txt')
    );
    $expectedStandings = unserialize(
        (string) file_get_contents(__DIR__ . '/../.../Fixture/sortedStandings.txt')
    );

    self::assertNotEquals($unsortedStandings, $expectedStandings['AC']);

    $results = $this->component->sort($unsortedStandings);

    self::assertEquals($expectedStandings['AC'], $results);
}
```

该断言失败了。那些测试数据（fixtures）中存在不良数据！下一步是修复此问题，并确保这两个测试数据确实不同。

接下来，我再次运行相同的测试用例，它通过了，这意味着我确实拥有不同的数据。我再次运行 Infection，情况有所改善……略微。

> 变异得分指标 (MSI)：14%
> 变异代码覆盖率：98%
> 已覆盖代码 MSI：14%

现在是时候去查看输出日志，寻找线索，看看是哪些变异体（mutants）成功躲过了我现有的那一个测试。

## 3. 变异测试

```diff
67) /workspace/src/Controller/Component/StandingsComponent.php:202 [M] DecrementInteger

--- Original
+++ New
@@ @@
 }
 array_multisort($column, SORT_DESC, $standings);
 // Determine who is the leader for games behind
- $leaderDiff = 0;
+ $leaderDiff = -1;
 foreach ($standings as $info) {
 $zVal = $info['w'] - $info['l'];
 if ($zVal > $leaderDiff) {



68) /workspace/src/Controller/Component/StandingsComponent.php:207 [M] GreaterThan

--- Original
+++ New
@@ @@
 $leaderDiff = 0;
 foreach ($standings as $info) {
 $zVal = $info['w'] - $info['l'];
- if ($zVal > $leaderDiff) {
+ if ($zVal >= $leaderDiff) {
 $leaderDiff = $zVal;
 }
 }
```

只有这两个变异体涉及我们最新测试所处理的排序方法。和之前一样，我直接修改源代码，以查看测试是否如预期般失败。测试仍然通过。接下来需要问的问题是：“这真的重要吗？”有些变异体实际上是假阳性。

对于变异体 67，关于它为什么是假阳性的答案可以在变异体 68 中找到。如果比较 $zVal 和 $leaderDiff 的条件得到满足，我会覆盖写入 $leaderDiff 的值，因此让该值从 -1 开始可能是不正确的，但这不会导致测试失败。

变异体 68 更有趣。在什么情况下，该条件语句的改变会有影响？根据我计算球队“落后场次”（games behind）的方式，我认为这完全无关紧要。这个可以被视为假阳性。

### 我何时应该使用变异测试？

正如我在上一节中展示的那样，使用变异测试的最佳时机是在开发阶段。通过检查任何“逃逸变异体”（escape mutants）来看是否可以采取某些措施，它可以作为一个工具引导你创建更好的测试。

在我的案例中，我一开始就有一个无效的测试。看，即使经验丰富的开发人员也会遇到这种情况！查看变异体并亲自应用更改，将带我走向修复损坏测试的道路。

我不会将变异测试作为任何持续集成构建系统的一部分运行。它可以返回假阳性这一事实意味着它可能会无故导致构建失败。

与静态代码分析工具类似，它是一个优秀的工具，可以将你的测试提升到“下一层次”。拥有测试是好事；拥有有效的测试则更好！

## 第 4 章

# 代码的 Lint 和格式化

我第一次遇到一种“开箱即用”就带有代码格式化程序的编程语言，那是十多年前我刚开始折腾 Go[^1] 的时候。令我同样震惊的是看到 Go 社区如此迅速地接受它。考虑到这些年来我在网上看到的关于诸如 JavaScript 中分号的使用以及 PHP 中开括号和闭括号位置等方面的种种争论，这感觉就像是一阵清新的微风。

多年来，我发现代码 Linter（检查器）和 Formatter（格式化器）能做的远不止告诉你“那个开括号位置不对”。它们可以强制执行许多在代码审查中经常出现的实践，并且也可以用于构建系统中为你应用这些更改。我曾经领导的一个 OSS 项目以令人惊讶的方式大量使用它们。

[^1]: https://golang.org

### 是什么

Linter 和 Formatter 通常是开发人员可以在本地运行的 CLI 工具。许多 IDE 也集成了使用它们的方案。充分了解你的 IDE 的里里外外！它可以帮助你自动化许多占编码工作很大比重的重复性工作。

这些工具分析你的代码，通常基于一组可自定义的规则，并识别未遵循这些规则的地方。Formatter 通常与 Linter 结合使用，并使用相同的可配置规则概念来识别然后修改代码。

它们可以通过 CLI 运行的优势在于，它们也可以用作任何持续集成或构建服务的一部分。

### 为什么

多年来，我试图向其他开发人员灌输的一个概念是，我们应该让计算机为我们执行任何重复性任务。这样（或者说根据我的理论），我们就不再需要担心那些任务，而可以将我们的脑力能量用于解决其他问题。

强制推行编码标准，甚至是特定语言结构的使用，意味着你拥有在整个应用程序中保持一致的代码。这种一致性反过来往往能加速理解和调试，并且通常允许你引入其他期望你的代码具有特定外观和行为的其他工具。

鉴于一些 Linter 和 Formatter 可以插入版权声明代码块，甚至告诉你某个代码缺少单元测试（是的，这是可以做到的），你为什么不想拥有一个基本上可以随时待命的同事，他不仅能指出（更重要的是）修复那些可能直到代码审查时才暴露的问题呢？

### 如何做

与我对测试框架、编辑器、静态代码分析器和操作系统的建议类似——选择一个能完成你需要它完成的工作的工具，然后在此基础上发展。没有完美的工具！

对于我自己的项目，我提倡使用 Easy Coding Standard[^2]，因为它允许你使用其他工具创建的定义。在我写这本书时，我使用的是版本 9.3.12。

[^2]: https://github.com/symplify/easy-coding-standard

我也曾使用 PHP_CodeSniffer[^3] 和 PHP CS Fixer[^4] 以及其他语言的代码 Linter 和 Fixer；对于我在 Mozilla 编写的 Python 代码，我偏好使用 Black[^5]。再次强调，使用哪一个并不真正重要。

我们实际该如何使用这些工具？我从另一个项目借用了一套 PHP CS Fixer 规则集，并让它与 ECS 良好地协作。ECS 项目有一些优秀的文档，指向其他博客文章，介绍其他人如何转换规则集。

对于我的第一次尝试，我让它：

- 强制使用短数组语法
- 强制使用 PSR-12[^6]
- 仅应用于我的 src 和 tests 目录

以下是 ecs.php 配置文件的样子：

```php
<?php

declare(strict_types=1);

use PhpCsFixer\Fixer\ArrayNotation\ArraySyntaxFixer;
use Symfony\Component\DependencyInjection\Loader\Configurator\ContainerConfigurator;
use Simplify\EasyCodingStandard\ValueObject\Option;
use Simplify\EasyCodingStandard\ValueObject\Set\SetList;

return static function (ContainerConfigurator $containerConfigurator): void {
    $parameters = $containerConfigurator->parameters();
    $parameters->set(Option::PATHS, [
        __DIR__ . '/src',
        __DIR__ . '/tests',
    ]);

    $services = $containerConfigurator->services();
    $services->set(ArraySyntaxFixer::class)
        ->call('configure', [
            'syntax' => 'short',
        ]);
    $containerConfigurator->import(SetList::PSR_12);
};
```

[^3]: https://github.com/squizlabs/PHP_CodeSniffer
[^4]: https://github.com/FriendsOfPhp/PHP-CS-Fixer
[^5]: https://github.com/psf/black
[^6]: https://www.php-fig.org/psr/psr-12




## 4. 代码的 LINTING 与格式化

是时候让它运行起来，看看它发现了什么问题！

```
[WARNING] 42 errors are fixable! Just add "--fix" to console command and rerun to apply.
```

考虑到代码库的年限，这并不令人惊讶。下一步是告诉工具帮我修复所有这些更改。

```
./vendor/bin/ecs check --fix
```

它完成所有工作，以下是它为我所做的修改示例之一：

```
1.  42) tests/TestCase/Util/BoxscoreTest.php
2.  
3.  ----------- begin diff -----------
4.  --- Original
5.  +++ New
6.  @@ -1,4 +1,5 @@
7.  <?php
8.  +
9.  declare(strict_types=1);
10. 
11.  use App\Model\Table\GamesTable;
12.  @@ -12,9 +13,9 @@
13.      public function it_finds_missing_boxscores(): void
14.      {
15.          /** @var GamesTable $games */
16.  -     $games = (new TableLocator())->get('Games');
17.  +     $games = (new TableLocator())->get('Games');
18. 
19.  -     $results = (new Boxscore)->getMissing($games->getMaxWeek());
20.  +     $results = (new Boxscore())->getMissing($games->getMaxWeek());
21. 
22.      if (count($results) === 0) {
23.          self::markTestSkipped('No missing boxscores available');
24.      ----------- end diff -----------
25. 
26. 
27.  Applied checkers:
28. 
29.  *  PhpCsFixer\Fixer\Operator\NewWithBracesFixer
30.  *  PhpCsFixer\Fixer\PhpTag\BlankLineAfterOpeningTagFixer
31. 
32. 
33. 
34.  [OK] 42 errors successfully fixed and no other errors found!
```

### 如何实现

看，现在工具做了所有的事情，要么是我不知道这些属于 PSR-12 标准的一部分，要么是我总是忘记自己要做的事情。

嗯。我注意到我的文件没有都包含 `declare(strict_types=1);` 语句。我们可以把这个作为一条规则加进去吗？

在文档中我看到确实有相关的规则：

```
$services->set(DeclareStrictTypesFixer::class);
```

我把它添加到我的 `ecs.php` 文件中，就这样解决了。

```
1.
2. All sorts of output snipped...
3.
4. 31) tests/bootstrap.php
5.
6.  ----------- begin diff -----------
7. --- Original
8. +++ New
9. @@ -1,4 +1,6 @@
10.  \<?php
11. +
12. +declare(strict_types=1);
13.  /**
14.  * Test runner bootstrap.
15.  *
16.  ----------- end diff -----------
17.
18.
19. Applied checkers:
20.
21.  \* PhpCsFixer\Fixer\PhpTag\BlankLineAfterOpeningTagFixer
22.  \* PhpCsFixer\Fixer\Strict\DeclareStrictTypesFixer
23.
24.
25.
26. [WARNING] 31 errors are fixable! Just add "--fix" to console command and rerun to apply.
```

很好；这是一个快速的修复，我再也不用担心这个了。

现在我检查一下确保没有破坏任何东西…… 我的测试显示了一些错误！都在一个没有严格类型声明的文件中。两次修改之后（将变量强制转换为期望的值），我的测试套件又通过了！它还能做什么？

比如防止我们忘记排序导入语句？

```
$services->set(OrderedImportsFixer::class);
```

```
1. src/Model\Table\GamesTable.php
2.  ----------- begin diff -----------
3. --- Original
4. +++ New
5. @@ -6,8 +6,8 @@
6.  
7. use Cake\ORM\Association\BelongsTo;
8. use Cake\ORM\Locator\TableLocator;
9. +use Cake\ORM\Query;
10. use Cake\ORM\Table;
11. -use Cake\ORM\Query;
12.  
13. /**
14.  * Games Model
15. ----------- end diff -----------
```

```
18.  
19. Applied checkers:
20.  
21. * PhpCsFixer\Fixer\Import\OrderedImportsFixer
```

我希望我的所有 PHPUnit 测试都使用注解来指示某个方法是测试用例，而不是在前面加上 test：

```
$services->set(PhpUnitTestAnnotationFixer::class)
    ->call('configure', [[
        'style' => 'annotation'
    ]]);
```

```
1. 3) tests/TestCase/Model/Table/GamesTableTest.php
2.
3. ```diff begin diff```
4. --- Original
5. +++ New
6. @@ -15,7 +15,10 @@
7. ```
8. ```class GamesTableTest extends TestCase
9. ```{
10. - ```public function testGetWeeklyResult(): void
11. + ```/**
12. + ```* @test
13. + ```*/
14. + ```public function getWeeklyResult(): void
15. + ```{
16. ```/** @var GamesTable $table */
17. ```$table = (new TableLocator())->get('Games');
18. ```
19. ```diff end diff```
20.
21. Applied checkers:
22.
23. * PhpCsFixer\Fixer\PhpUnit\PhpUnitTestAnnotationFixer
```

### 何时使用

根据我的经验，使用代码 Linter 和格式化工具有三个合适的时机：

#### 开发期间

如果某个项目没有强制要求，最常见的做法是让开发者在工作期间使用 Linting 和格式化工具，并希望在提交和推送代码进行审查或合并之前使用它们。

我在那些未强制要求使用这些工具的项目中就是这么做的。

#### 使用版本控制之前

如果你使用的版本控制系统具有“pre-commit hook”的概念，我强烈建议你阅读你的 VCS 文档，了解如何使用它们并设置一个。

这样，如果你忘记运行 Linter，它会在你的 VCS 工具将代码推送到仓库之前自动执行。

#### 构建或持续集成期间

这是我最喜欢的让 Linting 工具运行的时机，Linter 报告的任何问题都会被视为构建失败。同样，这也依赖于你拥有一个可以定制以便从命令行运行任意命令的构建系统或持续集成系统。

如果你使用的是像 GitHub Actions^[7]^ 这样的东西，你可以找到如何操作示例。在本书稍后介绍如何使用持续集成系统的章节中，你大概可以猜出在哪里添加 Linting 步骤。

^[7]^ GitHub Actions: https://github.com/features/actions

# 第 5 章

## 持续集成

我非常支持让计算机为我执行重复性的操作。这让我能腾出注意力去解决其他问题，而不是记住一系列步骤，其中漏掉任何一步都可能导致失败。

大多数编程项目面临的问题之一是找到一种方法，以最小的摩擦力集成代码更改。在开发端或工具创建端，没有任何无痛且无需努力的方法可以做到这一点。

在我撰写本文时（2021 年春天），有两种主流的代码集成方法。我称之为“带标志的主干集成”和“通过 Pull Request 集成”。

#### 通过 Pull Request 集成

由于大量开发者使用 GitHub（讽刺的是，这是一个用于分布式版本控制系统的集中式基于 Web 的工具集），阅读本文章的大多数人熟悉“Pull Request”的使用。

对于不熟悉的人来说，这里有一个高层级的解释：

开发者创建受版本控制的代码的一个分支，并在该分支中进行一些工作。一旦准备好分享，他们使用工具创建“Pull Request”，这是一种通知，表示有一些更改需要审查。通常来说，你是在将开发者在他们自己的分支上的工作与部署到生产环境的主分支进行比较。

审查 Pull Request 的人可以看到更改内容并对这些更改发表评论。Pull Request 方法的一个缺点是，如果代码库本身变化迅速，长期进行的工作很容易过时。反过来，这迫使开发者做大量工作，不断合并其他开发者已应用到主分支的更改。

这种方法通过将压力施加在工具上，通过提供减少管理所有这些更改摩擦力的工具来实现平滑集成。

#### 通过标志集成

随着更多人体验到以 Pull Request 为核心的集成计划的一些痛苦和挫折，其他程序员一直倡导不为工作使用单独的分支。相反，他们在部署的主分支上工作，并使用“功能标志”或其他技术，确保新代码仅在特定条件下使用。

功能标志或其他配置用户可访问代码的方式，可以复杂到一个定义这些值的行政系统，或者像围绕代码块的简单条件语句。

我在本书中使用的项目更多地采用“与主干集成”策略，通过几个标志来改变显示的内容。协助的其他开发者对他们的进行 Pull Request，因为他们对代码库的理解不如我深。

这种方法将集成压力放在开发者身上，以确保代码应执行的条件是正确的。

无论你选择哪种方法，执行任一方法的过程都是成熟的，并且有很多可用资源可以展示如何做。

#### 自动化集成与测试

#### 本地自动化

我强烈倡导对 Web 应用关键功能进行自动化测试的原因之一是，集成并部署的过程可能会非常有压力，尤其是在部署过程部分为手动操作的环境中。





#### 自动化集成与测试

那些每次向生产环境部署都令人倍感压力的场景都有一个共同点：缺乏测试来作为抵御集成问题的第一道防线。是的，我知道围绕遗留应用程序编写测试通常很困难。对我来说，这是值得的，因为它能增加对任何特定部署按预期运行的信心。

一旦有了某些测试就位，你就需要开始思考到达最终步骤“我的测试通过了吗？”所需的所有步骤。就本书中使用的示例项目而言，流程大致如下：

- 从 GitHub 拉取任何更改并将其应用到我的工作区。
- 创建一个全新的测试数据库并填充数据。
- 运行 `composer install` 以确保预期的依赖项到位。
- 运行我的测试。

如果测试通过，我会在该应用程序的生产服务器上进行手动部署。

如果我想要自动化这个过程怎么办？首先，我会创建一个可以在本地用一条命令完成这些操作的东西。对于使用 Composer 的项目，我可以在 `composer.json` 文件的 `scripts` 部分添加内容。

但首先，我会创建一个包含所有所需步骤的 `bash`[^1] 脚本。对于自动合并主分支更改的步骤，我持谨慎态度，因为这可能需要我在运行测试之前修复冲突或解决其他与 Git 相关的问题。

```bash
#!/usr/bin/env bash
PGPASSWORD=<redacted> psql -h 127.0.0.1 -U <redacted> ibl_test < ibl_stats.dump
composer install
vendor/bin/phpunit tests/
```

我已将此文件添加到项目中，命名为 `scripts/test-full.sh`。

对于这个项目，我会频繁获取生产数据库的快照，并在本地使用它们，始终将测试数据库重置为已知状态。然后，我使用 Postgres 的 CLI 工具导入该快照。接下来，我安装项目的所有依赖项，随后运行测试。

我已验证该脚本在本地可以运行，并且最终我的测试是通过的。

[^1]: https://www.gnu.org/software/bash

### 5. 持续集成

下一步是更新我们的 `composer.json` 文件，以便通过命令 `composer test-full` 执行此脚本。我在文件中当前定义的最后一项之后添加了以下内容：

```json
"scripts": {
    "test-full": "scripts/test-full.sh"
}
```

我已验证命令 `composer test-full` 现在可以运行我创建的 bash 脚本。我现在只需一条命令就可以完成所有工作。

#### 构建服务器

理想情况下，我还希望有一个自动系统来遵循这些步骤。这类系统通常被称为“构建服务器”或“持续集成”服务器。无论叫什么名字，它都是一个根据事件或触发器执行一系列用户定义命令的系统。

我首次接触持续集成系统是通过学习如何使用 Jenkins[^2] 来运行一个幻想体育平台 Python 代码的测试，该代码负责生成所有参与者的积分。Jenkins 仍然是那些希望围绕构建和部署流程实现自动化的用户的好选择。

如今，我使用 GitHub Actions[^3] 来完成这类工作。由于我所有的编码项目都使用 GitHub，利用它们提供的集成功能是合乎逻辑的。

由于 GitHub Actions 与语言无关，你必须告诉它去做很多配置工作和软件包安装，这些工作你为了启动本地开发环境已经做过了。

它们的文档非常好；我建议你阅读它以了解正在发生的事情。这是我项目的 GitHub Actions 配置文件。别担心，我会解释其中发生的事情：

[^2]: https://www.jenkins.io
[^3]: https://github.com/features/actions

```yaml
1. name: Grumpy CI
2. on: [push, pull_request]
3. jobs:
4.   CI:
5.     runs-on: ubuntu-latest
6.     services:
7.       postgres:
8.         image: postgres:10.8
9.         env:
10.          POSTGRES_USER: <redacted>
11.          POSTGRES_PASSWORD: <redacted>
12.          POSTGRES_DB: ibl_stats_test
13.      ports:
14.        - 5432:5432
15.      options: --health-cmd pg_isready --health-interval 10s --health-timeout 5s --health-retries 3
16.      steps:
17.        - name: Checkout
18.          uses: actions/checkout@v2
19.          with:
20.            lfs: true
21.        - name: Checkout LFS objects
22.          run: git lfs checkout
23.        - name: Setup PHP
24.          uses: shivammathur/setup-php@v2
25.          with:
26.            php-version: 7.4
27.            extensions: mbstring, intl, pdo_pgsql
28.        - name: Get composer cache directory
29.          id: composer-cache
30.          run: echo "::set-output name=dir::$(composer config cache-files-dir)"
31.        - name: Cache composer dependencies
32.          uses: actions/cache@v2
33.          with:
34.            path: ${{ steps.composer-cache.outputs.dir }}
35.            key: ${{ runner.os }}-composer-${{ hashFiles('**/composer.lock') }}
36.            restore-keys: ${{ runner.os }}-composer-
37.        - name: Install dependencies
38.          run: composer install --no-progress --prefer-dist --optimize-autoloader
39.        - name: Seed DB
40.          run: PGPASSWORD=<redacted> psql -U <redacted> ibl_test < ibl_stats.dump
41.        - name: Run PHPUnit tests
42.          run: vendor/bin/phpunit tests
```

所有这些工作都在某种容器化环境中进行。

从顶部开始，我赋予此流程一个名称，并告诉它我希望它响应任何与 GitHub 相关的推送事件或拉取请求。

接下来，我告诉它我要使用最新可用的 Ubuntu[^4] Linux 版本。GitHub 也会安装一组默认软件包。其他软件包的安装可以在后续步骤中进行。

定义好这些之后，我必须声明我想使用他们的一个 Postgres 容器，并指定我需要的某些配置值，同时添加一个健康检查选项，使整个流程暂停，直到 Postgres 容器启动并运行且准备好接受连接。

然后是一系列我希望遵循的步骤。第一步是检出正在推送的代码或拉取请求涉及的代码。

下一步是针对此项目特有的，但你可能会有兴趣。你是否有一些大文件（例如，Postgres 数据库转储文件）需要纳入版本控制？GitHub 不允许你添加那么大的文件。

幸运的是，当 GitHub 拒绝接受包含我数据库转储的推送时，它指引我去查看 Git Large File Storage[^5] 项目并使用它替代。在进行了一些仓库重置和回溯工作后，我成功地将数据库转储文件添加到了仓库中。文件 tbl_stats.dump 实际上是一个文本文件，包含一些元数据和指向文件下载位置的指针。

检出文件后，我要求安装 PHP，指定版本以及要安装的其他扩展。

接下来，我查找 Composer 的缓存位置，然后告诉 Composer，嗯，使用那个缓存！在那之后，我安装所有与 composer 相关的依赖项。

接着，我通过将该数据库转储的内容应用到我新创建的 Postgres 数据库来进行一些数据库种子填充。

最后一步是让构建系统运行我的 PHPUnit 测试。

现在，GitHub 遵循我在本地执行的相同步骤，以便我可以继续集成代码，并希望减少进入生产环境的 bug 数量。

我希望你可以将我提供的示例 GitHub Action 文件作为你自己构建系统的模板。基本上，几乎任何你为了到达可以运行测试的状态而需要做的事情，都可以在这里重复执行。

[^4]: https://ubuntu.com
[^5]: https://git-lfs.github.com

## 6
# 接下来做什么？

就像几乎所有与你 PHP 代码的自动化测试编写相关的事情一样，这是一段不会停止的旅程。我总是在学习新事物！我所有工作的目标目标是：

- 开发人员使用 TDD 创建或更新功能。
- CI 系统获取他们的补丁，并针对补丁运行综合测试套件。
- 如果所有测试通过，补丁将被合并并部署到生产环境。

达到这种状态可能需要大量工作；某些代码库和应用程序可能永远无法达到那里。然而，我们永远不应停止尝试使用那些鼓励代码中清晰意图、在用户看到问题之前提醒我们问题以及允许自信部署的工具。

在这一部分，我想简要谈谈我最近注意到的一些与测试互补的工具方面的事情。它们不需要整整一章的篇幅，但我认为花一点时间深入了解一下是值得的。




### 6. 接下来是什么？

#### 编辑器/IDE 集成

如前所述，在进行 PHP 编码工作时，我倾向于使用 PhpStorm。开箱即用的情况下，它自带了许多工具，使编写 PHP 代码变得更加容易。但其真正的优势在于其插件系统，该系统允许第三方扩展功能并集成集成点，以便在 IDE 内部使用 CLI 工具。

如果外部工具可以轻松地在 IDE 内使用，就花点时间去配置它。我更喜欢那种点击按钮即可运行 PHPUnit 测试用例的能力，而不必总是将焦点切换回终端 shell。

减少工具使用中的摩擦至关重要。我总是观察其他开发者是如何完成类似任务的。视频结对会话——其中我观看他人如何充分利用他们的工具——是重新审视和评估我所做之事的绝佳方式。

#### 容器化开发环境

在我评估 [Visual Studio Code](https://code.visualstudio.com)[^1] 时，我受到长期在线好友 Alvaro Videla[^2] 的鼓励，去查看 [Remote Containers](https://code.visualstudio.com/docs/remote/create-dev-container)[^3] 扩展，该扩展提供了许多其他编辑器所缺失的粘合剂，允许你使用 [Docker](https://docker.com)[^4] 创建和使用容器化开发环境。从阅读文档的第一部分到拥有一个与 Visual Studio 协同工作的可用开发环境，我花了不到 30 分钟。

我也知道你可以使用 Docker 和 PhpStorm 做类似的事情，但我自己的体验没有 Code 提供的那么顺畅。确保项目中的所有开发者拥有一致且可重复的开发环境，可以在消除“在我这里能运行”类 bug 方面大有帮助。

[^1]: https://code.visualstudio.com
[^2]: https://twitter.com/old_sound
[^3]: https://code.visualstudio.com/docs/remote/create-dev-container
[^4]: https://docker.com

![](img/ca14a770dd3609a915e3031a0db42a46_53_0.png)

> Chris Hartjes 自 1998 年起一直帮助人们构建各种大小和形状的 PHP 应用程序，自 2005 年起重点关注对其进行测试。除了撰写关于测试的文章外，他还参与了开源项目，并周游各地在会议上演讲。

他目前住在加拿大安大略省 Lucan-Biddulph 的雪域荒野中的家中。

# 了解一位愤世嫉俗的程序员如何改进他自己的代码库，包括使用的工具及其原因。

我觉得“测试”这一概念很难向初级程序员解释：“我们将编写确保你其他代码按预期工作的代码”。所有这些背后的假设是你已经知道如何使用所选语言编写计算机程序！这使得向初学者或经验不足的程序员教授它变得非常困难。当你将此与 PHP 不强制要求任何特定结构相结合时，你就拥有了一个只有真正有动力的人才会学习测试的环境。

《互补的 PHP 测试工具烹饪书》是我试图为那些已经拥有编写测试经验但希望提升水平的 PHP 程序员提供额外工具的一种方式。我相信，通过学习测试相关的技能（无论是技术还是核心技能），你将能够使用几乎任何测试框架和几乎任何 PHP 应用程序来编写测试。

在整个书中，我将向你展示我如何为我最古老的、仍在使用基于 PHP 的 web 应用程序添加有针对性的测试覆盖。它自 2004 年以来一直在运行，而我每隔几年更新一次基础框架，CakePHP。

