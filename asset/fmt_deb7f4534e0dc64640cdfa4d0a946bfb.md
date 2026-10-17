
## 使用其他网站的数据 405

首先为该信息找到原始源 URL。当你知道该 URL 后，每当有人访问你的主页时，你都可以与该 URL 建立连接，获取页面并提取出你所需的信息。

例如，我们编写了一个脚本，从雅虎财经（Yahoo! Finance）网站获取并重新格式股票报价。该网站在每个股票报价页面上都提供一个“数据”（Data）链接，且所有代码的链接遵循相同的通用 URL 格式。为了示例演示，我们获取了谷歌（Google）的当前股票价格。（你想在你的页面上包含的信息可能不同，但原理是相同的。）

我们的示例脚本计算了另一个网站提供的数据并将其显示在我们的网站上。脚本如列表 18.1 所示。

### 列表 18.1 `lookup.php` 根据股票代码 `$symbol` 从 NASDAQ 获取股票报价

```php
<!DOCTYPE html>
<html>
<head>
<title>来自 NASDAQ 的股票报价</title>
</head>
<body>

<?php
//选择要查看的股票代码
$symbol = 'GOOG';
echo '<h1>Stock Quote for '.$symbol.'</h1>';

$url = 'http://download.finance.yahoo.com/d/quotes.csv?s='.$symbol.'&e=.csv&f=sild1t1clohogv';

if (!($contents = file_get_contents($url))) {
    die('Failed to open '.$url.'.');
}

// 提取相关数据
list($symbol, $quote, $date, $time) = explode(',', $contents);
$date = trim($date, " \t");
$time = trim($time, " \t");

echo '<p>'.$symbol.' was last sold at: '.$quote.'</p>';
echo '<p>Quote source as of '.$date.' at '.$time.'</p>';

// 确认来源
echo '<p>This information retrieved from <br /><a href="'.$url.'">'.$url.'."</a></p>';

?>
</body>
</html>
```

## 406 第 18 章 使用网络和协议函数

列表 18.1 的一次示例运行的输出如图 18.1 所示。

![](img/654520c37415debd4290b9b4aa2c03f2_437_0.png)

图 18.1 `lookup.php` 使用正则表达式从从股票交易所获取的信息中提取出股票报价

脚本本身相当直观；事实上，它没有使用你之前见过的任何函数，只是对那些函数的新应用。

```php
if (!($contents = file_get_contents($url))) {
```

### 列表 18.3 `directory_submit.php`–验证 URL 和邮箱地址的脚本

```php
<!DOCTYPE html>
<html
<head>
    <title>站点提交结果</title>
</head>
<body>
    <h1>站点提交结果</h1>

<?php

// 提取表单字段
$url = $_POST['url'];
$email = $_POST['email'];

// 检查 URL
$url_parts = parse_url($url);
$host = $url_parts['host'];

if (!($ip = gethostbyname($host))) {
    echo 'URL 的主机没有有效的 IP 地址。';
    exit;
}

echo '主机 ('.$host.') 位于 IP ''.$ip.'<br/>';

// 检查邮箱地址
$email = explode('@', $email);
$emailhost = $email[1];

if (!getmxr($emailhost,$mxhostsarr)) {
    echo '邮箱地址不在有效的主机上。';
    exit;
}

echo '邮箱通过以下方式投递： <br/>';
<ul>
foreach ($mxhostsarr as $mx) {
    echo '<li>'.$mx.'.</li>';
}
echo '</ul>';

// 如果到达此处，说明一切正常
echo '<p>所有提交的详情都是正确的。</p>';
echo '<p>感谢提交您的站点。\n我们的工作人员之一很快就会访问它。</p>';
// 在实际情况中，将其添加到等待站点的数据库中...
?>
</body>
</html>
```

让我们来看一下这个脚本中很有意思的部分。

