places. However, PHP stores and displays numbers in the most efficient format. If the number is 10.00, it is displayed as 10. To put numbers into the proper format for dollars, you can use sprintf. The following statement formats a number into a dollar amount:

```
$newvariablename = sprintf("%01.2f", $oldvariablename);
```

This statement reformats the number in $oldvariablename and stores it in the new format in $newvariablename. For example, the following statements display money in the correct format:

```
$price = 25;
$f_price = sprintf("%01.2f",$price);
echo "$f_price<br>";
```

You see the following on the Web page:

```
25.00
```

sprintf can do more than format decimal places. For more information on using sprintf to format values, see Chapter 13.

If you want commas to separate thousands in your number, you can use number_format. The following statement creates a dollar format with commas:

```
$price = 25000;
$f_price = number_format($price,2);
echo "$f_price<br>";
```

You see the following on the Web page:

```
25,000.00
```

The 2 in the number_format statement sets the format to two decimal places. You can use any number to get any number of decimal places.

# Working with Character Strings

A character string is a series of characters. Characters are letters, numbers, and punctuation. When a number is used as a character, it is just a stored character, the same as a letter. It can't be used in arithmetic. For instance, a phone number is stored as a character string because it only needs to be stored — not added or multiplied.

When you store a character string in a variable, you tell PHP where the string begins and ends by using double quotes or single quotes. For instance, the following two statements are the same.