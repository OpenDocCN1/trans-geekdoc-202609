

# 定义 PSR-7 类

我们还需要定义一些信息性方法，以获取关于流的信息：

```php
public function getMetadata($key = null)
{
    if ($key) {
        return $this->metadata[$key] ?? NULL;
    } else {
        return $this->metadata;
    }
}

public function getSize()
{
    return $this->info->getSize();
}

public function isSeekable()
{
    return boolval($this->metadata['seekable']);
}

public function isWritable()
{
    return $this->stream->isWritable();
}

public function isReadable()
{
    return $this->info->isReadable();
}
```

遵循 PSR-7 指南，我们随后定义 `getContents()` 和 `__toString()` 方法，以便转储流的内容：

```php
public function __toString()
{
    $this->rewind();
    return $this->getContents();
}

public function getContents()
{
    ob_start();
    if (!fpassthru($this->stream)) {
        throw new RuntimeException(
            self::ERROR_BAD . __METHOD__
        );
    }
    return ob_get_clean();
}
```

前文所示的 Stream 类的一个重要变体是 TextStream，它专门针对主体为字符串（即编码为 JSON 的数组）而非文件的情况设计。由于我们需要绝对确保传入的 `$input` 值是字符串数据类型，因此在开始标签后立即调用 PHP 7 的严格类型声明。我们还标识了一个 `$pos` 属性（即位置），该属性将模拟文件指针，但它指向的是字符串内的位置，而不是文件：

```php
<?php
declare(strict_types=1);
namespace Application\Middleware;
use Throwable;
use RuntimeException;
use SplFileInfo;
use Psr\Http\Message\StreamInterface;

class TextStream implements StreamInterface
{
    protected $stream;
    protected $pos = 0;
```

大多数方法都非常简单且不言自明。`$stream` 属性即为输入字符串：

```php
public function __construct(string $input)
{
    $this->stream = $input;
}

public function getStream()
{
    return $this->stream;
}

public function getInfo()
{
    return NULL;
}

public function getContents()
{
    return $this->stream;
}

public function __toString()
{
    return $this->getContents();
}

public function getSize()
{
    return strlen($this->stream);
}
```

```php
public function close()
{
    // 不做任何事：你如何“关闭”字符串呢？
}
public function detach()
{
    return $this->close();  // 即：不做任何事！
}
```

为了模拟流行为，`tell()`、`eof()`、`seek()` 等方法都与 `$pos` 交互：

```php
public function tell()
{
    return $this->pos;
}
public function eof()
{
    return ($this->pos == strlen($this->stream));
}
public function isSeekable()
{
    return TRUE;
}
public function seek($offset, $whence = NULL)
{
    if ($offset < $this->getSize()) {
        $this->pos = $offset;
    } else {
        throw new RuntimeException(
            Constants::ERROR_BAD . __METHOD__ );
    }
}
public function rewind()
{
    $this->pos = 0;
}
public function isWritable()
{
    return TRUE;
}
```

`read()` 和 `write()` 方法与 `$pos` 和子字符串交互：

```php
public function write($string)
{
    $temp = substr($this->stream, 0, $this->pos);
    $this->stream = $temp . $string;
    $this->pos = strlen($this->stream);
}

public function isReadable()
{
    return TRUE;
}

public function read($length)
{
    return substr($this->stream, $this->pos, $length);
}

public function getMetadata($key = null)
{
    return NULL;
}
```

最后一个介绍的类值是 `Application\Middleware\UploadedFile`。与其他类一样，我们首先定义表示文件上传各个方面的属性：

```php
namespace Application\Middleware;
use RuntimeException;
use InvalidArgumentException;
use Psr\Http\Message\UploadedFileInterface;
class UploadedFile implements UploadedFileInterface
{
    protected $field;    // 文件上传字段的原始名称
    protected $info;     // $_FILES[$field]
    protected $randomize;
    protected $movedName = '';
```

在构造函数中，我们允许定义文件上传表单字段的名称属性，以及 `$_FILES` 中对应的数组。我们添加最后一个参数，以指示在确认上传的文件后，是否希望该类生成一个新的随机文件名：

