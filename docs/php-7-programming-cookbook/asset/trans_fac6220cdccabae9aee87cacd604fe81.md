
16. 正如在本食谱开头所述，我们用于假数据生成的数据源会有所不同。在某些情况下，如前几步所示，我们使用种子数组来构建假数据。在其他情况下，我们可能希望使用文本文件或 CSV 文件作为数据源。以下是此类方法的示例：

```php
public function getEntryFromFile($name, $type)
{
	if (empty($this->files[$name])) {
		$this->pullFileData($name, $type);
	}
	return $this->files[$name][
		random_int(0, count($this->files[$name]) - 1)
	];
}
```

17. 你会注意到，我们首先需要将文件数据拉入一个数组，该数组构成了返回值。以下是执行此操作的方法。如果指定的文件未找到，我们会抛出一个异常。文件类型被识别为我们类常量之一：`FILE_TYPE_TEXT` 或 `FILE_TYPE_CSV`。根据类型，我们使用 `fgetcsv()` 或 `fgets()`：

```php
public function pullFileData($name, $type)
{
	if (!file_exists($name)) {
		throw new Exception(self::ERROR_FILE);
	}
	$fileObj = new SplFileObject($name, 'r');
	if ($type === self::FILE_TYPE_CSV) {
		while (($data = $fileObj->fgetcsv()) !== false) {
			$this->files[$name][] = trim($data[0]);
		}
	} else {
		while (($data = $fileObj->fgets()) !== false) {
			$this->files[$name][] = trim($data);
		}
	}
}
```

18. 该过程中可能最复杂的方面是从数据库表中提取随机数据。我们接受的参数包括表名、构成主键的列名，以及一个映射数据库查找表中列名与目标列名之间关系的数组：

```php
public function getEntryFromTable($tableName, $idColumn, $mapping)
{
	$entry = array();
	try {
		if (empty($this->tables[$tableName])) {
			$sql = 'SELECT ' . $idColumn . ' FROM ' . $tableName . ' ORDER BY ' . $idColumn . ' ASC LIMIT 1';
			$stmt = $this->connection->pdo->query($sql);
			$this->tables[$tableName]['first'] = $stmt->fetchColumn();
			
			$sql = 'SELECT ' . $idColumn . ' FROM ' . $tableName . ' ORDER BY ' . $idColumn . ' DESC LIMIT 1';
			$stmt = $this->connection->pdo->query($sql);
			$this->tables[$tableName]['last'] = $stmt->fetchColumn();
		}

		// Step 19 content continues here
		$result = FALSE;
		$count = self::MAX_LOOKUPS;
		$sql = 'SELECT * FROM ' . $tableName . ' WHERE ' . $idColumn . ' = ?';
		$stmt = $this->connection->pdo->prepare($sql);

		// Step 20 content continues here
		do {
			$id = random_int($this->tables[$tableName]['first'], $this->tables[$tableName]['last']);
			$stmt->execute([$id]);
			$result = $stmt->fetch(PDO::FETCH_ASSOC);
		} while ($count-- && !$result);
		
		if (!$result) {
			error_log(__METHOD__ . ':' . self::ERROR_LOOKUP);
			throw new Exception(self::ERROR_LOOKUP);
		}
	} catch (PDOException $e) {
		error_log(__METHOD__ . ':' . $e->getMessage());
		throw new Exception(self::ERROR_DB);
	}

	// Step 21 content continues here
	foreach ($mapping as $key => $value) {
		$entry[$value] = $result[$key] ?? NULL;
	}
	return $entry;
}
```

19. 现在，我们已具备设置预编译语句并初始化若干关键变量的条件：

```php
$result = FALSE;
$count = self::MAX_LOOKUPS;
$sql = 'SELECT * FROM ' . $tableName . ' WHERE ' . $idColumn . ' = ?';
$stmt = $this->connection->pdo->prepare($sql);
```

20. 实际的查找过程放置在 do...while 循环中。这样做的原因是我们需要至少执行一次查询才能获得结果。只有在我们未得到结果时，才继续循环。我们在最低 ID 和最高 ID 之间生成一个随机数，然后在查询参数中使用该数字。请注意，我们还递减一个计数器以防止无限循环。这是因为如果 ID 不是连续的，我们可能会意外生成一个不存在的 ID。如果我们超过最大尝试次数且仍然没有结果，则抛出异常：

```php
do {
	$id = random_int($this->tables[$tableName]['first'], $this->tables[$tableName]['last']);
	$stmt->execute([$id]);
	$result = $stmt->fetch(PDO::FETCH_ASSOC);
} while ($count-- && !$result);
if (!$result) {
	error_log(__METHOD__ . ':' . self::ERROR_LOOKUP);
	throw new Exception(self::ERROR_LOOKUP);
}
```

注意：包裹此逻辑的 try-catch 块在第 21 步末尾闭合。

21. 然后，我们使用映射数组从源表中检索值，使用在目标表中期望的键：

```php
} catch (PDOException $e) {
	error_log(__METHOD__ . ':' . $e->getMessage());
	throw new Exception(self::ERROR_DB);
}
foreach ($mapping as $key => $value) {
	$entry[$value] = $result[$key] ?? NULL;
}
return $entry;
}
```

