```
$uri .= ($this->getHost() ? $this->getHost() : '';
$uri .= ($this->getPort()
? ':' . $this->getPort() : '';)
}
```

+   16. Before adding path, we first check whether the first character is \(/\). If not, we need to add this separator. We then add query and fragment, if present:
```php
$path = $this->getPath();
if ($path) {
    if ($path[0] != '/') {
        $uri .= '/' . $path;
    } else {
        $uri .= $path;
    }
}
$uri .= ($this->getQuery()
? '?' . $this->getQuery() : '';
$uri .= ($this->getFragment())
? '#' . $this->getFragment() : '';
return $uri;
}
```
```php
public function getUriString()
{
    return $this->__toString();
}
```

> Note the use of string dereferencing (that is, $path[0]), now part of PHP 7.

+   17. Next, we turn our attention to a class that represents the body of the message. As it is not known how large the body might be, PSR-7 recommends that the body should be treated as a stream. A stream is a resource that allows access to input and output sources in a linear fashion. In PHP, all file commands operate on top of the Streams sub-system, so this is a natural fit. PSR-7 formalizes this by way of Psr\Http\Message\StreamInterface that defines such methods as read(), write(), seek(), and so on. We now present Application\MiddleWare\Stream that we can use to represent the body of incoming or outgoing requests and/or responses:
```php
namespace Application\MiddleWare;
use SplFileInfo;
use Throwable;
```