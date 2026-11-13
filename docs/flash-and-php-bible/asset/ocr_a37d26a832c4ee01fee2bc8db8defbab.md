Before the method is created, you must load in the Database connection, exactly like you did in the Video class.

```
require_once 'DatabaseConnector.php';
```

The first part of the getCategories method is responsible for creating a new $rows variable that will hold the categories returned from the database. The link variable is filled with an active database connection, which will be used in the following SQL calls.

```
$rows = array();
$link = $this->getConnection();
```

The SQL query basically pulls in all the categories that are active, meaning the active column is set to a value of 1. This SQL query is then passed into mysql_query which is responsible for actually executing the SQL call.

```
$query = "SELECT id, name FROM categories WHERE active=1";
$result = mysql_query($query, $link);
```

The if statement checks for at least one valid row before continuing and will throw an error if no valid rows are found. Assuming valid rows are found, a while loop is used to fill the $rows variable and once the loop is complete the $rows variable is returned.

```
if (mysql_num_rows($result) == 0)
{
    trigger_error("No categories found");
    return false;
}
```

```
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    array_push($rows, $row);
}
```

```
return $rows;
```

That is all there is to the Category class, and as you can see the structure of the Category class is fairly similar to the Video class in the previous section.

Here is the completed Category class:

```
<?php

require_once 'DatabaseConnector.php';

class Categories extends DatabaseConnector
{

    /**
     * get categories
```