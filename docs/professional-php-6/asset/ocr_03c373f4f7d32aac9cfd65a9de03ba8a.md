In Chapter 6 you learned how the PDO class can connect to a completely different database back end by a simple change to its connection string. By connecting with "mysql:host=localhost;dbname=mydb", you can connect to a MySQL database running on the local machine and use to the database called "mydb". To connect to a PostgreSQL database, the connection string looks like "mysql:host=localhost;dbname=yourdb", which connects to a PostgreSQL database instance on the local machine and uses the database called "yourdb". After a connection has been established using this common connection string syntax, everything else about the use of the PDO class is identical, regardless of which RDBMS you're connected to. You can use a very similar construct to enable your Logger class to connect to any kind of storage medium.

The goal of the enhanced Logger class is to use a similar syntax for establishing a connection to a storage medium for log data. Because you'll be able to use different storage media, you should also be able to store different logs for different parts of the application. The new Logger class should support some sort of “registry” of log connections. For example, you should be able to have a log called “errors” and one called “queries,” which will store error messages and SQL statements, respectively. The following sample code represents what you should be able to do with the redesigned class:

```
<?php
Logger::register('errors', 'file:///var/log/error.log');
Logger::register('app',
    'pgsql://postgres@db/errors?table=applog&timestamp=datalog&' .
    'msg=smsg&level=slevel&module=smod');

$objQLog = Logger::getInstance('app');

$sql = "SELECT * FROM foo";
$objQLog->logMessage("Selecting all foos");

try {
    Database->getInstance()->select($sql);
} catch (DBQueryException $e) {
    $objErrLog = Logger::getInstance('errors');
    $objErrLog->logMessage($e->getMessage(), LOGGER_CRITICAL);
}
?>
```

Showing this code before showing the new class that drives it may be a little confusing, but sometimes it's easier to design a class by first knowing how you want to be able to use it. In a real application, you would put the first two lines in a globally included file. These two lines establish two different logs:

+   app—The app log will store its log messages in a PostgreSQL database, in a table called applog using the field names specified for the timestamp, message, logging level, and module.
+   errors—The error log will be a text file located in /var/log/error.log.

In the main part of the application, you would store most messages in the app log for later analysis. Any errors that occur will be stored in the errors log, which is a text file. A text file is used for the errors because one of the errors may be an inability to connect to the database.