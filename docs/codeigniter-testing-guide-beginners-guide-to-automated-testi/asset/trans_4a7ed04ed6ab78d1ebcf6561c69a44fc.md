

# 模型的单元测试

数据库类。事实上，`ci-phpunit-autoloader` 会加载类文件（因此我们不需要定义 `CI_DB` 类所扩展的 `CI_DB_query_builder` 类），但 `CI_DB` 类是由 Codeigniter 在一个函数（`DB()`）中定义的，我们并不调用它（因为它会尝试连接数据库）。

我们在此应用程序中使用 Query Builder，因此扩展了 `CI_DB_query_builder` 类。如果你没有使用 Query Builder，请扩展 `CI_DB_driver` 类。

如果你觉得这有点复杂，可以使用下面针对此特定练习的简化代码。真实的数据库类将在初始化期间初始化并连接到数据库，但这仅仅是连接。由于我们不会更改数据库中的任何数据，因此数据库状态保持不变，这不会影响我们的模型测试结果。然而，在未来的测试中情况就不如此了。

```
public function setUp()
{
    // 重置 Codeigniter 超对象
    $this->resetInstance();

    $this->obj = new News_model();
}
```

# 为 get_news 创建 Mock

现在，我们将为 `get_news()` 方法创建 mock。

```
$result_array = [ ... ];

// 为 CI_DB 创建 mock 对象
$db_result = $this->getMockBuilder('CI_DB_result')
    ->disableOriginalConstructor()
    ->getMock();
$db_result->method('result_array')->willReturn($result_array);

// 为 CI_DB 创建 mock 对象
$db = $this->getMockBuilder('CI_DB')
    ->disableOriginalConstructor()
    ->getMock();
$db->expects($this->once())
    ->method('get')
    ->with('news')
    ->willReturn($db_result);
```

# 模型的单元测试

我们首先定义 `$result_array`，它将由我们的 `CI_DB_result` mock 返回，然后我们构建 `CI_DB_result` mock，因为我们需要 `CI_DB` mock 返回。

在构建 mocks 时，我们添加了对 `disableOriginalConstructor()` 方法的调用。这禁用了原始构造函数。

`$db_result` 中的 `result_array()` 方法返回 `$result_array`。这允许按照代码期望的方式使用我们的 mock `CI_DB`。

mock `$db` 只能被调用一次，并将值 `'news'` 传递给 `get()` 方法，返回 mock `$db_result`。

```
$db->get('news');
```

# 编写测试方法

测试方法如下：

application/tests/models/News_model_with_mocks_test.php

```php
public function test_when_call_get_news_without_args_Then_get_items()
{
    $result_array = [
        "id" => "1",
        "title" => "News test",
        "slug" => "news-test",
        "text" => "News test",
    ],
    [
        "id" => "2",
        "title" => "News test 2",
        "slug" => "news-test-2",
        "text" => "News text 2",
    ];

    // 为 CI_DB_result 创建 mock 对象
    $db_result = $this->getMockBuilder('CI_DB_result')
        ->disableOriginalConstructor()
        ->getMock();
    $db_result->method('result_array')->willReturn($result_array);

    // 为 CI_DB 创建 mock 对象
    $db = $this->getMockBuilder('CI_DB')
        ->disableOriginalConstructor()
        ->getMock();
    $db->expects($this->once())
        ->method('get')
        ->with('news')
        ->willReturn($db_result);

    // 将 mock 对象注入到模型
    $this->obj->db = $db;

    $result = $this->obj->get_news();
    $this->assertEquals($result_array, $result);
}
```

**对于 Codeigniter 用户**

在这种情况下，你不需要调用 Codeigniter 的 `$load->model()` 方法。在创建 mocks 后，我们将 mock `$db` 对象注入到 `News_model` 对象的 `db` 属性中。这是依赖注入的形式。

```
// 将 mock 对象注入模型
$this->obj->db = $db;
```

运行 phpunit 命令并通过测试。

# 另一个 Mock

