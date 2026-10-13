

echo '<p class="error">The user could not be deleted due to a system error.</p>';

echo '<p>' . mysqli_error($dbc) . '<br />Query: ' . $q . '</p>';

}

`mysqli_affected_rows()` 函数检查 `DELETE` 查询是否恰好影响了一行。如果是，则显示一条成功消息 ![Image](graphics/circle-d.jpg)。如果不是，则发送一条错误消息。

![Image](graphics/10_figure_06_d.jpg)

![Image](graphics/circle-d.jpg)如果在表单中选择 *Yes*（请参阅 ![Image](graphics/graycircle-c.jpg)）并点击提交，结果应如下所示。

请记住，在没有发生 MySQL 错误的情况下，也有可能没有行受到影响。例如，如果查询试图删除用户 ID 等于 42000 的记录（而该记录不存在），则不会删除任何行，但也不会发生 MySQL 错误。尽管如此，由于首次加载表单时所做的检查，用户要达到这一点需要进行相当程度的“黑客”操作。

**8.** 完成 `$_POST['sure']` 条件判断：

```php
} else {
  echo '<p>The user has NOT been deleted.</p>';
}
```

如果用户没有明确勾选 *Yes* 按钮，则不会删除该用户，并显示此消息 ![Image](graphics/circle-e.jpg)。

![Image](graphics/10_figure_07_e.jpg)

![Image](graphics/circle-e.jpg)如果在表单中未选择 *Yes*，则不会对数据库进行任何更改。

**9.** 开始主提交条件判断的 `else` 子句：

```php
} else {
```

页面将处理表单或显示表单。在此之前的大部分代码在表单已提交时生效（如果 `$_SERVER['REQUEST_METHOD']` 等于 *POST*）。从这里开始的代码在表单尚未提交时生效，此时应显示表单。

**10.** 检索要删除用户的信息：

```php
$q = "SELECT CONCAT(last_name, ', ', first_name) FROM users WHERE user_id=$id";
$r = @mysqli_query ($dbc, $q);
if (mysqli_num_rows($r) == 1) {
  $row = mysqli_fetch_array ($r, MYSQLI_NUM);
```

为了确认脚本接收到了有效的用户 ID 并明确指出要删除的是谁（请参阅 ![Image](graphics/graycircle-c.jpg)），将从数据库中检索要删除用户的姓名 ![Image](graphics/circle-f.jpg)。

![Image](graphics/10_figure_08_f.jpg)

![Image](graphics/circle-f.jpg)在 mysql 客户端中运行相同的 `SELECT` 查询。

该条件判断——检查是否返回了单行——确保向脚本提供了有效的用户 ID。如果是，则将该记录获取到 `$row` 变量中。

**11.** 显示要删除的记录：

```php
echo "<h3>Name: $row[0]</h3>
Are you sure you want to delete this user?";
```

为了帮助防止意外删除错误的记录，首先显示要删除用户的姓名。该值可在 `$row[0]` 中获得，因为 `mysqli_fetch_array()` 函数（在第 10 步中）使用了 `MYSQLI_NUM` 常量，从而将返回的记录作为索引数组赋值给 `$row`。用户姓名是返回记录中的第一列，也是唯一一列，因此其索引为 0（数组通常从 0 开始索引）。

**12.** 创建表单：

```php
echo '<form action="delete_user.php" method="post">
<input type="radio" name="sure" value="Yes" /> Yes
<input type="radio" name="sure" value="No" checked="checked" /> No
<input type="submit" name="submit" value="Submit" />
<input type="hidden" name="id" value="' . $id . '" />
</form>';
```

该表单提交回此同一页面。它包含两个单选按钮，名称相同但值不同，一个提交按钮，和一个隐藏输入框。此处最重要的一步是将用户 ID（`$id`）存储为隐藏表单输入，以便处理过程也能访问此值 ![Image](graphics/circle-g.jpg)。

**13.** 完成 `mysqli_num_rows()` 条件判断：

```php
} else {
  echo '<p class="error">This page has been accessed in error.</p>';
}
```

如果 `SELECT` 查询未返回任何记录（因为提交了无效的用户 ID），则显示此消息。

如果您在测试此脚本时看到此消息但不明白原因，请应用 [第 8 章](#ch08.html#ch08) “[错误处理与调试](#ch08.html#ch08)” 末尾概述的标准调试步骤。

**14.** 完成 PHP 页面：

```php
}
mysqli_close($dbc);
include ('includes/footer.html');
?>
```

右大括号结束主提交条件判断。然后关闭 MySQL 连接并包含页脚文件。

**15.** 将文件保存为 `delete_user.php` 并将其放在您的 Web 目录中（应与 `view_users.php` 在同一目录下）。

**16.** 通过首先在 `view_users.php` 页面中点击 *Delete* 链接来运行该页面。

***

Tip

隐藏表单元素不会在 Web 浏览器中显示，但仍存在于 HTML 源代码中 ![Image](graphics/graycircle-g.jpg)。因此，切勿在其中存储任何必须真正保密的内容。

***

***

Tip

使用隐藏表单输入和向 URL 追加值只是让数据可供其他 PHP 页面使用的两种方法。另外两种方法——Cookie 和 Session——将在第 12 章 “[Cookie 和 Session](#ch12.html#ch12)” 中详细介绍。

***

![Image](graphics/10_figure_09_g.jpg)

![Image](graphics/circle-g.jpg)用户 ID 作为隐藏输入存储，以便在表单提交时可用。

**脚本 10.3.** `edit_user.php` 页面首先在表单中显示用户的当前信息。提交表单后，将在数据库中更新该记录。

***

```php
1   <?php # Script 10.3 - edit_user.php
2   // This page is for editing a user
      record.
3   // This page is accessed through view_
      users.php.
4
5   $page_title = 'Edit a User';
6   include ('includes/header.html');
7   echo '<h1>Edit a User</h1>';
8
9   // Check for a valid user ID, through
      GET or POST:
10  if ( (isset($_GET['id'])) && (is_numeric($_
      GET['id'])) ) { // From view_users.php
11      $id = $_GET['id'];
12  } elseif ( (isset($_POST['id'])) &&
      (is_numeric($_POST['id'])) ) { // Form
      submission.
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
25      $errors = array();
26
27      // Check for a first name:
28      if (empty($_POST['first_name'])) {
29          $errors[] = 'You forgot to enter
            your first name.';
30      } else {
31          $fn = mysqli_real_escape_string($dbc,
            trim($_POST['first_name']));
32      }
33
34      // Check for a last name:
35      if (empty($_POST['last_name'])) {
36          $errors[] = 'You forgot to enter
            your last name.';
37      } else {
38          $ln = mysqli_real_escape_string($dbc,
            trim($__POST['last_name']));
39      }
40
41      // Check for an email address:
42      if (empty($_POST['email'])) {
43          $errors[] = 'You forgot to enter
            your email address.';
44      } else {
45          $e = mysqli_real_escape_string
            ($dbc, trim($_POST['email']));
46      }
47
48      if (empty($errors)) { // If
          everything's OK.
49
50          // Test for unique email address:
51          $q = "SELECT user_id FROM users
            WHERE email='$e' AND user_id != $id";
52          $r = @mysqli_query($dbc, $q);
53          if (mysqli_num_rows($r) == 0) {
54
55              // Make the query:
56              $q = "UPDATE users SET first_
```

