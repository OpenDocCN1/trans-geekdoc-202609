
下面的完整清单创建并填充所需的表格。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
      password=pwd.")) {
  $data = file_get_contents(__FILE__);
  pg_query ($db, "CREATE TABLE files (
        obj_id oid,
        name VARCHAR(255)
  )");
  pg_query ($db, "BEGIN");
  $oid = pg_lo_create($db);
  $file = pg_escape_string(__FILE__);
  $result = pg_query($db,
        "INSERT INTO files (obj_id, name) VALUES ($oid, '$file')");
  $lo = pg_lo_open($db, $oid, "w");
  pg_lo_write($lo, $data);
  pg_lo_close($lo);
  pg_query($db, "COMMIT");
  pg_close($db);
  echo "File inserted.";
} else {
  echo "Error!";
}
?>
```

清单 23.11 文件已写入数据库 ... ("pgsql-lo-write.php")

查看 pgAdmin 等管理工具，可以发现 OID 实际上已写入 obj_id 列（参见图 23.7）。每个表元素也有一个 OID，它（当然）是不同的，但在当前版本的 pgAdmin 4 中并未明确显示。

读取数据需要几个步骤（参见图 23.8）：

- 1. 从表中读取一个 OID。
- 2. 使用 pg_lo_open() 打开 lo。文件模式现在为 "r"，用于读取。
- 3. 使用 pg_lo_read() 读取文件内容，或使用 pg_lo_read_all() 将其完整直接返回到 Web 浏览器。
- 4. 使用 pg_lo_close() 关闭 lo。
- 5. 使用 pg_close() 关闭到数据库的连接。

![](img/ae7820c36e8f24c1623d26668b28e80e_673_0.png)

图 23.7 数据库中只有 OID

![](img/ae7820c36e8f24c1623d26668b28e80e_673_1.png)

图 23.8 之前的文件已输出

下面的相应清单读取并输出刚插入的文件。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
    pg_query($db, "BEGIN");
    $result = pg_exec($db,
        "SELECT obj_id FROM files WHERE name LIKE
        '%pgsql-lo-write.php%'");
    $row = pg_fetch_assoc($result);
    $lo = pg_lo_open($db, $row["obj_id"], "r");
    pg_lo_read_all($lo);
    pg_lo_close($lo);
    pg_query($db, "COMMIT");
    pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.12 ... 并再次读取 ("pgsql-lo-read.php")

## 23.3 应用示例

此处的示例与所有其他数据库章节中的示例相同；区别在于细节。

### 23.3.1 创建表

表通过调用 CREATE TABLE 按常规方式创建。还应注意，特殊的 PostgreSQL 数据类型 SERIAL 用于自动值。

```php
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
    $sql = "CREATE TABLE guestbook (
    id SERIAL PRIMARY KEY,
    heading VARCHAR(1000),
    entry VARCHAR(8000),
    author VARCHAR(50),
    email VARCHAR(100),
    date TIMESTAMP
