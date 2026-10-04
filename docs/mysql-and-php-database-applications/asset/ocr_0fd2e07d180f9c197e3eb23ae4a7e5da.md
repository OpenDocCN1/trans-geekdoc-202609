# Chapter 5: Control Structures 99

| Symbol | example | Description |
| --- | --- | --- |
| or | if ($a ==0 or $b ==1) | Determines one or the other meets the condition. |
| || | if ($a ==0 || $b ==1) | Same as the previous row, but has a higher precedence (see Note below) |
| xor | if ($a ==0 xor $b ==1) | This is known as "exclusive or". determines if one of the two is true but not both. If both of these conditions are true, the overall test will be false |
| ! | if (!empty($a)) | Determines something is not the case. In this example the condition will be true if $a has a value |

![](bbox=[0.181, 0.446, 0.258, 0.497])

The difference between && and is their order of precedence. PHP must determine which operators to compare first. It does this on the list found at http://www.php.net/manual/language.operators. precedence.php.

# Complex if statements

Using the operators in Table 5-1 and 5-2 you can create statements that are a bit more complex than the basic one at the beginning of this chapter. Here are a few examples:

```
if ($var == 1 && $var2 <=5 && !empty($var)) {
    //do some stuff
}
```

Since this is a book dealing with MySQL databases, we'll show some examples of if statements you can use when playing with database queries.
To test a select query returned any rows, you could use either of the following:

```
$query = "select * from my_table";
$result = mysql_query($query)or
die(mysql_error());
if (mysql_num_rows($result) >0) {

```