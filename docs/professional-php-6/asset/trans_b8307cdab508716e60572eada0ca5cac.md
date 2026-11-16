

由于 PHP 6 中所有对象均按引用传递，您可以在 `getCoursesForStudent()` 内更改集合的内容，并在 `Student` 对象的 `$courses` 变量中看到这些变化生效。如果“按引用传递”这个短语对您来说不太熟悉，请参见第 4 章中关于按值传递与按引用传递函数参数之间差异的讨论。

要最终将所有这些好东西派上用场，请尝试以下代码：

```php
<?php
$studentID = 1; //use a valid studentID value from your student table
try {
    $objStudent = StudentFactory::getStudent($studentID);
} catch (Exception $e) {
    die("Student #$studentID doesn't exist in the database!");
}

print $objStudent . ($objStudent->courses->exists('CS101') ? ' is ' : ' is not ') .
    'currently enrolled in CS101';
//displays: "Bob Smith is enrolled in CS101"
?>
```

在已部署的应用程序中，如果找不到指定的学生，您应该采取比突然终止应用程序更优雅的做法，但这能让您明白为什么必须使用 `try...catch` 语句。

获取 `$objStudent` 后，这段代码会显示一条简单消息，告知该学生是否已注册 CS101。调用 `exists()` 方法后，`courses` 集合会从数据库中填充，这要归功于 `StudentFactory`。由于添加 `Course` 对象到集合时使用了课程代码作为键，您可以将课程代码（`'CS101'`）作为参数传递给 `exists()`。

## 改进集合类

您可能在想，`Collection` 类还能如何改进。它如何能更强大、更有用或更有趣呢？问题是，您目前还没有一种简单的方法来遍历整个集合（例如显示课程列表）。现在，您只能直接跳转到那些您已知在集合中的项目。显然，在开始使用集合之前，您并不总是知道集合的内容是什么，因此您需要一种方法来编写如下代码：

```php
<?php
$objStudent = StudentFactory::getStudent(1);
foreach ($objStudent->courses as $objCourse) {
    print $objStudent . ' is currently enrolled in ' . $objCourse . "<br>\n";
}
?>
```

如果您现在尝试运行这段代码，要么会得到一个错误，要么看不到任何内容（取决于 `error_reporting` 级别），因为 `$objStudent->courses` 不是数组（它是一个 `Collection`）。在 PHP 4 中，可用作 `foreach` 语句操作数的唯一数据类型是数组。随着 PHP 5 的发布（并在 PHP 6 中继续沿用），您有了两个新的内置接口，`Iterator` 和 `IteratorAggregate`，它们使您能够在对象上使用 `foreach`，前提是这些对象实现了这些接口。

## 总结

`Collection` 类是传统数组的一种非常有用的面向对象替代方案，您可以在几乎要构建的任何应用程序中有效地使用它。它提供了对其成员的精心管理以及一致的 API，这使得编写使用该类的代码变得容易。

对 `Collection` 进行子类化并重写 `addItem()` 方法以在第一个参数中包含类型提示，可让您控制添加到集合中的对象类型。虽然这并非严格必要，但这种方法提供了额外的错误检查层次。

通过将对 `addItem()`、`getItem()` 和 `removeItem()` 的所有调用都包装在 `try...catch` 块中，您可以完全控制这些方法中可能发生的任何错误。请务必使用比示例中所示的 `die()` 调用更优雅的方式来处理这些错误。

回调是一种非常强大的技术，您可以使用它来实现惰性实例化，这可以节省系统资源，并确保您只操作绝对必要的数据。当您拥有复杂的对象层次结构时，可以使用回调来自动处理子对象的实例化，并推迟创建当前应用程序活动不绝对必要的那些对象。请务必了解此工作原理，并看看能否为这种技术找到其他用途。

第 6 章介绍了一个强大的数据库抽象扩展，这是作者访问关系数据库并避免与使用 PHP 的本机 PostgreSQL（或 MySQL、Oracle 或其他）函数相关的一些陷阱的首选方式。

## 使用 PDO 进行数据库抽象

