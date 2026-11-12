And now here's a file called userequire.php that uses the function GetDateString in the myfunctions.php file:

```
<html><title>Today!</title>
<body>
Greetings! Today is
<?php
    require "myfunctions.php";
    print GetDateString();
?>
</body></html>
```

When you view this userequire.php file in a browser, you see something like this:

Greetings! Today is Tuesday, June 8, 2010

Hopefully by 2010, computers will be so powerful we won't need to write code in PHP or any other language.

I started the myfunctions.php file with <?php and ended it with ?>, even though I already had a <?php and ?> in the userequire.php file and I called require inside the <?php and ?> tag. I did this because the PHP rules require that every .php file must enclose the code inside the <?php and ?>, even if the require keyword is inside such delimiters.

# Including files

You can use the include keyword rather than the require keyword by simply changing the keyword require to include:

```
include "myfunctions.php";
```

The two keywords are interchangeable in functionality and syntax, with this single difference: If the PHP processor can't find the file you're trying to require or include, and you use a require statement, you get a fatal error, and the processor stops processing your file, displaying an error message in the resulting HTML. But if you use an include statement and the processor can't find the file, the processor only issues a warning (and prints it to the HTML) and continues processing the rest of the file. For most situations, I use require, and if I do my homework and actually test my software, I shouldn't have to worry about it — the files I include or require should be present. (Okay, if you're a true hacker, you might write code that intentionally attempts to include a file that may or may not be present, and then handle the situation accordingly, but I prefer not to write such complex code. It's hard to maintain.)