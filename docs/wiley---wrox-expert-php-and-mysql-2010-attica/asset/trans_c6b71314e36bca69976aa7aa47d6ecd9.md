
```
if ( $result )
    while ( $row = mysql_fetch_assoc($result) ) {
        // Execute logic or display row
    }
?>
```

这种突出显示的方法仅对最基本的 PHP 应用有益。当开始处理更大规模的数据集时，问题就会出现。请考虑一些常见的用例：

## 用例

以下用例说明了两位用户：一位管理库存，另一位想要浏览列表。

### Sue 需要管理书籍

Sue 已经运营读书俱乐部八年了，她希望将所有书籍在线展示，以便会员可以查看。她需要通过图书管理页面来管理库存，在该页面上她可以阅读前 20 本书。页面顶部可以看到总共有 75 本书。总共有四页。页面底部可以点击直接跳转到任意一页。每本书的右侧可以点击删除或编辑。

### Jane 想浏览读书俱乐部书籍

Jane 是读书俱乐部的会员，想要浏览书籍列表。她导航到一个页面，该页面上有 10 条图书结果。页面顶部可以看到总共有 75 条结果。页面底部可以从 1 到 8 跳转到任意页面，或点击 Next 直接进入下一页。

通常用于查询 MySQL 的基本过程式代码过于简单，无法实用。为了支持 Jane 的用例，必须在示例中添加更多代码。这个简单示例很快就会变得难以管理。对于单人团队来说这可能可以接受。然而，更大的团队会遇到严重问题。它要求设计视图的开发者了解书籍在数据库中存储的细节，并且使得更改底层存储机制变得困难。

Sue 的用例引入了一个略有不同的页面，但它共享许多相同的功能。在该页面上，她也在查看书籍列表。然而，她每页列出 20 本书，而不是 Jane 的 10 本，并且她还有一些额外的管理选项。利用这两个用例，你可以得到示例应用的需求列表：

- 应用必须便于浏览长度可变的书籍集合。
- 结果必须按每页任意数量的结果进行分页。你可以默认为 10。
- 如果结果尚未需要，就不应该从数据库中获取。并非所有书籍同时显示。相反，你也不应获取少于所需的数据，以避免过多的数据库调用。
- 业务逻辑应分离到可以被两个视图轻松重用的类中。
- 开发者必须能够轻松地遍历列表并从每本书中检索数据。
- 开发者无需担心如何分页列表或底层数据库的细节。存储机制可以随时更改，而不会破坏任一视图。

最后两项实际上并非来自用例。然而，当处理中型到大型团队或开源项目时，它们同样重要。原则上，逻辑业务单元应始终分离到类中。通过这样做，你创建了一种标准且易于理解的方法来访问和修改数据。这种方法可以缩短开发时间，降低维护成本，并缩短新加入团队的开发者学习曲线。在项目开始时考虑这些目标总是比等到代码库变大后再考虑更容易。你将使用迭代器和闭包来实现这些目标。

## 迭代器与 SPL

迭代器为 PHP 提供了一种使用 foreach 循环遍历任意数据集的方法。SPL 中存在预定义的迭代器，用于遍历数组、目录和 XML。迭代器的另一个常见用途，也是本章将实现的内容，就是遍历 MySQL 结果集。你还将使用 SPL 中的其他几个接口为你的对象创建类似数组的功能。

你还将创建三个新类：

- 一个检索数据的类
- 一个扩展 SPL 类之一以提供分页功能的类
- 一个存储、修改和访问书籍信息的 Book 类

### 应用的示例视图

你将使用 MySQL 作为数据库连接器以简化应用需求。该应用要求服务器运行 PHP 5.3 并使用 MySQL 原生驱动编译（将在下一章介绍）。该应用的视图可能如下所示：

