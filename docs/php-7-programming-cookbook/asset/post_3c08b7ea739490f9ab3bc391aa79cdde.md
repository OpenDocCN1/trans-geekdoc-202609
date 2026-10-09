
6. It might not be a bad idea to provide support for the query builder class mentioned in the previous recipe. This will make updating LIMIT and OFFSET much easier. All we need to do is to provide support for Application\Database\Finder is to use the class and modify the `__construct()` method to check to see if the incoming SQL is an instance of this class:

```php
if ($sql instanceof Finder) {
    $sql->limit($linesPerPage);
    $sql->offset($offset);
    $this->sql = $sql::getSql();
} elseif (is_string($sql)) {
    switch (TRUE) {
        case (stripos($sql, 'LIMIT')
          && stripos($sql, 'OFFSET') :
            // remaining code as shown in bullet #3 above
        }
    }
}
```

7. Now all that remains to be done is to add a getSql() method in case we need to confirm that the SQL statement was correctly formed:

```php
public function getSql()
{
    return $this->sql;
}
```

## How it works...

Copy the preceding code into a **Paginate.php** file in the Application/Database folder.
You can then create a chap_05_pagination.php calling program, which initializes the autoloader defined in *Chapter 1, Building a Foundation*:

```php
<?php
define('DB_CONFIG_FILE',  '/../config/db.config.php');
define('LINES_PER_PAGE',  10);
define('DEFAULT_BALANCE', 1000);
require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
```

Next, use the Application\Database\Finder, Connection, and Paginate classes, create an instance of Application\Database\Connection, and use Finder to generate SQL:

```php
use Application\Database\ { Finder, Connection, Paginate};
$conn = new Connection(include __DIR__ . DB_CONFIG_FILE);
$sql  = Finder::select('customer')->where('balance < :bal');
```

We can now get the page number and balance from $_GET parameters, and create the Paginate object, ending the PHP block:

```php
$page  = (int) ($_GET['page'] ?? 0);
$bal   = (float) ($_GET['balance'] ?? DEFAULT_BALANCE);
$Paginate = new Paginate($sql->getSql(), $page, LINES_PER_PAGE);
?>
```

In the output portion of the script, we simply iterate through the pagination using a simple foreach() loop:

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
    '------', str_repeat('|-', 20), '|------', '--------');
?>
<a href="?page=<?=$page - 1; ?>&balance=<?= $bal ?>">
<< Prev </a>&nbsp;&nbsp;
<a href="?page=<?= $page + 1; ?>&balance=<?= $bal ?>">
Next >></a>
</pre>
```

Here is page 3 of the output, where the balance is less than 1,000:

![](img/39390f6d56c5a83b28db083a8bd5185c_172_0.png)

## See also

For more information on the `LimitIterator` class, refer to this article:

- [http://php.net/manual/en/class.limititerator.php](http://php.net/manual/en/class.limititerator.php)

# Defining entities to match database tables

A very common practice among PHP developers is to create classes that represent database tables. Such classes are often referred to as **entity** classes, and form the core of the **domain model** software design pattern.

## How to do it...

1. First of all, we will establish some common features of a series of entity classes.
   These might include common properties and common methods. We will put these
   into a `Application\Entity\Base` class. All future entity classes will then extend
   Base.

2. For the purposes of this illustration, let’s assume all entities will have two properties in common: $mapping (discussed later), and $id (with its corresponding getter and setter):

```php
namespace Application\Entity;

class Base
{
    protected $id = 0;
    protected $mapping = ['id' => 'id'];

    public function getId() : int
    {
        return $this->id;
    }

    public function setId($id)
    {
        $this->id = (int) $id;
    }
}
```

3. It’s not a bad idea to define an arrayToEntity() method, which converts an array to an instance of the entity class, and vice versa (entityToArray()). These methods implement a process often referred to as hydration. As these methods should be generic, they are best placed in the Base class.

4. In the following methods, the $mapping property is used to translate between database column names and object property names. arrayToEntity() populates values of this object instance from an array. We can define this method as static in case we need to call it outside of an active instance:

```php
public static function arrayToEntity($data, Base $instance)
{
    if ($data && is_array($data)) {
        foreach ($instance->mapping as $dbColumn => $propertyName) {
            $method = 'set' . ucfirst($propertyName);
            $instance->$method($data[$dbColumn]);
        }
        return $instance;
    }
    return FALSE;
}
```

5. The `entityToArray()` produces an array from current instance property values:

```php
public function entityToArray()
{
    $data = array();
    foreach ($this->mapping as $dbColumn => $propertyName) {
        $method = 'get' . ucfirst($propertyName);
        $data[$dbColumn] = $this->$method() ?? NULL;
    }
    return $data;
}
```

6. To build the specific entity, you need to have the structure of the database table you plan to model at hand. Create properties that map to the database columns. The initial values assigned should reflect the ultimate data-type of the database column.

7. In this example we'll use the `customer` table. Here is the `CREATE` statement from a MySQL data dump, which illustrates its data structure:

```sql
CREATE TABLE `customer` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `name` varchar(256) CHARACTER SET latin1 COLLATE
 latin1_general_cs NOT NULL,
 `balance` decimal(10,2) NOT NULL,
 `email` varchar(250) NOT NULL,
 `password` char(16) NOT NULL,
 `status` int(10) unsigned NOT NULL DEFAULT '0',
 `security_question` varchar(250) DEFAULT NULL,
 `confirm_code` varchar(32) DEFAULT NULL,
 `profile_id` int(11) DEFAULT NULL,
 `level` char(3) NOT NULL,
 PRIMARY KEY (`id`),
 UNIQUE KEY `UNIQ_81398E09E7927C74` (`email`)
);
```

8. We are now in a position to flesh out the class properties. This is also a good place to identify the corresponding table. In this case, we will use a `TABLE_NAME` class constant:

```php
namespace Application\Entity;

class Customer extends Base
{
    const TABLE_NAME = 'customer';
    protected $name = '';
    protected $balance = 0.0;
    protected $email = '';
    protected $password = '';
    protected $status = '';
    protected $securityQuestion = '';
    protected $confirmCode = '';
    protected $profileId = 0;
    protected $level = '';
}
```

9. It is considered a best practice to define the properties as *protected*. In order to access these properties, you will need to design *public* methods that **get** and **set** the properties. Here is a good place to put to use the PHP 7 ability to data-type to the return value.

10. In the following block of code, we have defined getters and setters for $name and $balance. You can imagine how the remainder of these methods will be defined:

```php
public function getName() : string
{
    return $this->name;
}

public function setName($name)
{
    $this->name = $name;
}

public function getBalance() : float
{
    return $this->balance;
}

public function setBalance($balance)
{
    $this->balance = (float) $balance;
}
```

> It is not a good idea to data type check the incoming values on the setters. The reason is that the return values from a RDBMS database query will all be a *string* data type.

11. If the property names do not exactly match the corresponding database column, you should consider creating a mapping property, an array of key/value pairs where the key represents the database column name and the value the property name.
