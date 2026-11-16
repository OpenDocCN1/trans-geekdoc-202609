
A properly named database field indicates its data type by using a one-character prefix, letting you know what kind of data goes in the field. Having naming conventions is just as important for database design as it is for your code.

The propertyTable array is set up in the Address class to map friendly property names (such as city, state, and zip code) to the less friendly database field names (such as scity, cstate, and postalcode). Note that you can map multiple property names to the same database field name in propertyTable. This mapping enables you to refer to the primary key of the address by either $objAddress->addressid or $objAddress->id.

What's incredibly exciting about the Address class is that the overwhelming majority of the code is spent implementing business logic and data validation. There's almost no extraneous code here. Its sole responsibility is to populate itself and validate its own contents. Everything else is left up to the DataManager class (which you'll see in detail shortly) and the PropertyObject.

Following is the code for the Email class, which should look very familiar. Enter it into a file called class.EmailAddress.php:

```php
<?php
require_once('class.PropertyObject.php');
class Email extends PropertyObject {
    function __construct($emailid) {
        $arData = DataManager::getEmailData($emailid);
        parent::__construct($arData);
        $this->propertyTable['emailid'] = 'emailid';
        $this->propertyTable['id'] = 'emailid';
        $this->propertyTable['entityid'] = 'entityid';
        $this->propertyTable['email'] = 'semail';
        $this->propertyTable['type'] = 'stype';
    }
    function validate() {
        if(!$this->email) {
            $this->errors['email'] = 'You must set an email address.';
        }
        if(sizeof($this->errors)) {
            return false;
        } else {
            return true;
        }
    }
    function __toString() {
        return $this->email;
    }
}
?>
```

This file has very little ancillary code; it’s just fetching the code from the database and setting up the propertyTable. Everything else is data validation. Again, the UML diagram was the guide to deciding on the properties of the Email class and the structure of the corresponding database table.

The database table for the entityemail table looks like this:

```sql
CREATE TABLE "entityemail" (
 "emailid" SERIAL PRIMARY KEY NOT NULL,
 "entityid" int,
 "semail" varchar(255),
 "stype" varchar(50),
 CONSTRAINT "fk_entityemail_entityid"
 FOREIGN KEY ("entityid") REFERENCES "entity"("entityid")
 );
```

The PhoneNumber class works very much like Address and Email. Here’s the code to enter into class.PhoneNumber.php:

```php
<?php
 require_once('class.PropertyObject.php');
 class PhoneNumber extends PropertyObject {
 function __construct($phoneid) {
    $arData = DataManager::getPhoneNumberData($phoneid);
    parent::__construct($arData);
    $this->propertyTable['phoneid'] = 'phoneid';
    $this->propertyTable['id'] = 'phoneid';
    $this->propertyTable['entityid'] = 'entityid';
    $this->propertyTable['number'] = 'snumber';
    $this->propertyTable['extension'] = 'sextension';
    $this->propertyTable['type'] = 'stype';
 }
 function validate() {
    if(!$this->number) {
    $this->errors['number'] = 'You must supply a phone number.';
    }
    if(sizeof($this->errors)) {
    return false;
    } else {
    return true;
    }
 }
 function __toString() {
    return $this->number .
    ($this->extension ? ' x' . $this->extension : '');
 }
 }
 ?>
```

And here's the SQL statement to create the entityphone table:

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

## The DataManager Class

Let's now take a look at that DataManager class. It and the other database code samples in this chapter (and in the rest of this book) use PostgreSQL, although a class like this would work just as well with MySQL, Oracle, or any other RDBMS. Chapter 6 examines a more sophisticated way of handling database abstraction, but for now let's keep it simple using the PHP PostgreSQL functions.

The primary responsibility of the DataManager class is to put all the data access code into a single location, making it much easier to change the database type or connection parameters later. All the class's methods have been declared static because the class doesn't rely on any member variables. Note the use of the static function variable in getConnection(). This is used to ensure that only one database connection is open during a single page request. A lot of overhead is associated with establishing a database connection, so eliminating unnecessary connections helps to improve performance. Create a file called class.DataManager.php and enter the following class code:

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
   if(! ($res && pg_num_rows($res))) {
       die("Failed getting address data for address $addressID");
   }

   return pg_fetch_assoc($res);
 }

 public static function getEmailData($emailID) {
     $sql = "SELECT * FROM \"entityemail\" WHERE\"emailid\" = $emailID";
     $res = pg_query(DataManager::_getConnection(), $sql);
     if(! ($res && pg_num_rows($res))) {
     die("Failed getting email data for email $emailID");
     }

     return pg_fetch_assoc($res);
 }

 public static function getPhoneNumberData($phoneID) {
     $sql = "SELECT * FROM \"entityphone\" WHERE \"phoneid\" = $phoneID";
     $res = pg_query(DataManager::_getConnection(), $sql);
     if(! ($res && pg_num_rows($res))) {
     die("Failed getting phone number data for phone $phoneID");
     }

     return pg_fetch_assoc($res);
 }
 }
?>
```

The DataManager class provides the data structures used to populate the $data member of your PropertyObject subclasses. Separate functions return the data for each of the types. You’ll be adding a few new functions to this class a bit later in this chapter. Note that the values supplied to pg_connect do not need the square brackets. All of the values in the square brackets (including the brackets themselves) should be replaced with the appropriate connection details for your server.

All the methods of this class are declared to be static. Remember that static methods are those requiring all member variables to be static, too. You don’t need to instantiate static classes to use their methods. There are several scenarios in which this makes sense. Consider a class called Math that exposes methods such as squareRoot(), power(), and cosine(), and has properties including the mathematical constants e and pi. All instances of this class perform the same math. The square root of 2 doesn’t change; 4 raised to the third power will always be 64; and the two constants are, well, constant. There’s no need to create separate instances of this class because its state and properties never change. A class called Math implemented in this manner should allow for all its functions to be called statically.

The DataManager class is much the same. All the functions are self-contained. No nonstatic member variables are present for the functions to interact with. The class exposes no properties. You can invoke the methods of the class using the static method operator :: as a result. Because all the methods you’ve created are static, you need never instantiate the object with $obj = new DataManager() and then call methods using syntax such as $obj->getEmail(). Instead, you can use the simple syntax DataManager::getEmail().