您将要构建的几乎每个严肃的 Web 应用程序都会使用某种数据存储机制。这种数据存储通常用于存储应用程序设置、用户注册、动态内容——基本上是应用程序中任何将是动态的内容（即，它可能会在某个阶段发生变化，无论是由于您的某个用户的操作，还是由于拥有该应用程序的业务发生变化所致）。

对于除非常小型应用程序以外的所有应用程序，数据存储的公认选择通常是关系数据库管理系统（RDBMS）。其优势显而易见：可扩展性、易于查询、可靠性、韧性、数据完整性——还有更多。如果您希望除 PHP 以外的任何东西能够访问您的数据，这也是几乎必不可少的。通过为您的数据使用与平台无关的容器，您就不会人为地限制自己，例如，如果您有一天确定一个 .NET 应用程序也可能需要使用该数据。

诚然，“PHP 和数据库”的组合如此普及，以至于几乎所有初学者的书籍都在第一章就介绍 MySQL 数据库。LAMP（Linux、Apache、MySQL 和 PHP）这个缩写近年来不断出现——在 Google 上搜索“PHP and MySQL”短语可获得超过 200 万个结果。

不幸的是，与 PHP 中的许多事情一样，大多数人在 PHP 教育早期学习使用数据库的方式很少被视为最佳实践。构建可伸缩、可扩展、易于移植且易于维护的应用程序需要一种不同的方法。

在本章中，您将学习到正是这样。您将从回顾 PHP 的数据库支持开始，并提醒自己自多年前 PHP 推出以来数据库连接一直是如何处理的。通过考虑假设性示例，您将了解这种方法的局限性。然后，您将认识 PHP 数据对象（PDO），并学习 PDO 如何提供一种更适合企业级的方法。

### PHP 与数据库

自 PHP 3 初期以来，PHP 对关系数据库管理系统（RDBMS）享有广泛支持。与一些较旧的 Web 应用程序开发技术（尤其是 PERL）并非专门为此构建，以及一些其他技术（尤其是 Java）在 Web 开发之外拥有更广泛的吸引力不同，PHP 专门用于构建数据库驱动的 Web 应用程序。

### PHP 的数据库支持

开箱即用，PHP 可以支持 20 多种不同的关系数据库管理系统（RDBMS），各个供应商经常发布他们自己的 PHP 扩展。所有流行的版本都得到了支持，包括——也许最重要的是——四大数据库：MySQL、Oracle、SQL Server 和 PostgreSQL。

尽管很有用，但 PHP 中的数据库支持被视为扩展。这意味着它不被视为核心语言的一部分，因此必须在编译期间（在 UNIX 平台上）或运行时（在 Windows 平台上）通过在 php.ini 中启用相应的 DLL 来启用。

启动每个受支持的关系数据库管理系统（RDBMS）的技术在给定的 PHP 安装中各不相同。以下网址涉及非常有用的 php.net 参考网站：

- [ ] MySQL — http://uk.php.net/manual/en/mysql.installation.php
- [ ] PostgreSQL — http://uk.php.net/manual/en/pgsql.installation.php
- [ ] MS SQL Server — http://uk.php.net/manual/en/mssql.installation.php
- [ ] Oracle — http://uk.php.net/manual/en/oci8.setup.php

您可以通过使用 phpinfo() 语句轻松确定 PHP 安装中启用了哪些数据库支持。

打开您喜欢的文本编辑器，新建一个名为 phpinfo.php 的 PHP 文档。输入以下内容：

```php
<?php
phpinfo();
?>
```

现在启动 Web 浏览器并将其指向您刚刚创建的脚本。运气好的话，您将看到 PHP 配置的完整详细信息。使用浏览器的搜索功能，根据情况查找字符串 mysql、postgresql、mssql 或 oci8。如果您找到带有该标题的部分，那么您的 PHP 构建很可能已启用对该数据库的支持。

如果没有，是时候重新安装了。幸运的是，您会在附录 D 中找到相关信息，您将在其中了解在 Linux、Mac OS X 甚至 Windows 上安装 PHP 和 Apache 的最佳实践。

### PHP 与 PostgreSQL

这是本书中第一个涵盖数据库连接的章节。几乎每个后续章节都会以某种方式涉及它——考虑到这是一本关于 PHP 企业级开发的书，这也不足为奇。

