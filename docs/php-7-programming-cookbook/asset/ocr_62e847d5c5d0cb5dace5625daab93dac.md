2. We will also need to define a formal Application\Web\Response response class, based on AbstractHttp. The primary difference between this class and the others is that it accepts an instance of Application\Web\Request as an argument. The primary work is accomplished in the __construct( ) method. It’s also important to set the Content-Type header and status:

```
```php
namespace Application\Web;
class Response extends AbstractHttp
{
    public function __construct(Request $request = NULL,
        $status = NULL, $contentType = NULL)
    {
        if ($request) {
            $this->uri = $request->getUri();
            $this->data = $request->getData();
            $this->method = $request->getMethod();
            $this->cookies = $request->getCookies();
            $this->setTransport();
        }
        $this->processHeaders($contentType);
        if ($status) {
            $this->setStatus($status);
        }
    }
    protected function processHeaders($contentType)
    {
        if (!$contentType) {
            $this->setHeaderByKey(self::HEADER_CONTENT_TYPE,
                self::CONTENT_TYPE_JSON);
        } else {
            $this->setHeaderByKey(self::HEADER_CONTENT_TYPE,
                $contentType);
        }
    }
    public function setStatus($status)
    {
        $this->status = $status;
    }
    public function getStatus()
    {
        return $this->status;
    }
}
```
```