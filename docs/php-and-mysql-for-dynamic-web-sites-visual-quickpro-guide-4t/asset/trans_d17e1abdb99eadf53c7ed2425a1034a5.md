
这些示例本身将通过添加新的、流行的功能来扩展上一章开始的 Web 应用程序。您将看到几种管理数据库信息的技巧，特别是使用 PHP 编辑和删除记录。同时，将介绍几种向 PHP 页面传递数据的新方法。本章的最后几节将为 `view_users.php` 页面添加功能。

## 向脚本发送值

在迄今为止的示例中，PHP 脚本接收的所有数据都来自用户在表单中输入的内容。但是，您可以通过两种不同的方式将变量和值传递给 PHP 脚本，这两种方式都值得了解。

第一种方法是利用 HTML 的 `hidden`（隐藏）输入类型：

```html
<input type="hidden" name="do" value="this" />
```

只要这段代码位于 `form` 标签之间的任何位置，变量 `$_POST['do']` 在处理脚本中就会拥有值 `this`，前提是表单使用 POST 方法。如果表单使用 GET 方法，那么 `$_GET['do']` 将拥有该值。考虑到这一点，您实际上可以跳过创建表单的步骤，直接将一个 `name=value` 对追加到 URL 后面：

```text
www.example.com/page.php?do=this
```

同样，在这个特定示例中，`page.php` 接收到一个名为 `$_GET['do']` 的变量，其值为 `this`。

为了演示这个 GET 方法技巧，将编写一个新版本的 `view_users.php` 脚本（该脚本最初是在上一章创建的）。这个新版本将提供链接到允许您编辑或删除现有用户记录的页面。这些链接将把用户的 ID 传递给处理页面，这两个处理页面也将在本章中编写。

### 手动向 PHP 脚本发送值

