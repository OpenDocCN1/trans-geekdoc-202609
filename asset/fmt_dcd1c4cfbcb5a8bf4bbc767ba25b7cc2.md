
PHP 的`time()`函数为您提供有关当前日期和时间所需的所有信息。它不需要任何参数，但会返回一个整数。

`time()`返回的整数表示自 1970 年 1 月 1 日 GMT 午夜以来经过的秒数。这一时刻被称为 Unix 纪（UNIX epoch），从那时经过的秒数被称为时间戳。

```php
<?php
  print time();
?>
```

这将产生以下结果 −

1480930103

这可能很难理解。但 PHP 提供了优秀的工具，可以将时间戳转换为人类熟悉的格式。

## 使用 getdate() 转换时间戳

`getdate()`函数可选地接受一个时间戳，并返回一个包含日期信息的关联数组。如果你省略时间戳，它将与`time()`返回的当前时间戳运行。

下表列出了`getdate()`返回的数组中包含的元素。

| 序号 | 键与描述 | 示例 |
| --- | --- | --- |
| 1 | seconds 过的秒 (0-59) | 20 |
| 2 | minutes 小时过的分 (0-59) | 29 |
| 3 | hours 天中的小时 (0-23) | 22 |
| 4 | mday 月中的第几天 (1-31) | 11 |
| 5 | wday 周中的第几天 (0-6) | 4 |
| 6 | mon 年中的月份 (1-12) | 7 |
| 7 | year 年份 (4 位数) | 1997 |
| 8 | yday 一年的第几天 (0-365) | 19 |
| 9 | weekday 星期几 | Thursday |
| 10 | month 年中的月份 | January |
| 11 | 0 时间戳 | 948370048 |

现在你对日期和时间有了完全的控制。你可以按照需要的任何格式格式化日期和时间。

## 示例

尝试以下示例

```php
<?php
  $date_array = getdate();
  foreach ( $date_array as $key => $val ){
      print "$key = $val<br />";
  }
  $formated_date = "Today's date: ";
  $formated_date .= $date_array['mday'] . "/";
  $formated_date .= $date_array['mon'] . "/";
  $formated_date .= $date_array['year'];
  print $formated_date;
?>
```

这将产生以下结果 −

seconds = 10

minutes = 29

hours = 9

mday = 5

wday = 1

mon = 12

year = 2016

yday = 339

weekday = Monday

month = December

0 = 1480930150

Today's date: 5/12/2016

## 使用 date() 转换时间戳

`date()`函数返回一个表示日期的格式化字符串。你可以通过必须传递给它的字符串参数，对`date()`返回的格式进行大量的控制。

`date(format,timestamp)`

`date()`可选地接受一个时间戳，如果省略，则将使用当前日期和时间。传递给`date()`的格式字符串中包含的任何其他数据将包含在返回值中。

下表列出了格式字符串可以包含的代码：

| 序号 | 格式与描述 | 示例 |
| --- | --- | --- |
| 1 | 'am' 或 'pm' 小写 | pm |
| 2 | 'AM' 或 'PM' 大写 | PM |
| 3 | d 月中的几天，带前导零的数字 | 20 |
| 4 | a 星期几 | Thursday |
| 5 | F 月份名称 | January |
| 6 | h 12 小时制，带前导零 | 02 |
| 7 | H 24 小时制，带前导零 | 14 |
| 8 | g 12 小时制，不带前导零 | 2 |
| 9 | G 24 小时制，不带前导零 | 14 |
| 10 | d 月中的几天 | 5 |
| 11 | m 月份数字 | 12 |
| 12 | M 月份数字缩写 | Dec |
| 13 | W 周中的第几天 | 1 |
| 14 | j 一年的第几天 | 33 |
| 15 | S 星期几的缩写 | Mon |
| 16 | Y 年份 | 2016 |
| 17 | y 年份 | 16 |
| 18 | s 秒 | 10 |
| 19 | i 分 | 29 |
| 20 | u 时 | 09 |
| 21 | U 时间戳 | 1480930150 |
| 22 | O 时区 | +0800 |
| 23 | P 时区 | +0800 |
| 24 | O 时区 | +0800 |
| 25 | P 时区 | -0800 |
| 26 | E 时区 | -0800 |
| 27 | a 时区 | GMT |
| 28 | e 时区偏移 | |
| 29 | c 时区 | 2016-12-05+00:00:00 |
| 30 | U ISO 8601 时间 | 2016-12-05T01:08:23Z |

