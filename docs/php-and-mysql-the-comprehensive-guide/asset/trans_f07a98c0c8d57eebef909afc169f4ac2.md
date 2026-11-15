

## WSDL

手动生成 SOAP 消息并非一项愉快的任务。WSDL 的存在正是由此得到证明。与 SOAP 一样，WSDL 是由微软和 IBM 提交给 W3C 的。当前版本为 2.0（www.w3.org/TR/wsdl.html）。

WSDL 为 Web 服务提供了描述。该描述包含所有方法，但也可以提供许多当今已不常用的附加信息。

WSDL 被大多数 Web 服务实现所使用，以减轻开发人员的工作量。当你创建一个服务时，实现可以自动生成 WSDL。如果你使用该服务，实现会访问 WSDL 并自动从中生成所需的 SOAP 消息。

## The Problems

当今 Web 服务被广泛使用。然而，仍有许多因素尚未得到最佳解决，或者正在被研究：

- 安全性。
- 性能。
- 事务和流程。
- 目录服务并不十分成功；PHP 也没有现代的实现。

谈到安全性，标准在不断开发：OASIS 的 WS-Security 提供了一种良好的总体方法。WS-Security 具有非常开放的结构，并结合了许多其他现有标准，例如 XML Encryption 和 SAML。然而，例如在 PHP 中，仍然没有全面的实现。

在实践中，我们已经看到了许多用于身份验证和会话管理的自定义方案。一些 Web 服务提供商也省略了进一步的安全机制。Amazon 是一个示例。只使用开发者令牌（即唯一 ID），该令牌随方法调用一起发送。亚马逊不使用进一步的安全措施（例如 SSL 证书），因为亚马逊自身处理最后一步（付款），并且只允许亚马逊客户进行此操作。

另一个经常被提及的问题是与二进制传输相比的性能劣势。这里的一种解决方案是使用 HTTP 的 gzip 功能。但是，你应该对此进行测试，以便真正确定压缩对你的数据量是否必要。基于 SOAP 的 Web 服务还经常因描述数据的“开销”而从性能角度受到批评。基于 REST 的服务解决了这个问题。

第三个问题是事务和流程的覆盖。让我们谈谈一个简单的例子。假设你预订了一张火车票。然后你上了一班满载的乘客列车，对自己的预订感到高兴，挤过头等舱，来到自己的座位前。但座位并非空着：一位和蔼的老妇人坐在那里。你进行了一番小小的争论，老妇人出示了她的车票，车票上显示的预订时间与你的车票上完全相同。在这种情况下，应用程序中的事务安全性已经失败。⁴

目前有许多标准旨在提供事务和流程功能。最有前途的可能是 BPEL。

## The Implementations

在谈到互操作性时，人们常常忘记，你自然需要在服务器端编程语言中实现 Web 服务。⁵ PHP 凭借其多样化的开发者社区而繁荣，并提供了不同的实现。一方面，这是一种优势；另一方面，用于实现新标准的剩余资源并不多。

以下是最重要的 Web 服务库和包的非常简要的概述：⁶

- nuSOAP 基于迪特里希·阿亚拉开发的内容。nuSOAP 本身最初源自由迪特里希·阿亚拉编写的 SOAPx4 库。其优势在于能够动态生成 WSDL 并与各种编程语言成功实现互操作性。
- PHP-SOAP 是随 PHP 提供的标准库，因此是在 PHP 中使用基于 SOAP 的 Web 服务最常用的方法。

> 注释
> PHP-SOAP 的开发在 PHP 社区中颇具争议。许多人希望将 PHP 4 中最流行的包 PEAR::SOAP 移植到 PHP 5。这种观点之所以产生，是因为 PHP-SOAP 中存在一些错误。但是，PHP-SOAP 最终占据了主导地位。

### 27.1.2 安装

本节中安装说明的描述根据不同的实现进行了划分。

### nuSOAP

nuSOAP 的安装非常简单，因为它只是几个可以集成到项目中的 PHP 文件。从 https://github.com/contributte/nuSOAP 下载文件——这是原始 nuSOAP 针对现代 PHP 版本的重写。当前版本是 0.9.16。然后将 `lib` 目录放在项目文件夹或 Web 服务器上的任何其他文件夹中。你只需要将此文件集成到脚本中：

