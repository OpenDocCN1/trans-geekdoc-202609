
XML-RPC 可以看作是 SOAP 的复杂性与 REST 的简单性之间的折中。然而，它与 SOAP 非常相似，以至于被完全吸收到这种厂商友好的概念中。正如你将看到的，PHP XML-RPC 服务器可以交付 SOAP 响应。

可以在 `www.xmlrpc.org` 了解更多关于 XML-RPC 的信息。

## SOAP

SOAP 可能代表简单对象访问协议——委员会的一些成员对此有争议——但许多人现在已经说它通过使用已成为现实。SOAP 是 W3C 的一项提案，由一个很大程度上受大软件控制的委员会制定——在主要作者中，四位来自微软，一位来自 Lotus，一位来自 IBM，其余全是。这是 SOAP 的优点也是分歧：自从微软和 IBM 支持 SOAP，其他软件制造商的采纳非常迅速，但一直面临着开放标准被变为厂商锁定机制的持续威胁。

SOAP 与 XML-RPC 一样，使用 XML 封装发送消息，并具有相当严格的词汇，大量使用了命名空间。一个简单的请求可能如下：

```
POST /xmlrpc-epi/xmlrpc-php/sample/server.php HTTP/1.0
User-Agent: xmlrpc-php/0.2 (PHP)
Host: localhost:80
Content-Type: text/xml
Content-Length: 530
```

```
<?xml version='1.0' encoding='iso-8859-1' ?>
<SOAP-ENV:Envelope
xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope"
xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance"
xmlns:xsd="http://www.w3.org/1999/XMLSchema">
<SOAP-ENV:Header>

<SOAP-ENV:Body>
<greeting>
<xsd:string>World</xsd:string>
</greeting>
</SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

响应可能类似于以下：

```
<?xml version='1.0' encoding='iso-8859-1' ?>
<SOAP-ENV:Envelope
xmlns:soap="http://schemas.xmlsoap.org/soap/envelope"
xmlns:xsi="http://www.w3.org/1999/XMLSchema-instance"
xmlns:xsd="http://www.w3.org/1999/XMLSchema">
<SOAP-ENV:Header>

