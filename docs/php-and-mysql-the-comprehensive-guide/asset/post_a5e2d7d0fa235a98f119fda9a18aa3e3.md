
The regular expression must be enclosed in two identical simple symbols. By default, the symbol is the slash (/). Alternatively, pairs of brackets such as ( ) can also be used. If you use this symbol also in the regular expression, you have to escape it with a backslash (\).

The regular expression for the following example checks whether the string is a correct date for the last and current century in the form MM/DD/YYYY. The fact that days and months can only be written with one digit is also taken into account. In this case, the return value is 1 because it is a correct date and the defined format is found in the string accordingly.

```php
<?php
$date = "03/02/2028";
$reg = "/^(0?[1-9]|1[0-2])\/(0?[1-9]|[12]\\d|3[01])\/((19|20)?\\d{2})$/";
print preg_match($reg, $date);
?>
```

### Listing 10.1 “preg_match()” (“preg_match.php”)

With preg_match(RegEx, String, Variable), you can specify a variable as the third parameter, which then takes the individual parts of the string as an array.

```php
<?php
$date = "03/30/2028";
$reg = "/^(0?[1-9]|1[0-2])\/(0?[1-9]|[12]\\d|3[01])\/((19|20)?\\d{2})$/";
if (preg_match($reg, $date, $parts)) {
    print $parts[2] . ". . " . $parts[1] . ". . " . $parts[3];
}
?>
```

### Listing 10.2 “preg_match()” with Variable (“preg_match_parts.php”)

The variable, in this case $parts, is an array. The first index 0 contains all components; from 1 the brackets start. Incidentally, this matches the specifications in the regular expressions, where you also access the first bracket with \1.

preg_match(RegEx, String, Variable, Mode, Start_Position) recognizes Mode as the fourth option and Start_Position as the fifth. The mode can only have one value—namely, PREG_OFFSET_CAPTURE. If this is activated, not only the location in the variable array but also the position is returned (see Figure 10.1):

```php
$text = "Hello all!";
$reg = "//";
preg_match($reg, $text, $parts, PREG_OFFSET_CAPTURE);
```

![](img/ae7820c36e8f24c1623d26668b28e80e_297_0.png)

Figure 10.1 The Array with the Location and the Position in the String

The fourth parameter, String position, defines the string or position from which the search starts. Consider the modified example:

```php
$text = "Hello all!";
$reg = "/ll/";
preg_match($reg, $text, $parts, PREG_OFFSET_CAPTURE, 5);
```

The regular expression finds the second occurrence of ll, as it only searches from the fifth position in the string. Figure 10.2 shows the result.

![](img/ae7820c36e8f24c1623d26668b28e80e_297_1.png)

Figure 10.2 Here You Can See Start Position 7

preg_match() only ever finds the first occurrence of a search string. A more flexible option is preg_match_all(). You can see its output in Figure 10.3.

```php
<?php
$text = "Hello all!";
$reg = "/ll/";
preg_match_all($reg, $text, $parts, PREG_OFFSET_CAPTURE);
print_r($parts);
?>
```

### Listing 10.3 "preg_match_all()" ("preg_match_all.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_297_2.png)

Figure 10.3 "preg_match_all()" Finds Both Occurrences

However, preg_match_all(RegEx, String, Variable, Mode) has other values for the mode: PREG_PATTERN_ORDER and PREG_SET_ORDER. You can combine both with PREG_OFFSET_CAPTURE by writing the modes one after the other, separated by |. The default is PREG_PATTERN_ORDER if the specification is missing. The patterns found are saved as an array in the first array element of the variable (index 0). In the second and subsequent elements, the locations for parts of the pattern divided by brackets are specified.

Here is a small example to illustrate this:

```php
$text = "Otto";
$reg = "/(Ot|ot)|(to|tt)/";
preg_match_all($reg, $text, $parts, PREG_PATTERN_ORDER);
```

