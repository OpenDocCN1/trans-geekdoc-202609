The `errorCode()` method will return a five-character error code — for example, 45S02, which reflects what is known as the `SQLSTATE` of the last operation on the PDO instance or `PDOStatement` instance, as appropriate. Your database of choice should provide a list of `SQLSTATE` values in its own documentation; PostgreSQL provides one at www.postgresql.org/docs/8.2/static/errcodes-appendix.html.

The `errorInfo()` method will return a little more detail. A three-element array is your reward. The first element contains the same information as `errorCode()`; the second contains any driver-specific (e.g., PostgreSQL-specific) error code; and the third contains a human-readable error message from the database itself.

Both of these methods are useful, but it does require you (as a developer) to test for an error at virtually every stage. This isn’t really appropriate for production-grade applications and will quickly result in unwieldy code. You should instead tell PDO to throw an exception whenever it encounters a problem — and trap that exception yourself. This gives you the power to handle that error with whatever leniency or severity you deem appropriate as a developer. However, it does place the onus on you to ensure that every single possible error is caught. Any uncaught exceptions will cause a big, ugly PHP error — not something you want your users to see.

You can tell PDO to work in this way by using the following:

```
```php
$objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
```
```

This needs to be called more or less immediately after instantiating the PDO class, before you even try the first query preparation.

Any PDO usage, then, must be wrapped inside try/catch pairs. Here’s a complete example you can try for yourself:

```
```php
<?php
$strDSN = "pgsql:dbname=chaptersix;host=localhost;port=5432;user=chaptersix;
        password=chaptersix";

// Let's connect
try {
    $objPDO = new PDO($strDSN);
    $objPDO->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

// Let's interrogate the database
$i = 0;
$strQuery = "SELECT * FROM \"usdrs\"";
$objStatement = $objPDO->prepare($strQuery);
$objStatement->execute();
while ($arRow = $objStatement->fetch(PDO::FETCH_ASSOC)) {
    print "Row $i<br />\n";
    foreach ($arRow as $key => $value) {
        print " - Column $key, value $value<br />\n";
    };
    $i++;
};
// Let's disconnect
```
```