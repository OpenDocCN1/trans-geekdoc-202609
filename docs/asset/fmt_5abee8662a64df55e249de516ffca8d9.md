
```xml
<OurPrice>$39.99</OurPrice>
<UsedPrice>$15.00</UsedPrice>
</Details>
```

REST 客户端脚本的结果如图 41-1 所示。

![](img/70f9bfaf3d714f908e4cb0592b8eb9a6_809_0.png)

**图 41-1：** REST 客户端获取 XML 并输出 HTML。

从 XML 示例可以看出，Web 服务提供了许多我们没有使用的潜在数据——建议价格、发布日期等。这演示了使用 DOM XML 从馈中提取你需要的数据是多么简单。根据目前的 Amazon Web 服务的规则，你可以每秒轮询一次 Web 服务以获取新的 XML，从而保持这部分信息非常新鲜。

# 项目：一个 SOAP 服务器和客户端

这里我们有一个简单的 SOAP 服务和一个对应的客户端脚本。

XML-RPC 和 SOAP 服务有两个主要部分：实际编程逻辑以及将程序暴露或转换为 Web 服务的机制。后者是...

我们的客户端脚本（列表 41-5）可以在浏览器或命令行中运行，它请求食谱——食谱恰好是 XML 本身（列表 41-5），但在传输过程中它被视为封装在 SOAP XML 中的编码字符串。`NuSOAP` 会剥离所有的 SOAP 封包，并将负载作为 PHP 字符串交付以便进一步处理。我们希望在浏览器中显示食谱之外再做一些事情，因此我们使用 PHP 的解析器将配料写入文本文件作为购物清单，并可选地通过电子邮件发送食谱。

## 列表 41-5：一个 SOAP 客户端

```php
<?php
require_once('nusoap.php');

$recipe_name = $_GET['recipe'];

if ($recipe_name == '') {
    echo "You must supply a recipe name";
    exit;
}

$parameters = array('recipe'=>$recipe_name);

$soapclient = new soapclient('http://localhost/soap_recipe_server.php');
$result = $soapclient->call('getRecipe', $parameters);
// echo $result;

// Fire up the SAX parser to make a shopping list
// ------------------------------------------------------
$ingred_arr = array('types' => array(), 'values' => array());
$i = 0;
$e = -1;

// There is an element without a value, the recipe element
// so I'm jiggering this offset to match
function startElement($parser, $name, $attrs) {
    global $ingred_arr, $e;
    if ($name != 'INGREDIENT' && $name != 'RECIPE_NAME' && $e > 0) {
        $ingred_arr[$types][$e] = 1;
        $e++;
    }
}

function endElement($parser, $name) {
    // Just need to define an endElement function for the parser
}

function characterData($parser, $value)
{
    global $ingred_arr, $i;
    if (strlen($value) > 1) {
        $ingred_arr['values'][$i] = $value;
        $i++;
    }
}

// Run through the XML and stick the values in an array
// Also note if any of the elements are not recipe names
// ingredient
$simpleparser = xml_parser_create();
xml_set_element_handler($simpleparser, "startElement", "endElement");
xml_set_character_data_handler($simpleparser, "characterData");

if (!xml_parse($simpleparser, $result, strlen($result))) {
    die(xml_error(xml_get_code($simpleparser)));
}

xml_parser_free($simpleparser);

// Get rid of any values that aren't ingredients or recipe name
foreach ($ingred_arr['values'] as $key=>$val) {
    if ($ingred_arr['types'][$key] == 1) {
        $ingred_arr['values'] = array_slice($ingred_arr['values'], 0, $key);
    }
}

$shopping_list = implode("\n", $ingred_arr['values']);

// Write it out to a file
$file = "/home/me/shoppinglist.txt";
$fp = fopen($file, "a+");
$write_Int = fwrite($fp, $shopping_list);
fclose($fp);

// If you want, mail it to yourself
mail('me@example.com', 'Shopping list', $shopping_list);
```

