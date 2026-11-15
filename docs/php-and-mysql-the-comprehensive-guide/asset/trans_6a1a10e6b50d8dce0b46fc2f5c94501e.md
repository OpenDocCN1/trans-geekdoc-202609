

## 第三部分

### Web 技术

文件 vendor/laminas/laminas-db/src/Adapter/Adapter.php 说明了此工作原理。以下是摘录：

```php
$driverName = strtolower($parameters['driver']);
switch ($driverName) {
    case 'mysqli':
        $driver = new Driver\Mysqli\Mysqli($parameters, null, null, $options);
        break;
    // ...
    case 'pdo':
    default:
        if ($driverName === 'pdo' || strpos($driverName, 'pdo') === 0) {
            $driver = new Driver\Pdo\Pdo($parameters);
        }
}
```

因此，Driver\Pdo\Pdo 驱动程序是在我们的代码未显式请求甚至未知晓该类的情况下创建的。严格来说，这不是工厂，因为未使用工厂方法，但原理显而易见（且可比较）。

此适配器将用于现有的 MVC 应用程序。首先，有必要安装 laminas-db 包。为此，请直接在项目目录中执行以下命令：

composer require laminas/laminas-db

随后，系统将询问您是否要在配置中保存新包（参见图 12.7）。默认答案 `1` 是个不错的选择。之后，您可以从应用程序访问 Laminas\Db。

![](img/ae7820c36e8f24c1623d26668b28e80e_393_0.png)

图 12.7 安装 laminas-db

> **注意**
> 截至出版时，laminas-db 仅与 PHP 8.0 至 8.2 版本兼容，因此我们无法使用 PHP 8.3 复制以下步骤。

回到实际实现。适配器用于执行以下操作：

- 1. 在内存中创建 SQLite 数据库。
- 2. 创建表。
- 3. 用六个随机数填充表。
- 4. 读取这六个随机数。
- 5. 删除表。

前提是在 php.ini 中启用 pdo_sqlite 扩展（第 18 章将详细介绍）。以下清单包含完整代码，直接添加到上一示例的模型文件中。

```php
<?php
namespace Application\Model;

class HelloWorld {
public $numbers;

function __construct() {
$numbers = [];

$db = new \Laminas\Db\Adapter\Adapter(
[
"driver" => "Pdo_Sqlite",
"database" => ":memory:",
]
);

$db->query(
'CREATE table numbers (number INTEGER)',
\Laminas\Db\Adapter\Adapter::QUERY_MODE_EXECUTE);

for ($i = 0; $i < 6; $i++) {
$db->query(
'INSERT INTO numbers (number) VALUES (?)',
[rand(1, 49)]);
}

$stmt = $db->query('SELECT * FROM numbers');
$rows = $stmt->execute();
foreach ($rows as $row) {
    array_push($numbers, $row['number']);
}

$db->query(
    'DROP TABLE numbers',
    \Laminas\Db\Adapter\Adapter::QUERY_MODE_EXECUTE
);

$this->numbers = $numbers;
}
?>
```

清单 12.5 适配器模式（"module/Application/src/Model/HelloWorld.php"）

现在只需更新视图。数字列表将快速按数值排序，然后用逗号分隔输出。

```php
<div id="welcome">
<h1>Hello world!</h1>

<p>Your personal lucky numbers are: <b>
<?php
$numbers = $this->data->numbers ?? [];

usort(
    $numbers,
    function ($a, $b) {
        return $a - $b;
    }
);

echo implode(", ", $numbers);
?>
</b></p>
</div>
```

清单 12.6 已更新的视图（"module/Application/view/application/hello-world/index.phtml"）

您可以在图 12.8 中看到最终结果。数据库中的随机数已传输到视图并在那里排序。

![](img/ae7820c36e8f24c1623d26668b28e80e_396_0.png)

图 12.8 数据库中的随机数（在主内存中创建）

四人帮（Gang of Four）之一的 Erich Gamma 曾报道过一篇新闻组帖子，其中作者非常沮丧，因为他只使用了 Gamma 及其同事著作中 23 种设计模式中的 20 种。在使用模式时，务必兼顾务实精神与批判性审查。然而，若使用得当，模式可以提高软件的可维护性和质量。

