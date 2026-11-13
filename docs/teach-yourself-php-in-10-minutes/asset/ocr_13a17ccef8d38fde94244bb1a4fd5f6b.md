For example, to blank out a telephone number before displaying a string, you could use the following:

```
echo ereg_replace(
    "\(([:digit:]]{3})\)[:digit:]]{3}-[:digit:]]{4}$",
    "(XXX) XXX-XXXX", $string);
```

Just like you can use eregi in place of ereg , to perform a non-case-sensitive search and replace using regex, you can use eregi_replace .