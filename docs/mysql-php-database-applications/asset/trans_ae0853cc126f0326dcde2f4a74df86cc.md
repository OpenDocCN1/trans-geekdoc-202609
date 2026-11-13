

懂 C 语言编程的人都知道，这是一个“关联数组”，其中数组元素是通过名称而非数字来访问的。

对于返回内缝数据的 Web 服务来说，了解响应请求中返回的浮点数适用的单位会很有帮助。你可以修改 Body 元素的内容，将此信息存储在一个结构体中。

此处定义的结构体包含两个元素：_value_（浮点数值）和 _unit_（单位字符串，例如英寸、厘米或其他）。

```
<return xmlns:ns1="urn:referenceToWebService"
xsi:type="ns1:inseamInfo">
<unit xsi:type="xsd:string">inch</unit>
<value xsi:type="xsd:double">34.0</value>
</return>
```

在这种 SOAP 使用模式下，所引用的 Web 服务定义了一个名为 inseamInfo 的结构体，该结构体由一个名为 unit 的字符串和一个名为 value 的浮点数组成。通过在打开的 return 标签中声明返回值类型为 inseamInfo，你就可以合法地引用这些子元素了。

SOAP 规范还有很多内容，并非全部都晦涩难懂。其中一些更有趣、更有用的部分涉及如何通过 SOAP 记录错误和其他异常情况，而另一些则涉及如何在 SOAP 消息中描述其他复合数据类型。规范的这些方面超出了本章的范围，但当然值得学习。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_569_0.png)

万维网联盟网站上有大量关于 SOAP 的信息，包括概述（http://www.w3schools.com/soap/soap_intro.asp）和教程（http://www.w3schools.com/soap/default.asp）。

## 代码概览

任何成功的软件设计职业生涯的关键，在于能够自由利用他人的工作。开源运动正是关于这种实践，幸运的是，大量软件可供获取。NuSphere 公司（PHPE 的开发商，PHPE 是一种 PHP 开发环境）开发了一组名为 SOAPx4 的类，此后该类经过修改并重命名为 NuSOAP。这是一个功能非常强大的 SOAP 套件，几乎为你完成了所有繁重的工作。如果你使用的是 PHP 开发环境（例如 NuSphere 的 PHPE 3.0 或更高版本），你可能会发现使用 NuSOAP 更加轻松。在初始设置好环境后，你可以将自己的模块——例如 PHP 的新版本——添加到你的环境中。

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_570_0.png)

获取 NuSOAP 的最佳起点是迪特里希·阿亚拉的网站（http://dietrich.ganx4.com/nusoap/）。他的网站包括指向 NuSOAP 最新版本的链接，以及面向开发者和架构师的文档、邮件列表和其他资源的链接。

## NuSOAP 的精髓

NuSOAP 是一系列类。你将下载的文件（大多是 .php 文件）复制到 include 目录，然后在自己的 PHP 类中引用它们。NuSOAP 类负责创建 SOAP 客户端和服务器对象以及管理这些对象之间 SOAP 消息的传输等工作。NuSOAP 类甚至会处理本章前面讨论过的内容：将值编码为结构正确的 XML。

在大多数情况下，你可以把 NuSOAP 类视为黑盒。只需将 PHP 文件放入 include 目录，然后就不必再担心它们。你只需在编写想要作为 Web 服务提供者或消费者的 PHP 程序时，意识到自己拥有一些新的可用类即可。

假设你想构建一个服务器。换句话说，你想将一个 PHP 函数作为 Web 服务提供出来。添加所需的 include 语句（如下所示）后，你面前有一个四步流程。

```
require_once('nusoap.php');
```

- 1. 创建服务器对象。你只需将一个变量设置为等于 soap_server 对象（soap_server 是通过包含 NuSOAP 而提供的类之一）。很简单：

  $server = new soap_server;

- 2. 将本地函数之一注册到该新的 soap_server 对象。同样，没问题。你只需调用 soap_server 对象的 register() 函数，将本地函数之一作为唯一参数指定。完整语法如下：

  $server->register('getInseam');

- 3. 定义一个名为 getInseam() 的函数。它可以包含你想要的任何代码。推测在此情形下，它会访问数据库以检索特定人士的内缝测量值，然后返回一个值和单位。该函数的骨架如下：

  function getInseam($name) {
  // Function code...
  }

