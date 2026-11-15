

![](img/1ddec54918a4802eb9b4febec3d4e7f6_105_0.png)

图 4-4

## 工作原理

此脚本使用若干决策和循环来模拟信鸽飞向家园，并显示结果。

首先，脚本显示 XHTML 页面页头。接着，它设置一个变量 $mapSize，表示地图正方形的宽度和高度（你不妨尝试不同的值，看看它们如何影响模拟）：

```
$mapSize = 10;
```

接下来，你会遇到脚本中的第一个循环：一个 do...while 循环。这段代码使用 PHP 的 rand() 函数，在地图边界内随机定位家园点和信鸽。定位家园和信鸽后，do...while 循环的条件会检查，确保家园和信鸽之间至少相隔地图宽度（或高度）的一半；如果不满足条件，循环就会重复，生成新的随机位置。这样可以确保信鸽总有合理的飞行距离：

```
// Position the home and the pigeon

do {
    $homeX = rand ( 0, $mapSize-1 );
    $homeY = rand ( 0, $mapSize-1 );
    $pigeonX = rand ( 0, $mapSize-1 );
    $pigeonY = rand ( 0, $mapSize-1 );
} while ( ( abs( $homeX - $pigeonX ) < $mapSize/2 ) && ( abs( $homeY - $pigeonY ) < $mapSize/2 ) );
```

内置的 abs() 函数用于获取数字的绝对值。例如，abs( 3) 是 3，abs( -3) 也是 3。

脚本中的下一个循环同样是一个 do...while 循环，它构成了模拟的主体。循环内的第一段代码使用决策逻辑来模拟信鸽的归巢本能。它只需检查信鸽的 x 坐标是大于还是小于家园方块的 x 坐标，然后适当调整信鸽的 x 坐标。y 坐标的调整方式相同：

```
// Move the pigeon closer to home
if ( $pigeonX < $homeX )
	$pigeonX++;
elseif ( $pigeonX > $homeX )
	$pigeonX--;

if ( $pigeonY < $homeY )
	$pigeonY++;
elseif ( $pigeonY > $homeY )
	$pigeonY--;
```

请注意，如果信鸽的 x 或 y 坐标与对应的家园坐标匹配，则无需调整信鸽的坐标。因此，没有 else 代码分支。

循环内的最后一段代码用于显示当前地图。这段代码本身包含两个嵌套的 for 循环，遍历地图上的所有 x 和 y 坐标。对于地图中的每个方块，如果方块匹配家园位置的坐标，代码显示 + 符号；如果方块匹配信鸽的坐标，则显示 % 符号。否则，它显示一个点（.）。在每个方块之后，它会添加一个空格字符（除非是行上的最后一个方块）：

```
// Display the current map
echo '<div class="map" style="width: ' . $mapSize . 'em;"><pre>';
for ( $y = 0; $y < $mapSize; $y++ ) {
	for ( $x = 0; $x < $mapSize; $x++ ) {
		if ( $x == $homeX && $y == $homeY ) {
			echo '<span class="home">+</span>'; // Home
		} elseif ( $x == $pigeonX && $y == $pigeonY ) {
			echo '<span class="pigeon">%</span>'; // Pigeon
		} else {
			echo '<span class="empty">.</span>'; // Empty square
		}
		echo ( $x != $mapSize - 1 ) ? " " : "";
	}
	echo "\n";
}
echo "</pre></div>\n";
```

最后，你到达主 do...while 循环的末尾。如你所料，当信鸽坐标与家园坐标匹配时，循环结束：

```
} while ( $pigeonX != $homeX || $pigeonY != $homeY );
```

此外，脚本使用了多种 CSS 样式（嵌入在页面的 head 元素中）来改善地图的外观。

## 将决策与循环与 HTML 混合使用

在第 2 章中，你学习了可以将 PHP 嵌入 HTML 网页，而且，本书中的大多数示例都使用这种技术，在 PHP 代码周围包裹 XHTML 页面页头和页脚。

你还学习了可以通过使用 <?php ... ?> 标签，在显示 HTML 标记和执行 PHP 代码之间切换。在决策和循环中，这一功能尤其有用，因为你可以使用 PHP 控制网页显示哪些部分（以及如何显示）。

