# Chapter 9

```
(
    $sql = 'SELECT `' . $this->dataColumnName . '`'
        . '`FROM `' . $this->table . '`'
        . ' WHERE `' . $this->keyColumnName . '` = :key'
        . ' AND `' . $this->groupColumnName . '` = :group';
    $this->sql[_METHOD_] = $sql;
    $this->statementGetFromCache =
        $this->connection->pdo->prepare($sql);
)
```

+   6. Now we define a method that determines whether data for a given key exists:

```
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

+   7. The core methods are ones that read from and write to the cache. Here is the method that retrieves from the cache. All we need to do is to execute the prepared statement, which performs a SELECT, with a WHERE clause, which incorporates the key and group:

```
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
    }
```