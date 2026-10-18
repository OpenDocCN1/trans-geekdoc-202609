FIGURE 11.16 Implementing a stack

![](bbox=[0.218, 0.088, 0.914, 0.321])

# Counting occurrences

If an array contains a number of identical elements you may wish to count the numbers of each of them. Function array_count_values() can be used to do this and it looks like this:

```
`array array_count_values(array)`
```

The function requires an array as a parameter and returns an array of the results. The following script illustrates the use of the function:

```
```php
<?php
// File: example11-23.php
$arrColors = array ("Red", "Green", "Blue", "Yellow", "White",
                    "Yellow", "Green", "Blue", "Yellow", "Grey",
                    "Red", "Yellow", "Blue", "Yellow", "White");
$arrCount = array_count_values($arrColors);

foreach($arrCount as $strColor=>$intCount)
    echo "<p>$strColor occurs $intCount times</p>";
?>
```
```

The above script declares and populates an array:

```
```php
$arrColors = array ("Red", "Green", "Blue", "Yellow", "White",
                    "Yellow", "Green", "Blue", "Yellow", "Grey",
                    "Red", "Yellow", "Blue", "Yellow", "White");
```
```

The array_count_values() function is invoked creating a new array indexed on the number of occurances:

```
```php
$arrCount = array_count_values($arrColors);
```
```

The new array is then displayed:

```
```php
foreach($arrCount as $strColor=>$intCount)
    echo "<p>$strColor occurs $intCount times</p>";
```
```

The output produced from the above script is illustrated in Figure 11.17.