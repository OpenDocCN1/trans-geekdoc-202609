```
}
}
?>

```

The namespace Clients; line declares that the Person class is part of the Clients namespace. By declaring namespace Customers;, all classes defined in this PHP file belong to the Clients namespace. So, to use the Person class in another file, you need to import this namespace with the use directive.

In the Person.php file in the Students directory :

```
<?php

namespace Students;

class Person {
public function __construct($name, $email){
$this->name = $name;
$this->email = $email;
}

public function getStudentInfo(){
echo "Name: $this->name,
Email: $this->email";
}
}

```