For each retrieved row create a transaction object and add the object to $transactions array:

```
$item = new Book_Item($row[0], $row[7], null, $row[1], $row[2]);
$transaction = new Transaction($this->userId, $item, $row[3],
        $row[4], $row[5], $row[6]);
$transactions[] = $transaction;
}
mysql_free_result($result);
```

The SELECT statement to retrieves the details of music item transactionqs of the user:

```
$selectStmt = "SELECT Transaction.itemNo, title, artist, quantity,
        date, status, orderNo, itemType
        FROM MusicShop, Transaction
        WHERE MusicShop.itemNo = Transaction.itemNo
        AND userId = " . "'" . $this->userId . "'";

// Execute the query
if (!($result = mysql_query($selectStmt, $link))) {
        return Function_Result("Internal Error: Could not
                execute sql query", null);
}

while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```

For each retrieved row, create a transaction object and add the object to $transactions array:

```
$item = new Music_Item($row[0], $row[7], null,
        $row[1], $row[2]);
$transaction = new Transaction($this->userId, $item,
        $row[3], $row[4],
        $row[5], $row[6]);
$transactions[] = $transaction;
}
mysql_free_result($result);
return new Function_Result(null, $transactions);
}
```

The function saveTransactions () saves the account balance and the transactions of the user:

```
function saveTransactions($accountBalance, $transactions)
{
        // Get DB Connection
        $functionResult = getDBConnection();
        if ($functionResult->returnValue == null) {
                return $functionResult;
        }

        $link = $functionResult->returnValue;
```

The following SQL statement is used to insert the transactions in the Transaction table:

```
$insertStmt = "INSERT INTO Transaction(userId, itemNo,
        quantity, date, status) VALUES ";
for($i=0; $i < sizeof($transactions); $i++) {
        $transaction = $transactions[$i];
```