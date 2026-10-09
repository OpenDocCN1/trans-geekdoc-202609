# **Using anonymous classes as mock objects**

+   1. A nice variation on mock objects involves the use of the new PHP 7 anonymous class in place of creating a formal class that defines mock functionality. The advantage of using an anonymous class is that you can extend an existing class, which makes the object appear legitimate. This approach is especially useful if you only need to override one or two methods.

+   2. For this illustration, we will modify `VisitorServiceTest.php` presented previously, calling it `VisitorServiceTestAnonClass.php`:

```
<?php
use PHPUnit\Framework\TestCase;
require_once __DIR__ . '/VisitorService.php';
require_once __DIR__ . '/VisitorOps.php';
class VisitorServiceTestAnonClass extends TestCase
{
    protected $visitorService;
    protected $dbConfig = [
        'driver'   => 'mysql',
        'host'     => 'localhost',
        'dbname'   => 'php7cookbook_test',
        'user'     => 'cook',
        'password' => 'book',
        'errmode'  => PDO::ERRMODE_EXCEPTION,
    ];
    protected $testData;
```

+   3. You will notice that in `setup()`, we define an anonymous class that extends `VisitorOps`. We only need to override the `findAll()` method:

```
public function setup()
{
    $data = array();
    for ($x = 1; $x <= 3; $x++) {
        $data[$x]['id'] = $x;
        $data[$x]['email'] = $x . 'test@unlikelysource.com';
        $data[$x]['visit_date'] =
            '2000-0' . $x . '-0' . $x . ' 00:00:00';
        $data[$x]['comments'] = 'TEST ' . $x;
        $data[$x]['name'] = 'TEST ' . $x;
    }
    
    $this->testData = $data;
    $this->visitorService =
        new VisitorService($this->dbConfig);
    
    $ops$Mock =
        new class ($this->testData) extends VisitorOps {
```