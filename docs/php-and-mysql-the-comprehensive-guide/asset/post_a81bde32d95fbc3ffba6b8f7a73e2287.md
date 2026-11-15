
## 7.5.2 Replace

There are also several functions for replacing parts of a string. They differ mainly in how much they replace.

### Replace at Position

The substr_replace(String, replacement, start position, length) function works like its little brother substr(), except that the specified range is not cut but replaced. The length is optional, and negative values are possible for both the start position and the length.

The following script replaces red with blue.

```php
<?php
$a = "The red riders.";
echo substr_replace($a, "blue", 4, 3);
?>
```

### Listing 7.24 "substr_replace()" ("substr_replace.php")

### Search and Replace

The str_replace(search string, replacement, string) function is the "small" alternative to search and replace with regular expressions. It has several advantages: it is performant, as it is based on a binary comparison, and it is easy to remember. The first parameter contains the search string. The second contains the replacement for the position found, and the third is the string in which the search and replacement takes place.

```php
<?php
$a = "Jippiieejoy";
echo str_replace("e", "i", $a);
?>
```

### Listing 7.25 "str_replace()" ("str_replace.php")

> **Note**
> Note that the parameter sequence for string functions in PHP is unfortunately not standardized. Here, for example, the string in question is at the end.

In the preceding code above, all ‘e’s are replaced by ‘i’s.

> **Tip**
> A quick search and replace is very suitable for placeholders in your code, for example.

In addition to simple strings, `str_replace()` also supports arrays for all three parameters. In Listing 7.26 and Figure 7.14, you can see an example.

```php
<?php
$a = "Jippieejey";
$b = "Holadrioe";
$result = str_replace(array("e", "o"), array("i", "ö"), array($a, $b));
print_r($result);
?>
```

### Listing 7.26 “str_replace()” with Arrays (“str_replace_array.php”)

![](img/ae7820c36e8f24c1623d26668b28e80e_220_0.png)

## Figure 7.14 Wild String Switching

> **Note**
> str_ireplace(search string, replacement, string) is the case-insensitive variant of str_replace() and otherwise identical in construction.

### Replace Multiple Characters

The `strtr(String, From, In)` function works like `strpbrk()`. It searches for characters specified in a string (From) and replaces them with characters entered in a second string (In). Consider the following simple example.

```php
<?php
$a = "Jippieejey";
echo strtr($a, "ei", "ie");
?>
```

### Listing 7.27 “strtr()” in use (“strtr.php”)

Here, Jippieejey becomes Jeppiiijiy.

> **Note**
> If there are not the same number of characters in the From string and the In string, then the excess characters on one side are ignored.

strtr(String, Array) has a second syntax with an associative array. In this case, the index of the respective array element is the From and the value is the In. The following script therefore has the same effect as Listing 7.27, but with an associative array.

```php
<?php
$a = "Jippiieejey";
echo strtr($a, array("e"=>"i", "i"=>"e"));
?>
```

### Listing 7.28 "strtr()" with Associative Array ("strtr_asso.php")

## 7.6 Special Characters, HTML, and the Like

Regardless of whether you are working with HTML, database queries, or files, you will always encounter special characters. PHP already offers ready-made functions for the most important areas of application.

### 7.6.1 Escaping for Databases

For database queries, you must escape certain characters.11 This is done with the backslash (\). The addslashes(String) function inserts a backslash before single and double quotation marks, backslashes, and null values. When you write a string as a value in a database, you will often use this function so that the characters mentioned are not interpreted by SQL as belonging to the syntax. However, most database interfaces in PHP have their own invalidation functions. These are generally preferable to addslashes().

To undo addslashes(String), use stripslashes(String). The following simple example uses both.

```php
<?php
$a = 'Caesar said: "I came, I saw, I conquered!"';
$a = addslashes($a);
echo "With backslash: " . $a;
$a = stripslashes($a);
echo "<br />Without: " . $a;
?>
```

