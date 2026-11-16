SELECT query to retrieve book information for item number $itemNo:

```
$bookShopSelectQuery = "SELECT itemNo, itemType, price,
title, author FROM BookShop
WHERE itemNo='". $itemNo . '".";
```

Execute the query:

```
if (!($result = mysql_query($bookShopSelectQuery, $link))) {
 return new Function_Result("Internal Error: Could not
execute sql query ", null);
}
```

Fetch the row from the result of the query:

```
$row = mysql_fetch_array($result, MYSQL_NUM);
if ($row == null) {
 return new Function_Result(null, null);
} else {
```

Create a Book_Item object for the retrieved row:

```
$item =
 new Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
```

Return Book_Item object:

```
return new Function_Result(null, $item);
}
```

The function search() returns Book_Item objects which contain $searchText in author or title column:

```
function search($searchText)
{
```

SELECT statement retrieves the book items which contain $searchText in author or title column:

```
$searchStmt = "SELECT itemNo, itemType, price, title, author FROM
 BookShop WHERE author LIKE '%" . $searchText . "%' OR
 title LIKE '%" . $searchText . "%'";
```

Call getSearchResults() function to execute the $searchStmt SQL query:

```
$funcResult = $this->getSearchResults($searchStmt);
```