

然后你可以执行其他类似的测试，替换一个新的区域设置以获取不同的语言，或者使用另一个适配器来测试不同的数据源。以下是使用 `fr_PR` 区域设置和数据库翻译适配器时输出的示例：

![](img/39390f6d56c5a83b28db083a8bd5185c_327_0.png)

## 另请参阅

-   如需了解有关 Google 翻译 API 的更多信息，请参阅 `https://cloud.google.com/translate/v2/translating-text-with-rest`。
-   如需了解有关 Amazon Mechanical Turk 的更多信息，请参阅 `https://www.mturk.com/mturk/welcome`。如需了解有关 gettext 的更多信息，请参阅 `http://www.gnu.org/software/gettext/manual/gettext.html`。

# 第 9 章：开发中间件

在本章中，我们将涵盖以下主题：

-   使用中间件进行身份验证
-   使用中间件实现访问控制
-   使用缓存提高性能
-   实现路由
-   进行跨框架系统调用
-   使用中间件跨越语言

## 简介

在 IT 行业中，术语往往被发明，然后被使用和滥用。**中间件**（middleware）一词也不例外。可以说，该术语的首次使用源自于 **互联网工程任务组（IETF）**，时间是 2000 年。最初，该术语应用于任何在传输层（即 TCP/IP）和应用层之间运行的软件。近年来，特别是随着 **PHP 标准建议第 7 号（PSR-7）** 的接受，中间件，尤其是在 PHP 世界中，已被应用于 Web 客户端-服务器环境。

![](img/39390f6d56c5a83b28db083a8bd5185c_329_0.png)

本节的食谱将使用在 *附录，定义 PSR-7 类* 中定义的具体类。

## 使用中间件进行身份验证

中间件的一个非常重要用途是提供身份验证。大多数基于 Web 的应用程序需要能够通过用户名和密码验证访客的能力。通过在一个身份验证类中整合 PSR-7 标准，你将使其在各个方面都具有通用的实用性，可以说，它足够安全，可以在任何提供符合 PSR-7 标准的请求和响应对象的框架中使用。

### 如何操作...

1.  我们首先定义一个 `Application\Acl\AuthenticateInterface` 类。我们使用该接口来支持适配器（Adapter）软件设计模式，通过允许使用各种适配器来使我们的 `Authenticate` 类更具通用实用性，每个适配器都可以从不同的来源（例如，从文件、使用 OAuth2 等）获取身份验证。注意使用 PHP 7 定义返回值数据类型的能力：
    ```php
    namespace Application\Acl;

    use Psr\Http\Message\{ RequestInterface, ResponseInterface };
    interface AuthenticateInterface
    {
        public function login(RequestInterface $request) :
            ResponseInterface;
    }
    ```

![](img/39390f6d56c5a83b28db083a8bd5185c_330_0.png)

> 注意，通过定义一个需要符合 PSR-7 标准的请求并产生符合 PSR-7 标准的响应的方法，我们使此接口具有普遍适用性。

2.  接下来，我们定义实现接口所要求的 `login()` 方法的适配器。我们确保使用适当的类，并定义合适的常量和属性。构造函数使用在 *第 5 章，与数据库交互* 中定义的 `Application\Database\Connection`：
    ```php
    namespace Application\Acl;
    use PDO;

    use Application\Database\Connection;
    use Psr\Http\Message\{ RequestInterface, ResponseInterface };
    use Application\MiddleWare\{ Response, TextStream };
    class DbTable implements AuthenticateInterface
    {
        const ERROR_AUTH = 'ERROR: authentication error';
        protected $conn;
        protected $table;
        public function __construct(Connection $conn, $tableName)
        {
            $this->conn = $conn;
            $this->table = $tableName;
        }
    ```

3.  核心 `login()` 方法从请求对象中提取用户名和密码。然后我们执行直接的数据库查找。如果有匹配项，我们将用户信息存储在响应正文中，并进行 JSON 编码：
    ```php
    public function login(RequestInterface $request) :
    ResponseInterface
    {
        $code = 401;
        $info = FALSE;
        $body = new TextStream(self::ERROR_AUTH);
        $params = json_decode($request->getBody()->getContents());
        $response = new Response();
        $username = $params->username ?? FALSE;
        if ($username)
        {
            $sql = 'SELECT * FROM ' . $this->table
            . ' WHERE email = ?';
            $stmt = $this->conn->pdo->prepare($sql);
            $stmt->execute([$username]);
            $row = $stmt->fetch(PDO::FETCH_ASSOC);
            if ($row)
            {
                if (password_verify($params->password,
                $row['password']))
                {
                    unset($row['password']);
                    $body =
                    new TextStream(json_encode($row));
                    $response->withBody($body);
                    $code = 202;
                    $info = $row;
                }
            }
        }
        return $response->withBody($body)->withStatus($code);
    }
    ```