下面是一个简单的示例：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Fibonacci sequence</title>
<link rel="stylesheet" type="text/css" href="common.css" />
<style type="text/css">
th { text-align: left; background-color: #999; }
th, td { padding: 0.4em; }
tr.alt td { background: #ddd; }
</style>
</head>
<body>
<h2>Fibonacci sequence</h2>
<table cellspacing="0" border="0" style="width: 20em; border: 1px solid #666;">
<tr>
<th>Sequence #</th>
<th>Value</th>
</tr>
<tr>
<td>&lt;?sub 0< /sub&gt;
<td>0</td>
</tr>
<tr class="alt">
<td>&lt;?sub 1< /sub&gt;
<td>1</td>
</tr>
<?php
$iterations = 10;

$num1 = 0;
$num2 = 1;

for ( $i=2; $i <= $iterations; $i++ )
{
    $sum = $num1 + $num2;
    $num1 = $num2;
    $num2 = $sum;
?>
        <tr><?php if ( $i % 2 != 0 ) echo ' class="alt" ?>
        <td><?php echo $i?></td>
        <td><?php echo $num2?><td>
        </tr>
<?php
}
?>
</table>
</body>
</html>
```

尝试将此文件保存为 fibonacci.php，放在你的文档根文件夹中，并在浏览器中运行该脚本。图 4-5 显示了结果。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_108_0.png)

图 4-5

这段代码显示斐波那契数列的前 10 个数字。首先显示 XHTML 页面页头和表格页头。然后，一个 for 循环生成每个斐波那契数字，每次循环时跳出到 HTML 以显示包含该数字的表格行。请注意，脚本多次使用 `<?php ... ?>` 标签在 HTML 标记和 PHP 代码之间切换。交替的表格行是通过 head 元素中的 CSS 类与嵌入在表格行标记中的 if 决策结合实现的。

你可以看到，从循环内部或作为决策的结果，输出整个 HTML 块（在本例中为表格行）是多么容易。

## 总结

在本章中，你探讨了 PHP（或任何编程语言）的两个关键概念：决策和循环。决策允许你根据表达式的值选择运行一段代码，包括：

- if 语句，用于做简单的“二选一”决策
- else 和 elseif 语句，用于具有多种结果的决策
- switch 语句，用于根据表达式的值运行代码块
- ?（三元）运算符，用于编写紧凑的 if...else 风格决策

循环允许你反复运行同一段代码，直到满足某个条件。你学习了：

- while 循环，在循环开始时测试条件
- do...while 循环，在循环结束时测试条件
- for 循环，允许你编写整洁的“计数”循环

你还学习了其他与循环相关的语句，包括用于退出循环的 break 语句和用于跳过当前循环迭代的 continue 语句。最后，你探索了嵌套循环，并了解了 PHP 的一项强大功能：将决策和循环语句与 HTML 标记混合使用。

在下一章中，你将深入了解 PHP 中的字符串以及如何操作它们。不过，在阅读之前，请尝试以下两个练习，以巩固你对决策和循环的理解。一如既往，你可以在附录 A 中找到练习的参考答案。

## 练习

- 1. 编写一个脚本，以步长 1 从 1 数到 10。对于每个数字，显示该数字是奇数还是偶数，并且如果该数字是质数，还要显示一条消息。在 HTML 表格中显示这些信息。

- 2. 修改归巢信鸽模拟器，在同一张地图上模拟两只不同的信鸽，它们都飞向同一个家园点。当两只信鸽都回到家时，模拟结束。

## 字符串

你在前面的第 3 章中简要了解过字符串的概念。在编程术语中，字符串只是一系列字符。例如，"hello"、"how are you?"、"123" 和 "!@#$%" 这些值都是有效的字符串值。

从根本上说，Web 基于字符串数据。HTML 和 XHTML 页面由纯文本字符串组成，HTTP 头信息也是如此（第 16 章将详细介绍），URL 自然也是。你可以想象，这意味着 PHP 等 Web 编程语言特别适合处理字符串。事实上，PHP 有近 100 个不同的函数专门用于操作字符串。

例如，你可以使用 PHP 的字符串函数来：

- 在字符串中查找文本
- 将字符串中的一些文本替换为另一段文本
- 格式化字符串，使其更易于阅读或处理
- 使用各种流行的编码格式对字符串进行编码和解码

除此之外，你还可以使用正则表达式处理字符串（你将在第 18 章中了解正则表达式）。

在本章中，你将了解 PHP 中字符串的基础知识——如何创建字符串值和变量，以及如何访问字符串中的字符。然后，你将探索 PHP 的字符串函数。本章并不旨在涵盖 PHP 中的每一个字符串函数；这个主题本身就足以写一整本书。相反，你将学习日常情况下最有用（也最常用）的函数。

> 如果你想获取 PHP 字符串函数的完整列表，可以在在线 PHP 手册中查阅：www.php.net/manual/en/ref.strings.php。

