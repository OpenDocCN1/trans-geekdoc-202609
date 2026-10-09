```
```php
    ->withBody($body);
}

public function removeByGroup(RequestInterface $request)
{
    $text = array();
    $group = $request->getUri()->getQueryParams()['group']
            ?? Constants::DEFAULT_GROUP;
    $results = $this->adapter->removeByGroup($group);
    if (!$results) {
        $code = 204;
    } else {
        $code = 200;
        $text[] = $results;
    }
    $body = new TextStream(json_encode($text));
    return (new Response())->withStatus($code)
            ->withBody($body);
}
} // closing brace for class Core
```
```

# # How it works...

In order to demonstrate the use of the Acl class, you will need to define the classes
described in this recipe, summarized here:

| Class | Discussed in these steps |
| :--- | :--- |
| Application\Cache\Constants | 1 |
| Application\Cache\CacheAdapterInterface | 2 |
| Application\Cache\Database | 3 - 10 |
| Application\Cache\File | 11 |
| Application\Cache\Core | 12 - 16 |

Next, define a test program, which you could call chap_09_middleware_cache_db.php.
In this program, as usual, define constants for necessary files, set up autoloading, use the
appropriate classes, oh... and write a function that produces prime numbers (you're probably
re-reading that last little bit at this point. Not to worry, we can help you with that!):

```
```php
<?php
define('DB_CONFIG_FILE', __DIR__ . './../config/db.config.php');
define('DB_TABLE', 'cache');
define('CACHE_DIR', __DIR__ . '/cache');
define('MAX_NUM', 100000);
```
```