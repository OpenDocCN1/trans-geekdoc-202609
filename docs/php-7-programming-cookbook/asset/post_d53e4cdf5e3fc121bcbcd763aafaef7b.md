
Finally, in the public folder, define `index.php`, which sets up autoloading, and ultimately calls up both the `Authenticate` and `Acl` classes. As with other recipes, define configuration files, set up autoloading, and use certain classes. Also, don't forget to start the session:

```php
<?php
session_start();
session_regenerate_id();
define('DB_CONFIG_FILE', __DIR__ . '/../../config/db.config.php');
define('DB_TABLE', 'customer_09');
define('PAGE_DIR', __DIR__ . '/..');
define('SESSION_KEY', 'auth');
require __DIR__ . '/../../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/..');
use Application\Database\Connection;
use Application\Acl\ { Authenticate, Acl };
use Application\MiddleWare\ { ServerRequest, Request, Constants,
TxtStream };
```

## Best practice

It is a best practice to protect your sessions. An easy way to help protect a session is to use `session_regenerate_id()`, which invalidates the existing PHP session identifier and generates a new one. Thus, if an attacker were to obtain the session identifier through illegal means, the window of time in which any given session identifier is valid is kept to a minimum.

You can now pull in the ACL configuration, and create instances for `Authenticate` as well as `Acl`:

```php
$config = require __DIR__ . '/../chap_09_middleware_acl_config.php';
$acl    = new Acl($config);
$conn   = new Connection(include DB_CONFIG_FILE);
$dbAuth = new DbTable($conn, DB_TABLE);
$auth   = new Authenticate($dbAuth, SESSION_KEY);
```

Next, define incoming and outbound request instances:

```php
$incoming = new ServerRequest();
$incoming->initialize();
$outbound = new Request();
```

If the incoming request method was post, process the authentication calling the `login()` method:

```php
if (strtolower($incoming->getMethod()) == Constants::METHOD_POST) {
    $body    = new TextStream(json_encode(
            $incoming->getParsedBody()));
    $response = $auth->login($outbound->withBody($body));
}
```

If the session key defined for authentication is populated, that means the user has been successfully authenticated. If not, we program an anonymous function, called later, which includes the authentication login page:

```php
$info = $_SESSION[SESSION_KEY] ?? FALSE;
if (!$info) {
    $execute = function () use ($auth) {
        include PAGE_DIR . '/auth.php';
    };
}
```

Otherwise, you can proceed with the ACL check. You first need to find, from the original query, which web page the user wants to visit, however:

```php
} else {
    $query = $incoming->getServerParams()['QUERY_STRING'] ?? '';
```

You can then reprogram the `$outbound` request to include this information:

```php
$outbound->withBody(new TextStream(json_encode($info)));
$outbound->getUri()->withQuery($query);
```

Next, you'll be in a position to check authorization, supplying the outbound request as an argument:

```php
$response = $acl->isAuthorized($outbound);
```

You can then examine the return response for the authorized parameter, and program an anonymous function to include the return page parameter if OK, and the sorry page otherwise:

```php
$params     = json_decode($response->getBody()->getContents());
$isAllowed  = $params->authorized ?? FALSE;
if ($isAllowed) {
    $execute = function () use ($response, $params) {
        include PAGE_DIR .'/' . $params->page . '.php';
        echo '<pre>', var_dump($response), '</pre>';
        echo '<pre>', var_dump($_SESSION[SESSION_KEY]);
        echo '</pre>';
    };
} else {
    $execute = function () use ($response) {
        include PAGE_DIR .'/sorry.php';
        echo '<pre>', var_dump($response), '</pre>';
        echo '<pre>', var_dump($_SESSION[SESSION_KEY]);
        echo '</pre>';
    };
}
```

Now all you need to do is to set the form action and wrap the anonymous function in HTML:

```php
$action = $incoming->getServerParams()['PHP_SELF'];
?>
<!DOCTYPE html>
<head>
	<title>PHP 7 Cookbook</title>
	<meta http-equiv="content-type" content="text/html;charset=utf-8" />
</head>
<body>
	<?php $execute() ; ?>
</body>
</html>
```

