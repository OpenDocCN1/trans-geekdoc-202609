

## 2. 接下来，我们需要定义一个类 `Application\Database\Search\Engine`，并提供必要的类常量和属性。

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

## 3. 接下来，我们定义一组我们愿意支持的操作符。

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

## 4. 构造函数接受一个数据库连接实例作为参数。

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

## 5. 在构造函数之后，我们提供一系列有用的 getter 和 setter：

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

## 6. 最关键的方法可能是构建待准备的 SQL 语句的方法。

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

## 7. 现在核心 SELECT 已定义，我们移除末尾的 OR 关键字，并添加一个子句，使结果根据搜索列进行排序。

然后该语句被发送到数据库进行准备：

```php
    $this->sql = substr($this->sql, 0, -4)
        . ' ORDER BY ' . $this->mapping[$Criteria->key];
    $statement = $this->connection->pdo->prepare($this->sql);
    return $statement;
}
```

## 8. 现在我们要进入主要环节，即 search() 方法。

我们接受一个 `Application\Database\Search\Criteria` 对象作为参数。这确保了我们至少有一个项键和操作符。为了保险起见，我们添加了一个 `if()` 语句来检查这些属性：

```php
public function search(Criteria $Criteria)
{
    if (empty($Criteria->key) || empty($Criteria->operator)) {
        yield ['error' => self::ERROR_INVALID];
        return FALSE;
    }
```

## 9. 然后我们调用 prepareStatement()，并使用 try / catch 来捕获错误：

```php
    try {
        if (!$statement = $this->prepareStatement($Criteria)) {
            yield ['error' => self::ERROR_PREPARE];
            return FALSE;
        }
```

## 10. 接下来我们构建一个将提供给 execute() 的参数数组。

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

## 11. 语句被执行，并使用 `yield` 关键字返回结果，这实际上使该方法变成了一个生成器：

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

# 工作原理...

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

```php
$dbCols = [
    'cname' => 'Customer Name',
    'cbal' => 'Account Balance',
    'cmail' => 'Email Address',
    'clevel' => 'Level'
];

$mapping = [
    'cname' => 'name',
    'cbal' => 'balance',
    'cmail' => 'email',
    'clevel' => 'level'
];
```

现在你可以设置数据库连接并创建搜索引擎实例：

```php
$conn = new Connection(include __DIR__, DB_CONFIG_FILE);
$engine = new Engine($conn, 'customer', $dbCols, $mapping);
```

为了显示适当的下拉 SELECT 元素，我们基于 `Application\Form\*` 类定义包装器和元素：

```php
$wrappers = [
    Generic::INPUT => ['type' => 'td', 'class' => 'content'],
    Generic::LABEL => ['type' => 'th', 'class' => 'label'],
    Generic::ERRORS => ['type' => 'td', 'class' => 'error']
];

// define elements
$fieldElement = new Select('field',
                        Generic::TYPE_SELECT,
                        'Field',
                        $wrappers,
                        ['id' => 'field']);
$opsElement = new Select('ops',
                        Generic::TYPE_SELECT,
                        'Operators',
                        $wrappers,
                        ['id' => 'ops']);
$itemElement = new Generic('item',
                        Generic::TYPE_TEXT,
                        'Searching For ...',
                        $wrappers,
                        ['id' => 'item','title' => 'If more than one item,
                         separate with commas']);
$submitElement = new Generic('submit',
                            Generic::TYPE_SUBMIT,
                            'Search',
                            $wrappers,
                            ['id' => 'submit','title' => 'Click to Search',
                             'value' => 'Search']);
```

![](img/39390f6d56c5a83b28db083a8bd5185c_404_0.png)

