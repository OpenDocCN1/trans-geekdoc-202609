
#### 第 48.2 节：输出

以使用 UTF-8。唯一可靠的方法是像这样添加 `>` 标签：

![](img/Image01113.jpg)

| php | | . | ini | ，或手动发送 | Content | \- | Type |
| --- | --- | --- | --- | --- | --- | --- | --- |

![](img/Image01114.jpg)如果你的应用程序向其他系统传输文本，它们也需要知道字符编码。在 PHP 中，你可以在 `php.ini` 中使用 `default_charset` 选项，或手动发送 MIME 头部。这是针对现代浏览器时的首选方法。

[HTML 元数据](http://stackoverflow.com/q/4696499/4245525) 。

![](img/Image01115.jpg)

![](img/Image01116.jpg)

#### 第 48.3 节：数据存储与访问

![](img/Image01117.jpg)本主题专门讨论 UTF-8 以及将其与数据库一起使用时的注意事项。如果你想了解更多关于在 PHP 中使用数据库的信息，请查看该主题。

在 MySQL 数据库中存储数据：

![](img/Image01118.jpg)在数据库的所有表和文本列上指定 `utf8mb4` 字符集。这使得 MySQL 以 UTF-8 原生编码物理存储和检索值。

| utf8mb4_ |
| --- |

![](img/Image01119.jpg)如果指定了 `*` 排序规则（不带任何显式字符集），MySQL 将隐式使用 `utf8mb4` 编码。

旧版本的 MySQL (< 5.5.3) 不支持 `utf8mb4`，因此你将被迫使用 `utf8`，它仅支持 Unicode 字符的一个子集。

在 MySQL 数据库中访问数据：

![](img/Image01120.jpg)在你的应用程序代码中（例如 PHP），无论你使用哪种数据库访问方法，都需要将连接字符集设置为 `utf8mb4`。这样，当 MySQL 将数据传递给你的应用程序时（反之亦然），不会从其原生 UTF-8 进行转换。

![](img/Image01121.jpg)某些驱动程序提供自己的机制来配置连接字符集，这既更新了其自身的内部状态，又通知 MySQL 连接上将使用的编码。这通常是首选方法。

例如（关于 `utf8mb4` / `utf8` 的相同考虑如上所述）：

如果你使用 [PDO](http://www.php.net/manual/en/book.pdo.php) 抽象层且 PHP ≥ 5.3.6，你可以在 [DSN](http://www.php.net/manual/en/ref.pdo-mysql.connection.php) 中指定字符集：

| [set_charset](http://www.php.net/manual/en/mysqli.set-charset.php) |
| --- |

```
$handle = new PDO('mysql:charset=utf8mb4');
```

如果你使用 [mysqli](http://www.php.net/manual/en/book.mysqli.php) ，可以调用 `mysqli_set_charset()` ：

```
$conn = mysqli_connect('localhost', 'my_user', 'my_password', 'my_db');
$conn->set_charset('utf8mb4');     // 面向对象风格
mysqli_set_charset($conn, 'utf8mb4'); // 过程化风格
```

![](img/Image01122.jpg)

如果你不得不使用旧版 [mysql](http://www.php.net/manual/en/book.mysql.php) 但碰巧运行 PHP ≥ 5.2.3，你可以调用 `mysql_set_charset()` 。

```
$conn = mysql_connect('localhost', 'my_user', 'my_password');
$conn->set_charset('utf8mb4');     // 面向对象风格
mysql_set_charset($conn, 'utf8mb4'); // 过程化风格
```

| [SET NAMES](http://dev.mysql.com/doc/en/charset-connection.html) ['utf8mb4'](http://dev.mysql.com/doc/en/charset-connection.html) |
| --- |

如果数据库驱动程序没有提供自己的机制来设置连接字符集，你可能不得不发出一个查询来告诉 MySQL 你的应用程序期望连接上的数据如何编码： .

## 第 49 章：PHP 中的 Unicode 支持

#### 第 49.1 节：使用 PHP 将 Unicode 字符转换为 “\uxxxx” 格式

你可以使用以下代码进行双向转换。

![](img/Image01123.jpg)

用法：

![](img/Image01124.jpg)

输出：

![](img/Image01125.jpg)

#### 第 49.2 节：使用 PHP 将 Unicode 字符转换为其数值和/或 HTML 实体

你可以使用以下代码进行双向转换。

![](img/Image01126.jpg)

![](img/Image01127.jpg)

用法：

![](img/Image01128.jpg)

输出：

![](img/Image01129.jpg)

![](img/Image01130.jpg)

#### 第 49.3 节：用于 Unicode 支持的 Intl 扩展

原生字符串函数映射到单字节函数，它们不能很好地处理 Unicode。`iconv` 和 `mbstring` 扩展为 Unicode 提供了一些支持，而 `Intl` 扩展提供完整支持。`Intl` 是事实标准 ICU 库的封装，详细信息请参阅 [`site.icu-project.org`](http://site.icu-project.org/) ，这些信息在 [`php.net/manual/en/book.intl.php`](http://php.net/manual/en/book.intl.php) 上不可用。如果你无法安装该扩展，请查看 [Symfony 框架提供的 Intl 替代实现](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) [an alternative](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) [implementation of Intl from the Symfony framework](http://api.symfony.com/3.2/Symfony/Component/Intl/Intl.html) 。

ICU 提供完整的国际化支持，Unicode 只是其中较小的一部分。你可以轻松进行转码：

![](img/Image01131.jpg)

```
\UConverter::transcode($sString, 'UTF-8', 'UTF-8');  // 针对攻击剥离坏字节
```

但是，不要轻易放弃 `iconv`，请考虑：

![](img/Image01132.jpg)

## 第 50 章：URL

#### 第 50.1 节：解析 URL

| [parse_url](http://php.net/parse_url) |
| --- |

要将 URL 分离为各个组成部分，请使用 `parse_url()` ：

![](img/Image01133.jpg)

执行上述代码后，`$parts` 的内容将为：

![](img/Image01134.jpg)

你也可以选择性地仅返回 URL 的一个组件。仅返回查询字符串：

![](img/Image01135.jpg)

接受以下任意常量：`PHP_URL_SCHEME` 、`PHP_URL_HOST` 、`PHP_URL_PORT` 、`PHP_URL_USER` 、`PHP_URL_PASS` 、`PHP_URL_PATH` 、`PHP_URL_QUERY` 和 `PHP_URL_FRAGMENT` 。

| [parse_str](http://php.net/parse_str) |
| --- |

要进一步将查询字符串解析为键值对，请使用 `parse_str()` ：

![](img/Image01136.jpg)

执行上述代码后，`$params` 数组将填充以下内容：

![](img/Image01137.jpg)

#### 第 50.2 节：从数组构建 URL 编码的查询字符串

| [http_build_query](http://php.net/manual/function.http-build-query.php) |
| --- |

`http_build_query()` 将从数组或对象创建查询字符串。这些字符串可以附加到 URL 以创建 GET 请求，或用于 POST 请求（例如配合 cURL）。

![](img/Image01138.jpg)

`$queryString` 将具有以下值：

![](img/Image01139.jpg)

![](img/Image01140.jpg)

![](img/Image01141.jpg)

这是以下内容的 URL 编码版本：

![](img/Image01142.jpg)

#### 第 50.3 节：重定向到另一个 URL

| header |
| --- |

## 第 51 章：如何拆解 URL

在编写 PHP 代码时，你很可能会遇到需要将 URL 拆分为若干部分的情况。显然，根据你的需求，有不止一种方法可以实现。本文将为你解释这些方法，以便你找到最适合你的方案。

#### 第 51.1 节：使用 `parse_url()`

你可以使用 `header()` 函数指示浏览器重定向到不同的 URL：

```
header("Location: http://www.example.com/"); /* 重定向浏览器 */
exit;
```

你也可以重定向到相对 URL（这不属于官方 HTTP 规范的一部分，但在所有浏览器中均可工作）：

```
header("Location: /path/to/page.php"); /* 重定向浏览器 */
exit;
```

如果头部信息已发送，你可以选择发送一个 meta refresh HTML 标签。

> **警告**：meta refresh 标签依赖于客户端正确处理 HTML，但某些客户端不会这样做。通常，它仅在 Web 浏览器中有效。此外，请考虑到如果头部信息已发送，你可能存在一个 Bug，这应该触发一个异常。

你也可以为用户打印一个可点击的链接，以供忽略 meta refresh 标签的客户端使用：

```php
$saveUrl = htmlspecialchars($url); // 防止浏览器将 url 视为 HTML
// 告诉浏览器在 0 秒后将页面重定向到 $saveUrl
print '<meta http-equiv="refresh" content="0; url=' . $saveUrl . '">' ;
// 为用户显示链接
print '<p>Please continue to <a href="' . $saveUrl . '">' . $saveUrl . '</a></p>' ;
exit;
```

如果你需要分离路径，可以使用 `explode()`：

```php
$url = 'http://username:password@hostname:9090/path/to/resource?arg=value#anchor';
$parts = parse_url($url);
print_r($parts);
```

如果你需要路径的最后一部分，可以像这样使用 `end()`：

```php
$path = $parts['path']; // /path/to/resource
$segments = explode('/', $path);
$lastSegment = end($segments); // resource
```

如果 URL 包含 GET 变量，你也可以检索它们：

```php
$query = $parts['query']; // arg=value
parse_str($query, $vars);
print_r($vars); // Array ( [arg] => value )
```

如果你想拆解查询变量，可以像这样使用 `parse_str()`：

```php
$str = "first=value&arr[]=foo+bar&arr[]=baz";
parse_str($str, $output);
print_r($output);
```

#### 第 51.2 节：使用 `explode()`

`explode()`：返回一个字符串数组，每个元素是由 string delimiter 分隔形成的字符串的子串。

此函数非常直观。

```php
$url = "http://www.example.com/path/to/page.php";
$parts = explode('/', $url);
print_r($parts);
```

你可以通过以下方式获取 URL 的最后一部分：

```php
$lastPart = end($parts); // page.php
```

你也可以结合 `sizeof()` 和数学运算符在数组中导航，如下所示：

```php
$secondToLast = $parts[sizeof($parts) - 2]; // to
```

#### 第 51.3 节：使用 `basename()`

`basename()`：给定一个包含文件或目录路径的字符串，此函数将返回路径中的文件名部分。

此函数将仅返回 URL 的最后一部分：

```php
$url = "http://www.example.com/path/to/page.php";
$file = basename($url); // page.php
```

```php
$url = "http://www.example.com/path/to/page.php?arg=value";
$file = basename($url); // page.php?arg=value
```

如果你的 URL 包含更多内容，而你需要的是包含文件的目录名，可以结合 `dirname()` 这样使用：

```php
$url = "http://www.example.com/path/to/page.php";
$dir = dirname($url); // http://www.example.com/path/to
```

## 第 52 章：对象序列化

#### 第 52.1 节：Serialize / Unserialize

| 函数 | 说明 |
| --- | --- |
| `serialize()` | 返回一个字符串，包含了可以在 PHP 中存储的任意值的字节流表示。 |
| `unserialize()` | 可以使用该字符串重新创建原始的变量值。 |

序列化一个对象：

```php
$serialized = serialize($object);
```

反序列化一个对象：

```php
$object = unserialize($serialized);
```

示例：

```php
class A {
    public $var = 'value';
}
$obj = new A();
$serialized = serialize($obj);
echo $serialized; // O:1:"A":1:{s:3:"var";s:5:"value";}
$unserialized = unserialize($serialized);
var_dump($unserialized);
```

#### 第 52.2 节：`Serializable` 接口

##### 简介

| 方法 | 说明 |
| --- | --- |
| `__sleep()` | |
| `__wakeup()` | |
| `__destruct()` | |
| `unserialize()` | |
| `__construct()` | |

实现此接口的类将不再支持 `__sleep()` 和 `__wakeup()`。每当一个实例需要被序列化时，`serialize()` 方法会被调用。除非在方法内部编程，否则这不会调用 `__sleep()` 或产生任何其他副作用。当数据被反序列化时，类是已知的，并且会调用适当的 `unserialize()` 方法作为构造函数，而不是调用 `__construct()`。如果你需要执行标准构造函数，可以在该方法中进行。

基本用法：

```php
class MyClass implements Serializable {
    private $data;

    public function __construct($data) {
        $this->data = $data;
    }

    public function serialize() {
        return serialize($this->data);
    }

    public function unserialize($data) {
        $this->data = unserialize($data);
    }
}
```
