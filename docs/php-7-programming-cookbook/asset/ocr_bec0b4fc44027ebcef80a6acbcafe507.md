# ## How it works...

Copy the preceding code into a **Paginate.php** file in the Application/Database folder.  
You can then create a chap_05_pagination.php calling program, which initializes the autoloader defined in *Chapter 1, Building a Foundation*:

```
```php
<?php
define('DB_CONFIG_FILE',  '/../config/db.config.php');
define('LINES_PER_PAGE',  10);
define('DEFAULT_BALANCE', 1000);
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
```
```

Next, use the Application\Database\Finder, Connection, and Paginate classes, create an instance of Application\Database\Connection, and use Finder to generate SQL:

```
```php
use Application\Database\ { Finder, Connection, Paginate};
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$sql  = Finder::select('customer')->where('balance < :bal');
```
```

We can now get the page number and balance from $_GET parameters, and create the Paginate object, ending the PHP block:

```
```php
$page  = (int) ($_GET['page'] ?? 0);
$bal   = (float) ($_GET['balance'] ?? DEFAULT_BALANCE);
$Paginate = new Paginate($sql->getSql(), $page, LINES_PER_PAGE);
?>
```
```

In the output portion of the script, we simply iterate through the pagination using a simple foreach() loop:

```
```html
<h3><?= $Paginate->getSql(); ?></h3>
<hr>
<pre>
<?php
printf('%4s | %20s | %5s | %7s' . PHP_EOL,
    'ID', 'NAME', 'LEVEL', 'BALANCE');
printf('%4s | %20s | %5s | %7s' . PHP_EOL,
    '----', str_repeat('-', 20), '-----', '--------');
foreach ($Paginate->paginate($conn, PDO::FETCH_ASSOC,
       ['bal' => $bal]) as $row) {
    printf('%4d | %20s | %5s | %7.2f' . PHP_EOL,
      $row['id'], $row['name'], $row['level'], $row['balance']);
}
    printf('%4s | %20s | %5s | %7s' . PHP_EOL,
```

```