Each character and its entity are available as key=>value pairs in an associative array. The resulting array can be of use with the strtr() function.

# NUMBER_FORMAT()  This function formats a number to your specifications.

```
string number_format (float number, int decimals, [[string dec_point], [string thousands_sep]])
```

The fist argument will be the number you wish to format. The second argument will state the number of digits you would like after the decimal point. You can use this function with just these two arguments. For example,

```
echo number_format( (10/3), 2 );
```

will print “3.33”, and

```
echo number_format(1000,2);
```

will print “1,000”. Note that if there are two arguments, number_format() includes a comma as a thousands separator.

In the third and fourth arguments you can include a decimal point separator and a thousands separator, respectively. For example,

```
echo number_format( 10000.67, 2, "&", "R");
```

will print, 10R000&67.

![](bbox=[0.18, 0.6, 0.26, 0.68])

> If number_format() doesn't cut it for you, you can make use of PHP's sprintf(),printf(),and scanf() functions. If you have a background in Perl or C you probably know how these functions work. They're powerful, complex, and take a good deal of time to get used to. If you want to familiarize yourself with these functions, take a look at the PHP manual (http://www.php.net/manual/function.sprintf.php) and this tutorial: http://wdvl.com/Authoring/Scripting/Tutorial/perl_printf.html.

# HELPFUL STRING FUNCTIONS NOT USED IN THIS BOOK

Just because we didn't use them doesn't mean you won't. And again, it's entirely possible that something we didn't cover will suit your needs perfectly. Please look over the PHP manual for a complete list.