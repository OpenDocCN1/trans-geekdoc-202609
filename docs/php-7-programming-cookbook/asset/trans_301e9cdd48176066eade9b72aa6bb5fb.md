

以下是预期结果：

![](img/39390f6d56c5a83b28db083a8bd5185c_577_0.png)

接下来，从 /path/to/source/for/this/chapter 创建一个名为 uploads 的目录。请继续定义另一个调用程序 `chap_09_middleware_value_objects_file_upload.php`，该程序设置自动加载并使用相应的类：

```php
<?php
define('TARGET_DIR', __DIR__ . '/uploads');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\MiddleWare\UploadedFile;
```

在 try...catch 块中，检查是否有任何文件被上传。如果有，循环遍历 $_FILES，并在 tmp_name 已设置的情况下创建 UploadedFile 实例。然后可以使用 moveTo() 方法将文件移动到 TARGET_DIR：

```php
try {
    $message = '';
    $uploadedFiles = array();
    if (isset($_FILES)) {
        foreach ($_FILES as $key => $info) {
            if ($info['tmp_name']) {
                $uploadedFiles[$key] = new UploadedFile(
                    $key, $info, TRUE);
                $uploadedFiles[$key]->moveTo(TARGET_DIR);
            }
        }
    }
} catch (Throwable $e) {
    $message = $e->getMessage();
}
?>
```

在视图逻辑中，显示一个简单的文件上传表单。您也可以使用 phpinfo() 来显示关于已上传内容的信息：

```html
<form name="search" method="post"
    enctype="<?= Constants::CONTENT_TYPE_MULTI_FORM ?>">
    <table class="display" cellspacing="0" width="100%">
        <tr><th>Upload 1</th><td><input type="file" name="upload_1" /></td></tr>
        <tr><th>Upload 2</th><td><input type="file" name="upload_2" /></td></tr>
        <tr><th>Upload 3</th><td><input type="file" name="upload_3" /></td></tr>
        <tr><th>&nbsp;</th><td><input type="submit" /></td></tr>
    </table>
</form>
<?= ($message) ? '<h1>' . $message . '</h1>' : ''; ?>
```

接下来，如果有任何已上传的文件，您可以显示每个文件的信息。您还可以使用 getStream() 后跟 getContents() 来显示每个文件（假设您正在使用短文本文件）：

```html
<?php if ($uploadedFiles) : ?>
    <table class="display" cellspacing="0" width="100%">
        <tr>
            <th>Filename</th><th>Size</th>
            <th>Moved Filename</th><th>Text</th>
        </tr>
        <?php foreach ($uploadedFiles as $obj) : ?>
            <?php if ($obj->getMovedName()) : ?>
            <tr>
                <td><?= htmlspecialchars($obj->getClientFilename()) ?></td>
                <td><?= $obj->getSize() ?></td>
                <td><?= $obj->getMovedName() ?></td>
                <td><?= $obj->getStream()->getContents() ?></td>
            </tr>
            <?php endif; ?>
        <?php endforeach; ?>
    </table>
<?php endif; ?>
<?php phpinfo(INFO_VARIABLES); ?>
```

输出可能如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_579_0.png)

## 另请参阅

