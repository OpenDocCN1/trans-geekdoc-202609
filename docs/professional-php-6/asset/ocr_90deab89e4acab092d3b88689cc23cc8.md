And here's the SQL statement to create the entityphone table:

```
```sql
CREATE TABLE "entityphone" (
 "phoneid" SERIAL PRIMARY KEY NOT NULL,
 "entityid" int,
 "snumber" varchar(20),
 "sextension" varchar(20),
 "stype" varchar(50),
 CONSTRAINT "fk_entityemail_entityid"
 FOREIGN KEY ("entityid") REFERENCES "entity"("entityid")
 );
```
```

# # The DataManager Class

Let's now take a look at that DataManager class. It and the other database code samples in this chapter (and in the rest of this book) use PostgreSQL, although a class like this would work just as well with MySQL, Oracle, or any other RDBMS. Chapter 6 examines a more sophisticated way of handling database abstraction, but for now let's keep it simple using the PHP PostgreSQL functions.

The primary responsibility of the DataManager class is to put all the data access code into a single location, making it much easier to change the database type or connection parameters later. All the class's methods have been declared static because the class doesn't rely on any member variables. Note the use of the static function variable in getConnection(). This is used to ensure that only one database connection is open during a single page request. A lot of overhead is associated with establishing a database connection, so eliminating unnecessary connections helps to improve performance. Create a file called class.DataManager.php and enter the following class code:

```
```php
<?php

require_once('class.Entity.php'); //this will be needed later
require_once('class.Individual.php');
require_once('class.Organization.php');

class DataManager {

 private static function _getConnection() {
   static $hDB;

   if(isset($hDB)) {
     return $hDB;
   }

   $hDB = pg_connect("host=localhost port=5432 " .
     "dbname=[your db name] user=[your user name]
     password=[your password]");
   or die("Failure connecting to the database!");
   return $hDB;
 }

 public static function getAddressData($addressID) {
   $sql = "SELECT * FROM \"entityaddress\" WHERE\"addressid\" = $addressID";
   $res = pg_query(DataManager::_getConnection(), $sql);
 }
```
```