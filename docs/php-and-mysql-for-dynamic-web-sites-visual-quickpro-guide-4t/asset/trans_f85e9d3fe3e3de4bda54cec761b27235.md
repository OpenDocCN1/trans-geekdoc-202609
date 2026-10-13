
本示例对一个简单查询进行了分页，但如果你想对更复杂的查询（如搜索结果）进行分页，难度也不会增加太多。主要的区别在于，查询中使用的任何条件都必须通过链接从一页传递到下一页。如果从一次页面查看到下一次，主查询不是*完全相同*的，分页就会失败。

***

提示

如果你运行此示例，发现分页与本应返回的结果数量不匹配（例如，计数查询显示有 150 条记录，但分页只创建了 3 页，每页 10 条记录），这很可能是因为主查询和 `COUNT()` 查询差异太大。这两个查询永远不会完全相同，但它们必须执行相同的连接（如果适用），并且拥有相同的 `WHERE` 和/或 `GROUP BY` 子句，才能保证准确性。

***

提示

本脚本未包含错误处理，因为我知道这些查询按原样编写即可运行。如果你遇到问题，请记住你的 MySQL/SQL 调试步骤：打印查询语句，使用 mysql 客户端或 phpMyAdmin 运行它以确认结果，并根据需要调用 `mysqli_error()` 函数。

***

**脚本 10.5.** `view_users.php` 脚本的最新版本将表格的列标题变为可点击的链接。

***

```php
<?php # Script 10.5 - view_users.php #5
// This script retrieves all the records
// from the users table.
// This new version allows the results
// to be sorted in different ways.

$page_title = 'View the Current Users';
include ('includes/header.html');
echo '<h1>Registered Users</h1>';

require_once ('../mysqli_connect.php');

// Number of records to show per page:
$display = 10;

// Determine how many pages there are...
if (isset($_GET['p']) && is_numeric($_GET['p'])) { // Already been determined.
    $pages = $_GET['p'];
} else { // Need to determine.
    // Count the number of records:
    $q = "SELECT COUNT(user_id) FROM users";
    $r = @mysqli_query ($dbc, $q);
    $row = @mysqli_fetch_array ($r, MYSQLI_NUM);
    $records = $row[0];
    // Calculate the number of pages...
    if ($records > $display) { // More than 1 page.
        $pages = ceil ($records/$display);
    } else {
        $pages = 1;
    }
} // End of p IF.

// Determine where in the database to start returning results...
if (isset($_GET['s']) && is_numeric($_GET['s'])) {
    $start = $_GET['s'];
} else {
    $start = 0;
}

// Determine the sort...
// Default is by registration date.
$sort = (isset($_GET['sort'])) ? $_GET['sort'] : 'rd';

// Determine the sorting order:
switch ($sort) {
    case 'ln':
        $order_by = 'last_name ASC';
        break;
    case 'fn':
        $order_by = 'first_name ASC';
        break;
    case 'rd':
        $order_by = 'registration_date ASC';
        break;
    default:
        $order_by = 'registration_date ASC';
        $sort = 'rd';
        break;
}

// Define the query:
$q = "SELECT last_name, first_name, DATE_FORMAT(registration_date, '%M %d, %Y') AS dr, user_id FROM users ORDER BY $order_by LIMIT $start, $display";
$r = @mysqli_query ($dbc, $q); // Run the query.

// Table header:
echo '<table align="center" cellspacing="0" cellpadding="5" width="75%">
<tr>
    <td align="left"><b>Edit</b></td>
    <td align="left"><b>Delete</b></td>
    <td align="left"><b><a href="view_users.php?sort=ln">Last Name</a></b></td>
    <td align="left"><b><a href="view_users.php?sort=fn">First Name</a></b></td>
    <td align="left"><b><a href="view_users.php?sort=rd">Date Registered</a></b></td>
</tr>
';

// Fetch and print all the records....
$bg = '#eeeeee';
while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
    $bg = ($bg == '#eeeeee' ? '#ffffff' : '#eeeeee');
    echo '<tr bgcolor="' . $bg . '">
    <td align="left"><a href="edit_user.php?id=' . $row['user_id'] . '">Edit</a></td>
    <td align="left"><a href="delete_user.php?id=' . $row['user_id'] . '">Delete</a></td>
    <td align="left">' . $row['last_name'] . '</td>
    <td align="left">' . $row['first_name'] . '</td>
    <td align="left">' . $row['dr'] . '</td>
</tr>
';
} // End of WHILE loop.

echo '</table>';
mysqli_free_result ($r);
mysqli_close($dbc);

// Make the links to other pages, if necessary.
if ($pages > 1) {

    echo '<br /><p>';
    $current_page = ($start/$display) + 1;

    // If it's not the first page, make a Previous button:
    if ($current_page != 1) {
        echo '<a href="view_users.php?s=' . ($start - $display) . '&p=' . $pages . '&sort=' . $sort . '">Previous</a> ';
    }

    // Make all the numbered pages:
    for ($i = 1; $i <= $pages; $i++) {
        if ($i != $current_page) {
            echo '<a href="view_users.php?s=' . (($display * ($i - 1))) . '&p=' . $pages . '&sort=' . $sort . '">' . $i . '</a> ';
        } else {
            echo $i . ' ';
        }
    } // End of FOR loop.

    // If it's not the last page, make a Next button:
    if ($current_page != $pages) {
        echo '<a href="view_users.php?s=' . ($start + $display) . '&p=' . $pages . '&sort=' . $sort . '">Next</a>';
    }

    echo '</p>'; // Close the paragraph.

} // End of links section.

include ('includes/footer.html');
?>
```

***

### 创建可排序的显示

为了结束本章，还有一个最终功能可以添加到 `view_users.php` 中。在目前的状态下，用户列表按注册日期顺序显示。如果也能按姓名查看，那将很不错。

从 MySQL 的角度来看，完成此任务很简单：只需更改 `SELECT` 查询的 `ORDER BY` 子句。因此，要向脚本添加排序功能，只需要额外的 PHP 代码来更改 `ORDER BY` 子句。一个合乎逻辑的方法是链接列标题，以便点击它们可以更改显示顺序。正如你希望猜到的那样，这涉及使用 GET 方法将一个参数传回此页面，以指示首选的排序顺序。

#### 创建可排序链接

**1.** 在文本编辑器或 IDE 中打开 `view_users.php`（脚本 10.4），如果尚未打开的话。

**2.** 在确定起始点（`$s`）之后，定义一个 `$sort` 变量（脚本 10.5）：

```php
$sort = (isset($_GET['sort'])) ? $_GET['sort'] : 'rd';
```
