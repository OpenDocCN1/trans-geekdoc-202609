
在编程的早期，由于可用的程序代码内存有限，我们无法奢侈地充分命名函数。我记得自己坐在地板上，面对一摞摞打印出来的代码，试图解读名为 `x` 和 `y` 的函数含义，就像在使用秘密解码环一样。如今，没有理由不给函数起个好名字。

你希望函数的命名完整而简洁，因为这会让你的代码具有自文档性。例如，如果我要编写一个计算员工州所得税的函数，那么一个好的函数名可能是：`calculateEmployeeStateIncomeTax()`。我知道这名字很长，但该函数的意图毫无歧义。

如前所述，一个可遵循的好模板是使用“动词+名词”并视需要加入形容词来命名函数。如果你的函数返回布尔值 `true` 或 `false`（即函数回答一个问题），请考虑将其命名为类似 `isX()` 或 `hasY()` 的形式。在你参与的项目中寻找其他类似约定。例如，有些项目使用 `fetchQ()` 来表示与数据库或外部 API 交互的方法。

### 练习

为以下内容创建一个脚本 `functions.php`：

- 1. 创建函数来对两个数进行加、减、除、乘运算，并返回结果。输出每次运算的结果以及两个输入值。

- 2. 创建一个接受两个参数的函数：一个总额和一个以百分比表示的销售税率（因此 5% 的销售税率表示为 0.05）。返回总额应缴纳的销售税。然后输出总额、税率和应缴销售税。

## 第 11 章

## 使用 HTML 表单

> > “调试代码的难度是编写代码的两倍。因此，如果你尽可能巧妙地编写代码，那么按定义来说，你还不够聪明去调试它。”

> > 

> > ——布莱恩·W. 克尼汉

## 处理我们的表单并将输出返回网页

表单提交后，浏览器将表单数据发送到我们的 `postfullname.php` 脚本。在这里，我们获取表单数据，从中生成问候语，然后将其显示在网页上。

假设我在“名”中输入“Ken”，在“姓”中输入“Marks”，我希望问候语看起来像图 11.2 所示。我们的 `postfullname.php` 脚本如清单 11.2 所示。

清单 11.2.

```
1. <html>
2. <head>
3. <title>Full Name</title>
4. </head>
5. <body>
6. <h2>Greetings!</h2>
7. <?php
8. $first_name = $_POST['first_name'];
9. $last_name = $_POST['last_name'];
10. 
11. echo "Hello " . $first_name . " " . $last_name . ". Thanks for submitting the form!";
12. ?>
13. </body>
14. </html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_111_0.png)

我希望你注意几点。首先，PHP 被设计为可与 HTML 混合使用。你可以轻松地在 PHP 和 HTML 之间切换。其次，如果脚本中包含任何 PHP 代码，你需要使用 `.php` 扩展名来命名脚本。

### `$_POST` 超全局变量

`$_POST` 是 PHP 内置的一个特殊变量，用于保存表单数据，并且在 HTTP POST 后，它可在你的整个脚本集中使用。`$_POST` 是一个关联数组。你可以通过使用表单中的 `name` 属性作为关联键，访问 `$_POST` 超全局数组中的表单数据。

查看 `postfullname.php` 脚本，你会看到 `$_POST['first_name']` 来自 `postfullname.html` 中由 `first_name` 标识的 input 元素的 `name` 属性（`<input name="first_name"/>`）。同样，`$_POST['last_name']` 来自由 `last_name` 标识的 input 元素的 `name` 属性（`<input name="last_name"/>`）。

你还会注意到，我将 `$_POST['first_name']` 和 `$_POST['last_name']` 赋值给了局部变量。这样做并非必需，但通常有助于提高代码的可读性。我想指出，使用 `echo` 向网页输出 HTML 应当被使用。

## 11. 使用 HTML 表单

使用 `echo` 生成 HTML 输出可能会很繁琐，因此应谨慎使用。清单 11.3 是我们的 `postfullname.php` 脚本的一个修改示例，展示了另一种在 HTML 和 PHP 之间切换以输出 HTML 的方法。

清单 11.3.

```php
1. <html>
2.   <head>
3.     <title>Full Name</title>
4.   </head>
5.   <body>
6.     <h2>Greetings!</h2>
7.     Hello <?= $_POST['first_name'] . " " . $_POST['last_name'] ?>
8.     Thanks for submitting the form!
9.     <br/>
10.    <?php print_r($_POST) ?>
11.  </body>
12. </html>
```

我们使用 PHP 短标签 `<?=`，而不是使用 `echo`。该语法是 `<?php echo` 的简写形式，极为方便，因为你很可能在将数据转换为 HTML 输出之前，使用 PHP 处理数据。

关于这个简化示例，还有一点需要注意：我删除了局部变量，并使用 `$_POST` 超全局变量直接访问相应元素。

最后一点关于使用 `$_POST` 超全局变量或一般数组操作的说明。通常你需要检查数组的内容。例如，你可能想知道是否从表单中获得了预期内容。你可以使用浏览器自带的开发者工具（大多数开发者都这样做），但这只能显示客户端将发送什么。在你开发 PHP 脚本时，快速输出数组内容会非常方便。你可以使用函数 `print_r()`[1] 轻松做到这一点。

如果我在上述脚本的结束 `</body>` 标签之前添加以下行，就会得到如图 11.3 所示的输出。

```html
    <br/>
    <?php print_r($_POST) ?>
