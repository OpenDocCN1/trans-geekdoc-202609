

```php
30  // 获取并打印所有记录：
31  while ($row = $r->fetch_object()) {
32      echo '<tr><td align="left">' .
             $row->name . '</td><td align="left">' . $row->dr . '</td></tr>';
33  }
34
35  echo '</table>'; // 关闭表格。
36
37  $r->free(); // 释放资源。
38  unset($r);
39
40  } else { // 如果没有返回记录。
41
42      echo '<p class="error">There are currently no registered users.</p>';
43
44  }
45
46  // 关闭数据库连接。
47  $mysqli->close();
48  unset($mysqli);
49
50  include('includes/footer.html');
51  ?>
```

---

**6.** 在 `while` 循环中，更改每列值的打印方式：

```php
echo '<tr><td align="left">' . $row->name . '</td><td align="left">' . $row->dr . '</td></tr>';
```

由于 `$row` 变量现在是一个对象，必须使用对象表示法，而不是数组表示法，来引用每行中的列：`$row->name` 和 `$row->dr` 代替 `$row['name']` 和 `$row['dr']`。

**7.** 更改资源释放方式：

```php
$r->free();
unset($r);
```

要释放返回结果占用的内存，请调用 `MySQLi_Result` 对象的 `free()` 方法。此外，由于该对象在脚本中不再使用，可以将其销毁。

**8.** 更新数据库连接的关闭方式：

```php
$mysqli->close();
unset($mysqli);
```

**9.** 保存脚本，将其放置在您的 Web 目录中，并在 Web 浏览器中测试它。

`view_users.php`（脚本 16.3）的面向对象版本看起来与原始过程式版本相同。

> **提示**
>
> 使用 `fetch_object()` 方法的真正好处在于，您可以将结果作为*特定类型的对象*获取。例如，假设您在 PHP 中定义了一个 `Car` 类，并且一个脚本从数据库中获取了关于汽车的所有存储信息。在 PHP 脚本中，每条记录都可以作为 `Car` 类类型的对象获取。通过这样做，您将创建一个 PHP `Car` 对象，其数据来自数据库记录填充，但仍然可以调用 `Car` 类的方法。

---

#### 预处理语句

第 13 章介绍了执行查询的另一种方式：使用*预处理语句*。与运行查询的标准方法相比，预处理语句可以提供更好的安全性，甚至可能获得更好的性能。当然，您可以使用 MySQL Improved 扩展以对象的方式执行预处理语句。步骤是相同的：创建一个 `MySQLi` 对象（从而建立与数据库的连接）后，您需要

*   准备查询
*   绑定参数
*   执行查询

在实际代码中如下所示：

```php
$q = 'INSERT INTO tablename (this, that) VALUES (?, ?)';
$stmt = $mysqli->prepare($q);
$stmt->bind_param('si', $this, $that);
$this = 'Larry';
$that = 234;
$stmt->execute();
```

`MySQLi::prepare()` 方法返回一个 `MySQLi_STMT` 类型的对象。该对象有几个关键属性：

*   `affected_rows` 存储语句影响的行数，通常适用于 `INSERT`、`UPDATE` 和 `DELETE` 查询。
*   `num_rows` 反映 `SELECT` 查询结果集中的记录数。
*   `insert_id` 存储上一个 `INSERT` 查询自动生成的 ID 值。
*   `error` 表示可能发生的任何错误。

执行完预处理语句后，您应该关闭该语句：

```php
$stmt->close();
```

让我们通过更新 `post_message.php`（脚本 13.6）来应用这些信息。这是一个独立的脚本，使用 *forum* 数据库，并且在第 13 章或本章中未与任何其他脚本关联。

#### 执行预处理语句

**1.** 在文本编辑器或 IDE 中打开 `post_message.php`（脚本 13.6）。

**2.** 将数据库连接的创建更改为（脚本 16.4）：

```php
$mysqli = new MySQLi('localhost', 'username', 'password', 'forum');
$mysqli->set_charset('utf8');
```

该脚本的先前版本未使用单独的连接脚本，此版本也不会。请确保您的值对于连接到服务器上的 *forum* 数据库是正确的。

**3.** 将查询的准备更改为（原脚本第 21 行）：

```php
$stmt = $mysqli->prepare($q);
```

`MySQLi::prepare()` 方法准备一条语句，将查询作为其唯一参数。它返回一个 `MySQLi_STMT` 类型的对象，此处赋值给 `$stmt`。

**4.** 将参数绑定更改为：

```php
$stmt->bind_param('iiiss', $forum_id, $parent_id, $user_id, $subject, $body);
```

此代码更改仅是从 `mysqli_stmt_bind_param($stmt...` 改为 `$stmt->bind_param(...`。该方法的第一个参数是后续数据类型的指示符。后续参数是查询占位符所绑定的 PHP 变量。

**5.** 将语句的执行更新为：

```php
$stmt->execute();
```

**脚本 16.4.** 在本章 13 脚本的此版本中，使用 `MySQLi_STMT` 类来执行预处理语句。

```php
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
2       1.0 Transitional//EN" "http://www.w3.org/
3       TR/xhtml1/DTD/xhtml1-transitional.dtd">
4   <html xmlns="http://www.w3.org/1999/
5       xhtml" xml:lang="en" lang="en">
6   <head>
7       <meta http-equiv="Content-Type"
8           content="text/html; charset=utf-8" />
9       <title>Post a Message</title>
10  </head>
11  <body>
12  <?php # Script 16.4 - post_message.php
13  // This is an OOP version of the script
14      from Chapter 13.
15
16  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
17
18      // Validate the data (omitted)!
19
20      // Connect to the database:
21      $mysqli = new MySQLi('localhost',
22          'username', 'password', 'forum');
23      $mysqli->set_charset('utf8');
24
25      // Make the query:
26      $q = 'INSERT INTO messages (forum_id,
27          parent_id, user_id, subject, body,
28          date_entered) VALUES (?, ?, ?, ?, ?,
29          NOW())';
30
31      // Prepare the statement:
32      $stmt = $mysqli->prepare($q);
33
34      // Bind the variables:
35      $stmt->bind_param('iiiss',
36          $forum_id, $parent_id, $user_id,
37          $subject, $body);
38
39      // Assign the values to variables:
40      $forum_id = (int) $_POST['forum_id'];
41      $parent_id = (int) $_POST['parent_id'];
42      $user_id = 3; // The user_id value
43          would normally come from the session.
44      $subject = strip_tags($_POST
45          ['subject']);
46      $body = strip_tags($_POST['body']);
47
48      // Execute the query:
49      $stmt->execute();
50
51      // Print a message based upon the
52          result:
53      if ($stmt->affected_rows == 1) {
54          echo '<p>Your message has been
55              posted.</p>';
56      } else {
57          echo '<p style="font-weight: bold;
58              color: #C00">Your message could
59              not be posted.</p>';
60          echo '<p>' . $stmt->error . '</p>';
61      }
62
63      // Close the statement:
64      $stmt->close();
65      unset($stmt);
66
67      // Close the connection:
68      $mysqli->close();
69      unset($mysqli);
70
71  } // End of submission IF.
72
73  // Display the form:
74  ?>
75  <form action="post_message.php"
76      method="post">
77
78      <fieldset><legend>Post a message:
79          </legend>
80
81      <p><b>Subject</b>: <input
```

