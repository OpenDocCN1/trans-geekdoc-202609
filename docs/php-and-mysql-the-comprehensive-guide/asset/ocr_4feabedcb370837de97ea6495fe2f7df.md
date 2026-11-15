parameters are optional except for the string itself. The length specifies after how many characters the break is inserted. If you omit it, the system automatically breaks after 75 characters. The separator is a string that is inserted at the position of the break. If you omit it, PHP inserts a line break with \n. The truncate parameter determines whether individual words are truncated (true). This is deactivated by default (false).

> Note
> If you activate truncation, then wordwrap() works in the same way as chunk_split().

In the following script, breaks are inserted in the string after every three characters. However, as whole words are retained, the separation only occurs for the individual words PHP, CMS, and SHOP.

```
<?php
$a = "PHP CMS SHOP";
echo wordwrap($a, 3);
?>
```

# Listing 7.3 "wordwrap()" ("wordwrap.php")

You won't see anything in the browser in this example. Why is that? The wrapping is done with \n, so you can only see it in the source text (see Figure 7.3). HTML does not recognize \n and ignores it.

You could now simply enter <br /> as the separator.

```
wordwrap($a, 3, "<br />");
```

![](bbox=[0.146, 0.592, 0.706, 0.772])

# Figure 7.3 The Wrap Is Only Visible in the Source Text

Or you can use the nl2br(String) function. It converts all breaks in a string with \n into breaks with the <br /> HTML tag.