</body>
</html>
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_112_0.png)

图 11.3.

[1] `print_r()`: https://php.net/print_r

### 使用自引用页面进行清理

运行这个小型的 Web 程序时，需要注意一点：我们首先导航到包含表单的 URL。然后提交表单后，我们再导航到包含 PHP 代码的第二个页面。我们不必这样做。如果能在某个脚本中包含整个表单，并在用户准备提交表单时再运行自身，那会更好。

我们可以通过创建所谓的自引用页面来实现这一点。为此，我们需要使用 PHP 提供的另一个超全局变量，它引用当前网页的 URL，即 `$_SERVER['PHP_SELF']`。

让我们使用上面的示例，向输入名字和姓氏的用户输出问候语。

该脚本由两部分组成：表单和问候语的输出。对于这个程序，我们首先要输出表单。然后当用户提交表单时，我们希望在输出问候语时不再显示表单。请注意，有些设计会让你在提交后再次输出问候语和表单，但在这个示例中，我们希望用户提交后只输出问候语而不显示表单。

这种行为需要一点条件逻辑（`if/else`），因此我建议绘制一个简单的决策树或编写一些伪代码：

```text
IF user submitted form
    Output greeting with first and last name.
ELSE
    Output first and last name form
END IF
```

清单 11.4.

```php
1. <html>
2.   <head>
3.     <title>Form for Entering Full Name</title>
4.   </head>
5.   <body>
6.     <?php if (!isset($_POST['submit'])) { ?>
7.       <h2>Enter Full Name</h2>
8.       <form action="<?= $_SERVER['PHP_SELF'] ?>" method="POST">
9.         First name:<br/>
10.        <input name="first_name"/><br/>
11.        Last name:<br/>
12.        <input name="last_name"/><br/>
13.        <p>
14.          <input type="submit" name="submit" value="Submit Name" />
15.        </form>
16.    <?php } else { ?>
17.      <h2>Greetings!</h2>
18.      Hello <?= $_POST['first_name'] . " " . $_POST['last_name'] ?>
19.      Thanks for submitting the form!
20.    <?php } ?>
21.  </body>
22. </html>
```

上述代码根据用户是否提交了表单，来决定 HTML 文档主体中显示的内容。当该页面第一次渲染时，用户尚未提交表单，因此 `$_POST['submit']` 不会被设置。因此，第一个 `if` 语句中的所有 HTML（即显示表单的部分）都会渲染到页面上。而 `else` 语句中的 HTML 则不会被渲染。

一旦用户提交表单，浏览器就会将 HTTP POST 请求发送到完全相同的脚本（这从表单的 `action` 属性设置为 `$_SERVER['PHP_SELF']` 可以看出）。脚本从头开始执行。然而，当接下来执行 `if` 语句时，条件为假，因为用户确实提交了表单，并且 `$_POST['submit']` 现在已经被设置了。

此时，`else` 语句中的代码和 HTML 将分别执行和渲染，从而在网页上输出问候语（而不是表单）。

顺便提一下，`$_SERVER`[2] 是 PHP 提供的又一个超全局关联数组。它包含有关 Web 服务器和执行环境的信息。使用其内容时要小心，因为内容取决于你使用的服务器及其配置方式。

[2] `$_SERVER`: http://php.net/reserved.variables.server

### 练习：BadLibs，第 1 部分

- 1. 创建自引用的 `postfullname.php` 脚本，并确保它能正常工作。

- 2. 创建“BadLibs”第 1 部分程序。

本练习基于流行的填空单词游戏。编写一个简单的 Web 应用程序，其表单接受一个名词、一个动词、一个形容词和一个副词。一旦用户提交表单，你的应用程序就应将名词、动词、形容词和副词组合成一个有趣的句子或由你创作的一段短文。为了增加挑战性，可以考虑将其做成自引用表单，并通过使用更多的名词、动词、形容词和副词等，编写一个更长的故事/段落。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_115_0.png)

