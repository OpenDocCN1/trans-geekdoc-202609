

Babelfish 应用程序（http://babelfish.altavista.com）可让您将短语从英语翻译成法语、德语、意大利语、西班牙语或葡萄牙语。默认情况下，该程序设置为向 Babelfish 发送值 From beneath you, it devours。该应用程序为您提供以下翻译，其准确性各异。一般来说，如果在翻译中看到英文单词，则表示 Babelfish 遇到了困难。

- 法语 – De sous vous, il devours.
- 德语 – Von unter Ihnen es devours.
- 意大利语 – Sotto da voi, esso devours.
- 西班牙语 – Debajo de usted, él devours.
- 葡萄牙语 – Abaixo de você, ele devours.

显然，Babelfish 在 devours 方面存在问题。

有趣的是，所有操作均通过 Web 服务完成。您发送参数（前一示例中的 ISBN，以及后一示例中的目标语言和原始短语），而 Web 服务（可能很明显，并非本地托管）将返回您需要的字符串。

它是如何工作的？要回答这个问题，需要深入探索我们应用程序的代码，这部分内容将在下一节中介绍。

## 代码分解

要查看两个应用程序中的情况，您需要仔细查看 PHP 代码本身。Babelfish 应用程序和 Barnes & Noble 应用程序都是客户端——它们存在的目的是与在其他地方实现的服务器通信。

在此示例中，它们都与 XMethods（www.xmethods.com 或 www.xmethods.net）上的服务器通信，该网站托管了许多用于测试和实验的 Web 服务。您不需要知道这些远程服务的实现方式。它们可能使用 Java、C 或 PHP 编写。对您来说，这真的没有区别，因为它们已设置为通过 Internet 处理 SOAP 请求。

## Barnes & Noble 应用程序

Barnes & Noble 客户端将 ISBN 值（唯一标识印刷书籍）发送到 Web 服务，该服务返回 Barnes & Noble 网站 www.bn.com 上相应图书的售价。它会输出一个简单字符串，指示图书价格、www.bn.com 未列出该图书，或 Web 服务执行出错。

### 头文件

Barnes & Noble 和 Babelfish 应用程序中的许多文件最初会调用一个头文件。头文件 header.php 执行两项重要操作。首先，它导入关键的 nusoap.php 文件。它还指定本地应用程序如何处理错误。

这里是 header.php：

```php
<?php

require_once(preg_replace('/soap.*/','book.php',realpath(__FILE__)));
function soap_errors()
{
 $oh = set_error_handler('error_handler');
 if (empty($oh))
 {
 set_handler(0, H_ERROR);
 set_handler(E_ALL, H_LOG);
 }
 else
 {
 restore_error_handler();
 }
 }

soap_errors();

// include the class and function definitions for this application
require_once('lib/nusoap.php');
?>
```

### 客户端文件

客户端文件实际处理实例化连接到公开可访问的提供 Barnes & Noble 价格的 Web 服务的 SOAP 客户端的过程（实际上，它只是让 NuSOAP 完成脏活累活）。如下所示：

```php
<?php
// include the SOAP classes
require_once(dirname(__FILE__).'/header.php');
// define parameter array (ISBN number)
$param = array('isbn'=> '0385503954');
// define path to server application
$serverpath = 'http://services.xmethods.net:80/soap/servlet/rpcrouter';
//define method namespace
$namespace="urn:xmethods-BNPriceCheck";

// create client object
$client = new soapclient($serverpath);
// make the call
$price = $client->call('getPrice',$param,$namespace);
// if a fault occurred, output error info
if (isset($fault)) {
    print "Error: ". $fault;
}

else if ($price == -1) {
    print "The book is not in the database.";
} else {
    // otherwise output the result
    print "The price of book number ". $param['isbn'] ." is $". $price;
}
// kill object
unset($client);
?>
```

那么，这里发生了什么？其中一些内容应该很熟悉。首先，程序定义一个数组：

```php
$param = array('isbn'=>'0385503954');
```

然后，它设置一个变量（$serverpath），其中包含字符串形式的 URL：

```php
$serverpath = 'http://services.xmethods.net:80/soap/servlet/rpcrouter';
```

