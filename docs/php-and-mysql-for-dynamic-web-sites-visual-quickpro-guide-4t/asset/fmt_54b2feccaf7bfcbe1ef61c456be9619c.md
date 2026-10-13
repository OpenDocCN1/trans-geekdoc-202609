
## 错误处理与数据库连接关闭

```php
84        echo 'error(s) occurred:<br />';
85        foreach ($errors as $msg) {
86            // Print each error.
87            echo " - $msg<br />\n";
88        }
89        echo '</p><p>Please try again.</p><p><br /></p>';
90    } // End of if (empty($errors)) IF.
91
92    $mysqli->close(); // Close the database connection.
93    unset($mysqli);
94
95 } // End of the main Submit conditional.
96 ?>
```

## 注册表单

```php
97 <h1>Register</h1>
98 <form action="register.php" method="post">
99     <p>First Name: <input type="text" name="first_name" size="15" maxlength="20" value="<?php if (isset($_POST['first_name'])) echo $_POST['first_name']; ?>" /></p>
100     <p>Last Name: <input type="text" name="last_name" size="15" maxlength="40" value="<?php if (isset($_POST['last_name'])) echo $_POST['last_name']; ?>" /></p>
101     <p>Email Address: <input type="text" name="email" size="20" maxlength="60" value="<?php if (isset($_POST['email'])) echo $_POST['email']; ?>" /> </p>
102     <p>Password: <input type="password" name="pass1" size="10" maxlength="20" value="<?php if (isset($_POST['pass1'])) echo $_POST['pass1']; ?>" /></p>
103     <p>Confirm Password: <input type="password" name="pass2" size="10" maxlength="20" value="<?php if (isset($_POST['pass2'])) echo $_POST['pass2']; ?>" /></p>
104     <p><input type="submit" name="submit" value="Register" /></p>
105 </form>
106 <?php include ('includes/footer.html'); ?>
```

---

### 5. 修改查询执行的确认逻辑（原第 53 行）

将条件改为：

```php
if ($mysqli->affected_rows == 1) {
```

之前的脚本版本使用结果变量来确认查询是否成功：

```php
if ($r) {
```

此处，条件判断更正式地断言受影响的行数等于 1。

### 6. 更新调试错误信息以使用对象（原脚本第 66 行）

```php
echo '<p>' . $mysqli->error . '<br /><br />Query: ' . $q . '</p>';
```

不再调用 `mysqli_error()` 函数，而是使用对象的 `error` 属性来存储数据库报告的问题。

### 7. 修改关闭数据库连接的两处代码

```php
$mysqli->close();
unset($mysqli);
```

第一行关闭连接，第二行销毁变量。此步骤释放已用内存，虽非强制，但属于专业规范。原脚本在两处关闭了数据库连接，请确保两处均已更新。

### 8. 保存脚本，放入 Web 目录，并在 Web 浏览器中测试。

如果所有代码均已按要求更新，注册脚本应能像以前一样正常工作。

## 获取查询结果

上一节演示了如何执行“简单”查询，即不返回结果行的查询。执行 `SELECT` 查询时，代码略有不同，因为必须处理查询结果。首先，建立 `MySQLi` 对象后，使用 `query()` 方法在数据库上运行查询。若查询预期返回结果集，将方法调用的结果赋值给另一个变量：

```php
$q = 'SELECT * FROM tablename';
$result = $mysqli->query($q);
```

变量 `$result` 将是 `MySQLi_Result` 类型的对象：正如某些函数返回字符串或整数，`MySQLi::query()` 将返回 `MySQLi_Result` 对象。其 `num_rows` 属性反映查询结果中的记录数：

```php
if ($result->num_rows > 0) { // Handle the results.
```

若查询仅返回一行，可直接调用 `fetch_array()` 方法获取：

```php
$row = $result->fetch_array();
```

该方法与过程式对应函数 `mysqli_fetch_array()` 类似，接受一个常量作为可选参数，指示返回的行应视为关联数组 (`MYSQLI_ASSOC`)、索引数组 (`MYSQLI_NUM`) 还是两者兼有 (`MYSQLI_BOTH`)。`MYSQLI_BOTH` 为默认值。

若有多条记录需获取，可使用循环：

```php
while ($row = $result->fetch_array(MYSQLI_NUM)) {
    // Use $row.
}
```

此时循环中的 `$row` 为数组，可使用 `$row[0]` 或 `$row['column']` 访问单个列（假设使用了相应常量）。若偏好 OOP 语法，可改用 `fetch_object()` 方法，从而创建对象而非数组：

```php
$q = 'SELECT user_id, first_name FROM users';
$result = $mysqli->query($q);
while ($row = $result->fetch_object()) {
    // Use $row->user_id
    // Use $row->first_name
}
```

处理完结果后，应释放其占用的资源：

```php
$result->free();
```

让我们利用这些信息更新 `view_users.php`（[Script 9.6](#ch09.html#ch09ex06)）。

### 检索查询结果的步骤

**1.** 在文本编辑器或 IDE 中打开 `view_users.php`（[Script 9.6](#ch09.html#ch09ex06)）。

**2.** 将 MySQL 连接脚本的引入改为（**[Script 16.3](#ch16.html#ch16ex03)**）：

```php
require ('../mysqli_oop_connect.php');
```

同样，路径需根据您的设置进行调整。

**3.** 将查询执行代码改为（原第 14 行）：

```php
$r = $mysqli->query($q);
```

无论执行何种类型的查询，均调用同一个 `MySQLi::query()` 方法。但此处将查询执行的结果赋值给一个新变量，该变量将为 `MySQLi_Result` 类型的对象。为简洁起见，此处变量名为 `$r`，您也可使用更正式的 `$result`。

**4.** 修改确定返回行数的方式（原脚本第 17 行）：

```php
$num = $r->num_rows;
```

结果对象的 `num_rows` 属性反映查询返回的记录数。该值赋给变量 `$num`，与之前一致。

请注意这是一个**属性**，而非**方法**（即 `$r->num_rows`，而非 `$r->num_rows()`）。

**5.** 将 `while` 循环改为：

```php
while ($row = $r->fetch_object()) {
```

此处改为调用 `MySQLi_Result` 对象的 `fetch_object()` 方法，而非调用 `mysqli_fetch_array()`。

---

**Script 16.3.** 本脚本使用 `MySQLi` 和 `MySQLi_Result` 类从数据库获取记录。

```php
1  <?php # Script 16.3 - view_users.php
2  // This script retrieves all the records
3  // from the users table.
4  // This is an OOP version of the script
5  // from Chapter 9.
6
7  $page_title = 'View the Current Users';
8  include ('includes/header.html');
9
10 // Page header:
11 echo '<h1>Registered Users</h1>';
12
13 require ('../mysqli_oop_connect.php');
14 // Connect to the db.
15
16 // Make the query:
17 $q = "SELECT CONCAT(last_name, ', ',
18     first_name) AS name, DATE_FORMAT
19     (registration_date, '%M %d, %Y')
20     AS dr FROM users ORDER BY
21     registration_date ASC";
22 $r = $mysqli->query($q); // Run the query.
23
24 // Count the number of returned rows:
25 $num = $r->num_rows;
26
27 if ($num > 0) { // If it ran OK, display the records.
28
29     // Print how many users there are:
30     echo "<p>There are currently $num registered users.</p>\n";
31
32     // Table header.
33     echo '<table align="center"
34         cellspacing="3" cellpadding="3"
35         width="75%">
36     <tr><td align="left"><b>Name</b>
37         </td><td align="left"><b>Date Registered</b></td></tr>
38 ';
```
