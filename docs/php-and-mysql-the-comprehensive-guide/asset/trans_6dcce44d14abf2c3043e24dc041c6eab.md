

<price currency="Euro">22.50</price>
</product>
</products>

## 代码清单 29.13 XML文档 ("products_dtd.xml")

DOM扩展还针对此提供验证——实际上，有三种验证类型：

- 针对已知的 DTD
- 针对 XSD
- 针对 RELAX NG，一种非常简单的结构描述语言，在实践中非常流行¹

PHP 为这三种各提供了一个单独的方法：

- validate() 针对 DOMDocument 对象中链接的 DTD 进行验证：
  `$dom->validate();`
- schemaValidate(filename) 针对指定为文件名的架构文件进行验证：
  `$dom->schemaValidate("schema.xsd");`
  使用 schemaValidateSource(String)，也可以针对指定为字符串的 XSD 文档进行验证。
- relaxNGValidate(filename) 针对 RELAX NG 文件进行验证：
  `$dom->relaxNGValidate("relax.rng");`
  同样也有对应方法 relaxNGValidateSource(String)，它针对字符串进行验证。

## 代码清单 29.14 针对 DTD 进行验证 ("validate.php")

```php
<?php
$dom = new DOMDocument();
if ($dom->load("products.dtd.xml")) {
    if ($dom->validate()) {
        print "Validation successful!";
    } else {
        print "Validation failed!";
    }
}
?>
```

¹ RELAX NG 的主页位于 www.relaxng.org。RELAX NG 与 OASIS 合作，被标准化为 ISO 标准。

![](img/ae7820c36e8f24c1623d26668b28e80e_811_0.png)

## 图 29.9 带有（故意引入的）错误的验证

## 29.2.5 XSLT

与 XML 文档一样，XSLT 文档也是一个 DOMDocument 对象。从 PHP 角度来看，XSLT 转换非常简单，包含以下步骤：

1. 首先加载 XML 文件和 XMLReader。

2. 然后启动 XSLT 处理器：

```php
$pro = new XSLTProcessor();
```

3. 现在导入 XSLT：

```php
$pro->importStylesheet($xsl);
```

使用 setProperty(Namespace, Name, Value) 可以为转换设置属性。

4. 使用 transformToDoc(DOM) 执行转换：

```php
$erg = $pro->transformToDoc($dom);
```

> 注意
> 或者，你可以使用 transformToXml(DOM) 生成 XML 字符串。或者，你可以使用 transformToUri(DOM, URI) 将 DOM 文档转换为流。

5. 最后，保存结果。在这里，这是以字符串形式完成的：

```php
print $erg->saveXML();
```

你也可以使用 DOM 扩展的其他方法，例如 save(File) 将转换后的文档保存到文件中。

以下脚本——类似于代码清单 29.5——将 products.xml XML 文档转换为 HTML 页面（参见图 29.10）。

```php
<?php
$xml = new XMLReader();
$xml->open("products.xml");

while ($xml->read()) {
    if ($xml->nodeType == XMLReader::ELEMENT) {
        if ($xml->localName == "title") {
            $xml->read();
            echo htmlspecialchars($xml->value) .
                "<br />";
        }
    }
}
?>
```

## 代码清单 29.15 XSLT ("xslt.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_812_0.png)

## 图 29.10 作为 HTML 表格的产品

## 29.3 XMLReader 和 XMLWriter

XMLReader 和 XMLWriter 是新的 XML 访问变体，模仿了 Microsoft .NET Framework 中的 XmlReader 和 XmlWriter。它们与通过 SAX 访问类似，但使用更简单。

> **Note**
> 自 PHP 5.1 起，XMLReader 和 XMLWriter 已直接集成到 PHP 内核中。

### 29.3.1 XMLReader

与基于事件的 SAX 解析器不同，XMLReader 具有光标导向的解析器，这从读取文件中很常见。这意味着 XML 元素会逐个遍历。然后可以通过各种属性获取相应元素的更详细信息。诸如 XMLREADER::ELEMENT 之类的常量确定元素的类型（标签、文本等）。完整概览可见 http://s-prs.co/v602242。

与 DOM 解析器相比的优势显而易见：无需将整个文档存储在内存中。与 SAX 解析器相比，XMLReader 使用起来稍微简单一些，性能也略好。此外，目前还允许针对 RELAX NG 使用命名空间和验证。

以下清单显示了一个简单示例，它遍历 XML 文件并输出 `<title>` 标签内的所有值（参见图 29.11）。

```php
<?php
$xml = new XMLReader();
$xml->open("products.xml");

while ($xml->read())
{
if ($xml->nodeType == XMLReader::ELEMENT) {
if ($xml->localName == "title") {
$xml->read();
echo htmlspecialchars($xml->value) .
"<br />";
}
}
}
?>
```

## 代码清单 29.16 使用中的 XMLReader ("xmlreader.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_813_0.png)

## 图 29.11 读取两个产品的标题

