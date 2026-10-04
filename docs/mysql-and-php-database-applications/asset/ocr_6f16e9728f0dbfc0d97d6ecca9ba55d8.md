# Part II: Working with PHP

```
$c = 4.837; //this is a floating-point number
$d = "2"; //this is another string
```

Notice that = is the assignment operator. For comparison, you must use two consecutive equals signs (=). For example, if($x=-1).
PHP is flexible, and PHP is pretty smart about handling changes in types. For example, use the code you just saw, the following would evaluate as you'd prob- hope:

```
$e = $b + $d;
echo $e;
```

PHP would recognize that you want to treat the string in $d as an integer. The variable $e will be an integer type and will equal 6. In fact, PHP will also evaluate this as an integer:

```
$a = 2;
$b = "2 little piggies";
$c = $a + $b;
```

Here, $c will equal 4. If an integer or floating-point number is at the beginning of a string, PHP can evaluate it as such. Similarly, PHP will move smoothly among numeric types:

```
$f = 2; //$f is an integer
$g = 1.444; //$g is a double (floating-point) type
$f = $f + $g; //$f is now a double type
```

This kind of flexibility is nice, but it can lead to some difficulty. There will be times when you're not sure what variable types you are working with. We'll show how to deal with these circumstances in the section "Testing Variables."

# Delimiting Strings

In the preceding code, all strings were surrounded by double quotes. There are two other ways to delimit strings in PHP.
If you surround your strings with double quotes, variables within the string will be expanded. For instance:

```
$my_name = "Jay";
$phrase = "Hello, my name is, $my_name";
echo $phrase;
```