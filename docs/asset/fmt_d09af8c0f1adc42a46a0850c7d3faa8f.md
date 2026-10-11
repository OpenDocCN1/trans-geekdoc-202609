
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

现在你只需要设置表单操作并将匿名函数包装在 HTML 中：

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

为了测试它，你可以使用内置的 PHP web 服务器，但你必须使用 `-t` 标志来指示文档根目录是 `public`：

```bash
cd /path/to/source/for/this/chapter
php -S localhost:8080 -t public
```

你可以从浏览器访问 `http://localhost:8080/` URL。

如果你尝试访问任何页面，你会被重定向回登录页面。根据配置，`status = 1` 且 `level = BEG` 的用户只能访问页面 1 并注销。如果你以该用户身份登录并尝试访问页面 2，输出如下：

![](img/39390f6d56c5a83b28db083a8bd5185c_344_0.png)

## 参见

此示例依赖 `$_SESSION` 作为用户登录后的唯一用户身份验证方式。关于如何保护 PHP 会话的优秀示例，请参见**第十二章，提升 web 安全性**，特别是名为*保护 PHP 会话*的食谱。

## 使用缓存提高性能

缓存软件设计模式是指存储生成耗时较长的结果。这可能表现为冗长的视图脚本或复杂的数据库查询。如果你希望改善网站访问者的用户体验，存储目标当然需要具有高性能。由于不同的安装环境会有不同的潜在存储目标，缓存机制也适合适配器模式。潜在存储目标的示例包括内存、数据库和文件系统。

### 如何实现...

1. 与本章节中的其他几个食谱一样，由于存在共享常量，我们定义了一个离散的 `Application\Cache\Constants` 类：

```php
<?php
namespace Application\Cache;

class Constants
{
    const DEFAULT_GROUP   = 'default';
    const DEFAULT_PREFIX  = 'CACHE_';
    const DEFAULT_SUFFIX  = '.cache';
    const ERROR_GET      = 'ERROR: unable to retrieve from cache';
    // 并非显示所有常量以节省空间
}
```

2. 由于我们正在遵循适配器设计模式，接下来定义一个接口：

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

3. 现在，我们准备好定义第一个缓存适配器，在本例中，通过使用 MySQL 数据库。我们需要定义将持有列名以及预编译语句的属性：

```php
namespace Application\Cache;
use PDO;
use Application\Database\Connection;
```

4. 构造函数允许我们提供键列名以及 `Application\Database\Connection` 实例和用于缓存的表名：

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

5. 接下来的几个方法准备预编译语句，并在我们访问数据库时调用。我们不显示所有方法，但提供足够的信息让你了解其思路：

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

### 第9章

```php
$sql = 'SELECT `' . $this->dataColumnName . '`'
    . ' FROM `' . $this->table . '`'
    . ' WHERE `' . $this->keyColumnName . '` = :key'
    . ' AND `' . $this->groupColumnName . '` = :group';
$this->sql[_METHOD_] = $sql;
$this->statementGetFromCache =
    $this->connection->pdo->prepare($sql);
```

6. 现在我们定义一个方法，用于判断给定键的数据是否存在：

```php
public function hasKey($key)
{
    $result = 0;
    try {
        if (!$this->statementHasKey) $this->prepareHasKey();
        $this->statementHasKey->execute(['key' => $key]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_KEY);
    }
    return (int) $this->statementHasKey
        ->fetch(PDO::FETCH_ASSOC)[$this->idColumnName];
}
```

7. 核心方法是从缓存中读取和写入数据的方法。以下是从缓存中检索数据的方法。我们只需要执行预编译语句，该语句执行带有 WHERE 子句的 SELECT，其中包含键和组：

```php
public function getFromCache(
    $key, $group = Constants::DEFAULT_GROUP)
{
    try {
        if (!$this->statementGetFromCache)
            $this->prepareGetFromCache();
        $this->statementGetFromCache->execute(
            ['key' => $key, 'group' => $group]);
        while ($row = $this->statementGetFromCache
            ->fetch(PDO::FETCH_ASSOC)) {
            if ($row && count($row)) {
                yield unserialize($row[$this->dataColumnName]);
            }
        }
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_GET);
    }
}
```

8. 在写入缓存时，我们首先判断该缓存键是否存在条目。如果存在，我们执行 UPDATE；否则，我们执行 INSERT：

```php
public function saveToCache($key, $data,
$group = Constants::DEFAULT_GROUP)
{
    $id = $this->hasKey($key);
    $result = 0;
    try {
        if ($id) {
            if (!$this->statementUpdateCache)
                $this->prepareUpdateCache();
            $result = $this->statementUpdateCache
                ->execute(['key' => $key,
                'data' => serialize($data),
                'group' => $group,
                'id' => $id]);
        } else {
            if (!$this->statementSaveToCache)
                $this->prepareSaveToCache();
            $result = $this->statementSaveToCache
                ->execute(['key' => $key,
                'data' => serialize($data),
                'group' => $group]);
        }
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_SAVE);
    }
    return $result;
}
```

9. 然后我们定义两个方法，分别按键或按组删除缓存。按组删除提供了一种便捷的机制，适用于需要删除大量项目的情况：

```php
public function removeByKey($key)
{
    $result = 0;
    try {
        if (!$this->statementRemoveByKey)
            $this->prepareRemoveByKey();
        $result = $this->statementRemoveByKey->execute(
            ['key' => $key]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_KEY);
    }
    return $result;
}

public function removeByGroup($group)
{
    $result = 0;
    try {
        if (!$this->statementRemoveByGroup)
            $this->prepareRemoveByGroup();
        $result = $this->statementRemoveByGroup->execute(
            ['group' => $group]);
    } catch (Throwable $e) {
        error_log(__METHOD__ . ': ' . $e->getMessage());
        throw new Exception(Constants::ERROR_REMOVE_GROUP);
    }
    return $result;
}
```

10. 最后，我们为每个属性定义 getter 和 setter。此处未全部展示以节省空间：

```php
public function setTable($name)
{
    $this->table = $name;
}

public function getTable()
{
    return $this->table;
}
// 等等。
```

11. 文件系统缓存适配器定义了与之前相同的方法。请注意使用 `md5()`，并非出于安全目的，而是作为一种快速从键生成文本字符串的方式：