");
if (pg_query($db, $sql)) {
    echo "Table created.<br />";
} else {
    echo "Error: ". pg_last_error() . "!";
}
pg_close($db);
} else {
    echo "Error!";
}
?>
```

清单 23.13 表已创建 ("gb-create.php")

### 23.3.2 输入数据

输入数据时会遇到第一个潜在困难。如果遵循其他章节中的相同过程，当输入包含元音变音符号等特殊字符时，可能会收到一条晦涩的错误消息。如图 23.9 所示。

![](img/ae7820c36e8f24c1623d26668b28e80e_675_0.png)

图 23.9 特殊字符的可能错误消息

原因：PostgreSQL 使用 Unicode，因此您还必须确保数据库接收的是 Unicode。如果将 php.ini 的 default_charset 设置设为 "UTF-8"，这应该有帮助。否则，只需在将表单输入发送到数据库之前，使用 utf8_encode()（当然还要使用 pg_escape_string()）处理所有表单输入。这样插入也会起作用。在以下清单中，我们手动执行 UTF-8 编码，以便您可以看到这种方法。如果对您来说似乎不起作用，请删除这些调用，改为设置默认字符集。

另一个特殊功能是确定最后插入元素的自动值。如我们在第 23.2.4 节中已提到，可以使用 pg_last_oid() 来确定 oid 列的值。然后启动另一个 SELECT 查询以获取 id 列中的值：

```php
$oid = pg_last_oid($result);
$result = pg_query($db, "
SELECT id FROM guestbook WHERE oid=$oid");
$row = pg_fetch_row($result);
$id = $row[0];
```

出于前面提到的原因，您以后需要 id 列来进行编辑；oid 中的值不够。在以下完整清单中，特殊功能以粗体突出显示。

```php
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_POST["Name"]) &&
    isset($_POST["Email"]) &&
    isset($_POST["Heading"]) &&
    isset($_POST["Comment"])) {
if ($db = pg_connect("host=localhost port=5432
dbname=PHP user=postgres password=pwd.")) {
$sql = vsprintf("INSERT INTO guestbook
(heading,
entry,
author,
email,
date)
VALUES ('%s', '%s', '%s', '%s', '%s')", [
pg_escape_string(utf8_encode($_POST["Heading"])),
pg_escape_string(utf8_encode($_POST["Comment"])),
pg_escape_string(utf8_encode($_POST["Name"])),
pg_escape_string(utf8_encode($_POST["Email"])),
date("Y-m-d H:i")
]);
if ($result = pg_query($db, $sql)) {
$oid = pg_last_oid($result);
$result = pg_query($db,
"SELECT id FROM guestbook WHERE oid=$oid");
$row = pg_fetch_row($result);
$id = $row[0];
echo "Entry added.<a href=\"gb-edit.php?id=$id\">Edit</a>";
} else {
echo "Error: " . pg_last_error() . "!";
}
pg_close($db);
} else {
echo "Error!";
}
}
?>
<form method="post" action="">
Name <input type="text" name="Name" /> <br />
Email address <input type="text" name="Email" /> <br />
Heading <input type="text" name="Heading" /> <br />
Comment
<textarea cols="70" rows="10" name="Comment"></textarea><br />
<input type="submit" name="Submit" value="Submit" />
</form>
</body>
</html>
```

清单 23.14 可以输入数据 ("gb-enter.php")

### 23.3.3 输出数据

读取数据时必须反转数据的 UTF-8 编码；相应的 PHP 函数名为 utf8_decode()。以下清单显示了此目的的完整代码。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = pg_query($db, $sql);
while ($line = pg_fetch_object($result)) {
printf("<p><a href=\"mailto:%s\">%s</a> wrote on %s:</p>
<h3>%s</h3><p>%s</p>\n",
urlencode(utf8_decode($line->email)),
htmlspecialchars(utf8_decode($line->author)),
htmlspecialchars(utf8_decode($line->date)),
htmlspecialchars(utf8_decode($line->heading)),
nl2br(htmlspecialchars(utf8_decode($line->entry)))
);
}
pg_close($db);
} else {
echo "Error!";
}
?>
</body>
</html>
```

清单 23.15 已输出留言簿数据 ("gb-show.php")

如果忘记 `utf8_decode()`，则特殊字符可能无法正确显示。

### 23.3.4 删除数据

管理脚本在双击后向数据库发送 `DELETE` 命令。输出所有留言簿数据时，请务必使用 `utf8_decode()` 正确转换特殊字符。

```html
<html>
<head>
<title>Guestbook</title>
</head>
<body>
<h1>Guestbook</h1>
<?php
if (isset($_GET["id"]) && is_numeric($_GET["id"])) {
if (isset($_GET["ok"])) {
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$id = pg_escape_string($_GET["id"]);
$sql = "DELETE FROM guestbook WHERE id=$id";
if (pg_query($db, $sql)) {
echo "<p>Entry deleted.</p>
<p><a href=\"gb-admin.php\">Back to overview
</a></p>";
} else {
echo "Error: " . pg_last_error() . "!";
}
pg_close($db);
} else {
echo "Error!";
}
} else {
printf("<a href=\"gb-admin.php?id=%s&ok=1\">Really delete?</a>",
urlencode($_GET["id"]));
}
} else {
if ($db = pg_connect("host=localhost port=5432 dbname=PHP user=postgres
password=pwd.")) {
$sql = "SELECT * FROM guestbook ORDER BY date DESC";
$result = pg_query($db, $sql);
while ($row = pg_fetch_object($result)) {
printf("<a href=\"gb-admin.php?id=%s\">Delete this entry</a> <a href=\"gb-admin.php?id=%s\">Edit this entry</a></p>
<p><a href=\"mailto:%s\">%s</a> wrote on at %s:</p>
<h3>%s</h3><hr noshade=\"noshade\" />\n",
urlencode($row->id),
urlencode($row->id),
htmlspecialchars(utf8_decode($row->email)),
htmlspecialchars(utf8_decode($row->author)),
htmlspecialchars(utf8_decode($row->date)),
htmlspecialchars(utf8_decode($row->heading)),
nl2br(htmlspecialchars(utf8_decode($row->entry)))
);
}
pg_close($db);
} else {
echo "Error!";
}
}
?>
</body>
</html>
```

清单 23.16 带删除选项的所有数据显示 ("gb-admin.php")

### 23.3.5 编辑数据

最后，必须创建带有编辑选项的表单。这里需要在两个地方注意 Unicode 字符。从数据库读取数据以供显示时必须使用 utf8_decode()，写回时必须使用 utf8_encode()。其余代码与其他数据库模块完全类似，因此该示例可以非常快速地实现。
