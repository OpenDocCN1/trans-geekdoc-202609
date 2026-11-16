
## The Entity, Individual, and Organization Classes

With all the supporting classes in place, you can move on to the core of the application: the `Entity` class and its subclasses.

First, ensure that you’re updating your UML diagram as you make changes to the object hierarchy so that you keep track of what you (or the development team) are doing. You’ve created the `PropertyObject` class and made all your classes inherit from it, with one exception — the new `DataManager` class, which does not inherit from anything, but rather merely provides data abstraction functionality. The `PropertyObject` implements an abstract interface called `Validator`. Figure 3-7 shows the updated diagram.

![](img/a1b732997d9cb194dceec0570dc79710_77_0.png)

### Figure 3-7: Updated UML diagram

Now you can begin to develop the Entity, Individual, and Organization classes. The following code shows the fully implemented Entity class called class.Entity.php:

```php
<?php
require_once('class.PropertyObject.php');
require_once('class.PhoneNumber.php');
require_once('class.Address.php');
require_once('class.EmailAddress.php');

abstract class Entity extends PropertyObject {
private $emails;
private $addresses;
private $phonenumbers;

public function __construct($entityID) {
$arData = DataManager::getEntityData($entityID);

parent::__construct($arData);

$this->propertyTable['entityid'] = 'entityid';
$this->propertyTable['id'] = 'entityid';
$this->propertyTable['name1'] = 'sname1';
$this->propertyTable['name2'] = 'sname2';
$this->propertyTable['type'] = 'ctype';
$this->_emails = DataManager::getEmailObjectsForEntity($entityID);
$this->_addresses = DataManager::getAddressObjectsForEntity($entityID);
$this->_phonenumbers = DataManager::getPhoneNumberObjectsForEntity($entityID);
}

function setID($val) {
throw new Exception('You may not alter the value of the ID field!');
}

function setEntityID($val) {
$this->setID($val);
}

function phonenumbers($index) {
if(!isset($this->_phonenumbers[$index])) {
throw new Exception('Invalid phone number specified!');
} else {
return $this->_phonenumbers[$index];
}
}

function getNumberOfPhoneNumbers() {
return sizeof($this->_phonenumbers);
}

function addPhoneNumber(PhoneNumber $phone) {
    $this->_phonenumbers[] = $phone;
}

function addresses($index) {
    if(!isset($this->_addresses[$index])) {
        throw new Exception('Invalid address specified!');
    } else {
        return $this->_addresses[$index];
    }
}

function getNumberOfAddresses() {
    return sizeof($this->_addresses);
}

function addAddress(Address $address) {
    $this->_addresses[] = $address;
}

function emails($index) {
    if(!isset($this->_emails[$index])) {
        throw new Exception('Invalid email specified!');
    } else {
        return $this->_emails[$index];
    }
}

function getNumberOfEmails() {
    return sizeof($this->_emails);
}

function addEmail(Email $email) {
    $this->_emails[] = $email;
}

public function validate() {
    //Add common validation routines
}

?>
```

By moving all the accessor method functionality to the parent PropertyObject class, you simplify the Entity class and ensure that it is focused only on the code required to implement an entity.

The Entity class is declared abstract because it isn’t useful on its own. All entities are either Individuals or Organizations. You do not want to be able to instantiate objects of class Entity. Declaring it abstract prevents the class from being instantiable.

You've added requests to a few new functions of the DataManager::getEntityData() and get[x]ObjectsForEntity(). getEntityData() returns the data required to instantiate an entity, just as functions you've already seen do for the contact types. The following shows the code for the new functions in class.DataManager.php:

```php
// top of file omitted for brevity
...
die("Failed getting phone number data for phone $phoneID");
}
return pg_fetch_assoc($res);
}

public static function getEntityData($entityID) {
    $sql = "SELECT * FROM \"entity\" WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if (!($res && pg_num_rows($res))) {
        die("Failed getting entity $entityID");
    }
    return pg_fetch_assoc($res);
}

public static function getAddressObjectsForEntity($entityID) {
    $sql = "SELECT \"addressid\" from \"entityaddress\" WHERE " .
        "\"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting address data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new Address($rec['addressid']);
        }
        return $objs;
    } else {
        return array();
    }
}

public static function getEmailObjectsForEntity($entityID) {
    $sql = "SELECT \"emailid\" from \"entityemail\" " .
        "WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);
    if(!$res) {
        die("Failed getting email data for entity $entityID");
    }
    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new EmailAddress($rec['emailid']);
        }
        return $objs;
    } else {
        return array();
    }
}

public static function getPhoneNumberObjectsForEntity($entityID) {
    $sql = "SELECT \"phoneid\" from \"entityphone\" " .
        "WHERE \"entityid\" = $entityID";
    $res = pg_query(DataManager::getConnection(), $sql);

    if (!$res) {
        die("Failed getting phone data for entity $entityID");
    }

    if(pg_num_rows($res)) {
        $objs = array();
        while($rec = pg_fetch_assoc($res)) {
            $objs[] = new PhoneNumber($rec['phoneid']);
        }
        return $objs;
    } else {
        return array();
    }
}
```

These functions take an entity ID value. They query the database to determine whether any e-mails, addresses, or phone numbers exist for the entity in question. If they do, then the functions build an array of EmailAddress, Address, or PhoneNumber objects by passing each ID to the constructor for the appropriate object type. This array is then passed back to the Entity object, where it is stored in the appropriate private member variable.

With the Entity class doing all the heavy lifting, the remaining work is fairly simple. You just need to implement the Individual and Organization classes. Create a file called class.Individual.php and enter the following:

```php
<?php
require_once('class.Entity.php');
require_once('class.Organization.php');

class Individual extends Entity {

    public function __construct($userID) {
        parent::__construct($userID);

        $this->propertyTable['firstname'] = 'name1';
        $this->propertyTable['lastname'] = 'name2';
    }

    public function __toString() {
        return $this->firstname . ' ' . $this->lastname;
    }

    public function getEmployer() {
        return DataManager::getEmployer($this->id);
    }

    public function validate() {
        parent::validate();

        //add individual-specific validation
    }

}
?>
```

That's short and sweet. Inheritance makes this easy. The Individual class sets up a few new properties that make accessing the first and last name of the individual easier, instead of having to use the rather ugly name1 and name2 properties defined in the Entity class. It also defines a new method, getEmployer(), which requires a new function in the DataManager. You get to that function as soon as you have your Organization class, which is shown in the following code. Create a file called class.Organization.php and enter this code into it:

```php
<?php

require_once('class.Entity.php');
require_once('class.Individual.php');

class Organization extends Entity {

    public function __construct($userID) {
        parent::__construct($userID);
        $this->propertyTable['name'] = 'name1';
    }

    public function __toString() {
        return $this->name;
    }

    public function getEmployees() {
        return DataManager::getEmployees($this->id);
    }

    public function validate() {
        parent::validate();

        //do organization-specific validation
    }

}
?>