22. 这个类的核心是 `getRandomEntry()` 方法，它生成单个假数据数组。我们逐个遍历 `$mapping` 中的条目，并检查各种参数：

```php
public function getRandomEntry()
{
	$entry = array();
	foreach ($this->mapping as $key => $value) {
		if (isset($value['source'])) {
			switch ($value['source']) {
```

23. 源参数用于实现实际上充当策略模式的功能。我们支持四种不同的源可能性，全部定义为类常量。第一个是 `SOURCE_FILE`。在这种情况下，我们使用前面讨论的 `getEntryFromFile()` 方法：

```php
case self::SOURCE_FILE : 
	$entry[$key] = $this->getEntryFromFile(
		$value['name'], $value['type']);
	break;
```

24. 回调选项根据在 `$mapping` 数组中提供的回调返回一个值：

```php
case self::SOURCE_CALLBACK : 
	$entry[$key] = $value['name']();
	break;
```

25. `SOURCE_TABLE` 选项使用 `$mapping` 中定义的数据库表作为查找。请注意，前面讨论的 `getEntryFromTable()` 能够返回一个值数组，这意味着我们需要使用 `array_merge()` 来合并结果：

```php
case self::SOURCE_TABLE : 
	$result = $this->getEntryFromTable(
		$value['name'], $value['idCol'], $value['mapping']);
	$entry = array_merge($entry, $result);
	break;
```

26. `SOURCE_METHOD` 选项（也是默认选项）使用该类中已包含的方法。我们检查是否包含参数，如果是，则将这些参数添加到方法调用中。请注意使用 `{}` 来影响插值。如果我们进行 PHP 7 的 `$this->$value['name']()` 调用，由于抽象语法树（AST）重写，它会插值为此形式：`${$this->$value}['name']()`，这不是我们想要的：

```php
case self::SOURCE_METHOD : 
default :
	if (!empty($value['params'])) {
		$entry[$key] = $this->{$value['name']}(
			$entry, $value['params']);
	} else {
		$entry[$key] = $this->{$value['name']}($entry);
	}
}
return $entry;
}
```

27. 我们定义一个方法，循环执行 `getRandomEntry()` 以生成多行假数据。我们还添加了一个插入到目标表的选项。如果启用了此选项，我们将设置一个用于插入的预编译语句，并检查是否需要截断当前在此表中的任何数据：

```php
public function generateData(
	$howMany, $destTableName = NULL, $truncateDestTable = FALSE)
{
	try {
		if ($destTableName) {
			$sql = 'INSERT INTO ' . $destTableName
				. ' (' . implode(',', array_keys($this->mapping))
				. ') ' . ' VALUES ' . '(:'
				. implode(' ,:', array_keys($this->mapping)) . ')';
			$stmt = $this->connection->pdo->prepare($sql);
			$insert = TRUE;
		}
		if ($truncateDestTable) {
			$sql = 'DELETE FROM ' . $destTableName;
			$this->connection->pdo->query($sql);
		}
	} catch (PDOException $e) {
		error_log(__METHOD__ . ': ' . $e->getMessage());
		throw new Exception(self::ERROR_COUNT);
	}
```

28. 接下来，我们循环处理请求的数据行数，并执行 `getRandomEntry()`。如果请求了数据库插入，我们在 `try/catch` 块中执行预编译语句。无论如何，我们都使用 `yield` 关键字将此方法转换为生成器：

```php
	for ($x = 0; $x < $howMany; $x++) {
		$entry = $this->getRandomEntry();
		if ($insert) {
			try {
				$stmt->execute($entry);
			} catch (PDOException $e) {
				error_log(__METHOD__ . ':' . $e->getMessage());
				throw new Exception(self::ERROR_DB);
			}
		}
		yield $entry;
	}
}
```

### 最佳实践
如果返回的数据量巨大，最好是在数据生成时逐步输出（yield）数据，从而节省数组所需的内存。

## 工作原理…

首先要做的是确保你为随机数据生成准备好数据。在本食谱中，我们将假设目标表为 `prospects`，其在第 7 步中展示了相应的 SQL 数据库定义。

作为姓名的数据源，你可以为名字和姓氏创建文本文件。在本示例中，我们将引用 `data/files` 目录，以及 `first_names.txt` 和 `surnames.txt` 文件。对于城市、州或省、邮政编码和国家，从 `http://www.geonames.org/` 等来源下载数据并上传到 `world_city_data` 表可能会很有用。对于剩余字段，如地址、电子邮件、状态等，你可以使用内置于 `FakeData` 的方法，或者定义回调。

接下来，务必定义 `Application\Test\FakeData`，添加第 8 步到第 29 步讨论的内容。完成后，创建一个名为 `chap_13_fake_data.php` 的调用程序，该程序设置自动加载并使用相应的类。你还应定义与数据库配置路径以及名称文件路径相匹配的常量：

```php
<?php
define('DB_CONFIG_FILE', __DIR__ . '../../../config/db.config.php');
define('FIRST_NAME_FILE', __DIR__ . '../../../data/files/first_names.txt');
define('LAST_NAME_FILE', __DIR__ . '../../../data/files/surnames.txt');
```