我们将添加另一个测试方法。这次我们将测试带参数的 `get_news()` 方法。创建必要的 mocks 代码如下：

$slug = '...';
$row_array = [ ... ];

// 为 CI_DB_result 创建 mock 对象
```php
$db_result = $this->getMockBuilder('CI_DB_result')
    ->disableOriginalConstructor()
    ->getMock();
$db_result->method('row_array')->willReturn($row_array);
```

// 为 CI_DB 创建 mock 对象
```php
$db = $this->getMockBuilder('CI_DB')
    ->disableOriginalConstructor()
    ->getMock();
$db->expects($this->once())
    ->method('get_where')
    ->with('news', ['slug' => $slug])
    ->willReturn($db_result);
```

在这种情况下，mock 对象预计被调用一次并返回 mock `$db_result`。

```php
$db->get_where('news', ['slug' => $slug]);
```

# 提取创建 mocks 方法

创建 mock 代码与之前的代码相同，因此我们将方法提取出来以便复用。

```php
/**
 * 为 CI_DB_result 创建 Mock 对象
 * @param string $method 要 mock 的方法
 * @param array $return 返回值
 * @return Mock_DB_result
 */
public function getMock_DB_result($method, $return)
{
    $db_result = $this->getMockBuilder('CI_DB_result')
        ->disableOriginalConstructor()
        ->getMock();
    $db_result->method($method)->willReturn($return);

    return $db_result;
}

/**
 * 为 CI_DB 创建 Mock 对象
 * @param string $method 要 mock 的方法
 * @param array $args 参数
 * @param array $return 返回值
 * @return Mock_DB
 */
public function getMock_DB($method, $args, $return)
{
    $db = $this->getMockBuilder('CI_DB')
        ->disableOriginalConstructor()
        ->getMock();
    $mocker = $db->expects($this->once())
        ->method($method);

    switch (count($args)) {
        case 1:
            $mocker->with($args[0]);
            break;
        case 2:
            $mocker->with($args[0], $args[1]);
            break;
        case 3:
            $mocker->with($args[0], $args[1], $args[2]);
            break;
        case 4:
            $mocker->with($args[0], $args[1], $args[2], $args[3]);
            break;
        default:
            break;
    }

    $mocker->willReturn($return);

    return $db;
}
```

# 编写另一个测试方法

整个测试方法如下：

application/tests/models/News_model_with_mocks_test.php

```php
public function test_When_call_get_news_with_slug_Then_get_item()
{
    $slug = 'news-test-2';
    $row_array = [
        "id" => "2",
        "title" => "News test 2",
        "slug" => "news-test-2",
        "text" => "News text 2",
    ];

    // 为 CI_DB_result 创建 mock 对象
    $db_result = $this->getMock_DB_result('row_array', $row_array);

    // 为 CI_DB 创建 mock 对象
    $db = $this->getMock_DB(
        'where', ['news', ['slug' => $slug]], $db_result
    );

    // 将 mock 对象注入模型
    $this->obj->db = $db;

    $item = $this->obj->get_news($slug);
    $this->assertEquals($row_array, $item);
}
```

现在，我们可以恢复之前的测试方法：

```
--- a/CodeIgniter/tests/models/News_model_with_mocks_test.php
+++ b/CodeIgniter/tests/models/News_model_with_mocks_test.php
@@ -28,19 +28,10 @@ class News_model_with_mocks_test extends TestCase
 };
```

```php
// 为 CI_DB_result 创建 mock 对象
    $db_result = $this->getMockBuilder('CI_DB_result')
    ->disableOriginalConstructor()
    ->getMock();
    $db_result->method('row_array')->willReturn($row_array);
```

// 为 CI_DB 创建 mock 对象
```php
    $db = $this->getMockBuilder('CI_DB')
    ->disableOriginalConstructor()
    ->getMock();
    $db->expects($this->once())
    ->method('get_where')
    ->with('news', ['slug' => $slug])
    ->willReturn($db_result);
```

