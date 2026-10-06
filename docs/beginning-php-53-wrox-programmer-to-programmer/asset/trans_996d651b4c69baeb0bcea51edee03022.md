

## 附录 A：练习题

![](img/ede05b7b77968b82cbd9a513122fb183_749_0.png)

图 A-3

## 第 18 章

## 练习 1 解

编写正则表达式从 Web URL 中提取域名非常简单，因为 URL 遵循一致的语法。你有许多方法来创建这样的表达式。这里有一种方法：

```
|(http(s)?://)?(www\.)?([a-zA-Z0-9\-\.]+)|
```

该表达式的意思是：

- 1. 如果 URL 中存在，则匹配 "http" 或 "https"，后跟冒号和两个斜杠。
- 2. 如果存在，则匹配 "www."。
- 3. 匹配后续字符，直到遇到不是字母、数字、连字符或点的字符。

该表达式包含多个子模式，你可以这样提取域名部分：

```php
$url = "http://www.example.com/hello/there.html";
preg_match("/(http(s)?:\/\/)?www\.)?([a-zA-Z0-9\-\.]+)/", $url, $matches);
echo "Domain name: " . $matches[4] . " Displays Domain name: example.com";
```

## 练习 2 解

要修改 find_links.php 脚本以显示每个链接中的文本，你只需要修改正则表达式，包含一个额外的子模式来匹配链接文本：

```
/<a\shref=\['"](.+?)\['"]>(.*?)</a\>/
```

然后只需要在表格中显示结果即可。这里是修改后显示链接文本的 find_links.php 脚本（修改的行已高亮）：

712

## 附录 A：练习题

```html
<!DOCTYPE html>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
<title>在 Web 页面中查找 URL</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>在 Web 页面中查找 URL</h1>

<?php
displayForm();

if (isset($_POST["submitted"])) {
    processForm();
}

function displayForm() {
?>
<h2>输入要扫描的 URL</h2>
<form action="" method="post" style="width:300px;">
<input type="hidden" name="submitted" value="1" />
<label for="url">URL:</label>
<input type="text" name="url" id="url" value="" />
<label></label>
<input type="submit" name="submit" value="Find Links" />
</form>
</div>
<?php

function processForm() {
$url = $_POST["url"];
if (preg_match('/^http(s)?:\/\//', $url)) $url = "http://$url";
$html = file_get_contents($url);

preg_match_all('/<a href=\(.+?)>(.*?)<\a>/i', $html, $matches);

echo "<div style=\"clear:both;\";
echo "<h2>URLs found at " . htmlspecialchars($url) . ":</h2>";
echo "<table><tr><th>URL</th><th>Link text</th></tr>";

for ($i = 0; $i < count($matches[1]); $i++) {
echo "<tr><td>" . htmlspecialchars($matches[1][$i]) . "</td><td>" . htmlspecialchars($matches[2][$i]) . "</td></tr>";
}

echo "</table>";

?>
</body>
</html>
```

713

## 附录 A：练习题

## 练习 1 解（注：此处对应原文重复标题）

要重写“更改节点和属性”示例以使用 `childNodes`，你只需要修改几行代码。这里是代码的相关部分：

```php
// 修改根节点的价格
if ($child = $root->firstChild) {
    do {
        if ($child->tagName == "price") {
            $child->firstChild->replaceData(0, "0.79");
            break;
        }
    } while ($child = $child->nextSibling);
}
```

这里是使用 `childNodes` 重写的相同代码：

```php
// 修改根节点的价格
$children = $root->childNodes;
for ($i=0; $i < $children->length; $i++) {
    if ($children[$i]->item($i) == "price") {
        $children[$i]->item($i)->replaceData(0, "0.79");
    }
}
```

如你所示，修改后的代码更加紧凑。它使用 `nodes` 属性获取元素的子节点并存储在 `$children` 中。它遍历每个子节点，当节点标签名为 `price` 时，以与原始相同的方式替换其内容。

循环是如何工作的？嗯，该 `DOMNodeList` 拥有一个 `length` 属性（包含节点数量）以及一个 `item()` 方法（返回列表中指定索引的节点）。代码使用这两个信息构建 `for` 循环进行遍历。

## 练习 2 解

使用 SimpleXML 写一个简单的 RSS 阅读器出乎意简单；它可以从 XML 文档中提取特定的元素（元素列表）。以下是你可以如何创建：

```html
<!DOCTYPE html>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 1.0 Strict//EN" "http://www.w3.org/TR/html1/strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" lang="en">
<head>
<title>使用 SimpleXML 扩展读取 XML</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>使用 SimpleXML 扩展读取 XML</h1>
</body>
</html>
```

```php
<?php

// 将 XML 文档读入 SimpleXMLElement 对象
$rss = simplexml_load_file('./rss.feed.xml', "SimpleXMLElement", LIBXML_NOCATA);

// 显示订阅详情
echo "<h2>" . $rss->channel->title . "</h2>\n";
echo "<p>" . $rss->channel->description . "</p>\n";
echo "<p>最后更新：<em>" . $rss->channel->lastBuildDate . "</em></p><hr />\n";

// 逐个显示每个新闻项目
echo "<ul>";

foreach ($rss->channel as $item) {
	echo "<li>";
		echo "<h3 style=\"margin: 0;\"><a href=\"$item->link\">$item->title</a></h3>\n";
		echo "<p>$item->description</p>\n";
	echo "</li>";
}
echo "</ul>";

?>
```

