

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