```
require_once "lib/nusoap.php";
```

作为替代方案，你也可以使用 Composer 进行安装。

4. 所幸，铁路旅行的问题已经解决多年。在这方面，这是一个虚构的例子。
5. 假定你不想手动操作，而对于大多数项目来说这几乎不可行。
6. 该选择基于实践和文献中的使用情况，但当然在某种程度上是主观的。

### PHP-SOAP

PHP-SOAP 必须在 Linux 配置期间激活：

```
--enable-soap
```

在 Windows 中，需要将以下行添加到 `php.ini`：

```
extension=php_soap.dll
```

PHP 7.2 或更高版本足够：

```
extension=soap
```

主机上可能已经配置好。使用 `phpinfo()` 检查模块是否已存在（参见图 27.2）。

![](img/ae7820c36e8f24c1623d26668b28e80e_751_0.png)

图 27.2 PHP-SOAP 作为模块集成

## 27.2 REST

访问 REST 消息基本上非常简单。REST 原则意味着数据和服务始终隐藏在唯一的 URL 后面。这意味着你只需要提供一个具有 URL 结构的 REST 服务器，其中可以调用单个方法。最简单的方法是通过 URL 参数，例如，采用以下结构：

- method 指定作为参数调用的方法。
- parameter 接收一个带有参数的数组。

这是一个完整的示例 URL：

```
http://localhost/php/rest_server.php?method=square&parameter=[24]
```

REST 数据交换可能有多种格式。你可以定义自己的 XML 格式，也可以使用 JSON，这是一种常用于数组和对象的表示法。

> **注释**
>
> URL 参数的名称完全可以自由选择。数据格式也是如此。一方面，这是灵活的——但另一方面，这也是 REST 的一个特点，因为你实际上必须自己定义一切。

以下脚本通过为方法和参数指定两个 GET 参数来创建 REST 服务器：

- 1. 系统首先检查参数是否可用：
  
  ```
  if (isset($_GET['method']) && isset($_GET['parameter'])) {
  ```
  
  此时可以进行进一步检查。但是，对于这个简单示例，我们只需确定参数是否存在即可。
- 2. 然后处理 URL 参数。包含函数参数的第二个 URL 参数使用 `json_decode()` 从 JSON 格式转换为 PHP 数组：
  
  ```
  $method = $_GET['method'];
  $parameter = json_decode($_GET['parameter']);
  ```
- 3. 为了防止调用未知方法，我们检查被调用的函数是否存在：
  
  ```
  if (function_exists($method)) {
  ```
  
  在实际应用场景中，将所有可调用函数注册到数组或对象中，并仅允许注册的函数是有意义的。
- 4. 然后可以通过使用第一个参数调用方法来获取结果。结果本身在同一步骤中也被转换回数组，然后使用 `json_encode()` 转换为序列化数组：
  
  ```
  $result = [method($parameter[0])];
  echo json_encode($result);
  ```

当使用具有不同数量参数的多个方法时，必须在此处添加进一步检查。

清单 27.1 包含完整代码；图 27.3 显示输出。

```
<?php
function square($a) {
    if ($a != null && trim($a) != "") {
        $square = $a * $a;
        return $square;
    }
}

if (isset($_GET['method']) && isset($_GET['parameter'])) {
    $method = $_GET['method'];
    $parameter = json_decode($_GET['parameter']);
    if (function_exists($method)) {
        $result = [$method($parameter[0])];
        echo json_encode($result);
    }
}
?>
```

### 清单 27.1 REST 服务器 ("rest_server.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_753_0.png)

### 图 27.3 直接使用 "GET" 参数调用时服务器的返回

客户端的结构非常简单。如果在 `php.ini` 中激活了 `allow_url_fopen`，则可以使用文件函数直接访问 REST 服务。这里我们使用 `file_get_contents()`。核心是此处组装的 URL：

```
$url = 'http://localhost/php/rest_server.php?method=' .
    urlencode($method) . '&parameter=' . urlencode(json_encode($parameter));
```

