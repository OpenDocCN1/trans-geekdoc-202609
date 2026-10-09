```
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Database\Connection;
use Application\Cache\{ Constants, Core, Database, File };
use Application\MiddleWare\{ Request, TextStream };
```

Well, a function that takes a long time to run is needed, so prime number generator, here we go! The numbers 1, 2, and 3 are given as primes. We use the PHP 7 yield from syntax to produce these first three, then, we skip right to 5, and proceed up to the maximum value requested:

```
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

```
$conn    = new Connection(include DB_CONFIG_FILE);
$dbCache = new Database(
        $conn, DB_TABLE, 'id', 'key', 'data', 'group');
$core    = new Core($dbCache);
```

Alternatively, if you wish to use the file cache adapter instead, here is the appropriate code:

```
$fileCache = new File(CACHE_DIR);
$core      = new Core($fileCache);
```

If you wanted to clear the cache, here is how it might be done:

```
$uriString = '/?group=' . Constants::DEFAULT_GROUP;
$cacheRequest = new Request($uriString, 'get');
$response = $core->removeByGroup($cacheRequest);
```