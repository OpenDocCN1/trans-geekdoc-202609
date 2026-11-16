limited. It means that every database PHP wants to support creates at least 30 or so functions in this global namespace.

It gets worse. Check out the syntax for `mysql_query` and `pg_query`. You'd expect it to be the same, right? Wrong, as shown here:

```
resource mysql_query ( string $query [, resource $link_identifier ] )
resource pg_query ( resource $connection , string $query )
```

That's right. Despite being essentially identical in functionality, these two methods take their parameters in a different order.

This adds to a difficult situation. PHP has excellent database support (in terms of the breadth and depth of platforms supported), but an appalling implementation (mainly for historical reasons). As a result of this messy inconsistency, PHP database-driven applications built in this officially sanctioned way become a major headache to maintain — and an impossibility to scale or port.

# # Wrapper Classes

To address this disparity, as well as to bring some sense of order to the myriad database functions created in the global namespace, various third-party developers have, in recent years, attempted to create wrapper classes around these database methods.

A good example is MDB2, which is part of the PEAR repository. (See `http://pear.php.net/package/MDB2` for more information and comprehensive documentation.)

A typical session with MDB2 might look like the following. No need to try this out — it’s just an illustration:

```
<?php
require_once 'MDB2.php';
$dsn = 'pgsql://chaptersix:chaptersix@localhost/chaptersix';

$mdb2 = MDB2::factory($dsn);

if (PEAR::isError($mdb2)) {
    echo ($mdb2->getMessage().' - '.$mdb2->getUserinfo());
}

$query = 'SELECT * FROM "user"';
$result = $mdb2->query($query);

if (PEAR::isError($result)) {
    echo ($result->getMessage().' - '.$result->getUserinfo());
    exit();
}

while ($array = $result->fetchRow()) {
    var_dump($array);
};

$result->free();
?>
```