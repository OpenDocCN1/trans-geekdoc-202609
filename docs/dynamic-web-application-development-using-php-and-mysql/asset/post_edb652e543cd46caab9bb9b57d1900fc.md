
```
function setDescription($strDescription) {
    $this->strDescription = $strDescription;
}
}?
>
```

Finally, the following script creates the object instances of the classes, which requires the inclusion of the two scripts above:

```
<?php
// File: example16-6.php

require_once("person.php");
require_once("vehicle.php");

$objSimon = new person;
$objSimon->setDisplayFirstnameSurname("Simon", "Stobart");
$objBike = new vehicle;
$objBike->setDescription("Bicycle");
echo "<p>Vehicle: " . $objBike->getDescription() . "</p>";
?>
```

The output from the above script is the same as shown in Figure 16.4.

However, while this is really useful it does have one annoying feature: you have to write a long list of includes or requires statements at the beginning of each script (one for each class). In PHP 5, this is no longer necessary. You may define an __autoload function which is automatically called in case you are trying to use a class which hasn’t been defined yet. The function looks like this:

```
function __autoload($class_name) {
    require_once $class_name . '.php';
}
```

The function is invoked each time a class is required but hasn’t been defined. We can insert this function into our script:

```
<?php
// File: example16-7.php

function __autoload($class_name) {
    require_once $class_name . '.php';
}

$objSimon = new person;
$objSimon->setDisplayFirstnameSurname("Simon", "Stobart");
$objBike = new vehicle;
$objBike->setDescription("Bicycle");
echo "<p>Vehicle: " . $objBike->getDescription() . "</p>";
?>
```

The output from the above script is the same as Figure 16.4.

## 16.4 Constructors and destructors

### Constructors

You will have noticed by now that creating an object is a two-stage process. First we create a new object then we call a function that populates that object with data, for example:

```
$objSimon = new person;
$objSimon->setDisplayFirstnameSurname("Simon", "Stobart");
```

There is however a way to perform these two operations in one. In order to do so, we need to create a constructor. A constructor is a function, which is automatically called when you create a new object and it looks like this:

```
void function __construct (various)
```

| NOTE | For backwards compatibility, if PHP 5 cannot find a __construct() function for a given class, it will search for the old-style constructor function, by the name of the class. |
|------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Let’s create a constructor function for our person class. It looks like this:

```
function __construct ($strFirstname, $strSurname) {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
    $this->display();
}
```

The constructor function receives two arguments which are the values of firstname and surname and assigns these to the appropriate data members. Our complete person class, which we have now renamed to revisedperson now looks like this:

```
<?php
// File: revisedperson.php

class revisedperson {
    private $strFirstname;
    private $strSurname;

    function __construct ($strFirstname, $strSurname) {
        $this->setFirstname($strFirstname);
        $this->setSurname($strSurname);
        $this->display();
    }

    function getFirstname() {
        return $this->strFirstname;
    }

    function getSurname() {
        return $this->strSurname;
    }

    function setFirstname($strFirstname) {
        $this->strFirstname = $strFirstname;
    }

    function setSurname($strSurname) {
        $this->strSurname = $strSurname;
    }

    private function display() {
        echo "<p>Firstname: " . $this->strFirstname . "</p>";
        echo "<p>Surname: " . $this->strSurname . "</p>";
    }

    function setDisplayFirstnameSurname($strFirstname, $strSurname) {
        $this->setFirstname($strFirstname);
        $this->setSurname($strSurname);
        $this->display();
    }
}
?>
```

We can create a constructor for the vehicle class also:

```
function __construct ($strDescription) {
    $this->strDescription = $strDescription;
}
```

Having created a constructor we can now combine the creation of the object and the population of data with the syntax:

```
new class (various);
```

So in our main script we now have the following:

```
<?php
// File: example16-8.php

function __autoload($class_name) {
    require_once $class_name . '.php';
}

$objSimon = new revisedperson("Simon", "Stobart");

$objBike = new vehicle("Bicycle");
echo "<p>Vehicle: " . $objBike->getDescription() . "</p>";
?>
```

