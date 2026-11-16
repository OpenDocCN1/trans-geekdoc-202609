Now let's see how the Polish function is implemented:

```
```php
<?php
class Polish_Output extends Basic_Output
{
    function outNumFiles($count)
    {
        if ($count == 0) {
            return "Nie ma plików.";
        } elseif ($count == 1) {
            return "1 plik.";
        } elseif ($count <= 4) {
            return "$count pliki.";
        } elseif ($count <= 21) {
            return "$count plików.";
        } else {
            $last_digit = substr($count, -1);
            if ($last_digit >= 2 && $last_digit <= 4) {
                return "$count pliki.";
            } else {
                return "$count plików.";
            }
        }
    }
}
?>
```
```

The Polish object doesn't use the $string array declared in the parent class, because the outNumFiles( ) function provides all the strings itself. Although we're trying to separate the string from the code, we have here an example of the exact opposite. The reason for this is that it's only the core of the application that should be without hard-coded strings. The locales are free to override the methods in the base class how they want – they might use the $strings array, or they might hard-code the strings in the code, as above.

Even if the above method doesn't use the $strings array, it doesn't mean that other methods can't use it. In that case, the class would have to have a constructor that fills in the strings just like the Danish output class.

We use the Polish object just like we used the English and Danish objects:

```
```php
$obj = new Polish_Output();
echo($obj->outNumFiles(7)); // 7 plików.
```
```

Note that all the code from above can be downloaded from the Wrox web site at http://www.wrox.com/. The full example that uses all three objects is saved as object2.php, while all the classes are saved as className.php.