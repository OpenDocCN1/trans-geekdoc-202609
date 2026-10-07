
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

## 必需元素

与其他元素不同，目标是构建一个用于容器的 URL 字符串。图表类型的基础 URL 字符串是：

https://googleapis.com/chart/

从这里添加由 `&` 分隔的所有键值对（NP），`&` 是 `.` 的 URL 编码值。因为我们将把图表 URL 作为图像源嵌入网页中。为了获得正确的 URL 字符串，特殊字符需要进行 URL 编码。这包括数据中任何可能导致字符串出现问题的值。与其制作一个巨大的值字符串，我决定在 PHP 代码中定义必需和可选变量。然后按任何顺序组装最终 URL 字符串以读取和修改格式。NP 可以按任何顺序组装。

```php
<?php
// ... (组装最终 URL 字符串的逻辑)
$scht = "https://googleapis.com/chart/?cht=lc&";
```

```php
$chtt = 'chtt=SalesByRegion' . ' ' . date('m/d/Y') . ' ' . '&';
$chs = 'chs=FF0000,12,c' . ' ' . '&';
```

你可以在图表的任何位置显示图例信息。我建议，如果 X 轴标签相互重叠，图例可能并不可用。你还可以在图表下方显示一个包含数据的表格。

```php
$chdl = 'chdl' . '.labels' . ' ' . '&';
$chldp = 'chldp=1' . ' ' . '&';
```

你可以定义线条的颜色。默认情况下，你将获得橙色。你可以为每个柱状图指定单一颜色或自定义颜色。我建议默认颜色是最好的，因为它们代码更少，而且不会浪费 2K 的字符限制。不过，考虑到我确信总会有三条线，所以我为每个数据系列定义了颜色。

```php
$chco = 'chco' . '0000FF,FF0000,FF0000' . ' ' . '&';
```

图表和图例边距类似于图表的单元格填充（padding）。这些值将强制标签和图表正确缩放以适应图表的大小。

```php
$chma = 'chma' . '20,20,20|50,50' . ' ' . '&';
```

最后，你可以用自定义颜色、渐变甚至透明度设置填充图表的背景。这将为图表提供自定义的视觉外观。

```php
$chf = 'chf' . 'bg,s=EFEFEF' . ' ' . '&';
```

还有其他可选元素和数据函数可用。我鼓励你至少查看一下，看看它们是否对你感兴趣。我倾向于让我的图表简单且直接，让数据脱颖而出，而不一定是设计。

现在你已经已经在 PHP 代码中定义了所有变量，可以组装 NVP（可选参数）。我们将使用最简单的 GET 方法来获取图像。我们将使用源指向 Google Chart URL 的 `img` 标签。如果由于某种原因你的字符串超过了 2K，你可以利用 POST 方法获取图像。Google 提供了实现此图表的完整说明。现在，我们将使用图像标签和 PHP 代码来显示图表：

```html
<img src="https://chart.googleapis.com/chart?<?php echo $chtt . $chs . $chds . $chd . $chcl . $chxr . $chm . $chco . $chid; ?>">
```

你能想象必须用所有原始字符串来组装源吗？我相信在 PHP 代码中设置变量可以为每种类型的图表创建模板变得更容易，更容易修改图表的设计和显示，并且显然让图像更更容易组装和解析。

![](img/5a2c5fda68d42e5d65f51850276e49ec_308_0.png)

图 7-104：Google 折线图

## 第39 节：Google Map API 商店定位器

**目标：** 在本节中你将学习如何集成 Google map API。如果你一直尝试将 Google maps 集成到你的 FileMaker PHP 站点，我知道你查看过他们的代码，要么放弃了，要么在忍受无数页文档和 JavaScript 中浪费了时间。截至 2011 年 5 月，Brad Welled 发布了一个卓越的 PHP 类，让 Google Maps 变得极其容易使用。尽管没有被 Google “官方支持”（因为它不是内部项目），但他们在会议上展示了它，并为 Brad 提供了一个使用他们域名的漂亮网站。这告诉我 Google 真的很喜欢它，我也一样。你可以在此处找到关于该类的更多信息：

```
http://code.google.com/p/php-google-map-api/
```

**难度：** 困难

**示例文件：** 

- `PHPFiles/Advanced/Lesson39/GoogleMap.php`

- `PHPFiles/Advanced/Lesson39/JSMIn.php`

- `PHPFiles/Advanced/Lesson39/StoreLocator.php`

- `PHPFiles/Advanced/Lesson39/StoreLocator.f12`

本节使用独立的数据库文件来演示。请将 `StoreLocator.fmp2` 数据库文件上传到你的服务器。

![](img/5a2c5fda68d42e5d65f51850276e49ec_309_0.png)

**页面导航：**

| 列表 |

|---|

**FileMaker API 方法：**

- `newPerformScriptCommand(`

- `getRecords(`

- `getField(`

**代码：**

Brad 的 V3 版本中有许多可用功能，我可能花费大量时间来介绍开发者一些最常见的请求以涵盖所有内容。相反，我将获取并将其插入你自己的数据库中。我的目标是将现有的文档（或缺失文档）和示例代码转换为 FileMaker 开发者社区有用的东西。第一个示例将创建一个商店定位器，利用 Google 的地理编码服务（Geocoding service）查找并显示具有用户定义距离数据库记录。

