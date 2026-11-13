$my_array will have three elements: $my_array[0] => 24 $my_array[1] => 16 $my_array[2] => 9,54,21,88,17. You can see that the last element contains what's left of the original string. If you want to sort that contains only the first three elements in a string and discard the rest you might do this:

```
$str = "24,16,9,54,21,88,17";
//turn $str into an array
$array = explode(",", $str, 4);
unset($array[3]);
sort($array, SORT_NUMERIC);
echo implode(",", $array);
```

If the string separator does not exist, the entire string will be placed in array element zero. If the string does not exist, an empty string will be placed in the first element.

IMPLODE() As you might expect, implode() is the opposite of explode(): It turns an array into a string.

```
string implode (string glue, array pieces)
```

The first argument is the string that will separate the string elements. The second is the array to be separated.

A good example of where you might use implode() is a page that runs a SQL delete command. Suppose you have presented a series of checkboxes to indicate the rows you wish to delete from the database. You are probably going to want to pass the elements you wish to delete within an array. In the script that does the deletes, you can then run something like this:

```
//say $delete_items from an HTML page and
//contains (1,3,7)
if (is_array($delete_items"))
{
    $str = implode(",", , $delete_items);
    $query = "delete from table where item_id in ($str)";
    mysql_query($query);
}
```

SPLIT() The split() function does the same thing as explode(), but it enables you to specify a regular expression as the separation string.

```
array split (string pattern, string string [, int limit])
```