那个 URL 是什么？好吧，如果您在普通浏览器中打开它，会收到错误。错误实际上表明，在这种情况下您无法使用浏览器，因为这根本不是一个文档——而是一个远程过程调用（RPC）路由器。因此，您必须通过 HTTP POST 命令向其发送文本（即 SOAP XML）。这很合理，因为您希望从客户端向远程 Web 服务发送内容。

然后，您在该远程站点上指定正在使用的命名空间。这行代码用于实现该目的：

```php
$namespace="urn:xmethods-BNPriceCheck";
```

引用该站点的目的是检查其上存在的 Web 服务描述语言（WSDL）文件。WSDL 描述了特定站点上存在的 Web 服务以及它们公开的特定方法。您知道 BNPriceCheck 是 XMethods 上的有意义命名空间，因为您在 http://services.xmethods.net 上看到了其宣传。（它也在 http://www.xmethods.net/sd/2001/BNQuoteService.wsdl 上以编程方式描述。）

下一行应该看起来很熟悉。它是绑定到 XMethods RPC 路由器的 NuSOAP `soapclient` 对象的实例化：

```php
$client = new soapclient($serverpath);
```

完成所有这些后，您可以调用远程服务，并期望返回一个单个值：

```php
$price = $client->call('getPrice',$param,$namespace);
```

该行调用本地 `soapclient` 对象（包含在 `$client` 句柄中）的 `call()` 函数。它发送三个参数：

- `getPrice`—您正在调用的函数名称
- `$param`—您先前建立的结构体，包含 ISBN 值
- `$namespace`—您从 WSDL 文件中获取的命名空间，明确向 RPC 路由器表明您希望将查询发送到 Barnes & Noble 服务

请求发送后——请记住，NuSOAP 的工作是管理通过 HTTP（使用 `POST`）发送请求的机制，并在响应返回时处理它——您只需对返回的字符串做出反应。它将是以下三种情况之一：服务出错的指示、您发送的 ISBN 在数据库中未对应图书的指示，或价格值。以下是确定情况的代码：

```php
if (isset($fault)) {
	print "Error: ". $fault;
}

else if ($price == -1) {
	print "The book is not in the database.";
}
else {
	print "The price of book number ". $param['isbn'] ." is $".
	$price;
}
```

从该代码中可见，如果图书在数据库中，您期望的是一个浮点值，否则为 -1。如果存在名为 `$fault`（在 NuSOAP 中定义）的变量，则表示服务执行出现问题，并且 SOAP 响应的 `Header` 元素中使用了错误字段（有关 `Header` 元素如何指示错误条件的信息，请参阅 SOAP 规范）。

请注意，浮点值在精度方面存在一些风险。如果您处理大量数字，可能会出现舍入错误，而当这些错误涉及金钱时，您可能会陷入大麻烦！如有必要，请使用数学函数来保证精度，但在此无需担心——这不是问题。

## Babelfish 应用程序

Babelfish 应用程序（CD-ROM 上有三个）也是 SOAP 客户端，同样关注与 XMethods 实验站点上提供的 Web 服务通信。然而，这些应用程序与 Barnes & Noble 应用程序的区别在于，Babelfish 应用程序依赖于 XMethods（www.xmethods.com 或 www.xmethods.net）上公开的 WSDL 文件来了解 Web 服务。

出于讨论目的，请考虑 babel.php，即最简单的 Babelfish SOAP 客户端。其他客户端主要区别在于它们为不同语言多次执行相同操作。这是 babel.php：

```php
<?php
require_once(dirname(__FILE__).'/header.php');

$client = new soapclient(
    'http://www.xmethods.net/sd/2001/BabelFishService.wsdl'
    , 'wsdl'
);

$proxy = $client->getProxy();

$languages = array(
    'English'   => 'en',
    'French'    => 'fr',
    'German'    => 'de',
    'Italian'   => 'it',
    'Spanish'   => 'es',
    'Portuguese'=> 'pt'
);

$phrase = 'From beneath you, it devours.';

foreach ($languages as $language => $lc)
{
    if ($language == 'English')
        continue;
}
```
