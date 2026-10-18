# FIGURE 17.15 Comparing objects

![](bbox=[0.08, 0.07, 0.81, 0.27])

The output from the above script is illustrated in Figure 17.15.

# 17.10 The ‘final’ keyword

The ‘final’ keyword can be prefixed before a class method and prevents a child class from overriding the method. Consider the following example:

```
<?php
// File: example17-10.php

class Person {
    private $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
    final function showName() {
        echo "<p>" . $this->strName . "</p>";
    }
}
class Student extends Person {
    function showName() {
    }
}
?>
```

The above example creates a Person class with a constructor and showName() method which has the prefixed keyword final:

```
class Person {
    private $strName;
    function __construct ($strName) {
        $this->strName = $strName;
    }
```