To test it, you can use the built-in PHP web server, but you will need to use the `-t` flag to indicate that the document root is `public`:

```bash
cd /path/to/source/for/this/chapter
php -S localhost:8080 -t public
```

From a browser, you can access the `http://localhost:8080/` URL.

If you try to access any page, you will simply be redirected back to the login page. As per the configuration, a user with `status = 1`, and `level = BEG` can only access page 1 and log out. If, when logged in as this user, you try to access page 2, here is the output:

![](img/39390f6d56c5a83b28db083a8bd5185c_344_0.png)

## See also

This example relies on `$_SESSION` as the sole means of user authentication once they have logged in. For good examples of how you can protect PHP sessions, please see **Chapter 12, Improving Web Security**, specifically the recipe entitled *Safe guarding the PHP session*.

# Improving performance using the cache

The cache software design pattern is where you store a result that takes a long time to generate. This could take the form of a lengthy view script or a complex database query. The storage destination needs to be highly performant, of course, if you wish to improve the user experience of website visitors. As different installations will have different potential storage targets, the cache mechanism lends itself to the adapter pattern as well. Examples of potential storage destinations include memory, a database, and the filesystem.

## How to do it...

1. As with a couple of other recipes in this chapter, as there are shared constants, we define a discreet `Application\Cache\Constants` class:
   ```php
   <?php
   namespace Application\Cache;

   class Constants
   {
       const DEFAULT_GROUP   = 'default';
       const DEFAULT_PREFIX  = 'CACHE_';
       const DEFAULT_SUFFIX  = '.cache';
       const ERROR_GET      = 'ERROR: unable to retrieve from cache';
       // not all constants are shown to conserve space
   }
   ```

2. Seeing as we are following the adapter design pattern, we define an interface next:
   ```php
   namespace Application\Cache;
   interface CacheAdapterInterface
   {
       public function hasKey($key);
       public function getFromCache($key, $group);
       public function saveToCache($key, $data, $group);
       public function removeByKey($key);
       public function removeByGroup($group);
   }
   ```

3. Now we are ready to define our first cache adapter, in this illustration, by using a MySQL database. We need to define properties that will hold column names as well as prepared statements:
   ```php
   namespace Application\Cache;
   use PDO;
   use Application\Database\Connection;
   ```

4. The constructor allows us to provide key column names as well as an `Application\Database\Connection` instance and the name of the table used for the cache:
   ```php
   class Database implements CacheAdapterInterface
   {
   protected $sql;
   protected $connection;
   protected $table;
   protected $dataColumnName;
   protected $keyColumnName;
   protected $groupColumnName;
   protected $statementHasKey = NULL;
   protected $statementGetFromCache = NULL;
   protected $statementSaveToCache = NULL;
   protected $statementRemoveByKey = NULL;
   protected $statementRemoveByGroup = NULL;

   public function __construct(Connection $connection,
   $table,
   $idColumnName,
   $keyColumnName,
   $dataColumnName,
   $groupColumnName = Constants::DEFAULT_GROUP)
   {
       $this->connection = $connection;
       $this->setTable($table);
       $this->setIdColumnName($idColumnName);
       $this->setDataColumnName($dataColumnName);
       $this->setKeyColumnName($keyColumnName);
       $this->setGroupColumnName($groupColumnName);
   }
   ```

5. The next few methods prepare statements, and are called when we access the database. We do not show all the methods, but present enough to give you the idea:
   ```php
   public function prepareHasKey()
   {
       $sql = 'SELECT `' . $this->idColumnName . '`'
       . '`FROM ` . $this->table . '` '
       . '`WHERE `' . $this->keyColumnName . '` = :key ';
       $this->sql[__METHOD__] = $sql;
       $this->statementHasKey =
       $this->connection->pdo->prepare($sql);
   }
   public function prepareGetFromCache()
   ```
