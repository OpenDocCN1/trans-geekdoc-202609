

<?php
class DatabaseConnector
{
    private $host = "localhost";
    private $user = "root";
    private $pass = "password";
    private $dbName = "book_videoplayer";

    private $link = null;

    function DatabaseConnector() { }

    private function connect()
    {
        $this->link = mysql_connect(
            $this->host,
            $this->user,
            $this->pass
        );
        mysql_select_db($this->dbName, $this->link);
    }

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
}
?>

## 视频类

既然数据库连接器类已完成，接下来要开发的类是用于管理视频的。该类根据视频 ID 或类别 ID 返回视频列表。

此类的第一部分是加载数据库连接器文件，Videos 类将继承该文件。

```php
<?php

require_once 'DatabaseConnector.php';

?>
```

你可能还记得在之前的示例中开发的 ActionScript 类中的 extends。

PHP 的语法相同。基本上，定义类及其要扩展的类，类似如下所示：

```php
<?php

require_once 'DatabaseConnector.php';

class Videos extends DatabaseConnector
{
}

?>
```

视频类具有一个方法 getVideos。该方法将视频 ID 和类别 ID 作为单独的参数，以确定要返回哪些视频。

```
/**
 * get videos
 *
 * @access remote
 *
 * @returns array of videos
 *
 */
function getVideos($categoryID=-1, $videoID=-1)
{
    ...
}
```

此方法的第一部分需要检查有效 ID，以确保 SQL 不会被破坏。此步骤不是必需的，但可确保您的应用程序更安全。

```
if($categoryID == -1 || strlen($categoryID) == 0)
{
    trigger_error("Category ID required to return video list");
}
```

如果传入无效或缺失的类别 ID，此语句将调用 trigger_error。使用 trigger_error 的原因是 AMFPHP 会优雅地停止所有进一步处理，并将所需错误返回到调用脚本，在此示例中即为 ActionScript。

下一步是为此方法分配变量，并创建一个数组来保存将传回给 ActionScript 的视频数据。

```
$vidSQL = "";
$rows = array();
```

一旦基本内容已定义，下一步是确定脚本是查找单个视频还是查找列表。如果代码只应查找一个视频，则此步骤会分配正确的 SQL。

```
// look for specific video?
if($videoID != -1 && strlen($videoID) != 0)
{
$vidSQL = " AND v.id=" . $videoID;
}
```

只需调用 DatabaseConnector 类的 getConnection 方法即可定义数据库链接，因为视频类正在扩展该类。局部 $link 变量将分配给活动连接，以供此函数中其余的 MySQL 交互使用。

```
$link = $this->getConnection();
```

数据库查询相当复杂，因为它检查两个表中的数据，并根据该检查返回一个视频列表。此查询与您在本节开头测试数据库时构建的查询类似。此查询使用 $vidSQL，当不查找特定视频时，它将是 SQL 的有效补充或空字符串。

```
$query = sprintf("SELECT
v.name,
v.src,
v.id as 'vid',
c.name as 'cat',
v.description,
v.count
FROM categories c, videos v
WHERE v.catId=c.id
AND v.catId=%d
AND v.active=1 " . $vidSQL, $categoryID);
```

此 SQL 查询的特殊部分是修改列名，例如

```
v.id as 'vid'
```

这样做是因为结果集在两个表中都具有名称 id，且只能返回一个名称。如果保留标准命名，您只能访问一个表的 id 信息。哪个会被返回取决于调用顺序。重命名仅修改结果集，因此您无需担心原始数据受到影响。

下一步是运行 MySQL 查询并检索结果，然后遍历结果并将其作为多维数组传出函数。

```
$result = mysql_query($query, $link);
```

在运行循环之前，最好确保查询返回了一些行。不进行此简单检查可能会导致无限循环。这可能会损害 Web 服务器，因为您很可能不会意识到它正在发生。

此简单检查是通过使用 mysql_num_rows 函数检查返回的行数来完成的。该函数返回一个数值，表示查询中返回的行数。

```
if(mysql_num_rows($result) == 0)
{
    trigger_error("No videos found");
    return false;
}
```

假设找到了有效的结果集，下一步是遍历结果并填充之前定义的数组变量。

```
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    array_push($rows, $row);
}
```

此函数的最后一步是返回视频数据数组。除非有有效的视频数据准备传回，否则该方法不会到达此点。

```
return $rows;
```

这就是视频类的全部内容。此文件应保存为 Videos.php。这是完成的类，也可以在图书网站上的代码中找到。

```php
<?php
require_once 'DatabaseConnector.php';

class Videos extends DatabaseConnector
{

/**
* get videos
* @access remote
* @returns array of videos
*/
function getVideos($categoryID=-1, $videoID=-1)
{
    if($categoryID == -1 || strlen($categoryID) == 0)
    {
    trigger_error("Category ID required to return video list");
    }
    $vidSQL = "";
    $rows = array();
    // look for specific video?
    if($videoID != -1 && strlen($videoID) != 0)
    {
    $vidSQL = " AND v.id=" . $videoID;
    }
    $link = $this->getConnection();
    $query = sprintf("SELECT
    v.name,
    v.src,
    v.id as 'vid',
    c.name as 'cat',
    v.description,
    v.count
    FROM categories c, videos v
    WHERE v.catId=c.id
    AND v.catId=%d
    AND v.active=1 " . $vidSQL, $categoryID);
    $result = mysql_query($query, $link);
    if(mysql_num_rows($result) == 0)
    {
    trigger_error("No videos found");
    return false;
    }
    while($row = mysql_fetch_array($result, MYSQL_ASSOC))
    {
    array_push($rows, $row);
    }
    return $rows;
    }
}
?>
```

本示例的第二个类是类别类，它也具有一个方法。该方法负责将所有活动类别返回到视频播放器。

在创建方法之前，必须加载数据库连接，与您在视频类中所做的完全一样。

```
require_once 'DatabaseConnector.php';
```

getCategories 方法的第一部分负责创建一个新的 $rows 变量，用于保存从数据库返回的类别。link 变量填充有活动数据库连接，将在后续 SQL 调用中使用。

```
$rows = array();
$link = $this->getConnection();
```

SQL 查询基本上提取所有活动类别，即 active 列设置为值 1。然后将此 SQL 查询传递给 mysql_query，后者负责实际执行 SQL 调用。

```
$query = "SELECT id, name FROM categories WHERE active=1";
$result = mysql_query($query, $link);
```

if 语句在继续之前会检查至少一个有效行，如果未找到有效行，则会抛出错误。假设找到了有效行，则使用 while 循环填充 $rows 变量，循环完成后返回 $rows 变量。

```
if (mysql_num_rows($result) == 0)
{
    trigger_error("No categories found");
    return false;
}
```

```
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    array_push($rows, $row);
}
```

```
return $rows;
```

这就是类别类的全部内容，如您所见，类别类的结构与前一节中的视频类非常相似。

以下是完成的类别类：

```php
<?php

require_once 'DatabaseConnector.php';

class Categories extends DatabaseConnector
{

    /**
     * get categories
```