图 11.4 是一个可能外观的示例。

图 11.5 是输出的一个示例。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_115_1.png)

## 第 12 章：向 MySQL 数据库插入数据

> “很长一段时间里，我一直困惑不解：为什么一样东西如此昂贵、如此前沿，却可能如此无用。后来我意识到，计算机是一台愚蠢的机器，却有能力做极其聪明的事情；而计算机程序员是聪明的人，却有能力做极其愚蠢的事情。简而言之，他们完美匹配。”

> 

> ——比尔·布莱森

关于如何将 SQL 与 MySQL 配合使用的参考指南，请查阅 MySQL 文档[2]——目前在 Ubuntu LTS 发行版中为 8.0 版本。你很可能还会对 SQL 语句语法[3]感兴趣。

你可以通过在 Bash shell（而非 MySQL CLI）中键入以下命令，快速识别你的 MySQL 安装版本。你应该会看到类似于图 12.2 的输出。

```text
mysql --version
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_0.png)

### 创建“Northwind”数据库

为了演示 MySQL 的某些功能，让我们下载一个著名的示例数据库，这是微软多年前创建的，用于教授人们如何使用 Access 数据库应用程序。此后，它已被移植以支持 IIS 和 MySQL。Northwind 数据库保存着名为“Northwind Traders”的虚构公司的销售、库存和员工数据。

首先，我们需要使用 SQL 创建一个空数据库。为此，请在 MySQL CLI 工具中键入以下命令（图 12.3）。

```sql
CREATE DATABASE northwind;
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_1.png)

如果你输入正确，应该会看到一条 Query OK, 1 row affected 消息。

在第 2 章中，我们创建了一个名为 `testuser` 的用户。让我们授予 `testuser` 对 `northwind` 数据库的权限。输入以下命令（图 12.4）。

```sql
GRANT ALL PRIVILEGES ON northwind.* TO 'testuser'@'localhost';
```

输入 `exit` 退出 MySQL CLI 工具，然后返回 Bash shell：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_119_2.png)

[2] MySQL 文档: https://dev.mysql.com/doc/refman/8.0/en/

[3] SQL 语句语法: https://dev.mysql.com/doc/refman/8.0/en/sql-statements.html

## 12. 向 MySQL 数据库插入数据

### 加载 Northwind 数据库

Northwind 数据库包含在两个 SQL 文件中；一个包含模式，第二个包含数据。可以从以下位置下载：

- https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql

- https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql

你可以使用 Bash shell 中的 `wget` 下载它们。我喜欢将文件下载到我的主文件夹下的 Downloads 文件夹中。一旦你导航到想要下载 Northwind SQL 文件的文件夹，输入以下命令：

```bash
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind.sql
wget https://raw.githubusercontent.com/jpwhite3/northwind-MySQL/master/northwind-data.sql
```

下载文件并执行目录列表（`ls`）后，你将看到图 12.6 所示的输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_120_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_120_1.png)

现在让我们通过将键盘的 Unix 标准输入重定向到我们下载的文件，将 Northwind SQL 模式和数据文件导入 MySQL CLI 工具，输入以下命令在 Bash shell 中：

```bash
mysql -u testuser -p northwind < northwind.sql
mysql -u testuser -p northwind < northwind-data.sql
```

如果一切正常，按典型的 Unix 方式，我们不会得到任何响应。参见图 12.7。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_121_0.png)

### 基本 SQL 命令

以下各节将演示一些我们将用于处理数据库和表的基本 SQL 命令。

让我们通过在 Bash shell 中输入以下命令重新登录到 MySQL CLI 工具：

```bash
mysql -u testuser -p
```

### 显示数据库

如果我们有兴趣了解可供我们使用的数据库名称，可以输入以下 SQL 命令：

```sql
SHOW DATABASES;
```

我们应该在图 12.8 中看到输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_121_1.png)

### 使用数据库

让我们验证我们是否正确导入了 Northwind 数据库。要使用数据库，我们需要发出 SQL 命令表明我们想要使用它。在 `mysql>` 提示符下输入：

```sql
USE northwind;
```

你应该会看到类似图 12.9 的内容。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_122_0.png)

图 12.9。

### 显示表

我们可以通过发出以下 SQL 命令来显示 `northwind` 数据库中的所有表：

```sql
SHOW TABLES;
```

你应该会看到类似图 12.10 的输出。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_122_1.png)

图 12.10。

### 描述表

假设我们有兴趣了解 `products` 表结构的更多信息。我们可以通过发出以下 SQL 命令来描述表中的所有字段（或列）：

```sql
DESCRIBE products;
```

图 12.11 显示了输出。
