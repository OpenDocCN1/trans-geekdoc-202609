```
$a = stripslashes($a);
echo "<br />Without: " . $a;
?>
```

# Listing 7.29 Escaping with Backslash ("addslashes.php")

Slightly more flexible than addslashes() is the addcslashes(string, character) function. It adds backslashes to all characters that are specified as parameters in the string character.

```
addcslashes($a, " 'n")
```

therefore places a backslash before double quotation marks and before n (see Figure 7.15).

![](bbox=[0.145, 0.345, 0.755, 0.475])

Figure 7.15 Top with Backslashes, Bottom Without

> **Note**
> 
> The reverse conversion is performed with stripslashes(String). However, special characters such as \n are ignored. This means that if you were to use addcslashes($a, 'n'), you would still have line breaks in the source code instead of all n's after the reverse conversion. If you want to avoid this effect, use stripslashes(). This removes all backslashes.

# 7.6.2 Escaping for Regular Expressions

Like SQL, regular expressions use their own special characters, which should therefore be escaped in a string. The quotemeta(String) function is responsible for this.12 The following characters are escaped with a backslash:

+   . \\ * + ? [ ^ ] ( $ )

Consider the following simple example.