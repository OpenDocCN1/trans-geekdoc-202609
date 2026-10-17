
```
1. <?php
2. session_start();
3. require_once('pagetitles.php');
4. $page_title = MR_LOGIN_PAGE;
5. ?>
6. <!DOCTYPE html>
7. <html>
8. <head>
9. <title><?= $page_title ?></title>
10. <link rel="stylesheet"
11. href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/css/bootstrap.min.css"
12. integrity="sha384-9aIt2nRpC12Uk9gS9baDl4lN1QApFmC26EwAOH8WgZLSMYyXFfc+NcPbldKgj7Sk"
13. crossorigin="anonymous">
14. </head>
15. <body>
16. <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
17. integrity="sha384-DfXdzh0tPHlSSs5nCTpuJ/zy4C+OGpamoFVy38MBnE+IbbVYUew+OrCXaRkfj"
18. crossorigin="anonymous"></script>
19. <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js"
20. integrity="sha384-Q6E9RHvbIyZFJfh4iFTs1bLk6Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5Yf5"
21. crossorigin="anonymous"></script>
22. <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.0/js/bootstrap.min.js"
23. integrity="sha384-OgVRvuATP1z7JjHLkuOU7xW704h83LSr+GQ9U9YjZE3Ipu6Tp75j7B7h/k0JKI"
24. crossorigin="anonymous"></script>
25. </body>
26. </html>
```

# 23. 添加用户登录

注意，我调用了 `session_start()`[6] 函数，因为我们将在用户成功登录后为其创建会话变量。还要注意，我为页面标题添加了一个定义，该定义包含在名为 `pagetitles.php` 的脚本中：

```
<!DOCTYPE html>
<?php
session_start();
require_once('pagetitles.php');
$page_title = MR_LOGIN_PAGE;
?>
```

将登录页面的定义添加到 `pagetitles.php` 中：

```
<?php
// Page Titles
define('MR_SIGNUP_PAGE', 'Movie Reservations - Sign Up');
define('MR_LOGIN_PAGE', 'Movie Reservations - Login');
```

现在回到我们的 `login.php` 脚本。在 `<body>` 标签的开头，我们将添加一些描述性文本以及用于用户登录的表单，如清单 23.16 所示。

### 清单 23.16.

```
1. <body>
2. <div class="card">
3.     <div class="card-body">
4.         <h1>Login to Movie Reservations Account</h1>
5.         <hr/>
6.         <form class="needs-validation" novalidate method="POST"
7.             action="<?php $_SERVER['PHP_SELF'] ?>"
8.             <div class="form-group row">
9.                 <label for="user_name" class="col-sm-2 col-form-label-lg">User
10.                 Name</label>
11.                 <div class="col-sm-4">
12.                     <input type="text" class="form-control" id="user_name"
13.                         name="user_name" placeholder="Enter a user name" required>
14.                     <div class="invalid-feedback">
15.                         Please provide a valid user name.
16.                     </div>
17.                 </div>
18.             </div>
19.             <div class="form-group row">
20.                 <label for="password" class="col-sm-2 col-form-label-lg">Password</label>
21.                 <div class="col-sm-4">
22.                     <input type="password" class="form-control" id="password"
23.                         name="password" placeholder="Enter a password" required>
24.                     <div class="invalid-feedback">
25.                         Please provide a valid password.
```

[6] `session_start()`: https://php.net/session_start

### 创建 login.php 脚本

```
</div>
</div>
</div>
<button class="btn btn-primary" type="submit" name="login_submission">Log In</button>
</form>
</div>
</div>
</body>
```

与注册表单一样，我们将为密码和 `user_name` 字段添加 Bootstrap 的验证，这样当用户未在这些表单字段中输入任何数据时，我们会看到图 23.8 所示的效果。

与注册表单一样，我们需要将 JavaScript 函数（清单 23.17）包含在 HTML `<body>` 中的 `<script>` 元素标签内（紧挨着其他 `<script>` 标签之前）：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_363_0.png)

### 清单 23.17.

```
<body>
<div class="card">
<div class="card-body">
<h1>Login to Movie Reservations Account</h1>
<hr/>
<form ...>
...
</form>
</div>
</div>
<script>
// JavaScript for disabling form submissions if there are invalid fields
(function () {
'use strict';
window.addEventListener('load', function () {
// Fetch all the forms we want to apply custom Bootstrap validation styles to
var forms = document.getElementsByClassName('needs-validation');
// Loop over them and prevent submission
var validation = Array.prototype.filter.call(forms, function (form) {
form.addEventListener('submit', function (event) {
if (form.checkValidity() === false) {
event.preventDefault();
event.stopPropagation();
}
form.classList.add('was-validated');
}, false);
});
```

```
27.     });
28.     }, false);
29. })();
30. </script>
31. <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"
32.     integrity="sha384-DfXdzh0tPHlSSs5nCTpuJ/zy4C+OGpamoFvy38MBnE+IbbVYUeW+0rCXaRkfj"
33.     crossorigin="anonymous"></script>
```

