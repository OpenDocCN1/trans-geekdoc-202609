Save this code.

Now we test this function on file **testcrud.php**. We delete data with ID = 30. You can change this ID.

```
<?php

include('CRUDDemo.php');

$obj = new CRUDDemo();

// delete
// delete data with id = 30. Please change it
$success = $obj->deleteEmployee(30);
echo "Success: " . $success . "\n";
echo "Error message: " . $obj->getMsg();
```

Save this code and run **testcrud.php**.

![](bbox=[0.06, 0.43, 0.94, 0.63])

You can verify by opening table **hrd_employee**. Data with ID = 30 should not show.