### 29.3.2 XMLWriter

XMLWriter 是 XMLReader 的对照对象。它编写 XML 文档，并以严格的层级方式进行，与读取器一样。每个元素被启动（xmlwriter_start_element()）并结束（xmlwriter_end_element()）。它可以以函数导向和面向对象两种方式使用。代码清单 29.17 显示了函数导向访问的示例，结果如图 29.12 所示。

```php
<?php
$xmlwr = xmlwriter_open_memory();
xmlwriter_set_indent($xmlwr, true);
xmlwriter_start_document($xmlwr);
xmlwriter_start_element($xmlwr, "products");
xmlwriter_start_element($xmlwr, "product");
xmlwriter_start_element($xmlwr, "title");
xmlwriter_text($xmlwr, "Vacuum cleaner XY");
xmlwriter_end_element($xmlwr);
xmlwriter_start_element($xmlwr, "price");
xmlwriter_write_attribute($xmlwr, "currency", "Euro");
xmlwriter_text($xmlwr, "4,80");
xmlwriter_end_element($xmlwr);
xmlwriter_end_element($xmlwr);
xmlwriter_end_element($xmlwr);
xmlwriter_end_document($xmlwr);
echo htmlspecialchars(xmlwriter_output_memory($xmlwr));
?>
```

## 代码清单 29.17 使用中的 XMLWriter ("xmlwriter.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_814_0.png)

## 图 29.12 XMLWriter 在此输出 XML 文件

代码清单 29.18 显示了相同的示例，但采用面向对象的表示法。

```php
<?php
$xmlwr = new XMLWriter();
$xmlwr->openMemory();
$xmlwr->startDocument('1.0', 'UTF-8');
$xmlwr->setIndent(true);
$xmlwr->startDocument();
$xmlwr->startElement('products');
$xmlwr->startElement('product');
$xmlwr->startElement('title');
$xmlwr->text('Vacuum cleaner XY');
$xmlwr->endElement();
$xmlwr->startElement('price');
$xmlwr->writeAttribute('currency', 'Euro');
$xmlwr->text('4,80');
$xmlwr->endElement();
$xmlwr->endElement();
$xmlwr->endElement();
$xmlwr->endDocument();
echo htmlspecialchars($xmlwr->outputMemory());
?>
```

## 代码清单 29.18 XMLWriter: 面向对象 ("xmlwriter_oo.php")

## 29.4 EXIF

XML 有成千上万的应用示例。原则上，无论在哪里需要存储和交换数据，都会使用 XML。在本节中，XML 用于存储图像信息。数码相机的元信息存储在可交换图像文件格式（EXIF）中。2

我们的应用程序应允许用户上传图像。然后读取其部分 EXIF 数据并将其打包到 XML 文件中。第二个脚本访问 XML 文件并读取数据的一小部分。

### 29.4.1 准备工作

为了让 PHP 访问 EXIF 数据，你需要相应的扩展。在 Linux 下，使用 --enable-exif 配置 PHP。在 Windows 下，只需通过删除分号来注释掉以下行：

```
extension=php_exif.dll
```

2 EXIF 是一种存储有关相机、照片和拍摄参数信息的标准。但是，还有许多其他元数据格式，例如 Adobe 的可扩展元数据平台（XMP），它们部分基于 XML。

你可能仍需要激活 extension=php_mbstring.dll，并在调用 php_exif.dll 之前调用它。

### 29.4.2 实现

该应用程序由两个脚本组成：upload.php 脚本将图像上传到服务器，读取 EXIF 数据并将其保存在 XML 文件中。read.php 文件从 XML 文件和硬盘中检索 EXIF 数据和图像。

文件上传后，临时文件³ 使用 move_uploaded_file(origin, destination) 方法从原始存储位置复制到目标位置。图像应与用户计算机上的名称相同。该文件最终位于 images 子文件夹中：

```php
if (isset($_FILES["File"])) {
   move_uploaded_file($_FILES["File"]["tmp_name"], "./images/" .
   $_FILES["File"]["name"]);
}
```

> **Note**
> 
> 你可能需要检查是否已存在同名文件。如果你的管理系统有多个用户，那么每个用户都需要自己的目录。你还应该检查图像的大小并设置相应的限制。

下一步是读取 EXIF 数据。为此使用 exif_read_data(Image, Required, Array, Thumbnail) 方法。你将图像名称作为参数指定。随后是一个字符串，其中包含必须存在的 EXIF 信息部分，才能读取图像的 EXIF 头部。⁴ 第三个参数控制是否将 EXIF 数据作为数组返回；第四个参数确定是否也应传输缩略图，⁵ 缩略图通常存在于 EXIF 头部中：

其余部分则是 DOM 工作。如果文件尚不存在，则会创建新文档并写入根元素。随后是图像标签，它应包含刚刚上传图像的信息。各个 EXIF 信息由 foreach 循环提供。以下是针对文件信息的处理示例：

