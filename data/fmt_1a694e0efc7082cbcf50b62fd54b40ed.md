
When you test the page again, the backslash should have been removed.

### ![Image](img/note.jpg)**NOTE:**

This script comes from the PHP manual at [`docs.php.net/manual/en/security.magicquotes.disabling.php`](http://docs.php.net/manual/en/security.magicquotes.disabling.php) and is the least efficient way of dealing with magic quotes. You need to add the script to `library.php` only if there is a backslash in front of the apostrophe and you cannot use any other method of disabling magic quotes (see “Deciding to use or not to use ‘magic quotes’” in Lesson 2).

#### **Creating your own server behaviors**

Now you need to fix the redisplay of user input and error messages for the remaining input fields. Doing it all by hand is tedious. But take a look at what’s happened in `add_user.php`. In Design view, Dreamweaver has added what looks like a dynamic text object in the “First name” input field. The Server Behaviors panel also lists a Dynamic Attribute.

![Image](img/fig07_17.jpg)

Does this mean Dreamweaver has a server behavior that you can you use here? No, but it does have the Server Behavior Builder, which lets you create your own.

**1** With `add_user.php` open in the Document window, open the Server Behaviors panel by clicking its tab or choosing Window > Server Behaviors (`Ctrl+F9`/`Cmd+F9`). Click the plus button at the top left of the panel, and choose New Server Behavior.

**2.** In the New Server Behavior dialog box, make sure “Document type” is set to PHP MySQL, and type **Redisplay on Error** in the Name field. Leave the checkbox deselected, and click OK.

![Image](img/fig07_18.jpg)

### ![Image](img/note.jpg)**NOTE:**

Selecting the “Copy existing server behavior” checkbox lets you choose a server behavior on which to base a new one. However, you can do this only with server behaviors you have created yourself. You cannot use one of Dreamweaver’s built-in server behaviors.

This opens a large dialog box where you define the new server behavior.

**3.** Click the plus button labeled “Code blocks to insert” to open the Create a New Code Block dialog box. Accept the name suggested by Dreamweaver, and click OK. This lists the code block in the top pane and inserts some placeholder text in the “Code block” section.

![Image](img/fig07_19.jpg)

**4.** Replace the placeholder text with the PHP code that you added to the `<input>` tag’s `value` attribute in step 2 of “Preserving input when validation fails.” Here it is again:

```php
<?php if ($_POST && $errors) {  
    echo htmlentities($_POST['first_name'], ENT_COMPAT, 'UTF-8');  
}?>
```

**5.** If you leave the code like this, the server behavior would always use `$_POST['first_name']`. To make it editable, you need to replace `first_name` with a parameter.

Delete `first_name` but not the surrounding quotation marks. Make sure your insertion point is between the quotation marks of `$_POST['']`, and click the Insert Parameter in Code Block button.

**6.** In the “Parameter name” field, type **Field Name**, and click OK. The code in the “Code block” section should now look like this:

```php
<?php if ($_POST && $errors) {  
    echo htmlentities($_POST['@@Field Name@@'], ENT_COMPAT, 'UTF-8');  
}?>
```

The `@@` surrounding the parameter name tell Dreamweaver to replace the value when you use the server behavior.

**7.** You now need to tell the server behavior where to insert the code when you use it. You want to use it in the `value` attribute of an `<input>` tag.

Set “Insert code” to Relative to a Specific Tag. An option called Tag appears.

**8.** Select “input” from the Tag menu.

**9.** Set “Relative position” to “As the Value of an Attribute.” This opens up yet another option labeled Attribute.

**10.** Select “value” from the Attribute menu. The settings in the Server Behavior Builder dialog box should now look like this:

![Image](img/fig07_20.jpg)

**11** Click Next at the top right of the dialog box to open the dialog box that defines the options that will appear in the new server behavior’s dialog box.

![Image](img/fig07_21.jpg)

**12.** The values suggested by Dreamweaver are fine. Just click OK to complete the creation of the Redisplay on Error server behavior.

**13.** Create another custom server behavior to display the error messages. The process is the same, so the following instructions provide only the main points.

Click the plus button in the Server Behaviors panel, and choose New Server Behavior. Call it **Display Error Message**.

**14.** Create a new code block, and accept the default name. Replace the placeholder text with the following code:

```php
<?php if ($_POST && isset($errors['@@Field@@'])) {  
    echo $errors['@@Field@@'];  
} ?>
```

This is the same as the code used to display the error message next to the “First name” field except both instances of `first_name` have been replaced by the parameter `@@Field@@`.

**15.** The error message is displayed inside a `<span>` tag, so use the following settings at the bottom of the panel:

![Image](img/fig07_22.jpg)

**16.** Click Next, accept the default settings in the next dialog box, and click OK.

#### **Finishing the registration form**

The custom server behaviors make it easy to preserve user input and display error messages. As long as you use an array called `$errors` to store error messages, they can be used in any page, not just this one.

### ![Image](img/tip.jpg)**TIP:**

You could make the server behaviors more flexible by using a parameter for the `$errors` array. However, consistency in coding is a virtue, and using a fixed variable keeps the code simple.

**1.** With `add_user.php` open in Design view, select the “Family name” field in the registration form.

**2.** Click the plus button in the Server Behaviors panel, and choose “Redisplay on Error” to open the dialog box for your new server behavior.

**3.** Type **surname** in the Field Name field. The correct value should already be selected for “input tag.”

![Image](img/fig07_23.jpg)

**4.** Click OK. Dreamweaver inserts a dynamic text object in the field. It also lists “Redisplay on Error” in the Server Behaviors panel. Dreamweaver should also recognize the code in the “First name” field and list that as a “Redisplay on Error” server behavior.

### ![Image](img/note.jpg)**NOTE:**

Don’t worry if the hand-coded version isn’t recognized as a “Redisplay on Error” server behavior. Differences in spacing and new lines could affect Dreamweaver’s ability to recognize it as the same.

**5.** Repeat steps 1–4 with the Username and “Email address” fields, typing **username** and **email** respectively in Field Name.

**6.** You can’t apply the server behavior to the password fields. There’s no point in doing so anyway, because password fields don’t display user input.

**7.** Save `add_user.php`, and test the new server behavior by typing values in all fields except the password fields and submitting the form. The lack of passwords causes validation to fail and redisplays the values you entered.

### ![Image](img/note.jpg)**NOTE:**

If your page doesn’t work as expected, compare your code with `add_user03.php` in `lesson07/completed`. The most likely problem is a mistake in the “Code block” section of the Server Behavior Builder or in the parameter. You can edit a custom server behavior by clicking the plus button in the Server Behaviors panel and choosing Edit Server Behavior. To rebuild a server behavior from scratch, select its name in the Edit Server Behavior dialog box, and click Remove.

**8.** The error messages are displayed in `<span>` tags. In Design view, position the insertion point immediately to the right of the “Family name” input field, right-click, and choose Insert HTML.

This displays a small window for you to add an HTML tag. Type **sp** to highlight `span`, and press Enter/Return to insert an empty pair of `<span>` tags.

![Image](img/fig07_24.jpg)

**9.** Open Split view to make sure the insertion point is between the opening and closing `<span>` tags. If it isn’t, move it there by clicking between them.

**10.** Click the plus button in the Server Behaviors panel, and choose Display Error Message to open the dialog box for the other new server behavior.

**11.** Type **surname** in Field. The value of “span tag” should be “span [1]”. The span doesn’t have an `id` attribute, so Dreamweaver uses an array to identify it, counting from zero. So, this is the second `<span>` in the page.

![Image](img/fig07_25.jpg)

**12.** Repeat steps 8–11 for the remaining input fields. As long as the insertion point is between the opening and closing `<span>` tags, the Display Error Message dialog box selects the correct value for “span tag.” The value you type in Field should match the `name` attribute of each input field, namely: **username**, **password**, **conf_password**, and **email**.

![Image](img/fig07_26.jpg)

This completes `add_user.php`. Compare your code with `lesson07/completed/add_user.php` if the page doesn’t work as expected.

#### **Using a variable in a SELECT query**

The final part of the form input that needs to be validated before you can register the user in the database is the username. At the beginning of this lesson, you added a unique index to the `username` column, so the database rejects any attempt to insert the same value more than once. To avoid this, you need to check the database and display an error message if the username already exists.

`Zend_Db` offers several different ways of querying a database. In this case, the simplest way is to write your own SQL query. All you’re interested in is whether the username exists in the database, so selecting `user_id` is sufficient. To find the `user_id` for the username “hitchhiker,” the basic SQL query looks like this:

```sql
SELECT user_id FROM users WHERE username = 'hitchhiker'
```

SQL is designed to emulate human language, so the meaning should be obvious. By convention, the SQL commands are written in uppercase. The names of columns and tables are not enclosed in quotation marks, but string values are. So, this selects the values in the `user_id` column from the `users` table, where the value in the `username` column equals “hitchhiker.”

For this validation script, you want to match the value that comes from `$_POST['username']`, but you have no idea what this contains. It could be an attempt to hack into your database. So, you need to sanitize the value that’s inserted into the SQL. One way of doing this with `Zend_Db` is to use the `quoteInto()` method, which takes two arguments:

• The first argument is the SQL statement with a question mark used as a placeholder for the variable containing the user input.
• The second argument is the variable you want to use.

This sanitizes the value and wraps it in the necessary quotation marks.

To execute a `SELECT` query, you pass the SQL query to the `fetchAll()` method, which returns an array containing all the results.

#### **Checking for duplicate usernames**

Now that you know the basics of querying the database, you can fix the validation script so that it checks for a duplicate username.

**1.** The section in `user_registration.php` that validates the length and characters in the username ends with the following conditional statement (it should be around lines 19–21):

```php
if (!$val->isValid($_POST['username'])) {  
  $errors['username'] = 'Use 6-15 letters or numbers only';  
} else {  
  // check the database for duplicate username  
}
```

All the code in the following steps goes inside the `else` block.

**2.** Use the `quoteInto()` method to build the SQL statement with a question mark placeholder, and pass the variable to it as the second argument:

```php
$sql = $dbRead->quoteInto('SELECT user_id FROM users WHERE username = ?', $_POST['username']);
```

`$dbRead` is one of the `Zend_Db` objects you created in `library.php` earlier in this lesson to connect to the database.

**3** Execute the query by passing `$sql` to `fetchAll()`, and capture the result like this:

```php
$result = $dbRead->fetchAll($sql);
```

**4.** The `fetchAll()` method returns an array of results. PHP treats an array that contains any elements as `TRUE`. If a match is found, the username is a duplicate, so you can create an error message like this:

```php
if ($result) {  
  $errors['username'] = $_POST['username'] . ' is already in use';  
}
```

If no match is found, `$result` is empty, which PHP treats as `FALSE`, so the code inside the braces is ignored.

**5.** Save `user_registration.php`, and test `add_user.php` by entering a username that already exists in the database. If your database table is empty, you can add a record by selecting the `users` table in phpMyAdmin and clicking the Insert tab at the top of the page. When you submit the form with a duplicate username, you’ll see the error message.

You can compare your code with `lesson07/completed/scripts/user_registration03.php`.

#### **Inserting the user details with Zend_Db**

Inserting a record in a database with `Zend_Db` is very easy. You don’t need any SQL. Just create an associative array using the column names as the keys, and pass the table name and array as arguments to the `insert()` method.

You can now finish the user registration process:

**1.** If the user input passes all the validation tests, the `$errors` array is empty. You can use this to control whether to insert the data in the `users` table. Add this conditional statement at the end of the validation sequence, just above the `catch` block:

```php
if (!$val->isValid($_POST['email'])) {  
  $errors['email'] = 'Use a valid email address';  
}  
if (!$errors) {  
  // insert the details in the database  
}  
} catch (Exception $e) {
```

PHP implicitly treats an empty array as `FALSE`. The logical Not operator (an exclamation point) reverses a Boolean value, so this effectively means “if there are *no* errors.” If the `$errors` array is empty, the condition equates to `TRUE`, and the details will be inserted into the database.

All the remaining code goes inside this conditional statement.

**2** Create an associative array of the column names and values. You don’t need an array element for `user_id`, because MySQL automatically inserts the next available number for the primary key. The array should look like this:

```php
$data = array('first_name'  => $_POST['first_name'],  
              'family_name' => $_POST['surname'],  
              'username' => $_POST['username'],  
              'email' => $_POST['email'],  
              'password' => $_POST['password']  
);
```

```php
'username' => $_POST['username'],  
'password' => sha1($_POST['password']);
```

`Zend_Db` 会在将值插入数据库之前自动对其进行清理。密码是唯一需要特殊处理的值，它会传递给 `sha1()` 函数进行加密。

**3.** 要插入数据，需要使用具有读写权限的 `Zend_Db` 对象。在创建的数组后添加以下代码：

```php
$dbWrite->insert('users', $data);
```

`insert()` 方法的第一个参数是要使用的表名字符串，第二个参数是数据数组。

**4.** 插入数据就完成了。使用 `header()` 函数将用户重定向到登录页：

```php
header('Location: login.php');
```

### ![Image](img/note.jpg)**NOTE:**

严格来说，重定向时应该使用完整 URL，但所有当前浏览器都接受相对 URL。此快捷方式适用于本地调试，但在正式发布时应改为完整合格 URL。详见 [`docs.php.net/manual/en/function.header.php`](http://docs.php.net/manual/en/function.header.php)。

**5.** 保存 `user_registration.php`，并把 `lesson07/start/login.php` 复制到 `lesson07/workfiles` 文件夹。

**6.** 测试 `add_user.php` 以向数据库添加新用户。若无错误，则会跳转到 `login.php`。可将您的代码与 `lesson07/completed/scripts/user_registration.php` 对比。

### **Authenticating User Credentials with Zend_Auth**

改进后的注册表单的最终结果与 Dreamweaver 内置的“插入记录”服务器行为相同——它会将用户信息写入数据库。Dreamweaver 的用户身份验证服务器行为仍可用于控制页面访问。但 ZF 使创建用于验证用户凭据的脚本变得非常简便。使用外部文件存放控制访问和退出用户的脚本，可简化在任何页面中包含它们的过程。

#### **使用 Zend_Auth 控制用户访问**

`Zend_Auth` 类创建一个 *singleton* 对象，这意味着同一时间只能存在一个实例。实际影响是，你使用 `getInstance()` 而不是 `new` 关键字：

```php
$auth = Zend_Auth::getInstance();
```

`Zend_Auth` 支持多种验证方式。当用户凭据存储在数据库中时，验证由名为 `Zend_Auth_Adapter_DbTable` 的适配器完成，它接受以下五个参数：

• 一个 `Zend_Db` 对象，用于连接数据库  
• 包含用户凭据的表名  
• 存放用户名的列名  
• 存放密码的列名  
• 对密码应用的加密方式  

第五个参数使用问号 “?” 作为密码的占位符。`users` 表使用 `sha1()` 加密，因此适配器的创建方式如下：

```php
$adapter = new Zend_Auth_Adapter_DbTable($dbRead, 'users', 'username', 'password', 'sha1(?)');
```

当用户登录时，需要将用户名和密码传递给适配器：

```php
$adapter->setIdentity($_POST['username']);  
$adapter->setCredential($_POST['password']);
```

要检查用户凭据是否有效，将适配器传递给 `Zend_Auth` 对象的 `authenticate()` 方法：

```php
$result = $auth->authenticate($adapter);
```

如果登录成功，则存储用户信息：

```php
if ($result->isValid()) {  
  $storage = $auth->getStorage();  
  $storage->write($adapter->getResultRowObject(  
    array('username', 'first_name', 'family_name')));  
  header('Location: members_only.php');  
  exit;  
} else {  
  $failed = TRUE;  
}
```

### ![Image](img/note.jpg)**NOTE:**

`getStorage()` 与 `write()` 方法将用户信息存储为 `Zend_Auth_Storage_Session` 对象，这本质上只是另一种存储会话变量的方式。

通过 `hasIdentity()` 方法可以限制页面访问，该方法返回 `TRUE` 表示用户已登录。

要获取已登录用户的信息，使用 `getIdentity()` 方法：

```php
$auth = Zend_Auth::getInstance();  
if ($auth->hasIdentity()) {  
  $identity = $auth->getIdentity();  
}
```

可以通过 `$identity` 的属性访问详细信息，例如：

```php
$identity->first_name
```

要退出访客，使用 `clearIdentity()` 方法。

#### **创建登录脚本**

在 Lesson 6 中使用的“登录用户”服务器行为在验证失败时会跳转到另一页或重新显示登录表单，本次改进将显示错误消息以让用户了解情况。

**1.** 新建一个 PHP 页面，保存为 **user_authentication.php** 在 `lesson07/workfiles/scripts` 目录。该页面仅包含 PHP 代码，删除 Dreamweaver 自动插入的 HTML，并添加 PHP 开头标签。

**2.** 为错误消息创建一个 `FALSE` 布尔变量：

```php
$failed = FALSE;
```

如果登录失败，该变量会被设为 `TRUE` 并显示消息。

**3.** 登录脚本应仅在表单提交时运行。添加条件语句，在 `$_POST` 数组为 `TRUE` 时加载 `library.php`：

```php
if ($_POST) {  
  require_once('library.php');  
  // 检查用户凭据  
}
```

**4.** 由于脚本使用面向对象的写法，需在条件语句内部加入 `try` 与 `catch` 块，并在 `try` 块中实例化 `Zend_Auth`：

```php
try {  
  $auth = Zend_Auth::getInstance();  
} catch (Exception $e) {  
  echo $e->getMessage();  
}
```

### ![Image](img/tip.jpg)**TIP:**

快速选择 Zend_Auth 代码提示的方法是按下 `Ctrl+spacebar` 并输入 **dau**，这会立即选择 `Zend_Auth` 并插入。按回车确认后，输入两冒号可弹出 `getInstance()` 的代码提示。其余代码均放在 `try` 块内。

**5.** 创建 `Zend_Auth_Adapter_DbTable` 对象。在 `new` 关键字后输入 **hada** 可快速触发代码提示，该适配器需要五个参数，Dreamweaver 会在当前参数上高亮显示。

![Image](img/fig07_27.jpg)

该行代码应如下：

```php
$adapter = new Zend_Auth_Adapter_DbTable($dbRead, 'users', 'username', 'password', 'sha1(?)');
```

**6.** 设置适配器的身份和凭据值，它们来自 `$_POST` 数组中的 `username` 与 `password`：

```php
$adapter->setIdentity($_POST['username']);  
$adapter->setCredential($_POST['password']);
```

**7.** 将适配器传递给 `Zend_Auth` 对象的 `authenticate()` 方法，并保存结果：

```php
$result = $auth->authenticate($adapter);
```

**8.** 使用 `isValid()` 方法判断凭据是否正确。若正确，则存储信息并使用 `header()` 重定向到 `members_only.php`；若失败，则将 `$failed` 设为 `TRUE`。代码如下：

```php
if ($result->isValid()) {  
  $storage = $auth->getStorage();  
  $storage->write($adapter->getResultRowObject(array(  
    'username', 'first_name', 'family_name')));  
  header('Location: members_only.php');  
  exit;  
} else {  
  $failed = TRUE;  
}
```

相对链接在 include 文件中被视为相对于被 include 的页面，而不是相对于 include 文件本身的位置。虽然本脚本位于 `scripts` 文件夹，但它将被包含在 `login.php` 中，而 `login.php` 与 `members_only.php` 位于同一文件夹。因此，成功后重定向用户的相对链接需要相对于 `login.php`，而不是 `user_authentication.php`。

### 测试登录脚本

要使用登录脚本，需要在登录页面的 `DOCTYPE` 声明上方 include 它，并在登录失败时添加一个条件语句来显示错误信息。

1. 将 `lesson07/start` 中的 `login.php` 和 `members_only.php` 复制到 `lesson07/workfiles`。

2. 在 `login.php` 的 `DOCTYPE` 声明上方添加以下代码以 include `user_authentication.php`：

```php
```