要使用此脚本，请将食谱名称作为 GET 变量调用它：`soap_recipe_client.php?recipe=map_tofu`

你可能需要更改你的 Web 服务器或第 11 行。

你可能已经注意到，在本节之前，REST 示例和 SOAP 示例非常相似：它们都返回 XML 块。对于 PHP 这样的松类型语言，它们之间的主要区别在于 XML 是否在传输过程中被封装。在 REST 示例中，我们使用 DOM 进行管理；在本节中，我们通过 SAX 解析器运行。这展示了关于 Web 服务的两个基本点：对于简单的数据交换，REST 和 SOAP 功能上是对等同，且 XML 提供了许多方式的构建块。

# 总结

Web 服务是一个新兴领域。Web 服务在数据传输方面提供了即时回报，特别是对于应用程序，并最终释放了分布式计算的承诺。关于这些技术的炒作和误导信息，很多都发生在内网中。Web 服务标准现在是轻量级且易于使用的，而 SOAP 仍然是极其复杂的，但像 Microsoft 和 IBM 这样的大型供应商提供了支持。PHP 可用于创建服务器和客户端，在 REST、XML-RPC 和 SOAP 中。

# 第42章 图形

在本章中，我们将深入如何使用 PHP 创建图形。使用 `gd` 库可以帮助你创建 PNG 和 JPEG 图像。

