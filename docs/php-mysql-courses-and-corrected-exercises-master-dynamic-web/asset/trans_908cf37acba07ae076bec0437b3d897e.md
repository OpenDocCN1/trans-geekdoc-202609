

```
<textarea name="biography" placeholder="biography"></textarea><br>
<input type="submit" value="Save">
</form>
</body>
</html>
```

这段 HTML 代码创建了一个作者注册表单，包含姓、名、电子邮件和密码字段。提交表单时，数据将通过 POST 方法发送到文件 "author_registration.php"。表单使用外部样式表 "style.css" 进行样式设置，代码行如下：

```
<link rel="stylesheet" href="style.css">
```

## CSS 样式表

接下来，我们在 style.css 文件中放入以下代码来设置表单样式：

```
body {
font-family: Arial, sans-serif;
background-color: #f4f4f4;
margin: 0;
padding: 0;
display: flex;
justify-content: center;
align-items: center;
height: 100vh;
}

form {
background-color: #fff;
padding: 20px;
border-radius: 8px;
box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
width: 400px;
margin: auto; /* Ajout de cette ligne */
}

input {
width: calc(100% - 20px);
padding: 10px;
border: 1px solid #ccc;
border-radius: 4px;
margin-bottom: 15px;
}

textarea {
width: calc(100% - 20px);
padding: 10px;
border: 1px solid #ccc;
border-radius: 4px;
margin-bottom: 15px;
}
input[type="submit"] {
background-color: #007bff;
color: #fff;
border: none;
padding: 10px 20px;
cursor: pointer;
border-radius: 4px;
display: block;
margin: 0 auto;
}
input[type="submit"]:hover {
background-color: #0056b3;
}
```

表单的 "action" 属性指向名为 "author_registration.php" 的文件路径，该文件负责检索表单提交的数据，并将其插入到 "library" 数据库的 "authors" 表中。

让我们在 "library" 项目的根目录下创建此文件。

运行 index.php 将显示以下表单：

### 作者注册

姓
名
电子邮件
密码
个人简介
保存

## 数据处理与插入

### author_registration.php

```php
<?php
// Retrieve form data
$lastname = $_POST['lastname'];
$firstname = $_POST['firstname'];
$email = $_POST['email'];
$password = $_POST['password'];
$biography = $_POST['biography'];

// Database connection
$connection = new PDO("mysql:host=localhost;dbname=library", "root", "");
$connection->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Prepare insertion request
$request = $connection->prepare("INSERT INTO authors (last_name, first_name, email, password, biography) VALUES
(:lastname, :firstname, :email, :password, :biography)");

// Bind values to query parameters
$request->bindParam(':lastname', $lastname);
$request->bindParam(':firstname', $firstname);
$request->bindParam(':email', $email);
$request->bindParam(':password', $password);
$request->bindParam(':biography', $biography);

// Execute query
$result = $request->execute();

// Verify successful insertion
if ($result) {
    echo "Author is registered successfully!";
} else {
    echo "Error registered author.";
}

?>
```

这段 PHP 代码首先通过 POST 方法检索之前 HTML 表单传输的数据。接着，使用提供的凭据（主机名、数据库名、用户名和密码）通过 PDO 对象建立与 MySQL 数据库的连接。

随后，使用 **INSERT INTO** 语句准备一条插入 SQL 查询，以向 "authors" 表添加新行。"lastname"、"firstname"、"email" 和 "password" 字段的值通过 bindParam 方法绑定到查询参数。

将值绑定到参数后，使用 execute() 方法执行查询，并将执行结果存储在 $result 变量中。

最后，代码通过验证 $result 的值来检查插入是否成功。如果为 true，则显示一条消息，指示作者已成功注册。否则，将显示一条错误消息，指示注册作者时出现问题。

### 详细解释：

```php
$query = $connection->prepare("INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)");
```

这行代码准备了一条插入 SQL 查询，以便稍后在数据库中执行。详细解释如下：

**$connection->prepare()** ：这是 PDO 对象的一个方法，用于准备要执行的 SQL 查询。它返回一个表示已准备查询的 PDOStatement 对象。

"INSERT INTO authors (last_name, first_name, email, password, biography) VALUES (:lastname, :firstname, :email, :password, :biography)" ：这是已准备的插入 SQL 查询。它告诉数据库使用为 "last_name"、"first_name"、"email"、"password" 和 "biography" 列提供的值，向 "authors" 表插入一行新数据。列值由命名参数标签（":lastname"、":firstname"、":email"、":password"、":biography"）表示，这些标签将在运行查询时关联到提供的值。

查询结构如下：

- INSERT INTO authors：表示在 "authors" 表中执行插入请求。
- (last_name, first_name, email, password, biography)：指定要添加值的列名。
- VALUES (:lastname, :firstname, :email, :password, :biography)：指示要插入到相应列中的值。参数标记名为 ":lastname"、":firstname"、":email"、":password" 和 ":biography"。":password" 和 ":biography" 用于表示这些值。

通过使用命名参数标记，已准备的查询能够防止 SQL 注入攻击，并允许将 SQL 逻辑与要插入的数据值逻辑分离。

简而言之，这行代码在 "authors" 表中准备一条带有命名参数的插入查询，用于向指定列插入值。

- 带有 bindParam() 方法的五行代码将已准备查询中命名的参数标记的值绑定到指定的 PHP 变量。详细解释如下：

$request->bindParam(':lastname', $lastname); ：此行将 PHP 变量 $lastname 的值绑定到已准备查询中名为 ":lastname" 的参数标记。这意味着在执行查询时，变量 $lastname 的值将用于替换名为 ":lastname" 的参数标记。

$request->bindParam(':firstname', $firstname)；同样，此行将 PHP 变量 $firstname 的值绑定到已准备查询中名为 ":firstname" 的参数标记。

$request->bindParam(':email', $email)；此行将 PHP 变量 $email 的值绑定到已准备查询中名为 ":email" 的参数标记。

$request->bindParam(':password', $password)；同样，此行将 PHP 变量 $password 的值绑定到已准备查询中名为 ":password" 的参数标记。

$request->bindParam(':biography', $biography)；同样，此行将 PHP 变量 $biography 的值绑定到已准备查询中名为 ":biography" 的参数标记。

通过将 PHP 变量值关联到命名参数标记，这些行准备了带有指定值的查询，以便执行并向 "authors" 表的每个列插入值。这允许以安全可控的方式将用户提供的数据插入数据库。

代码行：$result = $request->execute(); 执行之前使用 PDO 对象的 prepare() 方法准备的查询。详细解释如下：

$result = $request->execute(); ：该指令在表示已准备查询的 PDOStatement 对象 $request 上调用 execute() 方法。该方法使用绑定到参数标记的值（之前通过 bindParam() 定义）执行已准备的 SQL 查询。如果查询执行成功，则返回 true；否则返回 false。返回值被赋给 $result 变量。随后可以使用该变量检查查询是否成功或失败。

此时，在 index.php 页面上提交并验证表单且未生成任何错误后，您将收到一条消息，显示 "Author is registered successfully!"。如果随后访问 URL http://localhost/phpmyadmin/ 并查询 "library" 数据库中的 "authors" 表，您应该看到一

