

发挥想象力，根据本章所学内容创建一些真实世界的Web服务。另外，我们重点介绍SOAP Web服务；XML-RPC如今似乎不太常用了，而JSON Web服务（本章后面会介绍）已经变得更为流行。

## 使用NuSOAP创建Web服务

```
<?php
    require_once 'nusoap.php';

    $soap = new soap_server;
    $soap->register('add');
    $soap->service($HTTP_RAW_POST_DATA);

    function add($a, $b) {
        return $a + $b;
    }
?>
```

一个使用NuSOAP的SOAP Web服务（soap-nusoap.server.php）

在 http://nusoap.sourceforge.net/ 上，你会发现NuSOAP，它是PHP最著名的外部SOAP类之一。有些人甚至可能知道它的前身SOAPx4。如今，其发布新版本的频率不高，但这个库相当稳定。你可能还想查看Subversion（SVN）仓库以获取最新代码。那里可能有几个文件，但你需要的只有nusoap.php。

使用NuSOAP创建Web服务非常简单，因为该模块处理了所有麻烦的事情，包括SOAP。只需按以下步骤操作：

- 1. 编写你想作为Web方法暴露的函数。
- 2. 实例化 `soap_server` 类。
- 3. 向SOAP服务器注册你的函数。
- 4. 调用 `service()` 方法并提交 `$HTTP_RAW_POST_DATA` 作为参数。

这段代码使用NuSOAP实现了一个SOAP服务器。图11.2展示了当你试图直接从客户端调用Web服务时浏览器的输出。错误消息提示XML为空——这是理所当然的，因为我们没有发送请求！

![](img/2862989e5dc7f1b1d0bc64321737f084_316_0.png)

图11.2 这个错误消息是个好兆头；脚本似乎可以工作（目前而言）。

![](img/2862989e5dc7f1b1d0bc64321737f084_319_0.png)

图11.4 这份WSDL是由NuSOAP生成的，而不是程序员编写的。

## 使用NuSOAP调用Web服务

```
<?php
    require_once 'nusoap.php';

    $soap = new soapclient('http://localhost/wsdl-nusoap-server.php?wsdl', true);
    $proxy = $soap->getProxy();
    $result = $proxy->add(47, 11);
    echo "47 + 11 = $result";
?>
```

使用NuSOAP调用Web服务（wsdl-nusoap-client.php）

实际上，使用NuSOAP服务比创建它还要容易。你只需加载WSDL文件，然后获得一个所谓的代理类。（这是一个本地类，其行为就像Web服务也是一个本地类一样。）因此，你可以直接调用Web服务的方法，NuSOAP会处理其余所有事情（包括打开到远程服务器的连接、组装和解析XML等）。

要做到这一点，必须实例化soapclient类（不带下划线字符），然后getProxy()方法会创建代理类。上面的代码针对前一个示例中的演示服务实现了这个流程。注意WSDL文件的URL：它是Web服务的URL末尾加上?wsdl；请根据你的系统相应地更改URL。

**注意：** 在URL末尾附加?wsdl以获取Web服务的WSDL描述，这个想法借鉴自Microsoft .NET（现在也被其他技术采用）。然而，在.NET中该后缀不区分大小写，而NuSOAP要求使用小写字母。在跨平台开发时请记住这一点。

## 使用PHP 5 SOAP扩展创建Web服务

```
<?php
$soap = new SoapServer(null, array('uri' => 'http://php.phrasebook.org/'));
$soap->addFunction('add');
$soap->handle();

function add($a, $b) {
    return $a + $b;
}
?>
```

*一个使用PHP 5 SOAP的Web服务（soap-php5-server.php）*

PHP 5的关键特性之一是新的SOAP扩展。由于它是用C语言编写的，因此比任何纯PHP代码都快得多。然而，这个扩展相对较新，因此仍然存在一些小问题和不完善的功能。不过，它通常能很好地工作。

要使用该扩展，你必须使用--enable-soap配置PHP；Windows用户必须在php.ini配置文件中添加extension=php_soap.dll。然后，扩展即可使用，编写SOAP服务器也变得相当容易。

