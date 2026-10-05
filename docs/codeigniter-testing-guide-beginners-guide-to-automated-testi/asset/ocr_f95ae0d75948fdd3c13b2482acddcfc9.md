# Unit Testing for Models

database classes. In fact, the ci-phpunit-autoloader loads class files (so we don't have to define the CI_DB_query_builder class our CI_DB class is extending), but the CI_DB class is defined by Codeigniter in a function (DB()), which we aren't going to call (since it would try to connect to the database).

We use Query Builder in this application, so we extended the CI_DB_query_builder class. If you don't use Query Builder, extend the CI_DB_driver class, instead.

If you find this a little complicated, you can use the simplified code below for this particular exercise. The real database classes will be initialized and connect to the database during initialization, but it is just connecting. Since we will not change any data in the database, the database state is the same, and it does not affect our model testing results. However, this will not be the case in future tests.

```
public function setUp()
    // Reset Codeigniter super object
    $this->resetInstance();

    $this->obj = new News_model();
}
```

# Creating Mocks for get_news

Now, we will create mocks for the get_news() method.

```
$result_array = [ ... ];

// Create mock object for CI_DB
$db_result = $this->getMockBuilder('CI_DB_result')
    ->disableOriginalConstructor()
    ->getMock();
$db_result->method('result_array')->willReturn($result_array);

// Create mock object for CI_DB
$db = $this->getMockBuilder('CI_DB')
    ->disableOriginalConstructor()
    ->getMock();
$db->expects($this->once())
    ->method('get')
    ->with('news')
    ->willReturn($db_result);
```