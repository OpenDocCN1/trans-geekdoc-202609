
-   [密码重置问题](https://wiki.example.org/lessons_6) 是用户注册系统的常见问题，人们往往会忘记自己的密码。当你使用 `sha1()` 函数加密密码（如在 [第6课](#ch06.html#ch06) 和 [第7课](#ch07.html#ch07)）时，这是一个单向操作——无法解密。因此，你需要提供让用户重置密码的功能。仅仅在网上放置一个更新表单是不够的。你必须确保是正确的人在修改密码。一个简单而有效的方法是生成安全令牌，将其存储在数据库中，并通过电子邮件发送给用户。

-   此项目整合了你已学习的许多技术：表单验证、数据库交互以及电子邮件发送。为了节省时间，起始文件已包含基本结构，让你能够专注于新特性。

-   使用 `Zend_Db` 更新记录无需编写 SQL。`Zend_Db_Adapter` 对象的 `update()` 方法（在本教材中为 `$dbWrite`）会自动完成所有操作。该方法接受三个参数：

  - 表名  
  - 一个关联数组，键为列名，值为更新后的值  
  - 一个表达式，用于标识要更新的记录  

-   关联数组使用列名作为数组键。例如，下面的数组会将 `password` 和 `token` 列的值分别设置为 `$_POST['password']` 和 `NULL`：

  ```php
  $data = array('password' => $_POST['password'], 'token' => NULL);
  ```

-   如果你有 SQL 经验，第三个参数相当于 `WHERE` 子句，但不需要使用关键字 `WHERE`。例如，要更新 `users` 表中 `user_id` 为 2 的记录，调用 `update()` 时的三个参数如下：

  ```php
  $dbWrite->update('users', $data, 'user_id = 2');
  ```

-   直接在第三个参数中写入已知值是安全的，但如果值来源于用户输入，则必须使用 `quoteInto()` 防止 SQL 注入。例如，要将从用户输入的电子邮件地址用于第三个参数，需这样准备：

  ```php
  $where = $dbWrite->quoteInto('email = ?', $_POST['email']);
  $dbWrite->update('users', $data, $where);
  ```

-   也可以使用下面这种数组语法（改编自数组表示法）：

  ```php
  $where['email = ?'] = $_POST['email'];
  $dbWrite->update('users', $data, $where);
  ```

-   虽然数组元素的键通常应为数字或仅包含字母数字字符的字符串，但 `Zend_Db` 允许这种非常规语法，作为便利的快捷方式。

-   由于第三个参数可以是数组，你可以组合多个条件来定位要更新的记录，例如：

  ```php
  $where['email = ?'] = $_POST['email'];
  $where['username = ?'] = $_POST['username'];
  $dbWrite->update('users', $data, $where);
  ```

-   这会更新 `users` 表中满足 `email` 列等于 `$_POST['email']` **且** `username` 列等于 `$_POST['username']` 的记录。

-   ![Image](graphics/note.jpg) **NOTE:**  
    将多值数组作为 `update()` 方法的第三个参数等价于在 SQL `WHERE` 子句中使用 `AND` 运算符。若要使用 `OR` 运算符指定备选条件，则需将第三个参数构造为字符串。

-   如果在 `update()` 方法中省略第三个参数，则会更新表中**所有**记录，且更新方式相同。

-   为安全起见，`Zend_Db` 会将数据数组中的值转换为字符串并转义特殊字符。因此，你不能直接在数据数组中包含 SQL 函数（如 `CURDATE()` 用于当前日期）。相反，需要使用 `Zend_Db_Expr` 将 SQL 函数包装，例如：

  ```php
  $data = array(
      'password' => $_POST['password'],
      'registered' => new Zend_Db_Expr('CURDATE()')
  );
  ```

  若要在 `update()` 方法的第三个参数中使用 SQL 函数，可这样操作：

  ```php
  $today = new Zend_Db_Expr('CURDATE()');
  $where = "start_date > $today";
  ```

-   在处理密码重置请求脚本之前，先了解其所需的决策链。下面的插图概述了整个流程。

  ![Image](graphics/fig08_23.jpg)

-   重置请求表单只包含一个用于输入用户邮箱地址的字段。处理脚本需要检查该邮箱是否已注册。若未注册，则显示错误信息并终止后续处理。

-   若邮箱已存在，脚本会从数据库获取用户信息并生成一个 32 字符的安全令牌（难以猜测）。同时，用户记录会被更新，将该令牌存入数据库。随后，会向用户发送包含重置密码页面链接的电子邮件。链接的查询字符串中会附带用户的主键和安全令牌，以供后续验证身份。将链接直接发送至用户注册的邮箱，可确保只有该用户能够进行密码重置。

-   本部分完成后，会在屏幕上显示一条消息，提示用户查收包含重置说明的邮件。

-   虽然流程看似复杂，但所需的 PHP 代码不超过 40 行：

  **1.** 将 `request_reset.php` 从 `lesson08/start/scripts` 复制到 `lesson08/workfiles/scripts`。该文件已包含以下代码：

  ```php
  $errors = FALSE;  
  $result = FALSE;  
  if ($_POST) {  
      require_once('library.php');  
      require_once('mail_connector.php');  
      try {  
      } catch (Exception $e) {  
          echo $e->getMessage();  
      }  
  }
  ```

  只需要一个错误信息，因此 `$errors` 设为 `FALSE`。若邮箱验证失败或未注册，则将其设为 `TRUE`。

  另一个布尔变量 `$result` 用于决定是显示表单还是提示用户等待邮件。它最初为 `FALSE`，随后用于存储数据库查询的结果。若未在数据库中找到记录，则保持 `FALSE`；否则，它会是一个包含用户详细信息的数组（PHP 会将其视为 `TRUE`）。

  **2.** 在 `try` 块内部，先对用户输入进行验证。添加以下代码：

  ```php
  $val = new Zend_Validate_EmailAddress();  
  if (!$val->isValid($_POST['email'])) {  
      $errors = TRUE;  
  }
  ```

  **3.** 若邮箱通过验证，则使用它查询数据库。添加以下代码来构建 SQL 语句并执行查询：

  ```php
  if (!$errors) {  
      $sql = $dbRead->quoteInto('SELECT user_id, first_name, family_name, email FROM users WHERE email = ?', $_POST['email']);  
      $result = $dbRead->fetchRow($sql);  
  }
  ```

  这是一个 `SELECT` 查询，使用只读账户的 `quoteInto()` 方法安全地将用户输入嵌入 SQL。查询从 `users` 表中取出四列：`user_id`、`first_name`、`family_name`、`email`。

  在 [第7课](#ch07.html#ch07) 中，你使用过 `fetchAll()`，但本例使用 `fetchRow()`。请参阅“Choosing Between fetchAll() and fetchRow()”侧边栏，了解两者的区别。

  **Choosing Between fetchAll() and fetchRow()**  
  主要区别在于：`fetchAll()` 返回所有匹配行，而 `fetchRow()` 仅返回第一行。在 [第7课](#ch07.html#ch07) 中，只需判断是否存在匹配即可，因此使用哪种方法均不影响结果。但当需要访问具体值时，选择就很重要。`fetchRow()` 只取一行，结果以列名为键的关联数组形式存储，例如 `$result['user_id']`。
