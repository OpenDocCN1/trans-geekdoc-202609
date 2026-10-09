+   12. Now we are ready to present the core cache mechanism. In the constructor, we accept a class that implements CacheAdapterInterface as an argument:
```
namespace Application\Cache;
use Psr\Http\Message\RequestInterface;
use Application\Middleware\{ Request, Response, TextStream };
class Core
{
    public function __construct(CacheAdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
```

+   13. Next are a series of wrapper methods that call methods of the same name from the adapter, but accept a Psr\Http\Message\RequestInterface class as an argument, and return a Psr\Http\Message\ResponseInterface as a response. We start with a simple one: hasKey(). Note how we extract the key from the request parameters:
```
public function hasKey(RequestInterface $request)
{
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $result = $this->adapter->hasKey($key);
}
```

+   14. To retrieve information from the cache, we need to pull the key and group parameters from the request object, and then call the same method from the adapter. If no results are obtained, we set a 204 code, which indicates the request was a success, but no content was produced. Otherwise, we set a 200 (success) code, and iterate through the results. Everything is then stuffed into a response object, which is returned:
```
public function getFromCache(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $group = $request->getUri()->getQueryParams()['group']
        ?? Constants::DEFAULT_GROUP;
    $results = $this->adapter->getFromCache($key, $group);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        foreach ($results as $line) $text[] = $line;
    }
}
```