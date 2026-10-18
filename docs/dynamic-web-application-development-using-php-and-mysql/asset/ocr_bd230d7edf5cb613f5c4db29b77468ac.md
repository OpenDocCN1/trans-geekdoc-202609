# FIGURE 16.6 Objects and function output

![](bbox=[0.2, 0.07, 0.9, 0.3])

This makes programming easier but you need to be aware that objects are handled differently from other data types.

# 16.7 Default arguments

Class functions, like their non-class counterparts, can include default argument values. This allows a function to be called with an argument or without, knowing that if it is missing the default value will be set. The constructor function in class revisedperson has been rewritten to include default arguments:

```
function __construct ($strFirstname = "Simon", $strSurname = "Stobart") {
    $this->setFirstname($strFirstname);
    $this->setSurname($strSurname);
}
```

We shall call this new class ‘revisedagainperson’. Consider the following script:

```
<?php
// File: example16-11.php

function __autoload($class_name) {
    require_once $class_name . '.php';
}

$objSimon = new revisedagainperson("Simon", "Stobart");
$objSimon->display();

$objAnotherSimon = new person();
$objAnotherSimon->display();
?>
```

Here an object called $objSimon is constructed using the arguments ‘Simon’ and ‘Stobart’. Then, an object called $objAnotherSimon is constructed without any arguments but the default values are used. The output from the above script is illustrated in Figure 16.7.