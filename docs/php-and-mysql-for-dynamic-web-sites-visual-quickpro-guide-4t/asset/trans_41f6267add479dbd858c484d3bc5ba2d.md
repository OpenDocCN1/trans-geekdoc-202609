

`$sort` 变量将用于确定查询结果的排序方式。此行使用三元运算符（请参阅本章前一节侧边栏）为 `$sort` 赋值。如果设置了 `$_GET['sort']`（用户单击任意链接后即会出现这种情况），则应将该值赋给 `$sort`。如果未设置 `$_GET['sort']`，则为 `$sort` 赋予默认值 `rd`（*registration date*，注册日期的缩写）。

**3.** 确定结果应如何排序：

```php
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
```

`switch` 将 `$sort` 与多个预期值进行比对。例如，如果它等于 `ln`，则结果应按姓氏升序排列。所赋予的 `$order_by` 变量将用于 SQL 查询中。

如果 `$sort` 的值为 `fn`，则结果应按名字升序排列。如果值为 `rd`，则结果将按注册日期升序排列。这也是默认情况。此处设置默认情况可以防止恶意用户将 `$_GET['sort']` 的值更改为可能破坏查询的内容。

**4.** 修改查询以使用新的 `$order_by` 变量：

```php
$q = "SELECT last_name, first_name, DATE_FORMAT(registration_date, '%M %d, %Y') AS dr, user_id FROM users ORDER BY $order_by LIMIT $start, $display";
```

此时，`$order_by` 变量已有一个值，指明返回的结果应如何排序（例如 `registration_date ASC`），因此可以轻松地将其添加到查询中。请记住 `ORDER BY` 子句位于 `LIMIT` 子句之前。如果生成的查询在您那里无法正常运行，请将其打印出来并检查其语法。

**5.** 修改表头的 `echo` 语句，使列标题变为链接：

```php
echo '<table align="center" cellspacing="0" cellpadding="5" width="75%">  

<tr>  

  <td align="left"><b>Edit</b></td>  

  <td align="left"><b>Delete</b></td>  

  <td align="left"><b><a href="view_users.php?sort=ln">Last Name</a></b></td>  

  <td align="left"><b><a href="view_users.php?sort=fn">First Name</a></b></td>  

  <td align="left"><b><a href="view_users.php?sort=rd">Date Registered</a></b></td>  

</tr>  

';
```

要将列标题变为可点击的链接，只需用 `A` 标签将其包围即可。每个链接的 `href` 属性值对应 `$_GET['sort']` 的可接受值（参见步骤 3 中的 `switch`）。

**6.** 修改创建 *Previous*（上一页）链接的 `echo` 语句，以便同时传递排序值：

```php
echo '<a href="view_users.php?s=' . ($start - $display) . '&p=' . $pages . '&sort=' . $sort . '"> Previous</a> ';
```

向 *Previous* 链接添加另一个 *name=value* 对，以便将排序顺序也发送到结果的每一页。如果不这样做，分页将会失败，因为 `ORDER BY` 子句会因页面不同而异。

**7.** 对编号页面和 *Next*（下一页）链接重复步骤 6：

```php
echo '<a href="view_users.php?s=' . (($display * ($i - 1))) . '&p=' . $pages . '&sort=' . $sort . '">' . $i . '</a> ';  

echo '<a href="view_users.php?s=' . ($start + $display) . '&p=' . $pages . '&sort=' . $sort . '"> Next</a>';
```

**8.** 将文件另存为 `view_users.php`，放入您的 Web 目录中，并在 Web 浏览器中运行它 ![Image](graphics/circle-a.jpg)和 ![Image](graphics/circle-b.jpg)。

![Image](graphics/10_figure_17_a.jpg)

![Image](graphics/circle-a.jpg)单击名字列后，结果按名字升序显示。

![Image](graphics/10_figure_18_b.jpg)

![Image](graphics/circle-b.jpg)单击 *Last Name*（姓氏）列，然后单击到第二个分页显示，页面显示按姓氏升序排列的第二组结果。

***

提示

本例还演示了一个非常重要的安全概念。代码没有直接在查询中使用 `$_GET['sort']` 的值，而是在 `switch` 中将其与假定的值进行核对。如果由于某种原因，`$_GET['sort']` 的值不是预期的值，则查询将使用默认排序顺序。关键在于：不要对接收到的数据做假设，也不要在 SQL 查询中使用未经验证的数据。

***

### 复习与实践

如果您对复习问题或实践提示有任何疑问，请访问本书的支持论坛 ([www.LarryUllman.com/forums/](http://www.LarryUllman.com/forums/))。

#### 复习

• 调试 PHP-MySQL 问题的标准步骤序列是什么（在 [第 8 章](#ch08.html#ch08) 末尾明确传达）？

• 向 PHP 脚本传递值的两种方式是什么（除用户输入外）？

• `delete_user.php` 和 `edit_user.php` 脚本采取了哪些安全措施来防止恶意或意外删除？

• 为什么可以在查询中直接使用 `$id` 值，而无需先通过 `mysqli_real_escape_string()` 处理？

• 在什么情况下 `mysqli_affected_rows()` 函数会返回假阴性（即报告没有记录受影响，尽管查询无错误运行）？

• 什么是三元运算符？如何使用它？

• 正确分页查询结果需要哪两个值？

• 如何修改查询以使其结果分页？

• 如果分页查询基于额外标准（超出 `LIMIT` 子句中使用的标准），如果这些标准不也在每个分页链接中传递，会发生什么？

• 为什么重要的是不要直接在查询中使用 `$_GET['sort']` 的值？

• 为什么重要的是在每个分页链接中传递排序值？

#### 实践

• 修改 `delete_user.php` 和 `edit_user.php` 页面，使它们都在浏览器窗口的标题栏中显示受影响的用户。

• 修改 `edit_user.php`，以便也能更改用户的密码。

• 如果您想挑战一下，修改 `edit_user.php`，使表单元素的值来自 `$_POST`（如果已设置），否则来自数据库。

• 更改 `view_users.php` 中 `$display` 变量的值以改变分页。

• 对另一个查询结果进行分页，例如 *banking* 数据库中找到的账户或客户列表。

• 为 *banking* 数据库创建删除和编辑脚本。您必须考虑到现有的外键约束，例如，限制删除仍拥有账户的客户。

## 11. Web 应用程序开发

本章内容

[发送电子邮件](#ch11.html#ch11lev1sec1) [330](#ch11.html#ch11lev1sec1)

[处理文件上传](#ch11.html#ch11lev1sec2) [336](#ch11.html#ch11lev1sec2)

[PHP 和 JavaScript](#ch11.html#ch11lev1sec3) [348](#ch11.html#ch11lev1sec3)

[理解 HTTP 头部](#ch11.html#ch11lev1sec4) [355](#ch11.html#ch11lev1sec4)

[日期和时间函数](#ch11.html#ch11lev1sec5) [362](#ch11.html#ch11lev1sec5)

[复习与实践](#ch11.html#ch11lev1sec6) [366](#ch11.html#ch11lev1sec6)

前两章重点介绍了如何将 PHP 和 MySQL 结合使用（毕竟这是本书的主要目的）。但仍有大量以 PHP 为中心的材料需要涵盖。在暂时告别 PHP 与 MySQL 的结合使用后，本章介绍了一些常用于更复杂 Web 应用程序的技术。

