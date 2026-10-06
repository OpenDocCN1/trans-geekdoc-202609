

# 第二部分：学习语言

![](img/ede05b7b77968b82cbd9a513122fb183_105_0.png)

图 4-4

## 工作原理

该脚本使用若干决策和循环来模拟鸽子飞回家的过程，并显示结果。

首先，脚本会显示一个 XHTML 页面头部。然后，它设置了一个变量 `$mapSize`，代表地图正格的宽度和高度（你可能想尝试不同的值，看看它们如何影响模拟结果）：

```php
$mapSize = 10;
```

接下来，你遇到了脚本的第一个循环：`do...while` 循环。这段代码使用 PHP 的 `rand()` 函数在地图边界内随机为家点和鸽子的位置。在确定了家和鸽子的位置后，`do...while` 循环的条件会检查并确保家和鸽子之间的距离至少为地图宽度（或高度）的一半；如果不是，循环将使用新的随机位置重复执行。这确保了鸽子有合理的距离可以飞行。

```php
// Position the home and the pigeon
```

```php
do {
    $homeX = rand ( 0, $mapSize-1 );
    $homeY = rand ( 0, $mapSize-1 );
    $pigeonX = rand ( 0, $mapSize-1 );
    $pigeonY = rand ( 0, $mapSize-1 );
} while ( abs( $homeX - $pigeonX ) < $mapSize/2 ) && ( abs( $homeY - $pigeonY ) < $mapSize/2 );
```

# 第 4 章：决策与循环

内置的 `abs()` 函数确定数字的绝对值。例如，`abs(3)` 是 3，而 `abs(-3)` 也是 3。

脚本中的下一个循环也是 `do...while` 循环，它包含了代码的主体。循环内部的第一段代码使用决策来模拟鸽子的归巢本能。它简单地检查鸽子的 x 坐标是否大于或小于家点的 x 坐标，并相应地调整鸽子的 x 坐标。y 坐标以同样的方式调整：

```php
// Move the pigeon closer to home

if ($pigeonX < $homeX)
    $pigeonX++;
else if ($pigeonX > $homeX)
    $pigeonX--;

if ($pigeonY < $homeY)
    $pigeonY++;
else if ($pigeonY > $homeY)
    $pigeonY--;
```

注意，如果鸽子的 x 或 y 坐标与对应的家坐标匹配，则不对鸽子的坐标进行任何调整。这里没有 `else` 代码分支。

循环内部的最后一段代码涉及显示当前地图。这段代码本身使用了两个嵌套循环来遍历地图上所有的 x 和 y 坐标。对于每个格，如果该格与家点的坐标匹配，则显示 `+` 符号；如果与鸽子的坐标匹配，则显示 `%` 符号。否则，显示 `.`。在每个格之后，它会添加一个空格字符（除非它是该行的最后一个格）：

```php
// Display the current map

echo '<div class="map" style="width: ' . $mapSize . 'em;"><pre>';

for ($y = 0; $y < $mapSize; $y++) {
    for ($x = 0; $x < $mapSize; $x++) {
        if ($x == $homeX && $y == $homeY) {
            echo '<span class="home">+</span></span>'; // Home
        } elseif ($x == $pigeonX && $y == $pigeonY) {
            echo '<span class="pigeon">%</span></span>'; // Pigeon
        } else {
            echo '<span class="empty">.</span></span>'; // Empty square
        }
        echo ($x == $mapSize - 1) ? " " : "";
    }
}

echo "\n";

echo "</div>\n";
```

最后，你到达了主 `while` 循环的终点。正如你预期的那样，一旦鸽子的坐标与家的坐标匹配，循环就会结束：

```php
} while ($pigeonX != $homeX && $pigeonY != $homeY);
```

此外，脚本使用了各种 CSS 样式（嵌入在页面的 head 元素中）来改善地图的外观。

## 在 HTML 中结合决策与循环

在第 2 章中，你学习了可以将 PHP 嵌入到 HTML Web 页面中，事实上，书中的大多数示例都使用了这种技术来在 PHP 代码周围包裹 XHTML 页面头部和页部。

你还学习了可以通过 `<?php ... ?>` 标签在显示 HTML 标记和导出 PHP 代码之间切换。这一功能在决策和循环中真正发挥了作用，因为你可以使用 PHP 来控制 Web 页面中显示哪些部分（以及如何显示它们）。

这是一个简单的示例：

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/html/DTD/xhtml-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
  <title>Fibonacci sequence</title>
  <link rel="stylesheet" type="text/css" href="common.css">
</head>
<body>
  <h2>Fibonacci sequence</h2>
  <table>
    <tr>
      <th>Sequence</th>
      <th>Value</th>
    </tr>
    <?php
    $iterations = 10;
    $num1 = 0;
    $num2 = 1;

    for ($i = 0; $i < $iterations; $i++) {
      $class = ($i % 2 == 0) ? "alt" : "";
      echo "<tr class='$class'>";
      echo "<td>$i</td>";
      echo "<td>$num1</td>";
      echo "</tr>";

      $temp = $num1 + $num2;
      $num1 = $num2;
      $num2 = $temp;
    }
    ?>
  </table>
</body>
</html>
```
*(注：由于原文提供的 HTML 示例在文本中存在标签闭合错误/混乱，翻译时保持了其逻辑结构并修正了明显的排版错误以确保可读)*

# 第二部分：学习语言

![](img/ede05b7b77968b82cbd9a513122fb183_108_0.png)

图 4-5

# 第二部分：学习语言

这段代码显示前10个斐波那契数列。首先显示 XHTML 页面头部和表头。然后使用 for 循环生成每个数字，每次都跳出 HTML 进行显示。注意脚本如何多次使用 `<?php ... ?>` 在 HTML 标记和 PHP 代码之间切换。交替表格行通过 head 中的 CSS 实现。

```php
<?php
$iterations = 10;
$num1 = 0;
$num2 = 1;

for ($i = 0; $i < $iterations; $i++) {
  $class = ($i % 2 == 0) ? "alt" : "";
  echo "<tr class='$class'>";
  echo "<td>$i</td>";
  echo "<td>$num1</td>";
  echo "</tr>";

  $temp = $num1 + $num2;
  $num1 = $num2;
  $num2 = $temp;
}
?>
```

# 总结

在本章中，你探索了 PHP（或任何语言）的核心概念：决策和循环。让我们根据表达式的值来运行代码块，包括：

- `if` 语句用于简单的或决策
- `else` 和 `elseif` 语句用于多结果的决策
- `switch` 语句根据表达式的值运行代码块
- `?`（三元）运算符用于编写 `if...else` 风格的决策

循环允许多次运行同一代码块直到满足特定条件。你学习了：

- `while` 循环在循环开始时测试条件
- `do...while` 循环在循环结束时测试条件
- `for` 循环用于编写整洁的计数循环

你还查看了其他循环相关的语句，包括用于退出循环的 `break` 语句和用于跳过当前循环迭代的 `continue` 语句。最后，你探索了嵌套循环，并查看了 PHP 的强大功能：结合 HTML 标记进行决策和循环。

# 练习

- 编写一个脚本从1计数到10。对于每个数字，显示该数字是奇数还是偶数，如果该数字是质数也显示一条消息。在 HTML 表格中显示这些信息。
- 修改鸽子模拟器，在同一地图上模拟两只不同的鸽子，它们都飞向同一个点，当这些鸽子回到家时结束。

