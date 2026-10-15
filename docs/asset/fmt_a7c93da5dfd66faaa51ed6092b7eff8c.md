
**注意**：**不要**在页面末尾添加关闭的 PHP 标签。关于省略闭合标签的说明请参见侧边栏 “Omitting the Closing PHP Tag”。

### 使用 Zend_Db 连接数据库

在 `ZF` 中，所有与数据库的通信均通过 `Zend_Db` 对象完成。这类似于 Dreamweaver 服务器行为中设置 MySQL 连接，但有两个显著优势：

- `Zend_Db` 对象在真正需要时才建立数据库连接，这比 Dreamweaver 的 MySQL 连接更节省资源，因为后者在脚本不需要时也会始终保持连接。

### 省略闭合 PHP 标签

当脚本以 PHP 代码结束时，闭合标签 `?>` 是可选的。事实上，`ZF` 编码规范禁止在仅包含 PHP 代码的页面中使用闭合标签。去掉闭合标签可以避免 “headers already sent” 错误（参见侧边栏 “Why the Next Page Doesn’t Always Load”），并防止产生大量不必要的空格。

Dreamweaver CS5 支持省略闭合标签，但如果在包含文件的同一页面中留下闭合标签后跟空白或换行，可能会导致 Design 视图切换到 CSS 奇偶模式。若此现象影响你的工作，可添加闭合标签，但确保其后没有任何空格或换行字符。

- 当 HTML 紧跟在 PHP 脚本的同一页面中时，必须使用闭合标签。若 HTML 位于父页面中，则不必在当前页面加入闭合标签；PHP 引擎会在包含文件结束时自动切回 HTML 模式。

- `Zend_Db` 包含多个适配器子类，用于连接不同的数据库系统。要连接其他数据库，只需使用相应的子类创建 `Zend_Db` 对象。通常只需一行代码，除非你的 SQL 使用了数据库特定的函数。

大多数页面都需要数据库连接，因此将 `Zend_Db` 对象实例化放在加载 `ZF` 类的同一文件中是合理的。

**1.** 要建立数据库连接，需要提供数据库服务器地址、用户名、密码以及数据库名称。将这些信息以关联数组形式（见 “Creating an associative array” 在 Lesson 3）传递给 `Zend_Db` 构造函数，使用键 `‘host’`、`‘username’`、`‘password’` 和 `‘dbname’`。

在 `library.php` 的底部，为 `cs5write` 账户创建数组如下：

```php
$write = array('host' => 'localhost',  
                 'username' => 'cs5write',  
                 'password' => 'Bow!e#CS5',  
                 'dbname' => 'phpcs5');
```

> ![Image](img/tip.jpg)**TIP:**  
> 对关联数组进行缩进并对齐 `=>` 运算符虽非必需，但能提升代码可读性和调试便利性。

**2.** 在 `cs5read` 数组的下方，再创建一个数组：

```php
$read = array('host' => 'localhost',  
                'username' => 'cs5read',  
                'password' => '5T@rmaN',  
                'dbname' => 'phpcs5');
```

**3.** 根据你使用的数据库以及远程服务器的 PHP 配置，选择相应的 `Zend_Db` 适配器：

- 如果远程服务器支持 `pdo_mysql`，使用：

```php
$dbWrite = new Zend_Db_Adapter_Pdo_Mysql($write);
```

- 如果远程服务器仅支持 `mysqli`，使用：

```php
$dbWrite = new Zend_Db_Adapter_Mysqli($write);
```

> ![Image](img/tip.jpg)**TIP:**  
> 不必完整输入类名。正如 Lesson 1 所述，Dreamweaver 的代码提示会忽略下划线，并在名称中匹配子串。输入 **pdomy** 即可跳转到 `Zend_Db_Adapter_Pdo_Mysql`，随后按回车确认。使用 `$write` 作为构造函数参数时，Dreamweaver 会自动插入左方括号，需要自行删除。

**4.** 为 `cs5read` 账户创建另一个对象，使用合适的适配器：

```php
$dbRead = new Zend_Db_Adapter_Pdo_Mysql($read);
```

```php
$dbRead = new Zend_Db_Adapter_Mysqli($read);
```

