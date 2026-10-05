

```php
$fm->setProperty('password', '12346');
```

你还需要包含两个所需的类文件。我已在下载文件中为你包含了它们。`GoogleMap.php` 包含了连接到 Google Map API 的所有代码。从技术上讲，你不需要对此文件进行任何操作。然而，如果你仔细阅读它，你会发现可以通过将值从 `false` 更改为 `true` 来配置 API 提供的任何可用功能。该文件中的大多数功能默认都是开启的。我可以很容易地说控制 Google Map API 的重要性。你会怎么做呢——是手动将值从 `false` 改为 `true`，还是处理 Google 的几百行代码？接下来是 `JSMin.php`，它包含了该类所有的 Google JavaScript 代码。再次，我向 Brad 致敬，因为他将所有代码都移植到了 PHP。你不需要任何 JavaScript，它就能运行！

```php
include_once("GoogleMap.php");
include_once("JSMin.php");
```

现在我们可以进入代码的核心部分，它将通过几行代码来驱动 Google Map API。在用户点击“更新”（Update）按钮之前，代码将不会运行。首先，在表中找到所有记录并存储在 `$records` 中。

```php
if(isset($_GET['Update'])) {
	$record = $fm->newFindAllCommand('Demo');
	$result = $record->execute();
	$records = $result->getRecords();
}
```

接下来，遍历所有记录以更新经纬度（lat/lon）值。创建新的 `GoogleMapAPI` 对象，并通过地址（Address）、城市（City）和州（State）检索坐标。坐标实际上是以关联数组的形式的。这使得代码更加简洁。我们通过指定 `$geo_coords` 为 `['lat']` 和 `['lon']` 来创建 `$lat` 和 `$lon` 变量。

```php
$map_object = new GoogleMapAPI();
foreach($records as $record) {
	$address = $record->getField('Address') . "," . $record->getField('City') .
	", " . $map_object->getField('State');
	$geo_coords = $map_object->getgeocode($address);
	$lat = $geo_coords['lat'];
	$lon = $geo_coords['lon'];
}
```

```php
Array (
	[lon] => -106.374
	[lat] => 39.6403
)
```

图 7-107：$geo_coords 数组 —— 纬度和经度值以关联数组的形式返回。

接下来，使用 `RecordID` 更新记录，以便为新的 `EditCommand` 识别每条记录。你们确实都需要更新带有经纬度值的记录。页面上看到的其余代码都是为了展示，除了可视化该过程之外完全没有必要。

```php
$edit = $fm->newEditCommand('Demo', $record->getField('RecordID'));
	$edit->addField('Lat', $lat);
	$edit->addField('Lon', $lon);
	$edit->execute();
}
```

最后，创建表单以便你可以点击“更新”（Update）按钮。这里没什么特别的，只需将表单指向同一个页面，因为 PHP 代码将在那里运行。

```html
<html>
<head>
</head>
<body>
<form action="<?php echo $_PHP_SELF;?>" method="get" id="Update">
点击按钮更新所有带有 Lat/Lon 值的记录。
<br>
<input name="Update" type="submit" value="Update">
</form>
</body>
</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_316_0.png)

图 7-108：使用 Google Map API 插入地理编码 —— 纬度和经度值。

# 第 39 节：Google Map API 地图标记

**目标：** 在本节中，你将学习如何集成 Google map API。本节与“店铺定位器”（Store Locator）课程相同，不同之处我们要为从数据库返回的每条记录显示 Google 地图和地图标记。

**难度：** 困难

**示例文件：**
- PHPFiles/Advanced/Lesson39/GoogleMap.php
- PHPFiles/Advanced/Lesson39/JSMin.php
- PHPFiles/Advanced/Lesson39/MapMarkers.php
- PHPFiles/Advanced/Lesson39/StoreLocator.fmp12

> 本节使用单独的数据库文件进行演示。请将 `StoreLocator.fmp12` 数据库文件上传到你的服务器。

**页面导航：**

![](img/5a2c5fda68d42e5d65f51850276e49ec_317_0.png)

**FileMaker API 方法：**
- newPerformScriptCommand()
- getRecords()
- getField()

**代码：**

数据库包含名称、地址、城市和州的字段。这些是显而易见的。`MarkerTitle` 和 `MarkerDescription` 字段分别用于在地图上的每个位置显示提示框或对话框。接下来是餐厅的纬度（Lat）和经度（Lon）。`SearchLat`、`SearchLon` 和 `Distance` 字段用于店铺定位器根据用户提供的值查找记录。距离计算使用大圆导航公式（即 Haversine 公式）来计算用户位置与每个商店之间的距离。关于该公式的更多信息可以在我们网站 www.formulationspro.com 的 FileMaker 部分找到我的文章《Map Distance》，或者访问：

```
http://en.wikipedia.org/wiki/Haversine_formula
```
或
```
http://www.best.vwh.net/avform.htm
```

# StoreLocator (FMS11v2 - 测试服务器)

# 使用 Google 地编码的 PHP 店铺定位器

说明

| Name | Value |
| :--- | :--- |
| Name | Aardwork Pizza & Sub |
| Address | 306A Caribou St |
| City | Banff |
| State | AB |
| Marker/Title | Aardwork Pizza & Sub |
| Marker/Description | Dine and Dish Magazine称为最好的披萨 |
| Lat | 51.766996 |
| Lon | -115.50362 |
| Search | |
| Search | |
| Distance | 621.8 |
| RecordID | 40 |

图 7-109：使用示例数据

距离计算涉及三角函数。距离以英里计算。脚本使用 Google Map API 为提供的每个地址查找坐标。然后使用这些结果来更新数据库。随后会显示带有每个位置标记的地图。这允许用户在地图上查看餐厅的所在地。