This returns Ot and to as the result of all pattern checks. The individual areas each provide one result (see Figure 10.4).

![](img/ae7820c36e8f24c1623d26668b28e80e_298_0.png)

Figure 10.4 The Individual Components

PREG_SET_ORDER, on the other hand, orders the results so that the first array element corresponds to the results of the first bracket, the second to those of the second, and so on (see Figure 10.5).

```php
<?php
$text = "Otto";
$reg = "/(Ot|ot)|(to|tt)/";
preg_match_all($reg, $text, $parts, PREG_SET_ORDER);
print_r($parts);
?>
```

### Listing 10.4 Options for "preg_match_all()" ("preg_match_all_opt.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_298_1.png)

Figure 10.5 The Two Results of the Individual Components

## 10.2.2 Further Functions

In addition to preg_match(), there are several other functions that allow further operations in addition to the simple search, as listed in Table 10.1.

| Function | Description |
| :--- | :--- |
| preg_split (RegEx, String, Limit, Mode) | Splits a string at the separators specified as the RegEx pattern. Returns an array whose individual elements are the components without separators. If Limit is set, only the number of separators specified there is executed. The last element then contains the rest of the string. -1 means no limit. You need this if you set a mode as the last parameter. The following options are available here: PREG_SPLIT_NO_EMPTY omits empty parts when splitting. PREG_SPLIT_DELIM_CAPTURE also returns individual results from areas of the RegEx in brackets. PREG_SPLIT_OFFSET_CAPTURE returns the position. |
| preg_replace (RegEx, replacement, element, limit, number) | Replaces the pattern with the replacement. The function returns the result. The limit specifies how many replacements are to be performed. Number returns the number of replacements. preg_replace() also replaces expressions in arrays: `$data = array("Hanno", "Anne"); $reg = "/nn/"; $result = preg_replace($reg, "ll", $data);` In the $result array, Hanno becomes Hallo and Anne becomes Alle. |
| preg_replace_callback (RegEx, function, element, limit, number) | Works like preg_replace(), except that this function executes a function instead of a replacement string. |
| preg_grep (RegEx, Array, Mode) | Searches for a regular expression within an array. Returns an array with the results. You can specify PREG_GREP_INVERT for the optional mode parameter. The elements that are not contained in the array are then returned. |
| preg_quote (expression, separator) | Evaluates the pattern characters of the regular expression. As an optional second parameter, you can specify a character to be used as a separator before and after the regular expression. This is usually the slash (/). |

Table 10.1 Perl-Compatible RegEx Functions

## 10.2.3 Reuse Replacement Strings

You can define several search strings in a regular expression with round brackets. This helps when replacing as you can "find" individual search strings again and then reformat them, for example. The following example changes a name in the form "First name last name" to the variant "Last name, first name", as shown in Figure 10.6.

```php
$name = "Ann Meyer";
$name_rotated = preg_replace("/([a-z]+)\s+([a-z]+)/i", "\\2, \\1", $name);
echo $name_rotated;
```

![](img/ae7820c36e8f24c1623d26668b28e80e_300_0.png)

Figure 10.6 The Name "Rotated" by a Regular Expression

> Note
> The example here is not perfect; the expression would fail if there were several first names, for example.

## 10.2.4 Modifiers for Search Patterns

There are several modifiers for regular expressions that change the behavior of the RegEx engine. One example is i. If you insert this character after the end character, then the regular expression is not case-sensitive. The following expression therefore assumes a and A:

/a/i

In addition to the letter for the modifier, there is also an internal designation. For i, for example, this designation is PCRE_CASELESS.

Here are two more examples:

- x (PCRE_EXTENDED) ignores empty spaces in search patterns.
- U (PCRE_UNGREEDY) switches a regular expression to be "not greedy." This means that quantifiers such as \d, even without maximum quantity specifications, do not return all the characters following them, but only the first one.