Note that, because our person script has a display() method which is invoked from the constructor, there is still not a need (unlike with the vehicle class) to invoke a method to
obtain the value of the object members. The output from the above script is the same as in Figure 16.4.

### Destructors

PHP 5 introduces a destructor concept similar to that of other object-oriented languages, such as C++. The destructor method is called as soon as all references to a particular object are removed or when the object is explicitly destroyed. The syntax of the method is:

```
void function __destruct (void)
```

An example of a destructor function is:

```
function __destruct() {
    echo "<p>Destroying Class</p>";
}
```

The above example doesn't really do anything useful but tells us at what point the object has been deleted. Destructors can be useful to include code to free up memory that the object has been using, for example.

## 16.5 Arrays and objects

Objects that have been created can be treated in the same way as you would variables. Therefore, you can easily create an array of objects, for example:

```
<?php
// File: example16-9.php

function __autoload($class_name) {
    require_once $class_name . '.php';
}

$objSimon = new revisedperson("Simon", "Stobart");
$objLiz = new revisedperson("Liz", "Hall");
$objIan = new revisedperson("Ian", "Walker");
$objBilly = new revisedperson("Billy", "Lee");
$objHayley = new revisedperson("Hayley", "West");
$arrPeople = array($objSimon, $objLiz, $objIan, $objBilly, $objHayley);
foreach($arrPeople as $objThePerson)
    echo($objThePerson->display() );
?>
```

The above script creates five objects of type ‘revisedperson’:

```
$objSimon = new revisedperson("Simon", "Stobart");
$objLiz = new revisedperson("Liz", "Hall");
$objIan = new revisedperson("Ian", "Walker");
$objBilly = new revisedperson("Billy", "Lee");
$objHayley = new revisedperson("Hayley", "West");
```

It then puts them in an array and uses a foreach loop to cycle through the array and display the contents of the object using the display() method:

```
$arrPeople = array($objSimon, $objLiz, $objIan, $objBilly, $objHayley);
foreach($arrPeople as $objThePerson)
    echo($objThePerson->display() );
```

To allow the above script to work as intended we must change the visibility of the display() method in the person class back to public so it looks like this:

```
function display() {
    echo "Firstname: " . $this->strFirstname;
    echo "<br/>Surname: " . $this->strSurname . "<br/>";
}
```

We also removed the invocation to the display() method from within the constructor, so that the constructor of the person class now looks like this:

```
function __construct ($strFirstname, $strSurname) {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
}
```

The output from the above script is illustrated in Figure 16.5.

### FIGURE 16.5 Objects and arrays

![](img/b2471264f405d17994ef173e4b9cec92_501_0.png)

## 16.6 Functions and objects

Objects can be passed to functions in the same way as variables. The following script illustrates something to be wary of however:

```
<?php
// File: example16-10.php

function __autoload($class_name) {
    require_once $class_name . '.php';
}

function change($objPerson){
    $objPerson->setFirstname("Tim");
}

$objSimon = new revisedperson("Simon", "Stobart");
change($objSimon);
$objSimon->display();
?>
```

In this example, you find a simple function called change() which receives a person object and changes its firstname to ‘Tim’:

```
function change($objPerson){
    $objPerson->setFirstname("Tim");
}
```

Next an object is created, the member values are set to ‘Simon’ and ‘Stobart’ and the object contents are displayed through the call to function display() within the constructor:

```
$objSimon = new revisedperson("Simon", "Stobart");
```

Finally, function change() is invoked, passing the object, and then function display() is invoked once more:

```
change($objSimon);
$objSimon->display();
```

‘Okay’, I hear you cry, ‘I know the answer to this, the object is passed by value and therefore function change() is going to simply change a copy of the object and so the original object when displayed the second time will still be as it was when it was first displayed’. Well, the output from this script is illustrated in Figure 16.6.

If you thought that the object was going to be unchanged you were wrong. In fact, objects in PHP 5 are very special creatures and are passed around by reference without the need for any special & characters.

| NOTE | Objects in versions of PHP prior to version 5 are passed by value and therefore behave like any other kind of variable. |
|------|-------------------------------------------------------------------------------------------------------------------------------|
