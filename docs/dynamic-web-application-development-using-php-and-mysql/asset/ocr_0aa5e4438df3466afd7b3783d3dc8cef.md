instantiated class object (though a static method can). Consider the following script:

```
<?php
// File: example17-6.php

class noInstancesRequiredClass {
    public static $strName = "Simon Stobart";
    public static function aStaticMethod() {
        echo "<p>" . self::$strName . "</p>";
    }
}
echo "<p>" . noInstancesRequiredClass::$strName . "</p>";
noInstancesRequiredClass::aStaticMethod();

$objExample = new noInstancesRequiredClass;
$objExample->aStaticMethod();
?>
```

The above script defines a class called ‘noInstancesRequiredClass’ and within this creates a static member variable called $strName:

```
class noInstancesRequiredClass {
    public static $strName = "Simon Stobart";
}
```

The class also contains a single static method called ‘aStaticMethod’ which will display the value of the static member:

```
public static function aStaticMethod() {
    echo "<p>" . self::$strName . "</p>";
}
```

Note that the method uses the self:: scope operator to access the member.

| NOTE | Because static methods are callable without an instance of the object created, the pseudo-variable $this is not available inside the method declared as static. |

Outside the class the scope operator is used to access the value of the static member without any need to instantiate the class:

```
echo "<p>" . noInstancesRequiredClass::$strName . "</p>";
```

It addition the static method is also invoked in a similar way:

```
noInstancesRequiredClass::aStaticMethod();
```