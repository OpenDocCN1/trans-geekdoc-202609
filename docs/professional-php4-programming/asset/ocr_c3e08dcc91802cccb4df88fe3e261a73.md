For each retrieved row, add a Book_Item object to $searchResults array:

```
$searchResults[] =
	new Book_Item($row[0], $row[1], $row[2], $row[3], $row[4]);
}
mysql_free_result($result);
```

Return the $searchResults array:

```
return new Function_Result(null, $searchResults);
}
}
?>
```

# The Music_Shop Class

The script MusicShop.php contains the class definition of Music_Shop class:

```
<?php
include_once("Common.php");
include_once("MusicItem.php");

class Music_Shop
{
```

The function getItems() returns the contents of the MusicShop table as an array of Music_Item objects on success:

```
function getItems()
{

```

Get the database connection:

```
$functionResult = getDBConnection();
if ($functionResult->returnValue == null) {
	return $functionResult;
}
$link = $functionResult->returnValue;
```

SELECT query to retrieve all the music items from the database:

```
$musicShopSelectQuery = "SELECT itemNo, itemType, price, title,
	artist FROM MusicShop";
```

Execute the query:

```
if (!($result = mysql_query($musicShopSelectQuery, $link))) {
	return new Function_Result("Internal Error: Could not
	execute sql query ", null);
}
```