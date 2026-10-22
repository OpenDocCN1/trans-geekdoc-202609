
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

## 12. 元测试

### 变异测试

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

## 第 13 章 构建测试文化

要营造一个让测试成为日常工作不可或缺一部分的环境，需要付出大量努力。它不能是事后的想法，也不能在截止日期逼近时被抛诸脑后。测试必须成为一项首要实践，否则根本无法奏效。我们还要确保把术语都弄清楚——当我说“构建测试文化”时，它到底意味着什么？

### 首要目标

首要目标应该是“我们的开发人员为所有进入生产环境的代码编写测试。”任何低于这一标准的情况，都会让那些纪律稍差或对交付时间更加焦虑的人有机会故态复萌，并放弃为所有代码编写测试这一首要目标。

首要目标本应是崇高而雄心勃勃的——但在这种情况下，它们完全可以实现。你绝对可以为开发人员提供他们学习编写测试所需的全部培训和支持。你只需要改变自己的行为，并且很可能需要挑战许多你原来关于编程的信念。

设定好首要目标之后，我们来谈谈实现首要目标所需的次级目标。

### 将测试视为一流组件

当然，如果你没有任何测试，就不可能拥有包含测试的文化！这通常是任何组织走向以测试为中心的最大障碍。回想一下你学习用 PHP 编程的时候——有人教过你编写测试吗？如果有，那你真是太幸运了！

这看起来可能不言而喻，但你要做的第一件事是承诺为任何新编写的代码编写测试。是的，随着组织转型，这很可能会很痛苦。是的，你可能会为此抱怨。我不止一次参加过这样的会议，人们抱怨说如果不是“因为这些我必须写的愚蠢测试”，他们的工作早就完成了。

开发人员大多以自己的逻辑和问题解决能力为傲，但他们和其他人一样抗拒改变。养成让代码总是伴随测试的习惯会很难。

如果你想找一种更轻松地开始添加测试的方法，这里有一些你可以采用的策略。

### 为 Bug 编写测试

每当有人报告 Bug 时，编写一个测试来验证该 Bug 确实存在。我的意思是，这个测试应该失败；你应该知道正确结果应该是什么，然后让测试生成它自己的结果，并与预期进行比较。

有了一个失败且包含正确结果预期的测试，你不断修改被测代码，直到测试通过。现在，你有了一个通过的测试！

由 Bug 修复组成的测试套件，还能让你看到代码中的一些常见模式——尤其是当你觉得自己在反复修复同一类 Bug 时。

从指导者的角度看，让项目新手编写能验证 Bug 存在的测试用例可能是一个好策略。这让他们有机会探索代码库，理解各个部分如何组合在一起。对于某些代码库来说，这肯定会让人望而生畏。让他们有机会通过测试来学习代码库，可能比分配需要上线到生产环境的工作风险更低。

### 为新功能编写测试

每当你添加新代码时，都必须附带能证明新代码按预期工作的测试。这与为 Bug 编写测试类似，但在这种情况下，你是用测试来帮助自己创建可工作的代码。

在“测试是为新功能服务”的语境下，测试驱动开发（TDD）可以真正大放异彩。TDD 本质上是一种以特定方式编写代码的策略——它能让代码在很少摩擦或开发痛苦的情况下被测试。

这并非没有代价。通常，遗留应用并不适合让你编写易于测试的代码。这是许多开发人员撞上的障碍，结果他们放弃了拥有测试的目标。

我没有任何捷径能让这件事变得更容易。你所感受到的痛苦既不好也不坏——它只是当前应用架构的结果。测试良好的应用往往由一些小型代码模块组成，这些模块：

- 接受少量输入
- 除了传入的内容之外不修改任何东西（无副作用）
- 返回少量输出

当你拥有这样的代码时，测试就很容易！大多数代码并非如此。你将需要重写一些代码；你将需要开始使用新的策略；你最终创建新代码及其配套测试所需的时间，会比你以为的更久。

这一切的好处在于，根据你编写代码时所掌握的信息，你拥有能证明新功能将按预期工作的测试。良好的防御性编码习惯会有一些帮助，但事实是，拥有 100% 覆盖率单元测试的代码并不总是意味着你的应用就能正确运行。你仍然需要将它们连接起来，并以合理的方式使用它们。测试绝对不是常识的替代品。
