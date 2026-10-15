
服务器。在这里，你传入打开文件的方法（GET 或 POST），并定义文件的打开方式。

## setRequestHeader("label","value")：

你可以通过传入一个表示标签及其值的字符串来为请求头（header）设置标签。此方法只能在 open() 方法使用之后、调用 send 函数之前调用。

## send(" ")：

这是实际将请求发送到服务器的方法。如果请求是异步发送的，响应将立即返回；如果不是异步的，则会在收到响应后返回。

## XMLHttpRequest 属性：

一些主要的 XMLHttpRequest() 属性如下：

## onreadystatechange：

onreadystatechange 属性是一个事件处理器，允许你在状态改变时触发特定的代码块或函数。

## readyState：

readyState 是一个对异常处理非常有用的属性，在决定何时执行某些操作时也很重要。例如，你可以让一组代码在 readyState 为加载状态时执行，或在 readyState 为完成状态时停止执行。

responseText：一旦请求完成，responseText 属性将被返回。如果你向某种脚本发起请求，脚本的输出将通过此属性返回。

一旦收到请求，服务器就会决定返回什么响应。有许多不同的响应代码，如下所示。

- 200 - 成功（OK）
- 401 未授权（Unauthorized）
- 403 禁止访问（Forbidden）
- 404 未找到（Not Found）
- 500 服务器内部错误（Internal Server Error）

## 向服务器发送请求：

要向服务器发出请求，你需要决定要连接哪个页面（或脚本），以及要将页面或脚本加载到哪个区域。

## 让我们看一个基本示例-

```html
<script>

function sendRequest(serverPage, objID)
{
```

## AJAX 操作的步骤

- 发生客户端事件。
- 创建 XMLHttpRequest 对象。
- 配置 XMLHttpRequest 对象。
- XMLHttpRequest 对象向 Web 服务器发出异步请求。
- Web 服务器返回包含 XML 文档的结果。
- XMLHttpRequest 对象调用 callback() 函数并处理结果。
- 更新 HTML DOM。

![](img/9ab4a56a650535285811bb802190e58f_172_0.png)

## 示例代码

```html
<script>

function showme(str)

{
```

Hirdesh Bhardwaj

```
// to check if you don’t enter anything...
if(str.length==0)
{
    document.getElementById("result").innerHTML='pls type something';
    return;
}
// make xmlhttp object for request
if (window.XMLHttpRequest)
{
    // code for IE7+, Firefox, Chrome, Opera, Safari
    xmlhttp=new XMLHttpRequest();
}
else
{
    // code for IE6, IE5
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
xmlhttp.onreadystatechange=function()
{
    document.getElementById("result").innerHTML=xmlhttp.responseText;
}
```

```
// send your request to getlist.java page via GET method with
argument city

xmlhttp.open("GET","getlist.php?city="+str,true);

xmlhttp.send();

}

</script>
```

```html
<form>

<input type="text" onkeyup="showme(this.value)" name="city" />

</form>
```

在这里，你将通过 getElementById 方法在 result 这个 id 中获取结果。

```html
<span id="result"></span>
```

## Getlist.php

```php
<?php

// Receive request on php page

$city=$_REQUEST['city'];

echo "City is ".$city;

// You may collect data from database on the base of requested city

?>
```

## 说明

## 托管你的网站

许多人喜欢在家中或办公室运行自己的服务器，如果你有时间，这是一个可行的托管解决方案。但自己托管网站可能会带来比其价值更多的问题。

你需要考虑备用电源、修补安全漏洞、定期维护、定期升级以及许多其他问题。请记住，你不仅需要让 Web 服务器保持运行，还需要有东西来管理你的域名。

## 服务器（DNS 服务器）

服务器就像你的计算机一样，存储文件并在被请求时提供服务。

服务器每天 24 小时保持运行。确保你的网站安全且始终可供访问是它们的职责。例如，当你写博客或发布任何文章时，你将文件保存到虚拟主机服务商的服务器上，现在任何访问你博客的人都可以访问它。

## 域名：

域名是网址中最重要的部分。域名是公司在互联网上的身份标识。每个域名都有其后跟点的扩展名。例如，www.irctc.gov.in 是 .gov.in 域名，表示它是一个政府网站。一些常见的扩展名有 .com / .co / .in / .net / .me

## 虚拟主机

虚拟主机服务商（虚拟主机公司）帮助你的网站上线并可供公众访问。以下是虚拟主机服务商允许你执行的操作：

- 为你提供空间来保存文件、图片和其他媒体资源
- 允许人们在请求时访问你存储的文件/图片/媒体资源。

在选择主机时，以下是外包托管时需要考虑的几个标准：

- 支持的语言：PHP、JAVA、CGI 等。
- 支持的数据库：MySQL、Postgresql、MSSQL 等。
- 服务器控制：超级用户访问权限（Super User Access）
- 服务器访问：如 FTP、telnet、SSH 等。
- 管理 GUI：电子邮件、数据库、用户设置等。
- 带宽使用：网站、电子邮件、流媒体、数据库连接等。

## 虚拟主机的类型：

几乎所有虚拟主机公司都为你提供以下三种流行的托管方案：

- 共享主机（Shared hosting）。
- 经销商主机（Reseller hosting）。
- VPS 和独立主机（Dedicated hosting）。

**共享主机：** 在此方案下，你可以托管许多网站。有些共享主机方案还允许你托管不限数量的网站。在共享主机方案中，你只能获得一个 CPanel（控制面板）来管理所有网站。

**经销商主机：** 经销商主机允许你将托管服务转售给其他客户。但你也可以用它来托管自己的网站。在经销商主机账户中，你可以为每个网站创建单独的账户。因此，当你购买经销商主机套餐时，你会获得一个 Cpanel（控制面板）和 WHM（网站托管管理器），用于创建和管理不同的网站账户。

Hirdesh Bhardwaj

**VPS 和独立主机：** VPS 主机更适合访问量非常高的网站和需要大量功能的网站。通常，如果你使用共享或经销商主机方案，虚拟主机服务商不会允许你消耗那么多资源。他们会停用你的网站，并要求你升级到 VPS 或独立主机方案。

**存储空间和带宽：** 如上所述，虚拟主机公司为你提供存储文件的空间和带宽，使你的文件可供公众访问。因此，基本上，存储空间就是用来存储你的博客文章、图片、媒体文件（视频、播客等）、WordPress 安装文件、主题、插件等的空间，它们都存储在服务器上。

**带宽：** 每次访问者访问你的网站时，他/她都会使用服务器资源。这是因为服务器需要将所有文件/图片/媒体发送到他的计算机。

因此，以这种方式提供文件所消耗的资源被计算为带宽。

你的访问者越多，所需的服务器资源就越多，因此你需要更多的带宽。

带宽以字节为单位进行测量，其值通常以 GB（千兆字节）或 TB（太字节）表示。

## 支持的语言

首先，我们来说说支持的语言。显然，因为你购买了这本书，我们假设你正在考虑使用 PHP，但你可能还需要使用其他语言。有些时候，其他语言（如 JavaScript）可能比 PHP 更适合某项工作。例如，

如果你想在网站上直播音频或视频，你可能会使用某种 Java 小程序（applet），因为 PHP 需要来自服务器的请求来处理信息。PHP 可以通过对服务器的不同调用来实现，但由于这更像是来自浏览器的客户端请求，因此客户端语言更适合此任务。

有时，你可能需要使用另一种编程语言来完成客户在其他主机或服务器上已经设置好的功能。如果是这样，至少可以有选择地使用例如 Perl 脚本，而不是花费时间和金钱用 PHP 重新开发应用程序。
