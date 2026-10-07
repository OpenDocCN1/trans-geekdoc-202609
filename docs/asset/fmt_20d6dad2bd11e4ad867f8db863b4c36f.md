
```php
echo '</table>';
echo '</tr>';
echo '</table>';
?>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_282_0.png)

图 7-99：显示当日的详细信息。

# 第 35 节：比较日期

## 目标
在本节中，你将学习如何使用 FileMaker 与 PHP 比较日期。早晚你都会需要显示通过日期过滤或某种类型比较的记录，以做出分支决策。例如，仅显示日期大于今天的相关记录计划。你们中的大多数人可能想：这很简单，我只需在数据库布局上对门户进行过滤，并使用 `setRelatedSetsFilters` 来过滤显示，这将会轻而易举。问题在于，在编写本节时，`setRelatedSetsFilters` 函数无法工作。因此，你将创建一个带有额外字段的特定发生（TOG），然后编写权限集（Privilege Set）来过滤记录，或者在你的 PHP 代码中执行日期比较。这两者各有优劣。额外的 TOG 意味着你的 PHP 站点增加了不必要的负担。权限集与使用门户过滤器对话框无区别。所有记录都会返回给你，而哪些记录是由 FileMaker 引擎控制的。因此，服务器上的负载与你发送所有记录一样。问题是，权限集会在每个布局上的任何时候过滤所有记录，而不仅仅是你的特殊 PHP 页面上的一个门户。因此，减少负担的唯一合理选择是在你的 PHP 页面上编写日期比较，以保持数据库尽可能整洁。本节将向你展示在 FileMaker 与 PHP 中比较日期的几种不同方法（以及陷阱）。

**难度：** 简单

**示例文件：**

- `PHPFiles/Advanced/Lesson35/CompareDates.php`
- `PHPFiles/Advanced/Lesson35/CompareDates.fp12`

| 此处使用独立的数据库文件来演示课程。请将 `CompareDates.fp12` 数据库文件上传到你的服务器 |
| :--- |

**页面导航：** N/A

**FileMaker API 方法：**

- `newFindAllCommand()`
- `execute()`
- `getFirstRecord()`
- `getField()`

### 代码

从连接数据库开始。

```html
<html>
<body>
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'CompareDates');
$fm->setProperty('hostspec', 'http://127.0.0.1');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>?>
```

我没有在这个示例中对数据进行任何特殊处理以显示数据。目标是比较日期并显示结果，以便你可以看到哪些方法有效，哪些方法存在问题。因此，我只显示表格中的第一条记录并将结果返回给 `$record` 变量。

```php
$request = $fm->findAllCommand('Demo');
$result = $request->execute();
$record = $result->getFirstRecord();
```

第一个示例比较了 FileMaker 内部的两个日期字段。这种直接从数据库比较日期的方法按预期工作，并将做出正确的判断并显示正确的结果。

```php
if($record->getField('Date1') < $record->getField('Date2')) {
    echo 'Date1: ' . $record->getField('Date1') . ' < Date2: ' . $record->getField('Date2');
} elseif ($record->getField('Date1') > $record->getField('Date2')) {
    echo 'Date1: ' . $record->getField('Date1') . ' > Date2: ' . $record->getField('Date2');
} else {
    echo 'Date1: ' . $record->getField('Date1') . ' = Date2: ' . $record->getField('Date2');
}
```

第二个示例比较了 FileMaker 内部的两个日期字段。这种直接从数据库比较日期的方法按预期工作，并将做出正确的判断并显示正确的结果。

秒数（自 1970 年 1 月 1 日 Unix 纪元）。

```
$today = date('U', strtotime($record->getField('Date')));
$date = date('U', strtotime($record->getField('Date2')));
If($today <= $date) {
    echo $today . "<" . $date;
} else {
    echo $today . ">" . $date;
}
?>
<body>
</</html>
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_286_0.png)

图 7-100：比较日期的五种方法。

# 第 36 节：使用 PHP 显示 HTML/CSS

**目标：** 在节中，你将学习如何显示存储在字段中的 HTML/CSS。对于使用 PHP 将数据发布到网络上的用户，你最终会遇到显示存储在字段中的 HTML 或 CSS 内容的需求。例如，你可能有一个购物车，其中所有的卡都存储在你的产品表中（如我们的产品 Pay eCommerce Pro），或者你可能想允许用户输入样式化文本，并使其在网页上正确显示，而无需用户了解任何 HTML 或 CSS 标签知识。

**难度：** 简单

**示例文件：**

