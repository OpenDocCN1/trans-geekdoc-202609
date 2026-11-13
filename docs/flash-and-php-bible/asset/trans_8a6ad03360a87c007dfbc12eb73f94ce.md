

### 图 17.2

Example of the video player design you will be working with in this chapter

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_454_0.png)

## 构建数据库和 MySQL 表

首先，打开您喜欢的数据库编辑器，为本项目创建一个新数据库。您可以随意命名此数据库。我使用了 `book_videoplayer`，但这只是一个建议。

数据库创建完成后，您可以开始添加视频和分类数据的表架构结构。对于此应用程序，表已经定义好了，但欢迎您查看它们以更好地了解它们各自负责的内容。

此应用程序中的表被拆分，以确保其经过优化，并能轻松了解哪个表负责每个任务。最好将功能拆分到多个表中，这也称为规范化。这样做可确保您的数据库最高效，并允许其扩展。

此应用程序中的表结构非常简单直接。例如，视频名称、描述和源引用位于 videos 表中，该表的构建方式类似于以下内容：

```sql
CREATE TABLE `videos` (
`id` int(11) NOT NULL auto_increment,
`catId` int(11) default NULL,
`name` varchar(200) default NULL,
`src` varchar(200) default NULL,
`description` text,
`count` int(11) default 0,
`active` varchar(1) default '1',
PRIMARY KEY (`id`)
) ENGINE=MyISAM;
```

如您所见，这个表并无特别之处，但它处理了应用程序管理的核心部分。如果您决定要扩展原始应用程序，可以添加更多列。

数据库不是唯一的存储选项。您可以使用 XML 文件，甚至在 Flash 中硬编码视频路径，但理念是开发一个可扩展的应用程序。这意味着数据库是存储视频和分类数据的最合理选项。数据库还提供随着应用程序添加更多功能而扩展和增长的能力。

您需要添加的第二个表是 categories 表，它存储下一节 PHP 中使用的 ID 以及在 Flash 应用程序中显示的类别名称。

```sql
CREATE TABLE `categories` (
`id` int(11) NOT NULL auto_increment,
`name` varchar(100) default NULL,
`active` varchar(1) default '1',
PRIMARY KEY (`id`)
) ENGINE=MyISAM;
```

## 向表中添加示例数据

现在可以预填充表以进行全部测试，如图 17.3 所示。您可以使用喜欢的数据库编辑器手动添加示例数据，或使用以下添加一些类别和视频的示例 INSERT 语句：

```sql
INSERT INTO categories (name) VALUES ('Category 1');
INSERT INTO categories (name) VALUES ('Category 2');
INSERT INTO videos (catId, name, src, description)
VALUES (1, 'Sample Video 0:1', 'sample.flv', 'Cool Video Here');
INSERT INTO videos (catId, name, src, description)
VALUES (2, 'Sample Video 0:2', 'sample.flv', 'Cool Video Here');
```

### 图 17.3 MySQL 查询浏览器中显示的示例表数据

![](img/d9d48cd53eee0fbc1ebc363c322fac2c_456_0.png)

## 测试数据库

将数据加载到数据库后，您可以对其进行测试。可以通过构建一个连接数据库并运行非常简单查询的简单 PHP 文件来完成此操作。您在之前的章节中已经学习了如何连接数据库。对于本示例，您需要定义连接详细信息并调用 mysql_connect 函数。

```php
<?php

$link = mysql_connect('localhost', 'root', 'password');
mysql_select_db('book_videoplayer', $link);

$catID = 1;
$query = sprintf("SELECT * FROM categories where id=%d", $catID);

$result = mysql_query($query, $link);
$row = mysql_fetch_array($result);

print "Category Name: <strong>" . $row['name'] . "</strong>";

?>
```

将此文件保存为 Web 服务器主目录中的 sqltest.php，并使用喜欢的 Web 浏览器调用它。执行 PHP 文件后，您应该会看到类似以下的输出：

类别名称: 类别 1

如果看到其他内容，请确保检查连接详细信息。如果出于某些原因您看到空白页，请在文件顶部放置以下行，以强制 PHP 显示所有潜在错误：

```php
error_reporting(E_ALL);
```

现在您已经看到使用本应用程序数据运行的简单 MySQL 查询，请尝试调用两个表并测试最终应用程序将具有的功能。需要修改的只有两行代码：SQL 查询和输出。

```php
<?php

$link = mysql_connect('localhost', 'root', 'password');
mysql_select_db('book_videoplayer', $link);

$catID = 1;
$query = sprintf("SELECT v.name FROM videos v, categories c WHERE
v.catID=c.id AND c.id=%d", $catID);

$result = mysql_query($query, $link);

while($row = mysql_fetch_array($result))
{
    print "Video Name: " . "<strong>" . $row['name'] . "</strong>";
}
?>
```

运行此代码时，您将看到该特定类别的视频列表。此代码会搜索类别和视频表，并返回共享相同 ID 的所有视频。这是 MySQL 表中最基本的连接，但对于此应用程序来说它非常完美。

## 远程集成

下一步是构建实际将由 Flash 使用远程方式调用的 PHP。事实上，本部分的相似之处在于您将使用 AMFPHP。但除此之外的实际开发部分有所不同。

> 交叉引用：第 8 章中可找到有关远程的更多信息。

使用远程方式构建此应用程序的优势在于，它使您能够更轻松地进行测试。这是因为您可以构建 AMFPHP 类，然后使用标准 PHP 代码或随 AMFPHP 附带的浏览器查看器对其进行测试。

您还可以在其他项目或同一项目的 HTML 部分中重用这些类。例如，假设您想构建一个可显示特定类别中最新电影的用户面板。您可以通过构建一个非常基本的 HTML 页面并调用远程类来返回所需数据，就像在 Flash 中所做的那样。

## 数据库连接器类

此应用程序中的类依赖于数据库。与其在每个类中定义连接详细信息，不如构建一个负责建立初始连接和存储连接凭据的数据库连接器类。

连接器类有五个私有变量。前四个定义连接信息。

```php
<?php

class DatabaseConnector
{

    private $host   = "localhost";
    private $user   = "root";
    private $pass   = "password";
    private $dbName = "book_videoplayer";

}

?>
```

第五个变量用于存储数据库链接资源 ID。

```php
private $link = null;
```

此类的构造函数为空，因为私有变量之前已定义。

```php
function DatabaseConnector() { }
```

仅在未找到现有连接时才会调用私有 connect 方法。此方法传入私有连接详细信息，并将资源 ID 存储在仅此类可见的 $this->link 属性中。

```php
private function connect()
{
    $this->link = mysql_connect($this->host, $this->user, $this->pass);
    mysql_select_db($this->dbName, $this->link);
}
```

第二个方法 getConnection 设置为公共，以便其他类可以访问它。但是，注释将其定义为私有，以确保远程类无法访问它。此方法首先检查现有连接资源，如果未找到，则调用 connect 方法。

此函数的最后一步是返回活动连接资源，该资源将在其他类中使用。

```php
/**
 * Get database connection
 * @access private
 * @returns database link, to be used in other sql calls
 */
public function getConnection()
{
    if($this->link == null)
    {
        $this->connect();
    }

    return $this->link;
}
```

如您所见，此类非常实用，因为它负责存储数据库连接。此外，如果未找到连接，它会创建一个。

以下是完成的类，应将其保存为项目目录中的 DatabaseConnector.php，以便其他类可以访问它。

