
# 使用内置函数

```
foreach($customerOrder as $amount)
{
    $total = $amount + compute_salestax($amount,$custState);
    echo "Your total is $total<br>";
}
```

`return` 语句只能返回一个值。不过，返回的值可以是数组，因此你实际上可以从一个函数返回多个值。

你可以在条件语句中使用 `return` 语句，根据不同条件返回不同的值。例如，下面的函数返回两个不同字符串之一：

```php
function compare_values($value1,$value2)
{
    if($value1 < $value2)
    {
        return "less than";
    }
    else
    {
        return "not less than";
    }
}
```

虽然该函数包含两个 `return` 语句，但根据 `$value1` 和 `$value2` 的值，只会执行其中一个。

PHP 的众多内置函数是 PHP 如此强大且适用于网页的原因之一。PHP 附带的函数是普通函数，它们与你自行创建的函数没有区别，只是 PHP 已经替你完成了所有工作。

我在本章和前面的章节中讨论了一些内置函数。例如，关于函数 `unset` 和 `number_format` 的更多信息，请参阅第 6 章。一些用于与 MySQL 数据库交互的非常有用的函数将在第 8 章中讨论。其他有用的函数列于本书的第 V 部分。当然，所有函数都在 PHP 官方网站 `www.php.net/docs.php` 的 PHP 文档中列出并加以描述。

# 第 8 章 数据输入，数据输出

## 本章内容

- 连接数据库
- 从数据库获取信息
- 将 HTML 表单与 PHP 结合使用
- 从 HTML 表单获取数据
- 处理用户在 HTML 表单中输入的信息
- 在数据库中存储数据
- 使用函数将数据移入和移出数据库

PHP 和 MySQL 配合得非常好。这种动态的伙伴关系使 PHP 和 MySQL 在 Web 数据库应用开发中如此具有吸引力。无论你是拥有一个充满信息并希望提供给用户的数据库（例如产品目录），还是一个等待用户填充的数据库（例如会员数据库），PHP 和 MySQL 都能协同工作来实现你的应用。

PHP 最强大的特性之一就是它与数据库交互的能力。它提供了使与 MySQL 通信变得极其简单的函数。你可以使用 PHP 函数向数据库发送 SQL 查询。你不需要了解与 MySQL 通信的细节；PHP 会处理这些细节。你只需要知道 SQL 查询以及如何使用 PHP 函数。

在本书前面的章节中，我描述了用于构建 Web 数据库应用程序的工具。你会在第 4 章了解如何构建 SQL 查询，并在第 6 章和第 7 章了解如何构建和使用 PHP 语言的基本构件。在本章中，你将了解如何将这些工具用于 Web 数据库应用程序需要执行的特定任务。

## PHP/MySQL 函数

你可以使用内置的 PHP 函数与 MySQL 进行交互。这些函数用于连接 MySQL 服务器、选择正确的数据库、发送 SQL 查询以及与 MySQL 数据库进行其他通信。你不需要了解与数据库交互的细节，因为 PHP 会处理所有细节。你只需要知道如何使用这些函数。

目前，PHP（从版本 5 开始）有两组用于与 MySQL 交互的函数。一组函数用于与 MySQL 4.0 或更早版本交互。另一组函数用于与 MySQL 4.1 或更高版本交互。

在本书中，我的示例和程序展示的是适用于 MySQL 4.0 版本的函数。在撰写本书时，MySQL 当前稳定版本是 4.0。此外，用于 MySQL 4.1 的 PHP 函数在 PHP 官方网站的文档中被描述为实验性的，并带有警告：使用此扩展风险自负。目前，MySQL 4.1 仅作为 alpha 软件提供，MySQL 手册对其定义如下：该版本包含一些尚未 100% 测试的大型新代码段。因此，我撰写本书时基于 MySQL 4.0 以及适用于该版本的 PHP 函数。

用于 MySQL 4.0 的 PHP 函数具有以下一般格式：

```
mysql_function(value,value,...);
```

函数名称的第二部分与具体函数相关，通常是一个描述函数功能的单词。此外，函数需要一个或多个要传递的值，用于指定数据库连接、数据位置等内容。以下是本章讨论的两个函数：

```
mysql_connect($connect);
mysql_query("SQL statement",$connect);
```

当你读到本书时，MySQL 4.1 可能是 MySQL 当前的稳定版本。如果是这样，你可以使用 MySQL 4.1 及与之配合使用的函数。截至撰写本书时，本书讨论的函数在 MySQL 4.0 和 MySQL 4.1 中是相同的，只是名称有所变化。用于 MySQL 4.1 的函数名称以 `mysqli_` 开头，而不是 `mysql_`。因此，上面显示的函数如果用于 MySQL 4.1，其名称将如下所示：

```
mysqli_connect($connect);
mysqli_query($connect,"SQL statement");
```

这些函数的功能和语法相同或非常相似。例如，请注意以下两个函数之间的区别：

```
mysql_query($sql,$connect)
mysqli_query($connect,$sql)
```

注意传递项的顺序不同。对于几个函数来说都是如此。