同样，只需很少的步骤：实例化SoapServer类，使用addFunction()添加你的函数，最后调用handle()。

## 使用PHP 5 SOAP扩展自动生成WSDL

PHP 5 SOAP的最大缺点是无法使用它自动生成WSDL。这一点并不常被提及，但它确实在现实生活中造成问题。WSDL非常复杂，其中的错误难以察觉，甚至更难找到。然而，你仍然可以通过几种方式为Web服务创建这样的WSDL描述，其中大部分已在真实项目中使用。

- 使用NuSOAP或PEAR::SOAP创建一个类似的服务，仅为了获取WSDL——只需修改<soap:address>元素
- 使用Ctrx_SOAP_AutoDiscover类（可从 http://crtx.org/index.php?area=Main&page=Crtx_SOAP_AutoDiscover 获取）
- 使用Webservice Helper工具（可从 http://www.jool.nl/new/index.php?file_id=1 获取）
- 使用WSDL_Gen类（可从 http://www.schlossnagle.org/~george/php/WSDL_Gen.tgz 获取）

因此你可以看到，WSDL支持正在开发中，但不是作为SOAP扩展本身的一部分，而是以外部项目的形式。希望有一天这种情况会改变。

如果你最终拥有了服务的WSDL描述（在下载归档中，你会找到一个名为AddService.wsdl的文件，它源自PEAR::SOAP生成的WSDL），服务器的代码只需稍作更新。SoapServer实例化的第一个参数接收WSDL URL；此外，Web服务的方法必须放在一个类中。然后，setClass()向SOAP扩展提供要使用的类名：

```
<?php
$soap = new SoapServer(
    'AddService.wsdl',
    array('uri' => 'http://php.phrasebook.org/')
);
$soap->setClass('ServiceClass');
$soap->handle();

class ServiceClass {
    function add($a, $b) {
        return $a + $b;
    }
}
?>
```

一个支持WSDL的、使用PHP 5 SOAP的Web服务（wsdl-php5-server.php）

## 使用PHP 5 SOAP扩展调用Web服务

```
<?php
$soap = new SoapClient('AddService.wsdl');
try {
    $result = $soap->add(47, 11);
    echo "47 + 11 = $result";
} catch (SoapFault $e) {
    echo "Error: {$e->faultstring}";
}
?>
```

使用PHP 5 SOAP调用Web服务（wsdl-php5-client.php）

调用同样很容易，只要你拥有WSDL描述。这段代码调用Web服务并捕获任何错误，这要归功于PHP 5的try-catch机制。

提示：为了提高性能，PHP 5的SOAP扩展默认会缓存WSDL。以下是php.ini中推荐的标准设置：

```
[soap]
; Enables or disables WSDL caching feature.
soap.wsdl_cache_enabled=1
; Sets the directory name where SOAP extension
will put cache files.
soap.wsdl_cache_dir="/tmp"
; (time to live) Sets the number of seconds while
cached file will be used
; instead of original one.
soap.wsdl_cache_ttl=86400
```

当开发Web服务并可能更改WSDL时，这当然是个不费脑筋的决定。因此，在开发期间将soap.wsdl_cache_enabled设置为Off，但在生产服务器上应将其打开。

## 使用Ajax

维基百科列出了Ajax一词几十种不同的含义，包括一支荷兰足球队、荷马《伊利亚特》中的两个人物，以及一种家用清洁产品。然而，自2005年以来，Ajax还代表Asynchronous JavaScript + XML。这项技术远非新事物（其底层技术——来自JavaScript的XML HTTP请求——已得到Internet Explorer、Firefox、Safari和Chrome最新版本的支持；而且，XML对此并不是必需的），但直到这个奇怪的术语被创造出来之后，人们才真正开始使用它。

其基本原理是，JavaScript现在可以调用远程服务器，然后处理返回值，而无需重新加载整个页面。当然，这与PHP关系不大；然而，一些Ajax类使得在PHP中使用Ajax变得非常容易。

