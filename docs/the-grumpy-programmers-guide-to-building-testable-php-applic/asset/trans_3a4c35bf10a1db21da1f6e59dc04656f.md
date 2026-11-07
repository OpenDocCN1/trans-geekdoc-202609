
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

## 12 基础设施债务

*这篇文章最初于 2011 年 11 月发布为博客文章，获得了关注并最终登上了 Hacker News。它与构建可测试应用程序的概念直接相关。希望你喜欢它。*

你可能遇到过“`technical debt`”这个术语，用来描述随着 `application` 增长和需求变化而在你的 `code base` 中犯下的小错误。如果你不非常小心地进行这些更改，你最终会得到一个大乱摊子。如果你曾经在担心改动会破坏某些东西而不敢更改的 `application` 上工作过，那么你就遇到了 `technical debt`。

积累 `technical debt` 非常容易：你因为感到有压力要完成任务而放入一个快速的 `hack`。需要勇气来反驳并说“不，该死，我需要时间来正确修复这个问题！”。我理解，这没关系。如果拥抱能让你感觉更好，我们可以拥抱一下。

`Technical debt` 可以通过无情的 `refactoring` 以及用 `tests` 包裹你的 `application` 来处理，这些 `tests` 会刺探你的 `application` 处理的 `edge cases`。但你最终会处理另一种债务。那是一种更难以处理和改变的债务。我称之为 `infrastructure debt`。

`Infrastructure debt` 是你因为没有关注创建 `application` 将存在的 `environments` 的过程，也没有关注你的 `code` 如何从 `development` 进入 `production` 的过程而积累的债务。在我看来，`Infrastructure debt` 比 `technical debt` 更难“偿还”。为什么？人们往往很难理解它甚至存在。

在我继续之前，如果你没有使用 `version control system` 来跟踪对你的 `code` 的更改，请停止阅读并去安装一个。用 `.1` 和 `.old` 这样的扩展名保存文件版本是你可能拥有的最糟糕的 `infrastructure debt`。现在是 21 世纪的第二个十年。`Version control` 是一个近 40 年历史、已被充分理解的概念。如果坚持认为 `version control` 对你毫无用处，我建议的任何东西都不会奏效。传递 `diff` 补丁不是 `version control`，我的朋友们。那是否认。不要告诉我，仅仅因为过去人们这样做，现在在所有可用选项面前就没问题了。人们曾经也认为地球是平的。

让我们从一个容易偿还的 `infrastructure debt` 开始：`development environments` 的不一致。如今，对于某人来说，为其选择的 `language` 创建 `development environment` 以及相关的组件如 `databases` 变得相当容易。问题是什么？就是某人很容易创建自己选择的 `development environment`。
