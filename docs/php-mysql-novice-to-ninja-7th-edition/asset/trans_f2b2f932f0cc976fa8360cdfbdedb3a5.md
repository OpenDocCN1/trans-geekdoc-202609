
### 示例：[PHP 掷骰子-双骰子](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-TwoDice)

```
$roll1 = rand(1, 6);
$roll2 = rand(1, 6);

echo '<p>You rolled a ' . $roll1 . ' and a ' . $roll2 . '</p>';

if ($roll1 == 6 && $roll2 == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
}

echo '<p>Thanks for playing</p>';
```

条件 `$roll1 == 6 && $roll2 == 6` 只有在 `$roll1 == 6` 为真 *和* `$roll2 == 6` 时才会被满足。这意味着玩家必须在两个骰子上都掷出 6 才能赢得游戏。如果我们将 and (`&&`) 改为 or (`||`)——即 `if ($roll1 == 6 || $roll2 == 6)`——玩家只要在任一骰子上掷出 6 就会获胜。

我们会在需要时查看更复杂的条件。目前，熟悉 `if … else` 语句就足够了。

### `and` 和 `or`

PHP 还允许使用 `or` 代替 `||`，使用 `and` 代替 `&&`。例如：

```
if ($roll == 6 or $roll == 5) { … }
```

`or` 和 `||` 的工作方式存在一些细微差异，这可能导致意外的行为。一般来说，避免使用“拼写出来”的运算符。坚持使用双竖线 (`||`) 和双与号 (`&&`) 有助于防止许多令人困惑的错误。

## 循环

另一种非常有用的控制结构是“循环”。**循环** 允许你一次又一次地重复相同的代码行。两种重要的循环是 `for` 循环和 `while` 循环。让我们看看它们是如何工作的。

### For 循环

`for` 循环用于在开始时就知道需要运行相同代码的次数。下面的图像显示了 `for` 循环的流程。

![for 循环的逻辑流程](Images/programming_flowchart_for.png)

它在代码中看起来是这样的：

```
for (declare counter; condition; increment counter) {
  ⋮ statement(s) to execute repeatedly as long as condition is true
}
```

`declare counter` 语句在循环开始时执行一次。`condition` 语句在每次循环之前检查，然后执行循环体中的语句。`increment counter` 语句在每次循环体中的语句执行后执行。

要使用 `for` 循环数到十，可以使用以下代码：

```
for ($count = 1; $count <= 10; $count++) {
  echo $count . ' ';
}
```

这看起来很吓人，因为有很多内容，但让我为你分解一下：
*   `$count = 1;`. 你已经熟悉这段代码。它创建了一个名为 `$count` 的变量并将其值设为 `1`。
*   `$count <= 10;`. 这是条件。可以读作“只要 `$count` 小于或等于 10 就继续循环”。
*   `$count++`. 这表示“每次将计数器加 1”。它等同于 `$count = $count + 1`。
*   `echo $count . ' ';`. 这会打印计数器的值后跟一个空格。

此示例中的条件使用了 `<=` 运算符。它与小于运算符 (`<`) 类似，但如果比较的数字 *小于或等于* 第二个数字，则求值为真。其他可用的运算符包括 `>=`（大于或等于）和 `!=`（不等于）。

`for` 循环的三个部分组合起来产生完整的循环。乍一看，代码似乎有点难以阅读，但将控制循环的所有代码放在同一位置，一旦习惯了语法，反而更容易理解。本书中的许多示例都会使用 `for` 循环，因此你会有充足的机会练习阅读它们。

你可以更改 `for` 循环的每个部分以获得不同的结果。例如，让我们看看如何每次加 `3` 你可以更改 `for` 循环通过修改最后一部分。

循环的最后一部分 `$count++` 表示 *将 1 加到 `$count` 的值上*，并且它是 `$count = $count + 1` 的简写方式。

通过将 `$count++` 更改为 `$count = $count + 3`，`for` 循环可用于按三计数。

### 示例：[PHP-For](https://github.com/spbooks/phpmysql7/tree/PHP-For)

```
for ($count = 1; $count <= 10; $count = $count + 3) {
  echo $count . ' ';
}
```

这将产生以下结果：

```
1 4 7 10
```

`for` 循环可以与其他语句（如 `if` 语句）结合使用，以在每次迭代中执行特定任务。例如，与其每次刷新页面玩我们的骰子游戏，我们可能希望掷骰子十次并打印结果。

### 示例：[PHP 掷骰子-多次掷骰子](https://github.com/spbooks/phpmysql7/tree/PHP-DiceRoll-ManyDice)

```
for ($count = 1; $count <= 10; $count++) {
  $roll = rand(1, 6);
  echo '<p>You rolled a ' . $roll . '</p>';

  if ($roll == 6) {
    echo '<p>You win!</p>';
  }
  else {
    echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
  }
}

echo '<p>Thanks for playing</p>';
```

这让我们可以在不每次刷新页面的情况下掷骰子十次。使用循环在功能上等同于复制并粘贴代码十次，并且会产生与以下完全相同的结果：

```
$roll = rand(1, 6);
echo '<p>You rolled a ' . $roll . '</p>';

if ($roll == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
}

$roll = rand(1, 6);
echo '<p>You rolled a ' . $roll . '</p>';

if ($roll == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
}

$roll = rand(1, 6);
echo '<p>You rolled a ' . $roll . '</p>';

if ($roll == 6) {
  echo '<p>You win!</p>';
}
else {
  echo '<p>Sorry, you didn\'t win. Better luck next time!</p>';
}

// and so on …
```

计算机不在乎你使用哪种方法：你可以复制/粘贴或使用循环。它只会运行代码。然而，作为一名开发者，你很快就会意识到循环是更好的选择。如果想更新代码以允许 `5` 也作为获胜数字，你需要在十个不同的地方更新条件。使用循环，你可以在一个地方更改代码，它将影响循环的每次迭代。如果你发现自己在复制/粘贴代码，总有更好的方法来实现你想要做的事情。

### For 循环挑战

有了你对循环的新知识，你应该能够开始为自己编写代码。你能完成这些挑战吗？
*   **挑战 1**：打印 21 到 99 之间的所有奇数。
*   **挑战 2**：打印九的乘法表直到 12 x 9（`9 18 27` … 等），不要使用乘法运算符（`*`）或 `if` 语句。
*   **挑战 3**：以以下格式打印九的乘法表：

```
1x9 = 9
2x9 = 18
… etc.
```

这次，你需要使用乘法运算符！

### While 循环

另一种常用的 PHP 控制结构是 `while` 循环。`if … else` 语句允许我们根据某个条件选择是否执行一组语句，而 `while` 循环允许我们使用条件来确定重复执行一组语句的 *次* 数。

下图显示了 `while` 循环的工作方式。

![while 循环的逻辑流程](Images/programming_flowchart_while.png)

`while` 循环在代码中看起来是这样的：

```
while (condition) {
  ⋮ statement(s) to execute repeatedly as long as condition is true
}
```

`while` 循环的工作方式与 `if` 语句非常相似。不同之处在于当条件为真且执行语句时。与其继续执行闭合大括号 (`}`) 之后紧跟的语句，条件会被再次检查。如果条件仍然为真，语句将被第二次执行，第三次执行，并且只要条件保持为真就会继续执行。条件第一次求值为假时（无论是第一次检查还是第一百次），执行会立即跳转到 `while` 循环之后的大括号之后的语句。
