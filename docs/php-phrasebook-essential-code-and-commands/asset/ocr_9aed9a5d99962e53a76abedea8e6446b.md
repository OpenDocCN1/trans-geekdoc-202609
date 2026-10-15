# Connecting to Oracle

# @oci_connect()

Two PHP extensions are available for Oracle, but only one is actively maintained and also works with more recent versions of the RDBMS. To install it, configure PHP with the switch --with-oci8. The environment variable ORACLE_HOME must be set so that PHP can find the client libraries. Windows users need the php.ini directive extension=php_oci8.dll. In addition, PHP requires read access to the client libraries. Then, oci_connect() tries to establish a connection to the server. The order of the parameters is a bit strange: first username and password, then the name of the service (that has been configured using the configuration assistant or is part of the tnsnames.ora file). The return value is a handle to the connection and is required by further operations in the database.

```
<?php
if ($db = @oci_connect('scott', 'tiger', 'orcl'))
{
 echo 'Connected to the database.';
 oci_close($db);
} else {
 echo 'Connection failed.';
}
?>
```

Connecting to Oracle (oci_connect.php)