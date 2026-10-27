```
```php
$db_Cursor = mysql_query($db_Query, $conn);
return $db_Cursor;
}

public static function DB_Fetch($db_Cursor)
{
return mysql_fetch_assoc($db_Cursor);
}

public static function DB_Query($db_Query, $conn)
{
$output = mysql_query($db_Query, $conn);
return mysql_num_rows($output);
}

public static function DB_Insert_Or_Update($db_Query, $conn)
{
$output = mysql_query($db_Query, $conn);
return intval(mysql_insert_id($conn));
}
}
?>
```
```

At this point, let’s “refactor” the carteProduct class and give it the essence of abstraction without actually making it abstract by using the __set(), __get(), and __isset() Magic Methods.

```
```php
Class CarteProduct
{
public function _construct(){}

function __set($Property_of_Carte, $value_Of_Property)
{
$this->$property_of_Carte = $value_Of_Property;
}

function __get($property_of_Carte)
{
if (isset($this->$property_of_Carte))
{
return $this->$property_of_Carte;
}
}
}
```
```

The CarteProduct class has been simplified and made more versatile, and it now works in conjunction with the restaurant database schema previously established. Rather than a Carte table, we'll need a CarteProduct table and a bridge table named CarteProductToCarte that associates a certain carte with a carteProduct. This design enables the appearance of a single carteProduct on several cartes, and as you may recall, leveraging interfaces enables us to alter the prices and serving sizes of carteProducts based on the cartes on which they appear. We'll, later on, revisit this restaurant carte application and add exception handling functionality.

Another useful implementation of static methods and attributes is the Singleton_design_pattern.

The Singleton_design_pattern bounds a class's capability to generate more than a single object.