首先，你从 `$_POST` 全局变量中获取 URL，并对其应用 `parse_url()` 函数。该函数返回一个包含 URL 不同组成部分的关联数组。可用的信息包括方案（scheme）、用户（user）、密码（pass）、主机（host）、端口（port）、查询（query）和片段（fragment）。通常，你不需要所有的部分，但这里有一个它们如何组成 URL 的示例。

考虑以下示例 URL：`http://nobody:secret@example.com:80/script.php?variable=value=anchor`。

数组中每个部分的值如下：

- scheme: http

- user: nobody

- pass: secret

- host: example.com

- port: 80

- path: /script.php

- query: variable=value

- fragment: anchor

在 `directory_submit.php` 脚本中，你只需要主机信息，因此你如下所示从数组中提取它：

```php
$url = parse_url($url);
$host = $url['host'];
```

完成此操作后，你可以获取主机 IP 地址（如果它在域名服务（DNS）中）。你可以通过 `gethostbyname()` 函数来实现此，如果存在则返回 IP，不存在则返回 false：

```php
$ip = gethostbyname($host);
```

你也可以通过使用 `gethostbyaddr()` 函数进行反向操作，该函数接受 IP 作为参数并返回主机名。如果你连续调用这些函数，最终得到的主机名可能与你开始时对应的不同。这可能意味着某个站点在使用虚拟托管服务，即一台物理机器和 IP IP 地址托管了多个域名。

如果 URL 是有效的，你将继续检查邮箱地址。首先，你通过调用 `explode()` 将其拆分为用户名和主机名：

```php
$email = explode('@', $email);
$emailhost = $email[1];
```

当你获得地址的主机端口后，可以使用 `getmxr()` 函数检查是否有邮件投递的地方：

```php
getmxr($emailhost,$mxhostsarr);
```

该函数在变量 `$mxhostsarr` 数组中返回了该地址的一组邮件交换（MX）记录。

MX 记录存储在 DNS 中，并作为主机名进行查询。MX 记录中列出的机器并不一定是邮件最终落脚的机器。相反，它是一台知道该将邮件路由（route）到何处的机器。（可能存在多个这样的机器；因此，此函数返回的是一个数组而不是主机名字符串）。如果你在 DNS 中没有 MX 记录，那么邮件将无处可去。

如果所有检查都通过，你可以将这些数据放入数据库中，供工作人员稍后查看。我们没有在这个脚本中实现具体的功能，但你可以在脚本末尾的注释中看到位置，将其用于快速检查有效性非常简单。

除了你刚刚使用的函数外，你还可以使用更通用的函数 `checkdnsr()`，它接受一个主机名，如果 DNS 中出现它的任何记录，则简单地返回 true。该函数的输出不会给你任何直接显示给用户的内容（就像脚本中使用的 `getmxr()` 函数那样），但对于快速检查有效性非常简单。

# 备份或镜像文件

文件传输（或 FTP）用于在网络上的主机之间传输文件。使用 PHP，你可以像使用 HTTP 连接一样使用 `fopen()` 和各种与 FTP 相关的函数，在 FTP 服务器之间和从中传输文件。然而，一组 FTP 特有的函数也随标准 PHP 安装一起提供。

这些函数默认没有内置在标准安装中。若要在 Unix 下使用它们，请运行带有 `--enable-ftp` 选项的 PHP 配置程序，然后重新运行 make。如果你使用的是 Windows 安装版，FTP 函数是自动启用的。

关于配置 PHP 的更多细节，请参见附录 A。

使用 FTP 备份或镜像文件

文件传输（或 FTP）用于在网络上的主机之间传输文件。使用 PHP，你可以像使用 HTTP 连接一样使用 `fopen()` 和各种与 FTP 相关的函数，在 FTP 服务器之间和从中传输文件。然而，一组 FTP 特有的函数也随标准 PHP 安装一起提供。

这些函数默认没有内置在标准安装中。若要在 Unix 下使用它们，请运行带有 `--enable-ftp` 选项的 PHP 配置程序，然后重新运行 make。如果你使用的是 Windows 安装版，FTP 函数是自动启用的。