<SOAP-ENV:Body>
<GreetingResponse>
<SOAP-ENV:Array arrayType="xsd:string">
<xsd:string>Hello, World</xsd:string>
</SOAP-ENV:Array>
</GreetingResponse>
</SOAP-ENV:Envelope>
```

SOAP 提供的数据类型比 XML-RPC 更多。然而，你必须提供比 XML-RPC 多得多，这两种协议非常相似。显然，SOAP 也受到了大软件的认可。可以在 `soap.org` 了解更多关于 SOAP 的信息。

## Web 服务

Web 服务可以意味着任何事物。它是一种编程语言、一个虚拟机、一组 Web 服务、一种跨互联网的用户识别服务、一个营销口号或以上所有内容。

到为止，问题在于是非微软客户端出现了互操作性问题。互操作性是任何开发者关注的一个大领域，因此有许多讨论，并希望微软向真正的通用标准移动。

## 标准

在 Web 服务真正流行之前，应用程序需要透明地处理其结果。由于 Web 服务标准仍在变动中，并且存在多个竞争标准，这种情况尚未发生。对于小型应用程序，如果服务发生变化并不是大事——但对于像 Lotus 这样的大应用程序，使用 SOAP 进行透明研究是一项巨大的投资。

## 隐藏与寻找

Web 服务的最终目标是让应用程序找到它需要的所有结果。假设你收到一封电子邮件——你的服务器或客户端应该足够智能到找到文档并将最终结果显示给你。为了实现这一点，我们需要某种目录系统和描述它们的标准。WSDL 和 UDDI 是使之可能的技术。WSDL（Web 服务语言）描述 Web 服务接口，而 UDDI（通用描述、发现和集成）是 Web 服务的注册。分别可以在 `uddi.org` 和 `www.w3.org/TR/wsdl` 了解更多关于 WSDL 和 UDDI。

我们距离应用程序自动发现和通信还有很远。事实上，许多部署 Web 服务的企业故意这样做——例如 FedEx 在被黑客利用后关闭了他们的服务器。Web 服务在半私交易领域增长最快。与此同时，如果你现在想玩玩 Web 服务，可以在以下网站找到：

- `syndic.com`（用 PHP 写的 Feed 源）
- `xmlrpc.com/directory/16b/services`
- `xmlmethods.com`（部分来自版权网站）

## 谁来付费？

关于公共 Web 服务最大的问题是：谁来付费？怎么付？到目前为止，你可以访问的大多数 Web 服务如博客和货币计算器——人们预计不会为这些服务付费。大软件的答案是创建巨大的 Web 服务网络，类似于 Hailstorm 或 Liberty Alliance 的网络。这对隐私和开放架构具有严重影响。

除非 Web 服务找到一种自我付费的方法，否则它们可能继续被部署在企业防火墙内部和非公开场合。

## 项目：REST 客户端

列表 41-1 是 Amazon 优雅 REST 服务的基本客户端脚本，该服务自 2002 年以来一直向 Amazon 联盟和其他开发者提供（带有某些更改）。你在脚本顶部输入一个搜索字符串，它在末尾输出一个 CSS 格式的框，其中包含有关书籍当前版本的信息。

此脚本清楚地演示了 REST 的最大优势：你可以使用已经熟悉的 HTTP 概念和 PHP 函数来与它工作。在所有方面，你只是使用 `http fopen()` 请求了一个 Web 页面。它很高兴是格式良好的 XML 而不是 HTML——但这只是传输机制的偶然。

我们选择使用 PHP 的 DOM 扩展来解析 XML，该扩展目前发现很少的实际应用（DOM 的描述请见第 40 章）。许多 PHP 开发者编写了使用其他类型解析（如字符串解析和正则）的脚本来提取所需信息——但我们向你展示使用 XML 本身的力量。

我们应该警告你，这种解决方案无法扩展——DOM XML 是臭昭名的内存大户。我们听过可靠的报告，将一个 1000 行的 XML 文档读入 DOM 会分配 1MB 的内存。然而，Amazon Web 服务每次只返回几个项目，因此 DOM XML 是此此目的恰当的技术。

> DOM 扩展在 PHP 中发生了巨大变化。此脚本在 5.0b2 之前的所有 PHP 版本上无法运行。显然，除非你之前编译 PHP 时使用了 `--with-dom` 标志和 libxml2，否则它无法工作。

### 列表 41-1：Amazon REST 服务客户端

```php
<?php
// 获取文件
$fwrite = 'phpfile.xml';
$file = 'http://www.amazon.com/onca/xml132t-webservices-20&dev=XXXXXXXXXXXXXXXXKeywordSearch=Parse+convert=PHP+&mode=books&type=lite&page=1&f=xml';
// 将 X 替换为 Amazon 开发者令牌
// 如果没有有效的令牌，注释掉下面的块
//并使用伪数据文件
// 将文本写入文件
$fp = fopen($file, "r");
$xml_array = file($file);
fclose($fp);
$xml_str = implode("", $xml_array);
$fp2 = fopen($fwrite, "w");
$fw_return = fwrite($fp2, $xml_str);
fclose($fp2);
?>

// Load up the xml file into memory
$dom = new DomDocument;
if (!$dom->load($writefile)) {
    echo "Cannot load xml file";
    exit;
}

// Get an immediately available edition
$editions = $dom->getElementsByTagName("Availability");
foreach ($editions as $edition_obj) {
    if ($edition_obj->nodeValue == "Usually ships within 24 hours") {
        // Get the data for this book
        $book_array = array();
        $parent_node = $parent_node->parentNode;
        $book_array['Details'] = $parent_node->getAttribute("url");
        $children = $parent_node->childNodes;
        foreach ($children as $child_obj) {
            $node_name = $child_obj->nodeName;
            if ($node_name != "@text") {
                $content_str = $child_obj->nodeValue;
                $book_array['$node_name'] = $content_str;
            }
        }
        continue;
    } else {
        // Give a message if availability isn't good
        $book_array['ProductName'] = 'Not available at this time:';
    }
}

