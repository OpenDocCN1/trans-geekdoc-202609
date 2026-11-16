The function getItems() returns the contents of the BookShop table as an array of Book_Item objects on success:

```
```
function getItems()
{
```
```

Get the database connection:

```
```
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
    return $functionResult;
}
$link = $functionResult->returnValue;
```
```

SELECT query to retrieve all the books from the database:

```
```
$bookShopSelectQuery = "SELECT itemNo, itemType, price,
title, author FROM BookShop";
```
```

Execute the SQL query:

```
```
if (!($result = mysql_query($bookShopSelectQuery, $link))) {
    return new Function_Result("Internal Error: Could not
execute sql query ", null);
}
$bookShopContent = null;
while (($row = mysql_fetch_array($result, MYSQL_NUM))) {
```
```

For each retrieved row, add a Book_Item object to the $bookShopContent array:

```
```
$bookShopContent[] = new
    Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
}
mysql_free_result($result);
```
```

Return $bookShopContent:

```
```
return new Function_Result(null, $bookShopContent);
}
```
```

The function getItem() returns the Book_Item object corresponding to item number $itemNo:

```
```
function getItem($itemNo)
{
// Get DB Connection
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
    return $functionResult;
}
$link = $functionResult->returnValue;
```
```