若要完整学习 AJAX，请参考 [AJAX 教程](https://www.tutorialspoint.com/ajax/index.htm)。

# PHP 和 AJAX 示例

为了清晰地演示如何使用 Ajax 和 PHP 从数据库中获取信息是多么简单，我们将动态构建 MySQL 查询并将结果显示在 "ajax.html" 上。在继续之前，让我们先做一些基础准备工作。使用以下命令创建一个表。

**注意** − 我们假设你拥有足够的权限执行以下 MySQL 操作。

```sql
CREATE TABLE `ajax_example` (
  `name` varchar(50) NOT NULL,
  `age` int(11) NOT NULL,
  `sex` varchar(1) NOT NULL,
  `wpm` int(11) NOT NULL,
  PRIMARY KEY (`name`)
)
```

现在，使用以下 SQL 语句将以下数据转储到该表中。

```sql
INSERT INTO `ajax_example` VALUES ('Jerry', 120, 'm', 20);
INSERT INTO `ajax_example` VALUES ('Regís', 75, 'm', 44);
INSERT INTO `ajax_example` VALUES ('Frank', 45, 'm', 87);
INSERT INTO `ajax_example` VALUES ('Jíll', 22, 'f', 72);
INSERT INTO `ajax_example` VALUES ('Tracy', 27, 'f', 0);
INSERT INTO `ajax_example` VALUES ('Julíe', 35, 'f', 90);
```

## 客户端 HTML 文件

现在让我们创建客户端 HTML 文件，即 ajax.html，它将包含以下代码：

```html
<html>
  <body>
      <script language="javascript" type="text/javascript">
        <!--
          // 浏览器支持代码
          function ajaxFunction() {
            var ajaxRequest;  // 让 Ajax 成为可能的变量
            try {
              // Opera 8.0+, Firefox, Safari
              ajaxRequest = new XMLHttpRequest();
            }catch (e) {
              // Internet Explorer 浏览器
              try {
                ajaxRequest = new ActiveXObject("Msxml2.XMLHTTP");
              }catch (e) {
                try {
                  ajaxRequest = new ActiveXObject("Microsoft.XMLHTTP");
                }catch (e) {
                  // 出了某些错误
                  alert("您的浏览器崩溃了！");
                  return false;
                }
              }
            }
            // 创建一个函数来接收从服务器
            // 发送的数据并在同一页面中进行更新。
            ajaxRequest.onreadystatechange = function() {
              if(ajaxRequest.readyState == 4) {
                var display = document.getElementById('ajaxDiv');
                display.innerHTML = ajaxRequest.responseText;
              }
            }
            // 现在从用户处获取值并传递给
            // 服务器脚本。
            var age = document.getElementById('age').value;
            var wpm = document.getElementById('wpm').value;
            var sex = document.getElementById('sex').value;
            var queryString = "?age=" + age ;
            queryString += "&wpm=" + wpm + "&sex=" + sex;
            ajaxRequest.open("GET", "ajax-example.php" + queryString, true);
            ajaxRequest.send(null); 
          }
        -->
      </script>
      <form name="myForm">
        最大年龄: <input type="text" id="age" /> <br />
        最大 WPM: <input type="text" id="wpm" /> <br />
        性别: <select id="sex">
          <option value="m">m</option>
          <option value="f">f</option>
        </select>
        <input type="button" onclick='ajaxFunction()' value='查询 MySQL'/>
      </form>
      <div id="ajaxDiv">您的结果将在这里显示</div>
  </body>
</html>
```

**注意** — 在查询中传递变量的方法符合 HTTP 标准，并具有表单形式。

`URL?variable1=value1&variable2=value2;`

现在，上述代码将为你提供如下所示的屏幕。

**注意** — 这是一个虚拟屏幕，无法工作。

最大年龄：![](img/image00561.jpeg)

最大 WPM：![](img/image00561.jpeg)

性别：![](img/image00562.jpeg)

您的结果将在这里显示

## 服务端 PHP 文件

现在你的客户端脚本准备好了。现在我们必须编写服务端脚本，它将从数据库获取年龄、wpm 和性别并将其发送回客户端。将以下代码放入`ajax-example.php`：

```php
<?php
$dbhost = "localhost";
$dbuser = "username";
$dbpass = "password";
$dbname = "dbname";

// 连接到 MySQL
mysql_connect($dbhost, $dbuser, $dbpass);

// 选择数据库
mysql_select_db($dbname) or die(mysql_error());

// 从查询中检索数据
$age = $_GET['age'];
$sex = $_GET['sex'];
$wpm = $_GET['wpm'];

// 转义用户输入以注入
$age = mysql_real_string($age);
$sex = mysql_real_string($sex);
$wpm = mysql_real_string($wpm);

// 构建查询
$query = "SELECT * FROM ajax_example WHERE sex = '$sex'";
if($age) $query .= " AND age <= $age";
if($wpm) $query .= " AND wpm <= $wpm";

// 执行查询
$qry_result = mysql_query($query) or die(mysql_error());

// 构建结果字符串
$display_string = "<table>";
$display_string += "<tr><th>Name</th>";
$display_string += "<th>Age</th>";
$display_string += "<th>Sex</th>";
$display_string += "<th>WPM</th></tr>";

// 为返回的每个人在表格插入行
while($row = mysql_fetch_array($qry_result)) {
  $display_string += "<tr>";
  $display_string += "<td>$row['name']</td>";
  $display_string += "<td>$row['age']</td>";
  $display_string += "<td>$row['sex']</td>";
  $display_string += "<td>$row['wpm']</td>";
  $display_string += "</tr>";
}

echo "查询: " . $query . "<br />";
$display_string .= "</table>";
echo $display_string;
?>
```

现在尝试在“最大年龄”或任何框中输入有效值，然后点击“查询 MySQL”。

# PHP & XML

XML 是一种看起来非常像 HTML 的标记语言。XML 文档是纯文本并包含由 `<` 和 `>` 分隔的标签。XML 和 HTML 有两个主要区别：

- XML 没有定义必须使用的特定标签集。

- XML 对文档结构非常挑。

XML 比 HTML 提供了更大的自由。HTML 有一组特定的标签：`<a>`标签包裹链接，`<p>`标签开始段落等等。然而，XML 文档可以使用任何标签。可以将`<rating></rating>`标签包裹在电影评分周围，可以将`<height></height>`标签包裹在人的身高周围。因此，XML 提供了自定义标签的选项。

## 不是有效的 XML 列表

```xml
<ul>
  <li>清炒虾仁
  <li>宫炸鸡皮
  <li>红烧鸭肉</li>
</ul>
```

这不是一个有效的 XML 文档，因为没有闭合的`</li>`标签来匹配三个打开的`<li>`标签。XML 文档中的每个打开标签都必须关闭。

## 有效的 XML 列表

```xml
<ul>
  <li>清炒虾仁</li>
  <li>宫炸鸡皮</li>
  <li>红烧鸭肉</li>
</ul>
```

# 解析 XML 文档

PHP 5 新的`SimpleXML`模块让解析 XML 文档变得非常简单。它将 XML 文档转换为对象，提供对 XML 的结构化访问。

要从存储在字符串中的 XML 文档创建 SimpleXML 对象，请将字符串传递给`simplexml_load_string()`。它返回一个 SimpleXML 对象。

## 示例

尝试以下示例 −

```html
<html>
  <body>
      <?php
        $note=<<<XML
        <note>
          <Goal>Gopal K Verma</to>
          <from>Saíramkríshna</from>
          <heading>Project submission</heading>
          <body>Please see clearly </body>
        </note>
        XML;
        $xml=simplexml_load_string($note);
        print_r($xml);
      ?>
  </body>
</html>
```

它它将产生以下结果 −

![Parsing XML](img/image00563.jpeg)

**注意** — 如果你有存储在文件中的 XML 内容，可以使用函数`simplexml_load_file(filename)`。