**最佳实践**

切勿以明文形式存储密码。当你需要进行密码匹配时，使用 `password_verify()`，它否定了重新生成密码哈希的需要。

4.  `Authenticate` 类是一个包装器，用于实现 `AuthenticateInterface` 的适配器类。相应地，构造函数接受一个适配器类作为参数，以及一个作为键的字符串，身份验证信息存储在 `$_SESSION` 中：
    ```php
    namespace Application\Acl;
    use Application\MiddleWare\ { Response, TextStream };
    use Psr\Http\Message\ { RequestInterface, ResponseInterface };
    class Authenticate
    {
        const ERROR_AUTH = 'ERROR: invalid token';
        const DEFAULT_KEY = 'auth';
        protected $adapter;
        protected $token;
        public function __construct(
        AuthenticationInterface $adapter, $key)
        {
            $this->key = $key;
            $this->adapter = $adapter;
        }
    ```

5.  此外，我们提供一个带有安全令牌的登录表单，这有助于防止 **跨站点请求伪造（CSRF）** 攻击：
    ```php
    public function getToken()
    {
        $this->token = bin2hex(random_bytes(16));
        $_SESSION['token'] = $this->token;
        return $this->token;
    }
    public function matchToken($token)
    {
        $sessToken = $_SESSION['token'] ?? date('Ymd');
        return ($token == $sessToken);
    }
    public function getLoginForm($action = NULL)
    {
        $action = ($action) ? 'action="' . $action . '" ' : '';
        $output = '<form method="post" ' . $action . '>';
        $output .= '<table><tr><th>Username</th><td>';
        $output .= '<input type="text" name="username" /></td>';
        $output .= '</tr><tr><th>Password</th><td>';
        $output .= '<input type="password" name="password" />';
        $output .= '</td></tr><tr><th>&nbsp;</th>';
        $output .= '<td><input type="submit" /></td>';
        $output .= '</tr></table>';
        $output .= '<input type="token" value="';
        $output .= $this->getToken() . '" />' ;
        $output .= '</form>';
        return $output;
    }
    ```

6.  最后，该类中的 `login()` 方法检查令牌是否有效。如果无效，则返回 400 响应。否则，调用适配器的 `login()` 方法：
    ```php
    public function login(
    RequestInterface $request) : ResponseInterface
    {
        $params = json_decode($request->getBody()->getContents());
        $token = $params->token ?? FALSE;
        if (!( $token && $this->matchToken( $token))) {
            $code = 400;
            $body = new TextStream(self::ERROR_AUTH);
            $response = new Response($code, $body);
        } else {
            $response = $this->adapter->login($request);
        }
        if ($response->getStatusCode() >= 200
        && $response->getStatusCode() < 300) {
            $_SESSION[$this->key] =
            json_decode($response->getBody()->getContents());
        } else {
            $_SESSION[$this->key] = NULL;
        }
        return $response;
    }
    ```

首先，务必遵循 *附录，定义 PSR-7 类* 中定义的食谱。然后，继续定义本食谱中介绍的类，如下表所示：

| 类 | 在这些步骤中讨论 |
| :--- | :--- |
| `Application\Acl\AuthenticateInterface` | 1 |
| `Application\Acl\DbTable` | 2 - 3 |
| `Application\Acl\Authenticate` | 4 - 6 |

然后你可以定义一个名为 `chap_09_middleware_authenticate.php` 的调用程序，它设置自动加载并使用适当的类：

```php
<?php
session_start();
define('DB_CONFIG_FILE', __DIR__ . '../../config/db.config.php');
define('DB_TABLE', 'customer_09');
define('SESSION_KEY', 'auth');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');

use Application\Database\Connection;
use Application\Acl\{ DbTable, Authenticate };
use Application\MiddleWare\{ ServerRequest, Request, Constants,
  TextStream };
```

现在你处于设置身份验证适配器和核心类的位置：

```php
$conn    = new Connection(include DB_CONFIG_FILE);
$dbAuth = new DbTable($conn, DB_TABLE);
$auth    = new Authenticate($dbAuth, SESSION_KEY);
```

务必初始化传入请求，并设置要发送到身份验证类的请求：

```php
$incoming = new ServerRequest();
$incoming->initialize();
$outbound = new Request();
```

检查传入类方法以查看它是否是 `POST`。如果是，则向身份验证类传递一个请求：

```php
if ($incoming->getMethod() == Constants::METHOD_POST) {
  $body = new TextStream(json_encode(
```

