

## 构造函数

```
public function __construct($id, $name, $email)
{
    $this->id = $id;
    $this->name = $name;
    $this->email = $email;
}

// Getters
public function getId()
{
    return $this->id;
}

public function getName()
{
    return $this->name;
}

public function getEmail()
{
    return $this->email;
}
}
```

代码清单 26.19 是一个使用我们类的脚本。注意，在实例化对象时，有三个参数传递给了构造函数。这将产生以下输出（图 26.4）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_491_0.png)

## 代码清单 26.19.

```
<?php
require_once('Student.php');

$jane = new Student(7, 'Jane Doe', 'jane@example.com');
?>
<table>
<tr>
<th>Name:</th>
<td><?= $jane->getName() ?></td>
</tr>
<tr>
<th>ID:</th>
<td><?= $jane->getId() ?></td>
</tr>
<tr>
<th>Email:</th>
<td><?= $jane->getEmail() ?></td>
</tr>
</table>
```

## 26. PHP 中的面向对象编程简介

## 关于构造函数

在 PHP 中使用构造函数和析构函数[8]时，需要记住的一点是，它们在其他面向对象语言中可能表现不同。看一下 PHP 手册中关于构造函数的一段引用，以确保你知道如何设计你的类，以你预期的方式利用构造：

> 如果子类定义了构造函数，父类构造函数不会隐式调用。要运行父构造函数，你必须在子构造函数中调用 parent::__construct()。如果子类没有定义构造函数，那么它可以从父类继承，并像标准类方法一样被调用（如果它没有被声明为 private）。

## PHP 8 中的构造函数属性提升

虽然本书假设使用 PHP 7.x，但在本书出版时，PHP 8 已经发布，并提供了一些新功能和增强。我只想向你介绍其中一个，称为构造函数属性提升。

构造函数属性提升允许你将类属性、构造函数定义和变量赋值全部合并到 __construct() 参数列表中。在标准定义类实例属性、构造函数和赋值时，你会使用类似代码清单 26.20 的代码。

## 代码清单 26.20.

```php
<?php

class Student
{
    private $id;
    private $name;
    private $email;

    // Constructor
    public function __construct(
        $id,
        $name,
        $email
    ) {
        $this->id = $id;
        $this->name = $name;
        $this->email = $email;
    }
}
```

[8] 构造函数和析构函数：https://php.net/manual/en/language.oop5.decon

我们在上面已经看到过这些内容。在构造函数属性提升中，我们可以用更少的样板代码将同样的代码重写为代码清单 26.21。

## 代码清单 26.21.

```php
<?php
class Student
{
    // Constructor
    public function __construct(
        private $id,
        private $name,
        private $email)
    {
    }
    // ...
}
```

只要构造函数参数列表中的变量前面有访问修饰符（private、protected 或 public），PHP 就会在底层创建属性，并将传入参数列表的值赋给它们。你仍然可以使用 this 关键字直接访问类中的属性。

详细信息包含在 PHP 手册的构造函数[9]章节中。如果你想了解更多，可以参考 PHP 手册 Wiki 上已为 PHP 8 批准的构造函数属性提升[10]的评论请求（RFC）。

## 使用面向对象编程创建参数化查询

在第 23 章“预处理语句”中，我向你展示了如何使用过程式函数 mysqli_prepare()、mysqli_stmt_bind_param()、mysqli_stmt_execute() 和 mysqli_stmt_get_result() 来创建更安全的参数化数据库查询。然而，还有一种面向对象的方式，可以使用 PHP 数据对象[11]（PDO）用更少的代码来实现数据库查询的参数化。我将通过创建一个简单的数据库表和一个管理数据进出该表的类来演示如何使用 PDO，以实现 PDO 的功能。

[9] 构造函数：https://php.net/language.oop5.decon.constructor.promotion
[10] 构造函数属性提升：https://wiki.php.net/rfc/constructor_promotion
[11] PHP 数据对象：https://php.net/book.pdo

## 26. PHP 中的面向对象编程简介

PDO 是用于与数据库交互的首选库，主要是因为它适用于多种不同的数据库技术。无论我们将数据存储在哪里，这个库都能为我们提供熟悉的 API。

首先，我们需要创建一个数据库和一个可以操作的简单表。对于这个演示，我将创建一个名为 Student 的简单数据库和一个名为 student 的表，用于存储学生的名、姓和电子邮件地址，如图 26.5 所示。

