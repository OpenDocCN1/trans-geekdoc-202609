A method showConstant() is defined and outputs the value of the constant. Note that the self:: scope operator is used to access the constant member as the -> operator will not work:

```
```php
function showConstant() {
    echo "<p>" . self::$strName . "</p>";
}
```
```

Outside the class, the scope operator is used to access the value of the constant member without any need to instantiate the class:

```
```php
echo "<p>" . constantClass::strName . "</p>";
```
```

Finally, the class is instantiated then a call to method showConstant() is made to illustrate that this also works:

```
```php
$objExample = new constantClass;
$objExample->showConstant();
```
```

The output from the above script is:

Simon Stobart
Simon Stobart

# 17.8 Type hinting

PHP 5 introduces the concept of type hinting. Functions can force parameters to be objects (by specifying the name of the class in the function prototype) or arrays. Consider the following script:

```
```php
<?php
// File: example17-8.php

class typeHintingClass {

    private $arrNames = array();

    function __construct(array $arrNames) {
        $this->arrNames = $arrNames;
    }

    function showContents() {
        foreach ($this->arrNames as $arrItem)
            echo "<p>$arrItem</p>";
    }

    function showOtherClass(typeHintingClass $objOther) {
        $objOther->showContents();
    }
}

$arrNames = array("Simon","Alan","Fred");
$arrColours = array("Red","Green","Blue","Yellow");

$objNames = new typeHintingClass($arrNames);
$objNames->showContents();
```
```