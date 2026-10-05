

# 第 38 Lesson：Google 折线图

**目标：** 在本节中，你将学习如何集成 Google 图表 API。我决定让它与我的 FileMaker Pro 11 文章《图表，第2部分》（可以在我们的网站 www.formulationspro.com/FileMaker 章节查看）非常相似，在该文中我创建了一个用于监控设施温度的统计过程控制图。你将能够看到 FileMaker Pro 与 PHP 制作图表之间的差异。PHP 的构建显然更加复杂，因为没有向导可以帮助你。结果是，你将能够构建一个完全按照你想要的方式显示数据的复合折线图。

**难度：** 中等

**示例文件：**
PHPFiles/Advanced/Lesson38/GoogleLineChart.php
PHPFiles/Advanced/Lesson38/GoogleLineCharts.fmp12

> 本节使用独立的数据库文件进行演示。请将 GoogleLineCharts.fmp12 数据库文件上传到你的服务器。

# 页面导航：

- 列表

**FileMaker API 方法：**
- newFindAllCommand()
- addSortRule()->execute()
- Records()
- getField()

# 代码：

折线图具有许多可以迅速变得复杂的特性。特别是当你有多个数据系列时。Google Chart API 允许你构建简单的无轴图表，为每个点定义 x 和 y 坐标，并创建复合折线图。我选择创建一个复合折线图来表示我的数据图表、上控制限（UCL）和下控制限（LCL）。

Google Chart API 让每个技能水平的人都能轻而易地创建图表。你将遇到的最困难的事情是从数据库中检索数据并按照它们的标准进行格式化，这其实并不困难。之后，就取决于你想要利用图表的哪些功能了。有几个必需的元素和大量可以你利用的可选元素。本节的示例网页包含了每个元素，仅需一行简单的代码即可嵌入图像，它将所有数据传递给 Google 并向你的网页返回一个图表。

> 有关 Google Chart API 的完整信息，请访问 Google 网页：http://google.com/apis/chart/image/docs/making_charts.html

始终从连接到数据库开始。

```php
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setDatabase('database', 'GoogleLineCharts');
```

```php
$fm->setProperty('hostspec', 'http://127.0.0.1');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
```

对于本文，我将简单地查找数据库中的所有记录并按 `Date` 字段升序排序。然后将数据以 Google API 要求的格式（即：Number、UCL 和 LCL 字段）存储在每个记录中，并用逗号进行格式化，每个索引数据系列通过图表轴显示为 1,2,3,4,5,6,7,8,9 分隔。X 轴（即从第一个数据点开始 1 的记录运行计数）需要用管道字符 `|` 进行格式化，例如 `|1|2|3|`。这些格式需要经过编辑，否则图表将返回错误。注意，管道字符比数字宽，所以看起来很奇怪，但我预计短期内不会修复这个问题。

我们还将计算 Y 轴的最小值和值。如果你没有定义这些数字，API 将把你的值归一化为 100%，这将超出图表的范围。为了计算值，我们将从 LCL 开始。然后当我们遍历记录时，我们只需要检查它是否小于任何数据、UCL 或 LCL 值，这将容纳一个带有负值的完整图表。否则，它会将 Y 轴缩放到 5%，以确保 Y 轴的最大值稍早出现。将值设为 UCL 开始。然后当我们遍历每条记录时，如果任何数据、UCL 或 LCL 值更大，我们就可以更改它。我还建议你将最终最大值缩放 5%，以确保线条位于图表内部，从而获得清晰的视觉效果。

```php
$request = $fm->newFindAllCommand('Demo');
$request->sort->addSortRule('Date', 1, FILEMARKER_SORT_ASCEND);
$result = $request->execute();
$records = $result->getRecords();
$record = $result->getFirstRecord();
if($record) {
	$min=$record->getField('LCL');
	$max=$record->getField('UCL');
	$n=1;
foreach($records as $record) {
		$data[]=$n . ",";
		$labels[] = "," . $n . ",";
		$ucl=$record->getField('UCL') . ",";
		$lcl=$record->getField('LCL') . ",";
		if(min($record->getField('LCL'), $record->getField('UCL')) < $min) {
			$min=min($record->getField('LCL'), $record->getField('UCL')));
			$record->getField('Number');
		}
		if(max($record->getField('LCL'), $record->getField('UCL')) > $max) {
			$max=max($record->getField('LCL'), $record->getField('UCL')));
			$record->getField('Number');
		}
		$data = rtrim($data, ",");
		$ucl = rtrim($ucl, ",");
		$lcl = rtrim($lcl, ",");
		$labels = rtrim($labels, ",");
		$data = $data . "." . $ucl . "." . $lcl;
		$n++;
}
}
```

# 必需元素

与其他元素不同，目标是构建一个用于容器的 URL 字符串。图表类型的基础 URL 字符串是：

https://googleapis.com/chart/

从这里添加由 `&` 分隔的所有键值对（NP），`&` 是 `.` 的 URL 编码值。因为我们将把图表 URL 作为图像源嵌入网页中。为了获得正确的 URL 字符串，特殊字符需要进行 URL 编码。这包括数据中任何可能导致字符串出现问题的值。与其制作一个巨大的值字符串，我决定在 PHP 代码中定义必需和可选变量。然后按任何顺序组装最终 URL 字符串以读取和修改格式。NP 可以按任何顺序组装。

```php
<?php
// ... (组装最终 URL 字符串的逻辑)
$scht = "https://googleapis.com/chart/?cht=lc&";
```