- 4. 将 soap_server 对象调制到它要监控的 HTTP 请求，并使其能够响应这些请求。你可以使用一段标准代码来完成此操作，该代码在不同的 NuSOAP 应用程序中几乎不会有变化：

  $server->service($HTTP_RAW_POST_DATA);

这些是 NuSOAP 实现下 SOAP 服务器的关键要素。那么，与该服务通信的客户端呢？它更加简单。

NuSOAP 客户端也必须包含 nusoap.php 文件。完成此操作后，他们只需用要调用的服务的 URL 作为参数来实例化一个 soapclient 对象（同样，soapclient 对象是 NuSOAP 集合的一部分）。例如，如果你在 http://www.wiley.com 上有一个名为 getInseam() 的服务（顺便说一句，实际上并没有），你可以这样做来创建一个用于调用它的 SOAP 客户端：

```
$soapclient = new soapclient('http://www.wiley.com/getInseam.php');
```

然后你可以通过该客户端向服务器发送调用，如下所示：

```
write( $soapclient->call('getInseam',array('name'=>'Joe Blogs')));
```

相当酷，对吧？参数作为数组发送，使你可以按喜好将发送的值与预期的值匹配。

## 简单的 NuSOAP 服务调用

现在我们快速看看一个借助 NuSOAP 类编写的“Hello, user”程序。实际上，这里有两个程序：一个客户端和一个服务器。服务器公开了一个简单的例程，它接收一个字符串（用户名），并返回由单词 Hello、提供的名称和一个句点组成的字符串。换句话说，如果你将 Ralph 作为参数发送给该服务，服务器会说 Hello, Ralph。

首先你需要一个服务器。服务器的名称与你想要公开的服务名称相同，因此在此将其命名为 hello.php。其完整内容如下：

```
require_once('nusoap.php');

$server = new soap_server;

$server->register('hello');

function hello ($name){
    return "Hello $name.";
}
```

```
$server->service($HTTP_RAW_POST_DATA);
```

其实并不复杂。只需将一个普通函数注册到特殊服务器对象，然后让该服务器处理 HTTP 活动即可。

每个服务器都需要一个客户端。在此例中，客户端文件可以命名为任何名称，并可以放置在服务器可通过 HTTP 访问的任何位置。

```
require_once('nusoap.php');

$soapclient = new soapclient('http://yourdomain.com/hello.php');

write($soapclient->call('hello',array('name'=>'Ralph')));
```

其实很简单。你只需将客户端绑定到服务（本示例假设你确切知道它的位置和名称），并在需要从中获取值时调用该客户端。

NuSOAP 的精髓在于其简单性。除了我们刚才讨论的内容之外，还有更多内容——随着章节的继续，你会看到一些更复杂的部分——但毫无疑问，NuSOAP 使将 SOAP 客户端和服务器功能集成到 PHP 程序中变得难以置信的容易。可以这样说，除出于教育目的外，再也没有理由编写自己的 SOAP 客户端和服务器类了。那将是重新发明一个已经非常完善的轮子。

## 确定应用程序的目标

是时候来看看 PHP 下的 SOAP 消息传递，以及通过 SOAP 与公开可访问的 Web 服务通信的一些方式。本章余下部分将着重介绍一个从不同来源请求信息、解析信息并将其呈现给用户的应用程序。

我们的目标是利用几个提供商提供的 Web 服务——巴诺书店（Barnes & Noble）和巴别鱼翻译服务——来收集信息。具体来说，我们使用巴诺书店服务来收集我们感兴趣的书籍信息，并使用巴别鱼服务将一段英文文本翻译成一系列欧洲语言。

巴诺书店应用程序接受国际标准图书编号（ISBN），并返回该编号所标识图书在巴诺书店网站 www.bn.com 上的价格。如果你将其发送值 0440234816（即 Karen Marie Moning 的小说《驯服高地战士》的 ISBN），你可以期望在本地 PHP 程序中看到以下输出：

图书编号 0440234816 的价格为 $6.99。

对于“一部带有超自然色彩的中世纪浪漫小说”来说，这个价格确实是一笔便宜货。