数据库具有名称、地址、城市和州的字段。这些应该是显而易见的。接下来是用于餐厅的纬度（Lat）和经度（Lon）字段。我已提供了记录的数据。在下一节中，我将向你展示如何获取并插入你自己的记录中。SearchLocation 和 Distance 字段用于商店定位器根据用户提供的信息查找记录。距离计算使用大圆导航公式（又称 Haversine 公式）来计算用户位置与每家商店之间的距离。关于该公式的更多信息，可以从我使用 FileMaker Pro 9 发表的《Map Distance》文章中找到：

```
http://www.formulations.com/pages/filemaker/detail.php?id=213
```

或者：

http://en.wikipedia.org/wiki/Haversine_formula

或者

距离计算的数学涉及相当复杂的三角学。由于数学课不是重点，我将让你自己理解这些数学，只要你可以直接使用该计算且它就能正常工作。关于距离计算，我唯一要说的是它是按英里计算距离。如果你在公里中使用它，可以更改计算中的常量。

### StoreLocator.php

有两个主要过程来使此解决方案运行。首先是 PHP 页面。其次是商店定位器。分别描述它们更高效，所以我们将从 PHP 页面开始。始终从包含数据库的连接开始。

```php
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'StoreLocator');
$fm->setProperty('hostname', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>
```

你还需要包含下载文件中要求你提供的两个类。`GoogleMap.php` 包含了连接到 Google Map API 的所有代码。从技术上说你不需要对其进行任何操作。但是，如果你浏览它，你会发现你可以通过将值从 `false` 改为 `true` 来配置通过 API 提供的任何功能。大多数功能在该文件中默认开启。对于控制 Google Map API 的简单性，我怎么说都不为过。你会怎么做——将值从 `false` 改为 `true`，还是处理 Google 的数百行代码？接下来是 `JSMin.php`，就这些了。再次，我向 Brad 致敬，因为他将所有代码移植到了 PHP。你不需要编写任何 JavaScript。它就能正常工作！

```php
<?php
include_once('GoogleMap.php');
include_once('JSMin.php');
?>
```

接下来，使用 `PHP_SELF` 动态快捷创建表单，将表单指向同一页面。之后，你可以根据你的解决方案设置任何合理值的距离弹出菜单。

```
<option value="25">25</option>
<option value="50">50</option>
<select>
<br>
<input name="submit" type="submit">
</form>
```

现在我们可以进入代码的核心部分，该类只需几行代码就能驱动 Google Map API。在用户点击提交（Submit）按钮之前，代码将不会运行。然后，你可以创建一个新的 `GoogleMapAPI` 对象并根据搜索字段检索坐标。坐标实际上是以值关联数组的形式返回的。这使得通过指定 'lat' 和 'lon' 的值可以轻松地创建 `$SearchLat` 和 `$SearchLon` 变量。不要忘记 URL 中可用的距离值。最后，该类还可以访问 API 结果以验证地址。如果地址无效，它将返回一个错误，你可以将其错误报告给用户。

```
if(isset($_GET['submit'])) {
    $map_object = new GoogleMapAPI();
    $geo_coords = $map_object->getGe($_GET['search']);
    if ($geo_coords["lat"] != false) {
        $SearchLat = $geo_coords["lat"];
        $SearchLon = $geo_coords["lon"];
        $Distance = $_GET['distance'];
    } else {
        echo 'Please enter a valid address or zip code.';
        exit;
    }
}
```

Array

(

[lon] => -106.374

[lat] => 39.6403

)

图 7-105 `$geo_coords` 数组 — lat 和 lon 值以值关联数组的形式返回。

现在我们有了 Lat、Lon 和 Distance 值，可以将这些值传递给数据库中的门店定位（Store Locator）脚本。我在调用 `PerformScriptCommand` 时使用变量，以便使代码更易读和易修改。修改用于数据库（Demo）的 `$Layout`、脚本名称 `$script`（Store Locator）以及脚本参数 `$script parameter`。如果你仔细查看我用于 SearchLat、SearchLon 和 Distance 的脚本参数，你会发现我正以一种类似 XML 的格式传递它们（例如：`<SearchLon>39.6403</SearchLon>`）。我更倾向于以这种格式传递变量，因为我在数据库中有一个自定义函数，可以通过指定字段名称来解析这些值，这非常有用。我将在下方的“门店定位”部分进行详细说明。不过，目前只是为了指出传递脚本参数的格式。执行代码后，它将运行脚本并将结果返回给用户。你所做的就是检查错误，最常见的错误是

```
$layout = 'Demo';
$script = 'Store Locator';
$parameter = "<SearchLat>$SearchLat</SearchLat><SearchLon>$SearchLon</SearchLon> <Distance>$Distance</Distance>";
$request = $fm->newPerformScriptCommand($layout, $script, $parameter);
$result = $request->execute();
if (File::iserror($result)) {
    echo 'There are no stores in your desired location.';
    exit;
}
```
