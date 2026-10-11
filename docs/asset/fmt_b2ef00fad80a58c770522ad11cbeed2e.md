
### 3. 然后将键提取到另一个数组 `$binary` 中，以便基于数字键执行二分排序。接着调用 `doBinarySearch()`，这会返回中间数组 `$search` 中的一个键，或者布尔值 `FALSE`：

```php
$binary = array_keys($search);
$result = $this->doBinarySearch($binary, $item);
return $this->primary[$search[$result]] ?? FALSE;
```

### 4. 第一个 `doBinarySearch()` 初始化了一系列参数。`$iterations`、`$found`、`$loop`、`$done` 和 `$max` 都用于防止无限循环。`$upper` 和 `$lower` 代表要检查的列表切片：

```php
public function doBinarySearch($binary, $item)
{
    $iterations = 0;
    $found = FALSE;
    $loop = TRUE;
    $done = -1;
    $max = count($binary);
    $lower = 0;
    $upper = $max - 1;
}
```

### 5. 然后实现一个 `while()` 循环并设置中点：

```php
while ($loop && !$found) {
    $mid = (int) (($upper - $lower) / 2) + $lower;
}
```

### 6. 现在可以使用新的 PHP 7 **太空船运算符**，它在单次比较中给出了小于、等于或大于的结果。如果小于，将上限设置为中点。如果大于，将下限调整为中点。如果相等，我们就完成了，安然脱身：

```php
switch ($item <=> $binary[$mid]) {
    // $item < $binary[$mid]
    case -1 :
        $upper = $mid;
        break;
    // $item == $binary[$mid]
    case 0 :
        $found = $binary[$mid];
        break;
    // $item > $binary[$mid]
    case 1 :
    default :
        $lower = $mid;
}
```

### 7. 现在进行一点循环控制。我们增加迭代次数，并确保其不超过列表的大小。如果是这样，肯定出了问题，我们需要退出。否则，我们检查上下限是否连续两次以上相同，如果是这样，则未找到搜索项。然后存储迭代次数并返回找到的（或未找到的）结果：

```php
$loop = (($iterations++ < $max) && ($done < 1));
$done += ($upper == $lower) ? 1 : 0;
}
$this->iterations = $iterations;
return $found;
```

## 工作原理...

首先，实现 `Application\Generic\Search` 类，定义本食谱中描述的方法。接下来，定义一个调用程序 `chap_10_binary_search.php`，设置自动加载并读取 `customer.csv` 文件作为搜索目标（如上一个食谱中所述）：

```php
<?php
define('CUSTOMER_FILE', __DIR__ . '/../data/files/customer.csv');
include __DIR__ . '/chap_10_linked_list_include.php';
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '../');

use Application\Generic\Search;
$headers = array();
$customer = readCsv(CUSTOMER_FILE, $headers);
```

然后你可以创建一个新的 `Search` 实例，并指定列表中间某处的一项。在这个示例中，搜索基于第 1 列（客户姓名），搜索项是 Todd Lindsey：

```php
$search = new Search($customer);
$item = 'Todd Lindsey';
$cols = [1];
echo "Searching For: $item\n";
var_dump($search->binarySearch($cols, $item));
```

为了说明，在 `Application\Generic\Search::doBinarySearch()` 中的 `switch()` 之前添加这一行：

```php
echo "Upper:Mid:Lower:<=> | " . $upper . ':' . $mid . ':' .
     $lower . ':' . ($item <=> $binary[$mid]);
```

输出显示如下。注意上限、中点和下限是如何调整直到找到项目的：

```text
Searching For: Todd Lindsey
Upper:Mid:Lower:<=> | 81:40:8:1
Upper:Mid:Lower:<=> | 81:60:40:1
Upper:Mid:Lower:<=> | 81:70:60:1
Upper:Mid:Lower:<=> | 81:75:70:1
Upper:Mid:Lower:<=> | 81:78:75:0
array(18) {
  [0]=>
  string(2) "58"
  [1]=>
  string(12) "Todd Lindsey"
  [2]=>
  string(5) "48.91"
  [3]=>
  string(24) "todd.lindsey@fastnet.net"
  [4]=>
  string(16) "an2O73Conscience"
  [5]=>
  string(1) "1"
  [6]=>
  string(0) ""
  [7]=>
  string(0) ""
  [8]=>
  string(0) ""
}
```

### 参见

有关二分查找的更多信息，维基百科上有一篇很棒的文章，详细讲解了基本数学原理，链接如下：https://en.wikipedia.org/wiki/Binary_search_algorithm。

## 实现搜索引擎

为了实现搜索引擎，我们需要为在搜索中包含多列做准备。此外，重要的是要认识到，搜索项可能位于字段的中间，而且用户很少会提供足够的信息来进行精确匹配。因此，我们将大量依赖 SQL LIKE `$value` 子句。

### 实现步骤...

1. 首先，我们定义一个基本类来保存搜索条件。该对象包含三个属性：键（最终代表数据库列）、运算符（LIKE、<、> 等）；以及可选的项目。项目可选的原因是，某些运算符，如 IS NOT NULL，不需要具体数据：

```php
namespace Application\Database\Search;

class Criteria
{
    public $key;
    public $item;
}
```

### 2. 接下来，我们需要定义一个类 `Application\Database\Search\Engine`，并提供必要的类常量和属性。

`$columns` 和 `$mapping` 之间的区别在于，`$columns` 保存最终将出现在 HTML SELECT 字段（或等效字段）中的信息。出于安全原因，我们不希望暴露数据库列的实际名称，因此需要另一个数组 `$mapping`：

