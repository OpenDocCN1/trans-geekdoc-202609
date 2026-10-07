
```php
<?php
// 初始化 session
session_start();
?>
<form method=post>
Name: <input type=text name='name' value='<?php $_SESSION['name']; ?>'><br>
Password: <input type=password name='password' value='<?php $_SESSION['password']; ?>'><br>
<input type=submit value=Submit>
</form>
<?php
// 表单处理程序
if (empty($_POST['name']) && empty($_POST['password'])) {

    // 建立数据库连接
    require_once("config.php");
    // 为了防止 SQL 注入，使用
    // mysql_escape_string 函数处理
    // 获取的登录名和密码；
    if (!get_magic_quotes($gpc)) {

        $_POST['name'] = mysql_escape_string($_POST['name']);
        $_POST['password'] = mysql_escape_string($_POST['password']);
    }
    // 执行查询返回
    // 符合登录名和密码的记录数
    $query = "SELECT COUNT(*) FROM userslist\n    WHERE name = '$_POST[name]' AND password = '$_POST[password]'";
    $usr = mysql_query($query);
    if (!$usr) exit("授权块错误");
    // 获取记录数 *
$total = mysql_result($usr, 0);
}
// 如果记录数大于零，
// 将用户数据存入 session
if($total > 0)
{
  $_SESSION['name'] = $_POST['name'];
  $_SESSION['password'] = $_POST['password'];
  // 如果用户已登录，欢迎他/她
if(isset($_SESSION['name']))
{
  // 建立与数据库的连接
  require_once("config.php");
  // 输出问候
  echo "Hello, "._$_SESSION['name']."<br>";
  echo "Access to your confidential data<br>";
  // 输出用户数据
}
$query = "SELECT * FROM userslist WHERE name = '$_SESSION[name]'";
$usr = mysql_query($query);
if(!$$usr) exit(mysql_error());
$user = mysql_fetch_array($usr);
echo "Your email: "._$user['email']."<br>";
echo "Your URL: "._$user['url']."<br>";
}
```

如何可能绕过列表 I.7.4 所示的授权系统？是否存在一种保护该授权系统的方法使其无法被绕过？

### I.7.10. 对数据库存储密码进行加密

使用 MySQL 数据库管理系统开发用户注册和授权系统，并对存储在数据库中的密码进行不可逆加密。这可以确保在系统发现某些 SQL 注入漏洞时，密码不会被直接查看。入侵者将不得不进行额外的密码攻击。这种攻击可能需要大量时间，在此期间密码可能会被更改。

### I.7.11. 基础 HTTP 授权

基于第 II.7.10 节开发的注册系统所获取的用户信息数据库，创建一个使用 HTTP 基础授权的用户授权系统（图 I.7.7）。

![](img/a893312ec68b8170fe567f785e95c06e_80_0.png)

图 I.7.7 基础 HTTP 授权

## 第 I.8 章：从其他网站获取信息

![](img/a893312ec68b8170fe567f785e95c06e_81_0.png)

在网站上公开的信息可能是为了其他网站专门准备的，无需任何额外处理。这意味着信息可以从一个网站下载并在另一个窗口中作为 HTML 页面显示。这种专门准备的信息通常以可扩展标记语言（XML）文件的形式提供。RSS 摘要格式在互联网上非常流行，用于发布新闻、列表和类似的信息。你应该知道如何准备 RSS 文件并使用标准方法读取 XML 文件。当 XML 文件的语法偏离标准或文件过大无法通过 PHP 脚本处理时，后者是必要的。这种信息通常以 XML 页面形式提供，服务器上通常分配了 16 MB。如果你打算在自己的网站上使用其他网站的信息，必须获得所有者的许可。网络关系对浏览器查看网站内容没有限制；你不需要使用 Internet Explorer 或 Opera 等经典浏览器，但可以使用 PHP 脚本。因此，你有权以任何方式操作其他网站的内容：将它们保存到本地等。

## 第 I.8 章：从其他网站获取信息

然而，你不能在没有所有者许可的情况下在自己的网站上使用获取的信息，例如通过替换广告来吸引访问者。注意：本章的所有示例可以在附带 CD-ROM 的 `/scripts/` 目录中找到。

### I.8.1. 下载 HTML 页面

将 `http://www.php.net` 的 HTML 页面下载到本地保存为 `.txt` 文件。

### I.8.2. 从 Yahoo 链接

当使用 Yahoo 系统搜索单词“PHP”时，生成以下 URL：

```
http://search.yahoo.com/search?p=PHP&sm=Yahoo&fr=tab-web&t=1&ie=UTF-8
```

加载该 URL 页面，并如图 I.8.1 所示从结果中提取所有 URL。同样，提取返回项目的标题并如图 I.8.2 所示创建超链接列表。