使用 PDO 的一种常见方式是创建一个称为 CRUD 包装器的类，它管理与数据库表的所有查询。CRUD 代表创建（Create）、读取（Read）、更新（Update）和删除（Delete），这些是我们对数据库表执行的常见操作。一个良好的实践是使用数据库表的“大驼峰式”（Studly Caps）命名变形，并在类名末尾拼接“Manager”一词。在本例中，由于我们的表叫做 student，我们应该将类命名为 StudentManager。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_494_0.png)

## 使用 PDO 创建新的数据库条目

代码清单 26.22 展示了该类以及用于向 student 表插入行的 create() 方法。

## 代码清单 26.22.

```php
<?php

class StudentManager
{
    // Database connection constants
    private const DB_TECHNOLOGY = "mysql";
    private const DB_HOST = "localhost";
    private const DB_NAME = "Student";
    private const DB_USER = "testuser";
    private const DB_PASSWORD = "testuser";

// Results in DSN = "mysql:host=localhost;dbname=Student"
private const DSN = self::DB_TECHNOLOGY
    . ':host=' . self::DB_HOST
    . ';dbname=' . self::DB_NAME;

public function create($first_name, $last_name, $email)
{
    $db = new PDO(self::DSN, self::DB_USER, self::DB_PASSWORD);

    // Insert a new record
    $sql = "INSERT INTO student(`first_name`, `last_name`, `email`) VALUES (:first_name, :last_name, :email)";

    $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

    try
    {
        $query = $db->prepare($sql);
        $query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
        $query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
        $query->bindParam(":email", $email, PDO::PARAM_STR);
        $query->execute();
    } catch (Exception $ex)
    {
        echo $ex->getMessage() . "<br/>";
    }

    // Returns the primary key of this INSERT
    return $db->lastInsertId();
}
```

实例化新 PDO 对象的构造函数需要三个参数：数据源名称、用户名和密码，创建时即连接到数据库。连接到 MySQL 数据库时，数据源名称必须如下所示：

```
"mysql:host=localhost;dbname=Student"
```

第 6 至 10 行的常量将数据源名称、用户名和密码输入参数设置给 PDO 构造函数。

第 17 行是我们的 create() 方法，它接收名、姓和电子邮件地址，这三个字段对应于我们要插入 student 表的三个字段。

要使用 PDO，我们在第 19 行实例化一个新对象，该对象创建与数据库的连接。

## 26. PHP 中的面向对象编程简介

我们在第 22 行创建 SQL 语句，将数据插入 student 表。注意，我们不用 ? 并依赖它们的顺序，而是可以使用以冒号（:）开头的任意名称来创建命名参数：

```
$sql = "INSERT INTO student(`first_name`, `last_name`, `email`)
        VALUES (:first_name, :last_name, :email)";
```

这里我们使用 :first_name、:last_name 和 :email 作为命名参数，我们将传入的参数 $first_name、$last_name 和 $email 绑定到这些命名参数上。

第 25 行允许我们通过设置一些 PDO 类常量属性来启用错误报告和异常处理。这样做使我们能够使用异常来处理数据库错误，而无需太多条件逻辑的复杂性。

```
$db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```

> 我还没有介绍异常处理，但简单来说，它允许我们尝试执行一些可能引发异常行为的代码（比如无法成功查询数据库表）。如果发生异常，我们可以有序地捕获它，希望这能让我们的应用程序优雅地恢复。如果一切在 try 块中都正常运行，则不会执行 catch 块。

面向对象方式的参数准备和绑定在 try 块的这些代码行中处理：

```
$query = $db->prepare($sql);
$query->bindParam(":first_name", $first_name, PDO::PARAM_STR);
$query->bindParam(":last_name", $last_name, PDO::PARAM_STR);
$query->bindParam(":email", $email, PDO::PARAM_STR);
```

首先，我们调用 PDO 对象的 prepare() 方法，将 SQL 语句作为参数传入，该方法返回一个 PDOStatement 对象，我们将其赋值给一个名为 $query 的变量。这是我们绑定参数的对象。注意，bindParam() 方法的第三个参数是指定数据类型的 PDO 类常量。虽然这个参数是可选的，但你应该显式包含它，以便 PDO 正确转义你的数据类型。

然后我们通过以下调用执行查询：

```
$query->execute();
```

