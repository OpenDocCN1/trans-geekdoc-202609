
### 修改查询与表结构

查询在几个方面进行了更改。首先，名和姓是分别选择的，而不是连接在一起。其次，现在也选择了 `user_id`，因为创建链接时需要该值。

**3. 向主表添加三列：**

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

在脚本的上一个版本中，只有两列：一列用于姓名，另一列用于用户注册日期。姓名列已拆分为两部分，并新增了两列：一列用于**编辑**链接，另一列用于**删除**链接。

**4. 更改 `while` 循环中的 `echo` 语句以匹配表的新结构：**

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

**5. 将文件保存为 `view_users.php`，将其放在您的 Web 目录中，并在 Web 浏览器中运行它。**

![Image](img/10_figure_01_a.jpg)

修订后的 `view_users.php` 页面，包含新列和链接。

不过，目前点击这些新链接没有任何作用，因为那些脚本尚未创建。

**6. 如果您愿意，可以查看页面的 HTML 源代码，以查看每个动态生成的链接。**

![Image](img/10_figure_02_b.jpg)

页面的部分 HTML 源代码显示了用户 ID 是如何添加到每个链接的 URL 中的。

---

> **提示**
>
> 要向 URL 追加多个变量，请使用以下语法：`page.php?name1=value1&name2=value2&name3=value3`。这只是使用和号（&），加上另一个 `name=value` 对的问题。

---

> **提示**
>
> 向 URL 添加变量的一个技巧是对字符串进行编码，以确保值被正确处理。例如，字符串 *Elliott Smith* 中的空格会造成问题。解决方法是使用 `urlencode()` 函数：
>
> ```php
> $url = 'page.php?name=' . urlencode('Elliott Smith');
> ```
>
> 只有在以编程方式向 URL 添加值时，才需要这样做。当表单使用 `GET` 方法时，它会自动对数据进行编码。

---

### 使用隐藏表单输入

在前面的示例中，编写了 `view_users.php` 脚本的新版本。该版本现在包含指向 `edit_user.php` 和 `delete_user.php` 页面的链接，通过 URL 传递每个用户的 ID。下一个示例 `delete_user.php` 将接收传递的用户 ID，并允许管理员删除该用户。虽然你可以让此页面在被访问时立即执行 `DELETE` 查询，但出于安全考虑（并防止意外删除），应该分多个步骤进行：

1.  页面必须检查是否接收到了数字用户 ID。
2.  一条消息将确认是否应删除该用户。
3.  用户 ID 将存储在隐藏表单输入中。
4.  提交此表单后，用户将实际被删除。

![Image](img/10_figure_03_c.jpg)

此图概述了用户删除脚本将执行的步骤。

#### 创建 `delete_user.php` 脚本

1.  在文本编辑器或 IDE 中开始一个新的 PHP 文档，命名为 `delete_user.php`（**脚本 10.2**）：

    ```php
    <?php # Script 10.2 - delete_user.php
    ```

2.  包含页面页眉：

    ```php
    $page_title = 'Delete a User';
    include ('includes/header.html');
    echo '<h1>Delete a User</h1>';
    ```

    该文档将使用与应用程序中其他页面相同的模板系统。如有需要，请参阅第 9 章和第 3 章以获取说明。

3.  检查有效的用户 ID 值：

    ```php
    if ( (isset($_GET['id'])) && (is_numeric($_GET['id'])) ) {
        $id = $_GET['id'];
    } elseif ( (isset($_POST['id'])) && (is_numeric($_POST['id'])) ) {
        $id = $_POST['id'];
    } else {
        echo '<p class="error">This page has been accessed in error.</p>';
        include ('includes/footer.html');
        exit();
    }
    ```

**脚本 10.2.** 该脚本期望通过 URL 向其传递用户 ID。然后它显示一个确认表单，并在提交时删除用户。

---

