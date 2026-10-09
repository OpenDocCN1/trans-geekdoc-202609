As before, you should wrap your database query in a try { } catch { } block. You can then place the code to test the recursive iteration inside the try { } block:

```
try {
    $connection = new Application\Database\Connection(
        include __DIR__ . DB_CONFIG_FILE);
    $sql    = 'SELECT * FROM iso_country_codes';
    $iterator = fetchAllAssoc($sql, $connection);
    $shallow = new RecursiveArrayIterator($iterator);
    foreach ($shallow as $item) var_dump($item);
    $deep    = new RecursiveIteratorIterator($shallow);
    foreach ($deep as $item) var_dump($item);
} catch (Throwable $e) {
    echo $e->getMessage();
}
```

Here is what you can expect to see in terms of output from RecursiveArrayIterator:

![](bbox=[0.31, 0.44, 0.68, 0.75])