**1.** 在文本编辑器或 IDE 中打开 `view_users.php`（[脚本 9.6](#ch09.html#ch09ex06)）。

**2.** 更改 SQL 查询如下（**[脚本 10.1](#ch10.html#ch10ex01）**）：

```php
$q = "SELECT last_name, first_name, DATE_FORMAT (registration_date, '%M %d, %Y') AS dr, user_id FROM users ORDER BY registration_date ASC";
```

**脚本 10.1.** `view_users.php` 脚本始于 [第 9 章](#ch09.html#ch09) “[将 PHP 与 MySQL 结合使用](#ch09.html#ch09)”，现已修改为呈现编辑和删除链接，并在每个 URL 中传递用户的 ID 编号。

* * *

```php
1   <?php # 脚本 10.1 - view_users.php #3

2   // 此脚本从 users 表中检索所有记录。
3   // 此新版本链接到编辑和删除页面。
4

5   $page_title = '查看当前用户';
6   include ('includes/header.html');
7   echo '<h1>已注册用户</h1>';
8

9   require_once ('../mysqli_connect.php');
10

11  // 定义查询：
12  $q = "SELECT last_name, first_name, DATE_FORMAT(registration_date, '%M %d, %Y') AS dr,
      user_id FROM users ORDER BY registration_date ASC";
13  $r = @mysqli_query ($dbc, $q);
14

15  // 计算返回的行数：
16  $num = mysqli_num_rows($r);
17

18  if ($num > 0) { // 如果运行正常，显示记录。
19

20      // 打印用户数量：
21      echo "<p>当前有 $num 位已注册用户。</p>\n";
22

23      // 表头：
24      echo '<table align="center" cellspacing="3" cellpadding="3" width="75%">
25      <tr>
26          <td align="left"><b>编辑</b></td>
27          <td align="left"><b>删除</b></td>
28          <td align="left"><b>姓氏</b></td>
29          <td align="left"><b>名字</b></td>
30          <td align="left"><b>注册日期</b></td>
31      </tr>
32  ';

33      // 获取并打印所有记录：
34      while ($row = mysqli_fetch_array($r, MYSQLI_ASSOC)) {
35          echo '<tr>
36              <td align="left"><a href="edit_user.php?id=' . $row['user_id'] . '">编辑</a></td>
37              <td align="left"><a href="delete_user.php?id=' . $row['user_id'] . '">删除</a></td>
38              <td align="left">' . $row['last_name'] . '</td>
39              <td align="left">' . $row['first_name'] . '</td>
40              <td align="left">' . $row['dr'] . '</td>
41          </tr>
42          ';
35      }

46      echo '</table>';
47      mysqli_free_result ($r);
48

49  } else { // 如果没有返回记录。
50      echo '<p class="error">当前没有已注册用户。</p>';
51  }

52  mysqli_close($dbc);
53

54  include ('includes/footer.html');
55  ?>
```

* * *

查询在几个方面进行了更改。首先，名和姓是分别选择的，而不是连接在一起。其次，现在也选择了 `user_id`，因为创建链接时需要该值。

**3.** 向主表添加三列：

```php
echo '<table align="center" cellspacing="3" cellpadding="3" width="75%">
<tr>
  <td align="left"><b>编辑</b> </td>
  <td align="left"><b>删除</b> </td>
  <td align="left"><b>姓氏</b> </td>
  <td align="left"><b>名字</b> </td>
  <td align="left"><b>注册日期</b> </td>
</tr>
';
```

在脚本的上一个版本中，只有两列：一列用于姓名，另一列用于用户注册日期。姓名列已拆分为两部分，并新增了两列：一列用于*编辑*链接，另一列用于*删除*链接。

**4.** 更改 `while` 循环中的 `echo` 语句以匹配表的新结构：

```php
echo '<tr>
  <td align="left"><a href="edit_user.php?id=' . $row['user_id'] . '">编辑</a></td>
  <td align="left"><a href="delete_user.php?id=' . $row['user_id'] . '">删除</a></td>
  <td align="left">' . $row['last_name'] . '</td>
  <td align="left">' . $row['first_name'] . '</td>
  <td align="left">' . $row['dr'] . '</td>
</tr>
';
```

对于从数据库返回的每条记录，此行将打印出一行包含五列的内容。后三列显而易见且易于创建：只需引用返回的列名即可。

对于前两列（提供编辑或删除用户的链接），语法稍微复杂一些。期望的最终结果是类似 `<a href="edit_user.php?id=`*`X`*`">编辑</a>` 的 HTML 代码，其中 *X* 是用户的 ID。了解这一点后，PHP 代码所要做的就是为 *X* 打印 `$row['user_id']`，同时注意引号的使用以避免解析错误。

由于 HTML 属性使用了大量双引号，而此 `echo` 语句需要打印大量变量，我发现最简单的方法是对 HTML 使用单引号，然后将变量与打印文本连接起来。

**5.** 将文件保存为 `view_users.php`，将其放在您的 Web 目录中，并在 Web 浏览器中运行它 ![Image](graphics/circle-a.jpg)。

![Image](graphics/10_figure_01_a.jpg)

![Image](graphics/circle-a.jpg)修订后的 `view_users.php` 页面，包含新列和链接。

不过，目前点击这些新链接没有任何作用，因为那些脚本尚未创建。

**6.** 如果您愿意，可以查看页面的 HTML 源代码，以查看每个动态生成的链接 ![Image](graphics/circle-b.jpg)。

![Image](graphics/10_figure_02_b.jpg)

![Image](graphics/circle-b.jpg)页面的部分 HTML 源代码（见 ![Image](graphics/graycircle-a.jpg)）显示了用户 ID 是如何添加到每个链接的 URL 中的。

* * *

> **提示**
>
> 要向 URL 追加多个变量，请使用以下语法：`page.php?name1=value1& name2=value2&name3=value3`。这只是使用和号（&），加上另一个 `name=value` 对的问题。

* * *

> **提示**
>
> 向 URL 添加变量的一个技巧是对字符串进行编码，以确保值被正确处理。例如，字符串 *Elliott Smith* 中的空格会造成问题。解决方法是使用 `urlencode()` 函数：
>
> ```php
> $url = 'page.php?name=' . urlencode('Elliott Smith');
> ```
