# Accessing Web Services

+   8. In this recipe, we will define a `Application\Web\Request` class that can accept parameters when we wish to generate a request, or, alternatively, populate properties with incoming request information when implementing a server that accepts requests:

```php
namespace Application\Web;
class Request extends AbstractHttp
{
    public function __construct(
        $uri = NULL, $method = NULL, array $headers = NULL,
        array $data = NULL, array $cookies = NULL)
    {
        if (!$headers) $this->headers = $_SERVER ?? array();
        else $this->headers = $headers;

        if (!$uri) $this->uri = $this->headers['PHP_SELF'] ?? '';
        else $this->uri = $uri;

        if (!$method) $this->method =
        $this->headers['REQUEST_METHOD'] ?? self::METHOD_GET;
        else $this->method = $method;

        if (!$data) $this->data = $_REQUEST ?? array();
        else $this->data = $data;

        if (!$cookies) $this->cookies = $_COOKIE ?? array();
        else $this->cookies = $cookies;

        $this->setTransport();
    }
}
```

+   9. Now we can turn our attention to a response class. In this case, we will define an `Application\Web\Received` class. The name reflects the fact that we are repackaging data received from the external web service:

```php
namespace Application\Web;
class Received extends AbstractHttp
{
    public function __construct(
        $uri = NULL, $method = NULL, array $headers = NULL,
        array $data = NULL, array $cookies = NULL)
    {
        $this->uri = $uri;
        $this->method = $method;
        $this->headers = $headers;
        $this->data = $data;
        $this->cookies = $cookies;
        $this->setTransport();
    }
}
```