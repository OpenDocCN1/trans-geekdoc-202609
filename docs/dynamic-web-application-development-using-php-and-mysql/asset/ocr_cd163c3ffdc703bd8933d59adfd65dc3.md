Finally, the class is instantiated then a call to aStaticMethod is made to illustrate that this also works:

```
$objExample = new noInstancesRequiredClass;
$objExample->aStaticMethod();
```

> NOTE  Static properties cannot be accessed through the object using the arrow operator ->.

The output from the above script is:

Simon Stobart
Simon Stobart
Simon Stobart

# 17.7 Class constants

PHP classes support the inclusion of constant values. Once defined these remain the same and are unchangeable. Constants differ from normal data members in that you don’t use the $ symbol to declare or use them. Consider the following script:

```
<?php
// File: example17-7.php

class constantClass {
    const strName = "Simon Stobart";
    function showConstant() {
        echo "<p>" . self::strName . "</p>";
    }
}

echo "<p>" . constantClass::strName . "</p>";
$objExample = new constantClass;
$objExample->showConstant();
?>
```

In the above script, constantClass is defined and a const member is created:

```
class constantClass {
    const strName = "Simon Stobart";
```

> NOTE  Constant members do not use the $ symbol to define them.