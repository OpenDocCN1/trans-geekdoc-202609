```
```php
<?php
$data = array(
    'Sams Publishing',
    '800 East 96th Street',
    'Indianapolis',
    'Indiana',
    '46240'
);
$address = implode('<br />', $data);
echo $address;
?>
```
```

*Turning an Array into a String (implode.php)*

# Sorting Arrays Alphabetically

```
```php
sort($a, SORT_NUMERIC);
sort($a, SORT_STRING);
```
```

Numerical arrays can be sorted rather easily by using `sort()`. However, a problem exists if the array contains both numerical and string values (for instance, "2" > "10" but 2 < 10). Therefore, the sorting can be tweaked so that a special data type is used for comparing elements when sorting:

+   - `SORT_NUMERIC` sorts elements as numbers
+   - `SORT_REGULAR` sorts elements according to their data type (standard behavior)
+   - `SORT_STRING` sorts elements as strings

```
```php
<pre>
<?php
$a = array('4', 31, '222', 1345);
sort($a, SORT_NUMERIC);
```
```