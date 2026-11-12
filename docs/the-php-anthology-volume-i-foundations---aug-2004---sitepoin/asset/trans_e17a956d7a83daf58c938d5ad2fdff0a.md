

/*
function getStartRow()
{
    return $this->startRow;
}
}
*/

我们只需在实例化此类时，将相关行信息以及当前正在查看的页码传递给它。它随后会告诉我们总页数以及应从哪个行号开始执行select查询。

下面是它的实际应用：

```
File: 3.php (excerpt)
// Instantiate MySQL connection
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

// Find out how many rows are available
$sql = "SELECT COUNT(*) AS num_rows FROM user";
$result = $db->query($sql);
$row = $result->fetch();

// Define the number of rows per page
$rowsPerPage = 10;

// Set a default page number
if (!isset($_GET['page'])) {
    $_GET['page'] = 1;
}

// Instantiate the pager
$pager = new SimplePager($rowsPerPage, $row['num_rows'],
    $_GET['page']);

// Build a table for the pager
echo "<table align=\"center\"/>\n<tr>\n";

// Build the HTML for the pager
for ($i = 1; $i <= $pager->getTotalPages(); $i++) {
    echo "<td><a href=\"" . $_SERVER['PHP_SELF'] . "?page=$i\">";
    if ($i == $_GET['page']) {
        echo "<strong>$i</strong>";
    } else {
        echo $i;
    }
    echo "</a></td>\n";
}
echo "</tr>\n</table>\n";
```

请注意，我们在用于构建页间导航链接的for循环中使用了getTotalPages方法。

在页面准备就绪且HTML构建完成后，我们现在可以利用getStartRow方法来创建结果表格：

```
File: 3.php (excerpt)

// Now construct the "real" SQL statement
$sql = "SELECT * FROM user
LIMIT " . $Pager->getStartRow() . ", " . $rowsPerPage;

// Fetch and display the results
$result = $db->query($sql);

echo "<table align=\"center\">\n";
echo "<tr>\n<th>Login</th><th>Name</th><th>Email</th>\n</tr>";

while ($row = $result->fetch()) {
    echo "<tr>\n";
    echo "<td>" . $row['login'] . "</td>";
    echo "<td>" . $row['firstName'] . " " . $row['lastName'] . "</td>";
    echo "<td>" . $row['email'] . "</td>\n";
    echo "</tr>\n";
}
echo "</table>";
```

我们现在可以每次显示十行来分页浏览用户表格。这是一个不错的开端，但代码有些凌乱。它还缺少一些功能，例如仅需点击“下一页”或“上一页”即可前进或后退一页的能力。并且一次显示的页数没有限制（对于大型表格，可能会有数百页，这会导致网页显得不美观）。

## 滑动页码

PEAR提供了另一个名为PEAR::Pager_Sliding[2]的实用包。由Lorenzo Alberton编写，Pager_Sliding将计算和链接构建结合在一个易于使用的类中。此处使用的版本为1.4。

- [2] http://pear.php.net/Pager_Sliding

该类并未提供我们想要的一切，因此我们首先需要一个扩展Pager_Sliding类以提供额外信息的类。顺便提一下，这使用了**继承**（有关更多信息，请参见第2章）。

```
/**
 * DB_Pager_Sliding - extends PEAR::Pager_Sliding
 * Provides an API to help build query result pagers
 * @access public
 * @package SPLIB
 */
class DB_Pager_Sliding extends Pager_Sliding {
    /**
     * DB_Pager_Sliding constructor
     * @param array params for parent
     * @access public
     */
    function DB_Pager_Sliding($params)
    {
        parent::Pager_Sliding($params);
    }

    /**
     * Returns the number of rows per page
     * @access public
     * @return int
     */
    function getRowsPerPage()
    {
        return $this->_perPage;
    }

    /**
     * The row number to start a SELECT from
     * @access public
     * @return int
     */
    function getStartRow()
    {
        if ($this->_currentPage == 0) {
            return $this->_perPage;
        } else {
            return ($this->_currentPage - 1) * $this->_perPage;
        }
    }
}
```

这个扩展类提供了构建查询所需的信息。现在，让我们将分页器添加到在“如何在表格中显示数据？”中构建的用户表格：

