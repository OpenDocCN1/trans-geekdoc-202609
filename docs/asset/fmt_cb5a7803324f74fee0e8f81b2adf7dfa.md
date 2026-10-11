
### 5. 下一个方法，未在 PSR-7 中定义，旨在填充 `$httpHeaders` 属性。该属性假设是一个关联数组，其中键是头，值是表示头值的字符串。如果有多个值，则以逗号分隔的附加值会被追加到字符串中。Apache 扩展有一个出色的 `apache_request_headers()` PHP 函数，如果在 `$httpHeaders` 中尚未提供头，则会产生这些头：

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

### 6. 如果 `apache_request_headers()` 不可用（即未启用 Apache 扩展），我们提供了一个替代方案 `altApacheReqHeaders()`：

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

### 7. 实现 `getHeaders()`（PSR-7 中要求）现在只是一个遍历 `getHttpHeaders()` 方法（在第 4 步中讨论）生成的 `$httpHeaders` 属性的简单循环：

```php
    public function getHeaders()
    {
        foreach ($this->getHttpHeaders() as $key => $value) {
            header($key . ': ' . $value);
        }
    }
```

### 8. 同样，我们提供了一系列 `with` 方法，旨在覆盖或替换头。由于可能有多个头，我们还提供一个方法向现有头集合中添加头。`withoutHeader()` 方法用于移除某个头实例。注意在前一步骤中提到的 `findHeader()` 的一致使用，以允许对头进行不区分大小写的处理：

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

### 9. 然后，我们提供了一系列有用的请求头相关方法，用于确认请求头是否存在、获取单个请求头行以及以数组形式获取请求头，符合 PSR-7 标准：

```php
public function hasHeader($name)
{
    return boolval($this->findHeader($name));
}

public function getHeaderLine($name)
{
    $found = $this->findHeader($name);
    if ($found) {
        return $this->httpHeaders[$found];
    } else {
        return '';
    }
}

public function getHeader($name)
{
    $line = $this->getHeaderLine($name);
    if ($line) {
        return explode(',', $line);
    } else {
        return array();
    }
}
```

### 10. 最后，为了完善请求头的处理，我们介绍了 `getHeadersAsString` 方法，该方法生成一个单独的请求头字符串，其中各请求头之间使用 `\r\n` 分隔，以便直接用于 PHP 流上下文：

```php
public function getHeadersAsString()
{
    $output = '';
    $headers = $this->getHeaders();
    if ($headers && is_array($headers)) {
        foreach ($headers as $key => $value) {
            if ($output) {
                $output .= "\r\n" . $key . ': ' . $value;
            } else {
                $output  = $key . ': ' . $value;
            }
        }
    }
    return $output;
}
```

### 11. 仍在 `Message` 类中，我们现在将注意力转向版本处理。根据 PSR-7，协议版本（即 HTTP/1.1）的返回值应仅包含数字部分。出于此原因，我们还提供了 `onlyVersion()` 方法，该方法去除所有非数字字符，但允许保留句号：

```php
public function getProtocolVersion()
{
    if (!isset($this->version)) {
        $this->version = $this->onlyVersion(
            $_SERVER['SERVER_PROTOCOL']
        );
    }
    return $this->version;
}
```

```php
public function withProtocolVersion($version)
{
    $this->version = $this->onlyVersion($version);
    return $this;
}
```

```php
protected function onlyVersion($version)
{
    if (!empty($version)) {
        return preg_replace('/[^0-9\.]/', '', $version);
    } else {
        return NULL;
    }
}
```

### 12. 最后，几乎是顺理成章地，我们准备好定义我们的 `Request` 类。然而，必须指出的是，我们需要考虑出站请求和入站请求。也就是说，我们需要一个类来表示客户端将向服务器发出的传出请求，以及服务器从客户端接收到的请求。相应地，我们提供了 `Application\MiddleWare\Request`（客户端将向服务器发出的请求）和 `Application\MiddleWare\ServerRequest`（服务器从客户端接收到的请求）。好消息是，我们的大部分工作已经完成：请注意，我们的 `Request` 类继承了 `Message`。我们还提供了表示 URL 和 HTTP 方法的属性：

