
`UPDATE` 查询类似于你在 [第 5 章](#ch05.html#ch05) “SQL 简介” 中可能见到的示例。该查询使用表单提交的值更新三个字段——名、姓和电子邮件地址。该系统之所以有效，是因为表单预先填充了现有值。因此，如果你在表单中编辑了名但未改动其他内容，数据库中的名值将使用这个新值进行更新，但姓和电子邮件地址的值将使用其当前值进行“更新”。这比试图确定哪些表单值已更改并仅更新数据库中的那些值要容易得多。

**8.** 报告更新结果：

```
if (mysqli_affected_rows($dbc) == 1) {
    echo '<p>The user has been edited.</p>';
} else {
    echo '<p class="error">The user could not be edited due to a system error. We apologize for any inconvenience.</p>';
    echo '<p>' . mysqli_error($dbc) . '<br />Query: ' . $q . '</p>';
}
```

`mysqli_affected_rows()` 函数将返回数据库中受最近一次查询影响的行数。如果三个表单值中的任何一个被修改了，该函数将返回值 1。此条件语句检测这一点并打印一条指示成功或失败的消息。

请记住，如果 `UPDATE` 命令成功运行但并未实际影响任何记录，`mysqli_affected_rows()` 函数将返回值 0。因此，如果你在不更改任何表单值的情况下提交此表单，将显示系统错误，这在技术上可能并不正确。一旦你让此脚本有效运行，你可以更改错误消息，以便在 `mysqli_affected_rows()` 返回 0 时指示未进行任何更改。

**9.** 完成邮箱条件判断：

```
} else {
    echo '<p class="error">The email address has already been registered.</p>';
}
```

此 `else` 完成了检查电子邮件地址是否已被其他用户使用的条件判断。如果是，则打印该消息。

**10.** 完成 `$errors` 条件判断：

```
} else {
    echo '<p class="error">The following error(s) occurred:<br />';
    foreach ($errors as $msg) {
        echo " - $msg<br />\n";
    }
    echo '</p><p>Please try again.</p>';
}
```

`else` 用于报告表单中的任何错误（即缺少名、姓或电子邮件地址），就像在注册脚本中一样。

**11.** 完成提交条件判断：

```
} // End of submit conditional.
```

最后的右大括号结束主提交条件判断。在本例中，每当访问该页面时都会显示表单。提交表单后，数据库将被更新，表单将再次显示，现在显示最新信息。

**12.** 检索被编辑用户的信息：

```
$q = "SELECT first_name, last_name, email FROM users WHERE user_id=$id";
$r = @mysqli_query($dbc, $q);
if (mysqli_num_rows($r) == 1) {
    $row = mysqli_fetch_array($r, MYSQLI_NUM);
}
```

为了填充表单元素，必须从数据库中检索该用户的当前信息。此查询类似于 `delete_user.php` 中的查询。条件判断——检查是否返回了单行——确保提供了有效的用户 ID。

**13.** 显示表单：

```
echo '<form action="edit_user.php" method="post">
<p>First Name: <input type="text" name="first_name" size="15" maxlength="15" value="' . $row[0] . '" /></p>
<p>Last Name: <input type="text" name="last_name" size="15" maxlength="30" value="' . $row[1] . '" /></p>
<p>Email Address: <input type="text" name="email" size="20" maxlength="60" value="' . $row[2] . '" /></p>
<p><input type="submit" name="submit" value="Submit" /></p>
<input type="hidden" name="id" value="' . $id . '" />
</form>';
```

表单只有三个文本输入框，每个输入框都使用从数据库检索的数据使其具有粘性。同样，用户 ID（`$id`）作为隐藏表单输入存储，以便处理过程也能访问此值。

**14.** 完成 `mysqli_num_rows()` 条件判断：

```
} else {
    echo '<p class="error">This page has been accessed in error.</p>';
}
```

如果因提交了无效的用户 ID 而导致数据库未返回任何记录，则显示此消息。

**15.** 完成 PHP 页面：

```
mysqli_close($dbc);
include('includes/footer.html');
?>
```

**16.** 将文件保存为 `edit_user.php` 并将其放在你的 Web 目录中（与 `view_users.php` 在同一文件夹下）。

**17.** 通过首先在 `view_users.php` 页面中单击 *Edit* 链接 ![Image](graphics/circle-b.jpg)和 ![Image](graphics/circle-c.jpg) 来运行该页面。

![Image](graphics/10_figure_11_b.jpg)

![Image](graphics/circle-b.jpg)成功更新数据库后，新值显示在表单中（与 ![Image](graphics/graycircle-a.jpg) 中的表单值进行比较）。

![Image](graphics/10_figure_12_c.jpg)

![Image](graphics/circle-c.jpg)如果你尝试将记录更改为现有的电子邮件地址，或者如果你省略了某项输入，则会报告错误。

---

Tip

按原样编写，粘性表单始终显示从数据库检索的值。这意味着如果发生错误，将使用数据库值，而不是用户刚刚输入的值（如果它们不同）。要更改此行为，粘性表单必须检查 `$_POST` 变量是否存在，如果存在则使用它们，如果不存在则使用数据库值。

---

Tip

此编辑页面不包含更改密码的功能。该概念已在 `password.php`（脚本 9.7）中演示。如果你想在此处加入该功能，请记住你无法显示当前密码，因为它以哈希格式存储（即不可解密）。相反，只需提供两个用于更改密码的框（新密码输入框和确认框）。如果提交了这些值，也要在数据库中更新密码。如果这些输入留空，则不更新数据库中的密码。

---

### 查询结果分页

*分页* 是一个你熟悉的概念，即使你不知道这个术语。当你使用像 Google 这样的搜索引擎时，它会将结果显示为一系列页面，而不是一个长长的列表。`view_users.php` 脚本将受益于此功能。

查询结果分页广泛使用了在 [第 5 章](#ch05.html#ch05) 中介绍的 `LIMIT` SQL 子句。`LIMIT` 限制实际返回的匹配记录的子集。要对查询返回的结果进行分页，每次页面迭代将使用不同的 `LIMIT` 参数运行相同的查询。第一次查看页面将请求前 *X* 条记录；第二次查看页面，第二组 *X* 条记录；以此类推。要使其工作，必须在 URL 中从页面传递两个值到页面，就像从 `view_users.php` 页面传递用户 ID 一样。第一个值是要显示的总页数。第二个值是指示页面在此次迭代中应显示哪些记录的指标（即从何处开始获取记录）。

此处将演示另一种更美观的技术：使用交替的背景颜色显示表格的每一行——每一条返回的记录 ![Image](graphics/circle-a.jpg)。利用三元运算符（参见侧边栏“三元运算符”），可以轻松实现此效果。

![Image](graphics/10_figure_13_a.jpg)

![Image](graphics/circle-a.jpg)交替表格行颜色使这份用户列表更易读（每隔一行具有浅灰色背景）。

这里有很多很好的新信息需要涵盖，所以为了更容易跟上，让我们从头编写这个版本，而不是试图修改脚本 10.1。
