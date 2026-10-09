
# 工作原理...

将本菜谱中讨论的所有代码放入 `Application\Security` 目录下的 `SessOptions.php` 文件中。然后，你可以定义一个名为 `chap_13_session_options.php` 的调用程序来测试这个新类，该程序设置了自动加载并使用该类：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../..');
use Application\Security\SessOptions;
```

接下来，定义一个数组，使用类的常量作为键，并根据需要设置值以管理会话。请注意，在本文中所示的示例中，会话信息存储在一个名为 session 的子目录中，你需要创建该目录：

```php
$options = [
    SessOptions::SESS_OP_USE_ONLY_COOKIES => 1,
    SessOptions::SESS_OP_COOKIE_LIFETIME => 300,
    SessOptions::SESS_OP_COOKIE_HTTPONLY => 1,
    SessOptions::SESS_OP_NAME => 'UNLIKELYSOURCE',
    SessOptions::SESS_OP_SAVE_PATH => __DIR__ . '/session'
];
```

现在，你可以创建 `SessOptions` 实例并运行 `start()` 方法来启动会话。你可以在这里使用 `phpinfo()` 来显示有关会话的一些信息：

```php
$sessOpt = new SessOptions($options);
$sessOpt->start();
$_SESSION['test'] = 'TEST';
phpinfo(INFO_VARIABLES);
```

如果你使用浏览器开发人员工具查找有关 Cookie 的信息，你会注意到名称设置为 `UNLIKELYSOURCE`，并且过期时间是从现在开始 5 分钟：

![](img/39390f6d56c5a83b28db083a8bd5185c_556_0.png)

如果你扫描会话目录，你会发现会话信息已存储在那里：

```bash
ed@ed: ~/Desktop/Repos/php7_recipes/source/chapter13
edged:~/Desktop/Repos/php7_recipes/source/chapter13$ ls -l session
total 4
-rw-r--r-- 1 ed ed 16 Jun 17 11:03 sess_789876c4d795aa8a8882ffdf09cda9576
edged:~/Desktop/Repos/php7_recipes/source/chapter13$
```

# 另请参阅...

- 有关与会话相关的 php.ini 指令的更多信息，请参见此摘要：http://php.net/manual/en/session.configuration.php

# 定义 PSR-7 类

在本附录中，我们将涵盖以下主题：

- 实现 PSR-7 值对象类
- 开发 PSR-7 Request 类
- 定义 PSR-7 Response 类

## 简介

**PHP 标准推荐编号 7（PSR-7）** 定义了许多接口，但没有提供实际的实现。因此，我们需要定义具体的代码实现，才能开始创建自定义中间件。

## 实现 PSR-7 值对象类

为了使用 PSR-7 请求和响应，我们首先需要定义一系列值对象。这些是代表逻辑对象的类，用于基于 Web 的活动，例如 URL、文件上传以及流式请求或响应主体。

### 准备工作

PSR-7 接口的源代码可以作为 `Composer` 包获取。使用 `Composer` 管理外部软件（包括 PSR-7 接口）被认为是一种最佳实践。

### 具体操作方法...

1. 首先，请访问以下 URL 以获取 PSR-7 接口定义的最新版本：`https://github.com/php-fig/http-message`。也可以获取源代码。在撰写本文时，以下是可用的定义：

| 接口 | 继承自 | 说明 | 方法处理的内容 |
| :--- | :--- | :--- | :--- |
| MessageInterface | | 定义了 HTTP 消息通用的方法 | 标头、消息主体（即内容）和协议 |
| RequestInterface | MessageInterface | 表示客户端生成的请求 | URI、HTTP 方法和请求目标 |

2. 不幸的是，我们需要创建实现这些接口的具体类，才能利用 PSR-7。幸运的是，接口类通过一系列注释在内部得到了广泛的文档记录。我们将从一个包含有用常量的独立类开始：

> 请注意，我们利用 PHP 7 引入的一个新特性，允许将常量定义为数组。

