```
$coolmammal = &$manatee;
$coolmammal = 70;
print "$manatee<br>\n";
?>
```

Look at the third set of lines. I changed what $coolmammal refers to.
Previously, it referred to $platypus. But when the PHP processor runs
the line $coolmammal = &$manatee;, $coolmammal will then be an alias
for $manatee.

In C++, you're not allowed to unset a reference variable — that is, make the
reference refer to another variable — at least not by the ANSI C++ standard.
(Some older compilers allowed you to do so.) In PHP, you can unset a vari-
able name and have it refer to a different variable. Just run another &= line.

# Processing Strings

The PHP language includes excellent support for strings. But even better is
the set of additional string-processing functions.

The PHP string library includes many string functions, some of them very
specialized. Check out www.php.net/strings for the whole list. (In the sec-
tions that follow, I discuss some of the more useful ones.)

# Doin' the C-style printf thing

If you're either an old C-hack like myself, or if you just like to format strings
during your free time, you'll appreciate the PHP printf function. I will
assume that you're familiar with printf in other languages here. If not, take
a look at www.php.net/sprintf for more information (yes, this is sprintf
with an s, which is a slightly different version, but the same rules apply).
The printf in PHP has all the usual goodies. Here's an example:

```
<?php
$mynum = 100;
$mystr = "Greetings Planet Earth";
$myfloat = 3.1415926;
printf ("%s from 0x%x on behalf of %f<br>\n",
$mystr, $mynum, $myfloat);
?>
```

Here's the output from this program:

Greetings Planet Earth from 0x64 on behalf of 3.141593<br>