本讨论指的是当前状态的 `mysqli` 函数。当然，`mysqli` 函数可能会发生变化。如果某个 `mysqli` 函数看起来无法按预期工作，请查阅手册以了解用法上可能存在的差异。

名称中新增的 `i` 代表*改进*；这组 MySQL 函数由改进的 MySQL 扩展提供。目前，PHP 默认不包含对 `mysqli` 的支持。它必须在安装 PHP 时启用。然而，到 MySQL 4.1 成为稳定版本时，`mysqli` 很可能将成为 PHP 的一部分，而无需你专门启用它。要查看 `mysqli` 的当前状态，请查看 `www.php.net/manual/en/ref.mysqli.php` 上的文档。

截至撰写本书时，你可以使用以下安装选项来启用 `mysqli`：

```
--with-mysqli=DIR
```

`DIR` 是名为 `mysql_config` 的程序所在目录的路径，该程序在安装 MySQL 4.1 时已安装。

## 建立连接

在存储或获取任何数据之前，你必须先连接到数据库。数据库可能与你的 PHP 程序位于同一台计算机上，也可能位于不同的计算机上。你不需要了解连接数据库的细节，因为 PHP 会处理所有细节。你只需要知道数据库的名称和位置。你可以把数据库连接想象成电话连接。你不需要知道你的话语是如何在电话之间传输的，只需要知道区号和电话号码。电话公司会处理这些细节。

连接到数据库后，你可以使用专门为此目的设计的 PHP 函数向 MySQL 数据库发送 SQL 查询。你可以根据需要发送任意数量的查询。连接会一直保持，直到你明确关闭它或程序结束。类似地，在电话通话中，连接会一直保持，直到你挂断电话才终止。

### 连接 MySQL 服务器

与 MySQL 数据库通信的第一步是连接 MySQL 服务器。要连接服务器，你需要知道数据库所在计算机的名称、MySQL 账户的名称以及 MySQL 账户的密码。要打开连接，请按如下方式使用 `mysql_connect` 函数：

```
$connection=mysqli_connect("addr","mysqlacctname","password")
    or die ("message");
```

## 处理 MySQL 错误

你使用 PHP 语言的 `mysql` 函数，例如 `mysql_connect` 和 `mysql_query`，来与 MySQL 数据库交互。如果其中某个函数执行不正确，会返回一条 MySQL 错误消息，其中包含有关问题的信息。然而，除非程序有意发送，否则此错误消息不会发送到浏览器。以下是调用 `mysql` 函数的三种常见方式：

- **不带错误处理的调用函数。** 函数在没有任何提供错误消息的语句的情况下被调用。例如，`mysql_connect` 函数可以按如下方式调用：

    ```php
    $connection = mysql_connect($host,$user,$password);
    ```

    如果此语句失败（例如，帐户无效），则不会建立连接，但程序中的其余语句仍会继续执行。在大多数情况下，这没有用，因为程序其余部分中的某些语句可能依赖于打开的连接，例如从数据库获取或存储数据。

- **使用 `die` 语句调用函数。** 函数与发送消息到浏览器的 `die` 语句一起调用。例如，`mysql_connect` 函数可以按如下方式调用：

    ```php
    $connection = mysql_connect($host,$user,$password)
        or die ("Couldn't connect to server");
    ```

    如果此语句失败，则不会建立连接，并且会执行 `die` 语句。`die` 语句会停止程序并将消息发送到浏览器。如果无法建立连接，则不会再执行任何语句。您可以在 `die` 语句中放置任何想要的消息。

- **在 `if` 语句中调用函数。** 函数通过使用 `if` 语句调用，如果连接失败则执行一组语句。例如，`mysql_connect` 函数可以按如下方式调用：

    ```php
    if (!$connection = mysql_connect($host,$user,$password))
    {
        $message = mysql_error();
        echo "$message<br>";
        die();
    }
    ```

    如果此语句失败，则会执行 `if` 块中的语句。`mysql_error` 函数返回 MySQL 错误消息并将其保存到变量 `$message` 中。然后回显错误消息。`die` 语句结束程序，因此不会再执行任何语句。**注意** `if` 语句中的 `!`（感叹号）。`!` 表示“非”。换句话说，如果赋值语句不为真，则 `if` 语句为真。

您希望在程序中包含什么错误处理取决于您期望程序中发生什么。在开发程序时，您预计会发生一些错误。因此，在开发期间，您可能希望使用更具描述性的错误处理，例如前述列表中的第三种方法。例如，假设您使用名为 `root` 的帐户访问数据库，并且在以下语句中出现拼写错误：

```
$host = "localhost";
$user = "rot";
$password = "";
if (!$connection = mysql_connect($host,$user,$password))
{
    $message = mysql_error();
    echo "$message<br>";
    die();
}
```

因为您输入了 `"rot"` 而不是 `"root"`，您会看到类似以下内容的错误消息：

```
Access denied for user: 'rot@localhost' (Using password: NO)
```

此错误消息包含您需要的信息来找出问题所在；它显示了带有拼写错误的帐户名。然而，在您的程序运行并且客户使用它之后，您可能不希望用户看到像前面那样的技术错误消息。相反，您可能希望使用第二种方法，并在 `die` 消息中使用一般性语句，例如 The Pet Catalog is not available at the moment. Please try again later.

