
## 使用特质和接口

将接口作为建立一组类分类的手段并保证某些方法存在的存在，被认为是一种最佳实践。特质和接口通常协同工作，是实现中的一个重要方面。每当有一个经常使用且定义了代码不变的方法（例如 setter 或 getter）的接口时，定义一个包含实际代码实现的 Trait 也是有用的。

### 如何实现...

- 1. 在本示例中，我们将使用第 4 章 *使用 PHP 面向对象编程* 中首次介绍的 `ConnectionAwareInterface`。该接口定义了一个 `setConnection()` 方法，用于设置 `$connection` 属性。`Application\Generic` 命名空间中的两个类 `CountryList` 和 `CustomerList` 包含冗余代码，这些代码与接口中定义的方法相匹配。

- 2. 以下是变更前的 `CountryList` 的样子：

```php
class CountryList
{
    protected $connection;
    protected $key    = 'iso3';
    protected $value  = 'name';
    protected $table  = 'iso_country_codes';

    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }

    public function list()
    {
        $list = [];
        $sql = sprintf('SELECT %s,%s FROM %s', $this->key,
                $this->value, $this->table);
        $stmt = $this->connection->pdo->query($sql);
        while ($item = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$item[$this->key]] =  $item[$this->value];
        }
        return $list;
    }
}
```

- 3. 现在我们将 `list()` 移动到一个名为 `ListTrait` 的特性中：

```php
trait ListTrait
{
    public function list()
    {
        $list = [];
        $sql = sprintf('SELECT %s,%s FROM %s',
                       $this->key, $this->value, $this->table);
        $stmt = $this->connection->pdo->query($sql);
        while ($item = $stmt->fetch(PDO::FETCH_ASSOC)) {
            $list[$item[$this->key]] = $item[$this->value];
        }
        return $list;
    }
}
```

- 4. 然后，我们可以将 `ListTrait` 中的代码插入到一个新类 `CountryListUsingTrait` 中，如下所示：

```php
class CountryListUsingTrait
{
    use ListTrait;
    protected $connection;
    protected $key = 'iso3';
    protected $value = 'name';
    protected $table = 'iso_country_codes';
    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

- 5. 接下来，我们观察到许多类都需要设置一个连接实例。同样，这也需要用到特性。不过，这次我们将该特性放在 `Application\Database` 命名空间中。以下是新的特性：

```php
namespace Application\Database;
trait ConnectionTrait
{
    protected $connection;
    public function setConnection(Connection $connection)
    {
        $this->connection = $connection;
    }
}
```

- 6. **特性常用于避免代码重复。** 通常你也需要识别使用特性的类。实现这一目标的一个好方法是开发一个与特性相匹配的接口。在本例中，我们将定义 `Application\Database\ConnectionAwareInterface`：

```php
namespace Application\Database;
use Application\Database\Connection;
interface ConnectionAwareInterface
{
    public function setConnection(Connection $connection);
}
```

- 7. **以下是修订后的 `CountryListUsingTrait` 类。** 请注意，由于新特性受其命名空间位置的影响，我们需要在类顶部添加一个 `use` 语句。你还会注意到，我们实现了 `ConnectionAwareInterface` 以表明该类需要特性中定义的方法。请注意，我们正在利用新的 PHP 7 分组 `use` 语法：

```php
namespace Application\Generic;
use PDO;
use Application\Database\ {
    Connection, ConnectionTrait, ConnectionAwareInterface
};
class CountryListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;
    use ConnectionTrait;
    protected $key     = 'iso3';
    protected $value  = 'name';
    protected $table  = 'iso_country_codes';
}
```

## 工作原理...

首先，确保在 *第 4 章，使用 PHP 面向对象编程* 中开发的类已创建。这些类包括在 *第 4 章，使用 PHP 面向对象编程* 的 *使用接口* 配方中讨论的 `Application\Generic\CountryList` 和 `Application\Generic\CustomerList` 类。将每个类保存在 `Application\Generic` 文件夹中的新文件 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 中。请务必更改类名以匹配新文件名！

如步骤 3 所述，从 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 列表类中移除 `list()` 方法，并添加 `use ListTrait;` 以替代被移除的方法。将移除的代码放入同一文件夹中名为 `ListTrait.php` 的单独文件中。

你还会注意到两个列表类之间存在更多的代码重复，在这种情况下是 `setConnection()` 方法。这又需要另一个特性！

从 `CountryListUsingTrait.php` 和 `CustomerListUsingTrait.php` 列表类中剪切 `setConnection()` 方法，并将移除的代码放入名为 `ConnectTrait.php` 的单独文件中。由于该特性在逻辑上与 `ConnectionAwareInterface` 和 `Connection` 相关，因此将其文件放在 `Application\Database` 文件夹中并相应地指定其命名空间是合理的。

最后，如步骤 6 所述定义 `Application\Database\ConnectionAwareInterface`。以下是所有更改后的最终 `Application\Generic\CustomerListUsingTrait` 类：

```php
<?php
namespace Application\Generic;
use PDO;
use Application\Database\Connection;
use Application\Database\ConnectTrait;
use Application\Database\ConnectionAwareInterface;
class CustomerListUsingTrait implements ConnectionAwareInterface
{
    use ListTrait;
    use ConnectTrait;

    protected $key = 'id';
    protected $value = 'name';
    protected $table = 'customer';
}
```

现在你可以将第 4 章 *使用 PHP 面向对象编程* 中提到的 `chap_04_op_simple_interfaces_example.php` 文件复制到名为 `chap_13_trait_and_interface.php` 的新文件中。将 `CountryList` 的引用更改为 `CountryListUsingTrait`。同样，将 `CustomerList` 的引用更改为 `CustomerListUsingTrait`。其他代码可以保持不变：

```php
<?php
define('DB_CONFIG_FILE', './../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');
$parms = include __DIR__ . DB_CONFIG_FILE;
try {
    $list = Application\Generic\ListFactory::factory(
        new Application\Generic\CountryListUsingTrait(), $parms);
    echo 'Country List' . PHP_EOL;
    foreach ($list->list() as $item) echo $item . ' ';
    $list = Application\Generic\ListFactory::factory(
        new Application\Generic\CustomerListUsingTrait(),
        $parms);
    echo 'Customer List' . PHP_EOL;
    foreach ($list->list() as $item) echo $item . ' ';
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

输出将与第 4 章 *使用面向对象编程* 的 *使用接口* 配方中描述的完全一致。你可以在下面的截图中看到输出中的国家列表部分：

![](img/39390f6d56c5a83b28db083a8bd5185c_510_0.png)

下一张图片显示了输出中的客户列表部分：

![](img/39390f6d56c5a83b28db083a8bd5185c_511_0.png)

## 通用异常处理器

异常在结合 `try`/`catch` 块中的代码使用时特别有用。然而，在某些情况下使用这种结构可能会很尴尬，使代码几乎无法阅读。另一个考虑因素是，许多类最终会抛出你未预见的异常。在这种情况下，拥有某种备用异常处理器将非常理想。

### 如何实现...

- 1. 首先，我们定义一个通用的异常处理类 `Application\Error\Handler`：

```php
namespace Application\Error;
class Handler
{
    // 代码在此处
}
```

- 2. 我们定义代表日志文件的属性。如果未提供名称，则按年、月和日命名。在构造函数中，我们使用 `set_exception_handler()` 将本类中的 `exceptionHandler()` 方法指定为备用处理器：

```php
protected $logFile;
public function __construct(
    $logFileDir = NULL, $logFile = NULL)
```
