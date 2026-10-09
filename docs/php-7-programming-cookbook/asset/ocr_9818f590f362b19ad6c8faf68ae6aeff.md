23. An important variation of the Stream class shown previously is TextStream that is designed for situations where the body is a string (that is, an array encoded as JSON) rather than a file. As we need to make absolutely certain that the incoming `$input` value is of the string data type, we invoke PHP 7 strict types just after the opening tag. We also identify a `$pos` property (that is, position) that will emulate a file pointer, but instead point to a position within the string:

```
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
```

24. Most of the methods are quite simple and self-explanatory. The `$stream` property is the input string:

```
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
```
```