在进入可视化之前，我们需要一些数据。[你知道如何在 HTML 中创建图形](https://example.com/img/70f9af3d71f90e4cb0f9a6_815_0.png)存储在 MySQL 数据库中，定义如下：

```sql
CREATE TABLE programmers (
  id int(11) NOT NULL auto_increment,
  name char(11) NOT NULL,
  age int(11) NOT NULL,
  language varchar(30) NOT NULL,
  os varchar(30) NOT NULL,
  country varchar(30) NOT NULL,
  PRIMARY KEY (id)
);
```

## 列表 42-1 示例数据集

| id | age | language | os | continent |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 33 | PHP | Linux | North America |
| 2 | 41 | Java | Solaris | North America |
| 3 | 41 | C++ | Solaris | North America |
| 5 | 45 | Lisp | MacOS | North America |
| 6 | 25 | C | Solaris | Antarctica |
| 7 | 17 | PHP | Linux | Denmark |
| 8 | 21 | Perl | Linux | Europe |
| 9 | 14 | PHP | Linux | Europe |
| 11 | 38 | PHP | Linux | Germany |
| 12 | 26 | C++ | Windows | North America |
| 13 | 22 | PHP | Windows | France | Europe |
| 14 | 37 | PHP | Linux | Japan | Asia |
| 15 | 38 | C | Solaris | South Korea | Asia |
| 16 | 19 | PHP | Linux | Canada | North America |
| 18 | 32 | Java | Solaris | Mexico | France |
| 19 | 23 | PHP | Solaris | Brazil | South America |
| 20 | 19 | PHP | Linux | Finland | Europe |
| 21 | 32 | PHP | Solaris | Brazil | South America |
| 22 | 51 | Java | Linux | | Europe |
| 23 | 29 | Java | | Japan | Asia |
| 24 | 29 | Java | Solaris | China | Asia |
| 25 | 21 | C++ | MacOS | | Germany |
| 26 | 21 | Perl | Solaris | France | Europe |
| 27 | 27 | PHP | Linux | India | Asia |
| 28 | 31 | Perl | Linux | Pakistan | Asia |
| 30 | 45 | C | Windows | USA | North America |

## 选项

为了看到图形创建如何融入 Web 世界，请查看以下选择：

- 你可以没有任何图形，只有纯文本信息。
- 你可以在 HTML 中嵌入静态图像，无论是你自己创建的还是其他人创建的。
- 你可以编写实际上动态生成的 HTML。
- 你可以在 HTML 页面中嵌入静态图形（甚至是图像动画，如果你坚持的话）。
- 你可以使用 `gd` 生成所有可能从你的代码产生的静态图形，将其存储在文件中并条件显示。
- 你可以根据需要创建图形图像，将其存储在文件中并条件显示。

我们在本示例中使用这些数据，但在第 48 章中一个更详细的示例中再次回到这里。

假设我们的目标是让不同列值的分布计数可视化——我们不仅想知道有多少受访者列出了某个项或编程语言，还想通过图表进行比较。

尽管我们的数据是一个 MySQL 数据库，但这段代码的显示部分并不一定与之绑定。我们可能希望将其用于完全不同的用途。我们分离出一个独立的函数，该函数根据特定格式的数组生成条形图，稍后再将其连接到通过 SQL 查询生成所需数组的代码中。将数组转换为条形图的代码在列表 42-2 中。

## 列表 42-2：`bar_graph.php`

```php
<?php
function array_to_bar_graph($array, $max_width) {
    // 期望输入数组，其中键为
    // 字符串标签，值为
    // 数字。值必须是非负数
    // 返回一个 HTML 条形图作为字符串
    // 对应 arms[1-5].gif，位于 images/ 目录下
    foreach($array as $value) {
        if ((isset($max_value) && ($value > $max_value))) {
            $max_value = $value;
        }
    }
    $pixels_per_value = ((double) $max_width / $max_value);
    $string_to_return = "<TABLE cellpadding='5'>";
    $counter = 0;
    foreach ($array as $name => $value) {
        $bar_width = $value * $pixels_per_value;
        $image_no = ($counter % 5) + 1;
        $string_to_return .= "<TR><TD>$name $value</TD><TD><IMG SRC='images/bar$image_no.gif' WIDTH=$bar_width HEIGHT=10>";
        $counter++;
    }
    $string_to_return .= "</TABLE>";
    return($string_to_return);
}
?>
```

条形图代码极其简单——它遍历一个数组，假设该数组键为名称，值为数量。它将最大值归一化为固定宽的条，并按比例计算所有其他条的宽度。最后，它使用 `<img>` 标签中的缩放参数显示条，以给每个变量提供适当宽度。它循环遍历图像列表，这些图像是原色的 GIF（可以使用你最喜欢的图形程序创建）。由于这些图像是单色的，它们的大小和形状与无关紧要。（如果你手头没有现成的图像，可以在此处的代码下载找到：`www.testworks.com/phpbook/`）

现在我们可以在条形图中显示名称和关联值，并通过 Web post 和 SQL 查询连接到数据库。这部分代码在列表 42-3 中。

## 列表 42-3：`bar_graph.form.php`

```php
<?php
include_once("dbconnect.php");
include_once("bar_graph.php");

if (isset($_POST['COLUMN_NAME'])) {
    $column_name = $_POST['COLUMN_NAME'];
    $query = "select $column_name, count(*) group by $column_name";
    $result = mysql_query($query) or die("error in database interaction<BR>".mysql_error());
    $array_collection = array();
    while ($row = mysql_fetch_row($result)) {
        $count = $row[0];
        $array_collection[$name] = $count;
    }
    $bar_graph = array_to_bar_graph($array_collection, 300);
} else {
    $bar_graph = "";
}

$self = $_SERVER['PHP_SELF'];

$form = <<EOT
<form METHOD="POST" ACTION="$self"?>
<h3>Choose a table for graphing/</h3>
<SELECT NAME="COLUMN_NAME">
<option VALUE="os">os</option>
<option VALUE="language">language</option>
<option VALUE="continent">continent</option>
<option VALUE="sex">sex</option>
</SELECT>
<INPUT TYPE=SUBMIT NAME=SUBMIT>
</form>
EOT;

$page = <<EOT
<HTML><HEAD><TITLE>Survey data</TITLE></HEAD>
<BODY>
$form
<BR>
$bar_graph
</BODY></HTML>
EOT;

echo $page;
?>
