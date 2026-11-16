```
$item = $transaction->getItem();
$insertStmt = $insertStmt . "(" . $transaction->getUserId()
    . "','" . $item->getItemNo() . "','"
    . $transaction->getQuantity()
    . "','" . $transaction->getDate()
    . "','" . $transaction->getStatus() .
    "');
if ($i < (sizeof($transactions)-1)) {
    $insertStmt = $insertStmt . ",";
}
}
```

Excecute the INSERT statement:

```
if (!($result = mysql_query($insertStmt, $link))) {
    return new Function_Result("Internal Error: Could not
    execute SQL Query", null);
}
```

SQL statement to update the account balance of the user:

```
$updateBalanceStmt = "UPDATE UserProfile SET accountBalance = " .
    $accountBalance . " WHERE userId = " . "'" .
    $this->userId . "'";
```

Execute the UPDATE statement:

```
if (!($result = mysql_query($updateBalanceStmt, $link))) {
    return new Function_Result("Internal Error: Could not
    execute SQL Query", null);
}
return new Function_Result(null, null);
}
?>
```

# Loading Users

The script UserFactory.php contains functions for creating new users in the database and loading users from the database:

```
<?php
include_once("Common.php");
include_once("CreditCard.php");
include_once("ShippingAddress.php");
include_once("User.php");
```