**5.** 由于 `Zend_Db` 对象在需要时才建立数据库连接，建议在代码末尾添加条件语句以测试连接是否正常。在 library.php 的末尾添加以下条件语句：

```php
if ($dbWrite->getConnection()) {  
  echo 'Write OK<br />';  
}  

if ($dbRead->getConnection()) {  
  echo 'Read OK';  
}
```

在对象后面输入 `->` 时，IDE 会提示该对象可用的方法。`getConnection()` 方法名很直观。如果每个连接都正常，条件语句会显示确认信息；如果有问题，会出现类似下面的致命错误：

![Image](img/fig07_13.jpg)

不要慌张。第二行的信息指出 `cs5write` 的访问被拒绝，并且使用了密码。这通常意味着密码错误。

另一个可能的原因是选择了错误的适配器类。很容易把 `Zend_Db_Adapter_Pdo_Mssql` 与 `Zend_Db_Adapter_Pdo_Mysql` 混淆。前者用于 Microsoft SQL Server。如果犯此错误，错误信息可能会提示 `mssql` 驱动程序未安装。即使已安装，也可能是连接到错误的数据库服务器。

请仔细检查代码，尤其是拼写和大小写。

**6.** 确认连接正常后，删除步骤 5 中添加的代码。已不再需要。

保持 library.php 打开，以便在下一节继续使用。

### ![Image](img/note.jpg)**NOTE:**

