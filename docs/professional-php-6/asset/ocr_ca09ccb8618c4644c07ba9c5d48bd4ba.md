In addition, the pre-packaged constraint types supplied here are not exhaustive. However, a quick glance at the code should make it quite clear how easily you can add your own, should your application require them.

# Constants

You do need to define a number of constants in order for your classes to work seamlessly together. They define the three types of parameter (GET, POST, and Cookies), as well as the various types of constraint you can apply. As previously mentioned, you should feel free to define additional constraints that may suit your application, as long as you also remember to implement them in the Request class.

Examine the following code and save it in a file called constants.phpm:

```
<?php // Constants

define(VERB_METHOD_COOKIE, 1);
define(VERB_METHOD_GET, 2);
define(VERB_METHOD_POST, 4);
define(CT_MINLENGTH, 1);
define(CT_MAXLENGTH, 2);
define(CT_PERMITTEDCHARACTERS, 3);
define(CT_NONPERMITTEDCHARACTERS, 4);
define(CT_LESSTHAN, 5);
define(CT_EQUALTO, 6);
define(CT_MORETHAN, 7);
define(CT_NOTEQUALTO, 8);
define(CT_MUSTMATCHREGEXP, 9);
define(CT_MUSTNOTMATCHREGEXP, 10);
?>
```

Note the two numbering schemes as an approach in defining these constants. These are an _exponential sequence_ to define the three verbs of parameters offered in an HTTP request, and a purely _sequential sequence_ to define the constraint types.

The reason for the two differing approaches touches briefly on the properties of _bitwise logic_. Because this subject has not been touched upon elsewhere in the book, let’s take a brief look at it here.

Consider the following piece of code:

```
$var3 = ($var1 && $var2);
```

The conditional statement here clearly requires that $var1 is true (either literally, or as some nonzero or non-empty value), and that $var2 is true (employing traditional use of the && operator to express Boolean logic). If both are true, $var3 will also be true. This if fairly basic, but there is a second form of comparison logic that uses the same basic operators, AND and OR.

Consider the following:

```
$var3 = ($var1 & $var2);
```

Note the single ampersand. This indicates that you want to perform bitwise (rather than Boolean) logic to effect the comparison. What then takes place (assuming that $var1 and $var2 are integers) is that the