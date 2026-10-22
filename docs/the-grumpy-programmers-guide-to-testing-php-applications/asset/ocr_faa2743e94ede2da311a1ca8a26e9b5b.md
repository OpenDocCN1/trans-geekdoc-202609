because creating a dependency without a type will likely cause PHP to complain. If you are using older codebases where types are not being used, you can create a dummy by using PHP’s built-in stdClass object.

So let’s say you are writing a test that needs to use this particular bit of code:

```
```php
1. class Roster
2. {
3.   public $_db;
4.   public $pdo;
5.   public $previous_season;
6.   public $current_season;
7.
8.   /**
9.    * Constructor for class
10.   *
11.   * @param Aura\SqlQuery\QueryFactory $db
12.   */
13.   public function __construct($db)
14.   {
15.     $this->_db = $db;
16.     $this->pdo = new PDO(
17.       'pgsql:host=localhost;dbname=user=;password=' );
18.   }
19.
20.   // Other code snipped out
21. }
```
```

But your test doesn’t need to do anything with it. You’d be okay creating a dummy without a type to satisfy the condition of needing “a RosterModel object.”

```
```php
// Create a dummy of our database and pass it to our Roster model
$db = new stdClass();
$rm = new Roster($db);
```
```

# Test Stub

In our world of typed PHP code, the dummy will get upgraded to the test stub. Again, using Wikipedia as our guide, we get the following definition:

> > "used for providing the tested code with ‘indirect input.’"