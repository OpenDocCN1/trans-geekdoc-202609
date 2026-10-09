# Chapter 5

Here is the resulting output:

![](bbox=[0.31, 0.17, 0.67, 0.43])

Add the option to the PDO constructor, which sets the error mode to EXCEPTION. Now alter the SQL statement and observe the resulting error message:

```
$opts = [PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION];
$pdo = new PDO($dsn, $params['user'], $params['pwd'], $opts);
$stmt = $pdo->query('THIS SQL STATEMENT WILL NOT WORK');
```

You will observe something like this:

![](bbox=[0.24, 0.57, 0.75, 0.72])

Placeholders can be named or positional. **Named placeholders** are preceded by a colon (:) in the prepared SQL statement, and are references as keys in an associative array provided to execute( . ). **Positional placeholders** are represented as question marks (?) in the prepared SQL statement.