`PHPFiles/Advanced/Lesson36/DisplayHTMLCSSUsingPHP.php`

`PHPFiles/Advanced/Lesson36/DisplayHTMLCSSUsingPHP.fmp12`

> 本节使用单独的数据库文件进行演示。请将 `DisplayHTMLCSSUsingPHP.fmp12` 数据库文件上传到你的服务器。

**页面导航：**

- - 列表

**FileMaker API 方法：**

`newFindAllCommand()`

`execute()`

`getFirstRecord()`

`getField()`

### 代码

从连接数据库开始。

```html
<<body>
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'DisplayHTMLCSSUsingPHP');
$fm->setProperty('hostspec', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>
</body>
```

滚动到代码底部，其从以下代码开始：

```
echo '<td>' . html_entity_decode($record->getField('Text')) . '</td>';
```

| `html_entity_decode(string)`: 将所有 HTML 实体转换为其相应的字符。 | http://us.php.net/manual/function.html-entity-decode |

你注意到的是使用了 PHP 函数 `html_entity_decode()`。该函数的作用是将所有 HTML 实体转换为相应的字符，并按预期显示来自 `Text` 字段的 HTML 和 CSS。如果你在编写普通的 FileMaker for PHP 代码时省略此函数，你将获得字段的“原样”内容，而没有任何 HTML 或 CSS 格式化效果。这意味着 HTML 和 CSS 标签将以原始文本的形式显示。当你将浏览器中的示例网页与数据库中的内容进行比较时，就能看到区别。

```php
echo '<td>' . $record->getField('Text') . '</td>';
```

FileMaker API 还有 `getFieldUnencoded()` 函数，它可以返回未编码的字段内容。然而，它没有将特殊字符转换为 HTML 实体的功能。

```php
echo '<td>' . $record->getFieldUnencoded('Text') . '</td>';
```

![](img/5a2c5fda68d42e5d65f51850276e49ec_288_0.png)

当你需要使用 PHP 和 FileMaker 编码/解码特殊字符时，可能会发现以下函数有用：

- `html_entity_decode()` — 将所有 HTML 实体转换为其相应的字符 http://us3.php.net/manual/en/function.html-entity-decode.php
- `htmlentities()` — 将所有相应的字符转换为 HTML 实体 http://www.php.net/manual/en/function.htmlentities.php
- `htmlspecialchars()` — 将特殊字符转换为 HTML 实体 http://www.php.net/manual/en/function.htmlspecialchars.php
- `htmlspecialchars_decode()` — 将特殊的 HTML 实体转换回字符 http://www.php.net/manual/en/function.htmlspecialchars-decode.php

所有 PHP 字符串函数 http://www.php.net/manual/en/ref/strings.php

## 第 36 节：使用 PHP 显示 HTML

| 解码后 | 原始文本 |
|---|---|
| 输入到字段中时将显示这段纯文本。 | 输入到字段中时将显示这段纯文本。 |
| 注意，你在 FileMaker 中应用的格式不会转换为 PHP 网页 | 注意，你在 FileMaker 中应用的格式不会转换为 PHP 网页。。 |
| 以下是如何为网页对字段中的数据进行格式化的下一记录和 | 以下是如何为网页对字段中的数据进行格式化的下一记录和 |

DisplayHTMLUsingPHP 示例网页

如果你需要包含 HTML 标签或 CSS 样式，使用 `html_entity_decode()`

未编码文本

输入到字段中时将显示这段纯文本。注意你在 FileMaker 中应用的格式不会转换为 PHP 网页。以下是如何为网页对字段中的数据进行格式化的下一记录。

DisplayHTMLUsingPHP 示例网页

如果你需要包含 HTML 标签或 CSS 样式，使用 `html_entity_decode()`

FileMaker 的一个特殊功能是你可以提供一个 CSS 脚本来为用户转换 CSS。你还可以使用计算，这可以让你在网页上使用计算时确保格式按预期显示。

```
<span style="font-size:14px;font-weight:bold;">html_entity_decode(Text)</span>
```

它是相当准确的，它使用脚本为用户转换 CSS。

通过产品表进行计算或查找链接，并将其与 `RandomKey` 值组合以完成完整的 URL 链接。最后，通过电子邮件将链接发送给客户。

**ExpirationDate** 字段用于使链接失效。在创建记录时，该字段会输入当前日期加 30 天。如果客户在过期后尝试下载文件，PHP 代码将阻止其下载文件。

