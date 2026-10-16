If you want to use ext/mysqli, the switch for --with-mysql has to point to /path/to/mysql config. Windows users have to use the files php_mysqli.dll and lib-mysql.dll; the rest of the previous install instructions remain unchanged.

Now connecting to the database is easy: Just call mysql_connect(), providing the server, username, and password. You then get a handle that can be used for mysqli_select_db() or to choose a database on the server. Finally, mysqli_close() closes the connection to the data source.

If you have worked with the older ext/mysql, keep in mind that the different variable order for mysql(i)_select_db() is one of the prominent differences between the two extensions. The newer one wants the database handle first. Another difference between these two extensions is that the database handle is a mandatory parameter whenever used. With ext/mysql, the last handle created by mysql_connect() is the current default handle for the page. One more difference: mysqli_connect() accepts the name of the database as an optional fourth parameter, so you can avoid using mysqli_select_db().

**NOTE:** Alternatively, the mysqli extension also offers an object oriented syntax to access a data source. Although this chapter uses the functional approach to make a possible transition from ext/mysql to ext/mysqli as painless as possible, the following shows what the object oriented approach looks like:

```
```php
$db = new mysqli('localhost', 'user', 'password');
$db->select_db('phrasebook');
$db->close();
```
```