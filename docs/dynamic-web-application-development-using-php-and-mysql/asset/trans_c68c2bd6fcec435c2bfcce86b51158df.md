
上述示例的输出如 图 18.3 所示。

## 18.5 一个动态直方图

假设你可能希望创建一个网站，该网站显示一个图表，几乎实时显示有关你网站的一些数据。这些数据可能是注册用户或在线用户的数量，或者例如过去一分钟内处理的交易或销售额。你可能还希望将此信息显示为直方图或条形图，并且通过使用 Ajax，你可以最大程度地减少不断更新此图表对网站用户的影响。

## 图 18.3 放大缩略图

![](img/b2471264f405d17994ef173e4b9cec92_558_0.png)

当网页加载时，'onload' 事件会调用函数 startJS()：

```
<body onload="startJS();">
```

接下来创建一个名为 "graph" 的 division，直方图将在其中显示：

```
<h2>Graph:</h2>
<div id="graph">
</div>
```

函数 startJS() 和 changePage() 在文件 'example18-4.js' 中定义：

```
function startJS() {
    xhrequest = null;
    try {
        xhrequest = getXMLHttpRequest();
    }
    catch(error) {
        document.write("Cannot run Ajax code using this browser");
    }

    if(xhrequest != null) {
        var objDate = new Date();
        var intSecs = objDate.getTime();

        var strUrl = "example18-4.php?intSecs=" + intSecs;
        xhrequest.onreadystatechange = changePage;
        xhrequest.open("GET", strUrl, true);
        xhrequest.send(null);
        setTimeout("startJS()", 500);
    }
}

function changePage() {
    if (xhrequest.readyState == 4 && xhrequest.status == 200) {
        var strResponse = xhrequest.responseText;
        document.getElementById("graph").innerHTML = strResponse;
    }
}
```

函数 startJS() 首先检查创建 xmlhttprequest 对象是否存在任何问题：

```
function startJS(intPicture) {
    xhrequest = null;
    try {
        xhrequest = getXMLHttpRequest();
    }
    catch(error) {
        document.write("Cannot run Ajax code using this browser");
    }
}
```

创建一个日期对象并使用 getTime( ) 方法返回自 1/1/1970 以来的秒数：

```javascript
if (xhrequest != null) {
    var objDate = new Date();
    var intSecs = objDate.getTime();
}
```

我们将使用获得的值来解决某些浏览器的缓存问题。某些浏览器如果认为它们在本地缓存中存储了一个完全良好的网页，就不会重新加载网页。这给我们带来了一个问题，因为我们希望图表脚本每隔几秒自动重新加载并重新显示图表。然而，这在某些浏览器中不起作用，因为它们只是重新显示旧的缓存页面，因此无法获取和显示任何新的图表条。我们可以通过使用秒数来解决这个问题，因为它一直在增长并且不断变化。如果我们将此值附加到脚本调用中，它会欺骗浏览器使其认为我们正在调用不同的脚本，从而不使用存储在缓存中的脚本。

如果没有问题，脚本将打开与 PHP 脚本的连接，并传递之前获得的秒数值。函数 changePage( ) 被定义为处理从 PHP 脚本产生的输出。

```javascript
var strUrl = "example18-4.php?intSecs=" + intSecs;
xhrequest.onreadystatechange = changePage;
xhrequest.open("GET", strUrl, true);
xhrequest.send(null);
```

与我们之前示例中的 startJS( ) 函数的另一个不同之处是包含了一个 setTimeout( ) 函数调用，该调用被定义为在 500 毫秒后调用 startJS( ) 函数：

```javascript
setTimeout("startJS()", 500);
```

函数 changePage( ) 从 PHP 脚本获取数据输出并将其存储在变量 strResponse 中。此数据，即定义直方图的整个 (X)HTML，然后使用 innerHTML 方法注入到 ‘graph’ 元素中：