```php
namespace Application\Database\Search;
use PDO;
use Application\Database\Connection;
class Engine
{
    const ERROR_PREPARE = 'ERROR: unable to prepare statement';
    const ERROR_EXECUTE = 'ERROR: unable to execute statement';
    const ERROR_COLUMN = 'ERROR: column name not on list';
    const ERROR_OPERATOR = 'ERROR: operator not on list';
    const ERROR_INVALID = 'ERROR: invalid search criteria';

    protected $connection;
    protected $table;
    protected $columns;
    protected $mapping;
    protected $statement;
    protected $sql = '';
```

### 3. 接下来，我们定义一组我们愿意支持的操作符。

键代表实际的 SQL。值是将在表单中显示的内容：

```php
protected $operators = [
    'LIKE' => 'Equals',
    '<' => 'Less Than',
    '>' => 'Greater Than',
    '<>' => 'Not Equals',
    'NOT NULL' => 'Exists',
];
```

### 4. 构造函数接受一个数据库连接实例作为参数。

为了我们的目的，我们将使用在*第 5 章，与数据库交互*中定义的 `Application\Database\Connection`。我们还需要提供数据库表的名称，以及 `$columns`，这是一个任意列键和标签的数组，这些标签将出现在 HTML 表单中。这将引用 `$mapping`，其中键与 `$columns` 匹配，但值代表实际的数据库列名：

```php
public function __construct(Connection $connection, 
                           $table, array $columns, array $mapping)
{
    $this->connection  = $connection;
    $this->setTable($table);
    $this->setColumns($columns);
    $this->setMapping($mapping);
}
```

### 5. 在构造函数之后，我们提供一系列有用的 getter 和 setter：

```php
public function setColumns($columns)
{
    $this->columns = $columns;
}

public function getColumns()
{
    return $this->columns;
}

// etc.
```

### 6. 最关键的方法可能是构建待准备的 SQL 语句的方法。

在初始 SELECT 设置之后，我们添加 WHERE 子句，使用 `$mapping` 添加实际的数据库列名。然后我们添加操作符并实现 `switch()`，根据操作符，可能会或不会添加一个命名占位符，该占位符将代表搜索项：

```php
public function prepareStatement(Criteria $criteria)
{
    $this->sql = 'SELECT * FROM ' . $this->table . ' WHERE ';
    $this->sql .= $this->mapping[$criteria->key] . ' ';
    switch ($criteria->operator) {
        case 'NOT NULL' :
            $this->sql .= ' IS NOT NULL OR ';
            break;
        default :
            $this->sql .= $criteria->operator . ' ';
            $this->sql .= $this->mapping[$criteria->key] . ' OR ';
    }
```

### 7. 现在核心 SELECT 已定义，我们移除末尾的 OR 关键字，并添加一个子句，使结果根据搜索列进行排序。

然后该语句被发送到数据库进行准备：

```php
    $this->sql = substr($this->sql, 0, -4)
        . ' ORDER BY ' . $this->mapping[$Criteria->key];
    $statement = $this->connection->pdo->prepare($this->sql);
    return $statement;
}
```

### 8. 现在我们要进入主要环节，即 search() 方法。

我们接受一个 `Application\Database\Search\Criteria` 对象作为参数。这确保了我们至少有一个项键和操作符。为了保险起见，我们添加了一个 `if()` 语句来检查这些属性：

```php
public function search(Criteria $Criteria)
{
    if (empty($Criteria->key) || empty($Criteria->operator)) {
        yield ['error' => self::ERROR_INVALID];
        return FALSE;
    }
```

### 9. 然后我们调用 prepareStatement()，并使用 try / catch 来捕获错误：

```php
    try {
        if (!$statement = $this->prepareStatement($Criteria)) {
            yield ['error' => self::ERROR_PREPARE];
            return FALSE;
        }
```

### 10. 接下来我们构建一个将提供给 execute() 的参数数组。

键代表在准备语句中用作占位符的数据库列名。注意，我们没有使用 `=`，而是使用了 `LIKE $value$` 构造：

```php
    $params = array();
    switch ($Criteria->operator) {
        case 'NOT NULL' :
            // do nothing; already in statement
            break;
        case 'LIKE' :
            $params[$this->mapping[$Criteria->key]] =
                '%' . $Criteria->item . '%';
            break;
        default :
            $params[$this->mapping[$Criteria->key]] =
                $Criteria->item;
    }
```

### 11. 语句被执行，并使用 `yield` 关键字返回结果，这实际上使该方法变成了一个生成器：

```php
    $statement->execute($params);
    while ($row = $statement->fetch(PDO::FETCH_ASSOC)) {
        yield $row;
    }
    } catch (\Throwable $e) {
        error_log(__METHOD__ . ':' . $e->getMessage());
        throw new Exception(self::ERROR_EXECUTE);
    }
    return TRUE;
}
```

## 工作原理...

将本食谱中讨论的代码放置在 `Application\Database\Search` 下的 `Criteria.php` 和 `Engine.php` 文件中。然后你可以定义一个调用脚本 `chap_10_search_engine.php`，该脚本设置自动加载。你可以利用*第 5 章，与数据库交互*中讨论的 `Application\Database\Connection` 类，以及*第 6 章，构建可扩展网站*中涵盖的表单元素类：

```php
<?php
define('DB_CONFIG_FILE', '/../config/db.config.php');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . '/../');

use Application\Database\Connection;
use Application\Database\Search\{ Engine, Criteria };
use Application\Form\Generic;
use Application\Form\Element\Select;
```

现在你可以定义哪些数据库列将出现在表单中，以及一个匹配的映射文件：