## 第 13 章

### 表单

表单是网站访问者与网站本身进行某种形式通信的重要方式，若非最重要方式也是如此。足以深入了解 PHP 的控制。

在学习 HTML 时，表单通常扮演着相当次要的角色。在培训课程中我们也注意到这一点：参与者通常对 HTML 有深入了解，但如果询问表单元素的具体细节，往往会看到困惑的面孔。

这引发两个问题：为什么 HTML 表单通常不被视为非常重要，以及为什么我们在本章（非常详尽的章节）中对这一主题如此重视？

答案已在引言中给出：表单用于网站访问者与网站本身之间的通信。否则，通信仅限于点击链接，这当然不太令人兴奋。不过，通过表单，用户可以输入数据，随后可在服务器端进一步处理。

本章展示了如何实现这一点。同时，它还解释了可能出现的风险、需要注意的事项以及可用的特殊应用。检查表单数据也很重要（例如，是否填写了所有字段？）。所有这些在实践中非常常见，但有时在文献中被忽略。在本章中，您将获得完整的方案。

但是，为什么 PHP 等服务器端技术对表单处理如此重要？答案是：由于 HTML 和 JavaScript 的可能性有限，如果没有 PHP（或竞争技术），就无法处理数据。

### 13.1 准备工作

PHP 表单支持不需要任何安装。然而，所必需的是对 HTML 表单元素的基本了解。本章大多数示例将围绕一个非常具体的示例表单展开，您可以在其中订购重大体育赛事的门票。门票买得早一点永远不为过：下次一定会更好。许多相关的表单元素出现在这个表单中——无论是巧合还是故意。该表单在以下清单中。

```html
<html>
<head>
<title>Order Form</title>
</head>
<body>
<h1>World Cup Ticket Service</h1>
<form>
<input type="radio" name="Salutation" value="Mr. " />
Mr.
<input type="radio" name="Salutation" value="Ms. " />
Ms. <br />
First name <input type="text" name="FirstName" /><br />
Last name<input type="text" name="LastName" /><br />
Email address <input type="text" name="Email" /><br />
Promo code <input type="password" name="Promo" /><br />
Number of tickets
<select name="Number">
<option value="0">Please select</option>
<option value="1">1</option>
<option value="2">2</option>
<option value="3">3</option>
<option value="4">4</option>
</select><br />
Desired section in the stadium
<select name="Section[]" size="4" multiple="multiple">
<option value="north">North</option>
<option value="south">South</option>
<option value="east">East</option>
<option value="west">West</option>
</select><br />
Comments/Notes
<textarea cols="70" rows="10" name="Comments"></textarea><br />
<input type="checkbox" name="Terms" value="ok" />
I accept the terms &amp; conditions.<br />
<input type="submit" name="Submit" value="Place order" />
</form>
</body>
</html>
```

清单 13.1 订单表单——尚未使用 PHP（"form.html"）

在本章中，此表单（参见图 13.1）将逐步扩展，每个中间步骤均作为单独文件在本书的在线材料中提供。首先，我们读取表单中的数据，然后转向更高级的任务，例如检查输入的数据。

![](img/ae7820c36e8f24c1623d26668b28e80e_401_0.png)

图 13.1 原始表单

表 13.1 对所使用的表单元素进行了简要概述，包括预分配选项（这在以后进行表单验证时是必要的）。

| HTML 元素 | 描述 | 预分配 |
|---|---|---|
| `<input type="text" />` | 单行文本字段 | `value="value"` |
| `<input type="password" />` | 单行密码字段 | `value="value"` |
| `<textarea></textarea>` | 多行文本字段 | 介于 `<textarea>` 和 `</textarea>` 之间 |
| `<input type="radio" />` | 单选按钮 | checked 属性 |
| `<input type="checkbox" />` | 复选框 | checked 属性 |
| `<select><option></option></select>` | 选择列表 | selected 属性 |
| `<input type="submit" />` | 发送按钮 | 不适用 |

表 13.1 所用表单元素概述

