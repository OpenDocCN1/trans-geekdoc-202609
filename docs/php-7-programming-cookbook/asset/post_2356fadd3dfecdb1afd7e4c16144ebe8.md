
15. Strangely, writing to the cache is almost identical, except that the results are expected to be either a number (that is, the number of rows affected), or a Boolean result:

```php
public function saveToCache(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $group = $request->getUri()->getQueryParams()['group']
        ?? Constants::DEFAULT_GROUP;
    $data = $request->getBody()->getContents();
    $results = $this->adapter->saveToCache($key, $data, $group);
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
```

16. The remove methods are, as expected, quite similar to each other:

```php
public function removeByKey(RequestInterface $request)
{
    $text = array();
    $key = $request->getUri()->getQueryParams()['key'] ?? '';
    $results = $this->adapter->removeByKey($key);
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

## How it works...

In order to demonstrate the use of the Acl class, you will need to define the classes described in this recipe, summarized here:

| Class | Discussed in these steps |
| :--- | :--- |
| Application\Cache\Constants | 1 |
| Application\Cache\CacheAdapterInterface | 2 |
| Application\Cache\Database | 3 - 10 |
| Application\Cache\File | 11 |
| Application\Cache\Core | 12 - 16 |

Next, define a test program, which you could call `chap_09_middleware_cache_db.php`. In this program, as usual, define constants for necessary files, set up autoloading, use the appropriate classes, oh... and write a function that produces prime numbers (you're probably re-reading that last little bit at this point. Not to worry, we can help you with that!):

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . './../config/db.config.php');
define('DB_TABLE', 'cache');
define('CACHE_DIR', __DIR__ . '/cache');
define('MAX_NUM', 100000);

require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Database\Connection;
use Application\Cache\{ Constants, Core, Database, File };
use Application\MiddleWare\{ Request, TextStream };
```

Well, a function that takes a long time to run is needed, so prime number generator, here we go! The numbers 1, 2, and 3 are given as primes. We use the PHP 7 `yield from` syntax to produce these first three, then, we skip right to 5, and proceed up to the maximum value requested:

```php
function generatePrimes($max)
{
    yield from [1,2,3];
    for ($x = 5; $x < $max; $x++)
    {
        if ($x & 1) {
            $prime = TRUE;
            for($i = 3; $i < $x; $i++) {
                if(($x % $i) === 0) {
                    $prime = FALSE;
                    break;
                }
            }
            if ($prime) yield $x;
        }
    }
}
```

You can then set up a database cache adapter instance, which serves as an argument for the core:

```php
$conn    = new Connection(include DB_CONFIG_FILE);
$dbCache = new Database(
        $conn, DB_TABLE, 'id', 'key', 'data', 'group');
$core    = new Core($dbCache);
```

Alternatively, if you wish to use the file cache adapter instead, here is the appropriate code:

```php
$fileCache = new File(CACHE_DIR);
$core      = new Core($fileCache);
```

If you wanted to clear the cache, here is how it might be done:

```php
$uriString = '/?group=' . Constants::DEFAULT_GROUP;
$cacheRequest = new Request($uriString, 'get');
$response = $core->removeByGroup($cacheRequest);
```

## Developing Middleware

You can use `time()` and `microtime()` to see how long this script runs with and without the cache:

```php
$start = time() + microtime(TRUE);
echo "\nTime: " . $start;
```

Next, generate a cache request. A status code of 200 indicates you were able to obtain a list of primes from the cache:

```php
$uriString = '/?key=Test1';
$cacheRequest = new Request($uriString, 'get');
$response = $core->getFromCache($cacheRequest);
$status   = $response->getStatusCode();
if ($status == 200) {
    $primes = json_decode($response->getBody()->getContents());
} else {
    $primes = array();
    foreach (generatePrimes(MAX_NUM) as $num) {
        $primes[] = $num;
    }
    $body = new TextStream(json_encode($primes));
    $response = $core->saveToCache(
        $cacheRequest->withBody($body)
    );
}
```

You can then check the stop time, calculate the difference, and have a look at your new list of primes:

```php
$time = time() + microtime(TRUE);
$diff = $time - $start;
echo "\nTime: $time";
echo "\nDifference: $diff";
var_dump($primes);
```

Here is the expected output before values were stored in the cache:

