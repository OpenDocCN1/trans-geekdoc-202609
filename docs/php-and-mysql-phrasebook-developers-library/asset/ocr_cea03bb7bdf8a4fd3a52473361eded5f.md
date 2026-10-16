There is one remaining reason to use the deprecated ext/mssql extension: In a heterogeneous network, UNIX/Linux systems can access MSSQL installations and connect to them using the old MSSQL extension. For this to work, you have to download the FreeTDS library from www.freetds.org/ and install it after unpacking the distribution with this command:

```
```
./configure --prefix=/usr/local/tds --with-tdsver=4.2
make
sudo make install
```
```

Then, reconfigure PHP with the switch --with-sybase=/usr/local/freetds.

Finally, you can connect to the server using `mssql_connect()` and select the database to be used using `mssql_select_db()`, similar to the API used by other database extensions. After executing a SQL query with `mssql_query()`, you can retrieve return data with one of the following functions:

+   - `mssql_fetch_assoc()` returns the current row in the resultset as an associative array.
+   - `mssql_fetch_object()` returns the current row in the resultset as an object.
+   - `mssql_fetch_row()` returns the current row in the resultset as a numeric array.

**NOTE:** MSSQL supports two modes to authenticate users: SQL authentication and Windows authentication. The latter checks whether the current Windows user has sufficient rights to access the database. In a controlled environment, this might be a better idea than using username and password. However, you first have to find out which user is used. For instance, Microsoft Internet Information Services (IIS) Web server software