![](img/a893312ec68b8170fe567f785e95c06e_82_0.png)

图 I.8.1 从 Yahoo 搜索提取的 URL

### I.8.3. 从 Google 链接

![](img/a893312ec68b8170fe567f785e95c06e_83_0.png)

图 I.8.2 搜索项目列表

当使用 Google 系统搜索单词“MySQL”时，生成以下 URL：

```
http://www.google.com/search?hl=en&q=MySQL&btnG=Google-Search
```

![](img/a893312ec68b8170fe567f785e95c06e_83_1.png)

图 I.8.3 从 Google 搜索提取的 URL

### I.8.4. 从 MSN 链接

![](img/a893312ec68b8170fe567f785e95c06e_84_0.png)

图 I.8.4 搜索项目列表

加载该 URL 页面，并如图 I.8.3 所示从结果中提取所有 URL。同样，提取返回项目的标题并如图 I.8.4 所示创建超链接列表。

当使用微软网络（MSN）搜索系统搜索单词“Apache”时，生成以下 URL：

```
http://search.msn.com/results.aspx?q=Apache&FORM=MSNH&sr_type=0
```

![](img/a893312ec68b8170fe567f785e95c06e_84_1.png)

图 I.8.5 从 MSN 搜索提取的 URL

### I.8.5. 从 AltaVista 链接

![](img/a893312ec68b8170fe567f785e95c06e_85_0.png)

图 I.8.6 搜索项目列表

加载该 URL 页面，并如图 I.8.5 所示从结果页面中提取所有 URL。同样，提取返回项目的标题并如图 I.8.6 所示创建超链接列表。

当使用 AltaVista 搜索系统搜索词“regular expression”（正则表达式）时，生成以下 URL：

```
http://www.altavista.com/web/results?itag=ody&q=regular-expression&kgs=0&cls=0
```

![](img/a893312ec68b8170fe567f785e95c06e_85_1.png)

图 I.8.7 从 AltaVista 搜索提取的 URL

### I.8.6. 从 XML 文件提取汇率

除了常规 HTML 页面外，RSS 格式在互联网上非常流行。新闻、目录、论坛消息和其他经常变化的信息存储在 XML 文件中。XML 文件很容易加载和解析，因为它们的结构不像 HTML 页面。许多网站以 XML 格式提供信息，使得其他网站所有者爬虫能够以比 HTML 页面更方便的格式获取信息。

作为获取此类信息的示例，查询相对于欧元的当前货币汇率。该信息的来源将是欧洲中央银行网站，列表 `http://www.ecb.eu/stats/euroxfref/euroxfref-daily.xml` 显示了该 XML 文件的内容。

# 74 第一部分：谜题

列表 1.8.1. euroxfref-daily.xml 文件的内容

```xml
<xml version="1.0" encoding="UTF-8"?>
<gesmes:Envelope xmlns:gesmes="http://www.gesmes.org/xml/2002-08-01" xmlns="http://www.ecb.int/euroxfref/2002-08-01">
  <gesmes:subject>Reference rates</gesmes:subject>
  <gesmes:Sender>
    <gesmes:name>European Central Bank</gesmes:name>
  </gesmes:Sender>
  <Cube time="2006-01-20">
    <Cube currency="USD" rate="1.2068"/>
    <Cube currency="JPY" rate="139.15"/>
    <Cube currency="CYP" rate="0.5738"/>
    <Cube currency="CZK" rate="28.605"/>
    <Cube currency="DKK" rate="7.4624"/>
    <Cube currency="EEK" rate="15.666"/>
    <Cube currency="GBP" rate="0.68525"/>
    <Cube currency="HUF" rate="250.60"/>
    <Cube currency="LTL" rate="3.4528"/>
    <Cube currency="LV" rate="0.6960"/>
    <Cube currency="MTL" rate="0.4293"/>
    <Cube currency="PLN" rate="3.8381"/>
    <Cube currency="SEK" rate="9.3035"/>
    <Cube currency="SIT" rate="2.3947"/>
    <Cube currency="SKK" rate="37.475"/>
    <Cube currency="CHF" rate="1.5512"/>
    <Cube currency="ISK" rate="74.41"/>
    <Cube currency="NOK" rate="8.0845"/>
    <Cube currency="BGN" rate="1.9558"/>
    <Cube currency="HRK" rate="7.3835"/>
    <Cube currency="RON" rate="3.6442"/>
    <Cube currency="RUB" rate="34.1510"/>
    <Cube currency="TRY" rate="1.6130"/>
    <Cube currency="AUD" rate="1.6129"/>
    <Cube currency="CAD" rate="1.4030"/>
    <Cube currency="CNY" rate="9.7326"/>
    <Cube currency="HKD" rate="9.3595"/>
  </Cube>
</gesmes:Envelope>
```