```php
namespace Application\MiddleWare;
class Constants
{
    const HEADER_HOST = 'Host'; // 主机标头
    const HEADER_CONTENT_TYPE = 'Content-Type';
    const HEADER_CONTENT_LENGTH = 'Content-Length';

    const METHOD_GET = 'get';
    const METHOD_POST = 'post';
    const METHOD_PUT = 'put';
    const METHOD_DELETE = 'delete';
    const HTTP_METHODS = ['get', 'put', 'post', 'delete'];

    const STANDARD_PORTS = [
        'ftp' => 21, 'ssh' => 22, 'http' => 80, 'https' => 443
    ];

    const CONTENT_TYPE_FORM_ENCODED =
        'application/x-www-form-urlencoded';
    const CONTENT_TYPE_MULTI_FORM = 'multipart/form-data';
    const CONTENT_TYPE_JSON = 'application/json';
    const CONTENT_TYPE_HAL_JSON = 'application/hal+json';

    const DEFAULT_STATUS_CODE = 200;
    const DEFAULT_BODY_STREAM = 'php://input';
    const DEFAULT_REQUEST_TARGET = '/';

    const MODE_READ = 'r';
    const MODE_WRITE = 'w';

    // 注意：为了节省空间，并非所有错误常量都显示在此处
    const ERROR_BAD = 'ERROR: ';
    const ERROR_UNKNOWN = 'ERROR: unknown';

    // 注意：并非在此处显示所有的状态代码！
    const STATUS_CODES = [
        200 => 'OK',
        301 => 'Moved Permanently',
        302 => 'Found',
        401 => 'Unauthorized',
        404 => 'Not Found',
        405 => 'Method Not Allowed',
        418 => "I'm A Teapot",
        500 => 'Internal Server Error',
    ];
}
```

> 完整的 HTTP 状态代码列表可以在这里找到：https://tools.ietf.org/html/rfc7231#section-6.1.

3. 接下来，我们将着手处理代表由其他 PSR-7 类使用的值对象的类。首先，这里是一个代表 URI 的类。在构造函数中，我们接受一个 URI 字符串作为参数，并使用 parse_url() 函数将其分解为其组成部分：

```php
namespace Application\MiddleWare;
use InvalidArgumentException;
use Psr\Http\Message\UriInterface;
class Uri implements UriInterface
{
    protected $uriString;
    protected $uriParts = array();

    public function __construct($uriString)
    {
        $this->uriParts = parse_url($uriString);
        if (!$this->uriParts) {
            throw new InvalidArgumentException(
                Constants::ERROR_INVALID_URI);
        }
        $this->uriString = $uriString;
    }
}
```

> **URI** 代表 **统一资源标识符**。这就是你在发起请求时会在浏览器顶部看到的内容。有关 URL 组成的更多信息，请参阅 http://tools.ietf.org/html/rfc3986。

4. 在构造函数之后，我们定义方法来访问 URI 的组成部分。**scheme**（方案）代表 PHP 封装器（即 HTTP、FTP 等）：

```php
public function getScheme()
{
    return strtolower($this->uriParts['scheme']) ?? '';
}
```

5. **authority**（权威）代表用户名（如果存在）、主机，以及可选的端口号：

```php
public function getAuthority()
{
    $val = '';
    if (!empty($this->getUserInfo()))
        $val .= $this->getUserInfo() . '@';
    $val .= $this->uriParts['host'] ?? '';
    if (!empty($this->uriParts['port']))
        $val .= ':' . $this->uriParts['port'];
    return $val;
}
```

6. **User info**（用户信息）代表用户名（如果存在）以及可选的密码。使用密码的一个例子是访问 FTP 网站，例如 ftp://username:password@website.com:/path：

```php
public function getUserInfo()
{
    if (empty($this->uriParts['user'])) {
        return '';
    }

    $val = $this->uriParts['user'];
    if (!empty($this->uriParts['pass']))
        $val .= ':' . $this->uriParts['pass'];

    return $val;
}
```

7. **Host**（主机）是包含在 URI 中的 DNS 地址：

```php
public function getHost()
{
    if (empty($this->uriParts['host'])) {
        return '';
    }

    return strtolower($this->uriParts['host']);
}
```

8. **Port**（端口）是 HTTP 端口（如果存在）。你会注意到，如果端口列在我们的 STANDARD_PORTS 常量中，根据 PSR-7 的要求，返回值将是 NULL：

```php
public function getPort()
{
    if (empty($this->uriParts['port'])) {
        return NULL;
    } else {
        if ($this->getScheme()) {
            if ($this->uriParts['port'] ==
                Constants::STANDARD_PORTS[$this->getScheme()]) {
                return NULL;
            }
        }

        return (int) $this->uriParts['port'];
    }
}
```