填写以下信息：

- `addr`：MySQL 安装所在的计算机的名称——例如，`databasehost.mycompany.com`。如果 MySQL 数据库与您的网站在同一台计算机上，您可以使用 `localhost` 作为计算机名称。如果此信息为空（`""`），PHP 会假定为 `localhost`。
- `mysqlacctname`：您的 MySQL 帐户的名称。（我在第 5 章中详细讨论了 MySQL 帐户。）您可以将此信息留空（`""`）——意味着任何帐户都可以连接——但出于安全原因，这通常是个坏主意。
- `password`：您 MySQL 帐户的密码。如果您的 MySQL 帐户不需要密码，请不要在引号之间输入任何内容：`""`。
- `message`：如果连接失败，则发送到浏览器的消息。如果计算机或网络关闭或 MySQL 服务器未运行，则连接会失败。如果提供的信息不正确，也可能失败——例如，密码中存在拼写错误。

在开发期间，您可能希望使用描述性消息，例如 Couldn't connect to server，但在应用程序投入使用后，使用更通用的适合客户的消息，例如 The Pet Catalog is not available at the moment. Please try again later.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_213_0.png)

![](img/d82df0828cfbc6d6be1e9a991861f3b7_214_0.png)

`addr` 包含连接所需的端口号。几乎总是，端口号是 3306。在极少数情况下，MySQL 管理员需要设置 MySQL 在不同的端口上连接。在这些情况下，需要端口号才能进行连接。端口号指定为 `主机名:端口号`。例如，您可能会使用 `localhost:8080`。

使用这些语句，`mysql_connect` 尝试使用提供的帐户名和密码打开到指定计算机的连接。如果连接失败，程序将在此处停止运行并将 *消息* 发送到浏览器。

以下语句使用不需要密码的名为 `catalog` 的 MySQL 帐户连接到本地计算机上的 MySQL 服务器：

```php
$connection = mysql_connect("localhost","catalog","")
    or die ("Couldn't connect to server.");
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_214_1.png)

出于安全原因，将连接信息存储在变量中并在连接语句中使用这些变量是个好主意，如下所示：

```php
$host="localhost";
$user="catalog";
$password="";
$connection = mysql_connect($host,$user,$password)
    or die ("Couldn't connect to server.");
```

事实上，为了更安全，您可以将连接信息的赋值语句放在隐藏位置的单独文件中，这样帐户名和密码甚至不在程序中。我在第 10 章中解释了如何做到这一点。

变量 `$connection` 包含标识连接的信息。您可以通过使用多个变量名同时打开多个连接。连接保持打开状态，直到您关闭它或程序结束。关闭连接如下：

```php
mysql_close($connectionname);
```

例如，要关闭前一个示例中的连接，请使用以下语句：

```php
mysql_close($connection);
```

## 选择正确的数据库

在与 MySQL 服务器的连接建立并打开后，您需要告诉 MySQL 您想要交互的数据库。使用 `mysql_select_db` 函数如下：

```php
$db = mysql_select_db("databasename",$connectionname)
     or die ("message");
```

填写以下信息：

- `databasename`：数据库的名称。
- `connectionname`：包含连接信息的变量。如果您没有输入连接，PHP 将使用最后打开的连接。
- `message`：如果无法选择数据库，则发送到浏览器的消息。选择可能失败，因为找不到数据库，这通常是数据库名称拼写错误的结果。

例如，您可以使用以下语句选择数据库 `PetCatalog`：

```php
$db = mysql_select_db("PetCatalog",$connection)
     or die ("Couldn't select database.");
```

如果 `mysql_select_db` 无法选择数据库，程序将在此处停止运行，并将消息 `Couldn't select database.` 发送到浏览器。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_215_0.png)

出于安全原因，将数据库名称存储在变量中并在连接语句中使用该变量是个好主意，如下所示：

```php
$database = "PetCatalog";
$db = mysql_select_db($database,$connection)
     or die ("Couldn't select database.");
```

事实上，为了更安全，您可以将数据库名称的赋值语句放在隐藏位置的单独文件中——正如为连接信息的赋值语句所建议的那样——这样数据库名称甚至不在程序中。我在第 10 章中解释了如何做到这一点。

数据库保持选中状态，直到您明确选择不同的数据库。要选择不同的数据库，只需使用新的 `mysql_select_db` 函数语句即可。

## 发送 SQL 查询

在您拥有到 MySQL 服务器的打开连接并且 PHP 知道您想要交互的数据库后，您发送 SQL 查询。*查询* 是向 MySQL 服务器请求存储一些数据、更新一些数据或检索一些数据的请求。（有关 SQL 语言的更多信息以及如何构建 SQL 查询，请参阅第 4 章。）

要与数据库交互，请将 SQL 查询放入变量中，并使用 `mysql_query` 函数将其发送到 MySQL 服务器，如下例所示：

```
$query = "SELECT * FROM Pet";
$result = mysql_query($query)
    or    die ("Couldn't execute query.");
```