当用户提交表单时，我们会验证凭据，然后要么让用户登录，要么重定向到需要修正输入的地方。要成功登录，用户必须存在于 Movie 数据库的 `user` 表中，且密码必须正确。一旦我们在数据库中验证了用户的凭据，我们就通过为该用户的 `user_id` 和 `user_name` 设置会话变量来标记其已通过身份验证。设置会话变量后，我们将用户重定向到 `index.php` 页面。如果用户导航到 `login.php` 脚本，我们会显示其已登录，而不是显示表单。

因此，添加以下条件逻辑，使表单仅在 `user_id` 会话变量为空时显示。然后，将表单移到 `if` 条件内。另外，添加一个 `elseif` 条件，当设置了 `user_name` 会话变量时，显示用户已登录，如清单 23.18 所示。

### 清单 23.18.

```
1. <h1>Login to Movie Reservations Account</h1>
2. <hr/>
3. <?php
4.     if (empty($_SESSION['user_id'])):
5. ?>
6. <form>
7.     <!-- ... -->
8. </form>
9. <?php
10.     elseif (isset($_SESSION['user_name'])):
11.         echo "<h4><p class='text-success'>You are logged in as:
12.             <strong>{$_SESSION['user_name']}</strong>.</p></h4>";
13.     endif;
14. ?>
```

### 登录用户

让我们添加代码以在成功验证其凭据后登录用户。

在 `if (empty($_SESSION['user_id'])):` 之前，添加一个条件来检查 `user_id` 会话变量是否为空且用户已提交表单（清单 23.19）。

### 清单 23.19.

```php
1. <h1>Login to Movie Reservations Account</h1>
2. <hr/>
3. <?php
4. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
5. {
6. }
7. 
8. if (empty($_SESSION['user_id'])):
9. ?>
10. <form ...>
```

在该条件内部（清单 23.20），从 `$_POST` 超全局变量中获取 `user_name` 和 `password` 字段，并添加一个条件来验证用户是否已为字段输入值，否则输出错误提示他们需要正确填写表单：

### 清单 23.20.

```php
1. if (empty($_SESSION['user_id']) && isset($_POST['login_submission']))
2. {
3. // Get user name and password
4. $user_name = $_POST['user_name'];
5. $password = $_POST['password'];
6. 
7. if (!empty($user_name) && !empty($password))
8. {
9. }
10. else
11. {
12. // Output error message
13. echo "<h4><p class='text-danger'>You must enter both a user name
14. and password.</p></h4><hr/>";
15. }
16. }
```

### 创建 login.php 脚本

### 清单 23.23.

```php
if (!empty($user_name) && !empty($password))
{
    // ...
    $results = parameterizedQuery($dbc, $query, 's', $user_name)
        or trigger_error(mysqli_error($dbc), E_USER_ERROR);

    // IF user was found, validate password
    if (mysqli_num_rows($results) == 1)
    {
    }
    else if(mysqli_num_rows($results) == 0) // User does not exist
    {
        echo "<h4><p class='text-danger'>An account does not exist for this username: "
           . "<span class='font-weight-bold'>{$user_name}</span>. "
           . "Please use a different user name.</p></h4><hr/>";
    }
    else
    {
        echo "<h4><p class='text-danger'>Something went terribly wrong!</p></h4><hr/>";
    }
}
```

> 为了减少可能泄露给潜在攻击者的信息，更好的做法是仅表示登录凭据无效，而不明确指出用户名或密码无效。否则，有人可能会建立有效和无效用户名的列表，然后针对有效的用户名尝试破解密码。这也是一个很好的后续练习。

在找到用户凭据的 `if` 条件中，我们需要验证提供的密码是否与存储的密码哈希匹配。如果验证通过，我们可以为用户设置 `user_id`、`user_name` 和 `user_access_privileges` 会话变量。然后，将他们重定向到主页。如果密码哈希验证失败，我们需要输出一条消息，提示输入了错误的密码，并让用户重试。添加清单 23.24 中的代码。

### 清单 23.24.

```php
// IF user was found, validate password
if (mysqli_num_rows($results) == 1)
{
    $row = mysqli_fetch_array($results);

    if (password_verify($password, $row['password_hash']))
    {
        $_SESSION['user_id'] = $row['id'];
        $_SESSION['user_name'] = $row['user_name'];
        $_SESSION['user_access_privileges'] = $row['access_privileges'];

        // Redirect to the home page
        $home_url = dirname($_SERVER['PHP_SELF']);
        header('Location: ' . $home_url);
        exit;
    }
    else
    {
        echo "<h4><p class='text-danger'>An incorrect user name or password was entered.</p></h4><hr/>";
    }
}
else if (mysqli_num_rows($results) == 0) // User does not exist
{
    ...
}
```

### 完整代码清单

清单 23.25 包含 `login.php` 页面的完整清单。

### 清单 23.25.
