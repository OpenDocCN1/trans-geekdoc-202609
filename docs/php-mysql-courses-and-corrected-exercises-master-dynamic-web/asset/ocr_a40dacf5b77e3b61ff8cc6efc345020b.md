![](bbox=[0.041, 0.042, 0.953, 0.392])

# Read access to an object's private properties

Access to an object's private properties is an important concept in object-oriented programming (OOP). Let's modify the Users class as follows:

```
<?php
class Users {
 private $name = "Dupont" ;
 private $firstname = "Karine" ;
 private $age = 27 ;
 private $email = "dupont-karine@gmail.com" ;
}
```