```php
<?php
$dbConn = new mysqli('localhost', 'mysql_user', 'mysql_password', 'bookclub');

$booksPerPage = 10;
$page = ( isset($_GET['page']) ? $_GET['page'] : 1 );

$bookList = new BookList($dbConn);
$bookPage = new Page($bookList, $page, $booksPerPage);
?>
```

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head><title>Book Club List</title> </head>
<body>
    <p>
        Showing books
        <?php
        printf('%d-%d of %d', $page->getFirstIndex(),
            $page->getLastIndex(), count($bookList) );
        ?>
    </p>
    <table>
        <thead>
            <th>Title</th>
            <th>Author</th>
            <th>Publisher</th>
        </thead>
        <tbody>
<?php
foreach ( $bookPage as $key => $book ) {
    printf('    <tr><td>%s</td><td>%s</td><td>%s</td></tr>\n',
        $book->title, $book->authors, $book->publisher);
}
?>
        </tbody>
    </table>
    <ul class="pages">
<?php
$totalPages = ceil(count($bookList)/$booksPerPage);
if ( $page > 1 )
    printf('    <li><a href="?page=%d">Prev</a></li>\n', $page-1);

for ( $i=1; $i <= $totalPages; $i++ ) {
    if ( $i == $page )
        printf('    <li>%d</li>\n', $i);
    else
        printf('    <li><a href="?page=%d">%d</a></li>\n', $i, $i);
}

if ( $page < $totalPages )
    printf('    <li><a href="?page=%d">Next</a></li>\n', $page+1);
?>
    </ul>
</body>
</html>
```

此视图满足该应用的所有主要需求。它在顶部显示总结果数，然后是图书结果表，最后如果访客尚未在最后一页，则显示页面列表和 Next 按钮。它还生成有效的 XHTML。遵循标记标准有助于设计师创建外观更好的页面并保持代码质量高。它还有一个好处是如果需要，可以使用 PHP DOM 对象打开页面。本书中的所有示例如果其输出面向 Web 浏览器，则都符合 XHTML 1.0 Strict。

为此读书俱乐部编写视图的开发者无需了解数据如何存储，并且可以使用标准的 foreach 循环为每本书打印一行。在项目开发早期，在完成对真实数据的访问之前，用虚拟数据填充应用是很常见的。这在大型团队中尤其如此，因为多个组可能会编写密切相关的代码。使用 PHP 中可用的标准设计模式可确保每个团队保持一致。

示例视图展示的另一个好处是能够使用 count($bookList) 来检索底层查询返回的书籍总数。Page 和 BookList 类都可以看起来并表现得像 PHP 中的标准数组一样。这种能力正是 SPL 如此强大的原因之一。

你将要构建的第一个迭代器是如列表 2-1 所示的 BookList 类。它将作为所有 MySQL 选择功能的包装器。在开始之前，你需要创建存储书籍的表并设计一个查询，以获取你可以使用格式的所有书籍：

### 列表 2-1: bookclub.sql

```
CREATE TABLE books ( id INT AUTO_INCREMENT PRIMARY KEY,
    ISBN VARCHAR(20) UNIQUE,
    title VARCHAR(50), publisher INT );
CREATE TABLE book_authors ( bookid INT, authorid INT,
    PRIMARY KEY (bookid,authorid) );
CREATE TABLE authors ( id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(20) );
CREATE TABLE publishers ( id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(20) );

SELECT `ISBN`, `title`, (
    SELECT GROUP_CONCAT( `name` )
    FROM `book_authors` AS t2
    JOIN `authors` AS t3 ON t2.authorid = t3.id
    WHERE t2.bookid = t1.id
    GROUP BY `bookid`
) AS `author`, `t4`.`name` AS publisher
FROM `books` AS t1
JOIN `publishers` AS t4 ON t1.publisher = t4.id;
```

现在数据库表已创建，是时候编写更多 PHP 代码了。如前所述，SPL 中的许多功能由接口提供。BookList 需要为此简单应用实现三个接口。完成后，新类将既健壮又可重用，几乎适用于应用中任何需要书籍列表的情况。相同的模式可以应用于任何类型的数据。

### Iterator 接口

第一个要实现的接口是恰如其名 Iterator 接口。Iterator 接口提供了一组五个方法，必须实现这些方法才能使迭代与内置 PHP
