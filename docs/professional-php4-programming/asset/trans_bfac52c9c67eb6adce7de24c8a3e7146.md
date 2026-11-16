

XML 文档 travel.xml 的文档树如图所示：

![](img/9cf7789dba9b16ef3f8576d5aea89186_789_0.png)

## 使用 PHP 的 DOM 支持

DOM 不是标准 PHP 配置的一部分。要使用 DOM 函数，必须通过指定 --with-dom 参数来配置 PHP。在配置 PHP 之前，需要安装 libxml 库。对于 Linux 和 UNIX 服务器，可以从以下位置下载该库：
http://www.xmlsoft.org/。如果运行的是 Windows，则可使用可用的 Windows 移植版：
http://www.fh-frankfurt.de/~igor/projects/libxml/index.html。

在 Windows 和 Apache 上使 DOM 工作并非易事。如果在使 DOM 代码正常工作时遇到问题，以下是一些需要检查的事项：

- 打开 php.ini。我们要查找两项内容，extension_dir 和
- extension=php_domxml.dll。首先要查看的设置是 extension_dir。它定义
- 为 PHP 扩展（例如 DOM）提供功能的文件存储位置。
- 大约在文件中间位置，你应该会看到一个名为“Paths and Directories”的部分，以及
- extension_dir 指令。此处 extension_dir 的值为 "./"，这意味着
- 当前文件夹：

```ini
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
extension_dir = ./ ; directory in which the loadable extensions (modules)
reside
```

请记住 extension_dir 的设置。目录位于哪里其实不重要，但你应确保 php_domxml.dll 文件位于其中。

向下稍远处有一个名为“Windows Extensions”的部分。查找条目 extension=php_domxml.dll。确保其前面没有分号 (;)。如果有，删除分号，然后保存并退出 php.ini 文件。

- 确保 libxml.dll 和 iconv.dll 位于 C:\WINNT\System32\ 目录中。

PHP 的 DOM XML 函数仍处于实验阶段（截至 PHP 4.0.6）。当 DOM 成熟后，PHP 中 DOM 的实际用法可能会发生变化。

## DOM 示例代码

DOM API 可实现 XML 的非常简便的读取和写入。我们将使用 DOM 创建一个 XML 文件，解析同一文件，将其转换为 HTML，并将其显示为表格。

## 使用 DOM 编写 XML

我们要做的第一件事是创建新的 DOM 对象。括号中的字符串将成为生成的 XML 文件中 XML 声明的版本号：

```php
<?php
$doc = new_xmldoc("1.0");
```

然后我们需要定义根节点：

```php
$root = $doc->add_root("Recordset");
```

现在，让我们通过使用 new_child() 为树添加分支。该函数有两个参数，第一个参数作为节点名称，第二个参数作为节点值。在此示例中，我们希望 Recordset 下的子节点为 Travelpackage，且它没有任何内容，因此我们将字符串留空。如果标签没有任何数据，我们必须包含空字符串。如果字符串留空，XML 文件将不格式正确：

```php
$one = $root->new_child("Travelpackage", "");
```

我们正在创建的 XML 文档具有一个名为 Travelpackage 的元素，其中带有属性 name="a"。要添加属性，我们使用 setattr() 函数。setattr() 有两个参数——第一个字符串是属性名称，第二个字符串是属性值。当 XML 文档创建完成后，我们得到 name="value"：

```php
$one->setattr("name", "a");
```

现在我们可以添加 Travelpackage 的其余子节点：

```php
$one->new_child("Country_name", "Cuba");
$one->new_child("City", "Cayo Coco");
$one->new_child("Resort", "Club Tryp Cayo Coco");
$one->new_child("Resort_rating", "4");
```

```php
$one->new_child("Resort_typeofholiday", "beach");
$one->new_child("Resort_watersports", "true");
$one->new_child("Resort_meals", "true");
$one->new_child("Resort_drinks", "true");
```

Travelpackage 的一个子节点是 Package，它是一个空节点，是另外两个节点的父节点。如果继续使用上述语法，则 Package 的子节点将变成 Travelpackage 的子节点。因此，我们创建一个名为 $oneSub 的新对象，并将其设为 Travelpackage 的子节点：