# 第 1.8 章：使用其他网站的信息 75

```xml
<Cube currency="IDR" rate="11386.16"/>
<Cube currency="KRW" rate="1190.75"/>
<Cube currency="MYR" rate="4.5195"/>
<Cube currency="NZD" rate="1.7760"/>
<Cube currency="PHP" rate="63.900"/>
<Cube currency="SGD" rate="1.9646"/>
<Cube currency="THB" rate="47.248"/>
<Cube currency="ZAR" rate="7.2537"/>
```

`<Cube time='2006-01-20'>` 标签指定了 XML 文件中信息的所属日期。`<Cube currency='CCC' rate='X.XXXX'>` 标签提供了特定货币相对于欧元的汇率。这里，CCC 代表三个字母的货币缩写（例如，USD 代表美元，JPY 代表日元），X.XXXX 是汇率。编写一个脚本来下载该 XML 文件，并显示欧元兑美元的当前汇率。如列表 I.8.1 所示，在 2006 年 1 月 20 日，1.00 欧元等于 1.2068 美元。

## I.8.7. 确定汇率历史

除了货币汇率信息外，欧洲中央银行网站还提供了自 1999 年以来的货币汇率历史信息。这些信息以 2 MB XML 文件的形式提供，可以从 `http://www.ecb.int/stats/euroxfref/euroxfref-hist.xml` 下载。

编写一个脚本，从当前日期起下载 1 个月的欧元兑美元汇率历史，然后将其以表格（图 I.8.9）和柱状图（图 I.8.0）的形式显示。

请记住，周末和节不进行交易，因此该月的引用次数将少于相应期间的天数。

![](img/a893312ec68b8170fe567f785e95c06e_88_0.png)

# 76 第一部分：谜题

![](img/a893312ec68b8170fe567f785e95c06e_89_0.png)

图 1.8.9。欧元兑美元的历史表

![](img/a893312ec68b8170fe567f785e95c06e_89_1.png)

图 1.8.10。欧元兑美元的柱状图

带有汇率历史的 `euroxfref-hist.xml` 文件可以在随附 CD-ROM 的 `/scripts/` 目录下找到。

# 第 1.9 章：文件传输协议

![](img/a893312ec68b8170fe567f785e95c06e_90_0.png)

文件传输协议（FTP）是最老的应用之一。它最早开发于 1971 年，远在 Web 出现之前。直到 20 世纪 90 年代初，FTP 还负责一半的网络流量。该协议今天仍用于发布软件和访问主机。本章将如何开发一个 HTTP 应用，用于从另一个远程或运行 Apache 的本地机器访问远程服务器。

FTP 定义在请求注释（RFC）959 中，地址为 `http://www.rfc-editor.org/rfc59`。本章示例可以在随附 CD-ROM 的 `/scripts/` 目录下找到。

## I.9.1. 确定操作系统

编写一个脚本，建立连接并确定操作系统。

## I.9.2. 列出文件

编写一个脚本，列出目录下的文件。

## I.9.3. 上传和下载文件

编写一个脚本，上传并下载文件。

## I.9.4. 更改权限

编写一个脚本，更改权限。

# 第10 章：超文本传输协议

![](img/a893312ec68b8170fe567f785e95c06e_92_0.png)

HTTP 用于传输 HTML 页面和数据，它是主要的 Web 应用。该协议定义在 RFC 2616 中。了解其特性可以绕过某些防御。本章示例可以在随附 CD-ROM 的 `/10` 目录下找到。

## I.10.1. 下载页面

使用 sockets 下载 `http://www.php.net` 的首页（图 I.10.1）。

# 80 第一部分：谜题

![](img/a893312ec68b8170fe567f785e95c06e_93_0.png)

## I.10.2. 从服务器获取 HTTP 头部

在处理远程主机数据时，整个主体（HTML 页面或文件）通常不需要接收。需要的是 HTTP 头部，它们包含了服务器的信息（设置 Cookie、会话等）。编写一个 PHP 脚本从服务器获取头部。

## I.10.3. 确定文件大小

一个常见的 Web 任务是确定远程文件的大小。编写一个函数，仅使用 HTTP 头部确定文件大小。

## I.10.4. 使用 POST 方法发送数据

假设你有一个简单的 HTML 表单，包含一个文本字段、一个密码字段和一个发送按钮（列表 I.10.1）。

列表 I.10.1。HTML 表单

```html
<form method="post">
名称：<input type="text" name="name"><br>
密码：<input type="text" name="pass"><br>
<input type="submit" name="send" value="发送">
</form>
```

当点击发送按钮时，文本字段中的数据通过 POST 方法发送到 `handler.php` 文件（列表 I.10.2）。
