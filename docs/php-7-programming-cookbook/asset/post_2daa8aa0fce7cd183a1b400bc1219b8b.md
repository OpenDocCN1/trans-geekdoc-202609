
# Defining PSR-7 Classes

We also need to define informational methods that tell us about the stream:

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

Following PSR-7 guidelines, we then define `getContents()` and `__toString()` in order to dump the contents of the stream:

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

An important variation of the Stream class shown previously is TextStream that is designed for situations where the body is a string (that is, an array encoded as JSON) rather than a file. As we need to make absolutely certain that the incoming `$input` value is of the string data type, we invoke PHP 7 strict types just after the opening tag. We also identify a `$pos` property (that is, position) that will emulate a file pointer, but instead point to a position within the string:

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

Most of the methods are quite simple and self-explanatory. The `$stream` property is the input string:

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
    // do nothing: how can you "close" string???
}
public function detach()
{
    return $this->close();  // that is, do nothing!
}
```

To emulate streaming behavior, `tell()`, `eof()`, `seek()`, and so on, work with `$pos`:

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

The `read()` and `write()` methods work with `$pos` and substrings:

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

The last of the value objects to be presented is `Application\Middleware\UploadedFile`. As with the other classes, we first define properties that represent aspects of a file upload:

```php
namespace Application\Middleware;
use RuntimeException;
use InvalidArgumentException;
use Psr\Http\Message\UploadedFileInterface;
class UploadedFile implements UploadedFileInterface
{
    protected $field;    // original name of file upload field
    protected $info;     // $_FILES[$field]
    protected $randomize;
    protected $movedName = '';
```

In the constructor, we allow the definition of the name attribute of the file upload form field, as well as the corresponding array in `$_FILES`. We add the last parameter to signal whether or not we want the class to generate a new random filename once the uploaded file is confirmed:

```php
public function __construct(
    $field, array $info, $randomize = FALSE)
{
    $this->field = $field;
    $this->info = $info;
    $this->randomize = $randomize;
}
```

Next, we create a Stream class instance for the temporary or moved file:

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

The `moveTo()` method performs the actual file movement. Note the extensive series of safety checks to help prevent an injection attack. If `randomize` is not enabled, we use the original user-supplied filename:

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

We then provide access to the other parameters returned in `$_FILES` from the `$info` property. Please note that the return values from `getClientFilename()` and `getClientMediaType()` should be considered untrusted, as they originate from the outside. We also add a method to return the moved filename:

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

# How it works...

First of all, go to `https://github.com/php-fig/http-message/tree/master/src`, the GitHub repository for the PSR-7 interfaces, and download them. Create a directory called `Psr/Http/Message` in `/path/to/` and place the files there. Alternatively, you can visit `https://packagist.org/packages/psr/http-message` and install the source code using Composer. (For instructions on how to obtain and use Composer, you can visit `https://getcomposer.org/`.)

Then, go ahead and define the classes discussed previously, summarized in this table:

| Class | Steps discussed in |
| --- | --- |
| Application\Middleware\Constants | 2 |
| Application\Middleware\Uri | 3 to 16 |
| Application\Middleware\Stream | 17 to 22 |
| Application\Middleware\TextStream | 23 to 26 |
| Application\Middleware\UploadedFile | 27 to 31 |

Next, define a `chap_09_middleware_value_objects_uri.php` calling program that implements autoloading and uses the appropriate classes. Please note that if you use Composer, unless otherwise instructed, it will create a folder called `vendor`. Composer also adds its own autoloader, which you are free to use here:

```php
<?php
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Middleware\Uri;
```

You can then create a Uri instance and use the `with` methods to add parameters. You can then echo the `Uri` instance directly as `__toString()` is defined:

```php
$uri = new Uri();
$uri->withScheme('https')
    ->withHost('localhost')
    ->withPort('8080')
    ->withPath('chap_09_middleware_value_objects_uri.php')
    ->withQuery('param=TEST');

echo $uri;
```
