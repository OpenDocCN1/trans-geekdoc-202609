# 爱抱怨的程序员的可测试 PHP 应用构建指南

\*   \*   \*   \*   \*

这是一本 [Leanpub](http://leanpub.com) 书籍。Leanpub 赋能作者和出版商使用精益出版流程。[Lean Publishing](http://leanpub.com/manifesto) 是指使用轻量级工具并通过多次迭代发布进行中的电子书，以获取读者反馈，在拥有合适的书籍后调整方向并建立势头。

\*   \*   \*   \*   \*

# 2 致谢

首先，我要感谢我的技术审阅者。他们抓住了我遗漏的所有细节，使本指南成为现在的样子。因此感谢（无特定顺序）Peter Meth、Joel Perras、Matthew Turland 和 Remi Woler 的帮助。更好的指南来自他人的贡献。

其次，我要感谢 PHP 社区中那些不断突破界限、始终大声清晰地谈论最佳实践重要性，同时努力回馈社区的人们。那些人激励我继续撰写和演讲关于我感兴趣且希望你也感兴趣的话题。我有时会觉得与“主流”PHP 社区脱节，但如果我的网络上的牢骚和抱怨激励了其他程序员提升自己的水平，那么我很感激自己产生了影响。

最后，我要感谢我的妻子 Claire，她在我从大学毕业的新手程序员到今天这个全面、经验丰富、极其爱发牢骚的程序员的旅程中一直陪伴着我。感谢她容忍程序员长时间盯着屏幕，而不是凝视伴侣美丽的眼睛。我的妻子是我做的一切事情的伙伴。

如 always，我欢迎你对本指南中的任何内容发表评论，有任何问题，或只是想听听我对编程相关各种话题的看法。棒球也是。

本指南是在 [Leanpub](http://leanpub.com) 的优秀人士帮助下构建的。我最初决定以文本加一些 [`AsciiDoc`](http://www.methods.co.nz/asciidoc/) 标记的方式撰写指南，这使得将其转换为 Leanpub 所要求的 [`Markdown`](https://en.wikipedia.org/wiki/Markdown) 变得更容易。我还使用 [`Pandoc`](http://johnmacfarlane.net/pandoc/) 来调整本指南中包含的三篇附赠文章的部分内容。

特别感谢 Elizabeth Gauthier 制作的精彩封面。我的妻子评论说它非常逼真。

不幸的是，本指南并不面向初学者程序员。编写可测试的应用是一件困难的事情，需要你已经具备扎实的编程背景。本指南面向的是有过编写测试经验、希望将技能提升到下一水平的 intermediate 级程序员。

如果你正在寻找编写单元测试的入门指南，我强烈推荐 [`PHPUnit` documentation](http://www.phpunit.de/manual/3.6/en/phpunit-book.html)。它涵盖了所有基础知识。

你可以通过电子邮件 chartjes@littlehart.net 联系到我，Twitter 上是 @grmpyprogrammer。我定期在 http://www.littlehart.net/atthekeyboard 上写博客。感谢你花时间查看本指南，希望你能从中获得帮助，更好地掌握测试 PHP 应用的能力。

# 3 测试很重要，可测试的应用更好

毫无疑问，PHP 世界在测试态度方面终于赶上了其他编程社区。因此，你可以从网上或你喜欢的零售商的书籍中找到大量非常好的资源。

这些信息大多集中在实际编写测试以及你需要编写的测试类型策略上。我发现大多数资源中缺少的是如何编写可以真正进行测试的应用。听起来很明显，至少对我来说是这样。

那里有一个公开的秘密：有些应用永远无法使用自动化测试工具进行测试。它们是以一种你只能编写检查其 HTML 输出的测试的方式构建的。这真的很遗憾，因为这种情况从不是有意为之。就像代码中的技术债务一样，它会随着时间的推移而积累，最终你会得到一个几乎像黑盒子的应用：你向其中输入数据，得到输出返回，却没有简单的方法来确定如果返回了你不期望的结果该如何修复。

但请不要误会：构建一个非平凡的可测试应用确实需要经验。很多经验。你会犯错。你需要在以后重构东西，并且经常会发现重构很痛苦，与你试图实现看似简单的功能请求相比更是如此。

我坚信自动化测试的力量可以给你一个可维护、可扩展且性能良好的应用。我并不总是能参与到致力于可测试性的应用开发中。这确实是对整个测试过程的一种不同看法。知道如何编写断言语句，或理解如何使用模拟对象来隔离正在测试的模块的组件是一回事；要创建一个可以从头到尾进行测试的应用又是另一回事。



# 构建可测试的应用

## 引言

我希望传达我对构建易于测试的应用的想法，并向你展示我用来让工作更轻松的一些技术。在本指南中，你将学习如何为你的应用创建合适的环境、一个名为 `Dependency Injection` 的编程概念，以及从命令行测试应用输出的一些最佳实践。

我真的认为，Web 应用的最佳架构是构建小型代码模块，然后将它们集成在一起以解决更大的问题。没有其他灵丹妙药可以构建复杂系统。我曾遇到过一句老话（我找不到出处），它说：“简单系统可以表现出复杂行为，但复杂系统只能表现出简单行为”。

保持你的模块、组件、库，无论你决定称它们为什么，都要小巧、可读，并且易于验证它们在隔离状态下或集成在一起时是否按预期工作。这样你将拥有一个非常容易编写测试的应用，并为你提供防止回归错误和其他意外道路颠簸的保护。

目标始终如一：创建一个工作流程，缩短代码从你选择的文本编辑器到生产环境所需的时间，同时尽可能减少错误。

## 构建可测试的应用很困难

如果你是一名 `PHP` 开发者有一段时间，你可能遇到过有人谈论测试代码的好处。[测试驱动开发 (TDD)](https://en.wikipedia.org/wiki/Test-driven_development)、[行为驱动开发 (BDD)](https://en.wikipedia.org/wiki/Behaviour_driven_development) 和 [功能测试](https://en.wikipedia.org/wiki/Functional_testing) 只是你可以使用的一些策略。不测试你的代码不应该是选项。

我也曾在那里：我不相信为我的代码编写测试的价值。我熟悉人们给出的所有借口：

*   “编写测试会让我变慢。”
*   “我们为什么不能只在浏览器中手动测试应用？”
*   “如果我不用写测试，这个功能早就完成了。”

说实话，这些都只是借口。鉴于 `PHP` 开发者可用的工具，没有理由不为你的应用编写测试。即使是那些抵制你将单元测试包装在单个组件周围的重构努力的可怕“不可测试应用”，也可以在自动化环境中进行测试。

投资自动化测试的理由很明显：在你的应用进入生产环境之前捕获的任何错误，与在生产环境中修复相比，在资源（金钱、开发时间）方面花费更少。在 [IBM 和 Microsoft 关于 TDD 的研究](http://www.infoq.com/news/2009/03/TDD-Improves-Quality) 中，他们发现了一些有趣的信息。使用 `TDD` 的项目比不使用 `TDD` 的项目完成时间长 20-40%。然而，生成的应用在生产环境中发现的错误少了 40-90%。如果你恰当地调整统计数据，20% 的额外时间换取 90% 更少的错误听起来如何？谁能对这种交易说不？

[`PHPUnit`](https://github.com/sebastianbergmann/phpunit/)，测试 `PHP` 代码的黄金标准，可以轻松集成到几乎任何项目中。通过 [`PEAR`](http://pear.php.net) 安装它，在你的应用中为测试创建一个目录，然后开始编写它们。然而，有时并非如此简单。并非每个应用都已为测试做好准备。

你是否使用第三方系统进行用户身份验证？你将不得不弄清楚如何模拟该系统的响应。你为与 Web 服务通信而硬编码了值？你将不得不提取它们并将它们放入配置文件中。现实是，一些应用在你甚至可以测试它们之前需要重构。

在本指南中，我将向你展示如何构建一个真正可测试的应用。当然我们从零开始，所以更容易，但我也会展示重构可能不太适合测试的代码的替代方案。

在每一章中，我们将涵盖不同的主题，这将提高你创建可为其创建测试的应用的能力。你可能遇到的一些问题很容易解决，而其他问题可能需要一些侵入性更改才能实现。

为了说明我认为的创建易于测试的应用的一些最佳实践，我将创建一个示例应用，利用我建议的许多内容。该应用的代码可通过我的 [Github 账户](https://github.com/chartjes/building-testable-applications) 找到

我们的配套应用基于一个模拟棒球联盟的网站。我自 1997 年以来一直参加 [互联网棒球联盟](http://www.ibl.org)，并使用现在非常过时的 [`CakePHP`](http://www.cakephp.org) 版本创建了该网站的这个版本。它确实完成了工作，但我一直想清理引擎盖下的东西并利用 `PHP 5.3` 的一些功能。

而不是复制整个应用，我提取了生成网站主页的那些部分。它可能是网站最复杂的面向公众的部分。它结合了多个模型的使用和相当复杂的模板使用。这是一个突出测试验证功能价值的绝佳候选。

尽管多年来我获得了“框架先生”的声誉，我们在这里根本不会使用框架。我认为重要的是向你展示，尽管 `PHP` 框架世界中的大多数主要参与者使为使用它们构建的应用编写测试变得容易，但你可以为几乎任何应用包装测试。

我使用了一组合并功能和设计模式。虽然我不沉迷于设计模式，但我相信对症下药。让我们看看我们使用的是什么：

*   `PHP 5.3.8` 安装在 `OS-X 10.7.2` 上，使用修改后的 [`Homebrew`](http://notfornoone.com/2010/07/install-php53-homebrew-snow-leopard/) 配方安装
*   用于代码覆盖率报告的 [`Xdebug`](http://www.xdebug.org) 扩展
*   用于提升 `PHP` 性能的 [`APC`](http://www.php.net/apc) 扩展
*   用于模板的 [`Twig`](http://twig.sensiolabs.org)
*   作为数据存储的 [`Postgres`](http://www.postgresql.org)
*   [`Pimple`](http://pimple.sensiolabs.org)，一个依赖注入容器，用作应用其他部分所需的对象和值的注册表

我还在我的 `MacBook` 上的 `Ubuntu 10.04` (`Lucid`) 虚拟机中测试了此应用。关于虚拟机在测试中的作用，将在后面的章节中详细介绍。

对于应用架构，我决定为应用的每个部分采用 `Page Controller` 结构。如果你使用过框架，你使用的是具有 `Front Controller` 结构的应用。这意味着每个请求都经过单个文件，然后框架本身解释请求并确定需要执行的控制器和操作对。

如 [Jason Sweat 关于设计模式的精彩书籍](http://www.phparch.com/books/phparchitects-guide-to-php-design-patterns/) 中所述的 `Data Mapper` 模式用于提供对数据库的访问。如果你认为可能需要更改你的数据存储，无论是迁移到集群解决方案还是切换到其中一种更新的 `NoSQL` 选项，数据映射器将有助于使该更改更容易。



在本指南中，我仅向你展示了伴随我们姊妹文章的测试的一瞥。请从 Github 获取代码副本并自行尝试应用程序和测试。代码可以从 [`github.com/chartjes/building-testable-applications`](https://github.com/chartjes/building-testable-applications) 下载，我认为拥有源代码将使本指南中概述的许多概念更容易理解。

# 5 环境一致性

说到底，以易于测试的方式构建你的应用程序需要纪律和对细节的关注。很多。我告诉你这一点，因为在你甚至写下第一行代码之前，你就必须做很多工作。

缺乏纪律的开发者最终会遇到大量本可修复的问题。如果你曾经遇到过“好吧，在我的电脑 / 笔记本 / 切片 / `EC2` 实例上它能运行”的说法，那么你就会明白我的意思。当我 100% 确信我的环境不是问题时，我也时不时会说出这些话。

这个问题可以如何解决？如果你只能做一件与代码无关的事情来帮助使你的应用程序更易于测试（自动化或其他），请确保你开发应用程序的环境与部署它的环境尽可能相似。你开发环境和生产环境之间的唯一区别应该是你正在操作的数据。

越来越少见的是遇到一个除了一个 `PHP` 脚本之外不依赖其他工具的应用程序。即使看看我们可用的最简单的编程栈：`LAMP`，即 `Linux` + `Apache` + `MySQL` + `PHP`。我正在进行的一个项目还包括 [`MongoDB`](http://mongodb.org)、[`Redis`](http://redis.io)、`APC` 和 [`Memcached`](http://memcached.org)。我可能遗漏了一些其他次要组件，但即使是这个列表也显示了一个相对简单的应用程序可能变得多么复杂。不管你选择使用哪些组件，确保每个环境都使用相同的一个至关重要。

实现这一点的最简单方法是实际上将你的开发环境与你进行开发工作的环境分开。这通常意味着你有两个选择：本地使用虚拟机或远程使用虚拟机。

我个人更喜欢本地使用虚拟机。大多数现代计算机可以在没有任何问题地运行 512MB 到 1GB 的虚拟机镜像。事实上，当进行开发工作时，即使同时运行 `MySQL` 和 `Memcached` 等一些额外组件，512MB 的虚拟机也会让你惊讶于其响应速度。要在本地虚拟机上工作，我觉得你真的只有两个选择：[`VMWare`](http://www.vmware.com/) 或 [`Virtualbox`](https://www.virtualbox.org/)

`VMWare` 和 `Virtualbox` 之间唯一的真正区别是，虽然 `VMWare` 是免费的，但它不像 `Virtualbox` 那样是开源的。我更喜欢使用开源解决方案，所以我选择 `Virtualbox`。使用你感觉舒适的任何工具，但它们都完成相同的任务：在你自己的机器上运行包含你选择的 operating system 的虚拟机。对于这两种选择，都有大量信息说明如何设置，以便你甚至可以本地编辑虚拟机上的代码。

对于 `VMWare` 用户，我能找到的最全面的关于为你设置本地开发的链接是这篇关于使用 VMWare Fusion 和 CentOS 创建 Drupal 开发环境的博客文章 [使用 VMWare Fusion 和 CentOS 创建 Drupal 开发环境](http://janaksingh.com/blog/drupal-development-osx-vmware-fusion-and-centos-53-43)。

如果你选择 `Virtualbox` 路线，我推荐使用 [`Vagrant`](http://vagrantup.com)，这是一个使用 `Virtualbox` 帮助你构建和分发虚拟化环境的工具。一旦你将事物配置好（你可以使用像 [`Chef`](http://www.opscode.com/chef/) 或 [`Puppet`](http://projects.puppetlabs.com/projects/puppet/) 这样的工具），你就可以创建开发人员和生产实例，这些实例可以在你的团队之间共享以开发和测试你的应用程序。为什么这是如此好的方法？你可以尝试你的应用程序，如果做类似意外删除数据库或搞砸应用程序所依赖的关联组件的配置文件的事情，只需将其丢弃即可。

你不必使用 `Chef` 和/或 `Puppet`，因为 `Vagrant` 可以只使用 shell 脚本作为其配置过程的一部分。技术审阅者和物理学家转机器语言程序员 Joel Perras 对 `Vagrant` 给了我以下建议：

> *   使用 `RVM` 安装最新版本的 Ruby（截至目前为 1.9.3），然后在自己的 gemset 中安装 `Vagrant`。这将为你节省 *很多* 以后的麻烦。我曾经花了 1.5 天调试一个 `Vagrant` 安装，每次加载时基本上都会崩溃，最后发现是开发者使用的 Ruby 版本与我测试时使用的版本不同。讽刺的是，我们并没有错过这一点。

> *   你不需要为了配置而疯狂使用 `Chef`/`Puppet`。`Vagrant` 还支持一种配置方法，让你可以指向一个 shell 脚本，该脚本将被执行，因此你可以用几行 `apt-get foo` 填充这个简单的文本文件，这将让你在不需要 `Chef`/`Puppet` 这种脑力扭曲的情况下走得很远。

现在，如果你不习惯在自己的桌面上摆弄虚拟机，一个很好的后备选择是在远程服务器上进行开发工作。`VPS` 账户（虚拟专用服务器）非常适合此用途，同时使用“云计算”服务如 [`Rackspace`](http://www.rackspace.com) 或 [亚马逊的 `AWS`](http://aws.amazon.com/) 来创建你可以工作的远程环境。我的现任雇主将我们的开发服务器运行在 Amazon 的 `EC2` 服务上。

对于习惯从 `CLI`（命令行界面）工作的用户，进行开发工作就像使用 `SSH` 连接到远程开发实例，然后使用你选择的为 `CLI` 设计的编辑器（通常是 `Vim` 或 `Emacs`）编辑代码一样简单。对于不太习惯这样工作的人来说，只要你的 GUI 编辑器支持通过 `SFTP` 或 `SSH` 连接，经过一点努力你就可以远程编辑这些文件。我发现当你需要进行各种小改动时，等待远程保存文件带来的性能损失很快就会变得烦人。我并没有发现使用 [`TextMate`](http://macromates.com) 配合 [`ExpanDrive`](http://expandrive.com) 的体验令人愉快。

撇开我对网络延迟的牢骚以及某些编辑器插件如 [`Vim`](http://www.vim.org) 和 `TextMate` 在网络连接上的行为不谈，你应该考虑使用虚拟机进行开发工作所带来的优势。为你的应用程序需求配置的虚拟机的分发是最终的一致性。

我们还见证了像 [`Orchestra`](http://orchestra.io) 和 [`Zend PHP Cloud`](http://www.zend.com/en/products/php-cloud/) 这样的服务的兴起，它们为那些希望在托管的预配置环境中运行其 `PHP` 应用程序的人提供服务。我喜欢这些服务，因为它们实际上在一致性方面帮助了你。部分原因是它们本身已经标准化了将支持的 `PHP` 版本、将支持的 `MySQL` 版本以及它们提供的其他组件。

这种东西与 `EC2` 或 `Rackspace` 等服务之间的区别在于，你实际上无法在本地开发环境中运行它的一个版本。虽然我非常喜欢 `Orchestra` 和 `PHP Cloud`，但在设置开发环境时，你必须小心不要偏离所提供的版本太远。



无论你选择什么解决方案，请记住目标：为应用程序存在的所有位置提供一致的环境。

# 6 静态代码分析

用于进行静态代码分析的工具在 PHP 的生命周期中出现得很晚。这类工具在 Java 或 C++ 等语言中更为常见：这些语言很容易创建复杂代码……如果失控则难以控制。

显然，对静态类型且编译的代码进行静态分析更容易。对动态语言进行适当的静态代码分析是困难的，并且一直是一些研究论文的主题。因此，将它们视为补充你正在做的事情的工具，而不是测试工具链的关键部分。

在本章中，我们将研究我在处理相当复杂的代码库时每天使用的几种工具。

对于多人需要协作的项目（或将其集成到自己的项目中），选择一种编码标准非常重要。这涵盖了制表符与空格、括号位置、变量命名约定等内容。当然，关于哪套编码标准是“最好”的，极客们争论不休，但最重要的是设定一个标准并遵循它。

你是否曾与一位程序员合作过，他的编码风格如此独特，以至于你能立刻分辨出哪些代码是他的？不要成为那样的人。遵循标准，把展现个性留给你的代码编辑器选择吧。

[PHP 代码嗅探器](https://github.com/squizlabs/PHP_CodeSniffer) 是一个 CLI 实用程序，它会将你的代码与特定标准进行比较。我发现它是一个有用的工具，可以确保你的代码保持有序和一致。

让我们在为本项目创建的一个文件上运行它，这是一个用于与我们的 Postgres 数据库通信以获取模拟棒球联赛中特许经营信息的数据映射器。

```
chartjes@yggdrasil [09:39:25] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpcs --standard=Zend FranchiseMapper.php 

FILE: /Users/chartjes/Sites/local.ibl/lib/ibl/FranchiseMapper.php
FOUND 4 ERROR(S) AND 5 WARNING(S) AFFECTING 9 LINE(S)
   6 | ERROR   | Expected 0 spaces before opening brace; 1 found
   7 | ERROR   | Protected member variable "conn" must contain a leading
     |         | underscore
   8 | ERROR   | Protected member variable "map" must contain a leading
     |         | underscore
  15 | WARNING | Line exceeds 80 characters; contains 86 characters
  77 | WARNING | Line exceeds 80 characters; contains 84 characters
 139 | WARNING | Line exceeds 80 characters; contains 90 characters
 142 | ERROR   | Line exceeds maximum limit of 120 characters; contains 181
     |         | characters
 152 | WARNING | Line exceeds 80 characters; contains 117 characters
 154 | WARNING | Line exceeds 80 characters; contains 86 characters

Time: 1 second, Memory: 5.50Mb
```

啊，看它发现了所有这些问题。啧啧，哈特耶斯先生。那里面有些懒惰。关于行长度的抱怨（使内容可读性降低）以及未遵循受保护变量的正确命名约定。

我现在就去修复这些问题，但让我们看看如果使用它默认的标准会发生什么。

```
chartjes@yggdrasil [09:39:37] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpcs FranchiseMapper.php 

FILE: /Users/chartjes/Sites/local.ibl/lib/ibl/FranchiseMapper.php
FOUND 13 ERROR(S) AND 5 WARNING(S) AFFECTING 18 LINE(S)
   2 | ERROR   | Missing file doc comment
   5 | ERROR   | Missing class doc comment
   6 | ERROR   | Expected 0 spaces before opening brace; 1 found
  10 | ERROR   | Missing function doc comment
  15 | WARNING | Line exceeds 85 characters; contains 86 characters
  20 | ERROR   | You must use "/**" style comments for a function comment
  36 | ERROR   | Missing function doc comment
  53 | ERROR   | Missing function doc comment
  74 | ERROR   | Missing function doc comment
  95 | ERROR   | Missing function doc comment
 109 | ERROR   | Missing function doc comment
 127 | ERROR   | Missing function doc comment
 136 | ERROR   | Missing function doc comment
 139 | WARNING | Line exceeds 85 characters; contains 90 characters
 142 | WARNING | Line exceeds 85 characters; contains 181 characters
 149 | ERROR   | Missing function doc comment
 152 | WARNING | Line exceeds 85 characters; contains 117 characters
 154 | WARNING | Line exceeds 85 characters; contains 86 characters

Time: 0 seconds, Memory: 6.75Mb
```

那是一组完全不同的问题。在这种情况下，它期望我在所有方法周围加上 [文档块](https://en.wikipedia.org/wiki/PHPDoc) 注释，并附带一些关于行长度的警告。

使用它默认包含的所有标准来分析你的代码是一个有趣的练习，只是为了看看关于代码应该如何显示的其他想法。PHP 代码嗅探器网站还展示了如何创建自己的编码标准，如果你想承担这样的任务。

然而，确保 100% 符合 PHP 代码嗅探器的报告并不总是切实可行的目标。例如，它抱怨我在模型类中使用非驼峰式、受保护的变量名。它们是受保护的，以防止开发者直接访问，并且是非驼峰式的，以匹配数据库表本身中的值。

修改代码以允许模型变量使用驼峰式并以下划线为前缀（这是 Zend 约定）可能也不切实际。动态确定需要返回哪个模型变量的代码也需要被修改。

我应该做必要的工作来实现它吗？这取决于。你是否有可以运行的测试，以便在幕后调整使其实现？当然有！

向你展示我对代码所做的更改的无聊补丁是不够的。相反，让我向你展示代码本身，我们将讨论必须做什么。

我真的只需要在一个地方更改代码：我扩展所有其他模型的 `BaseModel`：

```
<?php

// Base data model that all our existing models will extend off of
namespace IBL;

class BaseModel
{
    protected $_id;

    public function setId($id) 
    {
        // Never allow the ID for a model to be overwritten
        if (!$this->_id) {
            $this->_id = $id; 
        } 
    }

    public function __call($name, $args)
    {
        if (preg_match('/^(get|set)(\w+)/', $name, $match)) {
            $attribute = $this->validateAttribute($match[2]);

            if ($match[1] == 'get') {
                return $this->{$attribute};
            } else {
                $this->{$attribute} = $args[0];
            }
        } else {
            throw new \Exception(
                'Call to undefined ' . 
                __CLASS__ . 
                '::' . 
                $name . 
                '()'
            ); 
        }
    }
    
    protected function validateAttribute($name) 
    {
        // Convert first character of the string to lowercase 
        $field = '_' . $name;
        $field[1] = strtolower($field[1]); 

        // We don't use __CLASS__ here because there are scope problems
        $currentClass = get_class($this);

        if (in_array($field, array_keys(get_class_vars($currentClass)))) {
            return $field; 
        }

        return false;
    }
}
```

在此之前，我曾有一个 `inflect()` 模块，它使用 PHP 5.3 闭包将类似 `HomeTeamId` 的内容转换为 `home_team_id`，然后将其与模型可用的类变量进行匹配。

为了使类模型的所有类变量符合标准，我不再需要词形转换器。当然，那是一段很不错的代码，使用闭包作为回调，但这种巧妙性并不需要。



还请注意我对代码中使用的快捷方式的注释，该快捷方式用于将属性的第一个字母数字字符设为小写。我需要这样做是因为代码会取类似 `setHomeTeamId` 的内容并去掉 `set` 部分。为了匹配它，我需要将其更改为 `_homeTeamId` 以符合受保护变量的编码标准。

所以现在我的所有代码都符合 `Zend` 编码标准。接下来看看其他事情，比如这个看起来不错的代码有多混乱。

在更新我的代码、消除所有与 `FranchiseMapper` 代码符合 `Zend` 标准相关的警告之后，下一个要使用的工具是 [PHP Mess 检测器](http://phpmd.org)。

该工具的工作是检查你的代码的复杂性并提出修复建议。人们出于最无辜的原因在代码中创建复杂的方法，但（这里是在说废话）复杂性是可维护性和可扩展性的敌人。那么，让我们看看它对 `FranchiseMapper` 说了什么。

```
chartjes@yggdrasil [10:30:20] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpmd FranchiseMapper.php text codesize,design,naming,unusedcode

FranchiseMapper.php:5 This class has too many methods, consider 
    refactoring it.
FranchiseMapper.php:137 Avoid variables with short names like $id
```

哎，一点都不好玩。那里没有什么真正的新消息。但是如果我们把它用在更混乱的东西上呢？以下是我在工作中完成的某个复杂库上运行的同一个 `phpmd` 命令。

```
> % phpmd lib/vendor/Moontoast/RpcApi.php text 
    codesize,design,naming,unusedcode
RpcApi.php:12    The class RpcApi has an overall complexity of 77 which 
    is very high. The configured complexity threshold is 50 
RpcApi.php:12    The class RpcApi has a coupling between objects value
    of 14. Consider to reduce to number of dependencies under 13
RpcApi.php:27    Avoid unused parameters such as '$params'.
RpcApi.php:114   The method getProduct() has a Cyclomatic Complexity of 14.
RpcApi.php:114   The method getProduct() has an NPath complexity of 655.
RpcApi.php:114   Avoid really long methods.
RpcApi.php:114   Avoid variables with short names like $id
RpcApi.php:234   Avoid unused parameters such as '$params'.
RpcApi.php:282   The method getStore() has a Cyclomatic Complexity of 12.
RpcApi.php:282   Avoid really long methods.
RpcApi.php:302   Avoid unused local variables such as '$price'.
RpcApi.php:303   Avoid unused local variables such as '$previousPrice'.
RpcApi.php:398   Avoid unused parameters such as '$csc'.
RpcApi.php:477   The method saveCart() has a Cyclomatic Complexity of 26.
RpcApi.php:477   The method saveCart() has an NPath complexity of 5644802.
RpcApi.php:477   Avoid really long methods.
RpcApi.php:477   Avoid variables with short names like $id
RpcApi.php:588   Avoid excessively long variable names like 
    $useBillingForShipping
RpcApi.php:608   Avoid excessively long variable names like 
    $shippingAddressObject
RpcApi.php:671   Avoid unused local variables such as '$gateway'.
RpcApi.php:702   Avoid variables with short names like $q
RpcApi.php:707   Avoid variables with short names like $mm
```

你可以看到各种可以改进代码的地方。PHP Mess Detector 网站上对这些消息的含义有很好的文档说明，尽管其中一些应该相当不言自明。

我个人使用 PHP Mess Detector 的经验是，它非常擅长识别我在代码中试图在一个方法中做太多事情或设计出可能过于复杂的算法以完成我要求它完成的任务的地方。看到那些关于未使用参数和局部变量的抱怨让我很惊讶，因为我通常非常谨慎地避免做这类事情。

减少代码中的“混乱”也有助于找到实际测试它的最佳方法。

在试图“尽快完成”时，最大的诱惑之一就是放松对代码重用或将功能提取到其自身方法（甚至是自己的类）中的努力，而是在各处复制粘贴代码。[PHP Copy Paste 检测器](https://github.com/sebastianbergmann/phpcpd) 会静态检查你的代码并识别出你在代码中似乎重复自己的行，使其成为将该代码重构为其自身方法候选。让我们看看它对我们信赖的 `FranchiseMapper` 说了什么

```
-> % phpcpd ./FranchiseMapper.php 
phpcpd 1.3.2 by Sebastian Bergmann.

0.00% duplicated lines out of 197 total lines of code.
```

FLAWLESS VICTORY。再次，这相当无聊。让我们看看工作项目中的另一段代码，这段代码处理来自用于生成电子商务网站商店[content]
还请注意我对代码中使用的快捷方式的注释，该快捷方式用于将属性的第一个字母数字字符设为小写。我需要这样做是因为代码会取类似 `setHomeTeamId` 的内容并去掉 `set` 部分。为了匹配它，我需要将其更改为 `_homeTeamId` 以符合受保护变量的编码标准。

所以现在我的所有代码都符合 `Zend` 编码标准。接下来看看其他事情，比如这个看起来不错的代码有多混乱。

在更新我的代码、消除所有与 `FranchiseMapper` 代码符合 `Zend` 标准相关的警告之后，下一个要使用的工具是 [PHP Mess 检测器](http://phpmd.org)。

该工具的工作是检查你的代码的复杂性并提出修复建议。人们出于最无辜的原因在代码中创建复杂的方法，但（这里是在说废话）复杂性是可维护性和可扩展性的敌人。那么，让我们看看它对 `FranchiseMapper` 说了什么。

```
chartjes@yggdrasil [10:30:20] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpmd FranchiseMapper.php text codesize,design,naming,unusedcode

FranchiseMapper.php:5 This class has too many methods, consider 
    refactoring it.
FranchiseMapper.php:137 Avoid variables with short names like $id
```

哎，一点都不好玩。那里没有什么真正的新消息。但是如果我们把它用在更混乱的东西上呢？以下是我在工作中完成的某个复杂库上运行的同一个 `phpmd` 命令。

```
> % phpmd lib/vendor/Moontoast/RpcApi.php text 
    codesize,design,naming,unusedcode
RpcApi.php:12    The class RpcApi has an overall complexity of 77 which 
    is very high. The configured complexity threshold is 50 
RpcApi.php:12    The class RpcApi has a coupling between objects value
    of 14. Consider to reduce to number of dependencies under 13
RpcApi.php:27    Avoid unused parameters such as '$params'.
RpcApi.php:114   The method getProduct() has a Cyclomatic Complexity of 14.
RpcApi.php:114   The method getProduct() has an NPath complexity of 655.
RpcApi.php:114   Avoid really long methods.
RpcApi.php:114   Avoid variables with short names like $id
RpcApi.php:234   Avoid unused parameters such as '$params'.
RpcApi.php:282   The method getStore() has a Cyclomatic Complexity of 12.
RpcApi.php:282   Avoid really long methods.
RpcApi.php:302   Avoid unused local variables such as '$price'.
RpcApi.php:303   Avoid unused local variables such as '$previousPrice'.
RpcApi.php:398   Avoid unused parameters such as '$csc'.
RpcApi.php:477   The method saveCart() has a Cyclomatic Complexity of 26.
RpcApi.php:477   The method saveCart() has an NPath complexity of 5644802.
RpcApi.php:477   Avoid really long methods.
RpcApi.php:477   Avoid variables with short names like $id
RpcApi.php:588   Avoid excessively long variable names like 
    $useBillingForShipping
RpcApi.php:608   Avoid excessively long variable names like 
    $shippingAddressObject
RpcApi.php:671   Avoid unused local variables such as '$gateway'.
RpcApi.php:702   Avoid variables with short names like $q
RpcApi.php:707   Avoid variables with short names like $mm
```

你可以看到各种可以改进代码的地方。PHP Mess Detector 网站上对这些消息的含义有很好的文档说明，尽管其中一些应该相当不言自明。

我个人使用 PHP Mess Detector 的经验是，它非常擅长识别我在代码中试图在一个方法中做太多事情或设计出可能过于复杂的算法以完成我要求它完成的任务的地方。看到那些关于未使用参数和局部变量的抱怨让我很惊讶，因为我通常非常谨慎地避免做这类事情。

减少代码中的“混乱”也有助于找到实际测试它的最佳方法。

在试图“尽快完成”时，最大的诱惑之一就是放松对代码重用或将功能提取到其自身方法（甚至是自己的类）中的努力，而是在各处复制粘贴代码。[PHP Copy Paste 检测器](https://github.com/sebastianbergmann/phpcpd) 会静态检查你的代码并识别出你在代码中似乎重复自己的行，使其成为将该代码重构为其自身方法候选。让我们看看它对我们信赖的 `FranchiseMapper` 说了什么

```
-> % phpcpd ./FranchiseMapper.php 
phpcpd 1.3.2 by Sebastian Bergmann.

0.00% duplicated lines out of 197 total lines of code.
```

FLAWLESS VICTORY。再次，这相当无聊。让我们看看工作项目中的另一段代码，这段代码处理来自用于生成电子商务网站商店前端的 Flash 文件的 [AMF（Action Message Format）](https://en.wikipedia.org/wiki/Action_Message_Format) 调用：

```
-> % phpcpd lib/services/AMF_Checkout.php 
phpcpd 1.3.3 by Sebastian Bergmann.

Found 2 exact clones with 52 duplicated lines in 1 files:

  - AMF_Checkout.php:60-68
    AMF_Checkout.php:576-584

  - AMF_Checkout.php:88-132
    AMF_Checkout.php:602-646

7.21% duplicated lines out of 721 total lines of code.

Time: 0 seconds, Memory: 6.50Mb
```

这有点好一点。第一次分析让我担心，但 9 行重复代码并不算太糟糕。仔细检查后发现，它是同一组 ‘if’ 语句被执行。我会考虑是否要将其提取为它自己的方法。

第二个问题值得检查。几乎有 50 行代码被重复了。 definitely 值得提取到它自己的方法中，以将其减少到只有 50 行代码。代码越少，bug 越少……通常如此。

我发现使用这些工具的最佳方式是配合你尝试拥有良好组织的代码的努力。如果你发现自己在生成他人易于理解的代码时遇到问题，这些工具可用于识别代码库中出现摩擦的地方。

# 7 使用依赖注入解耦对象

每当我第一次遇到一个代码库时，我最初的想法是如何在修改应用程序的某些部分以满足新需求或修复错误时测试各个组件。在完美的世界里，你将继承一个具有大量相关测试和良好代码覆盖率的应用程序。

大多数时候你有一个正在工作的应用程序……而且没有办法隔离测试组件。这并不意味着应用程序很糟糕，这只是意味着在没有 nagging 的感觉你可能破坏了其他东西的情况下进行更改会很困难。

大多数 PHP 开发者在他们的应用程序中使用面向对象编程。你创建对象来完成某些任务，如果你采用了 `Model-View-Controller` 设计模式，你希望在模型中隔离业务逻辑，在控制器中处理路由请求，并在漂亮标记的模板中显示输出。

测试其中一些东西的问题在于大多数开发者倾向于创建紧密耦合的对象，这些对象执行经常偏离其原始目的的任务。所以如果你有一个需要测试的代码模块，首先要看的是解耦。

为了指导你解耦代码并将其移向由精心制作的模块组成的场景，这些模块通过彩虹和独角兽 sightings 相互交谈，我提供的第一个工具是概念 [德米特法则](http://en.wikipedia.org/wiki/Law_of_Demeter)。

我最喜欢的编程书籍之一 [《程序员修炼之道》](http://pragprog.com/book/tpp/the-pragmatic-programmer) 是这样描述德米特法则的：

> 德米特法则对于函数而言规定，对象的任何方法都应只调用属于它自身的方法、传递给该方法的任何参数、它创建的任何对象以及任何直接持有的组件对象。




## 迪米特法则与依赖注入

## 遵循规则的意义

那么真正的意义是什么？意义在于，只要你尽可能地遵守这些规则，你就能在修改代码时减少阻力，并且使测试变得更容易，因为在真正尝试隔离测试组件时，你将能够使用模拟对象。

## 拥抱迪米特法则的弊端

然而，真正拥抱迪米特法则的一个弊端是，你会发现自己写了大量“包装代码”，这种代码接收传入的内容，然后将其转交给其他函数或对象进行处理。

## 通过依赖注入保持积极面

我们如何保持在 `LoD` 的积极面？其实很简单：我们使用依赖注入（以下简称 `DI`）来传入我们的类完成工作所需的各种对象和值，并且不强迫它们对我们提供的依赖做出任何假设，除了它们的公共接口。

## 构造函数注入

我更喜欢使用的方法称为构造函数注入。通常我会为我的对象创建一个构造函数，接受它所需的所有依赖。这可以通过为你的类创建 `__construct()` 方法轻松实现。我想一些代码示例是有必要的。

## 示例应用：模型与数据映射器

在我们的示例应用中，我们使用两种类型的对象与数据源交互。一个 `Model` 对象，它提供数据库中单条记录的表示形式，以及一个数据映射器对象，它与数据源通信并进而创建 `Model` 对象。

现在，如果我不关心可测试性，我会创建一个执行所有这些功能的大对象。我会在构造函数中创建数据库连接，然后编写与数据库通信并将我想要的结果返回给我的方法。有道理，对吧？从测试角度来看可不是。

如果我们在这里应用迪米特法则，根据规则，我们的 `Model` 不需要知道有关 `Mapper` 的任何信息，除了如何使用它。这样我们就可以自由地做一些事情，比如在真正深入测试时提供模拟 `Mappers`。

## 使用依赖注入进行测试

那么如果我想测试一下怎么办？如果我在 `Mapper` 的构造函数中硬编码了 DB 连接的细节和创建方式，那么我无法在仅用于测试的数据库上运行任何测试。以下是一个测试，展示了仅仅撒上一点 `DI` 如何让你轻松测试代码。

```php
<?php

include 'test_bootstrap.php';

class FranchiseModelTest extends \PHPUnit_Framework_TestCase
{
    protected $_conn;

    public function setUp()
    {
        $this->_conn = new PDO(
            'pgsql:host=localhost;dbname=ibl_stats', 
            'stats', 
            'st@ts=Fun'
        ); 
    }

    ...

    public function testSaveUpdatesDatabase()
    {
        $mapper = new IBL\FranchiseMapper($this->_conn);
        $franchise = new IBL\Franchise();
        $franchise->setId(25);
        $franchise->setNickname('TST');
        $franchise->setName('Test Team');
        $franchise->setConference('Conference');
        $franchise->setDivision('Division');
        $franchise->setIp(0);
        $mapper->save($franchise);

        // Update existing model
        $franchise->setIp(35);
        $mapper->save($franchise);
        
        // Reload Franchise record and compare them
        $franchise2 = $mapper->findById($franchise->getId());
        $this->assertEquals(35, $franchise2->getIp());

        // Clean up the franchise
        $mapper->delete($franchise);
    }
}
```

这有道理，对吧？我们的 `Mapper` 不需要知道创建数据源连接的细节。它只需要知道它已被赋予一个可用的连接。

## FranchiseMapper 的 save() 方法

为了进一步看到这一点的工作原理，你甚至可以查看 `FranchiseMapper` 的 `save()` 方法。

```php
<?php

namespace IBL;

class FranchiseMapper
{
    protected $_conn;
    protected $_map = array();

    ...

    public function save(\IBL\Franchise $franchise)
    {
        if ($this->findById($franchise->getId())) {
            $this->_update($franchise); 
        } else {
            $this->_insert($franchise); 
        }
    }

    protected function _insert(\IBL\Franchise $franchise) 
    {
        try {
            $sql = "
                INSERT INTO franchises 
                (nickname, name, conference, division, ip, id) 
                VALUES(?, ?, ?, ?, ?, ?)";
            $sth = $this->_conn->prepare($sql);
            $binds = array(
                $franchise->getNickname(),
                $franchise->getName(),
                $franchise->getConference(),
                $franchise->getDivision(),
                $franchise->getIp(),
                $franchise->getId()
            );
            $sth->execute($binds);
        } catch(\PDOException $e) {
            echo "A database problem occurred: " . $e->getMessage(); 
        }
    }

    protected function _update(\IBL\Franchise $franchise)
    {
        try {
            $sql = "
                UPDATE franchises 
                SET nickname = ?, 
                name = ?, 
                conference = ?, 
                division = ?, 
                ip = ? 
                WHERE id = ?";
            $sth = $this->_conn->prepare($sql);
            $fields = array(
                'nickname', 
                'name', 
                'conference', 
                'division', 
                'ip', 
                'id'
            );
            $binds = array();

            foreach ($fields as $fieldName) {
                $field = $this->_map[$fieldName];
                $getProp = (string)$field->accessor;
                $binds[] = $franchise->{$getProp}();
            }

            $sth->execute($binds);
        } catch(\PDOException $e) {
            echo "A database problem occurred: " . $e->getMessage(); 
        }
    }
}
```

再次，我们告诉我们的方法“嘿，这里有一个你需要使用的项目”，它只知道如何使用它，而不知道内部是什么样的。

## 重构示例：访问控制层

这里有一个场景，可能会更清楚地说明如何借助 `LoD` 和 `DI` 重构代码。

想象一下，你正在创建自己的框架，并且正在编写一个访问控制层（简称 `ACL`）组件。对于不熟悉这个概念的人来说，`ACLs` 会查看你试图访问的资源，并将其与你当前拥有的用户级别进行比较，然后告诉你该用户是否可以访问该资源。它可能看起来像这样：

```php
<?php

namespace Grumpy;

class Acl {
    protected $_acls;

    ...

    public function accessAllowed()
    {
        $request = \Grumpy\Context::getRequest();

        return ($this->_acls[$request->getUri()] >= $_SESSION['user_level']); 
    }
        
}

// Meanwhile inside your controller

$acl = new \Grumpy\Acl();

if (!$acl->accessAllowed()) {
    \Grumpy\View::render('access_denied.tmpl');
} else {
    \Grumpy\View::render('show_stolen_cc.tmpl');
}
```

我们通过静态方法调用引入请求对象，并且直接从会话中获取用户信息。这是非常常见的编码实践，但完全不可测试。让我们稍微清理一下。

```php
<?php

namespace Grumpy;

class Acl {
    protected $_acls;
    protected $_request;
    protected $_userLevel;
    
    ...

    public function __construct($request, $userLevel)
    {
        ...

        $this->_request = $request;
        $this->_userLevel = $userLevel;
    }

    ...

    public function accessAllowed()
    {
        return ($this->_acls[$this->_request->getUri()] 
            >= $this->_userLevel); 
    }
        
}

// Meanwhile inside your controller

$acl = new \Grumpy\Acl($this->request, $_SESSION['user_level']);

if (!$acl->accessAllowed()) {
    \Grumpy\View::render('access_denied.tmpl');
} else {
    \Grumpy\View::render('show_stolen_cc.tmpl');
}
```

## 依赖注入容器

现在你已经了解了如何使用构造函数注入将依赖项传递到你的对象中，我们可以通过使用 [依赖注入容器](http://fabien.potencier.org/article/12/do-you-need-a-dependency-injection-container)，以下简称 `DIC`，来探索提升能力等级。



## 依赖注入容器

## 管理复杂对象

在某个阶段，你的应用变得足够大，你会发现自己不仅要管理大量对象，还要管理复杂的对象。你可能会问自己如何为了依赖注入的目的移动这些对象。处理此问题的最佳方法是把你知道需要移动的对象放入容器中，然后在需要时简单地检索它们。

## Web 应用框架

那么什么样的应用需要这种东西？能最大程度利用 DIC 的首选对象是 Web 应用框架。为什么？大多数框架都高度面向对象，并使用大量对象来完成任务。如果你把用户很可能需要频繁使用的对象放在容器中，可以让框架用户更容易使用。然后它们可以被检索以供以后使用，已经配置好并且准备就绪。

## 使用 Pimple 的示例

考虑我们具有 `Model` 和 `Mapper` 结构的应用。我们可以使用容器来存储数据库连接对象，而不是每次都自己创建实例。在这里，我们将使用 `Pimple` 作为我们的 DIC。

```
<?php

// Inside our bootstrap

// Create our container
$container = new \Pimple();

// Inject our DB connection object for later reuse
$container['db_connection'] = function ($c) {
    return new PDO(
        'pgsql:host=localhost;dbname=ibl_stats', 
        'stats',
        'st@ts=Fun'
    );
};


// Then in a controller somewhere...
$mapper = new IBL\FranchiseMapper($container['db_connection']);
```

这种做法的好处是现在你的对象真的不需要知道任何关于它们正在使用的其他对象或参数的信息。如果你真的想对这种事情完全发疯，你可以在 `bootstrap` 中提前创建所有你的 `Mapper` 实例，然后在需要时直接从容器中取出它们。

```
<?php

// In the bootstrap, after having already added
// in the database connection
$container['franchise_mapper'] = function ($c) {
    return new \IBL\FranchiseMapper($c['db_container']);
};
$container['game_mapper'] = function ($c) {
    return new \IBL\GameMapper($c['db_container']);
};
```

我并不是说这是最佳实践，但它说明了 DIC 的正确使用可以在很大程度上使你的应用程序符合德米特法则所倡导的原则。

## 优点与注册表模式

那么，现在我们有了依赖注入容器，还能做什么呢？使用它！在很多方面，你也可以把它看作是“增强版注册表”。我通常使用充当信息注册表的组件。我存储在整个应用程序中需要持久保存的各种值，然后通过对这个 `registry` 或 `configuration` 对象或其他你想称呼它的调用来按需检索它们。

使用容器来管理依赖的另一个原因是它创建了一个可以找到它们的地方。没有它，你的代码会充斥着在注入之前实例化这些依赖的请求。再次想象这样一个场景：你正在将数据映射器从使用 `Postgres` 作为后端切换到使用 `MongoDB` 的映射器：遍历所有代码并替换所有创建旧映射器并替换为新映射器的实例会有多痛苦？如果你使用容器，你只需要在 `bootstrap` 中更改它。

能够在需要注入时提取依赖项，在尝试构建可测试的应用时很有帮助。它节省了你在每次使用前实例化它们的麻烦，而且如果你使用容器，你可以返回一个已经按你需要配置好的对象。

## 滥用容器

使用 DIC 也很容易被滥用。假设你有一个名为 `Omega` 的对象，它有三个你需要传入的依赖项：

```
<?php

class Omega
{
    protected $foo;
    protected $bar;
    protected $bizz;

    public function __construct($foo, $bar, $bizz)
    {
        $this->foo = $foo;
        $this->bar = $bar;
        $this->bizz = $bizz; 
    }
}

$dep1 = new Foo();
$dep2 = new Bar();
$dep3 = new Bizz();
$newOmega = new Omega($dep1, $dep2, $dep3);
```

你决定聪明地使用依赖注入容器来存储东西。然后你想“为什么我不直接传入容器，因为东西已经在里面了？”

```
<?php

class Omega
{
    protected $foo;
    protected $bar;
    protected $bizz;

    public function __construct($container)
    {
        $this->foo = $container['foo'];
        $this->bar = $container['bar'];
        $this->bizz = $container['biz']; 
    }
}

$container['foo'] = new Foo();
$container['bar'] = new Bar();
$container['bizz'] = new Bizz();
$newOmega = new Omega($container);
```

现在，假设我被分配在正常的开发流程中审查这段代码。我会看一下并立即指出你现在已经将依赖注入容器与 `Omega` 耦合了。

“如果以后你更改容器呢？那么你就必须遍历所有使用容器的现有代码并重新处理它们！”

如果你要使用依赖注入容器（我强烈推荐在中等到大型复杂度的应用中使用），那么只把它当作容器对待，并在将依赖项注入对象之前从中检索它们。

依赖注入是我认为每个开发人员都需要理解的概念，即使他们更喜欢不使用它。我也认为依赖注入是创建可以以最低摩擦与其他对象集成对象的关键部分。

## 测试、模拟对象与 CLI 兼容性

你可以在测试中借助模拟对象来减少代码的紧密耦合。模拟对象的概念非常简单：你创建一个对象在测试中的依赖项的表示，然后只为该对象创建测试成功所需的那些功能。这里有一个示例，结合了模拟对象的使用，并确保你的代码可以在 Web 和 `CLI` 上运行。

`PHP` 能够解决 Web 1.0 的问题并取得成功的部分原因在于它为 Web 而建。将此与常见的“竞争对手”如 `Python` 和 `Ruby` 对比，它们起初在服务器上运行，随着时间的推移建立了库和框架，使它们在 Web 应用中也能很好地工作。

鉴于 `PHP` 与创建网页紧密耦合，避免直接与语言中内置的那些 Web 特定功能对话需要付出努力。Cookies、sessions 和 `$_SERVER` 立刻浮现在脑海。对于 `PHP` 开发者来说，与这些东西的交互是第二天性。

但如果你想构建一个可以通过 `CLI`（命令行界面）工具如 `PHPUnit` 进行测试的应用，这就成了一个问题。你必须确保抽象掉对 Web 特定信息或函数的任何访问，以便当模块从 `CLI` 访问时你的应用仍然可以正常工作。Cookies 浮现在脑海，我相信通过更多研究你会找到更多只存在于 Web 上的例子。

让我们考虑一下我之前向你展示的你自己的 `ACL` 实现的例子。如果我没记错，它要求你访问应用中使用的 `request` 对象……这与 Web 绑定。然后它需要一个你存储在 `session` 中的值……这通常与 Web 相关，但在 `CLI` 环境中也可以使用。

一切希望都未丧失。在我们第一次快速重构中，我们使用依赖注入将获取 `request` 对象和我们需要的来自 `session` 的值移到了 `ACL` 对象本身之外。如果你脚本不是在 Web 请求的上下文中运行，你会如何处理这种情况？



```
<?php

// Now here is our test case

include 'test_bootstrap.php';

class AclTest extends \PHPUnit_Framework_TestCase
{
    ...
 
    public function testDashboardAcl()
    {
        // Create a mock object
        $testRequest = $this->getMock(
            '\Grumpy\Request', 
            array('getUri')
        );

        // Create our test response
        $testRequest
            ->expects()
            ->method('getUri')
            ->with('/dashboard');

        $testUserLevel = 3;
        $testAcl = new \Grumpy\Acl($testRequest, $testUserLevel);
        $response = $testAcl->accessAllowed();
        $this->assertTrue($response);
    }

}
```

再说一次，光为了让测试通过而做额外的工作似乎有些多余，但它说明了确保你的代码解耦到根本不在乎运行环境这一点，实际上可以非常简单。

# 8 像洋葱一样，你的应用有层次

我认为很明显，如果你想用任何自动化工具来测试你的应用程序，就必须将业务逻辑与显示逻辑分开。

我们都曾构建过那种“一团乱麻”的应用。你知道的，就是两三个 PHP 脚本，把检查 `$_GET` 值、然后分支去执行 MySQL 查询、再进一步遍历结果集输出内容的代码混在一起。所有东西都在一个地方，但当你需要更新某样东西时却极其困难。而你当然会在服务器上直接进行现场更新。我就是那样的人。不要再那样做了。生活太短暂，工具也太多了，不再有借口了。

大多数 Web 应用框架通过鼓励使用 [模型-视图-控制器软件架构模式](http://en.wikipedia.org/wiki/Model-view-controller) 来完成这项任务。为什么这是个好主意？因为它强制解耦应用程序的不同层。当然，除非框架本身构建不当。嘿，这种情况也会发生。

因此向这些 Web 应用框架取经。即使你不打算使用其中任何一个，因为你在使用自制的珍贵雪花框架 (`PSF`)，至少要聪明地构建它，让你的业务逻辑在一个地方，请求-响应逻辑在另一个地方，显示逻辑在别处，这样你可以独立地处理它们。

把这些东西看作你应用程序的层次。用食物作类比，你的模型，即代表应用程序将使用的数据的代码，是蛋糕的底层。你的控制器，它们作为特定请求的结果被调用，然后确定正确的响应应该是什么，是蛋糕的第二层，也许带一点馅。最后，你的展示层是蛋糕的糖霜和美味的配料。你希望能够随时对这些层次中的任何一个进行更改。

我已经能听到你说“但是 Chris，你真的有多常更改这类东西？”比我愿意承认的要频繁得多。没人能在构建应用程序时每次都做出正确的选择。现在，你可能会被困在一个特定的框架中，因为它需要很大的自律才能只使用你真正需要的框架部分。

你真正想要的是一个由精心制作、经过良好测试的可重用组件组成的应用程序，这些组件仅把框架作为胶水来让它们相互通信。我曾参与过一个名为 [Phix](http://www.phix-project.org) 的开源项目，它试图帮助构建一套工具来鼓励这种确切类型的应用程序架构。但这不是关于 `Phix` 的指南。我们可以利用 `Phix` 背后的一些理念来帮助你。

如果你认真地为你的应用程序提供有用的测试，你必须遵循这条信条：

> 如果你无法为它自动化测试，那么它就是坏的。

我为什么这么说？如果没有一套好的测试，你真的不知道应用程序是否会按预期行为。当然，实现这一点有很多障碍。几乎所有这些都是因为开发者为问题选择了不正确的解决方案。这可能听起来很苛刻，但通常就是事实。我也不例外。

我认为测试数据模型是许多初级到中级测试人员犯错的一个领域。他们未能理解目标是确保你以预期的方式表示数据，并且能够将数据的生成与表示它的代码分开。

我可以诚实地告诉你，因为你已经读到我指南的这里：测试确实需要很多自律，你经常发现自己写的支持和脚手架代码与真正工作的代码一样多。个人而言，我认为其中大部分工作非常有用，因为它是对未来的预付款。所有这些额外的工作都是为了保护你的代码免受非预期后果的影响。换句话说，你希望你的测试能够检测到你在不知情的情况下破坏了什么。

这里有一个我称之为脚手架代码的例子，你需要它来支持提供价值的测试类型。在我们的测试应用程序中，我们必须生成排名。为此，我们在期望的日期范围内选择一系列 `Games` 对象，然后做很多工作来计算胜负场数，然后按胜率对该列表进行排序返回。

现在，如果我想，该如何测试这个东西？正确的测试方法可能涉及创建一个数据 fixture 文件，其中包含序列化对象，代表我们希望从中生成排名的所有比赛。

我们如何创建这个 fixture？

```
<?php
$conn = new PDO(
    'pgsql:host=localhost;dbname=ibl_stats', 
    'stats', 
    'st@ts=Fun'
);

echo "Collecting all games in our season...\n";
$gameMapper = new \IBL\GameMapper($conn);
$allGames = $gameMapper->findAll();
echo "Writing games objects into fixture file...\n";
file_put_contents('./fixtures/games.txt', serialize($allGames));
echo "Done\n";
```

既然我们有了 fixture，我们的测试看起来如何以确保我们的 `Standings` 模型按我们想要的方式工作？

```
<?php

$testGames = unserialize(file_get_contents('./fixtures/games.txt'));  
$conn = new \PDO(
    'pgsql:host=localhost;dbname=ibl_stats', 
    'stats', 
    'st@ts=Fun'
); 
$testFranchiseMapper = new \IBL\FranchiseMapper($conn);
$testStandings = new \IBL\Standings($testGames, $testFranchiseMapper);
$testResults = $testStandings->generateBasic();
$this->assertTrue(count($testResults) > 0);
$testResult = $testResults['AC']['East'][0];
$this->assertEquals(1, $testResult['teamId'], 'Got expected team ID');
$this->assertEquals(97, $testResult['wins'], 'Got expected win total');
$this->assertEquals(65, $testResult['losses'], 'Got expected loss total');
$this->assertEquals('--', $testResult['gb'], 'Got expected GB total'); 
```

还不错，第一次尝试来说，但你看到了这里的问题吗？我们使用的是真实的 `Franchise` mapper，而不是模拟的。那很重要，因为我们不应该实际连接到数据库来获取关于存在哪些 `Franchise` 的信息。那会使测试依赖于我们的数据库，而我们不希望这样。

我们应该做的是创建一个另一个 fixture，传入我们所需的所有 `Franchise` 对象，然后在内部修改 `Standings` 模型本身，使其依赖于这些对象获取所需的信息。

创建一个工具，根据数据库中的数据生成 `Franchise` fixture。



```
<?php
include 'test_bootstrap.php';

$conn = new PDO(
    'pgsql:host=localhost;dbname=ibl_stats', 
    'stats', 
    'st@ts=Fun'
);
echo "Collecting all fixtures for our league...\n";
$mapper = new \IBL\FranchiseMapper($conn);
$allFranchises = $mapper->findAll();
echo "Writing franchise objects into fixture file...\n";
file_put_contents('./fixtures/franchises.txt', serialize($allFranchises));
echo "Done\n";
```

现在，我们重写测试以使用新的 fixture，并测试我们的 `Standings` 模型是否接受 `Games` 数组和 `Franchises` 数组作为构造函数参数。

```
<?php
include './test_bootstrap.php';

class StandingsTest extends \PHPUnit_Framework_TestCase
{
    public function testGenerateRegular()
    {
        $data = file_get_contents('./fixtures/games.txt');
        $testGames = unserialize($data);
        $data = file_get_contents('./fixtures/franchises.txt');
        $testFranchises = unserialize($data);
        $testStandings = new \IBL\Standings($testGames, $testFranchises);
    
        // Rest of the test is the same
    }
}
```

我并不是开玩笑，支持除非常表面的测试集之外的测试套件确实需要大量额外的代码。同时，提供这种额外支持时常常需要的各种迂回，也能让你非常好地（而且往往很残酷地）审视代码的设计。

如果你注意到了，我这样做使用的是人们在进行单元测试时通常认为的 fixtures。最常见的方法是使用数据库 fixtures，然后引入某种库来处理将这些 fixtures 转换为数据。这样你就可以使用某种 mock 对象，在测试看来它就像一个数据库连接。

有时候你确实需要数据库 fixtures。也许你无法像我这样解耦事物。如果你想走使用数据库 fixtures 的路线，我建议你看看 [Phactory](http://phactory.org)。它提供了一种更简单、以代码驱动的方式来创建数据库 fixtures，如果你的应用程序使用 `PDO`，那将是理想的选择。

无论哪种方式，你都必须意识到使用 fixtures 的缺点。当你更改测试时，你会发现自己也必须更改 fixtures。它还会减慢测试速度，因为无论是传统方式还是我通过创建数据对象的方式，都需要加载 fixtures。测试越慢，开发人员越有可能尝试跳过运行完整的测试套件。

对于这个示例应用程序，如果我的测试发生变化，创建新的数据 fixtures 很简单，因为我编写了小型脚本来实际创建它们。修改 fixture 创建脚本，再次运行它，我就有了更新后的数据 fixture。如果测试需要不同的数据，这肯定比手动编辑大量 `XML` 文件容易得多。

换句话说：在为测试目的导入数据时要聪明。很可能你不需要完整的数据集，只需要一小部分数据来验证功能。如果你能重构代码以使用对象而不是模拟数据库连接，那就更好了。

这里还有一条你应该铭记的座右铭：

> 如果不是你的，就把它封装起来。

如果你使用第三方 API 来做用户认证之类的事情，你很快就会发现测试变得非常困难。一个典型的场景可能是这个第三方 API 需要重定向到他们的网站，用户在那里填写一些信息，然后他们带着某种令牌返回你的应用程序，证明你就是你声称的那个人。这对你来说是好事，因为它免除了你自己管理这些凭据的负担，但坏处是，你如何测试这样的东西？

你可能很幸运，所使用的应用程序有一种捕获请求和响应循环的方式。本指南的示例应用程序没有，所以让我们思考一下如何使用类似 `Facebook Connect` 的东西。

答案当然是，你将对第三方身份验证服务的使用放在一个包装器内部。跟我一起，我来解释这个逻辑。

不要想“如何创建一个与 Facebook 通信的测试”，而是反过来想“如何为一个使用 Facebook Connect 作为数据源的身份验证服务创建测试？”。我希望你能看出区别。

使用 Facebook Connect 的正常方式是使用他们自己的 SDK（或者如果你是受虐狂，你自己编写 `OAuth` 实现），它基本上会将用户重定向到 Facebook，在那里他们输入网站的登录凭据。如果凭据正确，他们将被重定向回你的应用程序，并附带一个令牌，你可以用它来获取有关用户的信息。

在我自己使用 Facebook Connect 进行身份验证的情况下，我倾向于将用户信息存储在 session 中，然后稍后引用它。以下是我所指的示例：

```
<?php
// Assume $facebookUser is the object representing info about our user

$_SESSION['email'] = $facebookUser->getEmail();
$_SESSION['name'] = 
     $facebookUser->getFirstName() . 
     ' ' . 
     $facebookUser->getLastName();

// In other parts of the app when I need to check if the user is
// authenticated properly

if (isset($_SESSION['email'])) {
    // Execute the desired functionality
} else {
    // Redirect user to log in with Facebook Connect
}
```

顺便说一下，我倾向于将检查用户是否已正确身份验证的代码放在最适合项目所用框架的结构中。有些框架比其他框架更容易在运行你的特定操作代码之前在控制器中执行代码。

然而，如果你看看我上面的小示例，你可以看到为什么那样测试会非常困难：我们依赖于 session 中存储的信息。我们该如何尝试修复这个问题？

我们需要做的第一件事是停止直接检查 session 的内容，并创建一个对象来处理告知我们是否已通过身份验证的任务。

```
<?php
// New object that holds info about your Authenticated user

class AuthUser
{

    ...

    public function check()
    {
        return (isset($_SESSION['email']));
    }
}

// Then in the controller where you check authorization...

$authUser = new AuthUser();

if ($authUser->check() === true) {
    // Execute the desired functionality
} else {
    // Redirect user to log in with Facebook Connect
}
```

这样更好，但我们仍然依赖于 session 的可用性。我们如何减少这种特定依赖？

```
<?php

class AuthUser
{
    protected $_sessionObject;

    public function __construct($sessionContents)
    {
        $this->_sessionContents = $sessionContents;
    }
   
    public function check()
    {
        return (isset($this->_sessionContents['email']));
    }
}
```

现在我们取得了更大的进展。现在让我们假设我们想要测试一些控制器逻辑。在我们的示例应用程序中，我们的目标是能够独立于我们所处的环境加载控制器代码。这意味着我们必须确保此代码不依赖于 `$_SESSION` 等事物的存在。

然而还有一些额外的顾虑。为了运行我们的测试，我们不想担心实际连接到 Facebook 以获取有关用户的信息。这就是 `mock objects` 概念可以加入我们工具包的地方。



# 模拟对象与测试显示逻辑

## 用于测试的模拟对象

模拟对象是专门为使测试变得容易而创建的。在最基本层面上，你使用它们来替换可能需要与“outside world”通信的对象，例如数据库或第三方 API。有许多不同的工具可以为你创建模拟对象（`PHPUnit` has built-in [支持它](http://www.phpunit.de/manual/3.6/en/phpunit-book.html#test-doubles)）但其他人喜欢使用 Padraic Brady’s excellent [`Mockery`](https://github.com/padraic/mockery) mock object framework。

## 创建 Facebook 模拟示例

在我们的假设案例中，我们想要为我们的 `Facebook` 对象创建一个模拟对象。以下是你可以这样做的方式：

```
<?php
// Inside your unit test
$facebookMock = \Mockery::mock(
    '\FacebookAPI\Facebook',
    array(
        'getEmail' => 'test@littlehart.net',
        'getName' => 'Testy McTesterson'
    )
);

$sessionContents['email'] = $facebookMock->getEmail();
$auth = new AuthUser($sessionContents);
$this->assertTrue($auth->check());
```

注意这里模拟对象有多有效。你可以获得拥有一个与你的代码依赖的对象匹配的对象的全部好处，而无需实际与 `Facebook` 通信来进行测试。我认为在测试方面这是一种双赢的情况。

## 测试显示逻辑

通过自动化测试来测试你的显示逻辑是我谈论时经常会让人一脸茫然的事情。“Why don’t you just test that stuff in a browser.” 我通常的回答是“because I’m a human and humans make mistakes and skip things when they are testing a web page for the 100th time.” 幸运的是，捕获你的 `PHP` 应用程序的输出用于测试目的并不需要太多工作。

### 控制器渲染示例

这是我们示例应用程序中控制器的一个片段

```
<?php
include 'bootstrap.php';                                                        

...

echo $twig->render(
    'index.html', 
    array(
        'currentWeek' => $currentWeek,
        'currentResults' => $currentResults,
        'currentRotations' => $currentRotations,
        'currentSchedules' => $currentSchedules,
        'franchises' => $franchises,
        'rotationWeek' => $rotationWeek,
        'scheduleWeek' => $scheduleWeek,
        'standings' => $regularStandings, 
    )
);
```

使用相同的结构，我们可以非常轻松地编写一个看起来像这样的测试

### 自动化测试示例

```
<?php
include './test_bootstrap.php';

class MainPageViewTest extends \PHPUnit_Framework_TestCase
{
    protected $_twig;

    public function setUp()
    {
        // also include our libraries installed using Composer
        include APP_ROOT . 'vendor/.composer/autoload.php';

        // We are using Twig for templating
        $loader = new \Twig_Loader_Filesystem(APP_ROOT . 'templates');
        $this->_twig = new \Twig_Environment($loader, array('debug' => true));
        $this->_twig->addExtension(new \Twig_Extensions_Extension_Debug());
    }

    public function tearDown()
    {
        unset($this->_twig);
    }

    public function testMainPage()
    {
        $dbConn = new PDO(
            'pgsql:host=localhost;dbname=ibl_stats', 
            'stats',
            'st@ts=Fun'
        );
        // Load data that we will need for the front page
        $gameMapper = new \IBL\GameMapper($dbConn);
        $franchiseMapper = new \IBL\FranchiseMapper($dbConn);
        $rotationMapper = new \IBL\RotationMapper($dbConn);
        $scheduleMapper = new \IBL\ScheduleMapper($dbConn);

        $games = unserialize(file_get_contents('./fixtures/games.txt'));
        $franchises = unserialize(
            file_get_contents('./fixtures/franchises.txt')
        );
        $standings = new \IBL\Standings($games, $franchises);
        $regularStandings = $standings->generateRegular();
        $currentWeek = 27;
        $currentGames = unserialize(
            file_get_contents('./fixtures/games-27.txt')
        );
        $currentResults = $gameMapper->generateResults(
            $currentGames,
            $franchises
        );
        $rotations = unserialize(
            file_get_contents('./fixtures/rotations-27.txt')
        );
        $currentRotations = $rotationMapper->generateRotations(
            $rotations,
            $franchises
        );
        $rawSchedules = unserialize(
            file_get_contents('./fixtures/raw-schedules-27.txt')
        );
        $franchiseMap = unserialize(
            file_get_contents('./fixtures/franchise-mappings.txt')
        );
        $currentSchedules = $scheduleMapper->generate(
            $rawSchedules,
            $franchiseMap
        );

        // Display the data
        $response = $this->_twig->render(
            'index.html', 
            array(
                'currentWeek' => $currentWeek,
                'currentResults' => $currentResults,
                'currentRotations' => $currentRotations,
                'currentSchedules' => $currentSchedules,
                'franchises' => $franchises,
                'rotationWeek' => $currentWeek,
                'scheduleWeek' => $currentWeek,
                'standings' => $regularStandings, 
            )
        );
        $standingsHeader = "Standings through week 27";
        $resultsHeader = "Results for week 27";
        $rotationsHeader = "Rotations for Week 27";
        $scheduleHeader = "Schedule for Week 27";
        $rotation = "KC Greinke, CHN Lilly -2, CHN Wells -2"; 
        $this->assertTrue(stripos($response, $standingsHeader) !== false);
        $this->assertTrue(stripos($response, $resultsHeader) !== false);
        $this->assertTrue(stripos($response, $rotationsHeader) !== false);
        $this->assertTrue(stripos($response, $scheduleHeader) !== false);

        // Look for a known team abbreviation
        $this->assertTrue(stripos($response, "MAD") !== false);

        // Look for a specific rotation to appear
        $this->assertTrue(stripos($response, $rotation) !== false);
    }
}
```

## 验证 HTML 输出

那么在我的看法中，最好的查找我们 HTML 输出内部数据的方法是什么？你有两个选择。

### 字符串搜索方法

如果你希望 HTML 输出中出现特定字符串，比如说你成功创建了一个新小部件的消息，那么你最好使用 `PHP` 的内置字符串搜索函数。

```
<?php

$standingsHeader = "Standings through week 27";
$resultsHeader = "Results for week 27";
$rotationsHeader = "Rotations for Week 27";
$scheduleHeader = "Schedule for Week 27";
$rotation = "KC Greinke, CHN Lilly -2, CHN Wells -2"; 
$this->assertTrue(stripos($response, $standingsHeader) !== false);
$this->assertTrue(stripos($response, $resultsHeader) !== false);
$this->assertTrue(stripos($response, $rotationsHeader) !== false);
$this->assertTrue(stripos($response, $scheduleHeader) !== false);

// Look for a known team abbreviation
$this->assertTrue(stripos($response, "MAD") !== false);

// Look for a specific rotation to appear
$this->assertTrue(stripos($response, $rotation) !== false);
```

### 结构化输出验证

如果你试图确保输出以特定方式格式化，你可能应该考虑使用像 `PHP` 的内置 `SimpleXML` 函数这样的工具来加载输出，将其创建为 XML（毕竟 HTML 真的是 XML 的子集）然后使用 `xpath()` 方法。学习 [`XPath`](http://en.wikipedia.org/wiki/Xpath) 并不是最容易的事情。我在为一家提供 XML 数据馈送的体育数据集成公司工作时做了很多这方面的工作。但如果你想编写测试来确保错误消息被正确地包裹在适当的 CSS 类中，嗯，真的没有其他方法可以实现这一点。

所以如果你想查找，比如说，生成的输出中的特定 `<div>` 标签，我认为测试看起来会像这样，有一点来自名为 [`Zend_Dom_Query`](http://framework.zend.com/manual/en/zend.dom.query.html) 的第三方库的帮助。



```
<?php

// $response contains the output of our test page...

$domQuery = new \Zend_Dom_Query($response);

// Find the div for our standings display
$node = $domQuery->queryXpath('//div[@id="standings"]');
$this->assertTrue($node != "");
```

我认为这里需要记住的重要一点是，我们构建可测试视图的目标是能够在 HTML 输出发送到浏览器之前捕获它。这样我们就可以在输出中搜索字符串（或如果你更喜欢这种方法，则是 DOM 元素）以匹配我们的预期。

# 9 Shells 与沙盒

*这篇文章最初于 2009 年出现在我的博客上。它介绍了一种在 Python 和 Ruby 等语言中经常使用但在 PHP 中几乎被忽略的工具。希望你喜欢。*

现在我成为了一名“重生”的测试人员，我开始从更高层次的角度审视我在工作中所做的测试。像 [SimpleTest](http://www.simpletest.org/) 和 [PHPUnit](http://www.phpunit.de/) 这样的工具 *真的* 在做什么？它们提供了一种自动化运行测试的机制。类似的工具也存在于像 [Django](http://www.djangoproject.com) 和 [Ruby on Rails](http://www.rubyonrails.org) 这样的框架中。我无法代表 Django 发言，但 Rails 社区在测试工具和测试最佳实践方面做出了非常大的投入。但 Ruby 和 Python 提供的另一种非常强大的测试工具是 PHP 所没有的。

Ruby 和 Python 都提供了一个可从命令行运行的 [读取-求值-打印循环](http://en.wikipedia.org/wiki/REPL)，它允许人们做与传统测试工具相反的事情：允许你对代码进行交互式测试。我曾使用 Python 中可用的 `REPL`（你知道，就是从命令行输入 `python`）来测试一个副项目中各种地理编码库的使用方法。我的 [最喜欢的 Ruby 程序员](http://gilesbowkett.blogspot.com/) 在做事时总是使用 `irb`。

从某种意义上说，`REPL` 是反自动测试。我认为如果 PHP 有一个好的 `REPL` 可用，测试最佳实践可能会更好地被采纳。也许 Alan Pinstein 的 [iphp](http://github.com/apinstein/iphp) 项目中对一个好的 PHP `REPL` 抱有希望。我记得曾尝试继续几年前为 `CakePHP` 创建的测试控制台的工作，很快意识到我需要的是一个 `REPL`。

由于我没有通过摆弄 `eval` 来编写自己的有限 PHP 解析器的欲望（尽管说实话，我确实尝试过玩弄它，并意识到我根本不知道自己在做什么），测试控制台就此夭折了。此外，到底有多少 PHP 开发者真的在命令行上使用 PHP？10%？1%？很难说，因为我关注的群体是自选择的，我确信他们大多数人都使用过命令行 PHP。在命令行上尝试使用它而不成为一名高级 PHP 开发者是很困难的。

我也很高兴得知（使用了一年之后才发现，至少）[eXist](http://exist-db.org/) 拥有自己的 `XQuery` `REPL`——他们称之为“沙盒”。这太棒了，因为我可以拿出我“6 个月前写的，现在记不清是否还能工作”的 `XQuery` 脚本来测试它们。就像是你的 `RDBMS` 的命令行客户端。它甚至在我在尝试执行它们之前就会告诉我语法或格式错误。说到为开发者节省时间。

对于像 `MySQL` 和 `Postgres` 这样的 `RDBMS` 是否存在类似的东西？想象一个在你 *输入时* 检查语法的交互式客户端。如果有这样东西，请告诉我！

再一次，我看到我开始跑题了。重新回到正轨。

所以，从测试的角度来看，很容易看出 shell 和沙盒如何成为必不可少的工具。例如，我见过的所有关于单元测试的好建议都明确提倡沙盒方法。你创建包含数据的夹具。你创建模拟对象来模拟可能具有破坏性的功能。你甚至可以为测试操作创建一个单独的数据库。很明显，这里的目标是创建一个与代码最终运行的环境相同但与“真实”环境分离的环境。

另一方面，`REPL` 非常强大也非常危险。如果你不小心，很容易就会将数据插入到当前的生产环境而不是测试环境中。正如许多其他事情一样，权力是有代价的。当然，我可以运行一些代码来弄清楚如何使用，比如 `SQLAlchemy`，但我最好确保自己没有向生产数据库写入数据。那就太傻了。

我猜 PHP 没有易于使用的 `REPL` 的主要原因是它首先在网络上成长，其次才是命令行。Ruby 和 Python 首先在命令行上开始，然后才走向网络。我认为真的就是这么简单。PHP 未来会得到一个被广泛接受的 `REPL` 吗？

# 10 重建你的编程和部署环境

*本文的某些内容最初于 2009 年出现在我的博客上，并更详细地介绍了快速轻松地重建环境的概念背后的内容。希望你觉得有用。*

我一直在密切关注人们在最佳实践和实际应用部署方面做了哪些事情。看看这些，我意识到自己最近有多松懈。这是孤身开发者为雇主进行持续、增量的编程所带来的压倒性倦怠吗？我是在讽刺（显然）但我越想想我是如何进行开发工作的，就越意识到我需要重新聚焦。

所以，我的编程环境对我来说似乎还算正常。我在我的笔记本电脑上使用 [唯一的真编辑器(tm)](http://www.vim.org) 编写代码，那里安装了 PHP、Python 和 Perl。由于我同时使用 `MySQL` 和 `Postgres`，它们也都在我的笔记本电脑上。有何奇怪，我的 MacBook 被塞满了 4 GB 的 RAM？我通常运行几个 `Terminal.app` 实例和几个 [MacVim](http://code.google.com/p/mavcim) 实例。我发现我经常使用 [Sequel Pro](http://www.sequelpro.com/) 和 [pgAdmin III](http://www.pgadmin.org/)，因为所有与体育数据相关的工作都需要我一点一点调整的大型查询。

我还发现了一个我一直忽略但对开发工作来说是救星的强大工具。当你有一个应用程序需要处理的大型数据集，而将其复制到本地完全不切实际时怎么办？`SSH` 隧道来救援！

```
ssh -fNg -L3308:localhost:3306 notchris@server.domain.com
```

这创建了一个到我们其中一台生产机器（我们以 NHL 球队命名）上的 `MySQL` 服务器的隧道，然后我可以通过在端口 `3308` 上建立 `MySQL` 连接来访问它。非常简单而且非常有效。我简直不敢相信我竟然忘了这件事。这种技术在使用像 `Sequel Pro` 这样的工具时效果很好，我们曾有一位 SQL 顾问也是这样连接的。



# 测试反思

你看，我在决定测试什么方面遇到问题。让我们以一个项目为例。我们有一个 [自托管 Web 服务](http://www.sportsdb.org/sd/sportscaster)，它在 GPL 下发布，我们不仅自己为一些客户使用它，还用它来排查问题。就编写测试而言，我认为最好的方法是用一组已知参数直接针对 `Sportscaster` “引擎” 编写测试，并确保返回的输出与我们预期的一致。对这种情况做单元测试是不是过度设计了？很难说，因为我们有一个 HTML 前端，它与“网关”通信，而“网关”又与“引擎”通信。我不是设计这个架构的人，但我必须确保它能正常工作。在这种情况下，我认为“你的测试应该验证应用程序输出的是你期望的内容”是最好的方法。对此的评论非常欢迎。

对于另一个项目，我尝试了 [与 PHPUnit 集成 Selenium](http://sebastian-bergmann.de/archives/631-Integrating-PHPUnit-with-Selenium.html)，但速度慢到完全没用。[Sportso](http://www.sportso.com) 是一个非常注重视觉的应用，它用 PHP 编写并与 [XML 数据库](http://exist.sourceforge.net) 通信，但在这里呈现才是关键。我们需要确保将正确的数据放入 XML 文档中，但应用程序的这一部分是可靠的。在这种情况下，我希望有测试来模拟用户在应用程序中点击和使用。然后我可以再次比较输出，并确保事物在期望的时间和地点显示出来。我认为 `PHPUnit-Selenium` 桥接是个坏主意，我应该只专注于 `Selenium`。再次强调，关于如何最好地处理此事的评论也非常欢迎。我不敢相信 `Selenium` 真的会这么慢，所以一定是我做错了什么。

另外，我也考虑过持续集成。这篇 [关于持续部署的极具启发性的文章](http://timothyfitz.wordpress.com/2009/02/10/continuous-deployment-at-imvu-doing-the-impossible-fifty-times-a-day/) 让我认真思考我的更改是如何从开发环境推送到生产环境的。我们没有资源使用 IMVU 似乎拥有的机器集群，但当你想到基础设施（更重要的是）现有的实践时，你只能对这一切感到惊叹。仅仅是它的 *规模* 就令人鼓舞。如果他们能做到这一点，我当然可以实现其中一个非常有效的子集。除了我自己的懒惰之外，真的没有任何理由不去做它。残酷的现实，毋庸置疑。

但真正的问题是政治博弈，你不可避免地要为引入通常是一个非常激进的概念而斗争：把测试作为开发过程的一部分的承诺。尤其是在开发人员严重人手不足的情况下。很多人似乎对自动化测试有病态的恐惧，说着诸如“我们可以用手快速测试它”之类的话。然后当你看到用户报告的产品错误时，你不禁会想“我们本可以更早发现这个问题吗？”除非是一个涉及竞态条件之类的非常晦涩的错误，否则答案当然是肯定的。

我读到 justin.tv 的一位主要开发者写的一篇文章，谈论他为什么认为 [单元测试毫无用处](http://abstractstuff.livejournal.com/60388.html)。虽然他有权持有自己的观点，但我忍不住认为他实际上是在做 `TDD`，只是他拒绝承认这一点。是的，最终，只有你的用户才能告诉你你的应用程序是否在输出错误。但如果你在用户看到之前不对事物进行任何严格的测试，我认为你是在拿你的业务冒险。我的公司很小（只有我们 7 个人），所以我非常接近业务的各个方面，我确实可以看到某些决策对公司底线的影响。这不是关于查找错误，这是 justin.tv 的人声称单元测试永远不会发生的事情。这是为了确保这些错误根本不会发生。

我必须说，我从未真正深入研究过部署后监控的世界，所以也许我应该向处理这类事情的人多问几个问题。同样，关键是要使其自动化，并在发现问题时报告。我们在工作中有一个非常好的 [nagios](http://en.wikipedia.org/wiki/Nagios) 基础设施，它会提醒我们服务器宕机以及客户数据陈旧和/或缺失的问题。我想下一步的逻辑是弄清楚如何查看那堆服务器日志并理解错误？下次我在工作中遇到编程问题需要换个思路时，绝对值得思考。

我知道我在这里有点啰嗦，所以让我把这些内容重新整理一下，使其更连贯：
*   `SSH` 隧道用于访问你无法轻松将其快照放入开发环境的资源。我建议如果可以的话使用只读访问，因为如果你需要进行更新或删除，你应该始终在本地副本上工作
*   `TDD` 是一种强大但仍有争议的工具，太多开发人员仍在忽视它
*   自动化是真正利用 `TDD` 所带来的好处的关键
*   部署后你需要有工具来查看你的更改是否产生了预期效果

# 11 PHP 开发者的持续集成现状

*本文最初于 2010 年发表在我的博客上，并因工具本身的一些变化而进行了更新。我希望这里的信息对你有所帮助。*

对于不熟悉 [持续集成](http://en.wikipedia.org/wiki/Continuous_integration) 概念的人，我可以用一句话概括：它让你在购买前就破坏你的代码。我的意思是，当与其他编程实践如自动化部署和测试驱动开发结合时，你有机会看到你今天编写的代码是否破坏了你昨天编写的内容。

如果我要设计一个持续集成（以下简称 `CI`）系统，它会是什么样子？撇开我已经在使用的那个系统不谈（稍后会详细介绍），我认为它需要一些关键特性：
*   能够与你的版本控制系统集成
*   跨平台访问构建结果的 Web 界面
*   能够运行你的单元测试套件并查看结果
*   能够将代码部署到任何你想要的地方
*   能够通过电子邮件发送测试构建结果
*   必须能够为你自动化所有这些操作

我称之为一套不平凡的需求。

它也说明了我最大的领悟：你不能没有编写测试（无论是单元测试还是集成测试）就拥有 `CI`，你也不能在没有开发者进一步操作的情况下触发创建“构建”的过程而拥有 `CI`。如果没有对编写有意义测试的承诺，它肯定不会奏效。我坚信确实存在无意义的测试，而且对我来说，达到 100% 代码覆盖率往往更多的是程序员的自我表现。

因此，PHP 开发者有几个选择。你可以使用 [`phpUnderControl`](http://phpundercontrol.org/)，它是一个 [`CruiseControl`](http://cruisecontrol.sourceforge.net/) 的插件，后者是一个基于 Java 的工具。我看了一下，看到所有那些 XML 配置文件就说“算了”。如果你喜欢摆弄 XML 配置文件，那么这可能就是适合你的工具。我喜欢我的点选式界面。或纯文本配置文件。还主要针对 Java 开发者。我的项目使用 PHP *和* Python，并且还需要能够支持 Java，因为另一位开发者正在进行一个非 Web 项目。



如果你偏爱 `PHP` 驱动方案的酷炫理念，可以看看 [`Xinc`](http://code.google.com/p/xinc/)。它通过 `PEAR` 安装（这总是個好主意），但会连带拖入其他几个 `PHP` 组件。我不知道，只做 `PHP` 对我来说并无特别吸引力。

某些组织也在使用 [`Buildbot`](http://en.wikipedia.org/wiki/BuildBot)，但搜索结果里满是人们讨论它对经验不足的程序员来说有多难用。它是用 `Python` 编写的，所以如果你有合适的技能，就可以修改它来随心所欲地使用。

最后，我选择了 [`Jenkins`](http://jenkins-ci.org)。和 `CruiseControl` 一样，它基于 `Java`，但这不是大问题，因为我们工作中的基础设施里已经有 `Java`，而且还有更多小部分正在迁移到它上面。此外，`Jenkins` 具有我喜欢的那种架构：一个小而紧凑的核心，加上大量插件来添加我想要的功能。使用 `Subversion`？添加插件。需要运行 [`py.test`](http://codespeak.net/py/dist/test/) 脚本？有插件。想查看你的 `PHPUnit` 测试结果？也有插件。

所以，不仅如此，我还可以编写一个在构建触发时运行的 `shell script`。在这种情况下，我使用的是 `post-commit` 触发器来启动构建，但如果我想要更教条一些，我会使用 `pre-commit` 触发器，并在测试失败时使 `commit` 尝试失败。我记得年轻气盛的我曾在之前的雇主那里大发雷霆，当时在我们的 `CVS` 仓库（是的，我已经足够老到真的用过 `CVS`）中放置了一个 `hook`，它会对任何签入的代码运行 `syntax checker`。可以预见的是，出现了问题，因为运行在 `CVS` 服务器上的 `PHP` 版本与我们在 `development` 和 `production` 中使用的版本不同，扩展的差异导致了问题。那是另一个故事。

我还发现使用 `post-commit` hook 允许我在 `staging` 环境中查看代码，以查找由 `development` 环境与 `staging` 之间细微差异引起的错误。今天，我通过使用 `PHP 5.3` 中可用的新三元运算符快捷方式修复了一个错误。每天学点新东西，是我的座右铭。

那么，构建实际上是如何工作的？以下是我的设置方式：

1. 开发人员将代码提交到 `SVN` 仓库的 `trunk`。我们目前不使用 `branches`，所以如果我们在 `branches` 中工作然后合并到 `trunk`，我就需要调整设置。
2. 当 `Jenkins` 看到 `commit` 时就会唤醒，并将代码检出到 `workspace`。
3. 然后 `Jenkins` 运行一系列 `shell script` 命令来做很多事情：运行我的 `Doctrine` 迁移脚本，运行我的 `PHPUnit` 测试，运行我的 `py.test` 测试，然后将代码复制到 `staging` 服务器上。
4. 创建一堆可在 `Jenkins` 本身中查看的 `test` 报告
5. 向我们的技术邮件列表发送 `email`，通知人们构建已被触发以及结果

我必须说，没有什么比看到构建成功更能让我感到自鸣得意的……也没有什么比看到构建失败更让我咒骂的了。但如果没有这些测试，我就不会发现本会进入生产环境的错误。任何进入生产环境的错误都很糟糕，而且尽管我在工作中经常使用绞刑架幽默来试图转移对这种事情的内心愤怒，但确实有可能进行生产推送的新代码不包含错误。

作为这一想法的后续，我现在有一个政策：每当在 `staging` 或 `production` 中发现错误时，我都会编写一个 `test` 来重现该错误，然后放入代码来修复它。我发现这会产生有趣的效果，给你一大堆 `unit` 和 `integration` 测试（感谢在 `Zend_Framework` `PHPUnit` 测试中能够测试 `controllers` 输出的能力），这些测试涵盖了真实用户发现的 `edge cases`。此外，你可能会深陷“我们需要创建 `fixtures` 才能测试操作动态生成内容的东西”这个兔子洞。我今天看到一个 `test` 可以从使用 `fixtures` 中受益，而不是简单地假设 `data` 总会存在。效果因人而异，但你必须明白，如果你没有实现生产出满足实际使用它的人目标的工作 `application` 的目标，对 `testing` 的奴性奉献对你没有任何好处。

我希望这篇文章能帮助你在决定是否要进行 `CI` 跨越时。我对花费的时间长度没有任何遗憾，以使 `Jenkins` 配置达到令人满意的状态。自动化构建的好处，其目标是保护你免受你自己的伤害，远远超过了几个下午挠头试图弄清楚 `Jenkins` 本身发生了什么。

# 12 基础设施债务

*这篇文章最初于 2011 年 11 月发布为博客文章，获得了关注并最终登上了 Hacker News。它与构建可测试应用程序的概念直接相关。希望你喜欢它。*

你可能遇到过“`technical debt`”这个术语，用来描述随着 `application` 增长和需求变化而在你的 `code base` 中犯下的小错误。如果你不非常小心地进行这些更改，你最终会得到一个大乱摊子。如果你曾经在担心改动会破坏某些东西而不敢更改的 `application` 上工作过，那么你就遇到了 `technical debt`。

积累 `technical debt` 非常容易：你因为感到有压力要完成任务而放入一个快速的 `hack`。需要勇气来反驳并说“不，该死，我需要时间来正确修复这个问题！”。我理解，这没关系。如果拥抱能让你感觉更好，我们可以拥抱一下。

`Technical debt` 可以通过无情的 `refactoring` 以及用 `tests` 包裹你的 `application` 来处理，这些 `tests` 会刺探你的 `application` 处理的 `edge cases`。但你最终会处理另一种债务。那是一种更难以处理和改变的债务。我称之为 `infrastructure debt`。

`Infrastructure debt` 是你因为没有关注创建 `application` 将存在的 `environments` 的过程，也没有关注你的 `code` 如何从 `development` 进入 `production` 的过程而积累的债务。在我看来，`Infrastructure debt` 比 `technical debt` 更难“偿还”。为什么？人们往往很难理解它甚至存在。

在我继续之前，如果你没有使用 `version control system` 来跟踪对你的 `code` 的更改，请停止阅读并去安装一个。用 `.1` 和 `.old` 这样的扩展名保存文件版本是你可能拥有的最糟糕的 `infrastructure debt`。现在是 21 世纪的第二个十年。`Version control` 是一个近 40 年历史、已被充分理解的概念。如果坚持认为 `version control` 对你毫无用处，我建议的任何东西都不会奏效。传递 `diff` 补丁不是 `version control`，我的朋友们。那是否认。不要告诉我，仅仅因为过去人们这样做，现在在所有可用选项面前就没问题了。人们曾经也认为地球是平的。

让我们从一个容易偿还的 `infrastructure debt` 开始：`development environments` 的不一致。如今，对于某人来说，为其选择的 `language` 创建 `development environment` 以及相关的组件如 `databases` 变得相当容易。问题是什么？就是某人很容易创建自己选择的 `development environment`。



你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

# 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你最终会发现你的开发人员都拥有略有不同的环境，这源于他们对软件包来源的选择或对组件版本偏好的不同。我通过自定义的 Homebrew 配方安装了 PHP 5.3.8，而我的其中一位同事则使用随 OS-X Snow Leopard 提供的标准版 PHP。他使用的 MySQL 版本比我的还领先两个版本。看到多么容易不同步了吗？

你有两个选择。第一个是专制的方案，即强制所有人使用相同的操作系统和相同的工具，以最大程度减少开发环境冲突的可能性。考虑到这会导致开发人员不满，我更倾向于一种更理性的做法：使用像 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 这样的工具，让你的开发人员在完全相同的虚拟机上工作，同时给予他们自由选择自己喜爱的开发和调试工具的权利。

此外，通过使用虚拟机，你可以鼓励开发人员大胆尝试并测试一些破坏性的操作，比如库升级或数据库变更。搞砸了？只需启动一台新的虚拟机再试一次。当你将其与良好的版本控制实践结合起来时，你应该能更快地从错误中恢复。

只要确保花时间创建尽可能与生产系统完全一致的虚拟机。老实说，你的开发环境和生产环境之间的唯一区别应该是应用程序所操作的数据。甚至在自己的电脑上创建一个虚拟机集群来模拟包含应用服务器、数据库服务器和 memcached 服务器的架构，也并不算太难。

这也有助于让新开发人员快速上手。“哦，在做 Project Alpha？我会把 wiki 上可以下载该项目虚拟机的链接发给你。”

查看 [Vagrant](http://vagrantup.com) ，这对希望在虚拟机中工作的开发人员来说是一个很棒的选择。

因此，在为你的开发环境注入了一些结构之后，基础设施债务像购物狂的信用卡账单一样堆积的最后一个前沿领域就是：部署流程。

我真的认为有一条规则：如果你的部署不能用一条命令完成，那么你就是做错了。如果你能把你在 shell 中执行的命令输入进去，那么你就可以把它们脚本化，这样就不用再重复输入了。如果你能脚本化部署，那么你就能自动化部署。如果你能自动化部署，那么你现在就拥有了一个一致且可重复的过程，每次部署时都会以相同的方式运行。

在 [Moontoast](http://www.moontoast.com) ，我们已经实现了自动化部署。当我们将代码合并到 staging 和 production 分支时，版本控制钩子会触发我们的部署工具。它会将代码检出到生产服务器上的正确位置。它运行需要执行的数据库迁移。它启动并重启应用程序使用的各种服务。简而言之，它做了我看到太多同事手动执行的事情。停止吧。通过让部署代码的过程成为一件无关紧要的事来清理你的基础设施债务。

如果你想自动化你的部署流程，可以研究一下像 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/) 这样的工具，甚至可以使用像 [Jenkins](http://jenkins-ci.org) 这样的工具，并利用其 Builds 的概念来自动化将最新代码变更推向生产的过程。

注意我说的是流程，因为技术债务可能意味着你的应用程序足够脆弱（没有足够的测试和/或测试覆盖率），以至于你所做的更改可能会导致其行为不当甚至完全崩溃系统。这感觉并不好，所以通过投入时间自动化你的部署流程，你至少可以消除一个头痛的问题。

我认为关于基础设施债务我想要传达的主要观点是，你真的需要审视超出单纯编码的流程。如果你发现自己不断在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你发现自己每次部署时都不断参考检查清单，你很可能有严重的基础设施债务。

每当我提起这个话题时，我听到的借口很多都与我倡导编写测试并自动化执行这些测试时听到的借口相同。人们为什么会对这类事情如此抵触？

我发现人们严重低估了完成一项任务所需的手工工作量。对很多人来说，是对失去控制的恐惧导致他们得出自动化部署不可信的结论，或者开发人员不应该有自由选择用于构建应用程序的工具。

技术债务是真实存在的，毫无疑问。但基础设施债务也是如此。就像在生产环境中发现 bug 的成本高于在开发环境中发现一样，修复基础设施债务的成本也越来越高。只要想想消除开发环境之间不一致性所解决的大量问题。再加上在手动部署应用程序时消除人为错误的能力。你为什么不想要这个呢？

开始偿还基础设施债务的决定并不容易，因为它通常需要许多人做出许多改变。大多数程序员都是习惯性动物，即使改变明显更好，他们也不喜欢改变。不要害怕改变，要害怕债务在你的代码库和基础设施中不断增长。它不会消失，也没有政府救助即将到来修复它。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你会发现开发人员各自的环境都略有不同，源于软件包来源的选择或组件版本偏好不同。我通过自定义 Homebrew 配方安装了 PHP 5.3.8，而同事用的是随 OS-X Snow Leopard 提供的标准 PHP。他的 MySQL 版本比我还新两个版本。看到多容易不同步吗？

你有两个选择。第一个是专制的做法，强制所有人使用相同操作系统和工具以减少冲突。但这会让开发人员不满，我更倾向于更合理的做法：用 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 等工具，让开发人员在完全相同的虚拟机上工作，同时自由选择自己喜欢的开发调试工具。

用虚拟机还能鼓励开发人员大胆测试破坏性操作，如库升级或数据库变更。搞砸了？启动一台新虚拟机再试。配合良好的版本控制，恢复错误会更快。

务必花时间创建与生产系统尽可能一致的虚拟机。说实话，开发环境和生产环境的唯一区别应是应用操作的数据。甚至在自己电脑上建一个虚拟机集群来模拟应用服务器、数据库服务器和 memcached 服务器的架构也不难。

这也有助于新开发人员快速上手。“哦，在做 Project Alpha？我把 wiki 上该项目虚拟机的下载链接发给你。”

查看 [Vagrant](http://vagrantup.com)，对想在虚拟机中工作的开发人员来说是很好的选择。

在为开发环境注入结构后，基础设施债务像购物狂信用卡账单一样堆积的最后一个前沿就是部署流程。

我认为有一条规则：如果部署不能用一条命令完成，你就是做错了。你能在 shell 输入的命令就能脚本化，避免重复输入。能脚本化就能自动化，能自动化就有了每次部署都一致可重复的过程。

在 [Moontoast](http://www.moontoast.com) 我们已实现自动化部署。合并代码到 staging 和 production 分支时，版本控制钩子触发部署工具。它把代码检出到生产服务器的正确位置，运行必要的数据库迁移，启动并重启应用使用的各种服务。简言之，它做了太多同事还在手动做的事情。停止吧。通过让部署代码成为一件无事来清理基础设施债务。

想自动化部署流程，可研究 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/)，或用 [Jenkins](http://jenkins-ci.org) 并利用其 Builds 概念自动化把最新代码变更推向生产。

注意我说的是流程，因为技术债务可能让应用足够脆弱（测试不足和/或覆盖率不够），导致更改使行为异常甚至崩溃系统。这感觉不好，所以投入时间自动化部署流程至少能消除一个头痛。

我关于基础设施债务想传达的主要点是，你需要审视超出编码的流程。如果你总在打“在我电脑上能运行”的仗，你很可能有严重的基础设施债务。如果你每次部署都不断查检查清单，你很可能也有严重的基础设施债务。

每当我提起这个话题，听到的借口和我倡导写测试并自动化执行测试时听到的很像。人们为什么对这类事如此抵触？

我发现人们严重低估完成任务所需的手工工作。对很多人来说，是害怕失去控制导致他们认为自动化部署不可信，或开发人员不应自由选择构建应用的工具。

技术债务是真实的，毫无疑问。基础设施债务也是如此。就像在生产发现 bug 的成本高于开发一样，修复基础设施债务的成本越来越高。想想消除开发环境不一致解决的大量问题。再加上手动部署时消除人为错误的能力。你为什么不要？

开始偿还基础设施债务的决定不容易，因为它通常需要很多人做很多改变。大多数程序员是习惯性动物，即使改变明显更好也不喜欢。不要怕改变，要怕债务在代码库和基础设施中增长。它不会消失，也没有政府救助来修复。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你会发现开发人员环境都略有不同，源于软件包来源或组件版本偏好不同。我用自定义 Homebrew 配方装了 PHP 5.3.8，同事用的是 OS-X Snow Leopard 自带的 PHP。他的 MySQL 比我新两个版本。看多容易不同步？

有两个选择。一种是专制做法，强制统一操作系统和工具以减少冲突，但会让开发人员不满。我更倾向合理做法：用 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 让大家在相同虚拟机工作，同时自由选择开发调试工具。

虚拟机还能鼓励测试破坏性操作如库升级或数据库变更。搞砸了就启动新虚拟机再试。配合良好版本控制，恢复更快。

务必创建与生产系统尽可能一致的虚拟机。开发环境和生产环境的唯一区别应是应用操作的数据。甚至在自己电脑上建虚拟机集群模拟应用服务器、数据库服务器和 memcached 服务器也不难。

这也有助于新人快速上手。“在做 Project Alpha？我把 wiki 上该项目虚拟机的下载链接发给你。”

查看 [Vagrant](http://vagrantup.com) 是个好选择。

在开发环境有了结构后，基础设施债务像购物狂信用卡账单一样堆积的最后前沿是部署流程。

我认为有一条规则：部署不能用一条命令完成就是做错了。能在 shell 输入的命令就能脚本化，能脚本化就能自动化，能自动化就有了每次都一致可重复的过程。

在 [Moontoast](http://www.moontoast.com) 我们已自动化部署。合并代码到 staging 和 production 分支时，版本控制钩子触发部署工具。它把代码检出到生产服务器正确位置，运行数据库迁移，启动重启应用服务。简言之，它做了太多同事还在手动做的事情。停止吧，让部署成为无事来清理基础设施债务。

想自动化部署，可研究 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/)，或用 [Jenkins](http://jenkins-ci.org) 的 Builds 概念自动化把最新代码推向生产。

注意我说的是流程，因为技术债务会让应用脆弱，测试不足导致更改引发异常甚至崩溃。自动化部署至少能消除一个头痛。

基础设施债务的核心是你要审视超出编码的流程。常打“在我电脑上能运行”的仗，或每次部署都查检查清单，都说明有严重基础设施债务。

提起此话题时听到的借口和倡导写测试并自动化执行时一样。人们为何抵触？

人们严重低估手工工作量。很多人因害怕失去控制而认为自动化部署不可信，或开发人员不应自由选工具。

技术债务真实存在，基础设施债务也真实存在。生产发现 bug 的成本高于开发，修复基础设施债务的成本也越来越高。消除开发环境不一致解决大量问题，再加上消除手动部署人为错误。你为何不要？

偿还基础设施债务不容易，需要很多人改变。大多数程序员习惯性，即使更好也不愿改变。不要怕改变，要怕债务增长。它不会消失，没有政府救助。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你会发现开发人员环境都略有不同，源于软件包来源或组件版本偏好不同。我用自定义 Homebrew 配方装了 PHP 5.3.8，同事用的是 OS-X Snow Leopard 自带的 PHP。他的 MySQL 比我新两个版本。看多容易不同步？

有两个选择。一种是专制做法，强制统一操作系统和工具以减少冲突，但会让开发人员不满。我更倾向合理做法：用 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 让大家在相同虚拟机工作，同时自由选择开发调试工具。

虚拟机还能鼓励测试破坏性操作如库升级或数据库变更。搞砸了就启动新虚拟机再试。配合良好版本控制，恢复更快。

务必创建与生产系统尽可能一致的虚拟机。开发环境和生产环境的唯一区别应是应用操作的数据。甚至在自己电脑上建虚拟机集群模拟应用服务器、数据库服务器和 memcached 服务器也不难。

这也有助于新人快速上手。“在做 Project Alpha？我把 wiki 上该项目虚拟机的下载链接发给你。”

查看 [Vagrant](http://vagrantup.com) 是个好选择。

在开发环境有了结构后，基础设施债务像购物狂信用卡账单一样堆积的最后前沿是部署流程。

我认为有一条规则：部署不能用一条命令完成就是做错了。能在 shell 输入的命令就能脚本化，能脚本化就能自动化，能自动化就有了每次都一致可重复的过程。

在 [Moontoast](http://www.moontoast.com) 我们已自动化部署。合并代码到 staging 和 production 分支时，版本控制钩子触发部署工具。它把代码检出到生产服务器正确位置，运行数据库迁移，启动重启应用服务。简言之，它做了太多同事还在手动做的事情。停止吧，让部署成为无事来清理基础设施债务。

想自动化部署，可研究 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/)，或用 [Jenkins](http://jenkins-ci.org) 的 Builds 概念自动化把最新代码推向生产。

注意我说的是流程，因为技术债务会让应用脆弱，测试不足导致更改引发异常甚至崩溃。自动化部署至少能消除一个头痛。

基础设施债务的核心是你要审视超出编码的流程。常打“在我电脑上能运行”的仗，或每次部署都查检查清单，都说明有严重基础设施债务。

提起此话题时听到的借口和倡导写测试并自动化执行时一样。人们为何抵触？

人们严重低估手工工作量。很多人因害怕失去控制而认为自动化部署不可信，或开发人员不应自由选工具。

技术债务真实存在，基础设施债务也真实存在。生产发现 bug 的成本高于开发，修复基础设施债务的成本也越来越高。消除开发环境不一致解决大量问题，再加上消除手动部署人为错误。你为何不要？

偿还基础设施债务不容易，需要很多人改变。大多数程序员习惯性，即使更好也不愿改变。不要怕改变，要怕债务增长。它不会消失，没有政府救助。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你会发现开发人员环境都略有不同，源于软件包来源或组件版本偏好不同。我用自定义 Homebrew 配方装了 PHP 5.3.8，同事用的是 OS-X Snow Leopard 自带的 PHP。他的 MySQL 比我新两个版本。看多容易不同步？

有两个选择。一种是强制统一操作系统和工具，但会让开发人员不满。我更倾向用 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 让大家在相同虚拟机工作，同时自由选择开发调试工具。

虚拟机还能鼓励测试破坏性操作。搞砸了就启动新虚拟机再试。配合良好版本控制，恢复更快。

务必创建与生产系统尽可能一致的虚拟机。开发环境和生产环境的唯一区别应是应用操作的数据。甚至在自己电脑上建虚拟机集群模拟应用服务器、数据库服务器和 memcached 服务器也不难。

这也有助于新人快速上手。“在做 Project Alpha？我把 wiki 上该项目虚拟机的下载链接发给你。”

查看 [Vagrant](http://vagrantup.com) 是个好选择。

基础设施债务像信用卡账单一样堆积的最后前沿是部署流程。

我认为有一条规则：部署不能用一条命令完成就是做错了。能脚本化就能自动化，能自动化就有了每次都一致可重复的过程。

在 [Moontoast](http://www.moontoast.com) 我们已自动化部署。合并代码到 staging 和 production 分支时，版本控制钩子触发部署工具。它检出代码、运行迁移、启动服务。停止手动操作，让部署成为无事来清理债务。

想自动化部署，可研究 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/)，或用 [Jenkins](http://jenkins-ci.org) 的 Builds 概念。

注意我说的是流程，技术债务会让应用脆弱，测试不足导致崩溃。自动化部署至少能消除一个头痛。

基础设施债务的核心是你要审视超出编码的流程。常打“在我电脑上能运行”的仗，或每次部署都查检查清单，都说明债务严重。

人们严重低估手工工作量。很多人因害怕失去控制而认为自动化部署不可信。

技术债务真实存在，基础设施债务也真实存在。修复成本越来越高。消除环境不一致和手动部署人为错误为何不要？

偿还债务不容易，需要很多人改变。不要怕改变，要怕债务增长。它不会消失，没有救助。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的[content]
你会发现开发人员环境都略有不同，源于软件包来源或组件版本偏好不同。我用自定义 Homebrew 配方装了 PHP 5.3.8，同事用的是 OS-X Snow Leopard 自带的 PHP。他的 MySQL 比我新两个版本。看多容易不同步？

有两个选择。一种是强制统一操作系统和工具，但会让开发人员不满。我更倾向用 [VMWare](http://www.vmware.com) 或 [VirtualBox](http://www.virtualbox.org) 让大家在相同虚拟机工作，同时自由选择开发调试工具。

虚拟机还能鼓励测试破坏性操作。搞砸了就启动新虚拟机再试。配合良好版本控制，恢复更快。

务必创建与生产系统尽可能一致的虚拟机。开发环境和生产环境的唯一区别应是应用操作的数据。甚至在自己电脑上建虚拟机集群模拟应用服务器、数据库服务器和 memcached 服务器也不难。

这也有助于新人快速上手。“在做 Project Alpha？我把 wiki 上该项目虚拟机的下载链接发给你。”

查看 [Vagrant](http://vagrantup.com) 是个好选择。

基础设施债务像信用卡账单一样堆积的最后前沿是部署流程。

我认为有一条规则：部署不能用一条命令完成就是做错了。能脚本化就能自动化，能自动化就有了每次都一致可重复的过程。

在 [Moontoast](http://www.moontoast.com) 我们已自动化部署。合并代码到 staging 和 production 分支时，版本控制钩子触发部署工具。它检出代码、运行迁移、启动服务。停止手动操作，让部署成为无事来清理债务。

想自动化部署，可研究 [Capistrano](https://github.com/capistrano/capistrano/wiki) 或 [Phing](http://www.phing.info/trac/)，或用 [Jenkins](http://jenkins-ci.org) 的 Builds 概念。

注意我说的是流程，技术债务会让应用脆弱，测试不足导致崩溃。自动化部署至少能消除一个头痛。

基础设施债务的核心是你要审视超出编码的流程。常打“在我电脑上能运行”的仗，或每次部署都查检查清单，都说明债务严重。

人们严重低估手工工作量。很多人因害怕失去控制而认为自动化部署不可信。

技术债务真实存在，基础设施债务也真实存在。修复成本越来越高。消除环境不一致和手动部署人为错误为何不要？

偿还债务不容易，需要很多人改变。不要怕改变，要怕债务增长。它不会消失，没有救助。

## 13 恐惧是心灵的杀手

*这篇文章最初于 2011 年 3 月出现在我的博客上。它讨论了恐惧如何阻止你做必要的使应用程序易于测试的工作。祝你阅读愉快*



但对于新技术往往还有另一种反应。那种反应就是恐惧。对使用自己不熟悉的一套技术感到恐惧。对自动化系统部署可能未得到充分测试的代码感到恐惧。对投入精力去做短期收益很少但长期收益很多的事情感到恐惧。恐惧是思想的杀手，是你脑海中那个小声音在告诉你你不够好，你的想法很烂，你根本不知道自己在说什么。

Seth Godin 谈到当一种技术被贴上死亡标签时，[真正酷的事情可以发生](http://sethgodin.typepad.com/seths_blog/2011/03/bring-me-stuff-thats-dead-please.html)。PHP 正是被 Mr. Godin 提到的“路过型技术宅”们贴上了死亡标签，尽管事实上它在构建 Web 应用时仍然是一个定位良好的工具。与此同时，我能感觉到大脑中那股恐惧的刺痛。“不要被落下”它在我耳边低语。“放弃 PHP 转投技术 X”它恳求我。当声音变得太大时，我开始背诵反恐祷文。PHP 本身仍有很多创新要做。PHP 的每个后续版本都在变得更快，并且（相当正确地）实现了让其他脚本语言变得有趣的功能。例证 A？[匿名函数](http://ca.php.net/manual/en/functions.anonymous.php)，允许编写一些非常有趣的代码。它是最新[品种](http://lithify.me/)[的](https://github.com/symfony/symfony)[框架](https://github.com/zendframework/zf2)不可或缺的一部分。

不要让恐惧决定你使用的技术。今天，我最擅长使用 PHP 构建 Web 应用，并加入一些 Javascript 来改善用户体验。明天，情况会有所不同。不是字面意义上的明天。你知道我的意思。我一直在技能集中添加 Python、[Django](https://github.com/chartjes/ibl)、[Flask 和 Google App Engine](https://github.com/chartjes/liesitoldmykids)。坦率地说，对于像我这样走“样样通”职业道路的人来说，成为单生态系统（即仅限 PHP）的专家风险很大。远比[站在巨人的肩膀上](http://en.wikipedia.org/wiki/Standing_on_the_shoulders_of_giants)更好，而不是只待在自己舒适的地方。

我想我试图传达的重点是，你可以将*反恐祷文*作为一种工具来激励自己真正分析对情况的反应。例如，我很难弄清楚如何让 Zend Framework + PHPUnit 充分测试工作中应用程序使用 Facebook Connect 的能力。我就是无法让它通过常规请求来执行操作，原因有很多我无法理解。我无法像我希望的那样深入查看请求。我预见到必须在应用程序中降一个层级，并承认我无法测试请求本身，只能测试控制权返回到应用程序后执行的代码。

恐惧会说“放弃吧，因为正确地测试东西太难了”。现实是，虽然我无法测试请求的*输出*，但我当然可以测试幕后本应发生的事情。这样的测试与能够捕获请求的响应并验证 DOM 中元素按预期存在一样有价值。也许有一天 PHP 中会有更好的工具来完成这项任务。我知道使用[其他工具](http://opensoul.org/blog/archives/2009/03/05/testing-facebook-with-cucumber/)可以做到这一点，我在这里坦白说：这让我对 PHP 测试工具的现状忍不住骂上几句。

# 14 测试在哪里？

*这篇文章最初于 2008 年 10 月出现在我的博客上，今天仍然非常适用。希望你喜欢。*

随着一个[工作项目](http://sportso.com)准备进行 Alpha 发布，我已经消除了所有严重 bug，现在有时间做本应从项目开始就包含的事情：编写测试。作为一名已淡出测试的测试者，每当应用程序变得复杂时，我总是对没有编写测试感到内疚。每当你做出更改时，你必须通过点按的方式遍历应用程序以确保没有东西被破坏。我厌倦了点按，所以我决定是时候闭嘴写一些测试了。由于我在这个项目中使用 Code Igniter 而不是 CakePHP（我提到过我继承了这个项目并且无法更换吗？）我开始研究围绕 Code Igniter 的测试文化。它弱得像个新生儿。

内置的测试系统是单元测试和“你必须自己创建测试结果模板”的某种奇怪混合体。WTF？你没在开玩笑吧。所以我很快就忽略了它。此外，第一批测试将使用 [PHPUnit](http://phpunit.de) 结合 [Selenium](http://selenium.openqa.org/)，这样我就可以让“验收测试”自动化。顺便说一下，我记得大约 3 年前在一次会议上与 Sebastian Bergmann（PHPUnit 背后的推动者）交谈，他告诉我他知道有人正在努力让 Selenium 和 PHPUnit 良好地协同工作。无论如何，它运行得很好。

所以，下一步是看看我是否能使用 Code Igniter 自带的那种极其糟糕的测试工具以外的东西。我找到了一个叫做 [fooStack](http://www.foostack.com/foostack/) 的东西，其中包含 `CIUnit`。它让你可以用 PHPUnit 与 Code Igniter 一起使用。现在我们说到点子上了！转眼间我就为我的模型编写了一些单元测试。好吧，在花了大量时间折腾测试并发现通过 Apache 运行应用程序与通过命令行测试模型之间的相对路径差异之后。感谢 Twitter 上所有对我大喊“使用 `php_sapi_name` 来判断你所在的環境，你这个白痴！”的人。

但这一切让我思考：其他一些 PHP 框架在测试方面表现如何？

*   Code Igniter 本身的框架为零测试。也许下次被要求从零开始创建一个项目时我会向我的老板提及这一点。哼，看来我只能相信他们的代码实际上按预期工作。

*   Zend Framework（完全披露：我是 `Zend_Service_Audioscrobbler` 组件的原始作者之一）为其框架本身拥有大量测试。事实上，任何新贡献都必须附带可工作的测试。

*   CakePHP 为核心有大量测试，我相信我在 CakePHP 1.2RC3 的变更日志中看到过一些内容，表明它们在 CakePHP 核心测试方面的代码覆盖率达到了 80%。CakePHP 的错误提交应该附带测试以证明存在可重复的问题。

*   Symfony 最近重写了其核心测试并为其创建了自己的测试框架。

所以现在当你开始比较框架彼此时，我认为你也应该考虑有多少精力投入到为该框架的核心功能创建测试。一个经过充分测试的框架在使用时应该意味着更少的意外。鉴于有这么多工具可以帮助你进行测试，我认为除了完全懒惰之外，没有任何借口不为任何应用程序的核心功能创建测试。现在付费，或以后付费，但你最终会为修复应用程序中的 bug 付费。现在付费 simply 更便宜。



你会把项目押在别人写的复杂代码上，而这段代码你根本无法测试吗？也许我看问题的角度不对，因为我身处框架创建者的文化中，但我实在看不出为什么你不愿意提供测试来证明你的东西确实如你所说那样工作。测试证明代码的行为符合你的预期，而且可测试的代码通常也更容易随着时间的推移进行修改。在修改代码、运行单元测试，然后发现自己没有破坏任何东西时，有一种病态的愉悦感。

# 15 元测试：理解模拟对象

*本文最初于 2012 年 3 月发表在我的博客上。*

在 [卡普兰专业](http://kaplanprofessional.com) 工作时，我很快学会欣赏的一件事就是非常庞大的单元测试和集成测试套件。我相信有 2000 多个测试，虽然代码覆盖率有所下降，但看到大多数项目的覆盖率仍在 65%以上，仍然令人印象深刻。我们很快就会把它恢复到应有的水平。

拥有如此庞大的测试阵列，我接受了关于编写真正认真对待单元测试的实时生产就绪代码的单元测试的真正含义的教育。我认为大多数开发者在进入测试驱动开发时遇到的最大问题是不理解如何高效地使用模拟对象。

如果你真的按照正确的方式编写单元测试，每个测试都专注于孤立地测试一个功能点，这意味着你将严重依赖模拟对象来使事情正常工作。我想出了一个示例场景，希望能很好地解释如何有效地使用模拟对象。

在这些示例中，我使用的是 `PHPUnit` 的 [内置支持](http://www.phpunit.de/manual/3.0/en/mock-objects.html) 来进行模拟对象。在 Kaplan，我们的测试工程师告诉我他曾尝试使用 [`Mockery`](https://github.com/padraic/mockery) ，但在使其与正在使用的依赖注入容器良好配合时遇到了问题（它是一个定制的 [`Pimple`](http://pimple.sensiolabs.org) 版本）。对此无法反驳。除非我自己尝试 `Mockery`，看看它是否比使用 `PHPUnit` 自带的功能带来任何好处。

所以这是我们的场景：我们有一个名为 `Alpha` 的类，其中包含一个名为 `munge()` 的方法。我们希望在单元测试中测试该方法。这个类看起来是什么样子的？

```php
<?php

class Alpha
{
    // Omit code showing constructor...

    public function munge(Foo $foo, Bar $bar)
    {
        $fooDetails = $foo->getDetails();
        $fooId = $foo->getId();

        $barStartDate = $bar->getStartDate();
        $barEndDate = $bar->getEndDate();

        $source = "{$fooId}|{$fooDetails}|{$barStartDate}|{$barEndDate}";
        
        return md5('rocksalt' . $source);
    }
}
```

我那爱挑剔的测试员眼光一看就立刻说“我们需要模拟那些 `Foo` 和 `Bar` 对象才能让这个测试工作。”首先我们需要看看 `Foo` 对象：

```php
<?php
class Foo 
{
    // Omit code showing how we construct a Foo object

    public function getId()
    {
        return $this->_id;
    }

    public function getDetails()
    {
        $tree = $this->_tree;
        $branch = $this->_branch;

        return $tree . '->' . $branch;
    }
}
```

看起来这个类代表系统中一个“`Foo`”对象。我省略了构造函数，因为它对我试图传授的课程来说并不重要。让我们假设我们可以通过某种映射器生成一个 `Foo` 对象。

我们的 `Alpha->munge()` 方法期望传入一个 `Foo` 对象，并通过 `getDetails()` 和 `getId()` 调用检索信息。让我们开始我们的测试并模拟它。

```php
<?php
class Test extends PHPUnit_Framework_TestCase
{

    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        // More test fun to come
    }
}
```

当你为测试构建模拟对象时，通常需要做两件事：

*   创建对象本身的模拟

*   告诉它在调用特定方法时该做什么

我在这里做的事情相当标准，除了使用 `disableOriginalConstructor()` 方法。为什么使用它呢？好吧，有时当你创建对象的模拟时，它通常会有接受参数的构造函数。我不是在测试是否可以创建对象，我只是试图模拟该对象的某些方法。

一旦我创建了对象的模拟，我就会告诉它在进行某些方法调用时该做什么。很明显，我只是为这个示例随意编造了一些值，但通常你可以通过，嗯，实际查看你正在模拟的代码来弄清楚一些合理的返回值应该是什么。

那么我们的 `Bar` 对象看起来是什么样子的？

```php
<?php
class Bar
{
    // Same drill, no need to show constructor details
    
    public function getStartDate()
    {
        return $this->_startDate;
    }

    public function getEndDate()
    {
        return $this->_endDate;
    }
}
```

是时候在我们的测试中添加一个模拟 `Bar` 了

```php
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        // More test fun to come
    }
}
```

关于 `$this->atLeastOnce()` 的快速说明：当你模拟对象时，你可以告诉它你期望该方法被调用的次数。我在发布这篇文章的原始版本后，与我们的测试工程师 Will Parker 就此进行了长时间的讨论。

我们有多个选项

*   `$this->once()` - 只有当你真的希望该方法只被调用一次时才应使用

*   `$this->atLeastOnce()` - 当你需要它被调用一次但不确定调用次数时应使用

*   `$this->any()` - 你真的不在乎它被调用多少次

如果你很懒，你会选择 `$this->any()`，这样就不用担心了。与 Will 讨论后，我开始喜欢使用 `$this->atLeastOnce()`。无论你选择哪一个，都不是决定性的，很多时候取决于个人偏好。

所以现在我们已经模拟了这两个对象。现在我们可以回到测试中，添加我们 `Alpha` 类的创建，将两个模拟对象注入到我们正在测试的方法中，并检查预期结果。



```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的[content]
```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的[content]
```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的
功能。

我希望这篇博文能让大家在理解创建单元测试时模拟对象的角色时变得清晰很多。

# 16 来自一位暴躁程序员的建议

我知道本指南中有很多内容需要你考虑。编写测试很容易，但创建一套真正有助于防止回归和其他问题的测试套件却很困难。

做到这一点所需的知识范围非常广。本指南只是触及了测试、自动化、持续集成和部署主题的表面。有很多种方法可以达到目标，所以不要因为选择太多而气馁。

慢慢开始，先构建你真正需要的部分。像 [IMVU](http://www.startuplessonslearned.com/2009/06/why-continuous-deployment.html) 和 [Etsy](http://codeascraft.etsy.com/) 这样的公司使用的花哨的东西不是一夜之间建成的。花了几年时间才达到那一步，而且他们在寻找适合自己的工具和实践组合的过程中犯了很多错误。

花时间找到适合你需求的正确工具组合。要达到持续部署的极乐境界，你只需要以下几点：

*   一个覆盖率足够捕获回归的测试套件
*   能够自动运行测试的能力
*   能够自动部署到指定目标的能力

就是这样。你的旅程始于使用一套工具编写一个测试的决定，并且永远不会真正结束。你会发现，当你坚持“测试先行”的理念时，你的代码会比以前更模块化、更简单。这就是你能真正要求的全部了。