- 有关 PSR 的更多信息，请查看 [PHP 标准推荐](https://en.wikipedia.org/wiki/PHP_Standard_Recommendation)
- 关于 PSR-7 的具体信息，这里是官方描述： [http://www.php-fig.org/psr/psr-7/](http://www.php-fig.org/psr/psr-7/)
- 有关 PHP 流的信息，请查看 [http://php.net/manual/en/book.stream.php](http://php.net/manual/en/book.stream.php)

## 开发 PSR-7 Request 类

PSR-7 中间件的一个关键特征是使用了 **Request** 和 **Response** 类。应用后，这使得不同的软件块能够协同工作，而它们之间不需要共享任何特定知识。在此上下文中，请求类应包含原始用户请求的所有方面，包括浏览器设置、请求的原始 URL、传递的参数等。

### 如何实现…

1.  首先，确保定义表示 `Uri`、`Stream` 和 `UploadedFile` 值对象的类，如前面的食谱中所述。
2.  现在我们可以定义核心 `Application\MiddleWare\Message` 类。该类使用 `Stream` 和 `Uri` 并实现 `Psr\Http\Message\MessageInterface`。我们首先定义关键值对象的属性，包括表示消息主体（即 `StreamInterface` 实例）、版本和 HTTP 头的属性：

```php
namespace Application\MiddleWare;
use Psr\Http\Message\ {
    MessageInterface,
    StreamInterface,
    UriInterface
};
class Message implements MessageInterface
{
    protected $body;
    protected $version;
    protected $httpHeaders = array();
```

3.  接下来，我们有表示 `StreamInterface` 实例的 `getBody()` 方法。一个配套方法 `withBody()` 返回当前的 `Message` 实例，并允许我们覆盖 `body` 的当前值：

```php
public function getBody()
{
    if (!$this->body) {
        $this->body = new Stream(self::DEFAULT_BODY_STREAM);
    }
    return $this->body;
}
public function withBody(StreamInterface $body)
{
    if (!$body->isReadable()) {
        throw new InvalidArgumentException(
            self::ERROR_BODY_UNREADABLE);
    }
    $this->body = $body;
    return $this;
}
```

4.  PSR-7 建议将头视为不区分大小写。因此，我们定义了一个 findHeader() 方法（未被 MessageInterface 直接定义），该方法使用 stripos() 定位头：

```php
protected function findHeader($name)
{
    $found = FALSE;
    foreach (array_keys($this->getHeaders()) as $header) {
        if (stripos($header, $name) !== FALSE) {
            $found = $header;
            break;
        }
    }
    return $found;
}
```

5.  下一个方法，未在 PSR-7 中定义，旨在填充 $httpHeaders 属性。该属性假设是一个关联数组，其中键是头，值是表示头值的字符串。如果有多个值，则以逗号分隔的附加值会被追加到字符串中。Apache 扩展有一个出色的 apache_request_headers() PHP 函数，如果在 $httpHeaders 中尚未提供头，则会产生这些头：

```php
protected function getHttpHeaders()
{
    if (!$this->httpHeaders) {
        if (function_exists('apache_request_headers')) {
            $this->httpHeaders = apache_request_headers();
        } else {
            $this->httpHeaders = $this->altApacheReqHeaders();
        }
    }
    return $this->httpHeaders;
}
```

6.  如果 apache_request_headers() 不可用（即未启用 Apache 扩展），我们提供了一个替代方案 altApacheReqHeaders()：

```php
protected function altApacheReqHeaders()
{
    $headers = array();
    foreach ($_SERVER as $key => $value) {
        if (stripos($key, 'HTTP_') !== FALSE) {
            $headerKey = str_replace('HTTP_', '', $key);
            $headers[$this->explodeHeader($headerKey)] = $value;
        }
```

## 定义 PSR-7 类

```php
            } elseif (stripos($key, 'CONTENT_') !== FALSE) {
                $headers[$this->explodeHeader($key)] = $value;
            }
        }
        return $headers;
    }
    protected function explodeHeader($header)
    {
        $headerParts = explode('-', $header);
        $headerKey = ucwords(implode(' ', strtolower($headerParts)));
        return str_replace(' ', '-', $headerKey);
    }
```

7.  实现 getHeaders()（PSR-7 中要求）现在只是一个遍历 getHttpHeaders() 方法（在第 4 步中讨论）生成的 $httpHeaders 属性的简单循环：

```php
    public function getHeaders()
    {
        foreach ($this->getHttpHeaders() as $key => $value) {
            header($key . ': ' . $value);
        }
    }
```

8.  同样，我们提供了一系列 with 方法，旨在覆盖或替换头。由于可能有多个头，我们还提供一个方法向现有头集合中添加头。withoutHeader() 方法用于移除某个头实例。注意在前一步骤中提到的 findHeader() 的一致使用，以允许对头进行不区分大小写的处理：

```php
    public function withHeader($name, $value)
    {
        $found = $this->findHeader($name);
        if ($found) {
            $this->httpHeaders[$found] = $value;
        } else {
            $this->httpHeaders[$name] = $value;
        }
        return $this;
    }

    public function withAddedHeader($name, $value)
    {
        $found = $this->findHeader($name);
        if ($found) {
```

