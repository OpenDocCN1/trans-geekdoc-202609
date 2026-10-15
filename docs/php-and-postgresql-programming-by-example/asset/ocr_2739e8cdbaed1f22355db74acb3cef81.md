```
```
    }
    }
```
```

Save this code.

To test this class, we create PHP file, called **testcrud.php**. After that, we try to insert 10 data.

```
```php
<?php

include('CRUDDemo.php');

$obj = new CRUDDemo();

// insert 10 data
for($i=1;$i<=10;$i++) {
    $id = $obj->createEmployee("person " . $i,"depertment " . $i,"A".$i);
    echo "Inserted Id: " .$id . " \n";
    echo "Error message: " . $obj->getMsg() . " \n\n";
}
```
```

Save the code and try to run **testcrud.php**.

The following is sample running test on Intellij IDEA.

![](bbox=[0.06, 0.54, 0.94, 0.91])