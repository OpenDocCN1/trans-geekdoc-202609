# Core PHP Programming

![](bbox=[0.22187, 0.10645, 0.77813, 0.29045])

```
<HTML>
<HEAD>
<TITLE>Listing 1.1</TITLE>
</HEAD>
<BODY>
Today's Date: <?php print(Date("1 F d, Y")); ?>
</BODY>
</HTML>
```

Whitespace, that is spaces, tabs, and carriage returns, is ignored by PHP. Used judiciously, it can enhance the readability of your code. Listing 1.2 is functionally the same as the previous example, though you may notice more easily that it contains PHP code.

# Listing 1.2 Reformatting for Readability

```
<HTML>
<HEAD>
<TITLE>Listing 1-2</TITLE>
</HEAD>
<BODY>
Today's Date:
<?php
    /* today's date
*/
    print(Date("1 F d, Y"));
?>
</BODY>
</HTML>
```

You may also notice that in Listing 1.2 there is a line of code that begins with a slash followed by an asterisk. This is a comment. Everything between the /* and the */ * is

IT-SC book 32