
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