```php
namespace Application\Middleware;

use InvalidArgumentException;
use Psr\Http\Message\{ RequestInterface, StreamInterface, UriInterface };

class Request extends Message implements RequestInterface
{
    protected $uri;
    protected $method; // HTTP method
    protected $uriObj; // Psr\Http\Message\UriInterface instance
```

### 13. 构造函数中的所有属性默认为 NULL，但我们保留了立即定义相应参数的可能性。我们使用继承的 `onlyVersion()` 方法对版本进行清理。我们还定义了 `checkMethod()`，以确保提供的任何方法都在我们支持的 HTTP 方法列表中，该列表在 `Constants` 中定义为常量数组：

```php
public function __construct($uri = NULL,
                           $method = NULL,
                           StreamInterface $body = NULL,
                           $headers = NULL,
                           $version = NULL)
{
    $this->uri = $uri;
    $this->body = $body;
    $this->method = $this->checkMethod($method);
    $this->httpHeaders = $headers;
    $this->version = $this->onlyVersion($version);
}

protected function checkMethod($method)
{
    if ($method !== NULL) {
        if (!in_array(strtolower($method), Constants::HTTP_METHODS)) {
            throw new InvalidArgumentException(
                Constants::ERROR_HTTP_METHOD
            );
        }
    }
    return $method;
}
```

### 14. 我们将解释请求目标为原始请求的 URI，形式为字符串。请记住，我们的 `Uri` 类有方法可以将其解析为其组成部分，因此我们提供了 `$uriObj` 属性。在 `withRequestTarget()` 的情况下，请注意我们运行了 `getUri()`，它执行上述解析过程：

```php
public function getRequestTarget()
{
    return $this->uri ?? Constants::DEFAULT_REQUEST_TARGET;
}

public function withRequestTarget($requestTarget)
{
    $this->uri = $requestTarget;
    $this->getUri();
    return $this;
}
```

### 15. 我们的 `get` 和 `with` 方法，代表 HTTP 方法，没有让人意外的地方。我们使用在构造函数中同样使用的 `checkMethod()`，以确保该方法匹配我们计划支持的那些方法：

```php
public function getMethod()
{
    return $this->method;
}

public function withMethod($method)
{
    $this->method = $this->checkMethod($method);
    return $this;
}
```

## 附录

### 16. 最后，我们有一个针对 URI 的 `get` 和 `with` 方法。如步骤 14 中所述，我们在 `Uri` 属性中保留原始请求字符串，在 `UriObj` 中保留新解析的 `Uri` 实例。注意额外的标志用于保留任何现有的 Host 请求头：

```php
public function getUri()
{
    if (!$this->uriObj) {
        $this->uriObj = new Uri($this->uri);
    }
    return $this->uriObj;
}

public function withUri(UriInterface $uri, $preserveHost = false)
{
    if ($preserveHost) {
        $found = $this->findHeader(Constants::HEADER_HOST);
        if (!$found && $uri->getHost()) {
            $this->httpHeaders[Constants::HEADER_HOST] = $uri->getHost();
        } elseif ($uri->getHost()) {
            $this->httpHeaders[Constants::HEADER_HOST] = $uri->getHost();
        }
        $this->uri = $uri->__toString();
        return $this;
    }
}
```

### 17. `ServerRequest` 类继承自 `Request`，并提供了额外功能，以检索处理传入请求的服务器感兴趣的信息。我们通过定义将表示从各种 PHP `$_` 超全局变量（即 `$_SERVER`、`$_POST` 等）读取的传入数据的属性开始：

```php
namespace Application\Middleware;
use Psr\Http\Message\{ ServerRequestInterface,
UploadedFileInterface };

class ServerRequest extends Request implements
ServerRequestInterface
{
    protected $serverParams;
    protected $cookies;
    protected $queryParams;
    protected $contentType;
    protected $parsedBody;
    protected $attributes;
    protected $method;
    protected $uploadedFileInfo;
    protected $uploadedFileObjs;
}
```

### 18. 然后我们定义了一系列获取器来提取超全局变量信息。为了节省空间，我们没有展示所有内容：
