
```
public function getController(string $controllerName): ?object {
```
这表示该函数必须返回一个 `object` 或 `null`，这让我们能够处理上述情况。

现在，在 `EntryPoint` 类中，我们可以检查 `$controller` 变量中是否存在实际的对象。

与其仅仅检查是否存在对象（顺便说一下，`is_object()` 函数可以做到这一点），我们可以检查 `controller` 和 `action` 是否包含可以调用的方法。

内置函数 `is_callable` 用于确定变量是否包含对可调用内容的引用。对于对象，可以指定一个数组。例如：
```
$databaseTable = new DatabaseTable();

//check if $databaseTable->save() is a real function that can be called
var_dump(is_callable([$databaseTable, 'save'])) //true


//check if $databaseTable->otherfunction() is a real function that can be called
var_dump(is_callable([$databaseTable, 'otherfunction'])) //false
```
即使 `$databaseTable` 为 null 或包含的不是函数，这也有效。我们可以利用这一点，在 `controller` 或 `action` 不存在时显示错误：
```
$controller = $this->website->getController($controllerName); 

if (is_callable([$controller, $action])) {
     $page = $controller->$action(...$route);

    $title = $page['title'];

    $variables = $page['variables'] ?? [];
    $output = $this->loadTemplate($page['template'], $variables);
}
else {
    http_response_code(404);
    $title = 'Not found';
    $output = 'Sorry, the page you are looking for could not be found.';
}
```
如果 `$controller` 为 null 或 `$action` 设置为不存在的方法，`else` 块将被触发，页面将显示错误。我还设置了 `404`（未找到）响应代码，这样浏览器就不会将页面存储在历史记录中，搜索引擎也不会索引该页面。

完整的 `EntryPoint` 类现在看起来像这样：
```
class EntryPoint {
    public function __construct(private \Ninja\Website $website) {
    }

     public function run(string $uri, string $method) {
        try {
            $this->checkUri($uri, $method);

            if ($uri == '') {
                $uri = $this->website->getDefaultRoute();
            }

            $route = explode('/', $uri);

            $controllerName = array_shift($route);
            $action = array_shift($route);

            if ($method === 'POST') {
                $action .= 'Submit';
            }

            $controller = $this->website->getController($controllerName); 

            if (is_callable([$controller, $action])) {
                 $page = $controller->$action(...$route);

                $title = $page['title'];

                $variables = $page['variables'] ?? [];
                $output = $this->loadTemplate($page['template'], $variables);
            }
            else {
                http_response_code(404);
                $title = 'Not found';
                $output = 'Sorry, the page you are looking for could not be found.';
            }

        } catch (\PDOException $e) {
            $title = 'An error has occurred';

            $output = 'Database error: ' . $e->getMessage() . ' in ' .
            $e->getFile() . ':' . $e->getLine();
        }

        include  __DIR__ . '/../templates/layout.html.php';
    }

    private function loadTemplate($templateFileName, $variables) {
        extract($variables);

        ob_start();
        include  __DIR__ . '/../templates/' . $templateFileName;

        return ob_get_clean();
    }

    private function checkUri($uri) {
        if ($uri != strtolower($uri)) {
            http_response_code(301);
            header('location: ' . strtolower($uri));
        }
    }
}
```
**示例：[CMS-EntryPoint-错误处理](https://github.com/spbooks/phpmysql7/tree/CMS-EntryPoint-ErrorHandling)**

## 你自己的框架

为 PHP 开发者编写框架是一项必经之路。每个人都会这么做，而我们刚刚写了一个！通过本书，我希望能帮助你避免开发者常会陷入的一些常见陷阱。

在本章中你学习了：
*   框架代码与项目特定代码之间的区别
*   如何通过目录结构和命名空间区分这两种代码
*   如何编写自动加载器
*   接口和 REST 的基础知识
*   如何创建用户友好的 URL 以及如何将它们映射到控制器操作

虽然本章没有添加任何 *功能*，但这里涵盖的知识将使你在处理现代 PHP 应用和同行开发者的第三方代码时拥有非常坚实的基础。

# 第 10 章：允许用户注册账户

既然我们已经完成了构建可扩展框架的所有艰苦工作，现在是时候为网站添加一些新功能了。我们将使其用户能够在网站上注册账户，以便他们自己发布笑话。

你应该已经在数据库中拥有 `authors` 表，并通过 MySQL Workbench 添加了一些数据。如果没有，你可以执行以下查询来创建表：
```
CREATE TABLE author (
  id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(50),
  email VARCHAR(100),
  password VARCHAR(255)
) DEFAULT CHARACTER SET utf8mb4 ENGINE=InnoDB
```
如果没有记录，不用担心添加。我们将创建一个表单，让我们能够从网站添加作者。

你可能会注意到 `password` 列的类型是 `VARCHAR(255)`。我知道 255 个字符听起来像是一个非常长的密码，但将列设得这么大是有原因的，我们稍后会提到。

首先需要的是控制器代码。让我们在 `Ijdb\Controllers` 目录中创建一个 `Author.php` 文件，然后创建具有以下变量、构造函数以及用于加载注册表单的方法的类。对于用户注册，唯一需要的依赖是代表 `authors` 表的 `DatabaseTable` 对象：
```
<?php
namespace Ijdb\Controllers;

use \Ninja\DatabaseTable;

class Author {
    public function __construct(private DatabaseTable $authorsTable) {
    }

    public function registrationForm() {
        return [
          'template' => 'register.html.php',
            'title' => 'Register an account'
         ];
    }

    public function success() {
        return ['template' => 'registersuccess.html.php',
            'title' => 'Registration Successful'];
    }
}
```
我添加了两个操作：一个用于显示表单，一个用于显示 *注册成功* 页面。

以下是 `templates` 目录中的 `register.html.php` 模板：
```
<form action="" method="post">
  <label for="email">Your email address</label>
  <input name="author[email]" id="email" type="text">

  <label for="name">Your name</label>
  <input name="author[name]" id="name" type="text">

  <label for="password">Password</label>
  <input name="author[password]" id="password" type="password">

  <input type="submit" name="submit" value="Register account">
</form>
```
以下是 `registersuccess.html.php`：
```
<h2>Registration Successful</h2>

<p>You are now registered on the Internet Joke Database</p>
```
如果我们访问 `https://v.je/author/registrationForm`，我们应该能看到表单。为了使表单工作，我们需要添加 `registrationFormSubmit` 方法来处理 `POST` 请求。`Author.php` 如下所示。

**示例：[注册表单](https://github.com/spbooks/phpmysql7/tree/Registration-Form)**
```
public function registrationFormSubmit() {
  $author = $_POST['author'];

  $this->authorsTable->save($author);

  header('Location: /author/success');
}
```
一旦表单被提交，`EntryPoint` 将自动在方法末尾追加 `Submit` 并调用 `registrationFormSubmit` 方法。
