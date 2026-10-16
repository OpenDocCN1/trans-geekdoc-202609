

要与数据库交互，请将 SQL 查询放入变量中，并使用 mysql_query 函数将其发送到 MySQL 服务器，如下例所示：

```
$query = "SELECT * FROM Pet";
$result = mysql_query($query)
    or    die ("Couldn't execute query.");
```

该查询会针对你所打开的上一个连接当前选定的数据库执行。如果需要——例如，如果你打开了多个连接——你可以像这样将查询发送到特定的数据库服务器：

```
$result = mysql_query($query,$connection)
    or    die ("Couldn't execute query.");
```

变量 $result 保存了执行查询所得结果的信息。该信息取决于查询是否从数据库获取数据：

- **对于不获取数据的查询：**变量 $result 包含查询是否成功执行的信息。如果成功，$result 会被设置为 TRUE；如果不成功，$result 会被设置为 FALSE。一些不返回数据的查询是 INSERT 和 UPDATE。
- **对于返回数据的查询：**变量 $result 包含一个结果标识符，该标识符标识返回数据的位置，而不是返回数据本身。一些确实返回数据的查询是 SELECT 和 SHOW。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_216_0.png)

在将查询字符串赋值给 $query 时，单引号和双引号的使用可能会让人有点困惑。实际上，你在两个层面上使用引号：将字符串赋值给 $query 所需的引号，以及 SQL 语言查询本身所包含的引号。以下规则将帮助你避免任何引号问题：

- 在字符串的开头和结尾使用双引号。
- 在变量名的前后使用单引号。
- 在任何字面值的前后使用单引号。

以下是赋值查询字符串的示例：

```
$query = "SELECT firstName FROM Member";
$query = "SELECT firstName FROM Member WHERE lastName='Smith'";
$query = "UPDATE Member SET lastName='$last_name'";
```

![](img/d82df0828cfbc6d6be1e9a991861f3b7_216_1.png)

查询字符串本身不包含分号（;），所以不要在最后的引号内放置分号。唯一的分号位于最末尾；这是结束语句的 PHP 分号。

## 从数据库获取信息

从数据库获取信息是 Web 数据库应用程序的常见任务。以下是数据库信息的两种常见用途：

- **使用该信息有条件地执行语句。** 例如，你可以从会员目录中获取居住州，并向居住在不同州的会员发送不同的消息。
- **在网页中显示该信息。** 例如，你可能想要显示数据库中的产品信息。

为了在程序中使用数据库信息，你需要将信息放入变量中。然后，你可以在条件语句、echo 语句或其他语句中使用这些变量。从数据库获取信息是一个两步过程：

1. 构建一条 SELECT 查询，并将该查询发送到数据库。查询执行时，选中的数据会存储在临时位置。
2. 将数据从临时位置移入变量，并在程序中使用。

## 发送 SELECT 查询

你使用 SELECT 查询从数据库获取数据。SELECT 查询是用 SQL 语言编写的。（我将在第 4 章详细讨论 SELECT 查询。）

要从数据库获取数据，请构建你需要的 SELECT 查询，将其存储在变量中，然后将查询发送到数据库。以下语句从 PetCatalog 数据库的 Pet 表中选择所有信息：

```
$query = "SELECT * FROM Pet";
$result = mysql_query($query)
    or    die ("Couldn't execute query.");
```

mysql_query 函数获取 SELECT 查询请求的数据，并将其存储在临时位置。你可以将这些数据视为存储在一个类似于 MySQL 表的表中，信息按行和列排列。

该函数返回一个结果标识符，其中包含查找数据临时存储位置所需的信息。在前面的语句中，结果标识符被放入变量 $result 中。执行该函数后，下一步是将数据从临时位置移动到可在程序中使用的变量中。

如果函数失败——例如，如果查询不正确——`$result` 将包含 `FALSE`。

## 获取并使用数据

你使用 `mysql_fetch_array` 函数从临时位置获取数据。该函数从临时位置获取一行数据。临时数据表可能只包含一行数据，或者更有可能的是，你的 select 查询在临时数据表中产生了多行数据。如果要从临时位置获取多行数据，请在循环中使用 `mysql_fetch_array` 函数。

### 获取一行数据

要将数据从临时位置移出并放入可在程序中使用的变量中，请使用 PHP 函数 `mysql_fetch_array`。`mysql_fetch_array` 函数的一般格式如下：

```php
$row = mysql_fetch_array($resultidentifier,typeofarray);
```

该语句从临时位置的数据表中获取一行，并将其放入名为 `$row` 的数组变量中。请填写以下信息：

- **`resultidentifier`：**指向结果临时位置的变量。
- **`typeofarray`：**结果所放入的数组类型。它可以是两种数组类型之一，也可以同时是两种类型。请使用以下值之一：
  - `MYSQL_NUM`：一个数组，对于行中的每一列都有一个键/值对，使用数字作为键。
  - `MYSQL_ASSOC`：一个数组，对于行中的每一列都有一个键/值对，使用列名作为键。
  - `MYSQL_BOTH`：一个包含两种键的数组。换句话说，该数组对每一列都有两个键/值对：一个以数字为键，一个以列名为键。如果在函数调用中未指定数组类型，则假定为 `MYSQL_BOTH`。

`mysql_fetch_array` 函数从临时位置获取一行数据。在某些情况下，一行就是你所选择的全部数据。例如，要检查用户输入的密码，你只需要从数据库获取用户的密码，并将其与用户输入的密码进行比较。以下语句检查密码：

```php
$userEntry = "secret";    // password user entered in form
$query = "SELECT password FROM Member
          WHERE loginName='gsmith'";
$result = mysql_query($query)
or die ("Couldn't execute query.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
if ( $userEntry == $row['password'] )
{
    echo "Login accepted<br>";
    statements that display Members Only Web pages
}
else
{
    echo "Invalid password<br>";
    statements that allow user to try another password
}
```

关于上述语句，请注意以下几点：

- SELECT 查询只从一行（gsmith 所在的行）请求一个字段（password）。
- mysql_fetch_array 函数返回一个名为 $row 的数组，以列名作为键。
- if 语句通过使用两个等号（==）将用户输入的密码（$userEntry）与从数据库获取的密码（$row['password']）进行比较，以判断它们是否相同。
- 如果比较结果为真，则密码匹配，并执行 if 块（该块显示仅限会员的 Web 页面）。
- 如果比较结果不为真，说明用户输入的密码与数据库中存储的密码不匹配，则执行 else 块。用户会看到一条说明密码不正确的错误消息，并返回到登录 Web 页面。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_219_0.png)

PHP 提供了一个快捷方式，便于使用通过 mysql_fetch_array 函数检索到的变量。你可以使用 extract 函数，该函数会将数组拆分为与键同名的变量。例如，你可以使用 extract 函数重写前面测试密码的语句。如下所示：

```
$userEntry = "secret"; #password user entered into HTML form
$query = "SELECT password FROM Member
          WHERE loginName='gsmith'";
$result = mysql_query($query)
    or  die ("Couldn't execute query.");
$row = mysql_fetch_array($result,MYSQL_ASSOC);
extract($row);
if ( $userEntry == $password )
{
    echo "Login accepted<br>";
    statements that display Members Only Web pages
}
else
```