```
561, 97571, 97577, 97579, 97583, 97607, 97609, 97613, 97649, 97651, 97673, 97687, 97711, 9772
9, 97771, 97777, 97787, 97789, 97813, 97829, 97841, 97843, 97847, 97849, 97859, 97861, 97871,
97879, 97883, 97919, 97927, 97931, 97943, 97961, 97979, 97973, 97987, 98009, 98011, 98017, 98
041, 98047, 98057, 98081, 98101, 98123, 98129, 98143, 98179, 98207, 98213, 98221, 98227, 9825
1, 98257, 98269, 98297, 98299, 98317, 98321, 98323, 98327, 98347, 98369, 98377, 98387, 98389,
98407, 98411, 98419, 98429, 98443, 98453, 98459, 98467, 98473, 98479, 98491, 98507, 98519, 98
533, 98543, 98561, 98563, 98573, 98597, 98621, 98627, 98639, 98641, 98663, 98669, 98709, 9879
1, 98713, 98717, 98729, 98731, 98737, 98773, 98779, 98801, 98807, 98809, 98837, 98849, 98867,
98869, 98873, 98887, 98893, 98897, 98899, 98899, 98911, 98927, 98929, 98939, 98947, 98953, 98
963, 98981, 98993, 98999, 99013, 99017, 99023, 99041, 99053, 99079, 99083, 99089, 99103, 9910
9, 99119, 99131, 99133, 99137, 99139, 99149, 99173, 99181, 99191, 99223, 99233, 99241, 99251,
99257, 99259, 99277, 99289, 99317, 99347, 99349, 99367, 99371, 99377, 99391, 99397, 99401, 99
409, 99431, 99439, 99469, 99487, 99497, 99523, 99527, 99529, 99551, 99559, 99563, 99571, 9957
7, 99581, 99607, 99611, 99623, 99643, 99661, 99667, 99679, 99689, 99707, 99709, 99713, 99719,
99721, 99733, 99761, 99767, 99787, 99793, 99809, 99817, 99823, 99829, 99833, 99839, 99859, 99
871, 99877, 99881, 99901, 99907, 99923, 99929, 99961, 99971, 99989, 99991]"

Time: 2934730510.8487
Difference: 33.938917160034

--------------------------------

(program exited with code: 0)
Press return to continue
```

You can now run the same program again, this time retrieving from the cache:

```
729, 97771, 97777, 97787, 97789, 97813, 97829, 97841, 97843, 97847, 97849, 97859, 97861, 9787
1, 97879, 97883, 97919, 97927, 97931, 97943, 97961, 97979, 97987, 98009, 98011, 98017,
98041, 98047, 98057, 98081, 98101, 98123, 98129, 98143, 98179, 98207, 98213, 98221, 98227, 98
251, 98257, 98269, 98297, 98299, 98317, 98321, 98323, 98327, 98347, 98369, 98377, 98387, 98389,
9, 98407, 98411, 98419, 98429, 98443, 98453, 98459, 98467, 98473, 98479, 98491, 98507, 98519,
98533, 98543, 98561, 98563, 98573, 98597, 98621, 98627, 98639, 98641, 98663, 98669, 98689, 98
711, 98713, 98717, 98729, 98731, 98737, 98773, 98779, 98801, 98807, 98809, 98837, 98849, 9886
7, 98869, 98873, 98887, 98893, 98897, 98899, 98899, 98911, 98927, 98929, 98939, 98947, 98953,
98963, 98981, 98993, 98999, 99013, 99017, 99023, 99041, 99053, 99079, 99083, 99089, 99103, 99
109, 99119, 99131, 99133, 99137, 99139, 99149, 99173, 99181, 99191, 99223, 99233, 99241, 9925
1, 99257, 99259, 99277, 99289, 99317, 99347, 99349, 99367, 99371, 99377, 99391, 99397, 99401,
99409, 99431, 99439, 99469, 99487, 99497, 99523, 99527, 99529, 99551, 99559, 99563, 99571, 99
577, 99581, 99607, 99611, 99623, 99643, 99661, 99667, 99679, 99689, 99707, 99709, 99713, 9971
9, 99721, 99733, 99761, 99767, 99787, 99793, 99809, 99817, 99823, 99829, 99833, 99839, 99859,
99871, 99877, 99881, 99901, 99907, 99923, 99929, 99961, 99971, 99989, 99991]

Time: 2934730718.9282
Difference: 0.00317278744506836

--------------------------------

(program exited with code: 0)
Press return to continue
```