```php
$oneSub = $one->new_child("Package", "");
```

现在我们为 Package 分配两个子节点：

```php
$oneSubSub = $oneSub->new_child("Package_dateofdep", "5/8/89");
$oneSubSub = $oneSub->new_child("Package_price", "879");
```

此过程对第二个 Travelpackage 实例重复。我们将使用数组和循环来构建第二个 Travelpackage 实例。在此情况下，我们将节点名称 Country_name 分配给数组键，将节点内容 Cuba 分配给数组值。数组可以通过数据库查询填充，其中键是表列名，值是表格单元格中的数据：

```php
$two = $root->new_child("Travelpackage", "");
$two->setattr("name", "b");

$nodeName = array(
"Country_name" => "Cuba",
"City" => "Varadero",
"Resort" => "Sol Club Paleras",
"Resort_rating" => "3",
"Resort_typeofholiday" => "beach",
"Resort_watersports" => "false",
"Resort_meals" => "true",
"Resort_drinks" => "false");

while (list($key,$value) = each($nodeName)) {
    $two->new_child($key, $value);
}

$twoSub = $two->new_child("Package", "");

$twoSubSub = $twoSub->new_child("Package_dateofdep", "5/1/89");
$twoSubSub = $twoSub->new_child("Package_price", "779");
```

现在我们已经为 XML 文档创建了所有节点，需要创建该文档。首先，我们创建一个新文件，然后将内存中的节点转储到新文件中。在 fopen() 中使用 "w+" 模式，我们将使用内存转储的内容创建一个新文件。这将替换任何同名现有文件：

```php
$fp = fopen("travel.xml", "w+");
```

要向现有文件追加内容，不能像处理普通文件那样与其交互。首先，我们需要将文件读入内存，然后才能添加一个新子节点，并使用 dumpmem() 转储内存来写入新追加的文件。请确保不要向文档发送新的根节点：

```php
fwrite($fp, $doc->dumpmem(), strlen($doc->dumpmem()));
fclose($fp);
```

以下代码打开 XML 文件，然后将其加载到内存中：

```php
$doc = xmldoc(join("", file("travel.xml")));
$root = $doc->root();
$nodes = $root->children();
```

首先，我们创建一个名为 $doc 的 DOM 对象实例，然后分配一个根节点，并使用根节点下的所有子节点填充 nodes 对象。当现有文件读入 XML 树后，我们可以向根节点添加新节点或子节点。这个新节点或子节点称为 Travelpackage，它将成为其余节点的父节点：

```php
$one = $root->new_child("Travelpackage", "");
$one->setattr("name", "c");
```

接下来是要添加到文档中的值的数组：

```php
$nodeName = array(
"Country_name" => "Jamaica",
"City" => "Ocho Rios",
"Resort" => "Sandles Ocho Rios",
"Resort_rating" => "3",
"Resort_typeofholiday" => "beach",
"Resort_watersports" => "true",
"Resort_meals" => "true",
"Resort_drinks" => "true");
```

使用 while 语句添加值：

```php
while (list($key,$value) = each($nodeName)) {
	$one->new_child($key, $value);
}
```

添加包详细信息：

```php
$oneSub = $one->new_child("Package", "");
$oneSubSub = $oneSub->new_child("Package_dateofdep", "5/11/89");
$oneSubSub = $oneSub->new_child("Package_price", "679");
```

然后我们将所有数据写回 XML 文件。我们可以通过更改 fopen() 语句中的文件名，将数据写回到另一个文件中。在向 XML 文档追加内容时，我们使用 w+ 模式，这似乎不合常理。如果使用 a+ 模式，最终会得到一个包含总共五组 Travelpackage 元素和两个根节点的 XML 文件。文件中已有两个 Travelpackage 元素，我们将它们读入内存，添加另一个，然后写入文件末尾，从而生成 2 + 2 + 1。这还会导致生成无效的 XML 文件，因为会出现两个 XML 声明。

