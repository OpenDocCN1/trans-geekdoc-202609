```
$fetchMode,
$params = array()
{
    try {
        $stmt = $connection->pdo->prepare($this->sql);
        if (!$stmt) return FALSE;
        if ($params) {
            $stmt->execute($params);
        } else {
            $stmt->execute();
        }
        while ($result = $stmt->fetch($fetchMode)) yield $result;
    } catch (PDOException $e) {
        error_log($e->getMessage());
        return FALSE;
    } catch (Throwable $e) {
        error_log($e->getMessage());
        return FALSE;
    }
}
```

+   6. It might not be a bad idea to provide support for the query builder class mentioned in the previous recipe. This will make updating LIMIT and OFFSET much easier. All we need to do is to provide support for Application\\Database\\Finder is to use the class and modify the `__construct()` method to check to see if the incoming SQL is an instance of this class:

```
if ($sql instanceof Finder) {
    $sql->limit($linesPerPage);
    $sql->offset($offset);
    $this->sql = $sql::getSql();
} elseif (is_string($sql)) {
    switch (TRUE) {
        case (stripos($sql, 'LIMIT')
          && stripos($sql, 'OFFSET') :
            // remaining code as shown in bullet #3 above
        }
    }
}
```

+   7. Now all that remains to be done is to add a getSql() method in case we need to confirm that the SQL statement was correctly formed:

```
public function getSql()
{
    return $this->sql;
}
```