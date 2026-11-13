Media, 2004). Perhaps more interestingly, you can easily convert this function into an object-oriented table formatter. Instead of explicitly declaring a state variable, you can make a class with a private variable to keep track of the state. The constructor and destructor open and close the table tags, respectively. Here's what the class looks like:

```
```php
class AltTable {
  function __construct() {
    $this->state = 0;
    print "<table>";
  }
  function __destruct() {
    print "</table>";
  }
  function print_row($row) {
    if ($this->state & 1) {
      $row_color = "row2";
    } else {
      $row_color = "row1";
    }
    print "<tr class=\"$row_color\">";
    foreach ($row as $value) {
      print "<td>$value</td>";
    }
    print "</tr>";
    $this->state++;
  }
}
```
```

And here's how to use the class (assume that the query is the same as the preceding example):

```
```php
$mytable = new AltTable;
while($row = mysql_fetch_row($result)) {
  /* Print results. */
  $mytable->print_row($row);
}
unset($mytable);
```
```

At first glance, you may think that this is great because it's a little easier to use—you don't have to mess with a state variable, the print_row() method can handle any number of columns, and you don't even have to write any HTML to start and finish the table. This is certainly a great advantage if all your tables look the same. However, this tidiness is at the cost of flexibility and some efficiency. Sure, you can add methods and attributes to do some fancy stuff such as add table headers, but you need to ask yourself if it's really worth it.