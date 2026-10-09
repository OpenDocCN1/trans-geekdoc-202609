```
if (!$this->statementRemoveByKey)
$this->prepareRemoveByKey();
$result = $this->statementRemoveByKey->execute(
['key' => $key]);
} catch (Throwable $e) {
error_log( __METHOD__ . ':' . $e->getMessage());
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
error_log( __METHOD__ . ':' . $e->getMessage());
throw new Exception(Constants::ERROR_REMOVE_GROUP);
}
return $result;
}
```

+   10. Lastly, we define getters and setters for each of the properties. Not all are shown here to conserve space:

```
public function setTable($name)
{
$this->table = $name;
}
public function getTable()
{
return $this->table;
}
// etc.
```

+   11. The filesystem cache adapter defines the same methods as defined earlier. Note the use of md5(), not for security, but as a way of quickly generating a text string from the key:

```
namespace Application\Cache;
use RecursiveIteratorIterator;
```