```php
public function __construct(
    $field, array $info, $randomize = FALSE)
{
    $this->field = $field;
    $this->info = $info;
    $this->randomize = $randomize;
}
```

接下来，我们为临时文件或移动后的文件创建一个 Stream 类实例：

```php
public function getStream()
{
    if (!$this->stream) {
        if ($this->movedName) {
            $this->stream = new Stream($this->movedName);
        } else {
            $this->stream = new Stream($info['tmp_name']);
        }
    }
    return $this->stream;
}
```

`moveTo()` 方法执行实际的移动文件操作。请注意，有大量的安全检查系列，以帮助防止注入攻击。如果没有启用 `randomize`，我们使用原始的用户提供文件名：

```php
public function moveTo($targetPath)
{
    if ($this->moved) {
        throw new Exception(Constants::ERROR_MOVE_DONE);
    }
    if (!file_exists($targetPath)) {
        throw new InvalidArgumentException(Constants::ERROR_BAD_DIR);
    }
    $tempFile = $this->info['tmp_name'] ?? FALSE;
    if (!$tempFile || !file_exists($tempFile)) {
        throw new Exception(Constants::ERROR_BAD_FILE);
    }
    if (is_uploaded_file($tempFile)) {
        throw new Exception(Constants::ERROR_FILE_NOT);
    }
```

```php
if ($this->randomize) {
    $final = bin2hex(random_bytes(8)) . '.txt';
} else {
    $final = $this->info['name'];
}
$final = $targetPath . '/' . $final;
$final = str_replace('//', '/', $final);
if (!move_uploaded_file($tempFile, $final)) {
    throw new RuntimeException(Constants::ERROR_MOVE_UNABLE);
}

$this->movedName = $final;
return TRUE;
}
```

随后，我们通过 `$info` 属性提供对 `$_FILES` 中返回的其他参数的访问。请注意，`getClientFilename()` 和 `getClientMediaType()` 的返回值应被视为不可信的，因为它们来自外部。我们还添加了一个方法来返回移动后的文件名：

```php
public function getMovedName()
{
    return $this->movedName ?? NULL;
}
public function getSize()
{
    return $this->info['size'] ?? NULL;
}
public function getError()
{
    if (!$this->moved) {
        return UPLOAD_ERR_OK;
    }
    return $this->info['error'];
}
public function getClientFilename()
{
    return $this->info['name'] ?? NULL;
}
public function getClientMediaType()
{
    return $this->info['type'] ?? NULL;
}
```

# 工作原理...

首先，前往 `https://github.com/php-fig/http-message/tree/master/src`，这是 PSR-7 接口的 GitHub 仓库，并下载这些文件。在 `/path/to/` 下创建一个名为 `Psr/Http/Message` 的目录，并将文件放置在那里。或者，你可以访问 `https://packagist.org/packages/psr/http-message` 并使用 Composer 安装源代码。（有关如何获取和使用 Composer 的说明，你可以访问 `https://getcomposer.org/`。）

然后，定义前面讨论过的类，总结如下表所示：

| 类 | 讨论所在步骤 |
| --- | --- |
| Application\Middleware\Constants | 2 |
| Application\Middleware\Uri | 3 到 16 |
| Application\Middleware\Stream | 17 到 22 |
| Application\Middleware\TextStream | 23 到 26 |
| Application\Middleware\UploadedFile | 27 到 31 |

接下来，定义一个名为 `chap_09_middleware_value_objects_uri.php` 的调用程序，该程序实现了自动加载并使用适当的类。请注意，如果你使用 Composer，除非另有指示，否则它会创建一个名为 `vendor` 的文件夹。Composer 还会添加其自己的自动加载器，你可以在这里自由使用它：

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Middleware\Uri;
```

然后，你可以创建一个 Uri 实例并使用 `with` 方法添加参数。随后，你可以直接输出 `Uri` 实例，因为定义了 `__toString()` 方法：

```php
$uri = new Uri();
$uri->withScheme('https')
    ->withHost('localhost')
    ->withPort('8080')
    ->withPath('chap_09_middleware_value_objects_uri.php')
    ->withQuery('param=TEST');

echo $uri;
```