11 Incidentally, various terms can be used for this process. In addition to escaping, masking or even commenting out can also be used.

### Listing 7.29 Escaping with Backslash ("addslashes.php")

Slightly more flexible than addslashes() is the addcslashes(string, character) function. It adds backslashes to all characters that are specified as parameters in the string character.

`addcslashes($a, " 'n")`

therefore places a backslash before double quotation marks and before n (see Figure 7.15).

![](img/ae7820c36e8f24c1623d26668b28e80e_222_0.png)

## Figure 7.15 Top with Backslashes, Bottom Without

> **Note**
>
> The reverse conversion is performed with stripslashes(String). However, special characters such as \n are ignored. This means that if you were to use addcslashes($a, 'n'), you would still have line breaks in the source code instead of all n's after the reverse conversion. If you want to avoid this effect, use stripslashes(). This removes all backslashes.

### 7.6.2 Escaping for Regular Expressions

Like SQL, regular expressions use their own special characters, which should therefore be escaped in a string. The quotemeta(String) function is responsible for this.12 The following characters are escaped with a backslash:

- .
- \
- *
- +
- ?
- [
- ^
- ]
- (
- $
- )

Consider the following simple example.

```php
<?php
$a = "Results in 50 * (5 - 3) 100?";
echo quotemeta($a);
?>
```

### Listing 7.30 "quotemeta()" ("quotemeta.php")

![](img/ae7820c36e8f24c1623d26668b28e80e_223_0.png)

## Figure 7.16 All Relevant Characters Are Commented Out

> **Tip**
> To convert back, simply use stripslashes().

### 7.6.3 HTML

HTML is a special—or you could also say, a strange—language. By definition, the browser does not recognize anything that does not fit into a simple character set. Entities13 are available for special characters. These include German umlauts, for example. PHP offers several functions for handling special characters in particular.

#### Convert Special Characters

All HTML-relevant special characters in a string can be converted with the htmlentities(String) function. In the following listing, we compare umlauts and double quotation marks with and without conversion.

```php
<?php
$a = 'Umlauts: "Ä", "ä", "Ö", "ö", "Ü", "ü"; echo "Without conversion: " . $a . "<br />\n";
echo "With conversion: " . htmlentities($a);
?>
```

### Listing 7.31 With and without Conversion ("html.php")

13 An entity is to be understood here as a prefabricated character string that stands as a placeholder for a special character. Entities in HTML always begin with the ampersand and end with a semicolon. For example, &auml; stands for ä. The abbreviation is even easy to understand: auml means a umlaut.

In a browser with the default language set to German, both variants are displayed identically. This is not the case in a browser with the default language set to English. However, you can already see the difference in the source code (see Figure 7.17). The quotation marks and the umlauts have become HTML entities.

![](img/ae7820c36e8f24c1623d26668b28e80e_224_0.png)

![](img/ae7820c36e8f24c1623d26668b28e80e_224_1.png)

## Figure 7.17 Convert Umlauts to HTML Special Characters

> If you are developing a guestbook, for example, then you should always convert the user input into special HTML characters before outputting it. This will also remove any HTML tags used by the user that could destroy the layout of the page14 or even be used for malicious scripts.15 If you want to allow formatting in the guestbook, then you must filter more precisely.

htmlentities(string, quotation marks, character set) offers two optional parameters. For quotation marks, you can set how double and single quotation marks are handled in a constant:

- ENT_QUOTES converts all quotation marks.
- ENT_NOQUOTES leaves all quotation marks as they are.
- ENT_COMPAT only converts double quotation marks to HTML special characters. This is the default value.

`htmlentities($a, ENT_NOQUOTES)`

prevents quotation marks from being converted. Instead of &quot;, you will see the double quotation mark in the source text.

14 In terms of web security, this is referred to as defacement.
15 This is called cross-site scripting.