```javascript
function changePage() {
    if (xhrequest.readyState == 4 && xhrequest.status == 200) {
        var strResponse = xhrequest.responseText;
        document.getElementById("graph").innerHTML = strResponse;
    }
}
```

以下 PHP 脚本生成直方图图表，其复杂程度比我们之前的示例稍高：

```php
<?php
// File: example18-4.php

$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error());

mysql_select_db("graph", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );

srand( (double) microtime() * 1000000);
$intPercentage = rand(0,99);

$dbWriteRecords = mysql_query("INSERT INTO percentageValues VALUES ('', '$intPercentage')", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );

$dbRecords = mysql_query("SELECT * FROM percentageValues", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );
$intCount = mysql_num_rows($dbRecords);
if ($intCount > 20) {
    $intStart = $intCount - 20;
    $dbRecords = mysql_query("SELECT * FROM percentageValues LIMIT $intStart,20", $dbLocalhost)
        or die("Problem reading table: " . mysql_error() );
}

$arrPercent = array (0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0);
$intSize = count($arrPercent);
$intCount = 0;

while ( ($arrRecords = mysql_fetch_array($dbRecords) ) ) {
    $arrPercent[$intCount++] = $arrRecords["Percentage"];
}
graph($arrPercent, $intSize);

function graph($arrData, $intSize) {
    $intBarWidth = 10;
    $intBarSpacing = 10;
    $intMultiplier = 1.5;

    $intSize=count($arrData);
    echo "<div id='graphScale'><img src='graphics/scale.gif' width='27' height='150' /></div>";
    echo "<div id='graphBars'>";
    echo "<img src='graphics/hiddenbar.gif' width='0' height=' " . 99 * $intMultiplier . "'>";
    for($intCount=0;$intCount<$intSize;$intCount++) {
        echo "<img src='graphics/redbar.gif' width='$intBarWidth' height=' " . $arrData[$intCount] * $intMultiplier . "'>";
    }
    echo "</div>";
}
?>
```

脚本首先建立与数据库 ‘graph’ 的连接：

```
$dbLocalhost = mysql_connect("localhost", "root", "")
    or die("Could not connect: " . mysql_error() );

mysql_select_db("graph", $dbLocalhost)
    or die("Could not find database: " . mysql_error() );
```

图表数据库有一个名为 percentageValues 的单个表，它仅由两个整数字段组成：Id 和 Percentage。表的內容由 PHP 脚本生成。脚本的下一部分生成 0 到 99 之间的随机数并将其存储在图表数据库中：

```
srand( (double) microtime() * 1000000);
$intPercentage = rand(0,99);

$dbWriteRecords = mysql_query("INSERT INTO percentageValues VALUES
('', '$intPercentage')", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );
```

接下来，读取数据库的内容并将数据库中的记录数存储在 $intCount 中：

```
$dbRecords = mysql_query("SELECT * FROM percentageValues", $dbLocalhost)
    or die("Problem reading table: " . mysql_error() );
$intCount = mysql_num_rows($dbRecords);
```

如果数据库中的记录数大于 20，则读取最后 20 条记录：

```
if ($intCount > 20) {
    $intStart = $intCount - 20;
    $dbRecords = mysql_query("SELECT * FROM percentageValues LIMIT $intStart,20",
        $dbLocalhost)
        or die("Problem reading table: " . mysql_error() );
}
```

定义一个数组，并将所选数据库记录的百分比值存储在该数组中：

```
$arrPercent = array (0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0);
$intSize = count($arrPercent);
$intCount = 0;

while ($arrRecords = mysql_fetch_array($dbRecords) ) {
    $arrPercent[$intCount++] = $arrRecords["Percentage"];
}
```

最后，调用函数 graph()，并向其传递数组内容和数组大小：

```
graph($arrPercent, $intSize);
```

函数 graph() 首先指定直方图条的宽度、它们之间的间距以及影响条高度的乘数：

```
function graph($arrData, $intSize) {
    $intBarWidth = 10;
    $intBarSpacing = 10;
    $intMultiplier = 1.5;
```