关于其他数据库的 `Zend_Db` 适配器类的详细信息，请参阅 [`framework.zend.com/manual/en/zend.db.adapter.html`](http://framework.zend.com/manual/en/zend.db.adapter.html)。

#### 使用 try 和 catch 捕获异常

ZF 是面向对象的框架。如果脚本的任何部分出现错误，它会 *抛出异常*。与普通 PHP 错误不同，普通错误会在出现的位置直接显示消息，而异常可以在脚本的其他部分进行处理。仔细观察前面截图中第一行的恐怖错误信息，你会看到它指的是 “uncaught exception”。抛出异常时必须捕获它。

为了避免这种丑陋的错误信息，应该始终把面向对象的代码包裹在 `try` 与 `catch` 块中：

```php
try {  
  // 主脚本  
} catch (Exception $e) {  
  echo $e->getMessage();  
}
```

`try` 块中的大括号内的代码是主脚本，PHP 会尝试执行这些代码。如果一切正常，代码按预期运行，`catch` 块被忽略；如果在 `try` 块内部抛出异常，`try` 块内的代码会被中止，`catch` 块随即执行。

对象可以定义多种异常类型，因此可以为每种异常编写独立的 `catch` 块。`catch` 括号里的 `Exception` 表示这是一个通用的捕获块，用于处理所有异常。异常被赋值给变量 `$e`，以便你可以访问其中的任何信息。当前的 `catch` 块仅使用 `echo` 和 `getMessage()` 方法来显示错误信息。在正式部署到真实站点时，你可以把 `catch` 块中的代码替换为更优雅的处理方式，例如显示专门的错误页面。

你需要在 library.php 的大部分代码上包裹 `try` 块，并在页面底部添加 `catch` 块。

**1.** 将光标放在下面这行的末尾，按回车键插入一行空行：

```php
require_once('Zend/Loader/Autoloader.php');
```

**2.** 在新行上输入 **try**，然后输入左大括号 `{`。

**3.** 选中下面那行到页面底部的所有代码，点击编辑器工具栏中的 **Indent Code** 图标 ![Image](img/indent_code.jpg) 以缩进，使其位于 `try` 块内。

**4.** 在页面底部新增一行，插入 `try` 块的闭合大括号 `}` 以及对应的 `catch` 块：

```php
} catch (Exception $e) {  
  echo $e->getMessage();  
}
```

**5.** 保存 library.php。你可以将你的代码与 lesson07/completed/library.php 进行对比。

#### 使用 Zend_Validate 检查用户输入

服务器端验证用户输入的标准做法是编写一系列条件语句来检查值是否满足特定条件。例如，若要检查密码长度是否在 8 到 15 个字符之间，可以使用 PHP 函数 `strlen()`，它返回字符串长度，如下所示：

```php
if (strlen($_POST['password']) >= 8 && strlen($_POST['password']) <= 15) {  
  // 合法  
}
```

这段代码能工作，但并未检查密码中使用了哪些字符。输入 8 个空格仍能通过此检查。因此，需要额外的条件语句来确保所有条件都满足。

`Zend_Validate` 的工作方式类似，但提供了一组常用的验证器。每个子类具有易记的名称，使你的验证脚本更易阅读，且无需成为 PHP 函数专家即可确保用户输入符合要求。 **表 7.1** 列出了最常用的子类。每个子类名前缀为 `Zend_Validate_`，因此 `Alnum` 变为 `Zend_Validate_Alnum`。

例如，要检查字符串长度是否在 8–15 个字符之间，使用 `Zend_Validate_StringLength` 如下：

```php
$val = new Zend_Validate_StringLength(8,15);
```

这创建了一个 `Zend_Validate_StringLength` 对象，将最小值和最大值分别设为 8 和 15，并赋值给 `$val`。

要检查 `$_POST['password']` 是否在 8–15 个字符之间，将其作为参数传递给 `isValid()` 方法：

```php
$val->isValid($_POST['password'])
```

如果 `$_POST['password']` 包含 8–15 个字符，则返回 `TRUE`；否则返回 `FALSE`。

通常在验证失败时会生成错误信息。可以使用逻辑非运算符（见“使用逻辑非运算符”在 第 3 课）如下实现：

```php
$val = new Zend_Validate_StringLength(8,15);  

if (!$val->isValid($_POST['password'])) {  
  $errors['password'] = 'Password should be 8-15 characters';  
}
```

逻辑非运算符查找不合法的值，因此只有当 `$_POST['password']` 不是 8–15 个字符时，错误信息才会被赋值给 `$errors['password']`。

该验证虽然能满足基本需求，但同样只检查字符数量。输入 8–15 个空格仍会通过验证。要同时满足多个条件，需要组合使用多个验证器。一种方法是编写一系列条件语句，但 Zend Framework 提供了另一种更简洁的方案——**链式验证**。

**表 7.1 常用验证类**（图片略）

![Image](img/t0229-01.jpg)

![Image](img/t0229-02.jpg)

#### 链式验证以设置多重条件

要检查多于一个条件时，创建一个通用的 `Zend_Validate` 对象，并使用其 `addValidator()` 方法添加每个新测试。你可以分别实例化每个验证器，然后将其作为 `addValidator()` 的参数，如下所示：

```php
$val = new Zend_Validate();  

$val1 = new Zend_Validate_StringLength(8, 15);  

$val2 = new Zend_Validate_Alnum();  

$val->addValidator($val1);  

$val->addValidator($val2);
```

不过，更简洁的写法是直接在 `addValidator()` 参数中实例化验证器：

```php
$val = new Zend_Validate();  

$val->addValidator(new Zend_Validate_StringLength(8, 15));  

$val->addValidator(new Zend_Validate_Alnum());
```

甚至可以将 `addValidator()` 调用串联起来：

```php
$val = new Zend_Validate();  

$val->addValidator(new Zend_Validate_StringLength(8, 15))  

-   addValidator);
```

Notice that there is no semicolon at the end of the second line, and the second `->` operator isn’t prefixed by the `$val` object. Indenting it like this makes the code easier to read, but you could place it immediately after the closing parenthesis at the end of the first `addValidator()` method.

### ![Image](img/note.jpg)`NOTE`:

Chaining methods like this will be familiar to readers with jQuery experience. Unfortunately, Dreamweaver CS5’s code hints don’t support chaining methods, so the code in this book always uses separate statements to apply methods to ZF objects.

All three sets of code perform the same task: `$val` tests for a string 8–15 characters long that contains only letters and numbers, with no spaces.

Armed with this knowledge, you can validate the input of the registration form.

#### Building the validation script (1)

The user registration form from Lesson 6 has been modified to add a text input field for the email address and some hints for the user. The style sheet has also been changed to make room for error messages.

**1.** Copy `add_user.php` from lesson07/start to lesson07/workfiles.

**2** It’s more efficient to use an external file for the validation code so you can reuse the code for other projects. Choose File > New, and create a new PHP page. Save it as **user_registration.php** in lesson07/workfiles/scripts.

**3.** In the file you just created, switch to Code view, delete the HTML code inserted by Dreamweaver, and add an opening PHP tag at the top of the page. This page will contain only PHP, so it shouldn’t have a closing PHP tag.

**4.** After the opening PHP tag, initialize an array to store error messages:

```php
$errors = array();
```

**5.** When the form is first loaded, there’s nothing to process, so the `$_POST` array is empty. An empty array is treated as `FALSE` (see “What PHP regards as false” in Lesson 3), so you can use this to ensure that the validation script is run only when the form is submitted. Add a conditional statement like this:

```php
if ($_POST) {  

  // run the validation script  

}
```

**6.** The validation script needs access to the ZF files. Include library.php by adding it between the curly braces of the conditional statement:

```php
require_once('library.php');
```

**7.** Add `try` and `catch` blocks inside the conditional statement created in the previous step:

```php
if ($_POST) {  

  // run the validation script  

  require_once('library.php');  

  try {  

    // main script goes here  

  } catch (Exception $e) {  

    echo $e->getMessage();  

  }  

}
```

**8.** The first input field you need to validate is `first_name`. Personal names are alphabetic, so `Zend_Validate_Alpha` seems like a good choice. Add the following code inside the `try` block:

```php
try {  

  // main script goes here  

  $val = new Zend_Validate_Alpha(TRUE);  

  if (!$val->isValid($_POST['first_name'])) {  

    $errors['first_name'] = 'Required field, no numbers';  

  }  

} catch (Exception $e) {
```

**9** Before going any further, it’s a good idea to test the script so far. Save user_registration.php, and switch to add_user.php.

Include user_registration.php by inserting space above the `DOCTYPE` declaration and adding the following code:

```php
<?php  

require_once('scripts/user_registration.php');  

?>
```

**10.** To display error messages next to each input field, you need to add a pair of `<span>` tags with a PHP conditional statement in between.

Locate the following line in Code view:

```html
<input type="text" name="first_name" id="first_name" />
```

### ![Image](img/tip.jpg)`TIP`:

It’s a good idea to work in Vertical Split view (choose View > Split Vertically and click Split in the Document toolbar). Select the input field in Design view to highlight the `<input>` tag in Code view.

**11.** Add the following code after the `<input>` tag:

```html
  <input type="text" name="first_name" id="first_name" />  
  <span>  
  <?php  
  if ($_POST && isset($errors['first_name'])) {  
    echo $errors['first_name'];  
  }  
  ?>  
  </span>  
</p>
```

The conditional statement begins by checking `$_POST`. If the form has been submitted, it equates to `TRUE`, so the next test is applied. The `isset()` function checks the existence of a variable. `$errors['first_name']` is created only if the validation test fails, so `$errors['first_name']` is displayed if the form has been submitted and the `first_name` field failed validation.

The `<span>` tags remain empty if there isn’t an error, so it might seem more logical to include them inside the conditional statement. They have been left outside to act as a hook for a custom server behavior that you’ll create later in this lesson to insert error messages for the other fields.

**12.** Save add_user.php, and click Live View or press F12/Opt+F12 to test it. Start by leaving the “First name” field blank. Submit the form, and remember to hold down the Ctrl/Cmd key if you’re in Live View. If all your code is OK, you should see an error message next to the “First name” field.

![Image](img/fig07_14.jpg)

**13.** Now try typing your own name and resubmitting the form. The error message disappears.

**14.** Type some numbers and resubmit. The error message reappears.

**15.** Click inside the field, and press the spacebar several times before resubmitting the form. The error message disappears. You still have the problem of an empty field.

Unfortunately, the `NotEmpty` validation class doesn’t have an option to handle this. Also, personal names sometimes include a hyphen or apostrophe. The best solution is to use a *regular expression*—a pattern for matching text.

**16.** Turn off Live View, if necessary, and switch back to user_registration.php. Change the validator from `Alpha` to `Regex` like this:

```php
$val = new Zend_Validate_Regex('/^[a-z]+[-\'a-z ]+$/i');
```

This regular expression—or regex, for short—makes sure the value begins with at least one letter and is followed by at least one more letter, hyphen, apostrophe, or space.

This is fine for English. If you need to accept accented letters or names written in a different script, such as Japanese or Chinese, use the following:

```php
$val = new Zend_Validate_Regex('/^\\p{L}+[-\\'\\p{L} ]+$/u');
```

This line performs the same task, but also accepts Unicode letter characters.

### ![Image](img/tip.jpg)`TIP`:

Regular expressions are used widely for matching text in PHP and other programming languages. Learn how to build your own regexes by following my tutorial series in the Adobe Developer Connection at [www.adobe.com/devnet/dreamweaver/articles/regular_expressions_pt1.html](http://www.adobe.com/devnet/dreamweaver/articles/regular_expressions_pt1.html).

**17.** Save user_registration.php, and test the “First name” field again. It now accepts names with spaces, hyphens, and apostrophes but rejects numbers and values that don’t begin with a letter.

The second regex accepts names like Françoise, ![Image](img/233fig01.jpg), and ![Image](img/233fig02.jpg).

You can compare your code with lesson07/completed/add_user01.php and lesson07/completed/scripts/user_registration01.php.

#### Building the validation script (2)

The rest of the script follows a similar pattern: You need a validator for each input field and need to add a message to the `$errors` array if the value fails the test. Sometimes a validator can be reused, but if it’s no longer appropriate, you can overwrite it by assigning a new one to the same variable.

**1.** The `surname` input field can use the same validator as first_name, so add the following code immediately after the first_name test in user_registration.php:

```php
if (!$val->isValid($_POST['first_name'])) {  
```

```php
$errors['first_name'] = 'Required field, no numbers';  
}  
if (!$val->isValid($_POST['surname'])) {  
$errors['surname'] = 'Required field, no numbers';  
}  
} catch (Exception $e) {  
}
```

**2.** The next input field to validate is `username`. A username should consist of letters and numbers only, and should be 6–15 characters long. This requires two tests, so you need to create a `Zend_Validate` object, and chain the validators. You don’t need the existing validator, so you can overwrite it.  
Add the following code immediately after the code you entered in the previous step (and still inside the `try` block):  
```php
$val = new Zend_Validate();  
$length = new Zend_Validate_StringLength(6,15);  
$val->addValidator($length);  
$val->addValidator(new Zend_Validate_Alnum());  
if (!$val->isValid($_POST['username'])) {  
$errors['username'] = 'Use 6-15 letters or numbers only';  
}
```

This starts by creating a generic `Zend_Validate` object ready for chaining. Next, a `StringLength` validator—with a minimum of 6 characters and a maximum of 15—is created and assigned to `$length`.  
In the third line, the `addValidator()` method chains `$length` to `$val`.  
Then the `Alnum` validator is chained to it. By not passing an argument to `Alnum`, no whitespaces are allowed.  
Why use different ways of chaining the validators? Surely the `StringLength` validator could have been passed directly as an argument to `addValidator()` in the same way as `Alnum,` right? It could, but the password field needs to be a minimum of 8 characters. Assigning the `StringLength` validator to its own variable lets you change the minimum value ready for reuse.  
**3.** On the line immediately after the code you just inserted, type **$length->**. As soon as you type the `->` operator, Dreamweaver code hints display the methods available to a `StringLength` validator. Type **s**. The code hints display a number of methods that begin with “set.”  
![Image](img/fig07_15.jpg)  
**4.** Use your arrow keys to scroll down to `setMin($min)` and press Enter/Return or double-click. Set the value to **8**, and type a closing parenthesis and semicolon. The finished line should look like this:  
```php
$length->setMin(8);
```
This resets the minimum number of characters required by the `StringLength` validator to 8. The maximum remains unchanged at 15.  
### ![Image](img/tip.jpg)**TIP:**  
Many ZF classes have methods that begin with “get” and “set” to find out or change the values of an object’s properties.  
**5.** Now that you have changed the minimum required by the `StringLength` validator, you can create the validation test for the `password` input field. It’s almost exactly the same as for `username`. Add this immediately after the line you just entered:  
```php
$val = new Zend_Validate();  
$val->addValidator($length);  
$val->addValidator(new Zend_Validate_Alnum());  
if (!$val->isValid($_POST['password'])) {  
$errors['username'] = 'Use 8-15 letters or numbers only';  
}
```
This allows any combination of letters and numbers. For a more robust password, use the `Regex` validator. There’s a regex for a strong password that requires a mixture of uppercase and lowercase characters and numbers at [`imar.spaanjaars.com/QuickDocId.aspx?quickdoc=297`](http://imar.spaanjaars.com/QuickDocId.aspx?quickdoc=297). In the comments on the same page, there’s an even stronger one that requires at least one special character.  
**6** To check that both password values are identical, use the `Identical` validator. This code goes immediately after the code in the preceding step:  
```php
$val = new Zend_Validate_Identical($_POST['password']);  
if (!$val->isValid($_POST['conf_password'])) {  
$errors['conf_password'] = "Passwords don't match";  
}
```
You want to check that `$_POST['conf_password']` is identical to `$_POST['password']`, so `$_POST['password']` is passed as the argument to the `Identical` validator.  
### ![Image](img/caution.jpg)**CAUTION!**  
The error message contains an apostrophe, so the string needs to be enclosed in double quotation marks.  
**7.** The final test is for the email. Add this after code in the previous step:  
```php
$val = new Zend_Validate_EmailAddress();  
if (!$val->isValid($_POST['email'])) {  
$errors['email'] = 'Use a valid email address';  
}
```
**8.** Save user_registration.php. You’ll come back to it later to add the code that inserts the user’s details in the database. If you want to check your code so far, compare it with lesson07/completed/scripts/user_registration02.php.  
#### Preserving input when validation fails  
Ever submitted an online form only to be told there’s an error, and all your input has been wiped out? Not much fun is it? Good validation and form design preserves the user’s input if there’s an error. It’s quite simple to do. The input is stored in the `$_POST` or `$_GET` array, depending on the method used to submit the form (most of the time, it’s `POST`). All that’s necessary is to assign the appropriate element of the `$_POST` or `$_GET` array to the `value` attribute of the input field.  
**1.** In add_user.php, locate the first `<input>` tag in Code view. It looks like this:  
```html
<input type="text" name="first_name" id="first_name" />
```  
**2.** The `<input>` tag doesn’t have a `value` attribute, so you need to add one, and use PHP to assign its content like this:  
```html
<input type="text" name="first_name" id="first_name"  
value="<?php if ($POST && $errors) {  
  echo htmlentities($_POST['first_name'], ENT_COMPAT, 'UTF-8');  
}?>" />
```
The PHP code block inside the quotation marks of the `value` attribute is controlled by a conditional statement that checks the `$_POST` and `$errors` arrays. The `$_POST` array is empty unless a form has been submitted, so the code inside the curly braces is ignored when the page first loads.  
The `$errors` array is declared at the top of user_registration.php, so it always exists, but elements get added to it only if the validation script finds any problems with the user input. Consequently, `$errors` will equate to `TRUE` only if the form has been submitted and at least one error has been found.  
If both tests equate to `TRUE`, the code passes `$_POST['first_name']` to a function called `htmlentities()` and uses `echo` to display the result. You could use `echo` on its own, but displaying raw user input in a web page is a security risk. The `htmlentities()` function sanitizes the input by converting characters that have a special meaning in HTML into HTML entities. For example, the angle brackets in `<script>` are converted to `&lt;` and `&gt;`, which prevent an unauthorized script from running in your web page.  
Often, `htmlentities()` takes just one argument—the string you want to convert. The second and third arguments have been added because `htmlentities()` uses Latin1 (iso-8859-1) as its default encoding. `ENT_COMPAT` is a constant that specifies preserving single quotation marks and converting only double ones. The third argument specifies UTF-8 (Unicode) as the encoding. This preserves accented or nonalphabetic characters.  
**3.** Save add_user.php, type anything in the “First name” field, and submit the form. The validation script detects errors in the other fields, so `$_POST` and `$errors` are no longer empty arrays. The value you entered is redisplayed.  
You can compare your code with lesson07/completed/add_user02.php.  
#### Dealing with unwanted backslashes  
In add_user.php, test the “First name” field with a name that contains an apostrophe, such as **O’Toole**. If magic quotes (see Lesson 2) are turned on, the apostrophe is preceded by a backslash like this when it’s redisplayed:  
![Image](img/fig07_16.jpg)

If you see a backslash in front of the apostrophe, add the following code after the `catch` block at the bottom of scripts/library.php (you can copy and paste it from lesson07/completed/scripts/library_magic_quotes.php):

```php
```
