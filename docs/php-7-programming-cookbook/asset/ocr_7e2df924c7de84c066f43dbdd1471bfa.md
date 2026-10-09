# How to do it…

+   1.  First, be sure to define classes to represent the `Uri`, `Stream`, and `UploadedFile` value objects, as described in the previous recipe.

+   2.  Now we are ready to define the core `Application\MiddleWare\Message` class. This class consumes `Stream` and `Uri` and implements `Psr\Http\Message\MessageInterface`. We first define properties for the key value objects, including those representing the message body (that is, a `StreamInterface` instance), version, and HTTP headers:

```
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

+   3.  Next, we have the `getBody()` method that represents a `StreamInterface` instance. A companion method, `withBody()`, returns the current `Message` instance and allows us to overwrite the current value of `body`:

```
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