# Joining strings

You can join strings, a process called *concatenation*, by using a dot (`.`). For instance, you can join strings with the following statements:

```
```php
$string1 = 'Hello';
$string2 = 'World!';
$stringall = $string1.$string2;
echo $stringall;
```
```

The `echo` statement outputs

```
```text
HelloWorld!
```
```

Notice that no space appears between `Hello` and `World`. That’s because no spaces are included in the two strings that are joined. You can add a space between the words by using the following concatenation statement rather than the earlier statement:

```
```php
$stringall = $string1." ".$string2;
```
```

You can use `.= ` to add characters to an existing string. For example, you can use the following statements in place of the preceding statements:

```
```php
$stringall = "Hello";
$stringall .= " World!";
echo $stringall;
```
```

The `echo` statement outputs this:

```
```text
Hello World!
```
```

You can also take strings apart. You can separate them at a given character or look for a substring in a string. You use functions to perform these and other operations on a string. I explain functions in Chapter 7.

# Working with Dates and Times

Dates and times can be important elements in a Web database application. PHP has the ability to recognize dates and times and handle them differently than plain character strings. Dates and times are stored by the computer in a format called a *timestamp*. However, this is not a format in which you or I would want to see the date. PHP converts dates from your notation into a timestamp that the computer understands and from a timestamp into a format that is familiar to people. PHP handles dates and times by using built-in functions.