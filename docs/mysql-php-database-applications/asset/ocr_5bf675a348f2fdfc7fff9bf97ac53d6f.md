```
```php
$array = array("name" => "Jay".
               "brand" => "Cohiba");
extract($array, "name");
echo $name;
```
```

will output this:

Jay

The extract_type_constant argument controls how namespace collisions are handled. The constant takes any of eight predefined values (see the PHP manual page on this at http://php.net/extract) such as EXTR_OVERWRITE and EXTR_SKIP. These dictate what the parser should do when it encounters collisions.

# NUMBER_FORMAT()

```
string number_format (float number [, int decimals [, string dec_point , string thousands_sep]])
```

Given a floating-point number, this function returns a string formatted for human consumption, containing the number with thousands separators and a decimal separator. By default these are a comma and a dot, respectively, but other symbols can be specified.

# JOIN()

```
string join (string glue, array pieces)
```

Given an array and a string, join() returns a string comprised of the elements of the array concatenated in order, with the glue string between each two elements.

join() is identical to the implode() function.

# RANGE()

```
array range (mixed from, mixed to [, int increment])
```

This function creates an array and automatically populates it with elements ranging from from to to. If a step increment is specified in the third argument, that will be the increment between elements; otherwise the increment will be one.