**IPAddress** 字段可以用于仅允许单个用户下载文件。这可以防止用户将链接分享给其他人，或防止链接缓存在服务器引擎上，导致你的产品免费提供给所有人！在测试时需要注意的是，本地（localhost）服务器的 IPv6 地址将返回为 "::"。这在 IPv4 网络上等同于 127.0.0.1。因此，当你在测试解决方案时，看起来可能有点奇怪。在 PHP 代码中，我添加了一个可选部分，你可以取消注释以通过代理服务器获取用户的真实 IP 地址。

**DownloadAttempts** 字段用于跟踪用户点击链接下载文件的次数。如果你能跳出常规思维，你可以重置链接，你会发现你也可以使用此文件和技术来报告你网站的使用统计数据。

**FileName** 字段是用户允许下载的文件。在本例中，使用一个名为 "downloads" 的文件夹，我将所有文件存储在那里。在完整的工作模型中，客户创建新记录后，其看起来将像产品表中的这个文件。

你可能认为这个过程很复杂；你必须为 URL 生成加密密钥，必须创建带有特定名称的新文件，然后在下载后删除它们，文件本身需要某种奇特的安全类型等。事实是，这并不复杂，你可以看到这个过程是如何工作的。最复杂的部分是识别你需要为客户实现的组件。数据库字段和 PHP 代码并不十分复杂。那么，让我们开始编写 PHP 代码吧：

首先连接到数据库。

```php
<html>
<body>
<?php
require_once ('FileMaker.php');
$fm = new FileMaker();
$fm->setProperty('database', 'ExpireLink');
$fm->setProperty('hotscape', 'http://127.0.0.1/');
$fm->setProperty('username', 'Admin');
$fm->setProperty('password', '1234');
?>
```

当用户点击电子邮件中的链接时，你的代码需要做的第一件事是使用 URL 中传递的 `RandomKey` 在数据库中查找记录。如果记录已被删除，你可以停止脚本。如果你找到了匹配的记录，就可以处理脚本的其余部分。

```php
$randomKey = $_GET['RandomKey'];
$request = $fm->newFindCommand('demo');
$request->addFilter('RandomKey', $randomKey);
$result = $request->execute();
if(FileMaker::isError($result)) {
    echo "Your key no longer exists.";
    exit;
} else {
?>
```

如果记录存在，你可以将字段值存储为变量，以便处理脚本的其余部分。以防万一你需要更新 `recordID` —— 这是 FileMaker 记录的内部 ID。FileMaker 根据此数字更新记录，而不是根据你自动生成的序列号。我们还需要将 PHP 日期转换为 FileMaker 格式（MM/DD/YYYY）。为了获取用户的远程地址，我们将使用 PHP 的 `$_SERVER` 方法。在用户使用代理服务器掩盖其 IP 地址的所有情况下，这种方法都有效。我在网页中包含了获取此信息的可选代码：

```php
$record = $result->getFirstRecord();
$link = $record->getField('Link');
$expiringdate = $record->getField('ExpirationDate');
$ipaddress = $record->getField('IPAddress');
$downloadattempts = $record->getField('DownloadAttempts');
$recordid = $record->getRecordID();
$currentdate = date('m/d/Y');
$filename = $record->getField('FileName');
$remoteipaddress = $_SERVER['REMOTE_ADDR'];
```

现在我们已经拥有了所有信息的变量，可以开始评估客户下载文件的权限了。当客户第一次尝试时，如果伪造了 IPAddress 字段，该字段将为空。这是合理的，因为我们并不一定知道他们来自哪里。因此，如果 `$ipaddress` 为空，我们可以用客户当前的 IP 地址更新记录。这将查找该特定 IP 地址的下载。因此，没有人将能够通过提供的链接访问下载。之后，只需检查数据库中的 `IPAddress` 是否与客户当前的 IP 地址匹配即可继续：

```php
if(empty($ipaddress)) {
  $edit = $fm->newEdit('Demo', $recordid);
  $edit->addField('IPAddress', $remoteipaddress);
  $edit->execute();
}
```

```php
elseif($ipaddress != $remoteipaddress) {
  echo "You are not authorized to download this file";
  exit;
}
```

下一步是验证链接的过期日期。如果当前日期大于记录中的过期日期，你就可以运行脚本。或者，某些人可能会建议在此时立即删除记录以防止其被访问。然而，从客户服务的角度来看，我提醒你，让你的员工重置现有记录的过期日期要比这容易得多。

```php
if($currentdate > $expirationdate) {
  echo "This link has expired.";
  exit;
}
```

接下来，我们需要增加 `DownloadAttempts` 字段。