print_r($book_array);
$title = $book_array['ProductName'];
$author = $book_array['Authors'];
$image = $book_array['ImageUrlSmall'];
$details_page = $book_array['Details'];
$price = $book_array['OurPrice'];

// Format a nice box
$box_str = <<< EONICEBOX
<HTML>
<HEAD>
<STYLE>
@content {
    float: left;
    padding: 10px;
    margin: 10px;
background: #FFFFFF;
border: 4px solid #008000;
width: 200px; /* ie5win fudge begins */
font-family: "|**";
font-family: inherit;
width: 200px;
}
body #content {
width: 170px; /* ie5win fudge ends */
font-family: Verdana, Arial, sans-serif;
font-size: 12px;
line-height: 22px;
margin-top: 3px;
margin-bottom: 2px;
}
<STYLE>
</HEAD>
<BODY>
<div id="content">
<P><IMG SRC="$image">
<BR><A HREF="$detail_page">$title</A>
<BR>author
<BR>price</P>
</BODY>
</HTML>
EONICEBOX;
echo $box_str;
```

如果你没有 Amazon 账户，可以使用列表 41-2 进行测试，你应该将其保存为树目录下的 `php.xml`。

### 列表 41-2：XML 示例

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ProductInfo xmlns:xsi="http://www.w3.org/2001/XMLSchema" xsi:noNamespaceLocationLocationhttp://www.amazon.com/schemas/3/dev-lite.xsd">

<Request>
<Args>
<Arg value="us" name="locale"/>
<Arg value="1" name="page"/>
<Arg value="Park Converse PHP">
</Args>
</Request>

<Request>
<Args>
<Arg value="KeywordSearch"/>
<Arg value="XXXXXXXXX" name="dev-t"/>
<Arg value="webservice" name="t"/>
<Arg value="xml" name="f"/>
<Arg value="books" name="mode"/>
<Arg value="lite" name="type"/>
</Args>
</Request>
<TotalResults>2</TotalResults>
<TotalPages>1</TotalPages>
<Details url="http://www.amazon.com/exec/ASIN/076454953/service=207-dev-t=XXXXXXXXX&camp=2025&link_code=xm2">
<AsIN>076454953</AsIN>
<ProductName>PHP, 2nd Edition</ProductName>
<Catalog>Book</Catalog>
<Authors>
<Author>Tim Converse</Author>
<Author>Joyce Park</Author>
</Authors>
<ReleaseDate>31 September, 2002</ReleaseDate>
<Manufacturer>John Wiley & Sons</Manufacturer>
<UrlSmall>http://www.amazon.com/images/P/076454953.01THUMB.jpg</UrlSmall>
<UrlMedium>http://www.amazon.com/images/P/076454953.01MZZZZ.jpg</UrlMedium>
<UrlLarge>http://www.amazon.com/images/P/076454953.01LZZZZ.jpg</UrlLarge>
<Availability>Ships within 24 hours</Availability>
<ListPrice>$49.99</ListPrice>
<UsedPrice>$24.49</UsedPrice>
</Details>
url="http://www.amazon.com/exec/ASIN/076454716X/service=207-dev-t=XXXXXXXXX&camp=2025&link_code=xm2"
<AsIN>076454716X</AsIN>
<ProductName>PHP 4 Bible</ProductName>
<Catalog>Book</Catalog>
<Authors>
<Author>Tim Converse</Author>
<Author>Joyce Park</Author>
</Authors>
<ReleaseDate>17 August, 2000</ReleaseDate>
<Manufacturer>John Wiley & Sons</Manufacturer>
<UrlSmall>http://www.amazon.com/images/P/076454716X.01THUMB.jpg</UrlSmall>
<UrlMedium>http://www.amazon.com/images/P/076454716X.01.MZZZZ.jpg</UrlMedium>
<UrlLarge>http://www.amazon.com/images/P/076454716X.01LZZZZ.jpg</UrlLarge>
<Availability>THIS TITLE IS CURRENTLY NOT AVAILABLE. If you would like to purchase this title, we recommend that you check this page to see if it has become available.</Availability>
<ListPrice>$39.99</ListPrice>
```