```
// Include the PEAR::HTML_Pager_Sliding class
require_once 'HTML/Sliding.php';

// Include the extended class
require_once 'DB_Pager_Sliding.php';

// Instantiate MySQL
$db = &new MySQL($host, $dbUser, $dbPass, $dbName);

$sql = "SELECT COUNT(*) AS num_rows FROM user";
$result = $db->query($sql);
$row = $result->fetch();

// Define pager settings
$pager_params = array(
  // The total number of rows
  'totalItems' => $row['num_rows'],
  // Rows per page
  'perPage' => 10,
  // The size of the sliding Window +/-.
  'delta' => 2,
  // Separator and spacing between links
  'separator' => ' . . ',
  'spacesBeforeSeparator' => 2,
  'spacesAfterSeparator' => 2,
  // The $_GET variable name
  'urlVar' => 'page',
  // Browser status bar text
  'altPrev' => 'Previous Page',
  'altNext' => 'Next Page',
  'altPage' => 'Page: ',
  // CSS Class names
  'curPageLinkClassName' => 'currentPage',
  'linkClass' => 'pageLink',
);

// Instantiate the pager
$pager = &new DB_Pager_Sliding($pager_params);

// Fetch the HTML links
$links = $pager->getLinks();
```

现在我们可以修改查询，以使用分页器生成的LIMIT子句：

```
// Basic SQL statement
$sql = "SELECT * FROM user";

// A switch to allow sorting by column
switch (@$_GET['sort']) {
    case 'login':
    $sql .= " ORDER BY login ASC";
    break;
    case 'email':
    $sql .= " ORDER BY email ASC";
    break;
    default:
    $sql .= " ORDER BY lastName, firstName ASC";
    break;
}

// Add the LIMIT clause
$sql .= " LIMIT " . $pager->getStartRow() . ", " .
    $pager->getRowsPerPage();
```

现在剩下的就是定义在分页器设置中指定的CSS类currentPage和pageLink，并在表格下方显示链接：

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title> Users </title>
<meta http-equiv="Content-Type"
content="text/html; charset=iso-8859-1" />
<style type="text/css">
.currentPage
{
 font-family: verdana;
 font-size: 10px;
 font-weight: bold;
 color: red;
}
.pageLink
{
 font-family: verdana;
 font-size: 10px;
 color: red;
}
</style>
</head>
<body>
<?php
// Display the table
echo $table->toHTML();
?>
<div align="center">
<?php
// Display the paging links
echo $links['all'];
?>
</div>
</body>
</html>
```

请注意，此处未复现构建表格的代码，但请放心，您将在与此解决方案关联的代码存档中找到它。

Pager_Sliding类在数组中提供已构建的链接。我们可以单独访问每个链接（如果想更精确地控制分页器在页面上的位置，这很有用），也可以像这里所示使用$links['all']显示完整的分页器。

完成的表格及其后的分页链接如图9.2所示。

## 图9.2. 分页显示所有用户...

| 登录名 | 姓名 | 电子邮件 |
|---|---|---|
| hwilliams | Hale Williams | hwilliams@mysql.com |
| jschwarzenegger | John Schwarzenegger | jschwarzenegger@hotmail.com |
| jwillis | John Willis | jwillis@mysql.com |
| mmoore | Madeline Moore | mmoore@php.net |
| mschwarzenegger | Madeline Schwarzenegger | mschwarzenegger@yahoo.co.uk |
| mtravolta | Madeline Travolta | mtravolta@mysql.com |
| rtravolta | Robin Travolta | rtravolta@hotmail.com |
| rwillis | Robin Willis | rwillis@mysql.com |

Pager_Sliding类的妙处在于，它显示的页码范围会随访客当前所在页面而变化。随着表格的增长，导航依然简便。在处理大型结果集时这一点至关重要；例如，如果查询返回超过十页的结果，没有“滑动分页器”，你的网页上将不得不显示一长串页码，这既难看又难以导航。Pager_Sliding类可帮助你实现类似于Google[3]使用的分页器，搜索通常会返回数百页的结果。

## 如何在PHP中处理HTML表单？

> “能力越大，责任越大。”
> —蜘蛛侠的本叔

与链接和URL相比，HTML表单提供了一种功能强大得多的机制，用于接收网站访客的信息。表单允许你开发复杂的界面，例如，使用户能够从动态生成的列表中选择值、输入大段文本，甚至上传文件。表单使从简单的留言本到复杂的用户注册和身份验证系统等一切成为可能。但功能增强也带来了更广泛的问题。你如何验证表单？如果表单填写不正确，应当如何处理？如何使用数据库中的数据填充表单？在处理表单时，你将面临这些挑战中的几个；还有更多。

### HTTP请求方法

因特网使用的HTTP协议（通常用于获取网页）定义了许多“方法”，浏览器可使用这些方法向Web服务器发送请求和数据。在可用方法中，最重要的是GET方法和POST方法。

- GET是因特网的“默认”方法，每当你使用浏览器请求页面时都会使用。请求中的所有数据必须编码到URL中。
- POST最常用于提交表单。它允许随请求一起发送额外的表单数据。

HTML允许你为每个表单标签指定要使用的方法。虽然GET是默认方法，但最常用的是POST，因为它避免了将提交的数据添加到URL中，从而避免URL过于杂乱。

- [3] http://www.google.com/