```php
1   <?php # Script 10.2 - delete_user.php
2   // This page is for deleting a user record.
3   // This page is accessed through view_users.php.
4
5   $page_title = 'Delete a User';
6   include ('includes/header.html');
7   echo '<h1>Delete a User</h1>';
8
9   // Check for a valid user ID, through
    // GET or POST:
10  if ( (isset($_GET['id'])) && (is_numeric
    ($_GET['id'])) ) { // From view_users.php
11      $id = $_GET['id'];
12  } elseif ( (isset($_POST['id'])) &&
    (is_numeric($_POST['id'])) ) { // Form
    // submission.
13      $id = $_POST['id'];
14  } else { // No valid ID, kill the script.
15      echo '<p class="error">This page has
    been accessed in error.</p>';
16      include ('includes/footer.html');
17      exit();
18  }
19
20  require_once ('../mysqli_connect.php');
21
22  // Check if the form has been submitted:
23  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
24
25      if ($_POST['sure'] == 'Yes') {
        // Delete the record.
26
27          // Make the query:
28          $q = "DELETE FROM users WHERE
            user_id=$id LIMIT 1";
29          $r = @mysqli_query ($dbc, $q);
30          if (mysqli_affected_rows($dbc) ==
            1) { // If it ran OK.
31
32              // Print a message:
33              echo '<p>The user has been
                deleted.</p>';
34
35          } else { // If the query did not
            // run OK.
36              echo '<p class="error">The user
                could not be deleted due to a
                system error.</p>'; // Public
                // message.
37              echo '<p>' . mysqli_error($dbc)
                . '<br />Query: ' . $q . '</p>';
                // Debugging message.
38          }
39
40      } else { // No confirmation of deletion.
41          echo '<p>The user has NOT been
            deleted.</p>';
42      }
43
44  } else { // Show the form.
45
46      // Retrieve the user's information:
47      $q = "SELECT CONCAT(last_name, ',
    ', first_name) FROM users WHERE
        user_id=$id";
48      $r = @mysqli_query ($dbc, $q);
49
50      if (mysqli_num_rows($r) == 1) {
        // Valid user ID, show the form.
51
52          // Get the user's information:
53          $row = mysqli_fetch_array ($r,
            MYSQLI_NUM);
54
55          // Display the record being deleted:
56          echo "<h3>Name: $row[0]</h3>
            Are you sure you want to delete
            this user?";
57
57          // Create the form:
58          echo '<form action="delete_user.
            php" method="post">
            <input type="radio" name="sure"
            value="Yes" /> Yes
            <input type="radio" name="sure"
            value="No" checked="checked" /> No
            <input type="submit" name="submit"
            value="Submit" />
            <input type="hidden" name="id"
            value="' . $id . '" />
            </form>';
66
67      } else { // Not a valid user ID.
68          echo '<p class="error">This page
            has been accessed in error.</p>';
69      }
70
71  } // End of the main submission conditional.
72
73  mysqli_close($dbc);
74
75  include ('includes/footer.html');
76  ?>
```

---

该脚本依赖于拥有一个有效的用户 ID，以便在 `DELETE` 查询的 `WHERE` 子句中使用。首次访问此页面时，用户 ID 应通过 URL 传递（页面 URL 将以 `delete_user.php?id=X` 结尾），这是在 `view_users.php` 页面中点击 **Delete** 链接后发生的。第一个 `if` 条件检查此类值是否存在且该值是否为数字。

正如你将看到的，脚本随后会将用户 ID 值存储在隐藏表单输入中。当表单提交（回到这个同一页面）时，脚本将通过 `$_POST` 接收该 ID。第二个条件检查这一点，并再次确认 ID 值为数字。

如果这两个条件都不为 TRUE，则页面无法继续，因此会显示一条错误消息并终止脚本的执行。

![Image](img/10_figure_04_b.jpg)

如果页面未接收到数字 ID 值，将显示此错误。

4.  包含 MySQL 连接脚本：

    ```php
    require_once ('../mysqli_connect.php');
    ```

    该脚本的两个过程——显示表单和处理表单——都需要数据库连接，因此此行位于主提交条件（步骤 5）之外。

5.  开始主提交条件：

    ```php
    if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    ```

    为了测试表单提交，脚本使用了在第 3 章中首次解释的相同条件，并在第 9 章中也已使用。

6.  如果合适则删除用户：

    ```php
    if ($_POST['sure'] == 'Yes') {
        $q = "DELETE FROM users WHERE user_id=$id LIMIT 1";
        $r = @mysqli_query ($dbc, $q);
    ```

    表单将强制用户点击单选按钮以确认删除。这一小小的要求可以防止任何意外。因此，处理过程首先检查是否选择了正确的单选按钮。如果是，则定义一个基本的 `DELETE` 查询，在 `WHERE` 子句中使用用户的 ID。`LIMIT` 子句作为额外的预防措施添加到查询中。

![Image](img/10_figure_05_c.jpg)

页面使用这个简单的表单确认用户删除。

7.  检查删除是否成功并做出相应响应：

    ```php
    if (mysqli_affected_rows($dbc) == 1) {
        echo '<p>The user has been deleted.</p>';
    } else {
    ```
